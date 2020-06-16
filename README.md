# Operationally Transparent Cyber (OpTC) Data Release


## Disclaimer

DARPA is releasing these files in the public domain to stimulate further research. Their release implies no obligation or desire to support additional work in this space. The data is released as-is. DARPA makes no warranties as to the correctness, accuracy, or usefulness of the released data. In fact, since the data was produced by research prototypes, it is practically guaranteed to be imperfect. Nonetheless, as this data represents a very large repository of semantically rich and structured data, DARPA believes that it is in the best interests of the Department of Defense and the research community to make them freely available.

## OpTC Overview

Operationally Transparent Cyber (OpTC) was a technology transition pilot study funded under Boston Fusion Corp.'s Cyber APT Scenarios for Enterprise Systems (CASES) project. Its primary objective was to determine if DARPA Transparent Computing (TC) program technologies could scale without loss of detection performance to address cyber defense capability gaps identified in USTRANSCOM's Joint Deployment Distribution Enterprise (JDDE) solicitation for the government fiscal years 2019-2023. Boston Fusion along with two performers from the TC program (Five Directions providing endpoint telemetry (TA1) and BAE providing analysis over the data (TA2)) worked to scale their systems from two machines to one thousand machines. The OpTC team conducted scaling and detection tests in the fall of 2019. A third performer (Provatek), not originally associated with the TC program, acted as a red team and test coordinator. This data set represents a subset of that activity.

The OpTC system architecture is based on one used in TC program evaluations. Kafka, an open-source stream-processing server, is used to pass information among system components. Each Windows 10 endpoint is equipped with an endpoint sensor that monitors host events, packs them into JSON records, and sends them to Kafka. As these records flow into Kafka, a translation server aggregates them into new data records in a format called eCAR that are then pushed back to Kafka. As the translation server pushes eCAR records to Kafka, a data analytics component integrates them into a graph data structure for analysis and visualization.

OpTC took TC system components that worked well on two hosts in TC program tests and scaled them up to work with one-thousand hosts. This scaled up system was evaluated over two weeks in a highly instrumented environment, and the data in this collection contains approximately a terabyte of data in compressed JSON compatible format from that evaluation. The evaluation started with a period of benign record generation, followed by the injection of malware by a red team. Benign traffic ran continuously during red team activity. Due to constraints in collection data space during the evaluation, data from five hundred hosts was collected rather than from the full set of one-thousand hosts.

## Data Collection

Data collection was funded by the DARPA Cyber Hunting at Scale (CHASE) program. Five Directions collected and post processed the data to enrich the dataset.

## File Manifest and Descriptions

* Ground Truth: The file **OpTCRedTeamGroundTruth.pdf** contains the ground truth constructed by the red team to help guide the evaluation. The evaluation took place on an isolated network environment, and so all the IP addresses and domain names referenced in the data are fictional and bear no relationship to routable and valid addresses and hostnames, respectively.

* eCAR:The file **ecar.md** explains the history and syntax of eCAR.

* Errata:The file **errata.md** describes issues with the data.

* Data: Due to the size of the data set it is hosted on Google Drive at https://drive.google.com/drive/u/0/folders/1n3kkS3KR31KUegn42yk3-e6JkZvf0Caa rather than here. The data set contains three folders: **ecar-bro**, **ecar**, and **bro**.

  * ecar-bro: Contains the eCAR FLOW-START events annotated with the bro-id of the flow enabling one to pivot between endpoint and network data. There are three sub-folders: short, evaluation, and benign. The short folder contains events with missing data. The evaluation folder contains data from the evaluation period of the exercise, and the benign folder contains data from the benign collection period of the exercise.

  * ecar: Contains the endpoint data from the exercise in three folders similar to ecar-bro, above.

  * bro: Contains the data from the bro sensor by date.



Distribution A: Approved for public release: distribution unlimited
