---
title: Vue d’ensemble de l’intégration des appareils macOS dans Microsoft 365
f1.keywords: NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: En savoir plus sur l’intégration d’appareils macOS dans des solutions de conformité
ms.openlocfilehash: b697b805b8a4c65a0528054ca301f16d203e5a64
ms.sourcegitcommit: 979343980f05ceb546ca0df23562504aaca34b88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2022
ms.locfileid: "66912756"
---
# <a name="onboard-macos-devices-into-microsoft-365-overview"></a>Vue d’ensemble de l’intégration des appareils macOS dans Microsoft 365

Les appareils MacOS peuvent être intégrés aux solutions Microsoft Purview à l’aide de Intune ou JAMF Pro. Les procédures d’intégration varient en fonction de la solution de gestion que vous utilisez. Si vos appareils macOS ont déjà été intégrés à Microsoft Defender pour point de terminaison (MDE), il y a moins d’étapes. Consultez [les étapes suivantes](#next-steps) pour obtenir des liens vers les procédures appropriées pour vous.

**S’applique à :**

- [Protection contre la perte de données (DLP) de point de terminaison](./endpoint-dlp-learn-about.md)
- [Gestion des risques internes](insider-risk-management.md)

## <a name="before-you-begin"></a>Avant de commencer

Avant de commencer à utiliser endpoint DLP sur les appareils macOS (Catalina 10.15 ou version ultérieure), vous devez vous familiariser avec les articles suivants :

- [Découvrir la protection contre la perte de données de point de terminaison](endpoint-dlp-learn-about.md)
- [Prise en main la protection contre la perte de données de point de terminaison](endpoint-dlp-getting-started.md)

Si vous n’êtes pas familiarisé avec DLP, vous devez également vous familiariser avec ces articles :

- [En savoir plus sur la prévention des pertes de données](dlp-learn-about-dlp.md#learn-about-data-loss-prevention)
- [Planifier la protection contre la perte de données (DLP)](dlp-overview-plan-for-dlp.md#plan-for-data-loss-prevention-dlp)
- [Référence de la stratégie de protection contre la perte de données](dlp-policy-reference.md#data-loss-prevention-policy-reference)

Si vous n’êtes pas familiarisé avec insider risk, vous devez vous familiariser avec les articles suivants :

 - [Gestion des risques internes](insider-risk-management.md)
 - [Planifier la gestion des risques Insider](insider-risk-management-plan.md#plan-for-insider-risk-management)

Vos appareils macOS doivent déjà être gérés via Intune ou JAMF Pro.
 
- Pour intégrer Intune, consultez le [guide de déploiement : Gérer les appareils macOS dans Microsoft Intune](/mem/intune/fundamentals/deployment-guide-platform-macos) et [inscrire votre Mac avec Portail d'entreprise Intune](/mem/intune/user-help/enroll-your-device-in-intune-macos-cp). 
- Pour intégrer JAMF Pro, consultez le [guide des administrateurs JAMF Pro](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/) et le [Guide de configuration et d’installation de JAMF Pro pour Mac](https://www.jamf.com/resources/product-documentation/jamf-pro-installation-guide-for-mac/)
<!--- Install the v95+ Edge browser on your macOS devices--> 

### <a name="supported-browsers"></a>Navigateurs pris en charge

Endpoint DLP prend en charge ces navigateurs sur macOS Catalina 10.15 ou version ultérieure :

- Microsoft Edge (dernière version)
- Safari (dernière version, macOS uniquement)
- Chrome (dernière version)
- Firefox (dernière version)

## <a name="licensing-guidance"></a>Conseils sur les licences

Consultez les [conseils relatifs aux licences Microsoft 365 pour la protection des informations](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-loss-prevention-for-exchange-online-sharepoint-online-and-onedrive-for-business).

## <a name="activities-that-can-be-audited-and-restricted-on-macos"></a>Activités pouvant être auditées et restreintes sur macOS 

Une fois qu’un appareil macOS est intégré aux solutions Microsoft Purview, vous pouvez surveiller et restreindre ces actions avec des stratégies de protection contre la perte de données (DLP).

**Copier sur un média amovible USB** : lorsqu’elle est appliquée, cette action bloque, avertit ou audite la copie ou le déplacement de fichiers protégés d’un périphérique de point de terminaison vers un support amovible USB 

**Copier sur des partages réseau** : lorsqu’elle est appliquée, cette action bloque, avertit ou audite la copie ou le déplacement de fichiers protégés d’un appareil de point de terminaison vers n’importe quel partage réseau 

**Imprimer** : lorsqu’elle est appliquée, cette action bloque, avertit ou audite lorsque des fichiers protégés sont imprimés à partir d’un appareil de point de terminaison 

**Copier dans le Presse-papiers** : lorsqu’elle est appliquée, cette action bloque, avertit ou audite les données dans un fichier protégé qui est copié dans un Presse-papiers sur un appareil de point de terminaison 

**Charger dans le cloud** : cette action bloque, avertit ou audite lorsque des fichiers protégés sont empêchés ou autorisés à être chargés vers des services cloud en fonction de la liste des domaines autorisés/non autorisés dans les paramètres globaux. Lorsque cette action est définie pour avertir ou bloquer, les autres navigateurs (définis sur la liste des navigateurs non autorisés sous Paramètres globaux) ne peuvent pas accéder au fichier. 

**Accessible par les applications non autorisées** : lorsqu’elle est appliquée, cette action empêche les applications figurant dans la liste des applications non autorisées (telles que définies dans les paramètres globaux) d’accéder aux fichiers protégés sur un appareil de point de terminaison. Exemples de scénarios 

## <a name="onboarding-devices-into-device-management"></a>Dispositifs d’intégration dans la gestion des appareils

Vous devez activer la surveillance des appareils et intégrer vos points de terminaison avant de pouvoir surveiller et protéger les éléments sensibles sur un appareil. Ces deux actions sont effectuées dans le portail de conformité Microsoft Purview.

Lorsque vous voulez intégrer des appareils qui n’ont pas encore été intégrés, vous devez télécharger et déployer les scripts appropriés sur ces appareils. <!--Follow the [Onboarding devices procedure](endpoint-dlp-getting-started.md#onboarding-devices).-->

<!--If you already have devices onboarded into [Microsoft Defender for Endpoint](/windows/security/threat-protection/), they will already appear in the managed devices list.-->

1. Ouvrez la page [paramètres portail de conformité Microsoft Purview](https://compliance.microsoft.com)  et **choisissez Activer la surveillance des appareils**.

   > [!NOTE]
   > Bien que l’activation de l’intégration des appareils dure généralement environ 60 secondes, patientez jusqu’à 30 minutes avant de contacter le support Microsoft.

2. Ouvrez la page paramètres du Centre de conformité et choisissez **Activer la surveillance des appareils macOS**.

## <a name="next-steps"></a>Prochaines étapes

L’intégration des appareils aux solutions Microsoft Purview est nécessaire pour recevoir les données de télémétrie des capteurs DLP et appliquer des stratégies de protection contre la perte de données. 

Rubrique | Description
:---|:---
|[Intégrer et déconnecter des appareils macOS dans les solutions Microsoft Purview à l’aide d’Intune](device-onboarding-offboarding-macos-intune.md)|Pour les appareils macOS gérés via Intune
|[Intégrer et désactiver les appareils macOS dans les solutions de conformité à l’aide d’Intune pour les clients Microsoft Defender pour points de terminaison](device-onboarding-offboarding-macos-intune-mde.md) |Pour les appareils macOS gérés via Intune et sur lesquels Microsoft Defender pour point de terminaison (MDE) est déployé
|[Intégrer et déconnecter des appareils macOS dans des solutions Microsoft Purview à l’aide de JAMF Pro](device-onboarding-offboarding-macos-jamfpro.md) | Pour les appareils macOS gérés via JAMF Pro
|[Intégrer et déconnecter des appareils macOS dans des solutions de conformité à l’aide de JAMF Pro pour les clients Microsoft Defender pour point de terminaison](device-onboarding-offboarding-macos-jamfpro-mde.md)|Pour les appareils macOS gérés via JAMF Pro et sur lesquels Microsoft Defender pour point de terminaison (MDE) est déployé


## <a name="related-topics"></a>Voir aussi

- [Utilisation des points de terminaison protection contre la perte de données](endpoint-dlp-using.md#using-endpoint-data-loss-prevention)
- [Tableau de prise en charge pour les conseils de stratégie DLP dans les applications Microsoft](dlp-policy-tips-reference.md#support-matrix-for-dlp-policy-tips-across-microsoft-apps)
