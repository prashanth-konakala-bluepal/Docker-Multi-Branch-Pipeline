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
						stage ('Maven Build') 
							{
								steps
								{
										sh 'mvn clean compile'
								}
							}
						stage ('Testing Stage')
							{
								steps
								{
									sh 'mvn test'
								}
							}
						stage ('Deploying to Dev')
							{
								steps
								{
										sh 'mvn deploy'
								}
							}
					}
		}
