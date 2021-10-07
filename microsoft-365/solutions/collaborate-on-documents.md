---
title: Collaborer avec des invités sur un document
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
ms.localizationpriority: medium
f1.keywords: NOCSH
recommendations: false
description: Dans cet article, vous allez découvrir comment collaborer avec des invités sur un document SharePoint et OneDrive.
ms.openlocfilehash: e51ec7e9695c564b2994089f0a827ca7ea4b67c6
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60158957"
---
# <a name="collaborate-with-guests-on-a-document"></a>Collaborer avec des invités sur un document

Si vous devez collaborer avec des personnes extérieures à votre organisation sur des documents dans SharePoint ou OneDrive, vous pouvez leur envoyer un lien de partage vers le document. Dans cet article, nous allons passer en revue les étapes de configuration Microsoft 365 nécessaires pour configurer des liens de partage pour SharePoint et OneDrive pour les besoins de votre organisation.

## <a name="video-demonstration"></a>Démonstration vidéo

Cette vidéo décrit les étapes de configuration décrites dans ce document.</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE450Vt?autoplay=false]

## <a name="azure-external-collaboration-settings"></a>Paramètres de collaboration externe Azure

Le partage dans Microsoft 365 est régi à son niveau le plus élevé par les [paramètres de collaboration externe B2B dans Azure Active Directory](/azure/active-directory/external-identities/delegate-invitations). Si le partage d’invités est désactivé ou restreint dans Azure AD, ce paramètre remplace tous les paramètres de partage que vous configurez dans Microsoft 365.

Vérifiez les paramètres de collaboration externe B2B pour vous assurer que le partage avec des invités n’est pas bloqué.

![Capture d’écran de la page des paramètres de relations organisationnelles d’Azure Active Directory.](../media/azure-ad-organizational-relationships-settings.png)

Pour définir les paramètres de collaboration externe

1. Connectez-vous à Azure Active Directory sur [https://aad.portal.azure.com](https://aad.portal.azure.com).
2. Dans le volet de navigation gauche, cliquez sur **Azure Active Directory**.
3. Cliquez sur **Identités externes**.
4. Dans l’écran **Prise en main**, dans le volet de navigation gauche, cliquez sur **Paramètres de collaboration externe**.
5. Assurez-vous que **Les administrateurs et les utilisateurs membres du rôle Inviteur d’invités peuvent envoyer des invitations** et **Les membres peuvent inviter** sont tous deux définis sur **Oui**.
6. Si vous avez effectué des modifications, cliquez sur **Enregistrer**.

Notez les paramètres dans la section **Restrictions de collaboration**. Assurez-vous que les domaines des invités avec qui vous voulez collaborer ne sont pas bloqués.

Si vous travaillez avec des invités de plusieurs organisations, vous souhaiterez peut-être restreindre leur capacité à accéder aux données d’annuaire. Cela les empêche de voir qui d’autre est invité dans l’annuaire. Pour ce faire, sous **Restrictions d’accès des utilisateurs invités**, sélectionnez **Les utilisateurs invités ont un accès limité aux propriétés et à l’appartenance aux paramètres des objets d’annuaire** ou **L’accès des utilisateurs invités est limité aux propriétés et à l’appartenance à leurs propres objets d’annuaire**.

## <a name="sharepoint-organization-level-sharing-settings"></a>SharePoint de partage au niveau de l’organisation

Pour que les personnes extérieures à votre organisation ont accès à un document en SharePoint ou OneDrive, les paramètres de partage au niveau de l’organisation SharePoint et OneDrive doivent autoriser le partage avec des personnes extérieures à votre organisation.

Les paramètres au niveau de l’SharePoint déterminent les paramètres qui seront disponibles pour les sites SharePoint individuels. Les paramètres de site ne peuvent pas être plus permissifs que les paramètres au niveau de l’organisation. Le paramètre au niveau de l’OneDrive détermine le niveau de partage qui sera disponible dans les bibliothèques OneDrive utilisateurs.

Pour SharePoint et OneDrive, si vous souhaitez autoriser le partage de fichiers et de dossiers non authentifiés, choisissez Tout le **monde.** Si vous souhaitez vous assurer que les personnes extérieures à votre organisation doivent s’authentifier, choisissez Invités nouveaux **et existants.** *Tout* le monde est le moyen le plus simple de partager : les personnes extérieures à votre organisation peuvent ouvrir le lien sans authentification et sont libres de le transmettre à d’autres personnes.

Pour SharePoint, choisissez le paramètre le plus permissif qui sera nécessaire à n’importe quel site de votre organisation.

![Capture d’écran des paramètres de partage SharePoint au niveau de l’organisation.](../media/sharepoint-organization-external-sharing-controls.png)


Pour définir les paramètres de partage SharePoint au niveau de l’organisation

1. Dans le Centre d’administration Microsoft 365, dans le volet de navigation gauche, sous **Centres d’administration**, cliquez sur **SharePoint**.
2. Dans le SharePoint d’administration, dans le volet de navigation de gauche, sous **Stratégies,** cliquez sur **Partage.**
3. Assurez-vous que le partage externe pour SharePoint ou OneDrive est définie sur **Tout** le monde ou Nouveau **et les invités existants.** (Notez que le paramètre OneDrive ne peut pas être plus permissif que le SharePoint paramètre.)
4. Si vous avez effectué des modifications, cliquez sur **Enregistrer**.

## <a name="sharepoint-organization-level-default-link-settings"></a>Paramètres de liaison par défaut au niveau de l’organisation SharePoint

Les paramètres par défaut de liaison de fichier et de dossier déterminent l’option de lien qui sera affichée par défaut aux utilisateurs lorsqu’ils partagent un fichier ou un dossier. Si vous le souhaitez, les utilisateurs peuvent modifier le type de lien vers l’une des autres options avant le partage.

N’oubliez pas que ce paramètre affecte SharePoint sites de votre organisation, ainsi que les OneDrive.

Choisissez un lien parmi les types suivants, qui est ensuite sélectionné par défaut lorsque les utilisateurs partagent des fichiers et des dossiers :

- **Toute personne partageant le lien** : choisissez cette option si vous prévoyez d’avoir un grand nombre de partages de fichiers et de dossiers non authentifiés. Si vous souhaitez autoriser les liens à *Tout le monde* mais que vous craignez un partage accidentel non authentifié, envisagez l'une des autres options comme valeur par défaut. Ce type de lien n’est disponible que si vous avez activé le partage **Tout le monde**.
- **Uniquement les personnes de votre organisation** : choisissez cette option si vous souhaitez que la plupart des partages de fichiers et de dossiers soient avec des personnes de votre organisation.
- **Personnes spécifiques** : envisagez cette option si vous prévoyez de partager beaucoup de fichiers et de dossiers avec vos invités. Ce type de lien fonctionne avec les invités et exige leur authentification.
 
![Capture d’écran des paramètres de partage de fichiers et dossiers au niveau de l’organisation dans SharePoint.](../media/sharepoint-organization-files-folders-sharing-settings.png)


Pour définir les paramètres SharePoint et OneDrive paramètres de lien par défaut au niveau de l’organisation

1. Accédez à la page Partage dans le Centre d’administration SharePoint.
2. Sous **Liens des fichiers et des dossiers**, sélectionnez le lien de partage par défaut que vous voulez utiliser.
3. Si vous avez effectué des modifications, cliquez sur **Enregistrer**.

Pour définir l’autorisation pour le lien de partage, sous **Choisir l’autorisation** sélectionnée par défaut pour le partage de liens.

1. Sélectionnez **Afficher** si vous ne souhaitez pas que les utilisateurs non authentifiés modifient les fichiers et dossiers.
2. Sélectionnez **Modifier** si vous souhaitez autoriser les utilisateurs non authentifiés à apporter des modifications aux fichiers et dossiers.

Notez que les deux options de prémission ci-dessus peuvent être appliquées non seulement pour les invités/utilisateurs externes, mais également pour les utilisateurs internes. L’option d’autorisation que vous choisissez est déterminée par la discrétion.

Pour définir des autorisations pour les liens qui autorisent le partage avec tout le monde

1. Sous ces **liens, vous pouvez accorder ces autorisations :** sous-volet, 
    1. À partir **de la** liste de listes de listes 
        - Sélectionnez **Afficher et modifier** si vous souhaitez autoriser les utilisateurs non authentifiés à apporter des modifications aux fichiers.
        - Sélectionnez **Afficher** si vous ne souhaitez pas que les utilisateurs non authentifiés modifient les fichiers.
    2. Dans la liste de listes de **dossiers,**
        - Sélectionnez **Afficher, modifier et charger** si vous souhaitez autoriser les utilisateurs non authentifiés à apporter des modifications aux dossiers.
        - Sélectionnez **Afficher** si vous ne souhaitez pas que les utilisateurs non authentifiés modifient les dossiers.

## <a name="sharepoint-site-level-sharing-settings"></a>Paramètres de SharePoint au niveau du site

Si vous partagez des fichiers et des dossiers situés dans un site SharePoint, vous devez également vérifier les paramètres de partage au niveau du site pour ce site.

![Capture d’écran des paramètres de partage externe de site SharePoint.](../media/sharepoint-site-external-sharing-settings.png)

Pour définir les paramètres au niveau du site

1. Dans le centre d’administration SharePoint, dans le volet de navigation de gauche, développez **Sites** et cliquez sur **Sites actifs**.
2. Sélectionnez le site sur lequel vous souhaitez partager des fichiers et des dossiers avec des invités.
3. Faites défiler vers la droite la ligne (dans laquelle le site sélectionné est présent) et cliquez n’importe où dans la **colonne de partage** externe.
4. Dans la page qui s’insérait, cliquez sur **l’onglet Stratégies.**
5. Sous le **volet de partage** externe, cliquez sur **Modifier.**
6. Assurez-vous que le partage est paramétré sur **Tout le monde** ou **Invités nouveaux et existants**.
7. Si vous avez effectué des modifications, cliquez sur **Enregistrer**.

## <a name="invite-users"></a>Inviter des utilisateurs

Les paramètres de partage d’invités sont désormais configurés ; afin que les utilisateurs peuvent désormais partager des fichiers et des dossiers avec des personnes extérieures à votre organisation. Pour [plus d OneDrive, voir](https://support.office.com/article/9fcc2f7d-de0c-4cec-93b0-a82024800c07) Partager des fichiers et des dossiers et Partager SharePoint fichiers ou [dossiers.](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c)

## <a name="see-also"></a>Voir aussi

[Meilleures pratiques relatives au partage de fichiers et de dossiers avec des utilisateurs non authentifiés](best-practices-anonymous-sharing.md)

[Limiter l’exposition accidentelle aux fichiers lors du partage avec des invités](share-limit-accidental-exposure.md)

[Intégration de SharePoint et de OneDrive à Azure AD B2B](/sharepoint/sharepoint-azureb2b-integration-preview)