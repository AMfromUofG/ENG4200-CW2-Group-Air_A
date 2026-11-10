# ENG4200 CW2 — Group Air A

We use `air-quality.csv` to compare models that predict carbon monoxide (CO) levels. The main notebook is [`CW2_Air_A.ipynb`](CW2_Air_A.ipynb).

Follow these steps to run the notebook in **VS Code** on Windows or macOS.

## 1. Check that Git is installed

Open **PowerShell** on Windows or **Terminal** on macOS. Type this command and press Enter.

```sh
git --version
```

If you see a version number, go to step 2. Otherwise, follow the instructions for your computer.

- **Windows** — Install [Git for Windows](https://git-scm.com/install/windows). Close and reopen PowerShell and VS Code, then run `git --version` again.
- **macOS** — If a window offers to install the command line developer tools, click **Install**. If you don’t get a prompt, run `xcode-select --install` in Terminal. Once the installation finishes, run `git --version` again. [Git for macOS](https://git-scm.com/install/mac)

You install Git once on your computer. Cloning creates a local copy of the team’s project.

## 2. Open the project in VS Code

**If you already cloned the project**, open VS Code and choose **File → Open Folder**. Select the `ENG4200-CW2-Group-Air_A` folder.

**If you still need to clone the project**, open a new VS Code window and follow these steps.

1. Click **Source Control**, the branching icon on the left.
2. Click **Clone Repository** and paste this address.

   ```text
   https://github.com/AMfromUofG/ENG4200-CW2-Group-Air_A.git
   ```

3. Choose where to save the project, such as **Documents**. When VS Code asks whether to open the cloned project, click **Open**. Sign in to GitHub if prompted.

Once the folder is open, click **Explorer**, the files icon on the left. You should see `CW2_Air_A.ipynb`, `requirements.txt`, and `air-quality.csv`.

Click **Terminal → New Terminal** in the top menu. Run this command in the panel that opens at the bottom.

```sh
git status
```

If Git shows the current branch, go to step 3. If it says `not a git repository`, check that you opened the cloned folder. If you used **Download ZIP** on GitHub, follow the clone steps above so you can pull team updates. Keep your ZIP copy if it contains any edits.

## 3. Set up Python for this project

If you haven’t installed `uv`, follow the steps for your computer in the [uv installation guide](https://docs.astral.sh/uv/getting-started/installation/). Then restart VS Code, reopen the project folder, and click **Terminal → New Terminal**.

Run the two commands for your computer, one at a time. The first creates a folder called `.venv` with Python for this project. The second installs the packages the notebook needs. If you already created `.venv` for this project, skip the first command.

**Windows (PowerShell)**

```powershell
uv venv --python 3.13.5 --seed
uv pip install --python .\.venv\Scripts\python.exe -r requirements.txt
```

**macOS**

```sh
uv venv --python 3.13.5 --seed
uv pip install --python ./.venv/bin/python -r requirements.txt
```

If the second command can’t find `requirements.txt`, check that the project folder from step 2 is open. Then open a new terminal inside VS Code and try again.

## 4. Run the notebook

1. Click **Extensions** in the left sidebar. Search for and install **Python** and **Jupyter**, both published by Microsoft.
2. Click **Explorer** in the left sidebar and open `CW2_Air_A.ipynb`.
3. Click **Select Kernel** in the top-right corner of the notebook. If needed, click **Select Another Kernel → Python Environments**. Choose the `.venv` for this project. Its Python path ends in `.venv\Scripts\python.exe` on Windows or `.venv/bin/python` on macOS.
4. Click the play button next to the first code cell under **Import all necessary libraries**. If it runs successfully, run the rest of the cells from top to bottom. Some model-training cells take a while.

## If something goes wrong

| What you see | What to do |
| --- | --- |
| `ModuleNotFoundError` or a prompt to install `ipykernel` | Check that you selected the project’s `.venv` in step 4. If the error continues, rerun the second command in step 3. |
| `externally-managed-environment` | VS Code is using the base Python installation. Select the project’s `.venv` in step 4. |
| `NameError` for a variable used in a later cell | Run the earlier cells in order, starting at the top. |
| `FileNotFoundError` in **Cost analysis** pointing to someone else’s Desktop | Change the CSV-loading line in that cell to `df = pd.read_csv("air-quality.csv")`. The CSV is already in the project folder. |

## When you come back to the project

- Before editing, click **Source Control → … → Pull** in VS Code to get the latest team changes.
- If `requirements.txt` changed, rerun the second command in step 3 for your computer.
- Before committing, check the changed files in **Source Control**. Running a notebook can change its saved outputs even if you didn’t edit any code. Keep `.venv`, `__pycache__`, and `.pyc` files on your own computer. Python creates its cache files automatically.