Hello!!

This text document contains all the details regarding the files that are present in this directory. 

As per each steps, I'll explain the parts of my project. 

Step 0: Setup
With respect to step 0, I created a VM instance in GCP and the details regarding the ip, port and core is present in the amuthusu_p1.json file outside the src directory.

Step 1: Scraping Wiki pages
For scraping the Wiki pages, I have used the API endpoint and Wrapper as given in the handout. The ipynb file titled "scrapper.ipynb" contains the code for scraping the wikipedia data based on the topics and subtopics. I have taken 550 documents for each topic which brings the total data documents collected to 5500 documents. The ipynb file saves all the collected data as CSV files within the "Data" Folder of the main directory. 

Step 2: Indexing

Preprocessing: For this process, I have coded the "preprocess.ipynb" file in the directory. It does Tokenization, Stemming, lemmatization and Stop word removal for all the CSV documents present in the Data Folder and I have combined the preprocessed data into a single CSV with 5500 documents titled "preprocessed_text.csv" that was used for indexing in Solr. The "preprocess.ipynb" is also coded to verify the grading criteria given in the handout for my own personal verification. 

Indexing: The "IRF23P1" core is created manually through the VM instance running Ubuntu using the commands from "https://tecadmin.net/install-apache-solr-on-ubuntu/" as given in the handout. The Schema of the core is as follows

<field name="revision_id" type="string" indexed="true" stored="true"/>
<field name="Title" type="string" indexed="true" stored="true"/>
<field name="summary" type="text_en" indexed="true" stored="true"/>
<field name="url" type="string" indexed="true" stored="true"/>
<field name="topic" type="string" indexed="true" stored="true"/>

The schema was manually fed onto the core's xml schema. Then, based on each schema field, the "preprocessed_text.csv" containg the preprocessed text from Topic, Title, Summary, URL and Revision ID as requested in the handout were indexed onto Solr with their appropriate fields. The indexing code can be found at "indexer.ipynb" file.

Submission Criteria:

As per the submission criteria, I have created a .json file containing the IP address of my GCP instance, port in which Solr is running and the core name. The file is named amuthusu_p1.json outside the src as requested with the following details
{
    "ip": "35.245.110.213",
    "port": "8983",
    "core": "IRF23P1",
    "ubit": "amuthusu"
}

I verified the above based on its validity in the given (Tool to check validity: https://jsonlint.com/ ) as per the handout. 

I guess, the .json file and the directory under src would suffice the submission guidelines.
1. amuthusu_p1.json
2. src
	a. scrapper.ipynb, preprocess.ipynb, indexer.ipynb and Data
	b. preprocessed_text.csv

Please do let me know, if you have any questions, require further clarification, or believe that any aspect of my submission is lacking or unclear.

Thank you.
Anirudh Muthusundaram


