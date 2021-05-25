---
title: Découvrir la rétention pour SharePoint et OneDrive
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
description: Découvrez comment la rétention fonctionne pour SharePoint et OneDrive.
ms.openlocfilehash: 90e94f4ff94b65860890ab65b451107d1d02963f
ms.sourcegitcommit: 686f192e1a650ec805fe8e908b46ca51771ed41f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2021
ms.locfileid: "52625244"
---
# <a name="learn-about-retention-for-sharepoint-and-onedrive"></a>Découvrir la rétention pour SharePoint et OneDrive

>*[Guide de sécurité et conformité pour les licences Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Les informations contenues dans cet article complètent l’article [Découvrir la rétention](retention.md), car elles contiennent des informations spécifiques à SharePoint et OneDrive.

Pour les autres charges de travail, consultez:

- [En savoir plus sur la rétention dans Microsoft Teams](retention-policies-teams.md)
- [Découvrir la rétention pour Yammer](retention-policies-yammer.md)
- [Découvrir la rétention pour Exchange](retention-policies-exchange.md)

## <a name="whats-included-for-retention-and-deletion"></a>Éléments composant la rétention et la suppression

Tous les fichiers stockés dans SharePoint ou OneDrive peuvent être conservés en appliquant une stratégie de rétention ou une étiquette de rétention. 

Les fichiers suivants peuvent être supprimés:

- Lorsque vous utilisez une stratégie de rétention : tous les fichiers dans les bibliothèques de documents, y compris les bibliothèques de documents SharePoint créées automatiquement, telles que **Eléments de site**.
    
- Lorsque vous utilisez des étiquettes de rétention : tous les fichiers dans toutes les bibliothèques de documents et tous les fichiers au niveau racine qui ne se trouvent pas dans un dossier.
    
> [!TIP]
> Lorsque vous utilisez une [requête avec une stratégie d’application automatique pour une étiquette de rétention](apply-retention-labels-automatically.md#auto-apply-labels-to-content-with-keywords-or-searchable-properties), vous pouvez exclure des bibliothèques de documents à l’aide de cette entrée : `NOT(DocumentLink:"<URL to document library>")`

Les éléments de liste ne sont pas pris en charge par les stratégies de rétention, mais sont pris en charge par les étiquettes de rétention à l’exception des éléments dans les listes. Il s’agit de listes masquées permettant à SharePoint de gérer le système et d’inclure le catalogue de pages maîtres, le catalogue de solutions et les sources de données. Lorsque vous appliquez une étiquette de rétention à un élément de liste pris en charge qui contient une pièce jointe au document :
- Pour une étiquette de rétention standard (qui ne déclare pas l'élément comme étant un document) :
    - La pièce jointe au document n’hérite pas automatiquement des paramètres de rétention de l’étiquette, mais peut être étiquetée de manière indépendante.
- Pour une étiquette de rétention qui déclare que l'élément est un document : 
    - La pièce jointe du document hérite automatiquement des paramètres de rétention de l'étiquette si le document n'est pas déjà étiqueté.

Les paramètres de rétention des stratégies de rétention et des étiquettes de rétention ne s’appliquent pas à l’organisation de structures qui incluent des bibliothèques, des listes et des dossiers.

Pour les stratégies de rétention et les stratégies d’application automatique des étiquettes : l’indexation des sites SharePoint est nécessaire pour l’application des paramètres de rétention. Cependant, si des éléments dans les bibliothèques de documents SharePoint sont configurés pour ne pas s’afficher dans les résultats de la recherche, cette configuration n’exclut pas les fichiers des paramètres de rétention.

## <a name="how-retention-works-for-sharepoint-and-onedrive"></a>Fonctionnement de la rétention pour SharePoint et OneDrive

Pour stocker les contenus qui doivent être conservés, SharePoint et OneDrive créent une bibliothèque Preservation Hold si elle n'existe pas. Vous pouvez afficher cette bibliothèque sur la page **Site.contents** dans le site de niveau supérieur de la collection de sites. La plupart des utilisateurs ne peuvent pas visualiser la bibliothèque de conservation et de préservation car elle est visible uniquement pour les administrateurs de collection de sites.

Les articles dans SharePoint qui ont une étiquette de conservation standard (qui ne déclare pas que l'article est un enregistrement) n'ont pas besoin de la bibliothèque Preservation Hold car ces articles restent dans leur emplacement d'origine. SharePoint empêche les utilisateurs de supprimer des éléments lorsque l'étiquette de conservation appliquée est configurée pour conserver le contenu, et le versionnage SharePoint préserve les anciennes versions lorsque les éléments sont modifiés. Mais pour d'autres scénarios, la bibliothèque Preservation Hold est utilisée lorsque les articles doivent être conservés :
- Articles dans OneDrive qui ont des étiquettes de conservation standard
- Les éléments dans SharePoint ou OneDrive qui ont des étiquettes de conservation qui les déclarent comme un enregistrement, et l'élément est déverrouillé pour l'édition
- Articles soumis à des politiques de rétention

Pour conserver ce contenu lorsqu'un utilisateur tente de le modifier ou de le supprimer, on vérifie si le contenu a été modifié depuis que les paramètres de conservation ont été appliqués. S’il s’agit du premier changement depuis l’application des paramètres de rétention, le contenu est copié dans la bibliothèque de conservation et de préservation des documents, ce qui permet ensuite à la personne de modifier ou de supprimer le contenu d’origine. Tout le contenu d’une collection de sites peut être copié dans la bibliothèque de conservation et de préservation des documents, indépendamment des paramètres de rétention.
  
Un travail du minuteur nettoie périodiquement la bibliothèque de conservation et de préservation des documents. Pour le contenu ayant passé plus de 30 jours dans la bibliothèque de conservation et de préservation des documents, ce travail compare le contenu à toutes les requêtes utilisées par les paramètres de rétention de ce contenu. Un contenu antérieur à la période de rétention configurée est alors supprimé de la bibliothèque de conservation et de préservation des documents, et de l’emplacement d’origine si celui-ci existe encore. Ce travail de timer s’exécute tous les sept jours, ce qui signifie qu’avec un minimum de 30 jours, la suppression du contenu de la bibliothèque de conservation et de préservation des documents peut prendre jusqu’à 37 jours.

Ce comportement pour la copie de fichiers dans la bibliothèque de conservation et de préservation des documents s’applique au contenu qui existe lorsque les paramètres de rétention ont été appliqués. En outre, pour les stratégies de rétention, tout nouveau contenu créé ou ajouté au site après son ajout à la stratégie est conservé dans la bibliothèque de conservation et de préservation des documents. Toutefois, le nouveau contenu n’est pas copié dans la bibliothèque de conservation et de préservation la première fois qu’il est modifié, uniquement lorsqu’il est supprimé. Pour conserver toutes les versions d’un fichier, vous devez activer le [contrôle de version](#how-retention-works-with-document-versions).
  
Les utilisateurs voient un message d'erreur s'ils essaient de supprimer une bibliothèque, une liste, un dossier ou un site qui est soumis à la conservation. Ils peuvent supprimer un dossier s'ils déplacent ou suppriment d'abord tous les fichiers du dossier qui sont soumis à la conservation.

> [!NOTE]
> Comme la bibliothèque de conservation et de préservation des documents n'est créée que lorsqu'elle est nécessaire, et non lorsque vous appliquez une politique de conservation ou une étiquette de conservation, vous devez d'abord modifier ou supprimer un élément soumis à la conservation pour que cela fonctionne.
  
Une fois que les paramètres de rétention sont attribués à un compte OneDrive ou un site SharePoint, les chemins d’accès au contenu sont fonction des paramètres de rétention qui consistent à conserver et à supprimer, à conserver uniquement ou à supprimer uniquement.

Lorsque les paramètres de la stratégie de rétention consistent à conserver et supprimer :

![Diagramme de cycle de vie de contenu dans SharePoint et OneDrive](../media/Retention_Diagram_of_retention_flow_in_sites.png)
  
1. **Si le contenu est modifié ou supprimé** pendant la période de rétention, une copie du contenu d’origine tel qu’il existait lors de l’attribution des paramètres de rétention est créée dans la bibliothèque de conservation et de préservation des documents. Là, le travail du minuteur identifie les éléments dont la période de rétention a expiré. Ces éléments sont déplacés vers la corbeille de second niveau, où ils sont définitivement supprimés au bout de 93 jours. La corbeille second niveau n’est pas visible par les utilisateurs finaux (seule le premier niveau de la corbeille l’est), mais les administrateurs de collection de sites peuvent afficher et restaurer du contenu à partir de cet emplacement.

    > [!NOTE]
    > Pour éviter toute perte de données par inadvertance, nous ne supprimons plus définitivement le contenu de la bibliothèque de conservation. Au lieu de cela, nous ne supprimons définitivement que le contenu de la corbeille de façon à ce que tout le contenu de la bibliothèque de conservation et de préservation passe transmis par la corbeille second niveau .
    
2. **Si le contenu n’est ni modifié ni supprimé** pendant la période de rétention, le travail de minuteur déplace le contenu vers la corbeille de premier niveau à la fin de la période de rétention. Si un utilisateur supprime le contenu à partir de là ou vide cette Corbeille (action également nommée « purge »), le document est déplacé vers la Corbeille second niveau. La période de rétention de 93 jours concerne tant la corbeille premier niveau que la corbeille second niveau. À la fin des 93 jours, le document est définitivement supprimé de l’emplacement en question (corbeille premier niveau ou second niveau). La Corbeille n’est pas indexée et n’est donc pas disponible pour les recherches. Par conséquent, une recherche eDiscovery ne peut pas trouver de contenu de la Corbeille auquel appliquer une conservation.

Lorsque les paramètres de la stratégie de rétention sont définis sur conserver uniquement ou supprimer uniquement, les chemins d’accès du contenu sont des variantes de l’option conserver et supprimer :

### <a name="content-paths-for-retain-only-retention-settings"></a>Chemins d’accès du contenu pour la stratégie de rétention de conservation uniquement

1. **Si le contenu est modifié ou supprimé** pendant la période de rétention : une copie du document d’origine est créée dans la bibliothèque de conservation et de préservation et conservée jusqu’à la fin de la période de rétention, lorsque celle-ci est déplacée vers la corbeille second niveau et supprimée définitivement après 93 jours.

2. **Si le contenu n’est pas modifié ou supprimé** pendant la période de rétention : rien ne se passe avant et après la période de rétention ; le document reste à son emplacement d’origine.

### <a name="content-paths-for-delete-only-retention-settings"></a>Chemins d’accès au contenu pour les paramètres de rétention uniquement pour la suppression

1. **Si le contenu est supprimé** pendant la période configurée : le document est déplacé vers la corbeille de premier niveau. Si un utilisateur supprime le contenu à partir de là ou vide cette corbeille, le document est déplacé vers la corbeille second niveau. La période de rétention de 93 jours concerne tant la corbeille premier niveau que la corbeille second niveau. À la fin des 93 jours, le document est définitivement supprimé de l’emplacement en question (corbeille premier niveau ou second niveau). Si le contenu est modifié pendant la période configurée, il suit le même chemin de suppression après la période configurée.

2. **Si le contenu n’est pas supprimé** pendant la période configurée : à la fin de la période configurée dans la stratégie de rétention, le document est déplacé vers la corbeille de premier niveau. Si un utilisateur supprime le contenu à partir de là ou vide cette corbeille (action également nommée « purge »), le document est déplacé vers la corbeille second niveau. La période de rétention de 93 jours concerne tant la corbeille premier niveau que la corbeille second niveau. À la fin des 93 jours, le document est définitivement supprimé de l’emplacement en question (corbeille premier niveau ou second niveau). La Corbeille n’est pas indexée et n’est donc pas disponible pour les recherches. Par conséquent, une recherche eDiscovery ne peut pas trouver de contenu de la Corbeille auquel appliquer une conservation.

## <a name="how-retention-works-for-onenote-content"></a>Fonctionnement de la rétention pour le contenu OneNote

Lorsque vous appliquez une stratégie de rétention à un emplacement qui inclut du contenu OneNote, en arrière-plan, les différentes sections OneNote constituent des fichiers séparés. Cela signifie que chaque section est conservée et supprimée séparément, conformément aux paramètres de rétention que vous spécifiez.

## <a name="how-retention-works-with-document-versions"></a>Fonctionnement de la rétention avec des versions de documents

Le contrôle de version est une fonctionnalité présente dans toutes listes et les bibliothèques de documents dans SharePoint et OneDrive. Par défaut, le contrôle de version conserve au moins les 500 versions principales, même si vous pouvez augmenter cette limite. Pour plus d’informations, consultez [Activer et configurer le contrôle de version pour une liste ou une bibliothèque](https://support.office.com/article/1555d642-23ee-446a-990a-bcab618c7a37) et [Fonctionnement du contrôle de version dans les listes et les bibliothèques](https://support.microsoft.com/office/how-versioning-works-in-lists-and-libraries-0f6cd105-974f-44a4-aadb-43ac5bdfd247).
  
Lorsqu’un document avec plusieurs versions est soumis à des paramètres de rétention pour conserver le contenu, les versions copiées dans la bibliothèque de conservation et de préservation des documents sont des éléments distincts. Si vous avez configuré les paramètres de rétention pour suppression à la fin de la période de rétention :

- Si la période de rétention est basée sur la date de création du contenu, chaque version comporte la même date d’expiration que le document d’origine. Le document d’origine et toutes ses versions expirent en même temps.

- Si la période de rétention est basée sur la date de la dernière modification du contenu, chaque version possède sa propre date d’expiration basée sur la date à laquelle le document d’origine a été modifié pour créer cette version. Le document d’origine et ses versions expirent séparément l’un de l’autre.

> [!NOTE]
> Les versions conservées des documents SharePoint et OneDrive ne sont pas consultables par les outils eDiscovery.

Lorsque l’action de rétention consiste à supprimer le document, elle supprime simultanément toutes les versions absentes de la bibliothèque de conservation et de préservation des documents, en fonction de la version actuelle.

Pour les éléments soumis à une stratégie de rétention (ou une conservation eDiscovery), le programme ignore les limites de contrôle de version de la bibliothèque de documents jusqu’à la période de rétention du document (où jusqu’à la fin de la conservation eDiscovery).Dans ce scénario, les anciennes versions ne sont pas purgées automatiquement et les utilisateurs ne peuvent pas supprimer les versions.

Ce n’est pas le cas des étiquettes de rétention lorsque le contenu n’est pas soumis à une stratégie de rétention (ou à une conservation eDiscovery). Au lieu de cela, les limites de contrôle de version sont honorées de sorte que les versions antérieures soient automatiquement supprimées afin de pouvoir accueillir les nouvelles versions, mais les utilisateurs ne peuvent pas supprimer les versions.

## <a name="when-a-user-leaves-the-organization"></a>Lorsqu’un utilisateur quitte l’organisation

**SharePoint** :

Lorsqu’un utilisateur quitte votre organisation, le contenu qu’il a créé n’est pas affecté car SharePoint est considéré comme un environnement collaboratif, contrairement à la boîte aux lettres ou au compte OneDrive de l’utilisateur.

**OneDrive** :

Si un utilisateur quitte votre organisation, tous les fichiers soumis à une stratégie de rétention ou contenant des étiquettes de rétention sont conservés pendant toute la durée de la stratégie ou de l’étiquette. Pendant cette période, tous les accès partagés continuent de fonctionner. À expiration de la période de rétention, le contenu est placé dans la Corbeille de collections de sites et n’est accessible à personne, à l’exception de l’administrateur. Si un document est marqué en tant qu’enregistrement par une étiquette de rétention, il est conservé jusqu’à la fin de la période de rétention, après quoi le contenu est définitivement supprimé.

## <a name="configuration-guidance"></a>Instructions de configuration

Si vous n’avez jamais configurer la rétention dans Microsoft 365, voir [Prise en main des stratégies et des étiquettes de rétention](get-started-with-retention.md).

Si vous êtes prêt à configurer une stratégie ou une étiquette de rétention pour Exchange, consultez les instructions suivantes :
- [Créer et configurer des stratégies de rétention](create-retention-policies.md)
- [Créer des étiquettes de rétention et les appliquer dans les applications](create-apply-retention-labels.md)
- [Appliquer automatiquement une étiquette de rétention au contenu](apply-retention-labels-automatically.md)