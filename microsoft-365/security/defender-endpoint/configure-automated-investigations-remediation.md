---
title: Configurer des fonctionnalités automatisées d’examen et de correction
description: Configurer vos fonctionnalités automatisées d’examen et de correction dans Microsoft Defender pour le point de terminaison.
keywords: configurer, configurer, automatisé, examen, détection, alertes, correction, réponse
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: JoeDavies-MSFT
ms.author: josephd
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: how-to
ms.date: 01/27/2021
ms.reviewer: ramarom, evaldm, isco, mabraitm, chriggs
ms.openlocfilehash: bd86458749db4019bb247a3664748b9891965754
ms.sourcegitcommit: 4fb1226d5875bf5b9b29252596855a6562cea9ae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2021
ms.locfileid: "52841329"
---
# <a name="configure-automated-investigation-and-remediation-capabilities-in-microsoft-defender-for-endpoint"></a>Configurer les fonctionnalités automatisées d’examen et de correction dans Microsoft Defender pour le point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-assignaccess-abovefoldlink)

Si votre organisation utilise [Microsoft Defender pour le](/windows/security/threat-protection/) point de terminaison (Defender pour point de terminaison), les fonctionnalités d’examen et de correction automatisées peuvent économiser du temps et des efforts de votre équipe en matière d’opérations de sécurité. [](/microsoft-365/security/defender-endpoint/automated-investigations) Comme indiqué dans ce [billet de blog,](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/enhance-your-soc-with-microsoft-defender-atp-automatic/ba-p/848946)ces fonctionnalités imitent les étapes idéales qu’un analyste de sécurité prend pour examiner et corriger les menaces. [En savoir plus sur l’examen et la correction automatisés.](/microsoft-365/security/defender-endpoint/automated-investigations) 

Pour configurer l’examen et la correction automatisés,
1. [Activer les fonctionnalités](#turn-on-automated-investigation-and-remediation); et 
2. [Configurer des groupes d’appareils.](#set-up-device-groups)

## <a name="turn-on-automated-investigation-and-remediation"></a>Activer l’examen et la correction automatisés

1. En tant qu’administrateur général ou administrateur de sécurité, Centre de sécurité Microsoft Defender ( [https://securitycenter.windows.com](https://securitycenter.windows.com) ) et connectez-vous.
2. Dans le volet de navigation, choisissez **Paramètres**.
3. Dans la section **Général,** sélectionnez **Fonctionnalités avancées.**
4. Activer **l’examen automatisé et** résoudre automatiquement les **alertes.**

## <a name="set-up-device-groups"></a>Configurer des groupes d’appareils

1. In the Centre de sécurité Microsoft Defender ( [https://securitycenter.windows.com](https://securitycenter.windows.com) ), on the **Paramètres** page, under **Permissions**, select **Device groups**.
2. Sélectionnez **+ Ajouter un groupe d’appareils.**
3. Créez au moins un groupe d’appareils, comme suit :
   - Spécifiez un nom et une description pour le groupe d’appareils.
   - Dans la liste **des niveaux Automation,** sélectionnez un niveau, tel que Complet , pour corriger automatiquement **les menaces.** Le niveau d’automatisation détermine si des actions de correction sont prises automatiquement, ou uniquement après approbation. Pour en savoir plus, consultez [Les niveaux Automation dans l’examen et la correction automatisés.](automation-levels.md)
   - Dans la section **Membres,** utilisez une ou plusieurs conditions pour identifier et inclure des appareils.
   - Sous **l’onglet** Accès utilisateur, sélectionnez [les groupes Azure Active Directory qui](/azure/active-directory/fundamentals/active-directory-manage-groups?context=azure/active-directory/users-groups-roles/context/ugr-context) doivent avoir accès au groupe d’appareils que vous créez.
4. Sélectionnez **Terminé** lorsque vous avez terminé la configuration de votre groupe d’appareils.

## <a name="next-steps"></a>Prochaines étapes

- [Visitez le centre de mise en œuvre pour afficher les actions de correction en attente et terminées](/microsoft-365/security/defender-endpoint/auto-investigation-action-center#the-action-center)
- [Examiner et approuver les actions en attente](/microsoft-365/security/defender-endpoint/manage-auto-investigation)

## <a name="see-also"></a>Voir aussi

- [Résoudre des faux négatifs/positifs dans Microsoft Defender pour point de terminaison](defender-endpoint-false-positives-negatives.md)
