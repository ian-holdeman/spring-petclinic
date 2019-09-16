echo 'Cool pipeline stuff starting...' 
        stage 'Compile' 
        node { 
          sh "/usr/bin/mvn -B compile war:war" 
        } 
        stage 'Test' 
        node { 
            sh "/usr/bin/mvn -B verify" 

          step([$class: 'ArtifactArchiver', artifacts: '**/target/*.war', fingerprint: true])   
          step([$class: 'JUnitResultArchiver', testResults: '**/target/surefire-reports/TEST-*.xml']) 
        } 
