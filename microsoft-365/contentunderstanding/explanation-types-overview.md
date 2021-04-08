---
title: Types d’explication
ms.author: efrene
author: efrene
manager: pamgreen
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
localization_priority: Priority
description: En savoir plus sur les types d’explications dans Microsoft SharePoint Syntex
ms.openlocfilehash: a5404230a59d1740a2b855527229a7aca92195a8
ms.sourcegitcommit: dc1ac43a57fac6f57438859dd668f927d94fdf34
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/07/2021
ms.locfileid: "51604404"
---
# <a name="introduction-to-explanation-types"></a>Introduction aux types d’explications

Les explications sont utilisées pour vous permettre de définir les informations que vous souhaitez étiqueter et extraire dans vos modèles de compréhension de documents dans Microsoft SharePoint Syntex. Lors de la création d’une explication, vous devez sélectionner un type d’explication. Cet article vous permet de comprendre les différents types d’explications et comment ils sont utilisés. 

![Types d’explication](../media/content-understanding/explanation-types.png) 
   
Les types d’explications suivants sont disponibles :

- **Liste d’expressions** : liste de mots, expressions, nombres ou autres caractères que vous pouvez utiliser dans le document ou les informations que vous extrayez. Par exemple, la chaîne de texte **Médecin référent** se trouve dans tous les documents de référence médicale que vous identifiez. Ou le **Numéro de téléphone** du médecin référent de tous les documents de référence médicale que vous identifiez.

- **Proximité** : décrit à quel point les explications sont proches les unes des autres. Par exemple, une liste de phrases de *numéros de rue* se trouve juste avant la liste d’expressions des *noms de rue*, sans jetons entre les deux (vous en apprendrez davantage sur les jetons plus loin dans cet article). L’utilisation du type de proximité nécessite que vous ayez au moins deux explications dans votre modèle. Dans le cas contraire, l’option sera désactivée. 
 
## <a name="phrase-list"></a>Liste d’expressions

Un type d’explication de liste d’expressions est généralement utilisé pour identifier et classer un document dans votre modèle. Comme décrit dans l’exemple d’étiquette *Médecin référent*, il s’agit d’une chaîne de mots, d’expressions, de nombres ou de caractères qui se trouve systématiquement dans les documents que vous identifiez.

Bien que ce ne soit pas obligatoire, vous pouvez améliorer les performances de votre explication si l’expression que vous capturez se trouve à un emplacement cohérent dans votre document. Par exemple, l’étiquette *Médecin référent* peut être située systématiquement dans le premier paragraphe du document. Vous pouvez également utiliser le paramètre avancé **[Configurer l’emplacement de survenance des phrases dans le document](https://docs.microsoft.com/microsoft-365/contentunderstanding/explanation-types-overview#configure-where-phrases-occur-in-the-document)** pour sélectionner des zones spécifiques dans lesquelles la phrase se situe, surtout s’il existe une possibilité que la phrase se produise dans plusieurs emplacements au sein de votre document.

Si le respect de la casse est une exigence pour identifier votre étiquette, l’utilisation du type de liste d’expressions vous permet de le spécifier dans votre explication en cochant la case **Seulement la mise en majuscule exacte**.

![Respect de la casse](../media/content-understanding/case-sensitivity.png) 

Un type de phrase est particulièrement utile lorsque vous créez une explication qui identifie et extraie des informations dans divers formats, telles que des dates, numéros de téléphone et de cartes bancaires. Par exemple, une date peut être affichée dans plusieurs formats différents (1/1/2020, 1-1-2020, 01/01/20, 01/01/2020, 1 janvier 2020, etc.). La définition d’une liste de phrases rend votre explication plus efficace en capturant toutes les variations possibles dans les données que vous essayez d’identifier et d’extraire. 

Pour l’exemple du **Numéro de téléphone**, vous extrayez le numéro de téléphone de chaque médecin traitant dans tous les documents de référence médicale que le modèle identifie. Lorsque vous créez l’explication, tapez les différents formats pouvant correspondre à un affichage de numéro de téléphone dans votre document de sorte que vous puissiez capturer les variations possibles. 

![Modèles de phrase de numéro de téléphone](../media/content-understanding/pattern-list.png)

Pour cet exemple, dans les **Paramètres avancés**, sélectionnez la case à cocher **N’importe quel chiffre de 0 à 9** pour identifier chaque valeur « 0 » utilisée dans votre liste de phrases comme un chiffre compris entre 0 et 9.

![Tous les chiffres de 0 à 9](../media/content-understanding/digit-identity.png)

De même, si vous créez une liste de phrases qui contient des caractères texte, sélectionnez la case à cocher **Une lettre de a à z** pour que chaque caractère « a » utilisé dans la liste de phrases soit n’importe quel caractère de « a » à « z ».

Par exemple, si vous créez une liste de phrases **Date** et que vous souhaitez vous assurer qu’un format de date tel que *Jan 1, 2020* est reconnu, vous devez :
- ajouter *aaa 0, 0000* et *aaa 00, 0000* à votre liste de phrases.
- vous assurer que **Toutes les lettres de a à z** est également sélectionnée.

![Toutes les lettres de a à z](../media/content-understanding/any-letter.png)

De plus, si vous avez des exigences de mise en majuscule dans votre liste de phrases, vous avez la possibilité de cocher la case **Seulement la mise en majuscule exacte**. Pour l’exemple Date, si vous souhaitez que la première lettre du mois soit en majuscule, vous devez :

- ajouter *Aaa 0, 0000* et *Aaa 00, 0000* à votre liste de modèles.
- vous assurer que **Seulement la mise en majuscule exacte** est également sélectionnée.

![Seulement la mise en majuscule exacte](../media/content-understanding/exact-caps.png)

> [!NOTE]
> Au lieu de créer manuellement une explication de liste de phrases, utilisez la [bibliothèque d’explications](https://docs.microsoft.com/microsoft-365/contentunderstanding/explanation-types-overview#use-explanation-templates) pour utiliser des modèles de liste de phrases pour une liste de phrases commune, comme les *dates*, *numéros de téléphone*, *numéro de carte bancaire*, etc.

## <a name="proximity"></a>Proximité 

Le type d’explication de proximité aide votre modèle à identifier les données en définissant la proximité d’un autre élément de données. Par exemple, dans votre modèle, vous avez défini deux explications qui étiquettent à la fois le *Numéro d’adresse* et le *Numéro de téléphone* du client. 

Remarquez également que les numéros de téléphone des clients apparaissent toujours avant le numéro de l’adresse postale. 

Alain Chauvin<br>
555-555-5555<br>
One Microsoft Way<br>
Redmond, WA 98034<br>

Utilisez l’explication de proximité pour définir la distance de l’explication du numéro de téléphone afin de mieux identifier le numéro de l’adresse postale dans vos documents.

![Explication de proximité](../media/content-understanding/proximity.png)

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

![Exemple de proximité](../media/content-understanding/proximity-example.png)


## <a name="configure-where-phrases-occur-in-the-document"></a>Configurer l’endroit où des phrases apparaissent dans le document

Lorsque vous créez une explication, par défaut, l’ensemble du document est recherché à la recherche de l’expression que vous essayez d’extraire. Toutefois, vous pouvez utiliser le **Où ces expressions se produisent** paramètre avancé pour vous aider à isoler un emplacement spécifique dans le document où se produit une expression. Cela est utile dans les situations où des instances similaires d’une expression peuvent apparaître à un autre endroit dans le document et dont vous voulez vous assurer que celle qui est correcte est sélectionnée. En référence à notre exemple de document de référence médical, la **Référence médecin** est toujours mentionnée dans le premier paragraphe du document. Avec le paramètre **Où ces expressions se produisent, dans cet exemple, vous pouvez configurer votre explication pour rechercher cette étiquette uniquement dans la section de début du document ou dans tout autre emplacement où elle pourrait se produire.

![Paramètre où ces phrases se produisent](../media/content-understanding/phrase-location.png)

Vous pouvez choisir l'une des trois options suivantes :

- N’importe où dans le fichier : recherche l’expression dans l’ensemble du document.

- Début du fichier : La recherche s’effectuera du début jusqu’à l’emplacement des expressions.

   ![Début du fichier](../media/content-understanding/beginning-of-file.png)

    Dans la visionneuse, vous pouvez ajuster manuellement la case à sélectionner de manière à inclure l’emplacement où la phase a lieu. La valeur **Position de fin** est mise à jour de manière à afficher le nombre de jetons inclus dans la zone sélectionnée. Notez que vous pouvez également mettre à jour la valeur de position de fin pour ajuster la zone sélectionnée.

   ![Zone Début de la position du fichier](../media/content-understanding/beginning-box.png)

- Fin du fichier : La recherche s’effectuera de la fin jusqu’à l’emplacement des expressions.

   ![Fin du fichier](../media/content-understanding/end-of-file.png)

    Dans la visionneuse, vous pouvez ajuster manuellement la case à sélectionner de manière à inclure l’emplacement où la phase a lieu. La valeur **Position de début** est mise à jour de manière à afficher le nombre de jetons inclus dans la zone sélectionnée. Notez que vous pouvez également mettre à jour la valeur de position de début pour ajuster la zone sélectionnée.

   ![Zone Fin de fichier](../media/content-understanding/end-box.png)

- Plage personnalisée : recherche l’emplacement de l’expression dans une plage spécifiée du document.

   ![Plage personnalisée.](../media/content-understanding/custom-file.png)

    Dans la visionneuse, vous pouvez ajuster manuellement la case à sélectionner de manière à inclure l’emplacement où la phase a lieu. Pour ce paramètre, vous devez sélectionner une position de **Début** et une position de **Fin**. Ces valeurs représentent le nombre de jetons dès le début du document. Bien que vous pouvez entrer manuellement ces valeurs, il est plus facile d’ajuster manuellement la case à sélectionner dans la visionneuse. 
   
## <a name="use-explanation-templates"></a>Utiliser des modèles d’explication

Bien que vous puissiez ajouter manuellement différentes valeurs de liste d'expressions pour votre explication, il peut être plus facile d’utiliser les modèles qui vous sont fournis dans la bibliothèque d’explications.

Par exemple, au lieu d’ajouter manuellement toutes les variantes de *Date*, vous pouvez utiliser le modèle de liste d’expressions pour *Date*, qui comprend déjà un certain nombre de valeurs de listes d’expressions :

![Bibliothèque d’explications](../media/content-understanding/explanation-template.png)
 
La bibliothèque d’explications comprend des explications de liste d’expressions couramment utilisées, notamment :

- Date : Dates du calendrier, tous les formats. Inclut du texte et des chiffres (par exemple, « 9 décembre 2020 »).
- Date (numérique) : Dates du calendrier, tous les formats. Inclut les numéros (par exemple 1-11-2020).
- Heure : formats 12 et 24 heures.
- Nombre : Nombres positifs et négatifs jusqu'à 2 décimales. 
- Pourcentage : Une liste de motifs représentant un pourcentage. Par exemple, 1%, 11%, 100%, 11,11%, etc.
- Numéro de téléphone : Formats américains et internationaux courants. Par exemple, 000 000 0000, 000-000-0000, (000)000-0000, (000) 000-0000, etc.
- Code postal : Formats de code postal américain. Par exemple, 11111, 11111-1111.
- Premier mot de la phrase : Modèles courants pour les mots jusqu'à 9 caractères. 
- Fin de phrase : Ponctuation courante pour la fin d'une phrase
- Carte de crédit : Formats courants de numéros de cartes de crédit. Par exemple, 1111-1111-1111-1111. 
- Numéro de sécurité sociale : Format du numéro de sécurité sociale américain. Par exemple, 111-11-1111. 
- Case à cocher : Une liste de phrases représentant des variations d'une case à cocher remplie. Par exemple, _X_, _ _X_, etc.
- La monnaie : Principaux symboles internationaux. Par exemple, $. 
- E-mail CC : Une liste de phrases avec le terme « CC : », que l'on trouve souvent près des noms ou des adresses e-mail de personnes ou de groupes supplémentaires auxquels le message a été envoyé.
- Date de l' e-mail : Une liste de phrases avec le terme « Envoyé le :», qui se trouve souvent près de la date d'envoi de l' e-mail.
- Message d'accueil par e-mail : Lignes d'ouverture courantes pour les e-mails.
- Destinataire de l' e-mail : Une liste de phrases avec le terme « À :», que l'on trouve souvent près des noms ou des adresses e-mail des personnes ou des groupes auxquels le message a été envoyé. 
- Expéditeur de l' email : Une liste de phrases avec le terme « De : », que l'on trouve souvent près du nom ou de l'adresse électronique de l'expéditeur. 
- Objet de l' e-mail : Une liste de phrases avec le terme « Objet : », qui se trouve souvent près de l'objet de l' e-mail. 

La bibliothèque d’explications inclut également trois types de modèles automatiques qui fonctionnent avec les données que vous avez étiquetées dans vos exemples de fichiers :

- Après l’étiquette : mots ou caractères qui apparaissent après les étiquettes dans les exemples de fichiers.
- Après l’étiquette : mots ou caractères qui apparaissent avant les étiquettes dans les exemples de fichiers.
- Étiquettes : jusqu’aux 10 premières étiquettes des exemples de fichiers.

Pour vous donner un exemple du fonctionnement des modèles automatiques, dans l’exemple de fichier suivant, nous allons utiliser le modèle d’explication avant étiquette pour fournir au modèle plus d’informations pour obtenir une correspondance plus précise.

![Options de sélecteur de fichiers exemple](../media/content-understanding/before-label.png)

Lorsque vous sélectionnez le modèle d’explication Avant étiquette, il recherche le premier jeu de mots qui apparaît avant l’étiquette dans vos exemples de fichiers. Dans l’exemple, les mots identifiés dans le premier exemple de fichier sont « En tant que ».

![Modèle Avant d’étiquette](../media/content-understanding/before-label-explanation.png)

Vous pouvez sélectionner **Ajouter** pour créer une explication à partir du modèle.  À mesure que vous ajoutez d’autres exemples de fichiers, des mots supplémentaires sont identifiés et ajoutés à la liste des expressions.

![Ajouter l'étiquette](../media/content-understanding/before-label-add.png)
 
#### <a name="to-use-a-template-from-the-explanation-library"></a>Pour utiliser un modèle de la bibliothèque d’explications

1. Dans la section **Explications** de la page **Entraîner** de votre modèle, sélectionnez **Nouveau**, puis **À partir d’un modèle**.

   ![Ajouter Avant l’étiquette](../media/content-understanding/from-template.png)

2.  Sur la page **Modèles d’explication**, sélectionnez l’explication que vous souhaitez utiliser, puis **Ajouter**.

    ![Sélectionner un modèle](../media/content-understanding/phone-template.png)

3. Les informations relatives au modèle que vous avez sélectionné s’affichent sur la page **Créer une explication**. Si nécessaire, modifiez le nom de l’explication et ajoutez ou supprimez des éléments de la liste d’expressions.  

    ![Modifier le modèle](../media/content-understanding/phone-template-live.png)

4. Lorsque vous avez terminé, cliquez sur **Enregistrer**.