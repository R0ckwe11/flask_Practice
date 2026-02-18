pipeline {
	agent any
	stages {
		// stage('Works?'){
		// 	steps {
		// 		sshagent(credentials: ['FlaskEC2']) {
		// 			sh "ssh ec2-user@ec2-18-156-176-75.eu-central-1.compute.amazonaws.com 'echo "Works!"'"
		// 		}
		// 	}
		// }
		stage('Works?'){ 
			steps {
				sh "echo 'Works!'"
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
}
