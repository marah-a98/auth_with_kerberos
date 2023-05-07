# auth_with_kerberos

#  Étapes pour configurer Kerberos sur UBUNTU :

#  Hostname and IP addresse:
faire la configuration des hostnames de notre machine kdc & client & server:

L'adresse IP de la machine cliente est 10.0.2.15
L'adresse IP de la machine du serveur de service (une des machines virtuelles) est 10.0.2.15
L'adresse IP de la machine KDC (l'autre machine virtuelle) est 10.0.2.15

Maintenant que nous avons ajouté des adresses IP aux machines virtuelles, nous allons commencer par définir des noms d'hôtes(hostname)  pour chaque machine :

.KDC machine :
 la commande est :
 hostnamectl --static set-hostname kdc.max.tn

![kdc_hostname](https://user-images.githubusercontent.com/74207234/236650088-0cdc3ca3-6163-4b90-a6b1-103b108b1561.JPG)

.Client machine
hostnamectl --static set-hostname client.max.tn


![client_hostname](https://user-images.githubusercontent.com/74207234/236650218-97ec4b8d-b5ce-4131-9c3e-e55b228245fd.JPG)


Ensuite, nous mapperons ces noms d'hôte à leurs adresses IP correspondantes sur les trois machines à l'aide du fichier /etc/hosts.
la commande est :
sudo nano /etc/hosts
Maintenant, nous devrions définir les informations ci-dessous sur /etc/hosts pour les trois machines :
<KDC_IP_ADDRESS>    kdc.max.com       kdc
<SERVER_ADDRESS>    server.max.com        server
<CLIENT_ADDRESS>    client.max.com    client
![host_file_config](https://user-images.githubusercontent.com/74207234/236650470-5040a4a0-1e0c-4083-9b2c-5471a4ba524e.JPG)

Une fois la configuration terminée, nous venons de faire et la commande ping pour nous assurer que les trois machines sont accessibles.
ici un exemple pour la machine kdc :
![ping_client](https://user-images.githubusercontent.com/74207234/236650769-5eaa6277-996a-4726-8e57-84d394d00366.JPG)

Le domaine est un réseau logique, similaire à un domaine, auquel appartiennent tous les utilisateurs et serveurs partageant la même base de données Kerberos.

La clé principale de cette base de données KDC doit être définie une fois l'installation terminée :

.avec la commande:

.sudo krb5_newrealm

![realm_conf](https://user-images.githubusercontent.com/74207234/236651077-62d67b59-9343-45dc-8d01-9f559e8ed441.JPG)

# Installation de kerberos 
Kerberos est un protocole de sécurité d'authentification client-serveur qui utilise un système de tickets pour permettre à un client de prouver son identité auprès d'un serveur. Le protocole est largement utilisé dans les environnements d'entreprise pour sécuriser les communications entre les ordinateurs et les services.
pour configurer Kerberos sur Ubuntu, voici les étapes générales que vous devez suivre :
1/ Installer les paquets Kerberos sur les machines client et serveur en utilisant la commande suivante :
 
![install_kerberos](https://user-images.githubusercontent.com/74207234/236649254-85c03a76-473c-480e-bde6-0111f0b88d2f.JPG)

2/ Configurer le fichier /etc/krb5.conf sur les machines client et serveur pour définir le royaume Kerberos et les serveurs KDC. 
Vous devez également spécifier le nom d'hôte de la machine sur laquelle le serveur KDC est installé. Par exemple, voici un exemple de configuration de /etc/krb5.conf :
 
 ![config_realm](https://user-images.githubusercontent.com/74207234/236649489-c264bf5a-178f-4c41-a36f-8f811eca2832.JPG)
 
 ![client_krb5_conf](https://user-images.githubusercontent.com/74207234/236652336-04018be6-d481-4d00-a2d3-3e3ef6eca1bb.JPG)

 
 Ajouter un utilisateur Kerberos en utilisant la commande suivante :
 
 $ sudo kadmin.local
 kadmin.local:  add_principal marah
 
 ![add_princiapl_](https://user-images.githubusercontent.com/74207234/236651685-699a0263-ed83-4048-a754-055a1939754c.JPG)
 On peut vérifier la liste des principaux en exécutant la commande : 
 kadmin.local: list_principals
 
 ![list_princial](https://user-images.githubusercontent.com/74207234/236651769-3c743252-e417-46ab-8105-87015cfcc58d.JPG)

# obtenir un ticket Kerberos pour le principal "max/admin". 
Cela signifie que l'utilisateur ou l'application qui exécute cette commande est authentifié auprès du serveur Kerberos en utilisant les informations d'identification associées au principal "max/admin".

Le ticket Kerberos obtenu par la commande "kinit max/admin" peut ensuite être utilisé pour accéder à des services protégés par Kerberos, tels que des partages de fichiers ou des applications qui nécessitent une authentification
![kinit](https://user-images.githubusercontent.com/74207234/236652120-1772523c-f36b-431a-82d3-3dd539db20df.JPG)
# afficher les tickets Kerberos actuels sur notre système
En exécutant la commande "klist" dans un terminal, vous pouvez voir une liste de tous les tickets Kerberos actuels pour l'utilisateur courant.

La liste affiche des informations telles que le nom du principal associé au ticket, la date et l'heure d'expiration du ticket, ainsi que d'autres détails pertinents. Si vous avez plusieurs tickets Kerberos, vous pouvez spécifier le ticket à afficher en utilisant l'option "-c" suivie du chemin du fichier de ticket.
![kinit](https://user-images.githubusercontent.com/74207234/236652241-c5727cd7-8660-4144-b90e-38f7faf1159b.JPG)



