# ansible-role-autorestic

This roles install autorestic and restic on a Debian 10 system.
It also can copy over autorestic conf file and your ssh keys.
This may work on other systems that have the restic package in their repo.

## Role Variables

```
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

## License

MIT
