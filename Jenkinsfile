pipeline{
    agent any
    tools{
        maven "MAVEN3"
        jdk "OracleJDK8"
    }

    environment{
        NEXUS_VERSION = "nexus3"
        SNAP_REPO = 'vprofile-release'
        NEXUS_USER = 'admin'
        NEXUS_PASS = 'admin123'
        RELEASE_REPO = 'vprofile-release' 
        CENTRAL_REPO = 'vpro-maven-central'
        NEXUS_IP = '10.10.139.55 ' 
        NEXUSPORT = '8081'
        NEXUS_GRP_REPO = 'vpro-maven-group'
        NEXUS_LOGIN = 'nexuslogin'
    }

    stages{
        stage('Build'){
            steps{
                sh 'mvn -s settings.xml -DskipTests install'
            }

        }
    }
}
