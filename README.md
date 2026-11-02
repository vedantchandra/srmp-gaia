# SRMP 2026: Planets and binary stars in Gaia

Materials for our Gaia project: tutorial notebooks, slides and data.

## Running the notebooks

Pick one. You don't need to install anything for the first two.

**Google Colab** (needs a Google account). Click a badge. Colab opens the notebook in your
browser. To keep your work, use **File → Save a copy in Drive** before you start. The Gaia notebook
downloads its data files by itself.

- Python basics: [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/vedantchandra/srmp-gaia/blob/main/tutorial/python_basics.ipynb)
- A first look at Gaia data: [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/vedantchandra/srmp-gaia/blob/main/tutorial/gaia_first_look.ipynb)

**GitHub Codespaces** (needs a free GitHub account). A full coding setup in your browser, with
every file in this repository:
[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/vedantchandra/srmp-gaia).
The first start takes a few minutes. Then open a notebook from the file list on the left (pick the
Python 3.12 kernel if it asks). Your files are kept between sessions. When you're done, stop the
codespace, because it uses up your free monthly hours while it runs.

**Your own laptop.** Follow [SETUP.md](SETUP.md). This is the best option for longer projects.

## What's here

```
tutorial/
    python_basics.ipynb       Python, numpy, matplotlib, scipy, astropy
    gaia_first_look.ipynb     loading and plotting real Gaia data
    data/                     saved copies of the data used in the Gaia notebook
slides/
    gaia_intro.pdf            introduction to the Gaia mission
    gaia_planets.pdf          finding planets with Gaia, and binary-star impostors
SETUP.md                      installing Python on your own laptop
environment.yml               the packages, for a conda install on your laptop
requirements.txt              the same packages, for Codespaces and pip
```

The data files in `tutorial/data/`:

- `gaia_50pc.csv`: Gaia DR3 stars with parallax > 20 mas and `parallax_over_error` > 10
  (the query is in the Gaia notebook, section 1)
- `gaia_dr3_orbits_100pc.csv`: Gaia DR3 astrometric orbit solutions (`nss_two_body_orbit`) with
  parallax > 10 mas (the query is in the Gaia notebook, section 7)
- `exoplanets.csv`: the NASA Exoplanet Archive `pscomppars` table, downloaded November 2026

Images in `slides/figures/images/` are from Wikimedia Commons: Gaia spacecraft and Milky Way map
(ESA, CC BY-SA 3.0 IGO), Gaia scanning diagram (Space Travel Blog / R. M. Jansone / M.-L. Aru,
CC BY 4.0).
