# Introduction

Original source code retrieved from (the link is broken): http://creckmodeling.chem.polimi.it/openfoam.html - the current version should be here: http://www.opensmoke.polimi.it/

A bit more information about these modifications: http://www.cfd-online.com/Forums/blogs/wyldckat/1280-libopensmoke-making-work-once-again-openfoam.html

## Notes

*   For using with OpenFOAM 2.2 and 2.3, please check the `flameletModel` variant of libOpenSMOKE by Tobias Holzmann: https://bitbucket.org/shor-ty/flameletmodel/overview

# Installation
## Prerequisites
Firstly, you need the GNU Scientific Library:

*   On Ubuntu, install GSL by simply running:

        sudo apt-get install gsl-bin libgsl0-dev

*   To build your own GSL, read the section "Compilation and Installation" on the [doc/UserGuide.pdf](libOpenSMOKE/blob/master/doc/UserGuide.pdf?raw=true "User Guide") document.

    Keep in mind that after you build your own GSL, doing `git clone` and before running `Allwmake`, edit that file `Allwmake` and change the path `$HOME/gsl` to your own installation path of GSL:

        export GSL_INST_DIR="$HOME/gsl"

*   In case you want to build applications and libraries based on `libOpenSMOKE`, without running `Allwmake`, then you need to add to your `~/.bashrc` one of the following lines:

        export GSL_INST_DIR="$HOME/gsl"
        alias gsl4smo='export GSL_INST_DIR="$HOME/gsl"'

    If you choose the second line, then every time you start a new terminal and build libOpenSMOKE applications, then you'll have to run the command:

        gsl4smo

## Installing `libOpenSMOKE`
To use the build with OpenFOAM 1.7.x (maybe works with 1.7.0 and 1.7.1), simply run:

    git clone https://github.com/wyldckat/libOpenSMOKE.git
    cd libOpenSMOKE
    ./Allwmake

To build with OpenFOAM 2.0.x or 2.1.x or above, before running `Allwmake`, check which versions exist by running:

    git branch -a

For example, if it shows `remotes/origin/v2.0.x`, then run these steps:

    git checkout v2.0.x
    ./Allwmake

The binaries will be installed in your own user folders, so please DO NOT INSTALL AS ROOT! To find out which are your own user folders for binaries, run the following commands:

    echo $FOAM_USER_LIBBIN
    echo $FOAM_USER_APPBIN

# Notes
*   The files on the folder `utilities/exe` are static binaries. I don't know where the original source code is, so you better ask the authors at http://creckmodeling.chem.polimi.it/openfoam.html

*   Secondly, those binaries in the folder `utilities/exe` are 64 bit only!! Also known as x86_64. You check if your system is compatible by running:

        uname -m

# Tutorials

The following list are the scripts available in the `tutorials` folder:

    rhoSimpleFoamPostProcessorSoot2E/KentHonneryPostProcessing/Allrun
    rhoSimpleFoamFlamelets/Sandia_COH2N2/Allrun
    rhoSimpleFoamFlamelets/Sandia_HE0/Allrun
    rhoSimpleFoamFlamelets/KentHonnery/Allrun
    LookUpTable_Assembling/Step01/Run.sh
    LookUpTable_Assembling/Step02/Run.sh

To run either one of them, go into the folder of where the script is and run it with `./` preppended to the name. For example:

    cd rhoSimpleFoamFlamelets/Sandia_COH2N2
    ./Allrun

For more information, see:
*   The user guide available at [doc/UserGuide.pdf](libOpenSMOKE/blob/master/doc/UserGuide.pdf?raw=true "User Guide") document.

*   The thread at [CFD-Online](http://www.cfd-online.com) where this library is being discussed: [libOpenSMOKE in the sub-forum OpenFOAM/Programming & Development](http://www.cfd-online.com/Forums/openfoam-programming-development/99645-libopensmoke.html)
