---
title: Redirection des comptes de Microsoft Defender pour le point de terminaison vers Microsoft 365 Defender
description: Comment rediriger les comptes et les sessions du point de terminaison Defender vers Microsoft 365 Defender.
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
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 444336af04ddf971c4a58e1f12fc296ecf4bc629
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60191466"
---
# <a name="redirecting-accounts-from-microsoft-defender-for-endpoint-to-microsoft-365-defender"></a>Redirection des comptes de Microsoft Defender pour le point de terminaison vers Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender
- Defender pour point de terminaison

Dans l’alignement de l’approche multi-domaines de Microsoft en matière de protection contre les menaces avec LA DÉTECTION SIEM et la détection et réponse étendue (XDR), nous avons renommé Microsoft Defender – Protection avancée contre les menaces en Microsoft Defender pour point de terminaison et l’avons unifié en un portail intégré unique , Microsoft 365 Defender.

Ce guide explique comment router les comptes vers Microsoft 365 Defender en activant la redirection automatique à partir de l’ancien portail Microsoft Defender pour points de terminaison (securitycenter.windows.com ou securitycenter.microsoft.com), vers le portail Microsoft 365 Defender (security.microsoft.com).

> [!NOTE]
> Microsoft Defender pour le point de terminaison dans Microsoft 365 Defender prend en charge l’octroi de l’accès aux fournisseurs de services de sécurité [gérés (MSSP)](/windows/security/threat-protection/microsoft-defender-atp/grant-mssp-access) de la même façon que l’accès est accordé dans le Centre de sécurité [Microsoft Defender.](./mssp-access.md)

## <a name="what-to-expect"></a>À quoi s’attendre
Une fois la redirection automatique activée, les comptes accédant à l’ancien portail Microsoft Defender for Endpoint sur securitycenter.windows.com ou securitycenter.microsoft.com sont automatiquement acheminés vers le portail Microsoft 365 Defender sur security.microsoft.com.
 
En savoir plus sur ce qui a changé : Microsoft Defender pour point de [terminaison dans Microsoft 365 Defender](microsoft-365-security-center-mde.md).

Cela inclut la redirection pour l’accès direct à l’ancien portail via le navigateur, y compris les liens pointant vers l’ancien portail securitycenter.windows.com, tels que les liens dans les notifications par courrier électronique et les liens renvoyés par les appels d’API SIEM.  

 Les liens externes provenant de notifications par courrier électronique ou d’API SIEM contiennent actuellement des liens vers les deux portails. Une fois la redirection activée, les deux liens pointent vers Microsoft 365 Defender jusqu’à ce que l’ancien lien soit finalement supprimé. Nous vous encourageons à adopter le nouveau lien pointant vers Microsoft 365 Defender.

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
| Page Alerte dans le portail du centre de sécurité | Page d’alerte dans security.microsoft.com | Page d’alerte dans security.microsoft.com | 
| Page Incident dans le portail du centre de sécurité | Page Incident dans security.microsoft.com  | Page Incident dans security.microsoft.com  |

## <a name="when-does-this-take-effect"></a>Quand cela prend-il effet ? 
Une fois activée, cette mise à jour peut prendre effet presque immédiatement pour certains comptes. Toutefois, la propagation de la redirection vers chaque compte de votre organisation peut prendre plus de temps. Les comptes dans les sessions actives pendant que ce paramètre est appliqué ne sont pas éjectés de leur session et sont acheminés uniquement vers Microsoft 365 Defender après la fin de leur session active et la nouvelle ouverture de session.  

### <a name="set-up-portal-redirection"></a>Configurer la redirection du portail
Pour démarrer le routage des comptes vers Microsoft 365 Defender :
1. Assurez-vous que vous êtes un administrateur général ou que vous avez des autorisations d’administrateur de sécurité dans Azure Active Directory 

2. [Connectez-vous](https://security.microsoft.com/) à Microsoft 365 Defender.

3. Accédez à **Paramètres**  >  **redirection du** portail général des points de terminaison ou cliquez  >    >   [ici.](https://security.microsoft.com/preferences2/portal_redirection)  

4. Basculez le paramètre de redirection automatique sur **Le**.

5. Cliquez **sur Activer** pour appliquer la redirection automatique à Microsoft 365 Defender.

>[!IMPORTANT]
>L’activation de ce paramètre ne met pas fin aux sessions utilisateur actives. Les comptes qui sont dans une session active pendant que ce paramètre est appliqué ne sont dirigés vers les Microsoft 365 Defender qu’après avoir mis fin à leur session active et se sont à nouveau signés.

>[!NOTE]
>Vous devez être administrateur général ou avoir des autorisations d’administrateur de sécurité Azure Active Directory pour activer ou désactiver ce paramètre.  

## <a name="can-i-go-back-to-using-the-former-portal"></a>Puis-je revenir à l’ancien portail ?
Si quelque chose ne fonctionne pas pour vous ou s’il y a quelque chose que vous ne parvenez pas à effectuer Microsoft 365 Defender, nous voulons en savoir plus. Si vous avez rencontré des problèmes avec la redirection, nous vous encourageons à nous le faire savoir à l’aide du formulaire d’envoi de commentaires.

Pour revenir à l’ancien portail Microsoft Defender pour points de terminaison :

1. [Connectez-vous](https://security.microsoft.com/) Microsoft 365 Defender en tant qu’administrateur général ou en utilisant et compte avec les autorisations d’administrateur de sécurité dans Azure Active Directory.

2. Accédez à **Paramètres** redirection du portail général des points de terminaison  >    >    >   [ou ouvrez la page ici.](https://security.microsoft.com/preferences2/portal_redirection)  

3. Basculez le paramètre de redirection automatique sur **Désintégation.**

4. Cliquez **sur Désactiver le** partage & commentaires lorsque vous y avez été invité.

Ce paramètre peut être à nouveau activé à tout moment. 

Une fois désactivés, les comptes ne seront plus acheminés vers security.microsoft.com, et vous aurez à nouveau accès à l’ancien portail ( securitycenter.windows.com ou securitycenter.microsoft.com). 

## <a name="related-information"></a>Informations connexes
- [Microsoft 365 Defender vue d’ensemble](overview-security-center.md)
- [Microsoft Defender pour le point de terminaison dans Microsoft 365 Defender](microsoft-365-security-center-mde.md)
- [Microsoft fournit un SIEM et XDR unifiés pour moderniser les opérations de sécurité](https://www.microsoft.com/security/blog/?p=91813) 
- [Infographie XDR et SIEM](https://afrait.com/blog/xdr-versus-siem/) 
- [Nouveau defender](https://afrait.com/blog/the-new-defender/) 
- [À propos Microsoft 365 Defender](https://www.microsoft.com/microsoft-365/security/microsoft-365-defender) 
- [Portails de sécurité Microsoft et centres d’administration](portals.md)