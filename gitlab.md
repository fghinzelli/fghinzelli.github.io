# Utils gitlab-rake commands

```bash
# Verify ldap status
gitlab-rake gitlab:ldap:check

```

## Logs
```bash
# Tail all logs; press Ctrl-C to exit
gitlab-ctl tail

# Drill down to a sub-directory of /var/log/gitlab
gitlab-ctl tail gitlab-rails

# Drill down to an individual file
gitlab-ctl tail nginx/gitlab_error.log
gitlab-ctl tail gitlab-rails/application_json.log
```
