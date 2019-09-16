echo 'Hello from Pipeline Demo' 
        stage 'Compile' 
        node { 
          git url: 'https://github.com/ian-holdeman/spring-petclinic.git'
          sh "/usr/bin/mvn -B compile war:war" 
        } 
        stage 'Test' 
        node { 
	          git url: 'https://github.com/ian-holdeman/spring-petclinic.git'
            sh "/usr/bin/mvn -B verify" 

          step([$class: 'ArtifactArchiver', artifacts: '**/target/*.war', fingerprint: true])   
          step([$class: 'JUnitResultArchiver', testResults: '**/target/surefire-reports/TEST-*.xml']) 
        } 
