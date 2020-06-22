---
title: Types d’informations sensibles personnalisés pour la protection contre la perte de données (DLP)
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.date: 04/23/2019
localization_priority: Priority
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Obtenez une vue d’ensemble des types d’informations sensibles personnalisés pour la protection contre la perte de données (DLP), tels que le modèle primaire, la proximité des caractères et le niveau de confiance.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 6934edba6eef03bc9d4bfc5c1c69f127a7d3a0e5
ms.sourcegitcommit: 973f5449784cb70ce5545bc3cf57bf1ce5209218
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2020
ms.locfileid: "44817963"
---
# <a name="custom-sensitive-information-types"></a>Types d’informations sensibles personnalisés

Microsoft 365 inclut différents types d’informations sensibles intégrés prêts à l’emploi, par exemple, pour la [protection contre la perte de données](data-loss-prevention-policies.md) (DLP) ou avec [Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security). Les types d’informations sensibles intégrés peuvent aider à identifier et à protéger des numéros de carte de crédit, de compte bancaire, de passeport et autres sur la base de modèles définis par une expression régulière (regex) ou une fonction. Pour en savoir plus, voir [Éléments recherchés par les types d’informations sensibles](what-the-sensitive-information-types-look-for.md).

Mais que se passe-t-il si vous devez identifier et protéger un autre type d’informations sensibles, par exemple, des ID d’employé ou des numéros de projet, à l’aide d’un format spécifique de votre organisation ? Vous pouvez créer un type d’informations sensibles personnalisé.

Les éléments fondamentaux d’un type d’informations sensibles personnalisé sont :

- **Modèle principal** : numéros d’identification d’employé, numéros de projet, etc. Cela est généralement identifié par une expression régulière (RegEx) mais il peut aussi s’agir d’une liste de mots clés.

- **Additional evidence**: Suppose you're looking for a nine-digit employee ID number. Not all nine-digit numbers are employee ID numbers, so you can look for additional text: keywords like "employee", "badge", "ID", or other text patterns based on additional regular expressions. This supporting evidence (also known as _supporting_ or _corroborative_ evidence) increases the likelihood that nine-digit number found in content is really an employee ID number.

- **Character proximity**: It makes sense that the closer the primary pattern and the supporting evidence are to each other, the more likely the detected content is going to be what you're looking for. You can specify the character distance between the primary pattern and the supporting evidence (also known as the _proximity window_) as shown in the following diagram:

    ![Diagramme de la fenêtre de proximité et de preuves probantes](../media/dc68e38e-dfa1-45b8-b204-89c8ba121f96.png)

- **Confidence level**: The more supporting evidence you have, the higher the likelihood that a match contains the sensitive information you're looking for. You can assign higher levels of confidence for matches that are detected by using more evidence.

  When satisfied, a pattern returns a count and confidence level, which you can use in the conditions in your DLP policies. When you add a condition for detecting a sensitive information type to a DLP policy, you can edit the count and confidence level as shown in the following diagram:

    ![Nombre d’instances et options de précision de correspondance](../media/11d0b51e-7c3f-4cc6-96d8-b29bcdae1aeb.png)

## <a name="creating-custom-sensitive-information-types"></a>Création de types d’informations sensibles personnalisés

Pour créer des types d’informations sensibles personnalisés dans le Centre de sécurité et conformité, vous disposez des options suivantes :

- **Utiliser EDM** (nouveau) Vous pouvez configurer des types d’informations sensibles personnalisés à l’aide d’une classification de correspondance exacte des données (EDM, Exact Data Match). Cette méthode vous permet de créer un type d’informations sensibles dynamique à l’aide d’une base de données sécurisée que vous pouvez actualiser régulièrement. Voir l’article sur la [création d’un type d’informations sensibles personnalisé à l’aide d’une classification de correspondance exacte des données](create-custom-sensitive-information-types-with-exact-data-match-based-classification.md).

- **Utiliser PowerShell** vous pouvez configurer des types d’informations sensibles personnalisés à l’aide de PowerShell. Bien que cette méthode soit plus complexe que celle de l’interface utilisateur, elle offre davantage d’options de configuration. Voir [Créer un type d’informations sensibles personnalisé dans l’interface PowerShell du Centre de sécurité et conformité](create-a-custom-sensitive-information-type-in-scc-powershell.md).

- **Utiliser l’interface utilisateur** Vous pouvez configurer un type d’informations sensibles personnalisé à l’aide de l’interface utilisateur du Centre de sécurité et de conformité. Cette méthode vous permet d’utiliser des expressions régulières, des mots clés et des dictionnaires de mots clés. Pour en savoir plus, voir [Créer un type d’informations sensibles personnalisé](create-a-custom-sensitive-information-type.md).



