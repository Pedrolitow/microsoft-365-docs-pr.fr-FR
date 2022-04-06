---
title: Inventaire des appareils
description: Découvrez les fonctionnalités disponibles que vous pouvez utiliser dans la liste Appareils, telles que le tri, le filtrage et l’exportation de la liste pour améliorer les examens.
keywords: sort, filter, export, csv, device name, domain, last seen, internal IP, health state, active alerts, active malware detections, threat category, review alerts, network, connection, malware, type, password stealer, ransomware, exploit, threat, general malware, unwanted software
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: d254eee546187311a25a0e6cc433005a26ff57e6
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2022
ms.locfileid: "64632424"
---
# <a name="device-inventory"></a>Inventaire des appareils

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-machinesview-abovefoldlink)

La **liste Appareils affiche** la liste des appareils de votre réseau sur lequel des alertes ont été générées. Par défaut, la file d’attente affiche les appareils visibles au cours des 30 derniers jours.

En un coup d’œil, vous verrez des informations telles que le domaine, le niveau de risque, la plateforme du système d’exploitation et d’autres détails pour faciliter l’identification des appareils les plus exposés.

Vous pouvez choisir parmi plusieurs options pour personnaliser l’affichage liste des appareils. Dans la barre de navigation supérieure, vous pouvez :

- Ajouter ou supprimer des colonnes
- Exporter la liste entière au format CSV
- Sélectionner le nombre d’éléments à afficher par page
- Appliquer des filtres

Pendant le processus d’intégration, la liste **Appareils** est progressivement remplie avec les appareils qui commencent à signaler les données de capteur. Utilisez cette vue pour suivre vos points de terminaison intégrés lors de leur mise en ligne ou téléchargez la liste complète des points de terminaison en tant que fichier CSV pour l’analyse hors connexion.

> [!NOTE]
> Si vous exportez la liste des appareils, elle contiendra tous les appareils de votre organisation. Le téléchargement peut prendre beaucoup de temps, en fonction de la taille de votre organisation. L’exportation de la liste au format CSV affiche les données de manière non filtrée. Le fichier CSV inclut tous les appareils de l’organisation, quel que soit le filtrage appliqué dans l’affichage lui-même.

:::image type="content" source="images/device-inventory.png" alt-text="Liste des appareils" lightbox="images/device-inventory.png":::

## <a name="sort-and-filter-the-device-list"></a>Trier et filtrer la liste des appareils

Vous pouvez appliquer les filtres suivants pour limiter la liste des alertes et obtenir une vue plus centrée.

### <a name="device-name"></a>Nom du périphérique

Pendant le Microsoft Defender pour point de terminaison d’intégration, les appareils intégrés à MDE sont progressivement intégrés dans l’inventaire des appareils à mesure qu’ils commencent à signaler les données du capteur. Ensuite, l’inventaire des appareils est rempli par les appareils qui sont découverts dans votre réseau via le processus de découverte d’appareils. L’inventaire des appareils possède trois onglets qui listent les appareils par :

- **Ordinateurs et appareils mobiles** : Enterprise terminaison (stations de travail, serveurs et appareils mobiles)
- **Périphériques réseau** : périphériques tels que les routeurs et commutateurs
- **Appareils IoT** : appareils tels que les imprimantes et les appareils photo

## <a name="navigate-to-the-device-inventory-page"></a>Accéder à la page Inventaire des appareils

Accédez à la page d’inventaire des appareils en sélectionnant **Inventaire** des appareils dans le menu **de navigation Points** de terminaison [dans Microsoft 365 Defender portail.](/defender/microsoft-365-security-center-mde)

## <a name="device-inventory-overview"></a>Vue d’ensemble de l’inventaire des appareils

L’inventaire des appareils s’ouvre sous **l’onglet Ordinateurs et Mobile** . En un coup d’œil, vous verrez des informations telles que le nom de l’appareil, le domaine, le niveau de risque, le niveau d’exposition, la plateforme du système d’exploitation, l’état d’intégration, l’état d’état du capteur et d’autres détails pour faciliter l’identification des appareils les plus exposés.

Utilisez la **colonne État de l’intégration** pour trier et filtrer les appareils détectés et ceux déjà intégrés à Microsoft Defender pour point de terminaison.

![Image de la liste des appareils avec liste d’appareils.](images/device-inventory.png)

Les onglets **Périphériques réseau** et **Appareils IoT** vous offrent également des informations telles que le fournisseur, le modèle et le type d’appareil :

![Image de la liste des périphériques réseau.](images/device-inventory-networkdevices.png)

En haut de chaque onglet Inventaire des appareils, vous pouvez voir le nombre total d’appareils, le nombre d’appareils qui ne sont pas encore intégrés et le nombre d’appareils identifiés comme étant plus risqués pour votre organisation. Vous pouvez utiliser ces informations pour vous aider à hiérarchiser les appareils pour améliorer la posture de sécurité.

Le **nombre d’appareils** récemment découverts pour les périphériques réseau et les onglets des appareils IoT indique le nombre de nouveaux appareils détectés, au cours des 7 derniers jours, répertoriés dans l’affichage actuel.

![Image du nouveau nombre d’appareils détectés.](images/new-discovered-devices.png)

## <a name="explore-the-device-inventory"></a>Explorer l’inventaire des appareils

Vous pouvez choisir parmi plusieurs options pour personnaliser l’affichage d’inventaire des appareils. Dans la barre de navigation supérieure de chaque onglet, vous pouvez :

- Rechercher un appareil par nom
- Recherche d’un appareil par l’adresse IP ou le préfixe d’adresse IP le plus récemment utilisé
- Ajouter ou supprimer des colonnes
- Exporter la liste entière au format CSV pour l’analyse hors connexion
- Sélectionner la plage de dates à afficher
- Appliquer des filtres

> [!NOTE]
> Si vous exportez la liste des appareils, elle contiendra tous les appareils de votre organisation. Le téléchargement peut prendre beaucoup de temps, en fonction de la taille de votre organisation. L’exportation de la liste au format CSV affiche les données de manière non filtrée. Le fichier CSV inclut tous les appareils de l’organisation, quel que soit le filtrage appliqué dans l’affichage lui-même.

Vous pouvez utiliser les fonctionnalités de tri et de filtrage disponibles sur chaque onglet d’inventaire des appareils pour obtenir une vue plus centrée et pour vous aider à évaluer et à gérer les appareils de votre organisation.

Le nombre en haut de chaque onglet sera mis à jour en fonction de l’affichage actuel.

## <a name="use-filters-to-customize-the-device-inventory-views"></a>Utiliser des filtres pour personnaliser les affichages d’inventaire des appareils

Filtre | Description
:---|:---
**Niveau de risque** </br> | Le niveau de risque reflète l’évaluation globale des risques de l’appareil en fonction d’une combinaison de facteurs, notamment les types et la gravité des alertes actives sur l’appareil. La résolution des alertes actives, l’approbation des activités de correction et la suppression des alertes suivantes peuvent réduire le niveau de risque.
**Niveau d’exposition** </br> | Le niveau d’exposition reflète l’exposition actuelle de l’appareil en fonction de l’impact cumulé de ses recommandations de sécurité en attente. Les niveaux possibles sont faibles, moyens et élevés. Une faible exposition signifie que vos appareils sont moins vulnérables à l’exploitation. </br> </br> Si le niveau d’exposition indique « Aucune donnée disponible », il existe plusieurs raisons pour lesquelles cela peut être le cas :</br>- L’appareil a cessé de signaler pendant plus de 30 jours. Dans ce cas, il est considéré comme inactif et l’exposition n’est pas calculée.</br>- Le système d’exploitation de l’appareil n’est pas pris en charge : consultez [la Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/minimum-requirements).</br>- Appareil avec agent obsolète (peu probable).
**Tags** </br> | Filtrez la liste en fonction du regroupement et du marquage que vous avez ajoutés à des appareils individuels. Voir [Créer et gérer des balises d’appareil](machine-tags.md).
**Valeur de l’appareil**</br> | Filtrez la liste selon que l’appareil a été marqué comme valeur élevée ou valeur faible.
**État d’exclusion** </br> | Filtrez la liste selon que l’appareil a été exclu ou non. Pour plus d’informations, voir [Exclure des appareils](exclude-devices.md).
**Plateforme du système d’exploitation** </br>| Filtrer selon les plateformes de système d’exploitation que vous souhaitez examiner </br></br>(_Ordinateurs et appareils mobiles et IoT uniquement_)
**Première vue** </br> | Filtrez votre vue en fonction de la première fois que l’appareil a été vu sur le réseau ou de la première fois qu’il a été signalé par le Microsoft Defender pour point de terminaison de données.</br></br>(_Ordinateurs et appareils mobiles et IoT uniquement_)
**Version de Windows** </br> | Filtrez par Windows versions que vous souhaitez examiner.</br></br> (_Ordinateurs et appareils mobiles uniquement_)
**État d’intégrité du capteur** </br> | Filtrez selon les états d’état de capteur suivants pour les appareils intégrés Microsoft Defender pour point de terminaison :</br> - **Actif** : appareils qui rapportent activement des données de capteur au service.</br> - **Inactif** : appareils qui ont cessé d’envoyer des signaux pendant plus de 7 jours. </br> - **Mal configuré : appareils** dont les communications avec le service sont réduites ou qui ne peuvent pas envoyer de données de capteur. </br> Les appareils mal configurés peuvent également être classés sur : </br>  - Aucune donnée de capteur </br>  - Communications altérées </br>  Pour plus d’informations sur la façon de résoudre les problèmes sur les appareils mal configurés, voir [Corriger les capteurs défectueux](/microsoft-365/security/defender-endpoint/fix-unhealthy-sensors).</br></br> (_Ordinateurs et appareils mobiles uniquement_)
**État de l’intégration** </br> | L’état d’intégration indique si l’appareil est actuellement Microsoft Defender pour point de terminaison ou non. Vous pouvez filtrer selon les états suivants : </br> - **Intégré :** le point de terminaison est intégré à Microsoft Defender pour point de terminaison.  </br> - **Peut être intégré :** le point de terminaison a été découvert dans le réseau en tant qu’appareil pris en charge, mais il n’est pas actuellement intégré. Microsoft recommande vivement l’intégration de ces appareils. </br> - **Non pris en charge** : le point de terminaison a été découvert dans le réseau, mais n’est pas pris en charge par Microsoft Defender pour point de terminaison. </br> - **Informations insuffisantes** : le système n’a pas pu déterminer la prise en charge de l’appareil.</br></br> (_Ordinateurs et appareils mobiles uniquement_)
**État de l’antivirus** </br> | Filtrez l’affichage selon que l’état antivirus est désactivé, non mis à jour ou inconnu.</br></br> (_Ordinateurs et appareils mobiles uniquement_)
**Group** </br> | Filtrez la liste en fonction du groupe que vous souhaitez examiner. </br></br> (_Ordinateurs et appareils mobiles uniquement_)
**Géré par** </br> | Géré par indique comment l’appareil est géré. Vous pouvez filtrer par :</br>- Microsoft Defender pour point de terminaison </br> - Gestion des périphériques mobiles (MDM) </br>- Inconnu : cela peut être dû à l’exécution d’une version Windows obsolète, de SCCM en place ou d’un autre système de gestion des données de gestion des données tiers.</br></br> (_Ordinateurs et appareils mobiles uniquement_)
**Type d’appareil** </br> | Filtrez selon le type d’appareil que vous souhaitez examiner.</br></br> (_Appareils IoT uniquement_)

## <a name="use-columns-to-customize-the-device-inventory-views"></a>Utiliser des colonnes pour personnaliser les affichages d’inventaire des appareils

Vous pouvez ajouter ou supprimer des colonnes de l’affichage et trier les entrées en cliquant sur un en-tête de colonne disponible.

Sous **l’onglet Ordinateur et mobiles** , sélectionnez **Personnaliser les colonnes** pour voir les colonnes disponibles. Les valeurs par défaut sont vérifiées dans l’image ci-dessous :

![Image des ordinateurs et des mobiles](images/computerandmobilescolumns.png)

Sous **l’onglet Périphériques réseau** , **sélectionnez Personnaliser les colonnes** pour voir les colonnes disponibles. Les valeurs par défaut sont vérifiées dans l’image ci-dessous :

![Image des colonnes de périphérique réseau](images/networkdevicescolumns.png)

Sous **l’onglet Appareils IoT** , sélectionnez **Personnaliser les colonnes** pour voir les colonnes disponibles. Les valeurs par défaut sont vérifiées dans l’image ci-dessous :

![Image des colonnes d’appareil IoT](images/iotdevicescolumns.png)

## <a name="related-articles"></a>Articles connexes

[Examiner les appareils de la liste Microsoft Defender pour point de terminaison périphériques](investigate-machines.md)
