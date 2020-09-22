---
title: Comment faire pour signaler les faux positifs ou les faux négatifs dans Office 365 automatisation de l’analyse et de la réponse
description: Un message a-t-il été manqué ou incorrectement détecté par Office 365 Advanced Threat Protection ? Découvrez comment soumettre des faux positifs ou faux négatifs à Microsoft pour analyse.
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
ms.date: 05/15/2020
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: conceptual
ms.custom: autoir
ms.openlocfilehash: 66b81a474ff81df57c0b2a59672b17061f7235cb
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "48196075"
---
# <a name="how-to-report-false-positivesnegatives-in-automated-investigation-and-response-capabilities"></a>Comment signaler les faux positifs/négatifs dans les fonctionnalités d’analyse et de réponse automatisées

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


**S’applique à :**
- Office 365 – Protection avancée contre les menaces

[Les fonctionnalités d’analyse et de réponse automatisées (air) d’Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/automated-investigation-response-office) manquent ou détectent-elles mal ? Il existe des étapes que vous pouvez suivre pour résoudre ce problème. Vous pouvez :
- [Signaler un faux positif/négatif à Microsoft](#report-a-false-positivenegative-to-microsoft-for-analysis);
- [Ajustez vos alertes (le](#adjust-an-alert-to-prevent-false-positives-from-recurring) cas échéant); les 
- [Annuler les actions correctives qui ont été entreprises](#undo-a-remediation-action). 

Utilisez cet article comme guide. 

## <a name="report-a-false-positivenegative-to-microsoft-for-analysis"></a>Signaler un faux positif/négatif à Microsoft pour analyse

Si Office 365 AIR n’a pas manqué un message électronique, une pièce jointe de message électronique, une URL dans un message électronique ou une URL dans un fichier Office, vous pouvez [Envoyer des messages indésirables, hameçons, URL et fichiers suspects à Microsoft pour l’analyse d’office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/admin-submission).

Vous pouvez également [Envoyer un fichier à Microsoft pour analyse contre les programmes malveillants](https://www.microsoft.com/wdsi/filesubmission).

## <a name="adjust-an-alert-to-prevent-false-positives-from-recurring"></a>Ajuster une alerte pour empêcher les faux positifs d’être périodiques

Si une alerte est déclenchée par une utilisation légitime ou si l’alerte est incorrecte, vous pouvez [gérer les alertes dans le portail de sécurité des applications Cloud](https://docs.microsoft.com/cloud-app-security/managing-alerts).

Si votre organisation utilise la [protection avancée contre les menaces Microsoft Defender](https://docs.microsoft.com/windows/security/threat-protection) en plus d’Office 365 et qu’un fichier, une adresse IP, une URL ou un domaine est traité comme un programme malveillant sur un appareil, même s’il est sûr, vous pouvez [créer un indicateur personnalisé avec une action « autoriser » pour votre appareil](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/manage-indicators).

## <a name="undo-a-remediation-action"></a>Annuler une action de correction

Dans la plupart des cas, si une action de correction a été effectuée sur un message électronique, une pièce jointe de courrier électronique ou une URL, et que l’élément n’est pas une menace, votre équipe d’opérations de sécurité peut annuler l’action de correction et prendre des mesures pour empêcher le faux positif d’être périodique. Vous pouvez utiliser l' [Explorateur de menaces](#undo-an-action-using-threat-explorer) ou l' [onglet actions pour effectuer une enquête](#undo-an-action-using-the-actions-tab-for-an-investigation) afin d’annuler une action. 

> [!IMPORTANT]
> Vérifiez que vous disposez des autorisations nécessaires avant d’effectuer les tâches suivantes.

### <a name="undo-an-action-using-threat-explorer"></a>Annuler une action à l’aide de l’Explorateur de menaces

Avec l’Explorateur de menaces, votre équipe des opérations de sécurité peut trouver un e-mail affecté par une action et éventuellement annuler l’action.

****

|Scénario|Options d’annulation|Si vous souhaitez en savoir plus|
|---|---|---|
|Un message électronique a été acheminé vers le dossier de courrier indésirable d’un utilisateur|-Déplacer le message vers le dossier éléments supprimés de l’utilisateur<br/>-Déplacer le message vers la boîte de réception de l’utilisateur <br/>-Supprimer le message|[Rechercher et identifier les courriers électroniques malveillants remis dans Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/investigate-malicious-email-that-was-delivered)|
|Un message électronique ou un fichier a été mis en quarantaine|-Libérer le courrier électronique ou le fichier <br/>-Supprimer le message électronique ou le fichier|[Gestion des messages et des fichiers mis en quarantaine en tant qu’administrateur dans Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/manage-quarantined-messages-and-files)|
|

### <a name="undo-an-action-using-the-actions-tab-for-an-investigation"></a>Annuler une action à l’aide de l’onglet actions pour une enquête

Dans le centre de notifications, vous pouvez voir les actions de correction qui ont été prises et éventuellement annuler l’action.

1. Accédez à [https://protection.office.com](https://protection.office.com) et connectez-vous. Vous accédez au centre de sécurité & conformité.

2. Accédez aux enquêtes de **gestion des menaces**  >  **Investigations**.

3. Dans la liste des enquêtes, sélectionnez l’icône **ouvrir dans une nouvelle fenêtre** en regard de l’ID d’un élément.

4. Sélectionnez l’onglet **actions** .

5. Sélectionnez un élément dont le statut est **terminé**, puis recherchez un lien, tel que **approuvé**, dans la colonne **décision** . Cette opération ouvre un menu volant avec plus de détails sur l’action.

6. Pour annuler l’action, sélectionnez **Supprimer la correction**.

## <a name="related-articles"></a>Articles connexes

[Protection avancée contre les menaces dans Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-atp)

[Prise en main de l’analyse et de la réponse automatisées (AIR) dans Office 365](office-365-air.md)
