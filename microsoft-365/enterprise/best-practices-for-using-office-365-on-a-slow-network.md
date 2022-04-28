---
title: Meilleures pratiques pour l’utilisation de Office 365 sur un réseau lent
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/29/2016
audience: End User
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
search.appverid:
- MET150
- MET150
- MOP150
- MEW150
- BCS160
ms.assetid: fd16c8d2-4799-4c39-8fd7-045f06640166
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
description: Cet article vous guide tout au long des meilleures pratiques que vous pouvez adopter pour utiliser Office 365 sur un réseau lent.
ms.openlocfilehash: 5ed3a9dfc665d5067fb3f310fc74aa4b100190f2
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091630"
---
# <a name="best-practices-for-using-office-365-on-a-slow-network"></a>Meilleures pratiques pour l’utilisation de Office 365 sur un réseau lent

Ne serait-ce pas bien si votre connexion Internet était toujours rapide et jamais en panne? Peut-être que ce jour viendra. Mais en attendant, il ya des choses pratiques que vous pouvez faire pour travailler autour d’un réseau balky et encore faire votre travail quotidien. Bien que Office 365 soit un service basé sur le cloud, il offre également de nombreuses façons d’utiliser votre contenu hors connexion et de maintenir en douceur la synchronisation de vos modifications. En outre, il est parfois plus efficace d’utiliser du contenu hors connexion simplement parce que les applications s’exécutent plus rapidement et que l’interface utilisateur est plus réactive. Le point est le suivante: Office 365 vous donne le meilleur des deux mondes. Voici comment en tirer parti.

> [!TIP]
> Vous voulez voir à quel point votre connexion réseau est lente (ou rapide) ? Essayez le [test de vitesse OOKLA](https://www.speedtest.net/) ou [l’application de test de vitesse réseau](https://www.windowsphone.com/store/app/network-speed-test/9b9ae06b-2961-41ef-987d-b09567cffe70).

## <a name="why-is-my-network-so-slow"></a>Pourquoi mon réseau est-il si lent ?

Bien que vous n’ayez pas le contrôle sur les performances du réseau lui-même, il est utile de comprendre ce qui se passe en arrière-plan. Internet est extrêmement complexe, mais il existe quelques concepts qui peuvent vous aider à mieux comprendre la situation. En suivant les meilleures pratiques de cet article, vous pouvez résoudre les problèmes de performances et réduire la frustration.

### <a name="major-factors-that-affect-network-performance"></a>Principaux facteurs qui affectent les performances réseau

![Facteurs de performances réseau.](../media/62a94322-3f1a-4d2d-bbdc-2aa0722d2d96.png)

 **Bande passante et latence** : les deux mesures les plus importantes des performances réseau sont la bande passante et la latence :

- La bande passante est le débit mesuré en bits par seconde. Plus grand est mieux. La bande passante est comme un canal d’eau. Plus le tuyau est grand, plus il y a d’eau que l’on peut « passer ».

- La latence est le temps nécessaire pour que le contenu passe d’un serveur ou d’un service à votre appareil et est mesurée en millisecondes. Plus vite, c’est mieux. La latence peut être due à un certain nombre de facteurs, notamment une faible bande passante, une connexion éparse ou un temps de transmission.

 **Problèmes courants** : outre la bande passante et la latence, d’autres problèmes ont un impact sur les performances du réseau et sont souvent imprévisibles. Les performances du réseau peuvent fluctuer en fonction de l’heure de la journée ou de votre emplacement physique. Le réseau peut être obstrué lorsque certains événements se produisent et que l’utilisation d’Internet est en forte augmentation, comme une catastrophe naturelle ou un événement public majeur. La taille et la complexité de la page chargée et le nombre et la taille des fichiers transférés ont une incidence directe sur les performances. Une connexion Wi-Fi peut se dégrader temporairement : par exemple, vous interrogez une grande réunion de conférence de milliers en demandant à tout le monde de tweeter en même temps.

 **Considérations relatives à un réseau satellite** : Un réseau satellite est utile lorsqu’un réseau terrestre n’est pas possible, comme l’arrière-pays, un navire de croisière ou une région scientifique éloignée. Ces réseaux reposent sur des satellites positionnés sur une orbite géosynchrone à 22 000 milles au-dessus de l’équateur. Toutefois, une transmission parcourt en fait environ 90 000 milles, et un réseau satellite a donc une latence plus lente (500 ms ou plus) qu’un réseau terrestre (20 à 50 ms). Dans les meilleures conditions, vous ne remarquerez peut-être pas cette latence, mais pour télécharger des fichiers volumineux, diffuser des vidéos en continu et jouer à des jeux, vous le serez probablement. Un autre problème est le « fondu de pluie » dans lequel les fortes conditions météorologiques, comme les orages et les blizzards, peuvent interrompre temporairement la transmission par satellite.

## <a name="are-you-sure-its-the-network"></a>Êtes-vous sûr que c’est le réseau ?

Chaque fois que vous rencontrez des problèmes de performances, assurez-vous d’abord que votre appareil n’est pas la cause racine du problème. Il existe deux choses que vous pouvez faire qui peuvent apporter une grande amélioration :

- Assurez-vous que votre appareil fonctionne bien et qu’il n’y a aucun programme malveillant sur votre ordinateur.

- Si possible, achetez plus de mémoire. L’ajout de mémoire est le moyen le plus simple et le plus efficace d’améliorer les performances sur votre appareil. Il est particulièrement utile lorsque vous travaillez avec des fichiers et des vidéos volumineux.

Pour plus d’informations, consultez [Windows Performances et maintenance](https://windows.microsoft.com/windows/performance-maintenance-help#performance-maintenance-help) et [Astuces pour améliorer les performances des PC dans Windows 10](https://support.microsoft.com/help/4002019/windows-10-improve-pc-performance).

## <a name="best-practices-for-using-your-browser"></a>Meilleures pratiques pour l’utilisation de votre navigateur

Votre navigateur est votre passerelle vers Office 365, ce qui peut avoir un impact sur les performances, en particulier avec le temps nécessaire pour charger une page et la fréquence à laquelle vous effectuez des allers-retours vers le service Office 365.

### <a name="browsers-in-general"></a>Navigateurs en général

Voici quelques suggestions pour les navigateurs en général :

- Désactivez les modules complémentaires de navigateur qui peuvent avoir un impact sur les performances ou dont vous n’avez pas vraiment besoin.

- Augmentez la taille du cache pour vos fichiers Internet temporaires.

- Une fois que vous êtes connecté à votre compte professionnel ou scolaire, laissez la fenêtre du navigateur ouverte tout au long de la journée. Vous pouvez ouvrir d’autres onglets et fenêtres sans vous reconnecter. Si vous devez vous connecter à un autre compte, utilisez la navigation privée.

- Une fois que chaque page est téléchargée et ouverte, gardez-les ouvertes à l’aide d’onglets. Il est facile de naviguer entre les onglets et d’utiliser la page plus tard dans la journée. Actualisez une page uniquement si vous avez besoin des données les plus récentes sur cette page.

- Si l’ouverture d’une page prend trop de temps, arrêtez le téléchargement de la page (appuyez sur Échap), puis actualisez la page (appuyez sur F5).

- Si possible, réduisez les allers-retours à Office 365. Par exemple, au lieu de paginer des listes ou des bibliothèques, utilisez la recherche pour localiser les fichiers dans une grande bibliothèque et le filtrage dans une liste pour accéder directement aux résultats souhaités. Vous pouvez également créer des vues qui réduisent le temps de chargement de la page. Pour plus d’informations, consultez [Gérer les listes et bibliothèques volumineuses dans Office 365](https://support.office.com/article/b4038448-ec0e-49b7-b853-679d3d8fb784#BKMK_PAGES).

- Si les performances vidéo sont médiocres, vous pouvez télécharger la vidéo et la regarder sur votre appareil. Un lien de téléchargement peut être disponible, ou vous pouvez cliquer avec le bouton droit sur le lien vidéo, puis sélectionner **Enregistrer la cible sous**.

### <a name="browser-specific"></a>Spécifique au navigateur

Voici quelques suggestions pour votre navigateur spécifique :

- **Internet Explorer** : mise à niveau vers Internet Explorer version 11 ou ultérieure pour améliorer considérablement les performances par rapport aux versions précédentes. Pour plus d’informations, consultez le [guide de résolution des problèmes pour Internet Explorer](https://support.microsoft.com/help/2437121/troubleshooting-guide-for-internet-explorer-when-you-access-office-365).
- **FireFox** : pour plus d’informations, consultez [Firefox est lent ou cesse de fonctionner](https://support.mozilla.org/products/firefox/fix-problems/slowness-or-hanging).
- **Safari** : Pour plus d’informations, consultez [Apple - Safari](https://www.apple.com/safari/).
- **Chrome** : pour plus d’informations, consultez [l’aide de Chrome](https://support.google.com/chrome/?hl=en).

## <a name="best-practices-for-using-outlook-and-outlook-web-app"></a>Meilleures pratiques pour utiliser Outlook et Outlook Web App

La lecture, l’écriture et l’organisation du courrier électronique constituent une grande partie de la journée de chacun. Outlook et Outlook Web App (OWA) offrent une prise en charge hors connexion. L’utilisation d’une application de messagerie sur votre téléphone intelligent est une autre alternative utile. Utilisez les options suivantes qui répondent le mieux à vos besoins :

- Effectuez une mise à niveau vers la dernière version de Outlook pour améliorer considérablement les performances par rapport aux versions précédentes.

- Outlook Web App vous permet de créer des messages hors connexion, des contacts et des événements de calendrier qui sont chargés lorsque OWA est en mesure de se connecter à Office 365. Pour plus d’informations sur la configuration et l’utilisation d’OWA en mode hors connexion, consultez [Utilisation de Outlook Web App hors connexion](https://support.office.com/article/3214839c-0604-4162-8a97-6856b4c27b36).

- Outlook vous permet de travailler en mode mis en cache, dans lequel il se connecte automatiquement dans la mesure du possible. Vous pouvez avoir Outlook télécharger l’intégralité de votre boîte aux lettres, ou simplement une partie de celle-ci. Pour plus d’informations, consultez [Activer le mode Exchange mis en cache](https://support.office.com/article/7885af08-9a60-4ec3-850a-e221c1ed0c1c) et [travailler hors connexion dans Outlook](https://support.office.com/article/f3a1251c-6dd5-4208-aef9-7c8c9522d633).

- Outlook offre également un mode hors connexion. Pour l’utiliser, vous devez d’abord configurer le mode mis en cache afin que les informations de votre compte soient copiées vers votre ordinateur. En mode hors connexion, Outlook tentez de vous connecter à l’aide des paramètres d’envoi et de réception, ou lorsque vous le définissez manuellement pour qu’il fonctionne en ligne. Pour plus d’informations, consultez [Travailler hors connexion pour éviter les frais de connexion de données](https://support.office.com/article/827fe51f-5609-4062-82b4-3578057f9282), [modifier les paramètres d’envoi et de réception lorsque vous travaillez hors connexion](https://support.office.com/article/f681ec10-cb14-40cb-8709-1909a13c304a) et [passer du mode hors connexion à la connexion en ligne](https://support.office.com/article/2460e4a8-16c7-47fc-b204-b1549275aac9).

- Si vous disposez d’un téléphone intelligent, vous pouvez l’utiliser pour trier votre courrier électronique et votre calendrier sur le réseau de votre opérateur téléphonique.

> [!NOTE]
> Voici quelques conseils sur l’utilisation de Outlook ou OWA. Si l’espace disque n’est pas un problème sur votre appareil, Outlook dispose d’un ensemble complet de fonctionnalités et peut vous être le mieux adapté. Si l’espace disque est un problème sur votre appareil, envisagez d’utiliser OWA qui a un sous-ensemble de fonctionnalités, mais qui fonctionne également mieux dans une situation en ligne. Bien sûr, vous pouvez utiliser l’un ou l’autre parce qu’ils fonctionnent bien ensemble.

## <a name="best-practices-for-using-onedrive-for-business"></a>Meilleures pratiques pour l’utilisation de OneDrive Entreprise

OneDrive Entreprise est conçu dès le départ pour fonctionner avec vos fichiers en ligne et hors connexion. Une fois que vous l’avez configurée, la synchronisation des modifications se produit automatiquement et de manière fiable où et à chaque fois que vous les apportez. Si le réseau est lent, vous pouvez utiliser la version hors connexion des fichiers.

L’application de synchronisation OneDrive Entreprise est fourni avec un abonnement SharePoint Online et Office 365 entreprise, ou vous pouvez [télécharger](https://support.microsoft.com/kb/2903984) l’application de synchronisation OneDrive Entreprise gratuitement. Cette application est également plus rapide que l’utilisation des commandes **Ouvrir dans l’Explorateur** ou **Télécharger**. Pour plus d’informations, consultez [Configurer votre ordinateur pour synchroniser vos fichiers OneDrive Entreprise dans Office 365](https://support.office.com/article/23e1f12b-d896-4cb1-a238-f91d19827a16).

Voici quelques conseils supplémentaires pour l’utilisation de l’application de synchronisation OneDrive Entreprise :

- Si vous synchronisez une bibliothèque volumineuse pour la première fois, démarrez la synchronisation pendant les heures creuses, par exemple, pendant la nuit.
- Vous pouvez utiliser l’option [Arrêter la synchronisation d’une bibliothèque avec la fonctionnalité d’application OneDrive Entreprise](https://support.office.com/article/a7e41f1f-3a98-4ca7-9443-f10250688330) pour arrêter temporairement la synchronisation des mises à jour. Toutefois, utilisez cette fonctionnalité pendant de courtes périodes, par exemple quelques heures à la fois, pour éviter de mettre en file d’attente un grand nombre de mises à jour et pour réduire le risque de conflits de fusion si plusieurs personnes travaillent sur le même document.

## <a name="best-practices-for-using-onenote"></a>Meilleures pratiques pour l’utilisation de OneNote

Chaque SharePoint site d’équipe dispose d’un bloc-notes OneNote intégré et vous pouvez facilement créer le vôtre. OneNote est un excellent moyen de collecter des informations opportunes dont vous avez besoin tous les jours pour effectuer des tâches. Par exemple, de nombreuses équipes utilisent OneNote comme point de collecte pour les réunions hebdomadaires, les notes de projet, les idées, les plans et les rapports d’état. Vous pouvez organiser soigneusement ces informations disparates à l’aide de pages, de sections et d’onglets.

La beauté de OneNote est que vous pouvez accéder au contenu à partir de pratiquement n’importe quel appareil, qu’il s’agisse d’un ordinateur de bureau, d’un ordinateur portable, d’une tablette ou d’un téléphone intelligent. Et vous n’avez pas à vous soucier de l’enregistrement ou de la synchronisation, car OneNote le fait pour vous.

Pour plus d’informations, consultez [Microsoft OneNote](https://office.microsoft.com/onenote).

## <a name="best-practices-for-using-skype-for-business-and-lync-online"></a>Meilleures pratiques pour l’utilisation de Skype Entreprise et Lync Online

Voici des instructions générales pour utiliser Skype Entreprise ou Lync Online lorsque votre réseau est lent :

- Utilisez la messagerie instantanée chaque fois que vous le pouvez, car elle fonctionne bien sur un réseau lent.

- Évitez d’effectuer des appels téléphoniques via un réseau privé virtuel (VPN) ou des connexions de service d’accès à distance (RAS).

- Assurez-vous que votre périphérique audio est approuvé. Pour plus d’informations, consultez [Téléphones et appareils qualifiés pour Microsoft Lync](/skypeforbusiness/lync-cert/ip-phones).

- Lorsque vous utilisez PowerPoint dans une présentation en ligne, réduisez la taille et la complexité des diapositives. Pour plus d’informations, consultez [Astuces pour améliorer les performances de votre présentation](https://support.office.com/article/34c82835-5f23-4bf0-98cc-72235bbd2949).

- Les performances vidéo dépendent beaucoup des performances du réseau. Évitez d’utiliser la vidéo si votre réseau est lent.

Pour plus d’informations, consultez [La qualité audio ou vidéo médiocre dans Lync Online](https://support.microsoft.com/kb/2386655), ou comment [résoudre les problèmes de connexion dans Skype Entreprise](https://support.office.com/article/troubleshoot-connection-issues-in-skype-for-business-ca302828-783f-425c-bbe2-356348583771).

## <a name="best-practices-for-using-sharepoint-lists"></a>Meilleures pratiques pour l’utilisation de listes SharePoint

L’utilisation des données de liste hors connexion pour « nettoyer », analyser ou signaler des données est un excellent moyen de réduire l’impact d’un réseau lent. Vous pouvez lire et écrire la plupart des listes à partir de Microsoft Access 2019 et de Microsoft Access 2016 en les liant. Vous pouvez également exporter une liste vers une table Excel, qui crée une connexion de données unidirectionnelle entre la table Excel et la liste. Découvrez comment [travailler hors connexion avec des tables liées à des listes SharePoint](https://support.office.com/article/work-offline-with-tables-that-are-linked-to-sharepoint-lists-5d66594a-6176-4a25-a198-320f13ccf41e).

Pour plus d’informations, consultez la section « Plus sur la gestion des listes volumineuses » dans [Gérer les listes et bibliothèques volumineuses dans Office 365](https://support.office.com/article/b4038448-ec0e-49b7-b853-679d3d8fb784).

## <a name="best-practices-for-customizing-web-pages"></a>Meilleures pratiques pour la personnalisation des pages web

Lorsque vous personnalisez une page web, vous risquez de provoquer par inadvertance des performances médiocres avec la page. Un certain nombre de facteurs peuvent avoir un impact, comme la complexité et la taille de la page, le nombre de composants WebPart ajoutés, le nombre d’éléments de liste ou de bibliothèque initialement affichés et la façon dont vous codez la page.

Pour plus d’informations, consultez [Tune SharePoint Online Performances](tune-sharepoint-online-performance.md).

## <a name="best-practices-for-using-project-online"></a>Meilleures pratiques pour l’utilisation de Project Online

Les instructions suivantes peuvent aider à améliorer les performances du réseau.

- Project Online et SharePoint Online nécessitent une synchronisation, ce qui peut prendre du temps. Si le chiffre d’affaires de vos équipes de projet est faible, désactivez Project Site Sync pour améliorer les performances Project Publier et Project Pages de détails. Limitez la synchronisation Active Directory aux groupes de ressources qui doivent réellement utiliser le système et surveillez les éventuels problèmes d’autorisation après la synchronisation de grands groupes.

- Si votre organisation utilise des sites de projet, créez-les à la demande plutôt que automatiquement. Cela accélère la première expérience de publication et évite de créer des sites et du contenu inutiles.

- Project Pages de détails (PDP) peut déclencher un recalcul de l’ensemble du projet et lancer des actions de flux de travail, qui peuvent toutes deux être des opérations nécessitant beaucoup de performances. Pour éviter de déclencher deux processus de mise à jour en même temps sur le même PDP, évitez de mettre à jour les champs de calendrier (date de début, date de fin, date d’état et date actuelle) et les champs non planifiés (nom du projet, description et propriétaire).

- Réduisez le nombre de composants WebPart et de champs personnalisés affichés sur chaque PDP. Créez un PDP dédié avec les seuls champs qui nécessitent une mise à jour pour améliorer la charge et gagner du temps.

- Lorsque vous utilisez OData pour la création de rapports, limitez la quantité de données que vous interrogez au moment de l’exécution à l’aide du filtrage côté serveur.

Pour plus d’informations, consultez [Tune Project Online performances](https://support.office.com/article/12ba0ebd-c616-42e5-b9b6-cad570e8409c).

## <a name="whats-the-best-way-to-report-problems"></a>Quelle est la meilleure façon de signaler les problèmes ?

Microsoft améliore continuellement les performances globales des Office 365 en surveillant le réseau, en mesurant la bande passante et la latence, en améliorant le temps de chargement des pages, en réduisant les E/S disque, en repensant les pages pour utiliser la stratégie de téléchargement minimale, en ajoutant du matériel aux centres de données et en ajoutant d’autres centres de données. Pour plus d’informations sur la vérification de votre état actuel et la création de rapports sur les problèmes, consultez [Comment vérifier Office 365'intégrité du service](view-service-health.md).

## <a name="see-also"></a>Voir aussi

[Planification réseau et optimisation des performances pour Office 365](network-planning-and-performance.md)

[Principes de connectivité réseau Office 365](microsoft-365-network-connectivity-principles.md)

[Gestion des points de terminaison Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)

[Points de terminaison Office 365 - FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
