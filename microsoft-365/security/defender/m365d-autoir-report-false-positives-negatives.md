---
title: Résoudre les faux positifs ou les faux négatifs dans Microsoft 365 Defender
description: Un problème a-t-il été détecté par AIR dans Microsoft 365 Defender ? Découvrez comment envoyer des faux positifs ou des faux négatifs à Microsoft à des fins d’analyse.
keywords: automatisé, investigation, alerte, correction, faux positif, faux négatif
search.appverid: met150
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: how-to
ms.custom:
- autoir
- admindeeplinkDEFENDER
ms.reviewer: evaldm, isco
ms.openlocfilehash: cab16efa7f5118a4b9fce44713536dc043dd6b7b
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67482381"
---
# <a name="address-false-positives-or-false-negatives-in-microsoft-365-defender"></a>Résoudre les faux positifs ou les faux négatifs dans Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Des faux positifs ou négatifs peuvent parfois se produire avec n’importe quelle solution de protection contre les menaces. Si [les fonctionnalités d’investigation et de réponse automatisées](m365d-autoir.md) dans Microsoft 365 Defender un élément manqué ou détecté à tort, votre équipe des opérations de sécurité peut effectuer les étapes suivantes :

- [Signaler un faux positif/négatif à Microsoft](#report-a-false-positivenegative-to-microsoft-for-analysis)
- [Ajuster vos alertes](#adjust-an-alert-to-prevent-false-positives-from-recurring) (si nécessaire)
- [Annuler les actions de correction qui ont été effectuées sur les appareils](#undo-a-remediation-action-that-was-taken-on-a-device)

Les sections suivantes décrivent comment effectuer ces tâches.

## <a name="report-a-false-positivenegative-to-microsoft-for-analysis"></a>Signaler un faux positif/négatif à Microsoft à des fins d’analyse

|Élément manqué ou détecté à tort |Service  |Procédure  |
|---------|---------|---------|
|- message Email <br/>- Email pièce jointe <br/>- URL dans un e-mail<br/>- URL dans un fichier Office      |[Microsoft Defender pour Office 365](/microsoft-365/security/office-365-security/defender-for-office-365)        |[Envoyer des courriers indésirables, des hameçonnages, des URL et des fichiers suspects à Microsoft à des fins d’analyse](../office-365-security/admin-submission.md)         |
|Fichier ou application sur un appareil    |[Microsoft Defender pour point de terminaison](/windows/security/threat-protection)         |[Envoyer un fichier à Microsoft pour l’analyse des programmes malveillants](https://www.microsoft.com/wdsi/filesubmission)         |

## <a name="adjust-an-alert-to-prevent-false-positives-from-recurring"></a>Ajuster une alerte pour éviter que les faux positifs ne se reproduisent

|Scénario |Service |Procédure |
|--------|--------|--------|
|- Une alerte est déclenchée par une utilisation légitime <br/>- Une alerte est inexacte    |[Microsoft Defender for Cloud Apps](/cloud-app-security)<br/> ou <br/>[Protection contre les menaces Azure](/azure/security/fundamentals/threat-detection)         |[Gérer les alertes dans le portail Defender pour Cloud Apps](/cloud-app-security/managing-alerts)         |
|Un fichier, une adresse IP, une URL ou un domaine est traité comme un programme malveillant sur un appareil, même s’il est sécurisé|[Microsoft Defender pour point de terminaison](/windows/security/threat-protection) |[Créer un indicateur personnalisé avec une action « Autoriser »](/windows/security/threat-protection/microsoft-defender-atp/manage-indicators) |

## <a name="undo-a-remediation-action-that-was-taken-on-a-device"></a>Annuler une action de correction qui a été effectuée sur un appareil

Si une action de correction a été effectuée sur une entité (par exemple, un appareil ou un e-mail) et que l’entité affectée n’est pas réellement une menace, votre équipe des opérations de sécurité peut annuler l’action de correction dans le [Centre d’actions](m365d-action-center.md).

1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a> et connectez-vous. 
2. Dans le volet de navigation, choisissez **Centre de notifications**. 
3. Sous l’onglet **Historique** , sélectionnez une action à annuler. Son volet volant s’ouvre.
4. Dans le volet de menu volant, sélectionnez **Annuler**.

> [!TIP]
> Voir [Annuler les actions terminées](m365d-autoir-actions.md#undo-completed-actions).

## <a name="see-also"></a>Voir aussi

- [Consulter les détails et les résultats d'un examen automatisé](m365d-autoir-results.md)
- [Recherche proactive des menaces avec repérage avancé dans Microsoft 365 Defender](advanced-hunting-overview.md)
