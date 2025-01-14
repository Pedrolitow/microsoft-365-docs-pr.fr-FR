---
title: Meilleures pratiques pour le partage non authentifié
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection:
- highpri
- SPO_Content
- M365-collaboration
- m365solution-3tiersprotection
- m365solution-securecollab
- m365initiative-externalcollab
ms.custom:
- seo-marvel-apr2020
- admindeeplinkSPO
ms.localizationpriority: high
f1.keywords: NOCSH
recommendations: false
description: Dans cet article, vous allez découvrir les meilleures pratiques relatives au partage de fichiers et de dossiers avec des utilisateurs non authentifiés.
ms.openlocfilehash: 289255c9a572b660b276c22b2df996e65d743944
ms.sourcegitcommit: fce27da5140691b013a6f7c0ea9c88b4ea4b7c10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2022
ms.locfileid: "67983451"
---
# <a name="best-practices-for-sharing-files-and-folders-with-unauthenticated-users"></a>Meilleures pratiques relatives au partage de fichiers et de dossiers avec des utilisateurs non authentifiés

Le partage non authentifié (liens *Tout le monde*) est pratique et utile dans différents scénarios. Les liens *Tout le monde* sont la méthode la plus simple pour partager : les personnes peuvent ouvrir le lien sans authentification et sont libres de le transmettre à d’autres personnes.

Usually, not all content in an organization is appropriate for unauthenticated sharing. This article covers the options available to help you create an environment where your users can use unauthenticated sharing of files and folders, but where there are safeguards in place to help protect your organization's content.

> [!NOTE]
> Pour que le partage non authentifié puisse fonctionner, vous devez l’activer pour votre organisation et pour le site ou l’équipe qui sera concerné. Pour plus d’informations sur le scénario que vous souhaitez mettre en place, voir [Collaborer avec des personnes extérieures à votre organisation](collaborate-with-people-outside-your-organization.md).

## <a name="set-an-expiration-date-for-anyone-links"></a>Définir une date d’expiration pour les liens Tout le monde

Les fichiers sont souvent stockés dans des sites, des groupes et des équipes pendant une période prolongée. Il peut arriver qu’une stratégie de rétention des données nécessite la conservation des fichiers pendant plusieurs années. Si ces fichiers sont partagés avec des personnes non authentifiées, cela peut entraîner un accès inattendu et des modifications aux fichiers dans le futur. Pour atténuer cette possibilité, vous pouvez configurer un délai d’expiration pour les liens *Tout le monde*.

Une fois qu' un lien *Tout le monde* arrive à expiration, il ne peut plus être utilisé pour accéder au contenu.

Pour définir une date d’expiration pour les liens Tout le monde dans l’organisation

1. Ouvrez le Centre d’administration SharePoint, développez **Stratégies**, puis sélectionnez <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**Partage**</a>.
1. Sous **Sélectionnez les options d’expiration et d’autorisations pour tous les liens**, sélectionnez la case à cocher **Ces liens doivent expirer dans ce nombre de jours**.</br>
   ![Capture d’écran des paramètres d’expiration du lien Tout le monde au niveau de l’organisation dans Microsoft Office SharePoint Online.](../media/sharepoint-organization-anyone-link-expiration.png)
1. Tapez un nombre de jours dans la zone, puis cliquez sur **Enregistrer**.

Si vous modifiez l’heure d’expiration, les liens existants conservent leur heure d’expiration actuelle si le nouveau paramètre est plus long ou sont mis à jour vers le nouveau paramètre si le nouveau paramètre est plus court.

Pour définir une date d’expiration pour les liens Tout le monde sur un site spécifique

1. Ouvrez le Centre d’administration SharePoint, développez **Sites**, puis sélectionnez <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Sites actifs**</a>.
1. Sélectionnez le site à modifier, puis sélectionnez **Partage**.
1. Sous **Paramètres avancés pour les liens Tout le monde**, sous **Expiration des liens Tout le monde**, désactivez la case à cocher **Identique au paramètre de niveau organisation** .</br>
   ![Capture d’écran des paramètres d’expiration du lien Tout le monde au niveau du site dans Microsoft Office SharePoint Online.](../media/sharepoint-organization-anyone-link-expiration-site.png)
1. Sélectionnez l’option **Ces liens doivent expirer dans ce nombre de jours** , puis tapez un nombre de jours dans la zone.
1. Sélectionnez **Enregistrer**.

Notez qu’une fois qu' un lien *Tout le monde* arrive à expiration, le fichier ou dossier peut être repartagé avec un nouveau lien *Tout le monde*.

Vous pouvez définir l'expiration du lien *Tout le monde* pour un site spécifique à l’aide de [Set-SPOSite](/powershell/module/sharepoint-online/set-sposite). 

```powershell
Set-SPOSite -Identity https://contoso.sharepoint.com/sites/marketing -OverrideTenantAnonymousLinkExpirationPolicy $true -AnonymousLinkExpirationInDays 15
```

## <a name="set-link-permissions"></a>Définir les autorisations de lien

By default, *Anyone* links for a file allow people to edit the file, and *Anyone* links for a folder allow people to edit and view files, and upload new files to the folder. You can change these permissions for files and for folders independently to view-only.

Si vous voulez autoriser le partage non authentifié, mais que vous craignez que des personnes non authentifiées modifient le contenu de votre organisation, vous pouvez définir les autorisations des fichiers et des dossiers sur **Vue**.

Pour définir des autorisations pour les liens Tout le monde dans l’organisation

1. Ouvrez le Centre d’administration SharePoint, puis sélectionnez <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**Partage**</a>.
1. Sous **Paramètres avancés pour les liens Tout le monde**, sélectionnez les autorisations d’accès aux fichiers et dossiers que vous souhaitez.</br>
   ![Capture d’écran des paramètres d’autorisation du lien Tout le monde au niveau de l’organisation dans Microsoft Office SharePoint Online.](../media/sharepoint-organization-anyone-link-permissions.png)

Lorsque les liens *Tout le monde* sont paramétrés sur **Vue**, les utilisateurs peuvent encore partager des fichiers et des dossiers avec des invités et leur octroyer des autorisations de modification à l’aide des liens *Personnes spécifiques*. Ces liens nécessitent que les personnes extérieures à votre organisation s’authentifient en tant qu’invités. Vous pouvez effectuer le suivi et l’audit de l’activité des invités sur les fichiers et dossiers partagés avec ces liens.

## <a name="set-default-link-type-to-only-work-for-people-in-your-organization"></a>Définir le type de lien par défaut de sorte qu’il fonctionne uniquement pour les membres de votre organisation

Lorsque le partage *Tout le monde* est activé pour votre organisation, le lien de partage par défaut est normalement réglé sur **Tout le monde**. Bien que cette fonctionnalité soit commode pour les utilisateurs, elle peut augmenter le risque d’un partage non authentifié involontaire. Si un utilisateur oublie de modifier le type de lien lors du partage d’un document sensible, il peut créer sans le vouloir un lien de partage qui ne nécessite pas d’authentification.

Vous pouvez réduire ce risque en modifiant le paramètre de lien par défaut en un lien qui fonctionne uniquement pour les personnes internes à votre organisation. Les utilisateurs qui souhaitent partager des documents avec des personnes non authentifiées doivent ensuite sélectionner cette option.

Pour définir le lien de partage de fichier et de dossier par défaut pour l’organisation :

1. Ouvrez le Centre d’administration SharePoint, puis sélectionnez <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**Partage**</a>.
1. Sous **Liens de fichier et de dossier**, sélectionnez **Uniquement les membres de votre organisation**.

   ![Capture d’écran du paramètre de type de lien par défaut de Microsoft Office SharePoint Online.](../media/sharepoint-default-sharing-link-company-link.png)

1. Sélectionnez **Enregistrer**.

Pour définir le lien de partage de fichier et de dossier par défaut pour un site spécifique :

1. Ouvrez le Centre d’administration SharePoint, développez **Sites**, puis sélectionnez <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Sites actifs**</a>.
1. Sélectionnez le site à modifier, puis sélectionnez **Partage**.
1. Sous **Type de lien de partage par défaut**, désactivez la case à cocher **Identique au paramètre de niveau organisation**.

   ![Capture d’écran des paramètres de type de lien par défaut au niveau du site de Microsoft Office SharePoint Online.](../media/sharepoint-organization-anyone-link-permissions-site.png)

1. Sélectionnez l’option **Uniquement les membres de votre organisation**, puis sélectionnez **Enregistrer**.

## <a name="prevent-unauthenticated-sharing-of-sensitive-content"></a>Empêcher le partage non authentifié de contenu sensible

Vous pouvez utiliser la [Protection contre la perte de données (DLP) Microsoft Purview](../compliance/dlp-learn-about-dlp.md) pour empêcher le partage non authentifié de contenu sensible. La protection contre la perte de données peut prendre des mesures basées sur l’étiquette de confidentialité, l’étiquette de rétention ou les informations sensibles d’un fichier proprement dit.

Création d’une stratégie DLP :

1. Dans le Centre de conformité Microsoft Purview, accédez à la [Page de protection contre la perte de données](https://compliance.microsoft.com/datalossprevention).
2. Cliquez sur la stratégie **Créer**.
3. Sélectionnez **Personnaliser**, puis cliquez sur **Suivant**.
4. Tapez un nom pour la stratégie, puis cliquez sur **Suivant**.
5. Dans la page **Emplacements pour appliquer la stratégie**, désactivez tous les paramètres, sauf **Sites SharePoint** et **Comptes OneDrive**, puis cliquez sur **Suivant**.
6. Sur la page **Définir les paramètres de stratégie**, cliquez sur **Suivant**.
7. Sur la page **Personnaliser les règles avancées de protection contre la perte de données** , cliquez sur **Créer une règle**, puis tapez un nom pour la règle.
8. Sous **Conditions**, cliquez sur **Ajouter une condition**, puis sélectionnez **Le contenu contient**.
9. Cliquez sur **Ajouter**, puis choisissez le type d’informations pour lesquelles vous souhaitez empêcher le partage non authentifié.

   ![Capture d’écran des options de conditions, types d’informations sensibles, étiquettes de confidentialité et étiquettes de rétention.](../media/limit-accidental-exposure-dlp-conditions.png)

10. Sous **Actions** cliquez sur **Ajouter une action**, puis sélectionnez **Restreindre l’accès ou chiffrer le contenu dans des emplacements Microsoft 365**.
11. Activez la case à cocher **Restreindre l’accès ou chiffrer le contenu dans des emplacements Microsoft 365** , puis sélectionnez l’option **Uniquement les personnes autorisées à accéder au contenu via les options « Tout le monde avec lien »**.

      ![Capture d’écran des options d’action de règle de protection contre la perte de données.](../media/limit-accidental-exposure-dlp-anyone-links.png)

12. Cliquez sur **Enregistrer**, puis sur **Suivant**.
13. Sélectionnez vos options de test, puis cliquez sur **Suivant**.
14. Cliquez sur **Envoyer**, puis sur **Terminé**.

## <a name="protect-against-malicious-files"></a>Se protéger contre les fichiers malveillants

Lorsque vous autorisez des utilisateurs anonymes à télécharger des fichiers, vous accroissez le risque de charger un fichier malveillant. Dans les organisations disposant de licences Microsoft Defender pour Office 365 Plan 1 ou Plan 2 (par exemple, dans Microsoft 365 E5 ou en tant que module complémentaire), vous pouvez utiliser la fonctionnalité *Pièces jointes fiables* pour faire détoner les fichiers chargés dans un environnement virtuel en mode bac à sable et mettre en quarantaine les fichiers qui sont jugés dangereux.

Pour obtenir des instructions, voir [Activer les pièces jointes fiables pour SharePoint, OneDrive et Microsoft Teams](../security/office-365-security/turn-on-mdo-for-spo-odb-and-teams.md).

Si vous avez des licences Microsoft 365 A5 ou E5 Sécurité, vous pouvez également activer (et utiliser) la fonctionnalité *Documents sécurisés*. Pour plus d’informations, consultez [Documents sécurisés dans Microsoft 365 A5 ou E5 Sécurité](../security/office-365-security/safe-docs.md).

## <a name="add-copyright-information-to-your-files"></a>Ajouter des informations de copyright à vos fichiers

Si vous utilisez des étiquettes de confidentialité dans le centre d’administration de la conformité Microsoft Purview, vous pouvez configurer vos étiquettes pour ajouter automatiquement un filigrane, un en-tête ou un pied de page aux documents Office de votre organisation. De cette façon, vous pouvez vous assurer que les fichiers partagés contiennent des informations de copyright ou de propriété.

Pour ajouter un pied de page à un fichier étiqueté

1. Ouvrez le [Centre d’administration Microsoft Purview](https://compliance.microsoft.com).
2. Dans le volet de navigation gauche, sous **Solutions**, cliquez sur **Protection des informations**.
3. Cliquez sur l’étiquette à laquelle vous voulez ajouter un pied de page, puis sur **Modifier l'étiquette**.
4. Cliquez sur **Suivant** pour atteindre l’onglet **Marquage du contenu**, puis réglez l’option marquage du contenu sur **Activé**.
5. Cochez la case correspondant au type de texte à ajouter, puis cliquez sur **Personnaliser le texte**.
6. Tapez le texte que vous souhaitez ajouter à vos documents, sélectionnez les options de texte souhaitées, puis cliquez sur **Enregistrer**.</br>
   ![Capture d’écran des paramètres de marquage de contenu pour une étiquette de confidentialité.](../media/content-marking-for-anonymous-sharing.png)
7. Cliquez sur **Suivant** pour atteindre la fin de l’Assistant, puis cliquez sur **Enregistrer l’étiquette**.

Avec l’option marquage de contenu activée pour l’étiquette, le texte spécifié est ajouté aux documents Office lorsqu’un utilisateur applique cette étiquette.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble des étiquettes de confidentialité](/Office365/SecurityCompliance/sensitivity-labels)

[Limiter l’exposition accidentelle aux fichiers lors du partage avec des invités](share-limit-accidental-exposure.md)

[Créer un environnement de partage sécurisé avec des invités](create-secure-guest-sharing-environment.md)
