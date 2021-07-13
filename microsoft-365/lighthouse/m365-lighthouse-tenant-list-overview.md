---
title: vue d Microsoft 365 Lighthouse liste des locataires
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Pour les fournisseurs de services gérés (MSP) utilisant Microsoft 365 Lighthouse, découvrez la liste des clients.
ms.openlocfilehash: 05c6bf6c1b9529d05fac04c2d5c43802280cfbc9
ms.sourcegitcommit: 00f001019c653269d85718d410f970887d904304
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2021
ms.locfileid: "53395174"
---
# <a name="microsoft-365-lighthouse-tenant-list-overview"></a>vue d Microsoft 365 Lighthouse liste des locataires

> [!NOTE]
> Les fonctionnalités décrites dans cet article sont en prévisualisation, peuvent faire l’objet de changements et sont uniquement disponibles pour les partenaires qui répondent aux [exigences.](m365-lighthouse-requirements.md) Si votre organisation n’a pas de Microsoft 365 Lighthouse, voir [S’inscrire pour Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md).

La liste Microsoft 365 Lighthouse client fournit des informations sur les différents locataires avec lesquels vous avez un contrat, y compris l’état d’intégration du client par rapport aux Microsoft 365 Lighthouse. La liste des locataires vous permet également de baliser les locataires pour fournir différents filtres dans Microsoft 365 Lighthouse et d’en savoir plus sur un client donné et l’état de son plan de déploiement.

Une fois que vos clients répondent [aux Microsoft 365 Lighthouse’intégration](m365-lighthouse-requirements.md)requises, leur statut s’affiche **comme actif** dans la liste des clients.

Pour accéder à la liste des  locataires dans Microsoft 365 Lighthouse, sélectionnez Les locataires dans le volet de navigation de gauche pour ouvrir la page Locataires.

## <a name="tenant-status"></a>État du client

Le tableau suivant présente les différents messages d’état et leur signification.<br><br>

| Message d’état | Description |
|--|--|
| Actif | L’intégration et le flux de données ont démarré. |
| In process | Client découvert, mais pas entièrement intégré. |
| Inéligible, DAP | La configuration des privilèges d’administration délégués (DAP) est requise. |
| Nombre d’utilisateurs non éligibles | Le client compte plus d’utilisateurs que le nombre autorisé. |
| Inéligible, license | Le client n’a pas de licence requise. |
| Inactif | Le client n’est plus actif. |

Une fois que vous avez désactivé un client, vous ne pouvez pas agir sur le client tant que Microsoft 365 Lighthouse termine le processus d’inactivation. L’inactivation peut prendre jusqu’à 48 heures.

Si vous décidez de réactiver un client, la réapparition des données peut prendre jusqu’à 48 heures.

## <a name="tenant-tags"></a>Balises de client

Vous pouvez marquer vos clients avec une étiquette personnalisée dans Microsoft 365 Lighthouse. Ces balises peuvent être utilisées pour organiser vos clients et peuvent également vous aider à filtrer facilement les affichages et informations existants disponibles pour les ensembles pertinents de clients. Vous pouvez également gérer vos balises et les locataires à qui elles sont affectées à partir de la page Locataires.

## <a name="related-content"></a>Contenu associé

[Requirements for Microsoft 365 Lighthouse](m365-lighthouse-requirements.md) (article)\
[Microsoft 365 Lighthouse FAQ](m365-lighthouse-faq.yml) (article)