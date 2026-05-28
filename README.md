# Character Ontology Paper: "Fans Reconstruct Heroes"

This repository accompanies the manuscript **"Fans Reconstruct Heroes: Modeling Fictional Characters in Participatory Culture"**, submitted to the *Semantic Web Journal* Special Issue on *Semantic Web and Ontology Design for Cultural Heritage*.

## 📜 Overview
The paper introduces the Character Module with evaluation using Competency Quesitons and Case Study of the **GOLEM Ontology** (Graphs and Ontologies for Literary Evolution Models), a framework for modeling fictional characters across canonical and fan-created works. The ontology:
- Bridges literary theory with participatory culture
- Provides formal representation of dynamic, multi-contextual characters
- Ensures interoperability with CIDOC-CRM, DOLCE, and other standards

## 🧩 GOLEM Ontology Features
| Feature | Description |
|---------|-------------|
| **Mixed Approach** | Top-down (theory) + bottom-up (fan data) integration |
| **Modular Design** | Reusable components for characters, events, relationships, etc. |
| **Interoperability** | Aligns with CIDOC-CRM, DOLCE-Lite-Plus, and LRMoo |
| **Implementation** | Developed in Protégé, documented with PyLode |

## 🔍 Case Study: Greek Mythology Fanfiction
**Dataset**: 10 curated stories from AO3's *Ancient Greek Religion and Lore* fandom (tagged "Major Character Death")

### Methodology
1. **Annotation**:
   - Manual tagging of death events (victim, perpetrator, method)
   - LLM-assisted feature extraction (Deepseek-V3) with human correction
2. **Modeling**:
   - RDF conversion using GOLEM ontology
   - SPARQL querying for evaluation
   
🔗 **Ontology Resources**:
- [GOLEM Main Repository](https://github.com/GOLEM-lab/golem-ontology)
- [SPARQL Endpoint](http://graph.golemlab.eu:8890/sparql)
- [Case Study Knowledge Graph]([https://golemlab.eu/graph/Greek10_Example](https://golemlab.eu/graph/Greek10_Character_Module_Demo))

## 📂 Repository Structure
```text
Character_Ontology_Paper/
├── CaseStudy_ttl/            # RDF datasets for case study
├── Controlled_vocabulary/           # Controlled Vocabulary RDF datasets
├── CQ-SPARQL-updated                 # Competency questions & queries
└── README.md                 # This file
```

## 🏗️ How to Use
1. Explore the CaseStudy_ttl and Controlled_vocabulary
2. Run SPARQL queries from CQ-SPARQL at our endpoint
3. Refer to the [GOLEM documentation](https://github.com/GOLEM-lab/golem-ontology) for ontology details

## 📄 Citation
```bibtex
@article{yang2025golem,
  title={Fans Reconstruct Heroes: Modeling Fictional Characters in Participatory Culture},
  author={Yang, Xiaoyan and Pianzola, Federico},
  journal={Semantic Web Journal},
  year={2025},
  note={Under review}
}
