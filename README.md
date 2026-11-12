
Failure Attribution for Coding Agents

<p align="center">
  <strong>Helping AI coding agents understand what went wrong after a code change.</strong>
</p><p align="center">
  A lightweight, rule-based system for analyzing test failures, tracking code changes, and identifying potential regressions.
</p>---

🔍 The Problem

When an AI coding agent modifies code and tests fail, it needs to understand why they failed.

Was the failure already present? Did the change introduce a regression? Did the modification make progress, or did nothing actually change?

Without this distinction, an agent may revert useful changes, repeat unsuccessful fixes, or commit broken code.

💡 The Approach

Failure Attribution for Coding Agents analyzes test results before and after a code change, alongside the Git diff, to determine the likely cause of a failure.

The system combines test-output comparison with code-change evidence to produce an attribution label that can guide the agent's next decision.

⚙️ How It Works

       Code Change
            │
            ▼
    Run Tests (Before)
            │
            ▼
    Run Tests (After)
            │
            ▼
    Compare Test Results
            │
            ▼
      Analyze Git Diff
            │
            ▼
    Failure Attribution
            │
            ▼
     Classification Label

🧠 Classification System

The classifier produces one of seven labels:

Label| Interpretation
"PASSED"| Tests pass after the change.
"PRE_EXISTING_ENV"| Evidence suggests the failure existed before the change or is environment-related.
"NO_EFFECT"| The change did not meaningfully affect the failure.
"PROGRESS"| Evidence suggests the change improved the outcome.
"REGRESSION_LIKELY"| Evidence suggests the change introduced a failure.
"UNKNOWN"| Available evidence is insufficient or ambiguous.
"NO_SIGNAL"| No meaningful test result is available for attribution.

🛠️ Project Components

File| Purpose
"failure_attribution_kaggle.ipynb"| Implements the attribution classifiers and synthetic benchmark experiments.
"attribution_prompt_snippet_v2.md"| Provides instructions for applying failure attribution in coding-agent workflows.

🧪 Evaluation

The project uses a synthetic benchmark containing author-created scenarios to examine how different attribution approaches classify failures.

The evaluation compares:

- The original rule-based classifier.
- An improved attribution classifier.
- A deterministic emulation of the prompt-based attribution rules.

The experiments focus on classification accuracy, false regression predictions, and the handling of pre-existing failures.

Important: These results are limited to the constructed benchmark. They do not establish performance on real-world repositories or prove that attribution improves coding-agent recovery.

🚀 Getting Started

Requirements

- Python 3.12+
- Git
- Jupyter Notebook
- pytest
- NumPy
- pandas
- Matplotlib
- seaborn
- scikit-learn

Installation

Clone the repository:

git clone https://github.com/YOUR_USERNAME/failure-attribution-for-coding-agents.git
cd failure-attribution-for-coding-agents

Install dependencies:

pip install numpy pandas matplotlib seaborn scikit-learn pytest jupyter

Launch the notebook:

jupyter notebook failure_attribution_kaggle.ipynb

Run the notebook cells in order.

⚠️ Current Limitations

- Evaluation currently relies on a synthetic benchmark.
- The benchmark scenarios are author-created and relatively small.
- The prompt instructions have not yet been evaluated with a live coding agent or LLM.
- Performance on external repositories and real-world software failures remains untested.
- The impact of failure attribution on agent recovery decisions has not yet been established.

🔮 Future Directions

- Evaluate the system with real AI coding agents and LLMs.
- Test attribution on external open-source repositories.
- Improve detection of ambiguous environment failures and regressions.
- Explore how attribution labels can guide agent recovery strategies.
- Investigate whether better failure attribution leads to more reliable code changes.

---

👩‍💻 Author

Riya Chauhan


---

<p align="center">
  <i>Building more reliable feedback and decision-making systems for AI coding agents.</i>
</p>
