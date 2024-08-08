# Jenkins CI/CD Pipeline for JMeter Test Execution

This repository contains a Jenkins pipeline script designed to execute a JMeter performance test in non-GUI mode and generate reports. Below is an overview of the pipeline's structure and functionality.

## Prerequisites

Before you run this pipeline, ensure the following prerequisites are met:

1. **JMeter Installation**: Apache JMeter must be installed on the machine where the Jenkins agent is running. The pipeline script uses JMeter version 5.6.3. Update the path in the pipeline script if your installation is different.
   
2. **JMeter Script**: The JMeter test script (`.jmx` file) should be available at the specified path in the `SCRIPT_PATH` environment variable.

## Pipeline Overview

The Jenkins pipeline is defined in a declarative syntax and consists of two main stages:

1. **Run JMeter Test**: Executes the JMeter test script and generates the results.
2. **Archive Results**: Archives the generated test results for later use or analysis.

### Pipeline Structure

The pipeline structure includes stages for running the JMeter test and archiving the results. Environment variables are used to define paths and file locations, and the `bat` command is used to execute Windows batch commands.

### Stages Explained

1. **Run JMeter Test**:
    - **Environment Variables**: Defines paths for JMeter, the test script, result directories, and output files.
    - **Preparation**: Ensures the result and HTML report directories exist before executing the test.
    - **Test Execution**: Runs the JMeter test script in non-GUI mode, generating both CSV results and an HTML report.
    - **Verification**: Lists the contents of the result directories to confirm the output files were generated.

2. **Archive Results**:
    - This stage is set up to archive the generated test results. The archiving commands are currently commented out. Uncomment and configure these commands as needed.

### Post-Execution

The `post` section always runs, providing a final message indicating that the pipeline execution is complete.

## Customization

- **JMeter Paths**: Update the `JMETER_HOME`, `SCRIPT_PATH`, `RESULT_DIR`, and other related environment variables to reflect your setup.
- **Archiving**: Uncomment the archiving steps in the `Archive Results` stage if you want Jenkins to store the test results.

## Running the Pipeline

To execute this pipeline:
1. Save the script in your Jenkins project.
2. Trigger the build through the Jenkins UI or configure it to run on a schedule or after specific events.

## Conclusion

This Jenkins pipeline script provides an automated way to run JMeter tests, generate reports, and optionally archive the results. Customize the paths and archiving steps as per your project requirements.
