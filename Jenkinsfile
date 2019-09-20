node{
    stage('SCM Checkout'){
         git 'https://github.com/seenuvasu145/myapp.git'
}
    stage('Compile-Package'){

         def mvnHome = tool name: 'maven', type: 'maven' 
         sh "${mvnHome}/bin/mvn package"
  } 
    
    stage('Docker image Run and Push to Hub'){
        
		      sh 'ansible-playbook /opt/k8s-lab/create-simple-devops-image.yml'
	}
}
