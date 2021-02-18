This repository contains a role that dispatches incoming GitHub webhooks
to playbooks provided by the caller.  To use this, create a top level
playbook like:

```
---
- name: Call webhook role
  hosts: localhost
  gather_facts: false
  roles:
    - role: github_webhook
      vars:
        check_tasks:
          - "github_check.yml"
        deploy_tasks:
          - "github_check.yml"
          - "github_deploy.yml"
```

The check tasks will be run on pull request, and the deploy tasks will be
run on merge.
