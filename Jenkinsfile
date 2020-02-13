node{
   
        
 
   
        stage("Git Clone"){
           git credentialsId: 'GIT_CREDENTIALS', url: 'https://github.com/MaherBaccouche/Hello-World-1.git'
           }
        stage("Maven Clean Build"){
           def mavenHome = tool name: "mavenLocal", type: "maven"
           def mavenCMD = "${mavenHome}/bin/mvn"
           sh "${mavenCMD} clean package"
           }
        
         stage('Unit Tests') {
             //when { anyOf { branch 'feature/*'; branch 'fix/*' } }
             steps {
                sh 'mvn test ${MAVEN_CLI_OPTS}'
             }

    

}
