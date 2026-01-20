# CNET 5052 — Advanced Tools for Complex Network Analysis (Spring 2026)
This repository contains the complete instructional materials for CNET 5052 (Spring 2026) and serves as the canonical, living home for course content throughout the semester.

* Repo: [https://github.com/network-science-data-and-models/cnet5052_sp26](https://github.com/network-science-data-and-models/cnet5052_sp26)


---

## Course information

* **Course:** CNET 5052 — Advanced Tools for Complex Network Analysis
* **Term:** Spring 2026
* **Meeting time:** Tuesdays, 1:30–4:50pm
* **Location:** 177 Huntington Ave, Room 226
* **Credits:** 4

This course extends the foundations of CNET 5051 into a set of advanced, research-facing tools for complex network analysis. Topics emphasize modern workflows for network inference and modeling (e.g. link prediction, sparsification, Bayesian/EM-style reasoning, stochastic block models and model fitting), computational methods for structure (e.g. distances, spectral tools, motifs, signed networks), and dynamics and simulation (e.g. reconstruction, games on networks, agent-based models).

A parallel goal throughout the semester is to develop good research habits: reproducible code, clear documentation, defensible evaluation, and careful interpretation. Students conclude the semester with a final project in the form of a short research-style paper accompanied by a reproducible GitHub repository.


### Design principles

* One week corresponds to one folder
* Week folders are as self-contained as possible
* Notebooks should run cleanly with **Restart Kernel → Run All**


### Instructors

* **Brennan Klein** — Network Science Institute, Northeastern University
* **Milo Trujillo** — Network Science Institute, Northeastern University


### Syllabus

* **PDF syllabus:** `syllabus/CNET_5052_Syllabus_sp26.pdf`

If you notice any discrepancy between the syllabus and this repository, please raise it—this repo will be updated continuously during the semester.

## Learning outcomes

By the end of the course, students should be able to:

1. Build reproducible network-analysis workflows in Python, including clear project structure, documentation, and version-controlled code suitable for research collaboration.
2. Implement and evaluate methods for network structure and inference, including graph distances, link prediction, and sparsification or sampling, using appropriate baselines and metrics.
3. Formulate and fit probabilistic and generative network models (e.g. stochastic block models), and interpret results with attention to uncertainty, assumptions, and diagnostics.
4. Apply computational tools for network structure beyond standard metrics, including spectral methods, motifs, and signed-network analysis.
5. Design and analyze network dynamics and simulation studies, including reconstruction problems, games on networks, and agent-based models.
6. Produce a research-style final project that integrates data, methods, results, and interpretation into a reproducible repository and a well-structured scientific paper.

---

## Coursework and grading

This is a once-weekly, hands-on, code-forward course focused on developing comfort, fluency, and independence with computational workflows in network science. Each class blends conceptual discussion, notebook-driven demonstrations, short implementation exercises, and guided work time.

Grading breakdown:

* **Participation and engagement (10%)** — attendance, preparation, and contribution to discussion
* **Assignments (45%)** — programming exercises, short write-ups, and theoretical questions
* **Final project (45%)**

  * Proposal: 5%
  * Mid-semester update presentation: 5%
  * Final paper and reproducible repository: 25%
  * Final presentation: 10%

---

## Final project

The final project is a research-style project designed to mirror how network science work is actually done. Students will pose a question or evaluate a method, assemble or generate data, implement an analysis pipeline, report results, and communicate limitations.

Projects may be methodological (e.g. comparing techniques, extending existing tools, theoretical investigations) or applied (e.g. focused empirical studies of social, biological, spatial, or infrastructure networks). Emphasis is placed on clarity, defensible evaluation, and reproducibility.

### Project milestones

* **Tue, Jan 27 (in class):** Proposal (up to 1 page) and short presentation
* **Tue, Feb 17 (in class):** Mid-semester update presentations
* **Tue, Apr 21 (in class):** Final project presentations and submission

### Final submission package

* A **reproducible GitHub repository** with:

  * a clear README describing the project and how to reproduce results
  * an environment specification (`requirements.txt` or `environment.yml`)
  * code and/or notebooks that run end-to-end
  * proper attribution for external data, code, or tools
* A **research paper (PDF)**, typically 8–12 pages
* An **in-class presentation** communicating motivation, methods, results, and limitations

Projects are evaluated on the clarity of the research question, correctness of implementation, quality of evaluation, careful interpretation of results, explicit discussion of limitations, reproducibility, and communication quality.

---

## Schedule → notebook mapping

| Week | Date   | Notebook(s)                                                           | Topic                                        |
| ---- | ------ | --------------------------------------------------------------------- | -------------------------------------------- |
| 01   | Jan 13 | `class_01_review_graphdistances.ipynb`                                | Introduction, growth models, graph distances |
| 02   | Jan 20 | `class_02_sparsification_linkprediction.ipynb`                        | Link prediction and sparsification           |
| 03   | Jan 27 | `class_03_bayesian_inference_em.ipynb`                                | Bayesian reasoning and EM                    |
| 04   | Feb 03 | `class_04_communities_sbm_forward.ipynb`                              | Communities and SBMs (forward process)       |
| 05   | Feb 10 | `class_05_graph_tool_sbm_inference.ipynb`                             | SBM inference with `graph-tool`              |
| 06   | Feb 17 | `class_06_spatial_networks.ipynb`                                     | Spatial networks and project updates         |
| 07   | Feb 24 | `class_07_ml_workflows_network_data.ipynb`                            | ML workflows for network data                |
| 08   | Mar 10 | `class_08_big_data_hyperloglog.ipynb`                                 | Big data topics; HyperLogLog                 |
| 09   | Mar 17 | `class_09_dynamics_reconstruction.ipynb`                              | Dynamics and network reconstruction          |
| 10   | Mar 24 | `class_10_games_abms.ipynb`                                           | Games on networks and ABMs                   |
| 11   | Mar 31 | `class_11_spectral_methods.ipynb`                                     | Spectral methods                             |
| 12   | Apr 07 | `class_12_motifs_signed_networks.ipynb`                               | Motifs and signed networks                   |
| 13   | Apr 14 | `class_13_flexible_topics_tooling.ipynb`                              | Flexible topics and tooling                  |
| 14   | Apr 21 | `class_14_final_presentations.ipynb`                                  | Final project presentations                  |

---

## Use of AI tools

AI tools (e.g. ChatGPT, Copilot, Claude) may be used when permitted by an assignment. Their use must be transparent and critically evaluated. You remain responsible for the accuracy, originality, and interpretation of all submitted work. AI should be treated as a tool to extend your abilities, not a replacement for your own reasoning.

---

## Academic integrity

All students are expected to follow Northeastern University’s Academic Integrity Policy. Proper citation is required for all external code, data, text, or ideas. Suspected violations will be referred to the Office of Student Conduct and Conflict Resolution.

---

## License

This repository is released under the **MIT License**, unless otherwise specified in individual subdirectories.

---

## Acknowledgments

The structure and workflow of this repository are inspired by the PHYS 7332 Network Science Data & Models course, adapted here for an advanced, tools-focused master's-level course.
