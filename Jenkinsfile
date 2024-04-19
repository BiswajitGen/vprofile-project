pipeline{
    agent any
    tools{
        maven "MAVEN3"
        jdk "OracleJDK8"
    }

    environment{
        SNAP_REPO = 'vprofile-snapshot'
        NEXUS_USER = 'admin'
        NEXUS_PASS = 'admin123'
        RELEASE_REPO = 'vprofile-release' 
        CENTRAL_REPO = 'vpro-maven-central'
        NEXUSIP = '10.10.139.55' 
        NEXUSPORT = '8081'
        NEXUS_GRP_REPO = 'vpro-maven-group'
        NEXUS_LOGIN = 'nexuslogin'
    }

    stages{
        stage('Build'){
            steps{
                sh 'mvn -s settings.xml -DskipTests install'
            }
            post{
                success{
                    echo "Now archiving"
                    archiveArtifacts artifacts: '**/*.war'
                }
            }

        }
        stage('Test'){
            steps{
                sh 'mvn test'
                echo "UNIT TEST"
            }
        }

        stage('Checkstyle Analysis'){
            steps{
                echo "CODE ANALYSIS VULNERABILITIES"
                sh 'mvn checkstyle:checkstyle'
            }
        }
    }
}
