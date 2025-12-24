# Mongolian Legal Entities Knowledge Graph

## Introduction

Reusability is one of the foundational principles in the Knowledge Graph Engineering (KGE) process defined by the iTelos methodology. Comprehensive project documentation plays a critical role in enhancing the reusability of resources handled and produced throughout the engineering process. A clear description of resources, processes, and sub-processes provides external readers with a thorough understanding of the project, thereby facilitating future exploitation of the project's outcomes.

## Project Overview

This project focuses on the construction of a Knowledge Graph utilizing open data from the State Registration of Legal Entities of Mongolia. The primary objective is to visualize, through a graph structure, the complex relationships among various stakeholders within the Mongolian corporate ecosystem.

### Relationship Categories

The project addresses the following relationship categories:

- **Shareholders and Members**: Individuals and entities holding ownership stakes in legal entities, including their classification and country of origin.

- **Officials and Controlling Entities**: Persons authorized to represent legal entities without a power of attorney, including their official positions and appointment dates.

- **Ultimate Beneficial Owners**: Natural persons who ultimately own or control legal entities, enabling transparency in corporate ownership structures.

Furthermore, for companies listed on the Mongolian Stock Exchange, the project aims to link and visualize relevant open datasets, creating an integrated view of corporate information that spans both registration data and capital market participation.

## Motivation and Significance

The transparency of corporate ownership structures is essential for various stakeholders, including regulatory authorities, financial institutions, investors, and the general public. In Mongolia, as in many jurisdictions, complex corporate structures can obscure the true ownership and control of legal entities.

### Key Benefits

This Knowledge Graph addresses transparency challenges by:

- Enabling the visualization of multi-layered ownership networks
- Facilitating the identification of individuals with significant influence across multiple entities
- Supporting regulatory compliance and anti-money laundering efforts
- Providing investors and business partners with comprehensive due diligence capabilities

## Project Structure

This project follows the iTelos methodology with the following structure:

```
knowledge_graph_legal_entities/
├── README.md
├── docs/
│   ├── 01-domain-of-interest/
│   ├── 02-project-development/
│   ├── 03-initial-resources/
│   ├── 04-purpose-formalization/
│   ├── 05-information-gathering/
│   ├── 06-language-definition/
│   ├── 07-knowledge-definition/
│   ├── 08-data-definition/
│   ├── 09-evaluation/
│   ├── 10-metadata-definition/
│   └── 11-open-issues/
├── data/
│   ├── raw/
│   ├── processed/
│   └── mapped/
├── ontology/
│   ├── teleology/
│   ├── teleontology/
│   └── protege-projects/
├── karma/
│   ├── models/
│   └── mappings/
├── graphdb/
│   ├── repositories/
│   └── configurations/
├── queries/
│   └── competency-questions/
├── scripts/
│   ├── data-collection/
│   ├── data-cleaning/
│   └── data-mapping/
└── results/
    ├── graphs/
    └── metrics/
```

## Documentation Structure

### Section 1: Domain of Interest (DoI)
Defines the spatial and temporal boundaries of the project scope.

**Location**: `docs/01-domain-of-interest/`

### Section 2: Project Development
High-level description of the data production process and strategy.

**Location**: `docs/02-project-development/`

### Section 3: Initial Resources
Description of pre-existing quality resources available for the project.

**Location**: `docs/03-initial-resources/`

### Section 4: Purpose Formalization
Scenarios, personas, competency questions, and ER model definition.

**Location**: `docs/04-purpose-formalization/`

### Section 5: Information Gathering
Collection of knowledge and data resources from identified sources.

**Location**: `docs/05-information-gathering/`

### Section 6: Language Definition
Concept identification, UKC alignment, and dataset filtering.

**Location**: `docs/06-language-definition/`

### Section 7: Knowledge Definition
Teleology, teleontology, and dataset cleaning activities.

**Location**: `docs/07-knowledge-definition/`

### Section 8: Data Definition
Entity identification and data mapping procedures.

**Location**: `docs/08-data-definition/`

### Section 9: Evaluation
Quality metrics and competency query execution results.

**Location**: `docs/09-evaluation/`

### Section 10: Metadata Definition
Metadata specifications for all produced resources.

**Location**: `docs/10-metadata-definition/`

### Section 11: Open Issues
Conclusions, limitations, and future work.

**Location**: `docs/11-open-issues/`

## Getting Started

### Prerequisites

#### Required Software

1. **Protégé** (v5.5.0 or later)
   - Ontology editor for creating and managing the teleontology
   - Download: https://protege.stanford.edu/
   - Used for ontology development, visualization, and reasoning

2. **Karma** (v2.0 or later)
   - Data integration tool for semantic mapping
   - Download: https://usc-isi-i2.github.io/karma/
   - Used for mapping source data to the ontology

3. **GraphDB** (Free or Enterprise Edition)
   - RDF triplestore and SPARQL query engine
   - Download: https://www.ontotext.com/products/graphdb/
   - Used for storing, querying, and reasoning over the knowledge graph

4. **Python Environment** (3.8+)
   ```bash
   # Required Python libraries
   - rdflib>=6.0.0
   - owlrl>=6.0.0
   - pandas>=1.3.0
   - SPARQLWrapper>=2.0.0
   - requests>=2.26.0
   ```

### Installation

#### 1. Clone the Repository
```bash
git clone https://github.com/dschinzo/knowledge_graph_legal_entities.git
cd knowledge_graph_legal_entities
```

#### 2. Install Python Dependencies
```bash
# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

#### 3. Setup Protégé
```bash
# Download and extract Protégé
# Open ontology files from ontology/teleontology/ directory
# Load the main ontology file: legal_entities_ontology.owl
```

#### 4. Setup Karma
```bash
# Download and extract Karma
# Import Karma models from karma/models/
# Configure Karma to use the ontology from Protégé
```

#### 5. Setup GraphDB
```bash
# Install GraphDB
# Create a new repository: legal-entities-kg
# Configure repository settings from graphdb/configurations/
# Import the ontology as a base schema
```

### Configuration

#### GraphDB Repository Configuration
```bash
# Copy the GraphDB configuration
cp graphdb/configurations/legal-entities-repo-config.ttl /path/to/graphdb/configs/

# Or create repository via GraphDB Workbench:
# - Repository ID: legal-entities-kg
# - Ruleset: OWL-Horst (Optimized)
# - Enable context index
# - Enable predicate list
```

#### Karma Configuration
```bash
# Set up Karma workspace
cd karma/
# Import models from karma/models/
# Load ontology from ontology/teleontology/legal_entities_ontology.owl
```

### Usage

#### 1. Ontology Development (Protégé)
```bash
# Open Protégé
# File -> Open -> ontology/teleontology/legal_entities_ontology.owl
# Edit classes, properties, and axioms
# Run reasoner to check consistency
# Save changes
```

#### 2. Data Mapping (Karma)
```bash
# Start Karma
./karma-web.sh  # On Windows: karma-web.bat

# Import source data from data/raw/
# Apply existing models from karma/models/
# Review and refine mappings
# Export RDF to data/mapped/
```

#### 3. Data Loading (GraphDB)
```bash
# Via GraphDB Workbench
# Import -> RDF -> Upload RDF files from data/mapped/

# Or via script
python scripts/data-loading/load_to_graphdb.py
```

#### 4. Run Data Collection Scripts
```bash
# Collect legal entity data
python scripts/data-collection/collect_legal_entities.py

# Collect stock exchange data
python scripts/data-collection/collect_stock_exchange.py
```

#### 5. Process and Clean Data
```bash
# Clean and validate data
python scripts/data-cleaning/clean_data.py

# Validate against business rules
python scripts/data-cleaning/validate_data.py
```

#### 6. Query Knowledge Graph
```bash
# Execute competency questions
python scripts/queries/run_competency_questions.py

# Or use GraphDB SPARQL endpoint
# Navigate to: http://localhost:7200/sparql
# Select repository: legal-entities-kg
# Load queries from queries/competency-questions/
```

### Workflow Overview

```
┌─────────────┐
│   Protégé   │ ──> Ontology Development
└──────┬──────┘
       │
       ↓ (Export OWL)
┌─────────────┐
│    Karma    │ ──> Data Mapping & Transformation
└──────┬──────┘
       │
       ↓ (Export RDF)
┌─────────────┐
│   GraphDB   │ ──> Storage, Querying & Reasoning
└─────────────┘
```

## Data Sources

- State Registration of Legal Entities of Mongolia (open data)
- Mongolian Stock Exchange listings
- Additional public corporate registries

## Project Tools & Technologies

| Tool | Purpose | Version | Documentation |
|------|---------|---------|---------------|
| **Protégé** | Ontology editing | 5.5.0+ | `docs/tools/protege-guide.md` |
| **Karma** | Data integration | 2.0+ | `docs/tools/karma-guide.md` |
| **GraphDB** | RDF storage | Free/Enterprise | `docs/tools/graphdb-guide.md` |
| **Python** | Data processing | 3.8+ | `docs/tools/python-scripts.md` |

## Competency Questions

Example competency questions the knowledge graph can answer:

1. Who are all the shareholders of company X?
2. Which individuals serve as officials in multiple companies?
3. What is the ultimate beneficial ownership chain for company Y?
4. Which companies have foreign shareholders?
5. What companies are listed on the stock exchange and their ownership structure?

See `queries/competency-questions/` for complete SPARQL queries.

## Contributing

Contributions are welcome! Please read the contributing guidelines before submitting pull requests.

### Development Workflow

1. Fork the repository
2. Create a feature branch
3. Make changes to ontology (Protégé) or mappings (Karma)
4. Test changes in GraphDB
5. Submit pull request with documentation

## License

This project is licensed under [LICENSE NAME] - see the LICENSE file for details.

## Contact

**Project Maintainer**: dschinzo  
**Repository**: https://github.com/dschinzo/knowledge_graph_legal_entities  
**Issues**: https://github.com/dschinzo/knowledge_graph_legal_entities/issues

## Acknowledgments

This project follows the iTelos methodology for Knowledge Graph Engineering, emphasizing reusability, documentation, and systematic development processes.

Special thanks to:
- Stanford University for Protégé
- USC Information Sciences Institute for Karma
- Ontotext for GraphDB

## Troubleshooting

### Common Issues

**Protégé won't open ontology**
- Ensure OWL file is valid XML
- Check for circular dependencies
- Verify namespace declarations

**Karma mapping errors**
- Validate source data format
- Check ontology is properly loaded
- Verify property domains and ranges

**GraphDB import failures**
- Check RDF syntax validity
- Ensure sufficient heap memory
- Verify repository configuration

See `docs/troubleshooting.md` for detailed solutions.

---

**Last Updated**: [Date]  
**Version**: 1.0.0
