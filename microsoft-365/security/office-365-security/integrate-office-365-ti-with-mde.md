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
ms.openlocfilehash: 1d54e4ec40c636b8b3ea319e79cbad5005850952
ms.sourcegitcommit: c70067b4ef9c6f8f04aca68c35bb5141857c4e4b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "53029262"
---
# <a name="use-microsoft-defender-for-office-365-together-with-microsoft-defender-for-endpoint"></a>Utiliser Microsoft Defender pour les Office 365 avec Microsoft Defender pour le point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


[Microsoft Defender pour Office 365](defender-for-office-365.md) peut être configuré pour fonctionner avec [Microsoft Defender pour endpoint](/windows/security/threat-protection).

L’intégration de Microsoft Defender pour Office 365 avec Microsoft Defender for Endpoint peut aider votre équipe des opérations de sécurité à surveiller et à prendre des mesures rapidement si les appareils des utilisateurs sont exposés. Par exemple, une fois l’intégration activée, votre équipe des opérations de sécurité pourra voir les appareils potentiellement affectés par un message électronique détecté, ainsi que le nombre d’alertes récentes générées pour ces appareils dans Microsoft Defender pour Endpoint.

L’image suivante illustre l’apparence de l’onglet **Appareils** lorsque l’intégration de Microsoft Defender for Endpoint est activée :

![Lorsque Microsoft Defender pour le point de terminaison est activé, vous pouvez voir une liste d’appareils avec des alertes.](../../media/fec928ea-8f0c-44d7-80b9-a2e0a8cd4e89.PNG)

Dans cet exemple, vous pouvez voir que les destinataires du message électronique détecté ont quatre appareils et un a une alerte. Cliquer sur le lien d’un appareil ouvre sa page [dans Microsoft 365 Defender](../defender-endpoint/microsoft-defender-security-center.md) (anciennement centre de sécurité Microsoft Defender).

> [!TIP]
> Le Microsoft 365 Defender de l’entreprise remplace le Centre de sécurité Microsoft Defender. Voir [Microsoft Defender pour le point de terminaison dans Microsoft 365 Defender](../defender/microsoft-365-security-center-mde.md).

## <a name="requirements"></a>Conditions requises

- Votre organisation doit avoir Microsoft Defender pour Office 365 (ou Office 365 E5) et Microsoft Defender pour point de terminaison.

- Vous devez être un administrateur général ou avoir un rôle d’administrateur de sécurité (par exemple, Administrateur de la sécurité) dans Microsoft 365. Pour plus d’informations, [voir Autorisations dans le portail Microsoft 365 Defender.](permissions-microsoft-365-security-center.md)

- Vous devez avoir accès à [l’Explorateur (ou aux détections en temps réel).](threat-explorer.md)

## <a name="to-integrate-microsoft-defender-for-office-365-with-microsoft-defender-for-endpoint"></a>Pour intégrer Microsoft Defender for Office 365 avec Microsoft Defender for Endpoint

L’intégration de Microsoft Defender pour Office 365 microsoft Defender pour le point de terminaison est définie dans Defender pour Point de terminaison et Defender pour Office 365.

1. En tant qu’administrateur général ou administrateur de sécurité, <https://security.microsoft.com/threatexplorer> .

2. Dans le volet de navigation, sélectionnez **Email & Collaboration** \> **Explorer.**

3. Dans la page **Explorateur,** dans le coin supérieur droit de l’écran, cliquez sur **MDE Paramètres**.

4. Dans le volant de connexion **Microsoft Defender** pour point de terminaison qui s’affiche, Connecter à **Microsoft Defender** pour le point de terminaison ( Activer/ Activer), puis cliquez sur Fermer l’icône ![ ](../../media/scc-toggle-on.png) ![ ](../../media/m365-cc-sc-close-icon.png) **Fermer**.

    :::image type="content" source="../../media/explorer-mdeconnection-dialognew.png" alt-text="Connexion MDE":::

5. De retour dans le volet de navigation, choisissez **Paramètres**. Dans la **page Paramètres,** choisissez **Points de terminaison**

6. Dans la page **Points de terminaison** qui s’ouvre, choisissez **Fonctionnalités avancées.**

7. Faites défiler vers le **bas Office 365 la connexion Threat Intelligence,** puis allumez-la ![ (activer). ](../../media/scc-toggle-on.png)

   Lorsque vous avez terminé, cliquez sur **Enregistrer les préférences.**

## <a name="related-articles"></a>Articles connexes

[Fonctionnalités d’examen et de réponse aux menaces dans Office 365](office-365-ti.md)

[Microsoft Defender pour Office 365](defender-for-office-365.md)

[Microsoft Defender pour point de terminaison](/windows/security/threat-protection)
