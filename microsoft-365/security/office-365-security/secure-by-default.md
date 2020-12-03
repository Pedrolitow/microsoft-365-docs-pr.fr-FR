---
title: Sécurité par défaut dans Office 365
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
description: En savoir plus sur le paramètre sécurisé par défaut dans Exchange Online Protection (EOP)
ms.openlocfilehash: 54000d351463ba90751f1f27638fb52847cf05ce
ms.sourcegitcommit: c1dd5be42fe0c5dcc7c05817c941edd9076febf8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2020
ms.locfileid: "49558513"
---
# <a name="secure-by-default-in-office-365"></a>Sécurité par défaut dans Office 365

[!INCLUDE [Prerelease information](../includes/prerelease.md)]
[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

« Sécurisé par défaut » est un terme utilisé pour définir les paramètres par défaut les plus sécurisés.

Toutefois, la sécurité doit être équilibrée en termes de productivité. Cela peut inclure l’équilibrage entre :

- **Convivialité**: les paramètres ne doivent pas bénéficier du mode de productivité de l’utilisateur.
- **Risque**: la sécurité peut bloquer des activités importantes.
- **Paramètres hérités**: il est possible que certaines configurations pour des produits et des fonctionnalités plus anciens doivent être conservées pour des raisons professionnelles, même si les nouveaux paramètres modernes sont améliorés.

Les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online sont protégées par Exchange Online Protection (EOP). Cette protection inclut :

- Les messages électroniques avec un programme malveillant suspectés seront automatiquement mis en quarantaine et les destinataires seront avertis. Consultez la rubrique [configure anti-malware Policies in EOP](configure-anti-malware-policies.md).
- Courrier électronique identifié comme un hameçonnage à niveau de confiance élevé sera géré en fonction de l’action de stratégie de blocage du courrier indésirable. Consultez la rubrique [configurer des stratégies anti-courrier indésirable dans EOP](configure-your-spam-filter-policies.md).

Étant donné que Microsoft souhaite assurer la sécurité de nos clients par défaut, certains remplacements de locataire ne sont pas appliqués pour les programmes malveillants ou le hameçonnage à haut niveau de confiance. Ces substitutions sont les suivantes :

- Listes d’expéditeurs autorisés ou listes de domaines autorisés (stratégies anti-courrier indésirable)
- Expéditeurs approuvés Outlook
- Liste d’adresses IP autorisées (filtrage des connexions)

Vous trouverez plus d’informations sur ces substitutions dans la [liste créer des listes d’expéditeurs approuvés](create-safe-sender-lists-in-office-365.md).

La sécurité par défaut n’est pas un paramètre qui peut être activé ou désactivé, mais c’est le mode de fonctionnement de notre filtrage qui permet de conserver les messages potentiellement dangereux ou indésirables dans vos boîtes aux lettres. Les messages hameçons et de confiance élevée doivent être mis en quarantaine. Seuls les administrateurs peuvent gérer les messages mis en quarantaine en tant que programmes malveillants ou hameçonnage à haute fiabilité, et ils peuvent également signaler des faux positifs à Microsoft à partir de là. Pour plus d’informations, consultez la rubrique [gestion des messages et des fichiers mis en quarantaine en tant qu’administrateur dans EOP](manage-quarantined-messages-and-files.md) .

## <a name="more-on-why-were-doing-this"></a>En savoir plus sur les raisons de cette opération

L’esprit de sécurité par défaut est le suivant : nous effectuons la même action sur le message que vous devez prendre si vous saviez que le message était malveillant, même si une autorisation était autorisée. Il s’agit de la même approche que celle utilisée pour les programmes malveillants et que nous étendons maintenant ce même comportement aux messages de hameçonnage à haute fiabilité. Nos données indiquent que le taux de faux positifs pour les messages de hameçonnage à haut niveau de confiance est très faible et que les administrateurs peuvent résoudre les faux positifs avec des soumissions de l’administrateur. Nos données indiquent également que les listes d’expéditeurs autorisés et les listes de domaines autorisés dans les stratégies de blocage du courrier indésirable et les expéditeurs approuvés dans Outlook étaient trop larges et de plus en plus nuisibles.

Pour en faire une autre : en tant que service de sécurité, nous faisons en sorte que vos utilisateurs ne soient pas compromis. Par ailleurs, la sécurisation par défaut ne constitue pas une prise en charge complète des options disponibles pour les messages de hameçonnage à haute fiabilité dans les stratégies de blocage du courrier indésirable. Bien que la mise en quarantaine soit recommandée, les autres actions toujours disponibles sont toujours disponibles (déplacer vers le dossier courrier indésirable ou rediriger vers une adresse de messagerie).

## <a name="exceptions"></a>Exceptions

La seule substitution qui permet de contourner le message de hameçonnage pour contourner le filtrage est celle des règles de flux de messagerie Exchange (également appelées règles de transport). Pour utiliser des règles de flux de messagerie pour contourner le filtrage, consultez [la rubrique use mail Flow Rules to Set the SCL in messages](use-mail-flow-rules-to-set-the-spam-confidence-level-scl-in-messages.md).

Vous devez envisager d’utiliser des remplacements uniquement dans les scénarios suivants :

- Simulations d’hameçonnage : les attaques simulées peuvent vous aider à identifier les utilisateurs vulnérables avant qu’une attaque réelle n’influe sur votre organisation.
- Boîtes aux lettres de sécurité/COP : boîtes aux lettres dédiées utilisées par les équipes de sécurité pour obtenir des messages non filtrés (à la fois bon et mauvais). Teams peut ensuite vérifier s’il contient du contenu malveillant.
- Filtres tiers : certains fournisseurs tiers vont recommander de désactiver EOP (SCL =-1) car le filtre tiers gérera le filtrage du courrier. Microsoft ne recommande pas de désactiver EOP au fur et à mesure que EOP est requis pour Office 365. Au lieu de cela, nous vous recommandons d’activer le [filtrage amélioré pour les connecteurs](https://docs.microsoft.com/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors).
- Faux positifs : vous pouvez autoriser temporairement certains messages qui sont toujours analysés par Microsoft [via des soumissions d’administration](admin-submission.md). Comme pour toutes les substitutions, il est recommandé qu’elles soient temporaires.
