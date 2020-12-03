---
title: Score de productivité Microsoft-confidentialité
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
monikerRange: o365-worldwide
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
search.appverid:
- MET150
- MOE150
description: La protection de la confidentialité avec le score de productivité.
ms.openlocfilehash: db123042761b07ed64dd2dd94e783d65205e1460
ms.sourcegitcommit: 4debeb8f0fce67f361676340fc390f1b283a3069
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2020
ms.locfileid: "49561509"
---
# <a name="privacy-controls-for-productivity-score"></a>Contrôles de confidentialité du score de productivité

Le score de productivité fournit des informations sur la transformation numérique de votre organisation, grâce à son utilisation de Microsoft 365 et aux technologies qui la prennent en charge.  Le score de votre organisation reflète les évaluations des personnes et de la technologie et peut être comparé aux tests d’évaluation provenant d’organisations semblables aux vôtres. Pour plus d’informations, consultez la [rubrique vue d’ensemble du score de productivité](productivity-score.md).

Votre confidentialité est importante pour Microsoft. Pour savoir comment nous protégeons votre confidentialité, consultez la [déclaration de confidentialité de Microsoft](https://privacy.microsoft.com/privacystatement). Le score de productivité vous permet, en tant qu’administrateur informatique de votre organisation, d’accéder aux paramètres de confidentialité afin de vous assurer que les informations de score de productivité que vous visualisez sont exploitables, tout en ne compromettant pas l’approbation de votre organisation dans Microsoft.

Dans la zone personnes expériences, les mesures sont disponibles au niveau de l’organisation uniquement. Cette zone examine la façon dont les utilisateurs utilisent Microsoft 365 en examinant les catégories de la collaboration de contenu, la mobilité, les réunions, le travail d’équipe et la communication. Nous vous offrons plusieurs niveaux de contrôles pour vous aider à répondre à vos besoins en matière de stratégie de confidentialité interne.
Les contrôles vous donnent les éléments suivants :

- Des rôles d’administrateur flexibles permettant de contrôler qui peut voir les informations dans le score de productivité.
- Possibilité de désactivation de la zone de personnes.

## <a name="flexible-admin-roles-to-control-who-can-see-the-information-in-productivity-score"></a>Rôles d’administrateur flexibles permettant de contrôler qui peut voir les informations dans le score de productivité

Pour afficher l’intégralité de la note de productivité, vous avez besoin de l’un des rôles d’administrateur suivants :

- Administrateur global
- Administrateurs Exchange
- Administrateur SharePoint
- Administrateur pour Skype Entreprise
- Administrateur Teams
- Lecteur général
- Lecteur de rapports
- Lecteur de rapports de synthèse d’utilisation

Affectez le lecteur rapports ou le rôle de lecteur rapports de synthèse de l’utilisation à toute personne responsable de la gestion et de l’adoption des modifications, mais pas nécessairement d’un administrateur informatique. Ce rôle leur donne accès à l’expérience complète des scores de productivité dans le centre d’administration 365 de Microsoft.

Le rôle de lecteur de rapports de synthèse d’utilisation doit être attribué via les cmdlets PowerShell jusqu’à ce qu’il devienne accessible à partir du centre d’administration Microsoft 365 plus loin dans 2020.

Pour attribuer le rôle de lecteur rapports de synthèse d’utilisation avec PowerShell :

- Exécutez l’PowerShell suivant :

```powershell
Connect-AzureAD
Enable-AzureADDirectoryRole -RoleTemplateId '75934031-6c7e-415a-99d7-48dbd49e875e'
$role=Get-AzureADDirectoryRole -Filter "roleTemplateId eq '75934031-6c7e-415a-99d7-48dbd49e875e'"
Get-AzureADDirectoryRoleMember -ObjectId $role.ObjectId
$u=Get-AzureADUser -ObjectId <user upn>
Add-AzureADDirectoryRoleMember -ObjectId $role.ObjectId -RefObjectId $u.ObjectId
```

</br>


## <a name="capability-to-opt-out-of-people-experiences"></a>Possibilité de désactiver les expériences de personnes

Vous pouvez également désactiver la zone des utilisateurs du score de productivité. Si vous désactivez l’option, personne de votre organisation ne pourra afficher ces mesures, et votre organisation sera supprimée des calculs impliquant la communication, les réunions, le travail d’équipe, la collaboration de contenu et la mobilité.

Pour choisir une option, procédez comme suit :

1. Dans le centre d’administration, accédez à **Settings** paramètres d'   >   **organisation** paramètres, puis, sous l’onglet **services** , sélectionnez **rapports**.
2. Désactivez la case à cocher  **autoriser l’utilisation des données d’utilisation de Microsoft 365 pour les personnes qui utilisent des idées**. Pour savoir comment modifier les paramètres de partage de données pour l’analyse des points de terminaison dans le gestionnaire de configuration Intune, sélectionnez **en savoir plus**.
3. Sélectionnez  **Enregistrer**.

:::image type="content" source="../../media/orgsettingspageoptout.png" alt-text="Page Paramètres de l’organisation dans laquelle vous pouvez désactiver les expériences de personnes.":::