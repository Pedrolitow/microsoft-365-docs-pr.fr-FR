---
title: Utilisez Azure Privileged Identity Management (PIM) dans Microsoft Defender pour Office 365 l’accès administrateur aux outils de cybersécurité.
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 09/03/2021
audience: ITPro
ms.topic: article
ms.localizationpriority: high
search.appverid:
- MET150
ms.assetid: 56fee1c7-dc37-470e-9b09-33fff6d94617
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
description: Apprenez à intégrer PIM afin d’accorder un accès limité dans le temps et juste-à-temps aux utilisateurs pour effectuer des tâches de privilège élevé dans Microsoft Defender pour Office 365, réduisant ainsi les risques pour vos données.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 9ea618a24c14aa49973ae05287a65cbb756f5467
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60196284"
---
<!--A-->
# <a name="privileged-identity-management-pim-and-why-to-use-it-with-microsoft-defender-for-office-365"></a>Privileged Identity Management (PIM) et pourquoi l’utiliser avec Microsoft Defender pour Office 365

La gestion des identités privilégiées (PIM) est une fonctionnalité d'Azure qui, une fois configurée, permet aux utilisateurs d'accéder à des données pendant une période limitée (parfois appelée période limitée dans le temps) afin de pouvoir effectuer une tâche spécifique. Cet accès est donné « juste-à-temps » pour l’action requise, puis révoqué. PIM limite l’accès et le temps dont dispose l’utilisateur aux données sensibles, ce qui réduit les risques d’exposition par rapport aux comptes d’administration privilégiés qui ont un accès à long terme aux données et à d’autres paramètres. Comment utiliser cette fonctionnalité (PIM) conjointement avec Microsoft Defender pour Office 365?

> [!TIP]
> L’accès PIM est limité au niveau du rôle et de l’identité et permet la réalisation de plusieurs tâches. Il ne faut pas le confondre avec Privileged Access Management (PAM) qui est limité au niveau de la tâche.

## <a name="steps-to-use-pim-to-grant-just-in-time-access-to-defender-for-office-365-related-tasks"></a>Étapes d’utilisation de PIM pour accorder un accès juste-à-temps à Defender pour Office 365 tâches associées

En configurant le PIM pour qu'il fonctionne avec Microsoft Defender pour Office 365, les administrateurs créent un processus permettant à un utilisateur de demander un accès pour prendre les mesures dont il a besoin. L'utilisateur doit *justifier* la nécessité de l'élévation de ses privilèges.

Dans cet exemple, nous allons configurer « Alex », un membre de notre équipe de sécurité qui n’aura aucun accès permanent au à Office 365, mais qui peut accéder à la fois à un rôle requis pour les opérations quotidiennes normales, telles que la [recherche de menaces](threat-hunting-in-threat-explorer.md), puis à un niveau de privilège supérieur lorsque des opérations moins fréquentes mais sensibles, telles que la [correction des messages électroniques malveillants remis](remediate-malicious-email-delivered-office-365.md), sont requises.

> [!NOTE]
> Nous allons vous expliquer les étapes nécessaires pour configurer le MIP pour un analyste de la sécurité qui a besoin de la capacité de purger les e-mails à l'aide de Threat Explorer dans Microsoft Defender pour Office 365, mais les mêmes étapes peuvent être utilisées pour d'autres rôles RBAC dans le portail de sécurité et de conformité. Par exemple, ce processus pourrait être utilisé pour un travailleur de l'information qui a besoin d'un accès quotidien à l'eDiscovery pour effectuer des recherches et travailler sur des dossiers, mais qui n'a besoin qu'occasionnellement du droit élevé d'exporter des données du locataire.

***Étape 1***. Dans la console Azure PIM de votre abonnement, ajoutez l’utilisateur (Alex) au rôle lecteur sécurité Azure et configurez les paramètres de sécurité liés à l’activation.

1. Connectez-vous [au Centre d’administration Azure AD](https://aad.portal.azure.com/) et **sélectionnez Azure Active Directory**  >  **rôles et administrateurs.**
2. Sélectionnez **lecteur sécurité dans** la liste des rôles, puis **Paramètres**  >  **Modifier**
3. Définissez la « **Durée maximale de l’activation (heures)** »sur un jour normal de travail et « Sur l’activation » pour exiger **Azure MFA**.
4. Comme il s’agit du niveau de privilège normal d’Alex pour les opérations quotidiennes, nous décochons Exiger une justification lors de **l’activation**> mise à **jour .**
5. Sélectionnez **Ajouter des devoirs**  >  **Aucun membre sélectionné** > sélectionnez ou tapez le nom pour rechercher le membre correct.
6. Cliquez **sur** le bouton Sélectionner pour choisir le membre que vous devez ajouter pour les privilèges PIM > cliquez sur  **Suivant** > ne modifiez pas la page Ajouter une affectation (les deux *types* d’affectation éligible et durée éligible par défaut seront les valeurs par défaut) et **Affecter**.

Le nom de votre utilisateur (ici 'Alex') apparaîtra sous Affectations admissibles sur la page suivante, ce qui signifie qu'il est en mesure de PIM dans le rôle avec les paramètres configurés précédemment.

> [!NOTE]
> Pour obtenir un aperçu rapide de Privileged Identity Management voir [cette vidéo.](https://www.youtube.com/watch?v=VQMAg0sa_lE)

:::image type="content" source="../../media/pim-mdo-role-setting-details-for-security-reader-show-8-hr-duration.png" alt-text="N’oubliez pas d’analyser les paramètres pour le rôle lecteur sécurité dans Privileged Access Management. Vous verrez ici que la durée maximale de l’activation PIM est de 8 heures.":::

***Étape 2***. Créez le deuxième groupe d’autorisations requis (élevé) pour les tâches supplémentaires et attribuez l’éligibilité.

À l’aide de [groupes d’accès privilégié](/azure/active-directory/privileged-identity-management/groups-features), nous pouvons maintenant créer nos propres groupes personnalisés et combiner des autorisations ou augmenter la granularité si nécessaire pour répondre aux besoins et pratiques de votre organisation.

### <a name="create-a-role-group-requiring-the-permissions-we-need"></a>Créez un groupe de rôles nécessitant les autorisations dont nous avons besoin.

Dans le portail de sécurité, créez un groupe de rôles personnalisé qui contient les autorisations que nous voulons.

1. Accédez au portail Microsoft 365 Defender ( https://security.microsoft.com)  >  **Autorisations & rôles** > sélectionner **des rôles** sous e-mail et collaboration > **créer**.
2. Nommez votre groupe pour refléter son objectif tel que « Search and Purge PIM ».
3. N’ajoutez pas de membres, enregistrez simplement le groupe et passe à la partie suivante!

### <a name="create-the-security-group-in-azure-ad-for-elevated-permissions"></a>Créer le groupe de sécurité dans Azure AD pour les autorisations élevées

1. Revenir au [Centre d’administration Azure AD](https://aad.portal.azure.com/) et accédez à **Groupe Azure AD**  >  **Nouveau**  >  **groupe.**
2. Nommez votre groupe AAD pour refléter son objectif, aucun propriétaire ou membre **n’est requis** pour le moment.
3. Tourner **les rôles Azure AD peuvent être assignés au groupe** à **Oui**.
4. N’ajoutez pas de rôles, de membres ou de propriétaires, créez le groupe.
5. Revenir au groupe que vous viennent de créer, puis sélectionnez **Accès privilégié**  >  **Activer l’accès privilégié**.
6. Dans le groupe, sélectionnez **Affectations éligibles** Ajouter des affectations > Ajouter l’utilisateur qui a besoin de la & purge en tant que rôle  >   de **membre.**
7. Configurez le **Paramètres** dans le volet Accès privilégié du groupe. Choisissez de **modifier** les paramètres pour le rôle de **membre.**
8. Modifiez le temps d’activation en fonction de votre organisation. Dans cet exemple, vous avez *besoin d’Azure MFA,* *de justification* et d’informations sur les *tickets* avant de sélectionner Mettre **à jour.**

### <a name="nest-the-newly-created-security-group-into-the-role-group"></a>Imbriquez le groupe de sécurité nouvellement créé dans le groupe de rôles.

1. [Connecter dans le Centre de sécurité & conformité PowerShell](/powershell/exchange/connect-to-scc-powershell) et exécutez ce qui suit :

    `Add-RoleGroupMember "<<Role Group Name>>" -Member "<<Azure Security Group>>"`

## <a name="test-your-configuration-of-pim-with-defender-for-office-365"></a>Testez votre configuration de PIM avec Defender pour Office 365

1. Connectez-vous à l’utilisateur de test (Alex), qui ne doit pas avoir d’accès administratif dans le portail [Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center) à ce stade.
2. Accédez à PIM, où l’utilisateur peut activer son rôle de lecteur de sécurité au quotidien.
3. Si vous essayez de purger un e-mail à l’aide de l’Explorateur de menaces, vous obtenez une erreur indiquant que vous avez besoin d’autorisations supplémentaires.
4. PIM une deuxième fois dans le rôle plus élevé, après un court délai, vous devriez maintenant être en mesure de purger les e-mails sans problème.

   :::image type="content" source="../../media/pim-mdo-add-the-search-and-purge-role-assignment-to-this-pim-role.PNG" alt-text="Si l’utilisateur que nous avons ajouté (Alex) via le rôle Security Reader PIM tente de supprimer un e-mail suspect, il reçoit un message lui disant « Vous avez besoin du rôle Recherche et purge pour agir sur ce courrier électronique. Contactez votre administrateur pour obtenir l’attribution de rôle ou ajoutez le courrier électronique à un incident.":::

L’attribution permanente de rôles d’administration et d’autorisations telles que le rôle de recherche et de vidage ne s’applique pas à l’initiative de sécurité de Confiance Zéro, mais comme vous pouvez le voir, PIM peut être utilisé pour accorder un accès juste-à-temps à l’ensemble d’outils requis.

*Nous remercions l’ingénieur client Ben Harris pour l’accès au billet de blog et aux ressources utilisées pour ce contenu.*

<!--A-->