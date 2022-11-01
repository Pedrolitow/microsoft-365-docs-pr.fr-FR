---
title: Data Residency pour Exchange Online
description: En savoir plus sur les Data Residency pour Exchange Online
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.service: microsoft-365-enterprise
ms.topic: article
f1.keywords:
- NOCSH
ms.date: ''
ms.reviewer: dmwmsft
ms.custom:
- it-pro
ms.collection:
- M365-subscription-management
ms.openlocfilehash: 17799d6d69daa50d6d9cb70ec3632314d5c64d3a
ms.sourcegitcommit: 0c72639cc3dc74667a6b14343d303f318e70d457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68805572"
---
# <a name="data-residency-for-exchange-online"></a>Data Residency pour Exchange Online

## <a name="data-residency-commitments-available"></a>Data Residency engagements disponibles

### <a name="product-terms"></a>Conditions du produit

Conditions requises :

Le locataire a un pays d’inscription inclus dans la zone géographique de la région locale, l’Union européenne ou le États-Unis.

_Pour connaître la langue actuelle, reportez-vous à la <a href="https://www.microsoft.com/licensing/terms/product/PrivacyandSecurityTerms/all" target="_blank">**page web**</a> Conditions du produit de confidentialité et de sécurité et consultez la section intitulée « Emplacement des données client au repos pour les principaux services en ligne »._

**Engagement:**

>[!NOTE]
>Si le client approvisionne son locataire en Australie, Au Brésil, au Canada, dans l’Union européenne, en France, en Allemagne, en Inde, au Japon, en Norvège, au Qatar, en Afrique du Sud, en Corée du Sud, en Suède, en Suisse, aux Émirats arabes unis, au Royaume-Uni ou États-Unis, Microsoft stocke les données client suivantes au repos uniquement dans cette zone géographique : Exchange Online contenu de boîte aux lettres (corps du courrier électronique, entrées de calendrier et contenu des pièces jointes de courrier électronique)

### <a name="advanced-data-residency-add-on"></a>Module complémentaire Data Residency avancé

Conditions requises :

1. Le client a un pays d’inscription inclus dans _Région locale Geography_ ou _Expanded Local Region Geography_.
1. Le locataire dispose d’un abonnement advanced Data Residency valide pour tous les utilisateurs du locataire
1. Les données client de l’abonnement Exchange Online sont approvisionnées dans Géographie locale ou Zone géographique locale étendue

**Engagement:**

Reportez-vous à la [page d’engagement ADR](m365-dr-commitments.md#exchange-online) pour comprendre les engagements spécifiques fournis par le biais des Conditions du produit. Voici quelques exemples de données validées : tous les types de boîtes aux lettres, y compris les boîtes aux lettres utilisateur, les boîtes aux lettres de ressources et les boîtes aux lettres d’archivage.

### <a name="multi-geo-add-on"></a>Module complémentaire multigéographique

Conditions requises :

1. Les locataires disposent d’un abonnement multigéographique valide qui couvre tous les utilisateurs affectés à une _zone géographique satellite_.
1. Le client doit avoir un Accord Entreprise actif.
1. Le nombre total d’unités multigéographiques achetées doit être supérieur à 5 % du nombre total de sièges éligibles dans le locataire.

**Engagement:**

Les clients peuvent affecter une zone géographique satellite prise en charge par multigéographique à un type de boîte aux lettres pris en charge. Pour plus d’informations, consultez la [section Disponibilité microsoft 365 multigéographique](microsoft-365-multi-geo.md#microsoft-365-multi-geo-availability) de la page Microsoft 365 Multi-Geo. Les données au repos pour Office 365 Services pour la boîte aux lettres, telles que définies par les termes du produit, doivent être stockées dans la zone géographique satellite affectée. Les types de boîtes aux lettres pris en charge incluent Exchange Online boîtes aux lettres principales et d’archivage utilisateur, les boîtes aux lettres de ressources, les boîtes aux lettres de groupe Microsoft 365 et les boîtes aux lettres partagées.

## <a name="multi-geo-capabilities-in-exchange-online"></a>Fonctionnalités multigéographiques d’Exchange Online

Les clients peuvent attribuer une _zone géographique satellite_ prise en charge par multigéographique à un utilisateur. Pour plus d’informations, consultez la [section Disponibilité microsoft 365 multigéographique](microsoft-365-multi-geo.md#microsoft-365-multi-geo-availability) de la page Microsoft 365 Multi-Geo. Les données au repos de l’utilisateur pour Office 365 Services, telles que définies par les termes du produit, doivent être stockées dans la _zone géographique satellite_ affectée. Cela inclut tous les types de boîtes aux lettres Exchange Online, y compris les boîtes aux lettres utilisateur, les boîtes aux lettres de ressources, les boîtes aux lettres de groupe Microsoft 365, les boîtes aux lettres partagées et les boîtes aux lettres d’archivage.

Vous pouvez placer des boîtes aux lettres dans des emplacements _géographiques satellites_ en :

1. Création d’une boîte aux lettres Exchange Online directement dans un emplacement _géographique satellite_.
1. Déplacement d’une boîte aux lettres Exchange Online existante vers un emplacement _géographique satellite_ en modifiant l’emplacement de données préféré de l’utilisateur.
1. Intégration d’une boîte aux lettres à partir d’une organisation Exchange locale directement dans un emplacement _géographique satellite_ .

### <a name="mailbox-placement-and-moves"></a>Positionnement et déplacement de boîte aux lettres

Une fois que Microsoft a effectué les étapes de configuration multigéographique requises, Exchange Online respectera l’attribut PreferredDataLocation sur les objets utilisateur dans Azure AD.
Exchange Online synchronise la propriété PreferredDataLocation d’AAD dans la propriété MailboxRegion du service d’annuaire Exchange Online. La valeur de MailboxRegion détermine la _zone géographique de la région_ macro ou la zone _géographique de la région locale_ où les boîtes aux lettres utilisateur et toutes les boîtes aux lettres d’archivage associées seront placées. Il n’est pas possible de configurer la boîte aux lettres principale et les boîtes aux lettres d’archivage d’un utilisateur pour qu’elles résident dans des emplacements _géographiques_ différents. Une seule _macro Région Géographique_ ou _Région locale Peut_ être configurée par objet utilisateur.

- Lorsque PreferredDataLocation est configuré sur un utilisateur disposant d’une boîte aux lettres existante, la boîte aux lettres est placée dans une file d’attente de réadressage et automatiquement déplacée vers la _zone géographique_ de la macro ou la _zone géographique de la région locale_ spécifiée.
- Lorsque PreferredDataLocation est configuré sur un utilisateur sans boîte aux lettres existante, lorsque vous approvisionnez la boîte aux lettres, elle est provisionnée dans la _macro Région Géographique_ ou _Zone géographique de la région locale_ spécifiée.
- Lorsque PreferredDataLocation n’est pas spécifié sur un utilisateur, lorsque vous approvisionnez la boîte aux lettres, elle est provisionnée dans la _zone géographique approvisionnée principale_.
- Si le code PreferredDataLocation est incorrect (par exemple, une faute de frappe de NAN au lieu de NAM), la boîte aux lettres est configurée dans la _zone géographique approvisionnée principale_.

>[!NOTE]
>Les fonctionnalités multigéographiques et les réunions Skype Entreprise en ligne hébergées régionalement utilisent la propriété PreferredDataLocation sur les objets utilisateur pour localiser les services. Si vous configurez des valeurs PreferredDataLocation sur des objets utilisateur pour les réunions hébergées dans une région, la boîte aux lettres de ces utilisateurs est automatiquement déplacée vers la _macro Région Géographique_ ou _Zone géographique de la région locale_ spécifiée après l’activation de multigéographique sur le locataire Microsoft 365.

### <a name="feature-limitations-for-multi-geo-in-exchange-online"></a>Limitations des fonctionnalités multigéographiques dans Exchange Online

- Les fonctionnalités de sécurité et de conformité (par exemple, audit et eDiscovery) qui sont disponibles dans le Centre d’administration Exchange (EAC) ne sont pas disponibles dans les organisations multigéographiques. Au lieu de cela, vous devez utiliser le Centre de conformité microsoft 365 Sécurité & pour configurer les fonctionnalités de sécurité et de conformité.
- Outlook pour Mac utilisateurs peuvent subir une perte temporaire d’accès à leur dossier d’archivage en ligne pendant que vous déplacez leur boîte aux lettres vers un nouvel emplacement _Geography_. Cette condition se produit lorsque les boîtes aux lettres primaire et d’archivage de l’utilisateur se trouvent dans des emplacements _Geography_ différents, car les déplacements de boîtes aux lettres intergéographiques peuvent se terminer à des moments différents.
- Les utilisateurs ne peuvent pas partager les dossiers de boîtes aux lettres entre des emplacements _Geography_ dans Outlook sur le web (anciennement Outlook Web App ou OWA). Par exemple, un utilisateur résidant dans l’Union européenne ne peut pas utiliser Outlook sur le web pour ouvrir un dossier partagé figurant dans une boîte aux lettres située aux États-Unis. Toutefois, les utilisateurs d’Outlook sur le web peuvent ouvrir d’autres boîtes aux lettres dans différents emplacements _Geography_ à l’aide d’une fenêtre de navigateur distincte, comme décrit dans Ouvrir la boîte aux lettres d’une autre personne dans une fenêtre de navigateur distincte dans Outlook Web App.

>[!NOTE]
>Le partage de dossiers de boîtes aux lettres intergéographiques est pris en charge dans Outlook sur Windows.

- Les dossiers publics sont pris en charge dans les organisations multigéographiques. Toutefois, les dossiers publics doivent rester à l’emplacement _Géographique approvisionné principal_ . Vous ne pouvez pas déplacer des dossiers publics vers des emplacements géographiques satellites.
- Dans un environnement multigéographique, l’audit de boîte aux lettres intergéographique n’est pas pris en charge. Par exemple, si un utilisateur se voit attribuer des autorisations pour accéder à une boîte aux lettres partagée dans un autre emplacement _Geography_ , les actions de boîte aux lettres effectuées par cet utilisateur ne sont pas enregistrées dans le journal d’audit de la boîte aux lettres partagée. Les événements d’audit de l’administrateur Exchange sont également disponibles uniquement pour l’emplacement par défaut. Pour plus d’informations, voir Gérer l’audit de boîte aux lettres.

### <a name="administering-exchange-multi-geo"></a>Administration d'Exchange Multi-Géo

#### <a name="administering-exchange-online-mailboxes-in-a-multi-geo-environment"></a>Administration de boîtes aux lettres Exchange Online dans un environnement multigéographique

Exchange Online PowerShell est nécessaire pour afficher et configurer les propriétés multigéographiques dans votre environnement Microsoft 365. Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

Pour voir la propriété **PreferredDataLocation** sur les objets utilisateur, vous devez disposer du [module PowerShell Microsoft Azure Active Directory](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 ou version v1.x ultérieure. La valeur **PreferredDataLocation** des objets utilisateur synchronisés via AAD Connect dans AAD ne peut pas être modifiée directement via AAD PowerShell. Les objets utilisateur cloud uniquement peuvent être modifiés via AAD PowerShell. Pour vous connecter à Azure AD PowerShell, voir [Se connecter à PowerShell](connect-to-microsoft-365-powershell.md).

Dans les environnements Exchange Online multigéographique, vous n’avez pas besoin d’effectuer d’étapes manuelles pour ajouter des zones géographiques à votre locataire. Une fois que vous avez reçu la publication du Centre de messages indiquant que la zone multigéographique est prête pour Exchange Online, toutes les zones géographiques disponibles sont prêtes et configurées pour que vous les utilisiez.

#### <a name="connect-directly-to-a-geo-location-using-exchange-online-powershell"></a>Se connecter directement à un emplacement géographique à l’aide d’Exchange Online PowerShell

En règle générale, Exchange Online PowerShell se connecte à l’emplacement _géographique approvisionné principal_. Toutefois, vous pouvez également vous connecter directement aux emplacements _géographiques satellites_ . En raison de l’amélioration des performances, nous vous recommandons de vous connecter directement à l’emplacement _Géographique satellite_ lorsque vous gérez uniquement les utilisateurs dans cet emplacement.

Les conditions requises pour l’installation et l’utilisation du module PowerShell Exchange Online sont décrites dans **[Installer et gérer le module PowerShell Exchange Online](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exchange-online-powershell-module)**.

Pour connecter Exchange Online PowerShell à un emplacement _Geography_ spécifique, le paramètre ConnectionUri est différent des instructions de connexion standard. Les autres commandes et valeurs sont identiques.

Plus précisément, vous devez ajouter la valeur ?email=\<emailaddress\> à la fin de la valeur ConnectionUri. \<emailaddress\> est l’adresse e-mail de **toute** boîte aux lettres dans l’emplacement _Géographique_ cible. Vos autorisations sur cette boîte aux lettres ou la relation à vos informations d’identification ne sont pas un facteur ; l’adresse e-mail indique simplement Exchange Online PowerShell où se connecter.
  
Les clients Microsoft 365 ou Microsoft 365 GCC n’ont généralement pas besoin d’utiliser le paramètre _ConnectionUri_ pour se connecter à Exchange Online PowerShell. Toutefois, pour vous connecter à un emplacement _Geography_ spécifique, vous devez utiliser le paramètre ConnectionUri afin de pouvoir utiliser ?email=\<emailaddress\> dans la valeur.
  
#### <a name="connect-to-a-_geography_-location-in-exchange-online-powershell"></a>Se connecter à un emplacement _geography_ dans Exchange Online PowerShell

Les instructions de connexion suivantes fonctionnent pour les comptes qui sont ou ne sont pas configurés pour l’authentification multifacteur (MFA).

1. Dans une fenêtre Windows PowerShell, chargez le module EXO V2 en exécutant la commande suivante :

  ```powershell
   Import-Module ExchangeOnlineManagement
   ```
  
1. Dans l’exemple suivant, admin@contoso.onmicrosoft.com est le compte d’administrateur et l’emplacement géographique cible est l’emplacement où réside la boîte aux lettres olga@contoso.onmicrosoft.com.
  
  ```powershell
   Connect-ExchangeOnline -UserPrincipalName admin@contoso.onmicrosoft.com -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com
   ```
  
1. Entrez le mot de passe du admin@contoso.onmicrosoft.com dans l’invite qui s’affiche. Si le compte est configuré pour l’authentification multifacteur, vous devez également entrer le code de sécurité.
  
#### <a name="view-the-available-_geography_-locations-that-are-configured-in-your-exchange-online-organization"></a>Afficher les emplacements _Géographiques_ disponibles qui sont configurés dans votre organisation Exchange Online

Pour afficher la liste des emplacements _Geography_ configurés dans Microsoft 365 Multi-Geo, exécutez la commande suivante dans Exchange Online PowerShell :

  ```powershell
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table
```
  
#### <a name="view-the-_primary-provisioned-geography_-location-for-your-exchange-online-organization"></a>Afficher l’emplacement _géographique principal approvisionné_ de votre organisation Exchange Online

Pour afficher l’emplacement _géographique approvisionné principal_ de votre locataire, exécutez la commande suivante dans Exchange Online PowerShell :

 ```powershell
Get-OrganizationConfig | Select DefaultMailboxRegion
```

#### <a name="find-the-_geography_-location-of-a-mailbox"></a>Rechercher l’emplacement _géographique_ d’une boîte aux lettres

La cmdlet **Get-Mailbox** dans Exchange Online PowerShell affiche les propriétés multigéographiques associées suivantes sur les boîtes aux lettres :

- **Base de données** : les 3 premières lettres du nom de la base de données correspondent au code _Geography_ , qui vous indique l’emplacement actuel de la boîte aux lettres. Pour les boîtes aux lettres d’archivage en ligne, il convient d’utiliser la propriété **ArchiveDatabase**.
- **MailboxRegion** : spécifie le code d’emplacement _Geography_ qui a été défini par l’administrateur (synchronisé à partir de PreferredDataLocation dans Azure AD).
- **MailboxRegionLastUpdateTime** : indique quand la propriété MailboxRegion a été mise à jour (automatiquement ou manuellement) pour la dernière fois.

Pour afficher ces propriétés pour une boîte aux lettres, utilisez la syntaxe suivante :

```powershell
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

  Par exemple, pour afficher les informations d’emplacement _geography_ pour la boîte aux lettres chris@contoso.onmicrosoft.com, exécutez la commande suivante :

  ```powershell
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

  Le résultat de la commande ressemble à ceci :

  ```powershell
Database                    : EURPR03DG077-db007
MailboxRegion               : EUR
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM
```
  
 > [!NOTE]
 >Si le code d’emplacement _Geography_ dans le nom de la base de données ne correspond pas à la valeur **MailboxRegion**, la boîte aux lettres est automatiquement placée dans une file d’attente de réadressage et déplacée vers l’emplacement _Geography_ spécifié par la valeur **MailboxRegion** (Exchange Online recherche une incompatibilité entre ces valeurs de propriété).

#### <a name="move-an-existing-cloud-only-mailbox-to-a-specific-geo-location"></a>Déplacer une boîte aux lettres cloud uniquement vers un emplacement géographique spécifique

Un utilisateur cloud uniquement est un utilisateur qui n’est pas synchronisé avec le locataire via AAD Connect. Cet utilisateur a été créé directement dans Azure AD. Utilisez les applets **de commande Get-MsolUser** et **Set-MsolUser** dans le module Azure AD pour Windows PowerShell pour afficher ou spécifier l’emplacement _Geography_ où sera stockée la boîte aux lettres d’un utilisateur cloud uniquement.

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

#### <a name="move-an-inactive-mailbox-to-a-specific-_geography_"></a>Déplacer une boîte aux lettres inactive vers une _zone géographique_ spécifique
  
Vous ne pouvez pas déplacer les boîtes aux lettres inactives qui sont conservées à des fins de conformité (par exemple, les boîtes aux lettres en conservation pour litige) en modifiant leur valeur **PreferredDataLocation** . Pour déplacer une boîte aux lettres inactive vers une autre _zone Geography_, procédez comme suit :

1. Récupérez la boîte aux lettres inactive. Pour obtenir des instructions, consultez [Récupérer une boîte aux lettres inactive](/microsoft-365/compliance/recover-an-inactive-mailbox).

1. Empêchez l’Assistant Dossier managé de traiter la boîte aux lettres récupérée en \<MailboxIdentity\> remplaçant par le nom, l’alias, le compte ou l’adresse e-mail de la boîte aux lettres et en exécutant la commande suivante dans [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) :

    ```powershell
    Set-Mailbox <MailboxIdentity> -ElcProcessingDisabled $true
    ```

1. Attribuez une licence **Exchange Online Plan 2** à la boîte aux lettres récupérée. Cette étape est nécessaire pour remettre la boîte aux lettres en attente pour litige. Pour obtenir des instructions, consultez [Attribuer des licences aux utilisateurs](/microsoft-365/admin/manage/assign-licenses-to-users).

1. Configurez la valeur **PreferredDataLocation** sur la boîte aux lettres comme décrit dans la section précédente.

1. Une fois que vous avez confirmé que la boîte aux lettres a été déplacée vers le nouvel emplacement géographique, remettez la boîte aux lettres récupérée en attente pour litige. Pour obtenir des instructions, consultez [Placer une boîte aux lettres en attente pour litige](/microsoft-365/compliance/create-a-litigation-hold#place-a-mailbox-on-litigation-hold).

1. Après avoir vérifié que la conservation pour litige est en place, autorisez l’Assistant Dossier managé à traiter à nouveau la boîte aux lettres en \<MailboxIdentity\> remplaçant par le nom, l’alias, le compte ou l’adresse e-mail de la boîte aux lettres et en exécutant la commande suivante dans [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) :

    ```powershell
    Set-Mailbox <MailboxIdentity> -ElcProcessingDisabled $false
    ```

1. Rendez la boîte aux lettres inactive à nouveau en supprimant le compte d’utilisateur associé à la boîte aux lettres. Pour obtenir des instructions, consultez [Supprimer un utilisateur de votre organisation](/admin/add-users/delete-a-user). Cette étape libère également la licence Exchange Online Plan 2 pour d’autres utilisations.

**Remarque** : Lorsque vous déplacez une boîte aux lettres inactive vers un autre emplacement géographique, vous pouvez affecter les résultats de la recherche de contenu ou la possibilité d’effectuer une recherche dans la boîte aux lettres à partir de l’emplacement géographique précédent. Pour plus d’informations, consultez [Recherche et exportation de contenu dans des environnements multigéographiques](/microsoft-365/compliance/set-up-compliance-boundaries#searching-and-exporting-content-in-multi-geo-environments).
  
#### <a name="create-new-cloud-mailboxes-in-a-specific-_geography_-location"></a>Créer des boîtes aux lettres cloud dans un emplacement _Géographique_ spécifique

Pour créer une boîte aux lettres dans un emplacement _géographique_ spécifique, vous devez effectuer l’une des étapes suivantes :

- Configurez la valeur **PreferredDataLocation** comme décrit dans la section précédente [Déplacer une boîte aux lettres cloud uniquement existante vers un emplacement _géographique_ spécifique](#move-an-existing-cloud-only-mailbox-to-a-specific-geo-location) _avant_ de créer la boîte aux lettres dans Exchange Online. Par exemple, configurez la valeur **PreferredDataLocation** sur un utilisateur avant d’attribuer une licence.

- Attribuer une licence lors de la définition de la valeur **PreferredDataLocation**.

Pour créer un utilisateur sous licence cloud uniquement (non synchronisé avec AAD Connect) dans un emplacement _géographique_ spécifique, utilisez la syntaxe suivante dans Azure AD PowerShell :

```powershell
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoLocationCode>
```

Cet exemple montre comment créer un compte d’utilisateur pour Elizabeth Brunner avec les valeurs suivantes :

- Nom d’utilisateur principal : ebrunner@contoso.onmicrosoft.com
- Prénom : Elizabeth
- Nom : Brunner
- Nom d’affichage : Elizabeth Brunner
- Mot de passe : généré de façon aléatoire et affiché dans les résultats de la commande (étant donné que nous n’utilisons pas le paramètre _Password_)
- Licence : `contoso:ENTERPRISEPREMIUM` (E5)
- Emplacement : Australie (AUS)

```powershell
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

Pour plus d’informations sur la création de comptes d’utilisateur et la recherche de valeurs LicenseAssignment dans Azure AD PowerShell, voir [Création de comptes d’utilisateurs avec PowerShell](create-user-accounts-with-microsoft-365-powershell.md) et [Afficher les licences et les services avec PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md).

> [!NOTE]
> Si vous utilisez Exchange Online PowerShell pour activer une boîte aux lettres et que vous avez besoin que la boîte aux lettres soit créée directement à l’emplacement _géographique_ spécifié dans **PreferredDataLocation**, vous devez utiliser une applet de commande Exchange Online telle que **Enable-Mailbox** ou **New-Mailbox** directement sur le service cloud. Si vous utilisez l’applet de commande **Enable-RemoteMailbox** dans Exchange PowerShell local, la boîte aux lettres est créée à l’emplacement _Géographique approvisionné principal_ .

#### <a name="onboard-existing-on-premises-mailboxes-in-a-specific-_geography_-location"></a>Intégrer des boîtes aux lettres locales existantes dans un emplacement _Géographique_ spécifique

Vous pouvez vous servir des outils et processus d’intégration standard pour migrer une boîte aux lettres d’une organisation Exchange locale vers Exchange Online. Ces outils sont le [Tableau de bord de migration dans le Centre d’administration Exchange](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331) et la cmdlet [New-MigrationBatch](/powershell/module/exchange/new-migrationbatch) dans Exchange Online PowerShell.

La première étape consiste à vérifier qu’un objet utilisateur existe pour chaque boîte aux lettres à intégrer, et que la valeur **PreferredDataLocation** correcte est configurée dans Azure AD. Les outils d’intégration respectent la valeur **PreferredDataLocation** et migrent les boîtes aux lettres directement vers la zone géographique spécifiée.

Vous pouvez également effectuer les étapes suivantes pour intégrer des boîtes aux lettres directement dans un emplacement _géographique_ spécifique à l’aide de l’applet [de commande New-MoveRequest](/powershell/module/exchange/new-moverequest) dans Exchange Online PowerShell.

1. Vérifiez que l’objet utilisateur existe pour chaque boîte aux lettres intégrée et que la valeur **PreferredDataLocation** est correctement définie dans Azure AD. La valeur **PreferredDataLocation** est synchronisée avec l’attribut **MailboxRegion** de l’objet utilisateur de courrier correspondant dans Exchange Online.

1. Connectez-vous directement à l’emplacement _Géographique satellite_ spécifique en suivant les instructions de connexion fournies plus haut dans cette rubrique.

1. Dans Exchange Online PowerShell, stockez les informations d’identification d’administrateur locales utilisées pour effectuer une migration de boîte aux lettres dans une variable en exécutant la commande suivante :

   ```powershell
   $RC = Get-Credential
   ```

1. Dans Exchange Online PowerShell, créez une cmdlet **New-MoveRequest** similaire à l’exemple suivant :

   ```powershell
   New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
   ```

1. Répétez l’étape 4 pour chaque boîte aux lettres à migrer d’Exchange sur site vers l’emplacement géographique satellite auquel vous êtes actuellement connecté.

1. Si vous devez migrer des boîtes aux lettres supplémentaires vers un autre emplacement géographique satellite, répétez les étapes 2 à 4 pour chaque emplacement spécifique.

## <a name="multi-geo-reporting"></a>Rapports multigéographiques
  
> [!NOTE]
> La fonctionnalité de création de rapports multigéographiques est actuellement en préversion, n’est pas disponible dans toutes les organisations et est susceptible d’être modifiée.

**Les rapports d’utilisation multigéographique** dans le Centre d'administration Microsoft 365 affichent le nombre d’utilisateurs par emplacement _géographique_. Le rapport présente la répartition des utilisateurs pour le mois en cours et les données historiques des 6 derniers mois.

## <a name="migration"></a>Migration

Étant donné qu’il faut du temps pour déplacer chaque utilisateur vers le nouveau centre de données _Geography_ pour un seul locataire, certains utilisateurs se trouveront toujours dans l’ancien centre de données _Geography_ pendant le déplacement, tandis que d’autres se trouveront dans le nouveau centre de données _Geography_. Cela signifie que certaines fonctionnalités qui impliquent l’accès à plusieurs boîtes aux lettres peuvent ne pas fonctionner entièrement pendant une période du processus de déplacement, qui peut durer des semaines. Ces fonctionnalités sont décrites dans les sections suivantes.

### <a name="open-shared-folder-in-outlook-web-access"></a>Ouvrez « Dossier partagé » dans Outlook Web Access 

Some users open a shared mail folder from another mailbox (that the user has read or write permissions to) in Outlook Web Access using the "Shared Folder" feature. The following table describes how access to shared folders works during a mailbox move. Please note that users with full permissions to a shared mailbox can open the mailbox by using Outlook Web Access during the move.

| Configuration | Description |
|:-----|:-----|
|L’utilisateur dispose d’autorisations de dossier de boîte aux lettres sur une autre boîte aux lettres  <br/> |Potentiellement limité.  <br/> Si l’utilisateur A et la boîte aux lettres B ne se trouvent pas dans la même _zone géographique_ pendant le déplacement du locataire, l’utilisateur A ne peut pas ouvrir le dossier de la boîte aux lettres B dans Outlook Web Access si l’utilisateur A n’est autorisé qu’à accéder à un dossier spécifique dans la boîte aux lettres B.  <br/> Pour ajouter un dossier partagé, cliquez avec le bouton droit de la souris sur le nom d’utilisateur dans le volet de navigation gauche, puis sélectionnez **Ajouter un dossier partagé**.  <br/> |
|Utilisateur disposant de droits d’accès complets sur une autre boîte aux lettres  <br/> |Entièrement pris en charge  <br/> Si l’utilisateur A dispose de l’autorisation « Accès total » à la boîte aux lettres B, l’utilisateur A peut cliquer sur le dossier partagé dans le volet de navigation gauche d’Outlook Web Access pour ouvrir une fenêtre affichant la boîte aux lettres B.  Un utilisateur peut ouvrir une boîte aux lettres partagée à l’aide d’Outlook Web Access pendant le déplacement sans aucun impact négatif. La limitation s’applique uniquement au partage au niveau du dossier dans une boîte aux lettres.

Le processus de migration des données de messagerie vers Microsoft 365 pendant la Exchange Online est un scénario courant et est pris en charge. La migration cloud entre les zones géographiques du centre de données n’interfère pas avec les migrations de boîtes aux lettres locales vers le cloud.

### <a name="how-can-i-determine-customer-data-location"></a>Comment puis-je déterminer l’emplacement des données client ?

Vous trouverez l’emplacement réel des données dans le Centre de Administration locataires.  En tant qu’administrateur client, vous pouvez trouver l’emplacement réel des données pour les données validées en accédant à Administration->Paramètres->Paramètres de l’organisation->Profil d’organisation->Emplacement des données.
