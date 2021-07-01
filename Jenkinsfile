pipeline {
    agent any
    parameters {
        string(name: "git_codebase", defaultValue: "git@ec2-18-200-215-85.eu-west-1.compute.amazonaws.com:ibm-admin/sastoaws-infra.git", description: "git location of the terraform config files")
        string(name: "ACCESS_KEY", defaultValue: "", description: "Access Key of FSMK-SecurityAccount"),
        string(name: "SECRET_KEY", defaultValue: "", description: "Secret Key of FSMK-SecurityAccount")
    }
    stages {
          stage('Checkout') {
          //git branch: branch, credentialsId: '', url: "https://github.com/${gitRepoUrl}"
            steps {
                git credentialsId: '4f246b54-c7f5-44fe-b114-1d8617879706', url: "${params.git_codebase}"
            }
      }
          stage('Create Packer AMI') {
              steps {
                sh 'packer build -var aws_access_key="$ACCESS_KEY" -var aws_secret_key="$SECRET_KEY"  packer/template.json'
      }
     }
   }
}