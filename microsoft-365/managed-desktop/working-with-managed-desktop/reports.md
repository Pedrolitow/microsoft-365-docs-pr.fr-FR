---
title: Utiliser les rapports
description: Les différents rapports disponibles dans Bureau géré Microsoft
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: b37ce09a0781aa83970502224ddbb3658ed07d69
ms.sourcegitcommit: 5d8de3e9ee5f52a3eb4206f690365bb108a3247b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2021
ms.locfileid: "52771884"
---
# <a name="work-with-reports"></a>Utiliser les rapports

Bureau géré Microsoft fournit plusieurs rapports et tableaux de bord que les administrateurs informatiques de votre organisation peuvent utiliser pour comprendre différents aspects de la population d’appareils. 

## <a name="reports-in-microsoft-endpoint-manager"></a>Rapports dans Microsoft Endpoint Manager

La console Microsoft Endpoint Manager regroupe les rapports de plusieurs produits dans un emplacement unique pour vous aider à surveiller et à examiner les problèmes de configuration et d’appareils de votre organisation Azure AD (« client »). Bureau géré Microsoft comprend une section sous **Rapports** dans le menu principal où vous pouvez trouver des rapports spécifiques à Bureau géré Microsoft gestion des appareils que vous avez enregistrés.

Ces rapports sont les suivants :
- **Appareils gérés**  >  **Mises à jour de fonctionnalités**: cet affichage affiche l’état global des mises à jour de fonctionnalités sur Bureau géré Microsoft appareils.
- **Appareils gérés**  >  **Office mises à** jour : cet affichage affiche l’état global des mises à jour Office mises à jour sur Bureau géré Microsoft appareils.

En outre, dans plusieurs emplacements dans Microsoft Endpoint Manager vous pouvez filtrer les rapports provenant d’autres groupes de produits afin d’inclure ou d’exclure spécifiquement vos appareils gérés par Bureau géré Microsoft. Ces rapports ont intégré cette fonctionnalité de filtrage :

- [Tous les appareils](/mem/intune/remote-actions/device-management#get-to-your-devices)
- [Conformité des appareils](/mem/intune/fundamentals/reports#device-compliance-report-organizational)
- [Appareils non conformes](/mem/intune/fundamentals/reports#noncompliant-devices-report-operational)

> [!NOTE]
> Les rôles Bureau géré Microsoft personnalisés garantissent l’accès uniquement aux Bureau géré Microsoft rapports. Pour accéder à d’autres parties Microsoft Endpoint Manager, telles que tous les **appareils,** voir Contrôle d’accès basé sur un [rôle avec Microsoft Intune](/mem/intune/fundamentals/role-based-access-control). 

## <a name="endpoint-analytics"></a>Analyse des points de terminaison
Bureau géré Microsoft est désormais intégré à [l’analyse des points de terminaison.](/mem/analytics/overview) Ces rapports vous donnent des informations sur la mesure du fonctionnement de votre organisation et de la qualité de l’expérience qu’ils offrent à vos utilisateurs. L’analyse des points de terminaison se trouve **dans le** menu Rapports [de Microsoft Endpoint Manager](https://endpoint.microsoft.com/). Pour faire pivoter un score afin d’inclure uniquement les  appareils gérés par Bureau géré Microsoft allez à n’importe quel rapport, sélectionnez le filtre de la baisse, puis sélectionnez Bureau géré Microsoft **appareils.**

Si l’analyse des points de terminaison n’a pas été configurée automatiquement pour votre organisation Azure AD (« client ») lors de l’inscription, vous pouvez le faire vous-même. Pour plus d’informations, [voir Intégrer dans le portail d’analyse des points de terminaison.](/mem/analytics/enroll-intune#bkmk_onboard) Vous pouvez inscrire tous vos appareils ou, si vous souhaitez inclure  uniquement des appareils Bureau géré Microsoft, sélectionnez les groupes d’appareils d’espace de travail modernes pour Test, Premier, Rapide et Large. Ces rapports peuvent nécessiter des autorisations différentes. Pour plus d’informations, [voir Autorisations](/mem/analytics/overview#permissions) pour vous assurer que des rôles sont correctement attribués.

> [!NOTE]
> Pour mieux respecter la confidentialité des données utilisateur, il doit y avoir plus de 10 appareils Bureau géré Microsoft inscrits avec Endpoint Analytics pour utiliser ce filtre.

 ## <a name="inventory-data"></a>Données d’inventaire

Outre les autres rapports, vous pouvez exporter des informations sur les appareils gérés par Bureau géré Microsoft. Dans la vue  **Appareils** de la zone Appareils  de Microsoft Endpoint Manager, utilisez l’onglet Exporter tout pour télécharger un [rapport d’inventaire détaillé.](device-inventory-report.md)
