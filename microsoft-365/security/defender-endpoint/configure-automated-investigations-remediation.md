---
title: Configurer les fonctionnalités d’investigation et de correction automatisées
description: Configurez vos fonctionnalités d’investigation et de correction automatisées dans Microsoft Defender pour point de terminaison.
keywords: configurer, configurer, automatiser, investigation, détection, alertes, correction, réponse
ms.service: microsoft-365-security
ms.subservice: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: dansimp
ms.author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: how-to
ms.reviewer: ramarom, evaldm, isco, mabraitm, chriggs
search.appverid: met150
ms.openlocfilehash: 428ceefa6b8921782864eac8f42105a44cc06c72
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67695734"
---
# <a name="configure-automated-investigation-and-remediation-capabilities-in-microsoft-defender-for-endpoint"></a>Configurer des fonctionnalités d’investigation et de correction automatisées dans Microsoft Defender pour point de terminaison

**S’applique à :**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour les PME](../defender-business/mdb-overview.md)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Si votre organisation utilise [Defender pour point de terminaison](/windows/security/threat-protection/) (ou [Defender entreprise](../defender-business/mdb-overview.md)), [les fonctionnalités d’investigation et de correction automatisées](/microsoft-365/security/defender-endpoint/automated-investigations) peuvent faire gagner du temps et des efforts à votre équipe chargée des opérations de sécurité. Comme indiqué dans [ce billet de blog](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/enhance-your-soc-with-microsoft-defender-atp-automatic/ba-p/848946), ces fonctionnalités imitent les étapes idéales qu’un analyste de sécurité effectue pour examiner et corriger les menaces. [En savoir plus sur l’examen et la correction automatisés](/microsoft-365/security/defender-endpoint/automated-investigations).

Pour configurer l’investigation et la correction automatisées :

1. [Activez les fonctionnalités](#turn-on-automated-investigation-and-remediation); Et
2. [Configurez des groupes d’appareils](#set-up-device-groups).

## <a name="turn-on-automated-investigation-and-remediation"></a>Activer l’examen et la correction automatisés

1. En tant qu’administrateur général ou administrateur de sécurité, accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) et connectez-vous.

2. Dans le volet de navigation, choisissez **Paramètres**.

3. Sélectionnez **Points de terminaison**, puis **Fonctionnalités avancées**.

4. Activez **l’investigation automatisée** et **résolvez automatiquement les alertes**.

## <a name="set-up-device-groups"></a>Configurer des groupes d’appareils

> [!NOTE]
> Cette procédure ne s’applique pas à Defender entreprise.

1. Dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), dans la page **Paramètres**, sous **Autorisations**, sélectionnez **Groupes d’appareils**.

2. Sélectionnez **+ Ajouter un groupe d’appareils**.

3. Créez au moins un groupe d’appareils, comme suit :

   - Spécifiez un nom et une description pour le groupe d’appareils.
   - Dans la **liste des niveaux Automation**, sélectionnez un niveau, par exemple **Full - Corriger automatiquement les menaces**. Le niveau d’automatisation détermine si les actions de correction sont effectuées automatiquement ou uniquement après approbation. Pour plus d’informations, consultez [les niveaux Automation dans l’examen et la correction automatisés](automation-levels.md).
   - Dans la section **Membres** , utilisez une ou plusieurs conditions pour identifier et inclure des appareils.
   - Sous **l’onglet Accès utilisateur** , sélectionnez les [groupes Azure Active Directory](/azure/active-directory/fundamentals/active-directory-manage-groups?context=azure/active-directory/users-groups-roles/context/ugr-context) qui doivent avoir accès au groupe d’appareils que vous créez.

4. Sélectionnez **Terminé** lorsque vous avez terminé la configuration de votre groupe d’appareils.

## <a name="next-steps"></a>Prochaines étapes

- [Visitez le Centre d’actions pour afficher les actions de correction en attente et terminées](/microsoft-365/security/defender-endpoint/auto-investigation-action-center#the-action-center)
- [Examiner et approuver les actions en attente](/microsoft-365/security/defender-endpoint/manage-auto-investigation)

## <a name="see-also"></a>Voir aussi

- [Résoudre des faux négatifs/positifs dans Microsoft Defender pour point de terminaison](defender-endpoint-false-positives-negatives.md)
