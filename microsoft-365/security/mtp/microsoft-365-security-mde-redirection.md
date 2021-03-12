---
title: Redirection des comptes de Microsoft Defender pour le point de terminaison vers le Centre de sécurité Microsoft 365
description: Comment rediriger les comptes et les sessions du point de terminaison Defender vers le Centre de sécurité Microsoft 365.
keywords: Centre de sécurité Microsoft 365, Mise en place du Centre de sécurité Microsoft 365, redirection du Centre de sécurité
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
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 626bc9950512438bfa43e6500adf72940ddcbfec
ms.sourcegitcommit: 3d48e198e706f22ac903b346cadda06b2368dd1e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2021
ms.locfileid: "50727564"
---
# <a name="redirecting-accounts-from-microsoft-defender-for-endpoint-to-the-microsoft-365-security-center"></a>Redirection des comptes de Microsoft Defender pour le point de terminaison vers le Centre de sécurité Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

[!INCLUDE [Prerelease](../includes/prerelease.md)]

**S’applique à :**
- Microsoft 365 Defender
- Defender pour point de terminaison

Dans l’alignement de l’approche multi-domaines de Microsoft en matière de protection contre les menaces avec LA DÉTECTION SIEM et la détection et réponse étendues (XDR), nous avons renommé Microsoft Defender – Protection avancée contre les menaces microsoft defender en Microsoft Defender pour point de terminaison et l’avons unifié en un portail intégré unique : le Centre de sécurité Microsoft 365.

Ce guide explique comment router les comptes vers le Centre de sécurité Microsoft 365 en activant la redirection automatique de l’ancien portail Microsoft Defender pour points de terminaison (securitycenter.windows.com ou securitycenter.microsoft.com) vers le portail du Centre de sécurité Microsoft 365 (security.microsoft.com).

> [!NOTE]
> Microsoft Defender pour le point de terminaison dans le Centre de sécurité Microsoft 365 prend en charge l’octroi de l’accès aux fournisseurs de services de sécurité [gérés (MSSP)](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/grant-mssp-access) de la même façon que l’accès est accordé dans le Centre de sécurité [Microsoft Defender.](https://docs.microsoft.com/microsoft-365/security/mtp/mssp-access)

## <a name="what-to-expect"></a>À quoi s’attendre
Une fois la redirection automatique activée, les comptes accédant à l’ancien portail Microsoft Defender for Endpoint sur securitycenter.windows.com ou securitycenter.microsoft.com sont automatiquement acheminés vers le portail du Centre de sécurité Microsoft 365 sur security.microsoft.com.
 
En savoir plus sur ce qui a changé : Microsoft Defender pour point de terminaison dans le Centre de sécurité [Microsoft 365.](microsoft-365-security-center-mde.md)

Cela inclut la redirection pour l’accès direct à l’ancien portail via le navigateur, y compris les liens pointant vers l’ancien portail securitycenter.windows.com, tels que les liens dans les notifications par courrier électronique et les liens renvoyés par les appels d’API SIEM.  

 Les liens externes provenant de notifications par courrier électronique ou d’API SIEM contiennent actuellement des liens vers les deux portails. Une fois la redirection activée, les deux liens pointent vers le Centre de sécurité Microsoft 365 jusqu’à ce que l’ancien lien soit finalement supprimé. Nous vous encourageons à adopter le nouveau lien pointant vers le Centre de sécurité Microsoft 365.

Pour plus d’informations sur les liens et le routage, voir le tableau ci-dessous.
## <a name="siem-api-routing"></a>Routage de l’API SIEM

|**Propriété**  |**Destination lorsque la redirection est off**  |**Destination lorsque la redirection est SUR** | 
|---------|---------|---------|
| LinkToWDATP | Page d’alerte dans securitycenter.windows.com | Page d’alerte dans security.microsoft.com  |
| IncidentLinkToWDATP | Page Incident dans securitycenter.windows.com  | Page Incident dans security.microsoft.com  |
| LinkToMTP | Page d’alerte dans security.microsoft.com | Page d’alerte dans security.microsoft.com  |
| IncidentLinkToMTP | Page Incident dans security.microsoft.com  | Page Incident dans security.microsoft.com  

## <a name="email-alert-notifications"></a>Notifications d’alerte par courrier électronique

|**Propriété**  |**Destination lorsque la redirection est off**  |**Destination lorsque la redirection est SUR** |
|---------|---------|---------|
| Page d’alerte  | Page d’alerte dans securitycenter.windows.com  | Page d’alerte dans security.microsoft.com  |
| Page Incident  |Page Incident dans securitycenter.windows.com  | Page Incident dans security.microsoft.com  
| Page d’alerte dans le portail du centre de sécurité | Page d’alerte dans security.microsoft.com | Page d’alerte dans security.microsoft.com | 
| Page Incident dans le portail centre de sécurité | Page Incident dans security.microsoft.com  | Page Incident dans security.microsoft.com  |

## <a name="when-does-this-take-effect"></a>Quand cela prend-il effet ? 
Une fois activée, cette mise à jour peut prendre effet presque immédiatement pour certains comptes. Toutefois, la propagation de la redirection vers chaque compte de votre organisation peut prendre plus de temps. Les comptes dans les sessions actives pendant que ce paramètre est appliqué ne seront pas éjectés de leur session et seront acheminés uniquement vers le Centre de sécurité Microsoft 365 après avoir mis fin à leur session en cours et en se dénouant à nouveau.  

### <a name="set-up-portal-redirection"></a>Configurer la redirection du portail
Pour démarrer le routage des comptes vers le Centre de sécurité Microsoft 365 :
1. Assurez-vous que vous êtes un administrateur général ou que vous avez des autorisations d’administrateur de sécurité dans Azure Active Directory 

2. [Connectez-vous](https://security.microsoft.com/) au Centre de sécurité Microsoft 365.

3. Accédez **à La redirection** du portail général des points de  >  **terminaison**  >    >   des paramètres [ou cliquez ici.](https://security.microsoft.com/preferences2/portal_redirection)  

4. Basculez le paramètre de redirection automatique sur **Le**.

5. Cliquez **sur Activer** pour appliquer la redirection automatique vers le portail du Centre de sécurité Microsoft 365.

>[!IMPORTANT]
>L’activation de ce paramètre ne met pas fin aux sessions utilisateur actives. Les comptes qui sont dans une session active pendant que ce paramètre est appliqué sont dirigés uniquement vers le Centre de sécurité Microsoft 365 après avoir mis fin à leur session active et se sont à nouveau signés.

>[!NOTE]
>Vous devez être administrateur général ou avoir des autorisations d’administrateur de sécurité dans Azure Active Directory pour activer ou désactiver ce paramètre.  

## <a name="can-i-go-back-to-using-the-former-portal"></a>Puis-je revenir à l’ancien portail ?
Si quelque chose ne fonctionne pas pour vous ou s’il y a quelque chose que vous ne pouvez pas effectuer via le portail du Centre de sécurité Microsoft 365, nous souhaitons en savoir plus. Si vous avez rencontré des problèmes avec la redirection, nous vous encourageons à nous le faire savoir à l’aide du formulaire d’envoi de commentaires.

Pour revenir à l’ancien portail Microsoft Defender pour points de terminaison :

1. [Connectez-vous](https://security.microsoft.com/) au Centre de sécurité Microsoft 365 en tant qu’administrateur général ou en utilisant et en utilisant des comptes avec des autorisations d’administrateur de sécurité dans Azure Active Directory.

2. Accédez **à La redirection** du portail général des points de terminaison des  >  **paramètres** ou  >    >   [ouvrez la page ici.](https://security.microsoft.com/preferences2/portal_redirection)  

3. Désaffectez le paramètre de redirection **automatique.**

4. Cliquez **sur Désactiver le** partage & commentaires lorsque vous y avez été invité.

Ce paramètre peut être à nouveau activé à tout moment. 

Une fois désactivés, les comptes ne seront plus acheminés vers security.microsoft.com, et vous aurez à nouveau accès à l’ancien portail : securitycenter.windows.com ou securitycenter.microsoft.com. 

## <a name="related-information"></a>Informations connexes
- [Vue d’ensemble du Centre de sécurité Microsoft 365](overview-security-center.md)
- [Microsoft Defender pour point de terminaison dans le Centre de sécurité Microsoft 365](microsoft-365-security-center-mde.md)
- [Microsoft fournit un SIEM et XDR unifiés pour moderniser les opérations de sécurité](https://www.microsoft.com/security/blog/?p=91813) 
- [Infographie XDR et SIEM](https://afrait.com/blog/xdr-versus-siem/) 
- [Nouveau defender](https://afrait.com/blog/the-new-defender/) 
- [À propos de Microsoft 365 Defender](https://www.microsoft.com/microsoft-365/security/microsoft-365-defender) 
- [Portails de sécurité Microsoft et centres d’administration](portals.md)
