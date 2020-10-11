# GitLab pipeline monitor shell script

## Instructions

1. Copy `pipeline-monitor.env.example` to `pipeline-monitor.env`
2. Edit `pipeline-monitor.env` with your details:
   - you'll need a [GitLab api access token](https://docs.gitlab.com/ee/user/profile/personal_access_tokens.html#creating-a-personal-access-token)
   - change the `projects` array to contain the ids of the GitLab projects whose
     pipelines you want to monitor
3. Execute with `./pipeline-monitor`. If the most recent pipeline of any of the
   projects failed, you will get a notification letting you know.

Obviously don't commit your GitLab access token to this repo. For this reason,
`pipeline-monitor.env` is protected in `.gitignore`.

## Scheduling

This script can be run as a cron job. E.g. adding this line to your crontab will
run it every 15 minutes from 9am-6pm, Monday to Friday:
```
*/15 9-18 * * 1-5 /full/path/to/pipeline-monitor
```

## Dependencies

- `jq`: for parsing json
- `notify-send`: tool to display desktop notifications. Available in Ubuntu,
  and possibly other Linux distros
