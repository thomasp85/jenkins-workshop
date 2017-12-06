node {
   stage("Preparation") {
      checkout scm
   }
   stage("Builde") {
       sh 'docker run -i --rm --name my-maven-project -v "$PWD":/usr/src/mymaven -w /usr/src/mymaven maven:3-jdk-8 mvn clean package'
   }
   stage("Javadoc") {
       sh 'docker run -i --rm --name my-maven-project -v "$PWD":/usr/src/mymaven -w /usr/src/mymaven maven:3-jdk-8 mvn site'
   }
   stage("Results") {
       junit '**/target/surefire-reports/TEST-*.xml'
       archiveArtifacts artifacts: 'target/gildedrose-*.jar', onlyIfSuccessful: true
   }
}
