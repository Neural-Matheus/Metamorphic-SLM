# Framework for fairness testing with RAG

A Metamorphic Testing Framework for Analyzing Large-Language Model fairness with RAG

# Modules

Execute the notebook files in the order that they are described to replicate the pipeline discribe in the paper

In order to replicate, you need to download our *faiss* folder [here](https://drive.google.com/drive/folders/1yWG_WZ_RgF1-aPChpK9pi6htg5jsynMu?usp=sharing) and move it inside Execution Module folder 

- **Execution Module**: Communicates with LLMs to get the responses
  - Files:
    - **dataset-cleaning.ipynb**: Responsible for cleaning the dataset used in the retriever. Outputs *gpt2-toxic-conversations.csv* (which was not added due to size limitations)
    - **CreatedPerturbations_Menu_ipynb**: Download (if not downloaded yet) each one of the LLMs used in this work and get the responses given by these models for all the normal and perturbed inputs. Outputs a file with these data with the prefix *CreatedFunctions_Fairness_Iteration0_sentiment_analysys_{{model_name}}.csv*
    - **Fairness/fairness_sa.csv**: Dataset used in METAL. Contains real comments and have been used to perform sentiment analyzes
    - **faiss**: Folder containing binary files for embeddings and parameters of the FAISS retriever

- **Evaluation Module**: Generates sheets with derived data from the Execution Module output data
  - Files:
    - **Extractor.ipynb**: Generates the *sentiment mismatches* folder files, with the difference between the classification given by the models to the normal inputs and perturbed inputs
    - **Retriever.ipynb**: Use any of the sheets generated in the Execution Module to copy the inputs given to LLMs and generates the *retrieval_summary.csv* file
    - **RetrievalSummaryAnalyzer.ipynb**: Use *retrieval_summary.csv* and the files in *sentiment mismatches* to generate another sheet with data to answer most of the RQs (except for RQ1.2)
    - **Metric_Analysis.ipynb**: Generate data to answer the RQ1.2 (Retriever Robustness Score - RRS)

- **Answers Module**: Use data from prior modules to answer the RQs
  - **RQsAnswers.ipynb**: Use the data from *analyze of sentiment mismatches* folder and from *Metric_Analysis.ipynb* to answer the RQs. Data from *analyze of sentiment mismatches* comes from *RetrievalSummaryAnalyzer.ipynb* notebook

