pipeline {
    agent any  // Run this pipeline on any available agent
    
    stages {

        stage('Build Frontend') {
            steps {
                dir('frontend') {
                    // Install Node.js dependencies and build the frontend application
                    sh 'npm install'  // Install frontend dependencies
                    sh 'npm run build'  // Build the frontend application
                }
            }
        }
        
        stage('Deploy to Nginx') {
            steps {
                script {
                    // Copy frontend build files to Nginx's HTML root
                    sh 'sudo cp -r build/* /usr/share/nginx/html/'  // Copy files to Nginx root
                    
                    // Restart Nginx to apply changes
                    sh 'sudo service nginx restart'  // Restart the Nginx service
                }
            }
        }
        
    }
}
