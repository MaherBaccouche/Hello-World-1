node{
   
   environment {
        MAVEN_CLI_OPTS = '-Dmaven.repo.local=.m2 -s .m2/settings.xml -B'
        MAVEN_RELEASE_CLI_OPTS = '-DskipTests=true -Dmaven.test.skip=true -DskipITs -Darguments="-Dadditionalparam=-Xdoclint:none" -DcheckModificationExcludeList=.m2/settings.xml,MYAPP_VERSION.txt,MYAPP_NAME.txt,MAJOR_VERSION.txt,MINOR_VERSION.txt,MICRO_VERSION.txt,CURRENT_RELEASE.txt,NEXT_MAJOR_RELEASE.txt,NEXT_MINOR_RELEASE.txt,NEXT_MICRO_RELEASE.txt'
        REGISTRY_URL = 'https://repo.apps.adserviolyon.fr/repository/adserviolyon-snapshots/'
        SONAR_URL = ''
    }
 
   
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
