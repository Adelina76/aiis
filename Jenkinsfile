pipeline {
    agent any
    options {
        timestamps()
    }
    stages {
        stage("Installing libraries") {
            steps {
                sh 'pip3 install -r requirements.txt'
		echo 'Libraries are ready'
            }
        }
        stage("Start") {
	    parallel {
		stage("Start pytest") {            
			steps {
	                	sh 'python3 -m pytest -v --junitxml=report.xml test.py'
				junit '*.xml'
				echo 'Pytest is ready'
	            	}
	        }
		
	}
    }
}
}
