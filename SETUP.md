# Setting up your laptop

We'll install Python and the packages astronomers use, with a tool called **conda**. Conda keeps
each project's packages in a separate "environment", so installing things for one project can't
break another.

This takes about 15 minutes, most of it waiting for downloads. You need about **4 GB of free disk
space** and an internet connection. If anything goes wrong, ask a mentor. Don't spend more than a
few minutes stuck.

**If your laptop is a Chromebook, a school-managed laptop where you can't install programs, or a
Mac running a very old version of macOS (older than macOS 10.15, from 2019),** skip this page and
use Google Colab or GitHub Codespaces instead. Both run in a web browser; the links are in
[README.md](README.md).

## 1. Install Miniforge

Miniforge is a small, free installer for conda. Go to https://conda-forge.org/download/ and
download the right installer:

- **Mac**: first check which chip your Mac has. Click the Apple menu (top left) → **About This
  Mac**. If it says **Chip: Apple M1/M2/M3/M4**, download the **arm64** installer. If it says
  **Processor: ... Intel**, download the **x86_64** installer.
- **Windows**: the **x86_64** `.exe` installer. (A few newer laptops have a Snapdragon / ARM chip
  instead; check under Settings → System → About → Processor. If it says Snapdragon, use
  **ARM64**.)
- **Linux**: the **x86_64** `.sh` installer.

**Mac**

1. Open the **Terminal** app (press Cmd + Space, type "Terminal", press Enter). The terminal is a
   window where you type commands. Press Enter after each command to run it.
2. Run the installer you downloaded. If it's in your Downloads folder, type this:
   ```bash
   bash ~/Downloads/Miniforge3-MacOSX-arm64.sh
   ```
   On an Intel Mac, the file name ends in `x86_64.sh` instead. Use whatever name your file has.
3. It shows a license. Press **q** to skip to the end, type `yes` to accept, and press Enter to
   accept the default install location. When it asks whether to initialize conda, type `yes`.
4. **Close Terminal and open it again.** You should now see `(base)` at the start of the line.
   This means conda is working, and you're in its default ("base") environment.

**Windows**

1. Run the `.exe` installer you downloaded. If Windows shows "Windows protected your PC", click
   **More info**, then **Run anyway**. Accept the defaults, and choose to install for "Just Me".
2. From the Start menu, open **Miniforge Prompt**. Use this window for all the commands below,
   not the regular Command Prompt or PowerShell. You should see `(base)` at the start of the line.

**Linux**

```bash
bash ~/Downloads/Miniforge3-Linux-x86_64.sh
```
Accept the license and say `yes` to initializing conda, then close and reopen the terminal.

**Check it worked.** Type this and press Enter:
```bash
conda --version
```
It should print a version number. If it says `command not found` (Mac/Linux) or
`'conda' is not recognized` (Windows), close and reopen the terminal (on Windows, make sure you're
in Miniforge Prompt). If it still fails, ask a mentor.

## 2. Get the course files

Go to https://github.com/vedantchandra/srmp-gaia, click the green **Code** button, then
**Download ZIP**. Unzip it somewhere easy to find,
like your Documents folder. Inside it you should see this file, `environment.yml`, and a
`tutorial` folder.

Now point the terminal at that folder. The easiest way: type `cd` followed by a space, then
**drag the folder from Finder / File Explorer into the terminal window**. Its location gets pasted
in. Press Enter. (On Windows, if the folder is on a different drive than `C:`, type `cd /d `
instead of `cd `.)

Check you're in the right place by listing the files: type `ls` (Mac/Linux) or `dir` (Windows).
You should see `environment.yml` in the list. If you don't, you may be one folder too high or too
low. (Unzipping on Windows sometimes makes a folder inside a folder with the same name. Go into
the inner one.)

## 3. Create the environment

```bash
conda env create -f environment.yml
```

This reads `environment.yml`, which lists the packages we need (numpy, scipy, matplotlib, pandas,
astropy, astroquery, and JupyterLab), and installs them into a new environment called `srmp`.
It will take a few minutes. When it's done, you can free up about 1 GB of disk space by deleting
the downloaded package files (type `y` if it asks you to confirm):

```bash
conda clean --all
```

Then **activate** the environment:

```bash
conda activate srmp
```

The start of the line should change from `(base)` to `(srmp)`. You need to activate the
environment every time you open a new terminal.

## 4. Start JupyterLab

```bash
jupyter lab
```

A browser tab should open with JupyterLab. (If the page looks broken, use an up-to-date Chrome or
Firefox.) Use the file browser on the left to open the `tutorial` folder, then
`python_basics.ipynb`. Click on the first code cell and press **Shift + Enter**. If it prints
`Hello, Gaia!`, you're all set.

Keep the terminal window open while you work. Closing it stops Jupyter. When you're done for the
day, save your notebook, close the browser tab, and press **Ctrl + C** in the terminal. If it asks
"Shutdown this Jupyter server (y/[n])?", type `y`. (If nothing happens, press Ctrl + C again, or
just close the window.)

**Every time after this**, open the terminal (Miniforge Prompt on Windows), `cd` into the course
folder (the drag trick works every time), and run:
```bash
conda activate srmp
jupyter lab
```

## Backup option: run in your browser

If the installation doesn't work, use the **Open in Colab** or **Open in GitHub Codespaces** links
in [README.md](README.md). Nothing to install. In Colab, use **File → Save a copy in Drive** to keep
your work.

## Common problems

| Problem | Fix |
|---|---|
| `conda: command not found` or `'conda' is not recognized` | Close and reopen the terminal. On Windows, make sure you're in "Miniforge Prompt". |
| `EnvironmentFileNotFound` | You're not in the folder with `environment.yml`. See step 2. |
| `No space left on device` | Free up disk space (you need about 4 GB), then run `conda clean --all` and try again. |
| `ModuleNotFoundError: No module named 'numpy'` in Jupyter | Jupyter was started without activating `srmp`. Stop it (Ctrl + C), run `conda activate srmp`, then `jupyter lab` again. |
| `FileNotFoundError: data/gaia_50pc.csv` | The notebook isn't in the `tutorial` folder next to `data`. Keep the folder structure as it came, and run the setup cell at the top of the notebook. |
| Browser doesn't open | Copy one of the `http://localhost:8888/...` links printed in the terminal into your browser. |
