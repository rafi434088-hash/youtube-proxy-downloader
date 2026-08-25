# youtube-proxy-downloader

The clean, shareable distribution of the **YouTube Proxy** browser extension — no
tokens, no personal config. This repo is also the **update source**: installed copies
check it for a newer version and pull the code from here, while keeping each user's own
`config.js` (token / repo / cookie key) untouched.

## Install

1. Download this repo (Code → Download ZIP) and extract it, or `git clone`.
2. Copy `extension/config.example.js` to `extension/config.js` and fill in your GitHub
   details (see the setup instructions bundled with the extension, or `embed_token.py`
   in the main project).
3. `chrome://extensions` → Developer mode → **Load unpacked** → pick the `extension`
   folder.
4. To enable the in-extension **update now** button, run `install-updater.bat` once
   from inside the `extension` folder.

## How updates work

- The extension checks `extension/manifest.json` in this repo a few times a day and
  shows an "update available" banner when its `version` is newer than what's installed.
- Clicking **update now** triggers `update.bat` (via a native-messaging host registered
  by `install-updater.bat`), which downloads this repo and copies the new code over the
  installed folder — **never** touching `config.js` — then reloads the extension.
- `update.bat` also works on its own: double-click it any time to update, then reload
  the extension at `chrome://extensions`.

Your connection details live only in `config.js`, which is never in this repo and is
never overwritten by an update.
