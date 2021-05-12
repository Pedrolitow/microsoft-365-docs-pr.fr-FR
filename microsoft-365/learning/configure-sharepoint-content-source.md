---
title: 'Bientôt disponible : configurer SharePoint en tant que source de contenu d’apprentissage pour Microsoft Learning (prévisualisation)'
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: chrisarnoldmsft
ms.date: 05/12/2021
audience: admin
ms.topic: article
ms.service: ''
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-viva-learning
localization_priority: None
description: Découvrez comment configurer SharePoint en tant que source de contenu d’apprentissage pour Microsoft Learning (prévisualisation).
ms.openlocfilehash: 2bed3a42d62e2aab2165ee38379eb07503807e6e
ms.sourcegitcommit: 967f64dfa1a05f31179c8316b96bfb7758a5d990
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2021
ms.locfileid: "52333577"
---
# <a name="coming-soon-configure-sharepoint-as-a-learning-content-source-for-microsoft-viva-learning-preview"></a>Bientôt disponible : configurer SharePoint en tant que source de contenu d’apprentissage pour Microsoft Learning (prévisualisation)

> [!NOTE]
> Les informations de cet article concernent un produit d’aperçu qui peut être considérablement modifié avant sa publication commerciale. 

Vous pouvez configurer SharePoint en tant que source de contenu d’apprentissage pour que le contenu de votre organisation soit disponible dans Learning (Prévisualisation).

## <a name="overview"></a>Vue d’ensemble

L’administrateur du savoir (ou administrateur général) fournit une URL de site où le service d’apprentissage peut créer un emplacement centralisé vide(référentiel de contenu d’application d’apprentissage) sous la forme d’une liste SharePoint structurée. Cette liste peut être utilisée par votre organisation pour contenir des liens vers des dossiers SharePoint entre entreprises qui contiennent du contenu d’apprentissage. Les administrateurs sont chargés de collecter et de organiser une liste d’URL pour les dossiers. Ces dossiers doivent inclure uniquement le contenu qui peut être mis à disposition dans Learning (Prévisualisation).

Learning (Prévisualisation) prend en charge les types de documents suivants :

- Word, PowerPoint, Excel, PDF
- Audio (.m4a)
- Vidéo (.mov, .mp4, .avi)

Pour plus d’informations, voir [Limites de SharePoint.](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits?redirectSourcePath=%252farticle%252fSharePoint-Online-limits-8f34ff47-b749-408b-abc0-b605e1f6d498) 

## <a name="permissions"></a>Autorisations

Les URL de dossier de bibliothèque de documents peuvent être collectées à partir de n’importe quel site SharePoint de l’organisation. Learning (Preview) suit toutes les autorisations de contenu existantes. Par conséquent, seul le contenu pour lequel un utilisateur a l’autorisation d’accéder est accessible et visible dans Learning (Preview). Tout contenu de ces dossiers est utilisable dans une recherche, mais seul le contenu pour lequel l’employé dispose d’autorisations peut être utilisé.

La suppression de contenu du référentiel de votre organisation n’est actuellement pas prise en charge.

Pour supprimer le contenu accidentellement surface, suivez les étapes suivantes :

1.  Pour restreindre l’accès à la bibliothèque de documents, sélectionnez l’option Afficher **les actions,** puis **sélectionnez Gérer l’accès.**
     
     ![Page bibliothèque de documents dans SharePoint montrant l’option Afficher les actions avec l’option Gérer l’accès élevé.](../media/learning/learning-sharepoint-permissions2.png)

2.  Supprimez le document d’origine dans la bibliothèque de documents.

Pour plus d’informations, [voir Partage et autorisations dans l’expérience moderne de SharePoint.](/sharepoint/modern-experience-sharing-permissions) 

## <a name="learning-service"></a>Service d’apprentissage

Le service d’apprentissage utilise les URL de dossier fournies pour obtenir des métadonnées à partir de tout le contenu stocké dans ces dossiers. Dans un délai de 24 heures après la fourniture de l’URL du dossier dans le référentiel centralisé, les employés peuvent rechercher et utiliser le contenu de votre organisation dans Learning (Prévisualisation). Toutes les modifications apportées au contenu, y compris les métadonnées et autorisations mises à jour, seront également appliquées dans le service d’apprentissage dans les 24 heures.

## <a name="configure-sharepoint-as-a-source"></a>Configurer SharePoint en tant que source

Vous devez être administrateur général Microsoft 365, administrateur SharePoint ou administrateur du savoir pour effectuer ces tâches.

Pour configurer SharePoint en tant que sources de contenu d’apprentissage dans Learning Learning (Prévisualisation), suivez les étapes suivantes :

1.  Dans le navigation de gauche du Centre d’administration Microsoft 365, allez aux **paramètres** de  >  **l’organisation Paramètres.**
 
2.  Dans la page **Paramètres de l’organisation,** sous l’onglet **Services,** **sélectionnez Learning (Prévisualisation).**

     ![Page Paramètres dans le Centre d’administration Microsoft 365 affichant Learning répertorié.](../media/learning/learning-sharepoint-configure1.png)

3.  Dans le **panneau Learning (Prévisualisation),** sous SharePoint, fournit l’URL du site SharePoint où vous souhaitez qu’Learning (Prévisualisation) crée un référentiel centralisé.

     ![Panneau d’apprentissage dans le Centre d’administration Microsoft 365 affichant SharePoint sélectionné.](../media/learning/learning-sharepoint-configure2.png)

4.  Une liste SharePoint est créée automatiquement dans le site SharePoint fourni.

     ![Liste SharePoint nouvellement créée dans le site SharePoint.](../media/learning/learning-sharepoint-configure3.png)

     Dans le navigation gauche du site SharePoint, sélectionnez Contenu du **site** Référentiel de contenu  >  **d’application d’apprentissage.** 

     ![Liste SharePoint affichant la navigation du contenu du site et la section Référentiel de contenu d’application d’apprentissage.](../media/learning/learning-sharepoint-configure4.png) 

5. Dans la page Référentiel de contenu **d’application** d’apprentissage, remplir la liste SharePoint avec des URL vers les dossiers de contenu d’apprentissage.

   1. Sélectionnez **Nouveau** pour afficher le **panneau Nouvel** élément. 

       ![Page Référentiel de contenu d’apprentissage dans SharePoint affichant l’option Nouvelle.](../media/learning/learning-sharepoint-configure5.png)
 
   2. Dans le **panneau Nouvel élément,** dans le champ **Titre,** ajoutez un nom de répertoire de votre choix. Dans le champ **URL du** dossier, ajoutez l’URL au dossier de contenu d’apprentissage. Sélectionnez **Enregistrer**.

       ![Nouveau panneau d’élément dans SharePoint affichant les champs d’URL de titre et de dossier.](../media/learning/learning-sharepoint-configure6.png)

   3. La page **Référentiel de contenu d’application d’apprentissage** est mise à jour avec le nouveau contenu d’apprentissage.

       ![Page Référentiel de contenu d’apprentissage dans SharePoint affichant les informations mises à jour.](../media/learning/learning-sharepoint-configure7.png)

> [!NOTE]
> Pour permettre un accès plus large au référentiel de contenu d’application d’apprentissage, un lien vers la liste sera bientôt disponible dans l’interface Learning (Prévisualisation) dans laquelle les utilisateurs peuvent demander l’accès et, en fin de compte, contribuer à remplir la liste. Les propriétaires de site et les administrateurs globaux doivent accorder l’accès à la liste. L’accès est spécifique à la liste uniquement et ne s’applique pas au site où la liste est stockée. Pour plus d’informations, voir [Fournir](#provide-your-own-organizations-content) le contenu de votre propre organisation plus loin dans cet article.

### <a name="folder-url-document-library-curation"></a>Curation de bibliothèque de documents d’URL de dossier

Les métadonnées par défaut (telles que la date de modification, créées par, le nom du document, le type de contenu et le nom de l’organisation) sont automatiquement extraites dans Learning Learning (Prévisualisation) par l’API Microsoft Graph.
 
Pour améliorer la pertinence globale de la recherche et de la découverte du contenu, nous vous recommandons d’ajouter une **colonne Description.**

Pour ajouter une **colonne Description** à la page de bibliothèque de documents, suivez les étapes suivantes :

1.  Dans la page **Documents,** sélectionnez **Ajouter une colonne.**

2. Sélectionnez **l’option Afficher les actions,** puis **sélectionnez Une seule ligne de texte.**

     ![Page Documents dans SharePoint affichant les options d’affichage des actions avec une seule ligne de texte en surbrillant.](../media/learning/learning-sharepoint-curation1.png)

3. Dans le **panneau Créer une colonne,** dans le champ **Nom,** ajoutez un nom descriptif pour la colonne. Sélectionnez **Enregistrer**.

     ![Créez un panneau de colonne dans SharePoint affichant le nom et d’autres champs.](../media/learning/learning-sharepoint-curation2.png)
 
4. Dans la page **Documents,** dans la **colonne Description,** ajoutez des descriptions personnalisées pour chaque élément. Si aucune description n’est fournie, Learning (Prévisualisation) fournit un message par défaut qui met en évidence le contenu comme provenant de votre propre bibliothèque SharePoint. 

     ![Page documents dans SharePoint affichant les descriptions dans la colonne Description.](../media/learning/learning-sharepoint-curation3.png)
 
### <a name="provide-your-own-organizations-content"></a>Fournir le contenu de votre propre organisation

Les administrateurs du savoir peuvent accéder au référentiel de contenu des applications d’apprentissage de leur organisation dans SharePoint, où ils peuvent fournir des références à des bibliothèques de documents entre les organisations. Le contenu de ces bibliothèques sera ensuite présenté comme du contenu d’apprentissage dans Learning (Prévisualisation).

1. Dans Learning (Prévisualisation), sélectionnez **Plus d’options** (**...**), puis **sélectionnez Paramètres.**

     ![Page bibliothèque SharePoint affichant l’option Options supplémentaires et Paramètres.](../media/learning/learning-sharepoint-library-1.png)
     
2. Sous **Paramètres,** sélectionnez **Autorisations.**

     ![Page d’options Paramètres dans SharePoint affichant les options Autorisations et Vérifier l’accès.](../media/learning/learning-sharepoint-library-2.png)

3. Sélectionnez **Vérifier l’accès** pour vous connecter à la bibliothèque centralisée de votre organisation.
     
