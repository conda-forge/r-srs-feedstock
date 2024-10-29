About r-srs-feedstock
=====================

Feedstock license: [BSD-3-Clause](https://github.com/conda-forge/r-srs-feedstock/blob/main/LICENSE.txt)

Home: https://CRAN.R-project.org/package=SRS

Package license: BSD-3-Clause

Summary: Analysis of species count data in ecology often requires normalization to an identical sample size. Rarefying (random subsampling without replacement), which is a popular method for normalization, has been widely criticized for its poor reproducibility and potential distortion of the community structure. In the context of microbiome count data, researchers explicitly advised against the use of rarefying. An alternative to rarefying is scaling with ranked subsampling (SRS). SRS consists of two steps. In the first step, the total counts for all OTUs (operational taxonomic units) or species in each sample are divided by a scaling factor chosen in such a way that the sum of the scaled counts Cscaled equals Cmin. In the second step, the non-integer Cscaled values are converted into integers by an algorithm that we dub ranked subsampling. The Cscaled value for each OTU or species is split into the integer part Cint  (Cint = floor(Cscaled)) and the fractional part Cfrac (Cfrac = Cscaled - Cints). Since the sum of Cint is smaller or equal to Cmin, additional  delta C = Cmin - the sum of Cint counts have to be added to the library to reach the total count of Cmin. This is achieved as follows. OTUs are ranked in the descending order of their Cfrac values. Beginning with the OTU of the highest rank, single count per OTU is added to the normalized library until the total number of added counts reaches delta C and the sum of all counts in the normalized library equals Cmin. When the lowest Cfrag involved in picking delta C counts is shared by several OTUs, the OTUs used for adding a single count to the library are selected in the order of their Cint values. This selection minimizes the effect of normalization on the relative frequencies of OTUs. OTUs with identical Cfrag as well as Cint are sampled randomly without replacement. See Beule & Karlovsky (2020) <doi:10.7717/peerj.9593> for details.

Current build status
====================


<table><tr><td>All platforms:</td>
    <td>
      <a href="https://dev.azure.com/conda-forge/feedstock-builds/_build/latest?definitionId=16052&branchName=main">
        <img src="https://dev.azure.com/conda-forge/feedstock-builds/_apis/build/status/r-srs-feedstock?branchName=main">
      </a>
    </td>
  </tr>
</table>

Current release info
====================

| Name | Downloads | Version | Platforms |
| --- | --- | --- | --- |
| [![Conda Recipe](https://img.shields.io/badge/recipe-r--srs-green.svg)](https://anaconda.org/conda-forge/r-srs) | [![Conda Downloads](https://img.shields.io/conda/dn/conda-forge/r-srs.svg)](https://anaconda.org/conda-forge/r-srs) | [![Conda Version](https://img.shields.io/conda/vn/conda-forge/r-srs.svg)](https://anaconda.org/conda-forge/r-srs) | [![Conda Platforms](https://img.shields.io/conda/pn/conda-forge/r-srs.svg)](https://anaconda.org/conda-forge/r-srs) |

Installing r-srs
================

Installing `r-srs` from the `conda-forge` channel can be achieved by adding `conda-forge` to your channels with:

```
conda config --add channels conda-forge
conda config --set channel_priority strict
```

Once the `conda-forge` channel has been enabled, `r-srs` can be installed with `conda`:

```
conda install r-srs
```

or with `mamba`:

```
mamba install r-srs
```

It is possible to list all of the versions of `r-srs` available on your platform with `conda`:

```
conda search r-srs --channel conda-forge
```

or with `mamba`:

```
mamba search r-srs --channel conda-forge
```

Alternatively, `mamba repoquery` may provide more information:

```
# Search all versions available on your platform:
mamba repoquery search r-srs --channel conda-forge

# List packages depending on `r-srs`:
mamba repoquery whoneeds r-srs --channel conda-forge

# List dependencies of `r-srs`:
mamba repoquery depends r-srs --channel conda-forge
```


About conda-forge
=================

[![Powered by
NumFOCUS](https://img.shields.io/badge/powered%20by-NumFOCUS-orange.svg?style=flat&colorA=E1523D&colorB=007D8A)](https://numfocus.org)

conda-forge is a community-led conda channel of installable packages.
In order to provide high-quality builds, the process has been automated into the
conda-forge GitHub organization. The conda-forge organization contains one repository
for each of the installable packages. Such a repository is known as a *feedstock*.

A feedstock is made up of a conda recipe (the instructions on what and how to build
the package) and the necessary configurations for automatic building using freely
available continuous integration services. Thanks to the awesome service provided by
[Azure](https://azure.microsoft.com/en-us/services/devops/), [GitHub](https://github.com/),
[CircleCI](https://circleci.com/), [AppVeyor](https://www.appveyor.com/),
[Drone](https://cloud.drone.io/welcome), and [TravisCI](https://travis-ci.com/)
it is possible to build and upload installable packages to the
[conda-forge](https://anaconda.org/conda-forge) [anaconda.org](https://anaconda.org/)
channel for Linux, Windows and OSX respectively.

To manage the continuous integration and simplify feedstock maintenance
[conda-smithy](https://github.com/conda-forge/conda-smithy) has been developed.
Using the ``conda-forge.yml`` within this repository, it is possible to re-render all of
this feedstock's supporting files (e.g. the CI configuration files) with ``conda smithy rerender``.

For more information please check the [conda-forge documentation](https://conda-forge.org/docs/).

Terminology
===========

**feedstock** - the conda recipe (raw material), supporting scripts and CI configuration.

**conda-smithy** - the tool which helps orchestrate the feedstock.
                   Its primary use is in the construction of the CI ``.yml`` files
                   and simplify the management of *many* feedstocks.

**conda-forge** - the place where the feedstock and smithy live and work to
                  produce the finished article (built conda distributions)


Updating r-srs-feedstock
========================

If you would like to improve the r-srs recipe or build a new
package version, please fork this repository and submit a PR. Upon submission,
your changes will be run on the appropriate platforms to give the reviewer an
opportunity to confirm that the changes result in a successful build. Once
merged, the recipe will be re-built and uploaded automatically to the
`conda-forge` channel, whereupon the built conda packages will be available for
everybody to install and use from the `conda-forge` channel.
Note that all branches in the conda-forge/r-srs-feedstock are
immediately built and any created packages are uploaded, so PRs should be based
on branches in forks and branches in the main repository should only be used to
build distinct package versions.

In order to produce a uniquely identifiable distribution:
 * If the version of a package **is not** being increased, please add or increase
   the [``build/number``](https://docs.conda.io/projects/conda-build/en/latest/resources/define-metadata.html#build-number-and-string).
 * If the version of a package **is** being increased, please remember to return
   the [``build/number``](https://docs.conda.io/projects/conda-build/en/latest/resources/define-metadata.html#build-number-and-string)
   back to 0.

Feedstock Maintainers
=====================

* [@conda-forge/r](https://github.com/orgs/conda-forge/teams/r/)
* [@pschloss](https://github.com/pschloss/)

