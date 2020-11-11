---
title: Types d’explication
ms.author: efrene
author: efrene
manager: pamgreen
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
localization_priority: Priority
description: En savoir plus sur les types d’explications dans Microsoft SharePoint Syntex
ms.openlocfilehash: 2d76fec3ee98f7c096c44a2b19b52da9fb70859d
ms.sourcegitcommit: 82d8be71c5861a501ac62a774b306a3fc1d4e627
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "48988761"
---
# <a name="introduction-to-explanation-types"></a>Introduction aux types d’explications

Les explications sont utilisées pour vous permettre de définir les informations que vous souhaitez étiqueter et extraire dans vos modèles de compréhension de documents dans Microsoft SharePoint Syntex. Lors de la création d’une explication, vous devez sélectionner un type d’explication. Cet article vous permet de comprendre les différents types d’explications et comment ils sont utilisés. 

   ![Types d’explication](../media/content-understanding/explanation-types.png) 
   
Les types d’explications suivants sont disponibles :

- **Liste d’expressions**  : liste de mots, expressions, nombres ou autres caractères que vous pouvez utiliser dans le document ou les informations que vous extrayez. Par exemple, la chaîne de texte **Médecin référent** se trouve dans tous les documents de référence médicale que vous identifiez.</br>

- **Liste de modèles**  : répertorie les modèles de chiffres, de lettres ou d’autres caractères que vous pouvez utiliser pour identifier les informations que vous extrayez. Par exemple, vous pouvez extraire le **numéro de téléphone** du médecin référent de tous les documents de référence médicale que vous identifiez.</br>

- **Proximité**  : décrit à quel point les explications sont proches les unes des autres. Par exemple, une liste de modèles de *numéros de rue* se trouve juste avant la liste d’expressions des *noms de rue* , sans jetons entre les deux (vous en apprendrez davantage sur les jetons plus loin dans cet article). L’utilisation du type de proximité nécessite que vous ayez au moins deux explications dans votre modèle. Dans le cas contraire, l’option sera désactivée. 
 
## <a name="phrase-list"></a>Liste d’expressions

Un type d’explication de liste d’expressions est généralement utilisé pour identifier et classer un document dans votre modèle. Comme décrit dans l’exemple d’étiquette *Médecin référent* , il s’agit d’une chaîne de mots, d’expressions, de nombres ou de caractères qui se trouve systématiquement dans les documents que vous identifiez.

Bien que ce ne soit pas obligatoire, vous pouvez améliorer les performances de votre explication si l’expression que vous capturez se trouve à un emplacement cohérent dans votre document. Par exemple, l’étiquette *Médecin référent* peut être située systématiquement dans le premier paragraphe du document.

Si le respect de la casse est une exigence pour identifier votre étiquette, l’utilisation du type de liste d’expressions vous permet de le spécifier dans votre explication en cochant la case **Seulement la mise en majuscule exacte**.

   ![Respect de la casse](../media/content-understanding/case-sensitivity.png) 

## <a name="pattern-lists"></a>Listes de modèles

Un type de liste de modèles est particulièrement utile lorsque vous créez une explication qui identifie et extrait des informations d’un document. Il est généralement présenté dans différents formats, tels que des dates, des numéros de téléphone et des numéros de carte bancaire. Par exemple, une date peut être affichée dans plusieurs formats différents (1/1/2020, 1-1-2020, 01/01/20, 01/01/2020, 1 janvier 2020, etc.). La définition d’une liste de modèles rend votre explication plus efficace en capturant toutes les variations possibles dans les données que vous essayez d’identifier et d’extraire. 

Pour l’exemple du **numéro de téléphone** , vous extrayez le numéro de téléphone de chaque médecin traitant dans tous les documents de référence médicale que le modèle identifie. Lorsque vous créez l’explication, sélectionnez le type de liste de modèles pour autoriser les différents formats que vous pouvez vous attendre à renvoyer.

   ![Liste de modèles de numéros de téléphone](../media/content-understanding/pattern-list.png)

Pour cet exemple, activez la case à cocher **N’importe quel chiffre de 0 à 9** pour identifier chaque valeur « 0 » utilisée dans votre liste de modèles comme un chiffre compris entre 0 et 9.

   ![Tous les chiffres de 0 à 9](../media/content-understanding/digit-identity.png)

De même, si vous créez une liste de modèles qui contient des caractères texte, sélectionnez la case à cocher **Une lettre de a à z** pour que chaque caractère « a » utilisé dans la liste de modèles soit n’importe quel caractère de « a » à « z ».

Par exemple, si vous créez une liste de modèles **Date** et que vous souhaitez vous assurer qu’un format de date tel que *Jan 1, 2020* est reconnu, vous devez :
- ajouter *aaa 0, 0000* et *aaa 00, 0000* à votre liste de modèles.
- vous assurer que **Toutes les lettres de a à z** est également sélectionnée.

   ![Toutes les lettres de a à z](../media/content-understanding/any-letter.png)

De plus, si vous avez des exigences de mise en majuscule dans votre liste de modèles, vous avez la possibilité de cocher la case **Seulement la mise en majuscule exacte**. Pour l’exemple Date, si vous souhaitez que la première lettre du mois soit en majuscule, vous devez :

- ajouter *Aaa 0, 0000* et *Aaa 00, 0000* à votre liste de modèles.
- vous assurer que **Seulement la mise en majuscule exacte** est également sélectionnée.

   ![Seulement la mise en majuscule exacte](../media/content-understanding/exact-caps.png)

> [!NOTE]
> Au lieu de créer manuellement une explication de liste de modèles, utilisez la [bibliothèque d’explications](https://docs.microsoft.com/microsoft-365/contentunderstanding/explanation-types-overview#use-explanation-templates) pour utiliser des modèles de liste de modèles pour une liste de modèles commune, comme les *dates* , *numéros de téléphone* , *numéro de carte bancaire* , etc.

## <a name="proximity"></a>Proximité 

Le type d’explication de proximité aide votre modèle à identifier les données en définissant la proximité d’un autre élément de données. Par exemple, dans votre modèle, vous avez défini deux explications qui étiquettent à la fois le *Numéro d’adresse* et le *Numéro de téléphone* du client. 

Remarquez également que les numéros de téléphone des clients apparaissent toujours avant le numéro de l’adresse postale. 

Alain Chauvin<br>
555-555-5555<br>
One Microsoft Way<br>
Redmond, WA 98034<br>

Utilisez l’explication de proximité pour définir la distance de l’explication du numéro de téléphone afin de mieux identifier le numéro de l’adresse postale dans vos documents.

   ![Explication de proximité](../media/content-understanding/proximity.png)</br>

#### <a name="what-are-tokens"></a>Que sont les jetons ?

Pour utiliser le type d’explication de proximité, vous devez comprendre ce qu’est un jeton, car l’explication de proximité mesure la distance entre deux explications grâce au nombre de jetons. Un jeton est une étendue continue (non compris les espaces et la ponctuation) de lettres et de chiffres. 

Le tableau suivant illustre des exemples sur la façon de déterminer le nombre de jetons dans une expression.

|Expression|Nombre de jetons|Explication|
|--|--|--|
|`Dog`|1|Un seul mot sans ponctuation ni espaces.|
|`RMT33W`|1|Un numéro de localisateur d’enregistrement. Il peut inclure des chiffres et des lettres, mais pas de ponctuation.|
|`425-555-5555`|5|Un numéro de téléphone. Chaque signe de ponctuation équivaut à un seul jeton, donc `425-555-5555` correspond à 5 jetons :<br>`425`<br>`-`<br>`555`<br>`-`<br>`5555` |
|`https://luis.ai`|7|`https`<br>`:`<br>`/`<br>`/`<br>`luis`<br>`.`<br>`ai`<br>|

#### <a name="configure-the-proximity-explanation-type"></a>Configurer le type d’explication de proximité

Pour l’exemple, configurez le paramètre de proximité pour définir la plage du nombre de jetons. L’explication dans le *Numéro de téléphone* provient de l’explication du *Numéro d’adresse*. Remarquez que la plage minimale est « 0 » car il n’y a pas de jetons entre le numéro de téléphone et le numéro d’adresse postale.

Certains numéros de téléphone dans les exemples de documents sont toutefois ajoutés avec un *(mobile)*.

Maurice Boule<br>
111-111-1111 (mobile)<br>
One Microsoft Way<br>
Redmond, WA 98034<br>

Il y a trois jetons dans *(mobile)*  :

|Expression|Nombre de jetons|
|--|--|
|(|1|
|mobile|2|
|)|3|

Configurez le paramètre de proximité pour avoir une plage de 0 à 3.

   ![Exemple de proximité](../media/content-understanding/proximity-example.png)</br>

## <a name="use-explanation-templates"></a>Utiliser des modèles d’explication

Bien que vous puissiez ajouter manuellement différentes valeurs de liste de modèles pour votre explication, il peut être plus facile d’utiliser les modèles qui vous sont fournis dans la bibliothèque d’explications.

Par exemple, au lieu d’ajouter manuellement toutes les variantes de *Date* , vous pouvez utiliser le modèle de liste de modèles pour *Date* , qui comprend déjà un certain nombre de valeurs de listes de modèles :</br>

   ![Bibliothèque d’explications](../media/content-understanding/explanation-template.png)</br>
 
La bibliothèque d’explications comprend des explications de liste de modèles couramment utilisées, notamment :</br>

- Date</br>
- Données (numériques)</br>
- Temps</br>
- Nombre</br>
- Numéro de téléphone</br>
- Code postal</br>
- Premier mot de la phrase</br>
- Carte bancaire</br>
- Numéro de sécurité sociale</br>

Notez que la bibliothèque d’explications comprend également des modèles pour les explications de liste d’expressions :
- Fin de la phrase
- Devise

#### <a name="to-use-a-template-from-the-explanation-library"></a>Pour utiliser un modèle de la bibliothèque d’explications

1. Dans la section **Explications** de la page **Entraîner** de votre modèle, sélectionnez **Nouveau** , puis **À partir d’un modèle**.</br>

   ![Créer à partir d’un modèle](../media/content-understanding/from-template.png)</br>

2.  Sur la page **Modèles d’explication** , sélectionnez l’explication que vous souhaitez utiliser, puis **Ajouter**.</br>

       ![Sélectionner un modèle](../media/content-understanding/phone-template.png)</br>

3. Les informations relatives au modèle que vous avez sélectionné s’affichent sur la page **Créer une explication**. Si nécessaire, modifiez le nom de l’explication et ajoutez ou supprimez des éléments de la liste des modèles. </br> 

   ![Modifier le modèle](../media/content-understanding/phone-template-live.png)</br>

4. Lorsque vous avez terminé, cliquez sur **Enregistrer**.
