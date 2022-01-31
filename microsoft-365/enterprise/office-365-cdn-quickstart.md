---
title: Office 365 réseau de distribution de contenu (CDN) Démarrage rapide
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 01/13/2022
audience: ITPro
ms.topic: article
ms.service: o365-administration
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
description: Office 365 réseau de distribution de contenu (CDN) Démarrage rapide
ms.openlocfilehash: b0684fdfd8583ae6780cb23d47dc697582ae133b
ms.sourcegitcommit: af73b93a904ce8604be319e8dc7cadaf65d50534
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2022
ms.locfileid: "62281434"
---
# <a name="office-365-content-delivery-network-cdn-quickstart"></a>Office 365 réseau de distribution de contenu (CDN) Démarrage rapide

Vous pouvez utiliser le **Office 365 réseau de distribution de contenu intégré (CDN)** pour héberger des ressources statiques (images, JavaScript, feuilles de style, fichiers WOFF) afin de fournir de meilleures performances pour vos pages SharePoint Online. Le réseau de distribution de contenu Office 365 améliore les performances en procédant à la mise en cache des ressources statiques au plus près des navigateurs qui les demandent, ce qui permet d’accélérer les téléchargements et de réduire la latence. En outre, le Office 365 CDN utilise le protocole HTTP/2 pour améliorer la compression et le pipelining HTTP. Le réseau de distribution de contenu Office 365 est inclus dans votre abonnement SharePoint Online.

Pour obtenir des instructions plus détaillées, [consultez la Office 365 réseau de distribution de contenu (CDN) avec SharePoint Online](use-microsoft-365-cdn-with-spo.md).

>[!NOTE]
>Le Office 365 CDN est uniquement disponible pour les clients du cloud de production (dans le monde). Les locataires du gouvernement des États-Unis, de la Chine et de l’Allemagne ne peuvent pas actuellement Office 365 CDN.

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-identify-items-not-in-cdn"></a>Utilisez l’outil Diagnostic de page SharePoint pour identifier les éléments qui ne sont pas CDN

Vous pouvez utiliser l’extension de navigateur De diagnostic de page pour SharePoint outil pour facilement lister les ressources dans vos pages SharePoint Online qui peuvent être **ajoutées** à une origine CDN défaut.

**L’outil Diagnostic de page pour SharePoint** est une extension de navigateur pour les nouveaux navigateurs Microsoft Edge (<https://www.microsoft.com/edge>) et Chrome qui analyse à la fois le portail moderne SharePoint Online et les pages de site de publication classiques. L’outil fournit un rapport pour chaque page analysée montrant comment la page se comporte par rapport à un ensemble défini de critères de performance. Pour installer et découvrir l’outil Diagnostic de page pour SharePoint, consultez [Utiliser l’outil Diagnostic de page pour SharePoint Online](./page-diagnostics-for-spo.md).

Lorsque vous exécutez l’outil Diagnostic de page pour SharePoint sur une page SharePoint Online, vous pouvez cliquer sur l’onglet **Tests de diagnostic** pour voir la liste des ressources qui ne sont pas hébergées par le CDN. Ces ressources sont répertoriées sous la vérification de titre **réseau de distribution de contenu (CDN),** comme illustré dans la capture d’écran ci-dessous.

![Diagnostics de page.](../media/page-diagnostics-for-spo/pagediag-results-general.PNG)

>[!NOTE]
>L’Outil Diagnostic de page fonctionne uniquement pour SharePoint Online et ne peut pas être utilisé sur une page système SharePoint.

## <a name="cdn-overview"></a>CDN vue d’ensemble

Le Office 365 CDN est conçu pour optimiser les performances pour les utilisateurs en distribuant des objets fréquemment utilisés tels que des images et des fichiers javascript sur un réseau global à haut débit, ce qui réduit le temps de chargement des pages et donne accès aux objets hébergés aussi près que possible de l’utilisateur. Le CDN récupère vos biens à partir d’un emplacement appelé _origine_. Une origine peut être un site SharePoint, une bibliothèque de documents ou un dossier accessible par une URL.

Le Office 365 CDN est séparé en deux types de base :

- **Les CDN** publiques sont conçues pour être utilisées pour les images JS (JavaScript), CSS (Feuilles de style), les fichiers de police web (WOFF, WOFF2) et les images non propriétaires telles que les logos d’entreprise.
- **Les CDN** privées sont conçues pour être utilisées pour les images (PNG, JPG, JPEG, etc.).

Vous pouvez choisir d’avoir des origines publiques ou privées pour votre organisation. La plupart des organisations choisiront d’implémenter une combinaison des deux. Les options publiques et privées offrent des gains de performances similaires, mais chacune possède des attributs et des avantages uniques. Pour plus d’informations sur les origines CDN public et privé, voir Choisir si chaque [origine doit être publique ou privée](use-microsoft-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate).

## <a name="how-to-enable-public-and-private-cdn-with-the-default-configuration"></a>Comment activer les CDN public et privé avec la configuration par défaut
Avant d’apporter des modifications aux paramètres de CDN client, vous devez vérifier qu’il répond aux stratégies de conformité, de sécurité et de confidentialité de votre organisation.

Pour obtenir des paramètres de configuration plus détaillés, ou si vous avez déjà activé CDN et que vous souhaitez ajouter des emplacements supplémentaires (origines), consultez la section Installer et configurer le Office 365 CDN à l’aide de [SharePoint Online Management Shell](use-microsoft-365-cdn-with-spo.md#set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell).

Connecter à votre client à l’aide de SharePoint Online Management Shell :

```PowerShell
Connect-SPOService -Url https://<YourTenantName>-admin.sharepoint.com
```

Pour permettre à votre organisation d’utiliser des origines publiques et privées avec la configuration par défaut, tapez la commande suivante :

```PowerShell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

La sortie de ces cmdlets doit ressembler à ce qui suit :

![Sortie de Set-SPOTenantCdnEnabled.](../media/O365-CDN/o365-cdn-enable-output.png)

## <a name="see-also"></a>Voir aussi

[Utiliser l’outil Diagnostic de page pour SharePoint Online](./page-diagnostics-for-spo.md)

[Utilisation du réseau de distribution de contenu Office 365 avec SharePoint Online](use-microsoft-365-cdn-with-spo.md)

[Réseaux de distribution de contenu](./content-delivery-networks.md)

[Planification réseau et optimisation des performances pour Office 365](./network-planning-and-performance.md)

[SharePoint Performance Series - série Office 365 CDN vidéo](https://www.youtube.com/playlist?list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA)
