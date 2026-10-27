# FlaskApp: a small Flask app with tests, Docker and CI

A minimal web app I built to practise the full path from code to an automated pipeline.

## What's inside

| File | What it does |
|---|---|
| `app.py` | A Flask app with one route (`/`) that returns "Hello, World!" on port 5001 |
| `test_app.py` | A pytest test that calls the route and checks the response |
| `Dockerfile` | Packages the app into a Docker image (Python 3.10) |
| `.github/workflows/ci.yml` | GitHub Actions pipeline: on every push or pull request to `main`, it installs dependencies, runs the tests, and if they pass, builds the Docker image |

## Run it

```bash
pip install -r requirements.txt
python app.py            # open http://localhost:5001
python -m pytest         # run the test
```

With Docker:

```bash
docker build -t flask-app .
docker run -p 5001:5001 flask-app
```

## What I learned

- How a CI pipeline runs tests automatically before anything is built
- Making one job depend on another (`needs: test`) so a broken build never gets packaged
- Containerising a Python app with Docker

## Next steps

- Add a real endpoint (for example, serving predictions from a small ML model)
- Push the image to a registry and deploy it
