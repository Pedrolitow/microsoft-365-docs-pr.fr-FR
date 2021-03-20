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
localization_priority: Priority
f1.keywords: NOCSH
description: Découvrez les étapes de configuration de Microsoft 365 nécessaires pour configurer une équipe pour la collaboration entre les tâches, les conversations et la documentation avec les invités dans Teams.
ms.openlocfilehash: 4e734af198563d0bc4599b4476b3823384989212
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50904659"
---
# <a name="collaborate-with-guests-in-a-team"></a>Collaborer avec des invités au sein d’une équipe

Si vous devez collaborer avec des invités au sein de documents, de tâches et de conversations, nous vous recommandons d’utiliser Microsoft Teams. Teams fournit toutes les fonctionnalités de collaboration disponibles dans Office et SharePoint avec une conversation permanente et un ensemble personnalisable et extensible d’outils de collaboration dans une expérience utilisateur unifiée.

Dans cet article, nous allons suivre les étapes de configuration de Microsoft 365 nécessaires pour configurer une équipe en collaboration avec des invités. Une fois que vous avez configuré l'accès invité, vous pouvez inviter des personnes à des équipes en suivant les étapes de la section [Ajouter des invités à une équipe dans Teams](https://support.microsoft.com/office/fccb4fa6-f864-4508-bdde-256e7384a14f).

## <a name="video-demonstration"></a>Démonstration vidéo

Cette vidéo décrit les étapes de configuration décrites dans ce document.</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE44NTr?autoplay=false]

## <a name="azure-external-collaboration-settings"></a>Paramètres de collaboration externe Azure

Le partage dans Microsoft 365 est régi à son niveau le plus élevé par les [paramètres de collaboration externe B2B dans Azure Active Directory](/azure/active-directory/external-identities/delegate-invitations). Si le partage invité est désactivé ou restreint dans Azure AD, ce paramètre remplace les paramètres de partage que vous configurez dans Microsoft 365.

Vérifiez les paramètres de collaboration externe B2B pour vous assurer que le partage avec les invités n’est pas bloqué.

![Capture d’écran de la page des paramètres de relations organisationnelles d’Azure Active Directory](../media/azure-ad-organizational-relationships-settings.png)

Pour définir les paramètres de collaboration externe

1. Connectez-vous à Azure Active Directory sur [https://aad.portal.azure.com](https://aad.portal.azure.com).
2. Dans le volet de navigation gauche, cliquez sur **Azure Active Directory**.
3. Cliquez sur **Identités externes**.
4. Dans l’écran **Prise en main**, dans le volet de navigation gauche, cliquez sur **Paramètres de collaboration externe**.
5. Assurez-vous que **Les administrateurs et les utilisateurs membres du rôle Inviteur d’invités peuvent envoyer des invitations** et **Les membres peuvent inviter** sont tous deux définis sur **Oui**.
6. Si vous avez effectué des modifications, cliquez sur **Enregistrer**.

Notez les paramètres dans la section **Restrictions de collaboration**. Assurez-vous que les domaines des invités avec qui vous voulez collaborer ne sont pas bloqués.

Si vous travaillez avec des invités de plusieurs organisations, vous souhaiterez peut-être restreindre leur capacité à accéder aux données d’annuaire. Cela les empêche de voir qui d’autre est invité dans l’annuaire. Pour ce faire, sous **Restrictions d’accès des utilisateurs invités**, sélectionnez **Les utilisateurs invités ont un accès limité aux propriétés et à l’appartenance aux paramètres des objets d’annuaire** ou **L’accès des utilisateurs invités est limité aux propriétés et à l’appartenance à leurs propres objets d’annuaire**.

## <a name="teams-guest-access-settings"></a>Paramètres d’accès invité Teams, procédez comme suit :

Teams dispose d’un commutateur maître d’accès par invité et de divers paramètres disponibles pour contrôler ce que les invités peuvent faire dans une équipe. Le commutateur maître, **Autoriser l’accès invité dans Teams** doit être **Activé** pour que l’accès invité fonctionne dans Teams.

Vérifiez que l’accès invité est activé dans Teams et ajustez les paramètres invités en fonction des besoins de votre entreprise. N’oubliez pas que ces paramètres affectent toutes les équipes.

![Capture d’écran du commutateur Accès invité dans Teams](../media/teams-guest-access-toggle-on.png)

Pour déterminer les paramètres d’accès invité Teams, procédez comme suit :

1. Connectez-vous au Centre d’administration Microsoft 365 sur[https://admin.microsoft.com](https://admin.microsoft.com).
2. Dans la barre de navigation de gauche, cliquez sur **Afficher tout**.
3. Sous **Centres d’administration**, cliquez sur **Teams**.
4. Dans le Centre d’administration Teams, dans le volet de navigation gauche, développez **Paramètres à l’échelle de l’organisation**, puis cliquez sur **Accès invité**.
5. Assurez-vous que **Autoriser l’accès invité dans Teams** est défini sur **Activé**.
6. Apportez les modifications souhaitées aux autres paramètres invités, puis cliquez sur **Enregistrer**.

Une fois l’accès invité Teams désactivé, vous pouvez éventuellement contrôler l’accès invité aux équipes individuelles et à leurs sites SharePoint associés à l’aide d’étiquettes de critère de critère de sécurité. Pour plus d’informations, voir [Utiliser les étiquettes de confidentialité pour protéger le contenu dans Microsoft Teams, les groupes Office 365 et les sites SharePoint](../compliance/sensitivity-labels-teams-groups-sites.md).

> [!NOTE]
> La mise en service des paramètres invité Teams peut prendre jusqu'à vingt-quatre heures.

## <a name="microsoft-365-groups-guest-settings"></a>Paramètres invités des groupes Microsoft 365

Teams utilise les groupes Microsoft 365 pour l’appartenance aux équipes. Les paramètres invités des groupes Microsoft 365 doivent être désactivés pour que l’accès invité dans Teams fonctionne.

![Capture d’écran des paramètres d’invité des Groupes Microsoft 365 dans le Centre d’administration Microsoft 365](../media/office-365-groups-guest-settings.png)

Pour définir les paramètres invités des groupes Microsoft 365

1. Dans le Centre d’administration Microsoft 365, dans le volet de navigation gauche, développez **Paramètres**.
2. Cliquez sur **Paramètres de l’organisation**.
3. Dans la liste, cliquez sur **Groupes Microsoft 365**.
4. Assurez-vous que les cases à cocher **Permettre aux propriétaires de groupe d’ajouter des personnes externes à votre organisation à des groupes Microsoft 365 en tant qu'invités** et **Permettre aux membres du groupe invités d’accéder au contenu du groupe** sont cochées.
5. Si vous avez effectué des modifications, cliquez sur **Enregistrer**.


## <a name="sharepoint-organization-level-sharing-settings"></a>Paramètres de partage SharePoint au niveau de l’organisation

Le contenu Teams, tel que les fichiers, dossiers et listes, est stocké dans SharePoint. Pour que les invités aient accès à ces éléments dans Teams, les paramètres de partage au niveau de l'organisation SharePoint doivent permettre le partage avec les invités.

Les paramètres au niveau de l’organisation déterminent les paramètres disponibles pour les sites individuels, y compris les sites associés à des équipes. Les paramètres de site ne peuvent pas être plus permissifs que les paramètres au niveau de l’organisation.

Si vous voulez autoriser le partage de fichiers et de dossiers avec des personnes non authentifiés, sélectionnez **Tout le monde**. Pour vous assurer que tous les invités doivent s’authentifier, Choisissez **Invités nouveaux et existants**. Choisissez le paramètre le plus permissif qui sera nécessaire pour n’importe quel site de votre organisation.

![Capture d’écran des paramètres de partage SharePoint au niveau de l’organisation](../media/sharepoint-organization-external-sharing-controls.png)


Pour définir les paramètres de partage SharePoint au niveau de l’organisation

1. Dans le Centre d’administration Microsoft 365, dans le volet de navigation gauche, sous **Centres d’administration**, cliquez sur **SharePoint**.
2. Dans le Centre d’administration SharePoint, dans le volet de navigation gauche, développez **Stratégies** puis cliquez sur **Partage**.
3. Assurez-vous que le partage externe pour SharePoint est **Tout le monde** ou **Invités nouveaux et existants**.
4. Si vous avez effectué des modifications, cliquez sur **Enregistrer**.


## <a name="sharepoint-organization-level-default-link-settings"></a>Paramètres de liaison par défaut au niveau de l’organisation SharePoint

Les paramètres par défaut de liaison de fichier et de dossier déterminent l’option de lien qui sera affichée par défaut aux utilisateurs lorsqu’ils partagent un fichier ou un dossier. Si vous le souhaitez, les utilisateurs peuvent modifier le type de lien vers l’une des autres options avant le partage.

N’oubliez pas que ce paramètre affecte toutes les équipes et les sites SharePoint dans votre organisation.

Choisissez l’un des types de liens suivants qui seront sélectionnés par défaut lorsque les utilisateurs partagent des fichiers et des dossiers :

- **Toute personne disposant du lien** : choisissez cette option si vous vous attendez à beaucoup de partage non authentifié de fichiers et de dossiers. Si vous souhaitez autoriser les liens à *Tout le monde* mais que vous craignez un partage accidentel non authentifié, envisagez l'une des autres options comme valeur par défaut. Ce type de lien n’est disponible que si vous avez activé le partage **Tout le monde**.
- **Uniquement les personnes de votre organisation** : choisissez cette option si vous souhaitez que la plupart des partages de fichiers et de dossiers soient avec des personnes de votre organisation.
- **Personnes spécifiques** : envisagez cette option si vous prévoyez de partager beaucoup de fichiers et de dossiers avec vos invités. Ce type de lien fonctionne avec les invités et exige leur authentification.
 
![Capture d’écran des paramètres de partage de fichiers et dossiers au niveau de l’organisation dans SharePoint](../media/sharepoint-organization-files-folders-sharing-settings.png)


Pour définir les paramètres de liaison par défaut au niveau de l’organisation SharePoint

1. Accédez à la page Partage dans le Centre d’administration SharePoint.
2. Sous **Liens des fichiers et des dossiers**, sélectionnez le lien de partage par défaut que vous voulez utiliser.
3. Si vous avez effectué des modifications, cliquez sur **Enregistrer**.

## <a name="create-a-team"></a>Créer une équipe

L'étape suivante consiste à créer l'équipe que vous comptez utiliser pour collaborer avec les invités.

Pour créer une équipe
1. Dans Teams, dans l’onglet **Teams** , cliquez sur **Rejoindre ou créer une équipe** en bas du volet gauche.
2. Cliquez sur **Créer une équipe**.
3. Cliquez sur **Créer une équipe à partir de zéro**.
4. Sélectionnez **Privé** ou **Public**.
5. Entrez le nom et une description du groupe, puis cliquez sur **Créer**.
6. Cliquez sur **Ignorer**.

Nous inviterons des utilisateurs plus tard. Ensuite, il est important de vérifier les paramètres de partage au niveau du site pour le site SharePoint associé à l’équipe.

## <a name="sharepoint-site-level-sharing-settings"></a>Paramètres de SharePoint au niveau du site

Vérifiez les paramètres de partage au niveau du site pour vous assurer qu’ils autorisent le type d’accès voulu pour cette équipe. Par exemple, si vous définissez les paramètres au niveau de l’organisation sur **Tout le monde**, mais que vous souhaitez que tous les invités s’authentifier au niveau de cette équipe, assurez-vous que les paramètres de partage au niveau du site sont **Invités nouveaux et existants**.

![Capture d’écran des paramètres de partage externe de site SharePoint](../media/sharepoint-site-external-sharing-settings.png)

Pour définir les paramètres au niveau du site
1. Dans le centre d’administration SharePoint, dans le volet de navigation de gauche, développez **Sites** et cliquez sur **Sites actifs**.
2. Sélectionnez le site de l’équipe que vous venez de créer.
3. Cliquez sur... puis sélectionnez **Partage**.
4. Assurez-vous que le partage est paramétré sur **Tout le monde** ou **Invités nouveaux et existants**.
5. Si vous avez effectué des modifications, cliquez sur **Enregistrer**.

## <a name="invite-users"></a>Inviter des utilisateurs

Les paramètres de partage invité sont désormais configurés. Vous pouvez ainsi commencer à ajouter des utilisateurs internes et des invités à votre équipe. 

Pour inviter des utilisateurs internes à une équipe
1. Dans l’équipe, cliquez sur **Plus d'options** (**\*\*\***), puis sur **Ajouter un membre**.
2. Tapez le nom de la personne que vous voulez inviter.
3. Cliquez sur **Ajouter**, puis sur **Fermer**.

Pour inviter à une équipe
1. Dans l’équipe, cliquez sur **Plus d'options** (**\*\*\***), puis sur **Ajouter un membre**.
2. Tapez l’adresse de courrier de la personne que vous voulez inviter.
3. Cliquez sur **Modifier les informations d’un utilisateur invité**.
4. Tapez le nom complet de l’invité, puis cliquez sur la coche.
5. Cliquez sur **Ajouter**, puis sur **Fermer**.

## <a name="see-also"></a>Voir aussi

[Meilleures pratiques relatives au partage de fichiers et de dossiers avec des utilisateurs non authentifiés](best-practices-anonymous-sharing.md)

[Limiter l’exposition accidentelle aux fichiers lors du partage avec des invités](share-limit-accidental-exposure.md)

[Créer un environnement de partage sécurisé avec des invités](create-secure-guest-sharing-environment.md)

[Créer un extranet B2B avec des invités gérés](b2b-extranet.md)

[Intégration de SharePoint et de OneDrive à Azure AD B2B](/sharepoint/sharepoint-azureb2b-integration-preview)

[Les options de partage sont grisées lors du partage à partir de SharePoint ou OneDrive](/sharepoint/troubleshoot/administration/sharing-options-grayed-out-when-sharing-from-sharepoint-online-or-onedrive)