# Rsbuild project

## Setup

Install the dependencies:

```bash
pnpm install
```

## Get started

Start the dev server:

```bash
pnpm dev
```

Build the app for production:

```bash
pnpm build
```

Preview the production build locally:

```bash
pnpm preview
```

## Deploying UI Updates to Docker

If you have installed BillionMailix via Docker (`install.sh`) and want to apply your local frontend UI changes to the running server:

1. Build the production frontend locally:
   ```bash
   pnpm run build
   ```
   *This generates a new `dist/` directory containing your compiled UI.*

2. Remove the old frontend from your running Docker container:
   ```bash
   docker exec billionmail-core-billionmail-1 rm -rf /opt/billionmail/core/public/dist
   ```

3. Copy your newly compiled `dist/` directory into the container:
   ```bash
   docker cp dist/ billionmail-core-billionmail-1:/opt/billionmail/core/public/dist
   ```

4. Do a **Hard Refresh** (Ctrl+F5 or Cmd+Shift+R) in your browser to see the changes. (If changes do not reflect, you can run `docker restart billionmail-core-billionmail-1`).
