---
title: Redirection des comptes du Centre Office 365 sécurité et conformité vers le nouveau Microsoft 365 Defender
description: Comment rediriger de Defender vers Office 365 vers Microsoft 365 Defender.
keywords: Microsoft 365 Defender, mise en Microsoft 365 Defender, redirection du centre de sécurité
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.custom:
- admindeeplinkDEFENDER
- admindeeplinkEXCHANGE
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 0253d0ac64443562053765c9f0cdaaee69aeaad6
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2021
ms.locfileid: "61421857"
---
# <a name="redirecting-accounts-from-office-365-security-and-compliance-center-to-microsoft-365-defender"></a>Redirection des comptes du Centre Office 365 sécurité et conformité vers Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender
- Defender pour Office 365

Cet article explique comment router des comptes vers Microsoft 365 Defender en activant la redirection automatique à partir de l’ancien Centre de sécurité et conformité Office 365 (protection.office.com), vers Microsoft 365 Defender (security.microsoft.com).

## <a name="what-to-expect"></a>À quoi s’attendre

Une fois la redirection automatique activée et active, les utilisateurs accédant aux fonctionnalités liées à la sécurité dans Office 365 Security and Compliance (protection.office.com), sont automatiquement acheminés vers <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>.

En savoir plus sur ce qui a changé [: Microsoft Defender pour Office 365 dans Microsoft 365 Defender](microsoft-365-security-center-mdo.md).

Lorsque la redirection automatique est désactivée, les utilisateurs sont acheminés vers Microsoft 365 Defender lorsqu’ils utilisent les fonctionnalités de sécurité dans le Centre Office 365 sécurité et conformité.

Il s’agit notamment des fonctionnalités de la section Gestion des menaces, des alertes (afficher les alertes et les stratégies d’alerte), ainsi que du tableau de bord et des rapports de gestion des menaces. Les éléments du Centre Office 365 sécurité et conformité qui ne sont pas liés à la sécurité ne sont pas redirigés vers Microsoft 365 Defender.

Les éléments liés à la conformité se trouvent dans le Centre de conformité Microsoft 365, et les éléments associés au flux de messagerie se trouvent dans le centre <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">d’administration Exchange.</a>

Toutes les autres fonctionnalités, que ce soit liées à la conformité ou aux fonctionnalités qui servent les deux ne sont pas affectées par la redirection.

### <a name="set-up-portal-redirection"></a>Configurer la redirection du portail

Depuis le début de l’octobre 2021, la redirection du portail est désormais effectuée automatiquement ou par défaut. Toutefois, si elle doit être temporairement désactivée, ces étapes suivent.

<!--To start routing accounts to Microsoft 365 Defender at <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">security.microsoft.com</a>:

1. Make sure you're a global administrator or have security administrator permissions in Azure Active directory.
2. Sign in to <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>.
3. Go to **Settings** > **Email & collaboration** > **Portal redirection**.  
4. Toggle the Automatic redirection setting to **On**.
5. Click **Enable** to apply automatic redirection to Microsoft 365 Defender.

> [!NOTE]
> After redirection is enabled, accounts in active sessions while this setting is applied will not be ejected from their session and will only be routed to Microsoft 365 Defender after ending their current session and signing back in again.-->

## <a name="can-i-go-back-to-using-the-former-portal"></a>Puis-je revenir à l’ancien portail ?

Si quelque chose ne fonctionne pas pour vous ou s’il y a quelque chose que vous ne parvenez pas à effectuer via Microsoft 365 Defender, nous voulons en savoir plus à son sujet à l’aide de l’option de commentaires du portail. Si vous avez rencontré des problèmes avec la redirection, n’hésitez pas à nous le faire savoir.

Pour revenir à l’ancien portail :

1. Connectez-vous <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> en tant qu’administrateur général ou en utilisant et compte avec des autorisations d’administrateur de sécurité dans Azure Active Directory.

2. Go to **Paramètres**  >  **Email & collaboration** Portal  >  **redirection**.

3. Désaffectez le paramètre de redirection **automatique.**

4. Cliquez **sur Désactiver le** partage & commentaires lorsque vous y avez été invité.

Ce paramètre peut être à nouveau activé à tout moment.

## <a name="related-information"></a>Informations connexes
- [Microsoft 365 Defender vue d’ensemble](microsoft-365-defender.md)
- [Microsoft Defender pour le point de terminaison dans Microsoft 365 Defender](microsoft-365-security-center-mde.md)
- [Microsoft fournit un SIEM et XDR unifiés pour moderniser les opérations de sécurité](https://www.microsoft.com/security/blog/?p=91813) 
- [Infographie XDR et SIEM](https://afrait.com/blog/xdr-versus-siem/) 
- [`The New Defender`](https://afrait.com/blog/the-new-defender/) 
- [À propos Microsoft 365 Defender](https://www.microsoft.com/microsoft-365/security/microsoft-365-defender) 
- [Portails de sécurité Microsoft et centres d’administration](portals.md)
