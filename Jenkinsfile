

@Library('sharedMulLib') _
pipeline{

 agent any
 
 tools{
  maven 'mavenlinux'
  jdk   'JDK17'
 }

 environment{
   projectKey = 'spring3-mvc-maven-xml-hello-world'
   url= 'http://104.197.209.222:9000'
   login='sqp_f03ac30b765d3bfa7dcef1122cbc388809d6bb00'
   
 }
 
  stages{
  
   stage("checkout"){
      steps{
		 echo "Executing step checkout"
	     timeout(time: 5, unit: 'SECONDS')
		 script{
			 def branch= 'master'
			 #def credentailsId= credentials(GitRepocredentials)
			  def credentailsId= 'GitRepoCredentials'
			 def url= 'https://github.com/sreekanthmys29/spring3-mvc-maven-xml-hello-world.git'
		     git(branch,credentailsId,url);
		 }
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
			 
		     sonar(${env.projectKey},${env.url},${env.login});
		 }
	  }
   }
   stage("Nexus"){
	steps{
	       echo "Executing step Nexus"
		   
	  }
   }
   stage("Docker"){
	steps{
	       echo "Executing step Docker"
	  }
   }
  }




}//pipeline
