Failure Attribution for Coding Agents

A rule-based failure attribution system that helps coding agents understand whether a code change fixed an issue, caused a regression, or left an existing failure unchanged.

Overview

The system compares test results before and after a code change and examines the Git diff to classify the outcome. It includes an original classifier, an improved classifier, and a synthetic benchmark for evaluation.

Classification Labels

Label| Meaning
"PASSED"| Tests pass after the change.
"PRE_EXISTING_ENV"| Failure existed before the code change.
"NO_EFFECT"| The change did not affect the failure.
"PROGRESS"| Evidence suggests improvement.
"REGRESSION_LIKELY"| Evidence suggests the change introduced a failure.
"UNKNOWN"| Evidence is insufficient or ambiguous.
"NO_SIGNAL"| No meaningful test result is available.

Project Files

File| Description
"failure_attribution_kaggle.ipynb"| Classifier implementations, synthetic benchmark, and evaluation.
"attribution_prompt_snippet_v2.md"| Prompt instructions for applying failure attribution in coding agents.

How It Works

1. Capture test results before a code change.
2. Run the same tests after the change.
3. Compare failures, error messages, and test outcomes.
4. Inspect the Git diff for relevant code changes.
5. Assign an attribution label based on the available evidence.

Setup and Usage

Requirements: Python 3.12+, Git, and pytest.

Clone the repository:

git clone https://github.com/YOUR_USERNAME/failure-attribution-for-coding-agents.git
cd failure-attribution-for-coding-agents

Install dependencies:

pip install numpy pandas matplotlib seaborn scikit-learn pytest jupyter

Launch the notebook:

jupyter notebook failure_attribution_kaggle.ipynb

Run the notebook cells in order.

Evaluation and Limitations

- Evaluated using a synthetic benchmark of author-created scenarios.
- Results are limited to the scenarios and test conditions included in the benchmark.
- The prompt instructions have not yet been evaluated with a live coding agent or LLM.
- The project does not yet establish whether failure attribution improves real-world agent recovery.

Future Work

- Evaluate with real coding agents and LLMs.
- Test on external repositories and real software failures.
- Improve handling of ambiguous environment and regression cases.
- Investigate whether attribution improves agent recovery decisions.

Author

Riya Chauhan
