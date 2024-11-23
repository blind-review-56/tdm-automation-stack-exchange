# Replication Package for Automating Technical Debt Management: Insights from Practitioner Discussions in Stack Exchange

## Description of this study:

Managing technical debt (TD) is essential for maintaining long-term software projects. Nonetheless, the time and cost involved in technical debt management (TDM) are often high, which may lead practitioners to omit TDM tasks. The adoption of tools, and particularly the usage of automated solutions, can potentially reduce the time, cost, and effort involved. However, the adoption of tools remains low, indicating the need for further research on TDM automation. To address this problem, this study aims at understanding which TDM activities practitioners are discussing with respect to automation in TDM, what tools they report for automating TDM, and the challenges they face that require automation solutions. To this end, we conducted a mining software repositories (MSR) study on three websites of Stack Exchange (Stack Overflow, Project Management, and Software Engineering) and collected 216 discussions, which were analyzed using both thematic synthesis and descriptive statistics. We found that identification and measurement are the most cited activities. Furthermore, 51 tools were reported as potential alternatives for TDM automation. Finally, a set of nine main challenges were identified and clustered into two main categories: challenges driving TDM automation and challenges related to tool usage. These findings highlight that tools for automating TDM are being discussed and used; however, several significant barriers persist, such as tool errors and poor explainability, hindering the adoption of these tools. Moreover, further research is needed to investigate the automation of other TDM activities such as TD prioritization.

## Structure of the replication package:

The replication package includes the datasets (for selected studies and automation artifacts), the scripts for data analysis, and all the figures used in the manuscript.

```
├── data
│   ├── discussions
│   │   ├── raw
│   │   │   ├── Tech_Debt Q's (discussions filtered with "tech debt" keyword)
│   │   │   └── Technical_Debt Q's (discussions filtered with "technical debt" keyword)
│   │   └── selected
│   │       └── 216 discussions selected after manual filtering
│   ├─  quotations.doc
│   ├── selected_activities.csv
│   ├── selected_discussions.csv
│   ├── selected_tools.csv
│   └──    stackexchange_archive.torrent
├── scripts
│   ├── extraction.py 
|   ├── helper.py
|   ├── link-discussions.py
│   ├── main.py
|   ├── pm_extraction
|   ├── se_extraction.py
|   └── so_extraction.py
├── figures
│   ├── challenges.pdf
│   ├── discussions-per-website.pdf
│   ├── discussions-per-year.pdf
│   └── research-method.pdf
├── README.md
└── env.yaml

```

## Running the data analysis

### Pre-requisites
To be able to run the scripts, you will need to have [Conda](https://docs.conda.io/projects/conda/en/stable/user-guide/install/index.html) installed.
### Extraction
#### Download the data dump
Download the following 7z files from the Stack Exchange [Data Dump](https://archive.org/details/stackexchange):
* `stackoverflow.com-Posts.7z`
* `stackoverflow.com-PostHistory.7z`
* `stackoverflow.com-Comments.7z`
* `pm.stackexchange.com.7z`
* `softwareengineering.stackexchange.com.7z`

Once downloaded, the `stackoverflow` files have to be placed into the `soData/` directory, the `pm` file into the `pmData/` directory and the `softwareengineering` file into the `seData/` directory.
**_(These should not be decompressed as the program is already set to do so)_**.

#### Technical Debt Question Extraction
1. In the terminal, change to the `scripts/` directory.
2. Create the conda environment. 

```
conda env create -f env.yaml
``` 

3. Activate the conda environment.

```
conda activate se-extraction
```

4. Run the script `main.py`
```
 python main.py
```
5. Once extraction is completed, delete the conda environment.
```
conda deactivate
conda env remove -n se-extraction
```

_Note: There is a p7zip dependency in the yaml file. The name of this dependency may differ in accordance with the OS being used_.