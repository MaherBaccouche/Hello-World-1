node{
    
    stage("Git Clone"){
        git credentialsId: 'GIT_CREDENTIALS', url: 'https://github.com/MaherBaccouche/Gestion.git'
    }
    stage("Maven Clean Build"){
        def mavenHome = tool name: "mavenLocal", type: "maven"
        def mavenCMD = "${mavenHome}/bin/mvn"
        sh "${mavenCMD} clean package"
       
    }
    }
