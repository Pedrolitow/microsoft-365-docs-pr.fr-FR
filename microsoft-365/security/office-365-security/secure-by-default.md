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
ms.openlocfilehash: 50d1c64e4d8343fdb9b25bfcbeee5d988ddc6b8a
ms.sourcegitcommit: 9dbc6a08177aaca112e84d30dbaa79a0a8e9dbf8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "48945329"
---
# <a name="secure-by-default-in-office-365"></a>Sécurité par défaut dans Office 365

[!INCLUDE [Prerelease information](../includes/prerelease.md)]
[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

« Sécurisé par défaut » est un terme utilisé pour définir les paramètres par défaut les plus sécurisés.

Toutefois, la sécurité doit être équilibrée en termes de productivité. Cela peut inclure l’équilibrage entre :

- Convivialité : les paramètres ne doivent pas bénéficier du mode de productivité de l’utilisateur.
- Risque : la sécurité peut bloquer des activités importantes.
- Paramètres hérités : il est possible que certaines configurations pour des produits et des fonctionnalités plus anciens doivent être conservées pour des raisons professionnelles, même si les nouveaux paramètres modernes sont améliorés.

Les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online sont protégées par Exchange Online Protection (EOP). Cette protection inclut :

1. Les messages électroniques avec un programme malveillant suspectés seront automatiquement mis en quarantaine et les destinataires seront avertis. Consultez la rubrique [configure anti-malware Policies in EOP](configure-anti-malware-policies.md).
1. Les e-mails de hameçonnage identifiés comme « à fiabilité élevée » seront gérés conformément à l’action de la stratégie de blocage du courrier indésirable. Consultez la rubrique [configurer des stratégies anti-courrier indésirable dans EOP](configure-your-spam-filter-policies.md).

Étant donné que Microsoft souhaite assurer la sécurité de nos clients par défaut, certains remplacements de locataire ne sont pas appliqués pour les logiciels malveillants ou les hameçons à haut niveau de fiabilité. Ces substitutions sont les suivantes :

- Listes d’expéditeurs autorisés ou listes de domaines autorisés (stratégies anti-courrier indésirable)
- Expéditeurs approuvés Outlook
- Liste d’adresses IP autorisées (filtrage des connexions)

Vous trouverez plus d’informations sur ces substitutions dans la [liste créer des listes d’expéditeurs approuvés](https://docs.microsoft.com/microsoft-365/security/office-365-security/create-safe-sender-lists-in-office-365).

Sécurisé par défaut il ne s’agit pas d’un paramètre qui peut être activé ou désactivé, mais de la façon dont notre filtrage fonctionne de la manière à ce que les messages potentiellement dangereux ou indésirables soient conservés de vos boîtes aux lettres. Les logiciels malveillants et les hameçons à haut niveau de fiabilité doivent être mis en quarantaine. Seuls les administrateurs peuvent gérer les messages mis en quarantaine en tant que programmes malveillants ou hameçonnage à haut niveau de confiance, et ils peuvent également signaler des faux positifs à Microsoft à partir de là. Pour plus d’informations, consultez la rubrique [gestion des messages et des fichiers mis en quarantaine en tant qu’administrateur dans EOP](manage-quarantined-messages-and-files.md) .

## <a name="exceptions"></a>Exceptions

Les seules substitutions qui contournent tous les filtres sont les suivantes :

- Règles de flux des règles de transport Exchange (ETR)/mail. Utilisez des règles de flux de messagerie pour définir le seuil de probabilité de courrier indésirable (SCL) dans les messages dans EOP.
- Liste d’adresses client autorisées/bloquées : gérer les URL et les fichiers dans la liste d’autorisation/de blocage de client.

Ces types de substitutions sont utiles pour :

- Simulations d’hameçon : les attaques simulées peuvent vous aider à identifier les utilisateurs vulnérables avant qu’une attaque réelle n’influe sur votre organisation.
- Boîtes aux lettres de sécurité/COP : boîtes aux lettres dédiées utilisées par les équipes de sécurité pour obtenir des messages non filtrés (à la fois bon et mauvais). Teams peut ensuite vérifier s’il contient du contenu malveillant.
- Filtres tiers : certains fournisseurs tiers recommandent de désactiver EOP (SCL =-1) car le filtre tiers gère le filtrage du courrier. Microsoft ne recommande pas de désactiver EOP au fur et à mesure que EOP est requis pour Office 365.
- Faux positifs : vous pouvez autoriser certains messages qui sont toujours analysés par Microsoft [via des soumissions d’administration](admin-submission.md). Comme pour toutes les substitutions, il est recommandé qu’elles soient temporaires.
