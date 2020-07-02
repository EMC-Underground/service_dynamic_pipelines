# Script Pipeline Service

This repo is designed to dynamically build pipelines for Concourse to execute
scripts and push the output to resources such as email, slack, ect...

## How to use:
1) Create a new Git hub repo with the following naming convention:
   "pipeline_script_<your_unique_name_here>"
2) Your new repo should contain the following:
   * Your Python or PowerShell script
   * A vars.yml file that is built using the vars.yml.example from the
     service_pipeline repo.
```
---
description: branch you want concourse to pull from to run your script
repo_branch: "master"

description: The Slack webhook url you want the script output to be sent to
slack_webhook_url: ((slack_webhook_url))

description: How often you want to have your script run
scheduled_minutes: "60"

description: The team name you want to use in Concourse (Used for logical
             seperation)
team_name: "main"

description: The name of the text file that will be created from your script
text_file_name: "Current-Unprotected-Report.csv"

description: The username/email address that the message in slack will be posted
             as
slack_username: ""

description: The emoji that will be used with the username in Slack
slack_icon_emoji: ""
```

3) Place unique sensitive information into Vault. ENTER URL HERE
   * An example of how you would reference the vault vales are as follows:
```
   $user = (get-childitem -path env:\VSPHERE_USERNAME).value
   $password = (get-childitem -path env:\VSPHERE_PASSWORD).value
```

## Environment Variables





The service dynamic pipeline builder is expecting a templatized version of your pipeline file
(pipeline.yml.tmpl)

