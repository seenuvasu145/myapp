node{
    stage('SCM Checkout'){
         git 'https://github.com/seenuvasu145/myapp.git'
}
    stage('Compile-Package'){

         def mvnHome = tool name: 'maven', type: 'maven' 
         sh "${mvnHome}/bin/mvn package"
	 sh 'cp target/*.war /opt/k8s-lab/myweb-0.0.5.war'
  } 
    
    stage('Build Docker image'){
        
	  sh 'ansible-playbook /opt/k8s-lab/create-simple-devops-image.yml'
	}
   stage('Push Docker image'){
        withCredentials([string(credentialsId: 'docker-pwd', variable: 'Dockerhubpwd')]) {
		sh " docker login -u vasucena145 -p ${Dockerhubpwd}"
	}
	  sh 'docker push vasucena145/simple-devops-image'
	  sh 'docker rmi simple-devops-image:latest vasucena145/simple-devops-image -f'
	}
  stage('Deploying to Kubernetes Cluster'){
        
	  sh 'ansible-playbook /opt/k8s-lab/kubernetes-esafe-deployment.yml'
	  sh 'ansible-playbook /opt/k8s-lab/kubernetes-esafe-service.yml'
	}
}
