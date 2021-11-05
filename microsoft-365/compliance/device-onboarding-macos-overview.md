---
title: Intégration des appareils macOS dans la vue d'ensemble de Microsoft 365 (aperçu)
f1.keywords: NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: En savoir plus sur l’intégration d’appareils macOS dans des solutions de conformité
ms.openlocfilehash: b24fd172224e0d1f8080ddd22cb3532dce0afe2b
ms.sourcegitcommit: 27bf284b3bfe334eb98847798734625bd2ffafb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2021
ms.locfileid: "60792291"
---
# <a name="onboard-macos-devices-into-microsoft-365-overview-preview"></a>Intégration des appareils macOS dans la vue d'ensemble de Microsoft 365 (aperçu)

Les appareils MacOS peuvent être intégrés à des solutions Microsoft 365 conformité à l’aide d’Intune ou de JAMF Pro. Les procédures d’intégration diffèrent en fonction de la solution de gestion que vous utilisez. Si vos appareils macOS ont déjà été intégrés à Microsoft Defender for Endpoint (MDE), il existe moins d’étapes. Consultez [les étapes](#next-steps) suivantes pour obtenir des liens vers les procédures appropriées pour vous.

## <a name="get-registered"></a>S’inscrire

Pour accéder à cette fonctionnalité, vous devez enregistrer votre locataire auprès de Microsoft. Voir, [inscrivez-vous à la Microsoft 365 prise en charge macOS.](https://aka.ms/EndpointDLPIgnite21-Previews)

**S’applique à :**

- [Microsoft 365 Protection contre la perte de données (DLP) de point de terminaison](./endpoint-dlp-learn-about.md)
- [Gestion des risques internes](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)
<!--- [Insider risk management](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)-->

## <a name="before-you-begin"></a>Avant de commencer

Avant de commencer avec endpoint DLP sur les appareils macOS (Contrôle 10.15 ou ultérieur), vous devez vous familiariser avec les articles suivants :

- [Découvrir la protection contre la perte de données des point de terminaison de Microsoft 365](endpoint-dlp-learn-about.md#learn-about-microsoft-365-endpoint-data-loss-prevention)
- [Prise en main la protection contre la perte de données de point de terminaison](endpoint-dlp-getting-started.md#get-started-with-endpoint-data-loss-prevention)

Si vous n’êtes pas du tout familiarisé avec la DLP, vous devez également vous familiariser avec les articles suivants :

- [En savoir plus sur la prévention des pertes de données](dlp-learn-about-dlp.md#learn-about-data-loss-prevention)
- [Planifier la protection contre la perte de données (DLP)](dlp-overview-plan-for-dlp.md#plan-for-data-loss-prevention-dlp)
- [Référence de stratégie de protection contre la perte de données](dlp-policy-reference.md#data-loss-prevention-policy-reference)

Vos appareils macOS doivent déjà être gérés via Intune ou JAMF Pro.
 
- Pour intégrer Intune, voir le guide de déploiement : Gérer les appareils [macOS](/mem/intune/fundamentals/deployment-guide-platform-macos) dans Microsoft Intune et inscrire votre [Mac avec Portail d'entreprise Intune](/mem/intune/user-help/enroll-your-device-in-intune-macos-cp). 
- Pour vous intégrer à JAMF Pro consultez le [guide des administrateurs de jamf Pro](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/) et le Guide de configuration et d’installation de [JAMF Pro](https://www.jamf.com/resources/product-documentation/jamf-pro-installation-guide-for-mac/) pour Mac
- Installer le navigateur Edge v95+ sur vos appareils macOS 

## <a name="licensing-guidance"></a>Recommandations en matière de licences

Consultez les [recommandations Microsoft 365 licences pour la protection des informations](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection)

## <a name="activities-that-can-be-restricted-on-macos"></a>Activités qui peuvent être restreintes sur macOS 

Une fois qu’un appareil macOS est intégré aux solutions de conformité Microsoft 365, vous pouvez surveiller et limiter ces actions avec des stratégies de protection contre la perte de données (DLP).

**Copier** sur un média amovible USB : lorsqu’elle est appliquée, cette action bloque, avertit ou audite la copie ou le déplacement de fichiers protégés d’un appareil de point de terminaison vers un support amovible USB 

**Copier sur des** partages réseau : lorsqu’elle est appliquée, cette action bloque, avertit ou audite la copie ou le déplacement de fichiers protégés d’un appareil de point de terminaison vers n’importe quel partage réseau 

**Imprimer** : lorsqu’elle est appliquée, cette action bloque, avertit ou audite lorsque des fichiers protégés sont imprimés à partir d’un appareil de point de terminaison 

**Copier dans le Presse-papiers** : lorsqu’elle est appliquée, cette action bloque, avertit ou audite les données dans le fichier protégé qui est copié dans un Presse-papiers sur un appareil de point de terminaison 

**Télécharger** vers le cloud : cette action bloque, avertit ou audite lorsque les fichiers protégés sont interdits ou autorisés à être téléchargés vers les services cloud en fonction de la liste des domaines autorisés/non autorisés dans les paramètres globaux. Lorsque cette action est définie pour avertir ou bloquer, l’accès au fichier est bloqué pour les autres navigateurs (définis dans la liste des navigateurs non autorisé sous Paramètres globaux). 

 Accès par les applications non autorisé : lorsqu’elle est appliquée, cette action empêche les applications qui se retrouvent dans la liste des applications non autorisé (comme défini dans les paramètres globaux) d’accéder aux fichiers protégés sur un appareil de point de terminaison. Exemples de scénarios 

## <a name="next-steps"></a>Prochaines étapes

L’intégration d’appareils Microsoft 365 solutions de conformité est nécessaire pour recevoir la télémétrie du capteur DLP et appliquer des stratégies de protection contre la perte de données. 

- Pour les appareils macOS gérés via Intune, voir Appareils macOS intégrés et hors intégration dans les solutions de conformité Microsoft 365 à l’aide [d’Intune (prévisualisation)](device-onboarding-offboarding-macos-intune.md#onboard-and-offboard-macos-devices-into-microsoft-365-compliance-solutions-using-intune-preview)

- Pour les appareils macOS qui sont gérés via Intune et sur qui Microsoft Defender pour le point de terminaison (MDE) est déployé, voir Appareils macOS intégrés et hors intégration dans les solutions de conformité à l’aide d’Intune pour Microsoft Defender pour les clients [endpoint (prévisualisation)](device-onboarding-offboarding-macos-intune-mde.md#onboard-and-offboard-macos-devices-into-compliance-solutions-using-intune-for-microsoft-defender-for-endpoint-customers-preview)

- Pour les appareils macOS qui sont gérés via jamf Pro, consultez Les appareils macOS intégrés et hors intégration dans les solutions de conformité Microsoft 365 à l’aide de [JAMF Pro (prévisualisation)](device-onboarding-offboarding-macos-jamfpro.md#onboard-and-offboard-macos-devices-into-microsoft-365-compliance-solutions-using-jamf-pro-preview)

- Pour les appareils macOS qui sont gérés par le biais de JAMF Pro et sur qui Microsoft Defender pour point de terminaison (MDE) est déployé, voir Appareils macOS intégrés et hors intégration dans les solutions de conformité à l’aide de JAMF Pro pour les clients [Microsoft Defender pour endpoint (prévisualisation)](device-onboarding-offboarding-macos-jamfpro-mde.md#onboard-and-offboard-macos-devices-into-compliance-solutions-using-jamf-pro-for-microsoft-defender-for-endpoint-customers-preview)


## <a name="related-topics"></a>Voir aussi

- [Utilisation de la prévention des pertes de données sur les points de terminaison](endpoint-dlp-using.md#using-endpoint-data-loss-prevention)
- [Matrice de prise en charge des conseils de stratégie DLP dans les applications Microsoft](dlp-policy-tips-reference.md#support-matrix-for-dlp-policy-tips-across-microsoft-apps)
