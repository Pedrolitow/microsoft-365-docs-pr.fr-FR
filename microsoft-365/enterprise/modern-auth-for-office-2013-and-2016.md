---
title: Fonctionnement de l’authentification moderne pour les applications clientes Office 2013 et Office 2016
ms.author: tracyp
author: MSFTTracyP
manager: scotv
ms.date: 8/1/2017
audience: Admin
ms.topic: conceptual
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- MED150
- GMA150
- GPA150
- GEA150
- BCS160
ms.assetid: e4c45989-4b1a-462e-a81b-2a13191cf517
ms.collection:
- M365-security-compliance
description: Découvrez comment les fonctionnalités d’authentification moderne de Microsoft 365 fonctionnent différemment pour les applications clientes Office 2013 et 2016.
ms.openlocfilehash: 36bd7252394cb23b2e1f8d4999e4c09095734716
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67690485"
---
# <a name="how-modern-authentication-works-for-office-2013-office-2016-and-office-2019-client-apps"></a>Fonctionnement de l’authentification moderne pour les applications clientes Office 2013, Office 2016 et Office 2019

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Lisez cet article pour découvrir comment les applications clientes Office 2013, Office 2016 et Office 2019 utilisent des fonctionnalités d’authentification modernes basées sur la configuration de l’authentification sur le locataire Microsoft 365 pour Exchange Online, SharePoint Online et Skype Entreprise Online.

> [!NOTE]
> Les applications clientes héritées, telles qu’Office 2010 et Office pour Mac 2011, ne prennent pas en charge l’authentification moderne et ne peuvent être utilisées qu’avec l’authentification de base.

## <a name="availability-of-modern-authentication-for-microsoft-365-services"></a>Disponibilité de l’authentification moderne pour les services Microsoft 365

Pour les services Microsoft 365, l’état par défaut de l’authentification moderne est :

- **Activé par** défaut pour Exchange Online. Consultez [Activer ou désactiver l’authentification moderne dans Exchange Online](https://support.office.com/article/58018196-f918-49cd-8238-56f57f38d662) pour la désactiver ou l’activer.

- **Activé par** défaut pour SharePoint Online.

- **Activé** par défaut pour Skype Entreprise Online. Voir [Activer Skype Entreprise Online pour que l’authentification moderne](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)l’éteigne ou l’active.

> [!NOTE]
> Pour les locataires créés **avant** le 1er août 2017, l’authentification moderne est **désactivée** par défaut pour Exchange Online et Skype Entreprise Online.

## <a name="sign-in-behavior-of-office-client-apps"></a>Comportement de connexion des applications clientes Office

Les applications clientes Office 2013 prennent en charge l’authentification héritée par défaut. Hérité signifie qu’ils prennent en charge l’assistant de connexion Microsoft Online ou l’authentification de base. Pour que ces clients utilisent des fonctionnalités d’authentification modernes, les clés de Registre doivent être définies pour le client Windows. Pour obtenir des instructions, consultez [Activer l’authentification moderne pour Office 2013 sur les appareils Windows](https://support.office.com/article/7dc1c01a-090f-4971-9677-f1b192d6c910).

Pour activer l'authentification moderne pour les appareils exécutant Windows (par exemple les ordinateurs portables et tablettes) et sur lesquels Microsoft Office 2013 est installé, vous devez définir les clés de Registre suivantes. Les clés doivent être définies sur chaque appareil pour lequel vous voulez activer l'authentification moderne :

|**Clé de Registre**|**Type**|**Valeur** |
|:-------|:------:|--------:|
|HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\EnableADAL  |REG_DWORD  |1  |
|HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\Version |REG_DWORD |1 |

Découvrez [comment utiliser l’authentification moderne (ADAL) avec Skype Entreprise](./hybrid-modern-auth-overview.md) pour en savoir plus sur son fonctionnement avec Skype Entreprise.

Les clients Office 2016 et Office 2019 prennent en charge l’authentification moderne par défaut, et aucune action n’est nécessaire pour que le client utilise ces nouveaux flux. Toutefois, une action explicite est nécessaire pour utiliser l’authentification héritée.

Cliquez sur les liens ci-dessous pour voir comment l’authentification client Office 2013, Office 2016 et Office 2019 fonctionne avec les services Microsoft 365, selon que l’authentification moderne est activée ou non.

- [Exchange Online](modern-auth-for-office-2013-and-2016.md#BK_EchangeOnline)

- [SharePoint Online](modern-auth-for-office-2013-and-2016.md#BK_SharePointOnline)

- [Skype Entreprise Online](modern-auth-for-office-2013-and-2016.md#BK_SFBO)

<a name="BK_EchangeOnline"> </a>
### <a name="exchange-online"></a>Exchange Online

Le tableau suivant décrit le comportement d’authentification pour les applications clientes Office 2013, Office 2016 et Office 2019 lorsqu’elles se connectent à Exchange Online avec ou sans authentification moderne.

|Version de l’application cliente Office****|Clé de Registre présente ?****|Authentification moderne activée ?****|Comportement d’authentification avec l’authentification moderne activée pour le locataire (par défaut)****|Comportement d’authentification avec l’authentification moderne désactivée pour le locataire****|
|:-----|:-----|:-----|:-----|:-----|
|Office 2019  <br/> |Non <br> AlwaysUseMSOAuthForAutoDiscover = 1 <br/> |Oui  <br/> |Force l’authentification moderne sur Outlook 2013, 2016 ou 2019. <br/> [Plus d’informations](https://support.microsoft.com/help/3126599/outlook-prompts-for-password-when-modern-authentication-is-enabled)|Force l’authentification moderne au sein du client Outlook.<br/> |
|Office 2019  <br/> |Non, ou EnableADAL = 1  <br/> |Oui  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’authentification de base est utilisée. Le serveur refuse l’authentification moderne lorsque le locataire n’est pas activé.  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’authentification de base est utilisée. Le serveur refuse l’authentification moderne lorsque le locataire n’est pas activé.  <br/> |
|Office 2019  <br/> |Oui, EnableADAL = 1  <br/> |Oui  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’authentification de base est utilisée. Le serveur refuse l’authentification moderne lorsque le locataire n’est pas activé.  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’authentification de base est utilisée. Le serveur refuse l’authentification moderne lorsque le locataire n’est pas activé.  <br/> |
|Office 2019  <br/> |Oui, EnableADAL=0  <br/> |Non  <br/> |Authentification de base  <br/> |Authentification de base  <br/> |
|Office 2016  <br/> |Non <br> AlwaysUseMSOAuthForAutoDiscover = 1 <br/> |Oui  <br/> |Force l’authentification moderne en 2013, 2016 ou 2019. <br/> [Plus d’informations](https://support.microsoft.com/help/3126599/outlook-prompts-for-password-when-modern-authentication-is-enabled)|Force l’authentification moderne au sein du client Outlook.<br/> |
|Office 2016  <br/> |Non, ou EnableADAL = 1  <br/> |Oui  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’authentification de base est utilisée. Le serveur refuse l’authentification moderne lorsque le locataire n’est pas activé.  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’authentification de base est utilisée. Le serveur refuse l’authentification moderne lorsque le locataire n’est pas activé.  <br/> |
|Office 2016  <br/> |Oui, EnableADAL = 1  <br/> |Oui  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’authentification de base est utilisée. Le serveur refuse l’authentification moderne lorsque le locataire n’est pas activé.  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’authentification de base est utilisée. Le serveur refuse l’authentification moderne lorsque le locataire n’est pas activé.  <br/> |
|Office 2016  <br/> |Oui, EnableADAL=0  <br/> |Non  <br/> |Authentification de base  <br/> |Authentification de base  <br/> |
|Office 2013  <br/> |Non  <br/> |Non  <br/> |Authentification de base  <br/> |Authentification de base  <br/> |
|Office 2013  <br/> |Oui, EnableADAL = 1  <br/> |Oui  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’authentification de base est utilisée. Le serveur refuse l’authentification moderne lorsque le locataire n’est pas activé.  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’authentification de base est utilisée. Le serveur refuse l’authentification moderne lorsque le locataire n’est pas activé.  <br/> |

<a name="BK_SharePointOnline"> </a>
### <a name="sharepoint-online"></a>SharePoint Online

Le tableau suivant décrit le comportement d’authentification pour les applications clientes Office 2013, Office 2016 et Office 2019 lorsqu’elles se connectent à SharePoint Online avec ou sans authentification moderne.

|Version de l’application cliente Office****|Clé de Registre présente ?****|Authentification moderne activée ?****|Comportement d’authentification avec l’authentification moderne activée pour le locataire (par défaut)****|Comportement d’authentification avec l’authentification moderne désactivée pour le locataire****|
|:-----|:-----|:-----|:-----|:-----|
|Office 2019  <br/> |Non, ou EnableADAL = 1  <br/> |Oui  <br/> |Authentification moderne uniquement.  <br/> |Échec de connexion.  <br/> |
|Office 2019  <br/> |Oui, EnableADAL = 1  <br/> |Oui  <br/> |Authentification moderne uniquement.  <br/> |Échec de connexion.  <br/> |
|Office 2019  <br/> |Oui, EnableADAL = 0  <br/> |Non  <br/> |Assistant de connexion Microsoft Online uniquement.  <br/> |Assistant de connexion Microsoft Online uniquement.  <br/> |
|Office 2016  <br/> |Non, ou EnableADAL = 1  <br/> |Oui  <br/> |Authentification moderne uniquement.  <br/> |Échec de connexion.  <br/> |
|Office 2016  <br/> |Oui, EnableADAL = 1  <br/> |Oui  <br/> |Authentification moderne uniquement.  <br/> |Échec de connexion.  <br/> |
|Office 2016  <br/> |Oui, EnableADAL = 0  <br/> |Non  <br/> |Assistant de connexion Microsoft Online uniquement.  <br/> |Assistant de connexion Microsoft Online uniquement.  <br/> |
|Office 2013  <br/> |Non  <br/> |Non  <br/> |Assistant de connexion Microsoft Online uniquement.  <br/> |Assistant de connexion Microsoft Online uniquement.  <br/> |
|Office 2013  <br/> |Oui, EnableADAL = 1  <br/> |Oui  <br/> |Authentification moderne uniquement.  <br/> |Échec de connexion.  <br/> |

### <a name="skype-for-business-online"></a>Skype Entreprise Online
<a name="BK_SFBO"> </a>

Le tableau suivant décrit le comportement d’authentification des applications clientes Office 2013, Office 2016 et Office 2019 lorsqu’elles se connectent à Skype Entreprise Online avec ou sans authentification moderne.

|Version de l’application cliente Office****|Clé de Registre présente ?****|Authentification moderne activée ?****|Comportement d’authentification avec l’authentification moderne activée pour le locataire****|Comportement d’authentification avec l’authentification moderne désactivée pour le locataire (par défaut)****|
|:-----|:-----|:-----|:-----|:-----|
|Office 2019  <br/> |Non, ou EnableADAL = 1  <br/> |Oui  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’Assistant connexion Microsoft Online est utilisé. Le serveur refuse l’authentification moderne lorsque Skype Entreprise locataires en ligne ne sont pas activés.  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’Assistant connexion Microsoft Online est utilisé. Le serveur refuse l’authentification moderne lorsque Skype Entreprise locataires en ligne ne sont pas activés.  <br/> |
|Office 2019  <br/> |Oui, EnableADAL = 1  <br/> |Oui  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’Assistant connexion Microsoft Online est utilisé. Le serveur refuse l’authentification moderne lorsque Skype Entreprise locataires en ligne ne sont pas activés.  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’Assistant connexion Microsoft Online est utilisé. Le serveur refuse l’authentification moderne lorsque Skype Entreprise locataires en ligne ne sont pas activés.  <br/> |
|Office 2019  <br/> |Oui, EnableADAL = 0  <br/> |Non  <br/> |Assistant de connexion Microsoft Online uniquement.  <br/> |Assistant de connexion Microsoft Online uniquement.  <br/> |
|Office 2016  <br/> |Non, ou EnableADAL = 1  <br/> |Oui  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’Assistant connexion Microsoft Online est utilisé. Le serveur refuse l’authentification moderne lorsque Skype Entreprise locataires en ligne ne sont pas activés.  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’Assistant connexion Microsoft Online est utilisé. Le serveur refuse l’authentification moderne lorsque Skype Entreprise locataires en ligne ne sont pas activés.  <br/> |
|Office 2016  <br/> |Oui, EnableADAL = 1  <br/> |Oui  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’Assistant connexion Microsoft Online est utilisé. Le serveur refuse l’authentification moderne lorsque Skype Entreprise locataires en ligne ne sont pas activés.  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’Assistant connexion Microsoft Online est utilisé. Le serveur refuse l’authentification moderne lorsque Skype Entreprise locataires en ligne ne sont pas activés.  <br/> |
|Office 2016  <br/> |Oui, EnableADAL = 0  <br/> |Non  <br/> |Assistant de connexion Microsoft Online uniquement.  <br/> |Assistant de connexion Microsoft Online uniquement.  <br/> |
|Office 2013  <br/> |Non  <br/> |Non  <br/> |Assistant de connexion Microsoft Online uniquement.  <br/> |Assistant de connexion Microsoft Online uniquement.  <br/> |
|Office 2013  <br/> |Oui, EnableADAL = 1  <br/> |Oui  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’Assistant connexion Microsoft Online est utilisé. Le serveur refuse l’authentification moderne lorsque Skype Entreprise locataires en ligne ne sont pas activés.  <br/> |Assistant de connexion Microsoft Online uniquement.  <br/> |

## <a name="see-also"></a>Voir aussi

[Activer l’Authentification moderne pour Office 2013 sur les appareils Windows](../admin/security-and-compliance/enable-modern-authentication.md)

[Authentification multifacteur pour Microsoft 365](../admin/security-and-compliance/multi-factor-authentication-microsoft-365.md)

[Se connecter à Microsoft 365 avec l’authentification multifacteur](https://support.microsoft.com/office/sign-in-to-microsoft-365-with-multi-factor-authentication-2b856342-170a-438e-9a4f-3c092394d3cb)

[Vue d’ensemble de Microsoft 365 Entreprise](microsoft-365-overview.md)