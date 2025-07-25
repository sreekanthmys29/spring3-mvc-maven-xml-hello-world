

@Library('sharedMulLib') _
pipeline{

 agent any
 
 tools{
  maven 'mavenlinux'
  jdk   'JDK17'
  git   'Default'
  
 }

 environment{
   projectKey = 'spring3-mvc-maven-xml-hello-world'
   url= 'http://104.197.209.222:9000'
   login='sqp_f03ac30b765d3bfa7dcef1122cbc388809d6bb00'
   
 }
 
  stages{
  
 
    stage('Checkout') {
            steps {
                gitclone(
                    branch: 'master',
                    url: 'https://github.com/sreekanthmys29/spring3-mvc-maven-xml-hello-world.git',
                    credentialsId: 'GitRepoCredentials'
                )
            }
    }
		      
   stage("Build"){
	steps{
	       echo "Executing step Checkout"
		    script{
			 def goal= 'package'
			 build(goal);
			 }
	  }
   }
   stage("sonarQube"){
     steps{
	       echo "Executing step sonarQube"
		    script{
			 
		     sonar( 
			     projectKey: env.projectKey,
			     url: env.url,
			     login: env.login);
		 }
	  }
   }
   stage("Nexus"){
	steps{
	       echo "Executing step Nexus"
		   
	  }
   }
   stage("Tomcat"){
	steps{
	       echo "Executing step Tomcat"
	  }
   }
  stage("Docker"){
	steps{
	       echo "Executing step Docker"
	  }
   }	  
 
  
 
  }




}//pipeline
