# Partie 1 : Gestion des utilisateurs

Q.2.1.1 
connecter en root je fait : useradd luca

Q.2.1.2 

je preconnise d'ajouter le nouvel utilisateur dans le goupe sudo
usermod -aG sudo luca

Partie 2 : Configuration de SSH

Q.2.2.1

![](https://github.com/Lucapouilly/Ckekpoint_3/blob/main/Exercice_2/root%20ssh%20no.png)

Q.2.2.2 

![](https://github.com/Lucapouilly/Ckekpoint_3/blob/main/Exercice_2/allowusers.png)

Q.2.2.3 
Generer une cle sur la machine client avec la commande : ssh-keygen -t rsa
copie de la cle sur le serveur avec la commande : ssh-copy-id

![](https://github.com/Lucapouilly/Ckekpoint_3/blob/main/Exercice_2/desac%20mdp.png)

Partie 3 : Analyse du stockage

Q.2.3.1

les systemes de fichier monte sont :

- devtmpfs
- tmpfs
- ext4
- ext2

Q.2.3.2 

les types de stockage sont RAID et LVM

Q.2.3.3

![](https://github.com/Lucapouilly/Ckekpoint_3/blob/main/Exercice_2/reconstruction%20du%20raid.png)

Q.2.3.4

- pvcreate /dev/sda
- lvcretae -L 2G -n lv_data cp3-vg 
- sudo mkfs.ext4 /dev/cp3-vg/backup_lv
- mkdir -p /var/lib/bareos/storage
- mount /dev/cp3-vg/lv_data /var/lib/bareos/storage
- ajout au fichier fstab de cete ligne "'/dev/cp3-vg/lv_data /var/lib/bareos/storage ext4 defaults 0 2"


Q.2.3.5 
 espace libre dans le volume : 1,79 Gib

Partie 4 : Sauvegarde



Partie 5 : Filtrage et analyse réseau

Q.2.5.1 Quelles sont actuellement les règles appliquées sur Netfilter ?

- Accepte les paquets d'une connexion deja existante
- Rejette les paquets inconnue
- Accepte les paquets sur l'interface loopback
- Accepte les paquets TCP
- Accepte les paquets ICMP et ICMPv6
- Accepte les paquets SSH

Q.2.5.2 Quels types de communications sont autorisées ?

- les ping
- SSH
- trafic local
- connexion etablie

Q.2.5.3 Quels types sont interdit ?

tous les paquets entrants non liste

Q.2.5.4

tcp dport {9101, 9102, 9103} ip saddr 192.168.1.0/24 accept 

Partie 6 : Analyse de logs