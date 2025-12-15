pipeline {
    agent any
    // Define the parameter here
    parameters {
        string(name: 'IMAGE_TAG', defaultValue: 'latest', description: 'The image tag to deploy')
    }
    stages {
        stage('Deploy on k8') {
            steps {           
                sh 'cp -R helm/* .'
                
                // Use params.IMAGE_TAG instead of image.tag
                // Note: We use double quotes "" for interpolation
                sh """
                    /usr/local/bin/helm upgrade --install petclinic-app ./mychart \
                    --set image.repository=registry.hub.docker.com/dschrute/test-repo \
                    --set image.tag=${params.IMAGE_TAG}
                """ 
            }           
        }
    }
}