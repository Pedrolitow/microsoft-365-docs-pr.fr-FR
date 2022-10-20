---
title: Utilisez Azure Privileged Identity Management (PIM) dans Microsoft Defender pour Office 365 l’accès administrateur aux outils de cybersécurité.
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 09/03/2021
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: high
search.appverid:
- MET150
ms.assetid: 56fee1c7-dc37-470e-9b09-33fff6d94617
ms.collection:
- m365-security
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
description: Apprenez à intégrer PIM afin d’accorder un accès limité dans le temps et juste-à-temps aux utilisateurs pour effectuer des tâches de privilège élevé dans Microsoft Defender pour Office 365, réduisant ainsi les risques pour vos données.
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: da1e105a218fe7885daf8e6e6059a5436695189e
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68633105"
---
<!--A-->
# <a name="privileged-identity-management-pim-and-why-to-use-it-with-microsoft-defender-for-office-365"></a>Privileged Identity Management (PIM) et pourquoi l’utiliser avec Microsoft Defender pour Office 365

La gestion des identités privilégiées (PIM) est une fonctionnalité d'Azure qui, une fois configurée, permet aux utilisateurs d'accéder à des données pendant une période limitée (parfois appelée période limitée dans le temps) afin de pouvoir effectuer une tâche spécifique. Cet accès est donné « juste-à-temps » pour l’action requise, puis révoqué. PIM limite l’accès et le temps dont dispose l’utilisateur aux données sensibles, ce qui réduit les risques d’exposition par rapport aux comptes d’administration privilégiés qui ont un accès à long terme aux données et à d’autres paramètres. Comment utiliser cette fonctionnalité (PIM) conjointement avec Microsoft Defender pour Office 365?

> [!TIP]
> L’accès PIM est limité au niveau du rôle et de l’identité et permet la réalisation de plusieurs tâches. Il ne faut pas le confondre avec Privileged Access Management (PAM) qui est limité au niveau de la tâche.

## <a name="steps-to-use-pim-to-grant-just-in-time-access-to-defender-for-office-365-related-tasks"></a>Étapes d’utilisation de PIM pour accorder un accès juste-à-temps à Defender pour Office 365 tâches associées

By setting up PIM to work with Defender for Office 365, admins create a process for a user to request access to take the actions they need. The user must *justify* the need for the elevation of their privileges.

Dans cet exemple, nous allons configurer « Alex », un membre de notre équipe de sécurité qui n’aura aucun accès permanent au à Office 365, mais qui peut accéder à la fois à un rôle requis pour les opérations quotidiennes normales, telles que la [recherche de menaces](threat-hunting-in-threat-explorer.md), puis à un niveau de privilège supérieur lorsque des opérations moins fréquentes mais sensibles, telles que la [correction des messages électroniques malveillants remis](remediate-malicious-email-delivered-office-365.md), sont requises.

> [!NOTE]
> Nous allons vous expliquer les étapes nécessaires pour configurer le MIP pour un analyste de la sécurité qui a besoin de la capacité de purger les e-mails à l'aide de Threat Explorer dans Microsoft Defender pour Office 365, mais les mêmes étapes peuvent être utilisées pour d'autres rôles RBAC dans le portail de sécurité et de conformité. Par exemple, ce processus pourrait être utilisé pour un travailleur de l'information qui a besoin d'un accès quotidien à l'eDiscovery pour effectuer des recherches et travailler sur des dossiers, mais qui n'a besoin qu'occasionnellement du droit élevé d'exporter des données du locataire.

***Step 1***. In the Azure PIM console for your subscription, add the user (Alex) to the Azure Security Reader role and configure the security settings related to activation.

1. Connectez-vous [au Centre d’administration Azure AD](https://aad.portal.azure.com/) et **sélectionnez Azure Active Directory**  >  **rôles et administrateurs.**
2. Sélectionnez **lecteur sécurité dans** la liste des rôles, puis **Paramètres**  >  **Modifier**
3. Définissez la « **Durée maximale de l’activation (heures)** »sur un jour normal de travail et « Sur l’activation » pour exiger **Azure MFA**.
4. Comme il s’agit du niveau de privilège normal d’Alex pour les opérations quotidiennes, nous décochons Exiger une justification lors de **l’activation**> mise à **jour .**
5. Sélectionnez **Ajouter des devoirs**  >  **Aucun membre sélectionné** > sélectionnez ou tapez le nom pour rechercher le membre correct.
6. Cliquez sur le bouton **Sélectionnez** pour choisir le membre que vous devez ajouter pour les privilèges PIM > cliquez sur **Suivant** > n’apportez aucune modification sur la page Ajouter une affectation (le type d’affectation *Éligible* et la durée *Éligible définitivement* sont les valeurs par défaut ) et **Affecter**.

Le nom de votre utilisateur (ici 'Alex') apparaîtra sous Affectations admissibles sur la page suivante, ce qui signifie qu'il est en mesure de PIM dans le rôle avec les paramètres configurés précédemment.

> [!NOTE]
> Pour obtenir un aperçu rapide de Privileged Identity Management voir [cette vidéo.](https://www.youtube.com/watch?v=VQMAg0sa_lE)

:::image type="content" source="../../media/pim-mdo-role-setting-details-for-security-reader-show-8-hr-duration.png" alt-text="Les détails du paramètre de rôle : Page Lecteur sécurité" lightbox="../../media/pim-mdo-role-setting-details-for-security-reader-show-8-hr-duration.png":::

***Step 2***. Create the required second (elevated) permission group for additional tasks and assign eligibility.

À l’aide de [groupes d’accès privilégié](/azure/active-directory/privileged-identity-management/groups-features), nous pouvons maintenant créer nos propres groupes personnalisés et combiner des autorisations ou augmenter la granularité si nécessaire pour répondre aux besoins et pratiques de votre organisation.

### <a name="create-a-role-group-requiring-the-permissions-we-need"></a>Créez un groupe de rôles nécessitant les autorisations dont nous avons besoin.

Dans le portail Microsoft 365 Defender, créez un groupe de rôles personnalisé qui contient les autorisations souhaitées.

1. Dans le portail Microsoft 365 Defender à <https://security.microsoft.com>, accédez à **Autorisations et rôles**, puis sélectionnez **Rôles** sous **E-mail et collaboration**. Pour aller directement à la page **Autorisations,** utilisez <https://security.microsoft.com/emailandcollabpermissions> .
2. Dans la page **Autorisations,** cliquez sur ![Icône Créer.](../../media/m365-cc-sc-create-icon.png) **Création**.
3. Nommez votre groupe pour refléter son objectif tel que « Search and Purge PIM ».
4. N’ajoutez pas de membres, enregistrez simplement le groupe et passe à la partie suivante!

### <a name="create-the-security-group-in-azure-ad-for-elevated-permissions"></a>Créer le groupe de sécurité dans Azure AD pour les autorisations élevées

1. Revenir au [Centre d’administration Azure AD](https://aad.portal.azure.com/) et accédez à **Groupe Azure AD**  >  **Nouveau**  >  **groupe.**
2. Nommez votre groupe Azure AD pour refléter son objectif, **aucun propriétaire ou membre n’est requis** pour le moment.
3. Tourner **les rôles Azure AD peuvent être assignés au groupe** à **Oui**.
4. N’ajoutez pas de rôles, de membres ou de propriétaires, créez le groupe.
5. Revenir au groupe que vous viennent de créer, puis sélectionnez **Accès privilégié**  >  **Activer l’accès privilégié**.
6. Dans le groupe, sélectionnez **Affectations éligibles** > **Ajouter des affectations** > Ajouter l’utilisateur qui a besoin de Rechercher et purger en tant que rôle de **Membre**.
7. Configurez le **Paramètres** dans le volet Accès privilégié du groupe. Choisissez de **modifier** les paramètres pour le rôle de **membre.**
8. Modifiez le temps d’activation en fonction de votre organisation. Dans cet exemple, vous avez *besoin d’Azure MFA,* *de justification* et d’informations sur les *tickets* avant de sélectionner Mettre **à jour.**

### <a name="nest-the-newly-created-security-group-into-the-role-group"></a>Imbriquer le groupe de sécurité nouvellement créé dans le groupe de rôles

1. [Connectez-vous à Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell) et exécutez la commande suivante :

   ```powershell
   Add-RoleGroupMember "<<Role Group Name>>" -Member "<<Azure Security Group>>"`
   ```

## <a name="test-your-configuration-of-pim-with-defender-for-office-365"></a>Testez votre configuration de PIM avec Defender pour Office 365

1. Connectez-vous à l’utilisateur de test (Alex), qui ne doit pas avoir d’accès administratif dans le portail [Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center) à ce stade.
2. Accédez à PIM, où l’utilisateur peut activer son rôle de lecteur de sécurité quotidien.
3. Si vous essayez de purger un e-mail à l’aide de l’Explorateur de menaces, vous obtenez une erreur indiquant que vous avez besoin d’autorisations supplémentaires.
4. PIM une deuxième fois dans le rôle plus élevé, après un court délai, vous devriez maintenant être en mesure de purger les e-mails sans problème.

   :::image type="content" source="../../media/pim-mdo-add-the-search-and-purge-role-assignment-to-this-pim-role.PNG" alt-text="Le volet Actions sous l’onglet Courrier électronique" lightbox="../../media/pim-mdo-add-the-search-and-purge-role-assignment-to-this-pim-role.PNG":::

L’attribution permanente de rôles d’administration et d’autorisations telles que le rôle de recherche et de vidage ne s’applique pas à l’initiative de sécurité de Confiance Zéro, mais comme vous pouvez le voir, PIM peut être utilisé pour accorder un accès juste-à-temps à l’ensemble d’outils requis.

*Nous remercions l’ingénieur client Ben Harris pour l’accès au billet de blog et aux ressources utilisées pour ce contenu.*

<!--A-->
