# PyGame

conda create --name monopoly python=3.9
conda install -c cogsci pygame

Collecting package metadata (current_repodata.json): done
Solving environment: failed with initial frozen solve. Retrying with flexible solve.
Solving environment: failed with repodata from current_repodata.json, will retry with next repodata source.
Collecting package metadata (repodata.json): done
Solving environment: failed with initial frozen solve. Retrying with flexible solve.
Solving environment: | 
Found conflicts! Looking for incompatible packages.
This can take several minutes.  Press CTRL-C to abort.
failed

UnsatisfiableError: The following specifications were found
to be incompatible with the existing python installation in your environment:

Specifications:

  - pygame -> python[version='2.7.*|3.5.*']

Your python: python=3.9

If python is on the left-most side of the chain, that's the version you've asked for.
When python appears to the right, that indicates that the thing on the left is somehow
not available for the python version you are constrained to. Note that conda will not
change your python version to a different minor version unless you explicitly specify
that.

$ pip install pygame
Collecting pygame
  Downloading pygame-2.1.0-cp39-cp39-macosx_10_9_x86_64.whl (5.2 MB)
     |████████████████████████████████| 5.2 MB 701 kB/s 
Installing collected packages: pygame
Successfully installed pygame-2.1.0

