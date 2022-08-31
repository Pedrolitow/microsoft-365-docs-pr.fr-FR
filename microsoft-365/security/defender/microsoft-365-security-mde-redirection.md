---
title: Redirection de comptes de Microsoft Defender pour point de terminaison vers Microsoft 365 Defender
description: Comment rediriger des comptes et des sessions de Defender pour point de terminaison vers Microsoft 365 Defender.
keywords: Microsoft 365 Defender, Prise en main de Microsoft 365 Defender, redirection du centre de sécurité
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.subservice: m365d
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
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.openlocfilehash: 90ddf53090f79c3d372aa2119330e71919849bc0
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67479971"
---
# <a name="redirecting-accounts-from-microsoft-defender-for-endpoint-to-microsoft-365-defender"></a>Redirection de comptes de Microsoft Defender pour point de terminaison vers Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender
- Defender pour point de terminaison

Conformément à l’approche inter-domaines de Microsoft en matière de protection contre les menaces avec SIEM et la détection et la réponse étendues (XDR), nous avons renommé Microsoft Defender Advanced Threat Protection comme Microsoft Defender pour point de terminaison et l’avons unifiée dans un portail intégré unique : Microsoft 365 Defender.

Ce guide explique comment router des comptes vers Microsoft 365 Defender en activant la redirection automatique à partir de l’ancien portail Microsoft Defender pour point de terminaison (securitycenter.windows.com ou securitycenter.microsoft.com) vers <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank"> Microsoft 365 Defender</a>.

> [!NOTE]
> Microsoft Defender pour point de terminaison dans Microsoft 365 Defender prend en charge [l’octroi de l’accès aux fournisseurs de services de sécurité gérés (MSSP)](/windows/security/threat-protection/microsoft-defender-atp/grant-mssp-access) de la même façon que [l’accès est accordé dans le Centre de sécurité Microsoft Defender](./mssp-access.md).

## <a name="what-to-expect"></a>À quoi s'attendre

Une fois la redirection automatique activée, les comptes accédant à l’ancien portail Microsoft Defender pour point de terminaison à securitycenter.windows.com ou securitycenter.microsoft.com sont automatiquement routées vers Microsoft 365 Defender portail à <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank"><security.microsoft.com></a>.

En savoir plus sur ce qui a changé : [Microsoft Defender pour point de terminaison dans Microsoft 365 Defender](microsoft-365-security-center-mde.md).

Cela inclut la redirection pour l’accès direct à l’ancien portail via le navigateur, y compris les liens pointant vers l’ancien portail securitycenter.windows.com, tels que les liens dans les notifications par e-mail et les liens retournés par les appels d’API SIEM.  

 Les liens externes à partir de notifications par e-mail ou d’API SIEM contiennent actuellement des liens vers les deux portails. Une fois la redirection activée, les deux liens pointent vers Microsoft 365 Defender jusqu’à ce que l’ancien lien soit supprimé. Nous vous encourageons à adopter le nouveau lien pointant vers Microsoft 365 Defender.

Reportez-vous au tableau ci-dessous pour plus d’informations sur les liens et le routage.
## <a name="siem-api-routing"></a>Routage de l’API SIEM

| Propriété | Destination lorsque la redirection est désactivée | Destination lorsque la redirection est activée |
|---------|---------|---------|
| LinkToWDATP | Page d’alerte dans securitycenter.windows.com | Page d’alerte dans security.microsoft.com |
| IncidentLinkToWDATP | Page Incident dans securitycenter.windows.com | Page Incident dans security.microsoft.com |
| LinkToMTP | Page d’alerte dans security.microsoft.com | Page d’alerte dans security.microsoft.com |
| IncidentLinkToMTP | Page Incident dans security.microsoft.com | Page Incident dans security.microsoft.com |

## <a name="email-alert-notifications"></a>Email notifications d’alerte

| Propriété | Destination lorsque la redirection est OFF** | Destination lorsque la redirection est activée |
|---------|---------|---------|
| Page d’alerte | Page d’alerte dans securitycenter.windows.com | Page d’alerte dans security.microsoft.com |
| Page Incident |Page Incident dans securitycenter.windows.com | Page Incident dans security.microsoft.com |
| Page d’alerte dans le portail Defender pour cloud | Page d’alerte dans security.microsoft.com | Page d’alerte dans security.microsoft.com |
| Page Incident dans le portail Defender pour cloud | Page Incident dans security.microsoft.com | Page Incident dans security.microsoft.com |

## <a name="when-does-this-take-effect"></a>Quand cela prend-il effet ?

Une fois activée, cette mise à jour peut prendre effet presque immédiatement pour certains comptes. Toutefois, la redirection peut prendre plus de temps pour se propager à chaque compte de votre organisation. Les comptes dans les sessions actives pendant l’application de ce paramètre ne seront pas éjectés de leur session et seront routées uniquement vers Microsoft 365 Defender après avoir mis fin à leur session active et être reconnectés.  

### <a name="set-up-portal-redirection"></a>Configurer la redirection du portail

Pour démarrer le routage des comptes vers Microsoft 365 Defender :

1. Vérifiez que vous êtes administrateur général ou que vous disposez d’autorisations d’administrateur de sécurité dans Azure Active Directory.

2. Connectez-vous à <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>.

3. Accédez à La **redirection du portail** **général** >  **paramètres** > **des** >  points de terminaison ou [cliquez ici](https://security.microsoft.com/preferences2/portal_redirection).  

4. Basculez le paramètre de redirection automatique **sur Activé**.

5. Cliquez sur **Activer** pour appliquer la redirection automatique à Microsoft 365 Defender.

>[!IMPORTANT]
>L’activation de ce paramètre ne met pas fin aux sessions utilisateur actives. Les comptes qui se trouvent dans une session active pendant l’application de ce paramètre ne sont dirigés vers Microsoft 365 Defender qu’après la fin de leur session active et la nouvelle connexion.

>[!NOTE]
>Vous devez être administrateur général ou disposer d’autorisations d’administrateur de sécurité dans Azure Active Directory pour activer ou désactiver ce paramètre.  

## <a name="can-i-go-back-to-using-the-former-portal"></a>Puis-je revenir à l’utilisation de l’ancien portail ?

Si quelque chose ne fonctionne pas pour vous ou s’il y a quelque chose que vous ne pouvez pas terminer par Microsoft 365 Defender, nous voulons en entendre parler. Si vous avez rencontré des problèmes de redirection, nous vous encourageons à nous le faire savoir à l’aide du formulaire De soumission de commentaires.

Pour revenir à l’ancien portail Microsoft Defender pour point de terminaison :

1. Connectez-vous à <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> en tant qu’administrateur général ou utilisez et comptez avec des autorisations d’administrateur de sécurité dans Azure Active Directory.

2. Accédez à La **redirection du portail** **général** > **paramètres** >  >  ou [ouvrez la page ici](https://security.microsoft.com/preferences2/portal_redirection).  

3. Basculez le paramètre de redirection automatique sur **Désactivé**.

4. Cliquez sur **Désactiver** & partager vos commentaires lorsque vous y êtes invité.

Ce paramètre peut être réactivé à tout moment. 

Une fois désactivés, les comptes ne seront plus routées vers security.microsoft.com et vous aurez à nouveau accès à l’ancien portail , securitycenter.windows.com ou securitycenter.microsoft.com. 

## <a name="related-information"></a>Informations connexes
- [vue d’ensemble de Microsoft 365 Defender](microsoft-365-defender.md)
- [Microsoft Defender pour point de terminaison dans Microsoft 365 Defender](microsoft-365-security-center-mde.md)
- [Microsoft fournit des SIEM et XDR unifiés pour moderniser les opérations de sécurité](https://www.microsoft.com/security/blog/?p=91813) 
- [Infographie XDR et SIEM](https://afrait.com/blog/xdr-versus-siem/) 
- [`The New Defender`](https://afrait.com/blog/the-new-defender/) 
- [À propos de Microsoft 365 Defender](https://www.microsoft.com/microsoft-365/security/microsoft-365-defender) 
- [Portails de sécurité et centres d’administration Microsoft](portals.md)
