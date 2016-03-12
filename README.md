# LOADLIN v1.6
      Why use LOADLIN ?
      =================

      LOADLIN is the safest way to boot Linux from your hard disk,
      if you have a bootable DOS-partition besides Linux on your machine.

      Most Linux-newbees are too impatient to read the very good (but also
      long) documentation of LILO (the standard Linux loader), and start
      using it incorrectly, resulting in an unbootable DOS after this
      (the MBR gots overwritten, 'fdisk /MBR' not always repairs).
      For those impatient ones LOADLIN is the best loader to start with.

      LOADLIN needs not to be installed in any way, it is usable as is
      and the kernel images can reside on any DOS accessable medium
      (even on a network drive). This also makes LOADLIN an exellent
      tool, if it comes to boot your Linux after a crash and a
      filesystem restore from backup medium (you must run LILO after
      this, but you can't if you have not yet booted, isn't it?).

      Many CDrom producers already have seen the advantage of starting
      the Linux-installation process by means of LOADLIN, because it
      runs out of the box. And using DOS to push Linux on the road
      isn't wrong, if you have DOS (or Windows 95 DOS mode) available.
      With LOADLIN you can directly boot Linux from the CD without
      needing an intermediate bootfloppy.

                         --------- +++  --------


      Features of LOADLIN
      ===================

      LOADLIN is highly adaptable to different DOS configurations, and now
      has very few loading restrictions. It makes use of extended memory and
      also can load big kernels (bzImages) and ramdisk images (initrd)
      directly high. The bzImage+initrd standard was jointly developed
      by the LILO-author (Werner Almesberger) and the LOADLIN-author (me)
      and is part of the official kernel since version 1.3.73.

      It is also capable of booting a UMSDOS-based system from a DOS drive.

      Some options (-v, -t, -d) produce debug information, so if you have
      problems, you can follow what is really being done by LOADLIN.

      LOADLIN also can load out of Virtual-86 mode (which is normal when
      using EMS drivers) if a VCPI server is present.



                         --------- +++  --------
