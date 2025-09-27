# CS61C Lab Workspace (Fall 2025)

Welcome to your personal workspace for **CS61C – Great Ideas in Computer Architecture (Machine Structures)**. This repository collects the lab starter code, tooling, and reference materials you will use throughout the semester.

## Prerequisites

Before you dive in, make sure the following tools are available in your environment:

- **Git** for pulling staff updates and submitting your work.
- A C toolchain such as **GCC** (or Clang) for the C programming labs (`lab01` & `lab02`).
- **Python 3** for helper scripts (for example, `lab00/code.py`).
- **Java 11+** to run the provided `.jar` tools (`venus.jar` for RISC-V assembly and `logisim-evolution.jar` for digital logic labs).
- (Recommended) A Unix-like shell (macOS, Linux, or WSL on Windows) so the provided shell scripts run without modification.

## Getting Started

1. **Clone your repository** (replace `<your-repo>` with the URL for your copy of `CS61C-fa25`):
   ```bash
   git clone <your-repo>
   cd CS61C-fa25
   ```
2. **Add the staff starter remote** (once per machine). The exact URL depends on your course offering; ask your TA if you are unsure:
   ```bash
   git remote add starter <staff-starter-url>
   git fetch starter
   ```
3. **Initialize Lab 00** (optional helper script). Inside `lab00/`, `init.sh` fast-forwards your `main` branch to the staff reference commit for Lab 00. Because it pushes to `origin`, confirm that `origin` points to your own GitHub repository before running it.
   ```bash
   cd lab00
   ./init.sh
   ```
4. **Install local preferences**. The repository ships with an `.editorconfig` and `.gitignore`; most editors will pick these up automatically.

## Repository Layout

```
code/
├── lab00/    # Intro scripting + Git warmup material
├── lab01/    # C basics: hello world, pointers, arrays, strings, structs
├── lab02/    # C tooling: compiler warnings, debugging, structs, test harnesses
├── lab03/    # RISC-V assembly practice and utilities
├── lab04/    # Additional RISC-V assembly exercises
└── tools/    # Course tooling (venus, logisim, helper scripts)
```

Supporting resources live outside `code/`:

- `docs/Lecture/` and `slides/` contain lecture notes and slide decks.
- `videos/` contains downloaded lecture recordings and helpers like `classify_lectures.ps1`.

## Typical Lab Workflow

1. Sync the latest starter code before beginning a new lab:
   ```bash
   git fetch starter
   git merge starter/<lab-branch>
   ```
   or cherry-pick individual updates as directed by the staff instructions.
2. Work through the exercises in the corresponding `labXX/` directory.
3. Use version control regularly:
   ```bash
   git status
   git add <files>
   git commit -m "Complete labXX exercise <n>"
   git push origin main
   ```
4. If a lab provides scripts (for example, `lab00/gen-debug.sh` or `lab00/get-ssh-key.sh`), make them executable with `chmod +x` and run them from a Unix-like shell.

## Running and Testing Labs

### C Labs (`lab01`, `lab02`)

Compile individual exercises with `gcc` (or your preferred compiler):

```bash
gcc lab01/ex1_hello.c -o lab01/ex1_hello
./lab01/ex1_hello
```

For multi-file exercises such as the vector implementation in `lab02/ex7_vector.c`, compile all necessary files together:

```bash
gcc lab02/ex7_vector.c lab02/ex7_test_vector.c -o lab02/vector_tests
./lab02/vector_tests
```

### RISC-V Assembly Labs (`lab03`, `lab04`)

Use the bundled Venus simulator:

```bash
java -jar tools/venus.jar lab03/ex1_hello.s
```

For programs that rely on helper routines found in `lab03/utils.s`, load both files in Venus or assemble them with your preferred toolchain.

### Digital Logic (Logisim)

When a lab requires digital logic design, open `tools/logisim-evolution.jar`. Depending on your Java installation, you may double-click the JAR or run:

```bash
java -jar tools/logisim-evolution.jar
```

## Helpful Scripts and Files

- `lab00/gen-debug.sh`: Generates a `debug.txt` template for TA office hours or Piazza posts.
- `lab00/get-ssh-key.sh`: Convenience script for retrieving your edX autograder key (if applicable).
- `lab03/utils.s`: Shared macros/functions for multiple assembly exercises.
- `tools/venus.jar`: RISC-V ISA simulator used throughout the assembly labs.
- `tools/logisim-evolution.jar`: Logic design tool used in later labs.

## Troubleshooting Tips

- **Missing remotes**: If `init.sh` reports `fatal: 'origin' does not appear to be a git repository`, add your own GitHub remote first: `git remote add origin <your-repo-url>`.
- **Executable scripts**: On Windows without WSL, consider running scripts from Git Bash or PowerShell with `wsl` to avoid incompatibilities.
- **Java errors**: Ensure `java -version` reports 11 or later; update your JDK if Venus or Logisim fail to launch.

## Additional Resources

- Course website and Piazza for up-to-date lab instructions and deadlines.
- Lecture notes (`docs/Lecture/`) and slide decks (`slides/`) for conceptual review.
- Recorded lectures inside `videos/` for asynchronous study.

Stay organized, commit often, and reach out on Piazza or office hours when you hit roadblocks. Happy hacking! 🎉
