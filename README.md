# auth_with_kerberos

#  Étapes pour configurer Kerberos sur UBUNTU :

Kerberos est un protocole de sécurité d'authentification client-serveur qui utilise un système de tickets pour permettre à un client de prouver son identité auprès d'un serveur. Le protocole est largement utilisé dans les environnements d'entreprise pour sécuriser les communications entre les ordinateurs et les services.
pour configurer Kerberos sur Ubuntu, voici les étapes générales que vous devez suivre :
1/ Installer les paquets Kerberos sur les machines client et serveur en utilisant la commande suivante :
 
![install_kerberos](https://user-images.githubusercontent.com/74207234/236649254-85c03a76-473c-480e-bde6-0111f0b88d2f.JPG)

2/ Configurer le fichier /etc/krb5.conf sur les machines client et serveur pour définir le royaume Kerberos et les serveurs KDC. 
Vous devez également spécifier le nom d'hôte de la machine sur laquelle le serveur KDC est installé. Par exemple, voici un exemple de configuration de /etc/krb5.conf :
