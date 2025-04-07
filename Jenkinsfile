// on basis of https://github.com/muratdemiray/jenkins-pipeline-load-generic/tree/main

// Parameters for the build
properties([
    parameters([
        string(name: 'JENKINS_FILE'),
    ]),
    pipelineTriggers([
        parameterizedCron('''
            */2 * * * * % JENKINS_FILE=pipelines/Jenkinsfile.1
        ''')
    ])
])

node {    
    //checkout main project files
    // need to manually checkout in scripted pipeline (differs from declarative pipeline which checkouts by default)
    def scmVars = checkout scm
    // pass the environment variables to new pipeline
    // withEnv(["COMMIT=${scmVars.GIT_COMMIT}","BRANCH=${scmVars.GIT_BRANCH}"]) {    
        // load Jenkinsfile Pipeline file from devops repository     
    sh "env | sort"

    if ( currentBuild.getBuildCauses('hudson.model.Cause$UserIdCause') || currentBuild.getBuildCauses('org.jenkinsci.plugins.parameterizedscheduler.ParameterizedTimerTriggerCause') ){
        load "${params.JENKINS_FILE}" 
    }

    // }
}