#### Intalling 7zip on Yeti

Download the binary file to your local computer:

```bash
wget https://sourceforge.net/projects/p7zip/files/p7zip/16.02/p7zip_16.02_x86_linux_bin.tar.bz2
```

Uncompress then copy to your home directory to Yeti:

```bash
scp -r p7zip_16.02/ nrapstine@yeti.cr.usgs.gov:~/
```

Then login to Yeti.

Copy the p7zip directory to another user's home:

```bash
sudo cp -r p7zip_16.02 /home/username/
```

Then change to their user: 

```bash
sudo su - username
```

Add the path to their bash profile:

```bash
vi ~/.bash_profile
```

Add the following line:

```vi
PATH=$PATH:$HOME/p7zip_16.02/bin
```

Then source the bash profile:

```bash
source ~/.bash_profile
```

Now, the executable `7z` is available anywhere on Yeti. 