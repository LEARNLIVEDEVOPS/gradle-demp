pipeline {
    agent any

    stages {
        stage ('Clone') {
            steps {
                git branch: 'master', url: "https://github.com/jfrog/project-examples.git"
            }
        }

       

        stage ('Exec Gradle') {
            steps {
                rtGradleRun (
                    tool: GRADLE_TOOL, // Tool name from Jenkins configuration
                    rootDir: "gradle-examples/gradle-example-ci-server/",
                    buildFile: 'build.gradle',
                    tasks: 'clean artifactoryPublish',
                    deployerId: "GRADLE_DEPLOYER",
                    resolverId: "GRADLE_RESOLVER"
                )
            }
        }

        
    }

