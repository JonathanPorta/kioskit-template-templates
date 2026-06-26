# kioskit-template-templates

Starter **template repository** for [Kioskit](https://kioskit.io). Create your own
copy from this one with GitHub's **"Use this template"** button, then connect it as
your *template repo* in the Kioskit console.

## What's in here

Each directory under `templates/` is one reusable device config. Kioskit copies one
into a device when you claim it, rendering it to `src/devices/<mac>/` in your **state
repo** as a pull request.

```
templates/
  menu-board/
    kioskit.yaml                              # manifest — what files go where on the device
    files/
      var/www/html/FullPageDashboard/urls.json  # the rotating list of pages
      etc/hostname                              # device hostname ({{hostname}} is filled in on claim)
```

## The `menu-board` template

A rotating menu/wallboard for Raspberry Pis running **FullPageOS + FullPageDashboard**.
Edit `urls.json` to point at your own pages. On claim, Kioskit writes:

| Source (in this repo)                            | Target (on the device)                       |
| ------------------------------------------------ | -------------------------------------------- |
| `files/var/www/html/FullPageDashboard/urls.json` | `/var/www/html/FullPageDashboard/urls.json`  |
| `files/etc/hostname`                             | `/etc/hostname`                              |

## Adding your own template

1. Copy `templates/menu-board/` to `templates/<your-name>/`.
2. Edit `kioskit.yaml` — list every file under `apply.files[]` with its `target`,
   `mode`, `owner`, and `group`.
3. Put the file contents under `files/…`, mirroring their absolute device paths.

Only `{{display_name}}`, `{{primary_mac}}`, and `{{hostname}}` may be substituted.
No `exec`/`command`/`script`/`shell`/`secret` fields are allowed.
