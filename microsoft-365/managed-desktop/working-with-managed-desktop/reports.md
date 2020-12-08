---
title: Utiliser les rapports
description: ''
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: bfd8305d23e0e6d761c629ee3048c6204f702d37
ms.sourcegitcommit: 98146c67a1d99db5510fa130340d3b7be8d81b21
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2020
ms.locfileid: "49585327"
---
# <a name="work-with-reports"></a>Utiliser les rapports

Microsoft Managed Desktop fournit plusieurs rapports et tableaux de bord que les administrateurs informatiques de votre organisation peuvent utiliser pour comprendre différents aspects de la population des appareils.Vous trouverez des rapports à deux emplacements : dans le [Gestionnaire de points de terminaison Microsoft](https://endpoint.microsoft.com) et dans le [centre d’administration 365 de Microsoft](https://admin.microsoft.com/adminportal/home?previewoff=false#/microsoftmanageddesktop). 

## <a name="reports-in-microsoft-endpoint-manager"></a>Rapports dans le gestionnaire de points de terminaison Microsoft

La console du gestionnaire de point de terminaison Microsoft rassemble des rapports à partir de plusieurs produits dans un même emplacement pour vous aider à surveiller et à étudier les problèmes liés à la configuration et aux périphériques de votre organisation Azure AD (« client »). Le bureau géré Microsoft comporte une section sous **rapports** dans le menu principal, dans laquelle vous pouvez trouver des rapports spécifiques à la gestion du bureau géré Microsoft des appareils que vous avez enregistrés.

En outre, dans plusieurs emplacements de Microsoft Endpoint Manager, vous pouvez filtrer les rapports d’autres groupes de produits pour inclure ou exclure spécifiquement vos appareils gérés par le bureau géré Microsoft. Ces rapports ont intégré cette fonctionnalité de filtrage :

- **Tous les appareils**
- **Conformité des appareils**
- **Appareils non conformes**

> [!NOTE]
> Les rôles de bureau géré Microsoft personnalisés garantissent l’accès uniquement aux rapports de bureau géré Microsoft. Pour accéder à d’autres parties du gestionnaire de points de terminaison Microsoft, telles que **tous les appareils**, consultez la rubrique [contrôle d’accès basé sur un rôle avec Microsoft Intune](https://docs.microsoft.com/mem/intune/fundamentals/role-based-access-control). 

## <a name="reports-in-microsoft-365-admin-center"></a>Rapports dans le centre d’administration Microsoft 365

Vous trouverez des rapports Microsoft Managed Desktop Insights en ouvrant le [Centre d’administration microsoft 365](https://admin.microsoft.com/adminportal/home?previewoff=false#/microsoftmanageddesktop), puis en accédant à **rapports** et en sélectionnant **Microsoft Managed Desktop**. Vous pouvez également suivre le lien direct vers ces rapports à partir de l’onglet **bureau géré Microsoft** de la page d’accueil du [Gestionnaire de points de terminaison Microsoft](https://endpoint.microsoft.com). 

Ces rapports sont les suivants : 

- [Perspectives sur l’utilisation](usage-insights.md) : cette vue fournit des mesures d’utilisation pour vos appareils de bureau gérés par Microsoft.
- [Perspectives de fiabilité](reliability-insights.md) : cette vue vous fournit un résumé de l’intégrité de vos appareils gérés.
- Informations sur la [batterie](battery-insights.md) : cette vue affiche des informations sur la consommation d’énergie des applications et la durée de vie de la batterie pour les périphériques de votre environnement.
- [Perspectives sur la mise à jour de sécurité Windows](security-update-insights.md) : cette vue vous montre des informations sur l’état des mises à jour de sécurité pour vos appareils de bureau gérés par Microsoft.

 ## <a name="inventory-data"></a>Données d’inventaire

Outre les autres rapports, vous pouvez exporter des informations sur les appareils gérés par le bureau géré Microsoft. Dans l’affichage **périphériques** de la zone **périphériques** du gestionnaire de points de terminaison Microsoft, utilisez l’onglet **Exporter tout** pour [Télécharger un rapport d’inventaire détaillé](device-inventory-report.md).