# What is it
A simple script to handle and run different installed versions of wine.

# Installation
For easier access, directly put the script in the **/usr/local/bin** directory.

```
git clone https://github.com/Intoxx/wines.git
```
```
cd wines
```
```
sudo cp wines /usr/local/bin
```

# Configuration
Edit the **wines** script, go at the top of it and find the following lines :
```sudo vim /usr/local/bin/wines```
`BUILDS["default"]="/opt/wine-5.6-staging-improved-amd64"`
`BUILDS["staging-improved"]="/opt/wine-5.6-staging-improved-amd64"`

You **must replace** those lines with your build installations with the following format : `BUILDS["<WINE_BUILD_NAME>"]="<WINE_BUILD_PATH>"`
Note that the `default` **WINE_BUILD_NAME** is a special name telling the script to use that build if no build has been specified *(see the following)*.

## Example configuration
`BUILDS["proton"]="/home/intoxx/wine-builds/proton-5.0.2"`

## Example usage
`wines proton winecfg // will start winecfg with the proton build and default wine prefix`
`wines proton /my/path/to/Wow.exe // will start Wow.exe with the proton build and default wine prefix`
`wines /my/path/to/Wow.exe // Won't work because you didn't create a "default" build to be used when we don't supply any`


# How
Usage: wines [build] <binary path | binary name>
Example: wines 
