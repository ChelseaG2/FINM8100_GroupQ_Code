# Motivation

While MLLMs exhibit advanced multimodal alignment capabilities, hallucinations remain a significant impediment to their practical deployment in financial applications where numerical precision is paramount. From a data science perspective, this issue extends beyond the commonly cited "next most likely token" generation strategy to encompass several specific mechanisms that exacerbate inaccuracies in financial contexts.

Three primary mechanisms contribute to hallucinations when MLLMs process financial data, each supported by recent empirical evidence. First, **numerical discretization and tokenization** decompose numerical values such as "3.1415" into multiple discrete sub-word tokens (e.g., "3", ".", "14", "15"), fragmenting the continuous semantic meaning and making it difficult for models to treat numbers as coherent quantitative entities. Golkar et al. (2023) explicitly demonstrate that standard tokenization splits such values into five or more tokens and propose a continuous alternative that reduces numerical error by up to 40% in scientific datasets. Singh and Abdou (2024) further quantify this effect through large-scale ablations, showing that arithmetic error grows monotonically with token length across GPT-3.5/4 variants, establishing that the bottleneck is fundamentally computational rather than merely linguistic.

Second, **probability-driven numerical generation** optimizes outputs for statistical plausibility rather than factual accuracy, enabling models to produce financial figures that appear authoritative but lack precision. This pathology has been systematically documented by Malghan et al. (2024) in clinical settings, where LLMs generate "authoritative yet inaccurate" numeric hallucinations in medical tables, representing a direct analogue to financial applications where precise quantitative accuracy is equally critical.

Third, **absence of inherent quantitative verification** allows outputs that maintain linguistic coherence while violating fundamental financial identities. During text generation, models focus on selecting the most probable next sub-token rather than ensuring the accuracy of the complete numerical value, meaning a model might generate numbers simply because this token sequence appears statistically likely, regardless of whether it represents a valid quantity in the given financial context.

This analysis gains theoretical support from recent developments in commercial LLM training. Contemporary frontier models like GPT-4o incorporate mathematics-specific training and demonstrate enhanced performance on mathematical benchmarks. Zhang et al. (2024) demonstrate that targeted mathematical fine-tuning unlocks advanced reasoning capabilities absent in vanilla checkpoints, suggesting sophisticated numerical processing capabilities exist within their vector spaces but remain partly inaccessible when numbers traverse the lossy text pipeline due to tokenization bottlenecks.

The core hypothesis posits that numerical data could bypass token-level discretization through visual channels such as plots or charts, significantly enhancing quantitative prediction accuracy. Wang et al. (2024) provide direct empirical support for this approach, demonstrating that GPT-4o and Claude-3 achieve markedly higher exact-answer accuracy on numeric extraction when identical data are presented as charts rather than raw text tables. Visual representations arrive at the model as dense embedding grids, sidestepping sub-token fragmentation and allowing the vision encoder to preserve magnitudes in a geometry that the language decoder can effectively exploit. This approach could circumvent tokenization-induced degradation while leveraging the models' demonstrated mathematical reasoning capabilities, potentially reducing numerical hallucinations while preserving interpretative value for financial analysis.

## References

Golkar, S., Pettee, M., Eickenberg, M., Bietti, A., & Ho, S. (2023). *xVal: A continuous numerical tokenization for scientific language models* (arXiv No. 2310.02989). arXiv. https://doi.org/10.48550/arXiv.2310.02989

Malghan, R., Yang, L., & Xu, L. (2024). *Evaluating computational accuracy of large language models in numerical healthcare tasks* (arXiv No. 2501.13936). arXiv.

Singh, A., & Abdou, M. (2024). *Tokenization counts: The impact of tokenization on numerical reasoning* (arXiv No. 2402.14903). arXiv.

Wang, Y., Liu, H., Li, J., & Zhu, J. (2024). *ChartInsights: Evaluating multimodal large language models for low-level chart question answering*. *Findings of EMNLP 2024*, 710–724. https://aclanthology.org/2024.findings-emnlp.710

Zhang, D., Huang, X., Zhou, D., Li, Y., & Ouyang, W. (2024). *Accessing GPT-4-level mathematical Olympiad solutions via Monte Carlo tree self-refine with LLaMA-3 8B* (arXiv No. 2406.07394). arXiv.

# Methodology

## Experiment Procedure

The experiment was organised around two forecasting scenarios that differed in both prediction target and feature composition. In the index level setting the NASDAQ Composite served as the dependent series, modelled against twelve U.S. interest rate benchmarks and eight standard macroeconomic indicators. In the firm level setting the closing price of NVIDIA (NVDA) was forecast using the same twenty macro-financial factors together with ten quarterly firm-specific fundamentals, yielding a richer but structurally comparable input space. 

The experimental design employed a systematic sliding window approach where a temporal cursor advances one month at a time through the merged monthly panel, creating highly overlapped yet chronologically ordered training examples. For every anchor month t, the preceding input_span months (either 6 or 12 months) constitute the conditioning context, while ground truth targets are recorded at multiple prediction horizons: 1, 3, 6, and 12 months ahead. This multi-horizon approach enables comprehensive evaluation of short to medium term predictive capability within a single modelling framework. The rolling construction maximises sample size under strict non-look-ahead constraints, with windows containing unresolved missing values after forward filling being systematically excluded. In the firm level scenario, quarterly fundamentals are temporally aligned to the last month inside each context window, ensuring only information that would have been publicly available at time t is incorporated into the conditioning set.

For every month end observation, the full conditioning window was rendered twice: once as a multi-panel graphic that plotted the target series alongside its explanatory variables, and once as a tokenised text table that listed identical values. A single natural language prompt template was applied uniformly across all experimental conditions, with only two dynamic placeholders varying between requests: the target asset name (NASDAQ Composite or NVDA) and the specific forecast horizon (1, 3, 6, or 12 months). This standardised prompt requested from the language model (i) a directional trend forecast, (ii) a percentage change estimate, and (iii) a concise textual justification, all to be returned in a fixed JSON schema. 

For each scenario the graph instances and their text equivalents were paired and written to batch items, producing four batch item types (NASDAQ graph, NASDAQ text, NVDA graph, NVDA text) that were uploaded to the OpenAI Batch API. Two LLM models were evaluated on every batch item: ChatGPT-4o with standard multimodal processing and o4-mini with enhanced reasoning mode (reasoning effort set to high, structured JSON output format). Aside from the model identifier and reasoning configuration, all request parameters were held constant, ensuring that comparisons isolate the effects of model capacity and input modality. The API's asynchronous execution returned structured files in which each line recorded the user content, the assistant's JSON prediction (trend sign, percentage magnitude, confidence label and justification), and runtime metadata; these artefacts were archived verbatim, preserving a full audit trail for downstream statistical evaluation.

# Discussion

## RLHF

Recent work on alignment suggests that reinforcement learning from human feedback (RLHF) pushes LLM toward risk averse behaviours: they prefer answers that minimise the chance of negative human judgements rather than maximise predictive accuracy. Empirically, this bias often manifests as longer, highly qualified explanations coupled with moderate or "neutral" confidence labels (rather than "confident" or "not confident"). In the experiment every prediction across both GPT-4o and o4-mini was tagged "neutral", despite large variation in subsequent errors. This pattern is consistent with the "risk averse fine-tuning" phenomenon: when the reward model penalises over confidence more than it rewards well calibrated boldness, the optimal strategy for the policy model is to stay in the middle of the scale (Chaudhary, Dinesha, Kalathil, & Shakkottai, 2024, Huang, Ouyang, & Krueger, 2024).

Calibration studies further show that alignment steps compress a model's confidence distribution. Zhu et al. (2023) document a systematic collapse of calibrated probabilities after RLHF, leading to poorer discrimination between easy and hard queries (Zhu, Xu, Wang, Zhang, & Mao, 2023). Taken together, these findings imply that the all neutral outputs are not an artefact of prompt design but a direct consequence of alignment objectives prioritising safety and user acceptability. While such conservatism reduces the risk of confidently wrong claims, it also eliminates potentially informative variation in confidence, making it impossible to exploit confidence scores for downstream decision making or error detection in financial forecasting. 

Chaudhary, S., Dinesha, U., Kalathil, D., & Shakkottai, S. (2024). *Risk-averse fine-tuning of large language models*. arXiv preprint arXiv:2501.06911.

Huang, S., Ouyang, L., & Krueger, D. (2024). *Reward model over-optimisation in iterated RLHF*. arXiv preprint arXiv:2505.18126.

Zhu, C., Xu, B., Wang, Q., Zhang, Y., & Mao, Z. (2023). *On the calibration of large language models and alignment*. In *Findings of EMNLP 2023*.

# Future Work

While the current approach successfully bypasses tokenization constraints on the input side through visual chart representations, the text based output generation still suffers from the same tokenization bottlenecks identified in the motivation. Future research should explore end to end visual pipelines that eliminate tokenization entirely from both input and output phases.

Specifically, image generation models such as OpenAI's Image-1 could process multimodal context (combining textual market analysis with visual time series charts) and directly output visual predictions: annotated charts showing forecasted price movements with confidence intervals. This approach would leverage the mathematical reasoning capabilities embedded in the models' vector spaces while completely circumventing the probabilistic text decoder that fragments numerical outputs into error prone sub-tokens.

Such image to image forecasting systems could potentially achieve the dual objectives of maintaining high numerical precision (through visual representation of predictions) while preserving interpretability (through visual annotations and contextual explanations embedded directly in the output charts), representing a fundamental shift from text centric to vision centric financial AI systems.








