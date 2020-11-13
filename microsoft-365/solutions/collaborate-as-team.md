---
title: Collaborer avec des invités au sein d’une équipe
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
ms.custom:
- seo-marvel-apr2020
localization_priority: Normal
f1.keywords: NOCSH
description: Découvrez les étapes de configuration de Microsoft 365 nécessaires pour configurer une équipe de collaboration pour les tâches, les conversations et la documentation avec des invités dans Teams.
ms.openlocfilehash: 7f00acb7b7b58169d6a66bfa4cabdc5a3035f67f
ms.sourcegitcommit: 8a726ed7ec19a8728c079780fa4d343a5f759fbb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2020
ms.locfileid: "49030028"
---
# <a name="collaborate-with-guests-in-a-team"></a>Collaborer avec des invités au sein d’une équipe

Si vous avez besoin de collaborer avec des invités dans des documents, des tâches et des conversations, nous vous recommandons d’utiliser Microsoft Teams. Teams fournit toutes les fonctionnalités de collaboration disponibles dans Office et SharePoint avec conversation permanente et un ensemble d’outils de collaboration personnalisable et extensible dans une expérience utilisateur unifiée.

Dans cet article, nous allons passer en revue les étapes de configuration de Microsoft 365 nécessaires pour configurer une équipe de collaboration avec des invités.

## <a name="video-demonstration"></a>Démonstration vidéo

Cette vidéo présente les étapes de configuration décrites dans ce document.</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE44NTr?autoplay=false]

## <a name="azure-organizational-relationships-settings"></a>Paramètres Azure de relations organisationnelles

Le partage dans Microsoft 365 est régi par les [paramètres de relations organisationnelles dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/external-identities/delegate-invitations). Si le partage d’invités est désactivé ou restreint dans Azure AD, ce paramètre remplace tous les paramètres de partage que vous configurez dans Microsoft 365.

Vérifiez les paramètres de relations organisationnelles pour vous assurer que le partage avec des invités n’est pas bloqué.

![Capture d’écran de la page des paramètres de relations organisationnelles d’Azure Active Directory](../media/azure-ad-organizational-relationships-settings.png)

Pour définir les paramètres de relation organisationnelle

1. Connectez-vous à Azure Active Directory à l’adresse [https://aad.portal.azure.com](https://aad.portal.azure.com) .
2. Dans le volet de navigation de gauche, cliquez sur **Azure Active Directory**.
3. Cliquez sur **identités externes**.
4. Sur l’écran de **prise en main** , dans le volet de navigation de gauche, cliquez sur **paramètres de collaboration externe**.
5. Assurez-vous que les **administrateurs et les utilisateurs du rôle d’invité invité peuvent inviter** et que les **membres peuvent inviter** sont tous deux la valeur **Oui**.
6. Si vous avez effectué des modifications, cliquez sur **Enregistrer**.

Notez les paramètres dans la section **restrictions de collaboration** . Assurez-vous que les domaines des invités avec lesquels vous souhaitez collaborer ne sont pas bloqués.

Si vous travaillez avec des invités de plusieurs organisations, vous souhaiterez peut-être limiter leur capacité à accéder aux données d’annuaire. Cela les empêchera de voir qui d’autre est un invité dans l’annuaire. Pour ce faire, sous **restrictions d’accès des utilisateurs invités** , sélectionnez **les utilisateurs invités ont un accès limité aux propriétés et l’appartenance aux paramètres d’objets d’annuaire** ou **l’accès des utilisateurs invités est limité aux propriétés et aux appartenances de leurs propres objets d’annuaire**.

## <a name="teams-guest-access-settings"></a>Paramètres d’accès invité de teams

Teams dispose d’un commutateur maître/inactif pour l’accès invité et de divers paramètres permettant de contrôler ce que les invités peuvent faire dans une équipe. Le commutateur maître, **autoriser l’accès invité dans teams** doit être **activé** pour que l’accès invité fonctionne dans Teams.

Vérifiez que l’accès invité est activé dans teams et effectuez les ajustements nécessaires aux paramètres invités en fonction des besoins de votre entreprise. N’oubliez pas que ces paramètres affectent toutes les équipes.

![Capture d’écran du commutateur Accès invité dans Teams](../media/teams-guest-access-toggle-on.png)

Pour déterminer les paramètres d’accès invité Teams, procédez comme suit :

1. Connectez-vous au Centre d’administration Microsoft 365 sur[https://admin.microsoft.com](https://admin.microsoft.com).
2. Dans le volet de navigation de gauche, cliquez sur **Afficher tout**.
3. Sous **Centres d’administration** , cliquez sur **Teams**.
4. Dans le centre d’administration Teams, dans le volet de navigation de gauche, développez Paramètres à l’échelle de l' **organisation** , puis cliquez sur **accès invité**.
5. Assurez-vous que **Autoriser l’accès invité dans Teams** est défini sur **Activé**.
6. Apportez les modifications souhaitées aux autres paramètres invités, puis cliquez sur **Enregistrer**.

> [!NOTE]
> La mise à niveau des paramètres invités de teams peut prendre jusqu’à vingt-quatre heures après son activation.

## <a name="microsoft-365-groups-guest-settings"></a>Paramètres invités des groupes Microsoft 365

Teams utilise les groupes Microsoft 365 pour les membres de l’équipe. Les paramètres invités des groupes Microsoft 365 doivent être activés pour que l’accès invité dans teams puisse fonctionner.

![Capture d’écran des paramètres d’invité des Groupes Microsoft 365 dans le Centre d’administration Microsoft 365](../media/office-365-groups-guest-settings.png)

Pour définir les paramètres invités des groupes Microsoft 365

1. Dans le centre d’administration Microsoft 365, dans le volet de navigation de gauche, développez **paramètres**.
2. Cliquez sur paramètres de l' **organisation**.
3. Dans la liste, cliquez sur **groupes Microsoft 365**.
4. Assurez-vous que les **propriétaires de groupe Let ajoutent des personnes extérieures à votre organisation aux groupes Microsoft 365 en tant qu’invités** et laissez les cases à cocher le **contenu des membres du groupe invité** sont tous deux activés.
5. Si vous avez apporté des modifications, cliquez sur **enregistrer les modifications**.


## <a name="sharepoint-organization-level-sharing-settings"></a>Paramètres de partage au niveau de l’organisation SharePoint

Le contenu de teams, tel que des fichiers, des dossiers et des listes, est tous stockés dans SharePoint. Pour que les invités aient accès à ces éléments dans Teams, les paramètres de partage au niveau de l’organisation SharePoint doivent autoriser le partage avec des invités.

Les paramètres au niveau de l’organisation déterminent les paramètres disponibles pour des sites individuels, y compris les sites associés à Teams. Les paramètres de site ne peuvent pas être plus permissants que les paramètres au niveau de l’organisation.

Si vous souhaitez autoriser le partage de fichiers et de dossiers avec des personnes non authentifiées, sélectionnez **tout le monde**. Si vous souhaitez vous assurer que tous les invités doivent s’authentifier, choisissez **nouveau et invités existants**. Choisissez le paramètre le plus permissif qui sera nécessaire pour tous les sites de votre organisation.

![Capture d’écran des paramètres de partage SharePoint au niveau de l’organisation](../media/sharepoint-organization-external-sharing-controls.png)


Pour définir les paramètres de partage au niveau de l’organisation SharePoint

1. Dans le centre d’administration 365 de Microsoft, dans le volet de navigation de gauche, sous **centres d’administration** , cliquez sur **SharePoint**.
2. Dans le centre d’administration SharePoint, dans le volet de navigation de gauche, développez **stratégies** , puis cliquez sur **partage**.
3. Assurez-vous que le partage externe pour SharePoint est défini sur **tout le monde** ou sur **des invités nouveaux et existants**.
4. Si vous avez effectué des modifications, cliquez sur **Enregistrer**.


## <a name="sharepoint-organization-level-default-link-settings"></a>Paramètres de lien par défaut au niveau de l’organisation SharePoint

Les paramètres de lien de fichier et de dossier par défaut déterminent l’option de lien qui apparaîtra par défaut aux utilisateurs lorsqu’ils partageront un fichier ou un dossier. Les utilisateurs peuvent remplacer le type de lien par l’une des autres options avant le partage, si vous le souhaitez.

N’oubliez pas que ce paramètre affecte toutes les équipes et tous les sites SharePoint de votre organisation.

Choisissez l’un des types de liaison suivants, qui sera sélectionné par défaut lorsque les utilisateurs partageront des fichiers et des dossiers :

- **Toute personne disposant du lien** : choisissez cette option si vous envisagez d’effectuer beaucoup de partage non authentifié de fichiers et de dossiers. Si vous souhaitez autoriser *tout le monde* à se lier, mais que vous êtes préoccupé par le partage non authentifié accidentel, envisagez l’une des autres options par défaut. Ce type de lien n’est disponible que si vous avez activé le partage d’un **utilisateur** .
- **Uniquement les personnes de votre organisation** : choisissez cette option si vous pensez que le partage de fichiers et de dossiers doit être associé à des personnes au sein de votre organisation.
- **Personnes spécifiques** : envisagez cette option si vous envisagez de faire beaucoup de partage de fichiers et de dossiers avec des invités. Ce type de lien fonctionne avec les invités et les requiert pour s’authentifier.
 
![Capture d’écran des paramètres de partage de fichiers et dossiers au niveau de l’organisation dans SharePoint](../media/sharepoint-organization-files-folders-sharing-settings.png)


Pour définir les paramètres de lien par défaut au niveau de l’organisation SharePoint

1. Accédez à la page de partage dans le centre d’administration SharePoint.
2. Sous **liens de fichiers et de dossiers** , sélectionnez le lien de partage par défaut à utiliser.
3. Si vous avez effectué des modifications, cliquez sur **Enregistrer**.

## <a name="create-a-team"></a>Créer une équipe

L’étape suivante consiste à créer l’équipe que vous envisagez d’utiliser pour collaborer avec des invités.

Pour créer une équipe
1. Dans Teams, sous l’onglet **teams** , cliquez sur **rejoindre ou créer une équipe** en bas du volet de gauche.
2. Cliquez sur **créer une équipe**.
3. Cliquez sur **créer une équipe de toutes pièces**.
4. Choisissez **privé** ou **public**.
5. Tapez un nom et une description pour l’équipe, puis cliquez sur **créer**.
6. Cliquez sur **Ignorer**.

Nous allons inviter les utilisateurs ultérieurement. Ensuite, il est important de vérifier les paramètres de partage au niveau du site pour le site SharePoint qui est associé à l’équipe.

## <a name="sharepoint-site-level-sharing-settings"></a>Paramètres de partage au niveau du site SharePoint

Vérifiez les paramètres de partage au niveau du site pour vous assurer qu’ils autorisent le type d’accès que vous souhaitez pour cette équipe. Par exemple, si vous définissez les paramètres au niveau de l’organisation sur tous les **utilisateurs** , mais que vous souhaitez que tous les invités s’authentifient pour cette équipe, assurez-vous que les paramètres de partage au niveau du site sont définis sur **nouveaux et invités existants**.

![Capture d’écran des paramètres de partage externe de site SharePoint](../media/sharepoint-site-external-sharing-settings.png)


Pour définir les paramètres de partage au niveau du site
1. Dans le centre d’administration SharePoint, dans le volet de navigation de gauche, développez **sites** , puis cliquez sur **sites actifs**.
2. Sélectionnez le site de l’équipe que vous venez de créer.
3. Cliquez sur... et choisissez **partage**.
4. Assurez-vous que le partage est défini sur **tout le monde** ou sur **des invités nouveaux et existants**.
5. Si vous avez effectué des modifications, cliquez sur **Enregistrer**.

## <a name="invite-users"></a>Inviter des utilisateurs

Les paramètres de partage des invités sont désormais configurés, de sorte que vous pouvez commencer à ajouter des utilisateurs et des invités internes à votre équipe. 

Pour inviter des utilisateurs internes à une équipe
1. Dans l’équipe, cliquez sur **plus d’options** ( **\*\*\*** ), puis sur **Ajouter un membre**.
2. Tapez le nom de la personne que vous souhaitez inviter.
3. Cliquez sur **Ajouter** , puis sur **Fermer**.

Pour inviter des invités à une équipe
1. Dans l’équipe, cliquez sur **plus d’options** ( **\*\*\*** ), puis sur **Ajouter un membre**.
2. Tapez l’adresse de messagerie de l’invité que vous souhaitez inviter.
3. Cliquez sur **modifier les informations invité**.
4. Tapez le nom complet de l’invité et cliquez sur la coche.
5. Cliquez sur **Ajouter** , puis sur **Fermer**.

## <a name="see-also"></a>Voir aussi

[Meilleures pratiques relatives au partage de fichiers et de dossiers avec des utilisateurs non authentifiés](best-practices-anonymous-sharing.md)

[Limiter l’exposition accidentelle aux fichiers lors du partage avec des invités](share-limit-accidental-exposure.md)

[Créer un environnement de partage sécurisé avec des invités](create-secure-guest-sharing-environment.md)

[Créer un extranet B2B avec des invités gérés](b2b-extranet.md)

[Intégration de SharePoint et de OneDrive avec Azure AD B2B](https://docs.microsoft.com/sharepoint/sharepoint-azureb2b-integration-preview)
