---
title: Vue d’ensemble de la page Conformité de l’appareil dans Microsoft 365 Lighthouse
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
ms.reviewer: ragovind
audience: Admin
ms.topic: article
ms.service: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- Tier1
- scotvorg
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Pour les fournisseurs de services managés (MSP) utilisant Microsoft 365 Lighthouse, découvrez la page Conformité des appareils.
ms.openlocfilehash: e4870db72860a732f08dec998f9e6bb728c30205
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68727672"
---
# <a name="overview-of-the-device-compliance-page-in-microsoft-365-lighthouse"></a>Vue d’ensemble de la page Conformité de l’appareil dans Microsoft 365 Lighthouse

Microsoft 365 Lighthouse vous permet d’afficher des insights et des informations sur Intune conformité des appareils pour tous vos locataires clients en sélectionnant **Appareils** > **Conformité de l’appareil** dans le volet de navigation gauche pour ouvrir la page Conformité de l’appareil. À partir de cette page, vous pouvez obtenir une vue d’ensemble de l’état de conformité entre les locataires, afficher une liste d’appareils pour chaque locataire et obtenir des rapports d’état sur les stratégies et les paramètres de conformité.

## <a name="overview-tab"></a>Onglet Overview  
  
Sous l’onglet Vue d’ensemble, vous pouvez afficher l’état de conformité des appareils dans vos locataires, consulter les tendances de conformité mensuelles des appareils et suivre si des stratégies de conformité sont attribuées aux appareils. Vous pouvez également voir combien de locataires n’ont aucune exigence de conformité d’appareil appliquée à l’aide de stratégies d’accès conditionnel. Vous pouvez sélectionner **Afficher plus** pour afficher plus de détails.

Pour obtenir des informations détaillées sur la conformité des appareils pour un locataire client particulier, sélectionnez une valeur sous l’une des colonnes d’état de ce locataire. L’onglet Appareils s’ouvre afin que vous puissiez afficher les détails de conformité des appareils pour le locataire sélectionné.

Pour exporter des données de conformité d’appareil vers un fichier de valeurs séparées par des virgules (.csv) Excel, sélectionnez **Exporter**.

:::image type="content" source="../media/m365-lighthouse-device-compliance-page-overview/device-overview-tab.png" alt-text="Capture d’écran de l’onglet Vue d’ensemble." lightbox="../media/m365-lighthouse-device-compliance-page-overview/device-overview-tab.png":::

## <a name="devices-tab"></a>Onglet Appareils

Sous l’onglet Appareils, la barre d’annotation de nombre de couleurs affiche le nombre total d’appareils sur tous vos locataires clients qui ont les états de conformité suivants : Conforme, Non conforme, En période de grâce et Non évalué. Pour plus d’informations sur les différents états de conformité, consultez [Surveiller les stratégies de conformité des appareils Intune](/mem/intune/protect/compliance-policy-monitor).

Pour voir quels locataires ont des appareils avec un état de conformité spécifique, sélectionnez cet état dans la barre count-annotation pour filtrer la liste. Pour afficher les états de conformité des appareils pour un ou plusieurs locataires clients spécifiques, utilisez le menu déroulant **Locataires** pour filtrer la liste.

Sélectionnez un nom d’appareil dans la liste pour afficher plus de détails sur l’état de conformité actuel de cet appareil. Vous pouvez synchroniser ou redémarrer l’appareil, ou sélectionner **Afficher l’appareil dans Microsoft Endpoint Manager** si vous devez résoudre les problèmes ou prendre d’autres mesures.

> [!NOTE]
> Lorsque vous redémarrez un appareil, le propriétaire de l’appareil n’est pas automatiquement averti et risque de perdre le travail non enregistré. Pour cette raison, vous pouvez avertir le propriétaire de l’appareil avant de redémarrer un appareil.

L’onglet Appareils inclut également les options suivantes :

- **Exportation:** Sélectionnez cette option pour exporter les données de conformité des appareils vers un fichier de valeurs séparées par des virgules (.csv) Excel.
- **Actualiser:** Sélectionnez cette option pour récupérer les données de conformité des appareils les plus actuelles.
- **Synchronisation:** Sélectionnez un ou plusieurs appareils dans la liste dont l’état est Non conforme, En période de grâce ou Non évalué, puis sélectionnez cette option pour forcer ces appareils à s’enregistrer auprès de Intune et recevoir immédiatement les stratégies qui leur ont été affectées.
- **Redémarrer:** Sélectionnez un ou plusieurs appareils dans la liste dont l’état est Non conforme, En période de grâce ou Non évalué, puis sélectionnez cette option pour redémarrer ces appareils.
- **Rechercher:** Entrez des mots clés pour localiser rapidement un appareil spécifique dans la liste.
 
:::image type="content" source="../media/m365-lighthouse-device-compliance-page-overview/devices-device-tab.png" alt-text="Capture d’écran de l’onglet Appareils." lightbox="../media/m365-lighthouse-device-compliance-page-overview/devices-device-tab.png":::

## <a name="policies-tab"></a>Onglet Stratégies

Sous l’onglet Stratégies, vous pouvez afficher les stratégies de conformité des appareils entre vos locataires et comparer deux ou trois stratégies du même type de plateforme à l’aide de l’option **Comparer** .

Pour afficher les stratégies des appareils sur une plateforme spécifique, utilisez le menu déroulant **du système d’exploitation** pour filtrer la liste. Pour afficher les stratégies d’un ou de plusieurs locataires clients spécifiques, utilisez le menu déroulant **Locataires** pour filtrer la liste.

Sélectionnez un nom de stratégie dans la liste pour afficher plus de détails sur cette stratégie. Si vous devez prendre des mesures ou afficher des informations supplémentaires, sélectionnez **Afficher cette stratégie dans Microsoft Endpoint Manager**.

L’onglet Stratégies inclut également les options suivantes :

- **Exportation:** Sélectionnez cette option pour exporter les données de stratégie de conformité des appareils vers un fichier de valeurs séparées par des virgules (.csv) Excel.
- **Actualiser:** Sélectionnez cette option pour récupérer les données de stratégie de conformité des appareils les plus actuelles.
- **Rechercher:** Entrez des mots clés pour localiser rapidement une stratégie de conformité d’appareil spécifique dans la liste.

:::image type="content" source="../media/m365-lighthouse-device-compliance-page-overview/devices-policies-tab.png" alt-text="Capture d’écran de l’onglet Stratégies." lightbox="../media/m365-lighthouse-device-compliance-page-overview/devices-policies-tab.png":::

## <a name="settings-tab"></a>Onglet Paramètres

L’onglet Paramètres fournit un rapport agrégé des paramètres non conformes sur les appareils clients. 

Pour afficher les paramètres non conformes pour les appareils sur une plateforme spécifique, utilisez le menu déroulant **Plateforme** pour filtrer la liste. Pour afficher les paramètres non conformes pour un ou plusieurs locataires clients spécifiques, utilisez le menu déroulant **Locataires** pour filtrer la liste.

Sélectionnez un nom de paramètre non conforme dans la liste pour ouvrir un volet dans lequel vous pouvez afficher la liste des locataires qui ont des appareils avec ce paramètre spécifique non conforme. À partir de là, vous pouvez explorer davantage en sélectionnant n’importe quel locataire dans la liste pour afficher des informations sur les appareils au sein de ce locataire qui ont le paramètre spécifique non conforme. Vous pouvez également synchroniser ou redémarrer l’appareil, ou sélectionner **Afficher l’appareil dans Microsoft Endpoint Manager** si vous devez résoudre les problèmes ou prendre d’autres mesures.

L’onglet Paramètres inclut également les options suivantes :

- **Exportation:** Sélectionnez cette option pour exporter les données de paramètres non conformes vers un fichier de valeurs séparées par des virgules (.csv) Excel.
- **Actualiser:** Sélectionnez cette option pour récupérer les données de paramètres non conformes les plus actuelles.
- **Rechercher:** Entrez des mots clés pour localiser rapidement un paramètre non conforme spécifique dans la liste.

:::image type="content" source="../media/m365-lighthouse-device-compliance-page-overview/device-settings-tab.png" alt-text="Capture d’écran de l’onglet Paramètres." lightbox="../media/m365-lighthouse-device-compliance-page-overview/device-settings-tab.png":::

## <a name="related-content"></a>Contenu associé

[Vue d’ensemble de la page Windows 365 (PC cloud) dans Microsoft 365 Lighthouse](m365-lighthouse-win365-page-overview.md) (article)\
[FAQ Microsoft 365 Lighthouse](m365-lighthouse-faq.yml) (article)
