# Tài liệu README.md

## Tài trợ
Alipay  
![20200312144201.png](https://vip1.loli.io/2020/03/12/7IJvKaTcrLBDbtz.png)

[Kiểm tra kho hàng trực tuyến BandwagonHost](https://bwg.ylx.me/)

## Chuẩn bị trước
**CentOS:**
```
yum install ca-certificates wget -y && update-ca-trust force-enable
```

**Debian/Ubuntu:**
```
apt-get install ca-certificates wget -y && update-ca-certificates
```

## Không gỡ bỏ phiên bản nhân
```
wget -O tcpx.sh "https://github.com/ylx2016/Linux-NetSpeed/raw/master/tcpx.sh" && chmod +x tcpx.sh && ./tcpx.sh
```

## Gỡ bỏ phiên bản nhân
```
bash <(wget --no-check-certificate -qO- ${GH_PROXY}https://raw.githubusercontent.com/ylx2016/Linux-NetSpeed/master/tcp.sh)
```

## Tự động biên dịch nhân thông qua action
[https://github.com/ylx2016/kernel/](https://github.com/ylx2016/kernel/)

## Thử thêm tham số để gọi tối ưu hóa trực tiếp
`./tcpx.sh op` hoặc `./tcpx.sh op2` (không kiểm tra hệ thống)

## Kiểm tra chất lượng IP
```
bash <(curl -Ls IP.Check.Place)
```

## Sử dụng đồng thời BBR và锐速 (RuiSu)
**Thêm BBR:**
```
echo "net.core.default_qdisc=fq" >> /etc/sysctl.d/99-sysctl.conf
```
```
echo "net.ipv4.tcp_congestion_control=bbr" >> /etc/sysctl.d/99-sysctl.conf
```
```
sysctl -p
```

**Chỉnh sửa tệp RuiSu:**
```
nano /appex/etc/config
```

**Kiểm tra mã có lỗi:**
Nếu RuiSu hoạt động bình thường, chạy lệnh để xem:
```
bash /appex/bin/lotServer.sh status | grep "LotServer"
```

**Kiểm tra BBR:**
Nhân mặc định sử dụng thuật toán BBR sẽ không có đầu ra:
```
lsmod | grep bbr
```

**Kiểm tra nhân đã cài trên CentOS:**
```
grubby --info=ALL|awk -F= '$1=="kernel" {print i++ " : " $2}'
```

**Xem các thuật toán TCP được hỗ trợ hiện tại:**
```
cat /proc/sys/net/ipv4/tcp_allowed_congestion_control
```

**Xem thuật toán đang chạy:**
```
cat /proc/sys/net/ipv4/tcp_congestion_control
```

**Xem thuật toán hàng đợi hiện tại:**
```
sysctl net.core.default_qdisc
```

**Lệnh:** `uname -a`  
**Tác dụng:** Xem phiên bản nhân hệ thống và tên hệ thống.

**Lệnh:** `cat /proc/version`  
**Tác dụng:** Xem thông tin version trong thư mục "/proc", cũng có thể lấy được phiên bản nhân và tên hệ thống hiện tại.

**Xem hàng đợi thực tế:**  
Việc thay đổi thuật toán hàng đợi có thể cần khởi động lại để có hiệu lực:  
```
tc -s qdisc show
```

**Tệp cấu hình:**  
`/etc/sysctl.d/99-sysctl.conf`  
```
sysctl --system
```

## Lưu ý
ylx2016 không có bất kỳ mối liên hệ nào với chiakge hay cx9208.  
**Tác giả thuật toán bbsplus:**  
[https://blog.csdn.net/dog250/article/details/80629551](https://blog.csdn.net/dog250/article/details/80629551)

**Tên đầu tiên của bbrplus:**  
[https://github.com/cx9208/bbrplus](https://github.com/cx9208/bbrplus)

**Phiên bản mới của bbrplus:**  
[https://github.com/UJX6N/bbrplus-5.10](https://github.com/UJX6N/bbrplus-5.10)

**Trang web Xanmod:**  
[https://xanmod.org](https://xanmod.org)

**Trang web Zen:**  
[https://liquorix.net/](https://liquorix.net/)

**RuiSu (锐速):**  
[https://moeclub.org/2017/03/09/14/](https://moeclub.org/2017/03/09/14/)

## Các nhân khác
- [https://github.com/alibaba/cloud-kernel](https://github.com/alibaba/cloud-kernel)  
- [https://github.com/Tencent/TencentOS-kernel](https://github.com/Tencent/TencentOS-kernel)

## Nhân được biên dịch sẵn
- [https://sourceforge.net/projects/xanmod/files/releases/current](https://sourceforge.net/projects/xanmod/files/releases/current)  
- [https://elrepo.org/linux/kernel/el7/x86_64/RPMS/](https://elrepo.org/linux/kernel/el7/x86_64/RPMS/)  
- [https://elrepo.org/linux/kernel/el8/x86_64/RPMS/](https://elrepo.org/linux/kernel/el8/x86_64/RPMS/)  
- [https://kernel.ubuntu.com/~kernel-ppa/mainline/](https://kernel.ubuntu.com/~kernel-ppa/mainline/)  
- [http://mirrors.aliyun.com/alinux/2.1903/plus/x86_64/Packages/](http://mirrors.aliyun.com/alinux/2.1903/plus/x86_64/Packages/)  
- [https://mirrors.tencent.com/tlinux/2.4/tlinux/x86_64/RPMS/](https://mirrors.tencent.com/tlinux/2.4/tlinux/x86_64/RPMS/)  
- [https://bintray.com/multipath-tcp/mptcp_rpm/mptcp/v0.95.1#files](https://bintray.com/multipath-tcp/mptcp_rpm/mptcp/v0.95.1#files)  
- [https://bintray.com/multipath-tcp/mptcp_deb/mptcp/v0.95.1#files](https://bintray.com/multipath-tcp/mptcp_deb/mptcp/v0.95.1#files)

## Script DD
- [https://git.beta.gs/](https://git.beta.gs/)  
- [https://www.cxthhhhh.com/network-reinstall-system-modify](https://www.cxthhhhh.com/network-reinstall-system-modify)

## Chu kỳ dịch vụ
- [https://zh.wikipedia.org/zh/Ubuntu](https://zh.wikipedia.org/zh/Ubuntu)  
- [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)  
- [https://wiki.debian.org/LTS](https://wiki.debian.org/LTS)  
- [https://wiki.centos.org/zh/About/Product](https://wiki.centos.org/zh/About/Product)
