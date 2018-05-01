node(slave43) {
// Delete the workspace
//deleteDir()
stage('Retrieve source code') {
    checkout scm
    
    }

   stage('Deploy') {
        sh "/bin/cp -f $WORKSPACE/Build-${env.BUILD_NUMBER}/docker${env.BUILD_NUMBER}.html /var/www/*.html
"
    }
  
   delivery.artifactory()
  }
  catch (e) {
      currentBuild.result = "FAILED"
      throw e
    }
}
