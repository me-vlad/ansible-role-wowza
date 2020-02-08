# ansible-wowza

Ansible role to install [Wowza Streaming Engine](https://www.wowza.com/products/streaming-engine) on Linux.

## Requirements

Requirements are listed in the role metadata.

## Role Variables

### Default role variables

``` yaml
wowza_download_path: "https://www.wowza.com/downloads/WowzaStreamingEngine-4-7-8/"
wowza_installer: "WowzaStreamingEngine-4.7.8-linux-x64-installer.run"
wowza_installer_checksum: "sha1:8088072198a5dec188b34fcdac375f7a39a29028"

# Wowza admin user
wowza_user: ""
# Wowza admin password
wowza_password: ""
# Wowza Streaming Engine license key
wowza_license_key: ""

# Must be located on the file system with exec mount option!!!
wowza_install_workdir: "/root"
```

## Ansible Galaxy

ansible-galaxy install me_vlad.wowza


## Example Playbook

``` yaml
- hosts: mediaservers
  roles:
    - me_vlad.wowza
```

## License

MIT

## Author Information

Vlad V. Teteria

