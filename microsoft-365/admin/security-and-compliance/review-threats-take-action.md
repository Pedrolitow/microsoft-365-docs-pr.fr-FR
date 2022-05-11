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
description: Découvrez comment examiner et gérer les menaces détectées par Antivirus Microsoft Defender sur vos appareils Windows 10.
ms.openlocfilehash: 9b819edc21d6cfcac663c54e15b1a060b2b16fa2
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2022
ms.locfileid: "65319306"
---
# <a name="review-detected-threats-and-take-action"></a>Examiner les menaces détectées et prendre des mesures

Dès qu’un fichier ou un logiciel malveillant est détecté, Antivirus Microsoft Defender le bloque et l’empêche de s’exécuter. Une fois la protection fournie par le cloud activée, les menaces nouvellement détectées sont ajoutées au moteur antivirus et anti-programme malveillant afin que vos autres appareils et utilisateurs soient également protégés.

Antivirus Microsoft Defender détecte et protège contre les types de menaces suivants :

- Virus, programmes malveillants et menaces web sur les appareils
- Tentatives d’hameçonnage
- Tentatives de vol de données

En tant que professionnel de l’informatique/administrateur, vous pouvez afficher des informations sur les détections de menaces sur [Windows 10 appareils inscrits dans Intune](/mem/intune/enrollment/device-enrollment) dans le Centre d'administration Microsoft 365. Vous verrez des informations récapitulatives, telles que :

- Combien d’appareils ont besoin d’une protection antivirus
- Nombre d’appareils non conformes aux stratégies de sécurité
- Nombre de menaces actuellement actives, atténuées ou résolues

Vous disposez de plusieurs options pour afficher des informations spécifiques sur les détections de menaces et les appareils :

- Page **Appareils actifs** dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d'administration Microsoft 365</a>. Consultez [Gérer les détections de menaces dans la page Appareils actifs](#manage-threat-detections-on-the-active-devices-page) de cet article.
- Page **Menaces actives** dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d'administration Microsoft 365</a>. Consultez [Gérer les détections de menaces dans la page Menaces actives](#manage-threat-detections-on-the-active-threats-page) de cet article.
- Page **Antivirus** dans <a href="https://go.microsoft.com/fwlink/p/?linkid=2150463" target="_blank">Microsoft Endpoint Manager</a>. Consultez [Gérer les détections de menaces dans Microsoft Endpoint Manager](#manage-threat-detections-in-microsoft-endpoint-manager) dans cet article.

Pour en savoir plus, consultez [Menaces détectées par Antivirus Microsoft Defender](threats-detected-defender-av.md).

## <a name="manage-threat-detections-on-the-active-devices-page"></a>Gérer les détections de menaces sur la page **Appareils actifs**

La procédure suivante s’applique aux clients qui ont Microsoft 365 Business Premium.

1. Accédez au Centre d'administration Microsoft 365 et <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a> connectez-vous.

2. Dans la page de navigation, sélectionnez **AppareilsActive** > . Vous verrez une liste des appareils actifs et des détails, tels que l’état de protection, l’état de protection antivirus (AV) et le nombre de menaces actives détectées.

3. Sélectionnez un appareil pour afficher plus de détails sur cet appareil et les actions disponibles. Un menu volant s’ouvre avec des recommandations et des actions disponibles, telles que **la stratégie de mise à jour**, **l’antivirus update**, **l’exécution d’une analyse rapide**, **l’exécution d’une analyse complète**, etc.

## <a name="manage-threat-detections-on-the-active-threats-page"></a>Gérer les détections de menaces sur la page **Menaces actives**

La procédure suivante s’applique aux clients qui ont Microsoft 365 Business Premium. [Windows 10 appareils doivent être sécurisés](../setup/secure-win-10-pcs.md) et [inscrits dans Intune](/mem/intune/enrollment/windows-enrollment-methods).

> [!NOTE]
> La page **de Antivirus Microsoft Defender** carte et **menaces actives** étant déployée par phases, vous n’avez peut-être pas accès immédiatement à celles-ci.

1. Accédez au Centre d'administration Microsoft 365 et <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a> connectez-vous.

2. Dans la carte **Antivirus Microsoft Defender**, sélectionnez **Afficher les menaces actives**. (Sinon, dans le volet de navigation, sélectionnez **Intégrité** >  **Menaces & antivirus**.)

3. Dans la page **Menaces actives** , sélectionnez une menace détectée pour en savoir plus. Un menu volant s’ouvre avec des détails sur cette menace, y compris les appareils concernés.

4. Dans le menu volant, sélectionnez un appareil pour afficher les actions disponibles, telles que **la stratégie de mise à jour**, **l’antivirus de mise à jour**, **l’exécution** d’une analyse rapide, etc.

## <a name="actions-you-can-take"></a>Actions que vous pouvez effectuer

Lorsque vous affichez des détails sur des menaces ou des appareils spécifiques, vous voyez des recommandations et une ou plusieurs actions que vous pouvez effectuer. Le tableau suivant décrit les actions que vous pouvez voir.<br><br>

| Opération | Description |
|--|--|
| Configurer la protection | Vos stratégies de protection contre les menaces doivent être configurées. Sélectionnez le lien pour accéder à la page de configuration de votre stratégie.<br><br>Besoin d’aide ? Consultez [Gérer la sécurité des appareils avec les stratégies de sécurité des points de terminaison dans Microsoft Intune](/mem/intune/protect/endpoint-security-policy). |
| Mettre à jour une stratégie | Vos stratégies de protection antivirus et en temps réel doivent être mises à jour ou configurées. Sélectionnez le lien pour accéder à la page de configuration de la stratégie.<br><br>Besoin d’aide ? Consultez [Gérer la sécurité des appareils avec les stratégies de sécurité des points de terminaison dans Microsoft Intune](/mem/intune/protect/endpoint-security-policy). |
| Exécuter une analyse rapide | Démarre une analyse antivirus rapide sur l’appareil, en se concentrant sur les emplacements courants où les programmes malveillants peuvent être inscrits, tels que les clés de Registre et les dossiers de démarrage connus Windows. |
| Exécuter l’analyse complète | Démarre une analyse antivirus complète sur l’appareil, en se concentrant sur les emplacements courants où les programmes malveillants peuvent être inscrits, ainsi que sur chaque fichier et dossier de l’appareil. Les résultats sont envoyés à [Microsoft Endpoint Manager](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager). |
| Mettre à jour l’antivirus | Requiert que l’appareil obtienne des [mises à jour du renseignement de sécurité](https://go.microsoft.com/fwlink/?linkid=2149926) pour la protection antivirus et anti-programme malveillant. |
| Redémarrer l’appareil | Force un appareil Windows 10 à redémarrer dans un délai de cinq minutes.<br><br>**IMPORTANT:** Le propriétaire ou l’utilisateur de l’appareil n’est pas automatiquement averti du redémarrage et peut perdre le travail non enregistré. |

## <a name="manage-threat-detections-in-microsoft-endpoint-manager"></a>Gérer les détections de menaces dans Microsoft Endpoint Manager

Vous pouvez utiliser Microsoft Endpoint Manager pour gérer les détections de menaces. Windows 10 appareils doivent être [inscrits dans Intune](/mem/intune/enrollment/windows-enrollment-methods) (partie de Microsoft Endpoint Manager).

1. Accédez au centre <a href="https://go.microsoft.com/fwlink/p/?linkid=2150463" target="_blank">https://endpoint.microsoft.com</a> d’administration Microsoft Endpoint Manager et connectez-vous.

2. Dans le volet de navigation, sélectionnez **Sécurité du point de terminaison**.

3. Sous **Gérer**, sélectionnez **Antivirus**. Vous verrez plusieurs onglets, tels que **Résumé**, **Windows 10 points de terminaison non sains** et **Windows 10 programmes malveillants détectés**.

4. Passez en revue les informations sur les onglets disponibles, puis effectuez les actions nécessaires.

Par exemple, supposons que les appareils soient répertoriés sous **l’onglet Windows 10 programmes malveillants détectés**. Lorsque vous sélectionnez un appareil, certaines actions sont disponibles, telles que **le redémarrage**, **l’analyse rapide**, **l’analyse complète**, la **synchronisation** ou **la mise à jour des signatures**. Sélectionnez une action pour cet appareil.

Le tableau suivant décrit les actions que vous pouvez voir dans Microsoft Endpoint Manager.<br><br>

| Opération | Description |
|--|--|
| Redémarrer | Force un appareil Windows 10 à redémarrer dans un délai de cinq minutes.<br><br>**IMPORTANT:** Le propriétaire ou l’utilisateur de l’appareil n’est pas automatiquement averti du redémarrage et peut perdre le travail non enregistré. |
| Analyse rapide | Démarre une analyse antivirus rapide sur l’appareil, en se concentrant sur les emplacements courants où les programmes malveillants peuvent être inscrits, tels que les clés de Registre et les dossiers de démarrage connus Windows. Les résultats sont envoyés à [Microsoft Endpoint Manager](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager). |
| Analyse complète | Démarre une analyse antivirus complète sur l’appareil, en se concentrant sur les emplacements courants où les programmes malveillants peuvent être inscrits, ainsi que sur chaque fichier et dossier de l’appareil. Les résultats sont envoyés à [Microsoft Endpoint Manager](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager). |
| Synchronisation | Nécessite qu’un appareil s’archive auprès de Intune (partie de Microsoft Endpoint Manager). Lorsque l’appareil s’enregistre, l’appareil reçoit toutes les actions ou stratégies en attente affectées à l’appareil. |
| Mettre à jour les signatures | Requiert que l’appareil obtienne des [mises à jour du renseignement de sécurité](https://go.microsoft.com/fwlink/?linkid=2149926) pour la protection antivirus et anti-programme malveillant. |

> [!TIP]
> Pour plus d’informations, consultez [Actions à distance pour les appareils](/mem/intune/protect/endpoint-security-manage-devices#remote-actions-for-devices).

## <a name="how-to-submit-a-file-for-malware-analysis"></a>Envoi d’un fichier pour l’analyse des programmes malveillants

Si vous avez un fichier que vous pensez avoir été manqué ou classé à tort en tant que programme malveillant, vous pouvez envoyer ce fichier à Microsoft pour analyse des programmes malveillants. Les utilisateurs et les administrateurs informatiques peuvent soumettre un fichier à des fins d’analyse. Visitez [https://www.microsoft.com/wdsi/filesubmission](https://www.microsoft.com/wdsi/filesubmission).

## <a name="see-also"></a>Voir aussi

[Meilleures pratiques pour sécuriser les plans Microsoft 365 pour les PME](../../admin/security-and-compliance/secure-your-business-data.md)

[Vue d’ensemble de Microsoft Defender pour les PME](../../security/defender-business/mdb-overview.md) (Defender entreprise est en cours de déploiement pour Microsoft 365 Business Premium clients, à compter du 1er mars 2022)