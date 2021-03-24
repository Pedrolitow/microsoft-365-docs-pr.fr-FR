---
title: Utiliser Microsoft Defender pour Office 365 avec Microsoft Defender pour le point de terminaison
f1.keywords:
- NOCSH
keywords: integrate, Microsoft Defender, ATP
ms.author: deniseb
author: denisebmsft
manager: dansimp
ms.date: 01/21/2021
audience: ITPro
ms.topic: article
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
description: Utilisez Microsoft Defender pour Office 365 avec Microsoft Defender pour le point de terminaison pour obtenir des informations plus détaillées sur les menaces contre vos appareils et le contenu de votre courrier électronique.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: bac2414419d673f261d0d0162d8ae742385fd4eb
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51065241"
---
# <a name="use-microsoft-defender-for-office-365-together-with-microsoft-defender-for-endpoint"></a>Utiliser Microsoft Defender pour Office 365 avec Microsoft Defender pour le point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


[Microsoft Defender pour Office 365](defender-for-office-365.md) peut être configuré pour fonctionner avec [Microsoft Defender pour point de terminaison.](/windows/security/threat-protection)

L’intégration de Microsoft Defender pour Office 365 à Microsoft Defender pour Endpoint peut aider votre équipe en charge des opérations de sécurité à surveiller et à prendre des mesures rapidement si les appareils des utilisateurs sont exposés. Par exemple, une fois l’intégration activée, votre équipe des opérations de sécurité pourra voir les appareils potentiellement affectés par un message électronique détecté, ainsi que le nombre d’alertes récentes générées pour ces appareils dans Microsoft Defender pour Endpoint.

L’image suivante illustre à quoi ressemble l’onglet **Appareils** lorsque l’intégration de Microsoft Defender pour les points de terminaison est activée :

![Lorsque Microsoft Defender pour le point de terminaison est activé, vous pouvez voir une liste d’appareils avec des alertes.](../../media/fec928ea-8f0c-44d7-80b9-a2e0a8cd4e89.PNG)

Dans cet exemple, vous pouvez voir que les destinataires du message électronique détecté ont quatre appareils et un a une alerte. Le fait de cliquer sur le lien d’un appareil ouvre sa page dans le Centre de sécurité Microsoft Defender ( <https://securitycenter.windows.com> ).

> [!TIP]
> **[En savoir plus sur le Centre de](/windows/security/threat-protection/microsoft-defender-atp/use)** sécurité Microsoft Defender (également appelé portail Microsoft Defender pour points de terminaison).)

## <a name="requirements"></a>Configuration requise

- Votre organisation doit avoir Microsoft Defender pour Office 365 (ou Office 365 E5) et Microsoft Defender pour point de terminaison.

- Vous devez être un administrateur général ou avoir un rôle d’administrateur de sécurité (par exemple, Administrateur de la sécurité) affecté dans le Centre de sécurité [& conformité.](https://protection.office.com) (Voir [Autorisations dans le Centre de sécurité & conformité)](permissions-in-the-security-and-compliance-center.md)

- Vous devez avoir accès à [l’Explorateur (ou](threat-explorer.md) aux détections en temps réel) dans le Centre de sécurité & conformité et le Centre de sécurité Microsoft Defender.

## <a name="to-integrate-microsoft-defender-for-office-365-with-microsoft-defender-for-endpoint"></a>Pour intégrer Microsoft Defender pour Office 365 à Microsoft Defender pour point de terminaison

L’intégration de Microsoft Defender pour Office 365 à Microsoft Defender pour endpoint est définie à l’aide du Centre de sécurité & conformité et du Centre de sécurité Microsoft Defender.

1. En tant qu’administrateur général ou administrateur de sécurité, <https://protection.office.com> connectez-vous. (Cette action vous place dans le Centre de sécurité et conformité Office 365&.)

2. Dans le volet de navigation, choisissez **l’Explorateur de gestion** \> **des menaces.**

   ![Explorateur dans le menu Gestion des menaces](../../media/ThreatMgmt-Explorer-nav.png)

3. Dans le coin supérieur droit de l’écran, choisissez Defender pour les paramètres de point de terminaison **(paramètres MDE).**

4. Dans la boîte de dialogue connexion Microsoft Defender pour point de terminaison, activer la connexion **à Microsoft Defender pour le point de terminaison.**

   ![Connexion microsoft Defender pour point de terminaison](../../media/Explorer-WDATPConnection-dialog.png)

5. Go to the Microsoft Defender Security Center ( <https://securitycenter.windows.com> ).

6. Dans la barre de navigation, choisissez **Paramètres.** Ensuite, sous **Général,** choisissez **Fonctionnalités avancées.**

7. Faites défiler vers le bas jusqu’à la connexion **Office 365 Threat Intelligence** et allumez la connexion.

   ![Connexion à l’intelligence des menaces Office 365](../../media/mdatp-oatptoggle.png)

## <a name="related-articles"></a>Articles connexes

[Fonctionnalités d’examen et de réponse aux menaces dans Office 365](office-365-ti.md)

[Microsoft Defender pour Office 365](defender-for-office-365.md)

[Microsoft Defender pour point de terminaison](/windows/security/threat-protection)