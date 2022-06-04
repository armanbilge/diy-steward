# diy-steward
Set up your very own Scala Steward!

1. Use this template to create a new repo.
2. Create a new GitHub App.
    - Personal app: https://github.com/settings/apps/new
    - Org app: `https://github.com/organizations/[your-org]/settings/apps/new`
3. You can disable the Webhook and set the App homepage to your new repo.
4. Grant the App the following permissions:
    - Actions: Read-only
    - Contents: Read and write
    - Metadata: Read-only
    - Pull requests: Read and write
    - Workflows: Read and write (this is required to support the sbt-github-actions plugin)
5. Create the app. Note the app ID, we will need it later.
6. Generate and download an App private key.
7. Install the app on your repos. It _must_ be installed in this repo and it should also be installed on any repo you want steward updates on.
    - Personal: `https://github.com/settings/apps/[your-app-name]/installations`
    - Org: `https://github.com/organizations/[your-org]/settings/apps/[your-app-name]/installations`
8. In this repo, set the secret `APP_PRIVATE_KEY` to the contents of the private key you downloaded.
9. Finally, edit [`.github/workflows/steward.yml`](.github/workflows/steward.yml):
    - Replace the 3 instances of `123456` with your app ID (see also [#1](https://github.com/armanbilge/diy-steward/issues/1))
    - Replace the 2 instances of `your-app-name` with your app's name.
    - Tweak the scheduling as you see fit. Default is ["At minute 0 past every 4th hour."](https://crontab.guru/#0_*/4_*_*_*)
10. That's it! To manually trigger your new steward, navigate to the Actions tab on this repo, select the Scala Steward workflow, and click "Run Workflow".

Please open issues or PRs with any improvements and fixes for this template. Thank you!
