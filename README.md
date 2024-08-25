# boinc-debian-client-machines-manager

Ansible playbooks for managing multiple Debian based remote machines running BOINC clients

## Server Initializer

This guide assumes you have already configured server connection and authentication. For more details about connecting Ansible to your server, see the [Ansible docs](https://docs.ansible.com/ansible/latest/getting_started/get_started_inventory.html).

The initializer playbook in this repository can help you to upgrade apt packerages on a server and then install the [BOINC](https://boinc.berkeley.edu/wiki/User_manual) client with attaching one of the [BOINC projects](https://boinc.berkeley.edu/projects.php).

Be aware that the playbook will reboot your server to get everything effective.

You would need to configure `BOINC_PROJECT_URL` and `BOINC_PROJECT_KEY` environmental variables

```bash
export BOINC_PROJECT_URL=https://numberfields.asu.edu/NumberFields/
export BOINC_PROJECT_KEY=<MY_KEY>
```

Alternatively, you can pass in `boinc_project_url` and `boinc_project_key` variables to Ansible directly

```bash
ansible-playbook ./machine-initializer.yaml --extra-vars "boinc_project_url=https://numberfields.asu.edu/NumberFields/ boinc_project_key=<MY_KEY>"
```

## Server Updater

This playbook simply upgrade all apt packages on your server and reboot the server if a kernel update needs a reboot to be effective.

```bash
ansible-playbook ./machine-updater.yaml
```
