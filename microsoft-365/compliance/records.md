---
title: Découvrir les enregistrements
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
description: Découvrir les enregistrements pour vous aider à implémenter une solution de gestion des enregistrements dans Microsoft 365.
ms.openlocfilehash: 6cdf29493a3fd95b060c52d9f9587ee34748edde
ms.sourcegitcommit: a53af7a228bb1f58cb8128a69a19da49f9e28700
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "45372519"
---
# <a name="learn-about-records"></a>Découvrir les enregistrements

>*[Guide de sécurité et conformité pour les licences Microsoft 365](https://aka.ms/ComplianceSD).*

La gestion des enregistrements dans Microsoft 365 permet à votre organisation de respecter les stratégies d’entreprise et les obligations légales ou réglementaires, tout en réduisant les risques et la responsabilité juridique.

Lorsque le contenu est marqué comme un enregistrement :

- Des restrictions sont appliquées aux éléments en ce qui concerne les [actions autorisées ou bloquées](#compare-restrictions-for-what-actions-are-allowed-or-blocked).

- Des activités supplémentaires sur l’élément sont enregistrées.

- Vous avez une preuve de destruction lorsque les éléments sont supprimés à la fin de la période de rétention.

Vous utilisez les [étiquettes de rétention](retention.md#retention-labels) pour marquer du contenu sous la forme d’un enregistrement. Vous pouvez soit publier ces étiquettes pour permettre aux utilisateurs et aux administrateurs de les appliquer manuellement au contenu, soit appliquer automatiquement ces étiquettes au contenu que vous voulez marquer comme enregistrement.

En utilisant des étiquettes de rétention pour marquer du contenu en tant qu’enregistrement, vous pouvez implémenter une stratégie de gestion des enregistrements unique et cohérente dans votre environnement Microsoft 365.

## <a name="compare-restrictions-for-what-actions-are-allowed-or-blocked"></a>Comparer des restrictions relatives aux actions autorisées ou bloquées

Utilisez le tableau suivant pour identifier les restrictions placées sur du contenu suite à l’application d’une étiquette de rétention standard, ainsi que les étiquettes de rétention qui marquent du contenu en tant qu’enregistrement. 

Une étiquette de rétention standard a la configuration de conservation des données sans marquer le contenu comme enregistrement.

>[!NOTE] 
> Pour couvrir tous les cas de figure, le tableau inclut les colonnes d’un enregistrement verrouillé et déverrouillé, applicable à SharePoint et OneDrive, mais pas à Exchange. La possibilité de verrouiller et de déverrouiller un enregistrement utilise le [contrôle de version](#record-versioning) qui n’est pas pris en charge pour les éléments Exchange. Par conséquent, pour tous les éléments Exchange marqués en tant qu’enregistrement, le comportement mappe vers l’**Enregistrement – colonne verrouillée**, et l’**Enregistrement – colonne déverrouillée** n’est pas pertinent.


|Action| Étiquette de rétention |Enregistrement – colonne verrouillée| Enregistrement – colonne déverrouillée|
|:-----|:-----|:-----|:-----|:-----|
|Modifier les contenus|Autorisé | **Bloqué** | Autorisé|
|Modifier les propriétés, y compris Renommer|Autorisé |Autorisé | Autorisé|
|Supprimer|<sup>1</sup> autorisé |**Bloqué** | **Bloqué**|
|Copier|Autorisé |Autorisé | Autorisé|
|Se déplacer au sein du conteneur <sup>2</sup>|Autorisé |Autorisé | Autorisé|
|Se déplacer dans les conteneurs <sup>2</sup>|Autorisé |Autorisé si jamais déverrouillé | Autorisé|
|Ouvert/lu|Autorisé |Autorisé | Autorisé|
|Modifier l’étiquette|Autorisé |Autorisé – administrateur de conteneur uniquement | Autorisé – administrateur de conteneur uniquement|
|Supprimer l’étiquette|Autorisé |Autorisé – administrateur de conteneur uniquement | Autorisé – administrateur de conteneur uniquement|

Notes de bas de page :

<sup>1</sup> Prise en charge par OneDrive et Exchange en conservant une copie dans un emplacement sécurisé, mais bloqué par SharePoint.

Message qu’un utilisateur voit s’il essaie de supprimer un document étiqueté dans SharePoint :

![Message indiquant que l’élément n’a pas été supprimé dans SharePoint](../media/d0020726-1593-4a96-b07c-89b275e75c49.png)


<sup>2</sup> Les conteneurs incluent les bibliothèques de documents SharePoint et les boîtes aux lettres Exchange.


## <a name="using-retention-labels-to-declare-records"></a>Utilisation d’étiquettes de rétention pour déclarer des enregistrements

Lorsque vous créez une étiquette de rétention, vous pouvez l’utiliser pour marquer le contenu en tant qu’enregistrement :

1. Dans le centre de conformité Microsoft 365, accédez à **Gestion des enregistrements** \> **plan de gestion de fichiers**. Dans la page **plan de fichiers**, cliquez **créer une étiquette**.

2. Sur la page **Paramètres d’étiquette** de l’Assistant, choisissez l’option permettant de classifier du contenu sous la forme d’un enregistrement.
    
   ![Cliquez sur Utiliser l’étiquette pour classifier du contenu en tant que case à cocher d’Enregistrement](../media/recordversioning6.png)

3. Appliquez l’étiquette de rétention aux documents SharePoint ou OneDrive et aux messages électroniques Exchange, le cas échéant. Pour obtenir des instructions :
    
    - [Créer des étiquettes de rétention et les appliquer dans les applications](create-apply-retention-labels.md)
    
    - [Appliquer automatiquement une étiquette de rétention au contenu](apply-retention-labels-automatically.md)

### <a name="applying-the-configured-retention-label-to-content"></a>Application de l’étiquette de rétention configurée au contenu

Lorsque des étiquettes de rétention qui marquent le contenu en tant qu’enregistrement sont mises à la disposition des utilisateurs pour qu’ils les appliquent dans les applications :

- Pour Exchange, tout utilisateur disposant d’un accès en écriture à la boîte aux lettres peut appliquer ces étiquettes. 
- Pour SharePoint et OneDrive, tous les utilisateurs du groupe Membres par défaut (niveau d’autorisation Collaboration) peuvent appliquer ces étiquettes.

Exemple d’un document marqué en tant qu’enregistrement à l’aide d’une étiquette de rétention :

![Volet Détails pour le document marqué comme enregistrement](../media/recordversioning7.png)

## <a name="record-versioning"></a>Contrôle de version d’enregistrement

La possibilité de marquer un document en tant qu’enregistrement et de restreindre les actions pouvant être effectuées sur l’enregistrement constitue un objectif essentiel pour toute solution de gestion d’enregistrements. Cependant, une collaboration peut également être nécessaire pour permettre aux utilisateurs de créer des versions ultérieures.

Par exemple, il peut arriver que vous marquiez un contrat de vente sous forme d’un enregistrement, mais qu’ensuite vous deviez mettre à jour le contrat avec de nouvelles conditions et marquer la dernière version comme nouvel enregistrement tout en conservant la version précédente de l’enregistrement. Pour ces types de scénarios, SharePoint et OneDrive Entreprise prennent désormais en charge le *contrôle de version d’enregistrement*. Les dossiers de bloc-notes OneNote ne prennent pas en charge le contrôle de version d’enregistrement.

Pour utiliser le contrôle de version d’un enregistrement, commencez par étiqueter le document et marquez-le en tant qu’enregistrement. À ce stade, une propriété de document appelée *Statut de l’enregistrement* s’affiche en regard de l’étiquette de rétention, et le statut de l’enregistrement initial est **Verrouillé**. 

Vous pouvez effectuer les actions suivantes :

  - **Modifier sans limites et conserver les versions individuelles du document en tant qu’enregistrements en déverrouillant et verrouillant la propriété Statut de l’enregistrement.** Une nouvelle version de l’enregistrement est uniquement conservée lorsque la propriété **État de l’enregistrement** est définie sur **Verrouillée**. Ce bouton bascule activé/désactivé permet de réduire le risque de conserver des versions et des copies du document superflues.

  - **Stockez automatiquement les enregistrements dans un référentiel d’enregistrements situé localement au sein de la collection de sites.** Chaque collection de sites dans SharePoint et OneDrive conserve le contenu dans la bibliothèque de conservation et de préservation. Les versions des enregistrements sont stockées dans le dossier Enregistrements de cette bibliothèque.

  - **Tenez à jour un document évolutif contenant toutes les versions.** Par défaut, un historique des versions est disponible dans le menu élément pour chaque document SharePoint et OneDrive. Dans cet historique des versions, vous pouvez facilement identifier quelles versions sont des enregistrements et afficher ces documents.

Le contrôle de version d’enregistrement est disponible automatiquement pour tout document comportant une étiquette de rétention qui marque l’élément comme enregistrement. Lorsqu’un utilisateur affiche les propriétés du document à l’aide du volet Détails, il peut basculer le **Statut de l’enregistrement** de **Verrouillé** vers **Déverrouillé**. Cette action crée un enregistrement dans le dossier Enregistrements de la bibliothèque de conservation et de préservation, où il résidera jusqu’à la fin de la période de rétention. 

Lorsque le document est déverrouillé, les utilisateurs disposant des autorisations de modification standard peuvent modifier le fichier. Toutefois, les utilisateurs ne peuvent pas supprimer le fichier, car il est encore considéré comme un enregistrement. Lorsque la modification est terminée, un utilisateur peut basculer vers la bascule de l’**État de l’enregistrement** de **Déverrouillé** vers **Verrouillé**, ce qui empêche les modifications ultérieures dans ce statut.
<br/><br/>

![Propriété statut de l’enregistrement sur le document marqué en tant qu’enregistrement](../media/recordversioning8.png)

### <a name="locking-and-unlocking-a-record"></a>Verrouillage et déverrouillage d'un enregistrement

Lorsqu’une étiquette de rétention qui marque le contenu en tant qu’enregistrement est appliquée à un document, tous les utilisateurs ayant des autorisations de collaboration ou un niveau d'autorisation plus réduit peuvent déverrouiller un enregistrement ou verrouiller un enregistrement déverrouillé.
<br/><br/>

![Le statut de l’enregistrement indique que le document enregistré est déverrouillé](../media/recordversioning9.png)

Lorsqu’un utilisateur déverrouille un enregistrement, il se produit les actions suivantes :

1. Si la collection de sites actuelle ne possède pas de bibliothèque de conservation et de préservation, une bibliothèque est créée.

2. Si la bibliothèque de conservation et de préservation ne possède pas de dossier Enregistrements, un dossier est créé.

3. Une action **Copier vers** copie la dernière version du document dans le dossier Enregistrements. L’action **Copier vers** inclut uniquement la dernière version et aucune version antérieure. Ce document copié est désormais considéré comme une version d’enregistrement du document et son nom de fichier présente le format suivant : \[Titre GUID Version\#\]

4. La copie créée dans le dossier Enregistrements est ajoutée à l’historique des versions du document d’origine et cette version affiche le mot **Enregistrement** dans le champ commentaires.

5. Le document d’origine est une nouvelle version qui peut être modifiée, mais pas supprimée. La colonne bibliothèque de documents **L’Élément est un Enregistrement** affiche toujours la valeur **Oui** parce que le document est encore considéré comme un enregistrement, même s’il peut désormais être modifié.

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

Les actions de verrouillage et déverrouillage des enregistrements sont enregistrées dans le journal d’audit. Vous pouvez rechercher les activités spécifiques **Statut de l’enregistrement basculé sur verrouillé** et **Statut de l’enregistrement basculé sur déverrouillé**, situées dans la section **Activités de fichier et de page** dans la liste déroulante **Activités** sur la page **Effectuer une recherche dans le journal d’audit** du centre de sécurité et conformité.
<br/><br/>

![Rechercher dans le journal d’audit des événements de contrôle de version d’enregistrement](../media/recordversioning13.png)

Pour plus d’informations sur la recherche de ces événements, voir la section « Activités de fichier et de page » dans [Effectuer une recherche dans le journal d’audit dans le Centre de sécurité et conformité](search-the-audit-log-in-security-and-compliance.md#file-and-page-activities).

## <a name="next-steps"></a>Étapes suivantes

Si vous n’avez pas encore d’étiquettes de rétention à utiliser pour la gestion des enregistrements, consultez [Prise en main des stratégies de rétention et des étiquettes de rétention](get-started-with-retention.md).

Si vous souhaitez en savoir plus sur la destruction des enregistrements, voir [Disposition de contenu](disposition.md).
