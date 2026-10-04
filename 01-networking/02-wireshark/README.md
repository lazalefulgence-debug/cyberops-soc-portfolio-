# 🦈 Travaux pratiques Wireshark

Cette section contient des exercices pratiques axés sur la capture et l'analyse du trafic réseau.

## Sujets

- Trames Ethernet
- TCP
- HTTP
- HTTPS/TLS
- Analyse de paquets
- Dépannage réseau

02-wireshark/
└── http-https-analysis/
README.md



# 🦈 Analyse du trafic HTTP/HTTPS avec Wireshark

## 🎯 Objectif

L'objectif de ce laboratoire est de capturer et d'analyser le trafic réseau à l'aide de **Wireshark** et **tcpdump**, en mettant l'accent sur la compréhension des différences entre le trafic **HTTP et HTTPS**.

Ce laboratoire vise également à comprendre quelles informations un analyste SOC peut observer lors de l'examen des communications réseau.

---

## 🖥️ Environnement

- Système d'exploitation : Linux
- Interface réseau : `enp0s3`
- Outil de capture de paquets : tcpdump
- Outil d'analyse réseau : Wireshark
- Protocoles analysés : HTTP, HTTPS/TLS

---

## 🛠️ Outils

- Wireshark
- tcpdump
- Terminal Linux

---

## 💻 Capture de paquets

La commande suivante a été utilisée pour capturer le trafic réseau :

```bash
sudo tcpdump -i enp0s3 -s 0 -w httpdump.pcap
```

### Explication de la commande

- `-i enp0s3` → capture le trafic sur l'interface `enp0s3`
- `-s 0` → capture le paquet complet
- `-w httpdump.pcap` → enregistre la capture dans un fichier `.pcap`

La capture peut ensuite être ouverte avec Wireshark :

```bash
wireshark httpdump.pcap
```

---

## 🌐 Analyse HTTP

Le protocole HTTP (HyperText Transfer Protocol) est un protocole de couche application traditionnellement utilisé pour échanger des informations entre un client et un serveur web.

Le trafic HTTP est transmis sans chiffrement.

Lors de l'analyse des paquets, des informations telles que les suivantes peuvent être visibles :

- Requêtes HTTP
- Réponses HTTP
- Adresses IP source et de destination
- Ports TCP
- Méthodes HTTP
- URL
- En-têtes HTTP
- Codes d'état de réponse

Par exemple, les requêtes HTTP peuvent contenir des méthodes telles que :

```text
GET
POST
```

---

## 🔐 Analyse HTTPS/TLS

Le protocole HTTPS utilise **TLS (Transport Layer Security)** pour protéger les communications entre le client et le serveur.

Contrairement au HTTP, les données applicatives échangées via HTTPS sont chiffrées. HTTPS assure :

- La confidentialité
- L'intégrité
- L'authentification du serveur

Cependant, l'utilisation du protocole HTTPS ne signifie **pas** automatiquement qu'un site web est entièrement sécurisé.

Un site web malveillant ou compromis peut tout à fait utiliser HTTPS.

---

## 🔎 HTTP vs HTTPS

| Caractéristique | HTTP | HTTPS |
|---|---|---|
| Chiffrement | ❌ Non | ✅ Oui |
| Confidentialité | ❌ Non | ✅ Oui |
| Protection de l'intégrité | ❌ Non | ✅ Oui |
| TLS | ❌ Non | ✅ Oui |
| Données applicatives visibles lors de la capture | Généralement oui | Généralement chiffrées |

---

## 🚨 Point de vue d'un analyste SOC

Ce laboratoire illustre un concept important pour les enquêtes menées au sein d'un centre des opérations de sécurité (SOC).

Un analyste SOC ne peut pas toujours lire le contenu des communications HTTPS chiffrées, mais les métadonnées réseau peuvent néanmoins fournir des informations utiles.

Un analyste peut examiner :

- L'adresse IP source
- L'adresse IP de destination
- Le port de destination
- Les horaires de connexion
- Le volume de trafic
- Les informations TLS
- Les connexions répétées
- Les schémas de communication suspects

Par conséquent, le trafic chiffré peut tout de même fournir des indicateurs précieux lors d'une enquête de sécurité.

---

## 📚 Enseignements tirés

Grâce à ce laboratoire, j'ai appris à :

- Capturer du trafic réseau avec tcpdump
- Ouvrir des fichiers `.pcap` avec Wireshark
- Analyser le trafic HTTP
- Comprendre le trafic HTTPS/TLS
- Distinguer les communications chiffrées de celles qui ne le sont pas
- Interpréter le trafic réseau sous l'angle de la sécurité
- Comprendre l'importance de l'analyse des paquets pour les opérations SOC

---

## 🎯 Point clé en matière de sécurité

> **HTTPS protège la communication, mais ne garantit pas que la destination elle-même est fiable.**

Pour un analyste SOC, comprendre à la fois le **contenu du trafic réseau** et les **métadonnées entourant les communications chiffrées** est essentiel pour détecter toute activité suspecte.


## 📸 Capture de paquets

La capture d'écran suivante montre le trafic réseau capturé avec tcpdump.

![Capture tcpdump]()
