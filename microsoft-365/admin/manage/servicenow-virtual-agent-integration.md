---
title: Intégrer Microsoft 365 à ServiceNow Virtual Agent
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
- Tier2
- scotvorg
- M365-subscription-management
- Adm_TOC
ms.custom: AdminSurgePortfolio
ROBOTS: NOINDEX, NOFOLLOW
search.appverid:
- MET150
description: Configurez l’intégration du support pour tester et fournir des commentaires à l’équipe d’intégration du support microsoft 365.
ms.openlocfilehash: 25c18c562776e7e28a9f6596950f36d6396021b4
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68735636"
---
# <a name="integrate-microsoft-365-with-servicenow-virtual-agent"></a>Intégrer Microsoft 365 à ServiceNow Virtual Agent

Lorsque vous configurez l’application d’intégration de support Microsoft 365 pour qu’elle fonctionne avec l’agent virtuel ServiceNow, vous accédez à l’aide autonome créée par les équipes de produit Microsoft 365 via deux expériences utilisateur différentes :

- Solutions pas à pas et pas à pas Microsoft 365.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-support-integration-2.png" lightbox="../../media/ServiceNow-guide/servicenow-support-integration-1.png" alt-text="Quick Insights.":::
    :::image type="content" source="../../media/ServiceNow-guide/servicenow-support-integration-2b.png" lightbox="../../media/ServiceNow-guide/servicenow-support-integration-2b.png" alt-text="Quick Insights.":::

- Principaux résultats de recherche web des articles microsoft 365 base de connaissances.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-support-integration-1.png" lightbox="../../media/ServiceNow-guide/servicenow-support-integration-1.png" alt-text="Résultats de la recherche d’un article de la base de connaissances.":::

## <a name="before-you-begin"></a>Avant de commencer

- Activez l’agent virtuel dans ServiceNow. Pour plus d’informations, consultez [Activer l’agent virtuel](https://docs.servicenow.com/bundle/quebec-now-intelligence/page/administer/virtual-agent/task/activate-virtual-agent.html).

- Installez et terminez la configuration de l’application d’intégration de support Microsoft 365 à partir du ServiceNow Store.

- Version minimale de ServiceNow : Rome.

- Rôle requis : Administrateur ou virtual_agent_admin ServiceNow.

## <a name="configure-microsoft-365-support-integration-to-work-with-servicenow-virtual-agent"></a>Configurer l’intégration de la prise en charge de Microsoft 365 pour utiliser l’agent virtuel ServiceNow

### <a name="standalone-fallback-topic"></a>Rubrique de secours autonome

Définissez Support Microsoft 365 comme rubrique de secours. Pour plus d’informations, consultez [Configurer une expérience de conversation d’agent virtuel](https://docs.servicenow.com/bundle/quebec-now-intelligence/page/administer/virtual-agent/task/configure-default-chat-experience.html).

:::image type="content" source="../../media/ServiceNow-guide/servicenow-support-integration-3.png" lightbox="../../media/ServiceNow-guide/servicenow-support-integration-3.png" alt-text="Définir la rubrique de secours de l’expérience de conversation par défaut.":::

### <a name="topic-blocks"></a>Blocs de rubriques

Si aucune rubrique n’est créée, vous pouvez utiliser la rubrique de secours autonome comme ci-dessus ou [créer votre propre rubrique d’agent virtuel](https://docs.servicenow.com/bundle/rome-now-intelligence/page/administer/virtual-agent/task/create-virtual-agent-topic.html).

Procédez comme suit pour ajouter le bloc de rubriques Support Microsoft 365 :

1. Sous **Utilitaires**, sélectionnez **Bloc de rubrique**, puis ajoutez-le à votre flux.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-topic-block-1.png" lightbox="../../media/ServiceNow-guide/servicenow-topic-block-1.png" alt-text="Ajoutez un bloc de rubriques à votre flux.":::

1. Sous **Propriétés du bloc de rubriques**, choisissez **Bloc de rubriques de support Microsoft 365**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-topic-block-2.png" lightbox="../../media/ServiceNow-guide/servicenow-topic-block-2.png" alt-text="Choisissez la propriété Bloc de rubriques de support.":::

1. Un bloc de rubrique de support Microsoft 365 accède au texte d’entrée dans cet ordre :

    a. Vérifie la variable d’entrée. Si la variable d’entrée n’est pas vide, récupère les résultats de la variable d’entrée.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-topic-block-3.png" lightbox="../../media/ServiceNow-guide/servicenow-topic-block-3.png" alt-text="Récupère les résultats de la variable d’entrée.":::

    b. Si la variable d’entrée est vide, recherche le texte entré par l’utilisateur dans la fenêtre de conversation et extrait les résultats du texte.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-topic-block-4.png" lightbox="../../media/ServiceNow-guide/servicenow-topic-block-4.png" alt-text="Recherche le texte entré dans la fenêtre de conversation.":::

    c. Si l’utilisateur n’a pas entré de texte, lui demande d’entrer du texte pour extraire les résultats.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-topic-block-5.png" lightbox="../../media/ServiceNow-guide/servicenow-topic-block-5.png" alt-text="Recherche le texte entré dans la fenêtre de conversation.":::

1. Le bloc de rubriques de support Microsoft 365 fournit une variable de sortie, qui correspond aux commentaires de l’utilisateur pour les résultats.

    a. Nom de la variable de sortie : m365_success b. Valeurs possibles des variables de sortie : OUI/NON

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-topic-block-6.png" lightbox="../../media/ServiceNow-guide/servicenow-topic-block-6.png" alt-text="Nom et valeurs de la variable de sortie.":::