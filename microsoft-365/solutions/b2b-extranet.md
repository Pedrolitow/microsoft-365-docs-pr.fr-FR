---
title: Créer un extranet B2B avec des invités gérés
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
ms.collection:
- SPO_Content
- M365-collaboration
- m365solution-3tiersprotection
- m365solution-securecollab
- m365initiative-externalcollab
ms.custom: ''
ms.localizationpriority: medium
f1.keywords: NOCSH
recommendations: false
description: Découvrez comment créer un site ou une équipe extranet B2B avec des invités gérés d’une organisation partenaire.
ms.openlocfilehash: 35410cc13b771a6f22d0e85d2f1592f1c7dbb048
ms.sourcegitcommit: d3ef9391f621e8f4ca70661184b3bb82c6cbda94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67579730"
---
# <a name="create-a-b2b-extranet-with-managed-guests"></a>Créer un extranet B2B avec des invités gérés

Vous pouvez utiliser [La gestion des droits d’utilisation Azure Active Directory](/azure/active-directory/governance/entitlement-management-overview) pour créer un extranet B2B afin de collaborer avec une organisation partenaire qui utilise Azure Active Directory. Cela permet aux utilisateurs de s’inscrire eux-mêmes dans le site ou l’équipe extranet et de recevoir l’accès via un flux de travail d’approbation.

Grâce à cette méthode de partage des ressources à des fins de collaboration, l’organisation partenaire peut aider à maintenir et approuver les invités de leur côté, ce qui réduit la charge sur votre service informatique et permet aux personnes les plus familières de l’accord de collaboration de gérer l’accès des utilisateurs.

Cet article décrit les étapes à suivre pour créer un package de ressources (dans ce cas, un site ou une équipe) que vous pouvez partager avec une organisation partenaire via un modèle d’inscription d’accès en libre-service. 

Avant de commencer, créez le site ou l’équipe que vous souhaitez partager avec l’organisation partenaire et activez-le pour le partage d’invités. Pour plus d’informations, consultez [Collaborer avec des invités d’un site](collaborate-in-site.md) ou [collaborer avec des invités d’une équipe](collaborate-as-team.md) . Nous vous recommandons également de consulter [Créer un environnement de partage d’invités sécurisé](create-secure-guest-sharing-environment.md) pour obtenir des informations sur les fonctionnalités de sécurité et de conformité que vous pouvez utiliser pour maintenir vos stratégies de gouvernance lors de la collaboration avec les invités.

## <a name="license-requirements"></a>Critères de licence

L’utilisation de cette fonctionnalité nécessite une licence Azure AD Premium P2. 

Les clouds spécialisés, tels qu’Azure Allemagne et Azure China 21Vianet, ne sont pas disponibles pour l’instant.

## <a name="video-demonstration"></a>Démonstration vidéo

Cette vidéo présente les procédures décrites dans cet article.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4wKUj?autoplay=false]

## <a name="connect-the-partner-organization"></a>Connecter l’organisation partenaire

Pour inviter des invités d’une organisation partenaire, vous devez ajouter le domaine du partenaire en tant qu’organisation connectée dans Azure Active Directory.

Pour ajouter une organisation connectée
1. Dans [Azure Active Directory](https://aad.portal.azure.com), cliquez sur **Gouvernance des identités**.
2. Cliquez sur **Organisations connectées**.
4. Cliquez sur **Ajouter une organisation connectée**.
5. Tapez un nom et une description pour l’organisation, puis cliquez sur **Suivant : Répertoire + domaine**.
6. Cliquez sur **Ajouter un répertoire + un domaine**.
7. Tapez le domaine de l’organisation que vous souhaitez connecter, puis cliquez sur **Ajouter**.
8. Cliquez sur **Connecter**, puis sur **Suivant : Sponsors**.
9. Ajoutez des personnes de votre organisation ou de l’organisation que vous connectez à qui vous souhaitez approuver l’accès pour les invités.
10. Cliquez sur **Suivant : Révision + Créer**.
11. Passez en revue les paramètres que vous avez choisis, puis cliquez sur **Créer**.

    ![Capture d’écran de la page Organisations connectées dans Azure Active Directory.](../media/identity-governance-connected-organizations.png)

## <a name="choose-the-resources-to-share"></a>Choisir les ressources à partager

La première étape de la sélection des ressources à partager avec une organisation partenaire consiste à créer un catalogue pour les contenir.

Pour créer un catalogue
1. Dans [Azure Active Directory](https://aad.portal.azure.com), cliquez sur **Gouvernance des identités**.
2. Cliquez sur **Catalogues**.
3. Cliquez sur **Nouveau catalogue**.
4. Tapez un nom et une description pour le catalogue et assurez-vous que **Activé** et **Activé pour les utilisateurs externes** sont tous les deux définis sur **Oui**.
5. Cliquez sur **Créer**.

   ![Capture d’écran de la page catalogues dans Azure Active Directory Identity Governance.](../media/identity-governance-catalogs.png)

Une fois le catalogue créé, vous ajoutez le site ou l’équipe SharePoint que vous souhaitez partager avec l’organisation partenaire.

Pour ajouter des ressources à un catalogue
1. Dans Azure AD Identity Governance, cliquez sur **Catalogues**, puis sur le catalogue dans lequel vous souhaitez ajouter des ressources.
2. Cliquez sur **Ressources** , puis sur **Ajouter des ressources**.
3. Sélectionnez les équipes ou les sites SharePoint que vous souhaitez inclure dans votre extranet, puis cliquez sur **Ajouter**.

   ![Capture d’écran de la page ressources du catalogue dans Azure Active Directory Identity Governance.](../media/identity-governance-catalog-resource.png)

Une fois que vous avez défini les ressources que vous souhaitez partager, l’étape suivante consiste à créer un package d’accès, qui définit le type d’accès accordé aux utilisateurs partenaires et le processus d’approbation pour les nouveaux utilisateurs partenaires qui demandent l’accès.

Pour créer un package d’accès
1. Dans Azure AD Identity Governance, cliquez sur **Catalogues**, puis sur le catalogue dans lequel vous souhaitez créer un package d’accès.
2. Cliquez sur **Packages Access**, puis sur **Nouveau package d’accès**.
3. Tapez un nom et une description pour le package d’accès, puis cliquez sur **Suivant : Rôles de ressources**.
4. Choisissez les ressources du catalogue que vous souhaitez utiliser pour votre extranet.
5. Pour chaque ressource, dans la colonne **Rôle** , choisissez le rôle d’utilisateur que vous souhaitez accorder aux invités qui utilisent l’extranet.
6. Cliquez sur **Suivant : Demandes**.
7. Sous **Utilisateurs qui peuvent demander l’accès**, choisissez **Pour les utilisateurs qui ne se trouvent pas dans votre répertoire**.
8. Vérifiez que l’option **Organisations connectées spécifiques** est sélectionnée, puis cliquez sur **Ajouter des répertoires**.
9. Choisissez l’organisation connectée que vous ajoutez précédemment, puis cliquez sur **Sélectionner**
10. Sous **Approbation**, choisissez **Oui** pour **Exiger l’approbation**.
11. Sous **Premier approbateur**, choisissez l’un des sponsors que vous avez ajoutés précédemment ou choisissez un utilisateur spécifique.
12. Cliquez sur **Ajouter une solution de secours** et sélectionnez un approbateur de secours.
13. Sous **Activer**, choisissez **Oui**.
14. Cliquez sur **Suivant : Cycle de vie**.
15. Choisissez les paramètres d’expiration et de révision d’accès que vous souhaitez utiliser, puis cliquez sur **Suivant : Vérifier + Créer**.
16. Passez en revue vos paramètres, puis cliquez sur **Créer**.

    ![Capture d’écran de l’écran des packages d’accès dans Azure Active Directory Identity Governance.](../media/identity-governance-access-packages.png)

Si vous collaborez avec une grande organisation, vous souhaiterez peut-être masquer le package d’accès. Si le package est masqué, les utilisateurs de l’organisation partenaire ne voient pas le package sur leur portail *Mon accès* . Au lieu de cela, un lien direct doit leur être envoyé pour s’inscrire au package. Le masquage du package d’accès peut réduire le nombre de demandes d’accès inappropriées et peut également aider à conserver les packages d’accès disponibles organisés dans le portail de l’organisation partenaire.

Pour définir un package d’accès sur masqué
1. Dans Azure AD Identity Governance, cliquez sur **Packages Access**, puis sur votre package d’accès.
2. Dans la page **Vue d’ensemble** , cliquez sur **Modifier**.
3. Sous **Propriétés**, choisissez **Oui** pour **Masqué**, puis cliquez sur **Enregistrer**.

   ![Capture d’écran d’un écran de modification des propriétés du package d’accès.](../media/identity-governance-access-package-hidden.png)

## <a name="invite-partner-users"></a>Inviter des utilisateurs partenaires

Si vous définissez le package d’accès sur masqué, vous devez envoyer un lien direct à l’organisation partenaire afin qu’elle puisse demander l’accès à votre site ou à votre équipe.

Pour trouver le lien du portail d’accès
1. Dans Azure AD Identity Governance, cliquez sur **Packages Access**, puis sur votre package d’accès.
2. Dans la page **Vue d’ensemble** , cliquez sur **Copier dans le presse-papiers** pour le **lien Du portail Mon accès**.

   ![Capture d’écran des propriétés du package d’accès avec le lien portail d’accès.](../media/identity-governance-access-portal-link.png)

Une fois que vous avez copié le lien, vous pouvez le partager avec votre contact auprès de l’organisation partenaire et l’envoyer aux utilisateurs de l’équipe de collaboration.

## <a name="see-also"></a>Voir aussi

[Créer un environnement de partage sécurisé avec des invités](create-secure-guest-sharing-environment.md)