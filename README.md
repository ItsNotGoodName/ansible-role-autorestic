# ansible-role-autorestic

This role installs and configures [autorestic](https://github.com/cupcakearmy/autorestic) and [restic](https://github.com/restic/restic).

## Features
- Install autorestic from GitHub
- Install restic from GitHub
- Copy autorestic configuration to home directory
- Add autorestic cron job, requires cron to be installed

## Role Variables

Set the autorestic configuration with the `autorestic_config_yaml` variable.

Autorestic configuration is copied to `root` user's home directory by default. 
It can be changed to another user's home directory with the `autorestic_user` variable. 

Disable cron by setting the `autorestic_cron` variable to `false`.

The `autorestic_user_directory` variable is set in the role using `set_fact` task.

The `autorestic_download_checksum ` and `autorestic_restic_download_checksum` can be optionally set to verify your autorestic and restic downloads.

### Required

None

### Optional

Example autorestic config.

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

## Todo

- Run `autorestic check` with a tag
- Run restic forget and prune on a schedule

## License

MIT
