# BeeGFS Best Practices

The BeeGFS file system on the {{ site.cluster.name }} cluster is designed for parallel use and is shared by all users.

## Some general guidelines for optimum use of BeeGFS:
* Prefer fewer, large files over many small ones
* Users are strongly encouraged to keep the number of reads and writes to a single directory to a reasonable number
* If writing many files, spread them out over a number of directories including SGE output and error files
* Use local scratch (`/scratch`) when possible
* Don't include anything in /wynton in your default `LD_LIBRARY_PATH`

## Anaconda Python environments

* Using software in Anaconda environments from one's home directory results in many files being read, much better is to develop Anaconda-based software in a Singularity container.


## What to expect from a parallel file system
