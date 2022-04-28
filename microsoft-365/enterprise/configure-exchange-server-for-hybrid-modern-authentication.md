---
title: Comment configurer Exchange Server en local pour utiliser l’authentification moderne hybride
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/27/2021
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: cef3044d-d4cb-4586-8e82-ee97bd3b14ad
ms.collection:
- M365-security-compliance
f1.keywords:
- NOCSH
description: Découvrez comment configurer un Exchange Server local pour utiliser l’authentification moderne hybride (HMA), ce qui vous offre une authentification et une autorisation utilisateur plus sécurisées.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 2ee190a541fdf3e4e77a251e040f2cb69416088c
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095749"
---
# <a name="how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication"></a>Comment configurer Exchange Server en local pour utiliser l’authentification moderne hybride

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

L’authentification moderne hybride (HMA) est une méthode de gestion des identités qui offre une authentification et une autorisation utilisateur plus sécurisées et est disponible pour Exchange déploiements hybrides locaux de serveur.

## <a name="definitions"></a>Définitions

Avant de commencer, vous devez connaître certaines définitions :

- HMA d’authentification \> moderne hybride

- Exchange localement \> EXCH

- \> Exchange Online EXO

En outre, *si un graphique de cet article a un objet « grisé » ou « grisé », cela signifie que l’élément affiché en gris n’est pas inclus dans la configuration spécifique à HMA*.

## <a name="enabling-hybrid-modern-authentication"></a>Activation de l’authentification moderne hybride

L’activation de HMA signifie :

1. Veillez à respecter les prérequis avant de commencer.

1. Étant donné que de nombreux **prérequis sont courants** pour les Skype Entreprise et les Exchange, [la vue d’ensemble de l’authentification moderne hybride et les prérequis pour l’utiliser avec des serveurs Skype Entreprise locaux et Exchange](hybrid-modern-auth-overview.md). Effectuez cette opération avant de commencer l’une des étapes décrites dans cet article.
Exigences relatives aux boîtes aux lettres liées à insérer.

1. Ajout d’URL de service web locaux en tant que **noms de principal de service (SPN)** dans Azure AD. Si EXCH est hybride avec **plusieurs locataires**, ces URL de service web locaux doivent être ajoutées en tant que SPN dans le Azure AD de tous les locataires qui sont hybrides avec EXCH.

1. S’assurer que tous les répertoires virtuels sont activés pour HMA

1. Recherche de l’objet serveur d’authentification EvoSTS

1. Activation de HMA dans EXCH.

> [!NOTE]
> Votre version de Office prend-elle en charge ma ? Découvrez [le fonctionnement de l’authentification moderne pour les applications clientes Office 2013 et Office 2016](modern-auth-for-office-2013-and-2016.md).

## <a name="make-sure-you-meet-all-the-prerequisites"></a>Veillez à respecter toutes les conditions préalables

Étant donné que de nombreux prérequis sont courants pour les Skype Entreprise et les Exchange, passez en revue la [vue d’ensemble de l’authentification moderne hybride et les prérequis pour l’utiliser avec des serveurs Skype Entreprise locaux et Exchange](hybrid-modern-auth-overview.md). Effectuez cette opération  *avant*  de commencer l’une des étapes décrites dans cet article.

> [!NOTE]
> Outlook Web App et Exchange Panneau de configuration ne fonctionne pas avec l’authentification moderne hybride.

## <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a>Ajouter des URL de service web locaux en tant que SPN dans Azure AD

Exécutez les commandes qui affectent vos URL de service web locales en tant que Azure AD SPN. Les SPN sont utilisés par les ordinateurs clients et les appareils lors de l’authentification et de l’autorisation. Toutes les URL qui peuvent être utilisées pour se connecter de l’environnement local à Azure Active Directory (Azure AD) doivent être inscrites dans Azure AD (cela inclut des espaces de noms internes et externes).

Tout d’abord, rassemblez toutes les URL que vous devez ajouter dans AAD. Exécutez ces commandes localement :

```powershell
Get-MapiVirtualDirectory | FL server,*url*
Get-WebServicesVirtualDirectory | FL server,*url*
Get-ClientAccessServer | fl Name, AutodiscoverServiceInternalUri
Get-OABVirtualDirectory | FL server,*url*
Get-AutodiscoverVirtualDirectory | FL server,*url*
Get-OutlookAnywhere | FL server,*hostname*
```

Vérifiez que les clients d’URL auxquels les clients peuvent se connecter sont répertoriés en tant que noms de principaux de service HTTPS dans AAD. Si EXCH est dans un environnement hybride avec **plusieurs locataires**, ces SPN HTTPS doivent être ajoutés dans le AAD de tous les locataires hybrides avec EXCH.

1. Tout d’abord, connectez-vous à AAD avec [ces instructions](connect-to-microsoft-365-powershell.md).

    > [!NOTE]
    > Vous devez utiliser l’option _Connecter-MsolService_ de cette page pour pouvoir utiliser la commande ci-dessous.

2. Pour vos URL liées à Exchange, tapez la commande suivante :

   ```powershell
   Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 | select -ExpandProperty ServicePrincipalNames
   ```

   Notez (et capture d’écran pour une comparaison ultérieure) la sortie de cette commande, qui doit inclure une et `https://*mail.yourdomain.com*` une `https://*autodiscover.yourdomain.com*` URL, mais principalement composée de noms de principal du service qui commencent par `00000002-0000-0ff1-ce00-000000000000/`. S’il manque `https://` des URL de votre site local, ces enregistrements spécifiques doivent être ajoutés à cette liste.

3. Si vous ne voyez pas vos enregistrements MAPI/HTTP, EWS, ActiveSync, OAB et De découverte automatique internes et externes dans cette liste, vous devez les ajouter à l’aide de la commande ci-dessous (les exemples d’URL sont `mail.corp.contoso.com` et `owa.contoso.com`, mais vous **remplaceriez les exemples d’URL par les vôtres**) :

   ```powershell
   $x= Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000
   $x.ServicePrincipalnames.Add("https://mail.corp.contoso.com/")
   $x.ServicePrincipalnames.Add("https://owa.contoso.com/")
   Set-MSOLServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
   ```

4. Vérifiez que vos nouveaux enregistrements ont été ajoutés en exécutant à nouveau la `Get-MsolServicePrincipal` commande à partir de l’étape 2 et en examinant la sortie. Comparez la liste/capture d’écran d’avant à la nouvelle liste de noms de principal du service. Vous pouvez également prendre une capture d’écran de la nouvelle liste de vos enregistrements. Si vous avez réussi, vous verrez les deux nouvelles URL dans la liste. En suivant notre exemple, la liste des SPN inclut désormais les URL `https://mail.corp.contoso.com` spécifiques et `https://owa.contoso.com`.

## <a name="verify-virtual-directories-are-properly-configured"></a>Vérifier que les répertoires virtuels sont correctement configurés

Vérifiez maintenant qu’OAuth est correctement activé dans Exchange sur tous les répertoires virtuels que Outlook pouvez utiliser en exécutant les commandes suivantes :

```powershell
Get-MapiVirtualDirectory | FL server,*url*,*auth*
Get-WebServicesVirtualDirectory | FL server,*url*,*oauth*
Get-OABVirtualDirectory | FL server,*url*,*oauth*
Get-AutoDiscoverVirtualDirectory | FL server,*oauth*
```

Vérifiez la sortie pour vous assurer **qu’OAuth** est activé sur chacun de ces VDirs. Il ressemblera à ceci (et la chose clé à examiner est « OAuth » ) :

```powershell
Get-MapiVirtualDirectory | fl server,*url*,*auth*

Server                        : EX1
InternalUrl                   : https://mail.contoso.com/mapi
ExternalUrl                   : https://mail.contoso.com/mapi
IISAuthenticationMethods      : {Ntlm, OAuth, Negotiate}
InternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
ExternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
```

Si OAuth est absent d’un serveur et de l’un des quatre répertoires virtuels, vous devez l’ajouter à l’aide des commandes appropriées avant de continuer ([Set-MapiVirtualDirectory](/powershell/module/exchange/set-mapivirtualdirectory), [Set-WebServicesVirtualDirectory](/powershell/module/exchange/set-webservicesvirtualdirectory), [Set-OABVirtualDirectory](/powershell/module/exchange/set-oabvirtualdirectory) et [Set-AutodiscoverVirtualDirectory](/powershell/module/exchange/set-autodiscovervirtualdirectory)).

## <a name="confirm-the-evosts-auth-server-object-is-present"></a>Confirmer que l’objet serveur d’authentification EvoSTS est présent

Revenez à l’interpréteur de commandes Exchange Management Shell local pour cette dernière commande. Vous pouvez maintenant vérifier que votre environnement local dispose d’une entrée pour le fournisseur d’authentification evoSTS :

```powershell
Get-AuthServer | where {$_.Name -like "EvoSts*"} | ft name,enabled
```

Votre sortie doit afficher un AuthServer du nom EvoSts avec un GUID et l’état « Activé » doit être True. Si vous ne le voyez pas, vous devez télécharger et exécuter la version la plus récente de l’Assistant Configuration hybride.

> [!NOTE]
> Si EXCH est hybride avec **plusieurs locataires**, votre sortie doit afficher un AuthServer du nom `EvoSts - {GUID}` pour chaque locataire hybride avec EXCH et l’état **Activé** doit être True pour tous ces objets AuthServer.

> [!IMPORTANT]
> Si vous exécutez Exchange 2010 dans votre environnement, le fournisseur d’authentification EvoSTS ne sera pas créé.

## <a name="enable-hma"></a>Activer HMA

Exécutez la commande suivante dans l’interpréteur de commandes Exchange Management Shell, localement, en \<GUID\> remplaçant dans la ligne de commande par la chaîne dans votre environnement :

```powershell
Set-AuthServer -Identity "EvoSTS - <GUID>" -IsDefaultAuthorizationEndpoint $true
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```

> [!NOTE]
> Dans les versions antérieures de l’Assistant Configuration hybride, EvoSts AuthServer s’appelait simplement EvoSTS sans GUID attaché. Il n’y a aucune action à effectuer. Modifiez simplement la ligne de commande ci-dessus pour refléter cela en supprimant la partie GUID de la commande :
>
> ```powershell
> Set-AuthServer -Identity EvoSTS -IsDefaultAuthorizationEndpoint $true
> ```

Si la version EXCH est Exchange 2016 (CU18 ou ultérieure) ou Exchange 2019 (CU7 ou version ultérieure) et qu’elle a été configurée avec HCW téléchargé après septembre 2020, exécutez la commande suivante dans Exchange Management Shell, localement :

```powershell
Set-AuthServer -Identity "EvoSTS - {GUID}" -DomainName "Tenant Domain" -IsDefaultAuthorizationEndpoint $true
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```

> [!NOTE]
> Si EXCH est hybride avec **plusieurs locataires**, plusieurs objets AuthServer sont présents dans EXCH avec des domaines correspondant à chaque locataire.  **L’indicateur IsDefaultAuthorizationEndpoint** doit être défini sur true (à l’aide de l’applet de commande **IsDefaultAuthorizationEndpoint**) pour l’un de ces objets AuthServer. Cet indicateur ne peut pas être défini sur true pour tous les objets Authserver et HMA est activé même si l’un des **indicateurs IsDefaultAuthorizationEndpoint** de l’objet AuthServer est défini sur true.
> 
> Pour le paramètre **DomainName** , utilisez la valeur de domaine du locataire, qui se présente généralement sous la forme `contoso.onmicrosoft.com`.

## <a name="verify"></a>Vérifier

Une fois que vous avez activé HMA, la prochaine connexion d’un client utilise le nouveau flux d’authentification. Notez que l’activation de HMA ne déclenche pas de nouvelle authentification pour n’importe quel client, et que la prise en charge des nouveaux paramètres par Exchange peut prendre un certain temps.

Vous devez également maintenir la touche CTRL enfoncée en même temps que vous cliquez avec le bouton droit sur l’icône du client Outlook (également dans la barre d’état Windows Notifications) et cliquez sur « État de la connexion ». Recherchez l’adresse SMTP du client par rapport à un type **d’authentification**`Bearer\*`, qui représente le jeton du porteur utilisé dans OAuth.

> [!NOTE]
> Vous avez besoin de configurer Skype Entreprise avec HMA ? Vous aurez besoin de deux articles : un qui [répertorie les topologies prises en charge](/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported) et un qui vous montre [comment effectuer la configuration](configure-skype-for-business-for-hybrid-modern-authentication.md).

## <a name="using-hybrid-modern-authentication-with-outlook-for-ios-and-android"></a>Utilisation de l’authentification moderne hybride avec Outlook pour iOS et Android

Si vous êtes un client local utilisant Exchange serveur sur TCP 443, autorisez le trafic réseau à partir des plages d’adresses IP suivantes :

```console
52.125.128.0/20
52.127.96.0/23
```

Ces plages d’adresses IP sont également [documentées dans des points de terminaison supplémentaires non inclus dans le service Web d’adresse IP et d’URL Office 365](/microsoft-365/enterprise/additional-office365-ip-addresses-and-urls).

## <a name="related-topics"></a>Voir aussi

[Configuration de l’authentification moderne requise pour la transition de Office 365 dédié/ITAR à vNext](/exchange/troubleshoot/modern-authentication/modern-authentication-configuration)
