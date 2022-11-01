---
title: Ajouter ou supprimer un administrateur géographique
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
ms.collection: SPO_Content
ms.localizationpriority: medium
f1.keywords:
- NOCSH
description: Vous avez besoin de configurer des administrateurs distincts pour chaque emplacement géographique ? Découvrez comment ajouter ou supprimer un administrateur géo dans Microsoft 365 Multi-Geo.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 511dcc104eb8898c974c811b87704b3f22d4a2c2
ms.sourcegitcommit: 0c72639cc3dc74667a6b14343d303f318e70d457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68804661"
---
# <a name="add-or-remove-a-_geography_-administrator-in-microsoft-365-multi-geo"></a>Ajouter ou supprimer un administrateur _Geography_ dans Microsoft 365 Multi-Geo

Vous pouvez configurer des administrateurs distincts pour chaque emplacement _Geography_ que vous avez dans votre _locataire_. Ces administrateurs auront accès aux paramètres SharePoint Online et OneDrive spécifiques à leur emplacement _géographique_ .

Certains services, tels que le magasin de termes, sont administrés à partir de l’emplacement _géographique approvisionné principal_ et répliqués vers des emplacements _géographiques satellites_ . L’administrateur _Geography_ pour l’emplacement _Géographique approvisionné principal_ a accès à ces éléments, contrairement aux administrateurs _Geography_ pour les emplacements _Géographiques satellites_ .

Les administrateurs généraux et les administrateurs SharePoint Online continuent d’avoir accès aux paramètres de l’emplacement _géographique approvisionné principal_ et de tous les emplacements _géographiques satellites_ .

## <a name="configuring-_geography_-administrators"></a>Configuration des administrateurs _geography_

La configuration des administrateurs _geography_ nécessite le module PowerShell SharePoint Online.

Utilisez [Connect-SPOService](/powershell/module/sharepoint-online/Connect-SPOService) pour vous connecter au centre d’administration de l’emplacement _Geography_ où vous souhaitez ajouter l’administrateur _Geography_ . (Par exemple, Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)

Pour afficher les administrateurs _geography_ existants d’un emplacement, exécutez `Get-SPOGeoAdministrator`

## <a name="adding-a-user-as-a-_geography_-admin"></a>Ajout d’un utilisateur en tant qu’administrateur _geography_

Pour ajouter un utilisateur en tant qu’administrateur _geography_ , exécutez `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`

Pour supprimer un utilisateur en tant que Administration _Geography_ d’un emplacement, exécutez`Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`

## <a name="adding-a-group-as-a-_geography_-admin"></a>Ajout d’un groupe en tant qu’administrateur _geography_

Vous pouvez ajouter un groupe de sécurité ou un groupe de sécurité à extension messagerie en tant qu’administrateur _Geography_. (Les groupes de distribution et les Groupes Microsoft 365 ne sont pas pris en charge.)

Pour ajouter un groupe en tant qu’administrateur _Geography_ , exécutez `Add-SPOGeoAdministrator -GroupAlias <alias>`

Pour supprimer un groupe en tant qu’administrateur _Geography_ , exécutez `Remove-SPOGeoAdministrator -GroupAlias <alias>`

Notez que certains groupes de sécurité n’ont pas d’alias de groupe. Si vous voulez ajouter un groupe de sécurité dépourvu d’alias, exécutez la cmdlet [MsolGroup Get](/powershell/module/msonline/get-msolgroup) pour récupérer une liste de groupes, recherchez l’ObjectID de votre groupe de sécurité, puis exécutez la cmdlet suivante :

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

Pour supprimer un groupe à l’aide de l’ObjectID, exécutez la cmdlet `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`.

## <a name="related-topics"></a>Voir aussi

[Add-SPOGeoAdministrator](/powershell/module/sharepoint-online/add-spogeoadministrator)

[Get-SPOGeoAdministrator](/powershell/module/sharepoint-online/get-spogeoadministrator)

[Remove-SPOGeoAdministrator](/powershell/module/sharepoint-online/remove-spogeoadministrator)

[Définir un alias (MailNickName) pour un groupe de sécurité](/powershell/module/azuread/set-azureadgroup)
