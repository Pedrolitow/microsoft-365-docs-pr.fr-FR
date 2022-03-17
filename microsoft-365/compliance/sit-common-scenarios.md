---
title: Scénarios d’usage courants pour les types d’informations sensibles
f1.keywords:
- NOCSH
ms.author: chrfox
author: v-tophillips
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
description: Comment implémenter des scénarios de cas d’utilisation des types d’informations sensibles courants
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 39afa17fc7bf258848de9d5554b3dd56a1ce21b5
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63525735"
---
# <a name="common-usage-scenarios-for-sensitive-information-types"></a>Scénarios d’usage courants pour les types d’informations sensibles

Cet article explique comment implémenter certains scénarios courants d’utilisation de type d’informations sensibles (SIT). Vous pouvez utiliser ces procédures comme exemples et les adapter à vos besoins spécifiques.

## <a name="protect-credit-card-numbers"></a>Protéger les numéros de carte de crédit

Contoso Bank doit classer les numéros de carte de crédit qu’elle émettra comme sensibles. Leurs cartes de crédit commencent par un ensemble de modèles à six chiffres. Ils souhaitent personnaliser la définition de carte de crédit « out of the box » pour détecter uniquement les numéros de carte de crédit en commençant par leurs modèles à six chiffres.

**Solution suggérée**

1. Créez une copie de la carte de crédit SIT. Utilisez les étapes pour [copier et modifier un type d’informations sensibles](create-a-custom-sensitive-information-type.md#copy-and-modify-a-sensitive-information-type) afin de copier la carte de crédit SIT.
1. Modifiez le modèle de confiance élevée. Suivez les étapes de [modification ou de suppression du modèle de type d’informations sensibles](sit-get-started-exact-data-match-create-rule-package.md#edit-or-delete-the-sensitive-information-type-pattern).
1. Ajoutez la vérification « commence par » et ajoutez la liste des chiffres bin (formatés & sans mise en forme). Par exemple, pour vous assurer que seules les cartes de crédit commençant par 411111 & 433512 doivent être considérées comme valides, ajoutez les informations suivantes à la liste 4111 11, 4111-11, 411111, 4335 12, 4335-12, 433512.
1. Répétez l’étape 2 & 3 pour le modèle de faible niveau de confiance.

## <a name="test-numbers-similar-to-social-security-numbers"></a>Numéros de test similaires aux numéros de sécurité sociale

Contoso a identifié quelques numéros de test à neuf chiffres qui déclenchent des correspondances de faux positifs dans la stratégie de protection contre la perte de données (DLP) du numéro de sécurité sociale (SSN). Ils souhaitent exclure ces numéros de la liste des correspondances valides pour SSN.

**Solution suggérée**

1. Créez une copie du SSN SIT. Utilisez les étapes pour [copier et modifier un type d’informations sensibles](create-a-custom-sensitive-information-type.md#copy-and-modify-a-sensitive-information-type) afin de copier le sit SSN.
1. Modifiez le modèle de confiance élevée. Suivez les étapes de [modification ou de suppression du modèle de type d’informations sensibles](sit-get-started-exact-data-match-create-rule-package.md#edit-or-delete-the-sensitive-information-type-pattern).
1. Ajoutez les nombres à exclure dans la vérification supplémentaire « Exclure des valeurs spécifiques ». Par exemple, pour exclure les & 23923532 239-23-532, l’ajout 23923532 suffit.
1. Répétez également l’étape 2 & 3 pour d’autres modèles de confiance

## <a name="phone-numbers-in-signature-trigger-match"></a>Téléphone dans la correspondance de déclencheur de signature

Contoso basé en Australie trouve que les numéros de téléphone dans les signatures électroniques déclenchent une correspondance pour leur stratégie DLP numéro d’entreprise en Australie.

**Solution suggérée**

Ajoutez un groupe « non » dans les éléments de prise en charge à l’aide d’une liste de mots clés contenant des mots clés couramment utilisés dans la signature d’e-mails tels que « Téléphone », « Mobile », « e-mail », « Merci et merci », etc. Conservez la proximité de cette liste de mots clés à une valeur plus petite comme 50 caractères pour une meilleure précision. Pour plus d’informations, [consultez La mise en place des types d’informations sensibles personnalisés](create-a-custom-sensitive-information-type.md).

## <a name="unable-to-trigger-aba-routing-policy"></a>Impossible de déclencher la stratégie de routage ABA

La stratégie DLP ne peut pas déclencher la stratégie de numéro de routage ABA dans les fichiers Excel de grande taille, car le mot clé requis ne se trouve pas dans 300 caractères.

**Solution suggérée**

Créez une copie du sit intégré et modifiez-la pour modifier la proximité de la liste de mots clés de « 300 caractères » à « Anywhere in the document ».

> [!TIP]
> Vous pouvez modifier la liste des mots clés pour inclure/exclure des mots clés pertinents pour votre organisation.

## <a name="unable-to-detect-credit-card-numbers-with-unusual-delimiters"></a>Impossible de détecter les numéros de carte de crédit avec des délimiteur inhabituels

Contoso Bank a remarqué que certains de leurs employés partagent des numéros de carte de crédit avec « / » comme délimiteur, par exemple 4111/1111/1111/1111, qui n’est pas détecté par la définition de carte de crédit standard. Contoso souhaite définir sa propre regex et la valider à l’aide de LuhnCheck.

**Solution suggérée**

1. Créez une copie de la carte de crédit SIT à l’aide des étapes de personnalisation d’un [type d’informations sensibles intégré](customize-a-built-in-sensitive-information-type.md).
1. Ajouter un nouveau modèle
1. Dans l’élément principal, sélectionnez une expression régulière
1. Définissez l’expression régulière qui inclut « / » dans le cadre de l’expression régulière, puis choisissez validateur et sélectionnez luhncheck ou func_credit_card pour vous assurer que l’expression régulière passe également le LuhnCheck.

## <a name="ignore-a-disclaimer-notice"></a>Ignorer une notification d’exclusion de responsabilité

De nombreuses organisations ajoutent des clauses d’exclusion de responsabilité juridiques, des déclarations de divulgation, des signatures ou d’autres informations en haut ou en bas des messages électroniques qui entrent ou quittent leur organisation et, dans certains cas, même au sein des organisations. Les employés eux-mêmes ont placé des signatures, notamment des guillemets de motivation, des messages sociaux, etc. Une clause d’exclusion de responsabilité ou une signature peut contenir les termes présents dans le lexicon d’un cc et générer un grand nombre de faux positifs.  

Par exemple, une clause d’exclusion de responsabilité classique peut contenir des mots comme sensibles ou confidentiels et une stratégie qui recherche des informations sensibles les détecte comme un incident, entraînant un grand nombre de faux positifs. Ainsi, fournir aux clients la possibilité d’ignorer la clause d’exclusion de responsabilité peut réduire les faux positifs et augmenter l’efficacité de l’équipe de conformité.

### <a name="example-of-disclaimer"></a>Exemple de clause d’exclusion de responsabilité

Prenons la clause d’exclusion de responsabilité suivante :

AVIS IMPORTANT : Ce message électronique est destiné à être reçu uniquement par les personnes autorisées à recevoir les informations confidentielles qu'il peut contenir. Les messages électroniques aux clients de Contoso peuvent contenir des informations confidentielles et privilégiées. Veuillez ne pas lire, copier, transférer ou stocker ce message si vous n’êtes pas un destinataire attendu de celui-ci. Si vous avez reçu ce message par erreur, veuillez le transférer à l’expéditeur et le supprimer complètement de votre système informatique.

Si la sit a été configurée pour détecter un mot clé confidentiel, le modèle appelle une correspondance chaque fois qu’une clause d’exclusion de responsabilité est utilisée dans l’e-mail, ce qui génère un grand nombre de faux positifs.

### <a name="ignore-disclaimer-using-prefix-and-suffix-in-sit"></a>Ignorer la clause d’exclusion de responsabilité à l’aide du préfixe et du suffixe dans SIT

Une façon d’ignorer les instances de mots clés dans la clause d’exclusion de responsabilité consiste à exclure les instances de mots clés qui sont précédées d’un préfixe et suivies d’un suffixe.

Considérez cette clause d’exclusion de responsabilité :

REMARQUE IMPORTANTE : ce message électronique est destiné uniquement aux personnes autorisées à recevoir les  informations confidentielles **qu’il peut contenir**. Les messages électroniques aux clients de Contoso peuvent contenir des informations confidentielles et privilégiées. Veuillez ne pas lire, copier, transférer ou stocker ce message si vous n’êtes pas un destinataire attendu de celui-ci. Si vous avez reçu ce message par erreur, veuillez le transférer à l’expéditeur et le supprimer complètement de votre système informatique.

Nous avons deux instances du mot clé « confidentiel » et si nous configurons la sit pour ignorer les instances de ce mot clé précédées de préfixes (italique dans l’exemple) et suivies de suffixes (en gras dans l’exemple), nous pouvons parvenir à ignorer les clauses d’exclusion de responsabilité dans la plupart des cas.

Pour ignorer la clause d’exclusion de responsabilité à l’aide du préfixe et du suffixe :

1. Ajoutez des vérifications supplémentaires dans la sit actuelle pour exclure le préfixe et le texte de suffixe du mot clé que nous voulons ignorer dans la clause d’exclusion de responsabilité.
1. Choisissez d’exclure le préfixe et, dans la zone de texte **Préfixes** , entrez **des informations**.
1. Choisissez d’exclure le suffixe et, dans la zone de texte **Suffixes** , entrez **et avez des privilèges juridiques**.
1. Répétez ce processus pour les autres instances des mots clés dans la clause d’exclusion de responsabilité, comme illustré dans le graphique suivant.

### <a name="ignore-disclaimer-by-excluding-secondary-elements"></a>Ignorer la clause d’exclusion de responsabilité en excluant les éléments secondaires

Une autre façon d’ajouter une liste d’éléments de prise en charge (instances dans une clause d’exclusion de responsabilité) qui doit être exclue consiste à exclure les éléments secondaires.

Considérez cette clause d’exclusion de responsabilité :

AVIS IMPORTANT : Ce message électronique est destiné à être reçu uniquement par les personnes autorisées à recevoir les informations confidentielles qu'il peut contenir. Les messages électroniques aux clients de Contoso peuvent contenir des informations confidentielles et privilégiées. Veuillez ne pas lire, copier, transférer ou stocker ce message si vous n’êtes pas un destinataire attendu de celui-ci. Si vous avez reçu ce message par erreur, veuillez le transférer à l’expéditeur et le supprimer complètement de votre système informatique.

Nous avons deux instances du mot clé « confidentiel » dans cet exemple. Si nous configurons la sit pour ignorer les instances de ce mot clé dans la clause d’exclusion de responsabilité (soulignée en rouge), nous pouvons dans la plupart des cas ignorer les clauses d’exclusion de responsabilité.

:::image type="content" source="../media/sit-scenario-edit-pattern.png" alt-text="Vous pouvez ajouter des conditions supplémentaires au modèle pour exclure des instances supplémentaires dans la clause d’exclusion de responsabilité.":::

Pour ignorer la clause d’exclusion de responsabilité à l’aide d’éléments secondaires :

1. **Sélectionnez Pas un de ces groupes** dans les éléments de prise en charge.
1. Ajoutez les instances de clause d’exclusion de responsabilité que nous voulons ignorer en tant que liste/dictionnaire de mots clés.
1. Ajoutez les mots clés en tant que nouvelle ligne que nous voulons ignorer. N’oubliez pas que la longueur de chaque texte ne peut pas être plus de 50 caractères.
1. Définissez la proximité de cet élément à 50 à 60 caractères de l’élément principal.
