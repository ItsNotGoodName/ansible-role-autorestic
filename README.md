# ansible-role-autorestic

This roles install autorestic and restic on Debian 10. 
It may work on other systems that have the restic package in their repository.

## Features

### Main
- Install restic via system package manager
- Install autorestic via github

### Optional
- Copy over private and public ssh key
- Copy over autorestic configuration

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
- Install restic via github
- Use `ansible` ssh key with autorestic
- Run `autorestic check` with a tag
- Refactor config and key paths/users

## License

MIT
