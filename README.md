firefox
=========

Installs and configures firefox for the user

Role Variables
--------------

The default variable values below are sourced from a fresh installation of Firefox.
It is recommended to set your own values as variables as shown in the Example Playbook below.

| Name | Type | Description | Default |
| ---- | ---- | ----------- | ------- |
| prevent\_default\_download\_pdf | string | A lowercase boolean value (true or false) to state whether PDFs should be prevented from automatically downloaded when opened in the browser. | "false" |
| remove\_close\_button\_from\_tabs | string | A lowercase boolean value (true or false) to state wether the close button should be enabled on tabs. | "false" |
| toolbar\_bookmark\_visibility | string | A lowercase value in double-quotes of ["always", "newtab", "never"] to state when the bookmarks toolbar should be visible. | '"always"' |
| startup\_page\_option | integer | A value of 0-2 to state what page your browser loads on startup, where 0 is a blank homepage, 1 is your homepage, and 2 is your last viewed page. | 1 |

Example Playbook
----------------

This example playbook shows how I would use this role, with custom variables to suit my needs.

```yaml
- hosts: localhost

  tasks:
    - name: Configure Firefox
      ansible.builtin.import_role:
        name: whalej84.firefox
      vars:
        prevent_default_download_pdf: "true"
        remove_close_button_from_tabs: "true"
        toolbar_bookmark_visibility: '"newtab"'
```
