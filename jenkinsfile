node {
    
    stage('Preparation') { // for display purposes
        // Get some code from a GitHub repository
         git 'https://github.com/NeelimaBontha/WEZVACICD.git'
        
    }
    stage('Build') {
        // Run the maven build
        sh 'mvn clean package'
    }

    stage('deployee the code'){
    
    sh '''cd target
    scp samplewar.war ubuntu@172.31.24.158:/home/ubuntu/.
    ssh ubuntu@172.31.24.158 \'sudo cp samplewar.war /var/lib/tomcat9/webapps/. ;
    sudo systemctl restart tomcat9\'
    '''
    }
    
 stage('Email Notification'){
		mail bcc: '', body: """Hi Team, You build successfully deployed
		                       Job URL : ${env.JOB_URL}
							   Job Name: ${env.JOB_NAME}

Thanks,
DevOps Team""", cc: '', from: '', replyTo: '', subject: "${env.JOB_NAME} Success", to: 'neelimagopireddy@gmail.com'   
}
}
