node("docker") {
    docker.withRegistry('birla01/docker2ec2', '6860942e-27fa-4e10-925a-de2613662b94') {
    
        git url: "https://github.com/birla01/docker-base-tester-behat.git", credentialsId: 'birla01'
    
        sh "git rev-parse HEAD > .git/commit-id"
        def commit_id = readFile('.git/commit-id').trim()
        println commit_id
    
        stage "build"
        def app = docker.build "birla01/docker2ec2"
    
        stage "publish"
        app.push 'master'
        app.push "${commit_id}"
    }
}
