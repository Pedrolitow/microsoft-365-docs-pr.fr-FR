---
title: Redirection des comptes de Microsoft Defender pour Office 365 vers le nouveau Centre de sécurité Microsoft 365
description: Comment rediriger de Defender pour Office 365 vers le Centre de sécurité Microsoft 365.
keywords: Centre de sécurité Microsoft 365, Mise en place du Centre de sécurité Microsoft 365, redirection du centre de sécurité
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
ms.openlocfilehash: ce8c178b4c46a00b83833f008080b776f4dc7e60
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51064641"
---
# <a name="redirecting-accounts-from-microsoft-defender-for-office-365-to-the-microsoft-365-security-center"></a>Redirection des comptes de Microsoft Defender pour Office 365 vers le Centre de sécurité Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender
- Defender pour Office 365

Cet article explique comment router les comptes vers le Centre de sécurité Microsoft 365 en activant la redirection automatique de l’ancien Centre de sécurité et conformité Microsoft (protection.office.com ou securitycenter.microsoft.com) vers le Centre de sécurité Microsoft 365 (security.microsoft.com).

>[!NOTE]
> La fonctionnalité de redirection de portail est disponible uniquement pour les clients Office 365 E5 et Microsoft Defender pour Office P2.

## <a name="what-to-expect"></a>À quoi s’attendre
Une fois la redirection automatique activée et active, les utilisateurs accédant aux fonctionnalités liées à la sécurité dans Office 365 Security and Compliance (protection.office.com) sont automatiquement acheminés vers le Centre de sécurité Microsoft 365 ( https://security.microsoft.com) .  

En savoir plus sur ce qui a changé : Microsoft Defender pour Office 365 dans le Centre de sécurité [Microsoft 365.](microsoft-365-security-center-mdo.md)

Lorsque la redirection automatique est désactivée, les utilisateurs sont acheminés vers le Centre de sécurité Microsoft 365 lorsqu’ils utilisent les fonctionnalités de sécurité du Centre de sécurité et conformité Office 365.

Il s’agit notamment des fonctionnalités de la section Gestion des menaces, du tableau de bord et des rapports de gestion des menaces. Les éléments du Centre de sécurité et conformité Office 365 qui ne sont pas liés à la sécurité ne sont pas redirigés vers le Centre de sécurité Microsoft 365.

Les éléments liés à la conformité se trouvent dans le Centre de conformité Microsoft 365, et les éléments liés au flux de messagerie se trouvent dans le Centre d’administration Exchange.

Toutes les autres fonctionnalités, que ce soit liées à la conformité ou aux fonctionnalités qui servent les deux ne sont pas affectées par la redirection. Les alertes de sécurité Office 365 apparaissent dans le Centre de sécurité Microsoft 365 et le Centre de sécurité et conformité Office 365, sans redirection.  

### <a name="set-up-portal-redirection"></a>Configurer la redirection du portail
Pour démarrer le routage des comptes vers le Centre de sécurité Microsoft 365, security.microsoft.com :

1. Assurez-vous que vous êtes un administrateur général ou que vous avez des autorisations d’administrateur de sécurité dans Azure Active Directory.
2. [Connectez-vous](https://security.microsoft.com/) au Centre de sécurité Microsoft 365.
3. Accédez à **Paramètres**  >  **E-mail &**  >  **redirection du portail de collaboration.**  
4. Basculez le paramètre de redirection automatique sur **Sur**.
5. Cliquez **sur Activer** pour appliquer la redirection automatique vers le portail du Centre de sécurité Microsoft 365.

> [!NOTE]
> Une fois la redirection activée, les comptes dans les sessions actives pendant que ce paramètre est appliqué ne sont pas éjectés de leur session et sont acheminés uniquement vers le Centre de sécurité Microsoft 365 après avoir mis fin à leur session active et se sont de nouveau ré-signés.

## <a name="can-i-go-back-to-using-the-former-portal"></a>Puis-je revenir à l’ancien portail ?
Si quelque chose ne fonctionne pas pour vous ou s’il y a quelque chose que vous ne parvenez pas à effectuer via le portail du Centre de sécurité Microsoft 365, nous souhaitons en savoir plus à ce sujet à l’aide de l’option de commentaires du portail. Si vous avez rencontré des problèmes de redirection, nous vous encourageons à contacter votre pm directement via la prévisualisation privée ou faites-le nous savoir via le formulaire d’envoi de commentaires.

Pour revenir à l’ancien portail :

1. [Connectez-vous](https://security.microsoft.com/) au Centre de sécurité Microsoft 365 en tant qu’administrateur général ou en utilisant et en utilisant des comptes avec des autorisations d’administrateur de sécurité dans Azure Active Directory.

2. Accédez **à La redirection** du portail général  >  **des points de**  >    >  **terminaison des paramètres.**  

3. Désaffectez le paramètre de redirection **automatique.**

4. Cliquez **sur Désactiver le** partage & commentaires lorsque vous y avez été invité.

Ce paramètre peut être à nouveau activé à tout moment.

Une fois désactivés, les comptes ne seront plus acheminés vers security.microsoft.com, et vous aurez à nouveau accès à l’ancien portail ( securitycenter.windows.com ou securitycenter.microsoft.com).

## <a name="related-information"></a>Informations connexes
- [Vue d’ensemble du Centre de sécurité Microsoft 365](overview-security-center.md)
- [Microsoft Defender pour le point de terminaison dans le Centre de sécurité Microsoft 365](microsoft-365-security-center-mde.md)
- [Microsoft fournit un SIEM et XDR unifiés pour moderniser les opérations de sécurité](https://www.microsoft.com/security/blog/?p=91813) 
- [Infographie XDR et SIEM](https://afrait.com/blog/xdr-versus-siem/) 
- [Le nouveau defender](https://afrait.com/blog/the-new-defender/) 
- [À propos de Microsoft 365 Defender](https://www.microsoft.com/microsoft-365/security/microsoft-365-defender) 
- [Portails de sécurité Microsoft et centres d’administration](portals.md)