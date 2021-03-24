---
title: Comment signaler des faux positifs ou des faux négatifs à la suite d’un examen automatisé dans Microsoft Defender pour Office 365
description: Un problème a-t-il été manqué ou détecté à tort par AIR dans Microsoft Defender pour Office 365 ? Découvrez comment soumettre des faux positifs ou des faux négatifs à Microsoft pour analyse.
keywords: automatisé, examen, alerte, déclencheur, action, correction, faux positif, faux négatif
search.appverid: met150
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
ms.prod: m365-security
ms.date: 01/29/2021
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.topic: how-to
ms.custom:
- autoir
ms.technology: mdo
ms.openlocfilehash: 4476578939f2ece90c638c919c7e4d134ea2d9ec
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51065622"
---
# <a name="how-to-report-false-positivesnegatives-in-automated-investigation-and-response-capabilities"></a>Comment signaler les faux positifs/négatifs dans les fonctionnalités automatisées d’examen et de réponse

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 Plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Si des fonctionnalités d’investigation et de réponse automatisées [(AIR) dans Office 365](automated-investigation-response-office.md) ont manqué ou détecté un problème, il existe des étapes que votre équipe des opérations de sécurité peut suivre pour résoudre ce problème. Ces actions sont les suivantes :

- [Signalement d’un faux positif/négatif à Microsoft](#report-a-false-positivenegative-to-microsoft-for-analysis);
- [Ajustement des alertes](#adjust-an-alert-to-prevent-false-positives-from-recurring) (si nécessaire) ; et
- [Annuler les actions de correction qui ont été prises.](#undo-a-remediation-action)

Utilisez cet article comme guide.

## <a name="report-a-false-positivenegative-to-microsoft-for-analysis"></a>Signaler un faux positif/négatif à Microsoft pour analyse

Si AIR dans Microsoft Defender pour Office 365 a manqué un message électronique, une pièce jointe, une URL dans un message électronique ou une URL dans un fichier Office, vous pouvez soumettre des messages suspects de courrier indésirable, de hameçonnage, d’URL et de fichiers à Microsoft pour l’analyse [Office 365.](admin-submission.md)

Vous pouvez également [soumettre un fichier à Microsoft pour analyse des programmes malveillants.](https://www.microsoft.com/wdsi/filesubmission)

## <a name="adjust-an-alert-to-prevent-false-positives-from-recurring"></a>Ajuster une alerte pour éviter que les faux positifs ne se répètent

Si une alerte est déclenchée par un usage légitime ou si l’alerte est inexacte, vous pouvez gérer les [alertes](/cloud-app-security/managing-alerts)dans le portail Cloud App Security .

Si votre organisation utilise Microsoft Defender pour [endpoint](/windows/security/threat-protection) en plus d’Office 365 et qu’un fichier, une adresse IP, une URL ou un domaine est traité comme un programme malveillant sur un appareil, même s’il est sécurisé, vous pouvez créer un indicateur personnalisé avec une [action](/windows/security/threat-protection/microsoft-defender-atp/manage-indicators)« Autoriser » pour votre appareil.

## <a name="undo-a-remediation-action"></a>Annuler une action de correction

Dans la plupart des cas, si une action corrective a été prise sur un message électronique, une pièce jointe ou une URL, et que l’élément n’est pas une menace, votre équipe des opérations de sécurité peut annuler l’action de correction et prendre des mesures pour empêcher le faux positif de se reproduire. Vous pouvez utiliser [l’Explorateur de](#undo-an-action-using-threat-explorer) menaces ou l’onglet Actions pour [un examen](#undo-an-action-in-the-action-center) afin d’annuler une action.

> [!IMPORTANT]
> Assurez-vous que vous avez les autorisations nécessaires avant d’essayer d’effectuer les tâches suivantes.

### <a name="undo-an-action-using-threat-explorer"></a>Annuler une action à l’aide de l’Explorateur de menaces

Avec l’Explorateur de menaces, votre équipe des opérations de sécurité peut trouver un message électronique affecté par une action et éventuellement annuler l’action.

|Scénario|Options d’annuler|En savoir plus|
|---|---|---|
|Un message électronique a été acheminé vers le dossier Courrier indésirable d’un utilisateur|- Déplacer le message vers le dossier Éléments supprimés de l’utilisateur<br/>- Déplacer le message vers la boîte de réception de l’utilisateur<br/>- Supprimer le message|[Rechercher et examiner les e-mails malveillants qui ont été remis dans Office 365](investigate-malicious-email-that-was-delivered.md)|
|Un message électronique ou un fichier a été mis en quarantaine|- Libérer le courrier électronique ou le fichier<br/>- Supprimer le courrier électronique ou le fichier|[Gérer les messages mis en quarantaine en tant qu’administrateur](manage-quarantined-messages-and-files.md)|
|

### <a name="undo-an-action-in-the-action-center"></a>Annuler une action dans le centre de l’action

Dans le centre de correction, vous pouvez voir les actions de correction qui ont été prises et éventuellement annuler l’action.

1. Go to the Microsoft 365 security center ( <https://security.microsoft.com> ).
2. Dans le volet de navigation, sélectionnez **Centre de l’action.**
3. Sélectionnez **l’onglet** Historique pour afficher la liste des actions terminées.
4. Sélectionnez un élément. Son volet volant s’ouvre.
5. Dans le volet volant, sélectionnez **Annuler.** (Seules les actions qui peuvent être annulées auront **un bouton Annuler.)**

## <a name="see-also"></a>Voir aussi

- [Microsoft Defender pour Office 365](defender-for-office-365.md)
- [Enquêtes automatisées dans Microsoft Defender pour Office 365](office-365-air.md)
