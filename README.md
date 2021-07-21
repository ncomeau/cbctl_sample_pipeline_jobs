# cbctl Sample Pipeline Jobs

In order to leverage this repo, please start by setting up your environment by following the [CBC_Container_CICD_Demo](https://github.com/ncomeau/CBC_Container_CICD_Demo) demo environment setup guide.

This repository is intended to provide several simple, single-use, Jenkins Pipeline Jobs. Each of these jobs are intended to highlight a specific capability offered by the CBC Container Security cbctl utility. 

If you want a more wholistic representation of how cbctl can be seamlessly incorporated in an end-to-end CI/CD build pipeline, please nagivate to the following repository and follow the simple setup instructions!
  * https://github.com/JaBarosin/K8sConfigs
  

## Setup & Usage Instructions

### Overview

As noted above, the forthcoming instructions are predicated on the notion that you have successfully completed the setup of the [CBC_Container_CICD_Demo](https://github.com/ncomeau/CBC_Container_CICD_Demo) demo environment.

This repository is comprised of 4 Branches:
  * **_main_** - this is purely used for initial overview and setup instructions
  * **_image_scan_** - this is the branch you would specify for highlighting the ```cbctl image scan``` 
      * _This capability allows for scanning of a container image to identify vulnerabilities which might exist, and prioritize accordingly based on intelligence-predicated, auto-generated severity scores._ 
  * **_image_validate_** - this is the branch you would specify for highlighting ```the cbctl image validate``` 
      * _This capability allows for validating the container image against the applicable CBC K8s security policy. Effectively allowing you to identify potential image violations prior to deploying said image into your environment._
  * **_k8s_validate_** - this is the branch you would specify for highlighting the ```cbctl k8s-object validate``` 
      * _This capability allows for validating the k8s yaml file configs against the applicable CBC K8s security policy. Effectively allowing you to identify potential k8s configuration violations prior to deploying said image into your environment, in an effort to improve hygiene and maintain a proactive container security posture._

### Setup Options

Now that the branches themselves have been described above, lets talk about their contents, and how to utilize them within your Jenkins Environment setup. 

If you look at each branch (go ahead, take a gander...I'll wait...) you will notice that each branch comes with its own readme (should there be any nuance to that specific job), possibly a deployment yaml (only for the k8s_validate), and most critically; its own **Jenkinsfile**. 

It is this **Jenkinsfile** which contains the configs for running the specific Jenkins Pipeline Job, and subsaquent cbctl action, within your own demo environment. 


