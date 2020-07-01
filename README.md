# Dynamic Script Pipelines Service

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
repo_branch: "master"
slack_webhook_url: ((slack_webhook_url))
scheduled_minutes: "60"
team_name: "main"
text_file_name: "Current-Unprotected-Report.csv"
slack_username: ""
slack_icon_emoji: ""
```

3) Place unique sensitive information into Vault.
   * An example of how you would reference the vault vales are as follows:
 ```
   $user = (get-childitem -path env:\VSPHERE_USERNAME).value
   $password = (get-childitem -path env:\VSPHERE_PASSWORD).value
```

## Environment Variables





The service dynamic pipeline builder is expecting a templatized version of your pipeline file
(pipeline.yml.tmpl)

