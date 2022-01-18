# notify-via-slack
A GitHub Action that notifies you via Slack the conclusion of your GitHub Actions workflow

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
Add above example at the end of your workflow and ensure all jobs before it (or only the last one if they are all already chained) are added to the `needs` field to work correctly. Optional settings are described below.

## Settings
### Mandatory
* **SLACK_CHANNEL** - The name of the Slack channel on which you want to be notified (with the #).
* **SLACK_WEBHOOK_URL** - The URL provided by the [Slack Webhook integration](https://puppet.slack.com/apps/A0F7XDUAZ).
### Optional
* **NOTIFY_ONLY_ON_CONCLUSION_CHANGE** - Set this to 'true' to send notification only when conclusion of current run differs from previous run to avoid spam.
* **EXTRA_INFORMATION** - Add here custom information to be printed besides the standard template

