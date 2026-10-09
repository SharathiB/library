# Library Management System — Vercel package

This package includes a Vercel Python serverless entry point and routing configuration.

## Deploy
1. Extract this ZIP.
2. Push the project folder to a GitHub repository.
3. In Vercel, choose **Add New → Project** and import that repository.
4. Keep the project root at this folder and deploy. Vercel should detect `vercel.json`.
5. Open the deployed URL.

## Important limitations before public production
- The existing app uses SQLite. Vercel serverless deployments do **not** provide a persistent writable local filesystem for runtime data. Any changes written to a local SQLite database may be lost or may not be shared across function instances. For a real deployment, migrate SQLite to a hosted database such as Neon Postgres or another persistent database.
- The current sign-in UI is a demo member switcher without passwords. Do not expose this publicly with real member data until proper authentication and authorization are added.
- The uploaded `library.db` is included as provided, but the serverless runtime may not be able to persist writes to it.
- Ensure the full `library/` package and `static/` assets are present in this folder before deploying; they were not among the uploaded files in this conversation. If they exist in another project folder, copy them in before deploying.

## Local development
```bash
pip install -r requirements.txt
python app.py
```

## Tests
```bash
python -m unittest discover -s tests -t .
```
