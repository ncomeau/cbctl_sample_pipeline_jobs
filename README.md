# cbctl Sample Pipeline Jobs

In order to leverage this repo, please start by setting up your environment by following the [CBC_Container_CICD_Demo_env](https://github.com/ncomeau/CBC_Container_CICD_Demo_Env) demo environment setup guide.

This repository is intended to provide several simple, single-use, Jenkins Pipeline Jobs. Each of these jobs are intended to highlight a specific capability offered by the CBC Container Security cbctl utility. 

If you want a more wholistic representation of how cbctl can be seamlessly incorporated in an end-to-end CI/CD build pipeline, please nagivate to the following repository and follow the simple setup instructions!
  * https://github.com/JaBarosin/K8sConfigs
  

## Setup & Usage Instructions

### Overview

As noted above, the forthcoming instructions are predicated on the notion that you have successfully completed the setup of the [CBC_Container_CICD_Demo Env](https://github.com/ncomeau/CBC_Container_CICD_Demo_Env) demo environment.

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

If you look at each branch (go ahead, take a gander...I'll wait...) you will notice that each branch comes with its own readme (should there be any nuance to that specific job), and most critically; its own **Jenkinsfile**. 

It is this **Jenkinsfile** which contains the configs for running the specific Jenkins Pipeline Job, and subsaquent cbctl action, within your own demo environment. 

There are 2 options for running any of the simple single-use jobs, which are elucidated below.

## Option 1: Import the Jenkinsfile 

***This is the recommended approach, because this process will be required for the [full pipeline demo](https://github.com/JaBarosin/K8sConfigs) to get the necessary files. However, option 2 is certainly easier, and viable for these single-use examples***

1. Login to your Jenkins Server _(can be either on the demo vm - 0.0.0.0:8080, or your Mac \<demo_machine_ip\>:8080)_

2. Select either ```Create a Job``` or ```New Item``` on the left-hand side
![image](https://user-images.githubusercontent.com/18126247/126556231-abf0ded9-fffc-494b-9bb5-df5ffabf1d02.png)
          
3. Add in a name of the job --> Select ```Pipeline``` --> Hit ```Ok```
![image](https://user-images.githubusercontent.com/18126247/126556584-384ea3a3-9fa0-46ce-8829-d5559189da29.png)

4. Check the box entitled ```Github Project```
   * Import in the repo url - in this case it would simply be: ```https://github.com/ncomeau/cbctl_sample_pipeline_jobs```
![image](https://user-images.githubusercontent.com/18126247/126557082-877995c0-70bf-4d55-8e51-4f6ca3d84370.png)

5. Continue to scroll down, and change the following:
     1. Change **Definition** field to ```Pipeline script from SCM```
     2. Change **SCM** field to ```Git```
     3. Change **Repository URL** to ```https://github.com/ncomeau/cbctl_sample_pipeline_jobs.git```
     4. Change **Branch Specifier** to ```*/<name of branch you want to import>```
        * _Ignore the red ✖️, that always happens_
     5. Lastly, click ```Apply``` & ```Save```
     ![image](https://user-images.githubusercontent.com/18126247/126558678-d3d1cc4e-93b4-45ed-b583-58de6caa7dac.png)
     
 
6. Everything should be all set - simply click ```Build Now``` on the left-hand side, and see it all in action!
![image](https://user-images.githubusercontent.com/18126247/126559789-c4d63498-ab01-4408-bf45-a4fba1115f39.png)




## Option 2: Copy and Paste Jenkinsfile

***This is the simplier of the two approaches, and allows for easy customization of the Jenkinsfile content within Jenkins, without having to fork this repo. However, although viable for these single-use examples, it does some limitations when utilizing more wholistic [demo pipelines](https://github.com/JaBarosin/K8sConfigs).***

1. Within this Github repo, navigate to the branch for the cbctl function you are intending to utilize

2. Click on the ```Jenkinsfile``` to expand the content

3. Copy out the entire ```Jenkinsfile``` content

4. Repeat Steps 1-3 in **Option** 1 noted above

5. Rather than check any boxes, simply scroll down to the bottom of the page
      1. Ensure that the **Definition** field is ```Pipeline Script```
      2. Paste the ```Jenkinsfile``` you copied in step 3 into the ```Script``` Section
      3. Lastly, click ```Apply``` & ```Save```
      ![image](https://user-images.githubusercontent.com/18126247/126561641-eead9f0a-7e67-473d-ac44-72f3a28a1ddd.png)

6.  Everything should be all set - simply click ```Build Now``` on the left-hand side, and see it all in action!
![image](https://user-images.githubusercontent.com/18126247/126562236-3c641b2b-2303-409b-85d1-a9e0436ed00f.png)



