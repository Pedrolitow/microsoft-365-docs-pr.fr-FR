---
title: Utiliser les étiquettes de confidentialité comme conditions dans les stratégies DLP (préversion)
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
localization_priority: Priority
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MET150
ms.custom:
- seo-marvel-apr2020
description: en savoir plus sur les types de services et d’éléments dont vous pouvez utiliser les étiquettes de confidentialité comme conditions dans les stratégies DLP
ms.openlocfilehash: 561a6cbd7b8aeb9082862319c5cc6419fd79c896
ms.sourcegitcommit: f7ca339bdcad38796c550064fb152ea09687d0f3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "48321109"
---
# <a name="use-sensitivity-labels-as-conditions-in-dlp-policies-preview"></a>Utiliser les étiquettes de confidentialité comme conditions dans les stratégies DLP (préversion)

Vous pouvez utiliser [ les étiquettes de confidentialité](sensitivity-labels.md)comme condition dans les stratégies de protection contre la perte de données pour cet emplacement:

- Messagerie Exchange Online
- SharePoint Online
- Sites OneDrive Entreprise
- Appareils Windows 10

Les étiquettes de confidentialité apparaissent comme une option dans la liste du **Contenu**.

![Étiquette de confidentialité comme condition](../media/dlp-sensitivity-label-as-a-condition.png)

## <a name="supported-items-scenarios-and-policy-tips"></a>Éléments, scénarios et conseils de stratégie pris en charge

Vous pouvez utiliser des étiquettes de confidentialité comme conditions sur ces éléments et dans ces scénarios.

### <a name="supported-items"></a>Éléments non pris en charge 

|service  |type d’élément  |disponible pour l’astuce de stratégie  |applicable  |
|---------|---------|---------|---------|
|Exchange    |Message électronique         |oui         |oui         |
|Exchange    |Pièce jointe         |non *         |non *         |
|SharePoint Online     |éléments dans SharePoint Online         |oui         |oui         |
|OneDrive Entreprise     |éléments         |oui         |oui         |
|Teams     |Teams et messages de canal         |non applicable         |non applicable         |
|Teams     |pièces jointes         |Oui **         |Oui **         |
|Appareils Windows 10 (préversion)     |éléments         |oui         |oui         |
|MCAS (préversion) |éléments         |oui         |oui         |

\* La détection DLP des étiquettes de confidentialité sur les messages électroniques est prise en charge. La détection DLP des pièces jointes à étiquettes de confidentialité n’est pas prise en charge.

\** Les pièces jointes envoyées dans Teams au cours des conversations ou canaux de 1:1 sont chargées automatiquement sur OneDrive pour Entreprise et SharePoint. Par conséquent, si SharePoint Online ou OneDrive pour Entreprise sont inclus dans votre stratégie DLP, les pièces jointes à étiquettes envoyées dans Teams sont automatiquement incluses dans l’étendue de cette condition. Il n’est pas nécessaire de sélectionner Teams comme emplacement dans la stratégie DLP.

### <a name="supported-scenarios"></a>Scénarios pris en charge

- L’administrateur DLP peut afficher la liste de toutes les étiquettes de confidentialité du client lorsqu’il choisit d’inclure une ou plusieurs étiquettes de confidentialité comme condition.
- L’utilisation d’étiquettes de confidentialité comme condition est prise en charge dans toutes les charges de travail, comme indiqué dans la matrice de support ci-dessus.
- Les conseils de stratégie DLP continueront à être présentés dans les charges de travail (sauf Outlook Win32) pour les stratégies DLP qui contiennent une étiquette de confidentialité comme condition.
- Les étiquettes de confidentialité s’affichent également dans le message de rapport d’incident si une stratégie DLP avec une étiquette de confidentialité comme condition est associée.
- Les détails de l’étiquette de confidentialité s’affichent également dans le journal d’audit de correspondance des règles DLP pour une correspondance de stratégie DLP qui contient l’étiquette de confidentialité comme condition.


### <a name="support-policy-tips"></a>Conseils de stratégie de support


|charge de travail  |conseils de stratégie pris en charge/non pris en charge  |
|---------|---------|
|OWA |    Pris en charge     |
|Outlook Win 32    |  non pris en charge       |
|SharePoint   |   Pris en charge      |
|OneDrive Entreprise    |    Pris en charge     |
|appareils de point de terminaison   |  non pris en charge       |
