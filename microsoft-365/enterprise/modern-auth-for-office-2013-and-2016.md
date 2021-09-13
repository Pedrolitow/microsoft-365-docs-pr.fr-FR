---
title: Fonctionnement de l’authentification moderne pour les applications clientes Office 2013 et Office 2016
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 8/1/2017
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
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
description: Découvrez comment Microsoft 365 fonctionnalités d’authentification moderne fonctionnent différemment pour Office applications clientes 2013 et 2016.
ms.openlocfilehash: 60b1729d9830fd12141d162c4fe721267e52d437
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59209234"
---
# <a name="how-modern-authentication-works-for-office-2013-office-2016-and-office-2019-client-apps"></a>Fonctionnement de l’authentification moderne Office 2013, Office 2016 et Office applications clientes 2019

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Lisez cet article pour savoir comment les applications clientes Office 2013, Office 2016 et Office 2019 utilisent des fonctionnalités d’authentification modernes basées sur la configuration de l’authentification sur le client Microsoft 365 pour Exchange Online, SharePoint Online et Skype Entreprise Online.

> [!NOTE]
> Les applications clientes héritées, telles que Office 2010 et Office pour Mac 2011, ne permettent pas l’authentification moderne et ne peuvent être utilisées qu’avec l’authentification de base.

## <a name="availability-of-modern-authentication-for-microsoft-365-services"></a>Disponibilité de l’authentification moderne pour Microsoft 365 services

Pour les services Microsoft 365, l’état par défaut de l’authentification moderne est :

- Cette **option est** Exchange Online par défaut. Voir [Activer ou désactiver l’authentification moderne dans Exchange Online](https://support.office.com/article/58018196-f918-49cd-8238-56f57f38d662) pour la désactiver ou l’activer.

- Cette **option est** SharePoint Online par défaut.

- Cette **option est Skype Entreprise** Online par défaut. Voir [Activer Skype Entreprise Online pour l’authentification](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)moderne pour la désactiver ou l’activer.

> [!NOTE]
> Pour les locataires créés **avant** le 1er août 2017, l’authentification moderne est **désactivée** par défaut pour Exchange Online et Skype Entreprise Online.

## <a name="sign-in-behavior-of-office-client-apps"></a>Comportement de la Office applications clientes

Office applications clientes 2013 permettent par défaut l’authentification héritée. L’héritage signifie qu’ils peuvent être en charge soit l’Assistant de authentification Microsoft Online, soit l’authentification de base. Pour que ces clients utilisent des fonctionnalités d’authentification modernes, le client Windows doit avoir des clés de Registre définies. Pour obtenir des instructions, [voir Enable Modern Authentication for Office 2013 on Windows devices](https://support.office.com/article/7dc1c01a-090f-4971-9677-f1b192d6c910).

Pour activer l'authentification moderne pour les appareils exécutant Windows (par exemple les ordinateurs portables et tablettes) et sur lesquels Microsoft Office 2013 est installé, vous devez définir les clés de Registre suivantes. Les clés doivent être définies sur chaque appareil pour lequel vous voulez activer l'authentification moderne :

|**Clé de Registre**|**Type**|**Valeur** |
|:-------|:------:|--------:|
|HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\EnableADAL  |REG_DWORD  |1  |
|HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\Version |REG_DWORD |1 |

Lisez [comment utiliser l’authentification moderne (ADAL) avec Skype Entreprise](./hybrid-modern-auth-overview.md) pour en savoir plus sur son fonctionnement avec Skype Entreprise.

Office 2016 et Office 2019 prendre en charge l’authentification moderne par défaut, et aucune action n’est nécessaire pour que le client utilise ces nouveaux flux. Toutefois, une action explicite est nécessaire pour utiliser l’authentification héritée.

Cliquez sur les liens ci-dessous pour voir comment l’authentification client Office 2013, Office 2016 et Office 2019 fonctionne avec les services Microsoft 365 selon que l’authentification moderne est ou non allumée.

- [Exchange Online](modern-auth-for-office-2013-and-2016.md#BK_EchangeOnline)

- [SharePoint Online](modern-auth-for-office-2013-and-2016.md#BK_SharePointOnline)

- [Skype Entreprise Online](modern-auth-for-office-2013-and-2016.md#BK_SFBO)

<a name="BK_EchangeOnline"> </a>
### <a name="exchange-online"></a>Exchange Online

Le tableau suivant décrit le comportement d’authentification pour les applications clientes Office 2013, Office 2016 et Office 2019 lorsqu’elles se connectent à Exchange Online avec ou sans authentification moderne.

|Office version de l’application cliente****|Clé de Registre présente ?*****|Authentification moderne sur ?****|Comportement de l’authentification moderne avec l’authentification moderne pour le client (par défaut)****|Comportement d’authentification avec l’authentification moderne désactivée pour le client****|
|:-----|:-----|:-----|:-----|:-----|
|Office 2019  <br/> |Non, <br> AlwaysUseMSOAuthForAutoDiscover = 1 <br/> |Oui  <br/> |Force l’authentification moderne Outlook 2013, 2016 ou 2019. <br/> [Plus d’informations](https://support.microsoft.com/help/3126599/outlook-prompts-for-password-when-modern-authentication-is-enabled)|Force l’authentification moderne au sein Outlook client.<br/> |
|Office 2019  <br/> |Non ou EnableADAL = 1  <br/> |Oui  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’authentification de base est utilisée. Le serveur refuse l’authentification moderne lorsque le client n’est pas activé.  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’authentification de base est utilisée. Le serveur refuse l’authentification moderne lorsque le client n’est pas activé.  <br/> |
|Office 2019  <br/> |Oui, EnableADAL = 1  <br/> |Oui  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’authentification de base est utilisée. Le serveur refuse l’authentification moderne lorsque le client n’est pas activé.  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’authentification de base est utilisée. Le serveur refuse l’authentification moderne lorsque le client n’est pas activé.  <br/> |
|Office 2019  <br/> |Oui, EnableADAL=0  <br/> |Non  <br/> |Authentification de base  <br/> |Authentification de base  <br/> |
|Office 2016  <br/> |Non, <br> AlwaysUseMSOAuthForAutoDiscover = 1 <br/> |Oui  <br/> |Force l’authentification moderne sur 2013, 2016 ou 2019. <br/> [Plus d’informations](https://support.microsoft.com/help/3126599/outlook-prompts-for-password-when-modern-authentication-is-enabled)|Force l’authentification moderne au sein Outlook client.<br/> |
|Office 2016  <br/> |Non ou EnableADAL = 1  <br/> |Oui  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’authentification de base est utilisée. Le serveur refuse l’authentification moderne lorsque le client n’est pas activé.  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’authentification de base est utilisée. Le serveur refuse l’authentification moderne lorsque le client n’est pas activé.  <br/> |
|Office 2016  <br/> |Oui, EnableADAL = 1  <br/> |Oui  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’authentification de base est utilisée. Le serveur refuse l’authentification moderne lorsque le client n’est pas activé.  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’authentification de base est utilisée. Le serveur refuse l’authentification moderne lorsque le client n’est pas activé.  <br/> |
|Office 2016  <br/> |Oui, EnableADAL=0  <br/> |Non  <br/> |Authentification de base  <br/> |Authentification de base  <br/> |
|Office 2013  <br/> |Non  <br/> |Non  <br/> |Authentification de base  <br/> |Authentification de base  <br/> |
|Office 2013  <br/> |Oui, EnableADAL = 1  <br/> |Oui  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’authentification de base est utilisée. Le serveur refuse l’authentification moderne lorsque le client n’est pas activé.  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’authentification de base est utilisée. Le serveur refuse l’authentification moderne lorsque le client n’est pas activé.  <br/> |

<a name="BK_SharePointOnline"> </a>
### <a name="sharepoint-online"></a>SharePoint Online

Le tableau suivant décrit le comportement d’authentification pour les applications clientes Office 2013, Office 2016 et Office 2019 lorsqu’elles se connectent à SharePoint Online avec ou sans authentification moderne.

|Office version de l’application cliente****|Clé de Registre présente ?*****|Authentification moderne sur ?****|Comportement de l’authentification moderne avec l’authentification moderne pour le client (par défaut)****|Comportement d’authentification avec l’authentification moderne désactivée pour le client****|
|:-----|:-----|:-----|:-----|:-----|
|Office 2019  <br/> |Non ou EnableADAL = 1  <br/> |Oui  <br/> |Authentification moderne uniquement.  <br/> |Échec de la connexion.  <br/> |
|Office 2019  <br/> |Oui, EnableADAL = 1  <br/> |Oui  <br/> |Authentification moderne uniquement.  <br/> |Échec de la connexion.  <br/> |
|Office 2019  <br/> |Oui, EnableADAL = 0  <br/> |Non  <br/> |Assistant de signature Microsoft Online uniquement.  <br/> |Assistant de signature Microsoft Online uniquement.  <br/> |
|Office 2016  <br/> |Non ou EnableADAL = 1  <br/> |Oui  <br/> |Authentification moderne uniquement.  <br/> |Échec de la connexion.  <br/> |
|Office 2016  <br/> |Oui, EnableADAL = 1  <br/> |Oui  <br/> |Authentification moderne uniquement.  <br/> |Échec de la connexion.  <br/> |
|Office 2016  <br/> |Oui, EnableADAL = 0  <br/> |Non  <br/> |Assistant de signature Microsoft Online uniquement.  <br/> |Assistant de signature Microsoft Online uniquement.  <br/> |
|Office 2013  <br/> |Non  <br/> |Non  <br/> |Assistant de signature Microsoft Online uniquement.  <br/> |Assistant de signature Microsoft Online uniquement.  <br/> |
|Office 2013  <br/> |Oui, EnableADAL = 1  <br/> |Oui  <br/> |Authentification moderne uniquement.  <br/> |Échec de la connexion.  <br/> |

### <a name="skype-for-business-online"></a>Skype Entreprise Online
<a name="BK_SFBO"> </a>

Le tableau suivant décrit le comportement d’authentification pour les applications clientes Office 2013, Office 2016 et Office 2019 lorsqu’elles se connectent à Skype Entreprise Online avec ou sans authentification moderne.

|Office version de l’application cliente****|Clé de Registre présente ?*****|Authentification moderne sur ?****|Comportement de l’authentification moderne pour le client****|Comportement d’authentification avec l’authentification moderne désactivée pour le client (par défaut)****|
|:-----|:-----|:-----|:-----|:-----|
|Office 2019  <br/> |Non ou EnableADAL = 1  <br/> |Oui  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’Assistant de connexion Microsoft Online est utilisé. Le serveur refuse l’authentification moderne Skype Entreprise les locataires En ligne ne sont pas activés.  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’Assistant de connexion Microsoft Online est utilisé. Le serveur refuse l’authentification moderne Skype Entreprise les locataires En ligne ne sont pas activés.  <br/> |
|Office 2019  <br/> |Oui, EnableADAL = 1  <br/> |Oui  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’Assistant de connexion Microsoft Online est utilisé. Le serveur refuse l’authentification moderne Skype Entreprise les locataires En ligne ne sont pas activés.  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’Assistant de connexion Microsoft Online est utilisé. Le serveur refuse l’authentification moderne Skype Entreprise les locataires En ligne ne sont pas activés.  <br/> |
|Office 2019  <br/> |Oui, EnableADAL = 0  <br/> |Non  <br/> |Assistant de signature Microsoft Online uniquement.  <br/> |Assistant de signature Microsoft Online uniquement.  <br/> |
|Office 2016  <br/> |Non ou EnableADAL = 1  <br/> |Oui  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’Assistant de connexion Microsoft Online est utilisé. Le serveur refuse l’authentification moderne Skype Entreprise les locataires En ligne ne sont pas activés.  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’Assistant de connexion Microsoft Online est utilisé. Le serveur refuse l’authentification moderne Skype Entreprise les locataires En ligne ne sont pas activés.  <br/> |
|Office 2016  <br/> |Oui, EnableADAL = 1  <br/> |Oui  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’Assistant de connexion Microsoft Online est utilisé. Le serveur refuse l’authentification moderne Skype Entreprise les locataires En ligne ne sont pas activés.  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’Assistant de connexion Microsoft Online est utilisé. Le serveur refuse l’authentification moderne Skype Entreprise les locataires En ligne ne sont pas activés.  <br/> |
|Office 2016  <br/> |Oui, EnableADAL = 0  <br/> |Non  <br/> |Assistant de signature Microsoft Online uniquement.  <br/> |Assistant de signature Microsoft Online uniquement.  <br/> |
|Office 2013  <br/> |Non  <br/> |Non  <br/> |Assistant de signature Microsoft Online uniquement.  <br/> |Assistant de signature Microsoft Online uniquement.  <br/> |
|Office 2013  <br/> |Oui, EnableADAL = 1  <br/> |Oui  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’Assistant de connexion Microsoft Online est utilisé. Le serveur refuse l’authentification moderne Skype Entreprise les locataires En ligne ne sont pas activés.  <br/> |Assistant de signature Microsoft Online uniquement.  <br/> |

## <a name="see-also"></a>Voir aussi

[Activer l’Authentification moderne pour Office 2013 sur les appareils Windows](../admin/security-and-compliance/enable-modern-authentication.md)

[Authentification multifacteur pour Microsoft 365](../admin/security-and-compliance/multi-factor-authentication-microsoft-365.md)

[Connectez-vous à Microsoft 365 avec l’authentification multifacteur](https://support.microsoft.com/office/sign-in-to-microsoft-365-with-multi-factor-authentication-2b856342-170a-438e-9a4f-3c092394d3cb)

[Vue d’ensemble de Microsoft 365 Entreprise](microsoft-365-overview.md)