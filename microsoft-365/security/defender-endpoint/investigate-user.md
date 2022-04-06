---
title: Examiner un compte d’utilisateur dans Microsoft Defender pour le point de terminaison
description: Examiner un compte d’utilisateur à la recherche d’informations d’identification potentiellement compromises ou pivoter sur le compte d’utilisateur associé au cours d’une enquête.
keywords: examiner, compte, utilisateur, entité utilisateur, alerte, Microsoft Defender pour le point de terminaison
ms.prod: m365-security
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
ms.technology: mde
ms.openlocfilehash: 76b0b7405c8dc1c434fbc9f991903b25d8b9d4f4
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64469336"
---
# <a name="investigate-a-user-account-in-microsoft-defender-for-endpoint"></a>Examiner un compte d’utilisateur dans Microsoft Defender pour le point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigatgeuser-abovefoldlink)

## <a name="investigate-user-account-entities"></a>Examiner les entités de compte d’utilisateur

Identifiez les comptes d’utilisateurs avec les alertes les plus actives (affichées sur le tableau de bord sous la forme « Utilisateurs à risque ») et examinez les cas d’informations d’identification potentiellement compromises, ou faites pivoter le compte d’utilisateur associé lors de l’examen d’une alerte ou d’un appareil afin d’identifier les éventuels mouvements latérals entre les appareils avec ce compte d’utilisateur.

Les informations de compte d’utilisateur sont disponibles dans les affichages suivants :

- Tableau de bord
- File d’attente des alertes
- Page Détails de l’appareil

Un lien de compte d’utilisateur cliquable est disponible dans ces affichages, qui vous permet d’obtenir la page de détails du compte d’utilisateur dans laquelle des détails plus détaillés sur le compte d’utilisateur sont affichés.

Lorsque vous examinez une entité de compte d’utilisateur, vous voyez :

- Détails du compte d’utilisateur, alertes Microsoft Defender pour l’identité et appareils connectés, rôle, type de session et autres détails
- Vue d’ensemble des incidents et des appareils de l’utilisateur
- Alertes associées à cet utilisateur
- Observé dans l’organisation (appareils connectés)

:::image type="content" source="images/atp-user-details-view.png" alt-text="Page des détails de l’entité du compte d’utilisateur" lightbox="images/atp-user-details-view.png":::

### <a name="user-details"></a>Détails de l’utilisateur

Le  volet d’informations Utilisateur de gauche fournit des informations sur l’utilisateur, telles que les incidents d’ouverture connexes, les alertes actives, le nom SAM, le SID, les alertes Microsoft Defender pour l’identité, le nombre d’appareils avec qui l’utilisateur est connecté, le moment où l’utilisateur a été vu pour la première fois, le rôle et les types d’ouverture de session. Selon les fonctionnalités d’intégration que vous avez activées, vous verrez d’autres détails. Par exemple, si vous activez l’Skype pour l’intégration d’entreprise, vous pourrez contacter l’utilisateur à partir du portail. La section **Alertes Azure ATP** contient un lien qui vous permet d’accès à la page Microsoft Defender pour l’identité, si vous avez activé la fonctionnalité Microsoft Defender pour l’identité et que des alertes sont associées à l’utilisateur. La page Microsoft Defender pour l’identité fournit plus d’informations sur les alertes.

> [!NOTE]
> Vous devez activer l’intégration sur Microsoft Defender pour l’identité et Defender pour le point de terminaison pour utiliser cette fonctionnalité. Dans Defender pour point de terminaison, vous pouvez activer cette fonctionnalité dans les fonctionnalités avancées. Pour plus d’informations sur l’activer, voir [Activer les fonctionnalités avancées](advanced-features.md).

La vue d’ensemble, les alertes et les observations dans l’organisation sont des onglets différents qui affichent différents attributs sur le compte d’utilisateur.


>[!NOTE]
>Pour les appareils Linux, les informations sur les utilisateurs connectés ne sont pas affichées.


### <a name="overview"></a>Présentation

**L’onglet** Vue d’ensemble affiche les détails des incidents et une liste des appareils sur qui l’utilisateur s’est connecté. Vous pouvez les développer pour voir les détails des événements de connexion pour chaque appareil.

### <a name="alerts"></a>Alertes

**L’onglet Alertes** fournit une liste des alertes associées au compte d’utilisateur. Cette liste est un affichage filtré de la [](alerts-queue.md)file d’attente des alertes et affiche les alertes où le contexte utilisateur est le compte d’utilisateur sélectionné, la date à laquelle la dernière activité a été détectée, une brève description de l’alerte, le périphérique associé à l’alerte, la gravité de l’alerte, l’état de l’alerte dans la file d’attente et l’utilisateur affecté à l’alerte.

### <a name="observed-in-organization"></a>Observé dans l’organisation

L’onglet Observé dans l’organisation vous permet de spécifier une plage de dates pour voir la liste des appareils sur lequel cet utilisateur a été connecté, le compte d’utilisateur connecté le plus fréquent et le moins fréquent pour chacun de ces appareils et le nombre total d’utilisateurs observés sur chaque appareil.

La sélection d’un élément dans le tableau Observé dans l’organisation développera l’élément, révélant plus de détails sur l’appareil. La sélection directe d’un lien au sein d’un élément vous enverra à la page correspondante.

## <a name="search-for-specific-user-accounts"></a>Rechercher des comptes d’utilisateurs spécifiques

1. **Sélectionnez Utilisateur** dans le menu déroulant **de la** barre de recherche.
2. Entrez le compte d’utilisateur dans le **champ** Recherche.
3. Cliquez sur l’icône de recherche ou appuyez sur **Entrée**.

Une liste d’utilisateurs correspondant au texte de la requête s’affiche. Vous verrez le domaine et le nom du compte d’utilisateur, la dernière fois que le compte d’utilisateur a été vu, ainsi que le nombre total d’appareils sur qui il a été connecté au cours des 30 derniers jours.

Vous pouvez filtrer les résultats selon les périodes suivantes :

- 1 jour
- 3 jours
- 7 jours
- 30 jours
- 6 mois

## <a name="related-topics"></a>Sujets associés

- [Afficher et organiser la file d’attente d’alertes Microsoft Defender pour point de terminaison](alerts-queue.md)
- [Gérer les alertes microsoft Defender pour les points de terminaison](manage-alerts.md)
- [Examiner microsoft Defender pour les alertes de point de terminaison](investigate-alerts.md)
- [Examiner un fichier associé à une alerte Defender for Endpoint](investigate-files.md)
- [Examiner les appareils dans la liste Defender pour les appareils de point de terminaison](investigate-machines.md)
- [Examiner une adresse IP associée à une alerte Defender for Endpoint](investigate-ip.md)
- [Examiner un domaine associé à une alerte Defender for Endpoint](investigate-domain.md)
