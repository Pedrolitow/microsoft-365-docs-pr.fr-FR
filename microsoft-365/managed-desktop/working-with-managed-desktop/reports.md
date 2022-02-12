---
title: Utiliser les rapports
description: Les différents rapports disponibles dans Microsoft Manged Desktop
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: f37a02c8cda29f48f926125f353d5e75410d9ab5
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2022
ms.locfileid: "62765491"
---
# <a name="work-with-reports"></a>Utiliser les rapports

La console Microsoft Endpoint Manager regroupe les rapports de plusieurs produits dans un emplacement unique pour vous aider à surveiller et à examiner les problèmes de configuration et d’appareils de votre organisation Azure AD (« client »).

Microsoft Manged Desktop contient une section dans **le menu Rapports** dans laquelle vous pouvez trouver des rapports spécifiques à Microsoft Manged Desktop gestion des appareils enregistrés. Dans plusieurs emplacements dans Microsoft Endpoint Manager, vous pouvez filtrer les rapports provenant d’autres groupes de produits. Vous pouvez inclure ou exclure des appareils gérés par Microsoft Manged Desktop.

## <a name="microsoft-managed-desktop-reports"></a>Microsoft Manged Desktop rapports

Microsoft Manged Desktop fournit plusieurs rapports et tableaux de bord. Les administrateurs informatiques de votre organisation peuvent utiliser ces rapports et tableaux de bord pour comprendre différents aspects de la population d’appareils. Dans Microsoft Endpoint Manager, accédez à la section Rapports, sous Microsoft Manged Desktop, sélectionnez Appareils gérés.

Dans **l’onglet** Résumé, vous trouverez des mesures rapides sur les mises à jour des périphériques. **Sélectionnez Afficher les détails d’une** mesure pour télécharger des informations supplémentaires pour l’analyse hors connexion, y compris le jeu de données sous-jacent pour la mesure.

Lorsque vous sélectionnez l’onglet **Rapports** , vous voyez les descriptions des rapports détaillés disponibles. Ces rapports sont plus complets et permettent la visualisation et le filtrage des données dans le portail. Vous pouvez également exporter les données sous-jacentes pour l’analyse ou la distribution hors connexion. Les rapports suivants sont disponibles aujourd’hui :

| Rapport | Description |
| ------ | ------ |
| [**Rapport d’état de** l’appareil](device-status-report.md) (*en prévisualisation*) | Ce rapport indique votre utilisation du service Microsoft Manged Desktop en fonction de l’activité et de l’utilisation de l’appareil. |
| **Tendance de l’état de** l’appareil (*en prévisualisation*) | Cela permet de surveiller les tendances de l’état des appareils au cours des 60 derniers jours pour Microsoft Manged Desktop appareils. Les tendances peuvent vous aider à associer l’état de l’appareil à d’autres modifications au fil du temps, par exemple de nouveaux déploiements. |
| [**Windows des mises à jour de sécurité**](security-updates-report.md) (*en prévisualisation*) | Ce rapport montre comment Windows mises à jour de sécurité sont publiées sur Microsoft Manged Desktop appareils. |
| [**Rapport d’utilisation des** applications](app-usage-report.md) | Ce rapport fournit des informations sur l’utilisation classique des applications sur Microsoft Manged Desktop appareils. Pour que les appareils fournissent des données à ce rapport, ils doivent être définies sur le niveau de données de diagnostic facultatif. |
| **Rapport de mesures de service** (*en prévisualisation*) | Ce rapport fournit des résumés simples des mesures clés pour Microsoft Manged Desktop mois. |

## <a name="endpoint-analytics"></a>Analyse des points de terminaison

Microsoft Manged Desktop est désormais intégré à [l’analyse des points de terminaison](/mem/analytics/overview). Ces rapports vous donnent des informations sur la mesure du fonctionnement de votre organisation et de la qualité de l’expérience qu’ils offrent à vos utilisateurs. Vous trouverez l’analyse des points de terminaison dans **le menu Rapports** [de Microsoft Endpoint Manager](https://endpoint.microsoft.com/). Pour faire pivoter un score afin d’inclure uniquement les appareils gérés par Microsoft Manged Desktop, sélectionnez n’importe  quel rapport, sélectionnez la Microsoft Manged Desktop **filtre**.

Si l’analyse des points de terminaison n’a pas été configurée automatiquement pour votre organisation Azure AD (« client ») lors de l’inscription, vous pouvez le faire vous-même. Pour plus d’informations, [voir Intégrer dans le portail d’analyse des points de terminaison](/mem/analytics/enroll-intune#bkmk_onboard). Vous pouvez inscrire tous vos appareils ou, si vous souhaitez inclure uniquement des appareils Microsoft Manged Desktop, sélectionnez les groupes d’appareils  d’espace de travail modernes pour Test, Premier, Rapide et Large. Ces rapports peuvent nécessiter des autorisations différentes. Pour plus d’informations, [voir Autorisations](/mem/analytics/overview#permissions) pour vous assurer que des rôles sont correctement attribués.

> [!NOTE]
> Pour mieux respecter la confidentialité des utilisateurs, il doit y avoir plus de 10 appareils Microsoft Manged Desktop inscrits avec Endpoint Analytics pour utiliser ce filtre.

## <a name="intune-reports"></a>Rapports Intune

Microsoft Intune est l’un des services que nous utilisons pour gérer les appareils en votre nom.

Dans certains cas, il peut être utile d’utiliser les rapports Intune pour surveiller spécifiquement l’administration de Microsoft Manged Desktop appareils mobiles. Vous pouvez exclure les appareils que nous gérons du rapport que vous utilisez pour gérer d’autres appareils. Les rapports suivants vous permet de filtrer la fonctionnalité pour inclure ou exclure Microsoft Manged Desktop appareils.

- [Tous les appareils](/mem/intune/remote-actions/device-management#get-to-your-devices)
- [Conformité des appareils](/mem/intune/fundamentals/reports#device-compliance-report-organizational)
- [Appareils non conformes](/mem/intune/fundamentals/reports#noncompliant-devices-report-operational)

> [!NOTE]
> Les rôles Microsoft Manged Desktop personnalisés garantissent l’accès uniquement aux Microsoft Manged Desktop rapports. Pour accéder à d’autres parties Microsoft Endpoint Manager, telles que tous les **appareils, voir** Contrôle d’accès basé sur [un rôle avec Microsoft Intune](/mem/intune/fundamentals/role-based-access-control).

## <a name="microsoft-managed-desktop-inventory-data"></a>Microsoft Manged Desktop d’inventaire

Outre les autres rapports, vous pouvez exporter des informations sur les appareils gérés par Microsoft Manged Desktop. Dans Microsoft Endpoint Manager, accédez à **la section Appareils**, sous Microsoft Manged Desktop, sélectionnez Appareils et utilisez l’onglet Exporter tout  pour télécharger un rapport d’inventaire [détaillé](device-inventory-report.md).
