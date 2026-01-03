# ansible-role-sudo

Configure sudo access for users and groups.

## Requirements

- Debian/Ubuntu

## Role Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `sudo_users` | `[]` | List of users with sudo access |
| `sudo_groups` | `[]` | List of groups with sudo access |
| `sudo_remove_users` | `[]` | Users to remove from sudoers |
| `sudo_remove_groups` | `[]` | Groups to remove from sudoers |

### User/Group structure

```yaml
sudo_users:
  - name: username
    nopasswd: true          # optional, default false
    commands: ALL           # optional, default ALL

sudo_groups:
  - name: groupname
    nopasswd: false
    commands: ALL
```

## Examples

### User with passwordless sudo

```yaml
sudo_users:
  - name: deploy
    nopasswd: true
```

### User with password required

```yaml
sudo_users:
  - name: developer
    nopasswd: false
```

### Limited commands

```yaml
sudo_users:
  - name: deployer
    nopasswd: true
    commands: "/usr/bin/systemctl restart nginx, /usr/bin/docker"
```

### Group sudo access

```yaml
sudo_groups:
  - name: devops
    nopasswd: true
    commands: ALL
```

### Remove sudo access

```yaml
sudo_remove_users:
  - olduser

sudo_remove_groups:
  - oldgroup
```

## License

MIT
