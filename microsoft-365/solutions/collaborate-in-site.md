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
description: Découvrez les étapes de configuration de Microsoft 365 nécessaires pour configurer un site SharePoint en vue de la collaboration avec des invités.
ms.openlocfilehash: 6862fe715fe2f19b968b773bc6df6c70c207a44f
ms.sourcegitcommit: 47de4402174c263ae8d70c910ca068a7581d04ae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/12/2020
ms.locfileid: "49663523"
---
# <a name="collaborate-with-guests-in-a-site"></a>Collaborer avec des invités sur un site

Si vous avez besoin de collaborer avec des invités dans des documents, des données et des listes, vous pouvez utiliser un site SharePoint. Les sites SharePoint modernes sont connectés aux groupes Microsoft 365 et peuvent gérer l’appartenance à un site et fournir des outils de collaboration supplémentaires tels qu’une boîte aux lettres partagée et un calendrier.

Dans cet article, nous allons passer en revue les étapes de configuration de Microsoft 365 nécessaires pour configurer un site SharePoint en vue de la collaboration avec des invités.

## <a name="video-demonstration"></a>Démonstration vidéo

Cette vidéo présente les étapes de configuration décrites dans ce document.</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE44Llg?autoplay=false]

## <a name="azure-external-collaboration-settings"></a>Paramètres de collaboration externe Azure

Le partage dans Microsoft 365 est régi au niveau le plus élevé par les [paramètres de collaboration externe B2B dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/external-identities/delegate-invitations). Si le partage d’invités est désactivé ou restreint dans Azure AD, ce paramètre remplace tous les paramètres de partage que vous configurez dans Microsoft 365.

Vérifiez les paramètres de collaboration externe B2B pour vous assurer que le partage avec des invités n’est pas bloqué.

![Capture d’écran de la page des paramètres de collaboration externe Azure Active Directory](../media/azure-ad-organizational-relationships-settings.png)

Pour définir les paramètres de collaboration externe

1. Connectez-vous à Azure Active Directory à l’adresse [https://aad.portal.azure.com](https://aad.portal.azure.com) .
2. Dans le volet de navigation de gauche, cliquez sur **Azure Active Directory**.
3. Cliquez sur **identités externes**.
4. Sur l’écran de **prise en main** , dans le volet de navigation de gauche, cliquez sur **paramètres de collaboration externe**.
5. Assurez-vous que les **administrateurs et les utilisateurs du rôle d’invité invité peuvent inviter** et que les **membres peuvent inviter** sont tous deux la valeur **Oui**.
6. Si vous avez effectué des modifications, cliquez sur **Enregistrer**.

Notez les paramètres dans la section **restrictions de collaboration** . Assurez-vous que les domaines des invités avec lesquels vous souhaitez collaborer ne sont pas bloqués.

Si vous travaillez avec des invités de plusieurs organisations, vous souhaiterez peut-être limiter leur capacité à accéder aux données d’annuaire. Cela les empêchera de voir qui d’autre est un invité dans l’annuaire. Pour ce faire, sous **restrictions d’accès des utilisateurs invités**, sélectionnez **les utilisateurs invités ont un accès limité aux propriétés et l’appartenance aux paramètres d’objets d’annuaire** ou **l’accès des utilisateurs invités est limité aux propriétés et aux appartenances de leurs propres objets d’annuaire**.

## <a name="microsoft-365-groups-guest-settings"></a>Paramètres invités des groupes Microsoft 365

Les sites SharePoint modernes utilisent les groupes Microsoft 365 pour contrôler l’accès au site. Les paramètres invités des groupes Microsoft 365 doivent être activés pour que l’accès invité dans les sites SharePoint fonctionne.

![Capture d’écran des paramètres d’invité des Groupes Microsoft 365 dans le Centre d’administration Microsoft 365](../media/office-365-groups-guest-settings.png)

Pour définir les paramètres invités des groupes Microsoft 365

1. Dans le centre d’administration Microsoft 365, dans le volet de navigation de gauche, développez **paramètres**.
2. Cliquez sur paramètres de l' **organisation**.
3. Dans la liste, cliquez sur **groupes Microsoft 365**.
4. Assurez-vous que les **propriétaires de groupe Let ajoutent des personnes extérieures à votre organisation aux groupes Microsoft 365 en tant qu’invités** et laissez les cases à cocher le **contenu des membres du groupe invité** sont tous deux activés.
5. Si vous avez apporté des modifications, cliquez sur **enregistrer les modifications**.

## <a name="sharepoint-organization-level-sharing-settings"></a>Paramètres de partage au niveau de l’organisation SharePoint

Pour que les invités aient accès aux sites SharePoint, les paramètres de partage au niveau de l’organisation SharePoint doivent autoriser le partage avec des invités.

Les paramètres au niveau de l’organisation déterminent les paramètres qui seront disponibles pour des sites individuels. Les paramètres de site ne peuvent pas être plus permissants que les paramètres au niveau de l’organisation.

Si vous souhaitez autoriser le partage de fichiers et de dossiers non authentifié, sélectionnez **tout le monde**. Si vous souhaitez vous assurer que toutes les personnes extérieures à votre organisation doivent s’authentifier, choisissez **nouveau et invités existants**. Choisissez le paramètre le plus permissif qui sera nécessaire pour tous les sites de votre organisation.

![Capture d’écran des paramètres de partage SharePoint au niveau de l’organisation](../media/sharepoint-organization-external-sharing-controls.png)


Pour définir les paramètres de partage au niveau de l’organisation SharePoint

1. Dans le centre d’administration 365 de Microsoft, dans le volet de navigation de gauche, sous **centres d’administration**, cliquez sur **SharePoint**.
2. Dans le centre d’administration SharePoint, dans le volet de navigation de gauche, sous **stratégies**, cliquez sur **partage**.
3. Assurez-vous que le partage externe pour SharePoint est défini sur **tout le monde** ou sur **des invités nouveaux et existants**.
4. Si vous avez effectué des modifications, cliquez sur **Enregistrer**.

## <a name="create-a-site"></a>Créer un site

L’étape suivante consiste à créer le site que vous envisagez d’utiliser pour collaborer avec des invités.

Pour créer un site
1. Dans le Centre d’administration SharePoint, sous **Sites**, cliquez sur **Sites actifs**.
2. Cliquez sur **Créer**.
3. Cliquez sur **site d’équipe**.
4. Tapez un nom de site et entrez un nom pour le propriétaire du groupe (propriétaire du site).
5. Sous **Paramètres avancés**, choisissez si vous souhaitez que ce site soit public ou privé.
6. Cliquez sur **Suivant**.
7. Cliquez sur **Terminer**.

Nous allons inviter les utilisateurs ultérieurement. Ensuite, il est important de vérifier les paramètres de partage au niveau du site pour ce site.

## <a name="sharepoint-site-level-sharing-settings"></a>Paramètres de partage au niveau du site SharePoint

Vérifiez les paramètres de partage au niveau du site pour vous assurer qu’ils autorisent le type d’accès souhaité pour ce site. Par exemple, si vous définissez les paramètres au niveau de l’organisation sur tous les **utilisateurs**, mais que vous souhaitez que tous les invités s’authentifient pour ce site, assurez-vous que les paramètres de partage au niveau du site sont définis sur **nouveaux et invités existants**.

Notez que le site ne peut pas être partagé avec des personnes non authentifiées (paramètre **tout le monde** ), mais avec des fichiers et dossiers individuels.

Vous pouvez également utiliser [les étiquettes de confidentialité pour contrôler les paramètres de partage externe pour les sites SharePoint](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-teams-groups-sites).

![Capture d’écran des paramètres de partage externe de site SharePoint](../media/sharepoint-site-external-sharing-settings.png)

Pour définir les paramètres de partage au niveau du site
1. Dans le centre d’administration SharePoint, dans le volet de navigation de gauche, développez **Sites** et cliquez sur **Sites actifs**.
2. Sélectionnez le site que vous souhaitez partager.
3. Cliquez sur..., puis sur **partage**.
4. Assurez-vous que le partage est défini sur **tout le monde** ou sur **des invités nouveaux et existants**.
5. Si vous avez effectué des modifications, cliquez sur **Enregistrer**.

## <a name="invite-users"></a>Inviter des utilisateurs

Les paramètres de partage des invités sont désormais configurés, de sorte que vous pouvez commencer à ajouter des utilisateurs et des invités internes à votre site. L’accès au site est contrôlé par le biais du groupe Microsoft 365 associé, c’est pourquoi nous allons y ajouter des utilisateurs.

Pour inviter des utilisateurs internes à un groupe
1. Accédez au site où vous souhaitez ajouter des utilisateurs.
2. Cliquez sur le lien **membres** dans le coin supérieur droit, qui indique le nombre de membres.
3. Cliquez sur **Ajouter des membres**.
4. Tapez les noms ou les adresses de messagerie des utilisateurs que vous souhaitez inviter sur le site, puis cliquez sur **Enregistrer**.

Les invités ne peuvent pas être ajoutés à partir du site. Vous devez les ajouter à l’aide d’Outlook sur le Web. Par conséquent, en tant que prérequis pour ajouter et inviter des invités à un groupe, cliquez sur l’URL du site dans la colonne **URL**  pour accéder à la page propre au site. À partir de cette page, cliquez sur l’icône du **lanceur d’applications** et sélectionnez **Outlook**. Il s’agit de l’écran à partir duquel vous pouvez inviter des invités à un groupe, pour lequel la procédure est décrite ci-dessous.

Pour inviter des invités à un groupe
1. Sous **groupes**, cliquez sur le groupe auquel vous souhaitez inviter des invités.
2. Ouvrez la carte de visite de groupe, cliquez sur le lien **membres** dans le coin supérieur droit (le lien qui indique le nombre de membres).
3. Cliquez sur **Ajouter des membres**.
4. Tapez les adresses de messagerie des invités que vous souhaitez inviter, puis cliquez sur **Ajouter**.
5. Cliquez sur **Fermer**.
Notez que vous devez cliquer sur **Fermer** uniquement si vous n’êtes pas le propriétaire du groupe et, par conséquent, si vous n’êtes pas autorisé à ajouter l’invité dans le groupe. Dans ce cas, la demande d’ajout de l’invité au groupe est transférée au propriétaire du groupe pour approbation.

## <a name="see-also"></a>Voir aussi

[Meilleures pratiques relatives au partage de fichiers et de dossiers avec des utilisateurs non authentifiés](best-practices-anonymous-sharing.md)

[Limiter l’exposition accidentelle aux fichiers lors du partage avec des invités](share-limit-accidental-exposure.md)

[Créer un environnement de partage sécurisé avec des invités](create-secure-guest-sharing-environment.md)

[Créer un extranet B2B avec des invités gérés](b2b-extranet.md)

[Intégration de SharePoint et de OneDrive avec Azure AD B2B](https://docs.microsoft.com/sharepoint/sharepoint-azureb2b-integration-preview)
