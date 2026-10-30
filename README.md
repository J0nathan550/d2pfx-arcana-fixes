# hero-base-fixes
Hero base models that are broken in the game's own files, compiled again by hand so they work: arcanas, personas and some immortals with their animations. Dota 2 Mod Manager's item builder downloads them from here.

Formerly `J0nathan550/d2pfx-arcana-fixes`.

## How the app trusts these files

The app reads `manifest.json` (every file of every base under `src/<id>/` with its git hash) and takes it only when `manifest.json.sig` is a good ed25519 signature over it, against the key pinned in the app's `src/arcana-base-store.ts`. Each file is then checked against its hash. A push that changes files without re-signing the manifest reaches nobody.

After changing anything under `src/`, run from a checkout of the app, then commit both files together with the change:

```
node tools/arcana-bases-manifest.mjs <this checkout> <private key .pem>
```

The private key never goes into this repository.

for details: https://github.com/dota2modmanager/dota2-mod-manager
