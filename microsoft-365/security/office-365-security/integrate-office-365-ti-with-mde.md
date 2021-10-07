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
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
description: Utilisez Microsoft Defender pour Office 365 avec Microsoft Defender pour le point de terminaison pour obtenir des informations plus détaillées sur les menaces contre vos appareils et le contenu de votre courrier électronique.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: c0d532f06ce4757e8bca7f337992706480916aba
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60149597"
---
# <a name="use-microsoft-defender-for-office-365-together-with-microsoft-defender-for-endpoint"></a>Utiliser Microsoft Defender pour les Office 365 avec Microsoft Defender pour le point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


[Microsoft Defender pour Office 365](defender-for-office-365.md) peut être configuré pour fonctionner avec [Microsoft Defender pour le point de terminaison.](/windows/security/threat-protection)

L’intégration de Microsoft Defender pour Office 365 avec Microsoft Defender for Endpoint peut aider votre équipe des opérations de sécurité à surveiller et à prendre des mesures rapidement si les appareils des utilisateurs sont exposés. Par exemple, une fois l’intégration activée, votre équipe des opérations de sécurité pourra voir les appareils potentiellement affectés par un message électronique détecté, ainsi que le nombre d’alertes récentes générées pour ces appareils dans Microsoft Defender pour Endpoint.

L’image suivante illustre à quoi ressemble l’onglet **Appareils** lorsque l’intégration de Microsoft Defender pour les points de terminaison est activée :

![Lorsque Microsoft Defender pour le point de terminaison est activé, vous pouvez voir une liste d’appareils avec des alertes.](../../media/fec928ea-8f0c-44d7-80b9-a2e0a8cd4e89.PNG)

Dans cet exemple, vous pouvez voir que les destinataires du message électronique détecté ont quatre appareils et un a une alerte. Le fait de cliquer sur le lien d’un appareil ouvre sa page dans le [portail Microsoft 365 Defender](../defender-endpoint/microsoft-defender-security-center.md) (anciennement centre de sécurité Microsoft Defender).

> [!TIP]
> Le Microsoft 365 Defender de l’entreprise remplace le Centre de sécurité Microsoft Defender. Voir [Microsoft Defender pour le point de terminaison dans Microsoft 365 Defender](../defender/microsoft-365-security-center-mde.md).

## <a name="requirements"></a>Conditions requises

- Votre organisation doit avoir Microsoft Defender pour Office 365 (ou Office 365 E5) et Microsoft Defender pour point de terminaison.

- Le rôle d’administrateur général ou d’administrateur de sécurité doit être attribué dans Microsoft 365. Pour plus d’informations, consultez [Autorisations dans le portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md).

- Vous devez avoir accès à [l’Explorateur (ou aux détections en temps réel).](threat-explorer.md)

## <a name="to-integrate-microsoft-defender-for-office-365-with-microsoft-defender-for-endpoint"></a>Pour intégrer Microsoft Defender for Office 365 avec Microsoft Defender for Endpoint

L’intégration de Microsoft Defender pour Office 365 microsoft Defender pour le point de terminaison est définie dans Defender pour Point de terminaison et Defender pour Office 365.

1. Go to the Microsoft 365 Defender portal ( [https://security.microsoft.com](https://security.microsoft.com) ) and sign in.

2. Go to **Email & collaboration** \> **Explorer**. 

3. Dans la page **Explorateur,** dans le coin supérieur droit de l’écran, sélectionnez **MDE Paramètres**.

3. Dans le volant de connexion **Microsoft Defender** pour point de terminaison qui s’affiche, Connecter à **Microsoft Defender** pour le point de terminaison ( Activer/ Activer), puis sélectionnez ![ ](../../media/scc-toggle-on.png) **Fermer**.

    :::image type="content" source="../../media/explorer-mdeconnection-dialognew.png" alt-text="Connexion MDE.":::

4. Dans le volet de navigation, choisissez **Paramètres**. Dans la **page Paramètres,** choisissez **Points de terminaison**

5. Dans la page **Points de terminaison** qui s’ouvre, choisissez **Fonctionnalités avancées.**

6. Faites défiler vers le **bas Office 365 la connexion Threat Intelligence,** puis allumez-la ( ![ Activer/ Activer). ](../../media/scc-toggle-on.png)

   Lorsque vous avez terminé, sélectionnez **Enregistrer les préférences.**

## <a name="see-also"></a>Voir aussi

[Fonctionnalités d’examen et de réponse aux menaces dans Office 365](office-365-ti.md)

[Microsoft Defender pour Office 365](defender-for-office-365.md)

[Microsoft Defender pour point de terminaison](/windows/security/threat-protection)
