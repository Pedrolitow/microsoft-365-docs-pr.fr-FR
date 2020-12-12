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
ms.service: O365-seccomp
localization_priority: Normal
ms.assetid: 4bfaf2ab-e633-4227-8bde-effefb41a3db
description: Découvrez comment gérer les utilisateurs de messagerie dans Exchange Online Protection (EOP), notamment à l’aide de la synchronisation d’annuaires, du centre d’administration Exchange et de PowerShell pour gérer les utilisateurs.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: a8258a63fe0fbf4a6b5641fbdef213f25de2e4dd
ms.sourcegitcommit: 0a8b0186cc041db7341e57f375d0d010b7682b7d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "49658832"
---
# <a name="manage-mail-users-in-standalone-eop"></a>Gérer les utilisateurs d’e-mail dans EOP autonome

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Dans les organisations Exchange Online Protection (EOP) autonomes sans boîtes aux lettres Exchange Online, les utilisateurs de messagerie constituent le type de compte d’utilisateur fondamental. Un utilisateur de messagerie dispose d’informations d’identification de compte dans votre organisation EOP autonome et peut accéder aux ressources (auxquelles des autorisations sont attribuées). L’adresse de messagerie d’un utilisateur de messagerie est externe (par exemple, dans votre environnement de messagerie local).

> [!NOTE]
> Lorsque vous créez un utilisateur de messagerie, le compte d’utilisateur correspondant est disponible dans le centre d’administration 365 de Microsoft. Lorsque vous créez un compte d’utilisateur dans le centre d’administration 365 de Microsoft, vous ne pouvez pas utiliser ce compte pour créer un utilisateur de messagerie.

La méthode recommandée pour créer et gérer des utilisateurs de messagerie en mode autonome EOP consiste à utiliser la synchronisation d’annuaires, comme décrit dans la section [utiliser la synchronisation d’annuaires pour gérer les utilisateurs de messagerie](#use-directory-synchronization-to-manage-mail-users) plus loin dans cet article.

Pour les organisations EOP autonomes avec un petit nombre d’utilisateurs, vous pouvez ajouter et gérer des utilisateurs de messagerie dans le centre d’administration Exchange ou dans une version PowerShell d’EOP autonome comme décrit dans cet article.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Pour ouvrir le centre d’administration Exchange, consultez la rubrique [Exchange Admin Center in standalone EOP](exchange-admin-center-in-exchange-online-protection-eop.md).

- Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Lorsque vous créez des utilisateurs de messagerie dans EOP PowerShell, il se peut que vous rencontriez une limitation. En outre, les cmdlets PowerShell d’EOP utilisent une méthode de traitement par lots qui entraîne un délai de propagation de quelques minutes avant que les résultats des commandes soient visibles.

- Pour pouvoir effectuer les procédures décrites dans cet article, vous devez disposer d’autorisations dans Exchange Online Protection. Plus précisément, vous avez besoin des rôles **création du destinataire de messagerie** (création) et **destinataires** (modifier), qui sont attribués aux groupes de rôles gestion de l' **organisation** (administrateurs globaux) et **gestion des destinataires** par défaut. Pour plus d’informations, consultez la rubrique [autorisations dans EOP autonome](feature-permissions-in-eop.md) et utiliser le centre d’administration Exchange pour [modifier la liste des membres dans les groupes de rôles](manage-admin-role-group-permissions-in-eop.md#use-the-eac-modify-the-list-of-members-in-role-groups).

- Pour plus d’informations sur les raccourcis clavier applicables aux procédures décrites dans cet article, reportez-vous à [la rubrique raccourcis clavier du centre d’administration Exchange dans Exchange Online](https://docs.microsoft.com/Exchange/accessibility/keyboard-shortcuts-in-admin-center).

> [!TIP]
> Vous rencontrez des difficultés ? Demandez de l’aide en participant aux forums Exchange. Visitez le forum [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351) .

## <a name="use-the-exchange-admin-center-to-manage-mail-users"></a>Utiliser le centre d’administration Exchange pour gérer les utilisateurs de messagerie

### <a name="use-the-eac-to-create-mail-users"></a>Utiliser le centre d’administration Exchange pour créer des utilisateurs de messagerie

1. Dans le centre d’administration Exchange, accédez à contacts des **destinataires** \> 

2. Cliquez sur **nouvelle** ![ icône ](../../media/ITPro-EAC-AddIcon.png) . Dans la page **nouvel utilisateur de messagerie** qui s’ouvre, configurez les paramètres suivants. Les paramètres marqués par un <sup>\*</sup> sont obligatoires.

   - **Prénom**

   - **Initiales**: initiale du deuxième prénom de la personne.

   - **Nom de famille**

   - <sup>\*</sup>**Nom d’affichage**: par défaut, cette zone affiche les valeurs des **zones Prénom**, **initiales** et nom de **famille** . Vous pouvez accepter cette valeur ou la modifier. La valeur doit être unique et sa longueur maximale est de 64 caractères.

   - <sup>\*</sup>**Alias**: entrez un alias unique, en utilisant jusqu’à 64 caractères, pour l’utilisateur.

   - **Adresse de messagerie externe**: entrez l’adresse de messagerie de l’utilisateur. Le domaine doit être externe à votre organisation en nuage.

   - <sup>\*</sup>**ID d’utilisateur**: entrez le compte que la personne utilisera pour se connecter au service. L’ID d’utilisateur est constitué d’un nom d’utilisateur à gauche du symbole arobas (@) et d’un domaine sur le côté droit.

   - <sup>\*</sup>**Nouveau mot de** passe et <sup>\*</sup> **confirmer le mot de passe**: entrez et entrez à nouveau le mot de passe du compte. Vérifiez que le mot de passe est conforme aux exigences de longueur, de complexité et d’historique de votre organisation.

3. Lorsque vous avez terminé, cliquez sur **Enregistrer** pour créer l'utilisateur de messagerie.

### <a name="use-the-eac-to-modify-mail-users"></a>Utiliser le centre d’administration Exchange pour modifier les utilisateurs de messagerie

1. Dans le CAE, accédez à **Destinataires** \> **Contacts**.

2. Sélectionnez l’utilisateur de messagerie à modifier, puis cliquez sur modifier l'  ![ icône modifier ](../../media/ITPro-EAC-AddIcon.png) .

3. Sur la page Propriétés de l’utilisateur de messagerie qui s’ouvre, cliquez sur l’un des onglets suivants pour afficher ou modifier les propriétés.

   Lorsque vous avez terminé, cliquez sur **Enregistrer**.

#### <a name="general"></a>Général

Utilisez l’onglet **général** pour afficher ou modifier des informations de base sur l’utilisateur de messagerie.

- **Prénom**

- **Initiales**

- **Nom de famille**

- **Nom d’affichage**: ce nom s’affiche dans le carnet d’adresses de votre organisation, sur les lignes à : et de : dans le courrier électronique, et dans la liste des contacts du centre d’administration Exchange. Ce nom ne peut pas contenir d'espaces vides avant ou après le nom complet.

- **ID utilisateur**: il s’agit du compte de l’utilisateur dans Microsoft 365. Vous ne pouvez pas modifier cette valeur ici.

#### <a name="contact-information"></a>Informations de contact

L’onglet **informations** sur le contact permet d’afficher ou de modifier les informations de contact de l’utilisateur. L'information sur cette page s'affiche dans le carnet d'adresses.

- **Street**
- **Ville**
- **État/Province**
- **Code postal**
- **Pays**
- **Téléphone professionnel**
- **Téléphone portable**
- **Fax**
- **Autres options**

  - **Bureau**
  - **Téléphone personnel**
  - **Page Web**
  - **Notes**

#### <a name="organization"></a>Organisation

L’onglet **organisation** permet d’enregistrer des informations détaillées sur le rôle de l’utilisateur dans l’organisation.

- **Poste**
- **Service**
- **Entreprise**

### <a name="use-the-eac-to-remove-mail-users"></a>Utiliser le centre d’administration Exchange pour supprimer des utilisateurs de messagerie

1. Dans le CAE, accédez à **Destinataires** \> **Contacts**.

2. Sélectionnez l’utilisateur de messagerie à supprimer, puis cliquez sur supprimer l'  ![ icône Supprimer ](../../media/ITPro-EAC-RemoveIcon.gif) .

## <a name="use-powershell-to-manage-mail-users"></a>Utiliser PowerShell pour gérer les utilisateurs de messagerie

### <a name="use-standalone-eop-powershell-to-view-mail-users"></a>Utilisation d’EOP PowerShell autonome pour afficher les utilisateurs de messagerie

Pour renvoyer une liste récapitulative de tous les utilisateurs de messagerie dans une version autonome d’EOP PowerShell, exécutez la commande suivante :

```powershell
Get-Recipient -RecipientType MailUser -ResultSize unlimited
```

Pour afficher des informations détaillées sur un utilisateur de messagerie spécifique, remplacez \<MailUserIdentity\> par le nom, l’alias ou le nom de compte de l’utilisateur de messagerie, puis exécutez les commandes suivantes :

```powershell
Get-Recipient -Identity <MailUserIdentity> | Format-List
```

```powershell
Get-User -Identity <MailUserIdentity> | Format-List
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Get-Recipient](https://docs.microsoft.com/powershell/module/exchange/get-recipient) et [Get-User](https://docs.microsoft.com/powershell/module/exchange/get-user).

### <a name="use-standalone-eop-powershell-to-create-mail-users"></a>Utilisation d’EOP PowerShell autonome pour créer des utilisateurs de messagerie

Pour créer des utilisateurs de messagerie dans une version autonome d’EOP PowerShell, utilisez la syntaxe suivante :

```powershell
New-EOPMailUser -Name "<UniqueName>" -MicrosoftOnlineServicesID <Account> -Password (ConvertTo-SecureString -String '<password>' -AsPlainText -Force) [-Alias <AliasValue>] [-DisplayName "<Display Name>"] [-ExternalEmailAddress <ExternalEmailAddress>] [-FirstName <Text>] [-Initials <Text>] [-LastName <Text>]
```

**Remarques** :

- Le paramètre _Name_ est obligatoire, sa longueur maximale est de 64 caractères et doit être unique. Si vous n’utilisez pas le paramètre _DisplayName_, la valeur du paramètre _Name_ est utilisée pour le nom complet.
- Si vous n’utilisez pas le paramètre _alias_ , le côté gauche du paramètre _MicrosoftOnlineServicesID_ est utilisé pour l’alias.
- Si vous n’utilisez pas le paramètre _ExternalEmailAddress_ , la valeur _MicrosoftOnlineServicesID_ est utilisée pour l’adresse de messagerie externe.

Cet exemple crée un utilisateur de messagerie avec les paramètres suivants :

- Le nom est JeffreyZeng et le nom d’affichage est Jeffrey Zeng.
- Le prénom est Jeffrey et le nom est Zeng.
- L'alias est jeffreyz.
- L'adresse de messagerie externe est jzeng@tailspintoys.com.
- Le nom du compte est jeffreyz@contoso.onmicrosoft.com.
- Le mot de passe est Pa$$word1.

```PowerShell
New-EOPMailUser -Name JeffreyZeng -MicrosoftOnlineServicesID jeffreyz@contoso.onmicrosoft.com -Password (ConvertTo-SecureString -String 'Pa$$word1' -AsPlainText -Force) -ExternalEmailAddress jeffreyz@tailspintoys.com -DisplayName "Jeffrey Zeng" -Alias jeffreyz -FirstName Jeffrey -LastName Zeng
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [New-EOPMailUser](https://docs.microsoft.com/powershell/module/exchange/new-eopmailuser).

### <a name="use-standalone-eop-powershell-to-modify-mail-users"></a>Utilisation d’EOP PowerShell autonome pour modifier des utilisateurs de messagerie

Pour modifier des utilisateurs de messagerie existants dans une version autonome d’EOP PowerShell, utilisez la syntaxe suivante :

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

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Set-EOPMailUser](https://docs.microsoft.com/powershell/module/exchange/set-eopmailuser).

### <a name="use-standalone-eop-powershell-to-remove-mail-users"></a>Utilisation d’EOP PowerShell autonome pour supprimer des utilisateurs de messagerie

Pour supprimer des utilisateurs de messagerie dans une version autonome d’EOP PowerShell, remplacez \<MailUserIdentity\> par le nom, l’alias ou le nom de compte de l’utilisateur de messagerie, puis exécutez la commande suivante :

```PowerShell
Remove-EOPMailUser -Identity <MailUserIdentity\>
```

Cet exemple supprime l’utilisateur de messagerie pour Jeffrey Zeng.

```PowerShell
Remove-EOPMailUser -Identity "Jeffrey Zeng"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Remove-EOPMailUser](https://docs.microsoft.com/powershell/module/exchange/remove-eopmailuser).

## <a name="how-do-you-know-these-procedures-worked"></a>Comment savoir si ces procédures ont fonctionné ?

Pour vérifier que vous avez bien créé, modifié ou supprimé des utilisateurs de messagerie dans une version autonome d’EOP, utilisez l’une des procédures suivantes :

- Dans le CAE, accédez à **Destinataires** \> **Contacts**. Vérifiez que l’utilisateur de messagerie est indiqué (ou non). Sélectionnez l’utilisateur de messagerie et affichez les informations dans le volet d’informations, ou cliquez sur **modifier** ![ l’icône modifier ](../../media/ITPro-EAC-AddIcon.png) pour afficher les paramètres.

- Dans la version autonome d’EOP PowerShell, exécutez la commande suivante pour vérifier que l’utilisateur de messagerie est indiqué (ou non) :

  ```powershell
  Get-Recipient -RecipientType MailUser -ResultSize unlimited
  ```

- Remplacez \<MailUserIdentity\> par le nom, l’alias ou le nom de compte de l’utilisateur de messagerie, puis exécutez les commandes suivantes pour vérifier les paramètres :

  ```powershell
  Get-Recipient -Identity <MailUserIdentity> | Format-List
  ```

  ```powershell
  Get-User -Identity <MailUserIdentity> | Format-List
  ```

## <a name="use-directory-synchronization-to-manage-mail-users"></a>Utilisation de la synchronisation d’annuaires pour gérer les utilisateurs de messagerie

Dans la version autonome d’EOP, la synchronisation d’annuaires est disponible pour les clients disposant d’Active Directory sur site. Vous pouvez synchroniser ces comptes avec Azure Active Directory (Azure AD), où les copies des comptes sont stockées dans le Cloud. Lorsque vous synchronisez vos comptes d’utilisateur existants avec Azure Active Directory, vous pouvez afficher ces utilisateurs dans le volet **destinataires** du centre d’administration Exchange ou dans un PowerShell d’EOP autonome.

**Remarques** :

- Si vous utilisez la synchronisation d’annuaires pour gérer vos destinataires, vous pouvez toujours ajouter et gérer des utilisateurs dans le centre d’administration 365 de Microsoft, mais ils ne seront pas synchronisés avec votre annuaire Active Directory local. En effet, la synchronisation d’annuaires ne synchronise que les destinataires de votre annuaire Active Directory sur site vers le nuage.

- Il est recommandé d’utiliser la synchronisation d’annuaires avec les fonctionnalités suivantes :

  - Listes **des expéditeurs approuvés Outlook et listes des expéditeurs bloqués**: lorsqu’ils sont synchronisés avec le service, ces listes prévalent sur le filtrage du courrier indésirable dans le service. Cela permet aux utilisateurs de gérer leur propre liste d’expéditeurs approuvés et la liste des expéditeurs bloqués avec des entrées individuelles de domaine et d’expéditeur. Pour plus d’informations, voir [Configurer les paramètres du courrier indésirable sur les boîtes aux lettres Exchange Online](configure-junk-email-settings-on-exo-mailboxes.md).

  - **Blocage du périmètre basé sur l’annuaire (DBEB)**: pour plus d’informations sur DBEB, voir [use Directory based Edge Blocking to Reject messages sent to Invalid Recipients](https://docs.microsoft.com/Exchange/mail-flow-best-practices/use-directory-based-edge-blocking).

  - **Accès de l’utilisateur final à la mise en quarantaine**: pour accéder à ses messages mis en quarantaine, les destinataires doivent disposer d’un ID d’utilisateur et d’un mot de passe valides dans le service. Pour plus d’informations sur la mise en quarantaine, consultez [la rubrique Rechercher et débloquer les messages mis en quarantaine en tant qu’utilisateur](find-and-release-quarantined-messages-as-a-user.md).

  - **Règles de flux de messagerie (également appelées règles de transport)**: lorsque vous utilisez la synchronisation d’annuaires, vos utilisateurs et groupes Active Directory existants sont automatiquement téléchargés dans le Cloud, et vous pouvez créer des règles de flux de messagerie qui ciblent des utilisateurs et/ou des groupes spécifiques sans avoir à les ajouter manuellement au service. Notez que les [groupes de distribution dynamique](https://docs.microsoft.com/Exchange/recipients-in-exchange-online/manage-dynamic-distribution-groups/manage-dynamic-distribution-groups) ne peuvent pas être synchronisés via la synchronisation d’annuaires.

Obtenir les autorisations nécessaires et préparer la synchronisation d’annuaires, comme décrit dans [What is Hybrid Identity with Azure Active Directory ?](https://docs.microsoft.com/azure/active-directory/hybrid/whatis-hybrid-identity).

### <a name="synchronize-directories-with-azure-active-directory-connect-aad-connect"></a>Synchroniser des annuaires avec Azure Active Directory Connect (AAD Connect)

1. Activer la synchronisation d’annuaires, comme décrit dans [Azure ad Connect Sync : comprendre et personnaliser la synchronisation](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sync-whatis).

2. Installez et configurez un ordinateur local pour exécuter AAD Connect comme décrit dans [Prerequisites for Azure ad Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites).

3. [Sélectionnez le type d’installation à utiliser pour Azure ad Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-select-installation):

   - [Express](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-express)

   - [Personnalisé](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-custom)

   - [Authentification directe](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-pta-quick-start)

> [!IMPORTANT]
> Après exécution de l'Assistant Configuration de l'outil de synchronisation Azure Active Directory, le compte **MSOL_AD_SYNC** est créé dans votre forêt Active Directory. Ce compte permet de lire et de synchroniser vos informations Active Directory sur site. Pour que la synchronisation d'annuaires fonctionne correctement, assurez-vous que le port TCP 443 est ouvert sur votre serveur de synchronisation d'annuaires sur site.

Après avoir configuré votre synchronisation, veillez à vérifier que la synchronisation AAD se synchronise correctement. Dans le CAE, accédez à **Destinataires** \> **Contacts** et vérifiez que la liste des utilisateurs a été correctement synchronisée à partir de votre environnement local.
