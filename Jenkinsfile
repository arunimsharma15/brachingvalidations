pipeline {
    agent {
        node{
            label 'maven'
        }
    }

    environment {
        PATH = "/opt/maven/apache-maven-3.9.6/bin:$PATH"
        version = ''
    }


    stage("Build stage"){
            steps {
                
                echo "----------- build started ----------"
                sh 'mvn clean deploy -Dmaven.test.skip=true'

                script {
                    version = sh(script: "mvn -q -Dexec.executable=echo -Dexec.args='\${project.version}' --non-recursive exec:exec", returnStdout: true).trim()
                }
                echo "----------- build complted ----------"

            }
        }
}
