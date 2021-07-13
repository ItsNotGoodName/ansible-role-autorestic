# ansible-role-autorestic

This role installs autorestic and restic from their Github repositories. 

## Features

- Install autorestic via github
- Install restic via github
- Copy over autorestic configuration

## Role Variables

It assumes that the user `root` is handling backups and can be changed with the `autorestic_user` variable. 

You can toggle installing autorestic and restic by setting `autorestic_autorestic_install` and `autorestic_restic_install` to `true` or `false`.

### Required

None

### Optional
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

- Cronjobs
- Run `autorestic check` with a tag

## License

MIT
