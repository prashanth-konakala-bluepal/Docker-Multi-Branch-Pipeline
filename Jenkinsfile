pipeline{	
		 agent { label 'master' }
	
		 stages
				{
					stage("Git Checkout")
					{
						 steps
								{
								 git branch: 'main', url: 'https://github.com/prashanth-konakala-bluepal/Multi-Branch-Pipeline.git'
								}
					}
				}	
		}
