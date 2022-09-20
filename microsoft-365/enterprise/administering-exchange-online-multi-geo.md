---
title: Administration des boîtes aux lettres Exchange Online dans un environnement multigéographique
ms.reviewer: adwood
ms.author: chrisda
author: chrisda
manager: serdars
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
f1.keywords:
- NOCSH
ms.custom: seo-marvel-mar2020
ms.localizationpriority: medium
description: Découvrez comment administrer Exchange Online paramètres multigéographiques dans votre environnement Microsoft 365 avec PowerShell.
ms.openlocfilehash: 9a8c9d82df0b5ded764b117583059c6ab0345d8a
ms.sourcegitcommit: 95ac076310ab9006ed92c69938f7ae771cd10826
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2022
ms.locfileid: "67851477"
---
# <a name="administering-exchange-online-mailboxes-in-a-multi-geo-environment"></a>Administration des boîtes aux lettres Exchange Online dans un environnement multigéographique

Exchange Online PowerShell est nécessaire pour afficher et configurer plusieurs propriétés géographiques dans votre environnement Microsoft 365. Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

Pour voir la propriété **PreferredDataLocation** sur les objets utilisateur, vous devez disposer du [module PowerShell Microsoft Azure Active Directory](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 ou version v1.x ultérieure. La valeur **PreferredDataLocation** des objets utilisateur synchronisés via AAD Connect dans AAD ne peut pas être modifiée directement via AAD PowerShell. Les objets utilisateur cloud uniquement peuvent être modifiés via AAD PowerShell. Pour vous connecter à Azure AD PowerShell, voir [Se connecter à PowerShell](connect-to-microsoft-365-powershell.md).

Dans Exchange Online environnements multigéographiques, vous n’avez pas besoin d’effectuer d’étapes manuelles pour ajouter des zones géographiques à votre locataire. Une fois que vous avez reçu le billet du Centre de messages indiquant que le multigéographique est prêt pour Exchange Online, toutes les zones géographiques disponibles sont prêtes et configurées pour que vous les utilisiez.

## <a name="connect-directly-to-a-geo-location-using-exchange-online-powershell"></a>Se connecter directement à un emplacement géographique à l’aide d’Exchange Online PowerShell

En règle générale, Exchange Online PowerShell se connecte à l’emplacement géographique central. Vous pouvez cependant aussi vous connecter directement à des emplacements satellites géographiques. En raison des améliorations apportées aux performances, nous vous recommandons de vous connecter directement à l’emplacement satellite géographique lorsque vous gérez uniquement des utilisateurs situés dans cet emplacement.

Les conditions requises pour l’installation et l’utilisation du module PowerShell Exchange Online sont décrites dans [Installer et gérer le module PowerShell Exchange Online](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exchange-online-powershell-module).

Pour connecter Exchange Online PowerShell à un emplacement géographique spécifique, le paramètre _ConnectionUri_ est différent des instructions de connexion régulières. Les autres commandes et valeurs sont identiques.

Plus précisément, vous devez ajouter la valeur à la `?email=<emailaddress>` fin de la valeur _ConnectionUri_ . `<emailaddress>` est l’adresse e-mail de **n’importe quelle** boîte aux lettres dans l’emplacement géographique cible. Vos autorisations sur cette boîte aux lettres ou la relation avec vos informations d’identification ne sont pas un facteur ; l’adresse e-mail indique simplement à Exchange Online PowerShell où se connecter.

Les clients Microsoft 365 ou Microsoft 365 GCC n’ont généralement pas besoin d’utiliser le paramètre _ConnectionUri_ pour se connecter à Exchange Online PowerShell. Toutefois, pour vous connecter à un emplacement géographique spécifique, vous devez utiliser le paramètre _ConnectionUri_ afin de pouvoir l’utiliser `?email=<emailaddress>` dans la valeur.

### <a name="connect-to-a-geo-location-in-exchange-online-powershell"></a>Se connecter à un emplacement géographique dans Exchange Online PowerShell

Les instructions de connexion suivantes fonctionnent pour les comptes qui sont ou ne sont pas configurés pour l’authentification multifacteur (MFA).

1. Dans une fenêtre PowerShell, chargez le module PowerShell Exchange Online en exécutant la commande suivante :

   ```powershell
   Import-Module ExchangeOnlineManagement
   ```

2. Dans l’exemple suivant, admin@contoso.onmicrosoft.com est le compte d’administrateur et l’emplacement géographique cible est l’emplacement de la boîte aux lettres olga@contoso.onmicrosoft.com réside.

   ```powershell
   Connect-ExchangeOnline -UserPrincipalName admin@contoso.onmicrosoft.com -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com
   ```

3. Entrez le mot de passe du admin@contoso.onmicrosoft.com dans l’invite qui s’affiche. Si le compte est configuré pour l’authentification multifacteur, vous devez également entrer le code de sécurité.

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
> Si le code d’emplacement géographique dans le nom de la base de données ne correspond pas à la valeur **MailboxRegion**, la boîte aux lettres est automatiquement placée dans une file d’attente de réadressage et déplacée vers l’emplacement géographique spécifié par la valeur **MailboxRegion** (Exchange Online recherche une incompatibilité entre ces valeurs de propriété).

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
> - Comme mentionné précédemment, vous ne pouvez pas utiliser cette procédure pour les objets utilisateur synchronisés à partir de Active Directory local. Vous devez modifier la valeur **PreferredDataLocation** dans Active Directory et la synchroniser à l’aide d’AAD Connect. Pour plus d’informations, voir [Synchronisation Azure Active Directory Connect : Configurer un emplacement de données par défaut pour les ressources Microsoft 365](/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).
>
> - Le temps nécessaire pour déplacer une boîte aux lettres vers un nouvel emplacement géographique dépend de plusieurs facteurs :
>
>   - la taille et le type de boîte aux lettres ;
>   - le nombre total de boîtes aux lettres déplacées ;
>   - la disponibilité des ressources nécessaires pour le déplacement.

### <a name="move-an-inactive-mailbox-to-a-specific-geo"></a>Déplacer une boîte aux lettres inactive vers une zone géographique spécifique

Vous ne pouvez pas déplacer les boîtes aux lettres inactives qui sont conservées à des fins de conformité (par exemple, les boîtes aux lettres en attente de litige) en modifiant leur valeur **PreferredDataLocation** . Pour déplacer une boîte aux lettres inactive vers une autre zone géographique, procédez comme suit :

1. Récupérez la boîte aux lettres inactive. Pour obtenir des instructions, consultez [Récupérer une boîte aux lettres inactive](../compliance/recover-an-inactive-mailbox.md).

2. Empêchez l’Assistant Dossier géré de traiter la boîte aux lettres récupérée en \<MailboxIdentity\> remplaçant par le nom, l’alias, le compte ou l’adresse e-mail de la boîte aux lettres et en exécutant la commande suivante dans [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) :

    ```powershell
    Set-Mailbox <MailboxIdentity> -ElcProcessingDisabled $true
    ```

3. Attribuez une licence **Exchange Online Plan 2** à la boîte aux lettres récupérée. Cette étape est nécessaire pour remettre la boîte aux lettres en attente de litige. Pour obtenir des instructions, consultez [Affecter des licences aux utilisateurs](../admin/manage/assign-licenses-to-users.md).

4. Configurez la valeur **PreferredDataLocation** sur la boîte aux lettres comme décrit dans la section précédente.

5. Une fois que vous avez confirmé que la boîte aux lettres a été déplacée vers le nouvel emplacement géographique, replacez la boîte aux lettres récupérée en attente du litige. Pour obtenir des instructions, consultez [Placer une boîte aux lettres en attente de litige](../compliance/create-a-litigation-hold.md#place-a-mailbox-on-litigation-hold).

6. Après avoir vérifié que la conservation du litige est en place, autorisez l’Assistant Dossier géré à traiter à nouveau la boîte aux lettres en \<MailboxIdentity\> remplaçant par le nom, l’alias, le compte ou l’adresse e-mail de la boîte aux lettres et en exécutant la commande suivante dans [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) :

    ```powershell
    Set-Mailbox <MailboxIdentity> -ElcProcessingDisabled $false
    ```

7. Réactivez la boîte aux lettres en supprimant le compte d’utilisateur associé à la boîte aux lettres. Pour obtenir des instructions, consultez [Supprimer un utilisateur de votre organisation](../admin/add-users/delete-a-user.md). Cette étape libère également la licence Exchange Online Plan 2 pour d’autres utilisations.

**Remarque** : lorsque vous déplacez une boîte aux lettres inactive vers un autre emplacement géographique, vous pouvez affecter les résultats de recherche de contenu ou la possibilité de rechercher la boîte aux lettres à partir de l’emplacement géographique précédent. Pour plus d’informations, consultez [Recherche et exportation de contenu dans des environnements multigéographiques](../compliance/set-up-compliance-boundaries.md#searching-and-exporting-content-in-multi-geo-environments).

## <a name="create-new-cloud-mailboxes-in-a-specific-geo-location"></a>Créer des boîtes aux lettres cloud dans un emplacement géographique spécifique

Pour créer une boîte aux lettres dans un emplacement géographique spécifique, vous devez effectuez l’une des opérations suivantes :

- Configurez la valeur **PreferredDataLocation** comme décrit dans la précédente section [Déplacer une boîte aux lettres cloud uniquement existante vers une section de géolocalisation spécifique](#move-an-existing-cloud-only-mailbox-to-a-specific-geo-location) *avant* de créer la boîte aux lettres dans Exchange Online. Par exemple, configurez la valeur **PreferredDataLocation** sur un utilisateur avant d’attribuer une licence.

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

Vous pouvez vous servir des outils et processus d’intégration standard pour migrer une boîte aux lettres d’une organisation Exchange locale vers Exchange Online. Ces outils sont le [Tableau de bord de migration dans le Centre d’administration Exchange](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331) et la cmdlet [New-MigrationBatch](/powershell/module/exchange/new-migrationbatch) dans Exchange Online PowerShell.

La première étape consiste à vérifier qu’un objet utilisateur existe pour chaque boîte aux lettres à intégrer, et que la valeur **PreferredDataLocation** correcte est configurée dans Azure AD. Les outils d’intégration respectent la valeur **PreferredDataLocation** et migrent les boîtes aux lettres directement vers la zone géographique spécifiée.

Ou bien, pour intégrer les boîtes aux lettres directement dans un emplacement géographique à l’aide de la cmdlet [New-MoveRequest](/powershell/module/exchange/new-moverequest) dans Exchange Online PowerShell, vous pouvez également procéder comme suit.

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

> [!NOTE]
> La fonctionnalité de création de rapports multigéographiques est actuellement en préversion, n’est pas disponible dans toutes les organisations et est susceptible de changer.

Les **rapports d’utilisation multigéographique** dans le Centre d’administration Microsoft 365 affichent le nombre d’utilisateurs par emplacement géographique. Le rapport présente la répartition des utilisateurs pour le mois en cours et les données historiques des 6 derniers mois.

## <a name="see-also"></a>Voir aussi

[Gestion de Microsoft 365 à l’aide de PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
