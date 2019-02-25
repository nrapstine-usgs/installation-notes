## Installing `fineRADstructure` on Yeti 

Login to Yeti.

Download the fineRADstructure repository.

```
git clone https://github.com/millanek/fineRADstructure.git
cd fineRADstructure
```

Load GCC module:

```
module load gcc/4.9.3
```

The installation requires an autotolls version 1.14. 

Check the Yeti version:

```
aclocal --version
```

You should see that Yeti has 1.11.1 autotools version. So, we have to edit `configure` file to specify 1.11 version instead of 1.14 otherwise the make step will throw an autotools version error:

```
vi ./configure
```

Change the line that reads `am__api_version='1.14'` to be:

```
am__api_version='1.11'
```

(Note, this is line 1881. If you are using vi editor, you can jump to that line in **command** mode by typing `:1881` then `enter` or search by typing `/` , followed by `1.14` then `enter`. Once you found the correct line in the file, press `i` to switch vi to **insert** mode and edit the version number. To save and exit the file, press `Esp` then type `:wq` and you should get back to the command line.)



Now, we are ready to install:

```
mkdir m4
./configure --prefix=$HOME/opt/fineRADstructure
make
```

Add the executable location path to your `bash_profile`:

```
vi ~/.bash_profile
```

Add this line to the end of the file:

```
export PATH=~/opt/fineRADstructure/bin:$PATH
```

Save, exit and source your bash_profile:

```
source ~/.bash_profile
```

Now, you can run from anywhere on Yeti:

```
finestructure
RADpainter 
```

