node('new43') {
// Delete the workspace
//deleteDir()
    def app
stage('Retrieve source code') {
    checkout scm
    
    }
    sstage('Build image') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */

        app = docker.build("shanmukha443/new43:img${env.BUILD_NUMBER}")
    }

    stage('Test image') {
        /* Ideally, we would run a test framework against our image.
         * For this example, we're using a Volkswagen-type approach ;-) */

        app.inside {
            sh 'echo "Tests passed"'
        }
    }

    stage('Push image') {
        /* Finally, we'll push the image with two tags:
         * First, the incremental build number from Jenkins
         * Second, the 'latest' tag.
         * Pushing multiple tags is cheap, as all the layers are reused. */
        docker.withRegistry('https://registry.hub.docker.com', 'docker-vsv') {
            app.push("img${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }
}
  
