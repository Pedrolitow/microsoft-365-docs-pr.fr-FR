---
title: Vue d’ensemble de l’authentification moderne hybride et configuration requise pour l’utilisation avec les serveurs Skype Entreprise et Exchange locaux
ms.author: kvice
ms.reviewer: smithre4
author: kelleyvice-msft
manager: scotv
ms.date: 12/03/2021
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
ms.assetid: ef753b32-7251-4c9e-b442-1a5aec14e58d
ms.collection:
- scotvorg
- M365-security-compliance
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
description: Dans cet article, vous allez découvrir l’authentification moderne hybride et les conditions préalables à l’utilisation avec des serveurs Skype Entreprise et Exchange locaux.
ms.openlocfilehash: 1a2fd711994d6400b1bc3751a90cec15e3f3426c
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68180690"
---
# <a name="hybrid-modern-authentication-overview-and-prerequisites-for-using-it-with-on-premises-skype-for-business-and-exchange-servers"></a>Vue d’ensemble de l’authentification moderne hybride et configuration requise pour l’utiliser avec les serveurs Skype Entreprise et Exchange locaux

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

_L’authentification moderne_ est une méthode de gestion des identités qui offre une authentification et une autorisation utilisateur plus sécurisées. Il est disponible pour Office 365 déploiements hybrides de Skype Entreprise serveur local et de serveur Exchange local, ainsi que pour les Skype Entreprise hybrides de domaine partagé. Cet article contient des liens vers des documents connexes sur les conditions préalables, la configuration/la désactivation de l’authentification moderne et à certaines informations relatives aux clients (par exemple, les clients Outlook et Skype).

- [Qu’est-ce que l’authentification moderne ?](hybrid-modern-auth-overview.md#BKMK_WhatisModAuth)
- [Qu’est-ce qui change lorsque j’utilise l’authentification moderne ?](hybrid-modern-auth-overview.md#BKMK_WhatChanges)
- [Vérifier l’état de l’authentification moderne de votre environnement local](hybrid-modern-auth-overview.md#BKMK_CheckStatus)
- [Remplissez-vous les conditions préalables pour l’authentification moderne ?](#do-you-meet-modern-authentication-prerequisites)
- [Que dois-je savoir d’autre avant de commencer ?](hybrid-modern-auth-overview.md#BKMK_Whatelse)

## <a name="what-is-modern-authentication"></a>Qu’est-ce que l’authentification moderne ?
<a name="BKMK_WhatisModAuth"> </a>

L’authentification moderne est le terme générique d’une combinaison de méthodes d’authentification et d’autorisation entre un client (par exemple, votre ordinateur portable ou votre téléphone) et un serveur, ainsi que certaines mesures de sécurité basées sur les stratégies d’accès que vous connaissez peut-être déjà. Elle comprend :

- **Méthodes d’authentification** : authentification multifacteur (MFA) ; l’authentification par carte à puce ; Authentification basée sur un certificat client
- **Méthodes d’autorisation**: implémentation de l’autorisation Open de Microsoft (OAuth)
- **Stratégies d’accès conditionnel** : accès conditionnel à la gestion des applications mobiles (GAM) et Azure Active Directory (Azure AD)

La gestion des identités des utilisateurs avec une authentification moderne donne aux administrateurs de nombreux outils différents à utiliser dans le cadre de la sécurisation des ressources et offre des méthodes plus sécurisées de gestion des identités à la fois pour les scénarios locaux (Exchange et Skype pour les entreprises), Exchange hybride et Skype Entreprise hybride/domaine fractionné .

Étant donné que Skype Entreprise fonctionne étroitement avec Exchange, le comportement de connexion Skype Entreprise utilisateurs clients sera affecté par l’état d’authentification moderne d’Exchange. Elle s’applique également si vous disposez d’une architecture hybride de _domaine partagé_ Skype Entreprise, dans laquelle vous avez Skype Entreprise Online et Skype Entreprise localement, avec des utilisateurs hébergés dans les deux emplacements.

Pour plus d’informations sur l’authentification moderne dans Office 365, consultez [Office 365 Prise en charge des applications clientes - authentification multifacteur](microsoft-365-client-support-multi-factor-authentication.md).

> [!IMPORTANT]
> Depuis août 2017, tous les nouveaux clients Office 365 qui incluent Skype Entreprise Online et Exchange Online ont l’authentification moderne activée par défaut. Les clients préexistants n’ont pas de modifications dans leur état MA par défaut, mais tous les nouveaux clients prennent automatiquement en charge l’ensemble étendu de fonctionnalités d’identité répertoriées ci-dessus. Pour vérifier votre état de MA, consultez la section [Vérifier l’état de l’authentification moderne de votre environnement local](hybrid-modern-auth-overview.md#BKMK_CheckStatus).

## <a name="what-changes-when-i-use-modern-authentication"></a>Qu’est-ce qui change lorsque j’utilise l’authentification moderne ?
<a name="BKMK_WhatChanges"> </a>

Lorsque vous utilisez l'authentification moderne avec Skype Entreprises ou le serveur Exchange sur site, vous continuez à *authentifier* les utilisateurs locaux, mais l'histoire de l'*autorisation* de leur accès aux ressources (comme les fichiers ou les e-mails) change. C'est pourquoi, bien que l'authentification moderne concerne la communication entre le client et le serveur, les mesures prises lors de la configuration de MA font que evoSTS (un service d'émission de jeton de sécurité utilisé par Azure AD) est défini comme serveur Auth pour Skype Entreprise et serveur Exchange locaux.

La modification apportée à evoSTS permet à vos serveurs locaux de tirer parti des fonctionnalités OAuth (émission de jeton) pour l’autorisation de vos clients, et permet également à vos serveurs locaux d’utiliser les méthodes de sécurité courantes dans le cloud (telles que l’authentification multifacteur). De plus, le evoSTS émet des jetons qui permettent aux utilisateurs de demander l’accès aux ressources sans fournir leur mot de passe dans le cadre de la demande. Quel que soit l'emplacement de vos utilisateurs (en ligne ou local), et quel que soit l'emplacement qui héberge la ressource nécessaire, EvoSTS devient le cœur de l'autorisation des utilisateurs et des clients une fois que l'authentification moderne configurée.

Par exemple, si un client Skype Entreprise doit accéder au serveur Exchange pour obtenir des informations de calendrier pour le compte d’un utilisateur, il utilise la bibliothèque d’authentification Microsoft (MSAL) pour ce faire. MSAL est une bibliothèque de code conçue pour rendre les ressources sécurisées de votre répertoire disponibles pour les applications clientes à l’aide de jetons de sécurité OAuth. MSAL fonctionne avec OAuth pour vérifier les revendications et échanger des jetons (plutôt que des mots de passe), pour accorder à un utilisateur l’accès à une ressource. Dans le passé, l’autorité d’une transaction comme celle-ci ( le serveur qui sait comment valider les revendications des utilisateurs et émettre les jetons nécessaires ) était peut-être un service de jetons de sécurité local, voire Services ADFS. Cependant, l’authentification moderne centralise cette autorité à l’aide d’Azure AD.

Cela signifie également que, même si vos environnements Exchange Server et Skype Entreprise peuvent être entièrement locaux, le serveur d’autorisation sera en ligne, et votre environnement local doit pouvoir créer et gérer une connexion à votre abonnement Office 365 dans le cloud (et l’instance Azure AD que votre abonnement utilise comme annuaire).

Qu’est-ce qui ne change pas ? Que vous soyez dans un environnement hybride divisé, ou que vous utilisiez Skype Entreprise et Exchange Server en local, tous les utilisateurs doivent d'abord s'authentifier en *local*. Dans une implémentation hybride de l’authentification moderne, _Lyncdiscovery_ et _Autodiscovery_ pointent vers votre serveur local.

> [!IMPORTANT]
> Si vous avez besoin de connaître les topologies de Skype Entreprise qui sont prises en charge par MA, celles-ci sont [documentées ici](/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported).

## <a name="check-the-modern-authentication-status-of-your-on-premises-environment"></a>Vérifier l’état de l’authentification moderne de votre environnement local
<a name="BKMK_CheckStatus"> </a>

Étant donné que l’authentification moderne modifie le serveur d’autorisation utilisé lorsque les services appliquent OAuth/S2S, vous devez savoir si l’authentification moderne est activée ou désactivée pour vos environnements locaux Skype Entreprise et Exchange. Vous pouvez vérifier l’état de vos serveurs Exchange en exécutant la commande PowerShell suivante :

```powershell
Get-OrganizationConfig | ft OAuth*
```

Si la valeur de la propriété _OAuth2ClientProfileEnabled_ est **faux**, l’authentification moderne est désactivée.

Pour plus d’informations sur l’applet de commande Get-OrganizationConfig, consultez [Get-OrganizationConfig](/powershell/module/exchange/get-organizationconfig).

Vous pouvez vérifier vos serveurs Skype Entreprise en exécutant la commande PowerShell suivante :

```powershell
Get-CSOAuthConfiguration
```

Si la commande renvoie une propriété _OAuthServers_ vide, ou si la valeur de la propriété _ClientADALAuthOverride_ n’est pas **Autorisée**, l’authentification moderne est désactivée.

Pour plus d’informations sur l’applet de commande Get-CsOAuthConfiguration, consultez [Get-CsOAuthConfiguration](/powershell/module/skype/get-csoauthconfiguration).

## <a name="do-you-meet-modern-authentication-prerequisites"></a>Remplissez-vous les conditions préalables pour l’authentification moderne ?

Vérifiez et cochez les éléments de votre liste avant de continuer :

- **Skype Entreprise spécifique**
  - La mise à jour cumulative de mai 2017 (CU5) est nécessaire pour tous les serveurs pour Skype Entreprise Server 2015 ou version ultérieure
    - **Exception** : solution de survie (SBA) sur la version actuelle (basée sur Lync 2013)
  - Votre domaine SIP est ajouté en tant que domaine fédéré dans Office 365
  - Tous les serveurs frontaux SFB doivent avoir des connexions sortantes vers Internet, vers des URL d’authentification Office 365 (TCP 443) et des url racine de certificat connues (TCP 80) répertoriées dans les lignes 56 et 125 de la section « Microsoft 365 Common and Office » de [Office 365 URL et plages d’adresses IP](urls-and-ip-address-ranges.md).

- **Skype Entreprise locale dans un environnement Office 365 hybride**
  - Déploiement de Skype Entreprise Server 2019 avec tous les serveurs exécutant Skype Entreprise Server 2019.
  - Déploiement de Skype Entreprise Server 2015 avec tous les serveurs exécutant Skype Entreprise Server 2015.
  - Un déploiement avec un maximum de deux versions de serveur différentes, comme indiqué ci-dessous :
    - Skype Entreprise Server 2015
    - Skype Entreprise Server 2019
  - Les mises à jour cumulatives les plus récentes doivent être installées sur tous les serveurs Skype Entreprise, pour rechercher et gérer toutes les mises à jour disponibles, consultez [Mises à jour de Skype Entreprise Server](/skypeforbusiness/sfb-server-updates).
  - Il n’existe pas de Lync Server 2010 ou 2013 dans l’environnement hybride.

>[!NOTE]
>Si vos serveurs frontaux Skype Entreprise utilisent un serveur proxy pour l'accès à Internet, l'adresse IP du serveur proxy et le numéro de port utilisé doivent être saisis dans la section de configuration du fichier web.config pour chaque frontal.

- C:\Program Files\Skype for Business Server 2015\Web Components\Web ticket\int\web.config
- C:\Program Files\Skype for Business Server 2015\Web Components\Web ticket\ext\web.config

```xml
<configuration>
  <system.net>
    <defaultProxy>
      <proxy
        proxyaddress="https://192.168.100.60:8080"
        bypassonlocal="true" />
    </defaultProxy>
  </system.net>
</configuration>
```

> [!IMPORTANT]
> Veillez à vous abonner au flux RSS pour [URL et plages d’adresses IP Office 365](urls-and-ip-address-ranges.md) pour rester à jour avec les dernières listes d’URL requises.

- **Serveur Exchange spécifique**
  - Vous utilisez Exchange Server 2013 CU19 et ultérieure, Exchange Server 2016 CU8 et ultérieure, ou Exchange Server 2019 CU1 et ultérieure.
  - Il n’y a pas de serveur Exchange Server 2010 dans l’environnement.
  - Le déchargement SSL n’est pas configuré. L’arrêt et le chiffrement SSL sont pris en charge.
  - Dans le cas où votre environnement utilise une infrastructure de serveur proxy pour autoriser les serveurs à se connecter à Internet, assurez-vous que le serveur proxy est défini sur tous les serveurs Exchange dans la propriété [InternetWebProxy](/powershell/module/exchange/set-exchangeserver).

- **Exchange Server en local dans un environnement Office 365 hybride**

  - Si vous utilisez Exchange Server 2013, au moins un serveur doit avoir les rôles serveur de boîtes aux lettres et serveur d’accès au client installés. Bien qu’il soit possible d’installer les rôles Boîte aux lettres et Accès client sur des serveurs distincts, nous vous recommandons vivement d’installer les deux rôles sur le même serveur pour fournir plus de fiabilité et d’amélioration des performances.
  - Si vous utilisez Exchange Server 2016 ou une version ultérieure, le rôle serveur de boîtes aux lettres doit être installé sur un serveur au minimum.
  - Il n’existe aucun serveur Exchange Server 2007 ou 2010 dans l’environnement hybride.
  - Les mises à jour cumulatives les plus récentes doivent être installées sur tous les serveurs Exchange, pour rechercher et gérer les mises à jour disponibles, consultez [Mettre à niveau Exchange vers les dernières mises à jour cumulatives](/exchange/plan-and-deploy/install-cumulative-updates).

- **Configuration requise pour le client et le protocole Exchange**

    La disponibilité de l’authentification moderne est déterminée par la combinaison du client, du protocole et de la configuration. Si l’authentification moderne n’est pas prise en charge par le client, le protocole et/ou la configuration, le client continue à utiliser l’authentification héritée.
  
    Les clients et protocoles suivants prennent en charge l’authentification moderne avec Exchange local lorsque l’authentification moderne est activée dans l’environnement :

  |**Clients**|**Protocole principal**|**Notes**|
  |:-----|:-----|:-----|
  |Outlook 2013 et version ultérieure  <br/> |MAPI sur HTTP  <br/> |MAPI sur HTTP doit être activé dans Exchange afin d’utiliser l’authentification moderne avec ces clients (activé ou True pour les nouvelles installations d’Exchange 2013 Service Pack 1 et versions ultérieures); Pour plus d’informations, consultez [le fonctionnement de l’authentification moderne pour les applications clientes Office 2013 et Office 2016](modern-auth-for-office-2013-and-2016.md).  <br/> Vérifiez que vous exécutez la build minimale requise d’Outlook, consultez [Dernières mises à jour pour les versions d’Outlook qui utilisent Windows Installer (MSI)](/officeupdates/outlook-updates-msi).  <br/> |
  |Outlook 2016 pour Mac et versions ultérieures  <br/> |Services Web Exchange  <br/> |  <br/> |
  |Outlook pour iOS et Android  <br/> | Technologie de synchronisation Microsoft <br/> |Pour plus d’informations, consultez [Utilisation de l’authentification moderne hybride avec Outlook pour iOS et Android](/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth).  <br/> |
  |Exchange ActiveSync clients (par exemple, iOS11 Mail)  <br/> |Exchange ActiveSync  <br/> |Pour les clients Exchange ActiveSync qui prennent en charge l’authentification moderne, vous devez recréer le profil pour passer de l’authentification de base à l’authentification moderne.  <br/> |

    Les clients et/ou protocoles qui ne sont pas répertoriés (par exemple, POP3) ne prennent pas en charge l’authentification moderne avec Exchange local et continuent d’utiliser des mécanismes d’authentification hérités même après l’activation de l’authentification moderne dans l’environnement.

- **Conditions préalables générales**
  - Les scénarios de forêt de ressources nécessitent une approbation bidirectionnelle avec la forêt de comptes pour garantir que les recherches SID appropriées sont effectuées lors des demandes d’authentification modernes hybrides. 
  - Si vous utilisez AD FS, vous devez disposer de Windows 2012 R2 AD FS 3.0 et versions ultérieures pour la fédération.
  - Vos configurations d’identité sont les types pris en charge par Azure AD Connect, tels que la synchronisation de hachage de mot de passe, l’authentification relais et le STS local pris en charge par Office 365.
  - Azure AD Connect est configuré et fonctionne pour la réplication et la synchronisation des utilisateurs.
  - Vous avez vérifié que le mode hybride est configuré à l’aide du mode de topologie hybride Exchange classique entre votre environnement local et Office 365. Déclaration de support officielle pour Exchange hybride indique que vous devez disposer d’une UC actuelle ou d’une UC - 1 actuelle.
    > [!NOTE]
    > L’authentification moderne hybride n’est pas prise en charge avec l’[Agent hybride](/exchange/hybrid-deployment/hybrid-agent).

  - Assurez-vous qu’un utilisateur de test local, ainsi qu’un utilisateur de test hybride hébergé dans Office 365, peut se connecter au client de bureau Skype Entreprise (si vous voulez utiliser l’authentification moderne avec Skype) et Microsoft Outlook (si vous souhaitez utiliser une authentification moderne avec Exchange).
  - Assurez-vous que le paramètre SignInOptions dans Microsoft Office n’est pas configuré sur son paramètre le plus restrictif. Pour plus d’informations, consultez [Comment autoriser Office à se connecter à Internet](/office365/troubleshoot/access-management/office-feature-disabled).

## <a name="what-else-do-i-need-to-know-before-i-begin"></a>Que dois-je savoir d’autre avant de commencer ?
<a name="BKMK_Whatelse"> </a>

- Tous les scénarios pour les serveurs locaux impliquent la configuration locale de l’authentification moderne (en fait, pour Skype Entreprise, une liste de topologies prises en charge est disponible) de sorte que le serveur responsable de l’authentification et de l’autorisation se trouve dans Microsoft Cloud (service de jeton de sécurité Azure AD, appelé « evoSTS ») et mettant à jour Azure AD sur les URL ou espaces de noms utilisés par votre installation locale de Skype Entreprise ou Exchange. Par conséquent, les serveurs locaux prennent une dépendance Microsoft Cloud. Il est possible de prendre en compte la configuration de l’authentification hybride.
- Cet article présente des liens vers d’autres qui vous aideront à choisir les topologies d’authentification moderne prises en charge (nécessaires uniquement pour Skype Entreprise) et les articles de procédure qui décrivent les étapes de configuration, ou les étapes de désactivation de l’authentification moderne, pour Exchange local et Skype Entreprise en local. Favorisez cette page dans votre navigateur si vous avez besoin d’une base domestique pour l’utilisation de l’authentification moderne dans votre environnement serveur.

## <a name="related-topics"></a>Rubriques connexes
<a name="BKMK_URLListforMA"> </a>

- [Comment configurer Exchange Server en local pour utiliser l’authentification moderne](configure-exchange-server-for-hybrid-modern-authentication.md)
- [Topologies Skype Entreprise prises en charge avec l’authentification moderne](/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported)
- [Comment configurer Skype Entreprise en local pour utiliser l’authentification moderne](configure-skype-for-business-for-hybrid-modern-authentication.md)
- [Suppression ou désactivation de l’authentification moderne hybride à partir de Skype Entreprise et Exchange](remove-or-disable-hybrid-modern-authentication-from-skype-for-business-and-excha.md)
