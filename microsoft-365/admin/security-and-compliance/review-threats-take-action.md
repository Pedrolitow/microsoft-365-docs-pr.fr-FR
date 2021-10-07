---
title: Examiner les menaces détectées et prendre des mesures
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
search.appverid: MET150
description: Découvrez comment examiner et gérer les menaces détectées par les Antivirus Microsoft Defender sur vos Windows 10 mobiles.
ms.openlocfilehash: 30c2114a3605c73214f773414fe64e18522d9093
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60180400"
---
# <a name="review-detected-threats-and-take-action"></a>Examiner les menaces détectées et prendre des mesures

Dès qu’un fichier ou un logiciel malveillant est détecté, Antivirus Microsoft Defender le bloque et l’empêche de s’exécute. Une fois la protection cloud est désactivée, les menaces nouvellement détectées sont ajoutées au moteur antivirus et anti-programme malveillant afin que vos autres appareils et utilisateurs soient également protégés.

Antivirus Microsoft Defender détection et protection contre les types de menaces suivants :

- Virus, programmes malveillants et menaces basées sur le web sur les appareils
- Tentatives d’hameçonnage
- Tentatives de vol de données

En tant qu’administrateur/professionnel de l’informatique, vous pouvez afficher des informations sur les détections de menaces sur Windows 10 appareils inscrits dans [Intune](/mem/intune/enrollment/device-enrollment) dans le Centre d'administration Microsoft 365. Vous verrez des informations récapitulatifs, telles que :

- Nombre d’appareils qui ont besoin d’une protection antivirus
- Nombre d’appareils non conformes aux stratégies de sécurité
- Nombre de menaces actuellement actives, atténuées ou résolues

Plusieurs options s’offrent à vous pour afficher des informations spécifiques sur les détections de menaces et les appareils :

- Page **Appareils actifs** dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d'administration Microsoft 365</a>. Voir [Gérer les détections de menaces sur la page Appareils actifs](#manage-threat-detections-on-the-active-devices-page) dans cet article.
- Page **Menaces** actives dans la <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d'administration Microsoft 365</a>. Voir [Gérer les détections de menaces sur la page Menaces actives](#manage-threat-detections-on-the-active-threats-page) dans cet article.
- Page **Antivirus** dans <a href="https://go.microsoft.com/fwlink/p/?linkid=2150463" target="_blank">Microsoft Endpoint Manager</a>. Voir [Gérer les détections de menaces Microsoft Endpoint Manager](#manage-threat-detections-in-microsoft-endpoint-manager) dans cet article.

Pour plus d’informations, voir [Menaces détectées par Antivirus Microsoft Defender](threats-detected-defender-av.md).

## <a name="manage-threat-detections-on-the-active-devices-page"></a>Gérer les détections de menaces sur la page **Appareils** actifs

La procédure suivante s’applique aux clients qui ont Microsoft 365 Business Premium.

1. Go to the Centre d'administration Microsoft 365 at <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a> and sign in.

2. Dans la page de navigation, sélectionnez **Appareils**  >  **actifs.** Vous verrez une liste des appareils actifs et des détails, tels que l’état de protection, l’état de protection antivirus et le nombre de menaces actives détectées.

3. Sélectionnez un appareil pour afficher plus de détails sur cet appareil et les actions disponibles. Un volant s’ouvre avec des recommandations et des actions disponibles, telles que la stratégie de mise à **jour,** **l’antivirus** de mise à **jour,** exécuter une analyse rapide, exécuter **une analyse** complète, etc.

## <a name="manage-threat-detections-on-the-active-threats-page"></a>Gérer les détections de menaces dans la page **Menaces actives**

La procédure suivante s’applique aux clients qui ont Microsoft 365 Business Premium. [Windows 10 appareils doivent être sécurisés](../setup/secure-win-10-pcs.md) et [inscrits dans Intune.](/mem/intune/enrollment/windows-enrollment-methods)

> [!NOTE]
> La **carte** **Antivirus Microsoft Defender** la page Menaces actives étant déployées par phases, vous n’avez peut-être pas un accès immédiat à ces cartes.

1. Go to the Centre d'administration Microsoft 365 at <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a> and sign in.

2. Sur la **Antivirus Microsoft Defender,** sélectionnez **Afficher les menaces actives.** (Sinon, dans le volet de navigation, sélectionnez **Santé**  >  **Menaces & antivirus**.)

3. Dans la page **Menaces** actives, sélectionnez une menace détectée pour en savoir plus. Un flyout s’ouvre avec des détails sur cette menace, y compris les appareils concernés.

4. Dans le volant, sélectionnez un appareil pour afficher les actions disponibles, telles que la stratégie de mise à **jour,** **l’antivirus** de mise à **jour,** l’analyse rapide, etc.

## <a name="actions-you-can-take"></a>Actions que vous pouvez prendre

Lorsque vous affichez des détails sur des menaces ou des appareils spécifiques, vous verrez des recommandations et une ou plusieurs actions que vous pouvez prendre. Le tableau suivant décrit les actions que vous pouvez voir.<br><br>

| Opération | Description |
|--|--|
| Configurer la protection | Vos stratégies de protection contre les menaces doivent être configurées. Sélectionnez le lien vers la page de configuration de votre stratégie.<br><br>Vous avez besoin d’aide ? Voir [Gérer la sécurité des appareils avec les stratégies de sécurité des](/mem/intune/protect/endpoint-security-policy)points de terminaison dans Microsoft Intune . |
| Mettre à jour une stratégie | Vos stratégies de protection antivirus et en temps réel doivent être mises à jour ou configurées. Sélectionnez le lien pour aller à la page de configuration de stratégie.<br><br>Vous avez besoin d’aide ? Voir [Gérer la sécurité des appareils avec les stratégies de sécurité des](/mem/intune/protect/endpoint-security-policy)points de terminaison dans Microsoft Intune . |
| Exécuter une analyse rapide | Démarre une analyse antivirus rapide sur l’appareil, en se concentrant sur les emplacements courants où les programmes malveillants peuvent être enregistrés, tels que les clés de Registre et les dossiers Windows de démarrage. |
| Exécuter une analyse complète | Démarre une analyse antivirus complète sur l’appareil, en se concentrant sur les emplacements courants où les programmes malveillants peuvent être enregistrés, y compris tous les fichiers et dossiers de l’appareil. Les résultats sont envoyés [à Microsoft Endpoint Manager](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager). |
| Mettre à jour un antivirus | Nécessite que l’appareil obtienne des mises à jour de [l’intelligence de sécurité](https://go.microsoft.com/fwlink/?linkid=2149926) pour la protection antivirus et anti-programme malveillant. |
| Redémarrer l’appareil | Force un Windows 10 à redémarrer dans les cinq minutes.<br><br>**IMPORTANT :** Le propriétaire ou l’utilisateur de l’appareil n’est pas averti automatiquement du redémarrage et risque de perdre du travail non notifié. |

## <a name="manage-threat-detections-in-microsoft-endpoint-manager"></a>Gérer les détections de menaces dans Microsoft Endpoint Manager

Vous pouvez utiliser Microsoft Endpoint Manager pour gérer les détections de menaces. Windows 10 appareils doivent [être inscrits dans Intune](/mem/intune/enrollment/windows-enrollment-methods) (partie de Microsoft Endpoint Manager).

1. Go to the Microsoft Endpoint Manager admin center at <a href="https://go.microsoft.com/fwlink/p/?linkid=2150463" target="_blank">https://endpoint.microsoft.com</a> and sign in.

2. Dans le volet de navigation, sélectionnez **Sécurité du point de terminaison.**

3. Sous **Gérer,** sélectionnez **Antivirus**. You’ll see several tabs, such **as Summary**, **Windows 10 unhealthy endpoints**, and **Windows 10 detected malware**.

4. Examinez les informations sous les onglets disponibles, puis prenez les mesures nécessaires.

Par exemple, supposons que les appareils sont répertoriés dans **l’onglet Windows 10 programmes** malveillants détectés. Lorsque vous sélectionnez un appareil, certaines actions sont disponibles, telles que le redémarrage, l’analyse **rapide,** l’analyse **complète,** la synchronisation ou la mise à jour des **signatures.** Sélectionnez une action pour cet appareil.

Le tableau suivant décrit les actions que vous pouvez voir dans Microsoft Endpoint Manager.<br><br>

| Opération | Description |
|--|--|
| Redémarrer | Force un Windows 10 à redémarrer dans les cinq minutes.<br><br>**IMPORTANT :** Le propriétaire ou l’utilisateur de l’appareil n’est pas averti automatiquement du redémarrage et risque de perdre du travail non notifié. |
| Analyse rapide | Démarre une analyse antivirus rapide sur l’appareil, en se concentrant sur les emplacements courants où les programmes malveillants peuvent être enregistrés, tels que les clés de Registre et les dossiers Windows de démarrage. Les résultats sont envoyés [à Microsoft Endpoint Manager](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager). |
| Analyse complète | Démarre une analyse antivirus complète sur l’appareil, en se concentrant sur les emplacements courants où les programmes malveillants peuvent être enregistrés, y compris tous les fichiers et dossiers de l’appareil. Les résultats sont envoyés [à Microsoft Endpoint Manager](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager). |
| Synchronisation | Nécessite un appareil pour l’enregistrement avec Intune (partie de Microsoft Endpoint Manager). Lorsque l’appareil est connecté, il reçoit les actions ou stratégies en attente attribuées à l’appareil. |
| Mettre à jour les signatures | Nécessite que l’appareil obtienne des mises à jour de [l’intelligence de sécurité](https://go.microsoft.com/fwlink/?linkid=2149926) pour la protection antivirus et anti-programme malveillant. |

> [!TIP]
> Pour plus d’informations, voir [Actions à distance pour les appareils.](/mem/intune/protect/endpoint-security-manage-devices#remote-actions-for-devices)

## <a name="how-to-submit-a-file-for-malware-analysis"></a>Comment soumettre un fichier pour analyse des programmes malveillants

Si vous avez un fichier que vous pensez avoir été manqué ou classé à tort comme programme malveillant, vous pouvez soumettre ce fichier à Microsoft pour analyse des programmes malveillants. Les utilisateurs et les administrateurs informatiques peuvent soumettre un fichier pour analyse. Visitez [https://www.microsoft.com/wdsi/filesubmission](https://www.microsoft.com/wdsi/filesubmission) .