---
title: Utilisation de PowerShell pour effectuer une migration à basculement vers Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
ms.assetid: b468cb4b-a35c-43d3-85bf-65446998af40
description: Découvrez comment utiliser PowerShell pour déplacer le contenu à partir d’un système de messagerie source en effectuant une migration de basculement vers Microsoft 365.
ms.openlocfilehash: 3761640c42a6907818886e96c9d6355d70073522
ms.sourcegitcommit: f302de988d98628922eea1f509a3f639634ddc64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2022
ms.locfileid: "66151203"
---
# <a name="use-powershell-to-perform-a-cutover-migration-to-microsoft-365"></a>Utilisation de PowerShell pour effectuer une migration à basculement vers Microsoft 365

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Vous pouvez migrer le contenu des boîtes aux lettres utilisateur d’un système de messagerie source vers Microsoft 365 à la fois à l’aide d’une migration de basculement. Cet article décrit les tâches correspondant à une migration de messagerie à basculement à l'aide d'Exchange Online PowerShell.

En examinant la rubrique, [ce que vous devez savoir sur une migration de messages de basculement vers Microsoft 365](/Exchange/mailbox-migration/what-to-know-about-a-cutover-migration), vous pouvez obtenir une vue d’ensemble du processus de migration. Une fois familiarisé avec son contenu, reportez-vous au présent article pour migrer des boîtes aux lettres d'un système de messagerie vers un autre.

> [!NOTE]
> Vous pouvez également utiliser le <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centre d’administration Exchange</a> pour effectuer une migration de basculement. Voir [Effectuer une migration de basculement de l’e-mail vers Microsoft 365](/Exchange/mailbox-migration/cutover-migration-to-office-365).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu’il faut savoir avant de commencer

Durée d'exécution estimée de cette tâche : entre 2 et 5 minutes pour créer un lot de migration. Une fois la migration du lot commencée, la durée de l'opération varie en fonction du nombre de boîtes aux lettres incluses dans le lot, de la taille de chacune d'elles et de la capacité réseau disponible. Pour plus d’informations sur d’autres facteurs qui affectent le temps nécessaire à la migration des boîtes aux lettres vers Microsoft 365, consultez [Performances de migration](/Exchange/mailbox-migration/office-365-migration-best-practices).

Des autorisations doivent vous être attribuées avant que vous puissiez exécuter cette procédure. Pour connaître les autorisations nécessaires, consultez l'entrée « Migration » dans un tableau de la rubrique [Autorisations des destinataires](/exchange/recipients-permissions-exchange-2013-help).

Pour utiliser les cmdlets Exchange Online PowerShell, vous devez vous connecter et importer les cmdlets dans votre session Windows PowerShell locale. Pour obtenir des instructions, consultez [Connecter pour Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

Pour la liste complète des commandes de migration, voir [Cmdlets de déplacement et de migration](/powershell/exchange/).

## <a name="migration-steps"></a>Étapes de migration

### <a name="step-1-prepare-for-a-cutover-migration"></a>Étape 1 : Préparez une migration à basculement
<a name="BK_Step1"> </a>

- **Ajoutez votre organisation Exchange locale en tant que domaine accepté de votre organisation Microsoft 365.** Le service de migration utilise l’adresse SMTP de vos boîtes aux lettres locales pour créer l’ID d’utilisateur et l’adresse e-mail microsoft Online Services pour les nouvelles boîtes aux lettres Microsoft 365. La migration échoue si votre domaine Exchange n’est pas un domaine accepté ou le domaine principal de votre organisation Microsoft 365. Pour plus d’informations, consultez [Vérifier votre domaine](../admin/setup/add-domain.md).

- **Configurez Outlook Anywhere sur votre serveur Exchange local** Le service de migration de messagerie utilise RPC sur HTTP ou Outlook Anywhere pour se connecter à votre serveur Exchange local. Pour plus d'informations sur la configuration d'Outlook Anywhere pour Exchange 2010, 2007 et 2003, consultez les rubriques suivantes :

  - [Exchange 2010 : Activer Outlook Anywhere](/previous-versions/office/exchange-server-2010/bb123542(v=exchg.141))

  - [Exchange 2007 : Procédure d'activation d'Outlook Anywhere](/previous-versions/office/exchange-server-2007/bb123889(v=exchg.80))

  - [Exchange 2003 : Scénarios de déploiement RPC sur HTTP](/previous-versions/tn-archive/bb124876(v=exchg.65))

  - [Procédure de configuration d'Outlook Anywhere avec Exchange 2003](/previous-versions/office/exchange-server-2007/aa996922(v=exchg.80))

    > [!IMPORTANT]
    > La configuration d'Outlook Anywhere doit être réalisée à l'aide d'un certificat émis par une autorité de certification (CA) approuvée. Il ne peut être configuré à l'aide d'un certificat auto-signé. Pour plus d'informations, consultez la rubrique [Procédure de configuration de SSL pour Outlook Anywhere](/previous-versions/office/exchange-server-2007/aa995982(v=exchg.80)).

- **Vérifiez que vous pouvez vous connecter à votre organisation Exchange à l'aide d'Outlook Anywhere** Pour tester vos paramètres de connexion, essayez l'une des méthodes suivantes :

  - Utilisez Microsoft Outlook hors de votre réseau d'entreprise pour vous connecter à votre boîte aux lettres Exchange locale.

  - Utilisez l'[analyseur de connectivité à distance Exchange](https://www.testexchangeconnectivity.com/) de Microsoft pour tester vos paramètres de connexion. Utilisez Outlook Anywhere (RPC sur HTTP) ou les tests de découverte automatique d'Outlook.

  - Dans Exchange Online PowerShell, exécutez les commandes suivantes.

  ```powershell
  $Credentials = Get-Credential
  ```

  ```powershell
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

- **Attribuez à un compte d'utilisateur local les autorisations nécessaires pour accéder aux boîtes aux lettres de votre organisation Exchange.** Le compte d’utilisateur local que vous utilisez pour vous connecter à votre organisation locale Exchange (également appelée administrateur de migration) doit disposer des autorisations nécessaires pour accéder aux boîtes aux lettres locales que vous souhaitez migrer vers Microsoft 365. Ce compte d'utilisateur permet de créer un point de terminaison de migration pour votre organisation locale.

    La liste suivante montre les privilèges administratifs requis pour migrer des boîtes aux lettres à l'aide d'une migration à basculement. Trois options sont possibles.

  - L'administrateur de migration doit être membre du groupe **Administrateurs de domaine** dans Active Directory au sein de l'organisation locale.

    Ou

  - L'administrateur de migration doit disposer de l'autorisation **FullAccess** pour chaque boîte aux lettres locale.

    Ou

  - L'administrateur de migration doit disposer de l'autorisation **Receive As** pour la base de données de boîtes aux lettres locale stockant les boîtes aux lettres d'utilisateurs.

- **Désactivez la messagerie unifiée.** Si les boîtes aux lettres locales que vous migrez sont activées pour la messagerie unifiée, vous devez désactiver cette dernière avant de procéder à la migration. Une fois la migration terminée, vous pouvez activer la messagerie unifiée sur les boîtes aux lettres.

- **Groupes de sécurité et délégués** Le service de migration de messagerie ne peut pas détecter si Active Directory local groupes sont des groupes de sécurité ou non. Il ne peut donc pas approvisionner des groupes migrés en tant que groupes de sécurité dans Microsoft 365. Si vous souhaitez avoir des groupes de sécurité dans votre locataire Microsoft 365, vous devez d’abord approvisionner un groupe de sécurité à extension messagerie vide dans votre locataire Microsoft 365 avant de commencer la migration de basculement. En outre, cette méthode de migration déplace uniquement les boîtes aux lettres, les utilisateurs de messagerie, les contacts de messagerie et les groupes à extension messagerie. Si un autre objet Active Directory, tel que l’utilisateur qui n’est pas migré vers Microsoft 365, est affecté en tant que gestionnaire ou délégué à un objet en cours de migration, il doit être supprimé de l’objet avant de migrer.

### <a name="step-2-create-a-migration-endpoint"></a>Étape 2 : Créez un point de terminaison de migration
<a name="BK_Step2"> </a>

Pour migrer correctement l’e-mail, Microsoft 365 doit se connecter et communiquer avec le système de messagerie source. Pour ce faire, Microsoft 365 utilise un point de terminaison de migration. Pour créer un point de terminaison de migration Outlook Anywhere, afin d'effectuer une migration à basculement, commencez par vous [connecter à Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell).

Pour la liste complète des commandes de migration, voir [Cmdlets de déplacement et de migration](/powershell/exchange/).

Dans Exchange Online PowerShell, exécutez les commandes suivantes :

```powershell
$Credentials = Get-Credential
```

Cet exemple utilise la cmdlet [Test-MigrationServerAvailability](/powershell/module/exchange/test-migrationserveravailability) pour obtenir et tester les paramètres de connexion au serveur Exchange local, puis utilise ces paramètres de connexion pour créer le point de terminaison de migration appelé « CutoverEndpoint ».

```powershell
$TSMA = Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress administrator@contoso.com -Credentials $credentials
```

```powershell
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name CutoverEndpoint -ConnectionSettings $TSMA.ConnectionSettings
```

> [!NOTE]
> La cmdlet **New-MigrationEndpoint** peut être utilisée pour spécifier une base de données pour le service à l'aide de l'option **-TargetDatabase**. Sinon, une base de données est affectée de manière aléatoire à partir du site Services ADFS (Active Directory Federation Services) 2.0 où se trouve la boîte aux lettres de gestion.

#### <a name="verify-it-worked"></a>Vérifier que l’opération a fonctionné

Dans Exchange Online PowerShell, exécutez la commande suivante pour afficher des informations sur le point de terminaison de migration « CutoverEndpoint » :

```powershell
Get-MigrationEndpoint CutoverEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*

```

### <a name="step-3-create-the-cutover-migration-batch"></a>Étape 3 : Créez le lot de migration à basculement
<a name="BK_Step3"> </a>

La cmdlet **New-MigrationBatch** d'Exchange Online PowerShell permet de créer un lot pour une migration à basculement. Vous pouvez créer un lot de migration et démarrer automatiquement son traitement en incluant le paramètre _AutoStart_. Vous pouvez également créer un lot de migration, puis démarrer manuellement son traitement par la suite à l'aide de la cmdlet **Start-MigrationBatch**. Cet exemple de code crée un lot de migration appelé « CutoverBatch » et utilise le point de terminaison de migration créé à l'étape précédente.

```powershell
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint -AutoStart
```

Cet exemple de code crée également un lot de migration appelé « CutoverBatch » et utilise le point de terminaison de migration créé à l'étape précédente. Le paramètre  _AutoStart_ n'étant pas inclus, le traitement du lot de migration doit être lancé manuellement sur le tableau de bord de migration ou à l'aide de la cmdlet **Start-MigrationBatch**. Comme indiqué précédemment, il ne peut y avoir qu'un seul lot de migration à basculement à la fois.

```powershell
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint
```

#### <a name="verify-it-worked"></a>Vérifier que l’opération a fonctionné

Pour vérifier que vous avez créé un lot de migration pour une migration à basculement, exécutez la commande suivante dans Exchange Online PowerShell pour afficher des informations sur le nouveau lot de migration :

```powershell
Get-MigrationBatch | Format-List
```

### <a name="step-4-start-the-cutover-migration-batch"></a>Étape 4 : Démarrez le lot de migration à basculement

Pour lancer le lot de migration dans Exchange Online PowerShell, exécutez la commande suivante. Cela crée un lot de migration appelé « CutoverBatch ».

```powershell
Start-MigrationBatch -Identity CutoverBatch
```

#### <a name="verify-it-worked"></a>Vérifier que l’opération a fonctionné

Si le traitement d’un lot de migration a démarré, son état dans le tableau de bord de migration est Synchronisation. Pour vérifier que le traitement d’un lot de migration a commencé à l’aide d’Exchange Online PowerShell, exécutez la commande suivante :

```powershell
Get-MigrationBatch -Identity CutoverBatch |  Format-List Status
```

### <a name="step-5-route-your-email-to-microsoft-365"></a>Étape 5 : Acheminer votre courrier électronique vers Microsoft 365

Les systèmes de messagerie utilisent un enregistrement DNS appelé enregistrement MX pour identifier l'emplacement de remise des messages électroniques. Pendant le processus de migration de la messagerie, votre enregistrement MX pointe vers votre système de messagerie source. Maintenant que la migration de l’e-mail vers Microsoft 365 est terminée, il est temps de pointer votre enregistrement MX vers Microsoft 365. Cela permet de s’assurer que l’e-mail est remis à vos boîtes aux lettres Microsoft 365. En déplaçant l'enregistrement MX, vous pouvez également désactiver votre ancien système de messagerie lorsque vous êtes prêt.

Pour plusieurs fournisseurs DNS, il existe des instructions spécifiques pour modifier votre enregistrement MX. Si votre fournisseur DNS n’est pas inclus, ou si vous souhaitez avoir une idée des instructions générales, [des instructions d’enregistrement MX générales](/microsoft-365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider?view=o365-worldwide#add-an-mx-record-for-email-outlook-exchange-online) sont également fournies.

Il faut compter jusqu'à 72 heures pour que les systèmes de messagerie de vos clients et partenaires reconnaissent l'enregistrement MX modifié. Patientez au moins 72 heures avant de procéder à la tâche suivante : [Étape 6 : Supprimez le lot de migration à basculement](#step-6-delete-the-cutover-migration-batch).

### <a name="step-6-delete-the-cutover-migration-batch"></a>Étape 6 : Supprimez le lot de migration à basculement

Après avoir modifié l'enregistrement MX et vérifié que tout le courrier est routé vers les boîtes aux lettres Microsoft 365, informez les utilisateurs que leur courrier est envoyé vers Microsoft 365. Après cela, vous pouvez supprimer le lot de migration à basculement. Avant de supprimer le lot de migration, vérifiez les points suivants.

- Tous les utilisateurs utilisent des boîtes aux lettres Microsoft 365. Une fois le lot supprimé, le courrier envoyé aux boîtes aux lettres locales Exchange Server n’est pas copié dans les boîtes aux lettres Microsoft 365 correspondantes.

- Microsoft 365 boîtes aux lettres ont été synchronisées au moins une fois après que le courrier leur a été envoyé directement. Pour ce faire, assurez-vous que la valeur du dernier fuseau horaire synchronisé pour le lot de migration est plus récente que lorsque le courrier a commencé à être routé directement vers Microsoft 365 boîtes aux lettres.

Pour supprimer le lot de migration « CutoverBatch » dans Exchange Online PowerShell, exécutez la commande suivante :

```powershell
Remove-MigrationBatch -Identity CutoverBatch
```

### <a name="section-7-assign-user-licenses"></a>Section 7 : Attribuez des licences utilisateur

 **Activez Microsoft 365 comptes d’utilisateur pour les comptes migrés en attribuant des licences.** Si vous n'attribuez pas de licence, la boîte aux lettres est désactivée à la fin de la période de grâce (30 jours). Pour attribuer une licence dans le Centre d'administration Microsoft 365, consultez [Affecter ou annuler l’attribution de licences](../admin/manage/assign-licenses-to-users.md).

### <a name="step-8-complete-post-migration-tasks"></a>Étape 8 : Exécutez les tâches post-migration

- **Créer un enregistrement DNS de Autodiscover afin que les utilisateurs puissent facilement accéder à leurs boîtes aux lettres** Une fois toutes les boîtes aux lettres locales migrées vers Microsoft 365, vous pouvez configurer un enregistrement DNS de découverte automatique pour votre organisation Microsoft 365 afin de permettre aux utilisateurs de se connecter facilement à leurs nouvelles boîtes aux lettres Microsoft 365 avec des clients Outlook et mobiles. Ce nouvel enregistrement DNS de découverte automatique doit utiliser le même espace de noms que celui que vous utilisez pour votre organisation Microsoft 365. Par exemple, si votre espace de noms en nuage est nuage.contoso.com, l’enregistrement DNS de découverte automatique que vous devez créer est decouverteautomatique.nuage.contoso.com.

    Si vous conservez votre Exchange Server, vous devez également vous assurer que l’enregistrement CNAME DNS de découverte automatique doit pointer vers Microsoft 365 dans le DNS interne et externe après la migration afin que le client Outlook se connecte à la boîte aux lettres correcte.

    > [!NOTE]
    >  Dans Exchange 2007, Exchange 2010 et Exchange 2013, vous devez également définir  `Set-ClientAccessServer AutodiscoverInternalConnectionURI` sur `Null`.

    Microsoft 365 utilise un enregistrement CNAME pour implémenter le service de découverte automatique pour les clients Outlook et mobiles. L'enregistrement CNAME de découverte automatique doit contenir les informations suivantes :

  - **Alias :** autodiscover

  - **Cible :** autodiscover.outlook.com

    Pour plus d’informations, consultez [Ajouter des enregistrements DNS pour connecter votre domaine](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

- **Désactivez des serveurs Exchange locaux.** Une fois que vous avez vérifié que tous les e-mails sont acheminés directement vers les boîtes aux lettres Microsoft 365 et que vous n’avez plus besoin de gérer votre organisation de messagerie locale ou de ne pas planifier l’implémentation d’une solution d’authentification unique, vous pouvez désinstaller Exchange de vos serveurs et supprimer votre organisation Exchange locale.

    Pour plus d’informations, voir les commandes suivantes :

  - [Modifier ou supprimer Exchange 2010](/previous-versions/office/exchange-server-2010/ee332361(v=exchg.141))

  - [Procédure de suppression d'une organisation Exchange 2007](/previous-versions/office/exchange-server-2007/aa998313(v=exchg.80))

  - [Procédure de désinstallation d'Exchange Server 2003](/previous-versions/tn-archive/bb125110(v=exchg.65))
