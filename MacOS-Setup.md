# Setting Up A MacOS (Monterey) Virtual Machine in VirtualBox Guide (In Windows)

## Downloading the ISO

- Go to https://www.mediafire.com/file/4fcx0aeoehmbnmp/macOS+Monterey+by+Techrechard.com.iso/file to download the iso.

## 1) First I'm going to assume you downloaded VirtualBox already

## 2) Click new and give it a name. (I named mine `MacOS Monterey`):

   - For type you want to select `Mac OS X`
   - For version choose `macOS 10.13 High Sierra (64-bit)` 
   - For memory, I have my VM set to `8000MB`
   - Select `Create a virtual hard disk now`
   - Select `VDI (VirtualBox Disk Image)`
   - Select `dynamically allocated`
   - For file location and size, you need a minimum of `50.00 GB` but with XCode too I bumped it up to `70.00GB` then hit create.
   
## 3) Adjusting the VM Settings:

   - Before you run your VM open up the `Settings` menu that is next to the blue `New` button.
   - Under system:
      - Uncheck `Floppy`
      - Still in system but under the processor tab, give it `2 CPU` cores. 
   - Under the display tab give it `128 MB` of video memory.
      - You can change this later to `256 MB` later if you want. 
   - For storage: 
      - Click on the empty disk
      - Then next to the dropdown menu there is another disk. Select `Choose/Create virtual optical disk`. 
      - Select `Add` and select your ISO that you downloaded then press `Choose`
   - Next you'll need to run some commands so open up command prompt or something (This section assumes you name it the same thing as me, if you didn't just replace "MacOS Monterey" with what you named your VM:
      ```
      1) cd C:\Program Files\Oracle\VirtualBox
      2) VBoxManage.exe modifyvm "MacOS Monterey" --cpuidset 00000001 000306a9 04100800 7fbae3ff bfebfbff
      3) VBoxManage setextradata "MacOS Monterey" "VBoxInternal/Devices/efi/0/Config/DmiSystemProduct" "MacBookPro11,3"
      4) VBoxManage setextradata "MacOS Monterey" "VBoxInternal/Devices/efi/0/Config/DmiSystemVersion" "1.0"
      5) VBoxManage setextradata "MacOS Monterey" "VBoxInternal/Devices/efi/0/Config/DmiBoardProduct" "Mac-2BD1B31983FE1663"
      6) VBoxManage setextradata "MacOS Monterey" "VBoxInternal/Devices/smc/0/Config/DeviceKey" "ourhardworkbythesewordsguardedpleasedontsteal(c)AppleComputerInc"
      7) VBoxManage setextradata "MacOS Monterey" "VBoxInternal/Devices/smc/0/Config/GetKeyFromRealSMC" 1
      ```
 ## 4) Starting the VM:
  
   - Hit the `Start` Button
   - Choose your language
   - Open up `Disk Utility`
      - Select `VBOX HARDISK Media` 
      - Click `Erase` that is to the right of the partition button. A menu will open up.
      - Name it `MacOS` and hit `Erase`.
      - Then press `Done` and go back. 
   - Next select `Install macOS Monterey` and go through the installation steps. 
      - For `Migration Assistant` I just selected `Not now`
      - For signing in with your Apple ID, I just selected `Set up Later` I don't know if even works and you can sign in. 
      - I turned off location services and unchecked the `Share Mac Analytics with Apple`
      - `Set Up Later` for Screen Time
        
 ## 5) Download XCode (Really hope you can figure this one out. Make sure you download `XCode 13.1` if you're getting it from the `developer.apple.com` website or else it won't be compatible. 
        
 ## 6) (Optional) Adjusting screen resolution and VRAM:
   
   - Since you can't install guest additions on this version of MacOS apparently or unless you can and I'm dumb you will just have to change the resolution manually. 
   
   - Open up command prompt once again and `cd C:\Program Files\Oracle\VirtualBox`
   - Run `VBoxManage setextradata "MacOS Monterey" VBoxInternal2/EfiGraphicsResolution "1920x1080"` or adjust to your desired resolution
   - To increase VRAM run this command: `VBoxManage modifyvm "MacOS Monterey" --vram 256`
      
##  7) Troubleshooting: 
   
   - If your VM doesn't run and you have a Ryzen CPU try running this command to possibly fix the problem: 
       - `VBoxManage modifyvm "MacOS Monterey" --cpu-profile "Intel Core i7-6700K"`
   - If your VM keeps "panic rebooting" try running this commmand: 
       - `VBoxManage setextradata "MacOS Monterey" "VBoxInternal/TM/TSCMode" "RealTSCOffset"`
   - Other than that I have no idea how to help you and the internet will probably be your best bet. 

   
        
   
      
   
   




