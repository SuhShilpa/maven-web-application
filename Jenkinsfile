node
{
    timestamps {
    // some block
buildDescription 'scriptedway project'
def mavenHome= tool name:"Maven 3.8.5"
 //get the code
    stage("CheckOut"){
git branch: 'development', credentialsId: 'git', url: 'https://github.com/SuhShilpa/maven-web-application.git'
    }
    
    //build stage
    stage("Build"){
        sh ("$mavenHome/bin/mvn clean package")
    }
    //execute sonar qube report.
      stage("Executesonar"){
        sh ("$mavenHome/bin/mvn sonar:sonar")
      }
        //execute upload to nexus
      stage("uploadtoNexus"){
        sh ("$mavenHome/bin/mvn deploy")
    }
    //execute deploytotomcat
    stage("deploytotomcat"){
        sshagent(['0a63885a-4cbb-4f14-941e-5bde37571e5b']) {
    sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@43.204.101.35:/opt/apache-tomcat-9.0.64/webapps/"
}
}
}
}
