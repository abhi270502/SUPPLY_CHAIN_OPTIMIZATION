# Project Overview
```
The system analyzes cargo transportation data using graph analytics to:

Build a comprehensive airport logistics network graph

Calculate network centrality measures (betweenness, degree, eigenvector)

Predict transportation delays using logistic regression

Identify high-risk airports and optimize routing decisions

```

# Download and extract the project files to your local directory
# Create virtual environment
python -m venv .venv

## Activate virtual environment
### On Windows:
.venv\Scripts\activate
### On macOS/Linux:
source .venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Neo4j Database Setup
Neo4j Desktop (Recommended for local development)
Download and install Neo4j Desktop from https://neo4j.com/download/

Create a new database instance

## Install the Graph Data Science (GDS) plugin and apoc plugin
### 🔽 Step 1: Download Plugins

| Plugin | Download URL |
|--------|--------------|
| APOC   | https://github.com/neo4j/apoc/releases |
| GDS    | https://github.com/neo4j/graph-data-science/releases |


### Step 2: Place Jars in plugins/ Folder
### 📂 Plugin Directory Paths

| System            | Path                                                  |
|-------------------|--------------------------------------------------------|
| macOS (Homebrew)  | `/opt/homebrew/Cellar/neo4j/*/libexec/plugins/`       |
| macOS (ZIP)       | `neo4j-x.x.x/plugins/`                                |
| Windows (ZIP)     | `C:\\neo4j\\neo4j-x.x.x\\plugins\\`                    |

### ⚙️ Step 3: Update `neo4j.conf`

**Locate the `neo4j.conf` file based on your system:**

| System                          | Path                                                                 |
|----------------------------------|----------------------------------------------------------------------|
| macOS (Homebrew)                 | `/opt/homebrew/Cellar/neo4j/*/libexec/conf/neo4j.conf`              |
| Manually Extracted ZIP (Mac/Win) | `neo4j-x.x.x/conf/neo4j.conf`                                       |

---

**Add the following lines to enable APOC & GDS (ensure no duplicate entries exist):**

``` properties
# Enable APOC & GDS Plugins
dbms.security.procedures.unrestricted=apoc.*,gds.*
dbms.security.procedures.allowlist=apoc.*,gds.*
```

### 🔄 Step 4: Restart Neo4j

| System              | Command / Action                                  |
|---------------------|---------------------------------------------------|
| macOS (Homebrew)    | `brew services restart neo4j`                     |
| macOS/Windows (ZIP) | `./bin/neo4j restart` or `neo4j.bat restart`      |
| Neo4j Desktop       | Click the **Restart** button in the UI            |

# Create .env file

NEO4J_URI=bolt://localhost:7687

NEO4J_USER=neo4j

NEO4J_PASSWORD=your_password


# Usage
## Data Ingestion
Run the data ingestion notebook to populate the Neo4j database: DataIngestion.ipynb

## Metrics Analysis
Execute the metrics analysis notebook for network analysis: jupyter notebook metrics.ipynb

