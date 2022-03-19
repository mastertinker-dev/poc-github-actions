# Scenarios

## 1. On push to `main`

If you uncomment lines 5 and 6 in `simple.yml` file, any push to `main` or `tmp` branches will trigger the workflow called `Simple Triggers`. Example with an empty commit:
```bash
git commit -m "trigger" --allow-empty
git push
```


## 2. Trigger manually

Also, `Simple Triggers` workflow can be triggered manually here: https://github.com/makar2/poc-github-actions/actions


## 3. Cron job

`Simple Triggers` workflow has a cron job to run at noon UTC every work day, but it's commented out.


## 4. Preparations with the help of composite actions
TODO


## 5. Caching
TODO


## 6. On PR Trigger `workflow_call` from this repo and from another repo
TODO
