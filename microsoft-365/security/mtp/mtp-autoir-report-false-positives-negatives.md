---
title: Gérer les faux positifs ou les faux négatifs dans l’AIR dans la protection contre les menaces Microsoft
description: Un message a-t-il été manqué ou incorrectement détecté par AIR dans la protection contre les menaces Microsoft ? Découvrez comment soumettre des faux positifs ou faux négatifs à Microsoft pour analyse.
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
ms.date: 01/29/2020
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: conceptual
ms.custom: autoir
ms.openlocfilehash: 90651aa258adb9f7fe46f99bcadf1d4d552a5b76
ms.sourcegitcommit: 58c1b4208a5e231463091573e40696d08fc39b8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2020
ms.locfileid: "42955660"
---
# <a name="handle-false-positivesnegatives-in-automated-investigation-and-response-capabilities"></a>Gérer les faux positifs/négatifs dans les fonctionnalités d’analyse et de réponse automatisées

**S’applique à :**
- Protection Microsoft contre les menaces

La protection contre les menaces a-t-elle permis d’effectuer des [recherches et des réponses automatiques](mtp-autoir.md) dans Microsoft Threat Protection ? Il existe des étapes que vous pouvez suivre pour résoudre ce problème. Vous pouvez :

- [Signaler un faux positif/négatif à Microsoft](#report-a-false-positivenegative-to-microsoft-for-analysis);

- [Ajustez vos alertes (le](#adjust-an-alert-to-prevent-false-positives-from-recurring) cas échéant); les 

- [Annuler les actions correctives qui ont été effectuées sur les appareils](#undo-a-remediation-action-that-was-taken-on-a-device). 

Utilisez cet article comme guide. 

## <a name="report-a-false-positivenegative-to-microsoft-for-analysis"></a>Signaler un faux positif/négatif à Microsoft pour analyse

|Élément manqué ou incorrectement détecté |Service  |Procédure  |
|---------|---------|---------|
|-Message électronique <br/>-Pièce jointe de courrier électronique <br/>-URL dans un message électronique<br/>-URL dans un fichier Office      |[Protection avancée contre les menaces dans Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-atp)        |[Soumission de courrier indésirable, hameçon, URL et fichiers suspects à Microsoft pour l’analyse Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/admin-submission)         |
|Fichier ou application sur un appareil    |[Microsoft Defender – Protection avancée contre les menaces](https://docs.microsoft.com/windows/security/threat-protection)         |[Envoi d’un fichier à Microsoft pour l’analyse des programmes malveillants](https://www.microsoft.com/wdsi/filesubmission)         |

## <a name="adjust-an-alert-to-prevent-false-positives-from-recurring"></a>Ajuster une alerte pour empêcher les faux positifs d’être périodiques

|Scénario |Service |Procédure |
|--------|--------|--------|
|-Une alerte est déclenchée par une utilisation légitime <br/>-Une alerte est incorrecte    |[Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security)<br/> ou <br/>[Détection de menaces avancées Azure](https://docs.microsoft.com/azure/security/fundamentals/threat-detection)         |[Gérer les alertes dans le portail de sécurité des applications Cloud](https://docs.microsoft.com/cloud-app-security/managing-alerts)         |
|Un fichier, une adresse IP, une URL ou un domaine est traité comme un programme malveillant sur un appareil, même s’il est sûr.|[Microsoft Defender – Protection avancée contre les menaces](https://docs.microsoft.com/windows/security/threat-protection) |[Créer un indicateur personnalisé avec une action « autoriser »](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/manage-indicators) |


## <a name="undo-a-remediation-action-that-was-taken-on-a-device"></a>Annuler une action de correction effectuée sur un appareil

Si une action de correction a été effectuée sur un appareil (par exemple, un appareil Windows 10) et que l’élément n’est pas une menace, votre équipe d’opérations de sécurité peut annuler l’action de correction dans le [Centre de maintenance](mtp-action-center.md).

> [!IMPORTANT]
> Vérifiez que vous disposez des [autorisations nécessaires](mtp-action-center.md#required-permissions-for-action-center-tasks) avant d’effectuer la tâche suivante.

1. Accédez à [https://security.microsoft.com](https://security.microsoft.com) et connectez-vous. 

2. Dans le volet de navigation, choisissez **Centre de notifications**. 

3. Sous l’onglet **historique** , sélectionnez une action que vous souhaitez annuler. Une fenêtre volante s’ouvre.<br/>
    > [!TIP]
    > Utilisez des filtres pour limiter la liste des résultats. 

4. Dans le menu volant de l’élément sélectionné, sélectionnez **ouvrir la page d’enquête**.

5. Dans la vue Détails de l’enquête, sélectionnez l’onglet **actions** .

6. Sélectionnez un élément dont le statut est **terminé**, puis recherchez un lien, tel que **approuvé**, dans la colonne **décisions** . Cette opération ouvre un menu volant avec plus de détails sur l’action.

7. Pour annuler l’action, sélectionnez **Supprimer la correction**.

## <a name="related-articles"></a>Articles connexes

- [Approuver ou refuser les actions liées à un examen et réponse automatisées](mtp-autoir-actions.md)

- [En savoir plus sur le centre de notifications](mtp-action-center.md).

- [Repérage proactive de menaces avec repérage avancé dans la Protection Microsoft contre les menaces](advanced-hunting-overview.md)
