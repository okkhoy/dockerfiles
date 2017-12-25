# Docker - Python ML Research

A `dockerfile` for unified research environment, focusing on machine learning in Python (and R).

## Design considerations

- We use `conda` based Python 2.7.14 version. It is easy to change to python 3.6.3 by changing 2 lines in the `RUN` command.
- We pin the followin packages:
| Package      | Version|
|--------------|--------|
| numpy        | 1.13.3 |
| scipy        | 1.0.0  |
| scikit-learn | 0.19.1 |
| statsmodels  | 0.8.0  |
| matplotlib   | 2.0.2  |
| pandas       | 0.21.1 |
| r            | 3.4.1  |
| conda        | 4.3.31 |
- These are the latest (except `conda`) versions of respective packages as of Dec 25, 2017.
- We don't do a generic `conda update *` as we want the environment to be stable and consistent across all machines.
- We build the container off a Ubuntu 14.04.5 base image. 
  - We avoid Ubuntu 16.04 to support our legacy Python2 code base off the box.

