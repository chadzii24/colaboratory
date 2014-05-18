# Experimental IPython Frontend
This project contains an experimental IPython front end, which
integrates Google Drive's realtime API, and also features in-browser
execution using Chrome's Native Client technology.  It also features
a number of other new experimental features.

## Setup
First create a directory to install this repo, e.g.
```
mkdir ~/experimental_frontend
cd ~/experimental_frontend
```

then clone this repo
```
git clone -b v2 https://github.com/google/colaboratory
```

then clone the Google Closure library repo,
```
git clone https://github.com/google/closure-library
```
 
Set build tools to executable
```
chmod +x closure-library/closure/bin/build/*
chmod +x colaboratory/*.sh
```

## Installing the Web App
Run
```
cd colaboratory
./install
```
to install the Web App (this creates an IPython profile which uses
IPython to serve the static web content for the new front end)

NOTE: both the install and run scripts
must be run from the colaboratory directory, e.g. running ```colaboratory/install.sh```
will not work.

Start IPython notebook:
```
./run
```
This launches IPython using the profile created in the install step.

Navigate to ```http://127.0.0.1:8888/static/frontend/welcome.html``` in
browser.

## Installing the Chrome App
Run
```
cd colaboratory
./install_chrome.sh
```
This creates an unpacked Chrome App, in the ```build_chrome/``` directory.

NOTE: this script must be run from the colaboratory directory, e.g. running ```colaboratory/install.sh```
will not work.

NOTE: The file ```pydata_pnacl.tar``` is too big for GitHub, and must be manually copied from
naclports to ```chrome/pnacl/```.

To install this app in Chrome, follow the instructions for installing an unpacked extension
(extensions are apps for these purposes), at https://developer.chrome.com/extensions/getstarted#unpacked.
The extension is located in ```colaboratory/build_chrome/```.


## Custom Python libraries
To add custom python libraries, do the following prior to running ```./install```.

First, add custom python libraries to the ```colaboratory/modules/```
directory.  Then, modify the file  ```colaboratory/build/profile_default/startup/startup.py```
to import these modules.  E.g. add the module ```myModule.py```
to ```colaboratory/modules/```, then add ```import myModule```
to ```startup.py```.
