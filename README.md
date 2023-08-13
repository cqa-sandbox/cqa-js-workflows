# CQA Reusable Workflows

This repository contains reusable workflows for our Code Sample Validation (CSV) and Code Quality Automation (CQA) related projects.

## Usage

 * Workflows are defined within the `.github/workflows` folder.

---

## About Reusable Workflows
GitHub Actions provides the capability to [reuse workflows](https://docs.github.com/en/actions/using-workflows/reusing-workflows) across projects for efficiency and consistency. 

* Reusable workflows are the _called_ workflows. 
* Workflows that use them are the _caller_ workflows.
    * A _caller_ can have multiple _called_ workflows 
    * Called workflows behave as though they were inline (part of the original caller workflow)
    * The `github` context gets associated with the _caller_ workflow.
    * The _called_ workflow gets seamless access to `github.token` and `secrets.GITHUB_TOKEN` for executing jobs within caller environment.
    * The _called_ workflow does **NOT** get access to `env` context defined at workflow level in the _caller_. To reuse variables, set them at {org, repo, or env} level and referene then using `vars` context.
 * You can call a maximum of **20 reusable workflows** from a caller workflow. Nested workflows count against this quota.

## About Starter Workflows

GitHub also has the capability to create [starter workflows](https://docs.github.com/en/actions/using-workflows/creating-starter-workflows-for-your-organization) that serve as baseline templates for your organization.

The primary difference is that _starter_ workflows help you `create` new workflows from a common base, while _reusable_ worflows help you `call` an existing workflow and run it inline with your current workflow as the runtime context.

You can reference a reusable workflow in a starter workflow as a way of making starters more _composable_ while centrally managing code.

---