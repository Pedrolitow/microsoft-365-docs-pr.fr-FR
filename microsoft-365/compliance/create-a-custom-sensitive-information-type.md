---
title: Créer des types d’informations sensibles personnalisés
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
description: Découvrez comment créer, modifier, supprimer et tester des types d’informations sensibles personnalisés dans le Centre de conformité.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: ff6a66b092d433fcfde7723f252fea679c2a3050
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/11/2022
ms.locfileid: "64759828"
---
# <a name="create-custom-sensitive-information-types-in-the-compliance-center"></a>Créer des types d’informations sensibles personnalisés dans le Centre de conformité

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
  - [Fonctions de type d’informations sensibles](sit-functions.md)
  - [Niveaux de confiance](sensitive-information-type-learn-about.md#more-on-confidence-levels)

- Vous devez avoir une autorisation d’administrateur général ou d’administrateur de conformité pour créer, tester et déployer un type d’informations sensibles personnalisé via l’interface utilisateur. Consulter [À propos des rôles d’administration](/office365/admin/add-users/about-admin-roles) dans Office 365.

- Votre organisation doit disposer d’un abonnement, par exemple, Office 365 Entreprise, qui inclut la protection contre la perte de données (DLP). Voir [Description du service Stratégie et conformité de messagerie](/office365/servicedescriptions/exchange-online-protection-service-description/messaging-policy-and-compliance-servicedesc).

> [!IMPORTANT]
> La division Support technique et Service clientèle Microsoft ne peut pas vous aider à créer des classifications personnalisées ou des modèles d’expressions régulières. Les ingénieurs du support technique peuvent offrir un support limité pour la fonctionnalité, comme vous fournir des exemples de modèles d’expressions régulières à des fins de test, ou vous aider à résoudre un problème avec un modèle d’expression régulière existant qui n’opère pas de déclenchement comme prévu. En revanche, ils ne peuvent pas garantir que le développement correspondant à du contenu personnalisé répondra à vos exigences ou obligations.

## <a name="create-a-custom-sensitive-information-type"></a>Créer un type d’informations sensibles personnalisé

Utilisez cette procédure pour créer un type d’informations sensibles que vous définissez entièrement.

1. Dans le Centre de conformité, accédez aux **types d’informations sensibles** de **classification** \> des données et choisissez **Créer un type d’informations sensibles**.

2. Remplissez les valeurs du **Nom** et de la **Description** puis sélectionnez **Suivant**.

3. Choisissez **Créer un motif**. Vous pouvez créer plusieurs motifs, chacun avec des éléments et des niveaux de confiance différents, lorsque vous définissez votre nouveau type d’informations sensibles.

4. Choisissez le niveau de confiance par défaut pour le motif. Les valeurs sont **Confiance faible,**, **Confiance moyenne,** et **Confiance élevé**.

5. Choisissez et définissez **L’élément principal**. L’élément principal peut être une **Expression régulière** avec un validateur facultatif, une **Liste de mots clés**, un **Dictionnaire de mots clés**, ou l’une des **Fonctions** pré-configurées. Pour plus d’informations sur les fonctions DLP, consultez [Fonctions de type Informations sensibles](sit-functions.md). Pour plus d’informations sur la date et les validateurs de somme de contrôle, consultez les [validateurs d’expression régulière du type d’informations sensibles](sit-regex-validators-additional-checks.md#sensitive-information-type-regular-expression-validators).

6. Remplissez une valeur pour la **Proximité de caractère**.

7. (Facultatif) Ajoutez des éléments de prise en charge si vous en avez. Les éléments de prise en charge peuvent être une expression régulière avec un validateur facultatif, une liste de mots clés, un dictionnaire de mots clés ou l’une des fonctions prédéfinies. Les éléments de prise en charge peuvent avoir leur propre configuration **de proximité de caractères** .

8. (Facultatif) Ajouter des [**vérifications supplémentaires**](sit-regex-validators-additional-checks.md#sensitive-information-type-additional-checks) à partir de la liste des vérifications disponibles.

9. Sélectionnez **Créer**.

10. Cliquez sur **Suivant**.

11. Choisissez le **Niveau de confiance recommandé** pour ce type d’informations sensibles.

12. Vérifiez votre paramètre, puis sélectionnez **Soumettre**.

    > [!IMPORTANT]
    > Microsoft 365 utilise le robot de recherche pour identifier et classer des informations sensibles sur les sites SharePoint Online et OneDrive Entreprise. Pour identifier votre nouveau type d’informations sensibles personnalisé dans du contenu existant, celui-ci doit être ré-analysé. Le contenu est analysé sur la base d’un planning, mais vous pouvez le réanalyser manuellement pour une collection de sites, une liste ou une bibliothèque. Pour plus d’informations, voir [Demander manuellement l’analyse et la réindexation d’un site, d’une bibliothèque ou d’une liste](/sharepoint/crawl-site-content).

13. Tous les types d’informations sensibles s’affichent sur la page **Classification des données**. Sélectionnez **Actualiser**, puis recherchez ou utilisez l’outil de recherche pour trouver le type d’informations sensibles que vous avez créé.

### <a name="copy-and-modify-a-sensitive-information-type"></a>Copier et modifier un type d’informations sensibles

Utilisez cette procédure pour créer un type d’informations sensibles basé sur un type d’informations sensibles existant.

> [!NOTE]
> Ces SIT ne peuvent pas être copiés :
>
> - Numéro de permis de conduire au Canada
> - Numéro de permis de conduire de l’UE
> - Numéro d’identification nationale de l’UE
> - Numéro de passeport de l’UE
> - Numéro de sécurité sociale de l’UE ou identification équivalente
> - Numéro d’identification fiscale de l’UE
> - Classification internationale des maladies (ICD-10-CM)
> - Classification internationale des maladies (ICD-9-CM)
> - Numéro de permis de conduire américain

Vous pouvez également créer des types d’informations sensibles personnalisés à l’aide de PowerShell et de fonctionnalités de correspondance exacte des données. Pour en savoir plus sur ces méthodes, consultez :

- [Créer un type d’informations sensibles personnalisé dans l’interface PowerShell du Centre de sécurité et conformité](create-a-custom-sensitive-information-type-in-scc-powershell.md)
- [En savoir plus sur les types d’informations sensibles exacts basés sur la correspondance de données](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)

1. Dans le centre de conformité, accédez à **Classifications des données** \> **Types d’informations sensibles**, puis sélectionnez le type d’informations sensibles que vous voulez copier.

2. Dans le lanceur, sélectionnez **Copier**.

3. Sélectionnez **Actualiser** dans la liste des types d’informations sensibles, puis recherchez la copie que vous avez faite. La recherche partielle cherche le travail de sorte à limiter votre recherche à `copy`rendant tous les types d’informations sensibles ayant le mot `copy` dans le nom.

4. Remplissez les valeurs du **Nom** et de la **Description** puis sélectionnez **Suivant**.

5. Sélectionnez la copie du type d’informations sensibles, puis sélectionnez **Modifier**.

6. Donnez un **Nom** et une **Description** à votre nouveau type d’informations sensibles.

7. Vous pouvez choisir de modifier ou de supprimer les motifs existants et d’en ajouter de nouveaux. Choisissez le niveau de confiance par défaut pour le nouveau motif. Les valeurs sont **Confiance faible,**, **Confiance moyenne,** et **Confiance élevé**.

8. Choisissez et définissez **L’élément principal**. L’élément principal peut être une **Expression régulière**, une **Liste de mots clés**, un **Dictionnaire de mots clés**, ou l’une des **Fonctions** pré-configurées. Voir, [Fonctions de type Informations sensibles](sit-functions.md).

9. Remplissez une valeur pour la **Proximité de caractère**.

10. (Facultatif) Si vous avez **des éléments de prise en charge** ou des [**vérifications supplémentaires**](sit-regex-validators-additional-checks.md#sensitive-information-type-additional-checks) , ajoutez-les. Si nécessaire, vous pouvez grouper vos **Éléments de prise en charge**.

11. Sélectionnez **Créer**.

12. Cliquez sur **Suivant**.

13. Choisissez le **Niveau de confiance recommandé** pour ce type d’informations sensibles.

14. Vérifiez votre paramètre, puis sélectionnez **Soumettre**.

## <a name="test-a-sensitive-information-type"></a>Tester un type d’informations sensibles

Vous pouvez tester n’importe quel type d’informations sensibles dans la liste. Nous vous suggérons de tester chaque type d’informations sensibles que vous créez avant de l’utiliser dans une stratégie.

1. Préparez deux fichiers, comme un document Word. Un fichier avec un contenu qui correspond aux éléments que vous avez spécifiés dans votre type d’informations sensibles et un autre qui ne correspond pas.

2. Dans le Centre de conformité, accédez à **Classification de données** \> **Types d’informations sensibles**, puis sélectionnez le type d’informations sensibles dans la liste pour ouvrir le volet des détails, puis sélectionnez **Tester**.

3. Téléchargez un fichier, puis sélectionnez **Tester**.

4. Sur la page **Résultats de correspondances**, examinez les résultats et sélectionnez **Terminer**.

## <a name="custom-sensitive-information-types-limits"></a>Limites des types d’informations sensibles personnalisées

Pour garantir des performances élevées et une latence inférieure, il existe des limitations dans les configurations SIT personnalisées.

|Limite|Valeur|
|---|---|
|nombre maximal de SIT personnalisés créés via le Centre de conformité| 500 |
|longueur maximale de l’expression régulière| 1 024 caractères|
|longueur maximale d’un terme donné dans une liste de mots clés| 50 caractères|
|nombre maximal de termes dans la liste des mots clés| 2048|
|nombre maximal d’expressions régulières distinctes par type d’informations sensibles| 20|
|taille maximale d’un dictionnaire de mots clés (après compression)| 1 Mo (~1 000 000 caractères)|
|nombre maximal de SIT basés sur un dictionnaire de mots clés dans un locataire|50 |

> [!NOTE]
> Si vous avez besoin de créer plus de 500 SIT personnalisés, veuillez créer un ticket de support.

### <a name="instance-count-supported-values-for-sit"></a>Nombre d’instances prises en charge pour SIT

La limite de nombre d’instances SIT s’applique lorsque des SIT sont utilisés dans ces solutions :

- Stratégies de protection contre la perte de données
- Protection des informations
- Gouvernance des informations
- Conformité des communications
- Gestion des enregistrements
- Microsoft Defender for Cloud Apps
- Microsoft Priva

Pour qu’un élément analysé réponde aux critères de règle, le nombre d’instances uniques d’un SIT dans un élément unique doit être compris entre les valeurs min et max. Il s’agit du **nombre d’instances**.

- **Champ min** : limite inférieure (nombre minimal) d’instances uniques d’un SIT qui doivent être trouvées dans un élément pour déclencher une correspondance. Le champ min prend en charge les valeurs suivantes :
  - 1 à 500
- **Champ maximal** : limite supérieure du nombre d’instances uniques d’un SIT qui se trouvent dans un élément et déclenchent toujours une correspondance. Le champ max prend en charge les valeurs suivantes :
  - 1 à 500 - Utilisez cette option lorsque vous souhaitez définir une limite supérieure spécifique de 500 ou moins sur le nombre d’instances d’un SIT dans un élément.
  - Any - Utiliser `Any` lorsque vous souhaitez que les critères de nombre d’instances uniques soient satisfaits lorsqu’un nombre non défini d’instances uniques d’un SIT est trouvé dans un élément analysé et que le nombre d’instances uniques atteint ou dépasse le nombre minimal de valeurs d’instances uniques. En d’autres termes, les critères de nombre d’instances uniques sont remplis tant que la valeur minimale est remplie.

Par exemple, si vous souhaitez que la règle déclenche une correspondance quand au moins 500 instances uniques d’un SIT sont trouvées dans un seul élément, définissez la valeur `500` **minimale** sur et la valeur **maximale** sur `Any`.

> [!NOTE]
> Microsoft 365 Information Protection prend désormais en charge, les langues de jeu de caractères à double octets pour :
>
> - Chinois (simplifié)
> - Chinois (traditionnel)
> - Korean
> - Japanese
>
> Cette prise en charge est disponible pour les types d’informations sensibles. Si vous souhaitez en savoir plus, consultez l’article [Prise en charge de la protection des informations pour les jeux de caractères à double octets (préversion)](mip-dbcs-relnotes.md).

> [!TIP]
> Pour détecter les modèles contenant des caractères chinois/japonais et des caractères d’octet unique ou pour détecter les modèles contenant du chinois/le japonais et l’anglais, définissez deux variantes du mot clé ou de regex.
>
> - Par exemple, pour détecter un mot clé tel que « 机密的document », utilisez deux variantes du mot clé ; l’un avec un espace entre le texte japonais et anglais et l’autre sans espace entre le texte japonais et l’anglais. Par conséquent, les mots clés à ajouter dans le SIT doivent être « 机密的 document » et « 机密的document ». De la même façon, pour détecter une expression « 東京オリンピック2020 », deux variantes doivent être utilisées : « 東京オリンピック 2020 » et « 東京オリンピック2020 ».
>
> En plus des caractères chinois/japonais/caractères sur deux octets, si la liste des mots clés/expressions contient également des mots non chinois/japonais (comme l’anglais uniquement), il est recommandé de créer deux dictionnaires/listes de mots clés. Un pour les mots clés contenant des caractères chinois/japonais/sur deux octets et un autre pour l’anglais uniquement.
>
> - Par exemple, si vous souhaitez créer un dictionnaire/liste de mots clés avec trois phrases « Hautement confidentiel », « 機密性が高い » et « document 机密的 », vous devez créer deux listes de mots clés.
>   1. Extrêmement confidentiel
>   2. Document 機密性が高い, 机密的 et document 机密的
>
> Lorsque vous créez une regex en utilisant un trait d'union à double octet ou un point à double octet, assurez-vous d'échapper les deux caractères comme on le ferait pour un trait d'union ou un point dans une regex. Voici un exemple regex pour référence :
>
> `(?<!\d)([4][0-9]{3}[\-?\-\t]*[0-9]{4})`
>
> Les caractères spéciaux sur deux octets ne doivent pas être utilisés dans le mot clé.
>
> Nous vous recommandons d’utiliser une correspondance de chaîne au lieu d’une correspondance de mot dans une liste de mots clés.
