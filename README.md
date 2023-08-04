Уязвимости и атаки на информационные системы. Васёв А.В.

## Задание 1

Скачайте и установите виртуальную машину Metasploitable: https://sourceforge.net/projects/metasploitable/.

Это типовая ОС для экспериментов в области информационной безопасности, с которой следует начать при анализе уязвимостей.

Просканируйте эту виртуальную машину, используя nmap.

Попробуйте найти уязвимости, которым подвержена эта виртуальная машина.

Сами уязвимости можно поискать на сайте https://www.exploit-db.com/.

Для этого нужно в поиске ввести название сетевой службы, обнаруженной на атакуемой машине, и выбрать подходящие по версии уязвимости.

Ответьте на следующие вопросы:

    Какие сетевые службы в ней разрешены?

```java
root@sql:/home/netology# nmap -A -p0-65535 192.168.1.134
Starting Nmap 7.80 ( https://nmap.org ) at 2023-08-04 09:14 +07
Nmap scan report for 192.168.1.134
Host is up (0.00096s latency).
Not shown: 64875 filtered ports, 631 closed ports
PORT      STATE SERVICE     VERSION
21/tcp    open  ftp         vsftpd 2.3.4
|_ftp-anon: Anonymous FTP login allowed (FTP code 230)
| ftp-syst: 
|   STAT: 
| FTP server status:
|      Connected to 192.168.1.86
|      Logged in as ftp
|      TYPE: ASCII
|      No session bandwidth limit
|      Session timeout in seconds is 300
|      Control connection is plain text
|      Data connections will be plain text
|      vsFTPd 2.3.4 - secure, fast, stable
|_End of status
22/tcp    open  ssh         OpenSSH 4.7p1 Debian 8ubuntu1 (protocol 2.0)
| ssh-hostkey: 
|   1024 60:0f:cf:e1:c0:5f:6a:74:d6:90:24:fa:c4:d5:6c:cd (DSA)
|_  2048 56:56:24:0f:21:1d:de:a7:2b:ae:61:b1:24:3d:e8:f3 (RSA)
23/tcp    open  telnet      Linux telnetd
25/tcp    open  smtp        Postfix smtpd
|_smtp-commands: metasploitable.localdomain, PIPELINING, SIZE 10240000, VRFY, ETRN, STARTTLS, ENHANCEDSTATUSCODES, 8BITMIME, DSN, 
|_ssl-date: 2023-08-04T02:31:38+00:00; 0s from scanner time.
53/tcp    open  domain      ISC BIND 9.4.2
| dns-nsid: 
|_  bind.version: 9.4.2
80/tcp    open  http        Apache httpd 2.2.8 ((Ubuntu) DAV/2)
|_http-server-header: Apache/2.2.8 (Ubuntu) DAV/2
|_http-title: Metasploitable2 - Linux
111/tcp   open  rpcbind     2 (RPC #100000)
139/tcp   open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
445/tcp   open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
512/tcp   open  exec        netkit-rsh rexecd
513/tcp   open  login?
514/tcp   open  tcpwrapped
1099/tcp  open  java-rmi    GNU Classpath grmiregistry
1524/tcp  open  bindshell   Metasploitable root shell
2049/tcp  open  nfs         2-4 (RPC #100003)
2121/tcp  open  ftp         ProFTPD 1.3.1
3306/tcp  open  mysql       MySQL 5.0.51a-3ubuntu5
| mysql-info: 
|   Protocol: 10
|   Version: 5.0.51a-3ubuntu5
|   Thread ID: 10
|   Capabilities flags: 43564
|   Some Capabilities: SwitchToSSLAfterHandshake, ConnectWithDatabase, LongColumnFlag, SupportsCompression, Support41Auth, SupportsTransactions, Speaks41ProtocolNew
|   Status: Autocommit
|_  Salt: `jt+q{7=n1I[n:sV3=v^
3632/tcp  open  distccd     distccd v1 ((GNU) 4.2.4 (Ubuntu 4.2.4-1ubuntu4))
5432/tcp  open  postgresql  PostgreSQL DB 8.3.0 - 8.3.7
|_ssl-date: 2023-08-04T02:31:38+00:00; 0s from scanner time.
5900/tcp  open  vnc         VNC (protocol 3.3)
| vnc-info: 
|   Protocol version: 3.3
|   Security types: 
|_    VNC Authentication (2)
6000/tcp  open  X11         (access denied)
6667/tcp  open  irc         UnrealIRCd
| irc-info: 
|   users: 1
|   servers: 1
|   lusers: 1
|   lservers: 0
|   server: irc.Metasploitable.LAN
|   version: Unreal3.2.8.1. irc.Metasploitable.LAN 
|   uptime: 0 days, 0:30:41
|   source ident: nmap
|   source host: 85D30CAC.78DED367.FFFA6D49.IP
|_  error: Closing Link: zbzfjlhvt[192.168.1.86] (Quit: zbzfjlhvt)
6697/tcp  open  irc         UnrealIRCd
8009/tcp  open  ajp13       Apache Jserv (Protocol v1.3)
|_ajp-methods: Failed to get a valid response for the OPTION request
8180/tcp  open  http        Apache Tomcat/Coyote JSP engine 1.1
|_http-favicon: Apache Tomcat
|_http-server-header: Apache-Coyote/1.1
|_http-title: Apache Tomcat/5.5
8787/tcp  open  drb         Ruby DRb RMI (Ruby 1.8; path /usr/lib/ruby/1.8/drb)
35503/tcp open  java-rmi    GNU Classpath grmiregistry
43916/tcp open  nlockmgr    1-4 (RPC #100021)
51219/tcp open  status      1 (RPC #100024)
51267/tcp open  mountd      1-3 (RPC #100005)
Device type: bridge|general purpose
Running (JUST GUESSING): Oracle Virtualbox (97%), QEMU (93%)
OS CPE: cpe:/o:oracle:virtualbox cpe:/a:qemu:qemu
Aggressive OS guesses: Oracle Virtualbox (97%), QEMU user mode network gateway (93%)
No exact OS matches for host (test conditions non-ideal).
Network Distance: 2 hops
Service Info: Hosts:  metasploitable.localdomain, irc.Metasploitable.LAN; OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel

Host script results:
|_ms-sql-info: ERROR: Script execution failed (use -d to debug)
|_nbstat: NetBIOS name: METASPLOITABLE, NetBIOS user: <unknown>, NetBIOS MAC: <unknown> (unknown)
|_smb-os-discovery: ERROR: Script execution failed (use -d to debug)
|_smb-security-mode: ERROR: Script execution failed (use -d to debug)
|_smb2-time: Protocol negotiation failed (SMB2)

TRACEROUTE (using port 80/tcp)
HOP RTT     ADDRESS
1   0.90 ms _gateway (10.0.2.2)
2   0.98 ms 192.168.1.134

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 1090.75 seconds
```


    Какие уязвимости были вами обнаружены? (список со ссылками: достаточно трёх уязвимостей)

	1. vsftpd 2.3.4

vsftpd 2.3.4 - Backdoor Command Execution (Metasploit)

https://www.exploit-db.com/exploits/17491

	2. Unreal 3.2.8.1

UnrealIRCd 3.2.8.1 - Backdoor Command Execution (Metasploit) 

https://www.exploit-db.com/exploits/16922

	3. Ruby 1.8

Ruby 1.8.6/1.9 (WEBick HTTPd 1.3.1) - Directory Traversal

https://www.exploit-db.com/exploits/5215


## Задание 2

Проведите сканирование Metasploitable в режимах SYN, FIN, Xmas, UDP.

Запишите сеансы сканирования в Wireshark.

Ответьте на следующие вопросы:

    Чем отличаются эти режимы сканирования с точки зрения сетевого трафика?
    Как отвечает сервер?

SYN (-sS) тип сканирования используемый по умолчанию. Способен сканировать тысячи портов в секунду, TCP соединение не устанавливается. Предоставляет информацию о состоянии порта - открыт, закрыт и фильтруется. В результате такого сканирования посылается SYN пакет, как если бы мы хотели установить реальное соединение и ждем. Наличие флагов SYN|ACK в ответе указывает на то, что порт удаленной машины открыт и прослушивается. Флаг RST в ответе означает обратное. Если Nmap принял пакет SYN|ACK, то в ответ немедленно отправляет RST-пакет для сброса еще не установленного соединения. Если после нескольких запросов не приходит никакого ответа, то порт помечается как фильтруемый.

![alt text](https://github.com/rus42/VulnerabilitiesAndAttacksOnIS/blob/main/Task_2.1.png)

![alt text](https://github.com/rus42/VulnerabilitiesAndAttacksOnIS/blob/main/Task_2.2.png)

FIN (-sF) - "невидимое" FIN сканирование. Используется в случае, если SYN-сканирование по каким-либо причинам оказалось неработоспособным. Некоторые фаерволы и пакетные фильтры "ожидают" поддельные SYN-пакеты на защищенные ими порты, и программы типа Synlogger или Courtney способны отследить SYN-сканирование. В FIN-сканировании в качестве запроса используется FIN-пакет. Согласно рекомендации RFC 973 п. 64, ОС сканируемого хоста должна ответить на такой пакет, прибывший на закрытый порт, пакетом RST, в то время как открытый порт должен игнорировать эти пакеты.
В данном случае опрашиваемая система посылает RST ответы на все запросы независимо от того, открыт порт или закрыт. Это привело к тому, что все порты помечены как закрытые.

![alt text](https://github.com/rus42/VulnerabilitiesAndAttacksOnIS/blob/main/Task_2.3.png)

![alt text](https://github.com/rus42/VulnerabilitiesAndAttacksOnIS/blob/main/Task_2.4.png)

Xmas (-sX) сканирование заключается в очистке заголовка SYN из TCP-пакета и замене его флагами FIN, PSH и URG (или заголовками Or) в обход брандмауэра. Также как и FIN сканирование Xmas считается скрытым сканированием. Поведение опрашиваемой системы в данном случае аналогично поведению при использовании FIN сканирования.

![alt text](https://github.com/rus42/VulnerabilitiesAndAttacksOnIS/blob/main/Task_2.5.png)

![alt text](https://github.com/rus42/VulnerabilitiesAndAttacksOnIS/blob/main/Task_2.6.png)

UDP (-sU) - сканирование UDP портов. UDP-соединения не имеют статических данных. UDP работает по принципу “сделал и забыл” — он отправляет пакеты, направленные на определенные порты, и надеется, что они дойдут. При этом больше внимания уделяется скорости, а не качеству. Отсутствие механизма обратной связи затрудняет идентификацию открытых портов. При отправке UDP-пакета на целевой порт возможны три сценария:

	Ответ не получен, тогда nmap помечает порт как open|filtered. В таком случае он отправляет еще один UDP-пакет для повторной проверки и если ответа снова нет, он помечает порт как open|filtered и идет дальше.
	Он может получить ответ UDP, но это бывает очень редко. В таком случае порт помечается как open.
	Если порт closed и он получает обратный echo-запрос ICMP, это означает, что порт недоступен.

![alt text](https://github.com/rus42/VulnerabilitiesAndAttacksOnIS/blob/main/Task_2.7.png)

![alt text](https://github.com/rus42/VulnerabilitiesAndAttacksOnIS/blob/main/Task_2.8.png)
