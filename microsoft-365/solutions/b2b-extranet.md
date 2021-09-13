---
title: Créer un extranet B2B avec des invités gérés
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- SPO_Content
- M365-collaboration
- m365solution-3tiersprotection
- m365solution-securecollab
- m365initiative-externalcollab
ms.custom: ''
localization_priority: Normal
f1.keywords: NOCSH
recommendations: false
description: Découvrez comment créer un site extranet B2B ou une équipe avec des invités gérés d’une organisation partenaire.
ms.openlocfilehash: 7e3ddf12473095b0a7ac91ded01256e77c299ddf
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59177323"
---
# <a name="create-a-b2b-extranet-with-managed-guests"></a>Créer un extranet B2B avec des invités gérés

Vous pouvez utiliser [Azure Active Directory gestion des](/azure/active-directory/governance/entitlement-management-overview) droits d’accès pour créer un extranet B2B afin de collaborer avec une organisation partenaire qui utilise Azure Active Directory. Cela permet aux utilisateurs de s’inscrire eux-mêmes sur le site ou l’équipe extranet et de recevoir un accès via un flux de travail d’approbation.

Grâce à cette méthode de partage de ressources pour la collaboration, l’organisation partenaire peut aider à maintenir et approuver les invités de leur côté, réduisant ainsi la charge qui pèse sur votre service informatique et permettant aux personnes les plus familiarisatrices avec le contrat de collaboration de gérer l’accès des utilisateurs.

Cet article décrit les étapes de création d’un package de ressources (dans ce cas, un site ou une équipe) que vous pouvez partager avec une organisation partenaire via un modèle d’inscription d’accès en libre-service. 

Avant de commencer, créez le site ou l’équipe que vous souhaitez partager avec l’organisation partenaire et activez-le pour le partage d’invités. Pour [plus d’informations, voir](collaborate-in-site.md) Collaborer avec des invités dans un site ou collaborer avec des invités d’une équipe. [](collaborate-as-team.md) Nous vous recommandons [](create-secure-guest-sharing-environment.md) également de consulter Créer un environnement de partage d’invités sécurisé pour obtenir des informations sur les fonctionnalités de sécurité et de conformité que vous pouvez utiliser pour maintenir vos stratégies de gouvernance lors de la collaboration avec des invités.

## <a name="license-requirements"></a>Critères de licence

L’utilisation de cette fonctionnalité nécessite Azure AD Premium P2 licence. 

Les clouds spécialisés, tels qu’Azure Germany et Azure China 21Vianet, ne sont actuellement pas disponibles.

## <a name="video-demonstration"></a>Démonstration vidéo

Cette vidéo illustre les procédures couvertes dans cet article.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4wKUj?autoplay=false]

## <a name="connect-the-partner-organization"></a>Connecter’organisation partenaire

Pour inviter des invités d’une organisation partenaire, vous devez ajouter le domaine du partenaire en tant qu’organisation connectée dans Azure Active Directory.

Pour ajouter une organisation connectée
1. Dans [Azure Active Directory,](https://aad.portal.azure.com)cliquez **sur Gouvernance des identités.**
2. Cliquez **sur Organisations connectées.**
4. Cliquez **sur Ajouter une organisation connectée.**
5. Tapez un nom et une description pour l’organisation, puis cliquez sur **Suivant : Répertoire + domaine.**
6. Cliquez **sur Ajouter un répertoire + domaine.**
7. Tapez le domaine de l’organisation à connecter, puis cliquez sur **Ajouter.**
8. Cliquez **Connecter,** puis cliquez sur **Suivant : Sponsors**.
9. Ajoutez des personnes de votre organisation ou de l’organisation à qui vous voulez approuver l’accès pour les invités.
10. Cliquez sur **Suivant : Révision + Créer**.
11. Examinez les paramètres que vous avez choisis, puis cliquez sur **Créer.**

    ![Capture d’écran de la page des organisations connectées dans Azure Active Directory.](../media/identity-governance-connected-organizations.png)

## <a name="choose-the-resources-to-share"></a>Choisir les ressources à partager

La première étape de la sélection des ressources à partager avec une organisation partenaire consiste à créer un catalogue pour les contenir.

Pour créer un catalogue
1. Dans [Azure Active Directory,](https://aad.portal.azure.com)cliquez **sur Gouvernance des identités.**
2. Cliquez **sur Catalogues.**
3. Cliquez **sur Nouveau catalogue.**
4. Tapez un nom et une  description pour  le catalogue et assurez-vous que activés et activés pour les utilisateurs externes sont tous deux définies sur **Oui**.
5. Cliquez sur **Créer**.

   ![Capture d’écran de la page catalogues dans Azure Active Directory gouvernance des identités.](../media/identity-governance-catalogs.png)

Une fois le catalogue créé, vous ajoutez le site SharePoint ou l’équipe que vous souhaitez partager avec l’organisation partenaire.

Pour ajouter des ressources à un catalogue
1. Dans Azure AD Identity Governance, cliquez sur **Catalogues,** puis cliquez sur le catalogue dans lequel vous souhaitez ajouter des ressources.
2. Cliquez **sur Ressources,** puis sur **Ajouter des ressources.**
3. Sélectionnez les équipes SharePoint sites que vous souhaitez inclure dans votre extranet, puis cliquez sur **Ajouter**.

   ![Capture d’écran de la page ressources du catalogue dans Azure Active Directory gouvernance des identités.](../media/identity-governance-catalog-resource.png)

Une fois que vous avez défini les ressources que vous souhaitez partager, l’étape suivante consiste à créer un package d’accès, qui définit le type d’accès accordé aux utilisateurs partenaires et le processus d’approbation pour les nouveaux utilisateurs partenaires demandant l’accès.

Pour créer un package d’accès
1. Dans La gouvernance des identités Azure AD, cliquez sur **Catalogues,** puis cliquez sur le catalogue dans lequel vous souhaitez créer un package d’accès.
2. Cliquez **sur Packages Access,** puis sur **Nouveau package d’accès.**
3. Tapez un nom et une description pour le package d’accès, puis cliquez sur **Suivant : Rôles de ressource.**
4. Choisissez les ressources du catalogue que vous souhaitez utiliser pour votre extranet.
5. Pour chaque ressource, dans la colonne **Rôle,** choisissez le rôle d’utilisateur que vous souhaitez accorder aux invités qui utilisent l’extranet.
6. Cliquez **sur Suivant : Demandes**.
7. Under **Users who can request access**, choose For users not in your **directory**.
8. Assurez-vous que **l’option Organisations connectées** spécifiques est sélectionnée, puis cliquez sur **Ajouter des répertoires.**
9. Choisissez l’organisation connectée que vous ajoutez précédemment, puis cliquez sur **Sélectionner**
10. Sous **Approbation,** **sélectionnez Oui** pour **Exiger l’approbation.**
11. Sous **Premier approuveur,** choisissez l’un des sponsors que vous avez ajoutés précédemment ou choisissez un utilisateur spécifique.
12. Cliquez **sur Ajouter un secours** et sélectionnez un approuveur de secours.
13. Under **Enable**, choose **Yes**.
14. Cliquez **sur Suivant : Cycle de vie**.
15. Choisissez les paramètres d’expiration et de révision d’accès que vous souhaitez utiliser, puis cliquez sur **Suivant : Révision + Créer.**
16. Examinez vos paramètres, puis cliquez sur **Créer.**

    ![Capture d’écran de l’écran packages d’accès Azure Active Directory gouvernance des identités.](../media/identity-governance-access-packages.png)

Si vous êtes partenaire d’une grande organisation, vous pouvez masquer le package d’accès. Si le package est masqué, les utilisateurs de l’organisation partenaire ne voient pas le package sur leur *portail My Access.* Au lieu de cela, un lien direct doit leur être envoyé pour s’inscrire au package. Le masquage du package d’accès peut réduire le nombre de demandes d’accès inappropriés et peut également aider à maintenir les packages d’accès disponibles organisés dans le portail de l’organisation partenaire.

Pour définir un package d’accès sur masqué
1. Dans Azure AD Identity Governance, cliquez **sur Packages Access,** puis cliquez sur votre package d’accès.
2. Dans la page **Vue d’ensemble,** cliquez sur **Modifier.**
3. Sous **Propriétés,** **sélectionnez Oui** pour **Masqué,** puis cliquez sur **Enregistrer.**

   ![Capture d’écran d’un écran modifier les propriétés du package d’accès.](../media/identity-governance-access-package-hidden.png)

## <a name="invite-partner-users"></a>Inviter des utilisateurs partenaires

Si vous définissez le package d’accès sur masqué, vous devez envoyer un lien direct à l’organisation partenaire afin qu’elle puisse demander l’accès à votre site ou à votre équipe.

Pour trouver le lien du portail d’accès
1. Dans Azure AD Identity Governance, cliquez **sur Packages Access,** puis cliquez sur votre package d’accès.
2. Dans la page **Vue d’ensemble,** cliquez **sur Copier dans le Presse-papiers** pour le lien **portail Mon accès.**

   ![Capture d’écran des propriétés du package d’accès avec lien du portail d’accès.](../media/identity-governance-access-portal-link.png)

Une fois que vous avez copié le lien, vous pouvez le partager avec votre contact au niveau de l’organisation partenaire et l’envoyer aux utilisateurs de son équipe de collaboration.

## <a name="see-also"></a>Voir aussi

[Créer un environnement de partage sécurisé avec des invités](create-secure-guest-sharing-environment.md)