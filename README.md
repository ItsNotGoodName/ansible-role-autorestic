# ansible-role-autorestic

This role installs and configures [autorestic](https://github.com/cupcakearmy/autorestic) and [restic](https://github.com/restic/restic).

## Features
- Install autorestic from GitHub
- Install restic from GitHub
- Copy autorestic configuration to home directory
- Add `autorestic --ci cron` to cron

## Role Variables

Autorestic configuration is copied to `root` user's home directory by default. 
It can be changed to another user's home directory with the `autorestic_user` variable. 

You can toggle installing autorestic and restic by setting `autorestic_install` and `autorestic_restic_install` to `true` or `false`.

### Required

Cron package installed for your distribution or disable cron by setting `autorestic_cron` to `false`.

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

## License

MIT
