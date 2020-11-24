---
title: Examiner les menaces détectées et prendre des mesures
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
search.appverid: MET150
description: Découvrez comment examiner et gérer les menaces détectées par l’antivirus Microsoft Defender sur vos appareils Windows 10.
ms.openlocfilehash: ffdf5cffb50d6145d6059233e0850839f4dfb582
ms.sourcegitcommit: 26b35012c42fef935d6c4a6509dde6c22a9b922a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2020
ms.locfileid: "49385239"
---
# <a name="review-detected-threats-and-take-action"></a>Examiner les menaces détectées et prendre des mesures

Dès qu’un fichier ou un logiciel malveillant est détecté, l’antivirus Microsoft Defender l’bloque et l’empêche de s’exécuter. En outre, si la protection sur le Cloud est activée, les menaces nouvellement détectées sont ajoutées au moteur antivirus et anti-programme malveillant afin que vos autres appareils et utilisateurs soient également protégés.

L’antivirus Microsoft Defender détecte et protège contre les types de menaces suivants :

- Virus, programmes malveillants et menaces basées sur le Web sur les appareils
- Tentatives de hameçonnage
- Tentatives de vol de données

En tant que professionnel de l’informatique/administrateur, vous pouvez afficher des informations sur les détections de menaces sur les [appareils Windows 10 qui sont déployés dans Intune](/mem/intune/enrollment/device-enrollment) dans le centre d’administration 365 de Microsoft. Vous verrez des informations récapitulatives, telles que :

- Nombre de périphériques nécessitant une protection antivirus
- Nombre de périphériques qui ne respectent pas les stratégies de sécurité
- Nombre de menaces actuellement actives, atténuées ou résolues

Vous disposez de plusieurs options pour afficher des informations spécifiques sur les périphériques et les détections de menace :

- Page **périphériques actifs** dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">centre d’administration 365 de Microsoft</a>. Consultez [la rubrique Manage Threat Detections sur la page périphériques actifs](#manage-threat-detections-on-the-active-devices-page) de cet article.
- Page **menaces actives** dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">centre d’administration 365 de Microsoft</a>. Voir [Manage Threat Detections sur la page Threats active](#manage-threat-detections-on-the-active-threats-page) dans cet article.
- La page **antivirus** dans le <a href="https://endpoint.microsoft.com" target="_blank">Gestionnaire de points de terminaison Microsoft</a>. Consultez la rubrique [Manage Threat Detections in Microsoft Endpoint Manager](#manage-threat-detections-in-microsoft-endpoint-manager) dans cet article.

Pour plus d’informations, consultez la rubrique [menaces détectées par l’antivirus Microsoft Defender](threats-detected-defender-av.md).

## <a name="manage-threat-detections-on-the-active-devices-page"></a>Gérer les détections de menaces sur la page **périphériques actifs**

La procédure suivante s’applique aux clients qui disposent de Microsoft 365 Business Premium.

1. Accédez au centre d’administration 365 de Microsoft à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a> et connectez-vous.

2. Sur la page de navigation, sélectionnez **périphériques**  >  **actifs**. Vous verrez une liste des périphériques actifs et des détails, tels que l’état de protection, l’état de protection antivirus et le nombre de menaces actives détectées.

3. Sélectionnez un appareil pour afficher plus de détails sur ce périphérique et les actions disponibles. Un menu volant s’ouvre avec des recommandations et des actions disponibles, telles que la **stratégie de mise à jour**, la **mise à jour** de l’antivirus, l' **exécution** de l’analyse **complète**, et bien plus encore.

## <a name="manage-threat-detections-on-the-active-threats-page"></a>Gérer les détections de menaces sur la page **menaces actives**

La procédure suivante s’applique aux clients qui disposent de Microsoft 365 Business Premium. Les [appareils Windows 10 doivent être sécurisés](/microsoft-365/business/secure-win-10-pcs) et [apportés dans Intune](/mem/intune/enrollment/windows-enrollment-methods).

> [!NOTE]
> La page de la carte **antivirus Microsoft Defender** et **les menaces actives** sont déployées en plusieurs phases, de sorte que vous ne pouvez pas y accéder immédiatement.

1. Accédez au centre d’administration 365 de Microsoft à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a> et connectez-vous.

2. Sur la carte **antivirus Microsoft Defender** , sélectionnez **afficher les menaces actives**. (Vous pouvez également sélectionner **intégrité**  >  dans le volet de navigation **Menaces & antivirus**.)

3. Sur la page **menaces actives** , sélectionnez une menace détectée pour en savoir plus. Un menu volant s’ouvre avec des détails sur cette menace, y compris sur les appareils qui sont affectés.

4. Dans le menu volant, sélectionnez un appareil pour afficher les actions disponibles, comme la **stratégie de mise à jour**, la **mise à jour** de l’antivirus, l’exécution de l' **analyse rapide**, et bien plus encore.

## <a name="actions-you-can-take"></a>Actions que vous pouvez effectuer

Lorsque vous affichez les détails sur des menaces ou des périphériques spécifiques, vous verrez des recommandations et une ou plusieurs actions que vous pouvez effectuer. Le tableau suivant décrit les actions que vous pouvez voir.<br><br>

| Opération | Description |
|--|--|
| Configurer la protection | Vos stratégies de protection contre les menaces doivent être configurées. Sélectionnez le lien pour accéder à votre page de configuration de stratégie.<br><br>Vous avez besoin d’aide ? Voir [Manage Device Security with Endpoint Security Policies in Microsoft Intune](/mem/intune/protect/endpoint-security-policy). |
| Mettre à jour une stratégie | Vos stratégies antivirus et de protection en temps réel doivent être mises à jour ou configurées. Sélectionnez le lien pour accéder à la page Configuration de la stratégie.<br><br>Vous avez besoin d’aide ? Voir [Manage Device Security with Endpoint Security Policies in Microsoft Intune](/mem/intune/protect/endpoint-security-policy). |
| Exécuter l’analyse rapide | Lance une analyse antivirus rapide sur l’appareil, en se concentrant sur les emplacements courants où des programmes malveillants peuvent être enregistrés, tels que les clés de Registre et les dossiers de démarrage Windows connus. |
| Exécuter une analyse complète | Démarre une analyse antivirus complète sur l’appareil, en se concentrant sur les emplacements courants où un programme malveillant peut être enregistré, et sur l’ajout de chaque fichier et dossier sur l’appareil. Les résultats sont envoyés au [Gestionnaire de points de terminaison Microsoft](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager). |
| Mettre à jour les antivirus | Exige que l’appareil obtient des [mises à jour](https://go.microsoft.com/fwlink/?linkid=2149926) de la sécurité pour les antivirus et la protection contre les programmes malveillants. |
| Redémarrer l’appareil | Force un appareil Windows 10 à redémarrer dans un délai de cinq minutes.<br><br>**Important :** Le propriétaire ou l’utilisateur de l’appareil n’est pas automatiquement informé du redémarrage et risque de perdre le travail non enregistré. |

## <a name="manage-threat-detections-in-microsoft-endpoint-manager"></a>Gérer les détections de menaces dans le gestionnaire de points de terminaison Microsoft

Vous pouvez utiliser le gestionnaire de points de terminaison Microsoft pour gérer les détections de menaces. Les appareils Windows 10 doivent être [inscrit dans Intune](/mem/intune/enrollment/windows-enrollment-methods) (partie du gestionnaire de points de terminaison Microsoft).

1. Accédez au centre d’administration du gestionnaire de points de terminaison de Microsoft à l’adresse <a href="https://endpoint.microsoft.com" target="_blank">https://endpoint.microsoft.com</a> et connectez-vous.

2. Dans le volet de navigation, sélectionnez **sécurité du point de terminaison**.

3. Sous **gérer**, sélectionnez **antivirus**. Plusieurs onglets, tels que **Résumé**, points de **terminaison non intègres Windows 10** et **Windows 10, ont été détectés**.

4. Passez en revue les informations sous les onglets disponibles, puis effectuez toutes les opérations nécessaires.

Par exemple, supposons que les périphériques sont répertoriés sous l’onglet **programmes malveillants détectés par Windows 10** . Lorsque vous sélectionnez un appareil, certaines actions sont disponibles, telles que le **redémarrage**, l' **analyse rapide**, l' **analyse complète**, la **synchronisation** ou la **mise à jour des signatures**. Sélectionnez une action pour ce périphérique.

Le tableau suivant décrit les actions que vous pouvez voir dans le gestionnaire de points de terminaison Microsoft.<br><br>

| Opération | Description |
|--|--|
| Redémarrer | Force un appareil Windows 10 à redémarrer dans un délai de cinq minutes.<br><br>**Important :** Le propriétaire ou l’utilisateur de l’appareil n’est pas automatiquement informé du redémarrage et risque de perdre le travail non enregistré. |
| Analyse rapide | Lance une analyse antivirus rapide sur l’appareil, en se concentrant sur les emplacements courants où des programmes malveillants peuvent être enregistrés, tels que les clés de Registre et les dossiers de démarrage Windows connus. Les résultats sont envoyés au [Gestionnaire de points de terminaison Microsoft](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager). |
| Analyse complète | Démarre une analyse antivirus complète sur l’appareil, en se concentrant sur les emplacements courants où un programme malveillant peut être enregistré, et sur l’ajout de chaque fichier et dossier sur l’appareil. Les résultats sont envoyés au [Gestionnaire de points de terminaison Microsoft](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager). |
| Synchronisation | Nécessite un périphérique pour l’archivage avec Intune (partie du gestionnaire de points de terminaison Microsoft). Lorsque l’appareil Archive, l’appareil reçoit les actions ou les stratégies en attente affectées à l’appareil. |
| Mettre à jour les signatures | Exige que l’appareil obtient des [mises à jour](https://go.microsoft.com/fwlink/?linkid=2149926) de la sécurité pour les antivirus et la protection contre les programmes malveillants. |

> [!TIP]
> Pour plus d’informations, consultez la rubrique [Remote actions for Devices](/mem/intune/protect/endpoint-security-manage-devices#remote-actions-for-devices).

## <a name="how-to-submit-a-file-for-malware-analysis"></a>Procédure d’envoi d’un fichier pour l’analyse contre les programmes malveillants

Si vous pensez qu’un fichier a été manqué ou mal classé comme programme malveillant, vous pouvez l’envoyer à Microsoft pour analyse contre les programmes malveillants. Les utilisateurs et les administrateurs informatiques peuvent soumettre un fichier à des fins d’analyse. Visitez le site [https://www.microsoft.com/wdsi/filesubmission](https://www.microsoft.com/wdsi/filesubmission) .
