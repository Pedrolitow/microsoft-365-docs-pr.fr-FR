---
title: Validateurs REGEX de type informations sensibles et vérifications supplémentaires
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Découvrez comment utiliser des validateurs REGEX et des vérifications supplémentaires dans vos types d’informations sentisitve.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 615d4757be16b3171005105aea8148536e6f3015
ms.sourcegitcommit: 437461fa1d38ff9bb95dd8a1c5f0b94e8111ada2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67679260"
---
# <a name="sensitive-information-type-regex-validators-and-additional-check"></a>Validateurs REGEX de type d’informations sensibles et vérification supplémentaire

> [!IMPORTANT]
> La division Support technique et Service clientèle Microsoft ne peut pas vous aider à créer des classifications personnalisées ou des modèles d’expressions régulières. Les ingénieurs du support technique peuvent offrir un support limité pour la fonctionnalité, comme vous fournir des exemples de modèles d’expressions régulières à des fins de test, ou vous aider à résoudre un problème avec un modèle d’expression régulière existant qui n’opère pas de déclenchement comme prévu. En revanche, ils ne peuvent pas garantir que le développement correspondant à du contenu personnalisé répondra à vos exigences ou obligations.

## <a name="sensitive-information-type-regular-expression-validators"></a>Validateurs d’expression régulière de type d’informations sensibles

### <a name="checksum-validator"></a>Validateur de somme de contrôle

Si vous devez exécuter une somme de contrôle sur un chiffre dans une expression régulière, vous pouvez utiliser le *validateur de somme de contrôle*. Par exemple, supposons que vous devez créer un SIT pour un numéro de licence à huit chiffres où le dernier chiffre est un chiffre de somme de contrôle validé à l’aide d’un calcul mod 9. Vous avez configuré l’algorithme de somme de contrôle comme suit :

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

2. Ajoutez ensuite le validateur de somme de contrôle.

3. Ajoutez les valeurs de poids séparées par des virgules, la position du chiffre de vérification et la valeur Mod. Pour plus d’informations sur l’opération Modulo, consultez [l’opération Modulo](https://en.wikipedia.org/wiki/Modulo_operation).

   > [!NOTE]
   > Si le chiffre de vérification ne fait pas partie du calcul de somme de contrôle, utilisez 0 comme pondération pour le chiffre à cocher. Par exemple, dans le cas ci-dessus, la pondération 8 est égale à 0 si le chiffre à cocher ne doit pas être utilisé pour calculer le chiffre à cocher.

   :::image type="content" alt-text="capture d’écran du validateur de somme de contrôle configuré." source="../media/checksum-validator.png" lightbox="../media/checksum-validator.png":::

### <a name="date-validator"></a>Validateur de date

Si une valeur de date incorporée dans l’expression régulière fait partie d’un nouveau modèle que vous créez, vous pouvez utiliser le *validateur de date* pour tester qu’il répond à vos critères. Par exemple, supposons que vous souhaitez créer un SIT pour un numéro d’identification d’employé à neuf chiffres. Les six premiers chiffres correspondent à la date d’embauche au format DDMMYY et les trois derniers sont des nombres générés de manière aléatoire. Pour vérifier que les six premiers chiffres sont au format correct.

1. Définissez l’élément principal avec cette expression régulière :

   ```console
   \d{9}
   ```

2. Ajoutez ensuite le validateur de date.

3. Sélectionnez le format de date et le décalage de début. Étant donné que la chaîne de date est les six premiers chiffres, le décalage est `0`.

   :::image type="content" alt-text="capture d’écran du validateur de date configuré." source="../media/date-validator.png" lightbox="../media/date-validator.png":::

### <a name="functional-processors-as-validators"></a>Processeurs fonctionnels en tant que validateurs

Vous pouvez utiliser des processeurs de fonction pour certains des SIT les plus couramment utilisés comme validateurs. Cela vous permet de définir votre propre expression régulière tout en vous assurant qu’elles réussissent les vérifications supplémentaires requises par le SIT. Par exemple, Func_India_Aadhar s’assure que l’expression régulière personnalisée définie par vous transmet la logique de validation requise pour la carte Aadhar indienne. Pour plus d’informations sur les fonctions DLP qui peuvent être utilisées comme validateurs, consultez [fonctions de type Informations sensibles](sit-functions.md). 

### <a name="luhn-check-validator"></a>Validateur de vérification Luhn

Vous pouvez utiliser le validateur de vérification Luhn si vous avez un type d’informations sensibles personnalisé qui inclut une expression régulière qui doit passer [l’algorithme Luhn](https://en.wikipedia.org/wiki/Luhn_algorithm).

## <a name="sensitive-information-type-additional-checks"></a>Vérifications supplémentaires du type d’informations sensibles

Voici des définitions et des exemples pour les contrôles supplémentaires disponibles.

**Exclure des correspondances spécifiques** : ce contrôle vous permet de définir des mots clés à exclure lors de la détection de correspondances au modèle que vous modifiez. Par exemple, vous pouvez exclure les numéros de carte de crédit tels que « 4111111111111111 » afin qu'ils ne soient pas considérés comme des numéros valides.

**Commence ou ne commence pas par les caractères** : ce contrôle vous permet de définir les caractères par lesquels les éléments en correspondance doivent ou non commencer. Par exemple, si vous souhaitez que le modèle détecte uniquement les numéros de carte de crédit qui commencent par 41, 42 ou 43, sélectionnez **Commence par** et ajoutez 41, 42 et 43 à la liste, séparés par des virgules. 

**Se termine ou ne se termine pas par des caractères**: ce contrôle vous permet de définir les caractères par lesquels les éléments en correspondance doivent ou ne doivent pas se terminer. Par exemple, si votre numéro d’ID d’employé ne peut pas se terminer par 0 ou 1, sélectionnez **Ne se termine pas par** et ajoute 0 et 1 à la liste, séparés par des virgules.

**Exclure les caractères en double** : ce contrôle vous permet d’ignorer les correspondances dont tous les chiffres sont identiques. Par exemple, si les six chiffres du numéro d'identification de l'employé ne peuvent pas tous être identiques, vous pouvez sélectionner **Exclure les caractères en double** pour exclure 111111, 222222, 333333, 444444, 555555, 666666, 777777, 888888, 999999 et 000000 de la liste des correspondances valides pour le numéro d'identification de l'employé.

**Inclure ou exclure des préfixes** : ce contrôle vous permet de définir les mots-clés qui doivent ou non se trouver immédiatement avant l'entité correspondante. En fonction de votre sélection, les entités seront mises en correspondance ou non si elles sont précédées des préfixes que vous incluez ici. Par exemple, si vous **Excluez** le préfixe **GUID:**, toute entité précédée de **GUID:** ne sera pas considérée comme une correspondance.

**Inclure ou exclure des suffixes** : ce contrôle vous permet de définir les mots-clés qui doivent ou non se trouver immédiatement après l'entité correspondante. En fonction de votre sélection, les entités seront mises en correspondance ou non si elles sont suivies des suffixes que vous incluez ici. Par exemple, si vous **Excluez** le suffixe **:GUID** , tout texte suivi de **:GUID** ne sera pas pris en compte.
