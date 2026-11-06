Initial Implementation: AI Act Classification Uncertainty
Research title: Representing Uncertainty in Rule-Based Classification of AI Act Use Cases
Team: Synthetix
Researchers: Avila Kumar Rajaboina and Manideep Galipelli
Project: — AI Act Classification Uncertainty

1. Project overview
This project explores how a rule-based screening system can represent missing facts and unresolved legal questions when examining hypothetical AI use cases under selected provisions of the European Union Artificial Intelligence Act (EU AI Act). The initial implementation compares a conventional binary baseline with an uncertainty-aware workflow that can request additional information or escalate a case for specialist review.

This submission is an unexecuted research implementation, not a completed legal assessment or a compliance tool.

2. Submission files
The submission contains two files:
- Team_Synthetix_Initial_Implementation.ipynb — a self-contained Jupyter Notebook with imports, embedded draft data, preprocessing functions, prototype classification logic, decision-trace generation, and planned evaluation steps.
- README.md — project description, dependencies, data access, and instructions for future execution.
The notebook includes its supporting code and input data. Separate Python modules and data folders are not required.

3. Dataset and legal source
The notebook contains 140 hypothetical AI use cases arranged into 70 A/B pairs, together with 19 draft rule identifiers. The draft records are stored inside the notebook as compressed CSV text and decoded in memory when the notebook is run. They are research inputs, not independently adjudicated legal cases.

The intended legal reference is Regulation (EU) 2024/1689, with a focus on selected provisions of Article 5, Article 6, and Annex III.

Official source: https://eur-lex.europa.eu/eli/reg/2024/1689/oj/eng

4. Software requirements
- Python 3.10 or newer
- Jupyter Notebook or JupyterLab
- Python standard library for the research code (no additional data-science packages required)
To install Jupyter Notebook on Windows, open Command Prompt and enter:
py -m pip install notebook

5. Notebook organization
1. Research design: project scope and four research questions.
2. Imports: required Python libraries.
3. Data access: embedded benchmark and draft rule codebook.
4. Data loading and preprocessing: CSV and JSON parsing, input checks, and preservation of unknown versus absent facts.
5. Rule evaluation and traces: predicate status, candidate-rule references, and recorded decision evidence.
6. Prototype approaches: binary baseline and uncertainty-aware decision routing.
7. Experimental design: paired-case comparison and descriptive evaluation functions.
8. Planned execution: a notebook cell that runs the experiment when executed later.
9. Future legal validation: placeholder for independently adjudicated labels and expert review.

6. How to run the notebook later
The notebook is supplied without executed cells or saved outputs, as required for the initial submission. To run it after submission:
1. Extract the submission ZIP to a folder.
2. Open Command Prompt in that folder.
3. Start Jupyter Notebook:
   py -m notebook
4. Open Team_Synthetix_Initial_Implementation.ipynb.
5. Run the cells in order, from top to bottom.
No separate dataset download is needed for the embedded hypothetical benchmark.

7. Planned evaluation
The implementation provides a starting point for:
- RQ1: identifying changes in prototype actions between paired scenarios.
- RQ2: comparing definitive-output and uncertainty-routing frequencies across the two approaches.
- RQ3: assessing the structural completeness of recorded decision traces.
- RQ4: summarizing which cases are routed for missing information or specialist review.
These are descriptive software measures. Legal accuracy, incorrect definitive classification rates, and appropriateness of specialist review cannot be established without qualified legal adjudication.

8. Research limitations
The benchmark uses hypothetical scenarios, the rule representations are drafts, and no independent legal gold labels are currently available. A fixed legal-source cutoff and review by qualified legal experts are needed before substantive regulatory claims can be made. The prototype does not provide legal advice or certify EU AI Act compliance.

9. Submission status
Initial implementation only: the Jupyter Notebook is provided with empty execution counts and no saved cell outputs. The submission demonstrates a feasible technical approach without presenting experimental findings as completed research results.