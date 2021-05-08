---
title: Gérer les faux positifs ou les faux négatifs dans AIR dans Microsoft 365 Defender
description: Un problème a-t-il été manqué ou détecté à tort par AIR dans Microsoft 365 Defender ? Découvrez comment soumettre des faux positifs ou des faux négatifs à Microsoft pour analyse.
keywords: automatisé, examen, alerte, correction, faux positif, faux négatif
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: how-to
ms.custom: autoir
ms.reviewer: evaldm, isco
ms.technology: m365d
ms.openlocfilehash: 727ca529dc1a16af778e01a08c9adcfe42b9b974
ms.sourcegitcommit: ff20f5b4e3268c7c98a84fb1cbe7db7151596b6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2021
ms.locfileid: "52245467"
---
# <a name="handle-false-positivesnegatives-in-automated-investigation-and-response-capabilities"></a>Gérer les faux positifs/négatifs dans les fonctionnalités automatisées d’examen et de réponse

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Les faux positifs/négatifs peuvent parfois se produire avec n’importe quelle solution de protection contre les menaces. Si [des fonctionnalités](m365d-autoir.md) d’investigation et de réponse automatisées dans Microsoft 365 Defender ont manqué ou détecté un problème, votre équipe des opérations de sécurité peut suivre les étapes suivantes :

- [Signaler un faux positif/négatif à Microsoft](#report-a-false-positivenegative-to-microsoft-for-analysis);
- [Ajuster vos alertes](#adjust-an-alert-to-prevent-false-positives-from-recurring) (si nécessaire) ; et 
- [Annuler les actions de correction qui ont été prises sur les appareils.](#undo-a-remediation-action-that-was-taken-on-a-device) 

Les sections suivantes décrivent comment effectuer ces tâches.

## <a name="report-a-false-positivenegative-to-microsoft-for-analysis"></a>Signaler un faux positif/négatif à Microsoft pour analyse

|Élément manqué ou détecté de manière erronée |Service  |Procédure  |
|---------|---------|---------|
|- Message électronique <br/>- Pièce jointe d’un e-mail <br/>- URL dans un message électronique<br/>- URL dans un fichier Office de données      |[Microsoft Defender pour Office 365](/microsoft-365/security/office-365-security/defender-for-office-365)        |[Soumettre des messages suspects de courrier indésirable, d’hameçonnage, d’URL et de fichiers à Microsoft pour analyse](../office-365-security/admin-submission.md)         |
|Fichier ou application sur un appareil    |[Microsoft Defender pour point de terminaison](/windows/security/threat-protection)         |[Envoyer un fichier à Microsoft pour analyse des programmes malveillants](https://www.microsoft.com/wdsi/filesubmission)         |

## <a name="adjust-an-alert-to-prevent-false-positives-from-recurring"></a>Ajuster une alerte pour éviter que les faux positifs ne se répètent

|Scénario |Service |Procédure |
|--------|--------|--------|
|- Une alerte est déclenchée par un usage légitime <br/>- Une alerte est inexacte    |[Microsoft Cloud App Security](/cloud-app-security)<br/> ou <br/>[Azure Advanced Threat Detection](/azure/security/fundamentals/threat-detection)         |[Gérer les alertes dans le portail Sécurité des applications cloud web](/cloud-app-security/managing-alerts)         |
|Un fichier, une adresse IP, une URL ou un domaine est traité comme un programme malveillant sur un appareil, même s’il est sûr|[Microsoft Defender pour point de terminaison](/windows/security/threat-protection) |[Créer un indicateur personnalisé avec une action « Autoriser »](/windows/security/threat-protection/microsoft-defender-atp/manage-indicators) |

## <a name="undo-a-remediation-action-that-was-taken-on-a-device"></a>Annuler une action de correction qui a été prise sur un appareil

Si une action de correction a été entreprise sur une entité (par exemple, un appareil ou un message électronique) et que l’entité concernée n’est pas réellement une menace, votre équipe des opérations de sécurité peut annuler l’action de correction dans le centre de [correction.](m365d-action-center.md)

1. Accédez à [https://security.microsoft.com](https://security.microsoft.com) et connectez-vous. 
2. Dans le volet de navigation, choisissez **Centre de notifications**. 
3. Sous **l’onglet** Historique, sélectionnez une action à annuler. Son volet volant s’ouvre.
4. Dans le volet volant, sélectionnez **Annuler.**

> [!TIP]
> Voir [Annuler les actions terminées.](m365d-autoir-actions.md#undo-completed-actions)

## <a name="see-also"></a>Voir aussi

- [Consulter les détails et les résultats d'un examen automatisé](m365d-autoir-results.md)
- [Recherche proactive des menaces avec le recherche avancée dans Microsoft 365 Defender](advanced-hunting-overview.md)
- [Résoudre des faux négatifs/positifs dans Microsoft Defender pour point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/defender-endpoint-false-positives-negatives)