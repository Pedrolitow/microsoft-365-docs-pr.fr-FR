---
title: Plan de résolution des problèmes de performances pour Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 5/10/2019
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: e241e5d9-b1d8-4f1d-a5c8-4106b7325f8c
ms.collection:
- M365-security-compliance
- Ent_O365
description: Cet article peut vous aider à résoudre Office 365 problèmes de performances et même résoudre certains des problèmes les plus courants.
ms.openlocfilehash: 6ef459d6469881c71ea7d1da3a32eb42eb3ead6b
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59182123"
---
# <a name="performance-troubleshooting-plan-for-office-365"></a>Plan de résolution des problèmes de performances pour Office 365

Avez-vous besoin de connaître les étapes à suivre pour identifier et corriger les retards, les hangs et les performances lentes entre SharePoint Online, OneDrive Entreprise, Exchange Online ou Skype Entreprise Online et votre ordinateur client ? Avant d’appeler le support technique, cet article peut vous aider à résoudre Office 365 problèmes de performances et même à résoudre certains des problèmes les plus courants.

Cet article est en fait un exemple de plan d’action que vous pouvez utiliser pour capturer des données précieuses sur votre problème de performances en cours. Certains problèmes principaux sont également inclus dans cet article.

Si vous débutez avec les performances du réseau et que vous souhaitez planifier à long terme la surveillance des performances entre vos ordinateurs clients et Office 365, jetez un œil à [l’optimisation](performance-tuning-using-baselines-and-history.md)et au dépannage des performances Office 365 - Administrateur et Pro .

## <a name="sample-performance-troubleshooting-action-plan"></a>Exemple de plan d’action de résolution des problèmes de performances

Ce plan d’action comprend deux parties : une phase de préparation et une phase de journalisation; Si vous avez un problème de performances pour le moment et que vous devez commencer à collectionr des données, vous pouvez commencer à utiliser ce plan immédiatement.

### <a name="prepare-the-client-computer"></a>Préparer l’ordinateur client

- Recherchez un ordinateur client qui peut reproduire le problème de performances. Cet ordinateur sera utilisé pendant le dépannage.
- Notez les étapes qui provoquent le problème de performances afin que vous soyez prêt au moment du test.
- Installez les outils de collecte et d’enregistrement des informations :
  - Installez [Netmon 3.4 (ou](https://www.microsoft.com/download/details.aspx?id=4865) utilisez un outil de suivi réseau équivalent).
  - Installez l’édition gratuite Basic Edition de [HTTPWatch](https://www.httpwatch.com/download/) (ou utilisez un outil de suivi réseau équivalent).
  - Utilisez un enregistreur d’écran ou exécutez l’enregistreur d’étapes (PSR.exe) qui est livré avec Windows Vista et ultérieur, afin de garder un enregistrement des étapes que vous prenez pendant le test.

### <a name="log-the-performance-issue"></a>Enregistrer le problème de performances

- Fermez tous les navigateurs Internet en trop.
- Démarrez l’enregistreur d’étapes ou un autre enregistreur d’écran.
- Démarrez votre capture Netmon (ou outil de suivi réseau).
- Clear your DNS cache on the client computer from the command line by typing ipconfig /flushdns.
- Démarrez une nouvelle session de navigateur et activer HTTPWatch.
- Facultatif : si vous testez Exchange Online, exécutez l’outil Exchange’analyseur de performances du client à partir de la console Office 365'administration.
- Reproduisez les étapes exactes à l’origine du problème de performances.
- Arrêtez la trace de votre netmon ou d’un autre outil.
- Sur la ligne de commande, exécutez un itinéraire de suivi vers votre abonnement Office 365 en tapant la commande suivante, puis en appuyant sur Entrée :

  ``` cmd
  tracert <subscriptionname>.onmicrosoft.com
  ```

- Arrêtez l’enregistreur d’étapes et enregistrez la vidéo. N’oubliez pas d’inclure la date et l’heure de la capture, ainsi que les performances bonnes ou mauvaises.
- Enregistrez les fichiers de suivi. Là encore, n’oubliez pas d’inclure la date et l’heure de la capture et de savoir si les performances sont bonnes ou mauvaises.

Si vous n’êtes pas familiarisé avec l’exécution des outils mentionnés dans cet article, ne vous inquiétez pas, car nous fournissons ces étapes ci-après. Si vous êtes habitué à ce type de capture réseau, vous pouvez passer à La collecte des lignes de [base,](performance-tuning-using-baselines-and-history.md#how-to-collect-baselines)qui décrit le filtrage et la lecture des journaux.

### <a name="flush-the-dns-cache-first"></a>Vider d’abord le cache DNS

Pourquoi ? En purgeant le cache DNS, vous démarrez vos tests avec une nouvelle tablette. En effavant le cache, vous réinitiaiaisez le contenu du résolveur DNS aux entrées les plus à jour. N’oubliez pas qu’un flush ne supprime pas les entrées de fichier HOSTs. Si vous utilisez des entrées de fichier HOST de manière intensive, vous devez copier ces entrées dans un fichier dans un autre répertoire, puis vider le fichier HÔTE.

#### <a name="flush-your-dns-resolver-cache"></a>Vider votre cache de résolution DNS

1. Ouvrez l’invite  de commandes (cmd démarrer \> **l’Windows** \>   \> **cmd**).
2. Tapez la commande suivante, puis appuyez sur Entrée :

    ``` cmd
    ipconfig /flushdns
    ```

## <a name="netmon"></a>Netmon

L’outil Surveillance du réseau[(Netmon)](https://www.microsoft.com/download/details.aspx?id=4865)de Microsoft analyse les paquets, c’est-à-dire le trafic, qui transite entre les ordinateurs sur les réseaux. En utilisant Netmon pour suivre le trafic avec Office 365 vous pouvez capturer, afficher et lire les en-têtes de paquets, identifier les appareils intermédiaires, vérifier les paramètres importants sur le matériel réseau, rechercher les paquets perdus et suivre le flux de trafic entre les ordinateurs de votre réseau d’entreprise et Office 365. Étant donné que le corps réel du trafic est chiffré, c’est-à-dire qu’il (circule sur le port 443 via SSL/TLS), vous ne pouvez pas lire les fichiers envoyés. Au lieu de cela, vous obtenez une trace non filtrée du chemin d’accès que le paquet prend, ce qui peut vous aider à suivre le comportement du problème.

Assurez-vous que vous n’appliquez pas de filtre pour le moment. Exécutez plutôt les étapes et démontrez le problème avant d’arrêter le suivi et d’enregistrer.

Après avoir installé Netmon 3.4, ouvrez l’outil et prenez les mesures suivantes :

### <a name="take-a-netmon-trace-and-reproduce-the-issue"></a>Suivre Netmon et reproduire le problème

1. Lancez Netmon 3.4.
Il existe trois volets sur la **page** de démarrage : **Captures récentes,** Sélectionner des réseaux **et** Prise en commencée avec Microsoft Network **Monitor 3.4. Remarque**. Le panneau Sélectionner des réseaux vous donne également une liste des réseaux par défaut à partir des lesquels vous pouvez capturer. Assurez-vous que les cartes réseau sont sélectionnées ici.

2. Cliquez **sur Nouvelle capture** en haut de la page **de** démarrage. Cela ajoute un nouvel onglet à côté de **l’onglet** de la page de démarrage appelé **Capture 1**.
![Interface utilisateur de Netmon avec les boutons Nouvelle capture, Démarrer et Arrêter mis en surbrillrillation.](../media/d4527d84-62ec-4301-82d5-e0166ff71f20.PNG)

3. Pour prendre une capture simple, cliquez sur **Démarrer** dans la barre d’outils.

4. Reproduisez les étapes qui présentent un problème de performances.

5. Cliquez **sur Arrêter** le \> **fichier** Enregistrer \> **sous**. N’oubliez pas de donner la date et l’heure avec le fuseau horaire et de mentionner s’il illustre des performances mauvaises ou bonnes.

## <a name="httpwatch"></a>HTTPWatch

[HTTPWatch est](https://www.httpwatch.com/download/) facturé et une édition gratuite. L’édition Basic Edition gratuite couvre tout ce dont vous avez besoin pour ce test. HTTPWatch surveille le trafic réseau et le temps de chargement des pages directement à partir de la fenêtre de votre navigateur. HTTPWatch est un plug-in d’Internet Explorer qui décrit graphiquement les performances. L’analyse peut être enregistrée et vue dans HTTPWatch Studio.

> [!NOTE]
> Si vous utilisez un autre navigateur, tel que Firefox, Google Chrome ou si vous ne pouvez pas installer HTTPWatch dans Internet Explorer, ouvrez une nouvelle fenêtre de navigateur et appuyez sur F12 sur votre clavier. L’outil de développement doit apparaître en bas de votre navigateur. Si vous utilisez Opera, appuyez sur Ctrl+Shift+I pour l’inspecteur web, puis cliquez sur l’onglet Réseau et terminez le test décrit ci-dessous.  Les informations seront légèrement différentes, mais les temps de chargement seront toujours affichés en millisecondes. > HTTPWatch est également très utile pour les problèmes de SharePoint temps de chargement de page en ligne.

### <a name="run-httpwatch-and-reproduce-the-issue"></a>Exécuter HTTPWatch et reproduire le problème

HTTPWatch est un plug-in de navigateur. L’exposition de l’outil dans le navigateur est donc légèrement différente pour chaque version d’Internet Explorer. En règle générale, vous pouvez trouver HTTPWatch sous la barre Commandes dans le navigateur Internet Explorer. Si vous ne voyez pas le plug-in HTTPWatch dans la fenêtre de  votre navigateur, vérifiez la version de votre navigateur en cliquant sur Aide à propos d’Internet Explorer ou dans les versions ultérieures d’Internet Explorer, cliquez sur le symbole d’engrenage et À propos \>  **d’Internet Explorer.** Pour lancer la **barre Commandes,** cliquez avec le bouton droit sur la barre de menus dans Internet Explorer, puis cliquez **sur Barre de commandes.**

Dans le passé, HTTPWatch était associé à la fois aux barres Commands et Explorer, donc une fois l’installation installée, si vous ne voyez pas immédiatement l’icône (même après le redémarrage) vérifier Outils et vos barres d’outils pour l’icône. N’oubliez pas que les barres d’outils peuvent être personnalisées et que des options peuvent y être ajoutées.

![Barre d’outils Commande d’Internet Explorer avec l’icône HTTPWatch affichée.](../media/198590b0-d7b1-4bff-a6ad-e4ec3a1e83df.png)

1. Lancez HTTPWatch dans une fenêtre de navigateur Internet Explorer. Elle apparaîtra ancre dans le navigateur au bas de cette fenêtre. Cliquez **sur Enregistrer**.

2. Reproduisez les étapes exactes impliquées dans le problème de performances. Cliquez sur **le bouton** Arrêter dans HTTPWatch.

3. **Enregistrez** httpWatch ou **Envoyer par courrier électronique.** N’oubliez pas de nommer le fichier de sorte qu’il inclut des informations de date et d’heure, ainsi qu’une indication du fait que votre surveillance contient une démonstration de bonnes ou de mauvaises performances.

![HTTPWatch affichant l’onglet Réseau pour le chargement de la page d’accueil Office 365.](../media/021a2c64-d581-49fd-adf4-4c364f589d75.PNG)

Cette capture d’écran est de la version Professional httpWatch. Vous pouvez ouvrir les suivis pris dans la version de base sur un ordinateur avec une version Professional et la lire à cet ordinateur. Des informations supplémentaires peuvent être disponibles à partir du suivi par le biais de cette méthode.

## <a name="problem-steps-recorder"></a>Enregistreur d’étapes du problème

L’enregistreur d'PSR.exe vous permet d’enregistrer les problèmes au cours de leur survenue. Il s’agit d’un outil très utile et très simple à exécuter.

### <a name="run-problem-steps-recorder-psrexe-to-record-your-work"></a>Exécuter l’Enregistreur d’étapes PSR.exe pour enregistrer votre travail

1. Utilisez le type **Démarrer** \> **l'PSR.exe** OK ou cliquez sur Windows type de touchePSR.exe\> puis  \>   \>  \> appuyez sur Entrée.

2. Lorsque la petite fenêtre PSR.exe s’affiche, cliquez sur **Démarrer** l’enregistrement et reproduisez les étapes qui reproduisent le problème de performances. Vous pouvez ajouter des commentaires selon vos besoins en cliquant sur **Ajouter des commentaires.**

3. Cliquez **sur Arrêter l’enregistrement** lorsque vous avez terminé les étapes. Si le problème de performances est un rendu de page, attendez que la page s’restituer avant d’arrêter l’enregistrement.

4. Cliquez sur **Enregistrer**.

![Capture d’écran de l’enregistreur d’étapes PSR.exe.](../media/8542b0aa-a3ff-4718-8dc4-43f5521c6c34.PNG)

La date et l’heure sont enregistrées pour vous. Cela lie votre RSP à votre suivi Netmon et HTTPWatch dans le temps, et facilite le dépannage de précision. La date et l’heure dans l’enregistrement PSR peuvent montrer qu’une minute s’est écoulée entre la connexion et la navigation de l’URL et le rendu partiel du site d’administration, par exemple.

## <a name="read-your-traces"></a>Lire vos suivis

Il n’est pas possible d’enseigner tout ce que quelqu’un doit savoir sur le dépannage du réseau et des performances via un article. L’obtention de bonnes performances prend de l’expérience et une connaissance du fonctionnement et des performances de votre réseau. Toutefois, il est possible d’arrondir une liste des principaux problèmes et de montrer comment les outils peuvent vous aider à éliminer plus facilement les problèmes les plus courants.

Si vous souhaitez acquérir des compétences en lecture de suivis réseau pour vos sites Office 365, il n’y a pas de meilleur enseignant que de créer régulièrement des suivis de chargements de page et d’acquérir de l’expérience en les lisant. Par exemple, lorsque vous en avez la possibilité, chargez un service Office 365 service et tracez le processus. Filtrez le suivi du trafic DNS ou recherchez dans FrameData le nom du service que vous avez parcouru. Analysez le suivi pour avoir une idée des étapes qui se produisent lors du chargement du service. Cela vous aidera à découvrir à quoi doit ressembler le chargement normal de la page, et dans le cas d’un dépannage, en particulier en ce qui concerne les performances, la comparaison de suivis bons à mauvais peut vous apprendre beaucoup.

Netmon utilise Microsoft Intellisense dans le champ De filtre d’affichage. IntelliSense, ou fin intelligente du code, est cette astuce où vous tapez un point et toutes les options disponibles sont affichées dans une zone de sélection de la zone de sélection de la zone de présentation. Si, par exemple, vous êtes préoccupé par la mise à l’échelle de la fenêtre TCP, vous pouvez trouver votre chemin d’accès à un filtre (par  `.protocol.tcp.window < 100` exemple) par cette voie.

![Capture d’écran de Netmon montrant que le champ Filtre d’affichage utilise intellisense.](../media/75a56c11-9a60-47ee-a100-aabdfb1ba10f.PNG)

Netmon traces can have a lot of traffic in them. Si vous n’avez pas l’expérience de les lire, il est probable que vous serez submergé d’ouvrir le suivi la première fois. La première chose à faire est de séparer le signal du bruit de fond dans le suivi. Vous avez testé Office 365, et c’est le trafic que vous voulez voir. Si vous êtes habitué à naviguer dans les traces, vous n’avez peut-être pas besoin de cette liste.

Le trafic entre votre client et Office 365 passe par TLS, ce qui signifie que le corps du trafic sera chiffré et ne pourra pas être lu dans un suivi Netmon générique. Votre analyse des performances n’a pas besoin de connaître les spécificités des informations dans le paquet. Toutefois, les en-têtes de paquets et les informations qu’ils contiennent l’intéressent beaucoup.

### <a name="tips-to-get-a-good-trace"></a>Astuces pour obtenir un bon suivi

- Connaissez la valeur de l’adresse IPv4 ou IPv6 de votre ordinateur client. Vous pouvez l’obtenir à partir de l’invite de commandes en **tapant IPConfig,** puis en appuyant sur Entrée. Le fait de connaître cette adresse vous permettra de déterminer d’un coup d’œil si le trafic dans le suivi implique directement votre ordinateur client. S’il existe un proxy connu, testez-le et obtenez également son adresse IP.

- Videz votre cache de résolveur DNS et, si possible, fermez tous les navigateurs à l’exception de celui dans lequel vous exécutez vos tests. Si vous n’êtes pas en mesure de le faire, par exemple, si la prise en charge utilise un outil basé sur un navigateur pour voir le bureau de votre ordinateur client, soyez prêt à filtrer votre suivi.

- Dans une trace occupée, recherchez le service Office 365 que vous utilisez. Si vous n’avez jamais ou rarement vu votre trafic auparavant, il s’agit d’une étape utile pour séparer le problème de performances des autres bruits du réseau. Il existe plusieurs façons de le faire. Directement avant votre test, vous pouvez utiliser _ping_ ou _PsPing_ par rapport à l’URL du service spécifique `ping outlook.office365.com` `psping -4 microsoft-my.sharepoint.com:443` (ou, par exemple). Vous pouvez également facilement trouver ce ping ou PsPing dans une trace Netmon (par son nom de processus). Cela vous permettra de commencer à regarder.

Si vous utilisez uniquement le suivi Netmon au moment du problème, cela ne pose aucun problème. Pour vous orienter, utilisez un filtre comme `ContainsBin(FrameData, ASCII, "office")` ou `ContainsBin(FrameData, ASCII, "outlook")` . Vous pouvez enregistrer votre numéro d’image à partir du fichier de suivi. Vous pouvez également faire  défiler le volet Résumé des images jusqu’à la droite et rechercher la colonne ID de conversation. Un numéro est indiqué ici pour l’ID de cette conversation spécifique que vous pouvez également enregistrer et examiner de manière isolée ultérieurement. N’oubliez pas de supprimer ce filtre avant d’appliquer tout autre filtrage.

> [!TIP]
> Netmon dispose de nombreux filtres intégrés utiles. Essayez le **bouton Charger le** filtre en haut du _volet_ Filtre d’affichage.

![Recherchez votre adresse IP à l’aide de PSPing sur la ligne de commande de l’ordinateur client.](../media/4c43ac67-e28e-4536-842d-7add7aa28847.PNG)

![Suivi Netmon à partir du client affichant la même commande PSPing via le filtre TCP. Flags.Syn == 1.](../media/0ae7ef7d-e003-4d01-a006-dc49bd1fcef2.PNG)

Familiarisez-vous avec votre trafic et apprenez à trouver les informations dont vous avez besoin. Par exemple, apprenez à déterminer quel paquet du suivi contient la première référence au service Office 365 que vous utilisez (comme « Outlook »).

En prenant Office 365 Outlook Online comme exemple, le trafic commence comme ceci :

- Requête DNS standard et réponse DNS pour les outlook.office365.com avec queryIDs correspondants. Il est important de noter le décalage de temps pour ce retournement, ainsi que l’endroit dans le monde où le DNS global Office 365 envoie la demande de résolution de nom. Dans l’idéal, aussi localement que possible, plutôt que dans le monde entier.

- Demande HTTP GET dont le rapport d’état a été déplacé définitivement (301)

- Trafic RWS, y compris RWS Connecter demandes et Connecter réponses. (Il s’agit de Winsock distant qui vous fait une connexion.)

- Une conversation TCP SYN et TCP SYN/ACK. Une grande partie des paramètres de cette conversation ont une incidence sur vos performances.

- Ensuite, une série de trafic TLS:TLS qui est l’endroit où les conversations de certificat TLS et de la conversation de certificat TLS ont lieu. (N’oubliez pas que les données sont chiffrées via SSL/TLS.)

Toutes les parties du trafic sont importantes et connectées, mais de petites parties du suivi contiennent des informations particulièrement importantes en termes de résolution des problèmes de performances. Nous allons donc nous concentrer sur ces domaines. En outre, étant donné que nous avons effectué suffisamment de résolution des problèmes de performances Office 365 chez Microsoft pour compiler une liste des dix principaux problèmes courants, nous allons nous concentrer sur ces problèmes et sur la façon d’utiliser les outils dont nous avons besoin pour les raciner ensuite.

Si vous ne les avez pas tous installés, la matrice ci-dessous utilise plusieurs outils. Dans la mesure du possible. Des liens sont fournis vers les points d’installation. La liste inclut les outils de suivi réseau courants tels que [Netmon](https://www.microsoft.com/download/details.aspx?id=4865) et [Wireshark,](https://www.wireshark.org/)mais utilise tout outil de suivi que vous êtes à l’aise avec et dans lequel vous êtes habitué à filtrer le trafic réseau. Lorsque vous testez, n’oubliez pas :

- *Fermez vos navigateurs et testez avec*  un seul navigateur en cours d’exécution, ce qui réduit le trafic global que vous capturez. Il permet une trace moins occupée.
- *Videz votre cache*  de résolution DNS sur l’ordinateur client. Cela vous donne une nouvelle tablette lorsque vous commencez à prendre votre capture, pour un suivi plus net.

## <a name="common-issues"></a>Problèmes courants

Certains problèmes courants que vous pouvez être confrontés et comment les trouver dans votre suivi réseau.

### <a name="tcp-windows-scaling"></a>Mise à l’échelle Windows TCP

Se trouve dans la syn - SYN/ACK. Le matériel hérité ou ancien peut ne pas tirer parti de la mise à l’échelle des fenêtres TCP.  Sans les paramètres de mise à l’échelle des fenêtres TCP appropriés, la mémoire tampon 16 bits par défaut dans les en-têtes TCP se remplit en millisecondes.  Le trafic ne peut pas continuer à envoyer tant que le client n’a pas reçu d’accusé de réception des données d’origine, ce qui provoque des retards.

#### <a name="tools"></a>Outils

- Netmon
- Wireshark

#### <a name="what-to-look-for"></a>Ce qu’il faut rechercher

Recherchez le trafic SYN - SYN/ACK dans votre suivi réseau.  Dans Netmon, utilisez un filtre comme  `tcp.flags.syn == 1` . Ce filtre est le même dans Wireshark.

![Filtre dans Netmon ou Wireshark pour les paquets Syn pour les deux outils : TCP. Flags.Syn == 1.](../media/4b9a12a1-c915-43c8-ac2f-a679d0435a29.PNG)

Notez que pour chaque syn, il existe un numéro de port source (SrcPort) qui correspond au port de destination (DstPort) de l’accusé de réception associé (SYN/ACK).

Pour voir la valeur Windows mise à l’échelle utilisée par votre connexion réseau, développez d’abord syn, puis syn/ACK associé.

![Graphique shows how to match SrcPort to DstPort in a trace, to get the time delta.](../media/6a4ca573-0253-4fbd-93e8-92821ee1c351.png)

### <a name="tcp-idle-time-settings"></a>Durée d’inactivité TCP Paramètres

Historiquement, la plupart des réseaux de périmètre sont configurés pour les connexions temporaires, ce qui signifie que les connexions inactives sont généralement interrompues. Les sessions TCP inactives peuvent être interrompues par des proxies et des pare-feu de plus de 100 à 300 secondes. Cela est problématique pour Outlook Online, car il crée et utilise des connexions à long terme, qu’elles soient inactives ou non.

Lorsque les connexions sont interrompues par des périphériques proxy ou pare-feu, le client n’est pas informé et une tentative d’utilisation de Outlook Online signifie qu’un ordinateur client essaiera, à plusieurs reprises, d’établir la connexion avant d’en effectuer une nouvelle. Vous pouvez voir des hangs dans le produit, des invites ou des performances lentes lors du chargement de la page.

#### <a name="tools"></a>Outils

- Netmon
- Wireshark

#### <a name="what-to-look-for"></a>Ce qu’il faut rechercher

Dans Netmon, recherchez un aller-retour dans le champ Décalage de temps. Un aller-retour est le délai entre l’envoi par le client d’une demande au serveur et la réception d’une réponse. Vérifiez entre le client et le point de sortie (par exemple. Client -- \> Proxy) ou client à Office 365 (Client -- \> Office 365). Vous pouvez le voir dans de nombreux types de paquets.

Par exemple, le filtre dans Netmon peut ressembler  `.Protocol.IPv4.Address == 10.102.14.112 AND .Protocol.IPv4.Address == 10.201.114.12` à , ou, dans Wireshark,  `ip.addr == 10.102.14.112 &amp;&amp; ip.addr == 10.201.114.12` .

> [!TIP]
> Vous ne savez pas si l’adresse IP de votre suivi appartient à votre serveur DNS ? Essayez de le regarder sur la ligne de commande. Cliquez **sur Démarrer** \> **l’exécuter** et \> **tapez cmd,** ou **appuyez sur Windows touche et** \> **tapez cmd**. À l’invite, tapez  `nslookup <the IP address from the network trace>` . Pour tester, utilisez nslookup par rapport à l’adresse IP de votre propre ordinateur. > pour consulter la liste des plages d’adresses IP de Microsoft, voir Office 365 URL et [plages d’adresses IP.](./urls-and-ip-address-ranges.md)

En cas de problème, attendez-vous à ce que des décalages de temps longs apparaissent, dans ce cas (Outlook Online), en particulier dans les paquets TLS:TLS qui affichent le passage de données d’application (par exemple, dans Netmon, vous pouvez trouver des paquets de données d’application via `.Protocol.TLS AND Description == "TLS:TLS Rec Layer-1 SSL Application Data"` ). Vous devriez voir une progression fluide dans le temps tout au long de la session. Si vous constatez de longs retards lors de l’actualisation de Outlook Online, cela peut être dû à un degré élevé de réinitialisations envoyées.

### <a name="latencyround-trip-time"></a>Latence/Durée de l’aller-retour

La latence est une mesure qui peut changer beaucoup en fonction de nombreuses variables, telles que la mise à niveau d’appareils plus récents, l’ajout d’un grand nombre d’utilisateurs à un réseau et le pourcentage de bande passante globale consommée par d’autres tâches sur une connexion réseau.

Il existe des calculatrices de bande passante Office 365 disponibles à partir de cette page planification réseau et optimisation des performances [pour Office 365](network-planning-and-performance.md) page.

Vous avez besoin de mesurer la vitesse de votre connexion ou de la bande passante de votre connexion ISP ? Essayez ce site (ou des sites comme celui-ci) : [Speedtest Official Site](https://www.speedtest.net/)ou interrogez votre moteur de recherche favori pour le test de vitesse **d’expression.**

#### <a name="tools"></a>Outils

- Ping
- PsPing
- Netmon
- Wireshark

#### <a name="what-to-look-for"></a>Ce qu’il faut rechercher

Pour suivre la latence dans un suivi, vous bénéficierez de l’enregistrement de l’adresse IP de l’ordinateur client et de l’adresse IP du serveur DNS dans Office 365. Cela a pour but de faciliter le filtrage du suivi. Si vous vous connectez via un proxy, vous aurez besoin de l’adresse IP de votre ordinateur client, de l’adresse IP proxy/sortie et de l’adresse IP DNS Office 365 pour faciliter le travail.

Une demande ping envoyée à outlook.office365.com vous indique le nom du centre de données qui reçoit la demande, même si  *ping*  peut ne pas être en mesure de se connecter pour envoyer les paquets ICMP consécutifs de marque. Si vous utilisez PsPing (un outil gratuit pour le téléchargement) et que vous précisez le port (443) et éventuellement pour utiliser IPv4 (-4), vous obtenez un aller-retour moyen pour les paquets envoyés. Cela fonctionne pour d’autres URL dans les services Office 365, comme `psping -4 yourSite.sharepoint.com:443` . En fait, vous pouvez spécifier un nombre de pings pour obtenir un échantillon plus important pour votre moyenne, essayez quelque chose comme `psping -4 -n 20 yourSite-my.sharepoint.com:443` .

> [!NOTE]
> PsPing n’envoie pas de paquets ICMP. Il teste avec des paquets TCP sur un port spécifique, afin que vous pouvez utiliser n’importe quel port que vous connaissez comme ouvert. Dans Office 365, qui utilise SSL/TLS, essayez d’attacher le port :443 à votre PsPing.

![Capture d’écran shows a ping resolving outlook.office365.com, and a PSPing with the 443 doing the same, but also reporting a 6.5ms average RTT.](../media/c64339f2-2c96-45b8-b168-c2a060430266.PNG)

Si vous avez chargé la page d’Office 365 lente lors d’un suivi réseau, vous devez filtrer une trace Netmon ou Wireshark pour `DNS` . Il s’agit de l’une desps que nous recherchons.

Voici les étapes à suivre pour filtrer votre Netmon afin d’obtenir l’adresse IP (et examiner la latence DNS). Cet exemple utilise outlook.office365.com, mais peut également utiliser l’URL d’un client SharePoint Online (hithere.sharepoint.com par exemple).

1. Ping sur l’URL et, dans les résultats, enregistrez le nom et l’adresse IP du serveur DNS à qui la demande `ping outlook.office365.com` ping a été envoyée.
2. Suivi réseau ouvrant la page, ou faisant l’action qui vous donne le problème de performances, ou, si vous voyez une latence élevée sur le ping, lui-même, le suivi réseau.
3. Ouvrez le suivi dans Netmon et le filtre pour DNS (ce filtre fonctionne également dans Wireshark, mais il est sensible à la `-- dns` cas). Étant donné que vous connaissez le nom du serveur DNS à partir de votre ping, vous pouvez également filtrer plus rapidement dans Netmon comme ceci : , qui ressemble à ceci dans wireshark dns et le cadre contient « `DNS AND ContainsBin(FrameData, ASCII, "namnorthwest")` namnorthwest ».<br/>Ouvrez le paquet de réponse et, dans la fenêtre **Détails** du cadre Netmon, cliquez sur **DNS** pour développer pour plus d’informations. Dans les informations DNS, vous trouverez l’adresse IP du serveur DNS vers qui la demande a été Office 365. Vous aurez besoin de cette adresse IP pour l’étape suivante (l’outil PsPing). Supprimez le filtre, cliquez avec le bouton droit sur la réponse DNS dans Netmon (**Frame Summary** \> **Find Conversations** \> **DNS**) pour voir la requête et la réponse DNS côte à côte.
4. Dans Netmon, notez également la colonne Décalage de temps entre la demande DNS et la réponse. Dans l’étape suivante, l’outil [PsPing](/sysinternals/downloads/psping) facile à installer et à utiliser est très pratique, car ICMP est souvent bloqué sur les pare-feu et PsPing suit de façon élégante la latence en millisecondes. PsPing termine une connexion TCP à une adresse et un port (dans notre cas, ouvrez le port 443).
5. Installez PsPing.
6. Ouvrez une invite de commandes (cmd de type Démarrer l’exécuter ou cmd de type de clé Windows) et modifiez le répertoire vers le répertoire où vous avez installé PsPing pour exécuter la commande \> \> \> PsPing. Dans mes exemples, vous pouvez voir que j’ai créé un dossier « Perf » à la racine de C. Vous pouvez faire de même pour un accès rapide.
7. Tapez la commande pour effectuer votre PsPing par rapport à l’adresse IP du serveur DNS Office 365 à partir de votre trace Netmon antérieure, y compris le numéro de port, par `psping -n 20 132.245.24.82:445` exemple. Vous aurez ainsi un échantillonnage de 20 pings et la latence moyenne à l’arrêt du PsPing.

Si vous souhaitez Office 365 via un serveur proxy, les étapes sont légèrement différentes. Vous devez d’abord psPing vers votre serveur proxy pour obtenir une valeur moyenne de latence en millisecondes pour proxy/sortie et retour, puis exécuter PsPing sur le proxy ou sur un ordinateur avec une connexion Internet directe pour obtenir la valeur manquante (celle vers Office 365 et retour).

Si vous choisissez d’exécuter PsPing à partir du proxy, vous aurez deux valeurs de millisecondes : ordinateur client vers serveur proxy ou point de sortie et serveur proxy vers Office 365. Et vous avez terminé ! Tout de même, l’enregistrement des valeurs.

Si vous exécutez PsPing sur un autre ordinateur client qui dispose d’une connexion directe à Internet, c’est-à-dire, sans proxy, vous aurez deux valeurs de millisecondes : l’ordinateur client vers le serveur proxy ou le point de sortie, et l’ordinateur client vers Office 365. Dans ce cas, soustrayez la valeur de l’ordinateur client au serveur proxy ou au point de sortie de la valeur de l’ordinateur client à Office 365, et vous aurez les numéros RTT de votre ordinateur client vers le serveur proxy ou le point de sortie, et du serveur proxy ou du point de sortie vers Office 365.

Toutefois, si vous pouvez trouver un ordinateur client directement connecté à l’emplacement touché, ou si vous ignorez le proxy, vous pouvez choisir de voir si le problème se reproduit à cet emplacement et de tester son utilisation par la suite.

La latence, comme dans un suivi Netmon, ces millisecondes supplémentaires peuvent s’ajouter, si elles sont suffisantes dans une session donnée.

![Latence générale dans Netmon, avec la colonne Délai par défaut Netmon ajoutée au Résumé de la trame.](../media/7ad17380-8527-4bc2-9b9b-6310cf19ba6b.PNG)

> [!NOTE]
> Votre adresse IP peut être différente des adresses IP indiquées ici, par exemple, votre ping peut renvoyer un nombre plus proche de 157.56.0.0/16 ou d’une plage similaire. Pour obtenir la liste des plages utilisées par les Office 365, consultez Office 365 [URL et plages d’adresses IP.](./urls-and-ip-address-ranges.md)

N’oubliez pas de développer tous les nodes (il existe un bouton en haut pour cela) si vous souhaitez rechercher, par exemple, 132.245.

### <a name="proxy-authentication"></a>Authentification proxy

Cela ne s’applique à vous que si vous êtes en train de passer par un serveur proxy. Si ce n’est pas le cas, vous pouvez ignorer ces étapes. Lorsque vous travaillez correctement, l’authentification proxy doit avoir lieu en millisecondes, de manière cohérente. Vous ne devriez pas voir de mauvaises performances intermittentes pendant les périodes d’utilisation maximales (par exemple).

Si l’authentification proxy est en cours, chaque fois que vous faites une nouvelle connexion TCP à Office 365 pour obtenir des informations, vous devez passer par un processus d’authentification en arrière-plan. Ainsi, par exemple, lorsque vous basculez du calendrier au courrier dans Outlook Online, vous vous authentifierez. Et dans SharePoint Online, si une page affiche du média ou des données provenant de plusieurs sites ou emplacements, vous vous authentifierez pour chaque connexion TCP nécessaire afin d’afficher les données.

Dans Outlook Online, les temps de chargement peuvent être lents chaque fois que vous basculez entre le calendrier et votre boîte aux lettres, ou les chargements de page lents dans SharePoint Online. Toutefois, d’autres symptômes ne sont pas répertoriés ici.

L’authentification proxy est un paramètre sur votre serveur proxy de sortie. Si elle provoque un problème de performances avec Office 365, vous devez consulter votre équipe réseau.

#### <a name="tools"></a>Outils

- Netmon
- Wireshark

#### <a name="what-to-look-for"></a>Ce qu’il faut rechercher

L’authentification proxy a lieu chaque fois qu’une nouvelle session TCP doit être resouverte, généralement pour demander des fichiers ou des informations au serveur, ou pour fournir des informations. Par exemple, vous pouvez voir l’authentification proxy autour des requêtes HTTP GET ou HTTP POST. Si vous souhaitez voir les images dans laquelle vous authentifier les demandes dans votre suivi, ajoutez la colonne « Résumé NTLMSSP » à Netmon et filtrez pour  `.property.NTLMSSPSummary` . Pour voir la durée de l’authentification, ajoutez la colonne Time Delta.

Pour ajouter une colonne à Netmon :

1. Cliquez avec le bouton droit sur une colonne telle que **Description.**
2. Cliquez **sur Choisir les colonnes.**
3. Recherchez _le résumé NTLMSSP_ et _le delta_ du temps dans la liste, puis cliquez sur **Ajouter.**
4. Déplacez les nouvelles colonnes en place avant ou derrière la colonne _Description_ afin de pouvoir les lire côte à côte.
5. Cliquez sur **OK**.

Même si vous n’ajoutez pas la colonne, le filtre Netmon fonctionne. Toutefois, votre résolution des problèmes sera beaucoup plus facile si vous voyez à quelle étape de l’authentification vous êtes.

Lorsque vous recherchez des instances d’authentification proxy, n’oubliez pas d’étudier tous les cadres où il existe un défi NTLM ou un message d’authentification. Si nécessaire, cliquez avec le bouton droit sur la partie spécifique du trafic et recherchez le \> protocole TCP Conversations. N’ignorez pas les valeurs de delta de temps dans ces conversations.

![Suivi Netmon montrant l’authentification proxy, filtrée par conversation.](../media/b640f176-0a52-4bbb-972e-60fb3d6aece2.PNG)

Un délai de quatre secondes dans l’authentification proxy comme dans Wireshark. Le **delta de** l’heure de la colonne d’image affichée précédente a été effectué en cliquant avec le bouton droit sur le champ du même nom dans les détails de l’image et en sélectionnant Ajouter en tant que colonne.  <br/> ![Dans Wireshark, la colonne « Time delta from previous displayed frame » peut être réalisée en cliquant avec le bouton droit sur le champ du même nom dans les détails de l’image et en sélectionnant Ajouter en tant que colonne.](../media/f5b7bde4-8067-4ee0-bc7f-e9062ce1ba6f.PNG)

### <a name="dns-performance"></a>Performances DNS

La résolution de noms fonctionne mieux et plus rapidement lorsqu’elle est aussi proche que possible du pays du client.

Si la résolution de nom DNS a lieu, elle peut ajouter des secondes aux chargements de page. Dans l’idéal, la résolution de nom se produit en moins de 100 ms. Si ce n’est pas le cas, vous devez poursuivre l’examen.

> [!TIP]
> Vous ne savez pas comment fonctionne la connectivité client Office 365 ? Jetez un coup d’œil au document référence de connectivité [client ici.](/previous-versions//dn741250(v=technet.10))

#### <a name="tools"></a>Outils

- Netmon
- Wireshark
- PsPing

#### <a name="what-to-look-for"></a>Ce qu’il faut rechercher

L’analyse des performances DNS est généralement un autre travail pour un suivi réseau. Toutefois, le PsPing est également utile dans ou en dehors, une cause possible.

Le trafic DNS est basé sur les demandes TCP et UDP et les réponses sont clairement marquées avec un ID qui vous aidera à faire correspondre une demande spécifique à sa réponse spécifique. Le trafic DNS s’affichera lorsque, par exemple, SharePoint Online utilise un nom de réseau ou une URL sur une page web. En règle générale, la majeure partie de ce trafic, sauf lors du transfert de zones, s’exécute sur UDP.

Dans Netmon et Wireshark, le filtre le plus simple qui vous permet d’examiner le trafic DNS est simplement `dns` . N’oubliez pas d’utiliser des cas inférieurs lors de la spécification du filtre. N’oubliez pas de vider votre cache de résolution DNS avant de commencer à reproduire le problème sur votre ordinateur client. Par exemple, si vous avez un chargement de page SharePoint Online lent pour la page d’accueil, vous devez fermer tous les navigateurs, ouvrir un nouveau navigateur, démarrer le suivi, vider votre cache de résolution DNS et parcourir votre site SharePoint Online. Une fois la page entière résolue, vous devez arrêter et enregistrer le suivi.

![Un filtre de base pour DNS dans Netmon est DNS.](../media/1bebc118-ca13-45f3-803f-ab73e7af401d.png)

Vous souhaitez examiner le décalage de temps ici. Il peut également être utile d’ajouter la colonne **Time Delta** à Netmon, ce que vous pouvez faire en effectuant les étapes suivantes :

1. Cliquez avec le bouton droit sur une colonne telle que **Description.**
2. Cliquez **sur Choisir les colonnes.**
3. Recherchez _Time Delta_ dans la liste, puis cliquez sur **Ajouter.**
4. Déplacez la nouvelle colonne en place avant ou derrière la colonne _Description_ afin de pouvoir les lire côte à côte.
5. Cliquez sur **OK**.

Si vous trouvez une requête intéressante, envisagez de l’isoler en cliquant avec le bouton droit sur cette requête dans le panneau Détails de l’image, en choisissant **Rechercher des conversations** \> **DNS**. Notez que le panneau Conversations réseau passe directement à la conversation spécifique dans son journal du trafic UDP.

![Une trace Netmon de Outlook Online filtrée par DNS, et l’utilisation de Find Conversations, puis DNS pour affiner les résultats.](../media/763cf20e-7b48-4a37-9449-c9978cfe118b.PNG)

Dans Wireshark, vous pouvez effectuer une colonne pour le temps DNS. Prenez votre trace (ou ouvrez un suivi) dans Wireshark et filtrez par `dns` , ou plus utilement,  `dns.time` . Cliquez sur une requête DNS et, dans le panneau affichant les détails,  `Domain Name System (response)` développez-les. Vous verrez un champ pour le temps (par exemple, `[Time: 0.001111100 seconds]` . Cliquez avec le bouton droit sur cette fois et **sélectionnez Appliquer en tant que colonne.** Vous aurez ainsi une colonne **Time** pour un tri plus rapide de votre suivi. Cliquez sur la nouvelle colonne pour trier en fonction des valeurs décro anses pour voir quel appel DNS a pris le plus de temps à résoudre.

[Une recherche sur SharePoint Online filtrée dans Wireshark par dns.time (en minuscules), avec l’heure des détails dans une colonne et triée par ordre croissant.](../media/1439dcc2-12ff-4ee2-9ef3-1484cf79c384.PNG)

Si vous souhaitez faire plus d’investigation sur le temps de résolution DNS, essayez un PsPing sur le port DNS utilisé par TCP (par exemple,  `psping <IP address of DNS server>:53` ) . Voyez-vous toujours un problème de performances ? Si vous le faites, le problème est plus susceptible d’être un problème de réseau plus large qu’un problème spécifique de l’application DNS que vous touchez pour résoudre le problème. Il est également utile de mentionner, là encore, qu’un test ping sur outlook.office365.com vous indiquera où se trouve la résolution de noms DNS pour Outlook Online (par exemple, outlook-namnorthwest.office365.com).

Si le problème semble spécifique au DNS, il peut être nécessaire de contacter votre service informatique pour examiner les configurations DNS et les forwardeurs DNS pour examiner ce problème plus en détail.

### <a name="proxy-scalability"></a>Évolutivité du proxy

Les services comme Outlook Online dans Office 365 accorder aux clients plusieurs connexions à long terme. Par conséquent, chaque utilisateur peut utiliser davantage de connexions nécessitant une durée de vie plus longue.

#### <a name="tools"></a>Outils

Mathématiques

#### <a name="what-to-look-for"></a>Ce qu’il faut rechercher

Il n’existe aucun outil de suivi ou de dépannage réseau spécifique à ce problème. Au lieu de cela, il est basé sur des calculs de bande passante en fonction de limitations et d’autres variables.

### <a name="tcp-max-segment-size"></a>Taille maximale du segment TCP

Se trouve dans la syn - SYN/ACK.  Effectuez cette vérification dans le suivi réseau de performances que vous avez pris pour vous assurer que les paquets TCP sont configurés pour transporter la quantité maximale de données possible.

L’objectif est d’obtenir un MSS de 1 460 octets pour la transmission des données. Si vous êtes derrière un proxy ou si vous utilisez un nat, n’oubliez pas d’exécuter ce test à partir du client vers proxy/sortie/NAT, et du proxy/sortie/NAT vers Office 365 pour obtenir de meilleurs résultats ! Il s’existe des sessions TCP différentes.

#### <a name="tools"></a>Outils

Netmon

#### <a name="what-to-look-for"></a>Ce qu’il faut rechercher

La taille de segment maximale TCP (MSS) est un autre paramètre de l’établir avec une combinaison triple dans votre suivi réseau, ce qui signifie que vous trouverez les données dont vous avez besoin dans le paquet SYN - SYN/ACK. MSS est en fait assez simple à voir.

Ouvrez la trace réseau de performances dont vous avez et trouvez la connexion qui vous intéresse, ou qui illustre le problème de performances.

> [!NOTE]
> Si vous recherchez un suivi et que vous avez besoin de trouver le trafic pertinent pour votre conversation, filtrez par l’adresse IP du client, ou l’adresse IP du serveur proxy ou du point de sortie, ou les deux. Directement, vous devrez tester l’URL que vous testez pour l’adresse IP de Office 365 dans le suivi et filtrer par celle-ci.

Vous regardez la trace de second main ? Essayez d’utiliser des filtres pour vous orienter. Dans Netmon, exécutez une recherche basée sur l’URL, par `Containsbin(framedata, ascii, "sphybridExample")` exemple, prenez note du numéro d’image.

Dans Wireshark, utilisez quelque chose comme  `frame contains "sphybridExample"` . Si vous remarquez que vous avez trouvé le trafic Winsock distant (RWS) (il peut apparaître comme un [PSH, ACK] dans Wireshark), n’oubliez pas que les connexions RWS sont visibles peu de temps avant les syn/AK pertinents, comme expliqué précédemment.

À ce stade, vous pouvez enregistrer le numéro  d’image, déposer le filtre, cliquer sur Tout le trafic dans la fenêtre Conversations réseau dans Netmon pour examiner la syn la plus proche.

Plus important encore, si vous n’avez reçu aucune des informations d’adresse IP au moment du suivi, la recherche de votre URL dans la trace (partie de , par exemple), vous donnera des adresses IP pour filtrer `sphybridExample-my.sharepoint.com` par.

Recherchez la connexion dans le suivi que vous souhaitez voir. Pour ce faire, vous pouvez analyser le suivi, en filtrant les adresses IP ou en sélectionnant des ID de conversation spécifiques à l’aide de la fenêtre Conversations réseau dans Netmon. Une fois que vous avez trouvé le paquet SYN, développez TCP (dans Netmon) ou le protocole de contrôle de transmission (dans Wireshark) dans le panneau Détails de l’image. Développez options TCP et MaxSegmentSize. Recherchez le cadre SYN-ACK associé et développez les options TCP et MaxSegmentSize. La plus petite des deux valeurs sera votre taille de segment maximale. Dans cette image, j’utilise la colonne intégrée dans Netmon appelée Résolution des problèmes TCP.

![Suivi réseau filtré dans Netmon à l’aide des colonnes intégrées.](../media/e073df13-71f8-497a-83b4-bb9f70bd9833.PNG)

La colonne intégrée se trouve en haut du panneau **Détails du** cadre. (Pour revenir à votre affichage normal, cliquez **à** nouveau sur Colonnes, puis choisissez **Fuseau horaire.)**

![Où trouver la liste déroulante des colonnes pour l’option Résolution des problèmes TCP (en haut du résumé de la trame).](../media/64fd4baa-a872-4f07-b959-752d7d37fd62.PNG)

Voici un suivi filtré dans Wireshark. Il existe un filtre spécifique à la valeur MSS ( `tcp.options.mss` ). Les images d’une liaison SYN, SYN/ACK et ACK sont liées en bas de l’équivalent Wireshark aux détails de trame (donc, image 47 ACK, liens vers 46 SYN/ACK, liens vers 43 SYN) pour faciliter ce type de travail.

![Suivi filtré dans Wireshark par tcp.options.mss pour la taille de segment maximale (MSS).](../media/51e278db-801b-48bc-9b68-87cf92f03fd6.PNG)

Si vous devez vérifier **l’accusé de** réception sélectif (rubrique suivante de cette matrice), ne fermez pas votre trace !

### <a name="selective-acknowledgment"></a>Accusé de réception sélectif

Se trouve dans la syn - SYN/ACK. Doit être signalé comme autorisé dans SYN et SYN/ACK. L’accusé de réception sélectif permet une retransmission plus fluide des données lorsqu’un ou plusieurs paquets sont manquants. Les appareils peuvent désactiver cette fonctionnalité, ce qui peut entraîner des problèmes de performances.

Si vous êtes derrière un proxy ou si vous utilisez un nat, n’oubliez pas d’exécuter ce test à partir du client vers proxy/sortie/NAT, et du proxy/sortie/NAT vers Office 365 pour obtenir de meilleurs résultats ! Il s’existe des sessions TCP différentes.

#### <a name="tools"></a>Outils

Netmon

#### <a name="what-to-look-for"></a>Ce qu’il faut rechercher

L’accusé de réception sélectif est un autre paramètre de l’établir avec SYN-SYN/ACK. Vous pouvez filtrer votre suivi pour SYN - SYN/ACK de nombreuses façons.

Recherchez la connexion dans le suivi qui vous intéresse soit en analysant le suivi, en filtrant par adresses IP, soit en cliquant sur un ID de conversation à l’aide de la fenêtre Conversations réseau dans Netmon. Une fois que vous avez trouvé le paquet SYN, développez TCP dans Netmon ou le protocole de contrôle de transmission dans Wireshark dans la section Détails de l’image. Développez options TCP, puis RESER. Recherchez le cadre SYN-ACK associé et développez les options TCP et son champ DROIT. Assurez-vous que LA COMBINAISON DNS est autorisée dans SYN et SYN/ACK. Voici les valeurs DNS comme dans Netmon et Wireshark.

![Accusé de réception sélectif (CAS) dans Netmon à la suite de tcp.flags.syn == 1.](../media/216f556f-5031-4ed2-b066-a0d9b3251fa2.PNG)

![SACK comme dans Wireshark avec le filtre tcp.flags.syn == 1.](../media/0a6e26e5-43dc-403b-adc9-3349a55f4e4b.PNG)

### <a name="dns-geolocation"></a>Géolocalisation DNS

Où dans le monde Office 365 tente de résoudre votre appel DNS a un impact sur votre vitesse de connexion.

Dans Outlook Online, une fois la première recherche DNS terminée, l’emplacement de ce DNS sera utilisé pour se connecter à votre centre de données le plus proche. Vous serez connecté à un serveur CAS Outlook Online, qui utilisera le réseau principal pour vous connecter au centre de données (dC) où vos données sont stockées. Cela est plus rapide.

Lorsque vous accédez à SharePoint Online, un utilisateur en déplacement est dirigé vers son centre de données actif, c’est-à-dire le centre de données dont l’emplacement est basé sur la base d’accueil de son client SPO (donc, un DC aux États-Unis si l’utilisateur est basé aux États-Unis).

Lync Online possède des nodes actifs dans plusieurs DC à la fois. Lorsque des demandes sont envoyées pour des instances de Lync Online, le DNS de Microsoft détermine l’endroit d’où la demande est envoyée dans le monde et retourne les adresses IP à partir du dC régional le plus proche où Lync Online est actif.

> [!TIP]
> Vous avez besoin d’en savoir plus sur la façon dont les clients se connectent Office 365 ? Prenons un coup d’œil à l’article de référence [sur](/previous-versions//dn741250(v=technet.10)) la connectivité client (et à ses graphismes utiles).

#### <a name="tools"></a>Outils

- Ping
- PsPing

#### <a name="what-to-look-for"></a>Ce qu’il faut rechercher

Dans la plupart des cas, les demandes de résolution de noms des serveurs DNS du client vers les serveurs DNS de Microsoft doivent dans la plupart des cas renvoyer l’adresse IP d’un centre de données régional(dC). Qu’est-ce que cela signifie pour vous ? Si votre siège social se trouve àLierre, en Inde, mais que vous êtes en déplacement aux États-Unis, lorsque votre navigateur effectue une demande pour Outlook Online, les serveurs DNS de Microsoft doivent vous remettre des adresses IP aux centres de données aux États-Unis , un centre de données régional. Si le courrier électronique est nécessaire Outlook, ces données sont envoyées sur le réseau principal rapide de Microsoft entre les centres de données.

DNS fonctionne plus rapidement lorsque la résolution de nom est effectuée aussi près que possible de l’emplacement de l’utilisateur. Si vous êtes en Europe, vous souhaitez passer à un DNS Microsoft en Europe et (idéalement) traiter avec un centre de données en Europe. Les performances d’un client en Europe allant vers DNS et un centre de données en Amérique seront plus lentes.

Exécutez l’outil Ping outlook.office365.com pour déterminer où votre demande DNS est acheminée dans le monde. Si vous êtes en Europe, vous devriez voir une réponse provenant d’un outlook-emeawest.office365.com. Dans les Amériques, attendez-vous à ce qu’un outlook-namnorthwest.office365.com.

Ouvrez l’invite de commandes sur l’ordinateur client (via la cmd Démarrer \> \> l’Windows \> cmd de type de clé). Tapez ping outlook.office365.com puis appuyez sur Entrée. N’oubliez pas de spécifier -4 si vous souhaitez spécifier un ping via IPv4. Vous ne pouvez pas obtenir de réponse des paquets ICMP, mais vous devez voir le nom du DNS vers lequel la demande a été acheminée. Si vous souhaitez voir les numéros de latence de cette connexion, essayez PsPing vers l’adresse IP du serveur qui est renvoyée par ping.

![Commande ping d’outlook.office365.com affichant la résolution dans outlook-namnorthwest.](../media/06c944d5-6159-43ec-aa31-757770695e8b.PNG)

![PSPing vers l’adresse IP renvoyée par la commande ping à outlook.office365.com latence moyenne de 28 millisecondes.](../media/f2b25a75-1a87-4479-b8a7-fa4375683507.PNG)

### <a name="office-365-application-troubleshooting"></a>Office 365 Résolution des problèmes d’application

#### <a name="tools"></a>Outils

- Netmon
- HTTPWatch
- Console F12 dans le navigateur

Nous ne couvrent pas les outils utilisés dans le dépannage propre à l’application dans cet article propre au réseau. Mais vous trouverez des ressources que vous *pouvez* utiliser [sur cette page.](https://support.office.com/article/Network-planning-and-performance-tuning-for-Office-365-e5f1228c-da3c-4654-bf16-d163daee8848)

## <a name="related-topics"></a>Voir aussi

[Gestion des points de terminaison Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)

[Points de terminaison Office 365 - FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)