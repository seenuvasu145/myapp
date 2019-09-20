node{
    stage('SCM Checkout'){
         git 'https://github.com/seenuvasu145/myapp.git'
}
    stage('Compile-Package'){

         def mvnHome = tool name: 'maven', type: 'maven' 
         sh "${mvnHome}/bin/mvn package"
	 sh 'cp target/*.war /opt/seenu/myweb-0.0.5.war'
  } 
    
    stage('Docker image Run and Push to Hub'){
        
	 sh 'ansible-playbook /opt/seenu/create-simple-devops-image.yml'
	}
}
