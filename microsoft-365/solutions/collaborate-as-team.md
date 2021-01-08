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
description: Découvrez les étapes de configuration de Microsoft 365 nécessaires pour configurer une équipe pour la collaboration de tâches, de conversations et de documentation avec des invités dans Teams.
ms.openlocfilehash: 34b7d5d47d7fb0c9196beda70184fa6510b6cc33
ms.sourcegitcommit: ec293978e951b09903b79e6642aa587824935e0c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2021
ms.locfileid: "49780543"
---
# <a name="collaborate-with-guests-in-a-team"></a>Collaborer avec des invités au sein d’une équipe

Si vous avez besoin de collaborer avec des invités dans des documents, des tâches et des conversations, nous vous recommandons d’utiliser Microsoft Teams. Teams fournit toutes les fonctionnalités de collaboration disponibles dans Office et SharePoint avec une conversation permanente et un ensemble personnalisable et extensible d’outils de collaboration dans une expérience utilisateur unifiée.

Dans cet article, nous allons passer en revue les étapes de configuration de Microsoft 365 nécessaires pour configurer une équipe pour la collaboration avec les invités.

## <a name="video-demonstration"></a>Démonstration vidéo

Cette vidéo montre les étapes de configuration décrites dans ce document.</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE44NTr?autoplay=false]

## <a name="azure-external-collaboration-settings"></a>Paramètres de collaboration externe Azure

Le partage dans Microsoft 365 est régi à son niveau le plus élevé par les [paramètres de collaboration externe B2B dans Azure Active Directory.](https://docs.microsoft.com/azure/active-directory/external-identities/delegate-invitations) Si le partage d’invités est désactivé ou restreint dans Azure AD, ce paramètre remplace tous les paramètres de partage que vous configurez dans Microsoft 365.

Vérifiez les paramètres de collaboration externe B2B pour vous assurer que le partage avec des invités n’est pas bloqué.

![Capture d’écran de la page des paramètres de relations organisationnelles d’Azure Active Directory](../media/azure-ad-organizational-relationships-settings.png)

Pour définir des paramètres de collaboration externe

1. Connectez-vous à Azure Active Directory sur [https://aad.portal.azure.com](https://aad.portal.azure.com) .
2. Dans le volet de navigation de gauche, cliquez **sur Azure Active Directory.**
3. Cliquez **sur Identités externes.**
4. Dans **l’écran De mise en** main, dans le volet de navigation de gauche, cliquez sur **Paramètres de collaboration externe.**
5. **Assurez-vous que les administrateurs et les utilisateurs** du rôle d’invite d’invités peuvent inviter et que les membres peuvent **inviter** sont tous les deux définies sur **Oui**.
6. Si vous avez effectué des modifications, cliquez sur **Enregistrer**.

Notez les paramètres de la section **Restrictions de** collaboration. Assurez-vous que les domaines des invités avec qui vous souhaitez collaborer ne sont pas bloqués.

Si vous travaillez avec des invités de plusieurs organisations, vous pouvez restreindre leur capacité à accéder aux données d’annuaire. Cela les empêche de voir qui d’autre est un invité dans l’annuaire. Pour ce faire, sous les restrictions d’accès des **utilisateurs invités,** sélectionnez Les utilisateurs invités ont un accès limité aux propriétés et à l’appartenance aux paramètres des objets d’annuaire ou l’accès des **utilisateurs** invités est limité aux propriétés et aux **appartenances** de leurs propres objets d’annuaire.

## <a name="teams-guest-access-settings"></a>Paramètres d’accès invité Teams

Teams dispose d’un commutateur master on/off pour l’accès invité et de divers paramètres disponibles pour contrôler ce que les invités peuvent faire dans une équipe. Le commutateur maître, **Autoriser l’accès invité dans Teams,** doit être **en** cours pour que l’accès invité fonctionne dans Teams.

Vérifiez que l’accès invité est activé dans Teams et ajustez les paramètres invité en fonction des besoins de votre entreprise. Gardez à l’esprit que ces paramètres affectent toutes les équipes.

![Capture d’écran du commutateur Accès invité dans Teams](../media/teams-guest-access-toggle-on.png)

Pour déterminer les paramètres d’accès invité Teams, procédez comme suit :

1. Connectez-vous au Centre d’administration Microsoft 365 sur[https://admin.microsoft.com](https://admin.microsoft.com).
2. Dans le volet de navigation de gauche, cliquez **sur Afficher tout.**
3. Sous **Centres d’administration**, cliquez sur **Teams**.
4. Dans le centre d’administration Teams, dans le volet de navigation de gauche, développez les **paramètres** à l’échelle de l’organisation et cliquez sur **Accès invité.**
5. Assurez-vous que **Autoriser l’accès invité dans Teams** est défini sur **Activé**.
6. Apportez les modifications souhaitées aux autres paramètres invités, puis cliquez sur **Enregistrer**.

Une fois l’accès invité Teams est désactivé, vous pouvez éventuellement contrôler l’accès invité à des équipes individuelles et à leurs sites SharePoint associés à l’aide d’étiquettes de sensibilité. Pour plus d’informations, voir [Utiliser les étiquettes de confidentialité pour protéger le contenu dans Microsoft Teams, les groupes Office 365 et les sites SharePoint](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-teams-groups-sites).

> [!NOTE]
> L’activité des paramètres invités teams peut prendre jusqu’à 24 heures une fois que vous l’avez active.

## <a name="microsoft-365-groups-guest-settings"></a>Paramètres invités des groupes Microsoft 365

Teams utilise les groupes Microsoft 365 pour l’appartenance à une équipe. Les paramètres invités des groupes Microsoft 365 doivent être allumés pour que l’accès invité dans Teams fonctionne.

![Capture d’écran des paramètres d’invité des Groupes Microsoft 365 dans le Centre d’administration Microsoft 365](../media/office-365-groups-guest-settings.png)

Pour définir les paramètres invités des groupes Microsoft 365

1. Dans le Centre d’administration Microsoft 365, dans le volet de navigation de gauche, développez **Paramètres.**
2. Cliquez **sur Paramètres de l’organisation.**
3. Dans la liste, cliquez **sur Groupes Microsoft 365.**
4. Assurez-vous que les propriétaires du groupe Permettre aux propriétaires d’ajouter des personnes extérieures à votre organisation aux groupes **Microsoft 365** en tant qu’invités et permettre aux membres du groupe invité d’accéder aux cases à cocher de contenu du groupe sont cochées. 
5. Si vous avez apporté des modifications, cliquez **sur Enregistrer les modifications.**


## <a name="sharepoint-organization-level-sharing-settings"></a>Paramètres de partage au niveau de l’organisation SharePoint

Le contenu Teams, tel que les fichiers, les dossiers et les listes, est stocké dans SharePoint. Pour que les invités ont accès à ces éléments dans Teams, les paramètres de partage au niveau de l’organisation SharePoint doivent autoriser le partage avec des invités.

Les paramètres au niveau de l’organisation déterminent les paramètres disponibles pour les sites individuels, y compris les sites associés à des équipes. Les paramètres de site ne peuvent pas être plus permissifs que les paramètres au niveau de l’organisation.

Si vous souhaitez autoriser le partage de fichiers et de dossiers avec des personnes non authentifiés, choisissez **Tout le monde.** Si vous souhaitez vous assurer que tous les invités doivent s’authentifier, choisissez **Invités nouveaux et existants.** Choisissez le paramètre le plus permissif qui sera nécessaire à n’importe quel site de votre organisation.

![Capture d’écran des paramètres de partage SharePoint au niveau de l’organisation](../media/sharepoint-organization-external-sharing-controls.png)


Pour définir les paramètres de partage au niveau de l’organisation SharePoint

1. Dans le Centre d’administration Microsoft 365, dans le volet de navigation de gauche, sous Centres d’administration, cliquez **sur SharePoint**.
2. Dans le Centre d’administration SharePoint, dans le volet de navigation de gauche, développez **Stratégies,** puis cliquez sur **Partage.**
3. Assurez-vous que le partage externe pour SharePoint est définie sur **Tout** le monde ou **Nouveau et les invités existants.**
4. Si vous avez effectué des modifications, cliquez sur **Enregistrer**.


## <a name="sharepoint-organization-level-default-link-settings"></a>Paramètres de lien par défaut au niveau de l’organisation SharePoint

Les paramètres de lien de fichiers et de dossiers par défaut déterminent l’option de lien qui sera affichée par défaut aux utilisateurs lorsqu’ils partagent un fichier ou un dossier. Les utilisateurs peuvent modifier le type de lien en l’une des autres options avant le partage, si vous le souhaitez.

N’oubliez pas que ce paramètre affecte toutes les équipes et les sites SharePoint de votre organisation.

Choisissez l’un des types de liens suivants qui sera sélectionné par défaut lorsque les utilisateurs partagent des fichiers et des dossiers :

- **Toute personne partageant le** lien : choisissez cette option si vous prévoyez d’avoir un grand nombre de partages non authentifiés de fichiers et de dossiers. Si vous souhaitez autoriser les liens *Tout* le monde mais que vous êtes préoccupé par le partage non authentifié accidentel, envisagez l’une des autres options par défaut. Ce type de lien est disponible uniquement si vous avez activé le partage **tout le** monde.
- **Seules les personnes de votre organisation** : choisissez cette option si vous pensez que la plupart des partages de fichiers et de dossiers seront partagés avec des personnes au sein de votre organisation.
- **Personnes spécifiques** : envisagez cette option si vous comptez faire beaucoup de partage de fichiers et de dossiers avec des invités. Ce type de lien fonctionne avec les invités et les oblige à s’authentifier.
 
![Capture d’écran des paramètres de partage de fichiers et dossiers au niveau de l’organisation dans SharePoint](../media/sharepoint-organization-files-folders-sharing-settings.png)


Pour définir les paramètres de lien par défaut au niveau de l’organisation SharePoint

1. Accédez à la page Partage dans le Centre d’administration SharePoint.
2. Sous **Liens de fichiers et de dossiers,** sélectionnez le lien de partage par défaut que vous souhaitez utiliser.
3. Si vous avez effectué des modifications, cliquez sur **Enregistrer**.

## <a name="create-a-team"></a>Créer une équipe

L’étape suivante consiste à créer l’équipe que vous prévoyez d’utiliser pour collaborer avec des invités.

Pour créer une équipe
1. Dans Teams, sous l’onglet **Teams,** cliquez sur **Rejoindre** ou créer une équipe en bas du volet gauche.
2. Cliquez **sur Créer une équipe.**
3. Cliquez **sur Créer une équipe à partir de zéro.**
4. Choisissez **Privé** ou **Public.**
5. Tapez un nom et une description pour l’équipe, puis cliquez sur **Créer.**
6. Cliquez **sur Ignorer.**

Nous inviterons les utilisateurs ultérieurement. Ensuite, il est important de vérifier les paramètres de partage au niveau du site pour le site SharePoint associé à l’équipe.

## <a name="sharepoint-site-level-sharing-settings"></a>Paramètres de partage au niveau du site SharePoint

Vérifiez les paramètres de partage au niveau du site pour vous assurer qu’ils autorisent le type d’accès que vous souhaitez pour cette équipe. Par exemple, si vous définissez les paramètres au niveau de l’organisation sur Tout le **monde,** mais que vous souhaitez que tous les invités s’authentifier pour cette équipe, assurez-vous que les paramètres de partage au niveau du site sont les invités nouveaux et existants. 

![Capture d’écran des paramètres de partage externe de site SharePoint](../media/sharepoint-site-external-sharing-settings.png)

Pour définir les paramètres de partage au niveau du site
1. Dans le Centre d’administration SharePoint, dans le volet de navigation de gauche, développez **Sites** et cliquez **sur Sites actifs.**
2. Sélectionnez le site de l’équipe que vous venez de créer.
3. Cliquez sur ... et choisissez **Partage.**
4. Assurez-vous que le partage est définie sur **Tout** le monde ou **Nouveau et sur les invités existants.**
5. Si vous avez effectué des modifications, cliquez sur **Enregistrer**.

## <a name="invite-users"></a>Inviter des utilisateurs

Les paramètres de partage d’invités sont désormais configurés, afin que vous pouvez commencer à ajouter des utilisateurs internes et des invités à votre équipe. 

Pour inviter des utilisateurs internes à une équipe
1. Dans l’équipe, cliquez **sur Plus d’options** ( **\*\*\*** ), puis cliquez sur Ajouter un **membre.**
2. Tapez le nom de la personne que vous voulez inviter.
3. Cliquez **sur** Ajouter, puis sur **Fermer.**

Pour inviter des invités à une équipe
1. Dans l’équipe, cliquez **sur Plus d’options** ( **\*\*\*** ), puis cliquez sur Ajouter un **membre.**
2. Tapez l’adresse e-mail de l’invité que vous voulez inviter.
3. Cliquez sur **Modifier les informations d’invité.**
4. Tapez le nom complet de l’invité et cliquez sur la coche.
5. Cliquez **sur** Ajouter, puis sur **Fermer.**

## <a name="see-also"></a>Voir aussi

[Meilleures pratiques relatives au partage de fichiers et de dossiers avec des utilisateurs non authentifiés](best-practices-anonymous-sharing.md)

[Limiter l’exposition accidentelle aux fichiers lors du partage avec des invités](share-limit-accidental-exposure.md)

[Créer un environnement de partage sécurisé avec des invités](create-secure-guest-sharing-environment.md)

[Créer un extranet B2B avec des invités gérés](b2b-extranet.md)

[Intégration de SharePoint et OneDrive à Azure AD B2B](https://docs.microsoft.com/sharepoint/sharepoint-azureb2b-integration-preview)

[Les options de partage sont grisées lors du partage à partir de SharePoint ou OneDrive](https://docs.microsoft.com/sharepoint/troubleshoot/administration/sharing-options-grayed-out-when-sharing-from-sharepoint-online-or-onedrive)
