# gcb_slack
Slack Notification for Google Cloud build


### Configuring Slack Notifications for Google Cloud Build


#### Prepare your Slack App

I assume you have Slack installed and that you have created and signed-in to your account.

Create a [new Slack app](https://api.slack.com/apps?new_app=1):

1. Choose the app’s name and your Slack team. Click Create.
2. Click Incoming Webhooks.
3. Activate incoming webhooks.
4. Click Add New Webhook to Workspace. An authorization page opens.
5. From the drop-down menu, select the channel to which you would like notifications sent.
6. Click Authorize.
7. A webhook for your Slack application has been created. Copy the webhook URL and save it for later use.


### Deploy the Cloud Function

**Note : Pass the right values for these Variables while creating the function**

* SLACK_WEBHOOK_URL : slack webhook which created before
* GH_ORG_NAME : GitHub organisation name
* GH_REPO_NAME : List of GitHub repository name (separated by ' ' {space}) --> for python code

## python
```shell
gcloud functions deploy subscribeSlack \
    --source=./python \
    --runtime=python38 \
    --trigger-topic cloud-builds \
    --set-env-vars SLACK_WEBHOOK_URL="https://hooks.slack.com/services/something",GH_ORG_NAME="akhilrajmailbox",GH_REPO_NAME="repo1 repo2 gcp-cicd-sample"
```

## nodejs
```shell
gcloud functions deploy subscribeSlack \
    --source=./node \
    --runtime=node8 \
    --trigger-topic cloud-builds \
    --set-env-vars SLACK_WEBHOOK_URL="https://hooks.slack.com/services/something",GH_ORG_NAME="akhilrajmailbox",GH_REPO_NAME="gcp-cicd-sample"
```

[gcb_slack_base](https://mehmandarov.com/slack-notifications-for-cloud-build/)

[gcb_slack_adv](https://amperon.co/blog/better-gcb-notifications-slack/)

