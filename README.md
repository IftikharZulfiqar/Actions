# GitHub-Actions Playbook ⚙️🚀
A curated collection of **GitHub Actions workflows** that demo common CI/CD patterns—plus a tiny Dockerised Python API you can use as a build target.

[![CI](https://img.shields.io/github/actions/workflow/status/IftikharZulfiqar/Actions/docker-image.yml?label=CI)](../../actions)
[![Licence](https://img.shields.io/github/license/IftikharZulfiqar/Actions)](LICENSE)
[![Last commit](https://img.shields.io/github/last-commit/IftikharZulfiqar/Actions)](../../commits)

---

## ✨ What’s inside?

| Workflow file                          | Trigger(s)           | What it shows off                                               |
|----------------------------------------|----------------------|-----------------------------------------------------------------|
| **`build-docker-img.yml`**             | `push` → `main`      | Build & push an image to **Docker Hub** (or ECR) using `docker/build-push-action` |
| **`docker-image.yml`**                 | Manual dispatch      | Multi-platform build (`linux/amd64, arm64`), tag with commit SHA |
| **`ENV_Variables.yaml`**               | `workflow_dispatch`  | Defining, masking and echoing repo / org environment variables |
| **`shell-commands.yml`**               | Schedule (06:00 UTC) | Run arbitrary bash, upload artifact, create issue on failure    |
| **`play.yml`**                         | PR open / sync       | Matrix test job, `actions/cache`, post PR comment via `github-script` |
| **`cheetay.yml`**                      | `push` (tagged)      | Semantic-version tag filter, publish GitHub Release             |
| **`github-actions.yml`**               | Reusable workflow    | Called from other repos via `uses: ./.github/workflows/github-actions.yml` |
| **`buildme.yml`**                      | **Composite Action** | Demonstrates creating a local composite for repeated shell steps |

> **Tip 💡**: Each YAML is deliberately self-contained so you can copy it into other projects.

---

## 📂 Repo structure

. ├── .github/ │ └── workflows/ # 9 example workflow files ├── api.py # Tiny Flask-style API (Python stdlib HTTP server) ├── Dockerfile # 6-line demo Dockerfile └── README.md # ← you are here


---

## 🏗️ Prerequisites

| Tool | Version |
|------|---------|
| Docker | 24.x |
| GitHub account | to fork & run workflows |
| (Optional) **Docker Hub** / **ECR** repo | for image pushes |

---

## 🚀 Quick start

### 1 — Fork the repo
Forking lets you push commits and see the workflows run under **Actions > Runs**.

### 2 — Add secrets / vars
* `DOCKER_USERNAME`, `DOCKER_PASSWORD` – for Docker Hub pushes  
* Any extra variables referenced in `ENV_Variables.yaml`

Settings → Secrets and variables → Actions.

### 3 — Push a change
```bash
echo "# test $(date)" >> CHANGELOG.md
git add CHANGELOG.md
git commit -m "chore: trigger workflows"
git push origin main
