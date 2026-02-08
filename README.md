# GLPI

## Installer GLPI
Format docker </br>
./docker-compose.yml</br>
./mariadb.env</br>
**Attention il s'agit d'un fichier de configuration de test et non à utiliser en cas d'usage réel** 

## Utiliser l'agent GLPI pour remonter d'information
### 1. Activier l'inventaire dans GLPI l'interface 
Administration > Inventaire > Activer l'inventaire
### 2. Télécharger le .deb pour l'installation sur linux
```
wget https://github.com/glpi-project/glpi-agent/releases/download/1.16/glpi-agent_1.16-1_all.deb
```
### 3. Configuration de l'agent GLPI
Pour une remonté d'informations plus rapide au démarage exemple lors d'un clone cloud init définir la remontée d'informations plus rapidement que les 24h par défaut avec la configuration suivante.</br></br>
Source : https://glpi-agent.readthedocs.io/en/latest/configuration.html</br>
Dans **/etc/glpi-agent/agent.cfg**
```
# Insérer le liens nom de votre serveur <serveur>
server = http://<serveur>/front/inventory.php
# Toute les 30 sec
delaytime = 30
lazy = 0
# Exporter tout les données
full-inventory-postpone = 0
```

Si il n'y a pas de remonté d'information tester la commande de debug 
```
# Test imédiat
sudo glpi-agent --force --full
```
```
# Debug
sudo glpi-agent --debug --force
```
