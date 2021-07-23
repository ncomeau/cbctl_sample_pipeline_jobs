# cbctl Sample Pipeline Jobs - Image Validate

This branch contains a single-use Jenkins job, aimed at highlighting the ```cbctl k8s-object validate``` capability. This capability allows for validating the k8s yaml file configs against the applicable CBC K8s security policy. Effectively allowing you to identify potential k8s configuration violations prior to deploying said image into your environment; in an effort to improve hygiene, and maintain a proactive container security posture.

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
Branches to build - Branch specifier: | ```*/k8s_validate```
Repository Browser: | (Auto)
Script Path: | ```Jenkinsfile```

### Option 2: Copy and Paste Jenkinsfile

Instructions remain the same as they were outlined [here.](https://github.com/ncomeau/cbctl_sample_pipeline_jobs/blob/main/README.md)

## Output

### Jenkins
   * **Note**: _The failure is intentional, because my CBC K8s policy had 'Memory Limits' & 'CPU Limits' requirements as an applicable rule, which were not implimented in the example.yaml created within the Jenkinsfile - this can be entirely customized, based on your own CBC K8s Policy for K8s Workloads._
   
![image](https://user-images.githubusercontent.com/18126247/126817888-5f587a5c-bfb3-442d-98de-07f61b2c9f39.png)



### Slack
   * **Note**: _The failure is intentional, because my CBC K8s policy had 'Memory Limits' & 'CPU Limits' requirements as an applicable rule, which were not implimented in the example.yaml created within the Jenkinsfile - this can be entirely customized, based on your own CBC K8s Policy for K8s Workloads._
   
![image](https://user-images.githubusercontent.com/18126247/126817974-4f8b4fda-1a9c-4d3b-a61b-6bf59bdf3cbb.png)


