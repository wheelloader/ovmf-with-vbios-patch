# ovmf-with-vbios-patch

Based on @marcosscriven's initial work.

Automates the build of a patched OVMF image to be used with QEMU for NVIDIA GPU PCI/VFIO Passthrough.

Additionally, adds support for Intel GVT-g / RAMFB, which finally allows emulating a hybrid GPU setup (Optimus).

Tested and confirmed to work on Dell XPS 15 (9570).

You can try to use Github Actions. Here is what I set up. Firstly, fork it. Then, upload your ROM to roms/ directory. After that go to bin/build.sh change gtx_1050_ti_mobile.rom at the end of the 5th line to the file name of the rom that you have just uploaded. Then go to the "Actions" tab follow there to activate the workflow since it is disabled by default on forks. If nothing started just make a dummy commit by adding new line to README.md. After that you can see the progress on actions tab. It should take slightly less than 10 minutes. After completion a zip file will show up on "Artifacts". Download it and extract them somewhere. Then on the libvirt xml of the VM, set "loader" to path to OVMF_CODE.fd and "nvram" to path to OVMF_VARS.fd. The file OVMF.fd is not used.
