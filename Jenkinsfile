node {
    stage('Preparation') {
        catchError(buildResult: 'SUCCESS') {
            sh 'docker stop samplerunning'
            sh 'docker rm samplerunning'
       			                   }
    			 }

    stage('Build') {
           git url: 'https://github.com/NobelFiers/cicd-sample-app.git', branch: 'main'
           sh 'pwd'
           if (fileExists('tempdir')) {
               sh 'rm -r tempdir'
                                      }    
	   sh 'bash ./sample-app.sh'
	}

    stage('Results') {
       sh '''
        curl -s http://172.17.0.2:5050/ | grep "You are calling me from 172.17.0.3"
       '''
    		     }
}