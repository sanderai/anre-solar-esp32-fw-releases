Update server address on the device:
`https://raw.githubusercontent.com/you/your-repo/main/manifest.json`

A release is then: 
1. bump `version.txt`
2. `pio run`
3. COPY released .bin to this repo under releases 
4. `gh release create v1.2.3 release/firmware-1.2.3.bin`
5. get SHA?
5. update `manifest.json`
6. commit + push.

Caveats: release-asset downloads go through a 302 redirect (the device
follows redirects, fine), and `raw.githubusercontent.com` caches for ~5
minutes, so a just-pushed manifest can take a few minutes to show up.

```json
{
  "version": "1.2.3",
  "url": "https://github.com/you/your-repo/releases/download/v1.2.3/firmware-1.2.3.bin",
  "sha256": "...",
  "notes": "Fix sensor drift."
}
```
