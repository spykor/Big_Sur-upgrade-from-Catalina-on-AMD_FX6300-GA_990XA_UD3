# Big_Sur-upgrrade-from-Catalina-on-AMD_FX6300-GA_990XA_UD3
 Succes!!! Upgrade from Catalina to Big Sur on a FX-6300 cpu and Gigabyte 990XA-UD3 motherboard, with audio and everything

 System Configuration

     Gigabyte 990XA-UD3 motherboard

     FX-6300 CPU

     8GB RAM

     Gigabyte (Nvidia) GT730 Silent 2GB graphics card (metal compatible)

     Embedded Etron EJ168 USB contollers for USB 2.0 and USB 3.0 (not compatible with macOS)

     Discrete (VIA based) USB 3.0 controller compatible with macOS

     Various HDDs and SSDs with Windows 10, Linux and OS X / macOS systems (Sierra, Catalina)

 Background

 After succesfully installing and running Catalina on the above system, it was time to try and upgrade to Big Sur.

 All the attempts following install instructions for AMD FX type systems failed, either because the Opencore would not boot properly or the install process hung on kernel panic errors or some other obsure errors.

 Finally the solution came from a post on https://forum.amd-osx.com site.

 The EFI provided by the author of the post worked flawlessly with just a minor adjustment for the number of CPUs in Kernel patches as per instructions in https://github.com/AMD-OSX/AMD_Vanilla/tree/master

 Prerequisites

   Apropriate SSDTs, kexts and patches for AMD FX CPU (SSDT-EC.aml, SSDT-USBX.aml, SSDT-XOSI.aml, Lilu.kext, VirttuslSMC.kext, etc.). Get info and necessary files from https://dortania.github.io/OpenCore-Install-Guide/AMD/fx.html#starting-point

   AMD Vanilla Kernel patches from https://github.com/AMD-OSX/AMD_Vanilla/tree/master

   Opencore package https://mackie100projects.altervista.org/download-opencore-configurator/

   All necessary files are included in the EFI folder provided in the given post: https://forum.amd-osx.com/index.php?threads/success-asus-sabertooth-990fx-r2-0-fx-8350-nvidia-gtx-690-oc-0-7-6-big-sur-11-6-2-monterey-12-1.2400/

   Prepare the Catalina installation for the Big Sur upgrade. Edit the OC config file to match the prerequisites for Big Sur. Edit the config.plist to the appropriate system model. I chose iMac Pro (iMacpro1,1). Upgrade the OpenCore bootloader to version 0.7.6 and download and install OpenCore configurator to match the OpenCore version.

   Open the above downloaded EFI folder and using the ProperTree editor make the appropriate adjustments in the config.plist regarding the number of cores of the CPU (06 in this case) for the three "algrey - Force cpuid_cores_per_package" patches and alter the Replace value only.

   Changing B8000000 0000/BA000000 0000/BA000000 0090* to B8 CoreCount 0000 0000/BA CoreCount 0000 0000/BA CoreCount 0000 0090* substituting CoreCount with the hexadecimal value matching your physical core count.

Instructions can be found in https://kaneis.wordpress.com/2022/06/15/success-big-sur-on-amd-fx-6300-ga-990xa-ud3-everything-working-almast-including-audio-voodoohda-kext-in-library-extensions/

 Post Install

 Reboot into the new system disk (Big Sur)

 Everything (but Sleep and proper Shutdown) should be working except Audio.
 ** Fix Audio / VoodooHDA in Big Sur**

 To fix audio in Big Sur (using VoodooHDA kext) follow the instructions from this post https://kaneis.wordpress.com/2022/06/13/how-to-fix-voodoohda-audio-for-amd-fx-cpus-ga-990xa-ud3-in-big-sur/
