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
author: JoeDavies-MSFT
ms.author: josephd
ms.prod: m365-security
ms.date: 01/29/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.topic: how-to
ms.custom:
- autoir
ms.technology: mdo
ms.openlocfilehash: 0096cb5f8c0d878ecc888de74f1548c77ed0dda9
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60196644"
---
# <a name="how-to-report-false-positivesnegatives-in-automated-investigation-and-response-capabilities"></a>Comment signaler les faux positifs/négatifs dans les fonctionnalités automatisées d’examen et de réponse

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 Plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Si des fonctionnalités d’investigation et de réponse automatisées [(AIR)](automated-investigation-response-office.md) Office 365 manquées ou détectées à tort, il existe des étapes que votre équipe des opérations de sécurité peut suivre pour résoudre ce problème. Ces actions sont les suivantes :

- [Signalement d’un faux positif/négatif à Microsoft](#report-a-false-positivenegative-to-microsoft-for-analysis);
- [Ajustement des alertes](#adjust-an-alert-to-prevent-false-positives-from-recurring) (si nécessaire) ; et
- [Annuler les actions de correction qui ont été prises.](#undo-a-remediation-action)

Utilisez cet article comme guide.

## <a name="report-a-false-positivenegative-to-microsoft-for-analysis"></a>Signaler un faux positif/négatif à Microsoft pour analyse

Si AIR dans Microsoft Defender pour Office 365 a manqué un message électronique, une pièce jointe, une URL dans un message électronique ou une URL dans un fichier Office, vous pouvez soumettre des messages suspects de courrier [indésirable,](admin-submission.md)de hameçonnage, d’URL et de fichiers à Microsoft pour l’analyse Office 365 .

Vous pouvez également [soumettre un fichier à Microsoft pour analyse des programmes malveillants.](https://www.microsoft.com/wdsi/filesubmission)

## <a name="adjust-an-alert-to-prevent-false-positives-from-recurring"></a>Ajuster une alerte pour éviter que les faux positifs ne se répètent

Si une alerte est déclenchée par un usage légitime ou si l’alerte est inexacte, vous pouvez gérer les alertes dans [le portail Sécurité des applications cloud.](/cloud-app-security/managing-alerts)

Si votre organisation utilise [Microsoft Defender](/windows/security/threat-protection) pour le point de terminaison en plus de Office 365 et qu’un fichier, une adresse IP, une URL ou un domaine est traité comme un programme malveillant sur un appareil, même s’il est sécurisé, vous pouvez créer un indicateur personnalisé avec une [action](/windows/security/threat-protection/microsoft-defender-atp/manage-indicators)« Autoriser » pour votre appareil.

## <a name="undo-a-remediation-action"></a>Annuler une action de correction

Dans la plupart des cas, si une action corrective a été prise sur un message électronique, une pièce jointe ou une URL, et que l’élément n’est pas une menace, votre équipe des opérations de sécurité peut annuler l’action de correction et prendre des mesures pour empêcher le faux positif de se reproduire. Vous pouvez utiliser [l’Explorateur de](#undo-an-action-using-threat-explorer) menaces ou l’onglet Actions pour [un examen](#undo-an-action-in-the-action-center) afin d’annuler une action.

> [!IMPORTANT]
> Assurez-vous que vous avez les autorisations nécessaires avant d’essayer d’effectuer les tâches suivantes.

### <a name="undo-an-action-using-threat-explorer"></a>Annuler une action à l’aide de l’Explorateur de menaces

Avec l’Explorateur de menaces, votre équipe des opérations de sécurité peut rechercher un message électronique affecté par une action et éventuellement annuler l’action.

<br>

****

|Scénario|Options d’annuler|En savoir plus|
|---|---|---|
|Un message électronique a été acheminé vers le dossier Courrier indésirable d’un utilisateur|<ul><li>Déplacer le message vers le dossier Éléments supprimés de l’utilisateur</li><li>Déplacer le message vers la boîte de réception de l’utilisateur</li><li>Supprimer le message</li></ul>|[Rechercher et examiner les e-mails malveillants qui ont été remis dans Office 365](investigate-malicious-email-that-was-delivered.md)|
|Un message électronique ou un fichier a été mis en quarantaine|<ul><li>Libérer le courrier électronique ou le fichier</li><li> Supprimer le courrier électronique ou le fichier</li></ul>|[Gérer les messages mis en quarantaine en tant qu’administrateur](manage-quarantined-messages-and-files.md)|
|

### <a name="undo-an-action-in-the-action-center"></a>Annuler une action dans le centre de données

Dans le centre de correction, vous pouvez voir les actions de correction qui ont été prises et éventuellement annuler l’action.

1. Go to the Microsoft 365 Defender portal ( <https://security.microsoft.com> ).
2. Dans le volet de navigation, sélectionnez **Centre de l’action.**
3. Sélectionnez **l’onglet** Historique pour afficher la liste des actions terminées.
4. Sélectionnez un élément. Son volet volant s’ouvre.
5. Dans le volet volant, sélectionnez **Annuler.** (Seules les actions qui peuvent être annulées auront **un bouton Annuler.)**

## <a name="see-also"></a>Voir aussi

- [Microsoft Defender pour Office 365](defender-for-office-365.md)
- [Examens automatisés dans Microsoft Defender pour Office 365](office-365-air.md)
