# ansible-role-autorestic

Install and configure [autorestic](https://github.com/cupcakearmy/autorestic) and [restic](https://github.com/restic/restic).

## Features

- Install autorestic from GitHub
- Install restic from GitHub
- Copy autorestic configuration to home directory
- Add autorestic cron job, requires cron to be installed and `autorestic_cron` has to be `true`

## Role Variables

Set the autorestic configuration with the `autorestic_config` variable.

Autorestic configuration is copied to `root` user's home directory by default.
It can be changed to another user's home directory with the `autorestic_user` variable.

Enable cron by setting the `autorestic_cron` variable to `True`.

The `autorestic_user_directory` variable is set in the role using `set_fact` task.

The `autorestic_download_checksum` and `autorestic_restic_download_checksum` can be optionally set to verify your autorestic and restic downloads.

### Required

None

### Optional

Example autorestic config.

```yaml
autorestic_config:
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
