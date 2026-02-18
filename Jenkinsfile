def remote = [:]
remote.name = 'Apache'
remote.host = 'ec2-18-156-176-75.eu-central-1.compute.amazonaws.com'
remote.allowAnyHosts = true

pipeline {
	agent any
	environment {
		CREDS = credentials('FlaskEC2')
	}
	stages {
		stage('Works?'){
			steps {
				sh "echo 'Works!'"
			}
		}
		stage('SSH Works?'){
			steps {
				script {
					remote.user = env.CREDS_USR
					remote.password = env.CREDS_PSW
				}
				sshCommand(remote: remote, command: "sudo touch ~/ssh_works")
				sshCommand(remote: remote, command: "ls -l ~ | grep ssh_works")
			}
		}
// 		stage('Checkout'){
// 			steps {
// 				git branch: "main", url: "https://github.com/RajanChettri/flask_Practice.git"
// 			}
// 		}
// 		stage('Configure'){
// 			steps {
// 			  	sh "pip install -r requirements.txt"
// 			}
// 		}
// 		stage('Create .env'){
// 			steps {
// 			  	sh "echo 'MONGO_URI=mongodb://127.0.0.1:27017/students' > .env"
// 			  	sh "echo 'SECRET_KEY=qwerty' >> .env"
// 			  	sh "cat .env"
// 			}
// 		}
// 		stage('Run'){
// 			steps {
// 				sh "python app.py"
// 	        }
// 		}
	}
	post {
		always {
			sleep 5
		}
	}
}
