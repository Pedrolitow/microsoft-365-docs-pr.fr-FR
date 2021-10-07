---
title: Vérifier la préparation d’évaluation téléchargeable
description: Vérifie les paramètres du périphérique et du réseau, y compris les points de terminaison requis
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
audience: Admin
ms.openlocfilehash: 57739b657f3aa296b92b67c16b7b7c5c3628e8b9
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60152441"
---
# <a name="downloadable-readiness-assessment-checker"></a>Vérifier la préparation d’évaluation téléchargeable

Pour fonctionner avec Microsoft Manged Desktop, les appareils doivent répondre à certaines exigences en matière de matériel et de paramètres. En outre, chaque appareil doit être en mesure d’atteindre les points de terminaison clés. Téléchargez et exécutez cet outil pour obtenir un rapport HTML, afficher les résultats, puis prendre des mesures. Vous devrez télécharger l’outil et les fichiers de prise en charge, puis l’exécuter manuellement sur chaque appareil que vous souhaitez inscrire dans Microsoft Manged Desktop.

Pour chaque vérification, l’outil signalera l’un des trois résultats possibles :


|Résultat  |Signification  |
|---------|---------|
|Prêt     | Aucune action n’est requise avant de terminer l’inscription.        |
|Avertissement    | Suivez les étapes de l’outil pour une expérience de l’inscription et pour les utilisateurs. Vous *pouvez terminer* l’inscription, mais vous devez résoudre ces problèmes avant de déployer votre premier appareil.        |
|Non prêt | *L’inscription échoue* si vous ne corrigez pas ces problèmes. Suivez les étapes de l’outil pour les résoudre.        |

## <a name="obtain-the-checker"></a>Obtenir le coche

Téléchargez le .zip à partir https://aka.ms/mmddratoolv0 de .

> [!NOTE]
> L’utilisateur qui exécute l’outil doit avoir des droits d’administrateur local sur l’appareil sur lequel il l’exécute.

 Exécutez ensuite l’outil en suivant les étapes suivantes :

1. Copiez le fichier .zip téléchargé sur chaque appareil que vous souhaitez vérifier.
2. Extrayez tous les fichiers dans le téléchargement compressé.
3. Exécutez **Microsoft.MMD.DeviceReadinessAssessmentTool.exe**.
4. Lorsque l’invite de contrôle d’accès utilisateur s’affiche, **sélectionnez Oui**. L’outil s’exécute et ouvre un rapport dans votre navigateur par défaut.

Vous pouvez également télécharger et extraire l’archive .zip  à un emplacement partagé, accéder auxMicrosoft.MMD.DeviceReadinessAssessmentTool.exeà partir de chaque appareil, puis l’exécuter localement.


## <a name="checks"></a>Vérifications

L’outil téléchargeable vérifie les éléments liés à l’appareil et au réseau :

### <a name="hardware"></a>Matériel

Les appareils doivent répondre à des exigences matérielles spécifiques pour fonctionner avec Microsoft Manged Desktop. Pour plus d’informations, voir [La requise pour l’appareil.](../service-description/device-list.md)

Si votre appareil échoue à l’une des vérifications, il n’est pas compatible avec Microsoft Manged Desktop.

### <a name="network-endpoints"></a>Points de terminaison réseau

Les appareils sont en grande partie en mesure d’atteindre plusieurs [points de terminaison clés](network.md) pour fonctionner avec Microsoft Manged Desktop.

Si l’outil **signale** un résultat non prêt, consultez le rapport détaillé pour savoir quels points de terminaison n’ont pas été accessibles. Ajustez ensuite votre pare-feu ou d’autres paramètres réseau pour vous assurer que ces points de terminaison sont accessibles.

### <a name="other-settings"></a>Autres paramètres

#### <a name="enterprise-wi-fi-profiles"></a>Enterprise wi-fi

Un **résultat d’avis** signifie que vous utilisez certains profils Wi-Fi qui ont besoin de certificats et de profils pour fonctionner correctement. Pour plus d’informations, voir Déployer des certificats et profil [Wi-Fi/VPN.](certs-wifi-lan.md#deploy-certificates-and-wi-fivpn-profile)

#### <a name="lan-profiles"></a>Profils LAN

Un **résultat d’avis** signifie que vous avez des lans qui ont besoin de certificats et de profils pour fonctionner correctement. Pour plus d’informations, [voir Préparer les certificats et les profils réseau pour Microsoft Manged Desktop](certs-wifi-lan.md).

#### <a name="vpn-profiles"></a>Profils VPN

Un **résultat d’avis** signifie que vous utilisez un réseau privé virtuel (VPN). Créez un profil VPN qui déploie des certificats intégrés à Microsoft Intune. Pour plus d’informations, [voir Préparer les certificats et les profils réseau pour Microsoft Manged Desktop](certs-wifi-lan.md).

#### <a name="mapped-drives"></a>Lecteurs mappés

Un **résultat d’avis** signifie que vous avez des lecteurs mappés, ce qui n’est pas recommandé. Pour plus d’informations, voir [Préparer les lecteurs Microsoft Manged Desktop](mapped-drives.md).

#### <a name="print-queues"></a>Imprimer les files d’attente

Un **résultat d’avis** signifie que vous avez des files d’attente d’impression en attente, ce qui n’est pas recommandé. Une solution consiste à utiliser l’impression cloud. Pour plus d’informations, voir [Préparer les ressources d’impression Microsoft Manged Desktop](printing.md).

#### <a name="proxies"></a>Proxies

Un **résultat d’avis** signifie que vous avez un serveur proxy en cours d’utilisation. Pour plus d’informations, [voir Configuration réseau pour Microsoft Manged Desktop](network.md).

