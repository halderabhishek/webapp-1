node{
    stage('SCM Checkout'){
        git url:'https://github.com/RajaPradeep/webapp-1.git'
    }
    stage('MVN Package'){
        def mvnHome = tool name: 'maven_3.6', type: 'maven'
        def mvnCMD = "${mvnHome}/bin/mvn"
        sh "${mvnCMD} clean package"
    }
 
    stage('Deploy'){
	    def dockerRun = '/home/ec2-user/deployWebApp.2_tomcat.sh'
	    sshagent(['15e5ae04-30fa-4b6d-b8ef-056ab51688e0']) {
            sh "ssh -o StrictHostKeyChecking=no ec2-user@172.31.81.16 ${dockerRun}"
        }             
    }
}
