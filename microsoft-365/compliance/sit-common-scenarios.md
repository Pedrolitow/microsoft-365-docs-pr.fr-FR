---
title: Scénarios d’usage courants pour les types d’informations sensibles
f1.keywords:
- NOCSH
ms.author: chrfox
author: robmazz
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
description: Comment implémenter des scénarios de cas d’usage courants de types d’informations sensibles
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 8afef4cdb027c8e2ccbb029a70df885dc685cb2d
ms.sourcegitcommit: 433f5b448a0149fcf462996bc5c9b45d17bd46c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2022
ms.locfileid: "67819202"
---
# <a name="common-usage-scenarios-for-sensitive-information-types"></a>Scénarios d’usage courants pour les types d’informations sensibles

Cet article explique comment implémenter des scénarios de cas d’utilisation courants de type d’informations sensibles (SIT). Vous pouvez utiliser ces procédures comme exemples et les adapter à vos besoins spécifiques.

## <a name="protect-credit-card-numbers"></a>Protéger les numéros de carte de crédit

Contoso Bank doit classer les numéros de carte de crédit qu’ils émettent comme sensibles. Leurs cartes de crédit commencent par un ensemble de modèles à six chiffres. Ils souhaitent personnaliser la définition de carte de crédit pour détecter uniquement les numéros de carte de crédit à partir de leurs modèles à six chiffres.

**Solution suggérée**

1. Créez une copie de la carte de crédit SIT. Suivez les étapes pour [copier et modifier un type d’informations sensibles](create-a-custom-sensitive-information-type.md#copy-and-modify-a-sensitive-information-type) afin de copier la carte de crédit SIT.
1. Modifiez le modèle de confiance élevée. Suivez les étapes de [modification ou de suppression du modèle de type d’informations sensibles](sit-get-started-exact-data-match-create-rule-package.md#edit-or-delete-the-sensitive-information-type-pattern).
1. Ajoutez la case à cocher « commence par » et ajoutez la liste des chiffres bin (mis en forme & non mis en forme). Par exemple, pour vous assurer que seules les cartes de crédit commençant par 411111 & 433512 doivent être considérées comme valides, ajoutez ce qui suit à la liste 4111 11, 4111-11, 411111, 4335 12, 4335-12, 433512.
1. Répétez l’étape 2 & 3 pour le modèle de faible confiance.

## <a name="test-numbers-similar-to-social-security-numbers"></a>Numéros de test similaires aux numéros de sécurité sociale

Contoso a identifié quelques numéros de test à neuf chiffres qui déclenchent des correspondances de faux positifs dans la stratégie de protection contre la perte de données (DLP) Microsoft Purview (Social Security Number). Ils souhaitent exclure ces nombres de la liste des correspondances valides pour SSN.

**Solution suggérée**

1. Créez une copie du sit SSN. Suivez les étapes pour [copier et modifier un type d’informations sensibles](create-a-custom-sensitive-information-type.md#copy-and-modify-a-sensitive-information-type) pour copier le sit SSN.
1. Modifiez le modèle de confiance élevée. Suivez les étapes de [modification ou de suppression du modèle de type d’informations sensibles](sit-get-started-exact-data-match-create-rule-package.md#edit-or-delete-the-sensitive-information-type-pattern).
1. Ajoutez les nombres à exclure dans la vérification supplémentaire « Exclure des valeurs spécifiques ». Par exemple, pour exclure le & 23923532 239-23-532, il suffit d’ajouter 23923532
1. Répétez l’étape 2 & 3 pour d’autres modèles de confiance.

## <a name="phone-numbers-in-signature-trigger-match"></a>Correspondance des numéros de téléphone dans le déclencheur de signature

Contoso, basé en Australie, constate que les numéros de téléphone dans les signatures électroniques déclenchent une correspondance pour leur stratégie DLP de numéro d’entreprise en Australie.

**Solution suggérée**

Ajoutez un groupe « not » dans les éléments de prise en charge à l’aide d’une liste de mots clés contenant des mots clés couramment utilisés dans la signature de l’e-mail comme « Phone », « Mobile », « email », « Thanks and regards », etc. Conservez la proximité de cette liste de mots clés avec une valeur inférieure comme 50 caractères pour une meilleure précision. Pour plus d’informations, consultez [Prise en main des types d’informations sensibles personnalisés](create-a-custom-sensitive-information-type.md).

## <a name="unable-to-trigger-aba-routing-policy"></a>Impossible de déclencher la stratégie de routage ABA

La stratégie DLP ne peut pas déclencher la stratégie de numéro de routage ABA dans les fichiers Excel volumineux, car le mot clé requis est introuvable dans les 300 caractères.

**Solution suggérée**

Créez une copie du SIT intégré et modifiez-le pour que la proximité de la liste de mots clés passe de « 300 caractères » à « N’importe où dans le document ».

> [!TIP]
> Vous pouvez modifier la liste de mots clés pour inclure/exclure des mots clés pertinents pour votre organisation.

## <a name="unable-to-detect-credit-card-numbers-with-unusual-delimiters"></a>Impossible de détecter les numéros de carte de crédit avec des délimiteurs inhabituels

Contoso Bank a remarqué que certains de ses employés partagent des numéros de carte de crédit avec « / » comme délimiteur, par exemple 4111/1111/1111/11111, ce qui n’est pas détecté par la définition de carte de crédit hors limite. Contoso souhaite définir son propre expression régulière et la valider à l’aide de LuhnCheck.

**Solution suggérée**

1. Créez une copie de la carte de crédit SIT en suivant les étapes décrites dans [Personnaliser un type d’informations sensibles intégré](customize-a-built-in-sensitive-information-type.md).
1. Ajouter un nouveau modèle
1. Dans l’élément principal, sélectionnez l’expression régulière
1. Définissez l’expression régulière qui inclut « / » dans l’expression régulière, puis choisissez le validateur, puis sélectionnez luhncheck ou func_credit_card pour vous assurer que l’expression régulière passe également le LuhnCheck.

## <a name="ignore-a-disclaimer-notice"></a>Ignorer un avis d’exclusion de responsabilité

De nombreuses organisations ajoutent des exclusions de responsabilité légales, des déclarations de divulgation, des signatures ou d’autres informations en haut ou en bas des messages électroniques qui entrent ou quittent leur organisation et dans certains cas même au sein de l’organisation. Les employés eux-mêmes mettent des signatures, notamment des citations de motivation, des messages sociaux, et ainsi de suite. Une clause d’exclusion de responsabilité ou une signature peut contenir les termes qui sont présents dans le lexique d’un CC et peuvent générer un grand nombre de faux positifs.  

Par exemple, une clause d’exclusion de responsabilité classique peut contenir des mots comme sensibles ou confidentiels, et une stratégie recherchant des informations sensibles la détecte comme un incident, ce qui entraîne de nombreux faux positifs. Ainsi, offrir aux clients la possibilité d’ignorer la clause d’exclusion de responsabilité peut réduire les faux positifs et augmenter l’efficacité de l’équipe de conformité.

### <a name="example-of-disclaimer"></a>Exemple de clause d’exclusion de responsabilité

Prenez en compte la clause d’exclusion de responsabilité suivante :

AVIS IMPORTANT : Ce message électronique est destiné à être reçu uniquement par les personnes autorisées à recevoir les informations confidentielles qu'il peut contenir. Les messages électroniques aux clients de Contoso peuvent contenir des informations confidentielles et privilégiées. Veuillez ne pas lire, copier, transférer ou stocker ce message si vous n’êtes pas un destinataire attendu de celui-ci. Si vous avez reçu ce message par erreur, veuillez le transférer à l’expéditeur et le supprimer complètement de votre système informatique.

Si le SIT a été configuré pour détecter un mot clé confidentiel, le modèle appelle une correspondance chaque fois qu’une exclusion de responsabilité est utilisée dans l’e-mail, ce qui entraîne un grand nombre de faux positifs.

### <a name="ignore-disclaimer-using-prefix-and-suffix-in-sit"></a>Ignorer la clause d’exclusion de responsabilité à l’aide du préfixe et du suffixe dans SIT

Une façon d’ignorer les instances de mots clés dans la clause d’exclusion de responsabilité consiste à exclure les instances de mots clés qui sont précédées d’un préfixe et suivies d’un suffixe.

Prenez en compte cette clause d’exclusion de responsabilité :

REMARQUE IMPORTANTE : Ce message électronique est destiné à être reçu uniquement par les personnes *autorisées à recevoir les* informations confidentielles **qu’il peut contenir**. Les messages électroniques aux clients de Contoso peuvent contenir des informations confidentielles et privilégiées. Veuillez ne pas lire, copier, transférer ou stocker ce message si vous n’êtes pas un destinataire attendu de celui-ci. Si vous avez reçu ce message par erreur, veuillez le transférer à l’expéditeur et le supprimer complètement de votre système informatique.

Nous avons deux instances du mot clé « confidentiel » et si nous configurons le SIT pour ignorer les instances de ce mot clé précédées de préfixes (italique dans l’exemple) et suivies de suffixes (mis en gras dans l’exemple), nous pouvons parvenir à ignorer les exclusions de responsabilité dans la plupart des cas.

Pour ignorer la clause d’exclusion de responsabilité à l’aide du préfixe et du suffixe :

1. Ajoutez des vérifications supplémentaires dans le sit actuel pour exclure le texte du préfixe et du suffixe au mot clé que nous voulons ignorer dans la clause d’exclusion de responsabilité.
1. Choisissez d’exclure le préfixe et, dans la zone de texte **Préfixes** , **entrez les informations correspondantes**.
1. Choisissez d’exclure le suffixe et, dans la zone de texte **Suffixes** , entrez **et légalement privilégiés**.
1. Répétez ce processus pour d’autres instances des mots clés dans la clause d’exclusion de responsabilité, comme illustré dans le graphique suivant.

### <a name="ignore-disclaimer-by-excluding-secondary-elements"></a>Ignorer la clause d’exclusion de responsabilité en excluant les éléments secondaires

Une autre façon d’ajouter une liste d’éléments de prise en charge (instances dans la clause d’exclusion de responsabilité) qui doit être exclue consiste à exclure les éléments secondaires.

Prenez en compte cette clause d’exclusion de responsabilité :

AVIS IMPORTANT : Ce message électronique est destiné à être reçu uniquement par les personnes autorisées à recevoir les informations confidentielles qu'il peut contenir. Les messages électroniques aux clients de Contoso peuvent contenir des informations confidentielles et privilégiées. Veuillez ne pas lire, copier, transférer ou stocker ce message si vous n’êtes pas un destinataire attendu de celui-ci. Si vous avez reçu ce message par erreur, veuillez le transférer à l’expéditeur et le supprimer complètement de votre système informatique.

Dans cet exemple, nous avons deux instances du mot clé « confidentiel ». Si nous configurons le SIT pour ignorer les instances de ce mot clé dans la clause d’exclusion de responsabilité (soulignée en rouge), nous pouvons parvenir à ignorer les exclusions de responsabilité dans la plupart des cas.

:::image type="content" source="../media/sit-scenario-edit-pattern.png" alt-text="Vous pouvez ajouter d’autres conditions au modèle pour exclure des instances supplémentaires dans la clause d’exclusion de responsabilité.":::

Pour ignorer la clause d’exclusion de responsabilité à l’aide d’éléments secondaires :

1. Sélectionnez **Aucun de ces** groupes dans les éléments de prise en charge.
1. Ajoutez les instances de clause d’exclusion de responsabilité que nous voulons ignorer en tant que liste/dictionnaire de mots clés.
1. Ajoutez les mots clés sous la forme d’une nouvelle ligne que nous voulons ignorer. N’oubliez pas que la longueur de chaque texte ne peut pas dépasser 50 caractères.
1. Définissez la proximité de cet élément à moins de 50 à 60 caractères de l’élément principal.
