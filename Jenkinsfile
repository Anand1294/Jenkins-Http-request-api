import groovy.json.JsonSlurper
pipeline {
    agent any
    stages {
        stage ("http request") {
            steps {
                script {
                    def response = httpRequest url: 'http://localhost:8080/api/json?pretty=true',
                        authentication: 'Anand-http-req'
                    println("Status: "+response.status)
                    println("Content: "+response.content)
                    /*def result = response.content
                    result_list = JSON.parse(result);
                    println("RESULT:"+result_list[0].jobs.name)*/
                    JsonSlurper jsonSlurper = new JsonSlurper()
                    def parseJson = jsonSlurper.parseText(response.content)
                    def i=1;
                    parseJson.jobs.each { id, data -> 
                    println ("Job Name "+i+" :" +id.name) 
                    i++;    
                    }
                }
            }
        }
    }
}
