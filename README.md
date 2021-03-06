# GitLab pipeline monitor shell script

## Instructions

1. Copy `.env.example` to `.env`
2. Edit `.env` with your details:
   - you'll need a [GitLab api access token](https://docs.gitlab.com/ee/user/profile/personal_access_tokens.html#creating-a-personal-access-token)
   - change the `projects` array to contain the ids of the GitLab projects whose
     pipelines you want to monitor. You can find them under the name of the
     project on the project's page on the GitLab website.
3. Execute with `./pipeline-monitor`. If the most recent pipeline of any of the
   projects failed, you will get a notification letting you know.

Obviously don't commit your GitLab access token to this repo. For this reason,
`*.env` is protected in `.gitignore`.

## Dependencies

- `jq`: for parsing json
- `notify-send`: tool to display desktop notifications. Available in Ubuntu
  (installed by default?), and possibly other Linux distros

## Scheduling

This script can be run as a cron job. E.g. adding this line to your crontab
(edit your crontab with `crontab -e`) will run it every 15 minutes from 9am-6pm,
Monday to Friday:

```
*/15 9-17 * * 1-5 /full/path/to/pipeline-monitor
```
