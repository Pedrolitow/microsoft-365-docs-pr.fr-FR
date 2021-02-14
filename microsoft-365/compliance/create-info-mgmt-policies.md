---
title: Créer et appliquer des stratégies de gestion des informations
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 5/16/2017
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- SPO160
- OSU150
- OSU160
- MET150
ms.assetid: 8ccac9e4-3a50-49fa-a95b-d186032a6ee3
ms.collection:
- M365-security-compliance
- SPO_Content
ms.custom:
- seo-marvel-apr2020
description: Découvrez comment configurer une stratégie de gestion des informations pour contrôler la durée de la gestion des informations et suivre les personnes qui utilisent ces informations.
ms.openlocfilehash: 2519f039e7495d01a828aee564ce1a6caf41342d
ms.sourcegitcommit: 973f5449784cb70ce5545bc3cf57bf1ce5209218
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2020
ms.locfileid: "44817993"
---
# <a name="create-and-apply-information-management-policies"></a>Créer et appliquer des stratégies de gestion des informations

Les stratégies de gestion des informations permettent à votre organisation de contrôler la durée de rétention du contenu, d’auditer ce que les personnes font avec le contenu et d’ajouter des codes-barres ou des étiquettes aux documents. Une stratégie peut aider à appliquer la conformité avec les réglementations juridiques et gouvernementales ou les processus d’entreprise internes. En tant qu’administrateur, vous pouvez configurer une stratégie pour contrôler le suivi des documents et la durée de rétention des documents.
  
Vous pouvez créer une stratégie de gestion des informations à trois emplacements différents dans la hiérarchie de sites, du plus large au plus étroit :
  
- Créez une stratégie à utiliser sur plusieurs types de contenu au sein d’une collection de sites.
    
- Créez une stratégie pour un type de contenu de site.
    
- Créez une stratégie pour une liste ou une bibliothèque.
    
Pour plus d’informations, voir [Introduction aux stratégies de gestion des informations.](intro-to-info-mgmt-policies.md)
  
## <a name="create-a-policy-for-multiple-content-types-within-a-site-collection"></a>Créer une stratégie pour plusieurs types de contenu au sein d’une collection de sites
<a name="__toc261001590"> </a>

Pour vous assurer qu’une stratégie d’information est appliquée à tous les documents d’un certain type au sein d’une collection de sites, envisagez de créer la stratégie au niveau de la collection de sites, puis appliquez ensuite la stratégie aux types de contenu. Ces stratégies sont appelées stratégies de collection de sites. 
  
1. Sur le bouton \> **Paramètres** sharePoint 2016 de la page d’accueil de la collection de ![ sites, dans la barre de titre.](../media/1c22d2d8-39e0-4930-82c6-c3eee44211d3.png) \>**Paramètres de site**.
    
    Dans un site connecté à un groupe SharePoint, cliquez sur **Paramètres,** sur Contenu du **site,** puis sur **Paramètres du site.** 
    
2. Dans la page Paramètres du site, sous **Modèles** de stratégie de type de contenu Administration de la collection \> **de sites.** 
  
![Lien Modèle de stratégie de type de contenu sur la page Paramètres du site](../media/26d3466a-23ec-443f-88f0-2aaff38e992b.png)
  
3. Dans la page \> **Stratégies, créez**. 
    
4. Entrez un nom et une description pour la stratégie, puis écrivez une brève déclaration de stratégie qui explique aux utilisateurs à quoi la stratégie est propre.
    
5. Consultez la section suivante sur la création de stratégies pour un type de contenu de site pour découvrir comment configurer les fonctionnalités que vous souhaitez associer à la stratégie. 
    
6. Sélectionnez **OK**.
    
## <a name="create-a-policy-for-a-site-content-type"></a>Créer une stratégie pour un type de contenu de site
<a name="__create_a_policy"> </a>

L’ajout d’une stratégie de gestion des informations à un type de contenu facilite l’association de fonctionnalités de stratégie à plusieurs listes ou bibliothèques. Vous pouvez choisir d’ajouter une stratégie de gestion des informations existante à un type de contenu ou de créer une stratégie unique spécifique à un type de contenu individuel.
  
 Vous pouvez également ajouter une stratégie de gestion des informations à un type de contenu spécifique aux listes. Cela a pour effet d’appliquer la stratégie uniquement aux éléments de cette liste qui utilisent le type de contenu. 
  
1. Sur le bouton \> **Paramètres** sharePoint 2016 de la page d’accueil de la collection de ![ sites, dans la barre de titre.](../media/1c22d2d8-39e0-4930-82c6-c3eee44211d3.png) \>**Paramètres de site**.
    
    Dans un site connecté à un groupe SharePoint, cliquez sur **Paramètres,** sur Contenu du **site,** puis sur **Paramètres du site.** 
    
2. Dans la page Paramètres du site, sous **Types** de contenu site Galeries \> **du concepteur** web.
  
![Lien Types de contenu de site sur la page Paramètres du site](../media/6f6fa51f-15d7-4782-b06f-a7b36e874cd3.png)
  
3. Dans la page Paramètres du type de contenu de site, sélectionnez le type de contenu à ajouter une stratégie.
    
4. Dans la page Type de contenu de site, sous **Paramètres Paramètres, paramètres** de stratégie de gestion \> **des informations.**
    
5. Dans la page Modifier la stratégie, entrez un nom et une description pour la stratégie, puis écrivez une brève description qui explique aux utilisateurs à quoi la stratégie est dédiée.
    
6. Dans les sections suivantes, sélectionnez les fonctionnalités de stratégie individuelles que vous souhaitez ajouter à votre stratégie de gestion des informations. 
  
![Types de stratégies de contenu](../media/19fcb8a3-974b-40d3-a13f-b76088d122f8.png)
  
7. Pour spécifier une période de rétention pour les documents et les éléments soumis à cette stratégie, sélectionnez Activer la **rétention,** puis spécifiez la période de rétention et les actions que vous souhaitez faire à l’expiration des éléments.
    
    Pour spécifier une période de rétention
    
||||||**1.**|**Choose **Add a retention stage for records...****|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
||||||2.  <br/> | Sélectionnez une option de période de rétention pour spécifier la date d’expiration des documents ou des éléments. Effectuez l’une des opérations suivantes :  <br/>  Pour définir la date d’expiration  en fonction d’une propriété de date, sous Événement Cette étape est basée sur une propriété de date sur l’élément, puis sélectionnez l’action de document ou d’élément (par exemple, Créé ou Modifié) et l’incrément de temps après cette action (par exemple, le nombre de jours, mois ou années) lorsque vous souhaitez que l’élément \> expire.  <br/>  Pour utiliser une formule de rétention personnalisée pour déterminer l’expiration, choisissez Définir par une formule de rétention personnalisée **installée sur ce serveur.**  <br/> > [!NOTE]> cette option est disponible uniquement si une formule personnalisée a été définie par votre administrateur.           |
||||||3.  <br/> |**L’option** Démarrer un flux de travail n’est disponible que si vous définissez une stratégie pour une liste, une bibliothèque ou un type de contenu qui possède déjà un flux de travail qui lui est associé. Vous aurez alors le choix entre les flux de travail.  <br/> |
||||||4.  <br/> |Dans  la section Récurrence, **sélectionnez Répéter l’action de cette étape...** et entrez la fréquence de récurrisation de l’action.  <br/> > [!NOTE]> cette option est disponible uniquement si l’action que vous avez sélectionnée peut être répétée. Par exemple, vous ne pouvez pas définir la récurrence de l’action **Supprimer définitivement**.           |
||||||5.  <br/> |Choisissez **OK**.  <br/> |
   
1. Pour activer l’audit pour les documents et les éléments soumis à cette stratégie, sélectionnez Activer **l’audit,** puis spécifiez les événements que vous souhaitez auditer.
    
    Pour activer l’audit
    
||||||1.****|On the Edit Policy page,** **under** **Auditing** **\>** **Enable auditing** **, and then select the check boxes next to the events you want to keep an audit trail for.****|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
||||||**2.** <br/> |**Pour inciter les utilisateurs à insérer ces codes-barres**  dans des documents, choisissez Invitez les utilisateurs à insérer un code-barres avant **l’enregistrement ou l’impression.**  <br/> |
||||||**3.** <br/> |**Choisissez** **OK** ** pour appliquer la fonctionnalité d’audit à la stratégie. ** <br/> |
|||||||La fonctionnalité stratégie d’audit permet aux organisations de créer et d’analyser des pistes d’audit pour les documents et de répertorier des éléments tels que des listes de tâches, des listes de problèmes, des groupes de discussion et des calendriers. Cette fonctionnalité de stratégie fournit un journal d’audit qui enregistre les événements, tels que l’affichage, la modification ou la suppression du contenu.  <br/> |
|||||||Lorsque l’audit est activé dans le cadre d’une stratégie de gestion des informations, les administrateurs peuvent afficher les données d’audit dans les rapports d’utilisation des stratégies basés dans Microsoft Excel et qui récapitulent l’utilisation actuelle. Les administrateurs peuvent se servir de ces rapports pour déterminer comment l'information est utilisée dans l'organisation. Ces rapports peuvent également aider les organisations à vérifier et documenter leur conformité réglementaire ou à examiner les problèmes potentiels.  <br/> |
|||||||Le journal d’audit enregistre les informations suivantes : nom de l’événement, date et heure de l’événement et nom système de l’utilisateur qui a effectué l’action.  <br/> |
   
1. Lorsque les codes-barres sont activés dans le cadre d’une stratégie, ils sont ajoutés aux propriétés du document et affichés dans la zone d’en-tête du document auquel le code-barres est appliqué. Comme les étiquettes, les codes-barres peuvent également être supprimés manuellement d’un document. Vous pouvez spécifier si les utilisateurs doivent être invités à inclure le code-barres lors  de l’impression ou de l’enregistrement d’un élément, ou si le code-barres doit être inséré manuellement à l’aide de l’onglet Insérer dans les programmes office 2010. 
    
    Pour activer les codes-barres
    
||||||1.****|**Dans la page Modifier la stratégie, sous **Codes-barres** \> **Activer les codes-barres.****|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
||||||**2.** <br/> |Pour inciter les utilisateurs à insérer ces codes-barres dans des documents, choisissez Invitez les utilisateurs à insérer un **code-barres avant l’enregistrement ou l’impression.**  <br/> |
||||||**3.** <br/> |Choisissez **OK** pour appliquer la fonctionnalité de code-barres à la stratégie.  <br/> |
|||||||
 La stratégie de code-barres génère des codes-barres standard code 39. Chaque image de code-barres comprend du texte sous le symbole de code-barres qui représente la valeur du code-barres. Cela permet d’utiliser les données de code-barres même lorsque le matériel d’analyse n’est pas disponible. Les utilisateurs peuvent taper manuellement le numéro de code-barres dans la zone de recherche pour localiser l’élément sur un site.  <br/> |
   
1. Pour exiger que les documents soumis à cette stratégie ont des étiquettes, sélectionnez Activer les étiquettes, puis spécifiez les paramètres que vous souhaitez pour les étiquettes.
    
    Pour activer les étiquettes
    
||||||**1.**|**Pour exiger que les utilisateurs ajoutent une étiquette à un document, sélectionnez Demander aux utilisateurs d’insérer une étiquette **avant d’enregistrer ou d’imprimer.**  <br/> > [!NOTE]> si vous souhaitez que les étiquettes soient facultatives, ne cochez pas cette case.        **|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
||||||2.  <br/> |Pour verrouiller une étiquette afin qu’elle ne puisse pas être modifiée après son insertion, sélectionnez Empêcher les modifications apportées aux étiquettes une fois **qu’elles ont été ajoutées.**  <br/>  Ce paramètre empêche la mise à jour du texte de l’étiquette une fois l’étiquette insérée dans un élément dans une application cliente telle que Word, Excel ou PowerPoint. Si vous souhaitez que l’étiquette soit mise à jour lorsque les propriétés de ce document ou de cet élément sont mises à jour, ne cochez pas cette case.  <br/> |
||||||3.  <br/> |Dans la zone de format Étiquette, entrez le texte de l’étiquette tel que vous souhaitez l’afficher. Les étiquettes peuvent contenir jusqu’à 10 références de colonnes, dont chacune peut comporter jusqu’à 255 caractères. Pour créer le format de votre étiquette, vous pouvez :  <br/> Tapez les noms des colonnes que vous souhaitez inclure dans l’étiquette dans l’ordre dans lequel vous souhaitez qu’elles apparaissent. Inséez les noms de colonne entre crochets ( ), comme illustré dans l’exemple de la {} page Modifier la stratégie.  <br/> Tapez des mots pour identifier les colonnes en dehors des crochets, comme illustré dans l’exemple de la page Modifier la stratégie.  <br/> |
||||||4.  <br/> |Pour ajouter un coupure de lignes, entrez **\n** où vous souhaitez qu’il apparaisse.  <br/> |
||||||5.  <br/> |Sélectionnez la taille de police et le style de votre choix, puis indiquez si vous souhaitez positionner l’étiquette à gauche, au centre ou à droite dans le document.  <br/>  Sélectionnez une police et un style disponibles sur les ordinateurs des utilisateurs. La taille de la police affecte la quantité de texte qui peut être affichée sur l’étiquette.  <br/> |
||||||6.  <br/> |Entrez la hauteur et la largeur de l’étiquette. La hauteur de l’étiquette peut être de 0,25 à 20 pouces, et la largeur de l’étiquette peut être de 0,25 à 20 pouces. Le texte de l’étiquette est toujours centré verticalement au sein de l’image d’étiquette.  <br/> |
||||||7.  <br/> |Sélectionnez **Actualiser** pour afficher un aperçu du contenu de l’étiquette.  <br/> |
   
1. Sélectionnez **OK**.
    
## <a name="create-a-policy-for-a-list-library-or-folder-location-based-retention-policy"></a>Créer une stratégie pour une liste, une bibliothèque ou un dossier (stratégie de rétention basée sur l’emplacement)
<a name="__create_a_policy"> </a>

Vous pouvez définir une stratégie de rétention qui s’applique uniquement à une liste, une bibliothèque ou un dossier spécifique. Toutefois, si vous créez une stratégie de rétention de cette façon, vous ne pouvez pas réutiliser cette stratégie sur d’autres listes, bibliothèques, dossiers ou sites, et vous ne pouvez pas appliquer une stratégie de collection de sites à une stratégie basée sur l’emplacement.
  
Si vous souhaitez appliquer une stratégie de rétention unique à tous les types de contenu dans un seul emplacement, vous souhaitez probablement utiliser la rétention basée sur l’emplacement. Dans la plupart des autres cas, vous souhaitez vérifier qu’une stratégie de rétention est spécifiée pour tous les types de contenu.
  
 Chaque sous-folder hérite de la stratégie de rétention de son parent, sauf si vous choisissez de rompre l’héritage et de définir une nouvelle stratégie de rétention au niveau enfant. 
  
Si vous souhaitez définir une stratégie de gestion des informations autre que la rétention dans une liste ou une bibliothèque, vous devez définir une stratégie de gestion des informations pour chaque type de contenu de liste associé à cette liste ou bibliothèque.
  
 Si, à un moment donné, vous décidez de passer d’un type de contenu à une stratégie basée sur l’emplacement pour une liste ou une bibliothèque, seule la stratégie de rétention sera utilisée comme stratégie basée sur l’emplacement. Toutes les autres stratégies de gestion (audits, codes-barres et codes-barres) sont héritées des types de contenu associés. 
  
 Les stratégies basées sur l’emplacement peuvent être désactivées pour une collection de sites en désactivant la fonctionnalité Rétention basée sur la bibliothèque et les dossiers. Cela permet aux administrateurs de collections de sites de s’assurer que leurs stratégies de type de contenu ne sont pas overridées par les stratégies d’emplacement d’un administrateur de liste. 
  
Vous avez besoin au moins de l’autorisation Gérer les listes pour modifier les paramètres de stratégie de gestion des informations d’une liste ou d’une bibliothèque.
  
1. Accédez à la liste ou à la bibliothèque pour laquelle vous souhaitez spécifier une stratégie de gestion des informations. 
    
2. Dans le ruban, sélectionnez l’onglet **Bibliothèque** **ou** Liste Paramètres de la bibliothèque ou \> **Paramètres** de **liste.**
    
    Dans SharePoint Online, cliquez sur **Paramètres,** puis sur **Paramètres de** liste ou **Paramètres de bibliothèque.** 
    
3. Sous **les paramètres de stratégie de** gestion des autorisations et des informations de \> **gestion.**
  
![Lien des stratégies de gestion des informations sur la page paramètres de la bibliothèque de documents](../media/9fa6d366-6aab-49e1-a05c-898ac6f536e6.png)
  
4. Dans la page Paramètres de stratégie de gestion des informations, assurez-vous que la source de rétention de la liste ou de la bibliothèque est définie sur Bibliothèque et Dossiers. 
  
Si **le type de contenu** apparaît en tant que source, cliquez sur Modifier la **source,** puis cliquez sur **Bibliothèque et dossiers.** Vous êtes averti que les stratégies de rétention de type de contenu seront ignorées. Sélectionnez **OK**. 
    
5. Dans la page Modifier la stratégie, sous **Planification** de rétention basée sur la bibliothèque, entrez une brève description de la stratégie que vous créez. 
    
6. Choisissez **Ajouter une étape de rétention...**
    
     Notez que sous Enregistrements, vous pouvez choisir de définir différentes stratégies de rétention pour les enregistrements en sélectionnant l’option Définir différentes étapes de rétention pour les enregistrements. 
    
7. Dans la boîte de dialogue Propriétés de l’étape, sélectionnez une option de période de rétention pour spécifier le moment où les documents ou les éléments doivent expirer. Effectuez l’une des opérations suivantes :
    
  - Pour définir la date d’expiration  en fonction d’une propriété de date, sous Événement Cette étape est basée sur une propriété de date sur l’élément, puis sélectionnez l’action de document ou d’élément (par exemple, Créé ou Modifié) et l’incrément de temps après cette action (par exemple, le nombre de jours, mois ou années) lorsque vous souhaitez que l’élément \> expire. 
    
  - Pour utiliser une formule de rétention personnalisée pour déterminer l’expiration, choisissez Définir par une formule de rétention personnalisée **installée sur ce serveur.** 
    
    > [!NOTE]
    >  Cette option est disponible uniquement si une formule personnalisée a été définie par votre administrateur. 
  
  - Sous **Action,** spécifiez ce que vous souhaitez faire à l’expiration du document ou de l’élément. Pour activer une action spécifique sur le document ou l’élément (par exemple, la suppression), sélectionnez une action dans la liste. 
    
8. **L’option** Démarrer un flux de travail n’est disponible que si vous définissez une stratégie pour une liste, une bibliothèque ou un type de contenu qui possède déjà un flux de travail qui lui est associé. Vous aurez alors le choix entre les flux de travail. 
    
9. Sous **Récurrence,** **sélectionnez Répéter l’action de cette étape...** et entrez la fréquence de récurrisation de l’action. 
    
    > [!NOTE]
    >  Cette option est disponible uniquement si l’action que vous avez sélectionnée peut être répétée. Par exemple, vous ne pouvez pas définir la récurrence de l’action **Supprimer définitivement**. 
  
10. Sélectionnez **OK**.
    
## <a name="apply-a-site-collection-policy-to-a-content-type"></a>Appliquer une stratégie de collection de sites à un type de contenu
<a name="__apply_a_site"> </a>

Si des stratégies de gestion des informations ont déjà été créées pour votre site en tant que stratégies de collection de sites, vous pouvez appliquer l’une de ces stratégies à un type de contenu. En faisant cela, vous pouvez appliquer la même stratégie à plusieurs types de contenu dans une collection de sites qui ne partagent pas le même type de contenu parent.
  
 Si vous souhaitez appliquer des stratégies à plusieurs types de contenu dans une collection de sites et que vous avez configuré un service de métadonnées gérées, vous pouvez utiliser la publication de types de contenu pour publier des stratégies de gestion des informations sur plusieurs collections de sites. Pour plus d’informations, voir la section Appliquer une stratégie entre [les collections](#apply-a-policy-across-site-collections) de sites. 
  
1. Accédez à la liste ou à la bibliothèque qui contient le type de contenu auquel vous souhaitez appliquer une stratégie.
    
2. Dans le ruban, sélectionnez l’onglet **Bibliothèque** **ou** Liste Paramètres de la bibliothèque ou \> **Paramètres** de **liste.**
    
    Dans SharePoint Online, cliquez sur **Paramètres,** puis sur **Paramètres de** liste ou **Paramètres de bibliothèque.** 
    
3. Sous **les paramètres de stratégie de** gestion des autorisations et des informations de \> **gestion.**
  
![Lien des stratégies de gestion des informations sur la page paramètres de la bibliothèque de documents](../media/9fa6d366-6aab-49e1-a05c-898ac6f536e6.png)
  
4. Vérifiez que la source de stratégie est définie sur **Types** de contenu et, sous Stratégies de **type** de contenu, sélectionnez le type de contenu à appliquer à la stratégie. 
    
5. Sous **Spécifier la stratégie Utiliser** une stratégie de collection de sites, puis sélectionnez la stratégie à appliquer dans la \> liste. 
    
    > [!NOTE]
    >  Si **l’option Utiliser une stratégie de collection de** sites n’est pas disponible, aucune stratégie de collection de sites n’a été définie pour la collection de sites. 
  
6. Sélectionnez **OK**.
    
     Si la liste ou la bibliothèque avec laquelle vous travaillez prend en charge la gestion de plusieurs types de contenu, sous **Types** de contenu, vous pouvez choisir le type de contenu pour lequel vous souhaitez spécifier une stratégie de gestion des informations. Vous allez ainsi directement à l’étape 5 ci-dessus. 
    
## <a name="apply-a-policy-across-site-collections"></a>Appliquer une stratégie entre les collections de sites
<a name="__toc260646789"> </a>

Partager des types de contenu entre des collections de sites à l’aide d’une application de service de métadonnées gérées pour configurer la publication des types de contenu. La publication de types de contenu vous permet de gérer le contenu et les métadonnées de manière cohérente dans vos sites, car les types de contenu peuvent être créés et mis à jour de manière centralisée, et les mises à jour peuvent être publiées dans plusieurs collections de sites ou applications Web d’abonnement.
  
## <a name="create-a-template-from-an-existing-policy-to-use-across-site-collections"></a>Créer un modèle à partir d’une stratégie existante à utiliser dans les collections de sites
<a name="__toc262125409"> </a>

Vous pouvez définir une stratégie de gestion des informations, puis créer un modèle à partir de cette stratégie pour l’utiliser selon vos besoins dans plusieurs collections de sites. Cette méthode peut être utilisée si vous souhaitez une sauvegarde de vos stratégies d’information, ou elle peut également servir de méthode alternative à l’utilisation de la publication de type de contenu pour appliquer une stratégie parmi les collections de sites. Vous créez un modèle ou une sauvegarde de la stratégie en exportant la stratégie à partir d’une collection de sites, puis en l’important dans un emplacement enregistré ou dans une autre collection de sites.
  
> [!IMPORTANT]
>  Si vous utilisez la fonctionnalité d’exportation/importation pour créer un ensemble de modèles de stratégie, gardez à l’esprit qu’il existe un identificateur unique dans le fichier .xml de stratégie. Pour cette raison, vous ne pouvez pas importer cette stratégie dans un site plusieurs fois sans modifier cet identificateur unique. 
  
### <a name="export-a-policy"></a>Exporter une stratégie
<a name="__toc260646790"> </a>

1. Sur la page d’accueil de la collection de sites, choisissez l’engrenage **Paramètres** petits paramètres qui a pris la place des paramètres du ![ site. ](../media/a47a06c3-83fb-46b2-9c52-d1bad63e3e60.png) \> **Paramètres du site.**
    
    Dans un site connecté à un groupe SharePoint, cliquez sur **Paramètres,** sur Contenu du **site,** puis sur **Paramètres du site.** 
    
2. Dans la page Paramètres du site, sous **Modèles** de stratégie de type de contenu Administration de la collection \> **de sites.** 
  
![Lien Modèle de stratégie de type de contenu sur la page Paramètres du site](../media/26d3466a-23ec-443f-88f0-2aaff38e992b.png)
  
3. Choisissez la stratégie que vous souhaitez exporter faire \> défiler vers le bas \> **Exporter.**
    
4. À l’invite d’enregistrer ou d’ouvrir le fichier, sélectionnez **Enregistrer,** puis sélectionnez un emplacement où enregistrer le fichier. Assurez-vous de sélectionner un emplacement disponible pour les collections de sites qui importent la stratégie.
    
5. Lorsque la boîte de dialogue Télécharger terminé s’affiche, choisissez **Fermer.**
    
### <a name="import-a-policy-to-a-different-site-collection"></a>Importer une stratégie dans une autre collection de sites
<a name="__toc260646791"> </a>

L’importation d’une stratégie de gestion des informations vous permet de l’appliquer à plusieurs types de contenu au niveau du site ou de la liste au sein d’une collection de sites donnée. Les avantages de cette modification sont doubles : vous n’avez pas besoin de re-définir et d’appliquer la stratégie sur chaque type de contenu, et vous pouvez plus facilement gérer les modifications de stratégie en a apporter des modifications à la stratégie au même endroit.
  
1. Sur la page d’accueil de la collection de sites à laquelle vous souhaitez appliquer la stratégie, choisissez l’engrenage **Paramètres** petits paramètres qui a pris la place des paramètres du ![ site. ](../media/a47a06c3-83fb-46b2-9c52-d1bad63e3e60.png) \> **Paramètres du site.**
    
    Dans un site connecté à un groupe SharePoint, cliquez sur **Paramètres,** sur Contenu du **site,** puis sur **Paramètres du site.** 
    
2. Dans la page Paramètres du site, sous **Modèles** de stratégie de type de contenu Administration de la collection \> **de sites.**
    
3. Dans la page \> **Stratégies,** \> **importez Parcourir** pour rechercher le fichier XML de la stratégie. 
    
4. Sélectionnez le fichier XML dans lequel la stratégie a été enregistrée \> **Ouverte.** 
    
5. Dans la page Importer une stratégie de collection de \> **sites, importez** la stratégie pour ajouter la stratégie à la collection de sites. 
    
Votre stratégie importée peut désormais être appliquée à un ou plusieurs types de contenu au niveau du site ou de la liste. 
  
Les stratégies de gestion des informations permettent à votre organisation de contrôler la durée de rétention du contenu, d’auditer ce que les personnes font avec le contenu et d’ajouter des codes-barres ou des étiquettes aux documents. Une stratégie peut aider à appliquer la conformité avec les réglementations juridiques et gouvernementales ou les processus d’entreprise internes. En tant qu’administrateur, vous pouvez configurer une stratégie pour contrôler le suivi des documents et la durée de rétention des documents.

Vous pouvez créer une stratégie de gestion des informations à trois emplacements différents dans la hiérarchie de sites, du plus large au plus étroit :
- Créez une stratégie à utiliser sur plusieurs types de contenu au sein d’une collection de sites.
- Créez une stratégie pour un type de contenu de site.
- Créez une stratégie pour une liste ou une bibliothèque.

Pour plus d’informations, voir [Introduction aux stratégies de gestion des informations.](intro-to-info-mgmt-policies.md)
  

