## `vps` 为 `ios/mac` 配置 `ipsec vpn` 的脚本文件

测试系统：ubuntu14.04 基于openVZ架构的vps

### 目的

    脚本用来简化在vps上配置ipsec vpn的繁琐步骤。

    最终可实现基于共享秘钥的ipsec vpn。

    对于支持cisco ipsec vpn 的设备可以直接使用
    用户名+密码以及共享秘钥连接vpn

### 使用方法

下载脚本需要修改两个地方。
* 修改主机ip地址
* 修改vpn账户用户名密码以及psk共享秘钥


    cat > /etc/ipsec.secrets<<EOF
    : PSK "YourPSKHere"
    accountNameHere : XAUTH "passwdForAccountHere"
    EOF

* 如有必要，修改/etc/sysctl.conf ,将`net.ipv4.ip_forward=1`前的`#`去掉,执行`sysctl -p`

最后执行脚本即可。
