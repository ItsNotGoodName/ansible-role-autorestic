# ansible-role-autorestic

This role installs and configures autorestic and restic from their Github repositories.

## Features

- Install autorestic via github
- Install restic via github
- Copy over autorestic configuration
- Setup cronjobs

## Role Variables

It assumes that the user `root` is handling backups but can be changed using the `autorestic_user` variable.

You can toggle installing autorestic and restic by setting `autorestic_autorestic_install` and `autorestic_restic_install` to `true` or `false`.

You can enable cron by setting `autorestic_cron_enable` to `true`.

### Required

None

### Optional

Example configure `.autorestic.yml` file.
```yaml
autorestic_config_yaml:
  locations:
    home:
      from: "{{ autorestic_user_directory }}"
      to: local
  backends:
    local:
      type: local
      path: /backup
      key: 123
```

Example backup every day and forget every week using cron.
```yaml
autorestic_cron_enable: true

autorestic_cron_daily: |
  #!/bin/bash
  su {{ autorestic_user }} -c "{{ autorestic_install_directory }}/{{ autorestic_install_binary }} backup -a --ci -c {{ autorestic_config_path }}"

autorestic_cron_weekly: |
  #!/bin/bash
  su {{ autorestic_user }} -c "{{ autorestic_install_directory }}/{{ autorestic_install_binary }} forget -a --ci -c {{ autorestic_config_path }}"
```

## Todo

- Run `autorestic check` with a tag
- Always run remove cron tasks
## License

MIT
