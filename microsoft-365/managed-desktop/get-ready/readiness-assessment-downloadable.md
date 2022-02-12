---
title: Vérifier la préparation d’évaluation téléchargeable
description: Vérifie les paramètres du périphérique et du réseau, y compris les points de terminaison requis
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: 9e3ad0953cdbd6561f9a0145ccff5aefe24b8dfb
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2022
ms.locfileid: "62765611"
---
# <a name="downloadable-readiness-assessment-checker"></a>Vérifier la préparation d’évaluation téléchargeable

Pour fonctionner avec Microsoft Manged Desktop, les appareils doivent répondre à certaines exigences en matière de matériel et de paramètres. Chaque appareil doit être en mesure d’atteindre les points de terminaison clés.

Téléchargez et exécutez l’outil de vérification de l’évaluation de la préparation pour obtenir un rapport HTML, afficher les résultats et prendre des mesures. Vous devez télécharger l’outil et les fichiers de prise en charge. Ensuite, exécutez-le manuellement sur chaque appareil que vous souhaitez inscrire dans Microsoft Manged Desktop.

Pour chaque vérification, l’outil signalera l’un des trois résultats possibles :

| Résultat | Signification |
| ----- | ----- |
| Prêt | Aucune action n’est requise avant de terminer l’inscription. |
| Avertissement | Suivez les étapes de l’outil pour une expérience de l’inscription et pour les utilisateurs. <br><br> Vous *pouvez terminer* l’inscription, mais vous devez résoudre ces problèmes avant de déployer votre premier appareil. |
| Non prêt | **L’inscription échoue** si vous ne corrigez pas ces problèmes. <br><br> Suivez les étapes de l’outil pour les résoudre. |

## <a name="obtain-the-checker"></a>Obtenir le coche

Téléchargez le .zip à partir de https://aka.ms/mmddratoolv0.

> [!NOTE]
> L’utilisateur qui exécute l’outil doit avoir des droits d’administrateur local sur l’appareil sur lequel il l’exécute.

**Pour exécuter l’outil :**

1. Copiez le fichier .zip téléchargé sur chaque appareil que vous souhaitez vérifier.
2. Extrayez tous les fichiers dans le téléchargement compressé.
3. **ExécutezMicrosoft.MMD.DeviceReadinessAssessmentTool.exe**.
4. Lorsque l’invite contrôle d’accès utilisateur s’affiche, sélectionnez **Oui**. L’outil s’exécute et ouvre un rapport dans votre navigateur par défaut.

Vous pouvez également télécharger et extraire l’archive .zip à un emplacement partagé, **Microsoft.MMD.DeviceReadinessAssessmentTool.exeà partir** de chaque appareil. Ensuite, exécutez-le localement.

## <a name="checks"></a>Vérifications

L’outil téléchargeable vérifie ces éléments liés au périphérique et au réseau :

| Chèque | Description |
| ----- | ----- |
| Matériel | Les appareils doivent répondre à des exigences matérielles spécifiques pour fonctionner avec Microsoft Manged Desktop. Pour plus d’informations, voir [Exigences relatives aux appareils](../service-description/device-list.md). <br><br> Si votre appareil échoue à l’une des vérifications, il n’est pas compatible avec Microsoft Manged Desktop. |
| Points de terminaison réseau | Les appareils sont en grande partie en mesure d’atteindre plusieurs [points de terminaison clés](network.md) pour fonctionner avec Microsoft Manged Desktop. <br><br> Si l’outil **signale un** résultat non prêt, consultez le rapport détaillé pour savoir quels points de terminaison n’ont pas été accessibles. Ensuite, ajustez votre pare-feu ou d’autres paramètres réseau pour vous assurer que ces points de terminaison sont accessibles. |

### <a name="other-settings"></a>Autres paramètres

| Setting | Description |
| ----- | ----- |
| Enterprise Wi-Fi profils | Un **résultat d’avis** signifie que vous utilisez certains profils Wi-Fi qui ont besoin de certificats et de profils pour fonctionner correctement. Pour plus d’informations, voir [Déployer des certificats et profil Wi-Fi/VPN](certs-wifi-lan.md#deploy-certificates-and-wi-fivpn-profile). |
| Profils LAN | Un **résultat d’avis** signifie que vous avez des lans qui ont besoin de certificats et de profils pour fonctionner correctement. Pour plus d’informations, voir [Préparer les certificats et les profils réseau pour Microsoft Manged Desktop](certs-wifi-lan.md). |
| Profils VPN | Un **résultat d’avis** signifie que vous utilisez un réseau privé virtuel (VPN). Créez un profil VPN qui déploie des certificats intégrés à Microsoft Intune. Pour plus d’informations, voir [Préparer les certificats et les profils réseau pour Microsoft Manged Desktop](certs-wifi-lan.md). |
| Lecteurs mappés | Un **résultat d’avis** signifie que vous avez des lecteurs mappés, ce qui n’est pas recommandé. Pour plus d’informations, voir [Préparer les lecteurs Microsoft Manged Desktop](mapped-drives.md). |
| Imprimer les files d’attente | Un **résultat d’avis** signifie que vous avez des files d’attente d’impression en attente, ce qui n’est pas recommandé. Une solution consiste à utiliser l’impression cloud. Pour plus d’informations, voir [Préparer les ressources d’impression Microsoft Manged Desktop](printing.md). |
| Proxies | Un **résultat d’avis** signifie que vous avez un serveur proxy en cours d’utilisation. Pour plus d’informations, [voir Configuration réseau pour Microsoft Manged Desktop](network.md). |
