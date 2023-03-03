node('node1')
{
    stage('vcs')
    {
        git url:'https://github.com/jayainjeti/openmrs-core.gitd ',
            branch: 'scripted'
    }
    stage('build') 
    {
        sh 'export PATH="/usr/lib/jvm/java-1.8.0-openjdk-amd64/bin:$PATH" && mvn package'

    }
    stage('postbuild')
    {
        archiveArtifacts onlyIfSuccessful: true,
            artifacts: '**/target/openmrs.war',
            allowEmptyArchive: false
    }
    stage('show the test results') {
        junit testResults: '**/surefire-reports/TEST-*.xml',
              allowEmptyArchive: true
        
    }
}