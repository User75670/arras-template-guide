# Setup guide (Windows)

*Note: this guide is specificially for people who want the original arras template. If you are here by mistake, you should probably use [OSA](https://github.com/AE0hello/open-source-arras)*

## What you need

* **Node.js \& npm** - Install the latest version [here](https://nodejs.org/) (make sure to include npm).
* **Code editor** - Recommended: [VS Code](https://code.visualstudio.com/).
* **Cloudflare Tunnel** - [Download here](https://developers.cloudflare.com/cloudflare-one/networks/connectors/cloudflare-tunnel/downloads/). (most low latency)
* **A browser**.

## Get the Project

You can either use the template provided above, or use the community forks:
* [https://github.com/Faris90/arras-template-fullversion](https://github.com/Faris90/arras-template-fullversion)
* [https://github.com/user75670/Arras42](https://github.com/User75670/Arras42) <-- *this is mine*
* [https://github.com/antojoarras/cx](https://github.com/antojoarras/cx)

## Key Files

You'll edit these most often:

* **`lib/definitions.js`** - Tank definitions.
* **`server.js`** - Main logic.
* **`config.json`** - Server settings.
* **`.env`** - Secrets like testbed token.

## Initial Setup

1. Open a **terminal** in the project directory (in VS Code: Ctrl+`  or Terminal > New Terminal).
2. Run:

```bash
   npm i
   ```

3. To start the server run:

```bash
   node server
   ```

   *(Server runs on port from `config.json`, default 3000.)*

   ## Expose with Cloudflare Tunnel

1. Download Cloudflare Tunnel executable, rename to `cloudflared.exe` (for the next step), place in a folder.
2. In a new terminal, navigate to that folder.
3. Run:

   ```bash
   cloudflared tunnel --url localhost:3000
   ```

   *(Replace  3000` if using different port. Generates a temporary link. Stable, fixed links are paid)*

   ## Joining the Server

1. Go to: `arras.cx/#host=CLOUDFLARE_LINK`

   *(Replace CLOUDFLARE_LINK with the link that cloudflare tunnel generated)*

   * Example: `arras.cx/#host=example.trycloudflare.com`
2. To use the testbed token (if you've set it to something): `arras.cx/#host=LINK&key=TOKEN`

   *(Replace TOKEN with the actual token)*
   
   ## Updating Changes

1. Make changes in your editor and **save** files (the ones you changed).
2. In the server terminal (not the cloudflare tunnel terminal): Stop (`Ctrl+C`) and restart:

   ```bash
   node server
   ```

3. **Cloudflare Tunnel**: No need to restart unless you want link to change or shut down your computer.

   Every time you start the server: `node server` in project directory, then `cloudflared tunnel --url localhost:3000` (or whatever port you put) in tunnel directory.
   You can also share the link with others, anyone with the link can join.
