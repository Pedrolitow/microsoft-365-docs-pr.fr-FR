---
title: Examiner les menaces détectées sur les appareils et prendre des mesures
f1.keywords: NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: conceptual
ms.service: microsoft-365-security
ms.subservice: other
ms.date: 09/15/2022
ms.localizationpriority: medium
ms.collection:
- m365-security
- tier1
search.appverid: MET150
description: Découvrez comment examiner et gérer les menaces détectées par Microsoft Defender Antivirus sur vos appareils Windows.
ms.openlocfilehash: c9dab2a71d7ce8ce352ae1315be9ff0453215108
ms.sourcegitcommit: 0283c436f3ba61a708b52b57a1955f5ea74376a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2022
ms.locfileid: "68097662"
---
# <a name="review-detected-threats"></a>Examiner les menaces détectées

Dès qu’un fichier ou un logiciel malveillant est détecté, Microsoft Defender le bloque et l’empêche de s’exécuter. Une fois la protection fournie par le cloud activée, les menaces nouvellement détectées sont ajoutées au moteur antivirus et anti-programme malveillant afin que vos autres appareils et utilisateurs soient également protégés.

Microsoft Defender Antivirus détecte et protège contre les types de menaces suivants :

- Virus, programmes malveillants et menaces web sur les appareils
- Tentatives d’hameçonnage
- Tentatives de vol de données

En tant que professionnel de l’informatique/administrateur, vous pouvez afficher des informations sur les détections de menaces sur les [appareils Windows inscrits dans Intune](/mem/intune/enrollment/device-enrollment) dans le Centre d'administration Microsoft 365. Vous verrez des informations récapitulatives, telles que :

- Combien d’appareils ont besoin d’une protection antivirus
- Nombre d’appareils non conformes aux stratégies de sécurité
- Nombre de menaces actuellement actives, atténuées ou résolues

## <a name="actions-you-can-take"></a>Actions que vous pouvez effectuer

Lorsque vous affichez des détails sur des menaces ou des appareils spécifiques, vous voyez des recommandations et une ou plusieurs actions que vous pouvez effectuer. Le tableau suivant décrit les actions que vous pouvez voir.<br><br>

| Opération | Description |
|--|--|
| Configurer la protection | Vos stratégies de protection contre les menaces doivent être configurées. Sélectionnez le lien pour accéder à la page de configuration de votre stratégie.<br><br>Besoin d’aide ? Consultez [Gérer la sécurité des appareils avec les stratégies de sécurité des points de terminaison dans Microsoft Intune](/mem/intune/protect/endpoint-security-policy). |
| Mettre à jour une stratégie | Vos stratégies de protection antivirus et en temps réel doivent être mises à jour ou configurées. Sélectionnez le lien pour accéder à la page de configuration de la stratégie.<br><br>Besoin d’aide ? Consultez [Gérer la sécurité des appareils avec les stratégies de sécurité des points de terminaison dans Microsoft Intune](/mem/intune/protect/endpoint-security-policy). |
| Exécuter une analyse rapide | Démarre une analyse antivirus rapide sur l’appareil, en se concentrant sur les emplacements courants où les programmes malveillants peuvent être inscrits, tels que les clés de Registre et les dossiers de démarrage Windows connus. |
| Exécuter l’analyse complète | Démarre une analyse antivirus complète sur l’appareil, en se concentrant sur les emplacements courants où les programmes malveillants peuvent être inscrits, ainsi que sur chaque fichier et dossier de l’appareil. Les résultats sont envoyés à [Microsoft Endpoint Manager](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager). |
| Mettre à jour l’antivirus | Requiert que l’appareil obtienne des [mises à jour du renseignement de sécurité](https://go.microsoft.com/fwlink/?linkid=2149926) pour la protection antivirus et anti-programme malveillant. |
| Redémarrer l’appareil | Force un appareil Windows à redémarrer dans un délai de cinq minutes.<br><br>**IMPORTANT:** Le propriétaire ou l’utilisateur de l’appareil n’est pas automatiquement averti du redémarrage et peut perdre le travail non enregistré. |

## <a name="view-and-manage-threat-detections-in-the-microsoft-365-defender-portal"></a>Afficher et gérer les détections de menaces dans le portail Microsoft 365 Defender

1. Accédez au ([portail Microsoft 365 Defender](https://security.microsoft.com)) et connectez-vous.

1. Dans le volet de navigation, choisissez **Analyse des menaces** pour voir toutes les menaces actuelles. Elles sont classées par gravité et type de menace.

1. Cliquez sur une menace pour afficher plus de détails sur la menace.

1. Dans le tableau, vous pouvez filtrer les alertes en fonction d’un certain nombre de critères.

## <a name="manage-threat-detections-in-microsoft-intune"></a>Gérer les détections de menaces dans Microsoft InTune

Vous pouvez également utiliser Microsoft Endpoint Manager pour gérer les détections de menaces. Tout d’abord, tous les appareils, qu’ils soient Windows, iOS ou Android, doivent être [inscrits dans Intune](/mem/intune/enrollment/windows-enrollment-methods) (partie de Microsoft Endpoint Manager).

1. Accédez au Centre d’administration Microsoft Endpoint Manager et <a href="https://go.microsoft.com/fwlink/p/?linkid=2150463" target="_blank">https://endpoint.microsoft.com</a> connectez-vous.

2. Dans le volet de navigation, sélectionnez **Sécurité du point de terminaison**.

3. Sous **Gérer**, sélectionnez **Antivirus**. Vous verrez des onglets pour **le résumé**, **les points de terminaison non sains et les programmes malveillants actifs**.

4. Passez en revue les informations sur les onglets disponibles, puis effectuez les actions nécessaires.

Par exemple, supposons que les appareils sont répertoriés sous l’onglet **Programmes malveillants actifs** . Lorsque vous sélectionnez un appareil, certaines actions sont disponibles, telles que **le redémarrage**, **l’analyse rapide**, **l’analyse complète**, la **synchronisation** ou **la mise à jour des signatures**. Sélectionnez une action pour cet appareil.

Le tableau suivant décrit les actions que vous pouvez voir dans Microsoft Endpoint Manager.<br><br>

| Opération | Description |
|--|--|
| Redémarrer | Force un appareil Windows à redémarrer dans un délai de cinq minutes.<br><br>**IMPORTANT:** Le propriétaire ou l’utilisateur de l’appareil n’est pas automatiquement averti du redémarrage et peut perdre le travail non enregistré. |
| Analyse rapide | Démarre une analyse antivirus rapide sur l’appareil, en se concentrant sur les emplacements courants où les programmes malveillants peuvent être inscrits, tels que les clés de Registre et les dossiers de démarrage Windows connus. Les résultats sont envoyés à [Microsoft Endpoint Manager](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager). |
| Analyse complète | Démarre une analyse antivirus complète sur l’appareil, en se concentrant sur les emplacements courants où les programmes malveillants peuvent être inscrits, ainsi que sur chaque fichier et dossier de l’appareil. Les résultats sont envoyés à [Microsoft Endpoint Manager](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager). |
| Synchronisation | Nécessite qu’un appareil s’archive auprès de Intune (partie de Microsoft Endpoint Manager). Lorsque l’appareil s’enregistre, l’appareil reçoit toutes les actions ou stratégies en attente affectées à l’appareil. |
| Mettre à jour les signatures | Requiert que l’appareil obtienne des [mises à jour du renseignement de sécurité](https://go.microsoft.com/fwlink/?linkid=2149926) pour la protection antivirus et anti-programme malveillant. |

> [!TIP]
> Pour plus d’informations, consultez [Actions à distance pour les appareils](/mem/intune/protect/endpoint-security-manage-devices#remote-actions-for-devices).

## <a name="how-to-submit-a-file-for-malware-analysis"></a>Envoi d’un fichier pour l’analyse des programmes malveillants

Si vous avez un fichier que vous pensez avoir été manqué ou classé à tort en tant que programme malveillant, vous pouvez envoyer ce fichier à Microsoft pour analyse des programmes malveillants. Les utilisateurs et les administrateurs informatiques peuvent soumettre un fichier à des fins d’analyse. Visitez [https://www.microsoft.com/wdsi/filesubmission](https://www.microsoft.com/wdsi/filesubmission).

## <a name="see-also"></a>Voir aussi

[Meilleures pratiques pour sécuriser les plans Microsoft 365 pour les PME](../admin/security-and-compliance/secure-your-business-data.md)

[Vue d’ensemble de Microsoft Defender pour entreprises](../security/defender-business/mdb-overview.md) (Defender entreprise est en cours de déploiement pour Microsoft 365 Business Premium clients, à compter du 1er mars 2022)
