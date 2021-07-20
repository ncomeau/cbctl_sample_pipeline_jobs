node {
  
    // Set env variables for easy image changing
    withEnv([
      "REPO=ncomeau",
      "IMAGE=demo",
      "TAG=latest",
    ]){
        
        // Perform cbctl vuln scan of specified image
        stage('Cbctl Image Scan') {
         
            sh '/var/jenkins_home/app/cbctl image scan ${REPO}/${IMAGE}:${TAG} -o json > cbctl_image_scan.json'
        }
        
        // Send Results of cbctl scan to Slack w/pre-built helper python scripts
        stage('Send Results to Slack'){
            
            try{
                sh 'git clone https://github.com/slackapi/python-slack-sdk.git'
            }
            catch(exists){
                echo 'already exists'
            }
            
            try{
                sh 'python3 /var/jenkins_home/app/image_scan_slack.py cbctl_image_scan.json'
                sh "python3 /var/jenkins_home/app/success.py '${env.JOB_NAME}' '${env.BUILD_NUMBER}'"
            }
            
            catch(fail){
                sh "python3 /var/jenkins_home/app/failure.py '${env.JOB_NAME}' '${env.BUILD_NUMBER}' '${env.STAGE_NAME}'"
            }
        }
    }
}
