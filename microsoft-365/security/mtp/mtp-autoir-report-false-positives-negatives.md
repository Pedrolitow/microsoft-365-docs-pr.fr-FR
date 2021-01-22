---
title: Gérer les faux positifs ou les faux négatifs dans AIR dans Microsoft 365 Defender
description: Un problème a-t-il été manqué ou détecté à tort par AIR dans Microsoft 365 Defender ? Découvrez comment soumettre des faux positifs ou des faux négatifs à Microsoft pour analyse.
keywords: automatisé, examen, alerte, déclencheur, action, correction, faux positif, faux négatif
search.appverid: met150
ms.prod: m365-security
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
ms.technology: m365d
ms.openlocfilehash: dbef240e28258d1ac4000c05538d0ce073a9d910
ms.sourcegitcommit: 855719ee21017cf87dfa98cbe62806763bcb78ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "49930353"
---
# <a name="handle-false-positivesnegatives-in-automated-investigation-and-response-capabilities"></a>Gérer les faux positifs/négatifs dans les fonctionnalités automatisées d’examen et de réponse

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Les [fonctionnalités d’investigation](mtp-autoir.md) et de réponse automatisées dans Microsoft 365 Defender ont-elle manqué ou détecté un problème ? Vous pouvez suivre certaines étapes pour y remédier. Vous pouvez :

- [Signaler un faux positif/négatif à Microsoft](#report-a-false-positivenegative-to-microsoft-for-analysis);

- [Ajuster vos alertes](#adjust-an-alert-to-prevent-false-positives-from-recurring) (si nécessaire) ; et 

- [Annuler les actions de correction qui ont été prises sur les appareils.](#undo-a-remediation-action-that-was-taken-on-a-device) 

Utilisez cet article comme guide. 

## <a name="report-a-false-positivenegative-to-microsoft-for-analysis"></a>Signaler un faux positif/négatif à Microsoft pour analyse

|Élément manqué ou détecté de manière erronée |Service  |Procédure  |
|---------|---------|---------|
|- Message électronique <br/>- Pièce jointe d’un e-mail <br/>- URL dans un message électronique<br/>- URL dans un fichier Office      |[Microsoft Defender pour Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-atp)        |[Soumettre des messages suspects de courrier indésirable, d’hameçonnage, d’URL et de fichiers à Microsoft pour analyse](https://docs.microsoft.com/microsoft-365/security/office-365-security/admin-submission)         |
|Fichier ou application sur un appareil    |[Microsoft Defender pour point de terminaison](https://docs.microsoft.com/windows/security/threat-protection)         |[Envoyer un fichier à Microsoft pour analyse des programmes malveillants](https://www.microsoft.com/wdsi/filesubmission)         |

## <a name="adjust-an-alert-to-prevent-false-positives-from-recurring"></a>Ajuster une alerte pour éviter que les faux positifs ne se répètent

|Scénario |Service |Procédure |
|--------|--------|--------|
|- Une alerte est déclenchée par un usage légitime <br/>- Une alerte est inexacte    |[Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security)<br/> ou <br/>[Azure Advanced Threat Detection](https://docs.microsoft.com/azure/security/fundamentals/threat-detection)         |[Gérer les alertes dans le portail Cloud App Security](https://docs.microsoft.com/cloud-app-security/managing-alerts)         |
|Un fichier, une adresse IP, une URL ou un domaine est traité comme un programme malveillant sur un appareil, même s’il est sécurisé|[Microsoft Defender pour point de terminaison](https://docs.microsoft.com/windows/security/threat-protection) |[Créer un indicateur personnalisé avec une action « Autoriser »](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/manage-indicators) |


## <a name="undo-a-remediation-action-that-was-taken-on-a-device"></a>Annuler une action de correction qui a été prise sur un appareil

Si une action de correction a été entreprise sur un appareil (tel qu’un appareil Windows 10) et que l’élément n’est pas une menace, votre équipe des opérations de sécurité peut annuler l’action de correction dans le centre de [correction.](mtp-action-center.md)

> [!IMPORTANT]
> Assurez-vous que vous avez les [autorisations nécessaires](mtp-action-center.md#required-permissions-for-action-center-tasks) avant d’essayer d’effectuer la tâche suivante.

1. Accédez à [https://security.microsoft.com](https://security.microsoft.com) et connectez-vous. 

2. Dans le volet de navigation, choisissez **Centre de notifications**. 

3. Sous **l’onglet** Historique, sélectionnez une action à annuler. Cela ouvre un volant.<br/>
    > [!TIP]
    > Utilisez des filtres pour affiner la liste des résultats. 

4. Dans le volant de l’élément sélectionné, sélectionnez **Ouvrir la page Ouvrir l’examen.**

5. Dans l’affichage Détails de l’examen, sélectionnez **l’onglet Actions.**

6. Sélectionnez un élément dont l’état est **Terminé** et recherchez un lien, tel que **Approuvé,** dans la colonne **Décisions.** Cela ouvre un volant avec plus de détails sur l’action.

7. Pour annuler l’action, sélectionnez **Supprimer la correction.**

## <a name="see-also"></a>Voir aussi

- [Consulter les détails et les résultats d'un examen automatisé](mtp-autoir-results.md)
- [Recherche proactive des menaces avec le hunting avancé dans Microsoft 365 Defender](advanced-hunting-overview.md)
