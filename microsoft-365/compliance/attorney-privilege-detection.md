---
title: Configurer la détection des privilèges avocat-client dans eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Utilisez le modèle de détection des privilèges avocat-client pour utiliser la détection basée sur l’apprentissage automatique du contenu privilégié lors de l’examen du contenu dans un cas de Microsoft Purview eDiscovery (Premium).
ms.openlocfilehash: b139ce012b305bc6ef59975c39c1aebf5808df8f
ms.sourcegitcommit: 433f5b448a0149fcf462996bc5c9b45d17bd46c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2022
ms.locfileid: "67823296"
---
# <a name="set-up-attorney-client-privilege-detection-in-ediscovery-premium"></a>Configurer la détection des privilèges avocat-client dans eDiscovery (Premium)

Un aspect important et coûteux de la phase de révision d’un processus eDiscovery consiste à examiner les documents pour le contenu privilégié. Microsoft Purview eDiscovery (Premium) fournit une détection basée sur le Machine Learning du contenu privilégié pour rendre ce processus plus efficace. Cette fonctionnalité est appelée *détection de privilèges avocat-client*.

## <a name="how-does-it-work"></a>Comment cela fonctionne-t-il ?

Lorsque la détection des privilèges avocat-client est activée, tous les documents d’un ensemble d’examens sont traités par le modèle de détection des privilèges avocat-client lorsque vous [analysez les données](analyzing-data-in-review-set.md) dans l’ensemble de révision. Le modèle recherche deux éléments :

- Contenu privilégié : le modèle utilise le Machine Learning pour déterminer la probabilité que le document contienne du contenu de nature légale.

- Participants : dans le cadre de la configuration de la détection des privilèges avocat-client, vous devez soumettre une liste d’avocats pour votre organisation. Le modèle compare ensuite les participants du document avec la liste des avocats pour déterminer si un document a au moins un participant avocat.

Le modèle produit les trois propriétés suivantes pour chaque document :

- **AttorneyClientPrivilegeScore:** La probabilité que le document soit de nature juridique; les valeurs du score sont comprises entre **0** et **1**.

- **HasAttorney :** Cette propriété est définie sur **true** si l’un des participants au document est répertorié dans la liste des avocats; sinon, la valeur est **false**. La valeur est également **faux** si votre organisation n’a pas chargé de liste d’avocat.

- **IsPrivilege :** Cette propriété est définie sur **true** si la valeur de **AttorneyClientPrivilegeScore** est supérieure au seuil *ou* si le document a un participant avocat ; sinon, la valeur est définie sur **false**.

Ces propriétés (et leurs valeurs correspondantes) sont ajoutées aux métadonnées de fichier des documents dans un jeu de révision, comme illustré dans la capture d’écran suivante :

![Propriétés de privilèges avocat-client affichées dans les métadonnées du fichier.](../media/AeDAttorneyClientPrivilegeMetadata.png)

Ces trois propriétés peuvent également faire l’objet d’une recherche dans un ensemble de révisions. Pour plus d’informations, consultez [Interroger les données dans un ensemble de révisions](review-set-search.md).

## <a name="set-up-the-attorney-client-privilege-detection-model"></a>Configurer le modèle de détection des privilèges avocat-client

Pour activer le modèle de détection des privilèges entre avocats et clients, votre organisation doit l’activer, puis charger une liste d’avocats.

### <a name="step-1-turn-on-attorney-client-privilege-detection"></a>Étape 1 : Activer la détection des privilèges avocat-client

Une personne qui est administrateur eDiscovery dans votre organisation (membre du sous-groupe Administrateur eDiscovery dans le groupe de rôles gestionnaire eDiscovery) doit rendre le modèle disponible dans vos cas eDiscovery (Premium).

1. Dans le portail de conformité Microsoft Purview, accédez à [eDiscovery (Premium),](https://go.microsoft.com/fwlink/p/?linkid=2173764) puis cliquez sur **les paramètres eDiscovery (Premium**).

   ![Sélectionner les paramètres eDiscovery (Premium)](..\media\HistoricalVersions1.png)

2. Dans la page **Paramètres** , sélectionnez l’onglet **Analyse** , puis activez le bouton bascule détection des **privilèges du client-avocat** .

   ![Cliquez sur basculer pour activer la détection des privilèges du client-avocat](..\media\TurnOnAttorneyClientPrivilegeDetection.png)

3. Cliquez sur **Enregistrer** pour enregistrer la modification.

### <a name="step-2-upload-a-list-of-attorneys-optional"></a>Étape 2 : Charger une liste d’avocats (facultatif)

Pour tirer pleinement parti du modèle de détection des privilèges avocat-client et utiliser les résultats de la détection has **attorney** ou **potentially privileged** qui a été décrite précédemment, nous vous recommandons de charger une liste d’adresses e-mail pour les avocats et le personnel juridique qui travaillent pour votre organisation.

Pour charger une liste d’avocats à utiliser par le modèle de détection de privilèges avocat-client :

1. Créez un fichier .csv (sans ligne d’en-tête), puis ajoutez l’adresse de messagerie de chaque personne appropriée sur une ligne distincte. Enregistrez ce fichier sur votre ordinateur local.

2. Dans la page **Paramètres** eDiscovery (Premium), sélectionnez l’onglet **Analyse** .

   La page **de privilèges avocat-client** s’affiche, et le bouton bascule **de détection des privilèges du client-avocat** est activé.

   ![Page de menu volant de privilèges avocat-client](..\media\AeDUploadAttorneyList1.png)

3. **Sélectionnez Choisir un fichier**, puis recherchez et sélectionnez le fichier .csv que vous avez créé à l’étape 1.

4. Sélectionnez **Enregistrer** pour charger la liste des avocats.

## <a name="use-the-attorney-client-privilege-detection-model"></a>Utiliser le modèle de détection de privilèges avocat-client

Suivez les étapes décrites dans cette section pour utiliser la détection des privilèges avocat-client pour les documents d’un ensemble de révisions.

### <a name="step-1-create-a-smart-tag-group-with-attorney-client-privilege-detection-model"></a>Étape 1 : Créer un groupe de balises actives avec un modèle de détection de privilèges avocat-client

L’un des principaux moyens d’afficher les résultats de la détection du privilège client-avocat dans le cadre de votre processus de révision est d’utiliser un groupe de balises actives. Un groupe de balises actives indique les résultats de la détection de privilège client-avocat et affiche les résultats en ligne en regard des balises dans un groupe de balises actives. Cela vous permet d’identifier rapidement les documents potentiellement privilégiés lors de l’examen des documents. De plus, vous pouvez également utiliser les balises du groupe de balises actives pour marquer des documents comme privilégiés ou non privilégiés. Pour plus d’informations sur les balises actives, consultez [Configurer des balises actives dans eDiscovery (Premium).](smart-tags.md)

1. Dans l’ensemble de révisions qui contient les documents que vous avez analysés à l’étape 1, **sélectionnez Gérer l’ensemble de révisions** , puis **sélectionnez Gérer les balises**.

2. Sous **Balises**, sélectionnez la liste déroulante en regard **d’Ajouter un groupe** , puis **sélectionnez Ajouter un groupe de balises actives**.

   ![Sélectionnez « Ajouter un groupe de balises actives ».](../media/AeDCreateSmartTag.png)

3. Dans la page **Choisir un modèle pour votre balise active** , **sélectionnez Sélectionner** en regard du **privilège avocat-client**.

   Un groupe de balises nommé **Privilège de client-avocat** s’affiche. Il contient deux balises enfants **nommées Positive** et **Négative**, qui correspondent aux résultats possibles produits par le modèle.

   ![Groupe de balises actives de privilèges d’avocat-client.](../media/AeDAttorneyClientSmartTagGroup.png)

3. Renommez le groupe de balises et les balises en fonction de votre révision. Par exemple, vous pouvez renommer **Positif** en **Privilégié** et **Négatif** en **Non privilégié**.

### <a name="step-2-analyze-a-review-set"></a>Étape 2 : Analyser un ensemble de révisions

Lorsque vous analysez les documents d’un ensemble de révisions, le modèle de détection des privilèges avocat-client s’exécute également et les propriétés correspondantes (décrites dans [Comment fonctionne-t-il ?](#how-does-it-work)) sont ajoutées à chaque document de l’ensemble de révision. Pour plus d’informations sur l’analyse des données dans l’ensemble de révisions, consultez [Analyser les données dans un jeu de révision dans eDiscovery (Premium).](analyzing-data-in-review-set.md)

### <a name="step-3-use-the-smart-tag-group-for-review-of-privileged-content"></a>Étape 3 : Utiliser le groupe de balises actives pour passer en revue le contenu privilégié

Après avoir analysé le jeu de révision et configuré des balises actives, l’étape suivante consiste à passer en revue les documents. Si le modèle a déterminé que le document est potentiellement privilégié, la balise active correspondante dans le **panneau d’étiquetage** indique les résultats suivants générés par la détection des privilèges avocat-client :

- Si le contenu du document peut être légal, le **contenu légal** de l’étiquette s’affiche en regard de la balise active correspondante (qui dans ce cas est la balise **positive** par défaut).

- Si le document contient un participant qui se trouve dans la liste des avocats de votre organisation, l’étiquette **Avocat** s’affiche en regard de la balise active correspondante (qui, dans ce cas, est également la balise **Positive** par défaut).

- Si le document contient du contenu qui peut être de nature juridique *et* a un participant trouvé dans la liste des avocats, le **contenu juridique**  et les étiquettes **d’avocat** sont affichés. 

Si le modèle détermine qu’un document ne contient pas de contenu légal ou qu’il ne contient pas de participant dans la liste des avocats, aucune étiquette n’est affichée dans le panneau d’étiquetage.

Par exemple, les captures d’écran suivantes montrent deux documents. Le premier contient du contenu qui est de nature juridique et a un participant trouvé dans la liste des avocats. La seconde ne contient ni l’une ni l’autre et n’affiche donc aucune étiquette.

![Document avec des étiquettes de contenu Avocat et Juridique.](../media/AeDTaggingPanelLegalContentAttorney.png)

![Document sans étiquette.](../media/AeDTaggingPanelNegative.png)

Après avoir examiné un document pour voir s’il contient du contenu privilégié, vous pouvez baliser le document avec la balise appropriée.
