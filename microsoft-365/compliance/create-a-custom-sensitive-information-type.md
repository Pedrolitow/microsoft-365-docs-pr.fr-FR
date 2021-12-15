---
title: Commencer à travailler avec des types d’informations sensibles personnalisées
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Découvrez comment créer, modifier, supprimer et tester des types d’informations sensibles personnalisés pour DLP dans le Centre de sécurité & conformité.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: a091608f7741b279b06a6289fb97b521976fc9ea
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2021
ms.locfileid: "61531884"
---
# <a name="get-started-with-custom-sensitive-information-types"></a>Commencer à travailler avec des types d’informations sensibles personnalisées

Si les types d’informations sensibles pré configurés ne répondent pas à vos besoins, vous pouvez créer vos propres types d’informations sensibles personnalisés que vous définissez entièrement, ou vous pouvez copier un des types pré configurés et le modifier.

Les types d’informations sensibles personnalisés que vous créez en utilisant cette méthode sont ajoutés au package de règles nommé `Microsoft.SCCManaged.CustomRulePack`.

Il existe deux façons de créer un type d’informations sensibles :

- [à partir de zéro pour la définition entière de tous les éléments](#create-a-custom-sensitive-information-type)
- [Copier et modifier un type d’informations sensibles existant](#copy-and-modify-a-sensitive-information-type)


## <a name="before-you-begin"></a>Avant de commencer

- Vous devez être familiarisé avec les types d’informations sensibles et leur composition. Consultez [En savoir plus sur les types d’informations sensibles](sensitive-information-type-learn-about.md). Il est essentiel de comprendre les rôles des :
    - [Expressions régulières](https://www.boost.org/doc/libs/1_68_0/libs/regex/doc/html/) - les types d’informations sensibles Microsoft 365 utilisent le moteur Boost.RegEx 5.1.3
    - listes de mots clés : vous pouvez créer vos propres listes de mots clés lorsque vous définissez votre type d’informations sensibles ou faites votre choix parmi des listes de mots clés existantes.
    - [Dictionnaire de mots clés](create-a-keyword-dictionary.md)
    - [Fonctions](what-the-dlp-functions-look-for.md)
    - [Niveaux de confiance](sensitive-information-type-learn-about.md#more-on-confidence-levels)
 
- Vous devez avoir une autorisation d’administrateur général ou d’administrateur de conformité pour créer, tester et déployer un type d’informations sensibles personnalisé via l’interface utilisateur. Consulter [À propos des rôles d’administration](/office365/admin/add-users/about-admin-roles) dans Office 365.

- Votre organisation doit disposer d’un abonnement, par exemple, Office 365 Entreprise, qui inclut la protection contre la perte de données (DLP). Voir [Description du service Stratégie et conformité de messagerie](/office365/servicedescriptions/exchange-online-protection-service-description/messaging-policy-and-compliance-servicedesc). 


> [!IMPORTANT]
> La division Support technique et Service clientèle Microsoft ne peut pas vous aider à créer des classifications personnalisées ou des modèles d’expressions régulières. Les ingénieurs du support technique peuvent offrir un support limité pour la fonctionnalité, comme vous fournir des exemples de modèles d’expressions régulières à des fins de test, ou vous aider à résoudre un problème avec un modèle d’expression régulière existant qui n’opère pas de déclenchement comme prévu. En revanche, ils ne peuvent pas garantir que le développement correspondant à du contenu personnalisé répondra à vos exigences ou obligations.

## <a name="create-a-custom-sensitive-information-type"></a>Créer un type d’informations sensibles personnalisé

Utilisez cette procédure pour créer un type d’informations sensibles que vous définissez entièrement. 

1. Dans le Centre de conformité, go to **Data classification** Sensitive \> **info types** and choose Create sensitive info **type**.

2. Remplissez les valeurs du **Nom** et de la **Description** puis sélectionnez **Suivant**.

3. Choisissez **Créer un motif**. Vous pouvez créer plusieurs motifs, chacun avec des éléments et des niveaux de confiance différents, lorsque vous définissez votre nouveau type d’informations sensibles.

4. Choisissez le niveau de confiance par défaut pour le motif. Les valeurs sont **Confiance faible,**, **Confiance moyenne,** et **Confiance élevé**.

5. Choisissez et définissez **L’élément principal**. L’élément principal peut être une **Expression régulière** avec un validateur facultatif, une **Liste de mots clés**, un **Dictionnaire de mots clés**, ou l’une des **Fonctions** pré-configurées. Pour obtenir plus d’informations sur les fonctions DLP, consultez l’article [Éléments recherchés par les fonctions DLP](what-the-dlp-functions-look-for.md). Pour plus d’informations sur la date et les validateurs de la checksum, voir Plus d’informations sur les [validateurs d’expression régulière.](#more-information-on-regular-expression-validators)

6. Remplissez une valeur pour la **Proximité de caractère**.

7. (Facultatif) Ajoutez des éléments de prise en charge si vous en avez. Les éléments de prise en charge peuvent être une expression régulière avec un validateur facultatif, une liste de mots clés, un dictionnaire de mots clés ou l’une des fonctions prédéfinies. Les éléments de prise en charge peuvent avoir leur propre configuration **de proximité des** caractères. 

8. (Facultatif) Ajouter des [**vérifications supplémentaires**](#more-information-on-additional-checks) à partir de la liste des vérifications disponibles.

9. Sélectionnez **Créer**.

10. Cliquez sur **Suivant**.

11. Choisissez le **Niveau de confiance recommandé** pour ce type d’informations sensibles.

12. Vérifiez votre paramètre, puis sélectionnez **Soumettre**.

    > [!IMPORTANT]
    > Microsoft 365 utilise le robot de recherche pour identifier et classer des informations sensibles sur les sites SharePoint Online et OneDrive Entreprise. Pour identifier votre nouveau type d’informations sensibles personnalisé dans du contenu existant, celui-ci doit être ré-analysé. Le contenu est analysé sur la base d’un planning, mais vous pouvez le réanalyser manuellement pour une collection de sites, une liste ou une bibliothèque. Pour plus d’informations, voir [Demander manuellement l’analyse et la réindexation d’un site, d’une bibliothèque ou d’une liste](/sharepoint/crawl-site-content).

13. Tous les types d’informations sensibles s’affichent sur la page **Classification des données**. Sélectionnez **Actualiser**, puis recherchez ou utilisez l’outil de recherche pour trouver le type d’informations sensibles que vous avez créé.

## <a name="test-a-sensitive-information-type"></a>Tester un type d’informations sensibles

Vous pouvez tester n’importe quel type d’informations sensibles dans la liste. Nous vous suggérons de tester chaque type d’informations sensibles que vous créez avant de l’utiliser dans une stratégie.

1. Préparez deux fichiers, comme un document Word. Un fichier avec un contenu qui correspond aux éléments que vous avez spécifiés dans votre type d’informations sensibles et un autre qui ne correspond pas.

2. Dans le Centre de conformité, accédez à **Classification de données** \> **Types d’informations sensibles**, puis sélectionnez le type d’informations sensibles dans la liste pour ouvrir le volet des détails, puis sélectionnez **Tester**.

3. Téléchargez un fichier, puis sélectionnez **Tester**.

4. Sur la page **Résultats de correspondances**, examinez les résultats et sélectionnez **Terminer**.

## <a name="custom-sensitive-information-types-limits"></a>Limites des types d’informations sensibles personnalisés

Pour garantir des performances élevées et une latence moindre, il existe des limitations dans les configurations SIT personnalisées.

|Limite|Valeur|
|--------|--------|
|nombre maximal de sits personnalisés créés via le Centre de conformité| 500 |
|longueur maximale de l’expression régulière| 1 024 caractères|
|Longueur maximale d’un terme donné dans une liste de mots clés| 50 caractères|
|nombre maximal de termes dans la liste de mots clés| 2048|
|nombre maximal d’regex distinctes par type d’informations sensibles| 20|
|taille maximale d’un dictionnaire de mots clés (post-compression)| 1 Mo (environ 1 000 000 caractères)|
|nombre maximal d’outils SIT basés sur un dictionnaire de mots clés dans un client|50 |

> [!NOTE] 
> Si votre entreprise a besoin de créer plus de 500 sits personnalisés, veuillez générer un ticket de support.

## <a name="modify-custom-sensitive-information-types-in-the-compliance-center"></a>Modifier des types d’informations sensibles personnalisés dans le centre de conformité

1. Dans le centre de conformité, accédez à **Classification de données** \> **Types d’informations sensibles**, puis sélectionnez le type d’informations sensibles dans la liste que vous voulez modifier, puis sélectionnez **Modifier**.

2. Vous pouvez ajouter d’autres motifs, avec des éléments principaux et de prise en charge uniques, des niveaux de confiance, la proximité des caractères et des [**vérifications supplémentaires**](#more-information-on-additional-checks), ou modifier/supprimer les éléments existants.

## <a name="remove-custom-sensitive-information-types-in-the-compliance-center"></a>Supprimer des types d’informations sensibles personnalisés dans le centre de Conformité 

> [!NOTE]
> Vous pouvez uniquement supprimer des types d’informations sensibles personnalisés ; vous ne pouvez pas supprimer des types d’informations sensibles intégrés.

> [!IMPORTANT]
> Avant de supprimer un type d’informations sensibles personnalisé, vérifiez qu’aucune stratégie DLP ou règle de flux de courrier Exchange (également appelées règles de transport) ne référence toujours le type d’informations sensibles.

1. Dans le centre de conformité, accédez à **Classification des données** \> **Types d’informations sensibles** puis choisissez le type d’informations sensibles dans la liste que vous voulez supprimer.

2. Dans le lanceur qui s’ouvre, sélectionnez **Supprimer**.

## <a name="copy-and-modify-a-sensitive-information-type"></a>Copier et modifier un type d’informations sensibles

Utilisez cette procédure pour créer un type d’informations sensibles basé sur un type d’informations sensibles existant. 

1. Dans le centre de conformité, accédez à **Classifications des données** \> **Types d’informations sensibles**, puis sélectionnez le type d’informations sensibles que vous voulez copier.

2. Dans le lanceur, sélectionnez **Copier**.

3. Sélectionnez **Actualiser** dans la liste des types d’informations sensibles, puis recherchez la copie que vous avez faite. La recherche partielle cherche le travail de sorte à limiter votre recherche à `copy`rendant tous les types d’informations sensibles ayant le mot `copy` dans le nom. 

4. Remplissez les valeurs du **Nom** et de la **Description** puis sélectionnez **Suivant**.

5. Sélectionnez la copie du type d’informations sensibles, puis sélectionnez **Modifier**. 

6. Donnez un **Nom** et une **Description** à votre nouveau type d’informations sensibles.

7. Vous pouvez choisir de modifier ou de supprimer les motifs existants et d’en ajouter de nouveaux. Choisissez le niveau de confiance par défaut pour le nouveau motif. Les valeurs sont **Confiance faible,**, **Confiance moyenne,** et **Confiance élevé**.

8. Choisissez et définissez **L’élément principal**. L’élément principal peut être une **Expression régulière**, une **Liste de mots clés**, un **Dictionnaire de mots clés**, ou l’une des **Fonctions** pré-configurées. Consultez, [Éléments recherchés par les fonctions DLP ](what-the-dlp-functions-look-for.md).

9. Remplissez une valeur pour la **Proximité de caractère**.

10. (Facultatif) Si vous avez des **Éléments de prise en charge** ou des [**Contrôles supplémentaires**](#more-information-on-additional-checks), ajoutez les. Si nécessaire, vous pouvez grouper vos **Éléments de prise en charge**.

11. Sélectionnez **Créer**.

12. Cliquez sur **Suivant**.

13. Choisissez le **Niveau de confiance recommandé** pour ce type d’informations sensibles.

14. Vérifiez votre paramètre, puis sélectionnez **Soumettre**.

> [!NOTE]
> Ces sits ne peuvent pas être copiés :
> - Numéro de permis de conduire canada
> - Numéro de permis de conduire de l’UE
> - Numéro d’identification national de l’UE
> - Numéro de passeport de l’UE
> - Numéro de sécurité sociale de l’UE ou identification équivalente
> - Numéro d’identification fiscale de l’UE
> - Classification internationale des maladie (ICD-10-CM)
> - Classification internationale des maladie (ICD-9-CM)
> - Numéro de permis de conduire américain

Vous pouvez également créer des types d’informations sensibles personnalisés à l’aide de PowerShell et de fonctionnalités de correspondance exacte des données. Pour en savoir plus sur ces méthodes, consultez :
- [Créer un type d’informations sensibles personnalisé dans l’interface PowerShell du Centre de sécurité et conformité](create-a-custom-sensitive-information-type-in-scc-powershell.md)
- [En savoir plus sur les types d’informations sensibles exacts basés sur la correspondance de données](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)

## <a name="more-information-on-regular-expression-validators"></a>Plus d’informations sur les validateurs d’expression régulière

### <a name="checksum-validator"></a>Validateur checksum

Si vous devez exécuter une base de contrôle sur un chiffre dans une expression régulière, vous pouvez utiliser le *validateur de la base de contrôle.* Par exemple, par exemple, vous devez créer une sit pour un numéro de licence à huit chiffres où le dernier chiffre est un chiffre de sommes de contrôle qui est validé à l’aide d’un calcul mod 9. Vous avez installé l’algorithme de sommes de contrôle comme ceci :

```console
Sum = digit 1 * Weight 1 + digit 2 * weight 2 + digit 3 * weight 3 + digit 4 * weight 4 + digit 5 * weight 5 + digit 6 * weight 6 + digit 7 * weight 7 + digit 8 * weight 8
Mod value = Sum % 9
If Mod value == digit 8
    Account number is valid
If Mod value != digit 8
    Account number is invalid
```

1. Définissez l’élément principal avec cette expression régulière :

   ```console
   \d{8}
   ```

2. Ajoutez ensuite le validateur de la checksum.

3. Ajoutez les valeurs de poids séparées par des virgules, la position du chiffre de contrôle et la valeur Mod. Pour plus d’informations sur l’opération Mod sous, consultez [l’opération Mod mode.](https://en.wikipedia.org/wiki/Modulo_operation)

   > [!NOTE]
   > Si le chiffre de contrôle ne fait pas partie du calcul de la sommes de contrôle, utilisez 0 comme poids pour le chiffre de contrôle. Par exemple, dans le cas ci-dessus, le poids 8 est égal à 0 si le chiffre de contrôle ne doit pas être utilisé pour calculer le chiffre de vérification.  Modulo_operation).

   :::image type="content" alt-text="Capture d’écran du validateur de la checkum configurée." source="../media/checksum-validator.png" lightbox="../media/checksum-validator.png":::

### <a name="date-validator"></a>Validateur de date

Si une valeur de date incorporée dans une expression régulière fait partie d’un nouveau modèle que vous créez, vous pouvez utiliser le *validateur* de date pour tester qu’elle répond à vos critères. Par exemple, dites que vous souhaitez créer un sit pour un numéro d’identification d’employé à neuf chiffres. Les six premiers chiffres sont la date d’embauche au format DDMMYY et les trois derniers sont des numéros générés de manière aléatoire. Pour vérifier que les six premiers chiffres sont au format correct.

1. Définissez l’élément principal avec cette expression régulière :

   ```console
   \d{9}
   ```

2. Ajoutez ensuite le validateur de date.

3. Sélectionnez le format de date et le décalage de début. Étant donné que la chaîne de date est les six premiers chiffres, le décalage est `0` .

   :::image type="content" alt-text="Capture d’écran du validateur de date configuré." source="../media/date-validator.png" lightbox="../media/date-validator.png":::

### <a name="functional-processors-as-validators"></a>Processeurs fonctionnels en tant que validateurs

Vous pouvez utiliser des processeurs de fonctions pour certains des sits les plus couramment utilisés comme validateurs. Cela vous permet de définir votre propre expression régulière tout en vous assurant qu’elle passe les vérifications supplémentaires requises par la sit. Par exemple, Func_India_Aadhar s’assure que l’expression régulière personnalisée définie par vous transmet la logique de validation requise pour la carte Aadhar indien. Pour plus d’informations sur les fonctions DLP qui peuvent être utilisées comme validateurs, voir ce que les fonctions [DLP recherchent.](what-the-dlp-functions-look-for.md#what-the-dlp-functions-look-for) 

### <a name="luhn-check-validator"></a>Validateur de vérification Luhn

Vous pouvez utiliser le validateur de vérification Luhn si vous avez un type d’informations sensibles personnalisé qui inclut une expression régulière qui doit transmettre l’algorithme [Luhn](https://en.wikipedia.org/wiki/Luhn_algorithm).

## <a name="more-information-on-additional-checks"></a>Informations supplémentaires sur les contrôles supplémentaires

Voici des définitions et des exemples pour les contrôles supplémentaires disponibles.

**Exclure des correspondances spécifiques** : ce contrôle vous permet de définir des mots clés à exclure lors de la détection de correspondances au modèle que vous modifiez. Par exemple, vous pouvez exclure les numéros de carte de crédit tels que « 4111111111111111 » afin qu'ils ne soient pas considérés comme des numéros valides.

**Commence ou ne commence pas par les caractères** : ce contrôle vous permet de définir les caractères par lesquels les éléments en correspondance doivent ou non commencer. Par exemple, si vous souhaitez que le modèle détecte uniquement les numéros de carte de crédit qui commencent par 41, 42 ou 43, sélectionnez **Commence par** et ajoutez 41, 42 et 43 à la liste, séparés par des virgules. 

**Se termine ou ne se termine pas par des caractères**: ce contrôle vous permet de définir les caractères par lesquels les éléments en correspondance doivent ou ne doivent pas se terminer. Par exemple, si votre numéro d’ID d’employé ne peut pas se terminer par 0 ou 1, sélectionnez **Ne se termine pas par** et ajoute 0 et 1 à la liste, séparés par des virgules.

**Exclure les caractères en double** : ce contrôle vous permet d’ignorer les correspondances dont tous les chiffres sont identiques. Par exemple, si les six chiffres du numéro d'identification de l'employé ne peuvent pas tous être identiques, vous pouvez sélectionner **Exclure les caractères en double** pour exclure 111111, 222222, 333333, 444444, 555555, 666666, 777777, 888888, 999999 et 000000 de la liste des correspondances valides pour le numéro d'identification de l'employé.

**Inclure ou exclure des préfixes** : ce contrôle vous permet de définir les mots-clés qui doivent ou non se trouver immédiatement avant l'entité correspondante. En fonction de votre sélection, les entités seront mises en correspondance ou non si elles sont précédées des préfixes que vous incluez ici. Par exemple, si vous **Excluez** le préfixe **GUID:**, toute entité précédée de **GUID:** ne sera pas considérée comme une correspondance.

**Inclure ou exclure des suffixes** : ce contrôle vous permet de définir les mots-clés qui doivent ou non se trouver immédiatement après l'entité correspondante. En fonction de votre sélection, les entités seront mises en correspondance ou non si elles sont suivies des suffixes que vous incluez ici. Par exemple, si vous **Excluez** le suffixe **:GUID** , tout texte suivi de **:GUID** ne sera pas pris en compte.


> [!NOTE]
> Microsoft 365 Information Protection prend désormais en charge, les langues de jeu de caractères à double octets pour :
> - Chinois (simplifié)
> - Chinois (traditionnel)
> - Korean
> - Japanese
>
>Cette prise en charge est disponible pour les types d’informations sensibles. Si vous souhaitez en savoir plus, consultez l’article [Prise en charge de la protection des informations pour les jeux de caractères à double octets (préversion)](mip-dbcs-relnotes.md).

> [!TIP]
> Pour détecter les modèles contenant des caractères chinois/japonais et des caractères d’octet unique ou pour détecter les modèles contenant du chinois/le japonais et l’anglais, définissez deux variantes du mot clé ou de regex. 
> - Par exemple, pour détecter un mot clé tel que « 机密的document », utilisez deux variantes du mot clé ; l’un avec un espace entre le texte japonais et anglais et l’autre sans espace entre le texte japonais et l’anglais. Par conséquent, les mots clés à ajouter dans le SIT doivent être « 机密的 document » et « 机密的document ». De la même façon, pour détecter une expression « 東京オリンピック2020 », deux variantes doivent être utilisées : « 東京オリンピック 2020 » et « 東京オリンピック2020 ».
>
> En plus des caractères chinois/japonais/caractères sur deux octets, si la liste des mots clés/expressions contient également des mots non chinois/japonais (comme l’anglais uniquement), il est recommandé de créer deux dictionnaires/listes de mots clés. Un pour les mots clés contenant des caractères chinois/japonais/sur deux octets et un autre pour l’anglais uniquement. 
> - Par exemple, si vous souhaitez créer un dictionnaire/liste de mots clés avec trois phrases « Hautement confidentiel », « 機密性が高い » et « document 机密的 », vous devez créer deux listes de mots clés. 
>     1. Extrêmement confidentiel
>     2. Document 機密性が高い, 机密的 et document 机密的
>
> Lorsque vous créez une regex en utilisant un trait d'union à double octet ou un point à double octet, assurez-vous d'échapper les deux caractères comme on le ferait pour un trait d'union ou un point dans une regex. Voici un exemple regex pour référence :
>    - (?<!\d)([４][０-９]{3}[\-?\－\t]*[０-９]{4}
>
> Nous vous recommandons d’utiliser une correspondance de chaîne au lieu d’une correspondance de mot dans une liste de mots clés.
