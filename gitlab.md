# Utils gitlab-rake commands

```bash
# Verify ldap status
gitlab-rake gitlab:ldap:check

```

## Logs
```bash
# Tail all logs; press Ctrl-C to exit
sudo gitlab-ctl tail

# Drill down to a sub-directory of /var/log/gitlab
sudo gitlab-ctl tail gitlab-rails

# Drill down to an individual file
sudo gitlab-ctl tail nginx/gitlab_error.log
```
