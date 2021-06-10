---
title: Utilisation de PowerShell pour effectuer une migration à basculement vers Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.assetid: b468cb4b-a35c-43d3-85bf-65446998af40
description: Découvrez comment utiliser PowerShell pour déplacer le contenu d’un système de courrier source en une seule fois en effectuez une migration à Microsoft 365.
ms.openlocfilehash: 6e59ac4d590208e0faed22e94cabe05601b17f18
ms.sourcegitcommit: 53acc851abf68e2272e75df0856c0e16b0c7e48d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2021
ms.locfileid: "51581057"
---
# <a name="use-powershell-to-perform-a-cutover-migration-to-microsoft-365"></a>Utilisation de PowerShell pour effectuer une migration à basculement vers Microsoft 365

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Vous pouvez migrer le contenu des boîtes aux lettres utilisateur à partir d’un système de messagerie source vers Microsoft 365 en une seule fois à l’aide d’une migration à cutover. Cet article décrit les tâches correspondant à une migration de messagerie à basculement à l'aide d'Exchange Online PowerShell.

En reviewant la rubrique« Ce que vous devez savoir sur une [migration](/Exchange/mailbox-migration/what-to-know-about-a-cutover-migration)de messagerie à Microsoft 365 , vous pouvez obtenir une vue d’ensemble du processus de migration. Lorsque le contenu de cet article vous est familier, utilisez celui-ci pour commencer la migration de boîtes aux lettres d'un système à l'autre.

> [!NOTE]
> Vous pouvez également utiliser le Centre d'administration Exchange pour effectuer la migration à basculement. See [Perform a cutover migration of email to Microsoft 365](/Exchange/mailbox-migration/cutover-migration-to-office-365).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu’il faut savoir avant de commencer

Durée d'exécution estimée de cette tâche : entre 2 et 5 minutes pour créer un lot de migration. Une fois la migration du lot commencée, la durée de l'opération varie en fonction du nombre de boîtes aux lettres incluses dans le lot, de la taille de chacune d'elles et de la capacité réseau disponible. Pour plus d’informations sur les autres facteurs qui affectent le temps de migration des boîtes aux lettres vers Microsoft 365, voir [Performances de migration.](/Exchange/mailbox-migration/office-365-migration-best-practices)

Des autorisations doivent vous être attribuées avant que vous puissiez exécuter cette procédure. Pour connaître les autorisations nécessaires, consultez l'entrée « Migration » dans un tableau de la rubrique [Autorisations des destinataires](/exchange/recipients-permissions-exchange-2013-help).

Pour utiliser les cmdlets Exchange Online PowerShell, vous devez vous connecter et importer les cmdlets dans votre session Windows PowerShell locale. Pour des instructions, voir [Connexion à Exchange Online à l'aide de Remote PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

Pour la liste complète des commandes de migration, voir [Cmdlets de déplacement et de migration](/powershell/exchange/).

## <a name="migration-steps"></a>Étapes de migration

### <a name="step-1-prepare-for-a-cutover-migration"></a>Étape 1 : Préparez une migration à basculement
<a name="BK_Step1"> </a>

- **Ajoutez votre organisation Exchange en tant que domaine accepté de votre Microsoft 365 organisation.** Le service de migration utilise l’adresse SMTP de vos boîtes aux lettres locales pour créer l’ID d’utilisateur Microsoft Online Services et l’adresse e-mail pour les nouvelles boîtes aux lettres Microsoft 365 locales. La migration échoue si votre domaine Exchange n’est pas un domaine accepté ou le domaine principal de votre Microsoft 365 organisation. Pour plus d’informations, [voir Vérifier votre domaine.](../admin/setup/add-domain.md)

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

- **Attribuez à un compte d'utilisateur local les autorisations nécessaires pour accéder aux boîtes aux lettres de votre organisation Exchange.** Le compte d’utilisateur local que vous utilisez pour vous connecter à votre organisation Exchange sur site (également appelée administrateur de migration) doit avoir les autorisations nécessaires pour accéder aux boîtes aux lettres sur site que vous souhaitez migrer vers Microsoft 365. Ce compte d'utilisateur permet de créer un point de terminaison de migration pour votre organisation locale.

    La liste suivante montre les privilèges administratifs requis pour migrer des boîtes aux lettres à l'aide d'une migration à basculement. Trois options sont possibles.

  - L'administrateur de migration doit être membre du groupe **Administrateurs de domaine** dans Active Directory au sein de l'organisation locale.

    Ou

  - L'administrateur de migration doit disposer de l'autorisation **FullAccess** pour chaque boîte aux lettres locale.

    Ou

  - L'administrateur de migration doit disposer de l'autorisation **Receive As** pour la base de données de boîtes aux lettres locale stockant les boîtes aux lettres d'utilisateurs.

- **Désactivez la messagerie unifiée.** Si les boîtes aux lettres locales que vous migrez sont activées pour la messagerie unifiée, vous devez désactiver cette dernière avant de procéder à la migration. Une fois la migration terminée, vous pouvez activer la messagerie unifiée sur les boîtes aux lettres.

- **Groupes de sécurité et délégués** Le service de migration de messagerie ne peut pas détecter si les groupes Active Directory locaux sont des groupes de sécurité ou non, il ne peut donc pas fournir de groupes migrés en tant que groupes de sécurité dans Microsoft 365. Si vous souhaitez avoir des groupes de sécurité dans votre client Microsoft 365, vous devez d’abord mettre en service un groupe de sécurité à messagerie vide dans votre client Microsoft 365 avant de commencer la migration à cutover. En outre, cette méthode de migration déplace uniquement les boîtes aux lettres, les utilisateurs de messagerie, les contacts de messagerie et les groupes à extension messagerie. Si un autre objet Active Directory, tel qu’un utilisateur qui n’est pas migré vers Microsoft 365, est affecté en tant que responsable ou délégué à un objet en cours de migration, il doit être supprimé de l’objet avant la migration.

### <a name="step-2-create-a-migration-endpoint"></a>Étape 2 : Créez un point de terminaison de migration
<a name="BK_Step2"> </a>

Pour migrer correctement le courrier électronique, Microsoft 365 doit se connecter au système de courrier source et communiquer avec celui-là. Pour ce faire, Microsoft 365 un point de terminaison de migration. Pour créer un point de terminaison de migration Outlook Anywhere, afin d'effectuer une migration à basculement, commencez par vous [connecter à Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell).

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
<a name="BK_Step4"> </a>

Pour lancer le lot de migration dans Exchange Online PowerShell, exécutez la commande suivante. Cela crée un lot de migration appelé « CutoverBatch ».

```powershell
Start-MigrationBatch -Identity CutoverBatch
```

#### <a name="verify-it-worked"></a>Vérifier que l’opération a fonctionné

Si le traitement d’un lot de migration a démarré, son état dans le tableau de bord de migration est Synchronisation. Pour vérifier que le traitement d’un lot de migration a commencé à l’aide d’Exchange Online PowerShell, exécutez la commande suivante :

```powershell
Get-MigrationBatch -Identity CutoverBatch |  Format-List Status
```

### <a name="step-5-route-your-email-to-microsoft-365"></a>Étape 5 : Router votre courrier vers Microsoft 365
<a name="BK_Step5"> </a>

Les systèmes de messagerie utilisent un enregistrement DNS appelé enregistrement MX pour identifier l'emplacement de remise des messages électroniques. Pendant le processus de migration de la messagerie, votre enregistrement MX pointe vers votre système de messagerie source. Maintenant que la migration de messagerie vers Microsoft 365 est terminée, il est temps de faire pointer votre enregistrement MX vers Microsoft 365. Cela permet de s’assurer que le courrier électronique est remis à Microsoft 365 boîtes aux lettres. En déplaçant l'enregistrement MX, vous pouvez également désactiver votre ancien système de messagerie lorsque vous êtes prêt.

Pour plusieurs fournisseurs DNS, il existe des instructions spécifiques pour modifier votre enregistrement MX. Si votre fournisseur DNS n’est pas inclus ou si vous souhaitez avoir une idée des instructions générales, des [instructions générales](https://support.office.microsoft.com/article/7b7b075d-79f9-4e37-8a9e-fb60c1d95166#bkmk_add_mx) sur l’enregistrement MX sont également fournies.

Il faut compter jusqu'à 72 heures pour que les systèmes de messagerie de vos clients et partenaires reconnaissent l'enregistrement MX modifié. Patientez au moins 72 heures avant de procéder à la tâche suivante : [Étape 6 : Supprimez le lot de migration à basculement](use-powershell-to-perform-a-cutover-migration-to-microsoft-365.md#Bk_step6).

### <a name="step-6-delete-the-cutover-migration-batch"></a>Étape 6 : Supprimez le lot de migration à basculement
<a name="Bk_step6"> </a>

Après avoir changé l’enregistrement MX et vérifié que tous les messages électroniques sont acheminés vers des boîtes aux lettres Microsoft 365, informez les utilisateurs que leur courrier va Microsoft 365. Après cela, vous pouvez supprimer le lot de migration à basculement. Avant de supprimer le lot de migration, vérifiez les points suivants.

- Tous les utilisateurs utilisent Microsoft 365 boîtes aux lettres. Une fois le lot supprimé, le courrier électronique envoyé aux boîtes aux lettres sur l’Exchange Server local n’est pas copié dans les boîtes aux lettres Microsoft 365 correspondantes.

- Microsoft 365 boîtes aux lettres ont été synchronisées au moins une fois après que le courrier leur a été envoyé directement. Pour ce faire, assurez-vous que la valeur de la zone Heure de la dernière synchronisation pour le lot de migration est plus récente que le moment où le courrier a commencé à être acheminé directement vers Microsoft 365 boîtes aux lettres.

Pour supprimer le lot de migration « CutoverBatch » dans Exchange Online PowerShell, exécutez la commande suivante :

```powershell
Remove-MigrationBatch -Identity CutoverBatch
```

### <a name="section-7-assign-user-licenses"></a>Section 7 : Attribuez des licences utilisateur
<a name="BK_Step7"> </a>

 **Activez Microsoft 365 comptes d’utilisateur pour les comptes migrés en attribuant des licences.** Si vous n'attribuez pas de licence, la boîte aux lettres est désactivée à la fin de la période de grâce (30 jours). Pour attribuer une licence dans le centre d Microsoft 365'administration, voir Attribuer ou [désattribuer des licences.](../admin/manage/assign-licenses-to-users.md)

### <a name="step-8-complete-post-migration-tasks"></a>Étape 8 : Exécutez les tâches post-migration
<a name="BK_Step8"> </a>

- **Créer un enregistrement DNS de Autodiscover afin que les utilisateurs puissent facilement accéder à leurs boîtes aux lettres** Une fois toutes les boîtes aux lettres sur site migrées vers Microsoft 365, vous pouvez configurer un enregistrement DNS de découverte automatique pour votre organisation Microsoft 365 afin de permettre aux utilisateurs de se connecter facilement à leurs nouvelles boîtes aux lettres Microsoft 365 avec des clients mobiles et Outlook. Ce nouvel enregistrement DNS de découverte automatique doit utiliser le même espace de noms que celui que vous utilisez pour Microsoft 365 organisation. Par exemple, si votre espace de noms en nuage est nuage.contoso.com, l’enregistrement DNS de découverte automatique que vous devez créer est decouverteautomatique.nuage.contoso.com.

    Si vous conservez votre Exchange Server, vous devez également vous assurer que l’enregistrement CNAME DNS de découverte automatique doit pointer vers Microsoft 365 à la fois dans le DNS interne et externe après la migration afin que le client Outlook se connecte à la boîte aux lettres correcte.

    > [!NOTE]
    >  Dans Exchange 2007, Exchange 2010 et Exchange 2013, vous devez également définir  `Set-ClientAccessServer AutodiscoverInternalConnectionURI` sur `Null`.

    Microsoft 365 utilise un enregistrement CNAME pour implémenter le service de découverte automatique pour Outlook clients mobiles et mobiles. L'enregistrement CNAME de découverte automatique doit contenir les informations suivantes :

  - **Alias :** autodiscover

  - **Cible :** autodiscover.outlook.com

    Pour plus d’informations, voir [Ajouter des enregistrements DNS pour connecter votre domaine.](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md)

- **Désactivez des serveurs Exchange locaux.** Une fois que vous avez vérifié que tous les messages électroniques sont acheminés directement vers les boîtes aux lettres Microsoft 365 et que vous n’avez plus besoin de gérer votre organisation de messagerie sur site ou que vous ne prévoyez pas d’implémenter une solution d' sign-on (SSO) unique, vous pouvez désinstaller les Exchange de vos serveurs et supprimer votre organisation Exchange sur site.

    Pour plus d’informations, voir les commandes suivantes :

  - [Modifier ou supprimer Exchange 2010](/previous-versions/office/exchange-server-2010/ee332361(v=exchg.141))

  - [Procédure de suppression d'une organisation Exchange 2007](/previous-versions/office/exchange-server-2007/aa998313(v=exchg.80))

  - [Procédure de désinstallation d'Exchange Server 2003](/previous-versions/tn-archive/bb125110(v=exchg.65))