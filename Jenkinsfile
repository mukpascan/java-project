node('linux') {   
	stage('Unit Test') {
		git 'https://github.com/mukpascan/java-project.git'
		sh 'ant -f test.xml -v'
		junit 'reports/result.xml'
	}
	
	stage('Build') {    
		sh 'ant -f build.xml -v'
	}
	
	stage('Deploy') {
		sh 'aws s3 cp /workspace/java-pipeline/dist/rectangle-${BUILD_NUMBER}.jar s3://cf-templates-cxezeqmiwxzj-us-east-1'
	}
	
	stage('Report'){
		withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: '9846ec93-c376-463a-a22a-d1d75143de0d', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
    		// some block
		
		sh 'aws cloudformation describe-stack-resources --region us-east-1 --stack-name jenkins'
		}
	}
	
	
}
