# Phase B1 — Semaine 3 (architecture AWS, sans VM obligatoire)

## Schéma

(Dessin ou ASCII : Internet → groupe de sécurité → EC2 → nginx ou Docker)

## Ports à ouvrir (inbound)

| Port | Protocole | Source | Usage |
|------|-----------|--------|--------|
| 22 | TCP | | SSH |
| 80 ou 5000 | TCP | | HTTP |

**Pourquoi ouvrir SSH (22) à 0.0.0.0/0 est dangereux en production ?**

## Commandes que vous lanceriez sur la VM

```bash
ssh -i cle.pem ubuntu@IP_PUBLIQUE
sudo apt update && sudo apt install -y nginx
curl http://localhost
```

Expliquez le rôle de : **clé SSH**, **IP publique**, **groupe de sécurité**.

## Choix techniques

- Région AWS et pourquoi :
- Type d’instance (ex. t2.micro) :
- Pourquoi **terminer** l’instance après un lab :
