pipeline
{
	agent any
	stages
	{
		stage('Build Application')
		{
			steps
			{
				bat 'mvn clean install'
			}
		}
		stage('Deploy Application To MuleSoft Cloudhub')
		{
			steps
			{
				bat 'mvn package deploy -DmuleDeploy'
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