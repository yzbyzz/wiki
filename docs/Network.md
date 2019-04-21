
# 网络

## DNS

查询工具

- nslookup

- dig

- host

```shell
$ host zhezhengcn.com

zhezhengcn.com is an alias for yzbyzz.github.io.
yzbyzz.github.io has address 185.199.111.153
yzbyzz.github.io has address 185.199.108.153
yzbyzz.github.io has address 185.199.110.153
yzbyzz.github.io has address 185.199.109.153

$ nslookup zhezhengcn.com
Server:		8.8.8.8
Address:	8.8.8.8#53

Non-authoritative answer:
zhezhengcn.com	canonical name = yzbyzz.github.io.
Name:	yzbyzz.github.io
Address: 185.199.111.153
Name:	yzbyzz.github.io
Address: 185.199.108.153
Name:	yzbyzz.github.io
Address: 185.199.109.153
Name:	yzbyzz.github.io
Address: 185.199.110.153

$ dig zhezhengcn.com

; <<>> DiG 9.10.6 <<>> zhezhengcn.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 26985
;; flags: qr rd ra; QUERY: 1, ANSWER: 5, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 512
;; QUESTION SECTION:
;zhezhengcn.com.			IN	A

;; ANSWER SECTION:
zhezhengcn.com.		599	IN	CNAME	yzbyzz.github.io.
yzbyzz.github.io.	3599	IN	A	185.199.108.153
yzbyzz.github.io.	3599	IN	A	185.199.110.153
yzbyzz.github.io.	3599	IN	A	185.199.109.153
yzbyzz.github.io.	3599	IN	A	185.199.111.153

;; Query time: 442 msec
;; SERVER: 8.8.8.8#53(8.8.8.8)
;; WHEN: Sat Apr 06 10:11:48 CST 2019
;; MSG SIZE  rcvd: 137

```