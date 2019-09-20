node{
    stage('SCM Checkout'){
         git 'https://github.com/seenuvasu145/myapp.git'
}
    stage('Compile-Package'){

         def mvnHome = tool name: 'maven', type: 'maven' 
         sh "${mvnHome}/bin/mvn package"
  } 
}
