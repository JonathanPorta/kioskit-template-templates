# kioskit-template-templates

Starter **templates repo** for [Kioskit](https://kioskit.io), reusable device configs.

## Setup

1. Click **Use this template** to create your own copy.
2. Connect it as your templates repo in the Kioskit console.

## How it works

Each folder under `templates/` is one device config. When you claim a device, Kioskit
renders the template you pick into your state repo as a PR.

```
templates/menu-board/
  kioskit.yaml          # which files go where on the device
  files/                # file contents, mirroring their device paths
```

`menu-board` is a rotating wallboard for FullPageOS. Edit its `urls.json` to list your
own pages.

## Adding a template

1. Copy `templates/menu-board/` to `templates/<name>/`.
2. List each file in `kioskit.yaml` under `apply.files[]` with its `target`, `mode`,
   `owner` and `group`.
3. Put the contents under `files/`, at the same path as on the device.

Only `{{display_name}}`, `{{primary_mac}}` and `{{hostname}}` are substituted. Commands
and secrets aren't allowed.
