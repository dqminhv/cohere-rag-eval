# Cohere Toolkit RAG Evaluation

**RAG Pipeline Evaluation and Optimization**

This repository is a part of Enterprise-Search-Chatbot project at fellowship.ai. It offers a comprehensive toolkit for evaluating and refining Retrieval-Augmented Generation (RAG) pipelines built from Cohere toolkit. It utilizes RAGAS and LangSmith for evaluation, and . 

## **Core Functionalities:**

* **Synthetic Test Data Generation:**
  - Create diverse and challenging question-answer pairs using the RAGAS framework.
  - This ensures a thorough evaluation of your RAG system's capabilities.  You can find the implementation in this [synthetic test data generation notebook](/notebook/1-ragas-synthetic-test-data-generation.ipynb) 
  - Test datatsets for all of the evaluation tests in this repo are stored [here](/data-test/test-dataset/)

* **RAG Component Optimization:**
  - Delve into the optimization of various RAG components, enabling you to fine-tune your system for optimal performance:
    - **a) Chunking Strategy:**  Investigate how different approaches to splitting text into chunks impact retrieval and generation quality. Refer to this [Chunking strategy optimization notebook](/notebook/optimization/7.1-rag-opimization-chunking-strategy.ipynb)
    - **b) Prompt Templates:**  Experiment with various prompts to guide the large language model (LLM) and influence the quality and direction of its responses. Refer to this [Prompt optimization notebook](/notebook/optimization/5-rag-prompt-opimization.ipynb)
    - **c) Query Transformation:**  Explore techniques for transforming user queries into forms that enhance retrieval and generation effectiveness. Refer to these notebooks [1](/notebook/optimization/7.2-rag-opimization-cohere-query-transformation.ipynb), [2](/notebook/optimization/7.3-rag-opimization-hyde.ipynb), [3](/notebook/optimization/7.4-rag-opimization-multi-query.ipynb) 
    - **d) Reranking:**  Evaluate the impact of reranking retrieved documents on the final response selection process. Refer to this [notebook](/notebook/optimization/7.5-rag-opimization-rerank.ipynb)
  - Test results for optimization process can be found [here](/data-test/eval-result/optimization-test-result/)
  - To evaluate the effectiveness of different optimization configurations, Rank-Based Methods can be employed. This approach involves the following steps:

    - Ranking Individual Options: For each performance score, assign a descending rank to each optimization option. A higher rank indicates better performance.
    - Calculating Average Ranks: Determine the average rank for each optimization option across all performance scores.
    - Identifying the Best Option: The optimization option with the highest average rank is typically considered the most effective, as a higher rank signifies superior performance.
    By using Rank-Based Methods, you can systematically compare and select the optimization configuration that yields the most favorable results.


* **Chat History Extraction:**
  - Extract chat history from a running Cohere toolkit Docker container for post-production evaluation. Refer to this [chat history extraction notebook](/notebook/2-chat-history-extraction.ipynb)
  - Analyze real-world user interactions to gauge system effectiveness.

* **Multi-Stage Evaluation:**
  - Conduct evaluations at different stages of the RAG pipeline's lifecycle:
    - **[Pre-Production](/notebook/3-cohere-toolkit-rag-pre-prod-eval.ipynb):** Employ predefined test data and ground truth to assess general performance metrics like answer relevancy and faithfulness. Real test run and results can be found [here](/notebook/pre-production%20evaluation/) and [here](/data-test/eval-result/)
    - **[Post-Production](/notebook/4-cohere-toolkit-rag-post-prod-eval.ipynb):** Analyze real-world user queries and system responses to understand user experience and identify areas for improvement. A sample test run and result can be found [here](/notebook/4-cohere-toolkit-rag-post-prod-eval.ipynb) and [here](/data-test/eval-result/eval_result_post_prod_test_dataset_hr_openai_deployment.csv)

* **Evaluation metrics**:
  - **Answer Relevancy**: Assesses how well the generated answer aligns with the given prompt. Incomplete or redundant answers receive lower scores, while higher scores indicate stronger relevancy.
  - **Faithfulness**: Measures the factual consistency of the generated answer with the retrieved context. It is calculated using both the answer and the context, with scores ranging from 0 to 1, where higher values indicate greater accuracy.
  - **Context Recall**: Evaluates how many relevant documents or pieces of information were successfully retrieved, emphasizing the importance of capturing all key details. Higher recall indicates fewer relevant documents were missed. Since recall focuses on not overlooking important content, it requires a reference (ground truth) for comparison during calculation.
  - **Context Precision**: measures the proportion of relevant chunks within the retrieved contexts. It is calculated as the average of precision@k for each chunk, where precision@k is the ratio of relevant chunks at rank k to the total number of chunks at that rank.
  
  For pre-production evaluation, we use all four metrics. In post-production, since we lack ground truth for user queries, we evaluate using only three metrics: Answer Relevancy, Faithfulness, and Context Precision.

* **LangSmith**
  - Evaluation test run can be store and run within [LangSmith](https://smith.langchain.com/) account.

## **Getting Started:**

1. **Prerequisites:**
    - Install Python (version 3.6 or later recommended).
    - Install required libraries using `pip install -r requirements.txt`.
    - Set up a Cohere toolkit Docker container (refer to Cohere documentation).

2. **Running the Notebooks:**
    - Launch Jupyter Notebook and navigate to the repository directory.
    - Each notebook provides detailed instructions and expected inputs to facilitate your exploration.

## **Envisioning the Future:**

* **Automated Testing:** Integrate automated testing tools to streamline the evaluation process and ensure consistent performance over time.
* **Benchmarking:** Incorporate standardized benchmarks for RAG performance, enabling comparisons with other systems and tracking progress.
* **Deployment Pipeline:** Develop a robust deployment pipeline to seamlessly integrate the optimized RAG system into the production environment.
* **Visualization Tools:** Implement visualization tools to provide intuitive insights into the behavior and decision-making processes within the RAG pipeline.

## **License:**

This repository is distributed under the MIT License. Refer to the LICENSE file for details.

## **Appendix**
* Evaluation results summary can be found [here](/data-test/eval-result/Evaluation%20Results%20Summary.pdf)