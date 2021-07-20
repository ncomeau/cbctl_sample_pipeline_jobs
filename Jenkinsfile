
node {
  
    // Set env variables for easy image changing
    withEnv([
      "REPO=ncomeau",
      "IMAGE=demo",
      "TAG=latest",
    ]){
        
        // Perform cbctl validate of the specified image against your CBC K8s policy, which maps to the applied scope & policy specified in the config yaml
        stage('Cbctl Image Validate') {
         
            sh '/var/jenkins_home/app/cbctl image validate ${REPO}/${IMAGE}:${TAG} -o json > cbctl_image_validate.json'
        }
        
        // Send Results of cbctl image validate to Slack w/pre-built helper python scripts
        stage('Send Results to Slack'){
            
            try{
                sh 'git clone https://github.com/slackapi/python-slack-sdk.git'
            }
            catch(exists){
                echo 'already exists'
            }
            
            try{
                sh "python3 /var/jenkins_home/app/success.py '${env.JOB_NAME}' '${env.BUILD_NUMBER}'"
            }
            
            catch(fail){
                sh 'python3 /var/jenkins_home/app/image_validate_slack.py cbctl_image_validate.json'
                sh "python3 /var/jenkins_home/app/failure.py '${env.JOB_NAME}' '${env.BUILD_NUMBER}' '${env.STAGE_NAME}'"
            }
        }
    }
}
