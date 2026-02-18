def remote = [:]
remote.name = 'FlaskEC2'
remote.host = '18.156.176.75'
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
					remote.identityFile = env.CREDS
				}
				sh "echo $env.CREDS_USR"
				sh "echo $env.CREDS"
				sshCommand(remote: remote, command: "touch ~/ssh_works")
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
