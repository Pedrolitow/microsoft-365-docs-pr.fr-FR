---
title: Activer l’intégration de la prise en charge de Microsoft 365 pour ServiceNow Virtual Agent
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- scotvorg
- M365-subscription-management
- Adm_TOC
ms.custom: AdminSurgePortfolio
ROBOTS: NOINDEX, NOFOLLOW
search.appverid:
- MET150
description: Configurez la fonctionnalité expérimentale d’intégration de support pour tester et fournir des commentaires à l’équipe d’intégration du support technique Microsoft 365.
ms.openlocfilehash: 48a49b1e4a19039c40db278adf398f9a0ccd3831
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68172948"
---
# <a name="enable-microsoft-365-support-integration-for-servicenow-virtual-agent"></a>Activer l’intégration de la prise en charge de Microsoft 365 pour ServiceNow Virtual Agent

> [!IMPORTANT]
> L’intégration de la prise en charge de ServiceNow Virtual Agent est une fonctionnalité expérimentale déployée pour permettre aux utilisateurs de tester et de fournir des commentaires à l’équipe d’intégration du support Technique Microsoft 365.

Lorsque vous configurez l’application d’intégration de support Microsoft 365 pour qu’elle fonctionne avec ServiceNow Virtual Agent, vous avez accès aux **solutions recommandées** via deux expériences utilisateur différentes :

- **Quick Insights** Similaire à ce qui apparaît sur la page Incidents, l’agent virtuel ServiceNow affiche les **articles recommandés** et les **solutions Recommend** en fonction du texte entré.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-support-integration-1.png" lightbox="../../media/ServiceNow-guide/servicenow-support-integration-1.png" alt-text="Quick Insights.":::

- **Expérience de branchement** La branche s’intègre à la fonctionnalité de recherche et d’assistant pour guider les utilisateurs dans un flux de dépannage qui retourne des réponses en fonction du texte entré.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-support-integration-2.png" lightbox="../../media/ServiceNow-guide/servicenow-support-integration-2.png" alt-text="Expérience de branchement.":::

## <a name="before-you-begin"></a>Avant de commencer

- Activez l’agent virtuel dans ServiceNow. Pour plus d’informations, consultez [Activer l’agent virtuel](https://docs.servicenow.com/bundle/quebec-now-intelligence/page/administer/virtual-agent/task/activate-virtual-agent.html).

- Téléchargez et terminez la configuration de l’application d’intégration de support Microsoft 365 à partir du ServiceNow Store.

- La version minimale de Microsoft 365 prend en charge l’intégration : v1.0.10.

- Version minimale de ServiceNow : Québec.

- Rôle requis : Administration.

## <a name="configure-microsoft-365-support-integration-to-work-with-servicenow-virtual-agent"></a>Configurer l’intégration de la prise en charge de Microsoft 365 pour qu’elle fonctionne avec ServiceNow Virtual Agent

- Définissez le support Microsoft 365 comme rubrique de secours. Pour plus d’informations, consultez [Configurer une expérience de conversation de l’agent virtuel](https://docs.servicenow.com/bundle/quebec-now-intelligence/page/administer/virtual-agent/task/configure-default-chat-experience.html).

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-support-integration-3.png" lightbox="../../media/ServiceNow-guide/servicenow-support-integration-3.png" alt-text="Définissez la rubrique de secours de l’expérience de conversation par défaut.":::