# Earth Trend Detective — public deployment package

## Included features
- Original M1–M4 regional investigation and four M4 anomaly candidates.
- User CSV upload and column mapping (date + numeric temperature/LST).
- Browser-local exploratory OLS trend chart, confidence interval, R², residual screening and data-quality counts.
- Downloadable analysis CSV and administrator submission JSON package.
- Missing/invalid dates and values are excluded, never replaced with zero.

## Run locally for preview
Run `python -m http.server 8000` in this folder and open `http://localhost:8000`. Internet access is required for Plotly and PapaParse CDN libraries.

## Publish publicly
Recommended immediate static hosting: GitHub Pages. Create a public GitHub repository, upload the contents of this folder (keep `index.html` at repository root), then open **Settings → Pages** and select **GitHub Actions** as the build and deployment source. The included `.github/workflows/deploy.yml` publishes the site whenever you push to `main`. GitHub will provide a public `https://<username>.github.io/<repository>/` address. See https://docs.github.com/en/pages/quickstart.

## Important submission/storage limitation
The user CSV is processed in the visitor's browser. The website does not upload, retain, or transmit it. The JSON package is a local download for the visitor to submit through an administrator-provided channel. A real in-site submission queue requires a backend API, authenticated administrator access, storage, retention policy, file-size limits, abuse protection and security rules. Do not enable anonymous public write access to a database or storage bucket.

## Recommended full-stack option
For the requested persistent administrator workflow, use **Azure Static Web Apps + Azure Functions API + private Azure Blob Storage**. Static Web Apps hosts the public site and can integrate serverless APIs; the API should validate uploads and create pending-review records, while Blob Storage keeps submitted files private. Configure admin-only access before launch. Documentation: https://learn.microsoft.com/azure/static-web-apps/overview/ and https://learn.microsoft.com/azure/static-web-apps/add-api.

## Scientific scope
The uploaded-data analysis is intentionally labelled exploratory OLS. It is not the M3 harmonic/HAC method and should not be presented as equivalent. It is not a replacement for quality control, domain review or causal analysis.
