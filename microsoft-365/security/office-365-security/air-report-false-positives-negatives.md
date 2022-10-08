---
title: Comment signaler des faux positifs ou des faux négatifs à la suite d’une enquête automatisée dans Microsoft Defender pour Office 365
description: Quelque chose a-t-il été manqué ou détecté à tort par AIR dans Microsoft Defender pour Office 365 ? Découvrez comment envoyer des faux positifs ou des faux négatifs à Microsoft à des fins d’analyse.
keywords: automatisé, investigation, alerte, déclencheur, action, correction, faux positif, faux négatif
search.appverid: met150
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
ms.service: microsoft-365-security
ms.date: 01/29/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- m365initiative-defender-office365
ms.topic: how-to
ms.custom:
- autoir
ms.subservice: mdo
ms.openlocfilehash: 6a7779ced613f5e6c175c2cd6a7181c2c4a00fa0
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68082858"
---
# <a name="how-to-report-false-positivesnegatives-in-automated-investigation-and-response-capabilities"></a>Comment signaler des faux positifs/négatifs dans les fonctionnalités d’investigation et de réponse automatisées

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 Plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Si [les fonctionnalités d’investigation et de réponse automatisées (AIR) dans Office 365](automated-investigation-response-office.md) manquées ou détectées à tort, votre équipe des opérations de sécurité peut effectuer des étapes pour la corriger. Ces actions sont les suivantes :

- [Signalement d’un faux positif/négatif à Microsoft](#report-a-false-positivenegative-to-microsoft-for-analysis) ;
- [Ajustement des alertes](#adjust-an-alert-to-prevent-false-positives-from-recurring) (si nécessaire) ; Et
- [Annulation des actions de correction qui ont été effectuées](#undo-a-remediation-action).

Utilisez cet article comme guide.

## <a name="report-a-false-positivenegative-to-microsoft-for-analysis"></a>Signaler un faux positif/négatif à Microsoft à des fins d’analyse

Si AIR dans Microsoft Defender pour Office 365 manqué un e-mail, une pièce jointe, une URL dans un e-mail ou une URL dans un fichier Office, vous pouvez [envoyer des courriers indésirables, des hameçonnages, des URL et des fichiers suspects à Microsoft pour Office 365 analyse](admin-submission.md).

Vous pouvez également [envoyer un fichier à Microsoft pour l’analyse des programmes malveillants](https://www.microsoft.com/wdsi/filesubmission).

## <a name="adjust-an-alert-to-prevent-false-positives-from-recurring"></a>Ajuster une alerte pour éviter que les faux positifs ne se reproduisent

Si une alerte est déclenchée par une utilisation légitime ou si elle est inexacte, vous pouvez [gérer les alertes dans le portail Defender pour Cloud Apps](/cloud-app-security/managing-alerts).

Si votre organisation utilise [Microsoft Defender pour point de terminaison](/windows/security/threat-protection) en plus de Office 365 et qu’un fichier, une adresse IP, une URL ou un domaine sont traités comme des programmes malveillants sur un appareil, même s’il est sécurisé, vous pouvez [créer un indicateur personnalisé avec une action « Autoriser » pour votre appareil](/windows/security/threat-protection/microsoft-defender-atp/manage-indicators).

## <a name="undo-a-remediation-action"></a>Annuler une action de correction

Dans la plupart des cas, si une action de correction a été effectuée sur un e-mail, une pièce jointe ou une URL, et que l’élément n’est en fait pas une menace, votre équipe des opérations de sécurité peut annuler l’action de correction et prendre des mesures pour empêcher le faux positif de se reproduise. Vous pouvez utiliser [l’Explorateur de menaces](#undo-an-action-using-threat-explorer) ou l’onglet [Actions pour une enquête](#undo-an-action-in-the-action-center) afin d’annuler une action.

> [!IMPORTANT]
> Vérifiez que vous disposez des autorisations nécessaires avant de tenter d’effectuer les tâches suivantes.

### <a name="undo-an-action-using-threat-explorer"></a>Annuler une action à l’aide de l’Explorateur de menaces

Avec l’Explorateur de menaces, votre équipe des opérations de sécurité peut trouver un e-mail affecté par une action et éventuellement annuler l’action.

|Scénario|Options d’annulation|En savoir plus|
|---|---|---|
|Un e-mail a été routée vers le dossier Junk Email d’un utilisateur|<ul><li>Déplacer le message vers le dossier Éléments supprimés de l’utilisateur</li><li>Déplacer le message vers la boîte de réception de l’utilisateur</li><li>Supprimer le message</li></ul>|[Rechercher et examiner les e-mails malveillants qui ont été remis dans Office 365](investigate-malicious-email-that-was-delivered.md)|
|Un e-mail ou un fichier a été mis en quarantaine|<ul><li>Libérer l’e-mail ou le fichier</li><li> Supprimer l’e-mail ou le fichier</li></ul>|[Gérer les messages mis en quarantaine en tant qu’administrateur](manage-quarantined-messages-and-files.md)|

### <a name="undo-an-action-in-the-action-center"></a>Annuler une action dans le centre d’action

Dans le Centre d’actions, vous pouvez voir les actions de correction qui ont été effectuées et qui peuvent éventuellement annuler l’action.

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez au Centre d’actions en sélectionnant **Centre d’actions**. Pour accéder directement au Centre d’actions, utilisez <https://security.microsoft.com/action-center/>.
2. Dans le Centre d’actions, sélectionnez l’onglet **Historique** pour afficher la liste des actions terminées.
3. Sélectionnez un élément. Son volet volant s’ouvre.
4. Dans le volet de menu volant, sélectionnez **Annuler**. (Seules les actions pouvant être annulées auront un bouton **Annuler** .)

## <a name="see-also"></a>Voir aussi

- [Microsoft Defender pour Office 365](defender-for-office-365.md)
- [Investigations automatisées dans Microsoft Defender pour Office 365](office-365-air.md)
