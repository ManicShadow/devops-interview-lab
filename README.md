# DevOps Interview Lab

A mobile-first app for practising DevOps interviews. Live site: https://manicshadow.github.io/devops-interview-lab/

It has two tabs:

- **Scenarios** (120): incident and design cases across Linux, Kubernetes, Helm, ArgoCD, Terraform, Ansible, Docker, CI/CD, GitLab, Jenkins, Monitoring, service mesh, SRE, AWS, Azure, GCP, cloud, networking, security, system design and behavioural topics. Each gives you a situation, an optional hint, then the troubleshooting steps and the commands to run, with a one-line explanation of each command. Behavioural scenarios give you a STAR structure and a sample answer.
- **Questions** (144): short concept questions on the same topics. Answer out loud, then reveal the answer.

Both tabs support a 5-question mock session, topic filters, keyword search and progress tracking. Missed items can be retried at the end of a session. Progress is stored in your browser only and can be cleared with "Reset progress". The topic filter scrolls sideways on phones and wraps on desktop.

It is a single static file (`index.html`) with no build step, no dependencies and no external requests. It follows the system light or dark theme.

## Run locally

Open `index.html` in a browser, or serve the folder:

    python3 -m http.server 8000

Then open http://localhost:8000.

## Deploy with GitHub Pages

1. Push this repo to GitHub.
2. Go to Settings, Pages, and set Source to GitHub Actions.
3. The workflow in `.github/workflows/pages.yml` publishes the site on every push to `main`.

On iPhone, open the site in Safari and use Share, Add to Home Screen.

## Add a question

Each entry in the `Q` array in `index.html` has this shape:

    [topic, question, answer]

- `topic` must be one of the names in the `T` array.
- The question text is its ID for saved progress. Keep questions unique, and note that renaming one resets its progress.

## Add a scenario

Each entry in the `S` array in `index.html` has this shape:

    [topic, level, title, situation, hint, [steps], [commands], takeaway]

- `topic` must be one of the names in the `T` array, and `level` is Junior, Mid or Senior.
- Write plain text. `<`, `>` and `&` are escaped for you, so `<pid>` is fine.
- The title is the scenario's ID for saved progress. Keep titles unique, and note that renaming one resets its progress.
- A command without a matching rule in the `EX` array shows no explanation. Add a `[/regex/, "explanation"]` rule there. Rules are checked in order, so put specific ones before general ones.

## Add a topic

Add the name to the `T` array, then add at least one scenario or question that uses it. The topic chips are built from `T`.
