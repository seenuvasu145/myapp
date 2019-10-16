node{
    stage('SCM Checkout'){
         git 'https://github.com/seenuvasu145/myapp.git'
      }
    stage('Build & Unit test'){
		sh 'mvn clean verify -DskipITs=true';
      		junit '**/target/surefire-reports/TEST-*.xml'
      		archive 'target/*.jar'
   	}
}
