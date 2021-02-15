---
title: Comment configurer Exchange Server en local pour utiliser l’authentification moderne hybride
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 06/16/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: cef3044d-d4cb-4586-8e82-ee97bd3b14ad
ms.collection:
- M365-security-compliance
f1.keywords:
- NOCSH
description: Découvrez comment configurer une Exchange Server local pour utiliser l’authentification moderne hybride (HMA), ce qui vous offre une authentification et une autorisation utilisateur plus sécurisées.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 3841f429399500cfc24ebadc89c74d478d2290d9
ms.sourcegitcommit: ec293978e951b09903b79e6642aa587824935e0c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2021
ms.locfileid: "49780283"
---
# <a name="how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication"></a>Comment configurer Exchange Server en local pour utiliser l’authentification moderne hybride

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

L’authentification moderne hybride (HMA) est une méthode de gestion des identités qui offre une authentification et une autorisation utilisateur plus sécurisées et est disponible pour les déploiements hybrides Exchange Server locaux.

## <a name="fyi"></a>Pour info

Avant de commencer, j’appelle :

- Authentification moderne \> hybride HMA

- EXCH exchange local \>

- Exchange Online \> EXO

En outre, si un graphique de cet article possède un objet « grisé » ou « grisé » qui signifie que l’élément affiché en gris n’est pas inclus dans la configuration propre à *HMA.*

## <a name="enabling-hybrid-modern-authentication"></a>Activation de l’authentification moderne hybride

L’ment HMA signifie :

1. Veillez à respecter les préreqs avant de commencer.

1. Étant  donné que de nombreux prérequis sont courants pour Skype Entreprise et Exchange, la vue d’ensemble de l’authentification moderne hybride et les conditions préalables à son utilisation avec les serveurs Skype Entreprise et [Exchange locaux.](hybrid-modern-auth-overview.md) Faites-le avant de commencer l’une des étapes de cet article.

1. Ajout d’URL de service web local en tant que noms principaux de **service (SNS)** dans Azure AD.

1. S’assurer que tous les répertoires virtuels sont activés pour HMA

1. Recherche de l’objet EvoSTS Auth Server

1. Activation du HMA dans EXCH.

 **Remarque** Votre version d’Office prend-elle en charge MA ? Découvrez comment fonctionne l’authentification moderne pour les applications [clientes Office 2013 et Office 2016.](modern-auth-for-office-2013-and-2016.md)

## <a name="make-sure-you-meet-all-the-prerequisites"></a>Assurez-vous que vous répondez à toutes les conditions préalables

Étant donné que de nombreux prérequis sont courants pour Skype Entreprise et Exchange, examinez la vue d’ensemble de l’authentification moderne hybride et les conditions préalables à son utilisation avec les serveurs Skype Entreprise et [Exchange locaux.](hybrid-modern-auth-overview.md) Faites-le  *avant de*  commencer l’une des étapes de cet article.

## <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a>Ajouter des URL de service web local en tant que SSN dans Azure AD

Exécutez les commandes qui affectent vos URL de service web local en tant que SSN Azure AD. Les SSN sont utilisés par les appareils et les ordinateurs clients lors de l’authentification et de l’autorisation. Toutes les URL qui peuvent être utilisées pour se connecter depuis l’environnement local à Azure Active Directory (Azure AD) doivent être enregistrées dans Azure AD (cela inclut les espaces de noms internes et externes).

Tout d’abord, rassemblez toutes les URL que vous devez ajouter dans AAD. Exécutez les commandes ci-après en local :

```powershell
Get-MapiVirtualDirectory | FL server,*url*
Get-WebServicesVirtualDirectory | FL server,*url*
Get-ClientAccessServer | fl Name, AutodiscoverServiceInternalUri
Get-OABVirtualDirectory | FL server,*url*
Get-AutodiscoverVirtualDirectory | FL server,*url*
Get-OutlookAnywhere | FL server,*url*
```

Assurez-vous que les url à qui les clients peuvent se connecter sont répertoriées en tant que noms principaux de service HTTPS dans AAD.

1. Tout d’abord, connectez-vous à AAD [avec ces instructions.](connect-to-microsoft-365-powershell.md)

   **Remarque** Vous devez utiliser l’option _Connect-MsolService_ à partir de cette page pour pouvoir utiliser la commande ci-dessous.

2. Pour vos URL liées à Exchange, tapez la commande suivante :

   ```powershell
   Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 | select -ExpandProperty ServicePrincipalNames
   ```

   Prenez note (et capture d’écran pour comparaison ultérieure) de la sortie de cette commande, qui doit inclure un  *autodiscover.yourdomain.com*  https:// et une URL  *https:// mail.yourdomain.com,* mais principalement des SSN qui commencent par 00000002-0000-0ff1-ce00-0000000000000/. Si des URL https:// de votre site local sont manquantes, nous devons ajouter ces enregistrements spécifiques à cette liste.

3. Si vous ne voyez pas vos enregistrements MAPI/HTTP, EWS, ActiveSync, OAB et Autodiscover internes et externes dans cette liste, vous devez les ajouter à l’aide de la commande ci-dessous (les exemples d’URL sont ' ' et ' ', mais vous devez remplacer les exemples d’URL par les `mail.corp.contoso.com` `owa.contoso.com` **vôtres)**:

   ```powershell
   $x= Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000
   $x.ServicePrincipalnames.Add("https://mail.corp.contoso.com/")
   $x.ServicePrincipalnames.Add("https://owa.contoso.com/")
   Set-MSOLServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
   ```

4. Vérifiez que vos nouveaux enregistrements ont été ajoutés en exécutant à nouveau Get-MsolServicePrincipal commande de l’étape 2 et en regardant la sortie. Comparez la liste /capture d’écran d’avant à la nouvelle liste de SSN. Vous pouvez également prendre une capture d’écran de la nouvelle liste pour vos enregistrements. Si vous avez réussi, vous verrez les deux nouvelles URL dans la liste. En suivant notre exemple, la liste des SNS inclut désormais les URL spécifiques  `https://mail.corp.contoso.com`  et  `https://owa.contoso.com` .

## <a name="verify-virtual-directories-are-properly-configured"></a>Vérifier que les répertoires virtuels sont correctement configurés

Vérifiez maintenant qu’OAuth est correctement activé dans Exchange sur tous les répertoires virtuels qu’Outlook peut utiliser en exécutant les commandes suivantes :

```powershell
Get-MapiVirtualDirectory | FL server,*url*,*auth*
Get-WebServicesVirtualDirectory | FL server,*url*,*oauth*
Get-OABVirtualDirectory | FL server,*url*,*oauth*
Get-AutoDiscoverVirtualDirectory | FL server,*oauth*
```

Vérifiez la sortie pour vous assurer **qu’OAuth** est activé sur chacun de ces VDirs, il ressemblera à ceci (et l’élément clé à examiner est « OAuth » ) :

```powershell
Get-MapiVirtualDirectory | fl server,*url*,*auth*

Server                        : EX1
InternalUrl                   : https://mail.contoso.com/mapi
ExternalUrl                   : https://mail.contoso.com/mapi
IISAuthenticationMethods      : {Ntlm, OAuth, Negotiate}
InternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
ExternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
```

Si OAuth est absent d’un serveur et de l’un des quatre répertoires virtuels, vous devez l’ajouter à l’aide des commandes pertinentes avant de poursuivre ([Set-MapiVirtualDirectory](https://docs.microsoft.com/powershell/module/exchange/set-mapivirtualdirectory), [Set-WebServicesVirtualDirectory](https://docs.microsoft.com/powershell/module/exchange/set-webservicesvirtualdirectory), [Set-OABVirtualDirectory](https://docs.microsoft.com/powershell/module/exchange/set-oabvirtualdirectory)et [Set-AutodiscoverVirtualDirectory](https://docs.microsoft.com/powershell/module/exchange/set-autodiscovervirtualdirectory)).

## <a name="confirm-the-evosts-auth-server-object-is-present"></a>Vérifier que l’objet serveur d’th EvoSTS est présent

Revenir à l’Exchange Management Shell local pour cette dernière commande. Vous pouvez maintenant vérifier que votre site local dispose d’une entrée pour le fournisseur d’authentification evoSTS :

```powershell
Get-AuthServer | where {$_.Name -eq "EvoSts"}
```

Votre sortie doit afficher un authServer nommé EvoSts et l’état « Activé » doit être True. Si ce n’est pas le cas, vous devez télécharger et exécuter la version la plus récente de l’Assistant Configuration hybride.

 **Important** Si vous exécutez Exchange 2010 dans votre environnement, le fournisseur d’authentification EvoSTS ne sera pas créé.

## <a name="enable-hma"></a>Activer HMA

Exécutez la commande suivante dans l’Exchange Management Shell, en local :

```powershell
Set-AuthServer -Identity EvoSTS -IsDefaultAuthorizationEndpoint $true
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```

## <a name="verify"></a>Vérifier

Une fois que vous avez activé HMA, la connexion suivante d’un client utilise le nouveau flux d’authentification. Notez que le simple fait d’allumer HMA ne déclenche pas de réauthentication pour un client. Les clients se réauthentent en fonction de la durée de vie des jetons d’th et/ou des jetons dont ils ont.

Vous devez également maintenir la touche Ctrl vers le bas en même temps que vous cliquez avec le bouton droit sur l’icône du client Outlook (également dans le bac notifications Windows) et cliquez sur « État de la connexion ». Recherchez l’adresse SMTP du client par rapport à un type « Authn » de « Bearer » qui représente le jeton du porteur utilisé dans \* OAuth.

 **Remarque** Vous devez configurer Skype Entreprise avec HMA ? Vous aurez besoin de deux articles : un qui répertorie les [topologies](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported)pris en charge et un qui vous montre comment [faire la configuration](configure-skype-for-business-for-hybrid-modern-authentication.md).

## <a name="using-hybrid-modern-authentication-with-outlook-for-ios-and-android"></a>Utilisation de l’authentification moderne hybride avec Outlook pour iOS et Android

Si vous êtes un client local utilisant le serveur Exchange sur TCP 443, ignorez le traitement du trafic pour les plages d’adresses IP suivantes :

```text
52.125.128.0/20
52.127.96.0/23
```

## <a name="related-topics"></a>Rubriques connexes

[Configuration requise pour l’authentification moderne pour la transition d’Office 365 dédié/ITAR vers vNext](https://docs.microsoft.com/exchange/troubleshoot/modern-authentication/modern-authentication-configuration)
