firefox
=========

Installs and configures firefox for the user

Requirements
------------

This role has no requirements.
To include this role in your `requirements.yml` file, add the following list item:

```yaml
---
roles:
  - name: whalej84.firefox
    src: https://github.com/WhaleJ84/ansible-role-firefox.git
    scm: git
```

Role Variables
--------------

The default variable values below are sourced from a fresh installation of Firefox.
It is recommended to set your own values as variables as shown in the Example Playbook below.

| Name | Type | Description | Default |
| ---- | ---- | ----------- | ------- |
| prevent\_default\_download\_pdf | string | A lowercase boolean value [true, false] to state whether PDFs should be prevented from automatically downloaded when opened in the browser. | "false" |
| remove\_close\_button\_from\_tabs | string | A lowercase boolean value [true, false] to state wether the close button should be enabled on tabs. | "false" |
| toolbar\_bookmark\_visibility | string | A lowercase value of [always, newtab, never] to state when the bookmarks toolbar should be visible. | "always" |
| startup\_page\_option | integer | A value of [0, 1, 3] to state what page your browser loads on startup, where 0 is a blank homepage, 1 is your homepage, and 3 is your last viewed page. | 1 |
| startup\_homepage | string | A URL for the homepage to load when a new tab is opened. **NOTE:** `startup_page_option` must be **1** for this to apply. | |
| allow\_health\_reporting | string | A lowercase boolean value [true, false] to state whether to allow Firefox to report health telemetry | "true" |
| allow\_study\_reporting | string | A lowercase boolean value [true, false] to state whether to allow Firefox to report study telemetry | "true" |
| load\_new\_tab\_in\_background | string | A lowercase boolean value [true, false] to state whether new tabs will be switched to immedately. | "true" |
| typeaheadfind\_sound\_enabled | string | A lowercase boolean value [true, false] to state whether a sound will play when there is no find result. | "true" |
| ask\_save\_passwords | string | A lowercase boolean value [true, false] to state whether the browser should prompt to save a password once entered. | "true" |
| ask\_use\_location | integer | A value of [0, 1, 2] to state whether the browser should prompt to use your location, where 0 is default, 1 is yes, and 2 is no. | 0 |
| ask\_use\_camera | integer | A value of [0, 1, 2] to state whether the browser should prompt to use your camera, where 0 is default, 1 is yes, and 2 is no. | 0 |
| ask\_use\_microphone | integer | A value of [0, 1, 2] to state whether the browser should prompt to use your microphone, where 0 is default, 1 is yes, and 2 is no. | 0 |
| ask\_notify\_desktop | integer | A value of [0, 1, 2] to state whether the browser should prompt to notify via the desktop, where 0 is default, 1 is yes, and 2 is no. | 0 |
| do\_not\_track | string | A lowercase boolean value [true, false] to state whether you want DNT headers to be included | "false" |
| global\_privacy\_control | string | A lowercase boolean value [true, false] to state whether you want GPC headers to be included | "false" |
| recommended\_stories | string | A lowercase boolean value [true, false] to state whether you want recommended stories shown on new tab pages | "true" |
| sponsored\_shortcuts | string | A lowercase boolean value [true, false] to state whether you want sponsored shortcuts shown on new tab pages | "true" |
| browser\_extensions | list | A list containing entries of 'id' and 'url' values for any browser extensions you wish to be installed. See example below. | [] |

Example Playbook
----------------

This example playbook shows how I would use this role, with custom variables to suit my needs.

```yaml
---
- hosts: localhost

  roles:
    - role: whalej84.firefox
      vars:
        prevent_default_download_pdf: "true"
        remove_close_button_from_tabs: "true"
        toolbar_bookmark_visibility: "newtab"
        startup_page_option: 0
        allow_health_reporting: "false"
        allow_study_reporting: "false"
        load_new_tab_in_background: "false"
        typeaheadfind_sound_enabled: "false"
        ask_save_passwords: "false"
        ask_use_location: 2
        ask_use_camera: 2
        ask_use_microphone: 2
        ask_notify_desktop: 2
        do_not_track: "true"
        global_privacy_control: "true"
        recommended_stories: "false"
        sponsored_shortcuts: "false"
        vertical_tabs: "true"
        browser_extensions:
          - id: uBlock0@raymondhill.net
            url: https://addons.mozilla.org/firefox/downloads/file/4290466/ublock_origin-latest.xpi
          - id: keepassxc-browser@keepassxc.org
            url: https://addons.mozilla.org/firefox/downloads/file/4285762/keepassxc_browser-latest.xpi
      tags: [ firefox ]
```

Notes
-----

- The default search engine cannot be configured via `user.js` at the time of 05/01/2024 and must be configured manually

