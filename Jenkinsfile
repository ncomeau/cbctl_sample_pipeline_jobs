node {
  
    violations = false
    // Set env variables for easy image changing
    withEnv([
      "REPO=ncomeau",
      "IMAGE=demo",
      "TAG=latest",
    ]){
        
        // Perform cbctl validate of the specified image against your CBC K8s policy, which maps to the applied scope & policy specified in the config yaml
        stage('Cbctl K8s Object Validate') {
          
          try{
            sh '/var/jenkins_home/app/cbctl k8s-object validate example.yaml -o json > cbctl_k8s_validate.json'
          }
          
          catch(violate){
            violations = true
          }
        }
        
        // Send Results of cbctl image validate to Slack w/pre-built helper python scripts
        stage('Send Results to Slack'){
            
          try{
                sh 'git clone https://github.com/slackapi/python-slack-sdk.git'
            }
          catch(exists){
                echo 'already exists'
            }
          
          if(violations == false){
                sh "python3 /var/jenkins_home/app/success.py '${env.JOB_NAME}' '${env.BUILD_NUMBER}'"
            }
            
          if(violations == true){
                sh 'python3 /var/jenkins_home/app/k8s_validate_slack.py cbctl_k8s_validate.json'

            }
        }
      
      stage('Confirm Success/Failure'){
        
        if(violations == false){
          echo "No violations found. You're image is good to go!"
        }
        
        if(violations == true){
          echo "Violations were found. Its ok, these things happen..."
          sh "python3 /var/jenkins_home/app/failure.py '${env.JOB_NAME}' '${env.BUILD_NUMBER}' '${env.STAGE_NAME}'"
          error("Failed Deployment due to CB Container policy violations.")
        }
      }
    }
}
