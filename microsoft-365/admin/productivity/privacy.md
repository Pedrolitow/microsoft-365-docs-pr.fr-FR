---
title: Score de productivité Microsoft - Confidentialité
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
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
description: Protection de la confidentialité par le score de productivité.
ms.openlocfilehash: 5b5997532ddcd1fdf43b4124f8e2d8183bb3d89e
ms.sourcegitcommit: 53acc851abf68e2272e75df0856c0e16b0c7e48d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2021
ms.locfileid: "51579169"
---
# <a name="privacy-controls-for-productivity-score"></a>Contrôles de confidentialité pour le score de productivité

Le Score de productivité fournit des informations sur la transformation numérique de votre organisation tout au long de son utilisation des Microsoft 365 et des expériences technologiques qui la supportent.  Le score de votre organisation reflète les mesures de l’expérience des personnes et des technologies et peut être comparé aux critères d’organisations similaires aux vôtres. Pour plus d’informations, consultez la vue [d’ensemble du score de productivité.](productivity-score.md)

Votre confidentialité est importante pour Microsoft. Pour découvrir comment nous protégeons votre confidentialité, consultez [la déclaration de confidentialité de Microsoft.](https://privacy.microsoft.com/privacystatement) Le Score de productivité vous permet, en tant qu’administrateur informatique de votre organisation, d’accéder aux paramètres de confidentialité pour vous aider à vous assurer que les informations du Score de productivité que vous visualisez sont actionnables, sans compromettre la confiance que votre organisation place dans Microsoft.

Dans le domaine des expériences des personnes, les mesures sont disponibles au niveau de l’organisation uniquement. Ce domaine examine la façon dont les utilisateurs Microsoft 365 en regardant les catégories de collaboration de contenu, de mobilité, de réunions, de travail d’équipe et de communication. Nous vous permettons d’avoir plusieurs niveaux de contrôles pour vous aider à répondre à vos besoins en matière de politique de confidentialité interne.
Les contrôles vous donnent :

- Rôles d’administrateur flexibles pour contrôler qui peut voir les informations dans le Score de productivité.
- Possibilité de refuser le domaine d’expériences des personnes.

## <a name="flexible-admin-roles-to-control-who-can-see-the-information-in-productivity-score"></a>Rôles d’administrateur flexibles pour contrôler qui peut voir les informations dans le Score de productivité

Pour afficher l’intégralité du score de productivité, vous devez être l’un des rôles d’administrateur suivants :

- Administrateur général
- Administrateurs Exchange
- Administrateur SharePoint
- Administrateur Skype Entreprise
- Administrateur Teams
- Lecteur général
- Lecteur de rapports
- Lecteur Rapports de synthèse de l’utilisation

Attribuez le rôle Lecteur de rapports ou Rapport de synthèse de l’utilisation à toute personne responsable de la gestion et de l’adoption des changements, mais pas nécessairement un administrateur informatique. Ce rôle leur donne accès à l’expérience de score de productivité complète dans le Centre d Microsoft 365'administration.

Le rôle lecteur rapports de synthèse de l’utilisation devra être attribué par le biais des cmdlets PowerShell jusqu’à ce qu’il soit affecté à partir du Centre d’administration Microsoft 365 plus tard en 2020.

Pour attribuer le rôle lecteur rapports de synthèse de l’utilisation avec PowerShell :

- Exécutez le PowerShell suivant :

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

Vous pouvez également refuser le domaine expériences des personnes du Score de productivité. Si vous le désistez, personne de votre organisation ne pourra afficher ces mesures et votre organisation sera supprimée des calculs qui impliquent la communication, les réunions, le travail d’équipe, la collaboration de contenu et la mobilité. Vous devez être un administrateur global pour refuser les rapports d’expériences des personnes à votre organisation.

Pour refuser :

1. Dans le Centre d’administration, Paramètres    >   **Org Paramètres**  >  **Productivity Score**.
2. Désochez la case qui indique autoriser **Microsoft 365'utilisation à utiliser pour** les informations sur les expériences utilisateur. Pour comprendre comment modifier les paramètres de partage de données pour Endpoint Analytics dans le Gestionnaire de configuration Intune, sélectionnez **En savoir plus.**
3. Sélectionnez **Enregistrer.**

:::image type="content" source="../../media/orgsettingspageoptout.png" alt-text="Page des paramètres de l’organisation dans laquelle vous pouvez refuser les expériences de personnes.":::
