.. Ethereum on ARM documentation documentation master file, created by
   sphinx-quickstart on Wed Jan 13 19:04:18 2021.

Download and Install
====================

There are 3 images available for **Raspberry Pi 4**, **Odroid M1** and **Rock 5B** (not available yet) boards.

Download
--------

**Raspberry Pi 4**

Download link:

ethonarm_22.04.00.img.zip_

.. _ethonarm_22.04.00.img.zip: https://ethereumonarm-my.sharepoint.com/:u:/p/dlosada/Ec_VmUvr80VFjf3RYSU-NzkBmj2JOteDECj8Bibde929Gw?download=1

You can verify the file with the following ``SHA256`` Hash:

``SHA256 fb497e8f8a7388b62d6e1efbc406b9558bee7ef46ec7e53083630029c117444f``

By running:

.. prompt:: bash $

  sha256sum ethonarm_22.04.00.img.zip

**Rock 5B**

Download link:

ethonarm_rock5b_22.07.00.img.zip_

.. _ethonarm_rock5b_22.07.00.img.zip: https://ethereumonarm-my.sharepoint.com/:u:/p/dlosada/EZEp3NlgoUJKpCoKRYLIVKMBtPGmFyy9lz__qdMKvc7xNw?download=1

You can verify the file with the following ``SHA256`` Hash:

``SHA256 a8ae4886564251c9f0abfa9dfb03fbe99872e97bafc25a3dc187d6565a6462d4``

By running:

.. prompt:: bash $

  sha256sum ethonarm_rock5b_22.07.00.img.zip

**Odroid M1**

Download link:

ethonarm_odroid_22.07.00.img.zip_

.. _ethonarm_odroid_22.07.00.img.zip: https://ethereumonarm-my.sharepoint.com/:u:/p/dlosada/EejUgF6sH55EoUY3Pc34jwEBMIwIxYmJYDUqfGp0TJ1Eyw?download=1



You can verify the file with the following ``SHA256`` Hash:

``SHA256 0be26b4ec9a3e8c0a328fdc175650daf1cd9ef339da2759a7b1601c3d6258cbb``

By running:

.. prompt:: bash $

  sha256sum ethonarm_odroid_22.07.00.img.zip


Flash 
-----

Insert the microSD in your Desktop / Laptop and flash the image.

.. note::
  If you are not comfortable with command line or if you are 
  running Windows, you can use Etcher_

.. _Etcher: https://www.balena.io/etcher/

Open a terminal and check your MicroSD device name running:

.. prompt:: bash $

   sudo fdisk -l

You should see a device named ``mmcblk0`` or ``sd(x)``.

.. warning::
  The ``dd`` command will completely erase your MicroSD device so make sure you are targeting 
  the correct one.

Unzip and flash the image (we are using here the Raspberry Pi 4 image):

.. prompt:: bash $

   unzip ethonarm_22.04.00.img.zip
   sudo dd bs=1M if=ethonarm_22.04.00.img of=/dev/mmcblk0 conv=fdatasync status=progress

Insert MicroSD
--------------

.. warning::
  The image will wipe out your USB SSD disk, so be careful if you already have data
  on it.

Insert de MicroSD into the board. Connect an Ethernet cable and attach 
the disk (make sure you are using a blue port which corresponds to USB 3).

Power on
--------

The Ubuntu OS will boot up in less than one minute and will start to perform the necessary tasks
to turn the device into a full Ethereum node.

.. warning::

  You need to wait for about 10-15 minutes to allow the script to install and configure all the software.

Log in
------

Once the device is available, You can log in through SSH or using the console (if you have a monitor 
and keyboard attached) using the ``ethereum`` account::

  User: ethereum
  Password: ethereum

Through SSH:

.. prompt:: bash $

  ssh ethereum@your_board_IP

.. tip::
  If you don't have a monitor with a keyboard you can get your board ``IP`` address by looking into your router 
  or using some kind of network tool such as ``fping`` or ``nmap``. For instance (assuming you are in the 192.168.1.0 network)).

  In your Linux Desktop / Laptop, run:

  Using Nmap

  .. prompt:: bash $
  
     sudo apt-get install nmap
     nmap -sP 192.168.1.0/24
  
  Using Fping

  .. prompt:: bash $

     sudo apt-get install fping
     fping -a -g 192.168.1.0/24
  
.. note::
  You will be prompted to change the password on first login, so you will need to log in twice.
