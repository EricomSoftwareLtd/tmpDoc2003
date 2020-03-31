***************************
How To Update CentOS Kernel
***************************

When using CentOS, the Kernel should be updated to 4.4.

To update the kernal, follow these steps: 

1.  Check the current kernel version::

        uname –msr

2.  Update CentOS repositories::

        sudo yum –y update

3.  Enable the ELRepo repository::

        sudo rpm --import https://www.elrepo.org/RPM-GPG-KEY-elrepo.org
        sudo rpm -Uvh http://www.elrepo.org/elrepo-release-7.0-3.el7.elrepo.noarch.rpm

4.  List available kernels::

        yum list available --disablerepo='*' --enablerepo=elrepo-kernel

5.  Install the new kernel version to 4.4.203-LT (LT signifies a stable long-term support release)

        sudo yum --enablerepo=elrepo-kernel install kernel-lt

6.  Reboot and select the new kernel. After the machine is rebooted you can select the new kernel from a list (using the arrows) - then press Enter.

7.  Verify the machine functions as usuall

8.  Set the default kernel version:: 

        sudo vim /etc/default/grub

    Search for the line that says *GRUB_DEFAULT=X**, and change it to *GRUB_DEFAULT=0** (zero). Save. Recreate the kernel configuration::

        sudo grub2-mkconfig -o /boot/grub2/grub.cfg

9.  Reboot once more.

To continue with the requirements, go `here <../requirements.html#connectivity>`_.





       
     
    
    
    
    
