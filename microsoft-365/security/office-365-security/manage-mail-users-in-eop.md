---
title: Gérer les utilisateurs d’e-mail dans EOP autonome
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
localization_priority: Normal
ms.assetid: 4bfaf2ab-e633-4227-8bde-effefb41a3db
description: Découvrez comment gérer les utilisateurs de messagerie dans Exchange Online Protection (EOP), notamment en utilisant la synchronisation d’annuaires, le CAE et PowerShell pour gérer les utilisateurs.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 863bde5ef860ee980f768ddc085379180e6a71aa
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50910617"
---
# <a name="manage-mail-users-in-standalone-eop"></a>Gérer les utilisateurs d’e-mail dans EOP autonome

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
-  [Exchange Online Protection autonome](exchange-online-protection-overview.md)

Dans les organisations Exchange Online Protection (EOP) autonomes sans boîtes aux lettres Exchange Online, les utilisateurs de messagerie représentent le type fondamental de compte d’utilisateur. Un utilisateur de messagerie dispose d’informations d’identification de compte dans votre organisation EOP autonome et peut accéder aux ressources (avoir des autorisations affectées). L’adresse de messagerie d’un utilisateur de messagerie est externe (par exemple, dans votre environnement de messagerie local).

> [!NOTE]
> Lorsque vous créez un utilisateur de messagerie, le compte d’utilisateur correspondant est disponible dans le Centre d’administration Microsoft 365. Lorsque vous créez un compte d’utilisateur dans le Centre d’administration Microsoft 365, vous ne pouvez pas l’utiliser pour créer un utilisateur de messagerie.

La [méthode](#use-directory-synchronization-to-manage-mail-users) recommandée pour créer et gérer des utilisateurs de messagerie dans EOP autonome consiste à utiliser la synchronisation d’annuaires comme décrit dans la section Utiliser la synchronisation d’annuaires pour gérer les utilisateurs de messagerie plus loin dans cet article.

Pour les organisations EOP autonomes avec un petit nombre d’utilisateurs, vous pouvez ajouter et gérer des utilisateurs de messagerie dans le Centre d’administration Exchange (CAE) ou dans EOP PowerShell autonome, comme décrit dans cet article.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Pour ouvrir le Centre d’administration Exchange (CAE), consultez le Centre [d’administration Exchange dans EOP autonome.](exchange-admin-center-in-exchange-online-protection-eop.md)

- Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Lorsque vous créez des utilisateurs de messagerie dans EOP PowerShell, vous pouvez rencontrer une limitation. En outre, les cmdlets EOP PowerShell utilisent une méthode de traitement par lots qui entraîne un délai de propagation de quelques minutes avant que les résultats des commandes ne soient visibles.

- Des autorisations doivent vous être attribuées dans Exchange Online Protection avant de pouvoir suivre les procédures de cet article. Plus précisément, vous avez besoin des **rôles** Création **(créer)** et Destinataires de messagerie (modifier),  qui sont affectés par défaut aux groupes de rôles Gestion de l’organisation **(administrateurs** globaux) et Gestion des destinataires. Pour plus d’informations, voir Autorisations dans [EOP](feature-permissions-in-eop.md) autonome et utiliser le CAE pour modifier la liste des membres des [groupes de rôles.](manage-admin-role-group-permissions-in-eop.md#use-the-eac-modify-the-list-of-members-in-role-groups)

- Pour plus d’informations sur les raccourcis clavier qui peuvent s’appliquer aux procédures de cet article, voir raccourcis clavier pour le Centre d’administration [Exchange dans Exchange Online.](/Exchange/accessibility/keyboard-shortcuts-in-admin-center)

> [!TIP]
> Vous rencontrez des difficultés ? Demandez de l’aide en participant aux forums Exchange. Visitez le forum [Exchange Online Protection.](https://social.technet.microsoft.com/Forums/forefront/home?forum=FOPE)

## <a name="use-the-exchange-admin-center-to-manage-mail-users"></a>Utiliser le Centre d’administration Exchange pour gérer les utilisateurs de messagerie

### <a name="use-the-eac-to-create-mail-users"></a>Utiliser le EAC pour créer des utilisateurs de messagerie

1. Dans le EAC, allez à **Contacts des** \> **destinataires**

2. Cliquez **sur Nouvelle** ![ ](../../media/ITPro-EAC-AddIcon.png) icône. Dans la page **Nouvel utilisateur de messagerie** qui s’ouvre, configurez les paramètres suivants. Les paramètres marqués par un <sup>\*</sup> paramètre sont obligatoires.

   - **Prénom**

   - **Initiales :** initiale du deuxième milieu de la personne.

   - **Nom de famille**

   - <sup>\*</sup>**Nom complet**: par défaut, cette zone affiche les valeurs des zones **Prénom,** **Initiales** **et** Nom. Vous pouvez accepter cette valeur ou la modifier. La valeur doit être unique et sa longueur maximale est de 64 caractères.

   - <sup>\*</sup>**Alias**: entrez un alias unique, en utilisant jusqu’à 64 caractères, pour l’utilisateur

   - **Adresse de messagerie externe**: entrez l’adresse e-mail de l’utilisateur. Le domaine doit être externe à votre organisation informatique.

   - <sup>\*</sup>**ID d’utilisateur**: entrez le compte que la personne utilisera pour se connecter au service. L’ID d’utilisateur se compose d’un nom d’utilisateur sur le côté gauche du symbole @) et d’un domaine sur le côté droit.

   - <sup>\*</sup>**Nouveau mot de passe** et confirmer le mot de passe : entrez et entrez de nouveau le mot de passe du <sup>\*</sup> compte. Vérifiez que le mot de passe est conforme aux exigences de longueur, de complexité et d’historique du mot de passe de votre organisation.

3. Lorsque vous avez terminé, cliquez sur **Enregistrer** pour créer l'utilisateur de messagerie.

### <a name="use-the-eac-to-modify-mail-users"></a>Utiliser le EAC pour modifier les utilisateurs de messagerie

1. Dans le CAE, accédez à **Destinataires** \> **Contacts**.

2. Sélectionnez l’utilisateur de messagerie à modifier, puis cliquez **sur** Modifier ![ l’icône ](../../media/ITPro-EAC-AddIcon.png) Modifier.

3. Dans la page des propriétés de l’utilisateur de messagerie qui s’ouvre, cliquez sur l’un des onglets suivants pour afficher ou modifier les propriétés.

   Lorsque vous avez terminé, cliquez sur **Enregistrer**.

#### <a name="general"></a>Général

Utilisez **l’onglet Général** pour afficher ou modifier des informations de base sur l’utilisateur de messagerie.

- **Prénom**

- **Initiales**

- **Nom de famille**

- **Nom d’affichage**: ce nom apparaît dans le carnet d’adresses de votre organisation, sur les lignes À : et De : du message électronique et dans la liste des contacts dans leAC. Ce nom ne peut pas contenir d'espaces vides avant ou après le nom complet.

- **ID utilisateur**: il s’agit du compte de l’utilisateur dans Microsoft 365. Vous ne pouvez pas modifier cette valeur ici.

#### <a name="contact-information"></a>Informations de contact

Utilisez **l’onglet Informations de** contact pour afficher ou modifier les informations de contact de l’utilisateur. L'information sur cette page s'affiche dans le carnet d'adresses.

- **Street**
- **Ville**
- **État/Province**
- **Code postal**
- **Pays**
- **Téléphone de travail**
- **Téléphone portable**
- **Fax**
- **Autres options**

  - **Bureau**
  - **Téléphone personnel**
  - **Page Web**
  - **Notes**

#### <a name="organization"></a>Organisation

Utilisez **l’onglet** Organisation pour enregistrer des informations détaillées sur le rôle de l’utilisateur dans l’organisation.

- **Poste**
- **Service**
- **Entreprise**

### <a name="use-the-eac-to-remove-mail-users"></a>Utiliser le EAC pour supprimer des utilisateurs de messagerie

1. Dans le CAE, accédez à **Destinataires** \> **Contacts**.

2. Sélectionnez l’utilisateur de messagerie à supprimer, puis cliquez sur **Supprimer** ![ l’icône ](../../media/ITPro-EAC-RemoveIcon.gif) .

## <a name="use-powershell-to-manage-mail-users"></a>Utiliser PowerShell pour gérer les utilisateurs de messagerie

### <a name="use-standalone-eop-powershell-to-view-mail-users"></a>Utiliser EOP PowerShell autonome pour afficher les utilisateurs de messagerie

Pour renvoyer une liste récapitulatif de tous les utilisateurs de messagerie dans EOP PowerShell autonome, exécutez la commande suivante :

```powershell
Get-Recipient -RecipientType MailUser -ResultSize unlimited
```

Pour afficher des informations détaillées sur un utilisateur de messagerie spécifique, remplacez-le par le nom, l’alias ou le nom de compte de l’utilisateur de messagerie, puis exécutez les \<MailUserIdentity\> commandes suivantes :

```powershell
Get-Recipient -Identity <MailUserIdentity> | Format-List
```

```powershell
Get-User -Identity <MailUserIdentity> | Format-List
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Get-Recipient](/powershell/module/exchange/get-recipient) et [Get-User.](/powershell/module/exchange/get-user)

### <a name="use-standalone-eop-powershell-to-create-mail-users"></a>Utiliser EOP PowerShell autonome pour créer des utilisateurs de messagerie

Pour créer des utilisateurs de messagerie dans EOP PowerShell autonome, utilisez la syntaxe suivante :

```powershell
New-EOPMailUser -Name "<UniqueName>" -MicrosoftOnlineServicesID <Account> -Password (ConvertTo-SecureString -String '<password>' -AsPlainText -Force) [-Alias <AliasValue>] [-DisplayName "<Display Name>"] [-ExternalEmailAddress <ExternalEmailAddress>] [-FirstName <Text>] [-Initials <Text>] [-LastName <Text>]
```

**Remarques** :

- Le _paramètre Name_ est obligatoire, a une longueur maximale de 64 caractères et doit être unique. Si vous n’utilisez pas le paramètre _DisplayName_, la valeur du paramètre _Name_ est utilisée pour le nom complet.
- Si vous n’utilisez pas le paramètre _Alias,_ le côté gauche du paramètre _MicrosoftOnlineServicesID_ est utilisé pour l’alias.
- Si vous n’utilisez pas le _paramètre ExternalEmailAddress,_ la valeur _MicrosoftOnlineServicesID_ est utilisée pour l’adresse de messagerie externe.

Cet exemple crée un utilisateur de messagerie avec les paramètres suivants :

- Le nom est JeffreyZeng et le nom complet est Jeffrey Zeng.
- Le prénom est Jeffrey et le nom est Zeng.
- L'alias est jeffreyz.
- L'adresse de messagerie externe est jzeng@tailspintoys.com.
- Le nom du compte est jeffreyz@contoso.onmicrosoft.com.
- Le mot de passe est Pa$$word1.

```PowerShell
New-EOPMailUser -Name JeffreyZeng -MicrosoftOnlineServicesID jeffreyz@contoso.onmicrosoft.com -Password (ConvertTo-SecureString -String 'Pa$$word1' -AsPlainText -Force) -ExternalEmailAddress jeffreyz@tailspintoys.com -DisplayName "Jeffrey Zeng" -Alias jeffreyz -FirstName Jeffrey -LastName Zeng
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [New-EOPMailUser](/powershell/module/exchange/new-eopmailuser).

### <a name="use-standalone-eop-powershell-to-modify-mail-users"></a>Utiliser EOP PowerShell autonome pour modifier les utilisateurs de messagerie

Pour modifier les utilisateurs de messagerie existants dans EOP PowerShell autonome, utilisez la syntaxe suivante :

```powershell
Set-EOPMailUser -Identity <MailUserIdentity> [-Alias <Text>] [-DisplayName <Text>] [-EmailAddresses <ProxyAddressCollection>] [-MicrosoftOnlineServicesID <SmtpAddress>]
```

```powershell
Set-EOPUser -Identity <MailUserIdentity> [-City <Text>] [-Company <Text>] [-CountryOrRegion <CountryInfo>] [-Department <Text>] [-Fax <PhoneNumber>] [-FirstName <Text>] [-HomePhone <PhoneNumber>] [-Initials <Text>] [-LastName <Text>] [-MobilePhone <PhoneNumber>] [-Notes <Text>] [-Office <Text>] [-Phone <PhoneNumber>] [-PostalCode <String>] [-StateOrProvince <String>] [-StreetAddress <Tet>] [-Title <Text>] [-WebPage <Text>]
```

Cet exemple illustre la configuration de l'adresse de messagerie externe pour Pilar Pinilla.

```PowerShell
Set-EOPMailUser -Identity "Pilar Pinilla" -EmailAddresses pilarp@tailspintoys.com
```

Cet exemple illustre la définition de la propriété Company sur Contoso pour tous les utilisateurs de messagerie.

```PowerShell
$Recip = Get-Recipient -RecipientType MailUser -ResultSize unlimited
$Recip | foreach {Set-EOPUser -Identity $_.Alias -Company Contoso}
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Set-EOPMailUser](/powershell/module/exchange/set-eopmailuser).

### <a name="use-standalone-eop-powershell-to-remove-mail-users"></a>Utiliser EOP PowerShell autonome pour supprimer des utilisateurs de messagerie

Pour supprimer des utilisateurs de messagerie dans EOP PowerShell autonome, remplacez-les par le nom, l’alias ou le nom de compte de l’utilisateur de messagerie, puis exécutez \<MailUserIdentity\> la commande suivante :

```PowerShell
Remove-EOPMailUser -Identity <MailUserIdentity\>
```

Cet exemple supprime l’utilisateur de messagerie pour Jeffrey Zeng.

```PowerShell
Remove-EOPMailUser -Identity "Jeffrey Zeng"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Remove-EOPMailUser](/powershell/module/exchange/remove-eopmailuser).

## <a name="how-do-you-know-these-procedures-worked"></a>Comment savoir si ces procédures ont fonctionné ?

Pour vérifier que vous avez correctement créé, modifié ou supprimé des utilisateurs de messagerie dans EOP autonome, utilisez l’une des procédures suivantes :

- Dans le CAE, accédez à **Destinataires** \> **Contacts**. Vérifiez que l’utilisateur de messagerie est répertorié (ou n’est pas répertorié). Sélectionnez l’utilisateur de messagerie et affichez les  informations dans le volet Détails, ou cliquez sur Modifier l’icône ![ Modifier pour afficher les ](../../media/ITPro-EAC-AddIcon.png) paramètres.

- Dans EOP PowerShell autonome, exécutez la commande suivante pour vérifier que l’utilisateur de messagerie est répertorié (ou n’est pas répertorié) :

  ```powershell
  Get-Recipient -RecipientType MailUser -ResultSize unlimited
  ```

- Remplacez-le par le nom, l’alias ou le nom de compte de l’utilisateur de messagerie, puis exécutez les commandes \<MailUserIdentity\> suivantes pour vérifier les paramètres :

  ```powershell
  Get-Recipient -Identity <MailUserIdentity> | Format-List
  ```

  ```powershell
  Get-User -Identity <MailUserIdentity> | Format-List
  ```

## <a name="use-directory-synchronization-to-manage-mail-users"></a>Utilisation de la synchronisation d’annuaires pour gérer les utilisateurs de messagerie

Dans EOP autonome, la synchronisation d’annuaires est disponible pour les clients avec Active Directory local. Vous pouvez synchroniser ces comptes avec Azure Active Directory (Azure AD), où les copies des comptes sont stockées dans le cloud. Lorsque vous synchronisez vos comptes d’utilisateur existants avec Azure Active Directory, vous pouvez afficher ces utilisateurs dans le volet **Destinataires** du Centre d’administration Exchange (CAE) ou dans EOP PowerShell autonome.

**Remarques** :

- Si vous utilisez la synchronisation d’annuaires pour gérer vos destinataires, vous pouvez toujours ajouter et gérer des utilisateurs dans le Centre d’administration Microsoft 365, mais ils ne seront pas synchronisés avec votre annuaire Active Directory local. En effet, la synchronisation d’annuaires ne synchronise que les destinataires de votre annuaire Active Directory sur site vers le nuage.

- Il est recommandé d’utiliser la synchronisation d’annuaires avec les fonctionnalités suivantes :

  - **Listes d’expéditeurs sûrs Outlook** et expéditeurs bloqués : lorsqu’elles sont synchronisées avec le service, ces listes prévalent sur le filtrage du courrier indésirable dans le service. Cela permet aux utilisateurs de gérer leurs propres listes d’expéditeurs sûrs et d’expéditeurs bloqués avec des entrées d’expéditeur et de domaine individuelles. Pour plus d’informations, voir [Configurer les paramètres du courrier indésirable sur les boîtes aux lettres Exchange Online](configure-junk-email-settings-on-exo-mailboxes.md).

  - Blocage du périphérie basé sur l’annuaire **(DBEB)**: pour plus d’informations sur DBEB, voir Utiliser le blocage de périphérie basé sur l’annuaire pour rejeter les messages envoyés à des [destinataires non valides.](/Exchange/mail-flow-best-practices/use-directory-based-edge-blocking)

  - **Accès des utilisateurs finaux** à la mise en quarantaine : pour accéder à leurs messages mis en quarantaine, les destinataires doivent avoir un ID d’utilisateur et un mot de passe valides dans le service. Pour plus d’informations sur la mise en quarantaine, voir Rechercher et libérer les messages mis en [quarantaine en tant qu’utilisateur.](find-and-release-quarantined-messages-as-a-user.md)

  - Règles de flux de messagerie (également appelées règles de **transport)**: lorsque vous utilisez la synchronisation d’annuaires, vos utilisateurs et groupes Active Directory existants sont automatiquement chargés dans le cloud, et vous pouvez ensuite créer des règles de flux de messagerie qui ciblent des utilisateurs et/ou des groupes spécifiques sans avoir à les ajouter manuellement dans le service. Notez [que les groupes de distribution](/Exchange/recipients-in-exchange-online/manage-dynamic-distribution-groups/manage-dynamic-distribution-groups) dynamique ne peuvent pas être synchronisés via la synchronisation d’annuaires.

Obtenez les autorisations nécessaires et préparez-vous à la synchronisation d’annuaires, comme décrit dans la description de l’identité hybride [avec Azure Active Directory .](/azure/active-directory/hybrid/whatis-hybrid-identity)

### <a name="synchronize-directories-with-azure-active-directory-connect-aad-connect"></a>Synchroniser des répertoires avec Azure Active Directory Connect (AAD Connect)

1. Activez la synchronisation d’annuaires comme décrit dans la synchronisation Azure AD Connect : [comprendre et personnaliser la synchronisation.](/azure/active-directory/hybrid/how-to-connect-sync-whatis)

2. Installez et configurez un ordinateur local pour exécuter AAD Connect, comme décrit dans les conditions [préalables pour Azure AD Connect.](/azure/active-directory/hybrid/how-to-connect-install-prerequisites)

3. [Sélectionnez le type d’installation à utiliser pour Azure AD Connect](/azure/active-directory/hybrid/how-to-connect-install-select-installation):

   - [Express](/azure/active-directory/hybrid/how-to-connect-install-express)

   - [Custom](/azure/active-directory/hybrid/how-to-connect-install-custom)

   - [Authentification directe](/azure/active-directory/hybrid/how-to-connect-pta-quick-start)

> [!IMPORTANT]
> Après exécution de l'Assistant Configuration de l'outil de synchronisation Azure Active Directory, le compte **MSOL_AD_SYNC** est créé dans votre forêt Active Directory. Ce compte permet de lire et de synchroniser vos informations Active Directory sur site. Pour que la synchronisation d'annuaires fonctionne correctement, assurez-vous que le port TCP 443 est ouvert sur votre serveur de synchronisation d'annuaires sur site.

Après avoir configuré votre synchronisation, vérifiez qu’AAD Connect se synchronise correctement. Dans le CAE, accédez à **Destinataires** \> **Contacts** et vérifiez que la liste des utilisateurs a été correctement synchronisée à partir de votre environnement local.