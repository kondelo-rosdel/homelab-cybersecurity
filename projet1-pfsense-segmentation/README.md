# Projet 1 – Mise en place d'un mini réseau sécurisé avec pfSense

## 🎯 Objectif
Créer une architecture réseau composée de :
- une zone LAN (Kali Linux)
- une DMZ (Metasploitable2)
- un firewall pfSense avec segmentation
- des règles restrictives pour limiter les flux

Ce projet démontre la compréhension de la segmentation réseau, du firewall et de la mise en place d’un environnement sécurisé pour l’analyse des menaces.

---

## 🧱 Architecture du réseau

![Image Alt](https://github.com/kondelo-rosdel/homelab-cybersecurity/blob/7f61788e8d61128b8d923a4aa6d3cc0ba74a85c4/projet1-pfsense-segmentation/images/Topologie%20Re%CC%81seau.png)


---

## ⚙️ Configuration réalisée

### ✔️ 1. Création de deux réseaux VirtualBox
- **LAN (LANHOME)** → Kali Linux
- **DMZ (DMZHOME)** → Metasploitable2
- pfSense possède deux cartes :
  - LAN : 192.168.1.1
  - DMZ : 192.168.2.1

---

## 🔐 2. Règles de firewall appliquées

### 🟥 Règles LAN → DMZ (autorisé)
- Autoriser le trafic depuis Kali vers Metasploitable2 pour les tests

### 🟧 Règles DMZ → LAN (bloqué)
- Empêcher Metasploitable2 de remonter vers le LAN
  → Limiter les mouvements latéraux

### 🟦 Règles DMZ → Internet (bloqué)
→ Une vraie DMZ n’a pas accès direct à l’extérieur

### 🟩 LAN → Internet (autorisé)
→ Kali peut mettre à jour et télécharger des outils

---

## 🛡️ 3. Ajout d’un IDS
Installation de **Snort** sur pfSense.

Déclenchement d’alertes lors de scans Nmap depuis Kali.

---

## 🧪 Tests effectués

- ping entre les segments
- scans Nmap depuis Kali → contrôlés par pfSense
- tests d’accès entre zones
- génération de logs IDS

Captures dans `images/`.

---

## 📊 Résultats

- Segmentation fonctionnelle
- Mouvements latéraux impossibles depuis DMZ
- pfSense détecte les scans et connexions
---

## 🧠 Compétences démontrées

- Mise en place d'un firewall
- Construction et isolation d’une DMZ
- Configuration de règles réseau
- Analyse basique IDS 
- Documentation

---

## 📄 Documents inclus
- Rapport PDF : `./documents/rapport-pfsense.pdf`
- Captures réseau / firewall : `./images/`
