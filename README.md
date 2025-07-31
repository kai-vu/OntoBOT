# 🤖 OntoBOT: A Unified Ontology for Personal Service Robotics

> 📄 **Official repository for the paper:**  
> _“An Ontology for Unified Modeling of Tasks, Actions, Environments, and Capabilities in Personal Service Robotics”_  
> _Martorana, Urgese, Tiddi, Schlobach (K-CAP 2025)_

---

## Overview

**OntoBOT** is a modular OWL ontology developed to **formally describe** the elements involved in **task execution by service robots**.  
It enables reasoning about:

- What a robot can do (`obot:Capability`)  
- Where it operates (`obot:Environment`)  
- What physical objects afford (`obot:Affordance`)  
- How tasks are structured and executed (`obot:Task`, `pko:Action`, `pplan:Step`)

This ontology bridges symbolic task descriptions and physical feasibility — allowing systems to **reason about actionability based on context, embodiment, and capabilities**.

---

## 📌 Purpose of the Paper

> “Robots should not just know _what to do_, but whether they _can_ do it.”

Current robotics ontologies often focus on isolated domains (e.g., perception, execution, planning).  
**OntoBOT** addresses the need for **interoperable**, **grounded**, and **reasoning-capable** models by integrating and extending:

- [DUL](http://www.ontologydesignpatterns.org/ont/dul/DUL.owl#): foundational entities and agents  
- [SOMA](http://www.ease-crc.org/ont/SOMA.owl#): affordances and spatial reasoning  
- [PKO](https://w3id.org/pko#) & [PPlan](https://vocab.linkeddata.es/p-plan/index.html): procedural task structure  
- [ROS.owl](http://data.mksmart.org/onto-ros/class#): robot software/hardware components

The paper evaluates OntoBOT using **two household activities**, **four robots**, and a **set of competency questions** executed via SPARQL.

---

## Core Concepts

OntoBOT integrates and extends foundational ontologies to model how robots perceive, act, and reason.  
Its design enables symbolic planning that is grounded in execution and environmental feasibility.

| Concept         | Description |
|----------------|-------------|
| `obot:Agent`    | A robot, modeled with ROS nodes and capabilities |
| `obot:Environment` | A physically bounded space (e.g., kitchen), containing `obot:Component`s |
| `obot:Component` | A physical object the robot can interact with (e.g., bowl, fridge) |
| `obot:Affordance` | An interaction possibility (e.g., grasping, pouring), relational between agent and object |
| `obot:Task`     | A goal-oriented activity, composed of actions and steps |
| `obot:Capability` | An executable functionality (e.g., grasp), linked to affordances via `enablesAffordance` |

### 📘 Ontology Schema

![OntoBOT Schema Diagram](<img width="763" height="796" alt="ontoBOT" src="https://github.com/user-attachments/assets/cff3b794-b7ef-4189-80ec-bd5011bf3302" />)

> **Figure**: Core structure of the OntoBOT ontology, illustrating how agents, environments, tasks, affordances, and capabilities are semantically interlinked.  
> Based on `obot`, `pko`, `pplan`, `soma`, and `ros` ontologies.

---

## Case Study: Kitchen Scenario

We model two robotic activities in a household kitchen, as inspired by the [EUROBIN Coopetitions](https://www.eurobin-project.eu/index.php/competitions/coopetitions):

1. **Prepare breakfast**: serve cereal and orange juice  
2. **Reorganize kitchen**: tidy items, load dishwasher

These were used to validate OntoBOT through **competency questions**, such as:

- ❓ What affordances are required by an activity?  
- 🤖 Which robots (Tiago, HSR, UR3, Stretch) have those capabilities?  
- ⚠️ What prevents a robot from completing a task?

🧪 Results were generated using **manually instantiated RDF graphs** and **SPARQL queries**, available below.

---

## 📂 Repository Contents

OntoBOT/
│
├── ontoBot/ # Ontology files (.ttl, .owl)
├── case-study/ # RDF data for robots, tasks, environment
│ ├── prepare-breakfast.ttl
│ ├── reorganise-kitchen.ttl
│ ├── robot-capabilities.ttl
│ └── cqs.ipynb # Jupyter notebook with SPARQL queries
├── docs/ # Diagrams and visualizations
├── LICENSE
└── README.md


---

## 🔍 Evaluation via Competency Questions

> _"Given this ontology, can we answer relevant task planning questions?"_

✅ **Yes.** All questions from the paper were answered via SPARQL, such as:

- `CQ1`: What objects and affordances are involved in “prepare breakfast”?  
- `CQ4`: Which robot is capable of all required actions?  
- `CQ6`: What steps fail for Robot X due to missing capabilities?

See: [`case-study/cqs.ipynb`](./case-study/cqs.ipynb)

---

## 📜 Citation

If you use OntoBOT, please cite:

```bibtex
@inproceedings{martorana2025ontobot,
  title     = {An Ontology for Unified Modeling of Tasks, Actions, Environments, and Capabilities in Personal Service Robotics},
  author    = {Martorana, Margherita and Urgese, Francesca and Tiddi, Ilaria and Schlobach, Stefan},
  booktitle = {Proceedings of the 12th International Conference on Knowledge Capture (K-CAP)},
  year      = {2025},
  publisher = {ACM}
}
