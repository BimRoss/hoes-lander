# hoes-lander

A landing page for **Hoes on Boats** — twelve friends, one 52' catamaran, Yacht Week Croatia, August 2026, and Don's 70th birthday. Published at https://hoes.makeacompany.ai.

## Stack

- `index.html` — vanilla HTML/CSS/JS, Google Fonts (Fraunces + Inter + JetBrains Mono), inline SVG, no build step.
- `Dockerfile` — `nginx:1.27-alpine` serving the file.
- `.github/workflows/build.yml` — builds + pushes `geeemoney/hoes-lander:<version>` to Docker Hub on tag.
- Cluster manifests live in [`BimRoss/rancher-admin`](https://github.com/BimRoss/rancher-admin) under `admin/apps/hoes/`.

## Releasing

```sh
git tag -a v0.1.0 -m "v0.1.0"
git push origin v0.1.0
# bump the image tag in rancher-admin/admin/apps/hoes/deployment.yaml via PR
```

## Local preview

```sh
docker build -t hoes-lander . && docker run --rm -p 8080:80 hoes-lander
# open http://localhost:8080
```
