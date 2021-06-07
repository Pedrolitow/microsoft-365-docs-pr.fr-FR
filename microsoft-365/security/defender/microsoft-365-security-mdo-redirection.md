---
title: Redirection des comptes du Centre Office 365 sécurité et conformité vers le nouveau centre de sécurité Microsoft 365 de sécurité
description: Comment rediriger de Defender vers Office 365 centre de sécurité Microsoft 365 de sécurité.
keywords: Microsoft 365 de sécurité, mise en Microsoft 365 centre de sécurité, redirection du centre de sécurité
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
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 703d3c3c9086aa2bdfada560c009e8738dffbb18
ms.sourcegitcommit: 5d8de3e9ee5f52a3eb4206f690365bb108a3247b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2021
ms.locfileid: "52768968"
---
# <a name="redirecting-accounts-from-office-365-security-and-compliance-center-to-microsoft-365-security-center"></a>Redirection des comptes du Centre Office 365 sécurité et conformité vers Microsoft 365 de sécurité

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender
- Defender pour Office 365

Cet article explique comment router les comptes vers le centre de sécurité Microsoft 365 en activant la redirection automatique de l’ancien Centre de sécurité et conformité Office 365 (protection.office.com) vers le centre de sécurité Microsoft 365 (security.microsoft.com).

## <a name="what-to-expect"></a>À quoi s’attendre
Une fois la redirection automatique activée et active, les utilisateurs accédant aux fonctionnalités liées à la sécurité dans Office 365 Security and Compliance (protection.office.com) sont automatiquement acheminés vers le centre de sécurité Microsoft 365 ( https://security.microsoft.com) .  

En savoir plus sur ce qui a changé [: Microsoft Defender pour Office 365 dans le centre Microsoft 365 de sécurité.](microsoft-365-security-center-mdo.md)

Lorsque la redirection automatique est désactivée, les utilisateurs sont acheminés vers le centre de sécurité Microsoft 365 lorsqu’ils utilisent les fonctionnalités de sécurité du Centre de sécurité et de conformité Office 365.

Il s’agit notamment des fonctionnalités de la section Gestion des menaces, du tableau de bord et des rapports de gestion des menaces. Les éléments du Centre Office 365 sécurité et conformité qui ne sont pas liés à la sécurité ne sont pas redirigés vers le centre Microsoft 365 sécurité.

Les éléments liés à la conformité se trouvent dans le centre Microsoft 365 conformité, et les éléments liés au flux de messagerie se trouvent dans le centre d Exchange’administration.

Toutes les autres fonctionnalités, que ce soit liées à la conformité ou aux fonctionnalités qui servent les deux ne sont pas affectées par la redirection. Office 365 alertes de sécurité s’affichent à la fois dans le centre de sécurité Microsoft 365 et dans le centre Office 365 sécurité et conformité, sans redirection.  

### <a name="set-up-portal-redirection"></a>Configurer la redirection du portail
Pour démarrer le routage des comptes vers le centre de sécurité Microsoft 365 à l’security.microsoft.com :

1. Assurez-vous que vous êtes un administrateur général ou que vous avez des autorisations d’administrateur de sécurité dans Azure Active Directory.
2. [Connectez-vous](https://security.microsoft.com/) au centre Microsoft 365 sécurité.
3. Accédez à **Paramètres**  >  **courrier électronique &**  >  **redirection du portail de collaboration.**  
4. Basculez le paramètre de redirection automatique sur **Le**.
5. Cliquez **sur Activer** pour appliquer la redirection automatique au portail Microsoft 365 centre de sécurité.

> [!NOTE]
> Une fois la redirection activée, les comptes dans les sessions actives pendant que ce paramètre est appliqué ne sont pas éjectés de leur session et sont acheminés uniquement vers le centre de sécurité Microsoft 365 après avoir mis fin à leur session en cours et se sont de nouveau ré-signés.

## <a name="can-i-go-back-to-using-the-former-portal"></a>Puis-je revenir à l’ancien portail ?
Si quelque chose ne fonctionne pas pour vous ou s’il y a quelque chose que vous ne pouvez pas effectuer via le portail du centre de sécurité Microsoft 365, nous souhaitons en savoir plus à ce sujet à l’aide de l’option de commentaires du portail. Si vous avez rencontré des problèmes avec la redirection, n’hésitez pas à nous le faire savoir.

Pour revenir à l’ancien portail :

1. [Connectez-vous](https://security.microsoft.com/) au centre de sécurité Microsoft 365 en tant qu’administrateur général ou en utilisant et compte avec des autorisations d’administrateur de sécurité dans Azure Active Directory.

2. Accédez à **Paramètres**  >  **courrier électronique &**  >  **redirection du portail de collaboration.**   

3. Désaffectez le paramètre de redirection **automatique.**

4. Cliquez **sur Désactiver le** partage & commentaires lorsque vous y avez été invité.

Ce paramètre peut être à nouveau activé à tout moment.

Une fois désactivés, les comptes ne seront plus acheminés vers security.microsoft.com et vous aurez de nouveau accès à l’ancien portail ( securitycenter.windows.com ou securitycenter.microsoft.com).

## <a name="related-information"></a>Informations connexes
- [Vue d’ensemble du Centre de sécurité Microsoft 365](overview-security-center.md)
- [Microsoft Defender pour le point de terminaison dans le centre Microsoft 365 sécurité](microsoft-365-security-center-mde.md)
- [Microsoft fournit un SIEM et XDR unifiés pour moderniser les opérations de sécurité](https://www.microsoft.com/security/blog/?p=91813) 
- [Infographie XDR et SIEM](https://afrait.com/blog/xdr-versus-siem/) 
- [Nouveau defender](https://afrait.com/blog/the-new-defender/) 
- [À propos Microsoft 365 Defender](https://www.microsoft.com/microsoft-365/security/microsoft-365-defender) 
- [Portails de sécurité Microsoft et centres d’administration](portals.md)
