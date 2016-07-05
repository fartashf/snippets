Installing Package in Debian/Ubuntu Repository for a Single User
================================================================
On shared computers, e.g. compute servers, individual users might not have root 
access to install packages. Here are the steps:

* `dpkg-query -s <PKG_NAME>`: check if it is already installed
* `apt-get download <PKG_NAME>`: download the right version of the deb package 
  from the repository
* `dpkg -x <DEB_NAME> $HOME/.local/`: extract files in `.local`, files will be 
  usually be inside `.local/usr`, so you need to do `cp -r .local/usr/* 
  .local/`.
* `export LD_LIBRARY_PATH=$HOME/.local/lib/`: add to the library search path.

There is of course `make install --prefix` if you are installing from source 
and `pip install --user` when it is a python package.
