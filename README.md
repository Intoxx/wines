# What
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
Edit the **wines** script :
```
sudo vim /usr/local/bin/wines
```
Go at the top of it and find the following lines :
```
BUILDS["default"]="/opt/wine-5.6-staging-improved-amd64"
BUILDS["staging-improved"]="/opt/wine-5.6-staging-improved-amd64"
```

You **must replace** those lines with your build installations while following the current format : 
```
BUILDS["<WINE_BUILD_NAME>"]="<WINE_BUILD_PATH>"
```
Note that the `default` **WINE_BUILD_NAME** is a special name telling the script to use that build if no build has been specified.

## Example configuration

### Example 1
```
BUILDS["proton"]="/home/intoxx/wine-builds/proton-5.0.2"
```

Usage :

```
wines proton winecfg // Will start winecfg with the proton build and default wine prefix
```
```
wines proton /path/to/Wow.exe // Will start Wow.exe with the proton build and default wine prefix
```
```
wines /path/to/Wow.exe // Won't work because you didn't create a "default" build to be used when we don't supply any
```

### Example 2
```
BUILDS["default"]="/home/intoxx/wine-builds/wine-staging-improved-5.8"
BUILDS["proton"]="/home/intoxx/wine-builds/wine-proton-5.0.2"
BUILDS["wine-staging-5.6"]="/home/intoxx/wine-builds/wine-staging-5.6"
```

Usage :

```
wines
```

# Supported environment variables
At any time, you can pass the following variables to the executable to override the default ones, passing anything not listed here will still be effective but won't be logged to the output.

* WINEPREFIX
* WINEDEBUG
* STAGING_WRITECOPY
* STAGING_SHARED_MEMORY
* DXVK_LOG_LEVEL
* RADV_PERFTEST

## Example
```
WINEPREFIX=/home/wine-prefixes/wow_1 WINEDEBUG=-all wines staging-improved /path/to/WoW.exe // Will run Wow.exe with specific profile and wine won't log anything to the output.
```

