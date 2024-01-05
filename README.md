firefox
=========

Installs and configures firefox for the user

Role Variables
--------------

| Name | Type | Description | Default |
| ---- | ---- | ----------- | ------- |
| prevent\_default\_download\_pdf | string | A lowercase boolean value (true or false) to state whether PDFs should be prevented from automatically downloaded when opened in the browser. | "false" |
| remove\_close\_button\_from\_tabs | string | A lowercase boolean value (true or false) to state wether the close button should be enabled on tabs. | "false" |

Example Playbook
----------------

```yaml
- hosts: localhost

  tasks:
    - name: Configure Firefox
      ansible.builtin.import_role:
        name: whalej84.firefox
      vars:
        prevent_default_download_pdf: "true"
        remove_close_button_from_tabs: "true"
```
