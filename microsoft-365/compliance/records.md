---
title: Vue d’ensemble des enregistrements
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
description: Pour implémenter une stratégie de gestion des enregistrements dans votre organisation Microsoft ou Office 365, utilisez des étiquettes de rétention qui déclarent du contenu sous la forme d’un enregistrement. Ensuite, publiez ou appliquez automatiquement l’étiquette de rétention d’enregistrement.
ms.openlocfilehash: ba69c9705c14c2f836f67c8747d30ee2280c6d99
ms.sourcegitcommit: e695bcfc69203da5d3d96f3d6a891664a0e27ae2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2020
ms.locfileid: "43106142"
---
# <a name="overview-of-records"></a>Vue d’ensemble des enregistrements

>*[Guide de sécurité et conformité pour les licences Microsoft 365](https://aka.ms/ComplianceSD).*

La gestion des enregistrements dans Microsoft 365 aide les organisations à respecter les stratégies d’entreprise, les obligations légales et réglementaires, tout en réduisant les risques et la responsabilité juridique.

À un niveau élevé, la déclaration de contenu en tant qu’enregistrement signifie que :

- L’élément devient immuable (un enregistrement ne peut pas être modifié ou supprimé)

- Des activités supplémentaires sur l’élément sont enregistrées

- Les enregistrements sont supprimés à l’expiration de leur période de rétention.

Vous pouvez utiliser les [étiquettes de rétention](labels.md) pour classer du contenu sous la forme d’un enregistrement. Une fois que vous avez créé des étiquettes de rétention qui déclarent des enregistrements, vous pouvez [publier](labels.md#how-retention-labels-work-with-retention-label-policies) ces étiquettes (de sorte que les utilisateurs puissent les utiliser pour classifier du contenu en tant qu’enregistrement) ou [appliquer automatiquement ces étiquettes](labels.md#applying-a-retention-label-automatically-based-on-conditions) au contenu que vous voulez classifier en tant qu’enregistrement. En utilisant les étiquettes de rétention pour déclarer des enregistrements, vous pouvez implémenter une stratégie de gestion des enregistrements simple et cohérente dans Office 365, tandis que les autres fonctionnalités de gestion des enregistrements telles que le Centre des enregistrements s’appliquent uniquement au contenu dans SharePoint Online.

Quelques rappels à propos des enregistrements :

  - **Les enregistrements sont immuables.** Une étiquette de rétention qui déclare du contenu en tant qu’enregistrement peut être appliquée au contenu dans Exchange, en plus de SharePoint et OneDrive Entreprise. Toutefois, [le contrôle de version d’enregistrement ](#record-versioning) est disponible uniquement dans SharePoint et OneDrive, et pas pour Exchange.

    Dans Exchange, le contenu étiqueté en tant qu’enregistrement est immuable jusqu’à sa suppression finale. Lorsqu’un élément Exchange est étiqueté en tant qu’enregistrement, quatre événements se produisent :

    - L’élément ne peut pas être supprimé définitivement.

    - L’élément ne peut pas être modifié.

    - L’étiquette ne peut pas être modifiée.

    - L’étiquette ne peut pas être supprimée.

  - **Enregistrements et dossiers.** Vous pouvez appliquer une étiquette de rétention à un dossier dans Exchange, SharePoint et OneDrive. Si un dossier est étiqueté en tant qu’enregistrement et que vous déplacez un élément vers ce dossier, l’élément est étiqueté en tant qu’enregistrement. Lorsque vous déplacez l’élément hors du dossier, l’élément reste étiqueté en tant qu’enregistrement.

    En outre, si vous changez l'étiquette qui est appliquée à un dossier (dans SharePoint et OneDrive) pour une étiquette de rétention qui ne déclare pas le contenu sous la forme d'un enregistrement, alors les éléments contenus dans le dossier conservent leur étiquette d'enregistrement existante.

    Pour plus d'informations sur l'application des étiquettes de rétention aux dossiers SharePoint et OneDrive, voir [Application d’une étiquette de rétention par défaut à tout le contenu dans une bibliothèque SharePoint, un dossier ou un ensemble de documents](labels.md#applying-a-default-retention-label-to-all-content-in-a-sharepoint-library-folder-or-document-set).

  - **Impossible de supprimer les enregistrements**. Si un utilisateur essaie de supprimer un enregistrement dans Exchange, l’élément est déplacé vers le dossier Éléments récupérables, comme décrit dans la rubrique [Fonctionnement d’une stratégie de rétention avec du contenu sur place](retention-policies.md#content-in-mailboxes-and-public-folders).

    Si un utilisateur essaie de supprimer un enregistrement dans SharePoint, une erreur annonce que l’élément n’a pas été supprimé, et l’élément reste dans la bibliothèque.

    ![Message indiquant que l’élément n’a pas été supprimé de SharePoint](../media/d0020726-1593-4a96-b07c-89b275e75c49.png)

    Si un utilisateur essaie de supprimer un enregistrement dans OneDrive, l’élément est déplacé vers la bibliothèque de conservation et de préservation des documents, comme décrit dans la rubrique [Fonctionnement d’une stratégie de rétention avec du contenu sur place](retention-policies.md#content-in-onedrive-accounts-and-sharepoint-sites).

  - **Les étiquettes d’enregistrement ne peuvent pas être supprimées.** Une fois qu’une étiquette d’enregistrement a été appliquée à un élément, seul l’administrateur de cet emplacement (par exemple, un administrateur de collection de sites d’un site SharePoint) peut supprimer cette étiquette d’enregistrement.

## <a name="using-retention-labels-to-declare-records"></a>Utilisation d’étiquettes de rétention pour déclarer des enregistrements

Lorsque vous créez une étiquette de rétention, vous pouvez l’utiliser pour classer le contenu en tant qu’enregistrement. Pour déclarer un contenu en tant qu'enregistrement, suivez la procédure suivante :

1. Créer une étiquette de rétention. Dans le centre de conformité Microsoft 365, accédez à **Gestion des enregistrements** \> **plan de gestion de fichiers**. Sur la page **Plan de gestion de fichiers**, cliquez sur **Créer une étiquette**.

2. Sur la page **Paramètres d’étiquette** de l’Assistant, choisissez l’option permettant de définir l’étiquette de rétention pour déclarer du contenu sous la forme d’un enregistrement.<br/>

   ![Cliquez sur la case à cocher Utiliser une étiquette pour classer du contenu en tant qu’Enregistrement](../media/recordversioning6.png)

3. [Publier](labels.md#how-retention-labels-work-with-retention-label-policies) ou [appliquer automatiquement](labels.md#applying-a-retention-label-automatically-based-on-conditions) l’étiquette de rétention aux sites SharePoint et/ou aux comptes OneDrive.

### <a name="applying-a-retention-label-to-content"></a>Application d’une étiquette de rétention au contenu

Pour Exchange, tout utilisateur disposant d’un accès en écriture à la boîte aux lettres peut appliquer une étiquette d’enregistrement à un message électronique. Pour le contenu dans SharePoint et OneDrive, tous les utilisateurs du groupe Membres par défaut (niveau d’autorisation Collaboration) peuvent appliquer une étiquette d’enregistrement au contenu. Seul un administrateur de la collection de sites peut supprimer ou modifier cette étiquette d’enregistrement une fois qu’elle a été appliquée. Comme indiqué précédemment, une étiquette de rétention qui classifie le contenu en tant qu’enregistrement peut être appliquée automatiquement au contenu.

Voici à quoi cela ressemble lorsque une étiquette d’enregistrement est appliquée à un document sur un site SharePoint ou un compte OneDrive.
<br/><br/>

![Volet Détails pour le document marqué comme enregistrement](../media/recordversioning7.png)

## <a name="record-versioning"></a>Contrôle de version d’enregistrement

Une partie essentielle de la gestion des enregistrements est la possibilité de déclarer un document sous la forme d’un enregistrement et de rendre cet enregistrement immuable. Toutefois, l’immuabilité de l’enregistrement empêche la collaboration sur le document si des personnes ont besoin de créer des versions ultérieures. Par exemple, il peut arriver que vous déclariez un contrat de vente sous la forme d’un enregistrement, mais qu’ensuite vous deviez mettre à jour le contrat avec de nouvelles conditions et déclarer la dernière version comme nouvel enregistrement tout en conservant la version précédente de l’enregistrement. Pour ce genre de cas, SharePoint Online et OneDrive Entreprise prennent désormais en charge le *contrôle de version d’enregistrement*. Les dossiers de bloc-notes OneNote ne sont pas pris en charge.

Pour utiliser le contrôle de version d’enregistrement, la première étape consiste à utiliser le Centre de conformité Microsoft 365 pour créer et publier des étiquettes de rétention qui déclarent des enregistrements sur tous les sites SharePoint et/ou les comptes OneDrive, ou les publier sur des sites SharePoint et/ou des comptes OneDrive spécifiques. L’étape suivante consiste à appliquer une étiquette de rétention d’enregistrement publiée à un document. Lorsque vous avez terminé, une propriété de document appelée *Statut de l’enregistrement* s’affiche en regard de l’étiquette de rétention, et le statut de l’enregistrement initial est **Verrouillé**. À ce stade, vous pouvez :

  - **Modifiez sans limites et déclarez les versions individuelles du document en tant qu’enregistrements en déverrouillant et verrouillant la propriété Statut de l’enregistrement.** Seules les versions déclarées en tant qu’enregistrements sont conservées lorsque la propriété **Statut de l’enregistrement** est paramétrée sur **Verrouillé**. Cela permet de réduire le risque de conserver des versions et des copies du document superflues.

  - **Stockez automatiquement les enregistrements dans un référentiel d’enregistrements situé localement au sein de la collection de sites.** Chaque collection de sites dans SharePoint et OneDrive conserve le contenu dans la bibliothèque de conservation et de préservation. Les versions des enregistrements sont stockées dans le dossier Enregistrements de cette bibliothèque.

  - **Tenez à jour un document évolutif contenant toutes les versions.** Par défaut, un historique des versions est disponible dans le menu élément pour chaque document SharePoint et OneDrive. Dans cet historique des versions, vous pouvez facilement identifier quelles versions sont des enregistrements et afficher ces documents.

Le contrôle de version d’enregistrement est disponible automatiquement pour tout document comportant une étiquette de rétention qui déclare l’élément comme enregistrement. Lorsqu’un utilisateur affiche les propriétés du document dans le volet Détails, il bascule le **Statut de l’enregistrement** de **Verrouillé** vers **Déverrouillé**. D’un seul clic, il crée un enregistrement dans le dossier Enregistrements de la bibliothèque de conservation et de préservation, où il résidera jusqu’à la fin de la période de rétention. Lorsque le document est déverrouillé, les utilisateurs disposant des autorisations appropriées peuvent modifier le fichier. Toutefois, les utilisateurs ne peuvent pas supprimer le fichier, car il est considéré comme un enregistrement déclaré. Une fois que les modifications nécessaires ont été apportées, l’utilisateur peut basculer le **Statut de l’enregistrement** de **Déverrouillé** à **Verrouillé**, si bien que le document est de nouveau déclaré comme un enregistrement et ne peut pas être modifié.
<br/><br/>

![Propriété statut de l’enregistrement sur le document marqué en tant qu’enregistrement](../media/recordversioning8.png)

> [!NOTE]
> Le contrôle de version d’enregistrement nécessite une licence Office 365 Entreprise E5 pour chaque utilisateur autorisé à modifier du contenu qui a été déclaré en tant qu’enregistrement dans un site SharePoint ou un compte OneDrive. Les utilisateurs disposant d’un accès en lecture seule n’ont pas besoin de cette licence.

### <a name="locking-and-unlocking-a-record"></a>Verrouillage et déverrouillage d'un enregistrement

Lorsqu’une étiquette d’enregistrement est attribuée à un document, tous les utilisateurs ayant des autorisations de collaboration ou un niveau d'autorisation plus réduit peuvent déverrouiller un enregistrement ou verrouiller un enregistrement déverrouillé.
<br/><br/>

![Le statut de l’enregistrement indique que le document enregistré est déverrouillé](../media/recordversioning9.png)

Lorsqu’un utilisateur déverrouille un enregistrement, il se produit les actions suivantes :

1. Si la collection de sites actuelle ne possède pas de bibliothèque de conservation et de préservation, une bibliothèque est créée.

2. Si la bibliothèque de conservation et de préservation ne possède pas de dossier Enregistrements, un dossier est créé.

3. Une action **Copier vers** copie la dernière version du document dans le dossier Enregistrements. L’action **Copier vers** inclut uniquement la dernière version et aucune version antérieure. Ce document copié est désormais considéré comme une version d’enregistrement du document et son nom de fichier présente le format suivant : \[Titre GUID Version\#\]

4. La copie créée dans le dossier Enregistrements est ajoutée à l’historique des versions du document d’origine et cette version affiche le mot **Enregistrement** dans le champ commentaires.

5. Le document d’origine est une nouvelle version qui peut être modifiée (mais pas supprimée). La colonne bibliothèque de documents **L’Élément est un Enregistrement** affiche toujours la valeur **Oui** parce que le document est toujours considéré comme un enregistrement, même s’il peut désormais être modifié.

Lorsqu’un utilisateur verrouille un enregistrement, le document d’origine ne peut pas être modifié. Mais c’est l’action de déverrouiller un enregistrement qui copie une version dans le dossier Enregistrements de la bibliothèque de conservation et de préservation.

### <a name="record-versions"></a>Versions d’enregistrement

Chaque fois qu’un utilisateur déverrouille un enregistrement, la version la plus récente est copiée dans le dossier Enregistrements de la bibliothèque de conservation et de préservation et cette version contient la valeur **Enregistrement** dans le champ **Commentaires** de l’historique des versions.
<br/><br/>

![Enregistrement affiché dans la bibliothèque de conservation et de préservation](../media/recordversioning10.png)

Pour afficher l’historique des versions, sélectionnez un document dans la bibliothèque de documents, puis cliquez sur **Historique des versions** dans le menu élément.

### <a name="where-records-are-stored"></a>Où sont stockés les enregistrements

Les enregistrements sont stockés dans le dossier Enregistrements de la bibliothèque de conservation et de préservation du site de niveau supérieur de la collection de sites. Dans le volet de navigation gauche, dans le site de niveau supérieur, sélectionnez **Contenu du site** \> **Bibliothèque de conservation et de préservation**.
<br/><br/>

![Bibliothèque de conservation et de préservation](../media/recordversioning11.png)

<br/><br/>

![Dossier Enregistrements dans la bibliothèque de conservation et de préservation](../media/recordversioning12.png)

La bibliothèque de conservation et de préservation est visible uniquement par les administrateurs de collection de sites. De plus, la bibliothèque de conservation et de préservation n’existe pas par défaut. Elle est créée uniquement lorsque le contenu soumis à une étiquette de rétention ou une stratégie de rétention est supprimé pour la première fois dans la collection de sites.

### <a name="searching-the-audit-log-for-record-versioning-events"></a>Rechercher dans le journal d’audit les événements de contrôle de version d’enregistrement

Les actions de verrouillage et déverrouillage des enregistrements sont enregistrées dans le journal d’audit Office 365. Vous pouvez rechercher les activités spécifiques **Statut de l’enregistrement basculé sur verrouillé** et **Statut de l’enregistrement basculé sur déverrouillé**, situées dans la section **Activités de fichier et de page** dans la liste déroulante **Activités** sur la page **Effectuer une recherche dans le journal d’audit** du centre de sécurité et conformité.
<br/><br/>

![Rechercher dans le journal d’audit des événements de contrôle de version d’enregistrement](../media/recordversioning13.png)

Pour plus d’informations sur la recherche de ces événements, voir la section « Activités de fichier et de page » dans [Effectuer une recherche dans le journal d’audit dans le Centre de sécurité et conformité](search-the-audit-log-in-security-and-compliance.md#file-and-page-activities).
