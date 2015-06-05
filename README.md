# ipfs-vbox - boot VMs in virtual box with IPFS

## Example

First, get a vm image and add it to ipfs, like this:

```
> ipfs add -w ipfs.iso
added QmRtavajASJyHcT4wVZkTS9s1XqtpFDW5jeUzGUzw6RPtb/ipfs.iso ipfs.iso
```

(That o/ is a valid VM, so you should be able to test this script with it)

Make sure you have [VirtualBox](https://www.virtualbox.org/wiki/Downloads) installed:

```
> VBoxManage --version
4.3.20r96996
```

Run the `ipfs daemon` mounted:

```sh
> ipfs daemon --mount
Initializing daemon...
API server listening on /ip4/127.0.0.1/tcp/5001
Gateway (readonly) server listening on /ip4/0.0.0.0/tcp/8080
```

Check the iso is there, in the mounted `/ipfs`:

```sh
> stat /ipfs/QmRtavajASJyHcT4wVZkTS9s1XqtpFDW5jeUzGUzw6RPtb/ipfs.iso
771751942 17996664729543829149 -r--r--r-- 0 jbenet staff 0 27676672 "Aug 30 14:43:42 1754" "Aug 30 14:43:42 1754" "Aug 30 14:43:42 1754" "Aug 30 14:43:42 1754" 1048576 54056 0 /ipfs/QmRtavajASJyHcT4wVZkTS9s1XqtpFDW5jeUzGUzw6RPtb/ipfs.iso
```

Now, boot it with this script!

```
> ipfs-vbox boot /ipfs/QmRtavajASJyHcT4wVZkTS9s1XqtpFDW5jeUzGUzw6RPtb/ipfs.iso
...
```

You should see it boot like this:

![](http://gateway.ipfs.io/ipfs/QmT1LRQEXdaKdUwLct9Z4hSn6Gn5uKHfvT9K2uupYR9rvK/vbox.png)

![](http://gateway.ipfs.io/ipfs/QmZ3G1saxLiCCrhyua3tvq3ETDVbLvvm3mwBfrwga8s8M4/smile.gif)

Remove the vm with:

```
> ipfs-vbox rm /ipfs/QmRtavajASJyHcT4wVZkTS9s1XqtpFDW5jeUzGUzw6RPtb/ipfs.iso
VBoxManage: error: Invalid machine state: PoweredOff (must be Running, Paused or Stuck)
VBoxManage: error: Details: code VBOX_E_INVALID_VM_STATE (0x80bb0002), component Console, interface IConsole, callee nsISupports
VBoxManage: error: Context: "PowerDown(progress.asOutParam())" at line 222 of file VBoxManageControlVM.cpp
0%...10%...20%...30%...40%...50%...60%...70%...80%...90%...100%
```
