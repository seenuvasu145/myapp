node{
    stage('SCM Checkout'){
         git 'https://github.com/seenuvasu145/myapp.git'
}
    stage('Compile-Package'){

         def mvnHome = tool name: 'maven', type: 'maven' 
         sh "${mvnHome}/bin/mvn package"
	 sh 'cp target/*.war /opt/seenu/myweb-0.0.5.war'
  } 
    
    stage('Build Docker image'){
        
	  sh 'ansible-playbook /opt/seenu/create-simple-devops-image.yml'
	}
   stage('Push Docker image'){
        withCredentials([string(credentialsId: 'docker-pwd', variable: 'Dockerhubpwd')]) {
		sh " docker login -u vasucena145 -p ${Dockerhubpwd}"
	}
	  sh 'docker push vasucena145/devops-image'
	  sh 'docker rmi devops-image:latest vasucena145/devops-image -f'
	}
}
