pipeline {
    agent any
    stages {
          stage('Baking AMI') {
              steps {
                      sh 'packer build packer/template.json'
//                    sh 'packer build fundingsocieties-base-amz-ecs.json'
//                    sh 'packer build fundingsocieties-base-amz-lnx2-with-consul.json'
//                    sh 'packer build fundingsocieties-base-amz-lnx2.json'
                     sh """ 
                     ami_id=($(cat manifest.json | jq .builds[0].artifact_id | tr -d '\"' | cut -b 16-))
                     """

      }
     }
          stage('Push AMI ID to SecurityAccount ParameterStore') {
              steps {
                  sh 'aws ssm put-parameter --name “/Prod/Images/FSMK/AmazonECS" --type "String" --value "${ami_id}" --overwrite'
              }
          }
         stage('Slack Notification') {
             steps {
                 sh " echo  SLACK MESSAGE ”'
             }
         }
   }
}
