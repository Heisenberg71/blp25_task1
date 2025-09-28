# [Hatespeech Identification Shared Task](https://multihate.github.io/) at [BLP Workshop @IJCNLP-AACL 2025](https://blp-workshop.github.io/)


## Task Website

### [Please visit this site to get updated information on this task.](https://multihate.github.io/)

[https://multihate.github.io/](https://multihate.github.io/)

## Objective

The [Bangla Multi-task Hate Speech Identification shared task](https://multihate.github.io/) is designed to address the complex and nuanced problem of detecting and understanding hate speech in Bangla across multiple related subtasks such as type of hate, severity, and target group. In contrast to single-task approaches, this shared task embraces a multi-task learning framework, where models are trained to jointly learn several hate speech detection objectives. This approach is more reflective of real-world scenarios, where identifying hate speech requires understanding not just its presence, but also its type, target, and severity. Please see the
[Task Description](#task-description) below.


__Table of contents:__
- [Important Dates](#important-dates)
- [Recent Updates](#recent-updates)
- [Contents of the Directory](#contents-of-the-directory)
- [Task Description](#task-description)
- [Dataset](#dataset)
- [Scorer and Official Evaluation Metrics](#scorer-and-official-evaluation-metrics)
- [Baselines](#baselines)
- [Format checker](#formatchecker)
- [Submission Guidelines](#submission-guidelines)
- [Organizers](#organizers)

## Important Dates
- **10 July 2025:** Registration on codalab and beginning of the development cycle
- **08 September 2025:** Beginning of the evaluation cycle (test sets release and run submission)
- **15 September 2025:** End of the evaluation cycle
- **17 September 2025:** Publish rank list and share paper submission details
- **29 September 2025:** Paper Submission Deadline (Shared Task System Papers Due)
- **03 November 2025:** Notification of acceptance
- **11 November 2025:** Camera-ready due
- **23-14 December 2025:** Workshop co-located with IJCNLP-AACL 2025 (Mumbai, India)


## Proceedings

### Instructions to Prepare Your Shared Task Paper
The title of paper should be in the following format: **< Team Name > at BLP-2025 Task 1: < Descriptive title of your paper >**

For example, team **AlphaX** would have their title as follows: **AlphaX at BLP-2025 Task 1: Transformer Models for Hate Speech Detection**

- **The shared task papers may consist of up to four (4) pages of content.**

**Templates:** The Shared tasks papers must follow the ACL 2025 two-column format, using the supplied [official templates](https://www.overleaf.com/latex/templates/association-for-computational-linguistics-acl-conference/jvxskxpnznfj). The templates can be downloaded in style files and formatting. Please do not modify these style files, nor should you use templates designed for other conferences. Submissions that do not conform to the required styles, including paper size, margin width, and font size restrictions, will be rejected without review. Verification to guarantee conformance to publication standards, we will be using the [ACL pubcheck tool](https://github.com/acl-org/aclpubcheck). The PDFs of camera-ready papers must be run through this tool prior to their final submission, and we recommend its use also at submission time.

Submissions are open to only for the teams who submitted their systems during the evaluation phase and listed in the leaderboard. The working notes are to be submitted in both anonymously and non-anonymously.

## Recent Updates

## Recent Updates
* __[11/07/2025]__  Release example scripts using DistilBERT model for subtask 1A and subtask 1B
* __[10/07/2025]__  Development phase starts
* __[10/07/2025]__  Training and dev data released


## Contents of the Directory
* Main folder: [data](./data)<br/>
  This directory contains data files for the task.
* Main folder: [baselines](./baselines)<br/>
    Contains scripts provided for baseline models of the task.
* Main folder: [example_scripts](./example_scripts)<br/>
    Contains an example script provided to run DistilBERT model for subtask 1A and subtask 1B.
* Main folder: [format_checker](./format_checker)<br/>
    Contains scripts provided to check the format of the submission file.
* Main folder: [scorer](./scorer)<br/>
    Contains scripts provided to score the output of the model when provided with the label (i.e., dev).

* [README.md](./README.md) <br/>
    This file!

## Task Description

This shared task is designed to identify the type of hate, its severity, and the targeted group from social media content. The goal is to develop robust systems that advance research in this area. In this shared task, we will have three subtasks:

- **Subtask 1A**: Given a Bangla text collected from YouTube comments, categorize whether it contains _Abusive_, _Sexism_, _Religious Hate_, _Political Hate_, _Profane_, or _None_.
- **Subtask 1B**: Given a Bangla text collected from YouTube comments, categorize whether the hate towards _Individuals_, _Organizations_, _Communities_, or _Society_.
- **Subtask 1C**: This subtask is a multi-task setup. Given a Bangla text collected from YouTube comments, categorize it into type of hate, severity, and targeted group.

## Dataset
For a brief overview of the dataset, kindly refer to the *README.md* file located in the data directory.


### Input data format

#### Subtask 1A
Each file uses the tsv format. A row within the tsv adheres to the following structure:

```
id	text	label
```
Where:
* id: an index or id of the text
* text: text
* label: _Abusive_, _Sexism_, _Religious Hate_, _Political Hate_, _Profane_, or _None_.

##### Example
```
490273	আওয়ামী লীগের সন্ত্রাসী কবে দরবেন এই সাহস আপনাদের নাই	Political Hate
```

#### Subtask 1B
Each file uses the tsv format. A row within the tsv adheres to the following structure:

```
id	text	label
```
Where:
* id: an index or id of the text
* text: text
* label: _Individuals_, _Organizations_, _Communities_, or _Society_.

##### Example
```
490273	আওয়ামী লীগের সন্ত্রাসী কবে দরবেন এই সাহস আপনাদের নাই	Organization
```

#### Subtask 1C
Each file uses the tsv format. A row within the tsv adheres to the following structure:

```
id	text	hate_type   hate_severity   to_whom
```
Where:
* id: an index or id of the text
* text: text
* hate_type: _Abusive_, _Sexism_, _Religious Hate_, _Political Hate_, _Profane_, or _None_.
* hate_severity: _Little to None_, _Mild_, or _Severe_.
* to_whom: _Individuals_, _Organizations_, _Communities_, or _Society_.

##### Example
```
490273	আওয়ামী লীগের সন্ত্রাসী কবে দরবেন এই সাহস আপনাদের নাই	"Political Hate"  "Little to None"  Organization
```

## Example Fine-tuning Script

We are pleased to release a set of example scripts to support participants in the Hate Speech Detection Shared Task. These scripts are designed to help you get started with data loading, preprocessing, and baseline model development for the three subtasks: subtask 1A, subtask 1B, and subtask 1C. We encourage you to use and adapt these examples to build and improve your own systems.
The scripts are available in the shared task repository: [example_scripts](./example_scripts)


## Scorer and Official Evaluation Metrics

### Scorers
The scorer for the task is located in the [scorer](./scorer) module of the project. The scorer will report official evaluation metrics and other metrics of a prediction file. The scorer invokes the format checker for the task to verify the output is properly shaped. It also handles checking if the provided predictions file contains all tweets from the gold one.


You can install all prerequisites through,
```
pip install -r requirements.txt
```
Launch the scorer for the task as follows:
```
python scorer/task.py --gold-file-path=<path_gold_file> --pred-file-path=<predictions_file>
```


##### Example

```
python scorer/task.py --pred_files_path task_dev_output.txt --gold_file_path data/dev.tsv
```

### Official Evaluation Metrics
The **official evaluation metric** for the subtask 1A and 1B is **micro-F1** and **weighted micro-F1** for subtask 1C. However, the scorer also reports accuracy, precision and recall.


## Baselines

The [baselines](baselines) module currently contains a majority, random and a simple n-gram baseline.


#### Subtask 1A

Baseline Results for the task on Test set (Evaluation Phase)

| Model                      | micro-F1 |
|----------------------------|----------|
| Random Baseline            | 0.1638   |
| Majority Baseline          | 0.5638   |
| n-gram Baseline            | 0.6020   |


Baseline Results for the task on Dev-Test set

| Model                      | micro-F1 |
|----------------------------|----------|
| Random Baseline            | 0.1465   |
| Majority Baseline          | 0.5760   |
| n-gram Baseline            | 0.6075   |


#### Subtask 1B
Baseline Results for the task on Test set (Evaluation Phase)

| Model                      | micro-F1 |
|----------------------------|----------|
| Random Baseline            | 0.2043   |
| Majority Baseline          | 0.5974   |
| n-gram Baseline            | 0.6209   |


Baseline Results for the task on Dev-Test set

| Model                      | micro-F1 |
|----------------------------|----------|
| Random Baseline            | 0.2118   |
| Majority Baseline          | 0.6083   |
| n-gram Baseline            | 0.6279   |


#### Subtask 1C
Baseline Results for the task on Test set (Evaluation Phase)

| Model                      | weighted micro-F1 |
|----------------------------|-------------------|
| Random Baseline            | 0.2304            |
| Majority Baseline          | 0.6072            |
| n-gram Baseline            | 0.6305            |



Baseline Results for the task on Dev-Test set

| Model                      | weighted micro-F1 |
|----------------------------|-------------------|
| Random Baseline            | 0.2300            |
| Majority Baseline          | 0.6222            |
| n-gram Baseline            | 0.6401            |

## Format checker

The format checkers for the task are located in the [format_checker](format_checker) module of the project. The format checker verifies that your generated results file complies with the expected format.

Before running the format checker please install all prerequisites,
```
pip install -r requirements.txt
```

To launch it, please run the following command:

```
python format_checker/task.py -p results_files
```

##### Example
```
python format_checker/task.py -p ./subtask_1A.tsv
```
**results_files**: can be one path or space-separated list of paths


<!-- **Note that the checker cannot verify whether the prediction file you submit contains all lines, because it does not have access to the corresponding gold file.** -->


## Submission

### Guidelines
Evaluation consists of two phases:

1. **Development phase:** This phase involves working on the *dev-test set*.
2. **Evaluation phase:** This phase involves working on the *test set*, which will be released during the ***evaluation cycle***.

For each phase, please adhere to the following guidelines:

- We request each team to establish and manage a single account for all submissions. Hence, all runs should be submitted through the same account. Any submissions made from multiple accounts by the same team may lead to your system being not ranked from the final ranking in the overview paper.
- The most recently uploaded file on the leaderboard will serve as your final submission.
- Adhere strictly to the naming convention for the output file, which must be labeled as 'task.tsv'. Deviation from this standard could trigger an error on the leaderboard.
- Submission protocol requires you to compress the '.tsv' file into a '.zip' file (for instance, zip task.zip task.tsv) and submit it through the Codalab page.
- With each submission, ensure to include your team name along with a brief explanation of your methodology.
- Each team is allowed a maximum of 100 submissions per day for the given task. Please adhere to this limit.

### Submission Format

#### Subtask 1A and 1B
Submission file format is tsv (tab seperated values). A row within the tsv adheres to the following structure:

```
id	label   model
```
Where:
* id: a id of the text
* label: __[_Abusive_, _Sexism_, _Religious Hate_, _Political Hate_, _Profane_, or _None_]__ or __[_Individuals_, _Organizations_, _Communities_, or _Society_.]__
* model: model name

#### Subtask 1C
Submission file format is tsv (tab seperated values). A row within the tsv adheres to the following structure:

```
id	hate_type   hate_severity   to_whom   model
```
Where:
* id: a id of the text
* hate_type: _Abusive_, _Sexism_, _Religious Hate_, _Political Hate_, _Profane_, or _None_.
* hate_severity: _Little to None_, _Mild_, or _Severe_.
* to_whom: _Individuals_, _Organizations_, _Communities_, or _Society_.
* model: model name


### Submission Site

#### Subtask 1A
**[https://www.codabench.org/competitions/9559/](https://www.codabench.org/competitions/9559/)**

#### Subtask 1B
**[https://www.codabench.org/competitions/9560/](https://www.codabench.org/competitions/9560/)**

#### Subtask 1C
**[https://www.codabench.org/competitions/9561/](https://www.codabench.org/competitions/9561/)**

## Citation
There are various papers associated with the task. Details for the papers specific to the task as well as an overall overview will be posted here as they come out. Bib entries for each paper are included here.
```
will update soon


@inproceedings{blp2025-overview-task1,
    title = "Overview of BLP 2025 Task 1: Bangla Hate Speech Identification",
    author = "Hasan, Md Arid and Alam, Firoj and Hossain, Md Fahad and Naseem, Usman and Ahmed, Syed Ishtiaque",
    booktitle = "Proceedings of the Second International Workshop on Bangla Language Processing (BLP-2025)",
    month = dec,
    year = "2025",
    address = "India",
    publisher = "Association for Computational Linguistics",
}

```


## Leaderboard

### Subtask 1A
|Rank| username         |F1-Macro|
|----|------------------|--------|
|1   | shifat_islam     |0.7362  |
|2   | SyntaxMind       |0.7345  |
|3   | zannatul_007     |0.734   |
|4   | mahim_ju         |0.7331  |
|5   | reyazul          |0.7328  |
|6   | mohaiminulhoque  |0.7323  |
|7   | nahidhasan       |0.7305  |
|8   | adib709          |0.7282  |
|9   | sahasourav17     |0.7275  |
|10  | ashraf_989       |0.7273  |
|11  | CUET-NLP_Zenith  |0.7263  |
|12  | nsu_milab        |0.725   |
|13  | abid_al_hossain  |0.7238  |
|14  | Penta Global Ltd |0.7178  |
|15  | mohaymen         |0.7133  |
|16  | ttprama          |0.7111  |
|17  | minjacodes9      |0.7075  |
|18  | samin007         |0.707   |
|19  | pritampal98      |0.7057  |
|20  | bahash_ai        |0.7028  |
|21  | programophile    |0.7013  |
|22  | fatin_anif       |0.6954  |
|23  | heytamjid        |0.6941  |
|24  | adriti12         |0.6921  |
|25  | im_tushu_221     |0.6901  |
|26  | sadman03samir    |0.6871  |
|27  | cuet_sntx_srfrs  |0.6867  |
|28  | abir_bot69       |0.684   |
|29  | antara_n_15      |0.6815  |
|30  | UB               |0.6761  |
|31  | quasar           |0.6733  |
|32  | shahriar_9472    |0.6689  |
|33  | intfloat         |0.6634  |
|34  | naim-parvez      |0.6587  |
|35  | Organizers       |0.5638  |
|36  | teddymas         |0.4589  |
|37  | mizba            |0.1077  |

### Subtask 1B

|Rank| username         |F1-Macro|
|----|------------------|--------|
|1   | mahim_ju         |0.7356  |
|2   | shifat_islam     |0.7335  |
|3   | mohaiminulhoque  |0.7328  |
|4   | reyazul          |0.7317  |
|5   | SyntaxMind       |0.7317  |
|6   | zannatul_007     |0.7315  |
|7   | abid_al_hossain  |0.7286  |
|8   | nahidhasan       |0.7279  |
|9   | adib709          |0.7275  |
|10  | sahasourav17     |0.7269  |
|11  | Penta Global Ltd |0.7256  |
|12  | mohaymen         |0.7254  |
|13  | CUET-NLP_Zenith  |0.7213  |
|14  | adriti12         |0.7125  |
|15  | ashraf_989       |0.7114  |
|16  | ttprama          |0.7095  |
|17  | nsu_milab        |0.6981  |
|18  | heytamjid        |0.6979  |
|19  | pritampal98      |0.6974  |
|20  | bahash_ai        |0.6954  |
|21  | cuet_sntx_srfrs  |0.6817  |
|22  | sadman03samir    |0.676   |
|23  | Organizers       |0.5974  |
|24  | lamiaa           |0.2848  |


### Subtask 1C
| Rank | username         |F1-Macro|
|------|------------------|--------|
| 1    | mahim_ju         |0.7392  |
| 2    | CUET-NLP_Zenith  |0.7378  |
| 3    | shifat_islam     |0.7361  |
| 4    | reyazul          |0.7332  |
| 5    | adib709          |0.7312  |
| 6    | mohaiminulhoque  |0.731   |
| 7    | sahasourav17     |0.7262  |
| 8    | abid_al_hossain  |0.725   |
| 9    | nur_163          |0.7241  |
| 10   | nahidhasan       |0.724   |
| 11   | ttprama          |0.7233  |
| 12   | zannatul_007     |0.7181  |
| 13   | Penta Global Ltd |0.7159  |
| 14   | pritampal98      |0.7153  |
| 15   | abir_bot69       |0.7129  |
| 16   | sadman03samir    |0.7129  |
| 17   | bahash_ai        |0.6969  |
| 18   | cuet_sntx_srfrs  |0.6842  |
| 19   | aacontest        |0.673   |
| 20   | Organizers       |0.6072  |
| 21   | adriti12         |0.3898  |


## Communication
Please join us in Slack channel for discussion and doubts:
 - [Slack](https://join.slack.com/t/blpworkshop/shared_invite/zt-1ryu9eyac-7fevK9A4_Bt~qN_eCK349g)

## Organizers
- [Md Arid Hasan](https:aridhasan.github.io), PhD Student, The University of Toronto
- [Firoj Alam](https://firojalam.one/), Senior Scientist, Qatar Computing Research Institute
- Md Fahad Hossain, Lecturer, Daffodil International University
- [Usman Naseem](https://usmaann.github.io/), Assistant Professor, Macquarie University
- [Syed Ishtiaque Ahmed](https://www.ishtiaque.net/), Associate Professor, The University of Toronto
