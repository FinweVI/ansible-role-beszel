<!-- DOCSIBLE START -->

# 📃 Role overview

## ansible-role-beszel



Description: Ansible role to install and configure a Beszel binary hub and/or agent.


| Field                | Value           |
|--------------------- |-----------------|
| Readme update        | 16/07/2025 |








### Defaults

**These are static variables with lower priority**

#### File: defaults/main.yml

| Var          | Type         | Value       |
|--------------|--------------|-------------|
| [beszel_version](defaults/main.yml#L6)   | str | `latest` |    
| [beszel_user](defaults/main.yml#L8)   | str | `beszel` |    
| [beszel_agent_install](defaults/main.yml#L11)   | bool | `True` |    
| [beszel_agent_install_dir](defaults/main.yml#L13)   | str | `/opt/beszel-agent` |    
| [beszel_agent_port](defaults/main.yml#L15)   | int | `45876` |    
| [beszel_agent_args](defaults/main.yml#L17)   | str |  |    
| [beszel_agent_service_enabled](defaults/main.yml#L19)   | bool | `True` |    
| [beszel_agent_service_state](defaults/main.yml#L21)   | str | `started` |    
| [beszel_extra_filesystems](defaults/main.yml#L23)   | list | `[]` |    
| [beszel_public_key](defaults/main.yml#L25)   | str |  |    
| [beszel_hub_install](defaults/main.yml#L28)   | bool | `False` |    
| [beszel_hub_install_dir](defaults/main.yml#L30)   | str | `/opt/beszel` |    
| [beszel_hub_port](defaults/main.yml#L32)   | int | `8090` |    
| [beszel_hub_args](defaults/main.yml#L34)   | str |  |    
| [beszel_hub_service_enabled](defaults/main.yml#L36)   | bool | `True` |    
| [beszel_hub_service_state](defaults/main.yml#L38)   | str | `started` |    
| [beszel_hub_extra_env](defaults/main.yml#L40)   | dict | `{}` |    





### Tasks


#### File: tasks/agent.yml

| Name | Module | Has Conditions |
| ---- | ------ | -------------- |
| Load SSH Pub Key if it exists | ansible.builtin.slurp | True |
| Register local_public_key | ansible.builtin.set_fact | True |
| Assert beszel_public_key is set | ansible.builtin.assert | False |
| Determine Beszel binary agent architecture | ansible.builtin.set_fact | False |
| Download Beszel binary agent tarball | ansible.builtin.get_url | False |
| Extract Beszel binary agent tarball | ansible.builtin.unarchive | False |
| Install Beszel binary agent systemd service | ansible.builtin.template | False |
| Start the Beszel binary agent systemd service | ansible.builtin.service | False |

#### File: tasks/hub.yml

| Name | Module | Has Conditions |
| ---- | ------ | -------------- |
| Download Beszel binary hub tarball | ansible.builtin.get_url | False |
| Extract Beszel binary hub tarball | ansible.builtin.unarchive | False |
| Install Beszel binary hub systemd service | ansible.builtin.template | False |
| Start the Beszel binary hub systemd service | ansible.builtin.service | False |

#### File: tasks/main.yml

| Name | Module | Has Conditions | Tags |
| ---- | ------ | -------------- | -----|
| Determine Beszel binary agent architecture | ansible.builtin.set_fact | False |  |
| Ensure base-packages are installed | ansible.builtin.apt | False |  |
| Create user for Beszel | ansible.builtin.user | False |  |
| Include hub tasks | ansible.builtin.import_tasks | True | beszel-hub |
| Include agent tasks | ansible.builtin.import_tasks | True | beszel-agent |







## Author Information
finwevi

#### License

MIT

#### Minimum Ansible Version

2.17

#### Platforms

No platforms specified.

#### Dependencies

No dependencies specified.
<!-- DOCSIBLE END -->
