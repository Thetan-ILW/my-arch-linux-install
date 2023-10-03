# Spyware 11 VM
I am using it to play 0 games, because I dont know what to play.  
Had to install tons of packages, find them on internet.  
Performance is great, better than wine by 1 millon times.  

### Based videos:  
https://www.youtube.com/watch?v=rA5iLjRTiZQ - Good and simple explanation.  
https://www.youtube.com/watch?v=29S7KReCdu8 - Good XML settings.  
https://www.youtube.com/watch?v=uOuzFd8Gd2o - EZ guide for looking glass.  

### GPU Passthrough
Just use this tool: https://github.com/uwzis/GPU-Passthrough-Manager  
Passthrough only the GPU, don't touch audio (buy a DAC).

### VirtManager
Be sure to have QEMU/KVM connection. LXC will never work. 

### XML
Windows will see that it's in a virtual machine, hiding this will cause drops to 10 fps in games when moving mouse.  
Huge pages are on. I set the ammout of them to 5150 on host.  
Because I use VirtIO, drivers should be installed on guest in order to internet and disk to work. Download them there: https://github.com/virtio-win/virtio-win-pkg-scripts/blob/master/README.md

### Audio
I use `https://github.com/duncanthrax/scream` for audio. 
If it throws an error, then set system time to 4th june 2023.  
Compile reciever with pulseaudio headers.  
Run with `scream -i virbr0`

### Kernel parameters
`kvm.ignore_msrs=1` Windows installer can't run without this  
`nitcall_blacklist=sysfb_init` I think I can remove this, not sure which problem it fixes, I dont remember  
`rd.driver.pre=vfio-pci` GPU passthrough  
`amd_iommu=on` GPU passthrough  