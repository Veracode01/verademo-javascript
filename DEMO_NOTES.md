# Demo Notes

Notes, tips, and hints for using the various Veracode scan types with this application.

Also see the `docs/flaws` folder for in-depth explanations of the various exploits exposed in this application.

## Static scanning

Build the app using veracode autopackager:

	./veracode package --source verademo-javascript -a

The veracode-auto-pack-verademo-javascript-js.zip file is the file to upload for scanning. Either upload this file to the Veracode platform for a Policy/Sandbox scan, or use it with the Veracode Pipeline scan.

## SCA scanning

### Upload/Scan

This will just happen as part of the Policy or Sandbox scan.

### Agent-based scan

Use either the command-line version of the SCA agent (follow the install and config instructions in the Veracode [docs center](https://docs.veracode.com/r/c_sc_what_is) ) or the IDE plugin to initiate an SCA scan.

### Vulnerable Methods

The Veracode agent-based SCA scan can also find [vulnerable methods](https://docs.veracode.com/r/Finding_and_Fixing_Vulnerabilities#fixing-vulnerable-methods). This app implements the vulnerable zipObjectDeep method.

### SBOM generation

SBOM generation for the application is supported after an SCA scan ([link](https://docs.veracode.com/r/Generating_a_Software_Bill_of_Materials_SBOM_for_Upload_Scans)) 

SBOM generation for the Docker container is supported by the Container/CLI scanner ([link](https://docs.veracode.com/r/veracode_sbom)).



### Veracode Fix
This application contains flaws that can be rectified with [Veracode Fix](https://docs.veracode.com/r/veracode_fix)

## Build the application

	./veracode package --source verademo-javascript -a

## Run the Veracode Pipeline scanner

	java -jar ${path-to-pipeline-scanner}/pipeline-scan.jar -f target/verademo-javascript.war -esd true 

## Run Veracode Fix
There's two ways to run the Fix

Install the VSCode plugin and scan within VSCode as seen below.

<img src="https://github.com/veracode-demo-labs/verademo-javascript/blob/main/docs/DEMO_NOTES_Images/VSCodePlugin.png" width="800" />  

Run fix in the Command-line

  	veracode fix src-app/controllers/userController.js

Theres an example of CWE-78 flaw on line 37 that has a fix.

### Container Scan
From the root of the project run the Veracode Container Scan

 	veracode scan --type directory --source . --output container_results.json	


trivial edit to trigger repo scan
