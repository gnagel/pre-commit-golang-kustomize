# pre-commit-kustomize
Pre-commit hook for running kustomize from your native system


## Example of .pre-commit-config.yaml that verifies that 3 overlays are not broken
```yaml
# See https://pre-commit.com for more information
# See https://pre-commit.com/hooks.html for more hooks
repos:
-   repo: https://github.com/pre-commit/pre-commit-hooks
    rev: v2.4.0
    hooks:
    -   id: check-yaml
        args: [--allow-multiple-documents]
    -   id: check-added-large-files
-   repo: https://github.com/gnagel/pre-commit-kustomize
    rev: master
    hooks:
    -   id: kustomize
        name: kustomize-development
        args: [overlays/development]
        verbose: false
    -   id: kustomize
        name: kustomize-staging
        args: [overlays/staging]
        verbose: false
    -   id: kustomize
        name: kustomize-production
        args: [overlays/production]
        verbose: false
