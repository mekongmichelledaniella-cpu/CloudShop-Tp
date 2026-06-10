# Phase B1 — Semaine 3 (architecture AWS, sans VM obligatoire)

## Schéma

(Dessin ou ASCII : Internet → groupe de sécurité → EC2 → nginx ou Docker)

Internet
   ↓
Groupe de sécurité (Security Group)
   ↓
Instance EC2
   ↓
Nginx ou Docker (application CloudShop)

## Ports à ouvrir (inbound)

| Port | Protocole | Source                | Usage                   |
| ---- | --------- | --------------------- | ----------------------- |
| 22   | TCP       | 0.0.0.0/0 (ou ton IP) | SSH (connexion à la VM) |
| 80   | TCP       | 0.0.0.0/0             | HTTP (site web)         |
| 5000 | TCP       | 0.0.0.0/0             | API Flask (optionnel)   |


**Pourquoi ouvrir SSH (22) à 0.0.0.0/0 est dangereux en production ?**

Parce que cela permet à n’importe qui sur Internet de tenter de se connecter à ta machine en SSH.

## Commandes que vous lanceriez sur la VM

```bash
ssh -i cle.pem ubuntu@IP_PUBLIQUE
sudo apt update && sudo apt install -y nginx
curl http://localhost
```

Expliquez le rôle de : 
**clé SSH**:C’est une clé privée/publique qui permet de se connecter à la VM sans mot de passe.
 Elle sécurise l’accès à ton serveur
**IP publique**:C’est l’adresse Internet de ta machine EC2.
Elle permet d’accéder à ton serveur depuis le navigateur.
**groupe de sécurité**:C’est un pare-feu AWS.
Il contrôle quels ports sont accessibles SSH, HTTP

## Choix techniques

- Région AWS et pourquoi :
eu-west-1 (Irlande)
. Choisie car
faible latence depuis l’Afrique
bonne disponibilité
services AWS complets
- Type d’instance (ex. t2.micro) :
gratuit
suffisant pour un petit projet CloudShop
faible consommation de ressources
- Pourquoi **terminer** l’instance après un lab :
éviter les coûts inutiles
libérer les ressources AWS
éviter facturation automatique
bonne pratique DevOps
