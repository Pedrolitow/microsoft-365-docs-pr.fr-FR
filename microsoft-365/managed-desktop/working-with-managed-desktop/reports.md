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
ms.openlocfilehash: a80616b58298ba544b9eab1d19ffb77f0e6825d4
ms.sourcegitcommit: 7ecd10b302b3b3dfa4ba3be3a6986dd3c189fbff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/21/2021
ms.locfileid: "49921349"
---
# <a name="work-with-reports"></a>Utiliser les rapports

Bureau géré Microsoft fournit plusieurs rapports et tableaux de bord que les administrateurs informatiques de votre organisation peuvent utiliser pour comprendre différents aspects de la population d’appareils.Vous trouverez des rapports à deux emplacements : dans [Microsoft Endpoint Manager](https://endpoint.microsoft.com) et dans le Centre d’administration [Microsoft 365.](https://admin.microsoft.com/adminportal/home?previewoff=false#/microsoftmanageddesktop) 

## <a name="reports-in-microsoft-endpoint-manager"></a>Rapports dans Microsoft Endpoint Manager

La console Microsoft Endpoint Manager regroupe les rapports de plusieurs produits dans un emplacement unique pour vous aider à surveiller et à examiner les problèmes de configuration et d’appareils de votre organisation Azure AD (« client »). Bureau géré Microsoft comprend une section sous **Rapports** dans le menu principal où vous trouverez des rapports spécifiques à la gestion par Microsoft Managed Desktop des appareils que vous avez enregistrés.

Ces rapports sont les suivants :
- **Appareils gérés**  >  **Mises à jour de fonctionnalités**: cet affichage affiche l’état global des mises à jour de fonctionnalités sur vos appareils de bureau géré Microsoft.
- **Appareils gérés**  >  **Mises à jour Office**: cet affichage affiche l’état global des mises à jour d’Office sur vos appareils de bureau géré Microsoft.

En outre, dans plusieurs emplacements de Microsoft Endpoint Manager, vous pouvez filtrer les rapports provenant d’autres groupes de produits afin d’inclure ou d’exclure spécifiquement vos appareils gérés par Bureau géré Microsoft. Ces rapports ont intégré cette fonctionnalité de filtrage :

- [Tous les appareils](https://docs.microsoft.com/mem/intune/remote-actions/device-management#get-to-your-devices)
- [Conformité des appareils](https://docs.microsoft.com/mem/intune/fundamentals/reports#device-compliance-report-organizational)
- [Appareils non conformes](https://docs.microsoft.com/mem/intune/fundamentals/reports#noncompliant-devices-report-operational)

> [!NOTE]
> Les rôles Bureau géré Microsoft personnalisés garantissent l’accès uniquement aux rapports Bureau géré Microsoft. Pour accéder à d’autres parties de Microsoft Endpoint Manager, telles que tous les **appareils,** voir Contrôle d’accès basé sur un rôle [avec Microsoft Intune](https://docs.microsoft.com/mem/intune/fundamentals/role-based-access-control). 

## <a name="reports-in-microsoft-365-admin-center"></a>Rapports dans le Centre d’administration Microsoft 365

Vous pouvez trouver des rapports d’informations sur le Bureau géré Microsoft en  ouvrant le Centre d’administration [Microsoft 365,](https://admin.microsoft.com/adminportal/home?previewoff=false#/microsoftmanageddesktop)puis en naviguant vers rapports et en sélectionnant **Bureau géré Microsoft.** Vous pouvez également suivre le lien direct vers ces rapports à partir de **l’onglet Bureau** géré Microsoft sur la page d’accueil [Microsoft Endpoint Manager](https://endpoint.microsoft.com). 

Ces rapports sont les suivants : 

- [Informations sur l’utilisation](usage-insights.md) : cet affichage fournit des mesures d’utilisation pour vos appareils bureau géré Microsoft.
- [Informations de fiabilité](reliability-insights.md) : cet affichage vous fournit un résumé d’état de vos appareils gérés.
- [Informations sur la batterie](battery-insights.md) : cet affichage vous présente des informations sur la consommation d’énergie des applications et l’autonomie de la batterie projetée pour les appareils de votre environnement.
- [Informations sur les mises à](security-update-insights.md) jour de sécurité Windows : cet affichage affiche des informations sur l’état des mises à jour de sécurité pour vos appareils bureau géré Microsoft.

 ## <a name="inventory-data"></a>Données d’inventaire

Outre les autres rapports, vous pouvez exporter des informations sur les appareils gérés par Bureau géré Microsoft. Dans la vue **Appareils** de la zone **Appareils**  de Microsoft Endpoint Manager, utilisez l’onglet Exporter tout pour télécharger un [rapport d’inventaire détaillé.](device-inventory-report.md)
