# 云服务器安装Routeros，并设置wireguard学习记录
1、打开安装RouterOS脚本网站：
https://mikrotik.ltd/

2、通过ssh连接服务器ubuntu和debian都可以，在命令窗口输入shell命令：
VERSION=7.21.2 bash <(curl https://mikrotik.ltd/chr.sh)

3、大概一分钟后，通过winbox连接上在服务器上安装好的RouterOS CHR系统，关闭除winbox的所有协议。
选择- IP - Services
<img width="962" height="579" alt="image" src="https://github.com/user-attachments/assets/b9fa4539-7780-4352-8e2e-3d5119c230ed" />

4、设置wireguard VPN。
选择- WireGuard - New - Apply - OK（都默认即可）
<img width="965" height="581" alt="image" src="https://github.com/user-attachments/assets/6ef5b401-308b-4eba-955a-6eddf54f3ad0" />

5、去给wg1添加ip网段。
<img width="963" height="579" alt="image" src="https://github.com/user-attachments/assets/c052dc65-23db-42a1-ac79-70637952a8c7" />

6、去防火墙把出站流量伪装一下（不然通过wg访问过来的流量不能访问公网）
选择 IP - Firewall — NAT - Chain(选择srcnat)、Out.Interface(选择ether1)出口网卡
<img width="905" height="584" alt="image" src="https://github.com/user-attachments/assets/f79514b5-767f-4565-8de0-c639dd19396e" />
<img width="909" height="581" alt="image" src="https://github.com/user-attachments/assets/420ad7fa-c2a9-4f32-bd49-b5eb7af42bea" />

7、然后去选择- WireGuard - Peer - New - 添加上需要的参数。
（PrivateKey 这个可以再创建一个wg2拿到公钥复制过来）
<img width="954" height="579" alt="image" src="https://github.com/user-attachments/assets/f593c2ce-f940-486c-9f2c-9c87c1c6cb52" />
按照图片这个格式配置好，选择 Apply 就会生成 配置参数 和 二维码 复制参数或者扫描二维码就能使用。
<img width="962" height="581" alt="image" src="https://github.com/user-attachments/assets/5ca26a65-ae77-400b-8bb0-9b32825698ec" />




