---
title: Microsoft 365 Rapports dans le Centre d’administration - Utilisation SharePoint site
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MST160
- MET150
- MOE150
description: Obtenez le rapport SharePoint’utilisation du site pour connaître le nombre de fichiers stockés par les utilisateurs dans les sites SharePoint, le nombre d’utilisateurs activement utilisés et le stockage total utilisé.
ms.openlocfilehash: 3b84a31b787e3ccf855e26befcf570e364a9e148
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60162037"
---
# <a name="microsoft-365-reports-in-the-admin-center---sharepoint-site-usage"></a>Microsoft 365 Rapports dans le Centre d’administration - Utilisation SharePoint site

En tant qu’administrateur Microsoft 365, le tableau de bord **Rapports** vous présente la vue d’ensemble de l’activité sur différents produits de votre organisation. Il vous permet d'explorer pour obtenir des informations plus précises sur les activités spécifiques de chaque produit. Par exemple, vous pouvez obtenir une vue d’ensemble de la valeur que vous obtenez de SharePoint en termes de nombre total de fichiers stockés par les utilisateurs sur des sites SharePoint, du nombre de fichiers activement utilisés et du stockage consommé sur tous ces sites. Ensuite, vous pouvez explorer le rapport de l'utilisation du site SharePoint pour comprendre les tendances et les détails par niveau de site. 
  
> [!NOTE]
> Vous devez être administrateur général, lecteur général ou lecteur de rapports dans Microsoft 365 ou administrateur Exchange, SharePoint, service Teams, Teams Communications ou administrateur Skype Entreprise pour voir les rapports.
Microsoft 365 Les rapports dans le Centre d’administration ne sont pas pris en charge Cloud de la communauté du secteur public les locataires Élevé et DoD.
 
## <a name="how-to-get-to-the-sharepoint-site-usage-report"></a>Comment accéder au Rapport Utilisation du site SharePoint

1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>. 
2. Dans la page d’accueil du tableau de bord, cliquez sur **le** bouton Afficher plus sur la SharePoint tableau de bord.

## <a name="show-user-details-in-the-reports"></a>Afficher les détails de l’utilisateur dans les rapports

Les rapports fournissent des informations sur les données d’utilisation de votre organisation. Par défaut, les rapports affichent des informations avec des noms identifiables pour les utilisateurs, les groupes et les sites. À compter du 1er septembre 2021, nous masquons les informations utilisateur par défaut pour tous les rapports dans le cadre de notre engagement continu à aider les entreprises à prendre en charge leurs lois locales sur la confidentialité.
  
Votre liste d’utilisateurs se présente comme suit :
  
![Rapports : liste d’utilisateurs rendus anonymes.](../../media/2ed99bce-4978-4ee3-9ea2-4a8db26eef02.png)
  
Les administrateurs globaux peuvent inverser cette modification pour leur client et afficher des informations d’utilisateur identifiables si les pratiques de confidentialité de leur organisation le permettent. Vous pouvez le faire dans le Centre d'administration Microsoft 365 en suivant les étapes suivantes :
  
1. Dans le Centre d’administration, allez à la page **Paramètres** \> **Paramètres de l’organisation** \> **Services**.

2. Sélectionnez **Rapports**. 
  
3. Décochez l’instruction **Dans tous les rapports, affichez les noms anonymisés des utilisateurs, des groupes et des sites**, puis enregistrez vos modifications. 
  
## <a name="interpret-the-sharepoint-site-usage-report"></a>Interpréter le rapport SharePoint’utilisation du site

Vous pouvez afficher l’utilisation du site dans le rapport SharePoint en choisissant l’onglet **Utilisation du** site.

:::image type="content" alt-text="Microsoft 365- Rapport d’utilisation SharePoint site microsoft." source="../../media/d1cb6200-e81c-460b-9d05-53f4bd7cf5ee.png" lightbox="../../media/d1cb6200-e81c-460b-9d05-53f4bd7cf5ee.png":::

Sélectionnez **Choisir des colonnes** pour ajouter ou supprimer des colonnes dans le rapport.

:::image type="content" alt-text="SharePoint d’utilisation du site : choisissez des colonnes." source="../../media/71ac3195-c494-40c1-9346-a858125ef6df.png":::

Vous pouvez également exporter les données du rapport dans un Excel .csv en sélectionnant le lien **Exporter.** Cela a pour effet d'exporter les données de tous les utilisateurs afin d'effectuer un tri et un filtrage simples à des fins d'analyse approfondie. Si vous avez moins de 2000 utilisateurs, vous pouvez trier et filtrer dans le tableau, au sein du rapport proprement dit. Si vous avez plus de 2000 utilisateurs, pour filtrer et trier les données, vous devez préalablement les exporter. 
  
|Métrique|Description|
|:-----|:-----|
|URL du site  |URL complète du site. |
|Supprimé  |État de suppression du site. La suppression effective des sites prend au minimum 7 jours.  |
|Propriétaire du site  |Nom d’utilisateur du propriétaire principal du site.   |
|Nom principal du propriétaire du site  |Adresse de messagerie du propriétaire du site. |
|Date de la dernière activité (UTC)  | Date de la dernière détection de l’activité de fichier ou de l’affichage d’une page sur le site.  |
|ID d’étiquette de sensibilité du site  | Étiquette de niveau de sensibilité sur le site.  |
|Partage externe  | Paramètres partageables externes sur le site.  |
|Stratégie d’appareil non gestion  | Stratégie d’accès au site pour les appareils non utilisés.  |
|Emplacement géographique  | Emplacement géographique du site.  |
|Fichiers  |Nombre de fichiers sur le site. |
|Fichiers actifs  | Nombre de fichiers actifs sur le site.<br/> REMARQUE : si des fichiers ont été supprimés pendant la période spécifiée pour le rapport, le nombre de fichiers actifs affichés dans le rapport peut être supérieur au nombre actuel de fichiers sur le site.  |
|Stockage utilisé (Mo)  |Quantité de stockage actuellement utilisée sur le site.  |
|Stockage alloués (Mo)  |Quantité maximale de stockage allouée au site.  |
|Vues de page  |Nombre de fois où des pages ont été vues sur le site.  |
|Pages visitées  |Nombre de pages uniques visitées sur le site.  |
|Nombre de liens anonymes  |Nombre de fois que des documents ou des dossiers sont partagés à l’aide de « Tout le monde avec le lien » sur le site.  |
|Nombre de liens d’entreprise  |Nombre de fois que des documents ou des dossiers sont partagés à l’aide de « Personnes de l’organisation avec le lien » sur le site.  |
|Lien sécurisé pour le nombre d’invités  |Nombre de fois que des documents ou des dossiers sont partagés à l’aide de « personnes spécifiques » sur le site.  |
|Lien sécurisé pour le nombre de membres  |Nombre de fois que des documents ou des dossiers sont partagés à l’aide de « personnes spécifiques » sur le site.  |
|Modèle web racine  |Modèle utilisé pour créer le site.  <br/> REMARQUE : si vous souhaitez filtrer les données par différents types de sites, exportez les données et utilisez la colonne Modèle Web racine. |

