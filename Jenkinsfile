node('linux') {   
	stage('Unit Test') {
		git git 'https://github.com/mukpascan/java-project.git'
		sh 'ant -f test.xml -v'
		junit 'reports/result.xml'
	}
}
