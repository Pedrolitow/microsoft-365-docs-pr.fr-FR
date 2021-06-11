---
title: Utiliser Microsoft Defender pour les Office 365 avec Microsoft Defender pour le point de terminaison
f1.keywords:
- NOCSH
keywords: intégrer, Microsoft Defender, Microsoft Defender pour point de terminaison
ms.author: deniseb
author: denisebmsft
manager: dansimp
ms.date: 06/10/2021
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
ms.openlocfilehash: 63ae9f8c1136a973e4fccb63ecfbaee2639c3f6f
ms.sourcegitcommit: 33d19853a38dfa4e6ed21b313976643670a14581
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2021
ms.locfileid: "52904079"
---
# <a name="use-microsoft-defender-for-office-365-together-with-microsoft-defender-for-endpoint"></a>Utiliser Microsoft Defender pour les Office 365 avec Microsoft Defender pour le point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


[Microsoft Defender pour Office 365](defender-for-office-365.md) peut être configuré pour fonctionner avec [Microsoft Defender pour le point de terminaison.](/windows/security/threat-protection)

L’intégration de Microsoft Defender pour Office 365 Microsoft Defender pour Endpoint peut aider votre équipe en matière d’opérations de sécurité à surveiller et à prendre des mesures rapidement si les appareils des utilisateurs sont exposés. Par exemple, une fois l’intégration activée, votre équipe des opérations de sécurité pourra voir les appareils potentiellement affectés par un message électronique détecté, ainsi que le nombre d’alertes récentes générées pour ces appareils dans Microsoft Defender pour Endpoint.

L’image suivante illustre l’apparence de l’onglet **Appareils** lorsque l’intégration de Microsoft Defender for Endpoint est activée :

![Lorsque Microsoft Defender pour le point de terminaison est activé, vous pouvez voir une liste d’appareils avec des alertes.](../../media/fec928ea-8f0c-44d7-80b9-a2e0a8cd4e89.PNG)

Dans cet exemple, vous pouvez voir que les destinataires du message électronique détecté ont quatre appareils et un a une alerte. Le fait de cliquer sur le lien d’un appareil ouvre sa page [dans Microsoft 365 Defender](../defender-endpoint/microsoft-defender-security-center.md) (anciennement Centre de sécurité Microsoft Defender).

> [!TIP]
> Le Microsoft 365 Defender remplace le Centre de sécurité Microsoft Defender. Voir [Microsoft Defender pour le point de terminaison dans Microsoft 365 Defender.](../defender/microsoft-365-security-center-mde.md)

## <a name="requirements"></a>Conditions requises

- Votre organisation doit avoir Microsoft Defender pour Office 365 (ou Office 365 E5) et Microsoft Defender pour point de terminaison.

- Vous devez être un administrateur général ou avoir un rôle d’administrateur de sécurité (par exemple, Administrateur de la sécurité) dans Microsoft 365. (Voir [Autorisations dans le Centre de sécurité & conformité)](permissions-in-the-security-and-compliance-center.md)

- Vous devez avoir accès à [l’Explorateur (ou aux détections en temps réel).](threat-explorer.md)

## <a name="to-integrate-microsoft-defender-for-office-365-with-microsoft-defender-for-endpoint"></a>Pour intégrer Microsoft Defender for Office 365 avec Microsoft Defender for Endpoint

L’intégration de Microsoft Defender pour Office 365 microsoft Defender pour le point de terminaison est définie dans Defender pour Point de terminaison et Defender pour Office 365.

1. En tant qu’administrateur général ou administrateur de sécurité, [https://protection.office.com](https://protection.office.com) connectez-vous. (Vous êtes alors Office 365 centre de sécurité & conformité.)

2. Dans le volet de navigation, choisissez **l’Explorateur de gestion** \> **des menaces.**

   ![Explorateur dans le menu Gestion des menaces](../../media/ThreatMgmt-Explorer-nav.png)

3. Dans le coin supérieur droit de l’écran, choisissez Defender pour le point de **terminaison Paramètres (MDE Paramètres).**

4. Dans la boîte de dialogue connexion Microsoft Defender pour point de terminaison, **Connecter à Microsoft Defender pour point de terminaison.**

   ![Connexion microsoft Defender pour point de terminaison](../../media/Explorer-WDATPConnection-dialog.png)

5. Go to the Microsoft 365 Defender portal ( [https://security.microsoft.com](https://security.microsoft.com) .

6. Dans la barre de navigation, choisissez **Paramètres**. Ensuite, sous **Général,** choisissez **Fonctionnalités avancées.**

7. Faites défiler vers le **bas Office 365 la connexion Threat Intelligence,** puis allumez la connexion.

   ![Office 365 d’intelligence contre les menaces](../../media/mdatp-oatptoggle.png)

## <a name="related-articles"></a>Articles connexes

[Fonctionnalités d’examen et de réponse aux menaces dans Office 365](office-365-ti.md)

[Microsoft Defender pour Office 365](defender-for-office-365.md)

[Microsoft Defender pour point de terminaison](/windows/security/threat-protection)
