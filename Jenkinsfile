pipeline {
    agent any
//     parameters {
// //         string(name: "git_codebase", defaultValue: "https://github.com/awsyadav/PackerAnsibleJenkins.git", description: "git location of the packer files")
// //         string(name: "ACCESS_KEY", defaultValue: "", description: "Access Key of FSMK-SecurityAccount")
// //         string(name: "SECRET_KEY", defaultValue: "", description: "Secret Key of FSMK-SecurityAccount")
// //         string(name: "AMI_NAME", defaultValue: "ubuntu/images/*ubuntu-xenial-16.04-amd64-server-*", description: "Select name in this formate ex:- awsami=amzn2-ami-hvm-2.0*, redhat8=RHEL-8.2_HVM-*, awsecsami=amzn2-ami-ecs-hvm-2.0*-x86_64-ebs, ubuntu20=ubuntu/images/hvm-ssd/ubuntu-groovy-20.10-amd64-server*")
// //         string(name: "ssh_username", defaultValue: "ubuntu", description: "Select SSH user based on above OS selection , ubunut, ec2-user")
//     }
    stages {
//           stage ('Packer Install') {
//               steps {
//                   checkout scm
//                     sh "ls -lat"
//                     sh "whoami"
//                     sh "sudo su -"
//                     sh "whoami"
//                     sh "pwd"
//                     sh "sudo yum install -y yum-utils"
//                     sh "sudo yum-config-manager --add-repo https://rpm.releases.hashicorp.com/AmazonLinux/hashicorp.repo"
//                     sh "sudo yum -y install packer"
//                     sh "packer version"
//               }
//           }
          stage('Baking AMI') {
              steps {
                   sh 'packer build packer/template.json'
//                    sh 'packer build fundingsocieties-base-amz-ecs.json'
//                    sh 'packer build fundingsocieties-base-amz-lnx2-with-consul.json'
//                    sh 'packer build fundingsocieties-base-amz-lnx2.json'
                  
//                 sh 'packer build -var aws_access_key="$ACCESS_KEY" -var aws_secret_key="$SECRET_KEY" -var AMI_NAME="$AMI_NAME" -var ssh_username="$ssh_username" packer/template.json'
//                 sh "cat manifest.json | jq .builds[0].artifact_id | tr -d '\"' | cut -b 11- > .ami"
//                 script {AMI_ID = readFile('.ami').trim()}
      }
     }
//          stage('Push AMI to ParameterStore') {
//              steps {
//                  sh 'aws ssm put-parameter --name “/Prod/Images/FSMK/Ubuntu" --type "String" --value "ami-id0asas" --overwrite'
//              }
//          }
         stage('Slack Notification') {
             steps {
                 sh " echo  SLACK MESSAGE ”'
             }
         }
   }
}
