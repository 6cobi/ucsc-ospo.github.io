---
title: "Kolmogorov-Arnold-based Transformer for LLMs: Implementation, Evaluation and Benchmarking "
authors: [saisumanv, zahmeeth]
author_notes: ["PhD Candidate, University of Nebraska-Lincoln","Assistant Professor, West Virginia University"]
tags: ["osre25", "reproducibility", "KALLM", "Transformers", "Kolmogorov-Arnold Networks", "smollm2"]
date: 2025-02-09T10:15:56-07:00
lastmod: 2025-02-09T10:15:56-07:00
---

###  Project Objectives
<!--- KALLM introduction --->
<!--- importance --->
[KALLM](https://github.com/saisumanv/KALLM) project proposes a new Kolmogorov-Arnold Network (KAN)-based Transformer implementation of an open-source LLM called SmolLM2. Transformers have found increasing success in many open-source LLMs across language reasoning tasks like text generation, summarization and some tasks imitating advanced critical thinking. However, Kolmogorov-Arnold Networks (KANs) are an attractive alternative to the Multi-Layer Perceptrons (MLPs) which are used in these Transformer architectures by default. KAN-based Transformers (KATs) offer several advantages over MLPs. (i) They follow the universal approximation property and hence can theoretically approximate any function i.e. they can learn from any complex input patterns. (ii) They are more interpretable as they decompose the entire input into multiple manageable components with each layer processing one component. This is unlike MLPs, where each layer processes the input sequences holistically. (iii) KANs can lead to faster convergence on certain reasoning tasks due to their ability to break down the input sequences into simple univariate functions. 

However, currently there exist little to no open-source implementations of KAN-based Transformers in open-source LLMs. Until recently, an efficient implementation of KAN was not available; the same can be said for KAN-based Transformer implementations. With the recent efficient implementations of open-source KAN-based Transformers (KATs), integrating them into open-source LLM engines becomes a possibility.  This project will implement KAT as the core architecture of the Transformer in SmolLM2, an open-source LLM and perform evaluation and benchmarking against language reasoning tasks. 
<p align="center">
  <img width="760" height="500" src="https://github.com/user-attachments/assets/aa4e2fa1-1a33-4511-a76c-2e95e24feee1">
</p>



### Project Methodology and Milestones
The project methodology is a mix of implementation and evaluation. The mentors are well-experienced in working with large codebases and will be available to guide through the technical and non-technical portions of the project. The step-by-step project methodology is outlined as follows. 

- **Installation of SmolLM2 from the official Git Repo:** The open-source implementation of SmolLM2 engine (hereon referred to as smollm plainly) is available on [GitHub](https://github.com/huggingface/smollm/tree/main/tools/smol_tools). The project primarily focuses on language reasoning and hence we limit ourselves to the SmolLM2 implementation and forego other forks of SmolLM such as the SmolVLM family.
  - The project needs to be sanity checked by installing the engine on local computers.
  - Following that, the students are to familiarize themselves with basic workflow such as running a sample code using the pretrained model. The instructions for installing SmolLM are located under the “tools” at smollm/tools/smol-tools subfolder.
  - Next step is to train the SmolLM using the prepackaged Transformer model called “HF://mlc-ai/SmolLM2-1.7B-Instruct-q0f16-MLC". The instructions are provided [here](https://github.com/huggingface/smollm/tree/main/tools/smol_tools).

- **Implementation—KAT in SmolLM:** The smollm pretrained model is at smollm/tools/smollm_local_inference/mlc.py. The pretrained model is called "HF://mlc-ai/SmolLM2-1.7B-Instruct-q0f16-MLC". This is an MLP-based Transformer. However, we will train the smollm with transformers ourselves with the same model as well as with KAT.
  - A KAT implementation is available on GitHub at [ICLR2025](https://github.com/Adamdad/kat). To implement KAT in smollm, we will replace the default Transformer (HF://mlc-ai/SmolLM2-1.7B-Instruct-q0f16-MLC) with the open-source KAT mentioned above.

- **Training SmolLM with default Transformer and with KAT:** This step will require compute resources and requires deployment of the implementation on Chameleon Cloud and/or National Research Platform (NRP). The mentors have access to these two testbeds and will provide the students access to those resources.
  - The first task of this step is to port to the implementation to Chameleon Cloud before the model can be trained. This task may require around a week’s worth of turnaround time and can be performed in parallel with steps 1 & 2 if needed.
  - **Training:** The FULL dataset for training smollm is called smolltalk located here: [HuggingFaceTB/smoltalk](https://huggingface.co/datasets/HuggingFaceTB/smoltalk). The training code and instructions are at  [huggingface/alignment-handbook](https://github.com/huggingface/alignment-handbook/tree/main/recipes/smollm2). Although the baseline uses SmolLM2-1.7.B-Instruct (pretrained model), we will instead train smollm for SmolLM2-135M-Instruct and SmolLM2-360M-Instruct as noted at the bottom of the page at [HuggingFaceTB/smoltalk](https://huggingface.co/datasets/HuggingFaceTB/smoltalk)· Datasets at Hugging Face. According to this, for SmolLM2-135M-Instruct and SmolLM2-360M-Instruct we will ONLY use the [smol-smolltalk dataset](https://huggingface.co/datasets/HuggingFaceTB/smol-smoltalk). 

- **Benchmarking:** Finally, the benchmarks used throughout this project to evaluate our implementations will be the same as those for the release (pretrained) versions SmolLM2-135M-Instruct and SmolLM2-360M-Instruct. The benchmarks for language reasoning will be [chosen](https://huggingface.co/spaces/open-llm-leaderboard/open_llm_leaderboard#/).


### Project Timeline
The following project timeline is anticipated. Some tasks may take longer or shorter than anticipated and hence the timeline is not 100% set in stone. However, it serves as a baseline based on the mentor’s prior experience on working with similar research projects. Each cell in the timeline chart is one week.
 ![image](https://github.com/user-attachments/assets/5a91f8fe-fb4c-4844-bff2-75c933e6f73a)


### Project Testbeds 
Sai Lamba Karanam has adminstrator-level access to the [National Research Platform (NRP)](https://nationalresearchplatform.org/) and will provide access to cloud resources (compute) to the students working on the project. Both mentors will also have access to [Chameleon Cloud platform](https://www.chameleoncloud.org/) and will grant access to compute resources for training, evaluation and benchmarking purposes.

### Project Deliverables
KALLM will be hosted on github at this [repo](https://github/saisumanv/KALLM). The mentors have extensive experience working with Machine Learning (ML) and Artifical Intelligence (AI) workflows in academic and industry settings. We seek to choose mentees that are willing to learn implementation of AI models and working with semi-large code bases. Mentees will have to become comfortable working with remote cloud testbeds (Chameleon and/or NRP) during the latter-half of the project. Some milestines described in the Project Methodolody can be done in parallel.

KALLM is part of larger collaborative effort between the mentors and involves milestones and outcomes that fall outside the scope of this project, but are related. The mentors plan to publish the large project outcomes aat ML-based venue(s) towards the end of Fall 2025. The mentees will be added as coauthors.


### KALLM

- **Topics**: Towards High Performance NCCL-enabled 2D partitioned PyLops-MPI library
- **Skills**: Python proficiency, scikit-learn, Experience with Linux, Introductory Experience with Cloud Computing Platforms
- **Difficulty**: Easy-Medium
- **Size**: Medium (175 hours)
- **Mentor**: {{< mention saisumanv >}}, {{< mention zahmeeth >}} 



