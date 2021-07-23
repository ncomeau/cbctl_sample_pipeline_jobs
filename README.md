# cbctl Sample Pipeline Jobs - Image Scanning

This branch contains a single-use Jenkins job, aimed at highlighting the ```cbctl image scan``` capability. This capability allows for scanning of a container image to identify vulnerabilities which might exist, and prioritize accordingly based on intelligence-predicated, auto-generated severity scores. Thus allowing you to identify potential security risks, and mitigate them prior to deploying to a production environment.

## Setup

Please read the two options for setup found in the Main branch's README.md [here.](https://github.com/ncomeau/cbctl_sample_pipeline_jobs/blob/main/README.md)

### Option 1: Import the Jenkinsfile

Full instructions in link above - the only potential would be to the step 5 configurations, as outlined by the table below

Pipeline config | Value
--------------------- | ---------------------
Pipeline Definition: | Pipeline script from SCM
SCM: | Git
Repositories - Reposiroty URL: | ```https://github.com/ncomeau/cbctl_sample_pipeline_jobs.git```
Credentials: | _none_
Branches to build - Branch specifier: | ```*/image_scan```
Repository Browser: | (Auto)
Script Path: | ```Jenkinsfile```

### Option 2: Copy and Paste Jenkinsfile

Instructions remain the same as they were outlined [here.](https://github.com/ncomeau/cbctl_sample_pipeline_jobs/blob/main/README.md)

## Output

### Jenkins

![image](https://user-images.githubusercontent.com/18126247/126816167-0a50ff8c-9b92-4d5a-8d8c-9b7851a93769.png)


### Slack

![image](https://user-images.githubusercontent.com/18126247/126816243-b3dd58b6-4f2e-4d64-a018-4dbcb3f24b18.png)
