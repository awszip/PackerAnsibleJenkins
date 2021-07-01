pipeline {
	agent any
	parameters {
		string(name: "git_codebase", defaultValue: "https://github.com/awsyadav/PackerAnsibleJenkins.git", description: "git location of the packer files")
		//string(name: "ACCESS_KEY", defaultValue: "", description: "Access Key of FSMK-SecurityAccount")
		//string(name: "SECRET_KEY", defaultValue: "", description: "Secret Key of FSMK-SecurityAccount")
		string(name: "AMI_NAME", defaultValue: "ubuntu/images/*ubuntu-xenial-16.04-amd64-server-*", description: "Select name in this formate ex:- awsami=amzn2-ami-hvm-2.0*, redhat8=RHEL-8.2_HVM-*, awsecsami=amzn2-ami-ecs-hvm-2.0*-x86_64-ebs, ubuntu20=ubuntu/images/hvm-ssd/ubuntu-groovy-20.10-amd64-server*")
		string(name: "ssh_username", defaultValue: "ubuntu", description: "Select SSH user based on above OS selection , ubunut, ec2-user")
	}
	stages {
		stage('Create Packer AMI') {
			steps {
				withCredentials([
					usernamePassword(credentialsId: 'devop1fs', passwordVariable: 'SECRET_KEY', usernameVariable: 'ACCESS_KEY')
				])
				sh 'packer build -var aws_access_key="${ACCESS_KEY}" -var aws_secret_key="${SECRET_KEY}" -var AMI_NAME="$AMI_NAME" -var ssh_username="$ssh_username" packer/template.json'
				sh "cat manifest.json | jq .builds[0].artifact_id | tr -d '\"' | cut -b 11- > .ami"
				script {
					AMI_ID = readFile('.ami').trim()
				}
			}
		}
	}
}
