---
title: Examiner une adresse IP associée à une alerte
description: Utilisez les options d’investigation pour examiner les communications possibles entre les appareils et les adresses IP externes.
keywords: examiner, investigation, adresse IP, alerte, Microsoft Defender pour point de terminaison, adresse IP externe
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
ms.topic: article
ms.date: 04/24/2018
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 41557fc56e9ccbe64a05f3aad3d280ff544473c4
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68232295"
---
# <a name="investigate-an-ip-address-associated-with-a-microsoft-defender-for-endpoint-alert"></a>Examiner une adresse IP associée à une alerte Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Examinez les communications possibles entre vos appareils et les adresses IP externes.

L’identification de tous les appareils de l’organisation qui ont communiqué avec une adresse IP malveillante suspecte ou connue, telle que des serveurs C2 (Command and Control), permet de déterminer l’étendue potentielle de la violation, des fichiers associés et des appareils infectés.

Vous trouverez des informations dans les sections suivantes dans la vue d’adresse IP :

- IP dans le monde entier
- Noms DNS inversés
- Alertes liées à cette adresse IP
- ADRESSE IP dans l’organisation
- Prévalence

## <a name="ip-worldwide-and-reverse-dns-names"></a>Noms DNS ip dans le monde entier et inverse

La section Détails de l’adresse IP affiche les attributs de l’adresse IP, tels que son ASN et ses noms DNS inversés.

## <a name="alerts-related-to-this-ip"></a>Alertes liées à cette adresse IP

Les **alertes liées à cette section IP** fournissent une liste d’alertes associées à l’adresse IP.

## <a name="ip-in-organization"></a>ADRESSE IP dans l’organisation

La section **IP de l’organisation** fournit des détails sur la prévalence de l’adresse IP dans l’organisation.

## <a name="prevalence"></a>Prévalence

La section **Prévalence** affiche le nombre d’appareils connectés à cette adresse IP, ainsi que le moment où l’adresse IP a été vue pour la première et la dernière fois. Vous pouvez filtrer les résultats de cette section par période ; la période par défaut est de 30 jours.

## <a name="most-recent-observed-devices-with-ip"></a>Appareils observés les plus récents avec IP

Les **appareils observés les plus récents** avec la section IP fournissent une vue chronologique des événements et des alertes associées qui ont été observés sur l’adresse IP.

**Examinez une adresse IP externe :**

1. Sélectionnez **l’adresse IP** dans le menu déroulant de la **barre de recherche** .
2. Entrez l’adresse IP dans le champ **De recherche** .
3. Cliquez sur l’icône de recherche ou **appuyez sur Entrée**.

Des détails sur l’adresse IP sont affichés, notamment : les détails de l’inscription (le cas échéant), les adresses IP inversées (par exemple, les domaines), la prévalence des appareils de l’organisation qui ont communiqué avec cette adresse IP (pendant une période sélectionnable) et les appareils de l’organisation qui ont été observés communiquant avec cette adresse IP.

> [!NOTE]
> Les résultats de la recherche ne sont retournés que pour les adresses IP observées en communication avec les appareils de l’organisation.

Utilisez les filtres de recherche pour définir les critères de recherche. Vous pouvez également utiliser la zone de recherche de chronologie pour filtrer les résultats affichés de tous les appareils de l’organisation qui communiquent avec l’adresse IP, le fichier associé à la communication et la dernière date observée.

Si vous cliquez sur l’un des noms d’appareils, vous accédez à la vue de cet appareil, où vous pouvez continuer à examiner les alertes, les comportements et les événements signalés.

## <a name="related-topics"></a>Voir aussi

- [Afficher et organiser la file d’attente d’alertes Microsoft Defender pour point de terminaison](alerts-queue.md)
- [Gérer les alertes Microsoft Defender pour point de terminaison](manage-alerts.md)
- [Examiner les alertes Microsoft Defender pour point de terminaison](investigate-alerts.md)
- [Examiner un fichier associé à une alerte de Microsoft Defender pour point de terminaison](investigate-files.md)
- [Examiner les appareils dans la liste des appareils Microsoft Defender pour point de terminaison](investigate-machines.md)
- [Examiner un domaine associé à une alerte de Microsoft Defender pour point de terminaison](investigate-domain.md)
- [Examiner un compte d’utilisateur dans Microsoft Defender pour point de terminaison](investigate-user.md)
