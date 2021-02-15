---
title: Démarrage rapide du réseau de distribution de contenu (CDN) Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 06/04/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
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
description: Démarrage rapide du réseau de distribution de contenu (CDN) Office 365
ms.openlocfilehash: e541b2ea63a69644de22329c45bd6963749964f7
ms.sourcegitcommit: d76a4c07f0be2938372bdfae50e0e4d523bd8e9f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2020
ms.locfileid: "48456410"
---
# <a name="office-365-content-delivery-network-cdn-quickstart"></a>Démarrage rapide du réseau de distribution de contenu (CDN) Office 365

Vous pouvez utiliser le réseau de distribution de contenu **(CDN) Office 365** intégré pour héberger des ressources statiques (images, JavaScript, feuilles de style, fichiers WOFF) afin de fournir de meilleures performances pour vos pages SharePoint Online. Le réseau de distribution de contenu Office 365 améliore les performances en procédant à la mise en cache des ressources statiques au plus près des navigateurs qui les demandent, ce qui permet d’accélérer les téléchargements et de réduire la latence. En outre, le CDN Office 365 utilise le protocole HTTP/2 pour améliorer la compression et le pipelining HTTP. Le réseau de distribution de contenu Office 365 est inclus dans votre abonnement SharePoint Online.

Pour obtenir des instructions plus détaillées, voir Utiliser le réseau de distribution de contenu [(CDN) Office 365 avec SharePoint Online.](use-microsoft-365-cdn-with-spo.md)

>[!NOTE]
>Le CDN Office 365 est uniquement disponible pour les clients dans le cloud de production (dans le monde). Les locataires du gouvernement des États-Unis, de la Chine et de l’Allemagne ne supportent pas actuellement le CDN Office 365.

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-identify-items-not-in-cdn"></a>Utiliser l’outil Diagnostic de page pour SharePoint pour identifier les éléments qui ne sont pas dans le CDN

Vous pouvez utiliser l’extension de navigateur de l’outil Diagnostic de page pour SharePoint pour lister facilement les ressources dans vos pages SharePoint Online qui peuvent être **ajoutées** à une origine cdN.

L’outil Diagnostic de page pour **SharePoint** est une extension de navigateur pour les nouveaux navigateurs Microsoft Edge (et Chrome qui analyse à la fois le portail moderne SharePoint Online et les pages de site de publication https://www.microsoft.com/edge) classiques). L’outil fournit un rapport pour chaque page analysée montrant comment la page se comporte par rapport à un ensemble défini de critères de performance. Pour installer et découvrir l’outil Diagnostic de page pour SharePoint, consultez [Utiliser l’outil Diagnostic de page pour SharePoint Online](https://aka.ms/perftool).

Lorsque vous exécutez l’outil Diagnostic de page pour SharePoint sur une page SharePoint Online, vous pouvez cliquer sur l’onglet Tests de **diagnostic** pour voir la liste des ressources qui ne sont pas hébergées par le CDN. Ces ressources sont répertoriées sous l’en-tête Réseau de distribution de contenu **(CDN),** comme illustré dans la capture d’écran ci-dessous.

![Diagnostics de page](../media/page-diagnostics-for-spo/pagediag-results-general.PNG)

>[!NOTE]
>L’Outil Diagnostic de page fonctionne uniquement pour SharePoint Online et ne peut pas être utilisé sur une page système SharePoint.

## <a name="cdn-overview"></a>Vue d’ensemble du CDN

Le CDN Office 365 est conçu pour optimiser les performances pour les utilisateurs en distribuant des objets fréquemment utilisés tels que des images et des fichiers javascript sur un réseau global haut débit, ce qui réduit le temps de chargement des pages et permet d’accéder aux objets hébergés aussi près que possible de l’utilisateur. Le CDN récupère vos ressources à partir d’un emplacement appelé _origine._ Une origine peut être un site SharePoint, une bibliothèque de documents ou un dossier accessible par une URL.

Le CDN Office 365 est séparé en deux types de base :

- **Le CDN public** est conçu pour être utilisé pour les images JS (JavaScript), CSS (Feuilles de style), Web Font File (WOFF, WOFF2) et les images non propriétaires telles que les logos d’entreprise.
- **Le CDN privé** est conçu pour être utilisé pour les images (PNG, JPG, JPEG, etc.).

Vous pouvez choisir d’avoir des origines publiques ou privées pour votre organisation. La plupart des organisations choisiront d’implémenter une combinaison des deux. Les options publiques et privées offrent des gains de performances similaires, mais chacune possède des attributs et des avantages uniques. Pour plus d’informations sur les origines du CDN public et privé, voir Choisir si [chaque origine doit être publique ou privée.](use-microsoft-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)

## <a name="how-to-enable-public-and-private-cdn-with-the-default-configuration"></a>Comment activer le CDN public et privé avec la configuration par défaut
Avant d’apporter des modifications aux paramètres du CDN client, vous devez vérifier qu’il répond aux stratégies de conformité, de sécurité et de confidentialité de votre organisation.

Pour obtenir des paramètres de configuration plus détaillés, ou si vous avez déjà activé le CDN et souhaitez ajouter des emplacements supplémentaires (origines), consultez la section Installer et configurer le [CDN Office 365](use-microsoft-365-cdn-with-spo.md#set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell) à l’aide de SharePoint Online Management Shell.

Connectez-vous à votre client à l’aide de SharePoint Online Management Shell :

```PowerShell
Connect-SPOService -Url https://<YourTenantName>-admin.sharepoint.com
```

Pour permettre à votre organisation d’utiliser des origines publiques et privées avec la configuration par défaut, tapez la commande suivante :

```PowerShell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

La sortie de ces cmdlets doit ressembler à ce qui suit :

![Sortie des Set-SPOTenantCdnEnabled](../media/O365-CDN/o365-cdn-enable-output.png)

## <a name="see-also"></a>Voir aussi

[Utiliser l’outil Diagnostic de page pour SharePoint Online](https://aka.ms/perftool)

[Utilisation du réseau de distribution de contenu Office 365 avec SharePoint Online](use-microsoft-365-cdn-with-spo.md)

[Réseaux de distribution de contenu](https://aka.ms/o365cdns)

[Planification réseau et optimisation des performances pour Office 365](https://aka.ms/tune)

[Série de performances SharePoint - Série de vidéos sur le CDN Office 365](https://www.youtube.com/playlist?list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA)
