---
title: Examiner un compte d’utilisateur dans Microsoft Defender pour point de terminaison
description: Examinez un compte d’utilisateur pour connaître les informations d’identification potentiellement compromises ou pivotez sur le compte d’utilisateur associé au cours d’une enquête.
keywords: examiner, compte, utilisateur, entité utilisateur, alerte, Microsoft Defender pour point de terminaison
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.date: 04/24/2018
ms.subservice: mde
ms.openlocfilehash: 61cdee1f64e81b7874c1ad564e7d9eb01d04557d
ms.sourcegitcommit: 228fa13973bf7c2d91504703fab757f552ae40dd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2022
ms.locfileid: "67520948"
---
# <a name="investigate-a-user-account-in-microsoft-defender-for-endpoint"></a>Examiner un compte d’utilisateur dans Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigatgeuser-abovefoldlink)

## <a name="investigate-user-account-entities"></a>Examiner les entités de compte d’utilisateur

Identifiez les comptes d’utilisateur avec les alertes les plus actives (affichées sur le tableau de bord comme « Utilisateurs à risque ») et examinez les cas d’informations d’identification potentiellement compromises, ou pivotez sur le compte d’utilisateur associé lors de l’examen d’une alerte ou d’un appareil pour identifier les déplacements latéral possibles entre les appareils avec ce compte d’utilisateur.

Vous trouverez des informations sur le compte d’utilisateur dans les affichages suivants :

- Tableau de bord
- File d’attente d’alertes
- Page détails de l’appareil

Un lien de compte d’utilisateur cliquable est disponible dans ces affichages, qui vous amène à la page de détails du compte d’utilisateur où plus de détails sur le compte d’utilisateur sont affichés.

Lorsque vous examinez une entité de compte d’utilisateur, vous voyez :

- Détails du compte d’utilisateur, alertes Microsoft Defender pour Identity et connexion aux appareils, rôle, type d’ouverture de session et autres détails
- Vue d’ensemble des incidents et des appareils de l’utilisateur
- Alertes liées à cet utilisateur
- Observé dans l’organisation (appareils connectés à)

:::image type="content" source="images/atp-user-details-view.png" alt-text="Page de détails de l’entité de compte d’utilisateur" lightbox="images/atp-user-details-view.png":::

### <a name="user-details"></a>Détails de l’utilisateur

Le volet **Détails de** l’utilisateur à gauche fournit des informations sur l’utilisateur, telles que les incidents ouverts connexes, les alertes actives, le nom SAM, le SID, les alertes Microsoft Defender pour Identity, le nombre d’appareils sur lesquels l’utilisateur est connecté, le moment où l’utilisateur a été vu pour la première fois, le rôle et les types d’ouverture de session. Selon les fonctionnalités d’intégration que vous avez activées, vous verrez d’autres détails. Par exemple, si vous activez l’intégration de Skype Entreprise, vous pouvez contacter l’utilisateur à partir du portail. La section **Alertes Azure ATP** contient un lien vous permettant d’accéder à la page Microsoft Defender pour Identity, si vous avez activé la fonctionnalité Microsoft Defender pour Identity et qu’il existe des alertes liées à l’utilisateur. La page Microsoft Defender pour Identity fournit plus d’informations sur les alertes.

> [!NOTE]
> Vous devez activer l’intégration sur Microsoft Defender pour Identity et Defender pour point de terminaison pour utiliser cette fonctionnalité. Dans Defender pour point de terminaison, vous pouvez activer cette fonctionnalité dans les fonctionnalités avancées. Pour plus d’informations sur l’activation des fonctionnalités avancées, consultez [Activer les fonctionnalités avancées](advanced-features.md).

La vue d’ensemble, les alertes et les observations dans l’organisation sont des onglets différents qui affichent différents attributs sur le compte d’utilisateur.


>[!NOTE]
>Pour les appareils Linux, les informations sur les utilisateurs connectés ne sont pas affichées.


### <a name="overview"></a>Vue d’ensemble

L’onglet **Vue d’ensemble** affiche les détails des incidents et une liste des appareils auxquels l’utilisateur s’est connecté. Vous pouvez les développer pour afficher les détails des événements d’ouverture de session pour chaque appareil.

### <a name="alerts"></a>Alertes

L’onglet **Alertes** fournit la liste des alertes associées au compte d’utilisateur. Cette liste est une vue filtrée de la [file d’attente d’alertes](alerts-queue.md) et affiche les alertes où le contexte utilisateur est le compte d’utilisateur sélectionné, la date à laquelle la dernière activité a été détectée, une brève description de l’alerte, l’appareil associé à l’alerte, la gravité de l’alerte, l’état de l’alerte dans la file d’attente et qui est affecté à l’alerte.

### <a name="observed-in-organization"></a>Observé dans l’organisation

L’onglet **Observé dans l’organisation** vous permet de spécifier une plage de dates pour afficher la liste des appareils sur lesquels cet utilisateur a été observé connecté, le compte d’utilisateur connecté le plus fréquent et le moins fréquent pour chacun de ces appareils et le nombre total d’utilisateurs observés sur chaque appareil.

La sélection d’un élément dans la table Observée dans l’organisation étend l’élément, en révélant plus de détails sur l’appareil. La sélection directe d’un lien dans un élément vous envoie à la page correspondante.

## <a name="search-for-specific-user-accounts"></a>Rechercher des comptes d’utilisateur spécifiques

1. Sélectionnez **Utilisateur** dans le menu déroulant de la **barre de recherche** .
2. Entrez le compte d’utilisateur dans le champ **De recherche** .
3. Cliquez sur l’icône de recherche ou **appuyez sur Entrée**.

Une liste d’utilisateurs correspondant au texte de la requête s’affiche. Vous verrez le domaine et le nom du compte d’utilisateur, lorsque le compte d’utilisateur a été vu pour la dernière fois, et le nombre total d’appareils sur lesquels il a été observé connecté au cours des 30 derniers jours.

Vous pouvez filtrer les résultats selon les périodes suivantes :

- 1 jour
- 3 jours
- 7 jours
- 30 jours
- 6 mois

## <a name="related-topics"></a>Voir aussi

- [Afficher et organiser la file d’attente d’alertes Microsoft Defender pour point de terminaison](alerts-queue.md)
- [Gérer les alertes Microsoft Defender pour point de terminaison](manage-alerts.md)
- [Examiner les alertes Microsoft Defender pour point de terminaison](investigate-alerts.md)
- [Examiner un fichier associé à une alerte Defender pour point de terminaison](investigate-files.md)
- [Examiner les appareils dans la liste Des appareils Defender pour point de terminaison](investigate-machines.md)
- [Examiner une adresse IP associée à une alerte Defender pour point de terminaison](investigate-ip.md)
- [Examiner un domaine associé à une alerte Defender pour point de terminaison](investigate-domain.md)
