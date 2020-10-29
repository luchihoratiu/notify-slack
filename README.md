# notify-via-slack
A GitHub Action that notifies you via Slack the result of your GitHub Actions workflow

## Features
It works with Ubuntu, macOS and Windows runners.

## Usage example
```yaml
  notify-via-slack:
    name: Notify workflow conclusion via Slack
    if: ${{ always() }}
    needs: MY_OTHER_JOB_NAMES_GO_HERE
    runs-on: 'ubuntu-latest'
    steps:
      - uses: luchihoratiu/notify-via-slack@main
        with:
          SLACK_CHANNEL: ${{ secrets.SLACK_CHANNEL }}
          SLACK_WEBHOOK_URL: ${{ secrets.SLACK_WEBHOOK_URL }}
```

## Settings
### Mandatory
* **SLACK_CHANNEL** - The name of the Slack channel on which you want to be notified (without the #).
* **SLACK_WEBHOOK_URL** - The URL provided by the [Slack Webhook integration](https://puppet.slack.com/apps/A0F7XDUAZ).
