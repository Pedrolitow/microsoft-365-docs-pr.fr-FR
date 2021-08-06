---
title: Collaborer avec des invités sur un site
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
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
recommendations: false
description: Découvrez les étapes Microsoft 365 configuration requises pour configurer un site SharePoint pour la collaboration avec des invités.
ms.openlocfilehash: 054de924b2cf5041694ca12dcf2fb4137242d16fb53060421aedb51aed9668a9
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53810173"
---
# <a name="collaborate-with-guests-in-a-site"></a>Collaborer avec des invités sur un site

Si vous avez besoin de collaborer avec des invités dans des documents, des données et des listes, vous pouvez utiliser un site SharePoint web. Les sites SharePoint modernes sont connectés à des groupes Microsoft 365 et peuvent gérer l’appartenance au site et fournir des outils de collaboration supplémentaires tels qu’une boîte aux lettres partagée et un calendrier.

Dans cet article, nous allons passer en revue les étapes de configuration Microsoft 365 nécessaires pour configurer un site SharePoint collaboration avec des invités.

## <a name="video-demonstration"></a>Démonstration vidéo

Cette vidéo décrit les étapes de configuration décrites dans ce document.</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE44Llg?autoplay=false]

## <a name="azure-external-collaboration-settings"></a>Paramètres de collaboration externe Azure

Le partage dans Microsoft 365 est régi à son niveau le plus élevé par les [paramètres de collaboration externe B2B dans Azure Active Directory](/azure/active-directory/external-identities/delegate-invitations). Si le partage invité est désactivé ou restreint dans Azure AD, ce paramètre remplace les paramètres de partage que vous configurez dans Microsoft 365.

Vérifiez les paramètres de collaboration externe B2B pour vous assurer que le partage avec des invités n’est pas bloqué.

![Capture d’écran Azure Active Directory page Paramètres collaboration externe](../media/azure-ad-organizational-relationships-settings.png)

Pour définir les paramètres de collaboration externe

1. Connectez-vous à Azure Active Directory sur [https://aad.portal.azure.com](https://aad.portal.azure.com).
2. Dans le volet de navigation gauche, cliquez sur **Azure Active Directory**.
3. Cliquez sur **Identités externes**.
4. Dans l’écran **Prise en main**, dans le volet de navigation gauche, cliquez sur **Paramètres de collaboration externe**.
5. Assurez-vous que **Les administrateurs et les utilisateurs membres du rôle Inviteur d’invités peuvent envoyer des invitations** et **Les membres peuvent inviter** sont tous deux définis sur **Oui**.
6. Si vous avez effectué des modifications, cliquez sur **Enregistrer**.

Notez les paramètres dans la section **Restrictions de collaboration**. Assurez-vous que les domaines des invités avec qui vous voulez collaborer ne sont pas bloqués.

Si vous travaillez avec des invités de plusieurs organisations, vous souhaiterez peut-être restreindre leur capacité à accéder aux données d’annuaire. Cela les empêche de voir qui d’autre est invité dans l’annuaire. Pour ce faire, sous **Restrictions d’accès des utilisateurs invités**, sélectionnez **Les utilisateurs invités ont un accès limité aux propriétés et à l’appartenance aux paramètres des objets d’annuaire** ou **L’accès des utilisateurs invités est limité aux propriétés et à l’appartenance à leurs propres objets d’annuaire**.

## <a name="microsoft-365-groups-guest-settings"></a>Paramètres invités des groupes Microsoft 365

Les sites SharePoint modernes utilisent Microsoft 365 groupes pour contrôler l’accès au site. Les paramètres Microsoft 365 groupes d’invités doivent être allumés pour que l’accès invité SharePoint sites fonctionne.

![Capture d’écran des paramètres d’invité des Groupes Microsoft 365 dans le Centre d’administration Microsoft 365](../media/office-365-groups-guest-settings.png)

Pour définir les paramètres invités des groupes Microsoft 365

1. Dans le Centre d’administration Microsoft 365, dans le volet de navigation gauche, développez **Paramètres**.
2. Cliquez sur **Paramètres de l’organisation**.
3. Dans la liste, cliquez sur **Groupes Microsoft 365**.
4. Assurez-vous que les cases à cocher **Permettre aux propriétaires de groupe d’ajouter des personnes externes à votre organisation à des groupes Microsoft 365 en tant qu'invités** et **Permettre aux membres du groupe invités d’accéder au contenu du groupe** sont cochées.
5. Si vous avez effectué des modifications, cliquez sur **Enregistrer**.

## <a name="sharepoint-organization-level-sharing-settings"></a>SharePoint de partage au niveau de l’organisation

Pour que les invités ont accès à SharePoint sites web, les paramètres SharePoint de partage au niveau de l’organisation doivent autoriser le partage avec des invités.

Les paramètres au niveau de l’organisation déterminent les paramètres qui seront disponibles pour les sites individuels. Les paramètres de site ne peuvent pas être plus permissifs que les paramètres au niveau de l’organisation.

Si vous souhaitez autoriser le partage de fichiers et de dossiers non authentifiés, choisissez **Tout le monde.** Si vous souhaitez vous assurer que toutes les personnes extérieures à votre organisation doivent s’authentifier, choisissez Invités nouveaux **et existants.** Choisissez le paramètre le plus permissif qui sera nécessaire pour n’importe quel site de votre organisation.

![Capture d’écran des paramètres de partage SharePoint au niveau de l’organisation](../media/sharepoint-organization-external-sharing-controls.png)


Pour définir les paramètres de partage SharePoint au niveau de l’organisation

1. Dans le Centre d’administration Microsoft 365, dans le volet de navigation gauche, sous **Centres d’administration**, cliquez sur **SharePoint**.
2. Dans le SharePoint d’administration, dans le volet de navigation de gauche, sous **Stratégies,** cliquez sur **Partage.**
3. Assurez-vous que le partage externe pour SharePoint est **Tout le monde** ou **Invités nouveaux et existants**.
4. Si vous avez effectué des modifications, cliquez sur **Enregistrer**.

## <a name="create-a-site"></a>Créer un site

L’étape suivante consiste à créer le site que vous prévoyez d’utiliser pour collaborer avec des invités.

Pour créer un site
1. Dans le Centre d’administration SharePoint, sous **Sites**, cliquez sur **Sites actifs**.
2. Cliquez sur **Créer**.
3. Cliquez **sur Site d’équipe.**
4. Tapez un nom de site et entrez un nom pour le propriétaire du groupe (propriétaire du site).
5. Sous **Paramètres avancés,** choisissez si vous souhaitez que ce site soit public ou privé.
6. Cliquez sur **Suivant**.
7. Cliquez sur **Terminer**.

Nous inviterons des utilisateurs plus tard. Ensuite, il est important de vérifier les paramètres de partage au niveau du site pour ce site.

## <a name="sharepoint-site-level-sharing-settings"></a>Paramètres de SharePoint au niveau du site

Vérifiez les paramètres de partage au niveau du site pour vous assurer qu’ils autorisent le type d’accès que vous souhaitez pour ce site. Par exemple, si vous définissez les paramètres au niveau de l’organisation sur Tout le **monde,** mais que vous souhaitez que tous les invités s’authentifier pour ce site, assurez-vous que les paramètres de partage au niveau du site sont les invités nouveaux et existants. 

Notez que le site ne peut pas être partagé avec des personnes non authentifiés **(paramètre** Tout le monde), mais que des fichiers et dossiers individuels le peuvent.

Vous pouvez également utiliser des [étiquettes de sensibilité pour contrôler les paramètres](../compliance/sensitivity-labels-teams-groups-sites.md)de partage externe pour SharePoint sites.

![Capture d’écran des paramètres de partage externe de site SharePoint](../media/sharepoint-site-external-sharing-settings.png)

Pour définir les paramètres au niveau du site
1. Dans le centre d’administration SharePoint, dans le volet de navigation de gauche, développez **Sites** et cliquez sur **Sites actifs**.
2. Sélectionnez le site que vous souhaitez partager.
3. Cliquez sur ..., puis sur **Partage.**
4. Assurez-vous que le partage est paramétré sur **Tout le monde** ou **Invités nouveaux et existants**.
5. Si vous avez effectué des modifications, cliquez sur **Enregistrer**.

## <a name="invite-users"></a>Inviter des utilisateurs

Les paramètres de partage d’invités sont désormais configurés, afin que vous pouvez commencer à ajouter des utilisateurs internes et des invités à votre site. L’accès au site est contrôlé par le groupe Microsoft 365 associé, donc nous y ajouterons des utilisateurs.

Pour inviter des utilisateurs internes à un groupe
1. Accédez au site où vous souhaitez ajouter des utilisateurs.
2. Cliquez **sur Lien** Membres dans le coin supérieur droit qui indique le nombre de membres.
3. Cliquez sur **Ajouter des membres**.
4. Tapez les noms ou adresses e-mail des utilisateurs que vous souhaitez inviter sur le site, puis cliquez sur **Enregistrer**.

Les invités ne peuvent pas être ajoutés à partir du site. Vous devez les ajouter à l’aide Outlook sur le web. Par conséquent, comme condition préalable pour ajouter et inviter des invités à un groupe, cliquez sur l’URL du site dans la colonne **URL**  pour accéder à la page spécifique au site. Dans cette page, cliquez sur **l’icône du lanceur** d’applications et **sélectionnez Outlook**. Il s’agit de l’écran à partir duquel vous pouvez inviter des invités dans un groupe, pour lequel la procédure est décrite ci-dessous.

Pour inviter des invités à un groupe
1. Sous **Groupes,** cliquez sur le groupe auquel vous souhaitez inviter des invités.
2. Ouvrez la carte de visite du groupe, cliquez sur **Le** lien Membres dans le coin supérieur droit (lien qui indique le nombre de membres).
3. cliquez **sur Ajouter des membres.**
4. Tapez les adresses de messagerie des invités que vous souhaitez inviter, puis cliquez sur **Ajouter.**
5. Cliquez sur **Fermer**.
Notez que vous devez cliquer sur **Fermer** uniquement si vous n’êtes pas le propriétaire du groupe et, par conséquent, vous n’êtes pas autorisé à ajouter l’invité au groupe. Dans ce cas, la demande d’ajout de l’invité au groupe est transférée au propriétaire du groupe pour approbation.

## <a name="see-also"></a>Voir aussi

[Meilleures pratiques relatives au partage de fichiers et de dossiers avec des utilisateurs non authentifiés](best-practices-anonymous-sharing.md)

[Limiter l’exposition accidentelle aux fichiers lors du partage avec des invités](share-limit-accidental-exposure.md)

[Créer un environnement de partage sécurisé avec des invités](create-secure-guest-sharing-environment.md)

[Créer un extranet B2B avec des invités gérés](b2b-extranet.md)

[Intégration de SharePoint et de OneDrive à Azure AD B2B](/sharepoint/sharepoint-azureb2b-integration-preview)