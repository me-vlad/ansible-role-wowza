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

# Must be located on the file system with exec mount option!!!
wowza_install_workdir: "/root"

wowza_install_script: wowza_install_script.exp

# Wowza admin user
wowza_user: ""
# Wowza admin password
wowza_password: ""
# Wowza Streaming Engine license key
wowza_license_key: ""

# Wowza Streaming Engine default path variables
wowza_directory: "/usr/local/WowzaStreamingEngine"
wowza_config_directory: "{{ wowza_directory }}/conf"
wowza_manager_directory: "{{ wowza_directory }}/manager"
wowza_manager_counfig_directory: "{{ wowza_manager_directory }}/conf"
wowza_lib_directory: "{{ wowza_directory }}/lib"
wowza_log_directory: "/var/log/wowza"
wowza_systemd_include_dir: "/etc/systemd/system/WowzaStreamingEngine.service.d"
wowza_systemd_service_files:
  - "/usr/lib/systemd/system/WowzaStreamingEngine.service"
  - "/usr/lib/systemd/system/WowzaStreamingEngineManager.service"
wowza_uninstall_files:
  - "{{ wowza_directory }}/uninstall"
  - "{{ wowza_directory }}/Uninstall\ Wowza\ Streaming\ Engine.desktop"

wowza_license_file: "{{ wowza_config_directory }}/Server.license"
wowza_config_server: "{{ wowza_config_directory }}/Server.xml"
wowza_config_vhost: "{{ wowza_config_directory }}/VHost.xml"
wowza_config_vhosts: "{{ wowza_config_directory }}/VHosts.xml"
wowza_config_tune: "{{ wowza_config_directory }}/Tune.xml"
wowza_config_mediacache: "{{ wowza_config_directory }}/MediaCache.xml"
wowza_config_startup_streams: "{{ wowza_config_directory }}/StartupStreams.xml"
wowza_config_admin_password: "{{ wowza_config_directory }}/admin.password"
wowza_config_publish_password: "{{ wowza_config_directory }}/publish.password"
wowza_config_jmxremote_access: "{{ wowza_config_directory }}/jmxremote.access"
wowza_config_jmxremote_password: "{{ wowza_config_directory }}/jmxremote.password"
wowza_config_log4j: "{{ wowza_config_directory }}/log4j.properties"
wowza_manager_config_log4j: "{{ wowza_manager_counfig_directory }}/log4j.properties"
wowza_manager_config_tomcat_log4j: "{{ wowza_manager_counfig_directory }}/tomcat-log4j.properties"

wowza_config_files:
  - "{{ wowza_config_server }}"
  - "{{ wowza_config_vhost }}"
  - "{{ wowza_config_vhosts }}"
  - "{{ wowza_config_tune }}"
  - "{{ wowza_config_mediacache }}"
  - "{{ wowza_config_startup_streams }}"
  - "{{ wowza_config_admin_password }}"
  - "{{ wowza_config_publish_password }}"
  - "{{ wowza_config_jmxremote_access }}"
  - "{{ wowza_config_jmxremote_password }}"
  - "{{ wowza_config_log4j }}"
  - "{{ wowza_manager_config_log4j }}"
  - "{{ wowza_manager_config_tomcat_log4j }}"

# Wowza Streaming Engine configs with sensitive data
wowza_config_secret_files:
  - "{{ wowza_license_file }}"
  - "{{ wowza_config_admin_password }}"
  - "{{ wowza_config_publish_password }}"
  - "{{ wowza_config_jmxremote_access }}"
  - "{{ wowza_config_jmxremote_password }}"
  - "{{ wowza_config_mediacache }}"

# Defaul AuthenticationMethod for HTTP Providers and WSE Manager
# none, admin-basic, admin-digest, admin-file-digest
wowza_auth_method: admin-digest
# Defaul AuthenticationMethod for REST API
# none, basic, digest, remotehttp, digestfile
wowza_rest_auth_method: digest

# Production or Development or custom size e.g. 8000M
wowza_tuning_heapsize: Development
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
