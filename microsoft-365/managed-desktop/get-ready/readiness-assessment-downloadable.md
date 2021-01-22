---
title: Téléchargeable readiness assessment checker
description: Vérifie les paramètres du périphérique et du réseau, y compris les points de terminaison requis
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: 2080b2fc924320f38d9972c82c0425fa1d8026e7
ms.sourcegitcommit: 7ecd10b302b3b3dfa4ba3be3a6986dd3c189fbff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/21/2021
ms.locfileid: "49921970"
---
# <a name="downloadable-readiness-assessment-checker"></a>Téléchargeable readiness assessment checker

Pour fonctionner avec le Bureau géré Microsoft, les appareils doivent répondre à certaines exigences en matière de matériel et de paramètres. En outre, chaque appareil doit être en mesure d’atteindre les points de terminaison clés. Téléchargez et exécutez cet outil pour obtenir un rapport HTML, afficher les résultats, puis prendre des mesures. Vous devrez télécharger l’outil et les fichiers de prise en charge, puis l’exécuter manuellement sur chaque appareil que vous souhaitez inscrire dans Bureau géré Microsoft.

Pour chaque vérification, l’outil signalera l’un des trois résultats possibles :


|Résultat  |Signification  |
|---------|---------|
|Prêt     | Aucune action n’est requise avant de terminer l’inscription.        |
|Avis    | Suivez les étapes de l’outil pour une expérience de l’inscription et pour les utilisateurs. Vous *pouvez terminer* l’inscription, mais vous devez résoudre ces problèmes avant de déployer votre premier appareil.        |
|Non prêt | *L’inscription échoue* si vous ne corrigez pas ces problèmes. Suivez les étapes de l’outil pour les résoudre.        |

## <a name="obtain-the-checker"></a>Obtenir le coche

Téléchargez le fichier .zip à partir https://aka.ms/mmddratoolv0 de .

> [!NOTE]
> L’utilisateur qui exécute l’outil doit avoir des droits d’administrateur local sur l’appareil sur lequel il l’exécute.

 Exécutez ensuite l’outil en suivant les étapes suivantes :

1. Copiez le fichier .zip téléchargé sur chaque appareil que vous souhaitez vérifier.
2. Extrayez tous les fichiers dans le téléchargement compressé.
3. Exécutez **Microsoft.MMD.DeviceReadinessAssessmentTool.exe**.
4. Lorsque l’invite de contrôle d’accès utilisateur s’affiche, **sélectionnez Oui**. L’outil s’exécute et ouvre un rapport dans votre navigateur par défaut.

Vous pouvez également télécharger et extraire l’archive  .zip vers un emplacement partagé, accéder auxMicrosoft.MMD.DeviceReadinessAssessmentTool.exeà partir de chaque appareil, puis l’exécuter localement.


## <a name="checks"></a>Vérifications

L’outil téléchargeable vérifie les éléments liés à l’appareil et au réseau :

### <a name="hardware"></a>Matériel

Les appareils doivent répondre à des exigences matérielles spécifiques pour fonctionner avec le Bureau géré Microsoft. Actuellement, seuls des [appareils approuvés spécifiques](../service-description/device-list.md) sont autorisés à s’inscrire. 

Si votre appareil échoue à l’une des vérifications, il n’est pas compatible avec bureau géré Microsoft.

### <a name="network-endpoints"></a>Points de terminaison réseau

Les appareils sont en grande partie en mesure d’atteindre plusieurs [points de terminaison clés](network.md) pour fonctionner avec bureau géré Microsoft.

Si l’outil **signale** un résultat non prêt, consultez le rapport détaillé pour savoir quels points de terminaison n’ont pas été accessibles. Ajustez ensuite votre pare-feu ou d’autres paramètres réseau pour vous assurer que ces points de terminaison sont accessibles.

### <a name="other-settings"></a>Autres paramètres

#### <a name="enterprise-wi-fi-profiles"></a>Profils Wi-Fi d’entreprise

Un **résultat d’avis** signifie que vous utilisez certains profils wi-fi qui ont besoin de certificats et de profils pour fonctionner correctement. Pour plus d’informations, voir Déployer des certificats et profil [Wi-Fi/VPN.](certs-wifi-lan.md#deploy-certificates-and-wi-fivpn-profile)

#### <a name="lan-profiles"></a>Profils LAN

Un **résultat d’avis** signifie que vous avez des lans qui ont besoin de certificats et de profils pour fonctionner correctement. Pour plus d’informations, voir [Préparer les certificats et les profils réseau pour bureau géré Microsoft.](certs-wifi-lan.md)

#### <a name="vpn-profiles"></a>Profils VPN

Un **résultat d’avis** signifie que vous utilisez un réseau privé virtuel (VPN). Créez un profil VPN qui déploie des certificats intégrés à Microsoft Intune. Pour plus d’informations, voir [Préparer les certificats et les profils réseau pour bureau géré Microsoft.](certs-wifi-lan.md)

#### <a name="mapped-drives"></a>Lecteurs mappés

Un **résultat d’avis** signifie que vous avez des lecteurs mappés, ce qui n’est pas recommandé. Pour plus d’informations, voir [Préparer les lecteurs mappés pour le Bureau géré Microsoft.](mapped-drives.md)

#### <a name="print-queues"></a>Imprimer les files d’attente

Un **résultat d’avis** signifie que vous avez des files d’attente d’impression en attente, ce qui n’est pas recommandé. Une solution consiste à utiliser l’impression cloud. Pour plus d’informations, voir [Préparer les ressources d’impression pour le Bureau géré Microsoft.](printing.md)

#### <a name="proxies"></a>Proxies

Un **résultat d’avis** signifie que vous avez un serveur proxy en cours d’utilisation. Pour plus d’informations, [voir Configuration réseau pour bureau géré Microsoft.](network.md)

