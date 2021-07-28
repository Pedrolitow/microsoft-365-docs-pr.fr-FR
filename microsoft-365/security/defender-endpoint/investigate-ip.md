---
title: Examiner une adresse IP associée à une alerte
description: Utilisez les options d’examen pour examiner les communications possibles entre les appareils et les adresses IP externes.
keywords: examiner, examen, adresse IP, alerte, Microsoft Defender pour point de terminaison, ADRESSE IP externe
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: article
ms.date: 04/24/2018
ms.technology: mde
ms.openlocfilehash: 9d204c7ad9aaecd077f2bce462d650a4cfdbf06e
ms.sourcegitcommit: 3576c2fee77962b516236cb67dd3df847d61c527
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2021
ms.locfileid: "53619542"
---
# <a name="investigate-an-ip-address-associated-with-a-microsoft-defender-for-endpoint-alert"></a>Examiner une adresse IP associée à une alerte Microsoft Defender pour le point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-investigateip-abovefoldlink)

Examinez les communications possibles entre vos appareils et les adresses IP externes.

L’identification de tous les appareils de l’organisation ayant communiqué avec une adresse IP malveillante suspectée ou connue, telle que les serveurs de commande et de contrôle (C2), permet de déterminer l’étendue potentielle de la violation, des fichiers associés et des appareils infectés.

Vous trouverez des informations dans les sections suivantes dans l’affichage d’adresse IP :

- IP dans le monde entier
- Noms DNS inversés
- Alertes associées à cette adresse IP
- IP dans l’organisation
- Prévalence

## <a name="ip-worldwide-and-reverse-dns-names"></a>Noms DNS IP dans le monde entier et inverses

La section Détails de l’adresse IP affiche les attributs de l’adresse IP, tels que son ASN et ses noms DNS inverses.

## <a name="alerts-related-to-this-ip"></a>Alertes associées à cette adresse IP

Les **alertes associées à cette** section IP fournissent une liste d’alertes associées à l’adresse IP.

## <a name="ip-in-organization"></a>IP dans l’organisation

La section **IP de l’organisation** fournit des détails sur la prévalence de l’adresse IP dans l’organisation.

## <a name="prevalence"></a>Prévalence

La section **Prévalence** affiche le nombre d’appareils connectés à cette adresse IP et le moment où l’adresse IP a été vue pour la première et la dernière fois. Vous pouvez filtrer les résultats de cette section par période . la période par défaut est de 30 jours.

## <a name="most-recent-observed-devices-with-ip"></a>Appareils les plus récemment observés avec ip

La section **Appareils les plus récemment observés** avec ip fournit une vue chronologique des événements et des alertes associées observés sur l’adresse IP.

**Examinez une adresse IP externe :**

1. Sélectionnez **l’adresse IP** dans **le** menu déroulant de la barre de recherche.
2. Entrez l’adresse IP dans le **champ** Recherche.
3. Cliquez sur l’icône de recherche ou appuyez sur **Entrée.**

Des détails sur l’adresse IP sont affichés, notamment : les détails d’inscription (le cas contraire), les adresses IP inversées (par exemple, les domaines), la prévalence des appareils de l’organisation qui ont communiqué avec cette adresse IP (pendant la période sélectionnable) et les périphériques de l’organisation qui ont été observés pour communiquer avec cette adresse IP.

> [!NOTE]
> Les résultats de la recherche seront renvoyés uniquement pour les adresses IP observées lors de la communication avec les appareils de l’organisation.

Utilisez les filtres de recherche pour définir les critères de recherche. Vous pouvez également utiliser la zone de recherche de chronologie pour filtrer les résultats affichés de tous les appareils de l’organisation observés en communication avec l’adresse IP, le fichier associé à la communication et la dernière date observée.

En cliquant sur l’un des noms d’appareils, vous pouvez continuer à examiner les alertes, comportements et événements signalés.

## <a name="related-topics"></a>Voir aussi

- [Afficher et organiser la file d’attente d’alertes Microsoft Defender pour point de terminaison](alerts-queue.md)
- [Gérer les alertes microsoft Defender pour les points de terminaison](manage-alerts.md)
- [Examiner microsoft Defender pour les alertes de point de terminaison](investigate-alerts.md)
- [Examiner un fichier associé à une alerte Microsoft Defender pour le point de terminaison](investigate-files.md)
- [Examiner les appareils de la liste Microsoft Defender pour les appareils de point de terminaison](investigate-machines.md)
- [Examiner un domaine associé à une alerte Microsoft Defender pour le point de terminaison](investigate-domain.md)
- [Examiner un compte d’utilisateur dans Microsoft Defender pour le point de terminaison](investigate-user.md)
