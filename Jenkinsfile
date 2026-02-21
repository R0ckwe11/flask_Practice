pipeline {
	agent any
	environment {
		CREDS = credentials('FlaskEC2')
	}
	stages {
		stage('Check SSH') {
			steps {
				sshagent(credentials: ['FlaskEC2']) {
					sh '''
						ssh -o StrictHostKeyChecking=no ec2-user@18.156.176.75 << EOF
							rm -rf ssh_test
							mkdir ssh_test
							touch ~/ssh_test/ssh_works
							cd ssh_test
							ls -l | grep ssh_works
					'''
				}
			}
		}
		stage('Clone repo') {
			steps {
				sshagent(credentials: ['FlaskEC2']) {
					sh '''
						ssh -o StrictHostKeyChecking=no ec2-user@18.156.176.75 << EOF
							rm -rf flask_Practice
							git clone https://github.com/R0ckwe11/flask_Practice.git
					'''
				}
			}
		}
		stage('VENV and dependencies') {
			steps {
				sshagent(credentials: ['FlaskEC2']) {
					sh '''
						ssh -o StrictHostKeyChecking=no ec2-user@18.156.176.75 << EOF
							rm -rf venv
							python -m venv venv
							source venv/bin/activate
							cd flask_Practice
							pip install -r requirements.txt
					'''
				}
			}
		}
		// stage('Install dependencies') {
		// 	steps {
		// 		sshagent(credentials: ['FlaskEC2']) {
		// 			sh '''
		// 				ssh -o StrictHostKeyChecking=no ec2-user@18.156.176.75 << EOF
		// 					cd flask_Practice
		// 					pip install -r requirements.txt
		// 			'''
		// 		}
		// 	}
		// }
		stage('Create .env') {
			steps {
				sshagent(credentials: ['FlaskEC2']) {
					sh '''
						ssh -o StrictHostKeyChecking=no ec2-user@18.156.176.75 << EOF
							cd flask_Practice
							echo 'MONGO_URI=mongodb://127.0.0.1:27017/students' > .env
							echo 'SECRET_KEY=qwerty' >> .env
							cat .env
					'''
				}
			}
		}
		// stage('Run'){
		// 	steps {
		// 		sh "python app.py"
	 //        }
		// }
	}
	post {
		always {
			sleep 5
		}
	}
}
