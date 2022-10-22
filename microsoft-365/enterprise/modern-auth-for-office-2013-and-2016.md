---
title: Fonctionnement de l’authentification moderne pour les applications clientes Office 2013 et Office 2016
ms.author: tracyp
author: MSFTTracyP
manager: scotv
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
- scotvorg
- M365-security-compliance
description: Découvrez comment les fonctionnalités d’authentification moderne de Microsoft 365 fonctionnent différemment pour les applications clientes Office 2013 et 2016.
ms.openlocfilehash: e22f4106d52301acccebe53c6b42caa3663e2787
ms.sourcegitcommit: a250d043a2e42ecbc7b86147468d1660af5a6ba7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68672972"
---
# <a name="how-modern-authentication-works-for-office-2013-office-2016-and-office-2019-client-apps"></a>Fonctionnement de l’authentification moderne pour les applications clientes Office 2013, Office 2016 et Office 2019

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Lisez cet article pour découvrir comment les applications clientes Office 2013, Office 2016 et Office 2019 utilisent des fonctionnalités d’authentification modernes basées sur la configuration de l’authentification sur le client Microsoft 365 pour Exchange Online, SharePoint Online et Skype Entreprise Online.

> [!NOTE]
> Les applications clientes héritées, telles qu’Office 2010 et Office pour Mac 2011, ne prennent pas en charge l’authentification moderne et ne peuvent être utilisées qu’avec l’authentification de base.

## <a name="availability-of-modern-authentication-for-microsoft-365-services"></a>Disponibilité de l’authentification moderne pour les services Microsoft 365

Pour les services Microsoft 365, l’état par défaut de l’authentification moderne est :

- **Activé pour** Exchange Online par défaut. Consultez [Activer ou désactiver l’authentification moderne dans Exchange Online](https://support.office.com/article/58018196-f918-49cd-8238-56f57f38d662) pour la désactiver ou l’activer.

- **Activé pour** SharePoint Online par défaut.

- **Activé pour** Skype Entreprise Online par défaut. Consultez [Activer Skype Entreprise Online pour l’authentification moderne](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)afin de la désactiver ou de l’activer.

> [!NOTE]
> Pour les locataires créés **avant** le 1er août 2017, l’authentification moderne est **désactivée** par défaut pour Exchange Online et Skype Entreprise Online.

## <a name="sign-in-behavior-of-office-client-apps"></a>Comportement de connexion des applications clientes Office

Les applications clientes Office 2013 prennent en charge l’authentification héritée par défaut. Hérité signifie qu’ils prennent en charge l’Assistant de connexion Microsoft Online ou l’authentification de base. Pour que ces clients utilisent des fonctionnalités d’authentification modernes, les clés de Registre doivent être définies pour le client Windows. Pour obtenir des instructions, voir [Activer l’authentification moderne pour Office 2013 sur les appareils Windows](https://support.office.com/article/7dc1c01a-090f-4971-9677-f1b192d6c910).

> [!IMPORTANT]
> L’utilisation de l’authentification de base est déconseillée pour les boîtes aux lettres Exchange Online sur Microsoft 365. Cela signifie que si Outlook 2013 n’est pas configuré pour utiliser l’authentification moderne, il perd la possibilité de se connecter. Lisez [cet article](https://techcommunity.microsoft.com/t5/exchange-team-blog/basic-authentication-deprecation-in-exchange-online-september/ba-p/3609437) pour plus d’informations sur la dépréciation de l’authentification de base.

To enable modern authentication for any devices running Windows (for example on laptops and tablets), that have Microsoft Office 2013 installed, you need to set the following registry keys. The keys have to be set on each device that you want to enable for modern authentication:

|**Clé de Registre**|**Type**|**Valeur** |
|:-------|:------:|--------:|
|HKEY_CURRENT_USER\SOFTWARE\Microsoft\Office\15.0\Common\Identity\EnableADAL  |REG_DWORD  |1  |
|HKEY_CURRENT_USER\SOFTWARE\Microsoft\Office\15.0\Common\Identity\Version |REG_DWORD |1 |
|HKEY_CURRENT_USER\Software\Microsoft\Exchange\AlwaysUseMSOAuthForAutoDiscover |REG_DWORD |1 |

Consultez [Utilisation de l’authentification moderne (ADAL) avec Skype Entreprise](./hybrid-modern-auth-overview.md) pour en savoir plus sur son fonctionnement avec Skype Entreprise.

## <a name="software-requirements"></a>Configuration logicielle requise

Pour activer l’authentification multifacteur (MFA) pour les applications clientes Office 2013, vous devez avoir installé les logiciels répertoriés ci-dessous (à la version répertoriée ci-dessous ou une version *ultérieure* ). Le processus est différent en fonction de votre type d’installation (msi-based, or via Click-to-run).

Tout d’abord, déterminez si votre installation d’Office est basée sur MSI ou « Démarrer en un clic » en suivant les étapes ci-dessous.

1. Démarrez Outlook 2013.
2. Dans le menu **Fichier** , sélectionnez **Compte Office**.
3. Pour les installations d’Outlook 2013 Démarrer en un *clic* , un élément **Options de mise à jour** s’affiche. Pour les installations basées sur MSI, l'élément Options de mise à jour ne s'affiche pas.
    1. Le bouton Options de **mise à jour** « Démarrer en un clic » indique « Mises à jour sont automatiquement téléchargés et installés » et votre version actuelle.

### <a name="click-to-run-based-installations"></a>Installations de type Démarrer en un clic

Pour les installations basées sur démarrer en un clic, les logiciels suivants *doivent être* installés dans une version de fichier répertoriée ci-dessous ou dans une version *de fichier ultérieure* . Si votre version de fichier n’est pas égale ou supérieure à la version de fichier répertoriée, mettez-la à jour en suivant les étapes ci-dessous.


|Nom de fichier  |Chemin d'installation sur votre ordinateur  |Version du fichier  |
|---------|---------|---------|
|MSO.DLL     |C:\Program Files\Microsoft Office 15\root\vfs\ProgramFilesCommonx86\Microsoft Shared\OFFICE15\MSO.DLL       |15.0.4753.1001       |
|CSI.DLL   |CSI.DLL C:\Program Files\Microsoft Office 15\root\office15\csi.dll         |15.0.4753.1000        |
|Groove.EXE*     |C:\Program Files\Microsoft Office 15\root\office15\GROOVE.exe       |15.0.4763.1000      |
|Outlook.exe     |C:\Program Files\Microsoft Office 15\root\office15\OUTLOOK.exe         |15.0.4753.1002     |
|ADAL.DLL    |C:\Program Files\Microsoft Office 15\root\vfs\ProgramFilesCommonx86\Microsoft Shared\OFFICE15\ADAL.DLL       |1.0.2016.624         |
|Iexplore.exe    |C:\Program Files\Internet Explorer     |variable         |

\* Si le composant Groove.EXE n’est pas présent dans votre installation Office, il n’a pas besoin d’être installé pour qu’ADAL fonctionne. Toutefois, si elle est présente, la build pour Groove.EXE répertoriée ici est obligatoire.

### <a name="msi-based-installations"></a>Installations basées sur MSI

Pour les installations basées sur MSI, les logiciels suivants *doivent* être installés à la version de fichier répertoriée ci-dessous, ou à une version *de fichier ultérieure* . Si votre version de fichier n’est pas égale ou supérieure à la version de fichier répertoriée ci-dessous, mettez à jour à l’aide du lien dans la colonne *Mettre à jour l’article* de la base de connaissances.


|Nom de fichier  |Chemin d'installation sur votre ordinateur  |Où obtenir la mise à jour  |Version  |
|---------|---------|---------|---------|
|MSO.DLL|C:\Program Files\Common Files\Microsoft Shared\OFFICE15\MSO.DLL     |[KB3085480](https://support.microsoft.com/en-us/topic/description-of-the-security-update-for-office-2013-september-10-2019-0d171ba2-2eba-a2ca-a54d-c0f568de6bcc)        |15.0.4753.1001       |
|CSI.DLL|C:\Program Files\Common Files\Microsoft Shared\OFFICE15\Csi.dll     |[KB3172545](https://support.microsoft.com/en-us/topic/july-11-2017-update-for-office-2013-kb3172545-d6b47054-04d5-5154-40ba-3436d1e0efdb)        |15.0.4753.1000         |
|Groove.exe*|C:\Program Files\Microsoft Office\Office15\GROOVE.EXE            |[KB4022226](https://support.microsoft.com/en-us/topic/august-7-2018-update-for-onedrive-for-business-for-office-2013-kb4022226-6163bb26-cbde-eb16-ac42-abfda7afbf68)        |15.0.4763.1000         |
|Outlook.exe|C:\Program Files\Microsoft Office\Office15\OUTLOOK.EXE          |[KB4484096](https://support.microsoft.com/en-us/topic/october-1-2019-update-for-outlook-2013-kb4484096-6513145a-cc75-1cd1-72b7-78cb62d8476b)        |15.0.4753.1002         |
|ADAL.DLL|C:\Program Files\Common Files\Microsoft Shared\OFFICE15\ADAL.DLL   |[KB3085565](https://support.microsoft.com/en-us/topic/july-5-2016-update-for-office-2013-kb3085565-1d1a6d24-fbd4-1bae-242f-a35e0e2aba40)        |1.0.2016.624         |
|Iexplore.exe|C:\Program Files\Internet Explorer                             |[MS14-052](https://support.microsoft.com/en-us/topic/ms14-052-cumulative-security-update-for-internet-explorer-september-9-2014-17d29b71-9e78-0bc1-8961-7b812d04e4e1)         |Non applicable         |

\* Si le composant Groove.EXE n’est pas présent dans votre installation Office, il n’a pas besoin d’être installé pour qu’ADAL fonctionne. Toutefois, si elle est présente, la build pour Groove.EXE répertoriée ici est obligatoire.

Les clients Office 2016 et Office 2019 prennent en charge l’authentification moderne par défaut, et aucune action n’est nécessaire pour que le client utilise ces nouveaux flux. Toutefois, une action explicite est nécessaire pour utiliser l’authentification héritée.

Cliquez sur les liens ci-dessous pour voir comment Office 2013, Office 2016 et l’authentification cliente Office 2019 fonctionne avec les services Microsoft 365, selon que l’authentification moderne est activée ou non.

- [Exchange Online](modern-auth-for-office-2013-and-2016.md#BK_EchangeOnline)

- [SharePoint Online](modern-auth-for-office-2013-and-2016.md#BK_SharePointOnline)

- [Skype Entreprise Online](modern-auth-for-office-2013-and-2016.md#BK_SFBO)

<a name="BK_EchangeOnline"> </a>
### <a name="exchange-online"></a>Exchange Online

Le tableau suivant décrit le comportement d’authentification pour les applications clientes Office 2013, Office 2016 et Office 2019 lorsqu’elles se connectent à Exchange Online avec ou sans authentification moderne.

|Version de l’application cliente Office****|Clé de Registre présente ?****|Authentification moderne sur ?****|Comportement d’authentification avec l’authentification moderne activée pour le locataire (par défaut)****|Comportement d’authentification avec l’authentification moderne désactivée pour le locataire****|
|:-----|:-----|:-----|:-----|:-----|
|Office 2019  <br/> |Non <br> AlwaysUseMSOAuthForAutoDiscover = 1 <br/> |Oui  <br/> |Force l’authentification moderne sur Outlook 2013, 2016 ou 2019. <br/> [Plus d’informations](https://support.microsoft.com/help/3126599/outlook-prompts-for-password-when-modern-authentication-is-enabled)|Force l’authentification moderne au sein du client Outlook.<br/> |
|Office 2019  <br/> |Non ou EnableADAL = 1  <br/> |Oui  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’authentification de base est utilisée. Le serveur refuse l’authentification moderne lorsque le locataire n’est pas activé.  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’authentification de base est utilisée. Le serveur refuse l’authentification moderne lorsque le locataire n’est pas activé.  <br/> |
|Office 2019  <br/> |Oui, EnableADAL = 1  <br/> |Oui  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’authentification de base est utilisée. Le serveur refuse l’authentification moderne lorsque le locataire n’est pas activé.  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’authentification de base est utilisée. Le serveur refuse l’authentification moderne lorsque le locataire n’est pas activé.  <br/> |
|Office 2019  <br/> |Oui, EnableADAL=0  <br/> |Non  <br/> |Authentification de base  <br/> |Authentification de base  <br/> |
|Office 2016  <br/> |Non <br> AlwaysUseMSOAuthForAutoDiscover = 1 <br/> |Oui  <br/> |Force l’authentification moderne sur 2013, 2016 ou 2019. <br/> [Plus d’informations](https://support.microsoft.com/help/3126599/outlook-prompts-for-password-when-modern-authentication-is-enabled)|Force l’authentification moderne au sein du client Outlook.<br/> |
|Office 2016  <br/> |Non ou EnableADAL = 1  <br/> |Oui  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’authentification de base est utilisée. Le serveur refuse l’authentification moderne lorsque le locataire n’est pas activé.  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’authentification de base est utilisée. Le serveur refuse l’authentification moderne lorsque le locataire n’est pas activé.  <br/> |
|Office 2016  <br/> |Oui, EnableADAL = 1  <br/> |Oui  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’authentification de base est utilisée. Le serveur refuse l’authentification moderne lorsque le locataire n’est pas activé.  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’authentification de base est utilisée. Le serveur refuse l’authentification moderne lorsque le locataire n’est pas activé.  <br/> |
|Office 2016  <br/> |Oui, EnableADAL=0  <br/> |Non  <br/> |Authentification de base  <br/> |Authentification de base  <br/> |
|Office 2013  <br/> |Non  <br/> |Non  <br/> |Authentification de base  <br/> |Authentification de base  <br/> |
|Office 2013  <br/> |Oui, EnableADAL = 1  <br/> |Oui  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’authentification de base est utilisée. Le serveur refuse l’authentification moderne lorsque le locataire n’est pas activé.  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’authentification de base est utilisée. Le serveur refuse l’authentification moderne lorsque le locataire n’est pas activé.  <br/> |

<a name="BK_SharePointOnline"> </a>
### <a name="sharepoint-online"></a>SharePoint Online

Le tableau suivant décrit le comportement d’authentification pour les applications clientes Office 2013, Office 2016 et Office 2019 lorsqu’elles se connectent à SharePoint Online avec ou sans authentification moderne.

|Version de l’application cliente Office****|Clé de Registre présente ?****|Authentification moderne sur ?****|Comportement d’authentification avec l’authentification moderne activée pour le locataire (par défaut)****|Comportement d’authentification avec l’authentification moderne désactivée pour le locataire****|
|:-----|:-----|:-----|:-----|:-----|
|Office 2019  <br/> |Non ou EnableADAL = 1  <br/> |Oui  <br/> |Authentification moderne uniquement.  <br/> |Échec de la connexion.  <br/> |
|Office 2019  <br/> |Oui, EnableADAL = 1  <br/> |Oui  <br/> |Authentification moderne uniquement.  <br/> |Échec de la connexion.  <br/> |
|Office 2019  <br/> |Oui, EnableADAL = 0  <br/> |Non  <br/> |Assistant de connexion Microsoft Online uniquement.  <br/> |Assistant de connexion Microsoft Online uniquement.  <br/> |
|Office 2016  <br/> |Non ou EnableADAL = 1  <br/> |Oui  <br/> |Authentification moderne uniquement.  <br/> |Échec de la connexion.  <br/> |
|Office 2016  <br/> |Oui, EnableADAL = 1  <br/> |Oui  <br/> |Authentification moderne uniquement.  <br/> |Échec de la connexion.  <br/> |
|Office 2016  <br/> |Oui, EnableADAL = 0  <br/> |Non  <br/> |Assistant de connexion Microsoft Online uniquement.  <br/> |Assistant de connexion Microsoft Online uniquement.  <br/> |
|Office 2013  <br/> |Non  <br/> |Non  <br/> |Assistant de connexion Microsoft Online uniquement.  <br/> |Assistant de connexion Microsoft Online uniquement.  <br/> |
|Office 2013  <br/> |Oui, EnableADAL = 1  <br/> |Oui  <br/> |Authentification moderne uniquement.  <br/> |Échec de la connexion.  <br/> |

### <a name="skype-for-business-online"></a>Skype Entreprise Online
<a name="BK_SFBO"> </a>

Le tableau suivant décrit le comportement d’authentification pour les applications clientes Office 2013, Office 2016 et Office 2019 lorsqu’elles se connectent à Skype Entreprise Online avec ou sans authentification moderne.

|Version de l’application cliente Office****|Clé de Registre présente ?****|Authentification moderne sur ?****|Comportement d’authentification avec l’authentification moderne activée pour le locataire****|Comportement d’authentification avec l’authentification moderne désactivée pour le locataire (par défaut)****|
|:-----|:-----|:-----|:-----|:-----|
|Office 2019  <br/> |Non ou EnableADAL = 1  <br/> |Oui  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’Assistant de connexion Microsoft Online est utilisé. Le serveur refuse l’authentification moderne lorsque les locataires Skype Entreprise Online ne sont pas activés.  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’Assistant de connexion Microsoft Online est utilisé. Le serveur refuse l’authentification moderne lorsque les locataires Skype Entreprise Online ne sont pas activés.  <br/> |
|Office 2019  <br/> |Oui, EnableADAL = 1  <br/> |Oui  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’Assistant de connexion Microsoft Online est utilisé. Le serveur refuse l’authentification moderne lorsque les locataires Skype Entreprise Online ne sont pas activés.  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’Assistant de connexion Microsoft Online est utilisé. Le serveur refuse l’authentification moderne lorsque les locataires Skype Entreprise Online ne sont pas activés.  <br/> |
|Office 2019  <br/> |Oui, EnableADAL = 0  <br/> |Non  <br/> |Assistant de connexion Microsoft Online uniquement.  <br/> |Assistant de connexion Microsoft Online uniquement.  <br/> |
|Office 2016  <br/> |Non ou EnableADAL = 1  <br/> |Oui  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’Assistant de connexion Microsoft Online est utilisé. Le serveur refuse l’authentification moderne lorsque les locataires Skype Entreprise Online ne sont pas activés.  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’Assistant de connexion Microsoft Online est utilisé. Le serveur refuse l’authentification moderne lorsque les locataires Skype Entreprise Online ne sont pas activés.  <br/> |
|Office 2016  <br/> |Oui, EnableADAL = 1  <br/> |Oui  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’Assistant de connexion Microsoft Online est utilisé. Le serveur refuse l’authentification moderne lorsque les locataires Skype Entreprise Online ne sont pas activés.  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’Assistant de connexion Microsoft Online est utilisé. Le serveur refuse l’authentification moderne lorsque les locataires Skype Entreprise Online ne sont pas activés.  <br/> |
|Office 2016  <br/> |Oui, EnableADAL = 0  <br/> |Non  <br/> |Assistant de connexion Microsoft Online uniquement.  <br/> |Assistant de connexion Microsoft Online uniquement.  <br/> |
|Office 2013  <br/> |Non  <br/> |Non  <br/> |Assistant de connexion Microsoft Online uniquement.  <br/> |Assistant de connexion Microsoft Online uniquement.  <br/> |
|Office 2013  <br/> |Oui, EnableADAL = 1  <br/> |Oui  <br/> |L’authentification moderne est tentée en premier. Si le serveur refuse une connexion d’authentification moderne, l’Assistant de connexion Microsoft Online est utilisé. Le serveur refuse l’authentification moderne lorsque les locataires Skype Entreprise Online ne sont pas activés.  <br/> |Assistant de connexion Microsoft Online uniquement.  <br/> |

## <a name="see-also"></a>Voir aussi

[Activer l’Authentification moderne pour Office 2013 sur les appareils Windows](../admin/security-and-compliance/enable-modern-authentication.md)

[Authentification multifacteur pour Microsoft 365](../admin/security-and-compliance/multi-factor-authentication-microsoft-365.md)

[Se connecter à Microsoft 365 avec l’authentification multifacteur](https://support.microsoft.com/office/sign-in-to-microsoft-365-with-multi-factor-authentication-2b856342-170a-438e-9a4f-3c092394d3cb)

[Vue d’ensemble de Microsoft 365 Entreprise](microsoft-365-overview.md)
