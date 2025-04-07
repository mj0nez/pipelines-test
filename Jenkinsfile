// Parameters for the build
properties([
    parameters([
        string(name: 'JENKINS_FILE'),
    ])
])

node {    
    //checkout main project files
    // need to manually checkout in scripted pipeline (differs from declarative pipeline which checkouts by default)
    scmVars = checkout scm
    // pass the environment variables to new pipeline
    // withEnv(["COMMIT=${scmVars.GIT_COMMIT}","BRANCH=${scmVars.GIT_BRANCH}"]) {    
        // load Jenkinsfile Pipeline file from devops repository     
    load params.JENKINS_FILE  
    // }
}