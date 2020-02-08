---
title: Protéger les fichiers SharePoint Online à l’aide d’une étiquette de confidentialité
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/27/2019
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- SPO_Content
ms.custom:
- Ent_Solutions
ms.assetid: 5b9c8e41-25d2-436d-89bb-9aecb9ec2b80
description: 'Résumé : Découvrez comment appliquer la protection Azure Information Protection pour protéger les fichiers d’un site d’équipe SharePoint Online hautement confidentiel.'
ms.openlocfilehash: 7b43ee5bcc3193da398359a155e2daeac2d06a85
ms.sourcegitcommit: 21be88a1b38b6554ffa1bc5b743c129fe8547704
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/06/2020
ms.locfileid: "41830968"
---
# <a name="protect-sharepoint-online-files-with-a-sensitivity-label"></a>Protéger les fichiers SharePoint Online à l’aide d’une étiquette de confidentialité

Suivez les étapes décrites dans cet article pour configurer une étiquette de confidentialité Office 365 afin de fournir le chiffrement et les autorisations pour les fichiers. Ces fichiers peuvent être ajoutés à une bibliothèque SharePoint configurée pour une protection hautement confidentielle. Vous pouvez également ouvrir un fichier directement à partir du site et appliquer l’étiquette. La protection via un chiffrement et des autorisations reste associée au fichier, même quand il est téléchargé à partir du site. 

Cette procédure fait partie d’une solution plus globale de configuration d’une protection hautement confidentielle pour les sites SharePoint et les fichiers contenus dans ces sites. Pour plus d’informations, reportez-vous à l’article [Sécuriser des sites et des fichiers SharePoint Online](../security/office-365-security/secure-sharepoint-online-sites-and-files.md). 

L’utilisation d’étiquettes de confidentialité pour les fichiers dans SharePoint Online n’est pas recommandée pour tous les clients, mais elle est proposée en option aux clients qui ont besoin de ce niveau de protection pour un sous-ensemble de fichiers.

Voici quelques remarques importantes concernant cette solution :
- Si votre organisation n’a pas [activé les étiquettes de confidentialité pour les fichiers Office dans SharePoint et OneDrive (préversion publique)](/microsoft-365/compliance/sensitivity-labels-sharepoint-onedrive-files) : notez que lorsque le chiffrement d'étiquettes de confidentialité est appliqué aux fichiers stockés dans Office 365, le service ne peut pas traiter leur contenu. La co-édition, eDiscovery, la recherche, Delve et d’autres fonctionnalités de collaboration ne fonctionnent pas. Les stratégies de protection contre la perte de données peuvent fonctionner seulement avec les métadonnées (notamment les étiquettes Office 365), mais pas avec le contenu de ces fichiers (comme des numéros de carte de crédit dans des fichiers).

- Cette solution exige que l’utilisateur sélectionne une étiquette qui applique la protection. Si vous avez besoin d'un chiffrement automatique et de la possibilité pour SharePoint d'indexer et d'inspecter les fichiers, pensez à utiliser la gestion des droits relatifs à l'information (IRM) dans SharePoint Online. Lorsque vous configurez une bibliothèque SharePoint pour la gestion des droits relatifs à l’information (IRM), les fichiers sont automatiquement chiffrés lorsqu’ils sont téléchargés à des fins de modification.  La gestion des droits relatifs à l’information (IRM) de SharePoint inclut des restrictions pouvant influencer votre décision. Pour plus d’informations, voir [Configurer la Gestion des droits relatifs à l’information (Information Rights Management, IRM) dans le Centre d’administration SharePoint](https://support.office.com/article/Set-up-Information-Rights-Management-IRM-in-SharePoint-admin-center-239CE6EB-4E81-42DB-BF86-A01362FED65C).

## <a name="admin-setup"></a>Configuration de l’administrateur

Pour atteindre ce niveau de sécurité supplémentaire pour les fichiers d'un site d'équipe SharePoint Online spécifique, vous devez configurer une étiquette de confidentialité personnalisée qui est soit sa propre étiquette, soit une sous-étiquette de l’étiquette générale pour les données hautement réglementées. Seuls les membres du groupe Office 365 du site d'équipe SharePoint Online verront l'étiquette ou la sous-étiquette personnalisée dans leur liste d'étiquettes.

- Utilisez une étiquette de confidentialité lorsque vous avez besoin d’un petit nombre d’étiquettes à la fois pour un usage global et pour des équipes privées individuelles.

- Utilisez une sous-étiquette de confidentialité lorsque vous avez un grand nombre d’étiquettes ou si vous souhaitez organiser les étiquettes pour les équipes hautement confidentielles sous une étiquette à usage général pour les fichiers hautement confidentiels.

Suivez [ces instructions](encryption-sensitivity-labels.md) pour configurer une étiquette distincte ou une sous-étiquette avec les paramètres suivants :

- Le nom de l’étiquette ou de la sous-étiquette contient le nom du site d’équipe
- Le chiffrement est activé
- Le groupe Office 365 du site d’équipe possède des autorisations de co-édition

Une fois que vous avez créé, publiez la nouvelle étiquette ou sous-étiquette pour vos utilisateurs, puis appliquez-les aux fichiers en local avant de les charger dans l’équipe ou plus tard une fois que le fichier est stocké dans l’équipe.
 
Une fois que vos utilisations peuvent sélectionner l'étiquette de sensibilité à partir de l'option **Sensibilité** du ruban **Accueil** dans Microsoft Word, Excel et PowerPoint.
  
> [!NOTE]
> Si vous disposez de plusieurs sites d'équipe SharePoint Online très sensibles, vous devez créer plusieurs étiquettes de sensibilité. 
  
## <a name="adding-permissions-for-external-users"></a>Ajout d’autorisations pour les utilisateurs externes
Vous pouvez accorder à des utilisateurs externes l’accès à des fichiers protégés avec une étiquette de confidentialité de deux façons. Dans les deux cas, les utilisateurs externes doivent disposer d’un compte Azure AD. Si les utilisateurs externes ne sont pas membres d’une organisation qui utilise Azure AD, ils peuvent obtenir un compte Azure AD individuel en utilisant cette page d’inscription : [https://aka.ms/aip-signup](https://aka.ms/aip-signup).

 - Ajouter des utilisateurs externes au groupe Office 365 pour le site d’équipe. Vous devez d’abord ajouter le compte à votre annuaire en tant qu’utilisateur B2B. La [mise en cache de l’appartenance à un groupe par Azure Rights Management](https://docs.microsoft.com/azure/information-protection/plan-design/prepare#group-membership-caching-by-azure-information-protection) peut prendre quelques heures.  
 - Ajouter des comptes d’utilisateur externe directement dans la configuration d’étiquette. Vous pouvez ajouter tous les utilisateurs issus d’une organisation (par exemple Fabrikam.com), un groupe Office 365 (par exemple un groupe financier d’une organisation) ou un utilisateur. Par exemple, vous pouvez ajouter une équipe externe de régulateurs aux permissions de votre étiquette de sensibilité.

## <a name="see-also"></a>Voir aussi

[Sécuriser les fichiers et sites SharePoint Online](../security/office-365-security/secure-sharepoint-online-sites-and-files.md)
  
[Conseils de sécurité Microsoft pour les campagnes électorales, les organisations à but non lucratif et d’autres organisations flexibles](/security/office-365-security/microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[Adoption du cloud et solutions hybrides](https://docs.microsoft.com/office365/enterprise/cloud-adoption-and-hybrid-solutions)
