pipeline{
	//agent any
	agent { docker { image 'vprasadk111/programusingdockergithubjenkins:0.0.1' } }
	environment{
        MY_FILE = fileExists 'launch.py'
   	 }
	stages{
		 stage('Confirmation') {
            	 steps {
             	 input('Do you really want to proceed with ?')
            		}
		 }
		
		stage('Check File'){
            	when { expression { MY_FILE == 'true' } }
            	steps {
                echo "file exists"
           		 }
		}
		
		stage('conditional if not exists'){
            	when { expression { MY_FILE == 'false' } }
                steps {
                echo "file does not exist"
            		}
        	}
		
		stage('Test'){
			steps{
				
				sh 'python --version'
				}
				}
			
		}
}
