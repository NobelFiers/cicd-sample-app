node {
    stage('Preparation') {
        catchError(buildResult: 'SUCCESS') {
            sh 'docker stop samplerunning'
            sh 'docker rm samplerunning'
        }
    }
    stage('Build') {
           git url: 'https://github.com/NobelFiers/cicd-sample-app.git', branch: 'main'
           sh pwd
           sh if [ -d "tempdir" ]; then rm -rf tempdir/; fi
           sh bash ./sample-app.sh
    }
    stage('Results') {
        build 'Test_SampleApp'
    }
}