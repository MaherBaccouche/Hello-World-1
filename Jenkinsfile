pipeline{
   agent any
    
   
   stages {
        stage("Git Clone"){
            git credentialsId: 'GIT_CREDENTIALS', url: 'https://github.com/MaherBaccouche/Hello-World-1.git'
    }
        stage("Maven Clean Build"){
         def mavenHome = tool name: "mavenLocal", type: "maven"
         def mavenCMD = "${mavenHome}/bin/mvn"
         sh "${mavenCMD} clean package"
           }
        stage('Versioning') {
            steps {
                sh '''
                    PROJECT_VERSION=$(mvn help:evaluate --non-recursive -Dexpression=project.version -q -DforceStdout)
                    APP_NAME=$(mvn help:evaluate --non-recursive -Dexpression=project.artifactId -q -DforceStdout)
                    MAJOR_VERSION=$(echo $PROJECT_VERSION | cut -d. -f1)
                    MINOR_VERSION=$(echo $PROJECT_VERSION | cut -d. -f2)
                    PATCH_VERSION=$(echo $PROJECT_VERSION | cut -d. -f3 | cut -d- -f1)
                    CURRENT_RELEASE=$(echo $PROJECT_VERSION | grep -o '.*[0-9]')
                    NEXT_MAJOR=$(echo "${MAJOR_VERSION+1}.${MINOR_VERSION}.${PATCH_VERSION}-SNAPSHOT")
                    NEXT_MINOR=$(echo "${MAJOR_VERSION}.${MINOR_VERSION+1}.${PATCH_VERSION}-SNAPSHOT")
                    NEXT_PATCH=$(echo "${MAJOR_VERSION}.${MINOR_VERSION}.${PATCH_VERSION+1}-SNAPSHOT")
                '''
            }

        
    }
}
}
