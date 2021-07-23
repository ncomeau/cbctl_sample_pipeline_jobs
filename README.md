# cbctl Sample Pipeline Jobs - Image Validate

This branch contains a single-use Jenkins job, aimed at highlighting the ```cbctl image validate``` capability. This capability allows for validating the container image against the applicable CBC K8s security policy. Thus, effectively allowing for the identification of potential image violations, prior to deploying said image into your environment, and optimization of a CI/CD deployment pipeline.

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
Branches to build - Branch specifier: | ```*/image_validate```
Repository Browser: | (Auto)
Script Path: | ```Jenkinsfile```

### Option 2: Copy and Paste Jenkinsfile

Instructions remain the same as they were outlined [here.](https://github.com/ncomeau/cbctl_sample_pipeline_jobs/blob/main/README.md)

## Output

### Jenkins
   * **Note**: _The failure is intentional, because my K8s image policy had 'Vulnerabilities with Fixes' as an applicable rule - this can be entirely customized, based on your own CBC K8s Policy for container images._
   
![image](https://user-images.githubusercontent.com/18126247/126816777-5b01193b-4b9a-41de-8961-41331b6545c2.png)



### Slack
   * **Note**: _The failure is intentional, because my K8s image policy had 'Vulnerabilities with Fixes' as an applicable rule - this can be entirely customized, based on your own CBC K8s Policy for container images._
   
![image](https://user-images.githubusercontent.com/18126247/126817090-580f8b5d-0d87-4efa-90f3-fc2c9398ab95.png)

