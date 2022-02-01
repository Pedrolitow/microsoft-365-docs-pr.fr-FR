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
ms.openlocfilehash: 92a927bf0cb3a5e568ca2b02d60d641907bc0407
ms.sourcegitcommit: 7fd1bcbd8246501029837e3ea92adea64c3406e1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2022
ms.locfileid: "62295385"
---
# <a name="configure-defender-for-endpoint-on-android-features"></a>Configurer Defender pour le point de terminaison sur les fonctionnalités Android

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

## <a name="conditional-access-with-defender-for-endpoint-on-android"></a>Accès conditionnel avec Defender pour point de terminaison sur Android

Microsoft Defender pour le point de terminaison sur Android, ainsi que Microsoft Intune et Azure Active Directory permet d’appliquer des stratégies de conformité et d’accès conditionnel aux appareils en fonction des niveaux de risque de l’appareil. Defender pour point de terminaison est une solution de défense contre les menaces mobiles que vous pouvez déployer pour tirer parti de cette fonctionnalité via Intune.

Pour plus d’informations sur la façon de configurer Defender pour Endpoint sur Android et l’accès conditionnel, voir [Defender pour Endpoint et Intune](/mem/intune/protect/advanced-threat-protection).

## <a name="configure-custom-indicators"></a>Configurer des indicateurs personnalisés

> [!NOTE]
> Defender pour le point de terminaison sur Android prend uniquement en charge la création d’indicateurs personnalisés pour les adresses IP et les URL/domaines.

Defender pour le point de terminaison sur Android permet aux administrateurs de configurer des indicateurs personnalisés pour prendre en charge également les appareils Android. Pour plus d’informations sur la configuration des indicateurs personnalisés, voir [Gérer les indicateurs](manage-indicators.md).

## <a name="configure-web-protection"></a>Configurer la protection web
Defender pour le point de terminaison sur Android permet aux administrateurs informatiques de configurer la fonctionnalité de protection web. Cette fonctionnalité est disponible dans le centre d Microsoft Endpoint Manager’administration.

> [!NOTE]
> Defender pour le point de terminaison sur Android utiliserait un VPN pour fournir la fonctionnalité de protection web. Il ne s’agit pas d’un VPN normal et d’un VPN local/en boucle autonome qui ne prend pas le trafic en dehors de l’appareil.
> Pour plus d’informations, voir [Configurer la protection web sur les appareils qui exécutent Android](/mem/intune/protect/advanced-threat-protection-manage-android).

## <a name="privacy-controls"></a>Contrôles de confidentialité

> [!IMPORTANT]
> Les contrôles de confidentialité pour Microsoft Defender pour point de terminaison sur Android sont en prévisualisation. Les informations suivantes concernent les produits pré-publiés qui peuvent être considérablement modifiés avant leur commercialisation. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

Les contrôles de confidentialité suivants sont disponibles pour configurer les données envoyées par Defender pour Endpoint à partir d’appareils Android :

|Rapport sur les menaces     |Détails      |
|--------------------|-------------|
|Rapport sur les programmes malveillants |Les administrateurs peuvent configurer le contrôle de confidentialité pour le rapport sur les programmes malveillants : si la confidentialité est activée, Defender pour le point de terminaison n’enverra pas le nom de l’application anti-programme malveillant et d’autres détails de l’application dans le cadre du rapport d’alerte anti-programme malveillant |
|Rapport d’hameçonnage |Les administrateurs peuvent configurer le contrôle de confidentialité pour le rapport d’hameçonnage : si la confidentialité est activée, Defender pour le point de terminaison n’enverra pas le nom de domaine et les détails du site web non sécurisé dans le cadre du rapport d’alerte de hameçonnage |
|Évaluation des vulnérabilités des applications (Android uniquement) |Par défaut, seules les informations sur les applications installées dans le profil de travail sont envoyées pour l’évaluation des vulnérabilités. Les administrateurs peuvent désactiver la confidentialité pour inclure des applications personnelles|

## <a name="configure-vulnerability-assessment-of-apps-for-byod-devices"></a>Configurer l’évaluation des vulnérabilités des applications pour les appareils BYOD

À partir de la version 1.0.3425.0303 de Microsoft Defender pour Endpoint sur Android, vous pourrez exécuter des évaluations des vulnérabilités du système d’exploitation et des applications installées sur les appareils mobiles intégrés.

**Remarques sur la confidentialité liée aux applications à partir d’appareils personnels (BYOD) :**

- Pour les Enterprise Android avec un profil de travail, seules les applications installées sur le profil de travail seront pris en charge.
- Pour les autres modes BYOD, par défaut, l’évaluation des vulnérabilités des applications ne **sera** pas activée. Toutefois, lorsque l’appareil est en mode administrateur, les administrateurs peuvent activer explicitement cette fonctionnalité via Microsoft Endpoint Manager pour obtenir la liste des applications installées sur l’appareil. Pour plus d’informations, voir les détails ci-dessous.

### <a name="configure-privacy-for-device-administrator-mode"></a>Configurer la confidentialité pour le mode administrateur d’appareil

Utilisez les étapes suivantes pour **activer l’évaluation des vulnérabilités des applications** à partir d’appareils **en** mode administrateur d’appareil pour les utilisateurs ciblés. 

> [!NOTE]
> Par défaut, cette option est désactivée pour les appareils inscrits avec le mode d’administration des appareils.

1. Dans [Microsoft Endpoint Manager d’administration](https://go.microsoft.com/fwlink/?linkid=2109431), go to **DevicesConfiguration** >  **profilesCreate** >  profile and enter the following settings:

   - **Plateforme :** sélectionner un administrateur d’appareil Android
   - **Profil** : sélectionnez « Personnalisé », puis cliquez sur Créer

2. Dans la section **Informations de** base, spécifiez un nom et une description du profil.

3. Dans les **paramètres de configuration**, sélectionnez Ajouter un **paramètre OMA-URI** :

   - **Nom** : entrez un nom et une description uniques pour ce paramètre OMA-URI afin de le trouver facilement plus tard.
   - OMA-URI : **./Vendor/MSFT/DefenderATP/DefenderTVMPrivacyMode**
   - Type de données : sélectionnez Entier dans la liste déroulante.
   - Valeur : entrez 0 pour désactiver le paramètre de confidentialité (par défaut, la valeur est 1)

4. Cliquez **sur Suivant** et affectez ce profil à des appareils/utilisateurs ciblés.

### <a name="configure-privacy-for-android-enterprise-work-profile"></a>Configurer la confidentialité pour le profil Enterprise travail Android

Defender pour le point de terminaison prend en charge l’évaluation des vulnérabilités des applications dans le profil de travail. Toutefois, si vous souhaitez désactiver cette fonctionnalité pour des utilisateurs ciblés, vous pouvez suivre les étapes suivantes :

1. In [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and go to **AppsApp** >  **configuration** **policiesAddManaged** >  >  **devices**.
2. Donnez un nom à la stratégie ; **Plateforme >'Enterprise Android** ; sélectionnez le type de profil.
3. **Sélectionnez Microsoft Defender pour le point de terminaison** comme application cible.
4. Dans Paramètres page, sélectionnez Utiliser le concepteur de **configuration** et ajoutez **DefenderTVMPrivacyMode** comme clé et type de valeur sous la forme **Integer**
   - Pour désactiver la vulnérabilité des applications dans le profil de travail, entrez la valeur sous `1` et affectez cette stratégie aux utilisateurs. Par défaut, cette valeur est définie sur `0`.
   - Pour les utilisateurs dont la `0`clé est définie comme , Defender pour point de terminaison envoie la liste des applications du profil de travail au service principal pour l’évaluation des vulnérabilités.
5. Cliquez **sur Suivant** et affectez ce profil à des appareils/utilisateurs ciblés.

La mise en place ou la mise hors fonction des contrôles de confidentialité ci-dessus n’aura pas d’impact sur la vérification de la conformité de l’appareil ou l’accès conditionnel.

## <a name="configure-privacy-for-phishing-alert-report"></a>Configurer la confidentialité pour le rapport d’alerte de hameçonnage

Le contrôle de confidentialité du rapport d’hameçonnage peut être utilisé pour désactiver la collecte des informations de nom de domaine ou de site web dans le rapport de menaces de hameçonnage. Cela donne aux organisations la possibilité de choisir s’ils souhaitent collecter le nom de domaine lorsqu’un site web malveillant ou de hameçonnage est détecté et bloqué par Defender for Endpoint.

### <a name="configure-privacy-for-phishing-alert-report-on-android-device-administrator-enrolled-devices"></a>Configurez la confidentialité du rapport d’alerte de hameçonnage sur les appareils inscrits à l’administrateur d’appareil Android :

Utilisez les étapes suivantes pour l’activer pour les utilisateurs ciblés :

1. Dans [Microsoft Endpoint Manager d’administration](https://go.microsoft.com/fwlink/?linkid=2109431), go to **DevicesConfiguration** >  **profilesCreate** >  profile and enter the following settings:

   - **Plateforme :** sélectionnez l’administrateur d’appareil Android.
   - **Profil** : sélectionnez « Personnalisé », puis cliquez sur **Créer**.

2. Dans la section **Informations de** base, spécifiez un nom et une description du profil.

3. Dans les **paramètres de configuration**, sélectionnez Ajouter un **paramètre OMA-URI** :

   - **Nom** : entrez un nom et une description uniques pour ce paramètre OMA-URI afin de le trouver facilement plus tard.
   - OMA-URI : **./Vendor/MSFT/DefenderATP/DefenderExcludeURLInReport**
   - Type de données : sélectionnez Entier dans la liste déroulante.
   - Valeur : Entrez 1 pour activer le paramètre de confidentialité. La valeur par défaut est 0.

4. Cliquez **sur Suivant** et affectez ce profil à des appareils/utilisateurs ciblés.

L’utilisation de ce contrôle de confidentialité n’aura pas d’impact sur la vérification de la conformité de l’appareil ou l’accès conditionnel.

### <a name="configure-privacy-for-phishing-alert-report-on-android-enterprise-work-profile"></a>Configurer la confidentialité pour le rapport d’alerte de hameçonnage sur Enterprise profil de travail Android

Pour activer la confidentialité des utilisateurs ciblés dans le profil de travail, utilisez les étapes suivantes :

1. In [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and go to **AppsApp** >  **configuration** **policiesAddManaged** >  >  **devices**.
2. Nommez la stratégie, **> android Enterprise**, sélectionnez le type de profil.
3. **Sélectionnez Microsoft Defender pour le point de terminaison** comme application cible.
4. Dans Paramètres page, sélectionnez Utiliser le concepteur de **configuration** et ajoutez **DefenderExcludeURLInReport** comme clé et type de valeur sous la forme **Integer**.
   - Entrez **1 pour activer la confidentialité**. La valeur par défaut est 0.
5. Cliquez **sur Suivant** et affectez ce profil à des appareils/utilisateurs ciblés.

La mise en place ou la mise hors fonction des contrôles de confidentialité ci-dessus n’aura pas d’impact sur la vérification de la conformité de l’appareil ou l’accès conditionnel.

## <a name="configure-privacy-for-malware-threat-report"></a>Configurer la confidentialité du rapport sur les menaces de programmes malveillants

Le contrôle de confidentialité du rapport sur les menaces de programmes malveillants peut être utilisé pour désactiver la collecte des détails de l’application (informations sur le nom et le package) du rapport sur les menaces de programmes malveillants. Cela donne aux organisations la possibilité de choisir s’ils souhaitent collecter le nom de l’application lorsqu’une application malveillante est détectée.

### <a name="configure-privacy-for-malware-alert-report-on-android-device-administrator-enrolled-devices"></a>Configurez la confidentialité du rapport d’alerte anti-programme malveillant sur les appareils inscrits à l’administrateur d’appareil Android :

Utilisez les étapes suivantes pour l’activer pour les utilisateurs ciblés :

1. Dans [Microsoft Endpoint Manager d’administration](https://go.microsoft.com/fwlink/?linkid=2109431), go to **DevicesConfiguration** >  **profilesCreate** >  profile and enter the following settings:

   - **Plateforme :** sélectionnez l’administrateur d’appareil Android.
   - **Profil** : sélectionnez « Personnalisé », puis cliquez sur **Créer**.

2. Dans la section **Informations de** base, spécifiez un nom et une description du profil.

3. Dans les **paramètres de configuration**, sélectionnez Ajouter un **paramètre OMA-URI** :

   - **Nom** : entrez un nom et une description uniques pour ce paramètre OMA-URI afin de le trouver facilement plus tard.
   - OMA-URI : **./Vendor/MSFT/DefenderATP/DefenderExcludeAppInReport**
   - Type de données : sélectionnez Entier dans la liste déroulante.
   - Valeur : Entrez 1 pour activer le paramètre de confidentialité. La valeur par défaut est 0.

4. Cliquez **sur Suivant** et affectez ce profil à des appareils/utilisateurs ciblés.

L’utilisation de ce contrôle de confidentialité n’aura pas d’impact sur la vérification de la conformité de l’appareil ou l’accès conditionnel. Par exemple, les appareils avec une application malveillante auront toujours un niveau de risque « Moyen ».

### <a name="configure-privacy-for-malware-alert-report-on-android-enterprise-work-profile"></a>Configurer la confidentialité du rapport d’alerte anti-programme malveillant sur le profil Enterprise travail Android

Pour activer la confidentialité des utilisateurs ciblés dans le profil de travail, utilisez les étapes suivantes :

1. In [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and go to **AppsApp** >  **configuration** **policiesAddManaged** >  >  **devices**.
2. Nommez la stratégie, **> android Enterprise**, sélectionnez le type de profil.
3. **Sélectionnez Microsoft Defender pour le point de terminaison** comme application cible.
4. Dans Paramètres page, sélectionnez Utiliser le concepteur de **configuration** et ajoutez **DefenderExcludeAppInReport** comme clé et type de valeur sous **la forme Integer**
   - Entrez **1 pour activer la confidentialité**. La valeur par défaut est 0.
5. Cliquez **sur Suivant** et affectez ce profil à des appareils/utilisateurs ciblés.

L’utilisation de ce contrôle de confidentialité n’aura pas d’impact sur la vérification de la conformité de l’appareil ou l’accès conditionnel. Par exemple, les appareils avec une application malveillante auront toujours un niveau de risque « Moyen ».

## <a name="related-topics"></a>Voir aussi

- [Vue d’ensemble de Microsoft Defender pour point de terminaison Android](microsoft-defender-endpoint-android.md)
- [Déployer Microsoft Defender pour point de terminaison Android via Microsoft Intune](android-intune.md)
