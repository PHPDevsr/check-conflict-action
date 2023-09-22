# Check signed commits in PR

A GitHub Action that checks the Pull Request with conflict branch, labeling custom conflict and also places a comment in the PR to inform the author about next steps.

## Usage

```yml
name: Check Conflict in PR 
on:
  schedule:
    - cron: '*/20 * * * *' # Run at every 20 minutes

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

For note: `The shortest interval you can run scheduled workflows is once every 5 minutes.`

See https://docs.github.com/en/actions/using-workflows/events-that-trigger-workflows#schedule

## Change PR Comment

The comment that will be placed in the PR upon detecting conflict branch can be changed using the `comment` field:

```yml
- name: Check conflict branch in PR
  uses: PHPDevsr/check-conflict-action@v1
  with:
    comment: |
      Customized comment in the PR
```

If you need tagged the author, you can use `authorTarget` magic get author in PR

## Change PR Label

The comment that will be placed in the PR upon detecting conflict branch can be changed using the `comment` field:

```yml
- name: Check conflict branch in PR
  uses: PHPDevsr/check-conflict-action@v1
  with:
    label: CustomizedLabel
```
