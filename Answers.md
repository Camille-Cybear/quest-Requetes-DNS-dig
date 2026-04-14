## 1.les adresses IP version 4 du site web de la **Wild Code School** ! [www.wildcodeschool.com](http://www.wildcodeschool.com)

Pour www.wildcodeschool.com les adresses IP sont bien  :
- 199.60.103.225
- 199.60.103.31

(Contrairement à 104.21.79.167 et	172.67.146.155 : pour wildcodeschool.com )

```bash
dig www.wildcodeschool.com

; <<>> DiG 9.18.39-0ubuntu0.24.04.3-Ubuntu <<>> www.wildcodeschool.com

.......

;; ANSWER SECTION:
www.wildcodeschool.com.	85	IN	CNAME	2902314.group14.sites.hubspot.net.

;; ADDITIONAL SECTION:
group14.sites.hscoscdn10.net. 85 IN	A	199.60.103.225
group14.sites.hscoscdn10.net. 85 IN	A	199.60.103.31
```

## 2.les adresses IP version 6 d'**odyssey** et en déduire l'hébergeur de ton fournisseur de quête préféré

L'hébergeur est Google CLOUD

```bash
dig AAAA odyssey.wildcodeschool.com

; <<>> DiG 9.18.39-0ubuntu0.24.04.3-Ubuntu <<>> AAAA odyssey.wildcodeschool.com

..........

;; ANSWER SECTION:
odyssey.wildcodeschool.com. 300	IN	CNAME	ghs.googlehosted.com.
ghs.googlehosted.com.	118	IN	AAAA	2a00:1450:400c:c07::79
```

## (Bonus) les noms des serveurs de noms faisant autorité sur le domaine wildcodeschool.com et le serveur primaire.

Les serveurs faisant authorité pour wildcodeschool.com sont 
- kim.ns.cloudflare.com.
- cash.ns.cloudflare.com.


```bash
dig wildcodeschool.com NS

; <<>> DiG 9.18.39-0ubuntu0.24.04.3-Ubuntu <<>> wildcodeschool.com NS

....

;; ANSWER SECTION:
wildcodeschool.com.	6723	IN	NS	kim.ns.cloudflare.com.
wildcodeschool.com.	6723	IN	NS	cash.ns.cloudflare.com.
```

Le serveur primaire est : cash.ns.cloudflare.com

```bash
dig wildcodeschool.com SOA

; <<>> DiG 9.18.39-0ubuntu0.24.04.3-Ubuntu <<>> wildcodeschool.com SOA

....

;; ANSWER SECTION:
wildcodeschool.com.	1331	IN	SOA	cash.ns.cloudflare.com. dns.cloudflare.com. 2400969826 10000 2400 604800 1800
```

## (Bonus) Refaire les requêtes précédentes en précisant l'utilisation du serveur récursif **quad9** "9.9.9.9 ou 2620:fe::9"

```bash

dig @9.9.9.9 www.wildcodeschool.com

; <<>> DiG 9.18.39-0ubuntu0.24.04.3-Ubuntu <<>> @9.9.9.9 www.wildcodeschool.com
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 64841
;; flags: qr rd ra; QUERY: 1, ANSWER: 4, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 512
;; QUESTION SECTION:
;www.wildcodeschool.com.		IN	A

;; ANSWER SECTION:
www.wildcodeschool.com.	300	IN	CNAME	2902314.group14.sites.hubspot.net.
2902314.group14.sites.hubspot.net. 120 IN CNAME	group14.sites.hscoscdn10.net.
group14.sites.hscoscdn10.net. 250 IN	A	199.60.103.31
group14.sites.hscoscdn10.net. 250 IN	A	199.60.103.225

;; Query time: 16 msec
;; SERVER: 9.9.9.9#53(9.9.9.9) (UDP)
;; WHEN: Tue Apr 14 22:20:56 CEST 2026
;; MSG SIZE  rcvd: 169
```


```bash
dig @2620:fe::9 AAAA odyssey.wildcodeschool.com

; <<>> DiG 9.18.39-0ubuntu0.24.04.3-Ubuntu <<>> @2620:fe::9 AAAA odyssey.wildcodeschool.com
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 24068
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 1232
;; QUESTION SECTION:
;odyssey.wildcodeschool.com.	IN	AAAA

;; ANSWER SECTION:
odyssey.wildcodeschool.com. 300	IN	CNAME	ghs.googlehosted.com.
ghs.googlehosted.com.	263	IN	AAAA	2a00:1450:400c:c0d::79

;; Query time: 18 msec
;; SERVER: 2620:fe::9#53(2620:fe::9) (UDP)
;; WHEN: Tue Apr 14 22:23:23 CEST 2026
;; MSG SIZE  rcvd: 114
```
