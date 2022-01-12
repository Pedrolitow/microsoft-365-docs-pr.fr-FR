---
title: Configurer des fonctionnalités automatisées d’examen et de correction
description: Configurer vos fonctionnalités automatisées d’examen et de correction dans Microsoft Defender pour le point de terminaison.
keywords: configurer, configurer, automatisé, examen, détection, alertes, correction, réponse
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: JoeDavies-MSFT
ms.author: josephd
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: how-to
ms.date: 01/27/2021
ms.reviewer: ramarom, evaldm, isco, mabraitm, chriggs
ms.openlocfilehash: 3f51ce7c0eb45861a8b5277266b18e6d03e53178
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2022
ms.locfileid: "61872488"
---
# <a name="configure-automated-investigation-and-remediation-capabilities-in-microsoft-defender-for-endpoint"></a>Configurer des fonctionnalités automatisées d’examen et de correction dans Microsoft Defender pour endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Si votre organisation utilise [Microsoft Defender pour le](/windows/security/threat-protection/) point de terminaison (Defender pour point de terminaison), les fonctionnalités d’examen et de correction automatisées peuvent économiser du temps et des efforts de votre équipe en matière d’opérations de sécurité. [](/microsoft-365/security/defender-endpoint/automated-investigations) Comme indiqué dans ce [billet de blog,](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/enhance-your-soc-with-microsoft-defender-atp-automatic/ba-p/848946)ces fonctionnalités imitent les étapes idéales qu’un analyste de sécurité prend pour examiner et corriger les menaces. [En savoir plus sur l’examen et la correction automatisés.](/microsoft-365/security/defender-endpoint/automated-investigations)

Pour configurer l’examen et la correction automatisés :

1. [Activer les fonctionnalités](#turn-on-automated-investigation-and-remediation); et
2. [Configurer des groupes d’appareils.](#set-up-device-groups)

## <a name="turn-on-automated-investigation-and-remediation"></a>Activer l’examen et la correction automatisés

1. En tant qu’administrateur général ou administrateur de sécurité, go to the Microsoft 365 Defender portal ( <https://security.microsoft.com> ) and sign in.
2. Dans le volet de navigation, choisissez **Paramètres**.
3. Dans la section **Général,** sélectionnez **Fonctionnalités avancées.**
4. Activer **l’examen automatisé et** résoudre automatiquement les **alertes.**

## <a name="set-up-device-groups"></a>Configurer des groupes d’appareils

1. Dans le portail Microsoft 365 Defender ( ), sur la <https://security.microsoft.com> page **Paramètres,** sous **Autorisations,** sélectionnez **Groupes d’appareils.**
2. Sélectionnez **+ Ajouter un groupe d’appareils.**
3. Créez au moins un groupe d’appareils, comme suit :
   - Spécifiez un nom et une description pour le groupe d’appareils.
   - Dans la liste **des niveaux Automation,** sélectionnez un niveau, tel que Complet, pour corriger automatiquement **les menaces.** Le niveau d’automatisation détermine si les actions de correction sont prises automatiquement ou uniquement après approbation. Pour en savoir plus, consultez [Les niveaux Automation dans l’examen et la correction automatisés.](automation-levels.md)
   - Dans la section **Membres,** utilisez une ou plusieurs conditions pour identifier et inclure des appareils.
   - Sous **l’onglet** Accès utilisateur, sélectionnez [les groupes Azure Active Directory qui](/azure/active-directory/fundamentals/active-directory-manage-groups?context=azure/active-directory/users-groups-roles/context/ugr-context) doivent avoir accès au groupe d’appareils que vous créez.
4. Sélectionnez **Terminé** lorsque vous avez terminé la configuration de votre groupe d’appareils.

## <a name="next-steps"></a>Prochaines étapes

- [Visitez le centre de mise en œuvre pour afficher les actions de correction en attente et terminées](/microsoft-365/security/defender-endpoint/auto-investigation-action-center#the-action-center)
- [Examiner et approuver les actions en attente](/microsoft-365/security/defender-endpoint/manage-auto-investigation)

## <a name="see-also"></a>Voir aussi

- [Résoudre des faux négatifs/positifs dans Microsoft Defender pour point de terminaison](defender-endpoint-false-positives-negatives.md)
