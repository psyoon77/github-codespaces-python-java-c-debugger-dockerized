<div align="center">

# 💻 GitHub Codespaces Python, Java & C Programming Platform 💻

### Dockerized Beginner Coding Environment in the Browser or VS Code

<p>
  <img alt="Workflow: GitHub Codespaces" src="https://img.shields.io/badge/workflow-GitHub%20Codespaces-181717">
  <img alt="Python: 3.11" src="https://img.shields.io/badge/Python-3.11-3776AB">
  <img alt="Java: 21" src="https://img.shields.io/badge/Java-21-ED8B00">
  <img alt="C: GCC and GDB" src="https://img.shields.io/badge/C-GCC%20%2B%20GDB-A8B9CC">
  <img alt="License: MIT" src="https://img.shields.io/badge/license-MIT-2ea44f">
</p>

<p>
  <a href="#-why-this-exists">Why this exists</a> •
  <a href="#-capabilities">Capabilities</a> •
  <a href="#-verified-in-github-codespaces">Verified</a> •
  <a href="#-codespaces-quick-start">Codespaces</a> •
  <a href="#-run-the-examples">Examples</a> •
  <a href="#-debug-with-vs-code">Debugging</a> •
  <a href="#-references">References</a>
</p>

</div>

This repository includes just the skeleton of the prior work.

Environment setup should not stop someone from learning to program. This
repository provides a prepared GitHub Codespaces and VS Code Dev Container
environment for beginners learning Python, Java, C, compilers, terminals, and
step-by-step debugging.

## 🎯 Why this exists

[GitHub Codespaces](https://docs.github.com/en/codespaces/about-codespaces/what-are-codespaces)
creates a cloud development environment from repository configuration. This
project defines that environment with a Dockerfile, Docker Compose, and
`.devcontainer/devcontainer.json`, giving learners a consistent Ubuntu toolchain
in browser-based VS Code or desktop VS Code.

It can serve as a beginner coding environment, programming classroom starter,
cloud development workspace, or reproducible Python, Java, and C debugging lab.

## 📋 Capabilities

| Area | Included |
| --- | --- |
| Primary workflow | GitHub Codespaces in browser VS Code or desktop VS Code |
| Local alternative | VS Code Dev Containers or plain Docker Compose on macOS, Windows, and Linux |
| Container | Ubuntu 24.04 development environment with `amd64` and `arm64` Miniforge support |
| Python | Python 3.11, `pip`, debugpy, and the VS Code Python and Jupyter extensions |
| Java | OpenJDK 21 and the VS Code Extension Pack for Java |
| C and C++ | GCC, G++, GDB, Make, CMake, Ninja, and Microsoft C/C++ extensions |
| Editor workflow | IntelliSense, integrated terminal, breakpoints, variable inspection, and step debugging |
| Developer tools | Git, Git LFS, GitHub CLI, SSH client, `curl`, `wget`, Vim, Nano, and tmux |
| Collaboration | Microsoft Live Share extension is preinstalled |
| Port configuration | Port `8888` is forwarded; no notebook server is started automatically |

## ✅ Verified in GitHub Codespaces

A fresh 2-core Codespace was tested end to end on September 1, 2026, in the
Southeast Asia region using browser-based VS Code. The repository built and
opened successfully at `/workspace` with 8 GB RAM and 32 GB storage.

The live container reported Python 3.11.16, Java 21.0.10, GCC 16.2.0, GDB
17.2, and CMake 4.4.3. The included Python, Java, and C programs ran
successfully, the CMake build completed, and the VS Code Python, Java, and C
debugger workflows all completed successfully. Port `8888` was forwarded as
configured; the project did not start a notebook server.

The Codespace was stopped immediately after validation. No Ollama service or
model was installed or used during this test.

## 🚀 Codespaces quick start

1. Open this repository on GitHub.
2. Select **Code**.
3. Open the **Codespaces** tab.
4. Select **Create codespace on main**.
5. Wait for the image, Conda environment, and VS Code extensions to finish.
6. Open a terminal and verify the toolchain:

```bash
python --version
javac -version
gcc --version
gdb --version
cmake --version
```

The codespace opens in browser-based VS Code by default and can also be opened
in the [desktop VS Code application](https://docs.github.com/en/codespaces/developing-in-a-codespace/using-github-codespaces-in-visual-studio-code).
If the environment needs to be recreated, open the Command Palette and select
**Codespaces: Rebuild Container**.

GitHub Codespaces can consume metered compute and storage. Review the official
[Codespaces billing documentation](https://docs.github.com/en/billing/concepts/product-billing/github-codespaces)
before creating or leaving a codespace running.

When you finish, open [Your codespaces](https://github.com/codespaces), select
the **Show more actions** menu for the codespace, and choose **Stop codespace**.
Stopping ends compute use; the stored codespace remains until it is deleted or
its auto-delete period expires.

## 💻 What VS Code and the container do

VS Code is the editor: it displays files, provides the terminal, installs
language extensions, and gives you buttons for running and debugging code. The
development container supplies the repeatable Linux toolchain—Python, Java,
GCC, GDB, CMake, and related command-line tools.

This separation is useful for beginners: the editor runs the learning workflow,
while the container prevents most host-specific installation differences.

## ▶ Run the examples

Run these commands inside the codespace or local development container.

### Python

```bash
python python/hello-world-for.py
```

### Java

```bash
javac -d java-out java/HelloWorldFor.java
java -cp java-out HelloWorldFor
```

### C

```bash
mkdir -p c/c-executables
gcc -O0 -g c/hello-world-for.c -o c/c-executables/hello-world-for
./c/c-executables/hello-world-for
```

You can also build the C example with CMake:

```bash
cmake -S . -B build
cmake --build build
./build/c/hello_world_for
```

## 🐞 Debug with VS Code

### Python debugging

1. Open `python/hello-world-for.py`.
2. Select the interpreter shown in the VS Code status bar. In the live test,
   VS Code initially chose `/usr/bin/python3`; change it to
   `/opt/conda/envs/cs-project-docker/bin/python` so debugging uses the same
   Python 3.11 environment as the terminal.
3. Add a breakpoint beside a line number.
4. Use the Run button menu and select **Python Debugger: Debug Python File**.

See the official [Python debugging guide](https://code.visualstudio.com/docs/python/debugging).

### Java debugging

1. Open `java/HelloWorldFor.java`.
2. Add a breakpoint.
3. Wait until the status bar says **Java: Ready**. A new Codespace can initially
   open Java in Lightweight Mode; select that status item and switch to
   Standard Mode before debugging.
4. Use **Run or Debug → Debug Java**.

See the official [Java debugging guide](https://code.visualstudio.com/docs/java/java-debugging).

### C debugging

1. Open `c/hello-world-for.c`.
2. Compile with `-g` using the command above.
3. Add a breakpoint.
4. Open **Run and Debug** and choose the C/C++ GDB workflow when prompted.

The live Codespaces test used **C/C++: gcc build and debug active file**. GDB
printed `Failed to set controlling terminal: Operation not permitted`, but the
debugger still ran the program and completed normally.

The container enables `SYS_PTRACE` and relaxes its seccomp profile for GDB.
Use it only with code you trust. See the official
[C/C++ debugging guide](https://code.visualstudio.com/docs/cpp/cpp-debug).

## 🐳 Local VS Code and Docker option

You can use the same repository without creating a codespace:

1. Install [Docker Desktop](https://docs.docker.com/desktop/),
   [Visual Studio Code](https://code.visualstudio.com/), Git, and Microsoft’s
   [Dev Containers extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers).
2. Start Docker.
3. Clone and open the repository:

```bash
git clone https://github.com/psyoon77/github-codespaces-python-java-c-debugger-dockerized.git
cd github-codespaces-python-java-c-debugger-dockerized
```

4. Open VS Code, select **File → Open Folder**, and choose the cloned
   `github-codespaces-python-java-c-debugger-dockerized` folder. If you have
   installed the optional `code` shell command, you can instead run `code .`.
5. Open the Command Palette and select **Dev Containers: Reopen in Container**.

The terminal-only Compose workflow is:

```bash
docker compose up -d --build
docker compose exec cs-project-docker bash
```

Leave the shell with `exit`, then stop the project with `docker compose down`.

## 🤖 Optional local AI example

`ai/chat-ollama-openai.py` expects an Ollama server at `localhost:11434` and the
`llama3.2:1b` model. Ollama is not installed or started by this repository’s
Compose configuration, so the script requires separate setup in the same
environment. See Ollama’s
[OpenAI compatibility documentation](https://docs.ollama.com/api/openai-compatibility).

## 📖 Preserved manual

The repository’s previous README is preserved byte-for-byte as
[`manual.txt`](manual.txt). Additional historical onboarding notes are under
`manuals/`.

These legacy notes may contain old repository names, account references, and
host-wide Docker cleanup commands. Review them before use. Never share
passwords, API keys, private SSH keys, access codes, or unattended remote-control
credentials. The quick start above is the supported beginner path.

## 📚 References

- [What are GitHub Codespaces?](https://docs.github.com/en/codespaces/about-codespaces/what-are-codespaces)
- [Create a codespace](https://docs.github.com/en/codespaces/developing-in-a-codespace/creating-a-codespace-for-a-repository)
- [GitHub Codespaces development containers](https://docs.github.com/en/codespaces/setting-up-your-project-for-codespaces/adding-a-dev-container-configuration/introduction-to-dev-containers)
- [VS Code Dev Containers](https://code.visualstudio.com/docs/devcontainers/create-dev-container)
- [Docker Compose](https://docs.docker.com/compose/)
- [Python in VS Code](https://code.visualstudio.com/docs/languages/python)
- [Java in VS Code](https://code.visualstudio.com/docs/languages/java)
- [C/C++ debugging in VS Code](https://code.visualstudio.com/docs/cpp/cpp-debug)
- [Conda environment management](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html)
- [MIT License](https://opensource.org/license/mit)

## ⚖ License and attribution

Released under the [MIT License](LICENSE). Third-party products, services,
extensions, and trademarks remain subject to their respective licenses and
terms. This is an independent learning project and is not affiliated with the
vendors referenced above.

Release note: AI-assisted tools were used to help review and prepare the release
documentation. The repository owner reviewed the released material and remains
responsible for its contents.

---

<div align="center">
  <sub>A browser-ready first workspace for learning Python, Java, C, containers, and debugging.</sub>
</div>
