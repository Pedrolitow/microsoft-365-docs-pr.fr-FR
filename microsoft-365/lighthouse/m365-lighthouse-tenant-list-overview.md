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
ms.openlocfilehash: af76322553296d1d22bb003ddf943ae168656734
ms.sourcegitcommit: f358e321f7e81eff425fe0f0db1be0f3348d2585
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2021
ms.locfileid: "58507877"
---
# <a name="microsoft-365-lighthouse-tenant-list-overview"></a>vue d Microsoft 365 Lighthouse liste des locataires

> [!NOTE]
> Les fonctionnalités décrites dans cet article sont en prévisualisation, peuvent faire l’objet de changements et sont uniquement disponibles pour les partenaires qui répondent aux [exigences.](m365-lighthouse-requirements.md) Si votre organisation n’a pas de Microsoft 365 Lighthouse, voir [S’inscrire pour Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md).

La liste Microsoft 365 Lighthouse client fournit des informations sur les différents locataires avec lesquels vous avez un contrat, y compris l’état d’intégration du client par rapport à l’État de l’île. La liste des locataires vous permet également de baliser les locataires afin de fournir différents filtres tout au long du projet, et d’en savoir plus sur un client donné et l’état de son plan de déploiement.

Une fois que vos clients répondent aux [exigences d’intégration de Onboard,](m365-lighthouse-requirements.md)leur statut s’affiche **comme actif** dans la liste des clients.

Pour accéder à la liste des locataires dans le Navigateur, sélectionnez Les **locataires** dans le volet de navigation de gauche pour ouvrir la page Locataires.

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

Une fois que vous avez désactivé un client, vous ne pouvez pas effectuer d’action sur le client tant que LeÉmanage termine le processus d’inactivation. L’inactivation peut prendre jusqu’à 48 heures.

Si vous décidez de réactiver un client, la réapparition des données peut prendre jusqu’à 48 heures.

## <a name="tenant-tags"></a>Balises de client

Vous pouvez baliser vos locataires clients avec une étiquette personnalisée dans Le Monde. Ces balises peuvent être utilisées pour organiser vos clients et peuvent également vous aider à filtrer facilement les vues et informations existantes disponibles pour les ensembles pertinents de clients. Vous pouvez également gérer vos balises et les locataires à qui elles sont affectées à partir de la page Locataires.

## <a name="related-content"></a>Contenu associé

[Requirements for Microsoft 365 Lighthouse](m365-lighthouse-requirements.md) (article)\
[Microsoft 365 Lighthouse FAQ](m365-lighthouse-faq.yml) (article)