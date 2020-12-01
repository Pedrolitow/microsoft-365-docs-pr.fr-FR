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
ms.openlocfilehash: c88886e9d1470bda48d023b77472e7dd296508a0
ms.sourcegitcommit: d3ca8021f7da00a474ac14aac5f1358204a848f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "49519352"
---
# <a name="privacy-controls-for-productivity-score"></a>Contrôles de confidentialité du score de productivité

Le score de productivité aide les organisations à transformer le travail obtenu avec des mesures qui vous aident à évaluer et à améliorer les expériences de personnes et de technologies. Elle vous permet d’obtenir une visibilité sur le fonctionnement de votre organisation et fournit des mesures qui vous permettent de vous concentrer sur l’amélioration des expériences.  Vous pouvez également connecter les mesures aux actions pour vous aider à mettre à jour les compétences et les systèmes afin que tout le monde puisse le faire. Le score reflète les performances de votre organisation et vous permet de comparer en toute sécurité votre score avec d’autres organisations comme les vôtres.  Pour plus d’informations, consultez [la rubrique vue d’ensemble des scores de productivité](productivity-score.md).

Votre confidentialité est importante pour nous. Pour savoir comment nous protégeons votre confidentialité, consultez la [déclaration de confidentialité de Microsoft](https://privacy.microsoft.com/privacystatement). Le score de productivité fournit des informations essentielles sur la façon dont les employés de votre organisation travaillent avec des contrôles pour s’assurer que les informations sont exploitables tout en ne compromettant pas l’approbation que vous avez effectuée dans Microsoft.

Dans la zone personnes expériences, les mesures sont disponibles au niveau de l’organisation et incluent tous les utilisateurs de votre client Microsoft 365. Cette zone examine la façon dont les utilisateurs utilisent Microsoft 365 en examinant les catégories de la collaboration de contenu, la mobilité, les réunions, le travail d’équipe et la communication. Pour vous aider à favoriser la formation et la sensibilisation à l’ensemble des personnes qui peuvent avoir besoin d’un support technique avec nos produits, nous vous avons également fourni des informations sur le niveau individuel. Bien que nous fournissons ce niveau de transparence, nous vous proposons également plusieurs niveaux de contrôles pour vous aider à répondre aux besoins de votre politique de confidentialité interne.
Les contrôles suivants vous permettent de :

- Des rôles d’administrateur flexibles permettant de contrôler qui peut voir les informations dans le score de productivité.
- La possibilité d’identifier les mesures au niveau de l’utilisateur.
- Possibilité de désactiver les expériences de personnes.
- Possibilité de désactiver la zone personnes

## <a name="flexible-admin-roles-to-control-who-can-see-the-information-in-productivity-score"></a>Rôles d’administrateur flexibles permettant de contrôler qui peut voir les informations dans le score de productivité

Pour afficher l’intégralité du score de productivité, y compris les mesures au niveau du client et les détails par utilisateur, votre rôle doit être l’un des rôles d’administrateur suivants :

- Administrateur général
- Administrateurs Exchange
- Administrateur SharePoint
- Administrateur pour Skype Entreprise
- Administrateur Teams
- Lecteur général
- Lecteur de rapports

Attribuez le rôle de lecteur de rapports à toute personne responsable de la gestion et de l’adoption des modifications. Ce rôle leur donne accès à l’expérience complète, y compris les mesures au niveau du client et les détails au niveau de chaque utilisateur.

Le rapport des expériences des personnes contient les détails de l’activité par utilisateur pour chaque page de détails de catégorie. Attribuez un rôle personnalisé appelé lecteur de rapports de synthèse d’utilisation (disponible à partir du 29 octobre 2020) pour permettre l’accès uniquement aux métriques agrégées des expériences de personnes. Ce rôle devra être attribué via les cmdlets PowerShell jusqu’à ce qu’il devienne accessible à partir du centre d’administration Microsoft plus tard au cours de l’année.

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

:::image type="content" source="../../media/communicationspage.jpg" alt-text="Page communications dans les rapports de productivité.":::

## <a name="de-identification-of-user-level-metrics"></a>Désidentification des mesures au niveau de l’utilisateur

Pour que les données collectées pour tous les rapports soient anonymes, vous devez être administrateur général. Cette action masque les informations identifiables telles que les noms d’utilisateur, de groupe et de site dans tous les rapports, y compris le score de productivité et l’utilisation de Microsoft 365.

1. Dans le centre d’administration, accédez à **Settings** paramètres d'   >   **organisation** paramètres, puis, sous l’onglet **services** , choisissez **rapports**.
2. Sélectionnez  **rapports**, puis choisissez d'  **afficher les identificateurs anonymes pour les noms d’utilisateur, de groupe et de site dans score de productivité et rapports d’utilisation**. Ce paramètre est appliqué à la fois aux rapports d’utilisation et à l’application de modèle.
3. Sélectionnez  **enregistrer les modifications**.

:::image type="content" source="../../media/orgsettings_anonymous.jpg" alt-text="Rendez les informations utilisateur anonymes pour les rapports.":::

## <a name="capability-to-opt-out-of-people-experiences"></a>Possibilité de désactiver les expériences de personnes

Lorsque le score de productivité est généralement disponible, vous pouvez également désactiver la zone des utilisateurs du score de productivité. Si vous désactivez, personne de l’organisation ne pourra afficher ces mesures et votre organisation est supprimée des calculs qui impliquent la communication, les réunions, le travail d’équipe, la collaboration de contenu et la mobilité.

1. Dans le centre d’administration, accédez à **Settings** paramètres d'   >   **organisation** paramètres, puis, sous l’onglet **services** , choisissez **rapports**.
2. Sélectionnez  **rapports**, puis désactivez la case à cocher  **autoriser les données d’utilisation de Microsoft 365 à être utilisées pour les utilisateurs**. Pour comprendre comment modifier les paramètres de partage de données pour l’analyse des points de terminaison dans le gestionnaire de configuration Intune, cliquez sur **en savoir plus**.
3. Sélectionnez  **enregistrer les modifications**.

:::image type="content" source="../../media/orgsettingspageoptout.jpg" alt-text="Page Paramètres de l’organisation dans laquelle vous pouvez désactiver les expériences de personnes.":::