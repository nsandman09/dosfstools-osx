# dosfstools for OSX

OSX 10.9 Mavericks does not have mkfs.vfat.
 
[dosfstools](http://daniel-baumann.ch/software/dosfstools/) are now-orphaned Linux version utilities for making and checking MS-DOS FAT filesystems.

###Problems

1. *ioctl(dev, HDIO_GETGEO, &geometry)* unable to get drive geometry
2. geometry.sectors and geometry.heads you may get from nondirect calculation (sample in the [diskdev-cmds] (http://www.opensource.apple.com/source/diskdev_cmds/diskdev_cmds-557.3.1/)), but geometry.start needed for set hidden_sectros not available

###Porting

1. Based on the last version of dosfstools (3.0.26)
2. Add some Linux headers
3. Removed Atari FAT support
4. Removed fatlabel utility (for now)

###Install with homebrew

```
$ brew create dosfstools
```

```ruby
require "formula"

class Dosfstools < Formula
  url "https://github.com/nsandman09/dosfstools-osx/archive/8fd9e494d96d10ccc9820c15a04169d00b89bd01.zip"
  homepage "https://github.com/nsandman09/dosfstools-osx"
  sha256 "8036284f6684fc0f8127b4a0915c7a0617356851ce4f23fb7d2745b188a89dd4"

  def install
    system "make"
    system "make", "install"
  end
end
```

