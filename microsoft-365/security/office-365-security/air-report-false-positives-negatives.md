---
title: Comment signaler les faux positifs ou les faux négatifs après une enquête automatisée dans Microsoft Defender pour Office 365
description: Un message a-t-il été manqué ou incorrectement détecté par AIR dans Microsoft Defender pour Office 365 ? Découvrez comment soumettre des faux positifs ou faux négatifs à Microsoft pour analyse.
keywords: automatisation, analyse, alerte, déclencheur, action, correction, faux positif, faux négatif
search.appverid: met150
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
ms.date: 09/29/2020
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.topic: conceptual
ms.custom:
- autoir
ms.openlocfilehash: 0fe8891f5ea6af215791c5f4321a93667a9d58f0
ms.sourcegitcommit: ee39faf3507d0edc9497117b3b2854955c959c6c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "49616175"
---
# <a name="how-to-report-false-positivesnegatives-in-automated-investigation-and-response-capabilities"></a>Comment signaler les faux positifs/négatifs dans les fonctionnalités d’analyse et de réponse automatisées

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


**S’applique à :**
- Microsoft Defender pour Office 365

[Les fonctionnalités d’analyse et de réponse automatisées (air) d’Office 365](automated-investigation-response-office.md) manquent ou détectent-elles mal ? Il existe des étapes que vous pouvez suivre pour résoudre ce problème. Vous pouvez :

- [Signaler un faux positif/négatif à Microsoft](#report-a-false-positivenegative-to-microsoft-for-analysis);
- [Ajustez vos alertes (le](#adjust-an-alert-to-prevent-false-positives-from-recurring) cas échéant); les
- [Annuler les actions correctives qui ont été entreprises](#undo-a-remediation-action).

Utilisez cet article comme guide.

## <a name="report-a-false-positivenegative-to-microsoft-for-analysis"></a>Signaler un faux positif/négatif à Microsoft pour analyse

Si Microsoft Defender pour Office 365 n’a pas manqué un message électronique, une pièce jointe à un message électronique, une URL dans un message électronique ou une URL dans un fichier Office, vous pouvez [soumettre des analyses de courrier indésirable, de hameçonnage, d’URL et de fichiers à Microsoft pour Office 365](admin-submission.md).

Vous pouvez également [Envoyer un fichier à Microsoft pour analyse contre les programmes malveillants](https://www.microsoft.com/wdsi/filesubmission).

## <a name="adjust-an-alert-to-prevent-false-positives-from-recurring"></a>Ajuster une alerte pour empêcher les faux positifs d’être périodiques

Si une alerte est déclenchée par une utilisation légitime ou si l’alerte est incorrecte, vous pouvez [gérer les alertes dans le portail de sécurité des applications Cloud](https://docs.microsoft.com/cloud-app-security/managing-alerts).

Si votre organisation utilise [Microsoft Defender pour le point de terminaison](https://docs.microsoft.com/windows/security/threat-protection) en plus d’Office 365 et qu’un fichier, une adresse IP, une URL ou un domaine est traité comme un programme malveillant sur un appareil, même s’il est sûr, vous pouvez [créer un indicateur personnalisé avec une action « autoriser » pour votre appareil](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/manage-indicators).

## <a name="undo-a-remediation-action"></a>Annuler une action de correction

Dans la plupart des cas, si une action de correction a été effectuée sur un message électronique, une pièce jointe de courrier électronique ou une URL, et que l’élément n’est pas une menace, votre équipe d’opérations de sécurité peut annuler l’action de correction et prendre des mesures pour empêcher le faux positif d’être périodique. Vous pouvez utiliser l' [Explorateur de menaces](#undo-an-action-using-threat-explorer) ou l' [onglet actions pour effectuer une enquête](#undo-an-action-using-the-actions-tab-for-an-investigation) afin d’annuler une action.

> [!IMPORTANT]
> Vérifiez que vous disposez des autorisations nécessaires avant d’effectuer les tâches suivantes.

### <a name="undo-an-action-using-threat-explorer"></a>Annuler une action à l’aide de l’Explorateur de menaces

Avec l’Explorateur de menaces, votre équipe des opérations de sécurité peut trouver un e-mail affecté par une action et éventuellement annuler l’action.

****

|Scénario|Options d’annulation|En savoir plus|
|---|---|---|
|Un message électronique a été acheminé vers le dossier de courrier indésirable d’un utilisateur|<ul><li>Déplacer le message vers le dossier éléments supprimés de l’utilisateur</li><li>Déplacer le message vers la boîte de réception de l’utilisateur</li><li>Supprimer le message</li></ul>|[Rechercher et identifier les courriers électroniques malveillants remis dans Office 365](investigate-malicious-email-that-was-delivered.md)|
|Un message électronique ou un fichier a été mis en quarantaine|<ul><li>Libérer le message électronique ou le fichier</li><li>Supprimer le message électronique ou le fichier</li></ul>|[Gérer les messages mis en quarantaine en tant qu’administrateur](manage-quarantined-messages-and-files.md)|
|

### <a name="undo-an-action-using-the-actions-tab-for-an-investigation"></a>Annuler une action à l’aide de l’onglet actions pour une enquête

Dans le centre de notifications, vous pouvez voir les actions de correction qui ont été prises et éventuellement annuler l’action.

1. Accédez à <https://protection.office.com> et connectez-vous. Vous accédez au centre de sécurité & conformité.

2. Accédez aux enquêtes de **gestion des menaces** \> .

3. Dans la liste des enquêtes, sélectionnez l’icône **ouvrir dans une nouvelle fenêtre** en regard de l’ID d’un élément.

4. Sélectionnez l’onglet **actions** .

5. Sélectionnez un élément dont le statut est **terminé**, puis recherchez un lien, tel que **approuvé**, dans la colonne **décision** . Cette opération ouvre un menu volant avec plus de détails sur l’action.

6. Pour annuler l’action, sélectionnez **Supprimer la correction**.

## <a name="related-articles"></a>Articles connexes

[Microsoft Defender pour Office 365](office-365-atp.md)

[AIR dans Microsoft Defender pour Office 365](office-365-air.md)
