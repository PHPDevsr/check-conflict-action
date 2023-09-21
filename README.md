# Check signed commits in PR

A GitHub Action that checks the Pull Request with conflict branch, labeling custom conflict and also places a comment in the PR to inform the author about next steps.

## Usage

```yml
name: Check Conflict in PR 
on:
  schedule:
    - cron: '0 */8 * * *' # Run at every 8 hours

jobs:
  build:
    name: Check conflict branch in PR
    permissions:
      contents: read
      pull-requests: write
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Check conflict branch in PR
        uses: PHPDevsr/check-conflict-action@v1
        with:
          token: ${{ secrets.GITHUB_TOKEN }}
          label: Conflicts
```

## Change PR Comment

The comment that will be placed in the PR upon detecting conflict branch can be changed using the `comment` field:

```yml
- name: Check conflict branch in PR
  uses: PHPDevsr/check-conflict-action@v1
  with:
    comment: |
      Customized comment in the PR
```

## Change PR Label

The comment that will be placed in the PR upon detecting conflict branch can be changed using the `comment` field:

```yml
- name: Check conflict branch in PR
  uses: PHPDevsr/check-conflict-action@v1
  with:
    label: CustomizedLabel
```