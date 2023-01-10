def appName='Jenkins_Test_App'
def deployName = 'prod'
def dataFormat ='json'
def configFile ='component3.json'
// 'config/**/Component/*.json'
def target ='COMPONENT'
def namePath ="/jenkinsTest/main/${currentBuild.number}"
def initCommit=false
def fnlCommit =true
def validate =true
def convertPath =false
def changesetNumber=""
def chgsetUpld2Dplybl=''
def snapshotName=''
def openChangeset ='Chset-87'
def inputFrRegistr =null
def secondInitRes=''
def publishAppName ='JENKINS_TEST_APP'
def publishDeployName ='preprod'
def publishSnapshotName='preprod-v49.dpl'
def getAppName='Jenkins_Test_App'
def getChngstNmbr='Chset-368'
def getDeployName=''
def isValidated =false
def outputForm='xml'
def validateRespnonse=''


def fullFileName="${appName}-${deployName}-${currentBuild.number}.${dataFormat}"
def exporterName ='returnAllData-now' 
// returnAllData-nowPreview1
def exporterArgs ="{\"nodepath\": \"Preprod\",\"pathSeparator\": \",\"}"




pipeline {
agent any
stages {
    stage('Clone repository') {               
       steps{
            // checkout scm
            git branch: 'master', url: 'https://github.com/iamkumaramit/samplejava.git'
       }
    }     
    stage('Upload Configuration file'){
        steps{
            script{
                sh "echo uploading configuration file ${configFile}"
                echo "name path ::::: ${namePath}"
                 echo "!!!!!!!!!!!Now uploading to Component!!!!!!!!!!!"
                //  changesetNumber =openChangeset
                 echo "********* changesetNumber:${changesetNumber}*************"
                changesetNumber = snDevOpsConfigUpload(
                         applicationName: "${appName}",
                         deployableName: "${deployName}",
                         changesetNumber:"${changesetNumber}",
                         dataFormat: "${dataFormat}",
                         configFile: "${configFile}",
                         target:"${target}",
                         namePath: "${namePath}",
                         autoCommit:"${initCommit}",
                         autoValidate:"${validate}",
                         convertPath:"${convertPath}",
                         showResults:true,
                         markFailed:false
                         )
                    echo "######### Intial upload changesetNumber:${changesetNumber} ##########"
                        //  if(changesetNumber == null){
                        //      changesetNumber=''
                        //      echo "will try now upload with changeset number as :${changesetNumber}"
                        //  }
                         
                 //upload to test
                  snDevOpsConfigUpload(
                         applicationName: "${appName}",
                         deployableName: "test",
                         changesetNumber:"${changesetNumber}",
                         dataFormat: "${dataFormat}",
                         configFile: "${configFile}",
                         target:"${target}",
                         namePath: "${namePath}",
                         autoCommit:"${fnlCommit}",
                         autoValidate:"${validate}",
                         convertPath:"${convertPath}",
                         showResults:true,
                         markFailed:false
                 )
                 echo "!!!!!!!!!!! Upload to component is done under changeset:${changesetNumber}"
                 
                 echo "!!!!!!!!!!!Now uploading to Deployables!!!!!!!!!!!"
                 echo"uploading to preprod"
                  //upload to PreProd
                //   chgsetUpld2Dplybl=openChangeset
                  echo "********* chgsetUpld2Dplybl:${chgsetUpld2Dplybl}*************"
                     chgsetUpld2Dplybl=    snDevOpsConfigUpload(
                         applicationName: "${appName}",
                         deployableName: "preprod",
                         changesetNumber:"${chgsetUpld2Dplybl}",
                         dataFormat: "${dataFormat}",
                         configFile: "${configFile}",
                         target:'DEPLOYABLE',
                         namePath: "${namePath}",
                         autoCommit:"${initCommit}",
                         autoValidate:"${validate}",
                         convertPath:"${convertPath}",
                         showResults:true,
                         markFailed:false
                 )
                 echo "Changeset: ${chgsetUpld2Dplybl}. created for the intial upload to deployable:preprod"
                //  if(chgsetUpld2Dplybl == null){
                //              chgsetUpld2Dplybl=''
                //              echo "will try now upload with chgsetUpld2Dplybl as :${chgsetUpld2Dplybl}"
                //          }
                 echo"uploading to prod"
                        snDevOpsConfigUpload(
                         applicationName: "${appName}",
                         deployableName: 'PROD',
                         changesetNumber:"${chgsetUpld2Dplybl}",
                         dataFormat: "${dataFormat}",
                         configFile: "${configFile}",
                         target:'DEPLOYABLE',
                         namePath: "${namePath}",
                         autoCommit:"${initCommit}",
                         autoValidate:"${validate}",
                         convertPath:"${convertPath}",
                         showResults:true,
                         markFailed:false
                 )
                         
                 echo"uploading to test"
                        snDevOpsConfigUpload(
                         applicationName: "${appName}",
                         deployableName: 'TEST',
                         changesetNumber:"${chgsetUpld2Dplybl}",
                         dataFormat: "${dataFormat}",
                         configFile: "${configFile}",
                         target:'DEPLOYABLE',
                         namePath: "${namePath}",
                         autoCommit:"${fnlCommit}",
                         autoValidate:"${validate}",
                         convertPath:"${convertPath}",
                         showResults:true,
                         markFailed:false
                 )
                 
                echo "Upload to deployable:test, is done under Change-set: ${chgsetUpld2Dplybl}"
            }
        }
    }
    stage("Get snapshots created"){
        steps{
            echo "amit-Triggering Get snapshots scenarios for applicationName:${getAppName},changesetNumber:${getChngstNmbr} & deployableName:${getDeployName}"
            // echo "Triggering Get snapshots for applicationName:${appName},deployableName:${deployName},changeSetId:${changesetNumber}"
            script{
            //   echo "######START1########## Application + Deployable ################"
            //   getDeployName="TEST"
            //   echo "@@@@@@@@@@@@@@@Inputs:${getAppName} & ${getDeployName} @@@@@@@@@@@@@@@"
            //     changeSetResults = snDevOpsConfigGetSnapshots(
            //             applicationName: "${getAppName}",
            //             changesetNumber: "",
            //             deployableName: "${getDeployName}",
            //             outputFormat:"xml",
            //             isValidated:"${isValidated}",
            //             showResults:true,
            //             markFailed:false
            //           )
            //     echo "######END1########## Application + Deployable Result : ${changeSetResults}"
                
                
                // echo "######START2########## Application + Changeset ################"
                // // getChngstNmbr =chgsetUpld2Dplybl
                // // getChngstNmbr ="chset-343"
                // echo "@@@@@@@@@@@@@@@Inputs:${getAppName} & ${getChngstNmbr} @@@@@@@@@@@@@@@"
                // changeSetResults = snDevOpsConfigGetSnapshots(
                //         applicationName: "${getAppName}",
                //         changesetNumber: "${getChngstNmbr}",
                //         deployableName: "",
                //         outputFormat:"xml",
                //         isValidated:"${isValidated}",
                //         showResults:true,
                //         markFailed:false
                //       )
                // echo "######END2########## Application + Changeset Result : ${changeSetResults}"
                
                echo "######START3########## Application + Changeset + Deployable ################"
                echo "@@@@@@@@@@@@@@@Inputs:${getAppName} , ${chgsetUpld2Dplybl} & ${getDeployName} & isValidated: ${isValidated} & ${outputForm}@@@@@@@@@@@@@@@"
                changeSetResults = snDevOpsConfigGetSnapshots(
                        applicationName: "${appName}",
                        changesetNumber: "${chgsetUpld2Dplybl}",
                        deployableName: "",
                        outputFormat:"xml",
                        isValidated:false,
                        showResults:true,
                        markFailed:false
                      )
                echo "######END3########## Application + Changeset + Deployable Result : ${changeSetResults}"
                if(changeSetResults !=null){
                    def changeSetResultsObject = readJSON text: changeSetResults
                    changeSetResultsObject.each {
                        if(it.validation == "passed"){
                            echo "validation passed for snapshot : ${it.name}"
                            snapshotName = it.name
                        }else{
                            echo "Snapshot failed to get validated : ${it.name}" ;
                            // assert it.validation == "passed"
                            def deployable = it.name.split('-')[0]
                            echo "################ : ${deployable}"
                            validateRespnonse = snDevOpsConfigValidate(
                                              applicationName: "${appName}", 
                                              deployableName: "${deployable}", 
                                              snapshotName: "${it.name}", 
                                              markFailed:false
                                              ,showResults:true
                                              )
                        }
                    }
            //   if (!snapshotName?.trim()){
            //     error "No snapshot found to proceed" ;
            //   }
              echo "Snapshot Name : ${snapshotName}"
                }
                    
                }
            }
        }
    
    
    stage("Get latest snapshots"){
        steps{
            echo "Triggering Get latest snapshots for applicationName:${appName},deployableName:${deployName}"
            // echo "Triggering Get snapshots for applicationName:${appName},deployableName:${deployName},changeSetId:${changesetNumber}"
            script{
                changeSetResults = snDevOpsConfigGetSnapshots(
                      applicationName: "${appName}",
                      changesetNumber: "",
                      deployableName: "${deployName}"
                       ,outputFormat:"xml",
                         showResults:true,
                         markFailed:false
                      )
                echo "ChangeSet Result : ${changeSetResults}"
                if(changeSetResults !=null){
                                    def changeSetResultsObject = readJSON text: changeSetResults
                     changeSetResultsObject.each {
                        if(it.validation == "passed" || it.validation == "passed_with_exception"){
                            echo "validation passed for snapshot : ${it.name}"
                            snapshotName = it.name
                        }else{
                            echo "Snapshot failed to get validated : ${it.name}" ;
                            // assert it.validation == "passed"
                            def deployable = it.name.split('-')[0]
                            echo "################ : ${deployable}"
                            validateRespnonse = snDevOpsConfigValidate(
                                              applicationName: "${appName}", 
                                              deployableName: "${deployable}", 
                                              snapshotName: "${it.name}", 
                                              markFailed:false
                                              ,showResults:true
                                              )
                        }
                    }
            //   if (!snapshotName?.trim()){
            //     error "No snapshot found to proceed" ;
            //   }
              echo "Snapshot Name : ${snapshotName}"
                }
            }
        }
    }
    stage("Register change set to pipeline"){
        steps{
            script{
                    // chngstFrRegistr = chgsetUpld2Dplybl
                    inputFrRegistr=chgsetUpld2Dplybl
                        // echo "Change set registration for changesetNumber: ${inputFrRegistr}"
                        echo "Registering pipeline using input as: ${inputFrRegistr}"
                        changeSetRegResult = snDevOpsConfigRegisterPipeline(
                        applicationName:"${appName}",
                        changesetNumber:"${inputFrRegistr}",
                        // snapshotName:"",
                                 showResults:true,
                                 markFailed:false
                        )
                        echo "Register pipeline step result: ${changeSetRegResult}"
    
            }
        }
    }
    stage('Initiate ChangeRequest'){
        steps{
            echo "Devops Change trigger change request"
            snDevOpsChange(
                applicationName:"${appName}",
                snapshotName: "${snapshotName}"
            )
        }

    }
    
    stage('Publish the snapshot'){
        steps{
            script{
                publishAppName =appName
                publishDeployName =deployName
                publishSnapshotName=snapshotName
                echo "Step to publish snapshot applicationName:${publishAppName},deployableName:${publishDeployName} snapshotName:${publishSnapshotName}"
                    publishSnapshotResults = snDevOpsConfigPublish(
                    applicationName:"${publishAppName}",
                    deployableName:"${publishDeployName}",
                    snapshotName: "${publishSnapshotName}",
                    showResults:true,
                    markFailed:false
                )
                 // echo " Publish result for applicationName:${appName},deployableName:${deployName} snapshotName:${snapshotName} is ${publishSnapshotResults}"
            }
        }
    }
    stage('Export Snapshots from Service Now') {
        steps{
            script{
                echo "Exporting for App: ${appName} Deployable; ${deployName} Exporter name ${exporterName} "
                echo "Configfile exporter file name ${fullFileName}"
                sh  'echo "<<<<<<<<<export file is starting >>>>>>>>"'
                response = snDevOpsConfigExport(
              applicationName: "${appName}", 
              snapshotName: "", 
              deployableName: "prod", 
              exporterFormat: "${dataFormat}", 
              fileName:"${fullFileName}", 
              exporterName: "${exporterName}",
              showResults:true,
              markFailed:false
            //   ,exporterArgs:"${exporterArgs}"
              )
                echo " RESPONSE FROM EXPORT : ${response}"
            }
        }
    }
    stage("Deploying to Prod"){
        steps{
            echo "Reading config from file name ${fullFileName}"
            echo " ++++++++++++ BEGIN OF File Content ***************"
            sh "ls ${fullFileName}"
            // sh "cat ${fullFileName}"
            echo " ++++++++++++ END OF File content ***************"
            echo "deploy finished successfully."
        }
    }
}
post{
     always{
         echo ">>>>>Displaying Test results"
           junit '**/*.xml'
     }
 }
}
