---
title: Score de productivité Microsoft et insights sur la confidentialité
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
monikerRange: o365-worldwide
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom: AdminSurgePortfolio
search.appverid:
- MET150
- MOE150
description: Protection de la confidentialité avec le score de productivité.
ms.openlocfilehash: 823e2cc087d3f0e9c486d8c0c4eca92ba42aee21
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/18/2022
ms.locfileid: "65467929"
---
# <a name="privacy-controls-for-productivity-score"></a>Contrôles de confidentialité pour le score de productivité

Le score de productivité fournit des insights sur le parcours de transformation numérique de votre organisation par le biais de son utilisation de Microsoft 365 et des expériences technologiques qui le prennent en charge.  Le score de votre organisation reflète les mesures des personnes et de l’expérience technologique et peut être comparé aux points de référence d’organisations similaires à la vôtre. Pour plus d’informations, consultez la [vue d’ensemble du score de productivité](productivity-score.md).

Votre confidentialité est importante pour Microsoft. Pour savoir comment protéger votre confidentialité, consultez la [déclaration de confidentialité de Microsoft](https://privacy.microsoft.com/privacystatement). Le score de productivité vous donne, en tant qu’administrateur informatique de votre organisation, accès aux paramètres de confidentialité pour vous assurer que toutes les informations de score de productivité que vous affichez sont exploitables, tout en ne compromettant pas la confiance que votre organisation place dans Microsoft.

Dans le domaine des expériences des personnes, les métriques sont disponibles uniquement au niveau de l’organisation. Ce domaine examine la façon dont les utilisateurs utilisent Microsoft 365 en examinant les catégories de collaboration de contenu, de mobilité, de réunions, de travail d’équipe et de communication. Nous vous proposons plusieurs niveaux de contrôle pour vous aider à répondre à vos besoins en matière de politique de confidentialité interne.
Les contrôles vous donnent :

- Rôles d’administrateur flexibles pour contrôler qui peut voir les informations dans le score de productivité.
- Possibilité de refuser le domaine des expériences de personnes.

## <a name="flexible-admin-roles-to-control-who-can-see-the-information-in-productivity-score"></a>Rôles d’administrateur flexibles pour contrôler qui peut voir les informations dans le score de productivité

Pour afficher l’intégralité du score de productivité, vous devez être l’un des rôles d’administrateur suivants :

- Administrateur général
- Administrateurs Exchange
- Administrateur SharePoint
- Administrateur Skype Entreprise
- Administrateur Teams
- Lecteur général
- Lecteur de rapports
- Lecteur Rapports de synthèse de l’utilisation

Attribuez le rôle Lecteur de rapports ou Lecteur de rapports de synthèse d’utilisation à toute personne responsable de la gestion et de l’adoption des modifications, mais pas nécessairement un administrateur informatique. Ce rôle leur donne accès à l’expérience de score de productivité complète dans le Centre d’administration Microsoft 365.

Le rôle Lecteur de rapports récapitulatifs d’utilisation doit être attribué via des applets de commande PowerShell jusqu’à ce qu’il devienne assignable à partir du Centre d'administration Microsoft 365 plus tard en 2020.

Pour attribuer le rôle Lecteur des rapports de synthèse d’utilisation avec PowerShell :

- Exécutez la commande PowerShell suivante :

```powershell
Connect-AzureAD
Enable-AzureADDirectoryRole -RoleTemplateId '75934031-6c7e-415a-99d7-48dbd49e875e'
$role=Get-AzureADDirectoryRole -Filter "roleTemplateId eq '75934031-6c7e-415a-99d7-48dbd49e875e'"
Get-AzureADDirectoryRoleMember -ObjectId $role.ObjectId
$u=Get-AzureADUser -ObjectId <user upn>
Add-AzureADDirectoryRoleMember -ObjectId $role.ObjectId -RefObjectId $u.ObjectId
```

</br>


## <a name="capability-to-opt-out-of-people-experiences"></a>Possibilité de refuser les expériences de personnes

Vous pouvez également refuser le domaine des expériences de personnes du score de productivité. Si vous refusez, personne de votre organisation ne sera en mesure d’afficher ces métriques, et votre organisation sera supprimée des calculs qui impliquent la communication, les réunions, le travail d’équipe, la collaboration de contenu et la mobilité. Vous devez être administrateur général pour refuser à votre organisation les rapports d’expériences de personnes.

Pour refuser :

1. Dans le centre d’administration, accédez à **Paramètres**  >   **Org Paramètres** >  **Productivity Score**.
2. Dés activez la case à cocher qui indique **autoriser l’utilisation des données d’utilisation Microsoft 365 pour les informations sur les expériences des utilisateurs**. Pour comprendre comment modifier les paramètres de partage de données pour Endpoint Analytics dans le gestionnaire de configuration Intune, **sélectionnez En savoir plus**.
3. Sélectionnez  **Enregistrer**.

:::image type="content" source="../../media/orgsettingspageoptout.png" alt-text="Page des paramètres de l’organisation dans laquelle vous pouvez refuser les expériences de personnes.":::
