# DevOps Interview Lab

A mobile-first app for practising DevOps interviews. It has 112 scenarios across Linux, Kubernetes, Helm, ArgoCD, Terraform, Ansible, Docker, CI/CD, GitLab, Jenkins, Monitoring, service mesh, SRE, AWS, cloud, networking, security, system design and behavioural questions.

Each incident scenario gives you a situation, an optional hint, then the troubleshooting steps and the commands to run. Behavioural questions give you a STAR structure and a sample answer. You can run a 5-question mock interview, filter by topic and track what you solved. Progress is stored in your browser.

It is a single static file (`index.html`) with no build step and no dependencies.

## Run locally

    python3 -m http.server 8000

Then open http://localhost:8000.

## Deploy with GitHub Pages

1. Push this repo to GitHub.
2. Go to Settings, Pages, and set Source to GitHub Actions.
3. The workflow in `.github/workflows/pages.yml` publishes the site on every push to `main`.

On iPhone, open the site in Safari and use Share, Add to Home Screen.

## Add a scenario

Each entry in the `S` array in `index.html` has this shape:

    [topic, level, title, situation, hint, [steps], [commands], takeaway]
