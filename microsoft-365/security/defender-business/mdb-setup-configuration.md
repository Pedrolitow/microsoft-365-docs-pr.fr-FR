---
title: Configurer et configurer Microsoft Defender pour entreprises
description: Découvrez comment configurer votre solution de cybersécurité Defender entreprise. Intégrer des appareils, passer en revue vos stratégies et modifier vos paramètres en fonction des besoins.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.date: 08/09/2022
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365solution-mdb-setup
ms.openlocfilehash: 4dfd112af96bbb421ace15e3ac4bd9a8e4e2733a
ms.sourcegitcommit: 217108c59be41b01963a393b4f16d137636fe6a8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/12/2022
ms.locfileid: "67328076"
---
# <a name="set-up-and-configure-microsoft-defender-for-business"></a>Configurer et configurer Microsoft Defender pour entreprises

Defender entreprise offre une expérience de configuration et de configuration rationalisée, spécialement conçue pour les petites et moyennes entreprises. Utilisez cet article comme guide pour le processus global.

> [!TIP]
> Si vous avez utilisé [l’Assistant Installation](mdb-use-wizard.md), vous avez déjà effectué plusieurs étapes de votre processus d’installation de base. Dans ce cas, vous pouvez :
> - [Intégrer d’autres appareils](mdb-onboard-devices.md)
> - [Configurer vos stratégies et paramètres de sécurité](mdb-configure-security-settings.md)
> - [Visitez votre tableau de bord Gestion des vulnérabilités Microsoft Defender](mdb-view-tvm-dashboard.md)


## <a name="the-setup-and-configuration-process"></a>Processus d’installation et de configuration

Le diagramme suivant illustre le processus d’installation et de configuration global pour Defender entreprise. Si vous avez utilisé l’Assistant Installation, vous avez probablement déjà effectué les étapes 1 à 3 et éventuellement l’étape 4. 

:::image type="content" source="media/mdb-setup-process-2.png" alt-text="Processus d'installation et de configuration de Defender pour entreprise.":::

| Étape  | Article | Description  |
|---------|---------|--------|
| 1 | [Consultez la configuration requise](mdb-requirements.md) | Passez en revue les exigences, y compris les systèmes d’exploitation pris en charge, pour Defender entreprise. Consultez [les exigences de Defender entreprise](mdb-requirements.md). |
| 2 | [Attribuer des rôles et des autorisations](mdb-roles-permissions.md)     | Personnes de votre équipe de sécurité ont besoin d’autorisations pour effectuer des tâches, telles que l’examen des menaces détectées & les actions de correction, l’affichage & la modification des stratégies, l’intégration d’appareils et l’utilisation de rapports. Vous pouvez accorder ces autorisations via certains rôles. Voir [Attribuer des rôles et des autorisations](mdb-roles-permissions.md).        |
| 3 | [Configurer des notifications par e-mail](mdb-email-notifications.md) | Vous pouvez spécifier qui doit recevoir des notifications par e-mail lorsque des alertes sont déclenchées ou que de nouvelles vulnérabilités sont découvertes. Voir [Configurer les notifications par e-mail](mdb-email-notifications.md).| 
| 4 | [Intégrer des appareils](mdb-onboard-devices.md)     | Vous pouvez choisir parmi plusieurs options pour intégrer les appareils de votre entreprise, comme l’utilisation d’un script téléchargeable ou l’inscription d’appareils dans Microsoft Intune. Consultez [Intégrer des appareils à Defender pour Entreprises](mdb-onboard-devices.md).         |
| 5 | [Configurer vos paramètres et stratégies de sécurité](mdb-configure-security-settings.md) | Vous pouvez choisir parmi plusieurs options pour configurer vos paramètres et stratégies de sécurité, comme le [processus de configuration simplifié](mdb-simplified-configuration.md) dans Defender entreprise ou Microsoft Intune. Consultez [Configurer vos paramètres et stratégies de sécurité](mdb-configure-security-settings.md). |

## <a name="next-steps"></a>Prochaines étapes

Passez à [l’étape 1 : Passez en revue les exigences pour Microsoft Defender pour entreprises](mdb-requirements.md).
