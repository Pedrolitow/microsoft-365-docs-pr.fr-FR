---
title: Configurer Microsoft Defender pour point de terminaison pour des fonctionnalités Android
description: Décrit comment configurer Microsoft Defender pour endpoint sur Android
keywords: microsoft, defender, Microsoft Defender pour le point de terminaison, mde, android, configuration
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 4db57a39d6270608a5107a77f41ce11fdd139c78
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60186631"
---
# <a name="configure-defender-for-endpoint-on-android-features"></a>Configurer Defender pour le point de terminaison sur les fonctionnalités Android

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

## <a name="conditional-access-with-defender-for-endpoint-on-android"></a>Accès conditionnel avec Defender pour point de terminaison sur Android

Microsoft Defender pour le point de terminaison sur Android, ainsi que Microsoft Intune et Azure Active Directory permet d’appliquer la conformité des appareils et des stratégies d’accès conditionnel en fonction des niveaux de risque de l’appareil. Defender pour point de terminaison est une solution de défense contre les menaces mobiles (MTD) que vous pouvez déployer pour tirer parti de cette fonctionnalité via Intune.

Pour plus d’informations sur la façon de configurer Defender pour Endpoint sur Android et l’accès conditionnel, voir [Defender pour Endpoint et Intune.](/mem/intune/protect/advanced-threat-protection)

## <a name="configure-custom-indicators"></a>Configurer des indicateurs personnalisés

> [!NOTE]
> Defender pour le point de terminaison sur Android prend uniquement en charge la création d’indicateurs personnalisés pour les adresses IP et les URL/domaines.

Defender pour le point de terminaison sur Android permet aux administrateurs de configurer des indicateurs personnalisés pour prendre en charge également les appareils Android. Pour plus d’informations sur la configuration des indicateurs personnalisés, voir [Gérer les indicateurs.](manage-indicators.md)

## <a name="configure-web-protection"></a>Configurer la protection web
Defender pour le point de terminaison sur Android permet aux administrateurs informatiques de configurer la fonctionnalité de protection web. Cette fonctionnalité est disponible dans le centre d Microsoft Endpoint Manager’administration.

> [!NOTE]
> Defender pour le point de terminaison sur Android utiliserait un VPN pour fournir la fonctionnalité de protection web. Il ne s’agit pas d’un VPN normal et d’un VPN local/en boucle autonome qui ne prend pas le trafic en dehors de l’appareil.
> Pour plus d’informations, voir [Configurer la protection web sur les appareils qui exécutent Android.](/mem/intune/protect/advanced-threat-protection-manage-android)

## <a name="configure-privacy-for-malware-threat-report"></a>Configurer la confidentialité du rapport sur les menaces de programmes malveillants

> [!NOTE]
> Les contrôles de confidentialité de Defender pour Endpoint sur Android sont actuellement en prévisualisation et peuvent être considérablement modifiés avant sa publication commerciale.

Le contrôle de confidentialité du rapport sur les menaces de programmes malveillants peut être utilisé pour désactiver la collecte des détails de l’application (informations sur le nom et le package) du rapport sur les menaces de programmes malveillants. Cela donne aux organisations la possibilité de choisir s’ils souhaitent collecter le nom de l’application lorsqu’une application malveillante est détectée. *Cette fonctionnalité est actuellement disponible uniquement pour les appareils inscrits en mode **Administrateur d’appareil Android.***

Pour l’activer pour des utilisateurs ciblés, utilisez les étapes suivantes :

1. Dans [Microsoft Endpoint Manager d’administration,](https://go.microsoft.com/fwlink/?linkid=2109431) allez **sur** Profils de configuration des appareils Créer un profil et entrez les  >    >   paramètres suivants :

   - **Plateforme :** sélectionner un administrateur d’appareil Android
   - **Profil**: sélectionnez « Personnalisé », puis cliquez sur Créer

2. Dans la section Informations de base, spécifiez un nom et une description du profil.
3. Dans les paramètres de configuration, sélectionnez Ajouter un **paramètre OMA-URI** :

   - **Nom**: entrez un nom et une description uniques pour ce paramètre OMA-URI afin de le trouver facilement plus tard.
   - OMA-URI : **./Vendor/MSFT/DefenderATP/DefenderExcludeAppInReport**
   - Type de données : sélectionnez Integer dans la liste liste.
   - Valeur : Entrez 1 pour activer le paramètre de confidentialité (par défaut, la valeur est 0)

4. Cliquez **sur Suivant** et affectez ce profil à des appareils/utilisateurs ciblés.

L’activation du contrôle de confidentialité ci-dessus n’aura pas d’impact sur la vérification de la conformité de l’appareil ou l’accès conditionnel, par exemple, les appareils avec une application malveillante auront toujours un niveau de risque « Moyen ».

## <a name="related-topics"></a>Rubriques connexes

- [Vue d’ensemble de Microsoft Defender pour point de terminaison Android](microsoft-defender-endpoint-android.md)
- [Déployer Microsoft Defender pour point de terminaison Android via Microsoft Intune](android-intune.md)
