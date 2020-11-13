---
title: Limiter l’exposition accidentelle
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
localization_priority: Priority
f1.keywords: NOCSH
description: Découvrez comment limiter l’exposition accidentelle des informations lorsque vous partagez des fichiers avec des personnes extérieures à votre organisation.
ms.openlocfilehash: 430c00d46fa3801d0869b05a651fadd3bf5dea28
ms.sourcegitcommit: 8a726ed7ec19a8728c079780fa4d343a5f759fbb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2020
ms.locfileid: "49029968"
---
# <a name="limit-accidental-exposure-to-files-when-sharing-with-people-outside-your-organization"></a>Limiter l’exposition accidentelle de fichiers lors de partages avec des personnes extérieures à votre organisation

Lorsque vous partagez des fichiers et des dossiers avec des personnes extérieures à votre organisation, plusieurs options permettent de réduire les risques de partager accidentellement des informations sensibles. Vous pouvez choisir l’une des options de cet article pour répondre au mieux aux besoins de votre organisation.

## <a name="use-best-practices-for-anyone-links"></a>Utiliser les pratiques recommandées pour les liens Tout le monde

Si des membres de votre organisation doivent effectuer un partage non authentifié, mais que vous êtes préoccupé par le fait que des personnes non authentifiées modifient du contenu, lisez les [meilleures pratiques relatives au partage anonyme](best-practices-anonymous-sharing.md) pour obtenir des instructions sur l’utilisation du partage non authentifié dans votre organisation.

## <a name="turn-off-anyone-links"></a>Désactiver les liens Tout le monde

Nous vous recommandons de laisser les liens *Tout le monde* activés pour le contenu approprié parce qu’il s’agit de la manière la plus simple de partager des documents et de réduire le risque que des utilisateurs recherchent d’autres solutions en dehors du contrôle de votre service informatique. Les liens *Tout le monde* peuvent être transférés à d’autres personnes mais l’accès aux fichiers est disponible uniquement pour les personnes qui dispose du lien.

Si vous voulez toujours que les personnes extérieures à votre organisation s’authentifient lors de l’accès au contenu dans SharePoint, les groupes ou Teams, vous pouvez désactiver le partage *Tout le monde*. Cela permet d’éviter que les utilisateurs ne partagent le même contenu.

Si vous désactivez les liens *Tout le monde* , les utilisateurs peuvent tout de même partager facilement du contenu avec des invités à l’aide de liens *Personnes spécifiques*. Dans ce cas, toutes les personnes extérieures à votre organisation devront s’authentifier avant de pouvoir accéder au contenu partagé.

Selon vos besoins, vous pouvez désactiver les liens *Tout le monde* vers des sites spécifiques ou pour l’ensemble de votre organisation.

Pour désactiver les liens *Tout le monde* de votre organisation
1. Dans le centre d’administration SharePoint, dans le volet de gauche, cliquez sur **Partage**.
2. Définissez les paramètres de partage externe de SharePoint sur **Invités nouveaux et existants**.

   ![Capture d’écran des paramètres de partage externe de site SharePoint au niveau de l’organisation](../media/sharepoint-organization-external-sharing-controls-new-users.png)

3. Cliquez sur **Enregistrer**.

Pour désactiver les liens *Tout le monde* d’un site
1. Dans le centre d’administration SharePoint, dans le volet de navigation de gauche, développez **Sites** et cliquez sur **Sites actifs**.
2. Sélectionnez sur le site à configurer.
3. Dans le ruban, cliquez sur **Partage**. 
4. Assurez-vous que le partage est paramétré sur **Invités nouveaux et existants**.

   ![Capture d’écran des paramètres de partage externe de site SharePoint au niveau de l’organisation](../media/sharepoint-site-external-sharing-settings.png)

5. Si vous avez effectué des modifications, cliquez sur **Enregistrer**.

## <a name="domain-filtering"></a>Filtrage de domaines

Vous pouvez utiliser des listes d’autorisation ou de refus de domaine pour spécifier les domaines que vos utilisateurs peuvent utiliser lors d’un partage avec des personnes extérieures à votre organisation.

Avec une liste d’autorisation, vous pouvez spécifier une liste de domaines sur lesquels les utilisateurs de votre organisation peuvent partager avec des personnes extérieures à votre organisation. Le partage sur d’autres domaines est bloqué. Si votre organisation collabore avec des personnes uniquement à partir d’une liste de domaines spécifiques, vous pouvez utiliser cette fonctionnalité pour empêcher le partage avec d’autres domaines.

Avec une liste d’exclusion, vous pouvez spécifier une liste de domaines à partir desquels les utilisateurs de votre organisation ne peuvent pas partager avec des personnes extérieures à votre organisation. Le partage avec ces domaines listés est bloqué. Cela peut s’avérer utile si vous avez des concurrents, par exemple, à qui vous souhaitez empêcher d’accéder à du contenu au sein de votre organisation.

Les listes d’autorisation et de refus n’affectent que le partage avec des invités. Les utilisateurs peuvent toujours partager du contenu avec des personnes de domaines interdits en utilisant les liens *Tout le monde* si vous ne les avez pas désactivés. Pour des résultats optimaux avec les listes d’autorisation et de refus de domaine, prévoyez de désactiver les liens *Tout le monde* , comme décrit ci-dessus.

Pour configurer une liste d’autorisation ou de refus de domaine
1. Dans le centre d’administration SharePoint, dans le volet de gauche, cliquez sur **Partage**.
2. Sous **Paramètres avancés pour le partage externe** , cochez la case **Limiter le partage externe par domaine**.
3. Cliquez sur **Ajouter des domaines**.
4. Choisissez si vous voulez bloquer des domaines, indiquez les domaines, puis cliquez sur **OK**.

   ![Capture d’écran du paramètre Limiter le partage externe de SharePoint](../media/sharepoint-sharing-block-domain.png)

5. Cliquez sur **Enregistrer**.

Si vous voulez limiter le partage par domaine à un niveau plus élevé que SharePoint et OneDrive, vous pouvez [autoriser ou bloquer les invitations à des utilisateurs B2B d’organisations spécifiques](https://docs.microsoft.com/azure/active-directory/b2b/allow-deny-list) dans Azure Active Directory. (Vous devez configurer [l’intégration de SharePoint et OneDrive avec Azure AD B2B (préversion)](https://docs.microsoft.com/sharepoint/sharepoint-azureb2b-integration-preview) pour que ces paramètres affectent SharePoint et OneDrive.)

## <a name="limit-sharing-of-files-folders-and-sites-with-people-outside-your-organization-to-specified-security-groups"></a>Limiter le partage de fichiers, de dossiers et de sites avec des personnes extérieures à votre organisation à des groupes de sécurité spécifiés

Vous pouvez limiter le partage de fichiers, de dossiers et de sites avec des personnes extérieures à votre organisation à des membres d’un groupe de sécurité spécifique. Cette fonction est utile si vous voulez activer le partage externe, mais avec un flux de travail d’approbation ou un processus de demande. Vous pouvez également demander à vos utilisateurs de suivre une formation avant d’être ajoutés au groupe de sécurité et d’être autorisés à partager en externe.

Limiter le partage externe aux membres d’un groupe de sécurité
1. Dans le [Centre d’administration SharePoint](https://admin.microsoft.com/sharepoint), dans le volet de gauche, sous **Stratégies** , cliquez sur **Partage**.
2. Sous **Partage externe** , développez **Autres paramètres de partage externe**.

3. Sélectionnez **Autoriser uniquement les utilisateurs de groupes de sécurité spécifiques à partager en externe** , puis sélectionnez **Gérer les groupes de sécurité**.

    ![Capture d’écran du volet Gérer les groupes de sécurité](https://docs.microsoft.com/sharepoint/sharepointonline/media/manage-security-groups.png)

4. Dans la zone **Ajouter un groupe de sécurité** , entrez un nom pour un groupe de sécurité. La boîte de dialogue du groupe de sécurité s’affiche.

5. En regard du nom du groupe de sécurité, dans le menu déroulant **Peut partager avec** , sélectionnez l’une des options suivantes :

    - **Invités authentifiés uniquement** (par défaut)
    - **Tout le monde**

6. Sélectionnez **Enregistrer**.

Notez que cela affecte les fichiers, dossiers et sites, mais pas les groupes Microsoft 365 ou Teams. Lorsque les membres acceptent des invités dans un groupe Microsoft 365 privé ou une équipe privée dans Microsoft Teams, l’invitation est envoyée au groupe ou au propriétaire de l’équipe pour approbation.

## <a name="see-also"></a>Voir aussi

[Créer un environnement de partage sécurisé avec des invités](create-secure-guest-sharing-environment.md)

[Meilleures pratiques relatives au partage de fichiers et de dossiers avec des utilisateurs anonymes](best-practices-anonymous-sharing.md)
