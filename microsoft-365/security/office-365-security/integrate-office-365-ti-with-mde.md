---
title: Utiliser Microsoft Defender pour Office 365 avec Microsoft Defender pour point de terminaison
f1.keywords:
- NOCSH
keywords: intégrer, Microsoft Defender, Microsoft Defender pour point de terminaison
ms.author: deniseb
author: denisebmsft
manager: dansimp
ms.date: 12/02/2021
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
description: Utilisez Microsoft Defender pour Office 365 avec Microsoft Defender pour point de terminaison pour obtenir des informations plus détaillées sur les menaces contre vos appareils et le contenu de vos e-mails.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 8df364538e6a799557956a8d624b0561c626e4fd
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64971107"
---
# <a name="use-microsoft-defender-for-office-365-together-with-microsoft-defender-for-endpoint"></a>Utiliser Microsoft Defender pour Office 365 avec Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

[Microsoft Defender pour Office 365](defender-for-office-365.md) peut être configuré pour fonctionner avec [Microsoft Defender pour point de terminaison](/windows/security/threat-protection).

L’intégration de Microsoft Defender pour Office 365 à Microsoft Defender pour point de terminaison peut aider votre équipe chargée des opérations de sécurité à surveiller et à prendre des mesures rapidement si les appareils des utilisateurs sont à risque. Par exemple, une fois l’intégration activée, votre équipe chargée des opérations de sécurité peut voir les appareils potentiellement affectés par un message électronique détecté, ainsi que le nombre d’alertes récentes générées pour ces appareils dans Microsoft Defender pour point de terminaison.

L’image suivante montre à quoi ressemble l’onglet **Appareils** lorsque Microsoft Defender pour point de terminaison intégration est activée :

:::image type="content" source="../../media/fec928ea-8f0c-44d7-80b9-a2e0a8cd4e89.PNG" alt-text="Liste des appareils avec des alertes" lightbox="../../media/fec928ea-8f0c-44d7-80b9-a2e0a8cd4e89.PNG":::

Dans cet exemple, vous pouvez voir que les destinataires du message électronique détecté ont quatre appareils et un a une alerte. Le fait de cliquer sur le lien d’un appareil ouvre sa page dans le [portail Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender).

> [!TIP]
> Le portail Microsoft 365 Defender remplace le Centre de sécurité Microsoft Defender. Voir [Microsoft Defender pour point de terminaison dans Microsoft 365 Defender](../defender/microsoft-365-security-center-mde.md).

## <a name="requirements"></a>Configuration requise

- Votre organisation doit avoir Microsoft Defender pour Office 365 (ou Office 365 E5) et Microsoft Defender pour point de terminaison.

- Vous devez avoir le rôle d’administrateur général ou d’administrateur de sécurité attribué dans Microsoft 365. Pour plus d’informations, consultez [Autorisations dans le portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md).

- Vous devez avoir accès à [l’Explorateur (ou aux détections en temps réel).](threat-explorer.md)

## <a name="to-integrate-microsoft-defender-for-office-365-with-microsoft-defender-for-endpoint"></a>Pour intégrer Microsoft Defender pour Office 365 à Microsoft Defender pour point de terminaison

L’intégration de Microsoft Defender pour Office 365 à Microsoft Defender pour point de terminaison est configurée dans Defender pour point de terminaison et dans Defender pour Office 365.

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) et connectez-vous.

2. Accédez à **Email & Collaboration** \> **Explorer**.

3. Dans la page **Explorateur**, dans le coin supérieur droit de l’écran, sélectionnez **MDE Paramètres**.

3. Dans le **menu volant de connexion Microsoft Defender pour point de terminaison** qui s’affiche, activez **Connecter pour Microsoft Defender pour point de terminaison** (![activer/désactiver),](../../media/scc-toggle-on.png) puis sélectionnez **Fermer**.

   :::image type="content" source="../../media/explorer-mdeconnection-dialognew.png" alt-text="Page Connexion MDE" lightbox="../../media/explorer-mdeconnection-dialognew.png":::

4. Dans le volet de navigation, choisissez **Paramètres**. Dans la page **Paramètres**, choisissez **Points de terminaison**

5. Dans la page **Points de terminaison** qui s’ouvre, choisissez **Fonctionnalités avancées**.

6. Faites défiler jusqu’à **Office 365 connexion Threat Intelligence** et activez-la (![activer/désactiver).](../../media/scc-toggle-on.png)

   Lorsque vous avez terminé, **sélectionnez Enregistrer les préférences**.

## <a name="see-also"></a>Voir aussi

[Fonctionnalités d’investigation et de réponse aux menaces dans Office 365](office-365-ti.md)

[Microsoft Defender pour Office 365](defender-for-office-365.md)

[Microsoft Defender pour point de terminaison](/windows/security/threat-protection)
