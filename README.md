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

Trigger `Cache with Composite` workflow here: https://github.com/makar2/poc-github-actions/actions

The workflow will use the `prep` composite action, which in its turn uses `cache`.


## 5. Caching

*How it works:*

1. When GitHub's `cache` action is called it checks for an existing cache first. It tries to find one by the key (name) given to it on the last line of `.github/utils/cache/action.yml` file.
1. If cache is hit, the step called `Install dependencies` is skipped due to the latter's `if` condition.
1. If cache is not hit:
    1. `Install dependencies` does happen.
    1. In the `Post ...` stage caching works again and dependencies get cached. Therefore, there is no need to have caching step duplicated after `Install dependencies` step.
    1. Consequent jobs (`job-1` in this case) will be able to benefit from those cached dependencies.


## 6. Trigger `workflow_call` from this repo and from another repo

`Caller` workflow can be triggered both manually and through a PR. It has 2 steps -- one internally and one from [this other repo](https://github.com/makar2/for-poc-github-actions). Checking the status demonstrates which repo's data it is running on.
