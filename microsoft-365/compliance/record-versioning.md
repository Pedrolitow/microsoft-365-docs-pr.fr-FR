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
localization_priority: Priority
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Découvrir les enregistrements pour vous aider à implémenter une solution de gestion des enregistrements dans Microsoft 365.
ms.openlocfilehash: be85632bb4b85231f3a95680c960846fa245d97a
ms.sourcegitcommit: f358e321f7e81eff425fe0f0db1be0f3348d2585
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2021
ms.locfileid: "58506525"
---
# <a name="use-record-versioning-to-update-records-stored-in-sharepoint-or-onedrive"></a>Utiliser le contrôle de version des enregistrements pour mettre à jour les enregistrements stockés dans SharePoint ou OneDrive

>*[Guide de sécurité et conformité pour les licences Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

> [!NOTE]
> Parce que les enregistrements réglementaires bloquent la modification, la version de l’enregistrement n’est pas disponible pour les enregistrements réglementaires.

La possibilité de marquer un document en tant qu’[enregistrement](records-management.md#records) et de restreindre les actions pouvant être effectuées sur l’enregistrement constitue un objectif essentiel pour toute solution de gestion d’enregistrements. Cependant, une collaboration peut également être nécessaire pour permettre aux utilisateurs de créer des versions ultérieures.

Par exemple, il peut arriver que vous marquiez un contrat de vente sous forme d’un enregistrement, mais qu’ensuite vous deviez mettre à jour le contrat avec de nouvelles conditions et marquer la dernière version comme nouvel enregistrement tout en conservant la version précédente de l’enregistrement. Pour ces types de scénarios, SharePoint et OneDrive Entreprise prennent désormais en charge le *contrôle de version d’enregistrement*. Les dossiers de bloc-notes OneNote ne prennent pas en charge le contrôle de version d’enregistrement.

Pour utiliser le contrôle de version d’un enregistrement, commencez par [étiqueter le document et marquez-le en tant qu’enregistrement](declare-records.md). À ce stade, une propriété de document appelée *Statut de l’enregistrement* s’affiche en regard de l’étiquette de rétention, et le statut de l’enregistrement initial est **Verrouillé**.

Vous pouvez effectuer les actions suivantes :

- **Modifier sans limites et conserver les versions individuelles du document en tant qu’enregistrements en déverrouillant et verrouillant la propriété Statut de l’enregistrement.** Une nouvelle version de l’enregistrement est uniquement conservée lorsque la propriété **État de l’enregistrement** est définie sur **Verrouillée**. Ce bouton bascule activé/désactivé permet de réduire le risque de conserver des versions et des copies du document superflues.

- **Stockez automatiquement les enregistrements dans un référentiel d’enregistrements situé localement au sein de la collection de sites.** Chaque collection de sites dans SharePoint et OneDrive conserve le contenu dans la bibliothèque de conservation et de préservation. Les versions des enregistrements sont stockées dans le dossier Enregistrements de cette bibliothèque.

- **Tenez à jour un document évolutif contenant toutes les versions.** Par défaut, un historique des versions est disponible dans le menu élément pour chaque document SharePoint et OneDrive. Dans cet historique des versions, vous pouvez facilement identifier quelles versions sont des enregistrements et afficher ces documents.

> [!TIP]
> Lorsque vous utilisez le contrôle de version d’enregistrement avec une étiquette de rétention ayant une action de suppression, nous vous recommandons de configurer également le paramètre de rétention **Démarrer la période de rétention sur la base de :** sur **Quand des éléments ont été étiquetés**. Avec ce paramètre d’étiquette, le début de la période de rétention est réinitialisé pour chaque nouvelle version d’enregistrement, ce qui garantit que les versions antérieures seront supprimées avant les versions plus récentes.

Le contrôle de version d’enregistrement est disponible automatiquement pour tout document comportant une étiquette de rétention qui marque l’élément comme enregistrement et qui est [publiée sur le site](create-apply-retention-labels.md#step-2-publish-retention-labels). Lorsqu’un utilisateur affiche les propriétés du document à l’aide du volet Détails, il peut basculer le **Statut de l’enregistrement** de **Verrouillé** vers **Déverrouillé**. Cette action crée un enregistrement dans le dossier Enregistrements de la bibliothèque de conservation et de préservation, où il résidera jusqu’à la fin de la période de rétention.

Lorsque le document est déverrouillé, les utilisateurs disposant des autorisations de modification standard peuvent modifier le fichier. Toutefois, les utilisateurs ne peuvent pas supprimer le fichier, car il est encore considéré comme un enregistrement. Lorsque la modification est terminée, un utilisateur peut basculer vers la bascule de l’**État de l’enregistrement** de **Déverrouillé** vers **Verrouillé**, ce qui empêche les modifications ultérieures dans ce statut.
<br/><br/>

![Propriété statut de l’enregistrement sur le document marqué en tant qu’enregistrement](../media/recordversioning8.png)

## <a name="locking-and-unlocking-a-record"></a>Verrouillage et déverrouillage d'un enregistrement

Lorsqu’une étiquette de rétention qui marque le contenu en tant qu’enregistrement est appliquée à un document, tous les utilisateurs ayant des autorisations de collaboration ou un niveau d'autorisation plus réduit peuvent déverrouiller un enregistrement ou verrouiller un enregistrement déverrouillé.
<br/><br/>

![Le statut de l’enregistrement indique que le document enregistré est déverrouillé](../media/recordversioning9.png)

Lorsqu’un utilisateur déverrouille un enregistrement, il se produit les actions suivantes :

1. Si la collection de sites actuelle ne possède pas de bibliothèque de conservation et de préservation, une bibliothèque est créée.

2. Si la bibliothèque de conservation et de préservation ne possède pas de dossier Enregistrements, un dossier est créé.

3. Une action **Copier vers** copie la dernière version du document dans le dossier Enregistrements. L’action **Copier vers** inclut uniquement la dernière version et aucune version antérieure. Ce document copié est désormais considéré comme une version d’enregistrement du document et son nom de fichier présente le format suivant : \[Titre GUID Version\#\]

4. La copie créée dans le dossier Enregistrements est ajoutée à l’historique des versions du document d’origine et cette version affiche le mot **Enregistrement** dans le champ commentaires.

5. Le document d’origine est une nouvelle version qui peut être modifiée, mais pas supprimée. La colonne bibliothèque de documents **L’Élément est un Enregistrement** affiche toujours la valeur **Oui** parce que le document est encore considéré comme un enregistrement, même s’il peut désormais être modifié.

Lorsqu’un utilisateur verrouille un enregistrement, le document d’origine ne peut pas être modifié. Mais c’est l’action de déverrouiller un enregistrement qui copie une version dans le dossier Enregistrements de la bibliothèque de conservation et de préservation.

## <a name="record-versions"></a>Versions d’enregistrement

Chaque fois qu’un utilisateur déverrouille un enregistrement, la version la plus récente est copiée dans la bibliothèque de conservation et de préservation des documents et cette version contient la valeur **Enregistrement** dans le champ **Commentaires** de l’historique des versions.
<br/><br/>

![Enregistrement affiché dans la bibliothèque de conservation et de préservation](../media/recordversioning10.png)

Pour afficher l’historique des versions, sélectionnez un document dans la bibliothèque de documents, puis cliquez sur **Historique des versions** dans le menu élément.

## <a name="where-records-are-stored"></a>Où sont stockés les enregistrements

Les enregistrements sont stockés dans le dossier Enregistrements de la bibliothèque de conservation et de préservation du site de niveau supérieur de la collection de sites. Dans le volet de navigation gauche, dans le site de niveau supérieur, sélectionnez **Contenu du site** \> **Bibliothèque de conservation et de préservation**.
<br/><br/>

![Bibliothèque de conservation et de préservation](../media/recordversioning11.png)

<br/><br/>

![Dossier Enregistrements dans la bibliothèque de conservation et de préservation](../media/recordversioning12.png)

Pour plus d’informations sur le fonctionnement de la bibliothèque de conservation et de préservation des documents, consultez [Fonctionnement de la rétention pour SharePoint et OneDrive](retention-policies-sharepoint.md#how-retention-works-for-sharepoint-and-onedrive).

## <a name="searching-the-audit-log-for-record-versioning-events"></a>Rechercher dans le journal d’audit les événements de contrôle de version d’enregistrement

Les actions de verrouillage et déverrouillage des enregistrements sont enregistrées dans le journal d’audit. Dans **Activités de fichier et de page**, sélectionnez **Modification de l’état de l’enregistrement à « verrouillé»,** et **Modification de l’état de l’enregistrement à « déverrouillé »**.

Pour plus d’informations sur la recherche de ces événements, consultez [Effectuer une recherche dans le journal d’audit](search-the-audit-log-in-security-and-compliance.md#file-and-page-activities).

## <a name="next-steps"></a>Étapes suivantes

Pour les autres scénarios pris en charge par la gestion des enregistrements, consultez [Scénarios courants pour la gestion des enregistrements](get-started-with-records-management.md#common-scenarios-for-records-management).
