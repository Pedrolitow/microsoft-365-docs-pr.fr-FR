---
title: Utiliser le contrôle de version des enregistrements pour mettre à jour les enregistrements stockés dans SharePoint ou OneDrive
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
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Découvrir les enregistrements pour vous aider à implémenter une solution de gestion des enregistrements dans Microsoft 365.
ms.openlocfilehash: 7fc4f9bb14e9e49c7894e864b8ff9e8f4337149a
ms.sourcegitcommit: 5eff41a350a01e18d9cdd572c9d8ff99d6c9563a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2022
ms.locfileid: "64835884"
---
# <a name="use-record-versioning-to-update-records-stored-in-sharepoint-or-onedrive"></a>Utiliser le contrôle de version des enregistrements pour mettre à jour les enregistrements stockés dans SharePoint ou OneDrive

>*[Guide de sécurité et conformité pour les licences Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

> [!NOTE]
> Parce que les enregistrements réglementaires bloquent la modification, la version de l’enregistrement n’est pas disponible pour les enregistrements réglementaires.
>
> Vous pouvez également empêcher le contrôle de version des enregistrements pour votre client, même si vous n’utilisez pas d’enregistrements réglementaires : accédez au nœud de **Gestion des enregistrements** dans le Centre de conformité Microsoft 365 > **Paramètres de gestion des enregistrements** > **Étiquettes de rétention** > **Configurer le contrôle de version des enregistrements** puis désactiver le paramètre pour **Activer le contrôle de version des enregistrements**.

La possibilité de marquer un document en tant qu’[enregistrement](records-management.md#records) et de restreindre les actions pouvant être effectuées sur l’enregistrement constitue un objectif essentiel pour toute solution de gestion d’enregistrements. Toutefois, une collaboration peut également être nécessaire pour que les utilisateurs puissent créer les versions suivantes.

Par exemple, il peut arriver que vous marquiez un contrat de vente sous forme d’un enregistrement, mais qu’ensuite vous deviez mettre à jour le contrat avec de nouvelles conditions et marquer la dernière version comme nouvel enregistrement tout en conservant la version précédente de l’enregistrement. Pour ces types de scénarios, SharePoint et OneDrive Entreprise prennent désormais en charge le *contrôle de version d’enregistrement*. Les dossiers de bloc-notes OneNote ne prennent pas en charge le contrôle de version d’enregistrement.

Pour utiliser le contrôle de version des enregistrements, vous devez d'abord étiqueter le document avec une étiquette de conservation [ qui est configurée pour marquer les éléments en tant qu'enregistrement ](declare-records.md). À ce stade, une propriété du document, appelée *État de l'enregistrement*, est affichée à côté de l'étiquette de rétention. Selon que l'étiquette est configurée pour déverrouiller l'enregistrement par défaut (actuellement en cours de déploiement), l'état initial de l'enregistrement est soit **Verrouillé**, soit **Déverrouillé**.

Vous pouvez effectuer les actions suivantes :

- **Modifier sans limites et conserver les versions individuelles du document en tant qu’enregistrements en déverrouillant et verrouillant la propriété Statut de l’enregistrement.** Une nouvelle version de l’enregistrement est uniquement conservée lorsque la propriété **État de l’enregistrement** est définie sur **Verrouillée**. Ce bouton bascule activé/désactivé permet de réduire le risque de conserver des versions et des copies du document superflues.
    
    > [!NOTE]
    > Si l'étiquette est configurée pour déverrouiller le document par défaut, mais que le contrôle de version n'est pas activé par l'administrateur, ou empêché par le paramètre de gestion des documents, les utilisateurs ne pourront pas déverrouiller le document après l'avoir verrouillé.

- **Faites en sorte que les documents soient automatiquement stockés dans un dépôt de documents sur place, situé sur le site**.  Chaque site dans SharePoint et OneDrive conserve le contenu dans sa bibliothèque de conservation de conservation. Les versions des enregistrements sont stockées dans le dossier Enregistrements de cette bibliothèque. Pour plus d’informations sur le fonctionnement de la bibliothèque de conservation et de préservation des documents, consultez [Fonctionnement de la rétention pour SharePoint et OneDrive](retention-policies-sharepoint.md#how-retention-works-for-sharepoint-and-onedrive).

- **Tenez à jour un document évolutif contenant toutes les versions.** Par défaut, un historique des versions est disponible dans le menu élément pour chaque document SharePoint et OneDrive. Dans cet historique des versions, vous pouvez facilement identifier quelles versions sont des enregistrements et afficher ces documents.

> [!TIP]
> Lorsque vous utilisez le contrôle de version d’enregistrement avec une étiquette de rétention ayant une action de suppression, nous vous recommandons de configurer également le paramètre de rétention **Démarrer la période de rétention sur la base de :** sur **Quand des éléments ont été étiquetés**. Avec ce paramètre d’étiquette, le début de la période de rétention est réinitialisé pour chaque nouvelle version d’enregistrement, ce qui garantit que les versions antérieures seront supprimées avant les versions plus récentes.

Par défaut, le contrôle de version des enregistrements est automatiquement disponible pour tout document auquel est appliquée une étiquette de conservation qui marque l'élément comme un enregistrement, et cette étiquette est [publiée sur le site](create-apply-retention-labels.md). Lorsqu'un utilisateur visualise les propriétés du document à l'aide du volet de détails, il peut faire basculer **l'état de l'enregistrement** entre **verrouillé** et **déverrouillé**.

Lorsque le document est déverrouillé, les utilisateurs disposant des autorisations de modification standard peuvent modifier le fichier. Toutefois, les utilisateurs ne peuvent pas supprimer le fichier, car il est encore considéré comme un enregistrement. Lorsque la modification est terminée, un utilisateur peut basculer vers la bascule de l’**État de l’enregistrement** de **Déverrouillé** vers **Verrouillé**, ce qui empêche les modifications ultérieures dans ce statut.
<br/><br/>

:::image type="content" alt-text="Propriété statut de l’enregistrement sur le document marqué en tant qu’enregistrement." source="../media/recordversioning8.png" lightbox="../media/recordversioning8.png":::

Pour plus d'informations sur les actions de l'utilisateur autorisées lorsqu'un enregistrement est verrouillé ou déverrouillé, voir [Comparer les restrictions concernant les actions autorisées ou bloquées](records-management.md#compare-restrictions-for-what-actions-are-allowed-or-blocked).

## <a name="locking-and-unlocking-a-record"></a>Verrouillage et déverrouillage d'un enregistrement

Lorsqu’une étiquette de rétention qui marque le contenu en tant qu’enregistrement est appliquée à un document, tous les utilisateurs ayant des autorisations de collaboration ou un niveau d'autorisation plus réduit peuvent déverrouiller un enregistrement ou verrouiller un enregistrement déverrouillé.
<br/><br/>

:::image type="content" alt-text="Le statut de l’enregistrement indique que le document enregistré est déverrouillé." source="../media/recordversioning9.png" lightbox="../media/recordversioning9.png":::

Lorsqu’un enregistrement est déverrouillé, les actions suivantes se produisent :

1. Si le site actuel n’a pas de bibliothèque de conservation de conservation, une bibliothèque est créée.

2. Si la bibliothèque de conservation et de préservation ne possède pas de dossier Enregistrements, un dossier est créé.

3. Une action **Copier vers** copie la dernière version du document dans le dossier Enregistrements. L’action **Copier vers** inclut uniquement la dernière version et aucune version antérieure. Ce document copié est désormais considéré comme une version d’enregistrement du document et son nom de fichier présente le format suivant : \[Titre GUID Version\#\]

4. La copie créée dans le dossier Enregistrements est ajoutée à l’historique des versions du document d’origine et cette version affiche le mot **Enregistrement** dans le champ commentaires.

5. Le document d’origine est une nouvelle version qui peut être modifiée, mais pas supprimée. La colonne bibliothèque de documents **L’Élément est un Enregistrement** affiche toujours la valeur **Oui** parce que le document est encore considéré comme un enregistrement, même s’il peut désormais être modifié.

Lorsqu’un utilisateur verrouille un enregistrement, le document d’origine ne peut pas être modifié. Mais c’est l’action de déverrouiller un enregistrement qui copie une version dans le dossier Enregistrements de la bibliothèque de conservation et de préservation.

## <a name="record-versions"></a>Versions d’enregistrement

Chaque fois qu'un document est déverrouillé, la dernière version est copiée dans la bibliothèque Preservation Hold, et cette version contient la valeur **Record** dans le champ **Comments** de l'historique des versions.
<br/><br/>

:::image type="content" alt-text="Enregistrement affiché dans la bibliothèque de conservation et de préservation." source="../media/recordversioning10.png" lightbox="../media/recordversioning10.png":::

Pour afficher l’historique des versions, sélectionnez un document dans la bibliothèque de documents, puis cliquez sur **Historique des versions** dans le menu élément.

## <a name="searching-the-audit-log-for-record-versioning-events"></a>Rechercher dans le journal d’audit les événements de contrôle de version d’enregistrement

Les actions de verrouillage et déverrouillage des enregistrements sont enregistrées dans le journal d’audit. Dans **Activités de fichier et de page**, sélectionnez **Modification de l’état de l’enregistrement à « verrouillé»,** et **Modification de l’état de l’enregistrement à « déverrouillé »**.

Pour plus d’informations sur la recherche de ces événements, consultez [Effectuer une recherche dans le journal d’audit](search-the-audit-log-in-security-and-compliance.md#file-and-page-activities).

## <a name="next-steps"></a>Étapes suivantes

Pour les autres scénarios pris en charge par la gestion des enregistrements, consultez [Scénarios courants pour la gestion des enregistrements](get-started-with-records-management.md#common-scenarios).
