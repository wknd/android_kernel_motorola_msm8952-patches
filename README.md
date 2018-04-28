# android_kernel_motorola_msm8952-patches
This repo houses a series of patches to the lineage OS motorola msm8952 kernel to get nethunter working.

Its a work in progress.


### List of patches

##### android-keyboard-gadget.patch
Patch for [https://github.com/pelya/android-keyboard-gadget](https://github.com/pelya/android-keyboard-gadget)
It makes the phone act as a HID device, both mouse and keyboard.
TODO: gotta add stuff to also tweak selinux I guess.

##### drivedroid patch
This is already in the default lineage os kernel, no further action required.

##### wireless patches
I based this off the changes made in the [kali-wifi-injection-3.18 patch](https://github.com/offensive-security/kali-arm-build-scripts/blob/master/patches/kali-wifi-injection-3.18.patch). This one seemed to have slightly more in it than the 3.12 one so we'll give it a try and hope nothing explodes.

### Apply a patch

To apply a patch, first make sure you got all your sources by following the instructions to [build lineage os])(https://wiki.lineageos.org/devices/athene/build).  
Then apply the patches before the ```brunch``` step by going to the kernel source directory and using:
```
patch -p1 < location/of/patch/file.patch
```
The -p1 will strip off the first / and everything before it inside the patchfile. so ```a/net/mac80211/tx.c``` becomes ```net/mac80211/tx.c```, meaning if you are in the root of the kernel folder for your device, it'll patch the right files.

For our motorola G4 plus, the location of this kernel will be ```wherever/lineage/kernel/motorola/msm8952/```.

Make sure to go back to the proper build location (```wherever/lineage/```) before ```brunch```.
