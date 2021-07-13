# ansible-role-autorestic

This roles install autorestic and restic from github. 

## Features

### Main
- Install restic via github
- Install autorestic via github

### Optional
- Copy over autorestic configuration

## Role Variables

### Optional
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
- Run `autorestic check` with a tag

## License

MIT
