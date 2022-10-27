---
title: Centre d'administration Microsoft 365 rapports d’utilisation des sites SharePoint
f1.keywords:
- NOCSH
ms.author: camillepack
author: camillepack
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier2
- scotvorg
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
description: Obtenez le rapport d’utilisation du site SharePoint pour connaître le nombre de fichiers stockés par les utilisateurs dans les sites SharePoint, le nombre de fichiers activement utilisés et le stockage total consommé.
ms.openlocfilehash: f31c48c3ba68aa52a842bf8d11776b509f077a06
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68722591"
---
# <a name="microsoft-365-reports-in-the-admin-center---sharepoint-site-usage"></a>Rapports Microsoft 365 dans le Centre d’administration - Utilisation du site SharePoint

En tant qu’administrateur Microsoft 365, le tableau de bord Rapports vous montre la vue d’ensemble de l’activité sur différents produits de votre organisation. Il vous permet d'explorer pour obtenir des informations plus précises sur les activités spécifiques de chaque produit. Par exemple, vous pouvez obtenir une vue d’ensemble de la valeur que vous obtenez à partir de SharePoint en termes de nombre total de fichiers que les utilisateurs stockent dans les sites SharePoint, du nombre de fichiers activement utilisés et du stockage consommé sur tous ces sites. Ensuite, vous pouvez explorer le rapport de l'utilisation du site SharePoint pour comprendre les tendances et les détails par niveau de site. 

## <a name="how-to-get-to-the-sharepoint-site-usage-report"></a>Comment accéder au Rapport Utilisation du site SharePoint

1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>. 
2. Dans la page d’accueil du tableau de bord, cliquez sur le bouton **Afficher plus** sur la carte SharePoint.

## <a name="show-user-details-in-the-reports"></a>Afficher les détails de l’utilisateur dans les rapports

Les rapports fournissent des informations sur les données d’utilisation de votre organisation. Par défaut, les rapports affichent des informations avec des noms identifiables pour les utilisateurs, les groupes et les sites. À compter du 1er septembre 2021, nous masquons les informations utilisateur par défaut pour tous les rapports dans le cadre de notre engagement continu à aider les entreprises à prendre en charge leurs lois locales sur la confidentialité.
  
Votre liste d’utilisateurs se présente comme suit :
  
![Rapports : liste d’utilisateurs rendus anonymes.](../../media/2ed99bce-4978-4ee3-9ea2-4a8db26eef02.png)
  
Les administrateurs globaux peuvent inverser cette modification pour leur client et afficher des informations d’utilisateur identifiables si les pratiques de confidentialité de leur organisation le permettent. Vous pouvez le faire dans le Centre d'administration Microsoft 365 en suivant les étapes suivantes :
  
1. Dans le Centre d’administration, allez à la page **Paramètres** \> **Paramètres de l’organisation** \> **Services**.

2. Sélectionnez **Rapports**. 
  
3. Décochez l’instruction **Dans tous les rapports, affichez les noms anonymisés des utilisateurs, des groupes et des sites**, puis enregistrez vos modifications. 
  
## <a name="interpret-the-sharepoint-site-usage-report"></a>Interpréter le rapport d’utilisation du site SharePoint

Vous pouvez afficher l’utilisation du site dans le rapport SharePoint en choisissant l’onglet **Utilisation du site** .

:::image type="content" alt-text="Rapports Microsoft 365 : rapport d’utilisation du site Microsoft SharePoint." source="../../media/d1cb6200-e81c-460b-9d05-53f4bd7cf5ee.png" lightbox="../../media/d1cb6200-e81c-460b-9d05-53f4bd7cf5ee.png":::

Sélectionnez **Choisir des colonnes** pour ajouter ou supprimer des colonnes du rapport.

:::image type="content" alt-text="Rapport d’utilisation du site SharePoint : choisissez des colonnes." source="../../media/71ac3195-c494-40c1-9346-a858125ef6df.png":::

Vous pouvez également exporter les données du rapport dans un fichier .csv Excel en sélectionnant le lien **Exporter** . Cela a pour effet d'exporter les données de tous les utilisateurs afin d'effectuer un tri et un filtrage simples à des fins d'analyse approfondie. 

Le rapport **d’utilisation du site SharePoint** peut être consulté pour connaître les tendances des 7 derniers jours, 30 jours, 90 jours ou 180 jours. Toutefois, si vous sélectionnez un jour particulier dans le rapport, la table affiche les données pendant jusqu’à 28 jours à partir de la date actuelle (et non la date à laquelle le rapport a été généré).
  
|Métrique|Description|
|:-----|:-----|
|URL du site  |URL complète du site. |
|Deleted  |État de suppression du site. La suppression effective des sites prend au minimum 7 jours.  |
|Propriétaire du site  |Nom d’utilisateur du propriétaire principal du site.   |
|Nom du principal du propriétaire du site  |Adresse e-mail du propriétaire du site. |
|Date de la dernière activité (UTC)  | Date de la dernière détection de l’activité de fichier ou de l’affichage d’une page sur le site.  |
|ID d’étiquette de confidentialité du site  | Étiquette de confidentialité sur le site.  |
|Partage externe  | Valeur du paramètre de partage externe pour le site. Cette valeur ne reflète pas les modifications apportées au paramètre effectif par les étiquettes de confidentialité de site. Si vous utilisez des étiquettes de confidentialité, utilisez les [rapports de gouvernance de l’accès aux données](/sharepoint/data-access-governance-reports) pour obtenir les valeurs correctes.|
|Stratégie d’appareil non managée  | Stratégie d’accès au site pour les appareils non gérés.  |
|Emplacement géographique  | Emplacement géographique du site.  |
|Fichiers  |Nombre de fichiers sur le site. |
|Fichiers actifs  | Nombre de fichiers actifs sur le site. Un fichier est considéré comme actif s’il a été enregistré, synchronisé, modifié ou partagé au cours de la période spécifiée.<br/> REMARQUE : Si des fichiers ont été supprimés pendant la période spécifiée pour le rapport, le nombre de fichiers actifs affichés dans le rapport peut être supérieur au nombre actuel de fichiers sur le site.  |
|Stockage utilisé (Mo)  |Quantité de stockage actuellement utilisée sur le site.  |
|Stockage alloué (Mo)  |Quantité maximale de stockage allouée pour le site.  |
|Affichages de page  |Nombre de fois où les pages ont été consultées sur le site.  |
|Pages visitées  |Nombre de pages uniques qui ont été visitées sur le site.  |
|Nombre de liens anonymes  |Nombre de fois où des documents ou dossiers sont partagés à l’aide de « Tout le monde avec le lien » sur le site.  |
|Nombre de liens d’entreprise  |Nombre de fois où des documents ou des dossiers sont partagés à l’aide de « Personnes dans l’organisation avec le lien » sur le site.  |
|Lien sécurisé pour le nombre d’invités  |Nombre de fois où des documents ou des dossiers sont partagés à l’aide de « personnes spécifiques » sur le site.  |
|Lien sécurisé pour le nombre de membres  |Nombre de fois où des documents ou des dossiers sont partagés à l’aide de « personnes spécifiques » sur le site.  |
|Modèle web racine  |Modèle utilisé pour créer le site.  <br/> REMARQUE : si vous souhaitez filtrer les données par différents types de sites, exportez les données et utilisez la colonne Modèle web racine. |

