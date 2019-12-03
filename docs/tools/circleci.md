# CircleCI

# FAQ

## Excluding a branch from CI

Use workflow to ignore branches

```yml
workflows:
  deploy: # workflow label
    jobs:
      - deploy: #job name
          filters:
            branches:
              ignore:
                - gh-pages # branch name to ignore
```

You can restrict CI to a particular using `only` filter

```yml
workflows:
  deploy: # workflow label
    jobs:
      - deploy: #job name
          filters:
            branches:
              only: gh-pages # branch name to ignore
```

If it is not possible to create `.circleci/config.yaml` in this branch, you can enable `Only build pull requests` from project config in CircleCI. For your default branch and tags, it will always build all commits
