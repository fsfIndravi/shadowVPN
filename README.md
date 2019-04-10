Install
-------

#### Debian & Ubuntu

For Debian 7 and Ubuntu 12+, add the following line to `/etc/apt/sources.list`

    deb http://shadowvpn.org/debian wheezy main

Then

    apt-get update && apt-get install shadowvpn
    service shadowvpn restart

#### Unix

Currently Linux, FreeBSD and OS X are supported.
Download a [release] and build. Do not clone the repo, since it's not stable.
Make sure to set `--sysconfdir=/etc`. You'll find conf files under `/etc`.

    # For Debian-based Linux
    sudo apt-get update
    sudo apt-get install build-essential automake libtool git -y
    ./configure --enable-static --sysconfdir=/etc
    make && sudo make install

#### OpenWRT

Download bundled [ShadowVPN with LuCI], or just [download ShadowVPN] itself,

Or build ShadowVPN yourself: cd into [SDK] root, then

    pushd package
    git clone https://github.com/clowwindy/ShadowVPN.git
    popd
    make menuconfig # select Network/ShadowVPN
    make V=s
    scp bin/xxx/ShadowVPN-xxx-xxx.ipk root@192.168.1.1
    # then log in your box and use opkg to install that ipk file

#### iOS

See [iOS]

#### Android

See [Android]

#### Windows

See [Build for Windows].

Configuration
-------------

- You can find all the conf files under `/etc/shadowvpn`.
- For the client, edit `client.conf`.
- For the server, edit `server.conf`.
- Update `server` and `password` in those files.
- The script file specified by `up` will be executed after VPN is up.
- The script file specified by `down` will be executed after VPN is down.
- If you need to specify routing rules, modify those scripts. You'll see a
placeholder at the end of those scripts.
- If you are using Windows, the IP address of TUN/TAP device `tunip` is
required to be specified in the conf file.
- You can [configure multiple users](https://github.com/clowwindy/ShadowVPN/wiki/Configure-Multiple-Users)


Usage
-----

Server:

    sudo shadowvpn -c /etc/shadowvpn/server.conf -s start
    sudo shadowvpn -c /etc/shadowvpn/server.conf -s stop

If you installed using apt-get, you can use `sudo service shadowvpn start` instead.

Client:

    sudo shadowvpn -c /etc/shadowvpn/client.conf -s start
    sudo shadowvpn -c /etc/shadowvpn/client.conf -s stop

Client(OpenWRT):

    /etc/init.d/shadowvpn start
    /etc/init.d/shadowvpn stop

You can also read [LuCI Configuration].


Bugs and Issues
----------------

- [FAQ]
- [Issue Tracker]
- [Mailing list]


[Android]:              https://github.com/clowwindy/ShadowVPNAndroid
[Build Status]:         https://travis-ci.org/clowwindy/ShadowVPN.svg?branch=master
[Build deb Package]:    https://github.com/clowwindy/ShadowVPN/wiki/Building-deb-Package
[Build for Windows]:    https://github.com/clowwindy/ShadowVPN/wiki/Build-for-Windows
[Compare]:              https://github.com/clowwindy/ShadowVPN/wiki/Compared-to-Shadowsocks-and-OpenVPN
[Chinese Readme]:       https://github.com/clowwindy/ShadowVPN/wiki/ShadowVPN-%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8E
[download ShadowVPN]:   https://github.com/clowwindy/ShadowVPN/releases
[FAQ]:                  https://github.com/clowwindy/ShadowVPN/wiki/FAQ
[iOS]:                  https://github.com/clowwindy/ShadowVPNiOS
[Issue Tracker]:        https://github.com/clowwindy/ShadowVPN/issues?state=open
[LuCI Configuration]:   https://github.com/clowwindy/ShadowVPN/wiki/Configure-Via-LuCI-on-OpenWRT
[Mailing list]:         http://groups.google.com/group/shadowsocks
[release]:              https://github.com/clowwindy/ShadowVPN/releases
[SDK]:                  http://wiki.openwrt.org/doc/howto/obtain.firmware.sdk
[ShadowVPN with LuCI]:  https://github.com/aa65535/openwrt-shadowvpn
[Travis CI]:            https://travis-ci.org/clowwindy/ShadowVPN
