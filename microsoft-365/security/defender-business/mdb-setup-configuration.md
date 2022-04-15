---
title: Configurer et configurer Microsoft Defender pour les PME
description: Obtenir une vue d’ensemble du processus d’installation et de configuration pour Microsoft Defender pour les PME
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 04/12/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: e832a06a27d479bcd9ffecaf00e07b20f55d1042
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2022
ms.locfileid: "64862651"
---
# <a name="set-up-and-configure-microsoft-defender-for-business"></a>Configurer et configurer Microsoft Defender pour les PME

> [!NOTE]
> Microsoft Defender pour les PME est désormais inclus dans [Microsoft 365 Business Premium](../../business-premium/index.md). 

Microsoft Defender pour les PME offre une installation et une expérience de configuration rationalisées, conçues spécialement pour les petites et moyennes entreprises. Utilisez cet article comme guide pour le processus global.

> [!TIP]
> Si vous avez utilisé [l’Assistant Installation](mdb-use-wizard.md), vous avez déjà effectué plusieurs étapes de votre processus d’installation de base. Dans ce cas, vous pouvez :
> - [Intégrer d’autres appareils](mdb-onboard-devices.md)
> - [Configurer vos stratégies et paramètres de sécurité](mdb-configure-security-settings.md)
> - [Visitez votre tableau de bord gestion des vulnérabilités](mdb-view-tvm-dashboard.md)

>
> **Avez-vous un peu de temps ?**
> Veuillez prendre notre <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">courte enquête sur la sécurité</a>. Vos commentaires sont les bienvenus.
>

## <a name="the-setup-and-configuration-process"></a>Processus d’installation et de configuration

Le diagramme suivant illustre le processus d’installation et de configuration global pour Defender entreprise. Si vous avez utilisé l’Assistant Installation, vous avez probablement déjà effectué les étapes 1 à 3 et éventuellement l’étape 4. 

:::image type="content" source="media/mdb-setup-process-2.png" alt-text="Processus d’installation et de configuration pour Microsoft Defender pour les PME.":::

| Étape  | Article | Description  |
|---------|---------|--------|
| 1 | [Consultez la configuration requise](mdb-requirements.md) | Passez en revue les exigences, y compris les systèmes d’exploitation pris en charge, pour Microsoft Defender pour les PME. Consultez [Microsoft Defender pour les PME exigences](mdb-requirements.md). |
| 2 | [Attribuer des rôles et des autorisations](mdb-roles-permissions.md)     | Les membres de votre équipe de sécurité ont besoin d’autorisations pour effectuer des tâches, telles que l’examen des menaces détectées & les actions de correction, l’affichage & la modification des stratégies, l’intégration d’appareils et l’utilisation de rapports. Vous pouvez accorder ces autorisations via certains rôles. Voir [Attribuer des rôles et des autorisations](mdb-roles-permissions.md).        |
| 3 | [Configurer des notifications par e-mail](mdb-email-notifications.md) | Vous pouvez spécifier qui doit recevoir des notifications par e-mail lorsque des alertes sont déclenchées ou que de nouvelles vulnérabilités sont découvertes. Voir [Configurer les notifications par e-mail](mdb-email-notifications.md).| 
| 4 | [Intégration des appareils](mdb-onboard-devices.md)     | Microsoft Defender pour les PME est configuré afin que vous puissiez choisir parmi plusieurs options pour intégrer les appareils de votre entreprise. Consultez [Intégrer des appareils à Microsoft Defender pour les PME](mdb-onboard-devices.md).         |
| 5 | [Configurer vos paramètres et stratégies de sécurité](mdb-configure-security-settings.md) | Vous pouvez choisir parmi plusieurs options pour configurer vos paramètres et stratégies de sécurité, notamment un processus de configuration simplifié ou Microsoft Endpoint Manager. Consultez [Configurer vos paramètres et stratégies de sécurité](mdb-configure-security-settings.md). |

## <a name="next-steps"></a>Prochaines étapes

Passez à [l’étape 1 : Passez en revue les conditions requises pour Microsoft Defender pour les PME](mdb-requirements.md).
