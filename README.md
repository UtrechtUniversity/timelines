# Timeline

This page contains the source code created for the DG.O 2024 paper "Reconstructing the decision-making processes of a city council based on references between documents".

This work is licensed under a Creative Commons Attribution International 4.0 License.

\
\
Disclaimer: The code was shared for the purpose of transparency, but it was not rewritten for easy re-usability. The code is fairly messy

We do not provide the XML iBabs dump we used, although everything is based on the open data available through https://zoek.openraadsinformatie.nl.


# What is this, and why?

Generating the decision history of council information history as a timeline, to be used to present search results within a temporal context.

Two main approaches to create the timeline
* Identifying the re-use of (near) duplicate documents during multiple council meetings
* Identifying references to (older) documents in the collection

The first approach is based on comparing the document id's, filenames, displaynames and filesizes

The second approach has three sub-approaches where we investigate references of decreasing specificity
1) References by URL (with document/agenda IDs in URL)
2) References by document title
3) References by date (where documents are frequently uploaded on the same date)

Implementation is based on the public council information of the municipality of utrecht


# How it works

The main components are (in order of use):

* "Download dataset from metadata dump.ipynb" - download the pdf's based on the XML data dump
* "Parse data.ipynb" - read meta-data into json, duplicate detection, co-citation approach
* "Create testset" - contains manual annotations for testing reference extraction
* "Approach 2.ipynb" - extracting references by title/date/url, grouping timelines with references to other timelines
* "evaluate approaches.ipynb" - evaluate reference extraction, compare manual and generated timelines

Also included is the full set of manually constructed decision histories