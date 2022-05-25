# ansible-role-autorestic

Install and configure [autorestic](https://github.com/cupcakearmy/autorestic) and [restic](https://github.com/restic/restic).

## Features

- Install autorestic from GitHub
- Install restic from GitHub
- Copy autorestic configuration to home directory
- Add autorestic cron job, requires cron to be installed and `autorestic_cron` has to be `true`
- Run autorestic check with `autorestic_check` tag

## Role Variables

Set the autorestic configuration with the `autorestic_config` variable.

Autorestic configuration is copied to `root` user's home directory by default.
It can be changed to another user's home directory with the `autorestic_user` variable.

Enable cron by setting the `autorestic_cron` variable to `true`.

The `autorestic_user_home` variable is set in the role using `ansible.builtin.set_fact` task.

The versions can be changed by setting the `autorestic_download_version` and `autorestic_restic_download_version` variables.

The `autorestic_download_checksum` and `autorestic_restic_download_checksum` can optionally be set to verify your downloads.

### Required

None

### Optional

Example autorestic config.

```yaml
autorestic_config:
  locations:
    home:
      from: "{{ autorestic_user_home }}"
      to: local
  backends:
    local:
      type: local
      path: /backup
      key: 123
```

## To Do

## License

MIT
