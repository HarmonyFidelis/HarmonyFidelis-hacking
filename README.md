Système d’exploitation :

BlackArch [ 2474 Tools]
Kali [ 600 Tools]

Logiciel :

Metasploit


Numérisation des ports / Fingerprint

L’empreinte est essentiel à tout attaque réussie, permettant la récolte d’information telle que le système d’exploitation, les ports ouverts, et tous les services s’exécutant sur se port ainsi que toutes les applications vulnérables installées.
C’est information seront primordiale pour déterminer la sélection d’outils et de technologies.

Il existe deux type d’empreinte actif ou passif :

L’empreinte active permet d’interagir directement avec la cible. Il est plus précis et plus rapide que le type passif.
Cependant, cela implique plus de risques de détection.

L’une des premières étapes de toute empreinte active consiste à réduire un ensemble de plages IP en un hôte ciblé et actif.

Pour ce faire, il nécessite une analyse des ports ou une empreinte digitale du système d’exploitation.
Il existe de nombreux type de scanners de ports.

Empreinte active [Nmap : Outil de découverte de réseaux]

Prise de contact TCP à trois voies

L’hôte qui tente une connexion envoie à un hôte de destination un paquet avec un drapeau SYN.
Ensuite, l’hôte distant vérifie que les autorisations sont en place pour que la connexion soit établie.
Si toute les conditions sont remplies, l’hôte distant envoie au premier hôte un paquet avec un drapeau SYN et ACK.
Enfin le premier hôte renvoie un seul indicateur ACK au deuxième hôte, terminant la négociation et établissant la connexion.

Scan de Base avec Nmap :

Nous effectuons une analyse ping de base qui envoie simplement un ping à chaque IP dans une plage d’adresse IP et signale tous les hôtes qui répondent.

La commande nmap -sn va diagnostiquer l’IP

Exemple : Analysons une plage d’IP 
nmap -sn 192.168.56.0/24 
va diagnostiquer IP de 192.168.56.0 à 192.168.56.255 	


Nous pouvons donc voir qu’il y a une liste d’hôte sur un réseaux.

Résultats de l’analyse :












192.168.56.101
192.168.56.102
192.168.56.103

Sont les hôtes en cours d’exécution.

Découverte du système d’exploitation :

Ensuite, Nous identifierons le système d’exploitation 

Exemple : Analyse du système d’exploitation 
nmap -0 192.168.56.101 
nmap -0 192.168.56.103

Résultat de l’analyse :

Compréhension balayage Nmap :

Il y a non seulement une analyse très basique avec Nmap, mais aussi une enquête complète comme les ports et services ouverts ou fermés ainsi que sa version.

La commande nmap -sV sonde activement les ports ouverts pour déterminer le service et la version qui l’exécute 

Exemple : Examinons les ports ouverts, les services et leur version. 
nmap -sV 192.168.56.101
nmap -sV 192.168.56.103

Résultats de l’analyse :

On peut voir les ports ouverts, le type de services s’exécutant sur ces ports et sa version avec précision.

Résumé :

La commande nmap -sn va scanner un plage d’IP.
nmap -sn 192.168.56.0/24 

Découverte du système d’exploitation sur une adresse IP active.
nmap -0 192.168.56.101 

Analyse des ports et services ouvert.
nmap -sV 192.168.56.101

 

