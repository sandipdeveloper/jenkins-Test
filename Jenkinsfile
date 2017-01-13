node("docker") {
    docker.withRegistry('https://artifactory.prodwest.citrixsaassbe.net:5000/setsale/test', 'docker') {
    
        git url: "https://github.com/sandipdeveloper/jenkins-Test.git", credentialsId: 'sandip-git'
    
        sh "git rev-parse HEAD > .git/commit-id"
        def commit_id = readFile('.git/commit-id').trim()
        println commit_id
    
        stage "build"
        def app = docker.build "jenkins-Test"
    
        stage "publish"
        app.push 'master'
        app.push "${commit_id}"
    }
}