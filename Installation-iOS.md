This guide will help you install Theos on your iOS jailbroken device.

| Platform | Minimum OS version | Targets supported
|----------|--------------------|-------------------|
| **iOS** | 5.0 | iOS |

1. Install the following prerequisites in Cydia:

    Under Sources / Edit / Add:

    * CoolStar’s repository: https://coolstar.org/publicrepo/
    * Sam Bingner’s repository: http://repo.bingner.com/

    Under Search:

    * Theos Dependencies (package on BigBoss repo, relies on the previous repositories being installed first)
    * swift-toolchain [optional] (package on BigBoss repo, required for compiling Swift code)

1. SSH to your iPhone

        ssh root@257.258.259.2510

   Default password:

        alpine

1. Set up the `THEOS` environment variable:

        echo "export THEOS=~/theos" >> ~/.profile

    Refresh:

        source ~/.profile

    Output of:

       echo $THEOS

    Should be:

        /var/root/theos

1. Clone Theos to your device:

        git clone --recursive https://github.com/theos/theos.git $THEOS

1. Get the toolchain:

	Theos Dependencies installs iOS Toolchain.

1. Get an iOS SDK:

    You can get patched SDKs from [our SDKs repo](https://github.com/theos/sdks).

        curl https://github.com/theos/sdks/archive/master.zip -o master.zip -L
        unzip master.zip -d $THEOS/sdks

    Note that if you wish to compile Swift code, the minimum SDK required is iOS 11.2.

1. Set up ghostbin script:

        curl https://ghostbin.com/ghost.sh -o $THEOS/bin/ghost
        chmod +x $THEOS/bin/ghost
