			pipeline {
				 agent any
				//agent {docker {image 'maven:3.6.3'}}
				environment{
				dockerHome = tool 'mydocker'
			        mevenHome = tool 'mymaven'
			        PATH = "$dockerHome/bin:$mevenHome/bin:$PATH"	
				}
				stages{
				stage('CheckOut') {
					steps {
				        sh 'mvn --version'	
					sh 'docker version'
					echo "Build"
					echo  "PATH --> $Path"
					echo  "BUILD NO --> $env.BUILD_NUMBER"
				       echo  "BUILD RUL -- > $env.BUILD_URL"
				     echo  "JOB --> $env.JOB_NAME"
					}
				}
			     stage('Compile') {
					steps {
					sh "mvn clean compile"
					}

				}		
					
					
				stage('Test') {
					steps {
					sh "mvn test"
					}

				}
				stage('Integration Test') {
					steps {
				sh "mvn failsafe:integration-test failsafe:verify"
					}
				}
				}
			}
