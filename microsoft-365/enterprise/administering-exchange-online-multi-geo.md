---
title: Administration des boîtes aux lettres Exchange Online dans un environnement multigéographique
ms.reviewer: adwood
ms.author: chrisda
author: chrisda
manager: serdars
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: seo-marvel-mar2020
localization_priority: normal
description: Découvrez comment administrer les paramètres multi-géo Exchange Online dans votre environnement Microsoft 365 avec PowerShell.
ms.openlocfilehash: 996566d67aa8ba7ebca1406cd5d6265458637fee
ms.sourcegitcommit: 27daadad9ca0f02a833ff3cff8a574551b9581da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "47546245"
---
# <a name="administering-exchange-online-mailboxes-in-a-multi-geo-environment"></a>Administration des boîtes aux lettres Exchange Online dans un environnement multigéographique

Exchange Online PowerShell est requis pour afficher et configurer les propriétés multi-géo dans votre environnement Microsoft 365. Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell).

Pour voir la propriété **PreferredDataLocation** sur les objets utilisateur, vous devez disposer du [module PowerShell Microsoft Azure Active Directory](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 ou version v1.x ultérieure. La valeur **PreferredDataLocation** des objets utilisateur synchronisés via AAD Connect dans AAD ne peut pas être modifiée directement via AAD PowerShell. Les objets utilisateur cloud uniquement peuvent être modifiés via AAD PowerShell. Pour vous connecter à Azure AD PowerShell, voir [Se connecter à PowerShell](connect-to-microsoft-365-powershell.md).

## <a name="connect-directly-to-a-geo-location-using-exchange-online-powershell"></a>Se connecter directement à un emplacement géographique à l’aide d’Exchange Online PowerShell

En règle générale, Exchange Online PowerShell se connecte à l’emplacement géographique central. Vous pouvez cependant aussi vous connecter directement à des emplacements satellites géographiques. En raison des améliorations apportées aux performances, nous vous recommandons de vous connecter directement à l’emplacement satellite géographique lorsque vous gérez uniquement des utilisateurs situés dans cet emplacement.

Les conditions requises pour l’installation et l’utilisation du module EXO v2 sont décrites dans [Installer et gérer le module EXO v2](https://docs.microsoft.com/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exo-v2-module).

Pour connecter Exchange Online PowerShell à un emplacement géographique spécifique, le paramètre *ConnectionUri* est différent des instructions de connexion normales. Les autres commandes et valeurs sont identiques.

Plus précisément, vous devez ajouter la `?email=<emailaddress>` valeur à la fin de la valeur _ConnectionUri_ . `<emailaddress>` est l’adresse de messagerie de **n’importe quelle** boîte aux lettres dans l’emplacement géographique cible. Vos autorisations sur cette boîte aux lettres ou la relation avec vos informations d’identification n’est pas un facteur ; l’adresse de messagerie indique simplement à Exchange Online PowerShell où se connecter.

Les clients Microsoft 365 ou Microsoft 365 GCC n’ont généralement pas besoin d’utiliser le paramètre _ConnectionUri_ pour se connecter à Exchange Online PowerShell. Toutefois, pour vous connecter à un emplacement géographique spécifique, vous devez utiliser le paramètre _ConnectionUri_ afin `?email=<emailaddress>` de pouvoir l’utiliser dans la valeur.

### <a name="connect-to-a-geo-location-in-exchange-online-powershell-using-multi-factor-authentication-mfa"></a>Se connecter à un emplacement géographique dans Exchange Online PowerShell à l’aide de Multi-Factor Authentication (MFA)

1. Dans une fenêtre Windows PowerShell, chargez le module EXO V2 en exécutant la commande suivante :

   ```powershell
   Import-Module ExchangeOnlineManagement
   ```

2. Dans l’exemple suivant, admin@contoso.onmicrosoft.com est le compte d’administrateur et l’emplacement géographique cible est l’emplacement où réside la boîte aux lettres olga@contoso.onmicrosoft.com.

  ```powershell
  Connect-ExchangeOnline -UserPrincipalName admin@contoso.onmicrosoft.com -ShowProgress $true -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com
  ```

### <a name="connect-to-a-geo-location-in-exchange-online-powershell-without-using-mfa"></a>Se connecter à un emplacement géographique dans Exchange Online PowerShell sans utiliser l’authentification multifacteur

1. Dans une fenêtre Windows PowerShell, chargez le module EXO V2 en exécutant la commande suivante :

   ```powershell
   Import-Module ExchangeOnlineManagement
   ```

2. Exécutez la commande suivante :

   ```powershell
   $UserCredential = Get-Credential
   ```

   Dans la boîte de dialogue **Demande d’informations d’identification Windows PowerShell** qui s’affiche, saisissez vos nom d’utilisateur et mot de passe, puis cliquez sur **OK**.

3. Dans l’exemple suivant, l’emplacement géographique cible est l’emplacement où réside la boîte aux lettres olga@contoso.onmicrosoft.com.

   ```powershell
   Connect-ExchangeOnline -Credential $UserCredential -ShowProgress $true -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com
   ```

## <a name="view-the-available-geo-locations-that-are-configured-in-your-exchange-online-organization"></a>Affichage des emplacements géographiques disponibles configurés dans votre organisation Exchange Online

Pour afficher la liste des emplacements géographiques configurés dans Microsoft 365 Multi-Geo, exécutez la commande suivante dans Exchange Online PowerShell :

```powershell
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table
```

## <a name="view-the-central-geo-location-for-your-exchange-online-organization"></a>Afficher l’emplacement géographique central de votre organisation Exchange Online

Pour afficher l’emplacement géographique central de votre locataire, exécutez la commande suivante dans Exchange Online PowerShell :

```powershell
Get-OrganizationConfig | Select DefaultMailboxRegion
```

## <a name="find-the-geo-location-of-a-mailbox"></a>Recherche de l’emplacement géographique d’une boîte aux lettres

La cmdlet **Get-Mailbox** dans Exchange Online PowerShell affiche les propriétés multigéographiques associées suivantes sur les boîtes aux lettres :

- **Database** : les 3 premières lettres du nom de base de données correspondent au géocode indiquant où la boîte aux lettres se trouve actuellement. Pour les boîtes aux lettres d’archivage en ligne, il convient d’utiliser la propriété **ArchiveDatabase**.

- **MailboxRegion** : spécifie le code de géolocalisation défini par l’administrateur (synchronisé à partir de **PreferredDataLocation** dans Azure AD).

- **MailboxRegionLastUpdateTime** : indique quand la propriété MailboxRegion a été mise à jour (automatiquement ou manuellement) pour la dernière fois.

Pour afficher ces propriétés pour une boîte aux lettres, utilisez la syntaxe suivante :

```powershell
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

Par exemple, pour afficher les informations d’emplacement géographique pour la boîte aux lettres chris@contoso.onmicrosoft.com, exécutez la commande suivante :

```powershell
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

Le résultat de la commande ressemble à ceci :

```powershell
Database                    : EURPR03DG077-db007
MailboxRegion               : EUR
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM
```

> [!NOTE]
> Si le code d’emplacement géographique dans le nom de la base de données ne correspond pas à la valeur **MailboxRegion** , la boîte aux lettres est automatiquement placée dans une file d’attente de relocalisation et déplacée vers l’emplacement géographique spécifié par la valeur **MailboxRegion** (Exchange Online recherche une incompatibilité entre ces valeurs de propriétés).

## <a name="move-an-existing-cloud-only-mailbox-to-a-specific-geo-location"></a>Déplacer une boîte aux lettres cloud uniquement vers un emplacement géographique spécifique

Un utilisateur cloud uniquement est un utilisateur qui n’est pas synchronisé avec le locataire via AAD Connect. Cet utilisateur a été créé directement dans Azure AD. Pour afficher ou spécifier la zone géographique dans laquelle sera stockée la boîte aux lettres d’un utilisateur cloud uniquement, utilisez les cmdlets **Get-MsolUser** et **Set-MsolUser** dans le module Azure AD pour Windows PowerShell.

Pour voir la valeur **PreferredDataLocation** pour un utilisateur, utilisez la syntaxe suivante dans Azure AD PowerShell :

```powershell
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

Par exemple, pour voir la valeur **PreferredDataLocation** pour l’utilisateur michelle@contoso.onmicrosoft.com, exécutez la commande suivante :

```powershell
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

Pour modifier la valeur **PreferredDataLocation** d’un objet utilisateur cloud uniquement, utilisez la syntaxe suivante dans Azure AD PowerShell :

```powershell
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoLocationCode>
```

Par exemple, pour définir la valeur **PreferredDataLocation** sur la zone géographique Union européenne (EUR) pour l’utilisateur michelle@contoso.onmicrosoft.com, exécutez la commande suivante :

```powershell
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

> [!NOTE]
>
> - Comme indiqué précédemment, vous ne pouvez pas utiliser cette procédure pour les objets utilisateur synchronisés à partir d’Active Directory local. Vous devez modifier la valeur **PreferredDataLocation** dans Active Directory et la synchroniser à l’aide d’AAD Connect. Pour plus d’informations, voir [Synchronisation Azure Active Directory Connect : Configurer un emplacement de données par défaut pour les ressources Microsoft 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).
>
> - Le temps nécessaire pour déplacer une boîte aux lettres vers un nouvel emplacement géographique dépend de plusieurs facteurs :
>
>   - la taille et le type de boîte aux lettres ;
>   - le nombre total de boîtes aux lettres déplacées ;
>   - la disponibilité des ressources nécessaires pour le déplacement.

### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a>Déplacer des boîtes aux lettres désactivées pour cause de Conservation pour litige

Il est possible de déplacer des boîtes aux lettres désactivées pour cause de Conservation pour litige à des fins de découverte électronique (eDiscovery) en modifiant leur valeur **PreferredDataLocation**. Pour déplacer une boîte aux lettres désactivée pour cause de Conservation pour litige :

1. Attribuez temporairement une licence à la boîte aux lettres.

2. Modifiez la valeur **PreferredDataLocation**.

3. Une fois la boîte aux lettres déplacée vers l’emplacement géographique choisi, supprimez sa licence afin de la remettre à l’état désactivé.

## <a name="create-new-cloud-mailboxes-in-a-specific-geo-location"></a>Créer des boîtes aux lettres cloud dans un emplacement géographique spécifique

Pour créer une boîte aux lettres dans un emplacement géographique spécifique, vous devez effectuez l’une des opérations suivantes :

- Configurer la valeur **PreferredDataLocation** de la manière décrite dans la section précédente *avant* de créer la boîte aux lettres dans Exchange Online ; par exemple, définir la valeur **PreferredDataLocation** sur un utilisateur avant l’attribution d’une licence.

- Attribuer une licence lors de la définition de la valeur **PreferredDataLocation**.

Pour créer un utilisateur titulaire d’une licence d’utilisation cloud uniquement (non synchronisé avec AAD Connect) dans une zone géographique spécifique, utilisez la syntaxe suivante dans Azure AD PowerShell :

```powershell
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoLocationCode>
```

Cet exemple montre comment créer un compte d’utilisateur pour Elizabeth Brunner avec les valeurs suivantes :

- Nom d’utilisateur principal : ebrunner@contoso.onmicrosoft.com
- Prénom : Elizabeth
- Nom : Brunner
- Nom d’affichage : Elizabeth Brunner
- Mot de passe : généré de façon aléatoire et affiché dans les résultats de la commande (étant donné que nous n’utilisons pas le paramètre *Password*)
- Licence : `contoso:ENTERPRISEPREMIUM` (E5)
- Emplacement : Australie (AUS)

```powershell
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

Pour plus d’informations sur la création de comptes d’utilisateur et la recherche de valeurs LicenseAssignment dans Azure AD PowerShell, voir [Création de comptes d’utilisateurs avec PowerShell](create-user-accounts-with-microsoft-365-powershell.md) et [Afficher les licences et les services avec PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md).

> [!NOTE]
> Sii vous utilisez Exchange Online PowerShell pour activer une boîte aux lettres et avez besoin que la boîte aux lettres soit créée directement dans la zone géographique spécifiée dans **PreferredDataLocation**, vous devez utiliser une cmdlet Exchange Online telle que **Enable-Mailbox** ou **New-Mailbox** directement sur le service cloud. Si vous utilisez la cmdlet **Enable-RemoteMailbox** dans le powerShell Exchange sur site, la boîte aux lettres est créée dans l’emplacement géographique central.

## <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo-location"></a>Intégrer des boîtes aux lettres locales existant dans un emplacement géographique spécifique

Vous pouvez vous servir des outils et processus d’intégration standard pour migrer une boîte aux lettres d’une organisation Exchange locale vers Exchange Online. Ces outils sont le [Tableau de bord de migration dans le Centre d’administration Exchange](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331) et la cmdlet [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/new-migrationbatch) dans Exchange Online PowerShell.

La première étape consiste à vérifier qu’un objet utilisateur existe pour chaque boîte aux lettres à intégrer, et que la valeur **PreferredDataLocation** correcte est configurée dans Azure AD. Les outils d’intégration respectent la valeur **PreferredDataLocation** et migrent les boîtes aux lettres directement vers la zone géographique spécifiée.

Ou bien, pour intégrer les boîtes aux lettres directement dans un emplacement géographique à l’aide de la cmdlet [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/new-moverequest) dans Exchange Online PowerShell, vous pouvez également procéder comme suit.

1. Vérifiez que l’objet utilisateur existe pour chaque boîte aux lettres intégrée et que la valeur **PreferredDataLocation** est correctement définie dans Azure AD. La valeur **PreferredDataLocation** est synchronisée avec l’attribut **MailboxRegion** de l’objet utilisateur de courrier correspondant dans Exchange Online.

2. Connectez-vous directement à la zone géographique satellite spécifique en suivant les instructions de connexion figurant plus haut dans cette rubrique.

3. Dans Exchange Online PowerShell, stockez les informations d’identification d’administrateur locales utilisées pour effectuer une migration de boîte aux lettres dans une variable en exécutant la commande suivante :

   ```powershell
   $RC = Get-Credential
   ```

4. Dans Exchange Online PowerShell, créez une cmdlet **New-MoveRequest** similaire à l’exemple suivant :

   ```powershell
   New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
   ```

5. Répétez l’étape 4 pour chaque boîte aux lettres à migrer d’Exchange sur site vers l’emplacement géographique satellite auquel vous êtes actuellement connecté.

6. Si vous devez migrer des boîtes aux lettres supplémentaires vers un autre emplacement géographique satellite, répétez les étapes 2 à 4 pour chaque emplacement spécifique.

## <a name="multi-geo-reporting"></a>Génération de rapports multigéographiques

Les **rapports d’utilisation multigéographique** dans le Centre d’administration Microsoft 365 affichent le nombre d’utilisateurs par emplacement géographique. Le rapport présente la répartition des utilisateurs pour le mois en cours et les données historiques des 6 derniers mois.

## <a name="see-also"></a>Voir aussi

[Gestion de Microsoft 365 et d’Exchange Online avec Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6)
