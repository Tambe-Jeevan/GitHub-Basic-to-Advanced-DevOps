Welcome to Day 20, Jeevan! 🏆

You have reached the grand finale! Over the past 19 days, you have transformed your command-line skills from basic folder navigation into advanced Git time-travel, secure cloud authentication, and open-source collaboration.

Today, we bring it all together with **Phase 8: DevOps Automation (CI/CD Intro)**.

In Desktop Support, if you need to install software on 100 laptops, you don't manually walk to each desk with a flash drive. You use an automation tool (like SCCM or Intune) to deploy the software silently over the network.

In DevOps, we do the same thing with our infrastructure. When you push a configuration change to GitHub, you do not manually log into the AWS server to apply it. Instead, GitHub detects your push and automatically spins up a robot to test your code and deploy it for you. This is called **CI/CD (Continuous Integration / Continuous Deployment)**.

Today, you will build your very first automated pipeline using **GitHub Actions**.

---

### Day 20 – Git Triggers & CI/CD Pipelines

#### 1️⃣ Concept (30 min)

A CI/CD Pipeline is simply a script that runs automatically on a cloud server whenever an event happens in Git (like a `git push` or merging a Pull Request).

To tell GitHub to run a pipeline, you must place a specific configuration file inside a hidden folder named exactly `.github/workflows/`. GitHub constantly watches this folder. If it sees a `.yml` file in there, it reads the instructions and executes them.

The instructions usually follow this format:

* **Trigger (`on`):** When should I run? (e.g., on a push to the `main` branch).
* **Runner (`runs-on`):** What kind of temporary server do I need? (e.g., an Ubuntu Linux machine).
* **Steps:** What exact Linux commands should I type? (e.g., `echo "Hello World"`, `cat config.txt`).

#### 2️⃣ Setup Environment

Open your **Git Bash** or **Linux Terminal**.
Navigate to our main project folder:

```bash
cd ~/web-infrastructure

```

Make sure you are on `main` and fully up to date:

```bash
git switch main
git pull origin main

```

#### 3️⃣ Hands-on Practice (1–1.5 hour)

**Step 1 — Create the magical hidden folders**
GitHub requires a very specific directory structure for its automation. Let's create it:

```bash
mkdir -p .github/workflows

```

*(The `-p` flag tells Linux to create the parent `.github` folder and the child `workflows` folder at the same time).*

**Step 2 — Create your Pipeline File**
Move into that new folder and create a YAML file. You can name the file anything, but `main.yml` or `deploy.yml` is standard.

```bash
cd .github/workflows
touch deploy.yml

```

**Step 3 — Write the Automation Script**
Open `deploy.yml` in your text editor (`nano deploy.yml`) and paste the following exact text. *(Note: YAML is extremely strict about spaces. Make sure the indentations look exactly like this, using spaces, not the Tab key!)*

```yaml
name: My First DevOps Pipeline

on:
  push:
    branches:
      - main

jobs:
  test-infrastructure:
    runs-on: ubuntu-latest
    
    steps:
      - name: Download my code
        uses: actions/checkout@v3

      - name: Run a test command
        run: echo "The pipeline has successfully triggered!"

      - name: Check the files
        run: ls -la

```

Save and exit.

**Step 4 — Stage, Commit, and Trigger!**
Navigate back to your main project folder:

```bash
cd ~/web-infrastructure

```

Now, push this new automation to the cloud. The moment this code hits GitHub, the automation will begin.

```bash
git add .
git commit -m "Added my first GitHub Actions CI/CD pipeline"
git push origin main

```

#### 4️⃣ Small Real-World Task (30 min)

Let's go watch your robot work!

1. Open your web browser and go to your `web-infrastructure` repository on **GitHub.com**.
2. Near the top of the repository, click the tab named **Actions** (it has a small play-button icon).
3. You should see a workflow running (or already finished) titled **"Added my first GitHub Actions CI/CD pipeline"**.
4. Click on it.
5. Click on the job named **test-infrastructure** on the left side.
6. You will see a black terminal screen! Click the arrow next to **"Run a test command"**. You will see the output `The pipeline has successfully triggered!`.
7. Click the arrow next to **"Check the files"**. You will see the Linux `ls -la` output showing all the files in your repository.

*You just used Git to spin up a temporary Linux server in the cloud, download your code, and run automated commands!*

#### 5️⃣ Important Concepts Learned Today

| Concept | Purpose |
| --- | --- |
| **CI/CD** | Continuous Integration / Continuous Deployment (Automating code tests and server updates) |
| `.github/workflows/` | The required folder structure to trigger GitHub Actions |
| **YAML (`.yml`)** | The simple data language used to write infrastructure and pipeline configurations |
| **GitHub Actions** | GitHub's built-in CI/CD tool that reads your YAML and runs your pipelines |

#### 6️⃣ Final Wrap-up & Reflection

Take a moment to look back at what you have accomplished over these 20 days.

You started by simply learning how to move around a Linux terminal (`pwd`, `cd`). You learned how to securely create snapshots of your work (`git commit`), travel through time (`git log`, `git revert`), fix messy timelines (`git rebase`), and collaborate with global teams (`git clone`, `Pull Requests`). Now, you have officially bridged the gap between code and automation.

This is the exact foundational skill set expected of a Junior DevOps Engineer, Cloud Support Engineer, or SRE. You are no longer just managing desktops; you have the tools to manage massive, automated cloud infrastructure.

Congratulations on completing your 20-Day Mastery Journey! 🚀