// put this file in the branches of the main/code repository

node {    
    //checkout main project files
    // need to manually checkout in scripted pipeline (differs from declarative pipeline which checkouts by default)
    scmVars = checkout scm

    //checkout devops repository (other repository)
    sh 'mkdir -p devops'
	dir("devops")
    {
        script{
            git branch: "main", 
                url: 'https://github.com/claudio-bianco/load-devops.git'            
        }
    }
    
    // pass the environment variables to new pipeline
    withEnv(["COMMIT=${scmVars.GIT_COMMIT}","BRANCH=${scmVars.GIT_BRANCH}"]) {    
        // load Jenkinsfile Pipeline file from devops repository     
        load 'devops/project_A/full-pipeline.Jenkinsfile'  
    }
}
