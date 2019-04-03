# vmware_make-vmnet.ko-failed-error-2
Makefile:1454: recipe for target '_module_/tmp/modconfig-IDZcfV/vmnet-only' failed
make[1]: *** [_module_/tmp/modconfig-IDZcfV/vmnet-only] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.4.0-144-generic'
Makefile:120: recipe for target 'vmnet.ko' failed
make: *** [vmnet.ko] Error 2
make: Leaving directory '/tmp/modconfig-IDZcfV/vmnet-only'
Unable to install all modules.  See log for details.

# Steps that worked for me on VMWARE Workstation
mkdir ./tmp
cd ./tmp/
wget https://github.com/mkubecek/vmware-host-modules/archive/workstation-14.1.1.tar.gz
tar xzf workstation-14.1.1.tar.gz
cd vmware-host-modules-workstation-14.1.1/
tar -cf vmmon.tar vmmon-only
tar -cf vmnet.tar vmnet-only
cp -v vmmon.tar vmnet.tar /usr/lib/vmware/modules/source/
sudo cp -v vmmon.tar vmnet.tar /usr/lib/vmware/modules/source/
sudo vmware-modconfig --console --install-all

