---
title: Déployer des équipes pour trois niveaux de protection des fichiers
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/31/2019
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: 1e8e3cfd-b878-4088-b941-9940363a5fae
description: Créez et configurez des équipes avec Microsoft Teams pour différents niveaux de protection des informations pour les fichiers.
ms.openlocfilehash: 3b90a1b084f7cd7e56d1d6448d74a7d2c2469a4d
ms.sourcegitcommit: 5710ce729c55d95b8b452d99ffb7ea92b5cb254a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2019
ms.locfileid: "39971822"
---
# <a name="deploy-teams-for-three-tiers-of-protection-for-files"></a>Déployer des équipes pour trois niveaux de protection des fichiers

Suivez les étapes décrites dans cet article pour créer et déployer des équipes de référence, sensibles et hautement confidentiels. Pour plus d’informations sur ces trois niveaux de protection, consultez [Sécuriser des fichiers dans Microsoft Teams](secure-files-in-teams.md).

## <a name="baseline-teams"></a>Équipes de référence

La protection Base de référence inclut les équipes publiques et privées. Les équipes publiques peuvent être découvertes et sont accessibles par toute personne de l’organisation. Les sites privés peuvent être découverts et sont accessibles seulement par les membres du groupe Office 365 associé à l’équipe. Ces deux types d’équipes permettent aux membres de partager le site avec d’autres utilisateurs.

### <a name="public"></a>Public

Utilisez les instructions de [cet article](https://support.office.com/article/174adf5f-846b-4780-b765-de1a0a737e2b) pour créer une équipe de référence avec accès et autorisations publics.

Voici la configuration finale.

![Protection de niveau de référence pour une équipe publique.](../media/baseline-public-team.png)

### <a name="private"></a>Privé

Utilisez les instructions de [cet article](https://support.office.com/article/174adf5f-846b-4780-b765-de1a0a737e2b) pour créer une équipe de référence avec accès et autorisations privés.

Voici la configuration finale.

![Protection de niveau de référence pour une équipe privée.](../media/baseline-private-team.png)

## <a name="sensitive-teams"></a>Équipes sensibles

Pour une équipe sensible, vous commencez par [créer une équipe privée](https://support.office.com/article/174adf5f-846b-4780-b765-de1a0a737e2b).

Vous configurez ensuite le site SharePoint sous-jacent pour empêcher le partage par les membres de l'équipe.

1. Dans la barre d’outils de l’équipe, cliquez sur **Fichiers**.

2. Cliquez sur les points de suspension, puis sur **Ouvrir dans SharePoint**.

3. Dans la barre d’outils du site SharePoint sous-jacent, cliquez sur l’icône Paramètres, puis cliquez sur **Autorisations du site**.

4. Dans le volet **Autorisations de site**, sous **Paramètres de partage**, cliquez sur **Modifier les paramètres de partage**.

5. Sous **Autorisations de partage**, sélectionnez **Seuls les propriétaires du site peuvent partager des fichiers, des dossiers et le site**, puis cliquez sur **Enregistrer**.

Voici la configuration finale.

![Protection sensible pour les membres d’une équipe.](../media/sensitive-team.png)

## <a name="highly-confidential-teams"></a>Équipe hautement confidentielles

Avec une équipe hautement confidentielle, vous commencez par [créer une équipe privée](https://support.office.com/article/174adf5f-846b-4780-b765-de1a0a737e2b).

Vous configurez ensuite le site SharePoint sous-jacent pour empêcher le partage par les membres de l'équipe et la demande d’accès par des non-membre de l’équipe.

1. Dans la barre d’outils de l’équipe, cliquez sur **Fichiers**.

2. Cliquez sur les points de suspension, puis sur **Ouvrir dans SharePoint**.

3. Dans la barre d’outils du site SharePoint sous-jacent, cliquez sur l’icône Paramètres, puis cliquez sur **Autorisations du site**.

4. Dans le volet **Autorisations de site**, sous **Paramètres de partage**, cliquez sur **Modifier les paramètres de partage**.

5. Sous **Autorisations de partage**, sélectionnez **Seuls les propriétaires du site peuvent partager des fichiers, des dossiers et le site**.

6. Désactivez **Autoriser les demandes d’accès**, puis cliquez sur **Enregistrer**.

Voici la configuration finale.

![Protection hautement confidentielle pour les membres d’une équipe.](../media/highly-confidential-team.png)

## <a name="next-step"></a>Étape suivante

[Protéger des fichiers dans Teams avec des étiquettes de rétention et la protection contre la perte de données (DLP)](deploy-teams-retention-DLP.md)

## <a name="see-also"></a>Voir aussi

[Sécuriser des fichiers dans Microsoft Teams](secure-files-in-teams.md)

[Adoption du cloud et solutions hybrides](https://docs.microsoft.com/office365/enterprise/cloud-adoption-and-hybrid-solutions)
