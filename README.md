# Table of Contents
* [Introduction](#nvidia-ai-workbench-introduction)
   * [Project Description](#project-description)
   * [Sizing Guide](#sizing-guide)
* [Quickstart](#quickstart)
   * [Prerequisites](#prerequisites)
   * [Tutorial (Desktop App)](#tutorial-desktop-app)
   * [Tutorial (CLI-Only)](#tutorial-cli-only)
* [License](#license)

# NVIDIA AI Workbench: Introduction [![Open In AI Workbench](https://img.shields.io/badge/Open_In-AI_Workbench-76B900)](https://ngc.nvidia.com/open-ai-workbench/aHR0cHM6Ly9naXRodWIuY29tL05WSURJQS93b3JrYmVuY2gtZXhhbXBsZS1taXh0cmFsLWZpbmV0dW5l)

<!-- Banner Image -->
<img src="https://developer-blogs.nvidia.com/wp-content/uploads/2024/07/rag-representation.jpg" width="100%">

<!-- Links -->
<p align="center"> 
  <a href="https://www.nvidia.com/en-us/deep-learning-ai/solutions/data-science/workbench/" style="color: #76B900;">:arrow_down: Download AI Workbench</a> •
  <a href="https://docs.nvidia.com/ai-workbench/" style="color: #76B900;">:book: Read the Docs</a> •
  <a href="https://docs.nvidia.com/ai-workbench/user-guide/latest/quickstart/example-projects.html" style="color: #76B900;">:open_file_folder: Explore Example Projects</a> •
  <a href="https://forums.developer.nvidia.com/t/support-workbench-example-project-mixtral-finetune/303413" style="color: #76B900;">:rotating_light: Facing Issues? Let Us Know!</a>
</p>

## Project Description
The Mixtral-8x7B model is a powerful sparse Mixture of Experts (MoE) architecture that can outperform many larger models, like the Llama 2 70B model, while maintaining efficient inference. This project will focus on finetuning the base model on the GEM/viggo video game dataset, which is a domain specific dataset capturing meaning representation. 

Meaning representation is the task of representing natural language in a structured and logical form that machines can understand and manipulate. Once finetuned to convergence, this model can generate text crucial for downstream tasks such as named entity relation, semantic parsing, and relation extraction, outperforming its own out-of-the-box capabilities. 

* ```mixtral-finetune.ipynb```: This notebook provides a sample workflow for fine-tuning a 4-bit quantized Mixtral-8x7b base model for meaning representation on the GEM/viggo dataset using Low-Rank Adaptation Fine-tuning (LoRA), a popular parameter-efficient fine-tuning method. 

| :memo: Remember             |
| :---------------------------|
| This project is meant as an example workflow and a starting point; you are free to swap out the dataset, choose a different task, and edit the training prompts as you see fit for your particular use case! |

## Sizing Guide

| GPU VRAM | Example Hardware | Compatible? |
| -------- | ------- | ------- |
| <16 GB | RTX 3080, RTX 3500 Ada | N |
| 16 GB | RTX 4080 16GB, RTX A4000 | N |
| 24 GB | RTX 3090/4090, RTX A5000/5500, A10/30 | N |
| 32 GB | RTX 5000 Ada  | Y |
| 40 GB | A100-40GB | Y |
| 48 GB | RTX 6000 Ada, L40/L40S, A40 | Y |
| 80 GB | A100-80GB | Y |
| >80 GB | 8x A100-80GB | Y |

# Quickstart

## Prerequisites
AI Workbench will prompt you to provide a few pieces of information before running any apps in this project. Ensure you have this information ready. 
   
   * The location where you would like the Mixtral-8x7b model to live on the underlying **host** system. 
   * The Hugging Face API Key w/ Mixtral-8x7b access (see below).

| :exclamation: Important             |
| :---------------------------|
| Verify you can see a "You have been granted access to this model." message on the Hugging Face [model card](https://huggingface.co/mistralai/Mixtral-8x7B-v0.1); if not, you may need to accept the terms to grant access for your HF token. |

## Tutorial (Desktop App)

If you do not NVIDIA AI Workbench installed, first complete the installation for AI Workbench [here](https://www.nvidia.com/en-us/deep-learning-ai/solutions/data-science/workbench/). Then, 

1. Fork this Project to your own GitHub namespace and copy the link

   ```
   https://github.com/[your_namespace]/<project_name>
   ```
   
2. Open NVIDIA AI Workbench. Select a location to work in. 
   
3. Clone this Project onto your desired machine by selecting **Clone Project** and providing the GitHub link.
   
4. Wait for the project to build. You can expand the bottom **Building** indicator to view real-time build logs. 
   
5. When the build completes, set the following configurations.

   * `Environment` &rarr; `Mounts` &rarr; `Configure`. Specify the file path of the mount, eg. where the Mixtral-8x7b model will live on your **host** machine.
   
      eg. if you would like your finetuned model to be saved in your home path, enter ```/home/[user]``` or ```/mnt/C/Users/[user]``` (Windows)

   * `Environment` &rarr; `Secrets` &rarr; `Configure`. Specify the Hugging Face Token as a project secret.

6. On the top right of the window, select **Jupyterlab**. 

7. Navigate to the `code` directory of the project. Then, open your fine-tuning notebook and get started. Happy coding!

## Tutorial (CLI-Only)
Some users may choose to use the **CLI tool only** instead of the Desktop App. If you do not NVIDIA AI Workbench installed, first complete the installation for AI Workbench [here](https://www.nvidia.com/en-us/deep-learning-ai/solutions/data-science/workbench/). Then, 
1. Fork this Project to your own GitHub namespace and copying the link

   ```
   https://github.com/[your_namespace]/<project_name>
   ```
   
2. Open a shell and activating the Context you want to clone into by

   ```
   $ nvwb list contexts
   
   $ nvwb activate <desired_context>
   ```

   | :bulb: Tip                  |
   | :---------------------------|
   | Use ```nvwb help``` to see a full list of  AI Workbench commands. |
   
3. Clone this Project onto your desired machine by running

   ```
   $ nvwb clone project <your_project_link>
   ```
   
4. Open the Project by

   ```
   $ nvwb list projects
   
   $ nvwb open <project_name>
   ```

5. Start **Jupyterlab** by

   ```
   $ nvwb start jupyterlab
   ```
   
   * Specify the file path of the mount, eg. where the Mixtral-8x7b model will live on your **host** machine.
   
      eg. if you would like your finetuned model to be saved in your home path, enter ```/home/[user]``` or ```/mnt/C/Users/[user]``` (Windows)

   * Specify the Hugging Face Token as a project secret.

6. Navigate to the `code` directory of the project. Then, open your fine-tuning notebook and get started. Happy coding!

# License
This NVIDIA AI Workbench example project is under the [Apache 2.0 License](https://github.com/NVIDIA/workbench-example-mixtral-finetune/blob/main/LICENSE.txt)

This project may utilize additional third-party open source software projects. Review the license terms of these open source projects before use. Third party components used as part of this project are subject to their separate legal notices or terms that accompany the components. You are responsible for confirming compliance with third-party component license terms and requirements. 

| :question: Have Questions?  |
| :---------------------------|
| Please direct any issues, fixes, suggestions, and discussion on this project to the DevZone Members Only Forum thread [here](https://forums.developer.nvidia.com/t/support-workbench-example-project-mixtral-finetune/303413) |
