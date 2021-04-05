pipeline{		 
		 agent any
		 
		 environment
			 {
			  PATH = "/opt/apache-maven-3.6.3/bin:$PATH"
			 }
		 
			 {
			  PATH = "/opt/jdk-11.0.10/bin:$PATH"
			 }
		 stages
				{
					stage("Git Checkout")
						{
						 steps
								{
								 git branch: 'main', url: 'https://github.com/prashanth-konakala-bluepal/Multi-Branch-Pipeline.git'
								}
						}
					stage("Maven Build")
						 {
						  steps
								{
								 sh "mvn clean package"
								 sh "mv /var/lib/jenkins/workspace/Multi-Branch-Pipeline/webapp/target/*.war /var/lib/jenkins/workspace/Multi-Branch-Pipeline/webapp/target/simpleweb.war"
								}
						 }		
					stage('Deploying to Dev')
								 steps
										{
										 sshagent(['Tomcat_server-1'])
												{
												 sh """
												
													scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/Multi-Branch-Pipeline/webapp/target/simpleweb.war ubuntu@52.14.15.3:/opt/tomcat/webapps/
													
													ssh ubuntu@52.14.15.3 /opt/tomcat/bin/shutdown.sh
													
													ssh ubuntu@52.14.15.3 /opt/tomcat/bin/startup.sh
													
												"""
												}
										}
				}	
		}
