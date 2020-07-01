# Dynamic Script Pipelines Service

This repo is designed to dynamically build pipelines for Concourse to execute
scripts and push the output to resources such as email, slack, ect...

## How to use:
1) Create a new Git hub repo with the following naming convention:
   "script_pipeline_<your_unique_name_here>"
2) Your new repo should contain the following:
   * Your Python or PowerShell script
   * A vars.yml file that is build using the vars.example from the repo.
```
---
repo_branch: "master"
slack_webhook_url: ((web_hook))
scheduled_minutes: "120"
```





The service dynamic pipeline builder is expecting a templatized version of your pipeline file
(pipeline.yml.tmpl)
