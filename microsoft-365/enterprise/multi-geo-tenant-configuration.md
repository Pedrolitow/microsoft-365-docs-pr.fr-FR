---
title: Configuration de client multigéographique dans Microsoft 365
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection:
- SPO_Content
- Strat_SP_gtc
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
localization_priority: Normal
description: Dans cet article, découvrez l’ajout d’emplacements satellites et la configuration de votre client pour Microsoft 365 Multi-Geo.
ms.openlocfilehash: c60e590f7eddc7f9e03c4754867600a39879cc49
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58576019"
---
# <a name="microsoft-365-multi-geo-tenant-configuration"></a>Configuration de client multigéographique dans Microsoft 365

Avant de configurer votre client pour Microsoft 365 Multi-Geo, assurez-vous que vous disposez de la lecture [Plan pour Microsoft 365 Multi-Geo](plan-for-multi-geo.md). Pour suivre la procédure décrite dans cet article, vous devez posséder la liste des emplacements géographiques que vous voulez activer en tant qu’emplacements satellites, ainsi que la liste des utilisateurs de test que vous désirez approvisionner à ces emplacements.

## <a name="add-the-multi-geo-capabilities-in-your-microsoft-365-plan-to-your-tenant"></a>Ajouter les fonctionnalités multigéographiques de votre plan Microsoft 365 à votre client

Pour utiliser Microsoft 365 Multi-Geo, vous avez besoin du plan _Fonctionnalités multigéographiques dans Microsoft 365_. Travaillez avec votre équipe des comptes pour ajouter cette offre à votre client. Votre équipe des comptes vous mettra en contact avec le spécialiste en gestion des licences approprié et votre client sera configuré.

Notez que le plan des _fonctionnalités multigéographiques dans Microsoft 365_ est un plan de service au niveau utilisateur. Vous avez besoin d’une licence pour chaque utilisateur que vous souhaitez héberger dans un emplacement satellite. Vous pouvez ajouter des licences supplémentaires au fur et à mesure que vous ajoutez des utilisateurs dans des emplacements satellites.

Une fois que votre client a été approvisionné avec l’offre _Fonctionnalités multigéographiques dans Microsoft 365_, l’onglet **Emplacements géographiques** est disponible dans les centres d’administration OneDrive et SharePoint.

## <a name="add-satellite-locations-to-your-tenant"></a>Ajouter des emplacements satellites à votre client

Vous devez ajouter un emplacement satellite à chaque emplacement géographique où vous souhaitez stocker des données. Le tableau suivant présente les emplacements géographiques disponibles :

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

![Capture d’écran de la page emplacements géographiques dans SharePoint centre d’administration.](../media/sharepoint-multi-geo-admin-center.png)

Pour ajouter un emplacement satellite

1. Ouvrez le Centre d’administration SharePoint.

2. Accédez à l’onglet **Emplacements géographiques**.

3. Cliquez sur **Ajouter un emplacement**.

4. Sélectionnez l’emplacement à ajouter, puis cliquez sur **Suivant**.

5. Saisissez le domaine que vous souhaitez utiliser avec l’emplacement géographique, puis cliquez sur **Ajouter**.

6. Cliquez sur **Fermer**.

La configuration peut prendre jusqu’à 72 heures selon la taille de votre client. Une fois que la configuration d’un emplacement satellite est terminée, vous recevez un e-mail de confirmation. Lorsque le nouvel emplacement géographique s’affiche en bleu sur la carte sur l’onglet **Emplacements géographiques** dans le centre d’administration OneDrive, vous pouvez définir l’emplacement des données par défaut des utilisateurs sur cet emplacement géographique. 

> [!IMPORTANT]
> Votre nouvel emplacement satellite est configuré avec des paramètres par défaut. Cela vous permettra de configurer cet emplacement satellite en fonction de vos besoins de conformité locale.

## <a name="setting-users-preferred-data-location"></a>Configuration de l’emplacement des données par défaut des utilisateurs
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

Lorsque vous activez les emplacements satellites nécessaires, vous pouvez mettre à jour vos comptes d’utilisateur pour utiliser l’emplacement de données par défaut approprié. Nous vous recommandons de définir un emplacement de données par défaut pour chaque utilisateur, même si cet utilisateur reste dans l’emplacement central.

> [!IMPORTANT]
> Si l’emplacement des données par défaut d’un utilisateur est défini sur un emplacement qui n’a pas été configuré en tant qu’emplacement satellite ou emplacement central, le système envoie les données par défaut vers l’emplacement central lorsqu’il approvisionne les sites OneDrive et SharePoint, ainsi que les boîtes aux lettres de groupe.

> [!TIP]
> Nous vous recommandons de commencer les validations avec un utilisateur de test ou un petit groupe d’utilisateurs avant de déployer à plus grande échelle les fonctionnalités multigéographiques dans votre organisation.

Deux types d’objets utilisateur sont disponibles dans Azure Active Directory (Azure AD) : les utilisateurs cloud uniquement et les utilisateurs synchronisés. Suivez les instructions appropriées pour votre type d’utilisateur.

### <a name="synchronize-users-preferred-data-location-using-azure-ad-connect"></a>Synchroniser l’emplacement des données par défaut de l’utilisateur à l’aide d’Azure AD Connect 

Si les utilisateurs de votre entreprise sont synchronisés à partir d’un système Active Directory local avec Azure AD, leur PreferredDataLocation doit être renseigné dans AD et synchronisé avec Azure AD.

Suivez le processus de [Azure Active Directory Connect Sync : configurer l’emplacement de données par défaut pour les ressources Microsoft 365](/azure/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation) pour configurer la synchronisation de l’emplacement des données par défaut à partir de vos services de domaine Active Directory (AD DS) locaux vers Azure AD.

Nous vous recommandons d’inclure la configuration de l’emplacement des données par défaut de l’utilisateur dans le cadre de votre flux de travail de création utilisateur standard.

> [!IMPORTANT]
> Pour les nouveaux utilisateurs sans OneDrive provisionné, attendez au moins 24 heures après que le PDL d'un utilisateur soit synchronisé avec Azure AD pour que les changements se propagent avant que l'utilisateur ne se connecte à OneDrive Entreprise. (Configurer l’emplacement des données par défaut avant que l’utilisateur ne se connecte pour approvisionner son OneDrive Entreprise permet de s’assurer que le nouveau OneDrive de l’utilisateur est approvisionné à l’emplacement approprié.)

### <a name="setting-preferred-data-location-for-cloud-only-users"></a>Configurer l’emplacement des données par défaut pour les utilisateurs cloud uniquement 

Si les utilisateurs de votre entreprise ne sont pas synchronisés à partir d’un système Active Directory local avec Azure AD, ce qui signifie qu'ils sont créés dans Microsoft 365 ou Azure AD, alors la PDL doit être définie à l'aide du module Microsoft Azure Active Directory pour Windows PowerShell.

Les procédures de cette section nécessitent le [module Microsoft Azure Active Directory pour le module PowerShell de Windows](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). Si ce module est déjà installé, assurez-vous que vous effectuez une mise à jour vers la dernière version.

1.  [Connectez-vous et enregistrez-vous](/powershell/connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) avec un ensemble d’informations d’identification d’administrateur général pour votre client.

2.  Utilisez la cmdlet [Set-MsolUser](/powershell/msonline/v1/set-msoluser) pour définir l’emplacement des données par défaut pour chacun de vos utilisateurs. Par exemple :

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    Vous pouvez vérifier pour confirmer que l’emplacement des données par défaut a été correctement mis à jour à l’aide de la cmdlet Get-MsolUser. Par exemple :

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![Capture d’écran de la fenêtre PowerShell montrant set-msoluser.](../media/multi-geo-tenant-configuration-image3.png)

Nous vous recommandons d’inclure la configuration de l’emplacement des données par défaut de l’utilisateur dans le cadre de votre flux de travail de création utilisateur standard.

> [!IMPORTANT]
> Pour les nouveaux utilisateurs sans approvisionnement OneDrive, attendez au moins 24 heures après la configuration d’un emplacement des données par défaut de l’utilisateur pour que les changements soient appliqués avant que l’utilisateur ne se connecte à OneDrive. (Configurer l’emplacement des données par défaut avant que l’utilisateur ne se connecte pour approvisionner son OneDrive Entreprise permet de s’assurer que le nouveau OneDrive de l’utilisateur est approvisionné à l’emplacement approprié.)

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a>Configuration de OneDrive et l’effet de PDL

Si l’utilisateur possède déjà un site OneDrive créé dans le client, configurer son emplacement des données par défaut ne déplace pas automatiquement son OneDrive existant. Pour déplacer le déplacement d’un OneDrive, voir [OneDrive Entreprise Geo Move](move-onedrive-between-geo-locations.md).

> [!NOTE]
> Exchange Online relocalisation automatique de la boîte aux lettres de l’utilisateur si le PLD change et que MailboxRegion ne correspond plus au code d’emplacement géographique de la base de données de boîtes aux lettres. Pour plus d’informations, [voir Administering Exchange Online mailboxes in a multi-geo environment](./administering-exchange-online-multi-geo.md).

Si l’utilisateur ne dispose pas d’un site OneDrive dans le client, OneDrive est approvisionné pour lui conformément à la valeur de son emplacement des données par défaut en supposant que ce dernier correspond à l’un des emplacements satellites de l’entreprise.

## <a name="configuring-multi-geo-search"></a>Configuration de la recherche Multi-Géo

Votre client Multi-Géo aura des fonctionnalités de recherche regroupées permettant à une requête de recherche de renvoyer des résultats de n’importe quel endroit dans le client.

Par défaut, les recherches effectuées à partir de ces points d’entrée renvoient des résultats regroupés, bien que chaque index de recherche se trouve dans son emplacement géographique approprié :

- OneDrive Entreprise

- Delve

- Page d’accueil SharePoint

- Centre de recherche

Par ailleurs, les fonctionnalités de recherche Multi-Géo peuvent être configurées pour vos applications de recherche personnalisées qui utilisent l’API de recherche SharePoint.

Consultez [Configurer la recherche pour OneDrive Entreprise Multi-Géo](configure-search-for-multi-geo.md) pour obtenir des instructions, y compris des informations sur les limitations et les différences.

## <a name="validating-the-microsoft-365-multi-geo-configuration"></a>Validation de la configuration de Microsoft 365 Multi-Geo

Voici certains cas d’utilisation de base que vous pourriez vouloir inclure dans votre plan de validation avant de déployer à grande échelle Microsoft 365 Multi-Geo dans votre entreprise. Une fois que vous avez terminé ces tests et les cas d’utilisation supplémentaires éventuels et pertinents pour votre entreprise, vous pouvez choisir de commencer à ajouter des utilisateurs à votre groupe pilote initial.

**OneDrive Entreprise**

Sélectionnez OneDrive à partir du lanceur d’applications de Microsoft 365 et vérifiez que vous êtes automatiquement redirigé vers l’emplacement géographique approprié de l’utilisateur, conformément à l’emplacement des données par défaut de l’utilisateur. OneDrive Entreprise doit maintenant commencer à être approvisionné à cet emplacement. Après l’approvisionnement, essayez de charger et de télécharger quelques documents.

**Application mobile OneDrive**

Connectez-vous à votre application mobile OneDrive à l’aide de vos informations d’identification de compte de test. Confirmez que vous pouvez voir vos fichiers OneDrive Entreprise et que vous pouvez interagir avec eux à partir de votre appareil mobile.

**Client de synchronisation OneDrive**

Vérifiez que le client de synchronisation OneDrive détecte automatiquement l’emplacement géographique de OneDrive Entreprise dès la connexion. Si vous devez télécharger le client de synchronisation, vous pouvez cliquer sur **Synchroniser** dans la bibliothèque OneDrive.

**Applications Office**

Confirmez que vous pouvez utiliser OneDrive Entreprise en vous connectant à partir d’une application Office, telle que Word. Ouvrez l’application Office, puis sélectionnez « OneDrive- <TenantName> ». Office détecte votre emplacement OneDrive et affiche les fichiers que vous pouvez ouvrir.

**Partage**

Essayez de partager des fichiers OneDrive. Vérifiez que le sélecteur de personnes affiche tous vos utilisateurs SharePoint en ligne indépendamment de leur emplacement géographique.