---
title: Découvrir les stratégies de rétention pour SharePoint et OneDrive
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Priority
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Découvrir les stratégies de rétention qui s’appliquent à SharePoint et OneDrive.
ms.openlocfilehash: e7a265d39b3cca2ffb9c403cf2c87f287a9325b2
ms.sourcegitcommit: 0650da0e54a2b484a3156b3aabe44397fbb38e00
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "45016245"
---
# <a name="learn-about-retention-policies-for-sharepoint-and-onedrive"></a>Découvrir les stratégies de rétention pour SharePoint et OneDrive

>*[Guide pour la sécurité et la conformité des licences Microsoft 365](https://aka.ms/ComplianceSD).*

Les informations contenues dans cet article complètent l’article [Découvrir les stratégies de rétention](retention-policies.md) car elles contiennent des informations spécifiques à SharePoint et OneDrive.

## <a name="how-a-retention-policy-works-with-sharepoint-and-onedrive"></a>Fonctionnement d’une stratégie de rétention avec SharePoint et OneDrive

Une stratégie de rétention est appliquée au niveau de la collection d’un site. Lorsque vous incluez une collection de sites SharePoint ou un compte OneDrive dans une stratégie de rétention, une bibliothèque de conservation et de préservation est créée, s’il n’en existe pas. Vous pouvez afficher cette bibliothèque sur la page **Site.contents** dans le site de niveau supérieur de la collection de sites. La plupart des utilisateurs ne peuvent pas visualiser la bibliothèque de conservation et de préservation car elle est visible uniquement pour les administrateurs de collection de sites.
  
Si une personne tente de modifier ou de supprimer le contenu dans un site qui est soumis à une stratégie de rétention, la stratégie vérifie d’abord si le contenu a été modifié depuis qu’elle a été appliquée. S’il s’agit du premier changement depuis l’application de la stratégie, la stratégie de rétention copie le contenu dans la bibliothèque de conservation et de préservation, et permet ensuite à la personne de modifier ou de supprimer le contenu d’origine. Tout contenu dans la collection du site peut être copié dans la bibliothèque de conservation et de préservation, même si le contenu ne correspond pas à la requête utilisée par la stratégie de rétention.
  
Un travail du minuteur nettoie périodiquement la bibliothèque de conservation et de préservation des documents. Ce travail compare tout le contenu de la bibliothèque de conservation et de préservation des documents à toutes les requêtes utilisées par les stratégies de rétention sur le site. Le contenu antérieur à la période de rétention configurée est supprimé de la bibliothèque de conservation et de préservation des documents et de l’emplacement d’origine si celui-ci existe toujours. Ce travail du minuteur s’exécute tous les sept jours, ce qui signifie que l’opération peut prendre jusqu’à sept jours pour que le contenu soit supprimé.
  
Ce comportement s’applique au contenu qui existe lorsque la stratégie de rétention est appliquée. En outre, tout contenu qui est créé ou ajouté au site après avoir été inclus dans la stratégie sera conservé après la suppression. Toutefois, le nouveau contenu n’est pas copié dans la bibliothèque de conservation et de préservation la première fois qu’il est modifié, uniquement lorsqu’il est supprimé. Pour conserver toutes les versions d’un fichier, vous devez activer le [contrôle de version](#how-a-retention-policy-works-with-document-versions-in-a-site-collection).
  
Un utilisateur reçoit une erreur s’il tente de supprimer une bibliothèque, une liste, un dossier ou un site soumis à une stratégie de rétention. Un utilisateur peut supprimer un dossier s’il déplace ou supprime d’abord les fichiers du dossier qui sont soumis à la stratégie. De plus, la bibliothèque de conservation et de préservation des documents est créée à ce stade, et non lorsque vous créez la stratégie de rétention. Cela signifie que pour tester votre stratégie, vous devez d’abord modifier ou supprimer un document d’un site soumis à la stratégie de rétention, puis parcourir la bibliothèque de conservation et de préservation des documents pour afficher la copie conservée.
  
Une fois qu’une stratégie de rétention est attribuée à un compte OneDrive ou un site SharePoint, les chemins d’accès au contenu sont fonction de la politique de rétention qui consiste à conserver et à supprimer, à conserver uniquement ou à supprimer uniquement.

Lorsque la stratégie de rétention doit conserver et supprimer :

![Diagramme de cycle de vie de contenu dans SharePoint et OneDrive](../media/Retention_Diagram_of_retention_flow_in_sites.png)
  
1. **Si le contenu est modifié ou supprimé** pendant la période de rétention, une copie du contenu d’origine tel qu’il existait lors de l’attribution de la stratégie de rétention est créée dans la bibliothèque de conservation et de préservation des documents. Là, le travail du minuteur identifie les éléments dont la période de rétention a expiré. Ces éléments sont déplacés vers la corbeille de second niveau, où ils sont définitivement supprimés au bout de 93 jours. La corbeille second niveau n’est pas visible par les utilisateurs finaux (seule le premier niveau de la corbeille l’est), mais les administrateurs de collection de sites peuvent afficher et restaurer du contenu à partir de cet emplacement.

    > [!NOTE]
    > Pour éviter toute perte de données par inadvertance, nous ne supprimons plus définitivement le contenu de la bibliothèque de conservation. Au lieu de cela, nous ne supprimons définitivement que le contenu de la corbeille de façon à ce que tout le contenu de la bibliothèque de conservation et de préservation passe transmis par la corbeille second niveau .
    
2. **Si le contenu n’est ni modifié ni supprimé** pendant la période de rétention, le travail de minuteur déplace le contenu vers la corbeille de premier niveau à la fin de la période de rétention. Si un utilisateur supprime le contenu à partir de là ou vide cette Corbeille (action également nommée « purge »), le document est déplacé vers la Corbeille second niveau. La période de rétention de 93 jours concerne tant la corbeille premier niveau que la corbeille second niveau. À la fin des 93 jours, le document est définitivement supprimé de l’emplacement en question (corbeille premier niveau ou second niveau). La Corbeille n’est pas indexée et n’est donc pas disponible pour les recherches. Par conséquent, une recherche eDiscovery ne peut pas trouver de contenu de la Corbeille auquel appliquer une conservation.

Lorsque la stratégie de rétention consiste à conserver uniquement ou à supprimer uniquement, les chemins d'accès au contenu sont des variantes de rétention et de suppression :

#### <a name="content-paths-for-retain-only-retention-policy"></a>Chemins d’accès au contenu pour la stratégie de rétention de conservation uniquement

1. **Si le contenu est modifié ou supprimé** pendant la période de rétention : une copie du document d’origine est créée dans la bibliothèque de conservation et de préservation et conservée jusqu’à la fin de la période de rétention, lorsque celle-ci est déplacée vers la corbeille second niveau et supprimée définitivement après 93 jours.

2. **Si le contenu n’est pas modifié ou supprimé** pendant la période de rétention : rien ne se passe avant et après la période de rétention ; le document reste à son emplacement d’origine.

#### <a name="content-paths-for-delete-only-retention-policy"></a>Chemins d’accès au contenu pour la stratégie de rétention de suppression uniquement

1. **Si le contenu est supprimé** pendant la période configurée : le document est déplacé vers la corbeille de premier niveau. Si un utilisateur supprime le contenu à partir de là ou vide cette corbeille, le document est déplacé vers la corbeille second niveau. La période de rétention de 93 jours concerne tant la corbeille premier niveau que la corbeille second niveau. À la fin des 93 jours, le document est définitivement supprimé de l’emplacement en question (corbeille premier niveau ou second niveau). Si le contenu est modifié pendant la période configurée, il suit le même chemin de suppression après la période configurée.

2. **Si le contenu n’est pas supprimé** pendant la période configurée : à la fin de la période configurée dans la stratégie de rétention, le document est déplacé vers la corbeille de premier niveau. Si un utilisateur supprime le contenu à partir de là ou vide cette corbeille (action également nommée « purge »), le document est déplacé vers la corbeille second niveau. La période de rétention de 93 jours concerne tant la corbeille premier niveau que la corbeille second niveau. À la fin des 93 jours, le document est définitivement supprimé de l’emplacement en question (corbeille premier niveau ou second niveau). La Corbeille n’est pas indexée et n’est donc pas disponible pour les recherches. Par conséquent, une recherche eDiscovery ne peut pas trouver de contenu de la Corbeille auquel appliquer une conservation.
    
## <a name="how-a-retention-policy-works-with-document-versions-in-a-site-collection"></a>Fonctionnement d’une stratégie de rétention avec les versions de document d’une collection de sites

Le contrôle de version est une fonctionnalité présente dans toutes les bibliothèques de documents dans SharePoint et OneDrive. Par défaut, le contrôle de version conserve au moins les 500 versions principales, même si vous pouvez augmenter cette limite. Pour plus d'informations, voir [Activer et configurer le contrôle de version pour une liste ou une bibliothèque](https://support.office.com/article/1555d642-23ee-446a-990a-bcab618c7a37).
  
Une stratégie de conservation uniquement conserve toutes les versions d’un document dans une collection de sites SharePoint ou un compte OneDrive. Lorsqu’un document soumis à une stratégie de rétention ou de conservation uniquement est modifié pour la première fois, une version du document d’origine est copiée dans la bibliothèque de conservation et de préservation des documents. Lorsqu’un document soumis à une stratégie de rétention ou de conservation uniquement est supprimé, toutes les versions sont copiées dans la bibliothèque de conservation et de préservation des documents si le contrôle de version est activé. Chaque version d’un document dans la bibliothèque Preservation Hold est présente sous la forme d’un élément distinct avec sa propre période de rétention :
  
- If the retention policy is based on when the content was created, each version has the same expiration date as the original document. The original document and its versions all expire at the same time.
    
- If the retention policy is based on when the content was last modified, each version has its own expiration date based on when the original document was modified to create that version. The original documents and its versions expire independently of each other.

> [!NOTE]
> Les versions conservées des documents SharePoint et OneDrive ne sont pas consultables par les outils eDiscovery.

## <a name="when-a-user-leaves-the-organization"></a>Lorsqu’un utilisateur quitte l’organisation 

**SharePoint** :

Lorsqu’un utilisateur quitte votre organisation, le contenu qu’il a créé n’est pas affecté car SharePoint est considéré comme un environnement collaboratif, contrairement à la boîte aux lettres ou au compte OneDrive de l’utilisateur.

**OneDrive** :

Si un utilisateur quitte votre organisation, tous les fichiers soumis à une stratégie de rétention ou contenant des étiquettes de rétention sont conservés pendant toute la durée de la stratégie ou de l’étiquette. Pendant cette période, tous les accès partagés continuent de fonctionner. À expiration de la période de rétention, le contenu est placé dans la Corbeille de collections de sites et n’est accessible à personne, à l’exception de l’administrateur. Si un document est marqué en tant qu’enregistrement par une stratégie de rétention, il est conservé jusqu’à la fin de la période de rétention, après quoi le contenu est définitivement supprimé. 

## <a name="how-to-configure-a-retention-policy-for-sharepoint-and-onedrive"></a>Comment configurer une stratégie de rétention pour SharePoint et OneDrive

Suivez les instructions pour [créer et configurer des stratégies de rétention](create-retention-policies.md) et pour la page **Choisir les emplacements** de l’assistant, sélectionnez l’une des options suivantes :

- **Appliquer la stratégie uniquement au contenu dans les courriers électroniques Exchange, les dossiers publics, les groupes Office 365, les documents OneDrive et SharePoint**

- **Choisir des emplacements spécifiques** > **Sites SharePoint**, **Comptes OneDrive** et **Groupes Office 365**.

Lorsque vous choisissez les emplacement des **sites SharePoint**, votre stratégie de rétention peut conserver le contenu des sites de communication SharePoint, des sites d’équipe qui ne sont pas connectés par des groupes Office 365 et des sites classiques. Cette option ne prend pas en charge les sites d’équipe connectés par des groupes Office 365. Utilisez plutôt des emplacements de **groupes Office 365** qui s’appliquent au contenu de la boîte aux lettres, du site et des fichiers du groupe. 

Lorsque vous spécifiez vos emplacements pour les sites SharePoint, aucune autorisation n’est nécessaire pour accéder au site, et aucune validation n’intervient au moment où vous spécifiez l’URL sur la page **Modifier les emplacements**. Toutefois, les sites doivent être indexés, et l’existence des sites que vous spécifiez est vérifiée à la fin de l’Assistant. 

Si cette vérification échoue, un message apparaît pour vous informer que la validation de l’URL entrée a échoué, et que l’Assistant ne créera pas la stratégie de rétention tant que la vérification de validation n’aura pas abouti. Si ce message apparaît, revenez à l’Assistant pour modifier l’URL ou supprimer le site.
