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
		// stage('Works?'){
		// 	steps {
		// 		sh "echo 'Works!'"
		// 	}
		// }
		stage('Check SSH'){
			steps {
				// script {
				// 	remote.user = env.CREDS_USR
				// 	remote.identityFile = env.CREDS
				// }
				// sshCommand(remote: remote, command: "touch ~/ssh_works")
				// sshCommand(remote: remote, command: "ls -l ~ | grep ssh_works")
				sshagent(credentials: ['FlaskEC2']) {
					sh '''
						ssh -o StrictHostKeyChecking=no ec2-user@18.156.176.75 << 'EOF'
							mkdir ssh_test
							touch ~/ssh_test/ssh_works
							cd ssh_test
							ls -l
							EOF
					'''
				}
			}
		}
		// stage('Clone repo'){
		// 	steps {
		// 		// git branch: "main", url: "https://github.com/RajanChettri/flask_Practice.git"
		// 		sshCommand(remote: remote, command: "rm -rf flask_Practice/")
		// 		sshCommand(remote: remote, command: "git clone https://github.com/R0ckwe11/flask_Practice.git")
		// 		sshCommand(remote: remote, command: "cd flask_Practice/")
		// 	}
		// }
		// stage('Create and activate venv'){
		// 	steps {
		// 	  	sshCommand(remote: remote, command: "python -m venv venv")
		// 		sshCommand(remote: remote, command: "source venv/bin/activate")
		// 	}
		// }
		// stage('Install dependencies'){
		// 	steps {
		// 		sshCommand(remote: remote, command: "ls -l")
		// 		sshCommand(remote: remote, command: "ls -l | grep requirements")
		// 		sshCommand(remote: remote, command: "pip install -r requirements.txt")
		// 	}
		// }
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
