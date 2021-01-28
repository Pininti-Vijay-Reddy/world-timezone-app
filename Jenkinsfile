pipeline
{
	agent any
	environment 
	{
    	//adding a comment for the commit test
    	DEPLOY_CREDS = credentials('anypoint-credentials')
    	MULE_VERSION = '4.3.0'
    	BG = "Capgemini"
    	WORKER = "Micro"
  	}
	stages
	{
		stage('Build Application')
		{
			steps
			{
				bat 'mvn -B -U -e -V clean -DskipTests package'
			}
		}
		stage('Munit Testing')
		{
			steps
			{
				bat 'mvn test'
			}
		}
		stage('Deploy Application To MuleSoft Cloudhub')
		{
			environment 
			{
        		ENVIRONMENT = 'India-Mulesoft-Practice-Sandbox'
        		APP_NAME = 'worldtimezone-service-vijay'
      		}
			steps
			{
				bat 'mvn -U -V -e -B -DskipTests deploy -DmuleDeploy -Dmule.version="%MULE_VERSION%" -Danypoint.username="%DEPLOY_CREDS_USR%" -Danypoint.password="%DEPLOY_CREDS_PSW%" -Dcloudhub.app="%APP_NAME%" -Dcloudhub.environment="%ENVIRONMENT%" -Dcloudhub.bg="%BG%" -Dcloudhub.worker="%WORKER%"'
			}
		}
		stage('Perfrom Regression Testing')
		{
			steps
			{
				bat 'C:\\Users\\Vijay\\AppData\\Roaming\\npm\\newman run D:\\Newman\\worldtimezone.postman_collection.json --disable-unicode'
			}
		}
	}
}