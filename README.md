# Fetch, clean, transform and save NCBI PubMed data and OpenAlex data for use in Dashboard app

This repository contains Jupyter Notebooks to fetch and prepare data for use by an interactive dashboard available at https://github.com/dgolowicz/bibliometrics_NMR.

The notebooks have rich markdown information and should be self-explanatory. Below is a short information on the workflow. 

## WORKFLOW

### 1_collect_data_pubmed_openalex.ipynb

- Fetches data from PubMed and OpenAlex and combine them into a single pandas dataframe

Note: The script starts with fetching all PMIDS that match a query using Entrez Direct: E-utilities on the Unix Command Line (https://www.ncbi.nlm.nih.gov/books/NBK179288/).
Entrez Direct is available for Linux and Mac operating systems, but you can also get PMIDS of interest another way. Another possibility is to use Bio.Entrez, which is required by the next step anyway. The drawback of using Bio.Entrez is that it can retrieve a maximum of 10000 entries at once, so you will have to fetch them in batches using the *retstart* parameter.
You are also advised to enter NCBI API KEY into the designated cells. Key is available for free from https://account.ncbi.nlm.nih.gov/settings/
By doing so, you can reduce the delay for your requests from 0.5 to 0.1 in the following line: pubmed_data = fetch_pmid_records(pmids, delay=0.5)

### 2_preprocessing.ipynb

- Clean and transform data in pandas

### 3_prepare_sqlite_db.ipynb

- Save preprocessed data from Script 2 to SQLite database - ready to use by Dashboard app from https://github.com/dgolowicz/bibliometrics_NMR
