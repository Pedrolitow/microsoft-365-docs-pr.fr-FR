---
title: Utiliser des modèles d’évaluation dans le Gestionnaire de conformité Microsoft
f1.keywords:
- NOCSH
ms.author: v-jgriffee
author: jmgriffee
manager: laurawi
audience: Admin
ms.topic: article
ms.custom: admindeeplinkMAC
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Comprendre comment utiliser et gérer des modèles pour la création d’évaluations dans le Gestionnaire de conformité Microsoft. Créez et modifiez des modèles à l’aide d’un fichier Excel formaté.
ms.openlocfilehash: 56bbe69b6baaa996a1b63e20ca657641b9da9038
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60173558"
---
# <a name="working-with-assessment-templates-in-compliance-manager"></a>Utiliser des modèles d’évaluation dans le Gestionnaire de conformité

**Dans cet article :** Comprendre **comment fonctionnent les modèles** et **comment les gérer** à partir de votre page de modèles d’évaluation. Obtenez des  instructions pour créer de  nouveaux modèles,  étendre et modifier des modèles existants, mettre en forme vos données de modèle avec **Excel** et exporter des rapports de **modèles.**

> [!IMPORTANT]
> Les modèles d’évaluation disponibles pour votre organisation dépendent de votre contrat de licence. [Examinez les détails.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)

## <a name="templates-overview"></a>Vue d’ensemble des modèles

Un modèle est une infrastructure de contrôles permettant de créer une évaluation dans le Gestionnaire de conformité. Notre ensemble complet de modèles peut aider votre organisation à se conformer aux exigences nationales, régionales et propres au secteur qui régissent la collecte et l’utilisation des données.

Nous faisons référence à des modèles du même nom que leur certification ou réglementation sous-jacente, comme le modèle R GDPR de l’UE et le modèle ISO/IEC 27701:2019. Étant donné que le gestionnaire de conformité peut être utilisé pour évaluer différents types de produits, chaque modèle est livré en deux versions : une qui s’applique à Microsoft 365 et une version universelle qui peut être adaptée à votre produit choisi.

Notez que les clients modérés, Cloud de la communauté du secteur public élevés et du département de la Défense (DoD) du gouvernement des États-Unis Community (Cloud de la communauté du secteur public) peuvent actuellement utiliser les versions du modèle Microsoft 365, mais pas universels.

## <a name="template-availability-and-licensing"></a>Disponibilité et gestion des licences des modèles

Il existe deux catégories de modèles dans le Gestionnaire de conformité : incluse et premium.

1. **Les modèles inclus sont accordés** par votre licence du Gestionnaire de conformité et couvrent les principales réglementations et exigences. Pour en savoir plus sur les modèles disponibles dans le cadre de votre contrat de licence, consultez les [détails de la gestion des licences.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#compliance-manager)
2. **Premium modèles supplémentaires** pour répondre à des besoins et scénarios supplémentaires peuvent être obtenus par l’achat de licences de modèles.

Lorsque vous commencez à créer des évaluations, le Gestionnaire de conformité suit le nombre de modèles actifs afin de pouvoir surveiller votre utilisation. Pour en savoir plus, [consultez les modèles actifs et inactifs.](compliance-manager-templates.md#active-and-inactive-templates)

Affichez [la liste complète des modèles disponibles](compliance-manager-templates-list.md) dans le Gestionnaire de conformité.

### <a name="purchase-premium-template-licenses"></a>Acheter des licences de modèle premium

Les licences de modèle peuvent être obtenues par une ou plusieurs de ces méthodes, en fonction de votre contrat de licence du Gestionnaire de conformité. Une fois votre achat finalisé, les modèles doivent être disponibles dans votre client dans les 48 heures.

**Commercial et Cloud de la communauté du secteur public Modéré**

Les comptes commerciaux et Cloud de la communauté du secteur public modérés peuvent acheter des licences de modèles dans le Centre d’administration (en savoir plus sur les[abonnements, les licences et la facturation).](/microsoft-365/commerce/) Sélectionnez le nombre de licences que vous souhaitez acheter et votre plan de paiement.

Liens d’achat :

- [Commerciale](https://admin.microsoft.com/Adminportal/Home?#/catalog/offer-details/compliance-manager-premium-assessment-add-on/46E9BF2A-3C8D-4A69-A7E7-3DA04687636D)
- [Cloud de la communauté du secteur public Modéré](https://admin.microsoft.com/Adminportal/Home?#/catalog/offer-details/compliance-manager-premium-assessment-add-on/3129986d-5f4b-413b-a34b-b706db5a7669)

Vous pouvez également acquérir des licences par le biais de votre participation au [programme fournisseur de solutions Cloud licences](https://partner.microsoft.com/membership/cloud-solution-provider) [en volume ou en volume.](https://www.microsoft.com/licensing/licensing-programs/licensing-programs)

**Cloud de la communauté du secteur public Comptes DOD et élevés**

Cloud de la communauté du secteur public Les comptes DOD et élevés doivent acheter des licences de modèles par le biais [de licences en volume.](https://www.microsoft.com/licensing/licensing-programs/licensing-programs)

### <a name="try-out-premium-templates"></a>Essayer des modèles Premium

Pour tester des modèles premium avant d’effectuer un achat, vous pouvez également acquérir des versions d’essai des licences. Les licences d’essai sont valides pour 25 modèles au plus pendant 90 jours. Une fois que vous avez obtenu votre licence d’essai, les modèles doivent être disponibles dans votre client dans les 48 heures.

Pour démarrer une version d’essai, choisissez le lien approprié pour votre organisation :

- [Commerciale](https://admin.microsoft.com/Adminportal/Home?#/catalog/offer-details/compliance-manager-premium-assessment-add-on/e320704d-b7c9-4012-b6a6-0a2679790360)
- [Cloud de la communauté du secteur public Modéré](https://admin.microsoft.com/Adminportal/Home?#/catalog/offer-details/compliance-manager-premium-assessment-add-on/87ed2908-0a8d-430a-9635-558ed42b581f)
- [GCC High](https://portal.office365.us/SubscriptionDetails?OfferId=e14362d7-2c11-4a43-9c92-59f1b499b96a)
- [DOD](https://portal.apps.mil/Commerce/Trial.aspx?OfferId=17e28290-7de6-41a9-af30-f6497396ab2e)

#### <a name="active-and-inactive-templates"></a>Modèles actifs et inactifs

Les modèles affichent un état d’activation comme actif ou inactif :

- Un modèle est considéré **comme actif** une fois que vous avez créé une évaluation à partir de ce modèle.
- Un modèle est considéré **comme inactif** si votre organisation ne l’utilise pas pour une évaluation.

Si vous liez des évaluations à un modèle Premium acheté, ce modèle sera actif pendant un an. Votre achat sera renouvelé automatiquement, sauf si vous annulez.

Vous pouvez également essayer des modèles Premium en version d’essai. Les licences d’essai sont valides pour 25 modèles au plus pendant 30 jours. Une fois votre version d’essai commencée, les modèles doivent être disponibles dans votre client dans les 48 heures. Les essais peuvent être activés via <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">le Centre d'administration Microsoft 365</a>.

#### <a name="activated-templates-counter"></a>Compteur de modèles activés

Votre page d’évaluation et votre page de modèles d’évaluation ont un compteur de **modèles** activé dans la partie supérieure. Le compteur affiche le nombre de modèles utilisés en dehors du nombre que vous êtes éligible pour utiliser conformément à votre contrat de licence. L’utilisation des modèles est comptabilisée au niveau de certification.

Par exemple, si votre compteur affiche 2/5, cela signifie que votre organisation a activé 2 modèles sur les 5 disponibles.

Si votre compteur affiche le 5/2, cela indique que votre organisation dépasse ses limites et doit acheter 3 des modèles Premium utilisés.

Microsoft 365 versions universelles et universelles des modèles ont des licences conjointes, afin que vous pouvez utiliser la même certification sous-jacente sur plusieurs produits. L’utilisation de l’une ou des deux versions du même modèle ne compte qu’en tant que modèle activé.

Pour plus d’informations, consultez les conseils de gestion [des licences du Gestionnaire de conformité.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#compliance-manager)

## <a name="view-and-manage-templates"></a>Afficher et gérer des modèles

La page modèles d’évaluation dans le Gestionnaire de conformité affiche une liste de modèles et des détails clés les concernant. La liste inclut les modèles fournis par le Gestionnaire de conformité, ainsi que tous les modèles que votre organisation a modifiés ou créés. Vous pouvez appliquer des filtres pour rechercher un modèle basé sur la certification, l’étendue du produit, le pays, l’industrie, qui l’a créé et si le modèle est activé pour la création de l’évaluation.

Sélectionnez un modèle dans sa ligne pour faire monter sa page de détails. Cette page contient une description du modèle et des informations supplémentaires sur la certification, l’étendue et les détails des contrôles. À partir de cette page, vous pouvez sélectionner les boutons appropriés pour créer une évaluation, exporter les données du modèle vers Excel ou modifier le modèle.

## <a name="format-template-data-with-excel"></a>Formater des données de modèle avec Excel

La feuille de calcul Excel[(télécharger](https://go.microsoft.com/fwlink/?linkid=2124865)un exemple) utilisée pour créer ou modifier des modèles possède un format et un schéma spécifiques qui doivent être utilisés pour importer correctement dans le Gestionnaire de conformité. Il contient quatre onglets, dont trois sont obligatoires :

1. [Modèle](#template-tab) (obligatoire)
2. [ControlFamily](#controlfamily-tab) (obligatoire)
3. [Actions](#actions-tab) (obligatoires)
4. [Dimensions](#dimensions-tab) (facultatif)

Lorsque vous remplissez votre feuille de calcul avec des données de modèle, la feuille de calcul doit inclure les **onglets** dans l’ordre répertorié ci-dessus, sinon vos données ne seront pas correctement importées dans un modèle.

##### <a name="template-tab"></a>Onglet Modèle

**L’onglet** Modèle est obligatoire. Les informations de cet onglet fournissent des métadonnées sur le modèle. Il existe quatre colonnes obligatoires. Les colonnes doivent conserver l’ordre dans la feuille Excel comme répertorié ci-dessous. Vous pouvez ajouter votre propre colonne **après les** quatre colonnes pour fournir vos propres dimensions. Si vous le faites, n’oubliez pas de les ajouter à **l’onglet Dimensions.**

- **titre**: il s’agit du titre de votre modèle, qui doit être unique. Il ne peut pas partager un nom avec un autre modèle que vous avez dans le Gestionnaire de conformité, y compris vos propres modèles ou un modèle gestionnaire de conformité.

- **produit**: il s’agit d’une dimension obligatoire. Liste du produit associé au modèle.

- **certification**: il s’agit de la réglementation que vous utilisez pour le modèle.

- **inScopeServices**: il s’agit des services au sein du produit que cette évaluation traite (par exemple, si vous avez répertorié Office 365 comme produit, Microsoft Teams peut être un service dans l’étendue). Vous pouvez lister plusieurs services séparés par deux points-virgules.

> [!NOTE]
> Les données que  vous insérez dans les cellules de produit et de **certification** ne peuvent pas être modifiées après avoir importé la feuille de calcul pour créer ou personnaliser un modèle. En outre, un groupe ne peut pas contenir deux évaluations qui ont la même combinaison **produit/certification.** Vous pouvez avoir plusieurs modèles avec la même combinaison produit/certification.

##### <a name="controlfamily-tab"></a>Onglet ControlFamily

**L’onglet ControlFamily** est obligatoire.  Les colonnes requises dans cet onglet, qui doivent suivre l’ordre indiqué dans l’exemple de feuille de calcul, sont les suivants :

- **controlName :** il s’agit du nom du contrôle de la certification, de la norme ou de la réglementation, qui est généralement un type d’ID. Les noms des contrôles doivent être uniques dans un modèle. Vous ne pouvez pas avoir plusieurs contrôles du même nom dans la feuille de calcul.

- **controlFamily**: fournissez un mot ou une expression pour le controlFamily, qui identifie un groupe étendu de contrôles. Un controlFamily n’a pas besoin d’être unique ; Il peut être répertorié plusieurs fois dans une feuille de calcul. Le même controlFamily peut également être répertorié dans plusieurs modèles, bien qu’ils n’ont aucune relation les uns avec les autres. Chaque controlFamily doit être mappé sur au moins un contrôle.

- **controlTitle :** fournir un titre pour le contrôle. Alors que controlName est un code de référence, le titre est un format de texte enrichi généralement vu dans les réglementations.

- **controlDescription**: fournir une description du contrôle.

- **controlActionTitle**: il s’agit du titre d’une action que vous souhaitez mettre en relation avec ce contrôle. Vous pouvez ajouter plusieurs actions en les séparant par deux points-virgules sans espace. Chaque contrôle que vous listez doit inclure au moins une action et l’action doit exister (ce qui signifie que vous pouvez lister une action que vous avez répertoriée sous l’onglet **Actions** de la même feuille de calcul, une action qui existe dans un autre modèle ou une action créée par Microsoft). Différents contrôles peuvent faire référence à la même action.

##### <a name="actions-tab"></a>Onglet Actions

**L’onglet Actions** est obligatoire.  Il désigne les actions d’amélioration gérées par votre organisation et non celles de Microsoft, qui existent déjà dans le Gestionnaire de conformité. Les colonnes requises pour cet onglet, qui doivent suivre l’ordre indiqué dans l’exemple de feuille de calcul, sont les suivants :

- **actionTitle**: il s’agit du titre de votre action et d’un champ obligatoire. Le titre que vous fournissez doit être unique. **Important**: si vous référencez une action que vous possédez qui existe déjà (par exemple dans un autre modèle) et que vous modifiez l’un de ses éléments dans les colonnes suivantes, ces modifications se propagent à la même action dans d’autres modèles.

- **implementationType**: dans ce champ obligatoire, listez l’un des trois types d’implémentation ci-dessous :
    - **Opérationnel** : actions implémentées par les personnes et les processus pour protéger la confidentialité, l’intégrité et la disponibilité des systèmes organisationnels, des ressources, des données et du personnel (exemple : sensibilisation et formation en matière de sécurité)
    - **Technique** : actions effectuées à l’aide de la technologie et des mécanismes contenus dans le matériel, les logiciels ou les composants du microprogramme du système d’information pour protéger la confidentialité, l’intégrité et la disponibilité des données et des systèmes organisationnels (exemple : authentification multifacteur)
    - **Documentation** : actions implémentées par le biais de stratégies et de procédures documentées établissant et définissant les contrôles requis pour protéger la confidentialité, l’intégrité et la disponibilité des systèmes organisationnels, des biens, des données et du personnel (par exemple, une stratégie de sécurité des informations)

- **actionScore**: dans ce champ obligatoire, fournissez une valeur de score numérique pour votre action. La valeur doit être un nombre entier compris entre 1 et 99 ; il ne peut pas être 0, null ou vide. Plus le nombre est élevé, plus sa valeur est grande pour améliorer votre posture de conformité. L’image ci-dessous montre comment le Gestionnaire de conformité contrôle les scores :

  ![Le Gestionnaire de conformité contrôle les valeurs de points.](../media/compliance-score-action-scoring.png "Le Gestionnaire de conformité contrôle les valeurs de point")

- **actionDescriptionTitle**: il s’agit du titre de la description et est obligatoire. Ce titre de description vous permet d’avoir la même action dans plusieurs modèles et d’en faire une description différente dans chaque modèle.  Ce champ vous aide à clarifier le modèle référent de la description. Dans la plupart des cas, vous pouvez placer le nom du modèle que vous créez dans ce champ.

- **actionDescription**: fournir une description de l’action. Vous pouvez appliquer une mise en forme telle que du texte gras et des liens hypertexte. Ce champ est obligatoire.

- **dimension-Action Purpose**: il s’agit d’un champ facultatif. Si vous l’incluez, l’en-tête doit inclure le préfixe « dimension - ». Toutes les dimensions que vous incluez ici seront utilisées comme filtres dans le Gestionnaire de conformité et apparaîtront dans la page détails des actions d’amélioration dans le Gestionnaire de conformité.

##### <a name="dimensions-tab"></a>Onglet Dimensions

**L’onglet Dimensions** est facultatif. Toutefois, si vous référencez une dimension ailleurs, vous devez la spécifier ici si elle n’existe pas dans un modèle que vous avez déjà créé ou dans un modèle Microsoft. Les colonnes de cet onglet sont répertoriées ci-dessous :

- **dimensionKey**: liste en tant que « produit », « certifications », « objectif de l’action »
- **dimensionValue :** exemples : Office 365, HIPPA, Préventive, Inspecteur

Lorsque vous exportez un modèle existant, la feuille de calcul exportée a l’onglet **Dimensions,** qui répertorie toutes les dimensions utilisées dans le modèle.

## <a name="create-an-assessment-template"></a>Créer un modèle d’évaluation

Pour créer votre propre modèle pour les évaluations personnalisées, vous utiliserez votre feuille de calcul spécialement mise en forme Excel pour assembler les données de contrôle nécessaires. Après avoir terminé la feuille de calcul, vous l’importez dans le Gestionnaire de conformité.

#### <a name="required-roles"></a>Rôles requis

Seuls les utilisateurs qui détiennent un rôle d’administrateur général ou d’administration du Gestionnaire de conformité peuvent créer et modifier des modèles. En savoir plus sur [les rôles et les autorisations.](compliance-manager-setup.md#set-user-permissions-and-assign-roles)

### <a name="create-new-template-in-compliance-manager"></a>Créer un modèle dans le Gestionnaire de conformité

1. Go to your **assessment templates** page in Compliance Manager.
2. Sélectionnez **Créer un modèle.** Un Assistant Création de modèle s’ouvre.
3. Choisissez le type de modèle que vous souhaitez créer. Dans ce cas, **sélectionnez Créer un modèle personnalisé,** puis sélectionnez **Suivant.**
4. Dans le **Télécharger** de fichiers,  sélectionnez Parcourir pour rechercher et télécharger votre fichier Excel formaté contenant toutes les données de modèle requises.
5. En l’absence de problème avec votre fichier, le nom du fichier téléchargé s’affiche. Sélectionnez **Suivant** pour continuer. (Si vous devez modifier le fichier, sélectionnez **Télécharger un autre fichier).**
    - En cas d’erreur avec votre fichier, un message d’erreur en haut explique ce qui ne va pas. Vous devez corriger votre fichier et le charger à nouveau. Des erreurs se résultent si votre feuille de calcul n’est pas correctement mise en forme ou s’il existe des informations non valides dans certains champs.
6. **L’écran Révision et fin** affiche le nombre d’actions et de contrôles d’amélioration et le score maximal pour le modèle. Lorsque vous êtes prêt à approuver, **sélectionnez Créer un modèle.** (Si vous devez apporter des modifications, sélectionnez **Retour.)**
7. Le dernier écran confirme qu’un nouveau modèle a été créé. Sélectionnez **Terminé** pour quitter l’Assistant.
8. Vous arrivez à la page de détails de votre nouveau modèle, où vous pouvez [créer votre évaluation.](compliance-manager-assessments.md#create-assessments)

## <a name="extend-microsoft-365-assessment-templates"></a>Étendre Microsoft 365 modèles d’évaluation

Le Gestionnaire de conformité offre la possibilité d’ajouter vos propres contrôles et actions d’amélioration à un modèle microsoft existant. Ce processus est appelé extension d’un modèle Microsoft. Lorsque vous étendez un modèle, il peut toujours recevoir des mises à jour publiées par Microsoft, ce qui peut se produire lorsque des modifications sont apportées à la réglementation ou au produit associé (voir Accepter les mises à jour des [évaluations).](compliance-manager-assessments.md#accept-updates-to-assessments)

Notez que si vous avez mis en place des évaluations pour des produits autres que Microsoft 365, votre processus sera différent. Pour plus d’informations, voir [Étendre les modèles d’évaluation universels.](#extend-universal-assessment-templates)

### <a name="prepare-template-data-and-create-extension"></a>Préparer les données de modèle et créer une extension

Pour vous préparer, vous devez assembler une feuille de calcul Excel spécialement mise en forme pour importer les données de modèle nécessaires. Les Excel suivent le même format général décrit ci-dessus, mais il existe des exigences spéciales pour les extensions. Consultez ces points supplémentaires pour éviter les erreurs :

- Votre feuille de calcul doit contenir uniquement les actions et les contrôles que vous souhaitez ajouter à l’évaluation.
- La feuille de calcul ne peut contenir aucun des contrôles ou actions qui existent déjà dans l’évaluation que vous souhaitez modifier.
- Envisagez d’inclure « extension » dans le titre de votre modèle, par exemple, « R GDPR – extension [nom de votre société] ». Cela facilite l’identification, dans la liste de vos **modèles** d’évaluation, du modèle standard fourni par Microsoft ou d’un modèle personnalisé avec un nom similaire.

Après avoir formaté votre feuille de calcul, suivez les étapes ci-dessous.

1. Go to your **Assessment templates** page and select **Create new template**. Un Assistant Création de modèle s’ouvre.

2. Choisissez le type de modèle que vous souhaitez créer. Dans ce cas, **sélectionnez Étendre un modèle Microsoft,** puis **sélectionnez Modèle Microsoft.**

3. Un volet volant de sélection de modèle s’affiche sur le côté droit de votre écran, affichant la liste de tous les modèles et leur statut d’actif ou inactif. Votre **compteur de modèles activés** indique le nombre de modèles actuellement utilisés sur le nombre total disponible. Si vous avez terminé votre limite, une barre de messages vous fournira un avis.

4. Un volet volant de sélection de modèle s’affiche sur le côté droit de votre écran. Utiliser **la recherche** pour appliquer des filtres pour localiser le modèle de votre recherche

5. Une fois que vous avez localisé votre modèle, sélectionnez la radio à gauche de son nom, puis sélectionnez **Enregistrer**.

6. L’écran suivant montre le modèle que vous avez sélectionné. Si la réponse est correcte, sélectionnez **Suivant.** (Si ce n’est pas le cas, **sélectionnez Sélectionner** un autre modèle à choisir à nouveau.)

7. Dans le **Télécharger** de fichiers,  sélectionnez Parcourir pour rechercher et télécharger votre fichier Excel formaté contenant toutes les données de modèle requises.

8. S’il n’y a aucun problème avec votre fichier, l’écran suivant affiche le nom du fichier téléchargé. Sélectionnez Suivant pour continuer (si vous devez modifier le fichier, sélectionnez **Télécharger un autre fichier).** 

    - En cas de problème avec votre fichier, un message d’erreur en haut explique ce qui ne va pas. Vous devrez corriger et charger à l’autre votre fichier. Des erreurs se résultent si votre feuille de calcul n’est pas correctement mise en forme ou s’il existe des informations non valides dans certains champs.

9. **L’écran Révision et fin** affiche le nombre d’actions et de contrôles d’amélioration et le score maximal pour le modèle. Lorsque vous êtes prêt à approuver, sélectionnez **Suivant.** (Si vous devez apporter des modifications, **sélectionnez Télécharger fichier différent.)**

10. Le dernier écran confirme qu’un nouveau modèle a été créé. Sélectionnez **Terminé** pour quitter l’Assistant.

11. Vous arrivez à la page de détails de votre nouveau modèle. À partir de là, vous pouvez créer votre évaluation en sélectionnant **Créer une évaluation.** Pour obtenir des conseils, [voir Créer et gérer des évaluations.](compliance-manager-assessments.md#create-assessments)

## <a name="extend-universal-assessment-templates"></a>Étendre les modèles d’évaluation universels

Les versions universelles des modèles peuvent également être étendues pour personnaliser vos évaluations spécifiques à vos produits. Vous recevrez un modèle d’extension spécial lorsque vous créerez une évaluation à l’aide d’un modèle universel et que l’évaluation possède une combinaison de produit et de certification unique. Cela peut être modifié pour répondre à vos besoins. Pour obtenir des instructions sur la modification du modèle, consultez les instructions ci-dessous sur la modification d’un modèle.

Lors de la modification d’un modèle universel, tout le contenu du modèle peut être modifié, mais cela va rompre l’héritage avec le modèle parent. Cela signifie qu’il ne recevra plus automatiquement les mises à jour de Microsoft si le modèle parent est actualisé.

## <a name="modify-a-template"></a>Modifier un modèle

Vous pouvez modifier un modèle que vous avez déjà créé, par exemple pour ajouter des contrôles ou ajouter ou supprimer des actions d’amélioration. Le processus est similaire au processus de création de modèle dans la façon dont vous allez charger le fichier Excel formaté avec vos données de modèle.

Toutefois, vous devez connaître certains détails lorsque vous formatez votre fichier avec les modifications apportées aux données de modèle existantes. **Nous vous recommandons de consulter attentivement ces instructions pour vous assurer que vous n’avez pas de données existantes à conserver.**

### <a name="format-your-excel-file-to-modify-an-existing-template"></a>Mettre en forme Excel fichier pour modifier un modèle existant

Dans la page **de vos modèles d’évaluation,** sélectionnez le modèle que vous souhaitez modifier, qui   fera monter sa page de détails. Ensuite, **sélectionnez Exporter Excel**. Un Excel avec toutes vos données de modèle sera téléchargé. Enregistrez le fichier sur votre ordinateur local.

Pour travailler avec ce fichier, allez dans la section ci-dessous pour trouver rapidement les instructions dont vous avez besoin :

- [Modifier les attributs du modèle principal](#edit-the-main-template-attributes)
- [Ajouter une action d’amélioration](#add-an-improvement-action)
- [Modifier les informations d’une action d’amélioration](#edit-an-improvement-actions-information)
- [Modifier le nom d’une action d’amélioration](#change-an-improvement-actions-name)
- [Supprimer une action d’amélioration](#remove-an-improvement-action)
- [Supprimer un contrôle](#remove-a-control)

#### <a name="edit-the-main-template-attributes"></a>Modifier les attributs du modèle principal

Sous **l’onglet Modèles,** vous  pouvez modifier n’importe quoi dans la colonne de titre, la colonne **inScopeServices** et dans toute autre colonne que vous avez peut-être ajoutée. Toutefois, vous ne pouvez rien modifier dans les colonnes **de** **produit ou de certification.**

#### <a name="add-an-improvement-action"></a>Ajouter une action d’amélioration

1. Go to the **Actions** tab. Ajoutez vos informations dans les champs obligatoires de la première ligne vide sous vos actions existantes.
2. Go to your **ControlFamily** tab. Recherchez la ligne contenant le contrôle sur lequel votre action d’amélioration est m interactive. Ajoutez votre nouvelle action à la colonne **controlActionTitle** de cette ligne (n’oubliez pas de séparer plusieurs actions de ce champ par deux points-virgules, sans espace entre les deux).
3. Enregistrez votre feuille de calcul.

#### <a name="edit-an-improvement-actions-information"></a>Modifier les informations d’une action d’amélioration

Vous pouvez modifier les informations de n’importe quelle action d’amélioration *à l’exception de son titre.* Vous pouvez modifier n’importe quelle cellule à partir des colonnes B et, lorsque vous importez de nouveau le fichier dans le modèle, les actions d’amélioration de ce modèle contiennent désormais les données mises à jour.

Vous ne pouvez pas modifier **actionTitle** (colonne A), car si vous le faites, le Gestionnaire de conformité considère qu’il s’agit d’une nouvelle action d’amélioration. Si vous souhaitez modifier le nom d’une action d’amélioration, consultez les instructions ci-dessous.

#### <a name="change-an-improvement-actions-name"></a>Modifier le nom d’une action d’amélioration

Si vous souhaitez modifier le nom d’une action d’amélioration, vous devez indiquer explicitement dans la feuille de calcul que vous remplacez un nom existant par un nouveau nom. Procédez comme suit :

1. Dans **l’onglet Actions** de votre feuille de calcul, ajoutez une nouvelle colonne à la feuille de calcul après la colonne A.
2. Dans cette nouvelle colonne, qui est maintenant la colonne B, placez comme en-tête dans la ligne 1 : **oldActionTitle**.
3. Copiez le contenu de la colonne A et collez-le dans la colonne B. Cela place vos titres d’action d’amélioration existants, qui sont ce que vous souhaitez modifier, dans la colonne B.
4. Dans la colonne A, **actionTitle**, supprimez l’ancien nom et remplacez-le par le nouveau nom de votre action d’amélioration.

Notez que les titres d’action, à la fois pour vos actions d’amélioration et pour les actions Microsoft, doivent être écrits en anglais afin d’être reconnus lorsqu’ils sont référencés dans les contrôles.

#### <a name="remove-an-improvement-action"></a>Supprimer une action d’amélioration

Pour supprimer une action d’amélioration d’un modèle, vous devez la supprimer de chaque contrôle qui le référence. Suivez les étapes ci-dessous pour modifier votre feuille de calcul :

1. Sous **l’onglet ControlFamily,** recherchez le titre de l’action d’amélioration à supprimer.
2. Supprimez le titre de l’action d’amélioration dans les cellules où elle apparaît. Si l’action d’amélioration est la seule action sur cette ligne, supprimez la ligne entière (ce qui supprime le contrôle).
3. Sous **l’onglet Actions,** supprimez la ligne qui contient l’action d’amélioration que vous supprimez.
4. Enregistrez votre feuille de calcul.

Lorsque vous importez de nouveau votre feuille de calcul dans le modèle, votre action d’amélioration est supprimée du modèle.

La suppression d’une action d’amélioration d’un modèle ne supprime pas complètement l’action d’amélioration du Gestionnaire de conformité. Cette action peut toujours être référencé par un autre modèle.

#### <a name="remove-a-control"></a>Supprimer un contrôle

Pour supprimer un contrôle, modifiez votre feuille de calcul en suivant les étapes ci-dessous, puis ré-importez votre feuille de calcul :

1. Sous **l’onglet ControlFamily,** recherchez le contrôle à supprimer dans la **colonne controlName.**
2. Supprimez la ligne de ce contrôle.
    - Si ce contrôle supprimé contient des actions d’amélioration qui ne sont référencés par aucun autre contrôle, vous devez supprimer ces actions d’amélioration de **l’onglet Actions.** Sinon, vous recevrez une erreur de validation.

3. Enregistrez votre feuille de calcul.

Lorsque vous importez de nouveau votre feuille de calcul dans le modèle, votre contrôle est supprimé du modèle.

### <a name="modify-template-info-in-compliance-manager"></a>Modifier les informations du modèle dans le Gestionnaire de conformité

Une fois que Excel fichier est terminé et enregistré, suivez ces étapes.

1. Ouvrez à nouveau la page du modèle d’évaluation et sélectionnez votre modèle. Sur la page de détails de votre modèle, **sélectionnez Modifier le modèle** pour lancer l’Assistant Modification.
2. Dans le **Télécharger de fichier,** sélectionnez **Parcourir** pour rechercher et télécharger Excel fichier.
3. S’il n’y a aucun problème avec votre fichier, l’écran suivant affiche le nom du fichier téléchargé. Sélectionnez Suivant pour continuer (si vous devez modifier le fichier, sélectionnez **Télécharger un autre fichier).** 
    - En cas de problème avec votre fichier, un message d’erreur en haut explique ce qui ne va pas. Vous devez corriger votre fichier et le charger à nouveau. Des erreurs se résultent si votre feuille de calcul n’est pas correctement mise en forme ou s’il existe des informations non valides dans certains champs.

4. **L’écran Révision et fin** affiche le nombre d’actions et de contrôles d’amélioration et le score maximal pour le modèle. Lorsque vous êtes prêt à approuver, sélectionnez **Suivant.**
5. Le dernier écran confirme que le modèle a été modifié. Sélectionnez **Terminé** pour quitter l’Assistant.

Votre modèle inclut désormais les modifications que vous avez apportées. Toutes les évaluations qui utilisent ce modèle modifié afficheront désormais les mises à jour en attente, et vous devrez accepter les mises à jour des évaluations pour refléter les modifications apportées dans le modèle. En savoir plus sur [les mises à jour des évaluations.](compliance-manager-assessments.md#accept-updates-to-assessments)

> [!NOTE]
> Si vous utilisez le Gestionnaire de conformité dans une langue autre que l’anglais, vous remarquerez qu’un texte s’affiche en anglais lorsque vous exportez un modèle vers Excel. Les titres des actions (vos actions d’amélioration et, le cas échéant, les actions Microsoft) doivent être en anglais pour être reconnus par les contrôles. Si vous modifiez un titre d’action, veillez à l’écrire en anglais afin que le fichier importe correctement.

## <a name="export-a-template"></a>Exporter un modèle

Vous pouvez exporter un Excel qui contient toutes les données d’un modèle. Vous devez exporter un modèle pour le modifier, car il s’agit du fichier Excel que vous modifiez et téléchargez dans le processus [de modification.](#modify-a-template) Vous pouvez également exporter un modèle pour référence si vous souhaitez utiliser des données à partir de ce modèle lors de la construction d’un nouveau modèle personnalisé.

Pour exporter votre modèle, go to your template details page and select the **Export to Excel** button.

Notez que lors de l’exportation d’un modèle que vous avez étendu à partir d’un modèle gestionnaire de conformité, le fichier exporté contient uniquement les attributs que vous avez ajoutés au modèle. Le fichier exporté n’inclut pas les données de modèle d’origine fournies par Microsoft. Pour obtenir un tel rapport, consultez les instructions d’exportation [d’un rapport d’évaluation.](compliance-manager-assessments.md#export-an-assessment-report)
