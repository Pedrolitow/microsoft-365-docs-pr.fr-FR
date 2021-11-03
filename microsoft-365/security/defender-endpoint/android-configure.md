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
ms.openlocfilehash: 53eed34cfff6d2318b87e781b32a9963c372b279
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2021
ms.locfileid: "60667385"
---
# <a name="configure-defender-for-endpoint-on-android-features"></a>Configurer Defender pour le point de terminaison sur les fonctionnalités Android

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

## <a name="conditional-access-with-defender-for-endpoint-on-android"></a>Accès conditionnel avec Defender pour point de terminaison sur Android

Microsoft Defender pour le point de terminaison sur Android, ainsi que Microsoft Intune et Azure Active Directory permet d’appliquer des stratégies de conformité et d’accès conditionnel aux appareils en fonction des niveaux de risque de l’appareil. Defender pour point de terminaison est une solution de défense contre les menaces mobiles que vous pouvez déployer pour tirer parti de cette fonctionnalité via Intune.

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


## <a name="configure-vulnerability-assessment-of-apps-for-byod-devices"></a>Configurer l’évaluation des vulnérabilités des applications pour les appareils BYOD

À partir de la version 1.0.3425.0303 de Microsoft Defender pour Endpoint sur Android, nous avons la possibilité d’exécuter une évaluation de vulnérabilité du système d’exploitation et des applications installées sur les appareils mobiles intégrés.

> [!NOTE]
> L’évaluation des vulnérabilités fait partie de [la gestion](next-gen-threat-and-vuln-mgt.md) des menaces et des vulnérabilités dans Microsoft Defender pour point de terminaison. Sur Android, cette fonctionnalité est actuellement en prévisualisation et peut être considérablement modifiée avant sa publication commerciale.

**Remarques sur la confidentialité liée aux applications à partir d’appareils personnels (BYOD) :**

- Pour les Enterprise Android avec un profil de travail, seules les applications installées sur le profil de travail seront pris en charge.
- Pour les autres modes BYOD, par défaut, l’évaluation des vulnérabilités des applications **n’est** pas activée. Toutefois, lorsque l’appareil est en mode administrateur, les administrateurs peuvent activer explicitement cette fonctionnalité via Microsoft Endpoint Manager pour obtenir la liste des applications installées sur l’appareil. Consultez la documentation pour en savoir plus.

### <a name="configure-privacy-for-device-administrator-mode"></a>Configurer la confidentialité pour le mode administrateur d’appareil

Utilisez les étapes suivantes pour activer l’évaluation des **vulnérabilités** des applications à partir d’appareils  en mode administrateur d’appareil pour les utilisateurs ciblés. 

> [!NOTE]
> Par défaut, cette option est désactivée pour les appareils inscrits avec le mode d’administration des appareils.

1. Dans [Microsoft Endpoint Manager centre d’administration,](https://go.microsoft.com/fwlink/?linkid=2109431) allez **sur** Profils de configuration des appareils Créer un profil  >    >   et entrez les paramètres suivants :

   - **Plateforme :** sélectionner un administrateur d’appareil Android
   - **Profil**: sélectionnez « Personnalisé », puis cliquez sur Créer

2. Dans la section **Informations de** base, spécifiez un nom et une description du profil.

3. Dans les **paramètres de configuration,** sélectionnez Ajouter un **paramètre OMA-URI** :

   - **Nom**: entrez un nom et une description uniques pour ce paramètre OMA-URI afin de le trouver facilement plus tard.
   - OMA-URI : **./Vendor/MSFT/DefenderATP/DefenderTVMPrivacyMode**
   - Type de données : sélectionnez Integer dans la liste liste.
   - Valeur : entrez 0 pour désactiver le paramètre de confidentialité (par défaut, la valeur est 1)

4. Cliquez **sur Suivant** et affectez ce profil à des appareils/utilisateurs ciblés.

### <a name="configure-privacy-for-android-enterprise-work-profile"></a>Configurer la confidentialité pour le profil Enterprise Travail Android

Defender pour le point de terminaison prend en charge l’évaluation des vulnérabilités des applications dans le profil de travail. Toutefois, si vous souhaitez désactiver cette fonctionnalité pour des utilisateurs ciblés, vous pouvez suivre les étapes suivantes :

1. In [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and go to **Apps** App  >  **configuration policies**  >  **Add** Managed  >  **devices**.
2. Donnez un nom à la stratégie ; **Plateforme > android Enterprise**; sélectionnez le type de profil.
3. Sélectionnez **Microsoft Defender pour le point de terminaison** comme application cible.
4. Dans Paramètres page, sélectionnez Utiliser le concepteur de **configuration** et ajoutez **DefenderTVMPrivacyMode** comme clé et type de valeur sous la forme **Integer**
   - Pour désactiver la vulnérabilité des applications dans le profil de travail, entrez la valeur 1 et affectez cette stratégie aux utilisateurs. Par défaut, cette valeur est définie sur 0.
   - Pour les utilisateurs dont la clé est définie sur « 0 » ( 0), Defender envoie la liste des applications du profil de travail au service principal pour l’évaluation des vulnérabilités.
5. Cliquez **sur Suivant** et affectez ce profil à des appareils/utilisateurs ciblés.

La mise en place ou la mise hors fonction des contrôles de confidentialité ci-dessus n’aura pas d’impact sur la vérification de la conformité de l’appareil ou l’accès conditionnel.


## <a name="configure-privacy-for-malware-threat-report"></a>Configurer la confidentialité du rapport sur les menaces de programmes malveillants

> [!NOTE]
> Les contrôles de confidentialité de Defender pour Endpoint sur Android sont actuellement en prévisualisation et peuvent être considérablement modifiés avant sa publication commerciale.

Le contrôle de confidentialité du rapport sur les menaces de programmes malveillants peut être utilisé pour désactiver la collecte des détails de l’application (informations sur le nom et le package) du rapport sur les menaces de programmes malveillants. Cela donne aux organisations la possibilité de choisir s’ils souhaitent collecter le nom de l’application lorsqu’une application malveillante est détectée. *Cette fonctionnalité est actuellement disponible uniquement pour les appareils inscrits en mode **Administrateur d’appareil Android.***

Utilisez les étapes suivantes pour l’activer pour les utilisateurs ciblés :

1. Dans [Microsoft Endpoint Manager centre d’administration,](https://go.microsoft.com/fwlink/?linkid=2109431) allez **sur** Profils de configuration des appareils Créer un profil  >    >   et entrez les paramètres suivants :

   - **Plateforme :** sélectionner un administrateur d’appareil Android
   - **Profil**: sélectionnez « Personnalisé », puis cliquez sur Créer

2. Dans la section **Informations de** base, spécifiez un nom et une description du profil.

3. Dans les **paramètres de configuration,** sélectionnez Ajouter un **paramètre OMA-URI** :

   - **Nom**: entrez un nom et une description uniques pour ce paramètre OMA-URI afin de le trouver facilement plus tard.
   - OMA-URI : **./Vendor/MSFT/DefenderATP/DefenderExcludeAppInReport**
   - Type de données : sélectionnez Integer dans la liste liste.
   - Valeur : Entrez 1 pour activer le paramètre de confidentialité (par défaut, la valeur est 0)

4. Cliquez **sur Suivant** et affectez ce profil à des appareils/utilisateurs ciblés.

L’utilisation de ce contrôle de confidentialité n’aura pas d’impact sur la vérification de la conformité de l’appareil ou l’accès conditionnel. Par exemple, les appareils avec une application malveillante auront toujours un niveau de risque « Moyen ».

## <a name="related-topics"></a>Rubriques connexes

- [Vue d’ensemble de Microsoft Defender pour point de terminaison Android](microsoft-defender-endpoint-android.md)
- [Déployer Microsoft Defender pour point de terminaison Android via Microsoft Intune](android-intune.md)
