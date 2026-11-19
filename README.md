# DevOps Interview Lab

A mobile-first app for practising DevOps interviews. It has 111 scenarios across Linux, Kubernetes, Helm, ArgoCD, Terraform, Ansible, Docker, CI/CD, GitLab, Jenkins, Monitoring, service mesh, SRE, AWS, cloud, networking, security, system design and behavioural questions.

Each incident scenario gives you a situation, an optional hint, then the troubleshooting steps and the commands to run, with a one-line explanation of each command. Behavioural questions give you a STAR structure and a sample answer. A separate Questions tab has short concept questions (answer out loud, then reveal). Both tabs support a 5-question mock session, filter by topic, search by keyword and track what you solved. Progress is stored in your browser only, and can be cleared with "Reset progress".

It is a single static file (`index.html`) with no build step, no dependencies and no external requests. It follows the system light or dark theme.

## Run locally

    python3 -m http.server 8000

Then open http://localhost:8000.

## Deploy with GitHub Pages

1. Push this repo to GitHub.
2. Go to Settings, Pages, and set Source to GitHub Actions.
3. The workflow in `.github/workflows/pages.yml` publishes the site on every push to `main`.

On iPhone, open the site in Safari and use Share, Add to Home Screen.

## Add a question

Each entry in the `Q` array is `[topic, question, answer]`. The question text is its ID for saved progress.

## Add a scenario

Each entry in the `S` array in `index.html` has this shape:

    [topic, level, title, situation, hint, [steps], [commands], takeaway]

- `topic` must be one of the names in the `T` array.
- Write plain text. `<`, `>` and `&` are escaped for you, so `<pid>` is fine.
- The title is the scenario's ID for saved progress. Keep titles unique, and note that renaming one resets its progress.
- A command without a matching rule in the `EX` array shows no explanation. Add a `[/regex/, "explanation"]` rule there.
