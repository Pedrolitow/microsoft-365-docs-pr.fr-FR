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
ms.localizationpriority: high
ms.collection:
- purview-compliance
- tier1
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Découvrez le fonctionnement de la rétention Microsoft 365 pour SharePoint et OneDrive, à l’aide de stratégies de rétention et d’étiquettes de rétention pour gérer la rétention automatique ou la suppression des données pour votre organisation.
ms.openlocfilehash: dc694171b6964b728a983597a246eb2446c9f472
ms.sourcegitcommit: 04e517c7e00323b5c33d8ea937115725cf2cfd4d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2022
ms.locfileid: "68564758"
---
# <a name="learn-about-retention-for-sharepoint-and-onedrive"></a>Découvrir la rétention pour SharePoint et OneDrive

>*[Guide de sécurité et conformité pour les licences Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Les informations contenues dans cet article complètent l’article [Découvrir la rétention](retention.md), car elles contiennent des informations spécifiques à SharePoint et OneDrive.

Pour les autres charges de travail, consultez:

- [En savoir plus sur la rétention dans Microsoft Teams](retention-policies-teams.md)
- [Découvrir la rétention pour Yammer](retention-policies-yammer.md)
- [Découvrir la rétention pour Exchange](retention-policies-exchange.md)

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="whats-included-for-retention-and-deletion"></a>Éléments composant la rétention et la suppression

Tous les fichiers stockés dans SharePoint ou OneDrive peuvent être conservés en appliquant une stratégie de rétention ou une étiquette de rétention. 

Les fichiers suivants peuvent être supprimés:

- Lorsque vous utilisez une stratégie de rétention : tous les fichiers dans les bibliothèques de documents, y compris les bibliothèques de documents SharePoint créées automatiquement, telles que **Eléments de site**.
    
- Lorsque vous utilisez des étiquettes de rétention : tous les fichiers dans toutes les bibliothèques de documents et tous les fichiers au niveau racine qui ne se trouvent pas dans un dossier.
    
> [!TIP]
> Lorsque vous utilisez une [requête avec une stratégie d’application automatique pour une étiquette de rétention](apply-retention-labels-automatically.md#auto-apply-labels-to-content-with-keywords-or-searchable-properties), vous pouvez exclure des bibliothèques de documents à l’aide de cette entrée : `NOT(DocumentLink:"<URL to document library>")`

Les éléments de liste ne sont pas pris en charge par les stratégies de rétention, mais sont pris en charge par les étiquettes de rétention à l’exception des éléments dans les listes. Il s’agit de listes masquées permettant à SharePoint de gérer le système et d’inclure le catalogue de pages maîtres, le catalogue de solutions et les sources de données. Lorsque des étiquettes de rétention sont appliquées à des éléments de liste pris en charge, elles sont toujours conservées en fonction des paramètres de rétention, mais pas supprimées si elles sont masquées dans la recherche.

Lorsque vous appliquez une étiquette de rétention à un élément de liste pris en charge qui contient une pièce jointe au document :
- Pour une étiquette de rétention standard (qui ne déclare pas l'élément comme étant un document) :
    - La pièce jointe au document n’hérite pas automatiquement des paramètres de rétention de l’étiquette, mais peut être étiquetée de manière indépendante.
- Pour une étiquette de rétention qui déclare que l'élément est un document : 
    - La pièce jointe du document hérite automatiquement des paramètres de rétention de l'étiquette si le document n'est pas déjà étiqueté.

Les paramètres de rétention des stratégies de rétention et des étiquettes de rétention ne s’appliquent pas à l’organisation de structures qui incluent des bibliothèques, des listes et des dossiers.

Pour les stratégies de rétention et les stratégies d’application automatique des étiquettes : l’indexation des sites SharePoint est nécessaire pour l’application des paramètres de rétention. Cependant, si des éléments dans les bibliothèques de documents SharePoint sont configurés pour ne pas s’afficher dans les résultats de la recherche, cette configuration n’exclut pas les fichiers des paramètres de rétention.


## <a name="how-retention-works-for-sharepoint-and-onedrive"></a>Fonctionnement de la rétention pour SharePoint et OneDrive

Pour stocker les contenus qui doivent être conservés, SharePoint et OneDrive créent une bibliothèque de conservation et de préservation des documents si elle n'existe pas. La bibliothèque de conservation et de préservation des documents n’est pas conçue pour être utilisée de manière interactive, mais stocke automatiquement les fichiers lorsque cela est nécessaire pour des raisons de conformité. Elle fonctionne de la manière suivante :

Lorsqu’un utilisateur modifie un élément soumis à rétention à partir d’une stratégie de rétention ou d’une étiquette de rétention qui marque les éléments en tant qu’enregistrement ou supprime tout élément soumis à rétention, le contenu d’origine est copié dans la bibliothèque de conservation de la conservation. Ce comportement permet à l’utilisateur de modifier ou de supprimer le contenu de son application, tout en conservant une copie de l’original pour des raisons de conformité.

Un travail du minuteur s’exécute régulièrement dans la bibliothèque de conservation et de préservation des documents. Pour le contenu ayant passé plus de 30 jours dans la bibliothèque de conservation et de préservation des documents, ce travail compare le contenu à toutes les requêtes utilisées par les paramètres de rétention de ce contenu. Le contenu plus ancien que la période de rétention configurée est ensuite supprimé de la bibliothèque de conservation et de préservation des documents, et de l’emplacement d’origine s’il est toujours là. Ce travail de timer s’exécute tous les sept jours, ce qui signifie qu’avec un minimum de 30 jours, la suppression du contenu de la bibliothèque de conservation et de préservation des documents peut prendre jusqu’à 37 jours.

This behavior for copying files into the Preservation Hold library applies to content that exists when the retention settings were applied. In addition, for retention policies, any new content that's created or added to the site after it was included in the policy will be retained in the Preservation Hold library. However, new content isn't copied to the Preservation Hold library the first time it's edited, only when it's deleted. To retain all versions of a file, [versioning](#how-retention-works-with-document-versions) must be turned on for the original site.
  
Les utilisateurs voient un message d'erreur s'ils essaient de supprimer une bibliothèque, une liste, un dossier ou un site qui est soumis à la conservation. Ils peuvent supprimer un dossier sans étiquette s’ils déplacent ou suppriment d’abord les fichiers du dossier soumis à rétention.

Les utilisateurs voient également un message d’erreur s’ils tentent de supprimer un élément étiqueté dans l’une des situations suivantes. L’élément n’est pas copié dans la bibliothèque de conservation et de préservation des documents, mais reste à l’emplacement d’origine :

- Le paramètre de gestion des enregistrements qui permet aux utilisateurs de supprimer des éléments étiquetés est désactivé.
    
    To check or change this setting, go to the **Records management** solution in the Microsoft Purview compliance portal > **Records management** > **Records management settings** > **Retention labels** > **Deletion of items**. There are separate settings for SharePoint and OneDrive.
    
    Sinon, et si vous n’avez pas accès à la solution de **gestion des enregistrements**, vous pouvez utiliser *AllowFilesWithKeepLabelToBeDeletedSPO* et *AllowFilesWithKeepLabelToBeDeletedODB* à partir de [Get-PnPTenant](https://pnp.github.io/powershell/cmdlets/Get-PnPTenant.html) et [Set-PnPTenant](https://pnp.github.io/powershell/cmdlets/Set-PnPTenant.html).

- L’étiquette de rétention marque les éléments en tant qu’enregistrements et elle est [verrouillée](record-versioning.md).
    
    Ce n’est que lorsque l’enregistrement est déverrouillé qu’une copie de la dernière version est stockée dans la bibliothèque de conservation et de préservation des documents.

- L’étiquette de rétention marque les éléments en tant qu’[enregistrements réglementaires](records-management.md#compare-restrictions-for-what-actions-are-allowed-or-blocked), ce qui empêche continuellement la modification ou la suppression de l’élément.

Une fois que les paramètres de rétention sont attribués à un compte OneDrive ou un site SharePoint, les chemins d’accès au contenu sont fonction des paramètres de rétention qui consistent à conserver et à supprimer, à conserver uniquement ou à supprimer uniquement. Dans les explications qui suivent, le contenu modifié est déplacé vers la bibliothèque de conservation des conservations pour les stratégies de rétention et les étiquettes de rétention qui marquent les éléments en tant qu’enregistrements (et le contenu est déverrouillé). Les éléments modifiés avec des étiquettes de rétention qui ne marquent pas les éléments en tant qu’enregistrements ne créent pas de copies dans la bibliothèque de conservation de la conservation, mais le font lorsque des éléments sont supprimés.

Lorsque les paramètres de la stratégie de rétention consistent à conserver et supprimer :

![Diagramme de cycle de vie de contenu dans SharePoint et OneDrive.](../media/Retention_Diagram_of_retention_flow_in_sites.png)
  
1. **Si le contenu est modifié ou supprimé** pendant la période de rétention, une copie du contenu d’origine tel qu’il existait lors de l’attribution des paramètres de rétention est créée dans la bibliothèque de conservation et de préservation des documents. Là, le travail du minuteur identifie les éléments dont la période de rétention a expiré. Ces éléments sont déplacés vers la corbeille de second niveau, où ils sont définitivement supprimés au bout de 93 jours. La corbeille second niveau n’est pas visible par les utilisateurs finaux (seule le premier niveau de la corbeille l’est), mais les administrateurs de collection de sites peuvent afficher et restaurer du contenu à partir de cet emplacement.

    > [!NOTE]
    > Pour éviter toute perte de données par inadvertance, nous ne supprimons plus définitivement le contenu de la bibliothèque de conservation. Au lieu de cela, nous ne supprimons définitivement que le contenu de la corbeille de façon à ce que tout le contenu de la bibliothèque de conservation et de préservation passe transmis par la corbeille second niveau .
    
2. **If the content is not modified or deleted** during the retention period, the timer job moves this content to the first-stage Recycle Bin at the end of the retention period. If a user deletes the content from there or empties this Recycle Bin (also known as purging), the document is moved to the second-stage Recycle Bin. A 93-day retention period spans both the first- and second-stage recycle bins. At the end of 93 days, the document is permanently deleted from wherever it resides, in either the first-stage or second-stage Recycle Bin. The Recycle Bin is not indexed and therefore unavailable for searching. As a result, an eDiscovery search can't find any Recycle Bin content on which to place a hold.

> [!NOTE]
> En raison du [premier principe de rétention](retention.md#the-principles-of-retention-or-what-takes-precedence), la suppression définitive est toujours suspendue si le même élément doit être retenu à cause d’une autre stratégie de rétention ou d’une étiquette de rétention ou qu’il est bloqué pour des raisons juridiques ou d’enquête.

Lorsque les paramètres de la stratégie de rétention sont définis sur conserver uniquement ou supprimer uniquement, les chemins d’accès du contenu sont des variantes de l’option conserver et supprimer :

### <a name="content-paths-for-retain-only-retention-settings"></a>Chemins d’accès du contenu pour la stratégie de rétention de conservation uniquement

1. **Si le contenu est modifié ou supprimé** pendant la période de rétention : une copie du document d’origine est créée dans la bibliothèque de conservation et de préservation et conservée jusqu’à la fin de la période de rétention, lorsque celle-ci est déplacée vers la corbeille second niveau et supprimée définitivement après 93 jours.

2. **Si le contenu n’est pas modifié ou supprimé** pendant la période de rétention : rien ne se passe avant et après la période de rétention ; le document reste à son emplacement d’origine.

### <a name="content-paths-for-delete-only-retention-settings"></a>Chemins d’accès au contenu pour les paramètres de rétention uniquement pour la suppression

1. **Si le contenu est supprimé** pendant la période configurée : le document est déplacé vers la corbeille de premier niveau. Si un utilisateur supprime le contenu à partir de là ou vide cette corbeille, le document est déplacé vers la corbeille second niveau. La période de rétention de 93 jours concerne tant la corbeille premier niveau que la corbeille second niveau. À la fin des 93 jours, le document est définitivement supprimé de l’emplacement en question (corbeille premier niveau ou second niveau). Si le contenu est modifié pendant la période configurée, il suit le même chemin de suppression après la période configurée.

2. **If the content is not deleted** during the configured period: At the end of the configured period in the retention policy, the document is moved to the first-stage Recycle Bin. If a user deletes the document from there or empties this Recycle Bin (also known as purging), the document is moved to the second-stage Recycle Bin. A 93-day retention period spans both the first-stage and second-stage recycle bins. At the end of 93 days, the document is permanently deleted from wherever it resides, in either the first-stage or second-stage Recycle Bin. The Recycle Bin is not indexed and therefore unavailable for searching. As a result, an eDiscovery search can't find any Recycle Bin content on which to place a hold.

## <a name="how-retention-works-with-cloud-attachments"></a>Fonctionnement de la rétention avec les pièces jointes cloud

Les pièces jointes dans le cloud sont des liens incorporés vers des fichiers partagés par les utilisateurs, qui peuvent être conservés et supprimés lorsque vos utilisateurs les partagent dans Outlook courriers électroniques et Teams messages électroniques. Lorsque vous appliquez automatiquement une étiquette de rétention aux pièces [jointes](apply-retention-labels-automatically.md#auto-apply-labels-to-cloud-attachments)cloud, l’étiquette de rétention est appliquée à une copie du fichier partagé, qui est stocké dans la bibliothèque de conservation et de préservation des documents.

Pour ce scénario, nous vous recommandons de configurer le paramètre d’étiquette pour démarrer la période de rétention en fonction du moment où l’élément est étiqueté. Si vous configurez la période de rétention en fonction de la date de création ou de dernière modification de l’élément, cette date est tirée du fichier d’origine au moment du partage. Si vous configurez le début de la rétention à la dernière modification, ce paramètre n’a aucun effet sur cette copie dans la bibliothèque de conservation et de préservation des documents.

Toutefois, si le fichier d’origine est modifié, puis partagé à nouveau, une nouvelle copie du fichier en tant que nouvelle version est enregistrée et étiquetée dans la bibliothèque de conservation et de préservation des données.

Si le fichier d’origine est partagé à nouveau mais n’est pas modifié, la date étiquetée de la copie dans la bibliothèque de conservation et de préservation des données est mise à jour. Cette action réinitialise le début de la période de rétention et c’est pourquoi nous vous recommandons de configurer le début de la période de rétention en fonction du moment où l’élément est étiqueté.

Étant donné que l’étiquette de rétention n’est pas appliquée au fichier d’origine, le fichier étiqueté n’est jamais modifié ou supprimé par un utilisateur. Le fichier étiqueté reste dans la bibliothèque Preservation Hold jusqu'à ce que le travail de minuterie identifie que sa période de conservation a expiré. Si les paramètres de rétention sont configurés pour supprimer des éléments, le fichier est ensuite déplacé vers la Corbeille second niveau, où il est définitivement supprimé au bout de 93 jours :

![Fonctionnement de la rétention pour les pièces jointes cloud stockées dans SharePoint et OneDrive](../media/retention-diagram-of-retention-flow-cloud-attachments.png)

La copie stockée dans la bibliothèque de conservation et de préservation des données est généralement créée dans l’heure qui s’agit de la pièce jointe cloud partagée.

Pour vous protéger contre la suppression du fichier d’origine par les utilisateurs avant que la copie puisse être créée et étiquetée, les fichiers situés dans les emplacements inclus dans la stratégie d’étiquetage automatique sont automatiquement copiés dans la bibliothèque de conservation de la conservation, s’ils sont supprimés. Ces fichiers ont une période de rétention temporaire d’une journée, puis suivent le processus de nettoyage standard décrit sur cette page. Une fois le fichier d’origine supprimé, la copie permettant de conserver les pièces jointes cloud utilise cette version du fichier. La conservation automatique et temporaire des fichiers supprimés dans la bibliothèque de conservation est unique aux stratégies d’étiquetage automatique pour les pièces jointes cloud.

## <a name="how-retention-works-with-onenote-content"></a>Fonctionnement de la rétention avec OneNote contenu

Lorsque vous appliquez une stratégie de rétention à un emplacement qui inclut du contenu OneNote ou une étiquette de rétention à un dossier OneNote, en arrière-plan, les différentes pages et sections OneNote sont des fichiers individuels qui héritent des paramètres de rétention. Cela signifie que chaque section d’une page sera conservée et supprimée individuellement, conformément aux paramètres de rétention que vous spécifiez.

Seules les pages et sections sont touchées par les paramètres de rétention que vous spécifiez. Par exemple, même si vous voyez une date de **modification** pour chaque bloc-notes individuel, cette date n’est pas utilisée par Microsoft 365 rétention.

## <a name="how-retention-works-with-document-versions"></a>Fonctionnement de la rétention avec des versions de documents

Versioning is a feature of all document lists and libraries in SharePoint and OneDrive. By default, versioning retains a minimum of 500 major versions, although you can increase this limit. For more information, see [Enable and configure versioning for a list or library](https://support.office.com/article/1555d642-23ee-446a-990a-bcab618c7a37) and [How versioning works in lists and libraries](https://support.microsoft.com/office/how-versioning-works-in-lists-and-libraries-0f6cd105-974f-44a4-aadb-43ac5bdfd247).
  
Lorsqu’un document comportant des versions est soumis à des paramètres de conservation pour conserver ce contenu, la façon dont les versions sont stockées dans la bibliothèque de conservation et de préservation des documents a changé en juillet 2022 pour améliorer les performances. Toutes les versions du fichier sont maintenant conservées dans un seul fichier dans la bibliothèque de conservation et de préservation des documents. Avant la modification, les versions étaient copiées dans la bibliothèque de conservation et de préservation des documents en tant que fichiers distincts et, après la modification, restent en tant que fichiers distincts.

Si vous avez configuré les paramètres de rétention pour suppression à la fin de la période de rétention :

- If the retention period is based on when the content was created, each version has the same expiration date as the original document. The original document and its versions all expire at the same time.

- Si la période de conservation est basée sur la date de la dernière modification du contenu :
    - **Après la modification où toutes les versions du fichier sont conservées dans un seul fichier dans la bibliothèque de conservation et de préservation des documents** : chaque version a la même date d’expiration que la dernière version du document. La dernière version du document et ses versions expirent toutes en même temps.
    - **Avant la modification où les versions ont été copiées dans la bibliothèque de conservation et de préservation des documents en tant que fichiers distincts** : chaque version a sa propre date d’expiration en fonction du moment où le document d’origine a été modifié pour créer cette version. Le document d’origine et ses versions expirent séparément les uns des autres.

Lorsque l’action de rétention consiste à supprimer le document, elle supprime simultanément toutes les versions absentes de la bibliothèque de conservation et de préservation des documents, en fonction de la version actuelle.

For items that are subject to a retention policy (or an eDiscovery hold), the versioning limits for the document library are ignored until the retention period of the document is reached (or the eDiscovery hold is released). In this scenario, old versions are not automatically purged and users are prevented from deleting versions.

Ce n’est pas le cas des étiquettes de rétention lorsque le contenu n’est pas soumis à une stratégie de rétention (ou à une conservation eDiscovery). Au lieu de cela, les limites de contrôle de version sont honorées de sorte que les versions antérieures soient automatiquement supprimées afin de pouvoir accueillir les nouvelles versions, mais les utilisateurs ne peuvent pas supprimer les versions.

## <a name="when-a-user-leaves-the-organization"></a>Lorsqu’un utilisateur quitte l’organisation

**SharePoint** :

Lorsqu’un utilisateur quitte votre organisation, le contenu qu’il a créé n’est pas affecté car SharePoint est considéré comme un environnement collaboratif, contrairement à la boîte aux lettres ou au compte OneDrive de l’utilisateur.

**OneDrive** :

Si un utilisateur quitte votre organisation, tous les fichiers qui sont soumis à une politique de conservation ou qui ont un label de conservation resteront soumis aux paramètres de conservation pour la durée de la période de conservation spécifiée dans la politique ou le label. Pendant ce temps, tout l’accès au partage continue de fonctionner et le contenu reste découvrable par la recherche de contenu et eDiscovery. 

Lorsque la période de rétention expire et que les paramètres de rétention incluent une action de suppression, le contenu se déplace dans la Corbeille de la collection de sites et n’est accessible à personne sauf à l’administrateur.

## <a name="configuration-guidance"></a>Instructions de configuration

Si vous débutez avec la configuration de la rétention dans Microsoft 365, consultez [Démarrage avec la gestion du cycle de vie des données](get-started-with-data-lifecycle-management.md).

Si vous êtes prêt à configurer une stratégie ou une étiquette de rétention pour Exchange, consultez les instructions suivantes :
- [Créer et configurer des stratégies de rétention](create-retention-policies.md)
- [Publier des étiquettes de rétention et les appliquer dans les applications](create-apply-retention-labels.md)
- [Appliquer automatiquement une étiquette de rétention au contenu](apply-retention-labels-automatically.md)
