---
title: Démarrage rapide Office 365 Content Delivery Network (CDN)
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 01/13/2022
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
- m365initiative-coredeploy
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
description: Démarrage rapide Office 365 Content Delivery Network (CDN)
ms.openlocfilehash: 8eefd20386431f653ef7c247bc07119113e78ef4
ms.sourcegitcommit: 437461fa1d38ff9bb95dd8a1c5f0b94e8111ada2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67670584"
---
# <a name="office-365-content-delivery-network-cdn-quickstart"></a>Démarrage rapide Office 365 Content Delivery Network (CDN)

Vous pouvez utiliser le **réseau de distribution de contenu (CDN) Office 365** intégré pour héberger des ressources statiques (images, JavaScript, feuilles de style, fichiers WOFF) afin de fournir de meilleures performances pour vos pages SharePoint Online. Le réseau de distribution de contenu Office 365 améliore les performances en procédant à la mise en cache des ressources statiques au plus près des navigateurs qui les demandent, ce qui permet d’accélérer les téléchargements et de réduire la latence. En outre, le CDN Office 365 utilise le protocole HTTP/2 pour améliorer la compression et la pipelining HTTP. Le réseau de distribution de contenu Office 365 est inclus dans votre abonnement SharePoint Online.

Pour plus d’informations, consultez [Utiliser le réseau de distribution de contenu (CDN) Office 365 avec SharePoint Online](use-microsoft-365-cdn-with-spo.md).

>[!NOTE]
>La Office 365 CDN est uniquement disponible pour les locataires dans le cloud de production (dans le monde entier). Les locataires des clouds du gouvernement des États-Unis, de la Chine et de l’Allemagne ne prennent actuellement pas en charge le CDN Office 365.

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-identify-items-not-in-cdn"></a>Utiliser l’outil Diagnostics de page pour SharePoint pour identifier les éléments qui ne sont pas dans CDN

Vous pouvez utiliser l’extension de navigateur **Outil Diagnostics de page pour SharePoint pour** répertorier facilement les ressources de vos pages SharePoint Online qui peuvent être ajoutées à une origine CDN.

**L’outil Diagnostics de page pour SharePoint** est une extension de navigateur pour les nouveaux navigateurs Microsoft Edge (<https://www.microsoft.com/edge>) et Chrome qui analysent à la fois le portail moderne SharePoint Online et les pages de site de publication classiques. L’outil fournit un rapport pour chaque page analysée montrant comment la page se comporte par rapport à un ensemble défini de critères de performance. Pour installer et découvrir l’outil Diagnostic de page pour SharePoint, consultez [Utiliser l’outil Diagnostic de page pour SharePoint Online](./page-diagnostics-for-spo.md).

Lorsque vous exécutez l’outil Diagnostics de page pour SharePoint sur une page SharePoint Online, vous pouvez cliquer sur l’onglet **Tests de diagnostic** pour afficher la liste des ressources non hébergées par le CDN. Ces ressources sont répertoriées sous l’en-tête **CdN (Content Delivery Network),** comme illustré dans la capture d’écran ci-dessous.

![Diagnostics de page.](../media/page-diagnostics-for-spo/pagediag-results-general.PNG)

>[!NOTE]
>L’Outil Diagnostic de page fonctionne uniquement pour SharePoint Online et ne peut pas être utilisé sur une page système SharePoint.

## <a name="cdn-overview"></a>Vue d’ensemble du CDN

Le Office 365 CDN est conçu pour optimiser les performances des utilisateurs en distribuant des objets fréquemment consultés, tels que des images et des fichiers javascript, sur un réseau global à haut débit, ce qui réduit le temps de chargement des pages et fournit l’accès aux objets hébergés aussi près que possible de l’utilisateur. Le CDN extrait vos ressources à partir d’un emplacement appelé _origine_. Une origine peut être un site SharePoint, une bibliothèque de documents ou un dossier accessible par une URL.

Le CDN Office 365 est séparé en deux types de base :

- **Le CDN public** est conçu pour être utilisé pour les images JS (JavaScript), CSS (StyleSheets), Web Font File (WOFF, WOFF2) et non propriétaires comme les logos de l’entreprise.
- **Le CDN privé** est conçu pour être utilisé pour les images (PNG, JPG, JPEG, etc.).

Vous pouvez choisir d’avoir des origines publiques ou privées pour votre organisation. La plupart des organisations choisiront d’implémenter une combinaison des deux. Les options publiques et privées offrent des gains de performances similaires, mais chacune présente des attributs et des avantages uniques. Pour plus d’informations sur les origines des CDN publics et privés, consultez [Choisir si chaque origine doit être publique ou privée](use-microsoft-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate).

## <a name="how-to-enable-public-and-private-cdn-with-the-default-configuration"></a>Comment activer le CDN public et privé avec la configuration par défaut
Avant d’apporter des modifications aux paramètres CDN du locataire, vous devez vérifier qu’il respecte les stratégies de conformité, de sécurité et de confidentialité de votre organisation.

Pour obtenir des paramètres de configuration plus détaillés, ou si vous avez déjà activé CDN et souhaitez ajouter des emplacements supplémentaires (origines), consultez la section [Configurer et configurer le CDN Office 365 à l’aide de SharePoint Online Management Shell](use-microsoft-365-cdn-with-spo.md#set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell)

Connectez-vous à votre locataire à l’aide de SharePoint Online Management Shell :

```PowerShell
Connect-SPOService -Url https://<YourTenantName>-admin.sharepoint.com
```

Pour permettre à votre organisation d’utiliser des origines publiques et privées avec la configuration par défaut, tapez la commande suivante :

```PowerShell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

La sortie de ces applets de commande doit ressembler à ce qui suit :

![Sortie de Set-SPOTenantCdnEnabled.](../media/O365-CDN/o365-cdn-enable-output.png)

## <a name="see-also"></a>Voir aussi

[Utiliser l’outil Diagnostics de page pour SharePoint Online](./page-diagnostics-for-spo.md)

[Utilisation du réseau de distribution de contenu Office 365 avec SharePoint Online](use-microsoft-365-cdn-with-spo.md)

[Réseaux de distribution de contenu](./content-delivery-networks.md)

[Planification réseau et optimisation des performances pour Office 365](./network-planning-and-performance.md)

[Série de performances SharePoint - série de vidéos Office 365 CDN](https://www.youtube.com/playlist?list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA)
