---
title: Configurer la détection des privilèges client-avocat dans Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Utilisez le modèle de détection des privilèges client-avocat pour utiliser la détection basée sur l’apprentissage automatique du contenu privilégié lors de l’examen du contenu dans Advanced eDiscovery cas.
ms.openlocfilehash: babf0088b7880e614234c0eea0432b0a7fa22db0
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58569128"
---
# <a name="set-up-attorney-client-privilege-detection-in-advanced-ediscovery"></a>Configurer la détection des privilèges client-avocat dans Advanced eDiscovery

Un aspect majeur et coûteux de la phase de révision de tout processus eDiscovery consiste à examiner des documents pour le contenu privilégié. Advanced eDiscovery permet une détection basée sur l’apprentissage automatique du contenu privilégié pour rendre ce processus plus efficace. Cette fonctionnalité est appelée *détection des privilèges client-avocat.*

## <a name="how-does-it-work"></a>Comment cela fonctionne-t-il ?

Lorsque la détection des privilèges client-avocat est activée, tous les documents d’un [](analyzing-data-in-review-set.md) jeu à réviser sont traitées par le modèle de détection des privilèges client-avocat lorsque vous analysez les données du jeu à réviser. Le modèle recherche deux éléments :

- Contenu privilégié : le modèle utilise l’apprentissage automatique pour déterminer la probabilité que le document contienne du contenu de nature juridique.

- Participants : dans le cadre de la configuration de la détection des privilèges client-avocat, vous devez soumettre une liste d’avocats pour votre organisation. Le modèle compare ensuite les participants du document avec la liste des avocats pour déterminer si un document a au moins un participant avocat.

Le modèle produit les trois propriétés suivantes pour chaque document :

- **AttorneyClientPrivilegeScore :** La probabilité que le document soit de nature juridique ; les valeurs du score sont entre **0** et **1**.

- **HasAttorney :** Cette propriété est définie sur **true si** l’un des participants au document est répertorié dans la liste des avocats ; Sinon, la valeur est **false**. La valeur est également **faux** si votre organisation n’a pas chargé de liste d’avocat.

- **IsPrivilege :** Cette propriété est définie sur **true** si la valeur de **AttorneyClientPrivilegeScore** est supérieure au seuil ou si le document a un participant avocat ;  Sinon, la valeur est définie sur **false**.

Ces propriétés (et leurs valeurs correspondantes) sont ajoutées aux métadonnées de fichier des documents dans un jeu à réviser, comme illustré dans la capture d’écran suivante :

![Propriétés de privilège client-avocat affichées dans les métadonnées de fichier.](../media/AeDAttorneyClientPrivilegeMetadata.png)

Ces trois propriétés sont également utilisables dans un jeu à réviser. Pour plus d’informations, [voir Interroger les données dans un jeu à réviser.](review-set-search.md)

## <a name="set-up-the-attorney-client-privilege-detection-model"></a>Configurer le modèle de détection des privilèges client-avocat

Pour activer le modèle de détection des privilèges client-avocat, votre organisation doit l’activer, puis télécharger une liste d’avocats.

### <a name="step-1-turn-on-attorney-client-privilege-detection"></a>Étape 1 : Activer la détection des privilèges client-avocat

Une personne qui est administrateur eDiscovery dans votre organisation (membre du sous-groupe Administrateur eDiscovery dans le groupe de rôles Gestionnaire eDiscovery) doit rendre le modèle disponible dans vos cas Advanced eDiscovery.

1. In the Centre de conformité Microsoft 365, go to **eDiscovery > Advanced**.

2. Sur la **Advanced eDiscovery** d’accueil, dans la **vignette Paramètres,** cliquez sur **Configurer les paramètres d’analyse globale.**

   ![Sélectionnez « Configurer les fonctionnalités expérimentales ».](../media/AeDExperimentalFeatures.png)

3. Sous **l’onglet Paramètres d’analyse,** sélectionnez Gérer le paramètre de **privilège client-avocat.**

4. Sur la page de menu déroulant **Privilège client-avocat**, utilisez le bouton bascule pour activer la fonctionnalité, puis sélectionnez **Enregistrer**.

### <a name="step-2-upload-a-list-of-attorneys-optional"></a>Étape 2 : Télécharger liste des avocats (facultatif)

Pour tirer pleinement parti du modèle de détection des privilèges client-avocat et utiliser les résultats de la détection Has **Attorney** ou **Potentially Privileged** précédemment décrite, nous vous recommandons de charger une liste d’adresses de messagerie pour les avocats et le personnel juridique qui travaillent pour votre organisation. 

Pour télécharger une liste d’avocats à utiliser par le modèle de détection des privilèges client-avocat :

1. Créez un fichier .csv (sans ligne d’en-tête), puis ajoutez l’adresse de messagerie de chaque personne appropriée sur une ligne distincte. Enregistrez ce fichier sur votre ordinateur local.

2. Sur la page **Advanced eDiscovery** d’accueil, dans la **vignette Paramètres,** sélectionnez Configurer les fonctionnalités expérimentales, puis sélectionnez Gérer le paramètre de privilège **client-avocat.**

   La page **Privilège client-avocat** s’affiche et le basculement de détection des privilèges **client-avocat** est allumé.

   ![Page de flyout de privilège client-avocat.](../media/AeDUploadAttorneyList.png)

3. Sélectionnez **Parcourir,** puis recherchez et sélectionnez .csv fichier que vous avez créé à l’étape 1.

4. Sélectionnez **Enregistrer** pour télécharger la liste des avocats.

## <a name="use-the-attorney-client-privilege-detection-model"></a>Utiliser le modèle de détection des privilèges client-avocat

Suivez les étapes de cette section pour utiliser la détection des privilèges client-avocat pour les documents d’un jeu à réviser.

### <a name="step-1-create-a-smart-tag-group-with-attorney-client-privilege-detection-model"></a>Étape 1 : Créer un groupe de balises intelligentes avec le modèle de détection des privilèges client-avocat

L’un des principaux moyens d’afficher les résultats de la détection du privilège client-avocat dans le cadre de votre processus de révision est d’utiliser un groupe de balises actives. Un groupe de balises actives indique les résultats de la détection de privilège client-avocat et affiche les résultats en ligne en regard des balises dans un groupe de balises actives. Cela vous permet d’identifier rapidement les documents potentiellement privilégiés lors de la révision des documents. De plus, vous pouvez également utiliser les balises du groupe de balises actives pour marquer des documents comme privilégiés ou non privilégiés. Pour plus d’informations sur les balises intelligentes, voir [Configurer des balises intelligentes dans Advanced eDiscovery](smart-tags.md).

1. Dans le jeu à réviser qui contient les documents que vous avez analysés à l’étape 1, sélectionnez Gérer le jeu à **réviser,** puis **sélectionnez Gérer les balises.**
 
2. Sous **Balises,** sélectionnez le pull-down à côté **d’Ajouter** un groupe, puis **sélectionnez Ajouter un groupe de balises intelligentes.**

   ![Sélectionnez « Ajouter un groupe de balises intelligentes ».](../media/AeDCreateSmartTag.png)

3. On the **Choose a model for your smart tag** page, choose **Select** next to **Attorney-client privilege**.

   Un groupe de balises **nommé Privilège client-avocat** s’affiche. Il contient deux balises enfants nommées **Positive** et **Negative,** qui correspondent aux résultats possibles produits par le modèle.

   ![Groupe de balises à puce privilège client-avocat.](../media/AeDAttorneyClientSmartTagGroup.png)

3. Renommez le groupe de balises et les balises selon votre avis. Par exemple, vous pouvez renommer **Positive** en **Privilégié** et **Négatif** en **Non privilégié**.

### <a name="step-2-analyze-a-review-set"></a>Étape 2 : Analyser un jeu à réviser

Lorsque vous analysez les documents d’un jeu à réviser, le modèle de détection des privilèges client-avocat s’exécute également et les propriétés correspondantes (décrites dans How [does it work?](#how-does-it-work) sont ajoutées à chaque document du jeu à réviser). Pour plus d’informations sur l’analyse des données dans le jeu à réviser, voir Analyser les données dans un jeu à [réviser Advanced eDiscovery](analyzing-data-in-review-set.md).

### <a name="step-3-use-the-smart-tag-group-for-review-of-privileged-content"></a>Étape 3 : Utiliser le groupe de balises intelligentes pour passer en revue le contenu privilégié

Après l’analyse de l’ensemble de révision et la configuration des balises intelligentes, l’étape suivante consiste à examiner les documents. Si le modèle a déterminé que le document est  potentiellement privilégié, la balise intelligente correspondante dans le panneau de marquage indiquera les résultats suivants obtenus par la détection des privilèges client-avocat :

- Si le document possède du contenu de  nature juridique, le contenu de l’étiquette Legal s’affiche à côté de la balise smart correspondante (qui est dans ce cas la balise **positive** par défaut).

- Si le document contient un participant qui figure dans la liste des avocats de votre organisation, l’étiquette **Avocat** s’affiche à côté de la balise active correspondante (qui est également la balise **Positive** par défaut dans ce cas).

- Si le document contient du contenu de *nature* juridique et qu’un  participant  figure dans la liste des avocats, le contenu juridique et les étiquettes Avocat sont affichés. 

Si le modèle détermine qu’un document ne contient pas de contenu juridique ou qu’il ne contient pas de participant de la liste des avocats, aucune des étiquettes n’est affichée dans le panneau de marquage.

Par exemple, les captures d’écran suivantes montrent deux documents. Le premier contient du contenu de nature juridique et un participant trouvé dans la liste des avocats. Le second ne contient ni étiquette, ni aucune étiquette.

![Document avec étiquettes de contenu avocat et juridique.](../media/AeDTaggingPanelLegalContentAttorney.png)

![Document sans aucune étiquette.](../media/AeDTaggingPanelNegative.png)

Après avoir passé en revue un document pour voir s’il contient du contenu privilégié, vous pouvez marquer le document avec la balise appropriée.
