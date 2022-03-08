---
title: vue d Microsoft 365 Lighthouse de la page de conformité des appareils
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Pour les fournisseurs de services gérés (MSP) utilisant Microsoft 365 Lighthouse, découvrez la page de conformité des appareils.
ms.openlocfilehash: 76cb914b878b3da8236e91ddda538cb13fa3aa8c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63317596"
---
# <a name="microsoft-365-lighthouse-device-compliance-page-overview"></a>vue d Microsoft 365 Lighthouse de la page de conformité des appareils

Microsoft 365 Lighthouse vous permet d’afficher des informations et des informations relatives à la conformité des appareils Intune pour tous vos clients en sélectionnant Appareils  dans le volet de navigation gauche pour ouvrir la page Conformité de l’appareil. À partir de cette page, vous pouvez obtenir une vue d’ensemble de l’état de conformité entre les locataires, afficher la liste des appareils pour chaque client et obtenir des rapports d’état sur les stratégies et paramètres de conformité.

## <a name="overview-tab"></a>Onglet Overview  
  
Sous l’onglet Vue d’ensemble, vous pouvez afficher l’état de conformité des appareils sur tous vos locataires, consulter les tendances mensuelles de conformité des appareils et déterminer si des stratégies de conformité leur sont affectées sur les appareils. Vous pouvez également voir combien de locataires n’ont aucune exigence de conformité des appareils appliquée à l’aide de stratégies d’accès conditionnel. Vous pouvez sélectionner **Afficher plus pour** afficher plus de détails.

Pour obtenir des informations détaillées sur la conformité des appareils pour un client particulier, sélectionnez une valeur sous l’une des colonnes d’état de ce client. Cela ouvre l’onglet Appareils afin que vous pouvez afficher les détails de conformité de l’appareil pour le client sélectionné.

Pour exporter les données de conformité de l’appareil vers Excel fichier de valeurs séparées par des virgules (.csv), sélectionnez **Exporter**.

:::image type="content" source="../media/m365-lighthouse-device-compliance-page-overview/device-overview-tab.png" alt-text="Capture d’écran de l’onglet Vue d’ensemble." lightbox="../media/m365-lighthouse-device-compliance-page-overview/device-overview-tab.png":::

## <a name="devices-tab"></a>Onglet Appareils

Sous l’onglet Appareils, la barre de nombre d’annotations couleur affiche le nombre total d’appareils sur tous les clients qui ont les statuts de conformité suivants : Conforme, Non conforme, En période de grâce et Non évalué. Pour plus d’informations sur les différents statuts de conformité, voir Surveiller les stratégies de conformité des [appareils Intune](/mem/intune/protect/compliance-policy-monitor).

Pour voir quels locataires ont des appareils avec un état de conformité spécifique, sélectionnez cet état dans la barre d’annotations de nombre pour filtrer la liste. Pour voir les statuts de conformité des appareils pour un ou plusieurs clients spécifiques,  utilisez le menu déroulant Clients pour filtrer la liste.

Sélectionnez n’importe quel nom d’appareil dans la liste pour afficher plus de détails sur l’état de conformité actuel de cet appareil. Vous pouvez synchroniser ou redémarrer l’appareil, ou sélectionner Afficher l’appareil **dans Microsoft Endpoint Manager** si vous devez résoudre des problèmes ou prendre des mesures supplémentaires.

> [!NOTE]
> Lorsque vous redémarrez un appareil, le propriétaire de l’appareil n’est pas averti automatiquement et risque de perdre du travail non notifié. Pour cette raison, vous pouvez avertir le propriétaire de l’appareil avant de redémarrer un appareil.

L’onglet Appareils inclut également les options suivantes :

- **Exporter :** Sélectionnez cette sélection pour exporter les données de conformité des appareils vers Excel fichier de valeurs séparées par des virgules (.csv).
- **Actualiser :** Sélectionnez cette sélection pour récupérer les données de conformité des appareils les plus récentes.
- **Synchronisez :** Sélectionnez dans la liste un ou plusieurs appareils dont l’état est Non conforme, En période de grâce ou Non évalué, puis sélectionnez cette option pour forcer ces appareils à s’enregistrer auprès d’Intune et à recevoir immédiatement les stratégies qui leur ont été attribuées.
- **Redémarrez :** Sélectionnez dans la liste un ou plusieurs appareils dont l’état est Non conforme, En période de grâce ou Non évalué, puis sélectionnez cette option pour redémarrer ces appareils.
- **Recherche :** Entrez des mots clés pour localiser rapidement un appareil spécifique dans la liste.
 
:::image type="content" source="../media/m365-lighthouse-device-compliance-page-overview/devices-device-tab.png" alt-text="Capture d’écran de l’onglet Appareils." lightbox="../media/m365-lighthouse-device-compliance-page-overview/devices-device-tab.png":::

## <a name="policies-tab"></a>Onglet Stratégies

Sous l’onglet Stratégies, vous pouvez afficher les stratégies de conformité des appareils sur vos locataires et comparer deux ou trois stratégies du même type de plateforme à l’aide de l’option **Comparer** .

Pour voir les stratégies pour les appareils sur une plateforme spécifique, utilisez le menu déroulant du système d’exploitation pour filtrer la liste. Pour voir les stratégies d’un ou de plusieurs clients spécifiques, utilisez le menu déroulant Clients pour filtrer la liste.

Sélectionnez n’importe quel nom de stratégie dans la liste pour afficher plus de détails sur cette stratégie. Si vous devez prendre des mesures ou afficher des informations supplémentaires, **sélectionnez Afficher cette stratégie dans Microsoft Endpoint Manager**.

L’onglet Stratégies inclut également les options suivantes :

- **Exporter :** Choisissez d’exporter les données de stratégie de conformité des appareils vers Excel fichier de valeurs séparées par des virgules (.csv).
- **Actualiser :** Sélectionnez pour récupérer les données de stratégie de conformité des appareils les plus récentes.
- **Recherche :** Entrez des mots clés pour localiser rapidement une stratégie de conformité d’appareil spécifique dans la liste.

:::image type="content" source="../media/m365-lighthouse-device-compliance-page-overview/devices-policies-tab.png" alt-text="Capture d’écran de l’onglet Stratégies." lightbox="../media/m365-lighthouse-device-compliance-page-overview/devices-policies-tab.png":::

## <a name="settings-tab"></a>Paramètres’onglet

L’onglet Paramètres fournit un rapport agrégé des paramètres non conformes sur les appareils des locataires. 

Pour voir les paramètres non conformes pour les appareils sur une plateforme spécifique,  utilisez le menu déroulant Plateforme pour filtrer la liste. Pour voir les paramètres non conformes pour un ou plusieurs clients spécifiques, utilisez le  menu déroulant Clients pour filtrer la liste.

Sélectionnez n’importe quel nom de paramètre non conforme dans la liste pour ouvrir un volet dans lequel vous pouvez afficher la liste des locataires qui ont des appareils avec ce paramètre non conforme spécifique. À partir de là, vous pouvez aller plus loin en sélectionnant n’importe quel client dans la liste pour afficher des informations sur les appareils au sein de ce client qui ont le paramètre non conforme spécifique. Vous pouvez également synchroniser ou redémarrer l’appareil, ou sélectionner Afficher l’appareil **dans Microsoft Endpoint Manager** si vous devez résoudre des problèmes ou prendre des mesures supplémentaires.

L’onglet Paramètres inclut également les options suivantes :

- **Exporter :** Choisissez d’exporter les données de paramètres non conformes vers un Excel valeurs séparées par des virgules (.csv).
- **Actualiser :** Sélectionnez pour récupérer les données de paramètres non conformes les plus récentes.
- **Recherche :** Entrez des mots clés pour localiser rapidement un paramètre non conforme spécifique dans la liste.

:::image type="content" source="../media/m365-lighthouse-device-compliance-page-overview/device-settings-tab.png" alt-text="Capture d’écran de Paramètres’onglet." lightbox="../media/m365-lighthouse-device-compliance-page-overview/device-settings-tab.png":::

## <a name="related-content"></a>Contenu associé

[Windows page 365 (Pc cloud) vue](m365-lighthouse-win365-page-overview.md) d’ensemble (article)\
[Microsoft 365 Lighthouse FAQ](m365-lighthouse-faq.yml) (article)
