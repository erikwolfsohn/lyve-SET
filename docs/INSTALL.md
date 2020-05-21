Installation
============

## Containers

Here are the methods for installing with either Docker or Singularity.

    docker pull staphb/lyveset:1.1.4f

    singularity build lyveset.1.1.4f.sif docker://staphb/lyveset:1.1.4f

Requirements
------------

* **Perl, multithreaded**
  * BioPerl
* **BLAST+**
* **Edirect** (for downloading of test data)
* **GIT**, **SVN** (for installation and updating)

### Other requirements

Usually these packages are installed, but if you have a totally fresh system, you might want to consider installing the following

* zlib
* curses
* zip/unzip
* build-essential

Some Perl modules are needed in earlier versions of Lyve-SET including v1.1.4f.

* File::Slurp
* URI::Escape

Quickie Installation
--------------------

1. Run `make install` while you are in the Lyve-SET directory. This step probably takes 10-20 minutes.
2. Update the path to include the scripts subdirectory. You can do this yourself if you are comfortable or run `make env`.
3. Update your current session's path: `source ~/.bashrc`

In-depth Installation
---------------------

Download the latest stable version from https://github.com/lskatz/lyve-SET/releases.  You can also roll the dice by getting the cutting edge version with git.

    tar -zxvf lyve-SET-1.1.4f.tar.gz
    cd lyve-SET-1.1.4f.tar.gz
    make install
    make env

Other Installation Options
------------
* `make install`
* `make install-optional` to install optional prerequisite software including bwa and snap
* `make env` - update `PATH` and `PERL5LIB` in the `~/.bashrc` file.
* `make check` - check and see if you have all the prerequisites
* `make test` - run a test phage dataset provided by CFSAN
* `make help` - for other `make` options
* `make clean` - clean up an old installation in preparation for a new installation

### Fine details

* `make install-*` - Many other installation options are available including but not limited to:
  * `make install-smalt`
  * `make install-CGP`
  * `make install-samtools`
* `make clean-*` - Every `make install` command comes with a `make clean` command, e.g.:
  * `make clean-CGP`

Upgrading
---------

### By stable releases
Unfortunately the best way to get the next stable release is to download the full version like usual, followed by `make install`.  If successful, then delete the directory containing the older version.

    cd ~/tmp
    wget https://github.com/lskatz/lyve-SET/archive/v1.1.4f.tar.gz
    tar zxvf release.tar.gz
    cd Lyve-SET
    make install # takes 10-20 minutes to download packages on broadband; install
    cd ~/bin
    rm -r Lyve-SET && mv ~/tmp/Lyve-SET .

### By `git`
    git pull -u origin master
    make clean
    make install
