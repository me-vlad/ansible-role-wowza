# ansible-wowza

Ansible role to install [Wowza Streaming Engine](https://www.wowza.com/products/streaming-engine) on Linux.

## Idempotence note

Please note: checking for already installed on the server Wowza Streaming Engine realised by determining status of the Wowza license file which installed by default to the /usr/local/WowzaStreamingEngine/conf/Server.license path.

## Requirements

Requirements are listed in the role metadata.

## Role Variables

### Default role variables

``` yaml
wowza_download_path: "https://www.wowza.com/downloads/WowzaStreamingEngine-4-8-0/"
wowza_installer: "WowzaStreamingEngine-4.8.0-linux-x64-installer.run"
wowza_installer_checksum: "sha1:09a0f7d6ae3f420e001ea2195f75dd1e5cd6d44a"

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
