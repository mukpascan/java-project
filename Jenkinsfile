node('linux') {   
	stage('Unit Test') {
		git 'https://github.com/mukpascan/java-project.git'
		sh 'ant -f test.xml -v'
		junit 'reports/result.xml'
	}
	
	stage('Build') {    
		sh 'ant -f build.xml -v'
	}
	
	
}
