---
title: Migration de boîtes aux lettres inter-clients
description: Comment déplacer des boîtes aux lettres entre Microsoft 365 ou Office 365 client.
ms.author: josephd
author: JoeDavies-MSFT
manager: Laurawi
ms.prod: microsoft-365-enterprise
ms.topic: article
f1.keywords:
- NOCSH
ms.date: 09/21/2020
ms.reviewer: georgiah
ms.custom:
- it-pro
ms.collection:
- M365-subscription-management
ms.openlocfilehash: 40ec3887cd37ddb412df3ae78300c1f9e9c60ecc
ms.sourcegitcommit: 4d26a57c37ff7efbb8d235452c78498b06a59714
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/22/2021
ms.locfileid: "53053046"
---
# <a name="cross-tenant-mailbox-migration-preview"></a>Migration de boîtes aux lettres entre locataires (prévisualisation)

Auparavant, lorsqu’un client Exchange Online devait déplacer des boîtes aux lettres vers un autre client dans le même service Exchange Online, il devait les déboarder complètement sur site, puis les intégrer à un nouveau client. Grâce à la nouvelle fonctionnalité de migration de boîtes aux lettres entre les locataires, les administrateurs client des locataires source et cible peuvent déplacer des boîtes aux lettres entre les locataires avec des dépendances d’infrastructure minimales dans leurs systèmes locaux. Cela permet de supprimer la nécessité d’intégrer et d’intégrer des boîtes aux lettres.

En commun, lors de fusions ou de dédessons, vous avez besoin de la possibilité de déplacer des utilisateurs et du contenu vers un nouveau client. Lorsque l’administrateur client cible exécute le déplacement, il s’agit d’un déplacement pull, semblable à l’intégration sur site aux migrations d’intégration cloud.

Les déplacements de boîtes aux lettres inter-clients Exchange sont entièrement libre-service par les administrateurs clients, à l’aide d’interfaces connues qui peuvent être scriptées dans les flux de travail plus volumineux nécessaires à la transition des utilisateurs vers leur nouvelle organisation. Les administrateurs peuvent utiliser la cmdlet, disponible via le rôle de gestion Déplacer des boîtes aux lettres, pour exécuter des déplacements `New-MigrationBatch` entre les locataires. Le processus de déplacement inclut les vérifications d’autorisation du client lors de la synchronisation et de la finalisation des boîtes aux lettres. 
 
Les utilisateurs qui migrent doivent être présents dans le système d’Exchange Online client cible en tant que MailUsers, marqués avec des attributs spécifiques pour permettre les déplacements entre clients. Les déplacements du système échouent pour les utilisateurs qui ne sont pas correctement configurer dans le client cible.  

Lorsque les déplacements sont terminés, la boîte aux lettres système source est convertie en MailUser et l’adresse cible (affichée sous la marque ExternalEmailAddress dans Exchange) est estampillée avec l’adresse de routage vers le client de destination. Ce processus laisse l’utilisateur mailuser hérité dans le client source et autorise une période de coexistence et de routage du courrier. Lorsque les processus d’entreprise le permettent, le client source peut supprimer la source MailUser ou les convertir en contact de messagerie. 

Les migrations Exchange boîtes aux lettres entre les locataires sont uniquement pris en charge pour les locataires hybrides ou en nuage, ou pour n’importe quelle combinaison des deux.

Cet article décrit le processus de déplacement de boîtes aux lettres entre les locataires et fournit des instructions sur la préparation des locataires sources et cibles pour le déplacement de contenu.  

## <a name="preparing-source-and-target-tenants"></a>Préparation des locataires sources et cibles

La fonctionnalité de migration de boîtes aux lettres Exchange client nécessite une autorisation et une portée pour les migrations entre les locataires. À l’aide de l’application Azure Enterprise et des solutions de stockage de coffre de clés, les administrateurs clients sont désormais habilités à gérer à la fois l’autorisation et l’portée des migrations de boîtes aux lettres Exchange Online d’un client à un autre. Les déplacements de boîtes aux lettres entre locataires prend en charge un modèle d’invitation et de consentement pour établir une application Azure Active Directory (Azure AD) utilisée pour l’authentification entre une paire de locataires. Des composants supplémentaires tels qu’une relation organisationnelle et un point de terminaison de migration sont également requis.

Cette section n’inclut pas les étapes spécifiques requises pour préparer les objets utilisateur MailUser dans le répertoire cible, ni l’exemple de commande pour envoyer un lot de migration. Pour plus [d’informations, voir Préparer](#prepare-target-user-objects-for-migration) les objets utilisateur cibles pour la migration.

## <a name="prerequisites"></a>Conditions préalables

La fonctionnalité de déplacement de boîtes aux lettres entre clients nécessite [Azure Key Vault](/azure/key-vault/basic-concepts) pour établir une application Azure propre à une paire de clients afin de stocker et d’accéder en toute sécurité au certificat/clé secrète utilisé pour authentifier et autoriser la migration de boîtes aux lettres d’un client à l’autre, supprimant ainsi toutes les conditions requises pour partager des certificats/clés secrètes entre les clients. 

Avant de commencer, assurez-vous que vous avez les autorisations nécessaires pour exécuter les scripts de déploiement afin de configurer Azure Key Vault, l’application de déplacement de boîte aux lettres, le point de terminaison de migration EXO et la relation d’organisation EXO. En règle générale, l’administrateur général est autorisé à effectuer toutes les étapes de configuration.

En outre, les groupes de sécurité à messagerie dans le client source sont requis avant l’exécution de l’installation. Ces groupes sont utilisés pour cibler la liste des boîtes aux lettres qui peuvent passer du client source (ou parfois appelé ressource) au client cible. Cela permet à l’administrateur client source de restreindre ou d’étendue l’ensemble spécifique de boîtes aux lettres qui doivent être déplacées, ce qui empêche la migration des utilisateurs non voulus. Les groupes imbrmbrés ne sont pas pris en charge.

Vous devrez également communiquer avec votre société partenaire de confiance (avec laquelle vous déplacerez des boîtes aux lettres) pour obtenir leur ID Microsoft 365 client approuvé. Cet ID de client est utilisé dans le champ Relation `DomainName` d’organisation.

Pour obtenir l’ID de locataire d’un abonnement, connectez-vous au Centre d’administration Microsoft 365 puis allez à [https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties) . Cliquez sur l’icône de copie de la propriété ID de client pour la copier dans le Presse-papiers.

Voici comment fonctionne le processus.

:::image type="content" source="../media/tenant-to-tenant-mailbox-move/prepare-tenants-flow.png" alt-text="Préparation du client pour la migration de boîtes aux lettres.":::

[Voir une version plus grande de cette image.](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/tenant-to-tenant-mailbox-move/prepare-tenants-flow.png)

<!--
[![Tenant preparation for mailbox migration](../media/tenant-to-tenant-mailbox-move/prepare-tenants-flow.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/tenant-to-tenant-mailbox-move/prepare-tenants-flow.png)
--> 

### <a name="prepare-tenants"></a>Préparer les locataires

À un niveau élevé, les actions de configuration suivantes ont lieu lors de l’exécution des scripts d’installation.

Préparez le client cible :

1. Si un groupe de ressources Azure existant n’est pas fourni, un nouveau groupe de ressources est créé (SCRIPT).
2. Si un coffre de clés existant n’est pas fourni, un nouveau coffre est créé (SCRIPT).
3. Une nouvelle stratégie d’accès est créée pour l’application Office 365 Exchange Online migration de boîtes aux lettres (SCRIPT).
4. Un nouveau certificat est créé (ou existant, s’il est spécifié) pour contenir la question secrète dans l’application de migration (SCRIPT).
5. Une nouvelle application Azure AD est créée (SCRIPT).
6. Le certificat/la question secrète est téléchargé vers l’application de migration (SCRIPT).
7. Les autorisations de migration de boîtes aux lettres sont affectées à l’application (SCRIPT).
8. Le script de déploiement s’interrompt jusqu’à ce que l’administrateur cible consente à sa propre application (SCRIPT).
9. L’administrateur client cible consent aux autorisations accordées à l’application (MANUAL).
10. Une relation d’organisation est créée avec le client cible (SCRIPT).
11. Un point de terminaison de migration est créé pour tirer les boîtes aux lettres vers le client cible (SCRIPT).

Préparez le client source :

1. L’administrateur client source accepte le consentement à l’invitation de l’application de migration de boîtes aux lettres à partir du client cible (MANUAL).
2. L’administrateur client source crée un groupe de sécurité à messagerie dans son client pour contenir la liste des boîtes aux lettres autorisées à être déplacées par l’application de migration (MANUAL).
3. Une relation d’organisation est créée avec le client cible en spécifiant que l’application de migration de boîte aux lettres doit être utilisée pour la vérification OAuth afin d’accepter la demande de déplacement (SCRIPT).

#### <a name="step-by-step-instructions-for-the-target-tenant-admin"></a>Instructions pas à pas pour l’administrateur client cible

1. Téléchargez le script SetupCrossTenantRelationshipForTargetTenant.ps1 pour la configuration du client cible à partir du [référentiel GitHub.](https://github.com/microsoft/cross-tenant/releases/tag/Preview) 
2. Enregistrez le script (SetupCrossTenantRelationshipForTargetTenant.ps1) sur l’ordinateur à partir duquel vous allez exécuter le script.
3. Créez une connexion PowerShell distante au client Exchange Online cible. Là encore, assurez-vous que vous avez les autorisations nécessaires pour exécuter les scripts de déploiement afin de configurer le certificat et le stockage Azure Key Vault, l’application de déplacement de boîte aux lettres, le point de terminaison de migration EXO et la relation d’organisation EXO.
4. Modifiez le répertoire du dossier de fichiers en emplacement de script ou vérifiez que le script est actuellement enregistré à l’emplacement actuellement dans votre session PowerShell distante.
5. Exécutez le script avec les valeurs et paramètres suivants.

    | Paramètre | Valeur | Obligatoire ou facultatif
    |---------------------------------------------|-----------------|--------------|
    | -TargetTenantDomain                         | Domaine client cible, tel que fabrikam \. onmicrosoft.com. | Obligatoire |
    | -ResourceTenantDomain                       | Domaine client source, tel que contoso \. onmicrosoft.com. | Obligatoire |
    | -ResourceTenantAdminEmail                   | Adresse de messagerie de l’administrateur client source. Il s’agit de l’administrateur client source qui consentira à l’utilisation de l’application de migration de boîte aux lettres envoyée par l’administrateur cible. Il s’agit de l’administrateur qui recevra l’invitation par courrier électronique pour l’application. | Obligatoire |
    | -ResourceTenantId                           | ID d’organisation client source (GUID). | Obligatoire |
    | -SubscriptionId                             | L’abonnement Azure à utiliser pour créer des ressources. | Obligatoire |
    | -ResourceGroup                              | Nom du groupe de ressources Azure qui contient ou contiendra le coffre de clés. | Obligatoire |
    | -KeyVaultName                               | Instance Azure Key Vault qui stockera votre certificat/clé secrète d’application de migration de boîte aux lettres. | Obligatoire |
    | -CertificateName                            | Nom du certificat lors de la génération ou de la recherche de certificat dans le coffre de clés. | Obligatoire |
    | -CertificateSubject                         | Nom d’objet du certificat Azure Key Vault, tel que CN=contoso_fabrikam. | Obligatoire |
    | -AzureResourceLocation                      | Emplacement du groupe de ressources Azure et du coffre de clés. | Obligatoire |
    | -ExistingApplicationId                      | Application de migration de messagerie à utiliser si une application a déjà été créée. | Facultatif |
    | -AzureAppPermissions                        | Autorisations requises pour l’application de migration de boîte aux lettres, telles que Exchange ou MSGraph (Exchange pour le déplacement de boîtes aux lettres, MSGraph pour l’utilisation de cette application pour envoyer une invitation de lien de consentement au client de ressource). | Obligatoire |
    | -UseAppAndCertGeneratedForSendingInvitation | Paramètre d’utilisation de l’application créée pour la migration à utiliser pour envoyer une invitation de lien de consentement à l’administrateur client source. S’il n’est pas présent, les informations d’identification de l’administrateur cible sont invités à se connecter au gestionnaire d’invitation Azure et à envoyer l’invitation en tant qu’administrateur cible. | Facultatif |
    | -KeyVaultAuditStorageAccountName            | Compte de stockage dans lequel les journaux d’audit du coffre de clés sont stockés. | Facultatif |
    | -KeyVaultAuditStorageResourceGroup          | Groupe de ressources qui contient le compte de stockage pour le stockage des journaux d’audit du coffre de clés. | Facultatif |
    ||||

    >[!Note]
    > Assurez-vous que vous avez installé le module Azure AD PowerShell avant d’exécutez les scripts. Reportez-vous ![ ici pour ](/powershell/azure/install-az-ps?view=azps-5.1.0) les étapes d’installation

6. Le script s’interrompt et vous demande d’accepter ou d’accepter l’application Exchange migration de boîtes aux lettres qui a été créée au cours de ce processus. Voici un exemple.

    ```powershell
    PS C:\PowerShell\> # Note: the below User.Invite.All permission is optional, and will only be used to retrieve access token to send invitation email to source tenant
    PS C:\PowerShell\> .\SetupCrossTenantRelationshipForTargetTenant.ps1 -ResourceTenantDomain contoso.onmicrosoft.com -ResourceTenantAdminEmail admin@contoso.onmicrosoft.com -TargetTenantDomain fabrikam.onmicrosoft.com -ResourceTenantId ksagjid39-ede2-4d2c-98ae-874709325b00 -SubscriptionId e4ssd05d-a327-49ss-849a-sd0932439023 -ResourceGroup "Cross-TenantMoves" -KeyVaultName "Cross-TenantMovesVault" -CertificateName "Contoso-Fabrikam-cert" -CertificateSubject "CN=Contoso_Fabrikam" -AzureResourceLocation "Brazil Southeast" -AzureAppPermissions Exchange, MSGraph -UseAppAndCertGeneratedForSendingInvitation -KeyVaultAuditStorageAccountName "t2tstorageaccount" -KeyVaultAuditStorageResourceGroup "Demo"

    cmdlet Get-Credential at command pipeline position 1
    Supply values for the following parameters:
    Credential
    Setting up key vault in the fabrikam.onmicrosoft.com tenant

    Name                                     Account                                 SubscriptionName                        Environment                             TenantId
        ----                                     -------                                 ----------------                        -----------                             --------
    Pay-As-You-Go (ewe23423-a3327-34232-343... Admin@fabrikam... Pay-As-You-Go                           AzureCloud                              dsad938432-dd8e-s9034-bf9a-83984293n43
    Auditing setup successfully for Cross-TenantMovesVault
    Exchange application given access to KeyVault Cross-TenantMovesVault
    Application fabrikam_Friends_contoso_2520 created successfully in fabrikam.onmicrosoft.com tenant with following permissions. MSGraph - User.Invite.All. Exchange - Mailbox.Migration
    Admin consent URI for fabrikam.onmicrosoft.com tenant admin is -
    https://login.microsoftonline.com/fabrikam.onmicrosoft.com/adminconsent?client_id=6fea6ere-0dwe-404d-ad35-c71a15cers5c&redirect_uri=https://office.com
    Admin consent URI for contoso.onmicrosoft.com tenant admin is -
    https://login.microsoftonline.com/contoso.onmicrosoft.com/adminconsent?client_id=6fea6ssd-0753-404d-wer5-c71a154d675c&redirect_uri=https://office.com
    Application details to be registered in organization relationship: ApplicationId: [ 6fes8en4-sjo3-406d-ad35-sldkfjiew993 ]. KeyVault secret Id: [ https://cross-tenantmovesvault.vault.azure.net:443/certificates/Contoso-Fabrikam-cert/ksdfj843nt8476h84c288c5a3fb8ec5fdb08 ]. These values are available in variables $AppId and $CertificateId respectively
    Please consent to the application for fabrikam.onmicrosoft.com before sending invitation to admin@contoso.onmicrosoft.com:
    ```  

7. Une URL s’affiche dans la session PowerShell distante. Copiez le lien fourni pour le consentement de votre client et collez-le dans un navigateur Web.

8. Connectez-vous avec vos informations d’identification d’administrateur global. Lorsque l’écran suivant est présenté, sélectionnez **Accepter**.

    :::image type="content" source="../media/tenant-to-tenant-mailbox-move/permissions-requested-dialog.png" alt-text="Boîte de dialogue Accepter les autorisations":::

9. Revenir à la session PowerShell distante et accéder à Entrée pour continuer.

10. Le script configure les objets d’installation restants. Voici un exemple.

    ```powershell
    Successfully sent invitation to admin@contoso.onmicrosoft.com
    Setting up exchange components on target tenant: fabrikam.onmicrosoft.com
    MigrationEndpoint created in fabrikam.onmicrosoft.com for target contoso.onmicrosoft.com
    Exchange setup complete. Migration endpoint details are available in $MigrationEndpoint variable
    ```

La configuration de l’administrateur cible est maintenant terminée !

#### <a name="step-by-step-instructions-for-the-source-tenant-admin"></a>Instructions pas à pas pour l’administrateur client source

1.  Connectez-vous à votre boîte aux lettres en tant que -ResourceTenantAdminEmail spécifié par l’administrateur cible lors de sa configuration. Recherchez l’invitation par courrier électronique à partir du client cible, puis sélectionnez **Prise en main** bouton.

    :::image type="content" source="../media/tenant-to-tenant-mailbox-move/invited-by-target-tenant.png" alt-text="Boîte de dialogue Vous avez été invité":::

2. Sélectionnez **Accepter** pour accepter l’invitation.

    :::image type="content" source="../media/tenant-to-tenant-mailbox-move/permissions-requested-accept.png" alt-text="Boîte de dialogue pour accepter les autorisations":::

   > [!NOTE]
   > Si vous ne recevez pas cet e-mail ou si vous ne le trouvez pas, l’administrateur client cible a reçu une URL directe qui peut vous être fournie pour accepter l’invitation. L’URL doit être dans la transcription de la session PowerShell distante de l’administrateur client cible.

3. Dans la session Centre d’administration Microsoft 365 ou une session PowerShell distante, créez un ou plusieurs groupes de sécurité à messagerie pour contrôler la liste des boîtes aux lettres autorisées par le client cible à tirer (déplacer) du client source vers le client cible. Vous n’avez pas besoin de remplir ce groupe à l’avance, mais au moins un groupe doit être fourni pour exécuter les étapes de configuration (script). Les groupes d’imbrouillement ne sont pas pris en charge. 

4. Téléchargez le script SetupCrossTenantRelationshipForResourceTenant.ps1 pour la configuration du client source à partir du GitHub de données ici [https://github.com/microsoft/cross-tenant/releases/tag/Preview](https://github.com/microsoft/cross-tenant/releases/tag/Preview) : 

5. Créez une connexion PowerShell distante au client source avec vos autorisations Exchange administrateur. Les autorisations d’administrateur global ne sont pas nécessaires pour configurer le client source, uniquement le client cible en raison du processus de création d’application Azure.

6. Modifiez le répertoire vers l’emplacement du script ou vérifiez que le script est actuellement enregistré à l’emplacement actuellement dans votre session PowerShell distante.

7. Exécutez le script avec les valeurs et paramètres requis suivants.

    | Paramètre | Valeur |
    |-----|------|
    | -SourceMailboxMovePublishedScopes | Groupe de sécurité à messagerie créé par le client source pour les identités/boîtes aux lettres qui sont dans l’étendue de la migration. |
    | -ResourceTenantDomain | Nom de domaine du client source, tel que contoso \. onmicrosoft.com. |
    | -ApplicationId | ID d’application Azure (GUID) de l’application utilisée pour la migration. ID d’application disponible via votre portail Azure (Azure AD, Enterprise Applications, nom de l’application, ID d’application) ou inclus dans votre courrier électronique d’invitation.  |
    | -TargetTenantDomain | Nom de domaine du client cible, tel que fabrikam \. onmicrosoft.com. |
    | -TargetTenantId | ID de client du client cible. Par exemple, l’ID de client Azure AD de contoso \. onmicrosoft.com client. |
    |||

    Voici un exemple.
    ```powershell
    SetupCrossTenantRelationshipForResourceTenant.ps1 -SourceMailboxMovePublishedScopes "MigScope","MyGroup" -ResourceTenantDomain contoso.onmicrosoft.com -TargetTenantDomain fabrikam.onmicrosoft.com -ApplicationId sdf5e87sa-0753-dd88-ad35-c71a15cs8e44c -TargetTenantId 4sdkfo933-3904-sd93-bf9a-sdi39402834
    Exchange setup complete.

    ```

La configuration de l’administrateur source est maintenant terminée !

### <a name="verify-setup"></a>Vérifier la configuration

Vérifiez que les relations d’organisation dans les clients source et cible et le point de terminaison de migration dans la cible ont été correctement créées.

#### <a name="target-tenant"></a>Client cible

**Relation organisationnelle**

Vérifiez que l’objet relation organisationnelle a été créé et configuré avec cette commande.

```powershell
Get-OrganizationRelationship <source tenant organization name> | fl name, DomainNames, MailboxMoveEnabled, MailboxMoveCapability
```
Voici un exemple :

```powershell
PS C:\PowerShell\> Get-OrganizationRelationship fabrikam_contoso_1178 | fl name, DomainNames, MailboxMoveEnabled, MailboxMoveCapability

Name                  : fabrikam_contoso_1123
DomainNames           : {sd0933me9f-9304-s903-s093-s093mfi903m4}
MailboxMoveEnabled    : True
MailboxMoveCapability : Inbound

```

**Point de terminaison de migration**

Vérifiez que l’objet de point de terminaison de migration a été créé et configuré avec cette commande.

```powershell
Get-MigrationEndpoint "<fabrikam_contoso_1123> | fl Identity, RemoteTenant, ApplicationId, AppSecretKeyVaultUrl
```

Voici un exemple.

```powershell
PS C:\PowerShell\> Get-MigrationEndpoint fabrikam_contoso_1123 | fl Identity, RemoteTenant, ApplicationId, AppSecretKeyVaultUrl


Identity             : fabrikam_contoso_1123
RemoteTenant         : contoso.onmicrosoft.com
ApplicationId        : s93mf93-das9-dq24-dq234-dada9033904m
AppSecretKeyVaultUrl : https://cross-tenantmyvaultformoves.vault.azure.net:443/certificates/Contoso-Fabrikam-cert/ae79348mx94384c288c5a3dfsioepw308

```

#### <a name="source-tenant"></a>Client source

**Relation organisationnelle**

Vérifiez que l’objet relation organisationnelle a été créé et configuré avec cette commande.

```powershell
Get-OrganizationRelationship | fl name, MailboxMoveEnabled, MailboxMoveCapability, MailboxMovePublishedScopes, OAuthApplicationId
```

Voici un exemple.

```powershell
PS C:\PowerShell\> Get-OrganizationRelationship | fl name, MailboxMoveEnabled, MailboxMoveCapability, MailboxMovePublishedScopes, OAuthApplicationId


Name                       : fabrikam_contoso_001
MailboxMoveEnabled         : True
MailboxMoveCapability      : RemoteOutbound
MailboxMovePublishedScopes : {MigScope}
OAuthApplicationId         : sd9890342-3243-3242-fe3w2-fsdade93m0
```

#### <a name="verify-setup-script"></a>Vérifier le script d’installation

Si vous recevez des erreurs lors de la configuration des locataires source ou cible, vous pouvez exécuter le script VerifySetup.ps1 situé sur [GitHub](https://github.com/microsoft/cross-tenant/releases/tag/Preview) et passer en revue la sortie.

Voici un exemple d’exécution de VerifySetup.ps1 sur le client cible :

```powershell
VerifySetup.ps1 -PartnerTenantId <SourceTenantId> -ApplicationId <AADApplicationId> -ApplicationKeyVaultUrl <appKeyVaultUrl> -PartnerTenantDomain <PartnerTenantDomain> -Verbose
```

Voici un exemple d'VerifySetup.ps1 sur le client source :

```powershell
VerifySetup.ps1 -PartnerTenantId <TargetTenantId> -ApplicationId <AADApplicationId>
```

### <a name="move-mailboxes-back-to-the-original-source"></a>Déplacer les boîtes aux lettres vers la source d’origine

Si un déplacement de boîte aux lettres vers le client source d’origine est nécessaire, le même ensemble d’étapes et de scripts devra être exécuté dans les nouveaux locataires source et cible. L’objet Relation d’organisation existant sera mis à jour ou mis à jour, et non recréé.

## <a name="prepare-target-user-objects-for-migration"></a>Préparer les objets utilisateur cibles pour la migration

Les utilisateurs qui migrent doivent être présents dans le client cible et le système Exchange Online (en tant que MailUsers) marqués avec des attributs spécifiques pour activer les déplacements entre clients. Les déplacements du système échouent pour les utilisateurs qui ne sont pas correctement configurer dans le client cible. La section suivante détaille les conditions requises pour l’objet MailUser pour le client cible.

### <a name="prerequisites"></a>Conditions préalables
  
Vous devez vous assurer que les objets et attributs suivants sont définies dans l’organisation cible.  

1. Pour toute boîte aux lettres qui se déplace à partir d’une organisation source, vous devez mettre en service un objet MailUser dans l’organisation cible : 

   - L’utilisateur de messagerie cible doit avoir les attributs de la boîte aux lettres source ou affectés avec le nouvel objet User :
      - ExchangeGUID (flux direct de la source à la cible) : le GUID de boîte aux lettres doit correspondre. Le processus de déplacement ne se poursuit pas s’il n’est pas présent sur l’objet cible. 
      - ArchiveGUID (flux direct de la source à la cible) : le GUID d’archivage doit correspondre. Le processus de déplacement ne se poursuit pas s’il n’est pas présent sur l’objet cible. (Cette demande est requise uniquement si la boîte aux lettres source est activée pour l’archivage). 
      - LegacyExchangeDN (flow as proxyAddress, « x500: « ) : LegacyExchangeDN doit être présent sur la cible MailUser en tant que <LegacyExchangeDN> x500 : proxyAddress. Le processus de déplacement ne se poursuit pas s’il n’est pas présent sur l’objet cible. 
      - UserPrincipalName : UPN s’alignera sur la nouvelle identité ou la société cible de l’utilisateur (par exemple, user@northwindtraders.onmicrosoft.com). 
      - Adresse SMTP principale : l’adresse SMTP principale s’alignera sur la société NEW de l’utilisateur (par exemple, user@northwind.com). 
      - TargetAddress/ExternalEmailAddress : MailUser référencera la boîte aux lettres actuelle de l’utilisateur hébergée dans le client source (par exemple, user@contoso.onmicrosoft.com). Lors de l’affectation de cette valeur, vérifiez que vous avez/attribuez également PrimarySMTPAddress, sinon cette valeur définira PrimarySMTPAddress qui provoquera des échecs de déplacement. 
      - Vous ne pouvez pas ajouter des adresses proxy smtp héritées à partir de la boîte aux lettres source à la cible MailUser. Par exemple, vous ne pouvez pas conserver contoso.com sur l’fabrikam.onmicrosoft.com des objets client). Les domaines sont associés à un seul client Azure AD Exchange Online client.
 
     Exemple **d’objet** MailUser cible :
 
     | Attribut             | Valeur                                                                                                                    |
     |-----------------------|--------------------------------------------------------------------------------------------------------------------------|
     | Alias                 | LaraN                                                                                                                    |
     | RecipientType         | MailUser                                                                                                                 |
     | RecipientTypeDetails  | MailUser                                                                                                                 |
     | UserPrincipalName     | LaraN@northwintraders.onmicrosoft.com                                                                                    |
     | PrimarySmtpAddress    | Lara.Newton@northwind.com                                                                                                |
     | ExternalEmailAddress  | SMTP:LaraN@contoso.onmicrosoft.com                                                                                       |
     | ExchangeGuid          | 1ec059c7-8396-4d0b-af4e-d6bd4c12a8d8                                                                                     |
     | LegacyExchangeDN      | /o=First Organization/ou=Exchange Administrative Group                                                                   |
     |                       | (FYDIBOHF23SPDLT)/cn=Recipients/cn=74e5385fce4b46d19006876949855035Lara                                                  |
     | EmailAddresses        | x500:/o=First Organization/ou=Exchange Administrative Group (FYDIBOHF23SPDLT)/cn=Recipients/cn=d11ec1a2cacd4f81858c8190  |
     |                       | 7273f1f9-Lara                                                                                                            |
     |                       | smtp:LaraN@northwindtraders.onmicrosoft.com                                                                              |
     |                       | SMTP:Lara.Newton@northwind.com                                                                                           |
     |||

     Exemple **d’objet mailbox** source :

     | Attribut             | Valeur                                                                    |
     |-----------------------|--------------------------------------------------------------------------|
     | Alias                 | LaraN                                                                    |
     | RecipientType         | UserMailbox                                                              |
     | RecipientTypeDetails  | UserMailbox                                                              |
     | UserPrincipalName     | LaraN@contoso.onmicrosoft.com                                            |
     | PrimarySmtpAddress    | Lara.Newton@contoso.com                                                  |
     | ExchangeGuid          | 1ec059c7-8396-4d0b-af4e-d6bd4c12a8d8                                     |
     | LegacyExchangeDN      | /o=First Organization/ou=Exchange Administrative Group                   |
     |                       | (FYDIBOHF23SPDLT)/cn=Recipients/cn=d11ec1a2cacd4f81858c81907273f1f9Lara  |
     | EmailAddresses        | smtp:LaraN@contoso.onmicrosoft.com 
     |                       | SMTP:Lara.Newton@contoso.com          |
     |||

   - Des attributs supplémentaires peuvent déjà être inclus dans Exchange’écriture hybride. Si ce n’est pas le cas, elles doivent être incluses. 
   - msExchBlockedSendersHash : écrit en ligne les données d’expéditeurs sécurisés et bloqués des clients vers Active Directory local.
   - msExchSafeRecipientsHash : écrit en ligne les données d’expéditeurs sécurisés et bloqués des clients vers Active Directory local.
   - msExchSafeSendersHash : écrit en ligne les données d’expéditeurs sécurisés et bloqués des clients vers Active Directory local.

2. Si la boîte aux lettres source est sur LitigationHold et que la taille des éléments récupérables de la boîte aux lettres source est supérieure à la taille par défaut de notre base de données (30 Go), les déplacements ne se déroulent pas, car le quota cible est inférieur à la taille de boîte aux lettres source. Vous pouvez mettre à jour l’objet MailUser cible pour faire passer les indicateurs de boîte aux lettres ELC de l’environnement source à la cible, ce qui déclenche le développement du quota de MailUser par le système cible à 100 Go, ce qui permet le déplacement vers la cible. Ces instructions ne fonctionnent que pour l’identité hybride exécutant Azure AD Connecter, car les commandes pour marquer les indicateurs ELC ne sont pas exposées aux administrateurs client.

    >[!Note]
    > EXEMPLE – EN L’ABSENCE DE GARANTIE<br/>Ce script suppose une connexion à la boîte aux lettres source (pour obtenir les valeurs sources) et à la cible Active Directory sur site (pour marquer l’objet ADUser). Si la source est pour litige ou si la récupération d’élément unique est activée, définissez-la sur le compte de destination.  Cela augmente la taille de benne du compte de destination à 100 Go.

    ```powershell
    $ELCValue = 0 
    if ($source.LitigationHoldEnabled) {$ELCValue = $ELCValue + 8} if ($source.SingleItemRecoveryEnabled) {$ELCValue = $ELCValue + 16} if ($ELCValue -gt 0) {Set-ADUser -Server $domainController -Identity $destination.SamAccountName -Replace @{msExchELCMailboxFlags=$ELCValue}} 
    ```

3. Les locataires cibles non hybrides peuvent modifier le quota sur le dossier Éléments récupérables des mailUsers avant la migration en exécutant la commande suivante pour activer la attente pour litige sur l’objet MailUser et en augmentant le quota à 100 Go : `Set-MailUser -EnableLitigationHoldForMigration $TRUE` Notez que cela ne fonctionne pas pour les locataires dans un mode hybride.

4. Les utilisateurs de l’organisation cible doivent être titulaires d’une licence Exchange Online les abonnements applicables à l’organisation. Vous pouvez appliquer une licence avant le déplacement d’une boîte aux lettres, mais seulement une fois que l’utilisateur de messagerie cible est correctement installé avec ExchangeGUID et les adresses proxy. L’application d’une licence avant l’application d’ExchangeGUID entraîne la mise en service d’une nouvelle boîte aux lettres dans l’organisation cible. 

    > [!Note]
    > Lorsque vous appliquez une licence à un objet Mailbox ou MailUser, toutes les adresses proxy de type SMTP sont nettoyées pour garantir que seuls les domaines vérifiés sont inclus dans le tableau Exchange EmailAddresses. 

5. Vous devez vous assurer que le MailUser cible n’a aucun ExchangeGuid précédent qui ne correspond pas à l’ExchangeGuid source. Cela peut se produire si l’utilisateur à messagerie utilisateur cible a été précédemment titulaire d’une licence Exchange Online et a fourni une boîte aux lettres. Si la cible MailUser a déjà été titulaire d’une licence ExchangeGuid ou qu’elle avait un ExchangeGuid qui ne correspond pas à l’ExchangeGuid source, vous devez effectuer un nettoyage de l’UI de cloud. Pour ces meus cloud, vous pouvez exécuter `Set-User <identity> -PermanentlyClearPreviousMailboxInfo` .  

    > [!Caution]
    > Ce processus est irréversible. Si l’objet possède une boîte aux lettres supprimée (softDeleted), il ne peut pas être restauré après ce point. Une fois effacé, toutefois, vous pouvez synchroniser l’objet ExchangeGuid correct avec l’objet cible et MRS connectera la boîte aux lettres source à la boîte aux lettres cible nouvellement créée. (Référencez le blog EHLO sur le nouveau paramètre.)  

    Recherchez des objets qui étaient auparavant des boîtes aux lettres à l’aide de cette commande.

    ```powershell
    Get-User <identity> | select Name, *recipient* | ft -AutoSize
    ```

    Voici un exemple. 

    ```powershell
    PS demo> get-user John@northwindtraders.com |select name, *recipient*| ft -AutoSize  

    Name        PreviousRecipientTypeDetails     RecipientType RecipientTypeDetails  
    ----       ---------------------------- ------------- --------------------  
    John       UserMailbox                  MailUser      MailUser  
    ```  

    Effacez la boîte aux lettres supprimée (à l’aide de cette commande).

    ```powershell
    Set-User <identity> -PermanentlyClearPreviousMailboxInfo
    ```

    Voici un exemple.

    ```powershell
    PS demo> Set-User John@northwindtraders.com -PermanentlyClearPreviousMailboxInfo Confirm 
    Are you sure you want to perform this action? 
    Delete all existing information about user “John@northwindtraders.com"?. This operation will clear existing values from Previous home MDB and Previous Mailbox GUID of the user. After deletion, reconnecting to the previous mailbox that existed in the cloud will not be possible and any content it had will be unrecoverable PERMANENTLY.  
    Do you want to continue? 
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [?] Help (default is "Y"): Y  
    ```

## <a name="perform-mailbox-migrations"></a>Effectuer des migrations de boîtes aux lettres

Les migrations entre Exchange boîtes aux lettres sont envoyées en tant que lots de migration initiés à partir du client cible. Cela est similaire au mode de travail des lots de migration d’embarquement lors de la migration de Exchange en local vers Microsoft 365. 

### <a name="create-migration-batches"></a>Créer des lots de migration

Voici un exemple de cmdlet de lot de migration pour supprimer les déplacements.

```powershell
New-MigrationBatch -Name T2Tbatch-testforignitedemo -SourceEndpoint target_source_7977 -CSVData ([System.IO.File]::ReadAllBytes('users.csv')) -Autostart -TargetDeliveryDomain targetformoves.onmicrosoft.com -AutoComplete

Identity                   Status  Type               TotalCount
--------                   ------  ----               ----------
T2Tbatch-testforignitedemo Syncing ExchangeRemoteMove 1

```

> [!Note]
> L’adresse de messagerie dans le fichier CSV doit être celle spécifiée dans le client cible, et non le client source.

L’envoi de lot de migration est également pris en charge à partir du nouveau centre d Exchange’administration lorsque vous sélectionnez l’option entre les locataires.

#### <a name="update-on-premises-mailusers"></a>Mettre à jour les mailusers locaux

Une fois que la boîte aux lettres passe de la source à la cible, vous devez vous assurer que les utilisateurs de messagerie locaux, source et cible, sont mis à jour avec la nouvelle adresse cible. Dans les exemples, le targetDeliveryDomain utilisé dans le déplacement **est contoso.onmicrosoft.com**. Mettez à jour les utilisateurs de messagerie avec cette adresse cible.

## <a name="frequently-asked-questions"></a>Questions fréquemment posées

**Devons-nous mettre à jour RemoteMailboxes dans la source sur site après le déplacement ?**

Oui, vous devez mettre à jour la cibleAddress (RemoteRoutingAddress/ExternalEmailAddress) des utilisateurs locaux source lorsque la boîte aux lettres du client source se déplace vers le client cible.  Bien que le routage du courrier puisse suivre les références entre plusieurs utilisateurs de messagerie avec des adresses cibles différentes, les recherches de libre/occupé pour les utilisateurs de messagerie doivent cibler l’emplacement de l’utilisateur de boîte aux lettres. Les recherche de libre/occupé ne pourront pas poursuivre plusieurs redirections. 

**Les réunions Teams-elles migrer entre les locataires ?**  

Les réunions déplacent toutefois l’URL Teams réunion n’est pas mise à jour lorsque les éléments migrent entre les locataires. Étant donné que l’URL n’est pas valide dans le client cible, vous devrez supprimer et recréer Teams réunions.

**Le contenu Teams de conversation migre-t-il entre les locataires ?**  

Non, le contenu Teams de conversation ne migre pas entre les locataires.  

**Comment puis-je voir uniquement les déplacements qui sont des déplacements inter-locataires, et non mes déplacements d’intégration et de off-embarquement ?**

Utilisez le `-flags` paramètre. Voici un exemple.

```powershell
Get-MoveRequest -Flags "CrossTenant"  
```

**Pouvez-vous fournir des exemples de scripts pour copier les attributs utilisés lors des tests ?**

> [!Note]
> EXEMPLE – EN L’ABSENCE DE GARANTIE<br/>Ce script suppose une connexion à la boîte aux lettres source (pour obtenir les valeurs sources) et aux services de domaine Active Directory locaux cibles (pour marquer l’objet ADUser). Si la source est pour litige ou si la récupération d’élément unique est activée, définissez-la sur le compte de destination.  Cela augmente la taille de benne du compte de destination à 100 Go.

```powershell
#Dumps out the test mailboxes from SourceTenant 
#Note, the filter applied on Get-Mailbox is for an attribute set on CustomAttribute1 = "ProjectKermit" 
#These are the ‘target’ users to be moved to the Northwind org tenant #################################################################  
$outFileUsers = "$home\desktop\userstomigrate.txt"
$outFileUsersXML = "$home\desktop\userstomigrate.xml"
#output the test objects 
Get-Mailbox -Filter "CustomAttribute1 -like 'ProjectKermit'" -ResultSize Unlimited | Select-Object -ExpandProperty Alias | Out-File $outFileUsers
$mailboxes = Get-Content $outFileUsers
$mailboxes | ForEach-Object {Get-Mailbox $_} | Select-Object PrimarySMTPAddress,Alias,SamAccountName,FirstName,LastName,DisplayName,Name,ExchangeGuid,ArchiveGuid,LegacyExchangeDn,EmailAddresses | Export-Clixml $outFileUsersXML

################################################################# 
#Copy the file $outfile to the desktop of the target on-premises 
#then run the below to create MEU in Target 
#################################################################  
$mailboxes = Import-Clixml $home\desktop\userstomigrate.xml

foreach ($m in $mailboxes) {
    $organization = "@contoso.onmicrosoft.com"
    $mosi = $m.Alias+$organization
    $Password = [System.Web.Security.Membership]::GeneratePassword(16,4) | ConvertTo-SecureString -AsPlainText -Force
    $x500 = "x500:" +$m.LegacyExchangeDn
    $tmpUser = New-MailUser -MicrosoftOnlineServicesID $mosi -PrimarySmtpAddress $mosi -ExternalEmailAddress $m.PrimarySmtpAddress -FirstName $m.FirstName -LastName $m.LastName -Name $m.Name -DisplayName $m.DisplayName -Alias $m.Alias -Password $Password
    $tmpUser | Set-MailUser -EmailAddresses @{add=$x500} -ExchangeGuid $m.ExchangeGuid -ArchiveGuid $m.ArchiveGuid -CustomAttribute1 "ProjectKermit"
    $tmpx500 = $m.EmailAddresses | ?{$_ -match "x500"}
    $tmpx500 | %{Set-MailUser $m.Alias -EmailAddresses @{add="$_"}}
    }

################################################################# 
# On AADSync machine, run AADSync 
#################################################################  
Start-ADSyncSyncCycle 
 
#AADSync and FWDSync will create the target MEUs in the Target tenant 
```
**Comment pouvons-nous accéder Outlook jour 1 une fois que la boîte aux lettres d’utilisation a été déplacée ?**

Étant donné qu’un seul client peut posséder un domaine, l’ancienne adresse SMTP principale n’est pas associée à l’utilisateur dans le client cible une fois le déplacement de la boîte aux lettres terminé . uniquement les domaines associés au nouveau client. Outlook utilise le nouvel UPN des utilisateurs pour s’authentifier au service et le profil Outlook s’attend à trouver l’adresse SMTPAddress principale héritée pour correspondre à la boîte aux lettres dans le système cible. Étant donné que l’adresse héritée ne se trouve pas dans le système cible, le profil Outlook ne se connecte pas pour rechercher la boîte aux lettres nouvellement déplacée. 

Pour ce déploiement initial, les utilisateurs devront reconstruire leur profil avec leur nouvel UPN, l’adresse SMTP principale et synchroniser à nouveau le contenu OST. 

> [!Note]
> Planifiez en conséquence le traitement par lots de vos utilisateurs. Vous devez tenir compte de l’utilisation et de la capacité du réseau lorsque Outlook profils clients sont créés et que les fichiers OST et OAB suivants sont téléchargés vers les clients. 
 
**De quels Exchange RBAC ai-je besoin d’être membre pour configurer ou effectuer un déplacement entre locataires ?**
 
Il existe une matrice de rôles basée sur l’hypothèse de tâches déléguées lors de l’exécution d’un déplacement de boîte aux lettres. Actuellement, deux rôles sont requis :  

- Le premier rôle est une tâche de configuration qui établit l’autorisation de déplacer du contenu vers ou hors de vos limites client/organisation. Étant donné que le déplacement des données hors de votre contrôle organisationnel est une préoccupation critique pour toutes les entreprises, nous avons choisi le rôle d’administrateur d’organisation (OrgAdmin) le plus élevé. Ce rôle doit modifier ou configurer un nouvel OrganizationRelationship qui définit la -MailboxMoveCapability avec l’organisation distante. Seul l’OrgAdmin peut modifier le paramètre MailboxMoveCapability, tandis que d’autres attributs de OrganizationRelationhip peuvent être gérés par l’administrateur de partage fédéré. 
 
- Le rôle d’exécution des commandes de déplacement réelles peut être délégué à une fonction de niveau inférieur. Le rôle de déplacement de boîtes aux lettres se voit attribuer la possibilité de déplacer des boîtes aux lettres à l’intérieur ou à l’intérieur de l’organisation à l’aide du `-RemoteTenant` paramètre.  

**Comment cibler l’adresse SMTP sélectionnée pour targetAddress (TargetDeliveryDomain) sur la boîte aux lettres convertie (en conversion MailUser) ?**
 
Exchange déplacements de boîtes aux lettres à l’aide du service MRS tissent l’adresse cible sur la boîte aux lettres source d’origine lors de la conversion en MailUser en correspondant à une adresse e-mail (proxyAddress) sur l’objet cible. Le processus prend la valeur -TargetDeliveryDomain transmise dans la commande de déplacement, puis recherche un proxy correspondant pour ce domaine côté cible. Lorsque nous trouvons une correspondance, le proxyAddress correspondant est utilisé pour définir ExternalEmailAddress (targetAddress) sur l’objet de boîte aux lettres convertie (désormais MailUser).
 
**Comment les autorisations de boîte aux lettres sont-ils en cours de transition ?**

Les autorisations de boîte aux lettres incluent Envoyer de la part de et Accès aux boîtes aux lettres : 

- Send On Behalf Of (AD:publicDelegates) stocke le nom DN des destinataires ayant accès à la boîte aux lettres d’un utilisateur en tant que délégué. Cette valeur est stockée dans Active Directory et ne se déplace actuellement pas dans le cadre de la transition de boîte aux lettres. Si la boîte aux lettres source a publicDelegates définie, vous devrez restamper les publicDelegates sur la boîte aux lettres cible une fois la conversion de l’utilisateur à l’utilisateur à boîte aux lettres terminée dans l’environnement cible en cours `Set-Mailbox <principle> -GrantSendOnBehalfTo <delegate>` d’exécution. 
 
- Les autorisations de boîte aux lettres stockées dans la boîte aux lettres sont déplacées avec la boîte aux lettres lorsque le principal et le délégué sont déplacés vers le système cible. Par exemple, l’utilisateur TestUser_7 accès total à la boîte aux lettres TestUser_8 dans le client SourceCompany.onmicrosoft.com. Une fois le déplacement de la boîte TargetCompany.onmicrosoft.com terminé, les mêmes autorisations sont définies dans le répertoire cible. Des exemples *d’utilisation de Get-MailboxPermission* TestUser_7 dans les clients source et cible sont présentés ci-dessous. Exchange cmdlets sont précédées du préfixe source et cible en conséquence. 
 
Voici un exemple de sortie de l’autorisation de boîte aux lettres avant un déplacement. 

```powershell
PS C:\PowerShell\> Get-SourceMailboxPermission testuser_7 |ft -AutoSize User, AccessRights, IsInherited, Deny
User                                             AccessRights                                                            IsInherited Deny
----                                             ------------                                                            ----------- ----
NT AUTHORITY\SELF                                {FullAccess, ReadPermission}                                            False       False
TestUser_8@SourceCompany.onmicrosoft.com         {FullAccess}                                                            False       False....
```
Voici un exemple de sortie de l’autorisation de boîte aux lettres après le déplacement. 

```powershell
PS C:\PowerShell\> Get-TargetMailboxPermission testuser_7 | ft -AutoSize User, AccessRights, IsInherited, Deny
User                                             AccessRights                                                            IsInherited Deny
----                                             ------------                                                            ----------- ----
NT AUTHORITY\SELF                                {FullAccess, ReadPermission}                                            False       FalseTestUser_8@TargetCompany.onmicrosoft.com         {FullAccess}                                                            False       False
```
 
> [!Note]
> Les autorisations de calendrier et de boîte aux lettres entre locataires ne sont PAS pris en charge. Vous devez organiser les principaux et les délégués en lots de déplacement consolidés afin que ces boîtes aux lettres connectées soient transitionn es en même temps à partir du client source. 

**Quel proxy X500 doit être ajouté aux adresses proxy MailUser cibles pour permettre la migration ?**  

La migration de boîtes aux lettres entre locataires nécessite que la valeur LegacyExchangeDN de l’objet de boîte aux lettres source soit estampillée comme adresse de messagerie x500 sur l’objet MailUser cible.  

Exemple :  
```powershell
LegacyExchangeDN value on source mailbox is:  
/o=First Organization/ou=Exchange Administrative Group(FYDIBOHF23SPDLT)/cn=Recipients/cn=d11ec1a2cacd4f81858c81907273f1f9Lara  

so the x500 email address to be added to target MailUser object would be:  
x500:/o=First Organization/ou=Exchange Administrative Group (FYDIBOHF23SPDLT)/cn=Recipients/cn=d11ec1a2cacd4f81858c81907273f1f9-Lara  
```

> [!Note]  
> Outre ce proxy X500, vous devrez copier tous les proxys X500 de la boîte aux lettres dans la source vers la boîte aux lettres dans la cible.  

**Où commencer à résoudre les problèmes si les déplacements ne fonctionnent pas ?**  

Commencez par l’exécution VerifySetup.ps1 script situé sur GitHub et [examinez](https://github.com/microsoft/cross-tenant/releases/tag/Preview) la sortie.

Voici un exemple d’exécution de VerifySetup.ps1 sur le client cible :

```powershell
VerifySetup.ps1 -PartnerTenantId <SourceTenantId> -ApplicationId <AADApplicationId> -ApplicationKeyVaultUrl <appKeyVaultUrl> -PartnerTenantDomain <PartnerTenantDomain> -Verbose
```

Voici un exemple d’exécution de VerifySetup.ps1 sur le client source :

```powershell
VerifySetup.ps1 -PartnerTenantId <TargetTenantId> -ApplicationId <AADApplicationId>
```

**Le client source et cible peut-il utiliser le même nom de domaine ?**  

Non. Les noms de domaine du client source et cible doivent être uniques. Par exemple, un domaine source de contoso.com et le domaine cible de fourthcoffee.com.

**Les boîtes aux lettres partagées seront-ils toujours en déplacement et fonctionneront-ils ?**

Oui, toutefois, nous ne conserveons que les autorisations du Store comme décrit dans les articles suivants :

- [Documentation Microsoft | Gérer les autorisations pour les destinataires dans Exchange Online](/exchange/recipients-in-exchange-online/manage-permissions-for-recipients)

- [Support Microsoft | Comment accorder des autorisations Exchange et Outlook aux boîtes aux lettres dans Office 365 dédié](https://support.microsoft.com/topic/how-to-grant-exchange-and-outlook-mailbox-permissions-in-office-365-dedicated-bac01b2c-08ff-2eac-e1c8-6dd01cf77287)

**Azure Key Vault est-il requis et quand les transactions sont-elles réalisées ?**  

Oui, un abonnement Azure est requis pour utiliser le coffre de clés pour stocker le certificat afin d’autoriser la migration. Contrairement aux migrations d’intégration qui utilisent le mot de passe & nom d’utilisateur pour s’authentifier à la source, les migrations de boîtes aux lettres entre locataires utilisent OAuth et ce certificat comme secret/informations d’identification. L’accès au coffre de clés doit être maintenu tout au long de toutes les migrations de boîtes aux lettres, car il est accessible une fois au début et une fois à la fin de la migration, ainsi qu’une fois toutes les 24 heures pendant les périodes de synchronisation incrémentielle. Vous pouvez consulter les détails de coût AKV [ici.]( https://azure.microsoft.com/en-us/pricing/details/key-vault/)  

**Avez-vous des recommandations pour les lots ?**  

Ne dépassez pas 2 000 boîtes aux lettres par lot. Nous vous recommandons vivement d’envoyer des lots deux semaines avant la date de cut-over, car cela n’a aucun impact sur les utilisateurs finaux pendant la synchronisation. Si vous avez besoin de conseils pour les quantités de boîtes aux lettres de plus de 50 000, vous pouvez accéder à la liste de distribution des commentaires techniques sur crosstenantmigrationpreview@service.microsoft.com.

**Que se passe-t-il si j’utilise le chiffrement de service avec la clé client ?**

La boîte aux lettres sera déchiffrée avant le déplacement. Assurez-vous que la clé client est configurée dans le client cible si elle est toujours requise. Pour [plus d’informations,](../compliance/customer-key-overview.md) voir ici.  

**Quelle est la durée de migration estimée ?**

Pour vous aider à planifier [](/exchange/mailbox-migration/office-365-migration-best-practices#estimated-migration-times) votre migration, le tableau présenté ici présente les instructions relatives à la fin des migrations de boîtes aux lettres en bloc ou individuelles. Ces estimations sont basées sur une analyse des données des migrations de clients précédentes. Étant donné que chaque environnement est unique, votre vitesse de migration exacte peut varier.  

N’oubliez pas que cette fonctionnalité est actuellement en prévisualisation et que le SLA et les niveaux de service applicables ne s’appliquent pas aux problèmes de performances ou de disponibilité pendant l’état d’aperçu de cette fonctionnalité.

## <a name="known-issues"></a>Problèmes connus  

-  **Problème : les archives à extension automatique ne peuvent pas être migrées.** La fonctionnalité de migration entre locataires permet de migrer la boîte aux lettres principale et la boîte aux lettres d’archivage d’un utilisateur spécifique. Si l’utilisateur dans la source possède toutefois une archive à extension automatique , ce qui signifie que plusieurs boîtes aux lettres d’archivage, la fonctionnalité ne peut pas migrer les archives supplémentaires et doit échouer.

- **Problème : les mailusers cloud avec un proxyAddress smtp non propriétaire bloquent mrs déplace l’arrière-plan.** Lorsque vous créez des objets MailUser de client cible, vous devez vous assurer que toutes les adresses proxy SMTP appartiennent à l’organisation du client cible. S’il existe un proxy SMTPAddress sur l’utilisateur de messagerie cible qui n’appartient pas au client local, la conversion de MailUser en boîte aux lettres est empêchée. Cela est dû à notre assurance que les objets de boîte aux lettres peuvent uniquement envoyer des messages à partir de domaines pour lesquels le client fait autorité (domaines revendiqués par le client) : 

   - Lorsque vous synchronisez des utilisateurs en local à l’aide d’Azure AD Connecter, vous provisionnez les objets MailUser locaux avec ExternalEmailAddress pointant vers le client source où la boîte aux lettres existe (laran@contoso.onmicrosoft.com) et vous marquez PrimarySMTPAddress comme un domaine qui réside dans le client cible (Lara.Newton@northwind.com). Ces valeurs sont synchronisées avec le client et un utilisateur de messagerie approprié est approvisionnement et prêt pour la migration. Un exemple d’objet est illustré ici.
     ```powershell
     target/AADSynced user] PS C> Get-MailUser laran | select ExternalEmailAddress, EmailAddresses   
     ExternalEmailAddress               EmailAddresses 
     --------------------               -------------- 
     SMTP:laran@contoso.onmicrosoft.com {SMTP:lara.newton@northwind.com} 
     ```

   > [!Note]
   > *L contoso.onmicrosoft.com’adresse* de messagerie *n’est* pas présente dans le tableau EmailAddresses/proxyAddresses.

- **Problème : les objets MailUser avec des adresses SMTP principales « externes » sont modifiés/réinitialisés sur les domaines revendiqués par l’entreprise « internes »**

   Les objets MailUser sont des pointeurs vers des boîtes aux lettres non locales. Dans le cas des migrations de boîtes aux lettres entre locataires, nous utilisons des objets MailUser pour représenter la boîte aux lettres source (du point de vue de l’organisation cible) ou la boîte aux lettres cible (du point de vue de l’organisation source). Les utilisateurs de messagerie auront une adresse ExternalEmailAddress (targetAddress) qui pointe vers l’adresse smtp de la boîte aux lettres réelle (ProxyTest@fabrikam.onmicrosoft.com) et l’adresse PRIMARYSMTP qui représente l’adresse SMTP affichée de l’utilisateur de boîte aux lettres dans l’annuaire. Certaines organisations choisissent d’afficher l’adresse SMTP principale en tant qu’adresse SMTP externe, et non en tant qu’adresse propriétaire/vérifiée par le client local (par exemple, fabrikam.com plutôt que comme contoso.com).  Toutefois, une fois qu’un objet plan de service Exchange est appliqué à MailUser via des opérations de gestion des licences, l’adresse SMTP principale est modifiée pour s’afficher comme un domaine vérifié par l’organisation locale (contoso.com). Il existe deux raisons possibles :
   
   - Lorsqu’un plan de service Exchange est appliqué à un mailuser, le processus Azure AD commence à appliquer le nettoyage de proxy pour s’assurer que l’organisation locale n’est pas en mesure d’envoyer des messages électroniques, usurpations ou messages à partir d’un autre client. Toute adresse SMTP sur un objet destinataire avec ces plans de service sera supprimée si l’adresse n’est pas vérifiée par l’organisation locale. Comme c’est le cas dans l’exemple, le domaine Fabikam.com n’est PAS vérifié par le client contoso.onmicrosoft.com, de sorte que le nettoyage supprime ce fabrikam.com domaine. Si vous souhaitez rendre persistants ces domaines externes sur MailUser, avant la migration ou après la migration, vous devez modifier vos processus de migration afin d’obtenir des licences à la fin du déplacement ou avant le déplacement pour vous assurer que la marque externe attendue est appliquée aux utilisateurs. Vous devez vous assurer que l’objet de boîte aux lettres est correctement titulaire d’une licence pour ne pas affecter le service de messagerie.<br/><br/>Un exemple de script pour supprimer les plans de service sur un MailUser dans le Contoso.onmicrosoft.com client est illustré ici.

    ```powershell
    $LO = New-MsolLicenseOptions -AccountSkuId "contoso:ENTERPRISEPREMIUM" DisabledPlans 
    "LOCKBOX_ENTERPRISE","EXCHANGE_S_ENTERPRISE","INFORMATION_BARRIERS","MIP_S_CLP2","
    MIP_S_CLP1","MYANALYTICS_P2","EXCHANGE_ANALYTICS","EQUIVIO_ANALYTICS","THREAT_INTE
    LLIGENCE","PAM_ENTERPRISE","PREMIUM_ENCRYPTION" 
    Set-MsolUserLicense -UserPrincipalName proxytest@contoso.com LicenseOptions $lo 
    ```

       Les résultats de l’ensemble des Plans de service affectés sont affichés ici.

    ```powershell
    (Get-MsolUser -UserPrincipalName proxytest@contoso.com).licenses |select 
    -ExpandProperty servicestatus |sort ProvisioningStatus -Descending   
    ServicePlan           ProvisioningStatus 
    -----------           ------------------ 
    ATP_ENTERPRISE        PendingProvisioning 
    MICROSOFT_SEARCH      PendingProvisioning 
    INTUNE_O365           PendingActivation 
    PAM_ENTERPRISE        Disabled 
    EXCHANGE_ANALYTICS    Disabled 
    EQUIVIO_ANALYTICS     Disabled 
    THREAT_INTELLIGENCE   Disabled 
    LOCKBOX_ENTERPRISE    Disabled 
    PREMIUM_ENCRYPTION    Disabled 
    EXCHANGE_S_ENTERPRISE Disabled 
    INFORMATION_BARRIERS  Disabled 
    MYANALYTICS_P2        Disabled 
    MIP_S_CLP1            Disabled 
    MIP_S_CLP2            Disabled 
    ADALLOM_S_O365        PendingInput 
    RMS_S_ENTERPRISE      Success 
    YAMMER_ENTERPRISE     Success 
    PROJECTWORKMANAGEMENT Success 
    BI_AZURE_P2           Success 
    WHITEBOARD_PLAN3      Success 
    SHAREPOINTENTERPRISE  Success 
    SHAREPOINTWAC         Success 
    KAIZALA_STANDALONE    Success 
    OFFICESUBSCRIPTION    Success 
    MCOSTANDARD           Success 
    Deskless              Success 
    STREAM_O365_E5        Success 
    FLOW_O365_P3          Success 
    POWERAPPS_O365_P3     Success 
    TEAMS1                Success 
    MCOEV                 Success 
    MCOMEETADV            Success 
    BPOS_S_TODO_3         Success 
    FORMS_PLAN_E5         Success 
    SWAY                  Success 

    ```
 
       L’adresse PrimarySMTPAddress de l’utilisateur n’est plus nettoyée. Le fabrikam.com n’appartient pas au client contoso.onmicrosoft.com et est persistant en tant qu’adresse SMTP principale affichée dans l’annuaire.

       Voici un exemple.

    ```powershell
    get-recipient proxytest | ft -a userprin*, primary*, external*   
    PrimarySmtpAddress        ExternalDirectoryObjectId               ExternalEmailAddress 
    ------------------        -------------------------               -------------------- 
    proxytest@fabrikam.com    e2513482-1d5b-4066-936a-cbc7f8f6f817    SMTP:proxytest@fabrikam.com 
    ```

   - Lorsque msExchRemoteRecipientType est définie sur 8 (DeprovisionMailbox), pour les mailusers locaux migrés vers le client cible, la logique de nettoyage de proxy dans Azure supprime les domaines nonowned et réinitialise le primarySMTP sur un domaine propriétaire. En effaissant msExchRemoteRecipientType dans l’mailuser local, la logique de nettoyage proxy ne s’applique plus. <br/><br>Voici l’ensemble complet des plans de service possibles qui incluent Exchange Online.

   | Nom                                              |
   |---------------------------------------------------|
   | Advanced eDiscovery Stockage (500 Go)               |
   | Référentiel sécurisé client                                  |
   | Protection contre la perte de données                              |
   | Services CAL Exchange Enterprise (EOP, DLP)       |
   | Exchange Essentials                               |
   | Exchange Foundation                               |
   | Exchange Online (P1)                              |
   | Exchange Online (plan 1)                          |
   | Exchange Online (plan 2)                          |
   | Archivage Exchange Online pour Exchange Online     |
   | Archivage Exchange Online pour Exchange Server     |
   | Exchange Online Modules de modules utilisateur inactifs              |
   | Exchange Online Kiosk                             |
   | Exchange Online Multi-Geo                         |
   | Exchange Online (plan 1)                            |
   | Exchange Online POP                               |
   | Exchange Online Protection                        |
   | Obstacles à l’information                              |
   | Protection des informations pour Office 365 – Premium   |
   | Protection des informations pour Office 365 – Standard  |
   | Informations par MyAnalytics                           |
   | Microsoft 365 Audit avancé                   |
   | Microsoft Bookings                                |
   | Microsoft Business Center                         |
   | Microsoft MyAnalytics (complet)                      |
   | Office 365 Advanced eDiscovery                    |
   | Microsoft Defender pour Office 365 (Plan 1)    |
   | Microsoft Defender pour Office 365 (Plan 2)    |
   | Office 365 Privileged Access Management           |
   | Premium Chiffrement dans Office 365                  |
