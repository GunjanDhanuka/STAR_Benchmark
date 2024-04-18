## STAR: A Benchmark for Situated Reasoning in Real-World Videos
The STAR Challenge this year is begining: [STAR Challenge](https://eval.ai/web/challenges/challenge-page/1325/leaderboard/3328/Mean)

<div align="center">
<img src="img/NeurIPS2021_star_teaser.png" width="600" >
</div>

[[STAR Homepage](https://bobbywu.com/STAR)]
Reasoning in the real world is not divorced from situations. A key challenge is to capture the present knowledge from surrounding situations and reason accordingly. STAR is a novel benchmark for Situated Reasoning, which provides challenging question-answering tasks, symbolic situation descriptions and logic-grounded diagnosis via real-world video situations.

## Overview
>
[STAR: A Benchmark for Situated Reasoning in Real-World Videos](https://bobbywu.com/STAR) [[Paper PDF](https://openreview.net/pdf?id=EfgNF5-ZAjM)]  
Bo Wu, Shoubin Yu, Zhenfang Chen, Joshua B Tenenbaum, Chuang Gan, *NeurIPS*, 2021.
>
* 4 Qutestion Types
* 60k Situated Questions
* 23k Situation Video Clips
* 140k Situation Hypergraphs

## Online Evaluation

You are welcome to use [STAR Challenge Leaderboard](https://eval.ai/web/challenges/challenge-page/1325/overview) for the online evaluation on the test dataset.

## STAR Visulazation

We prodive `code/QA_Visualization.ipynb` to visualize Question / Options / Video / Situation Graphs of the STAR data by using [QA Visualization Script](https://github.com/csbobby/STAR_Benchmark).
 * before visualization, please download the Supporting Data (include video keyframes from Action Genome and original videos from Charades) and place them in the mentioned directories in the scripts.

## STAR Data Outline

### Question, Multiple Choice Answers and Situation Graphs  
 * Questions and Answers (.json) : [Train](https://star-benchmark.s3.us-east.cloud-object-storage.appdomain.cloud/Question_Answer_SituationGraph/STAR_train.json) [Val](https://star-benchmark.s3.us-east.cloud-object-storage.appdomain.cloud/Question_Answer_SituationGraph/STAR_val.json) [Test](https://star-benchmark.s3.us-east.cloud-object-storage.appdomain.cloud/Question_Answer_SituationGraph/STAR_test.json)
 * [Train/Val/Test Split File (.json)](https://star-benchmark.s3.us-east.cloud-object-storage.appdomain.cloud/Question_Answer_SituationGraph/split_file.json)

### Question-Answer Templates and Programs  
 * [Question Templates (.csv)](https://star-benchmark.s3.us-east.cloud-object-storage.appdomain.cloud/Templates_Programs/QA_templates.csv)
 * [QA Programs (.csv)](https://star-benchmark.s3.us-east.cloud-object-storage.appdomain.cloud/Templates_Programs/QA_programs.csv)

### Situation Video Data  
 * [Video Segments (.csv)](https://star-benchmark.s3.us-east.cloud-object-storage.appdomain.cloud/Situation_Video_Data/Video_Segments.csv)
 * [Video Keyframe IDs (.csv)](https://star-benchmark.s3.us-east.cloud-object-storage.appdomain.cloud/Situation_Video_Data/Video_Keyframe_IDs.csv)
 * [Frame Dumping Tool from Action Genome](https://github.com/JingweiJ/ActionGenome)

### Annotations  
 * [Classes Files (.zip)](https://star-benchmark.s3.us-east.cloud-object-storage.appdomain.cloud/Annotations/classes.zip) 
 * [Human Poses (.zip)](https://star-benchmark.s3.us-east.cloud-object-storage.appdomain.cloud/Annotations/pose.zip)
 * [Object Bounding Boxes (.pkl)](https://star-benchmark.s3.us-east.cloud-object-storage.appdomain.cloud/Annotations/object_bbox_and_relationship.pkl)
 * [Human Bounding Boxes (.pkl)](https://star-benchmark.s3.us-east.cloud-object-storage.appdomain.cloud/Annotations/person_bbox.pkl)

### Supporting Data  
Our bench built upon [Charades Dataset](https://prior.allenai.org/projects/charades) and [Action Genome](https://www.actiongenome.org), please download raw videos from Charades Dataset as follows:
* Video Frames
  * [Raw Videos from Charades Dataset (scaled to 480p)](https://prior.allenai.org/projects/charades)
* Video Features
  * [Visual Features from Charades Dataset](https://prior.allenai.org/projects/charades)

## Data Usage

To download STAR dataset, please refer to the [STAR Homepage](https://bobbywu.com/STAR) or follow the instructions below.

* **Raw Video**

	Download raw videos (scaled to 480p) from [Charades Videos](https://prior.allenai.org/projects/charades). 

* **Frame Dumping Tool** 

	To get keyframes in each video, please follow the instruction in [Action Genome](https://github.com/JingweiJ/ActionGenome). Please note that graph annotations offered by STAR use the same frame index generated by the above dumping tool.

* **Video Clips**

	We offer video start and end time of each QA in [Video Segments](https://star-benchmark.s3.us-east.cloud-object-storage.appdomain.cloud/Situation_Video_Data/Video_Segments.csv), and keyframes index in [Video Keyframe IDs](https://star-benchmark.s3.us-east.cloud-object-storage.appdomain.cloud/Situation_Video_Data/Video_Keyframe_IDs.csv). You can use them to get the same video clips used in STAR. We use ffmpeg to trim raw videos with annotations, run:
	* ` ffmpeg -y -ss start_time -to end_time -i input_path -codec copy output_path`

* **Question, Multiple Choice Answers and Situation Graphs**
	
	You can download STAR Video QA via following links:

	Questions and Answers: [Train](https://star-benchmark.s3.us-east.cloud-object-storage.appdomain.cloud/Question_Answer_SituationGraph/STAR_train.json) | [Val](https://star-benchmark.s3.us-east.cloud-object-storage.appdomain.cloud/Question_Answer_SituationGraph/STAR_val.json) | [Test](https://star-benchmark.s3.us-east.cloud-object-storage.appdomain.cloud/Question_Answer_SituationGraph/STAR_test.json) | [Train/Val/Test Split File](https://star-benchmark.s3.us-east.cloud-object-storage.appdomain.cloud/Question_Answer_SituationGraph/split_file.json)

* **Classes**
	
	The classes of actions, verbs, objects, and relationships are included in [classes files](https://star-benchmark.s3.us-east.cloud-object-storage.appdomain.cloud/Annotations/classes.zip)

* **Human Poses**
	
	We extracted human poses in each keyframe via [AlphaPose](https://github.com/MVIG-SJTU/AlphaPose). You can download [poses](https://star-benchmark.s3.us-east.cloud-object-storage.appdomain.cloud/Annotations/pose.zip) we extracted. Poses are referred by video ID and keyframe ID. 

* **Other**
	
	We offer the question, answer and program templates we designed in [Question Templates](https://star-benchmark.s3.us-east.cloud-object-storage.appdomain.cloud/Templates_Programs/QA_templates.csv) and [QA Programs](https://star-benchmark.s3.us-east.cloud-object-storage.appdomain.cloud/Templates_Programs/QA_programs.csv). 

	You can use those templates, [Object Bounding Boxes](https://star-benchmark.s3.us-east.cloud-object-storage.appdomain.cloud/Annotations/object_bbox_and_relationship.pkl), and [Human Bounding Boxes](https://star-benchmark.s3.us-east.cloud-object-storage.appdomain.cloud/Annotations/person_bbox.pkl) to generate new QAs with Situation Graphs.

## STAR Program Execution

In STAR, we introduce a neuro-symbolic framework Neuro-Symbolic Situated Reasoning (NS-SR) to get answers by executing programs with corresponding situation graphs.
run

 * `python run_program.py --qa_dir your_path`

to utlize STAR program excutor.


## STAR Generation

We also prodive our QA generation code, you can generate new STAR questions from more situation videos: [QA Generation Code](https://github.com/csbobby/STAR_Benchmark)


## Citation

If you use STAR in your research or wish to refer to the results published in the paper, please use the following BibTeX entry.
```BibTeX
@inproceedings{wu2021star_situated_reasoning,
author={Wu, Bo and Yu, Shoubin and Chen, Zhenfang and Tenenbaum, Joshua B and Gan, Chuang},
title = {{STAR}: A Benchmark for Situated Reasoning in Real-World Videos},
booktitle = {Thirty-fifth Conference on Neural Information Processing Systems (NeurIPS)},
year = {2021}
}
```



