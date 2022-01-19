# GreenFrame CLI action

This action install the GreenFrame CLI and perform an analysis by using your configuration file.

![GreenFrame Documentation](https://docs.greenframe.io)

## Inputs

### `CONFIG_PATH`

The path to your config file. Default `./.greenframe.yml`.

## Environnement variable

### `GREENFRAME_SECRET_TOKEN`

You have to provide your `GREENFRAME_SECRET_TOKEN`. Do not paste it directly in your repository but use ![Github Encrypted Secrets](https://docs.github.com/en/actions/security-guides/encrypted-secrets#creating-encrypted-secrets-for-a-repository) instead.

## Example usage

Create a file: `.github/workflows/greenframe.yml`

```
on: [push]

jobs:
  greenframe_action_workflow:
    runs-on: ubuntu-latest
    name: Run a GreenFrame CLI Action
    steps:
      # To use this repository's private action,
      # you must check out the repository
      - name: Checkout
        uses: actions/checkout@v2
        with:
          fetch-depth: 0 # Fetch all the git history to enable git comparison
      - name: GreenFrame Analysis
        uses: actions/greenframe-action@v1
        env:
          GREENFRAME_SECRET_TOKEN: ${{secrets.GREENFRAME_SECRET_TOKEN}}
```
