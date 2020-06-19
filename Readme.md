As a group we are committed to developing software and models that are easily shared, initially within the group but with a view of wider usage in the future.

To facilitate this it's essential that we all work in the same programming language - which for us is python - and in a common package environment. This is conveniently achieved through the use of python environment management software called conda (https://conda.io/en/master/).

We also like to use common plotting styles, which is achieved through a matplotlib style file.

# The BSGIP conda environment

We strongly encourage all team members to develop within a unix environment (linux or mac). The recommended avenue for Windows users is to run Windows 10 and install ubuntu through Windows Subsystem for Linux (https://docs.microsoft.com/en-us/windows/wsl/install-win10).

The following documentation is written for linux - a mac user can provide a parallel document for mac.

## Installing miniconda

Conda is available through two packages: Anaconda and miniconda. This document uses miniconda as this is more lightweight than anaconda.

Download linux 64-bit installer from https://conda.io/en/master/miniconda.html

Run the installer from the linux terminal

$ bash Miniconda3-latest-Linux-x86_64.sh

Close that terminal and open a new one.

## Getting the BSGIP environment

Download our shared environment definition. To do this in your terminal go to your preferred directory (eg where you installed miniconda) and run

$ wget https://raw.githubusercontent.com/bsgip/conda_environment/master/BSGIP_conda.yml

Now create the environment from the downloaded file

$ conda env create -f BSGIP_conda.yml

## Testing your environment installation

Before working on BSGIP projects you must ensure that you've activated the BSGIP environment (which is creatively named bsgip). This is done in the terminal as

$ conda activate bsgip

      

To test the installation, start python

$ python3

Inside python try loading a test package, eg.

\>>> import cyipopt

If there are no errors then you should be sweet.

## Updating our shared environment

If/when you find that you need addition packages feel free to add these. To do this, make sure you've activated the BSGIP environment, then simply 

$ conda install package_name

These packagesA will then become a part of your BSGIP environment (so they'll be there next time you activate that environment).

If/when you want another team member to use your program that depends on new packages you should update the shared BSGIP_conda.yml file.

To do this, make sure you're in the bsgip environment, then export the updated yml file (ignore the middle section of this command, it just removes unimportant path information)

$ conda env export --no-build | grep -v "^prefix: " > BSGIP_conda.yml

Now git clone the repository https://github.com/bsgip/conda_environment 

Override the BSGIP_conda.yml file

Commit your changes, and

Push them to github

## A Simple Guide to GIT

http://rogerdudler.github.io/git-guide/

# The BSGIP matplotlib style

## Getting the BSGIP style file

Download the file from:

$ wget https://raw.githubusercontent.com/bsgip/conda_environment/master/BSGIP_style.mplstyle

Move it to:

~/.config/matplotlib/stylelib/

## Using the style

At the top of python files that contain plots just add the following two lines:

plt.style.use('BSGIP_style')

colors = \[color\['color'] for color in list(plt.rcParams\['axes.prop_cycle'])]

and when you plot lines you can select from the BSGIP brand colors by using the color keyword argument 

plt.plot(... , color=colors\[2])
