---
title: Gérer les faux positifs ou les faux négatifs dans l’AIR dans Microsoft 365 Defender
description: Un message a-t-il été manqué ou incorrectement détecté par AIR dans Microsoft 365 Defender ? Découvrez comment soumettre des faux positifs ou faux négatifs à Microsoft pour analyse.
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
ms.date: 09/16/2020
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
ms.custom: autoir
ms.reviewer: evaldm, isco
ms.openlocfilehash: 92ad4a96665a5355bce7e3546f8c52779f770927
ms.sourcegitcommit: 815229e39a0f905d9f06717f00dc82e2a028fa7c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "48843731"
---
# <a name="handle-false-positivesnegatives-in-automated-investigation-and-response-capabilities"></a>Gérer les faux positifs/négatifs dans les fonctionnalités d’analyse et de réponse automatisées

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

[Les fonctionnalités d’enquête et de réponse automatisées](mtp-autoir.md) dans Microsoft 365 Defender manquent ou détectent-elles mal ? Il existe des étapes que vous pouvez suivre pour résoudre ce problème. Vous pouvez :

- [Signaler un faux positif/négatif à Microsoft](#report-a-false-positivenegative-to-microsoft-for-analysis);

- [Ajustez vos alertes (le](#adjust-an-alert-to-prevent-false-positives-from-recurring) cas échéant); les 

- [Annuler les actions correctives qui ont été effectuées sur les appareils](#undo-a-remediation-action-that-was-taken-on-a-device). 

Utilisez cet article comme guide. 

## <a name="report-a-false-positivenegative-to-microsoft-for-analysis"></a>Signaler un faux positif/négatif à Microsoft pour analyse

|Élément manqué ou incorrectement détecté |Service  |Procédure  |
|---------|---------|---------|
|-Message électronique <br/>-Pièce jointe de courrier électronique <br/>-URL dans un message électronique<br/>-URL dans un fichier Office      |[Microsoft Defender pour Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-atp)        |[Soumission de courrier indésirable, hameçon, URL et fichiers suspects à Microsoft pour analyse](https://docs.microsoft.com/microsoft-365/security/office-365-security/admin-submission)         |
|Fichier ou application sur un appareil    |[Microsoft Defender pour point de terminaison](https://docs.microsoft.com/windows/security/threat-protection)         |[Envoi d’un fichier à Microsoft pour l’analyse des programmes malveillants](https://www.microsoft.com/wdsi/filesubmission)         |

## <a name="adjust-an-alert-to-prevent-false-positives-from-recurring"></a>Ajuster une alerte pour empêcher les faux positifs d’être périodiques

|Scénario |Service |Procédure |
|--------|--------|--------|
|-Une alerte est déclenchée par une utilisation légitime <br/>-Une alerte est incorrecte    |[Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security)<br/> ou <br/>[Détection de menaces avancées Azure](https://docs.microsoft.com/azure/security/fundamentals/threat-detection)         |[Gérer les alertes dans le portail de sécurité des applications Cloud](https://docs.microsoft.com/cloud-app-security/managing-alerts)         |
|Un fichier, une adresse IP, une URL ou un domaine est traité comme un programme malveillant sur un appareil, même s’il est sûr.|[Microsoft Defender pour point de terminaison](https://docs.microsoft.com/windows/security/threat-protection) |[Créer un indicateur personnalisé avec une action « autoriser »](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/manage-indicators) |


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

6. Sélectionnez un élément dont le statut est **terminé** , puis recherchez un lien, tel que **approuvé** , dans la colonne **décisions** . Cette opération ouvre un menu volant avec plus de détails sur l’action.

7. Pour annuler l’action, sélectionnez **Supprimer la correction**.

## <a name="see-also"></a>Voir aussi

- [Consulter les détails et les résultats d'un examen automatisé](mtp-autoir-results.md)
- [Recherche proactive de menaces à l’aide de la chasse avancée dans Microsoft 365 Defender](advanced-hunting-overview.md)
