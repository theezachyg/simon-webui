# Simon skin on Open WebUI

`simon-skin.patch` holds every change that turns stock Open WebUI (v0.11.4) into the Simon build:
the "Study" palette and fonts (`src/tailwind.css`, `static/static/custom.css`), the Simon logo, favicons and splash
(`static/static/*`, `backend/open_webui/static/*`), the name without the "(Open WebUI)" suffix (`backend/open_webui/env.py`),
the landing page (`src/lib/components/OnBoarding.svelte`), the page title (`src/app.html`, `src/lib/constants.ts`),
and a single GitHub Actions workflow that builds `ghcr.io/<owner>/simon-webui:latest` for linux/amd64.

## Rebuild on a newer Open WebUI

```bash
git clone --depth 1 --branch vX.Y.Z https://github.com/open-webui/open-webui.git simon-webui-new
cd simon-webui-new
git apply --binary --3way ../simon-skin.patch     # fix any conflicts, then commit
```

Then push to the `simon-webui` repo's `main` branch; the workflow builds and publishes the image, and the pod
(`simon-webui` on RunPod) picks it up on its next restart because it pulls `ghcr.io/<owner>/simon-webui:latest`.

## License note

Open WebUI's license permits altering its branding for deployments with fewer than 50 users in any 30-day period.
The About page keeps the "powered by Open WebUI" attribution that the upstream code shows whenever the name is changed.
