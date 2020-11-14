---
title: Migration de boîtes aux lettres inter-clients
description: Comment déplacer des boîtes aux lettres entre des clients Microsoft 365 ou Office 365.
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
ms.openlocfilehash: 1e2624fea7a93013e4b4de2dd4ede4144000f075
ms.sourcegitcommit: fcc1b40732f28f075d95faffc1655473e262dd95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2020
ms.locfileid: "49073082"
---
# <a name="cross-tenant-mailbox-migration-preview"></a>Migration de boîtes aux lettres entre clients (aperçu)

Auparavant, lorsqu’un client Exchange Online avait besoin de déplacer des boîtes aux lettres vers un autre client dans le même service Exchange Online, il devra le débarquement entièrement sur site, puis les intégrer à un nouveau client. Avec la nouvelle fonctionnalité de migration de boîtes aux lettres entre clients, les administrateurs de client dans les clients source et cible peuvent déplacer des boîtes aux lettres entre les clients avec des dépendances d’infrastructure minimales dans leurs systèmes locaux. Cela supprime le besoin de débarquement et des boîtes aux lettres intégrées.

En règle générale, lors de fusions ou de cessions, vous avez besoin de pouvoir déplacer des utilisateurs et du contenu vers un nouveau client. Lorsque l’administrateur client cible exécute le déplacement, il s’agit d’un déplacement par extraction, semblable aux migrations d’intégration dans le Cloud.

Les déplacements de boîtes aux lettres Exchange interlocataires sont entièrement en libre-service par les administrateurs client, à l’aide d’interfaces connues qui peuvent être scriptées dans les flux de travail plus volumineux nécessaires pour faire passer les utilisateurs à leur nouvelle organisation. Les administrateurs peuvent utiliser l’applet de commande `New-MigrationBatch` , disponible via le rôle de gestion déplacer des boîtes aux lettres, pour exécuter des déplacements entre clients. Le processus de déplacement inclut des vérifications d’autorisation client lors de la synchronisation et de la finalisation des boîtes aux lettres. 
 
Les utilisateurs qui migrent doivent être présents dans le système Exchange Online client cible en tant que MailUsers, marqués avec des attributs spécifiques pour permettre le déplacement entre clients. Le système ne bascule pas pour les utilisateurs qui ne sont pas correctement configurés dans le client cible. 

Une fois les déplacements terminés, la boîte aux lettres du système source est convertie en MailUser et le targetAddress (indiqué comme ExternalEmailAddress dans Exchange) est marqué avec l’adresse de routage vers le client de destination. Ce processus laisse le MailUser hérité dans le client source et autorise une période de coexistence et de routage du courrier. Lorsque les processus d’entreprise sont autorisés, le client source peut supprimer la source MailUser ou les convertir en contact de messagerie. 

Les migrations de boîtes aux lettres Exchange interclientes sont prises en charge pour les clients en environnement hybride ou en nuage uniquement, ou n’importe quelle combinaison des deux.

Cet article décrit le processus de déplacement de boîtes aux lettres entre clients et fournit des conseils sur la façon de préparer les clients source et cible pour le déplacement de contenu. 

## <a name="preparing-source-and-target-tenants"></a>Préparation des clients source et cible

La fonctionnalité de migration de boîte aux lettres Exchange entre les clients requiert une autorisation et une portée pour les migrations entre clients. À l’aide des solutions de stockage de clés et d’applications Azure Enterprise, les administrateurs clients sont désormais habilités à gérer à la fois l’autorisation et l’étendue des migrations de boîtes aux lettres Exchange Online d’un client à l’autre. Les déplacements entre boîtes aux lettres interclientes prennent en charge une invitation et un modèle de consentement pour établir une application Azure Active Directory (Azure AD) utilisée pour l’authentification entre une paire de locataires. Des composants supplémentaires, tels qu’une relation organisationnelle et un point de terminaison de migration, sont également requis.

Cette section n’inclut pas les étapes spécifiques requises pour préparer les objets utilisateur MailUser dans l’annuaire cible, ni inclure l’exemple de commande pour soumettre un lot de migration. Pour plus d’informations, consultez la rubrique [Prepare Target User Objects for Migration](#prepare-target-user-objects-for-migration) .

## <a name="prerequisites"></a>Conditions préalables

La fonctionnalité de déplacement de boîte aux lettres entre les clients nécessite [Azure Key Vault](https://docs.microsoft.com/azure/key-vault/basic-concepts) pour établir une application Azure spécifique à une paire de clients afin de stocker et d’accéder en toute sécurité au certificat/secret utilisé pour authentifier et autoriser la migration des boîtes aux lettres d’un client vers l’autre, en supprimant toutes les exigences de partage des certificats/secrets entre les clients. 

Avant de commencer, assurez-vous que vous disposez des autorisations nécessaires pour exécuter les scripts de déploiement afin de configurer le coffre-fort des clés Azure, l’application de boîte aux lettres de déplacement, le point de terminaison de migration EXO et la relation organisationnelle EXO. En règle générale, l’administrateur général est autorisé à effectuer toutes les étapes de configuration.

En outre, les groupes de sécurité à extension messagerie dans le client source sont requis avant d’exécuter le programme d’installation. Ces groupes permettent d’étendre la liste des boîtes aux lettres pouvant être déplacées depuis le client source (ou parfois appelé ressource) vers le client cible. Cela permet à l’administrateur client source de limiter ou d’étendre l’ensemble spécifique des boîtes aux lettres qui doivent être déplacées, empêchant ainsi les utilisateurs indésirables d’être migrés. Les groupes imbriqués ne sont pas pris en charge.

Vous devrez également communiquer avec votre société partenaire approuvée (avec laquelle vous allez transférer des boîtes aux lettres) pour obtenir son ID de client Microsoft 365. Cet ID de locataire est utilisé dans le champ relation organisationnelle `DomainName` .

Pour obtenir l’ID de client d’un abonnement, connectez-vous au centre d’administration Microsoft 365 et accédez à [https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties) . Cliquez sur l’icône de copie de la propriété ID de client pour la copier dans le presse-papiers.

Voici comment fonctionne le processus.

:::image type="content" source="../media/tenant-to-tenant-mailbox-move/prepare-tenants-flow.png" alt-text="Préparation du client pour la migration de boîtes aux lettres.":::

[Afficher une version plus grande de cette image](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/tenant-to-tenant-mailbox-move/prepare-tenants-flow.png).

<!--
[![Tenant preparation for mailbox migration](../media/tenant-to-tenant-mailbox-move/prepare-tenants-flow.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/tenant-to-tenant-mailbox-move/prepare-tenants-flow.png)
--> 

### <a name="prepare-tenants"></a>Préparer les locataires

À un niveau élevé, les actions de configuration suivantes ont lieu lors de l’exécution des scripts de configuration.

Préparez le client cible :

1. Si aucun groupe de ressources Azure existant n’est fourni, une nouvelle ressource est créée (SCRIPT).
2. Si un coffre-fort de clés existant n’est pas fourni, un nouveau coffre est créé (SCRIPT).
3. Une nouvelle stratégie d’accès est créée pour l’application de migration de boîte aux lettres Exchange Online pour Office 365.
4. Un nouveau certificat est créé (ou existant, s’il est spécifié) pour contenir le secret de l’application de migration (SCRIPT).
5. Une nouvelle application Azure AD est créée (SCRIPT).
6. Le certificat/secret est téléchargé vers l’application de migration (SCRIPT).
7. Les autorisations de migration de boîte aux lettres sont affectées à l’application (SCRIPT).
8. Le script de déploiement s’interrompt jusqu’à ce que l’administrateur cible accepte sa propre application (SCRIPT).
9. L’administrateur client cible accepte les autorisations accordées à l’application (manuelle).
10. Une relation organisationnelle est créée vers le client cible (SCRIPT).
11. Un point de terminaison de migration est créé pour extraire des boîtes aux lettres vers le client cible (SCRIPT).

Préparez le client source :

1. L’administrateur client source accepte l’invitation à une application de migration de boîtes aux lettres à partir du client cible (manuel).
2. L’administrateur client source crée un groupe de sécurité à extension messagerie dans son client pour contenir la liste des boîtes aux lettres pouvant être déplacées par l’application de migration (manuelle).
3. Une relation organisationnelle est créée vers le client cible en spécifiant que l’application de migration de boîte aux lettres doit être utilisée pour la vérification OAuth afin d’accepter la demande de déplacement (SCRIPT).

#### <a name="step-by-step-instructions-for-the-target-tenant-admin"></a>Instructions pas à pas pour l’administrateur client cible

1. Téléchargez le script de SetupCrossTenantRelationshipForTargetTenant.ps1 pour le programme d’installation du client cible à partir du [référentiel GitHub](https://github.com/microsoft/cross-tenant/releases/tag/Preview). 
2. Enregistrez le script (SetupCrossTenantRelationshipForTargetTenant.ps1) sur l’ordinateur à partir duquel vous allez exécuter le script.
3. Créez une connexion PowerShell à distance vers le client cible Exchange Online. Assurez-vous que vous disposez des autorisations nécessaires pour exécuter les scripts de déploiement afin de configurer le stockage et le certificat du coffre-fort des clés Azure, de déplacer l’application de boîte aux lettres, de point de terminaison de migration EXO et de la relation organisationnelle EXO.
4. Modifiez le répertoire du dossier de fichiers à l’emplacement du script ou vérifiez que le script est actuellement enregistré à l’emplacement qui se trouve actuellement dans votre session PowerShell distante.
5. Exécutez le script avec les paramètres et valeurs suivants.

    | Paramètre | Valeur | Obligatoire ou facultatif
    |---------------------------------------------|-----------------|--------------|
    | -ResourceTenantDomain                       | Domaine client source, tel que Fabrikam \. onmicrosoft.com. | Requis |
    | -ResourceTenantAdminEmail                   | Adresse de messagerie de l’administrateur client source. Il s’agit de l’administrateur client source qui sera envoyé à l’utilisation de l’application de migration de boîtes aux lettres envoyée par l’administrateur cible. Il s’agit de l’administrateur qui recevra l’invitation par courrier électronique pour l’application. | Requis |
    | -TargetTenantDomain                         | Domaine client cible, tel que contoso \. onmicrosoft.com. | Requis |
    | -ResourceTenantId                           | ID de l’organisation cliente source (GUID). | Requis |
    | -SubscriptionId                             | Abonnement Azure à utiliser pour créer des ressources. | Requis |
    | -N                              | Nom du groupe de ressources Azure qui contient ou contiendra le coffre-fort de clés. | Requis |
    | -KeyVaultName                               | Instance de coffre-fort de clés Azure qui stockera votre certificat/secret d’application de migration de boîte aux lettres. | Requis |
    | -CertificateName                            | Nom du certificat lors de la génération ou de la recherche de certificat dans le coffre-fort. | Requis |
    | -CertificateSubject                         | Nom d’objet du certificat Azure Key Vault, tel que CN = contoso_fabrikam. | Requis |
    | -ExistingApplicationId                      | Application de migration de messagerie à utiliser si une application a déjà été créée. | Facultatif |
    | -AzureAppPermissions                        | Les autorisations doivent être accordées à l’application de migration de boîtes aux lettres, telle qu’Exchange ou MSGraph (Exchange pour le transfert de boîtes aux lettres, MSGraph pour l’utilisation de cette application pour envoyer une invitation de lien de consentement au locataire de ressources). | Requis |
    | -UseAppAndCertGeneratedForSendingInvitation | Paramètre d’utilisation de l’application créée pour la migration à utiliser pour envoyer une invitation de lien de consentement à l’administrateur de client source. Si ce n’est pas le cas, vous pouvez demander aux informations d’identification de l’administrateur cible de se connecter au gestionnaire d’invitations et envoyer l’invitation en tant qu’administrateur cible. | Facultatif |
    | -KeyVaultAuditStorageAccountName            | Le compte de stockage dans lequel les journaux d’audit du coffre-fort principal seraient stockés. | Facultatif |
    | -KeyVaultAuditStorageResourceGroup          | Le groupe de ressources qui contient le compte de stockage pour le stockage des journaux d’audit de coffre de clés. | Facultatif |
    ||||

6. Le script s’interrompt et vous demande d’accepter ou d’accepter l’application de migration de boîte aux lettres Exchange créée pendant ce processus. Voici un exemple.

    ```powershell
    PS C:\Users\Admin\scripts\T2TMovesV2> .\SetupCrossTenantRelationshipForTargetTenant.ps1 -ResourceTenantDomain contoso.onmicrosoft.com -ResourceTenantAdminEmail admin@contoso.onmicrosoft.com -TargetTenantDomain fabrikam.onmicrosoft.com -ResourceTenantId ksagjid39-ede2-4d2c-98ae-874709325b00 -SubscriptionId e4ssd05d-a327-49ss-849a-sd0932439023 -ResourceGroup "Cross-TenantMoves" -KeyVaultName "Cross-TenantMovesVault" -CertificateName "Contoso-Fabrikam-cert" -CertificateSubject "CN=Contoso_Fabrikam" -AzureAppPermissions Exchange, MSGraph -UseAppAndCertGeneratedForSendingInvitation -KeyVaultAuditStorageAccountName "t2tstorageaccount" -KeyVaultAuditStorageResourceGroup "Demo"

    cmdlet Get-Credential at command pipeline position 1
    Supply values for the following parameters:
    Credential
    Setting up key vault in the fabrikam.onmicrosoft.com tenant

    Name                                     Account                                 SubscriptionName                        Environment                             TenantId
        ----                                     -------                                 ----------------                        -----------                             --------
    Pay-As-You-Go (ewe23423-a3327-34232-343... Admin@fabrikam... Pay-As-You-Go                           AzureCloud                              dsad938432-dd8e-s9034-bf9a-83984293n43
    Auditing setup successfully for Cross-TenantMovesVault
    Exchange application given access to KeyVault Cross-TenantMovesVault
    Application fabrikam_Friends_contoso_2520 created successfully in fabrikam.onmicrosoft.com tenant with following permissions. MSGraph - Directory.ReadWrite.All. Exchange - Mailbox.Migration
    Admin consent URI for fabrikam.onmicrosoft.com tenant admin is -
    https://login.microsoftonline.com/fabrikam.onmicrosoft.com/adminconsent?client_id=6fea6ere-0dwe-404d-ad35-c71a15cers5c&redirect_uri=https://office.com
    Admin consent URI for contoso.onmicrosoft.com tenant admin is -
    https://login.microsoftonline.com/contoso.onmicrosoft.com/adminconsent?client_id=6fea6ssd-0753-404d-wer5-c71a154d675c&redirect_uri=https://office.com
    Application details to be registered in organization relationship: ApplicationId: [ 6fes8en4-sjo3-406d-ad35-sldkfjiew993 ]. KeyVault secret Id: [ https://cross-tenantmovesvault.vault.azure.net:443/certificates/Contoso-Fabrikam-cert/ksdfj843nt8476h84c288c5a3fb8ec5fdb08 ]. These values are available in variables $AppId and $CertificateId respectively
    Please consent to the application for fabrikam.onmicrosoft.com before sending invitation to admin@contoso.onmicrosoft.com:
    ``` 

7. Une URL s’affichera dans la session PowerShell distante. Copiez le lien fourni pour le consentement de votre client et collez-le dans un navigateur Web.

8. Connectez-vous avec vos informations d’identification d’administrateur général. Lorsque l’écran suivant s’affiche, sélectionnez **accepter**.

    :::image type="content" source="../media/tenant-to-tenant-mailbox-move/permissions-requested-dialog.png" alt-text="Boîte de dialogue accepter les autorisations":::
    
9. Revenez à la session PowerShell distante et appuyez sur entrée pour continuer.

10. Le script configurera les objets d’installation restants. Voici un exemple.

    ```powershell
    Successfully sent invitation to admin@contoso.onmicrosoft.com
    Setting up exchange components on target tenant: fabrikam.onmicrosoft.com
    MigrationEndpoint created in fabrikam.onmicrosoft.com for target contoso.onmicrosoft.com
    Exchange setup complete. Migration endpoint details are available in $MigrationEndpoint variable
    ```

L’installation de l’administration cible est maintenant terminée.

#### <a name="step-by-step-instructions-for-the-source-tenant-admin"></a>Instructions pas à pas pour l’administrateur de client source

1.  Connectez-vous à votre boîte aux lettres en tant que-ResourceTenantAdminEmail spécifié par l’administrateur cible lors de son installation. Recherchez l’invitation par courrier électronique à partir du client cible, puis sélectionnez le bouton **prise en main** .

    :::image type="content" source="../media/tenant-to-tenant-mailbox-move/invited-by-target-tenant.png" alt-text="La boîte de dialogue a été invitée":::

2. Sélectionnez **accepter** pour accepter l’invitation.

    :::image type="content" source="../media/tenant-to-tenant-mailbox-move/permissions-requested-accept.png" alt-text="Boîte de dialogue pour accepter les autorisations":::

   > [!NOTE]
   > Si vous ne recevez pas ce message ou si vous ne le trouvez pas, l’administrateur client cible a reçu une URL directe qui vous permet d’accepter l’invitation. L’URL doit être dans la transcription de la session PowerShell distante de l’administrateur du client cible.

3. Dans le centre d’administration Microsoft 365 ou une session PowerShell distante, créez un ou plusieurs groupes de sécurité à extension messagerie pour contrôler la liste des boîtes aux lettres autorisées par le client cible à extraire (déplacer) du client source vers le client cible. Vous n’avez pas besoin de remplir ce groupe à l’avance, mais au moins un groupe doit être fourni pour exécuter les étapes de configuration (script). Les groupes imbriqués ne sont pas pris en charge. 

4. Téléchargez le script de SetupCrossTenantRelationshipForTargetResource.ps1 pour le programme d’installation du client source à partir du référentiel GitHub [ici](https://github.com/microsoft/cross-tenant/releases/tag/Preview). 

5. Créez une connexion PowerShell à distance vers le client source avec vos autorisations d’administrateur Exchange. Les autorisations d’administrateur global ne sont pas nécessaires pour configurer le client source, uniquement le client cible en raison du processus de création d’application Azure.

6. Remplacez le répertoire par l’emplacement du script ou vérifiez que le script est actuellement enregistré à l’emplacement actuellement présent dans votre session PowerShell distante.

7. Exécutez le script avec les paramètres et valeurs obligatoires suivants.

    | Paramètre | Valeur |
    |-----|------|
    | -SourceMailboxMovePublishedScopes | Groupe de sécurité à extension messagerie créé par le client source pour les identités/boîtes aux lettres qui sont dans l’étendue de la migration. |
    | -ResourceTenantDomain | Nom de domaine client source, tel que Fabrikam \. onmicrosoft.com. |
    | -TargetTenantDomain | Nom de domaine client cible, tel que contoso \. onmicrosoft.com. |
    | -ApplicationId | ID d’application Azure (GUID) de l’application utilisée pour la migration. ID d’application disponible via votre portail Azure (Azure AD, applications d’entreprise, nom de l’application, ID de l’application) ou inclus dans votre courrier électronique d’invitation.  |
    | -TargetTenantId | ID de client du client cible. Par exemple, l’ID de client Azure AD du \. client contoso onmicrosoft.com. |
    |||
    
    Voici un exemple.
    ```powershell
    SetupCrossTenantRelationshipForResourceTenant.ps1 -SourceMailboxMovePublishedScopes "MigScope","MyGroup" -ResourceTenantDomain contoso.onmicrosoft.com -TargetTenantDomain fabrikam.onmicrosoft.com -ApplicationId sdf5e87sa-0753-dd88-ad35-c71a15cs8e44c -TargetTenantId 4sdkfo933-3904-sd93-bf9a-sdi39402834
    Exchange setup complete.

    ```

La configuration de l’administration source est maintenant terminée !

### <a name="verify-setup"></a>Vérifier la configuration

Vérifiez que les relations de l’organisation dans les clients source et cible et le point de terminaison de la migration dans la cible ont été créés avec succès.

#### <a name="target-tenant"></a>Client cible

**Relation organisationnelle**

Vérifiez que l’objet de relation d’organisation a été créé et configuré à l’aide de cette commande.

```powershell
Get-OrganizationRelationship <source tenant organization name> | fl name, DomainNames, MailboxMoveEnabled, MailboxMoveCapability
```
Voici un exemple :

```powershell
PS C:\Users\Admin\scripts\T2TMovesV2> Get-OrganizationRelationship fabrikam_contoso_1178 | fl name, DomainNames, MailboxMoveEnabled, MailboxMoveCapability

Name                  : fabrikam_contoso_1123
DomainNames           : {sd0933me9f-9304-s903-s093-s093mfi903m4}
MailboxMoveEnabled    : True
MailboxMoveCapability : Inbound

```

**Point de terminaison de migration**

Vérifiez que l’objet de point de terminaison de migration a été créé et configuré à l’aide de cette commande.

```powershell
Get-MigrationEndpoint "<fabrikam_contoso_1123> | fl Identity, RemoteTenant, ApplicationId, AppSecretKeyVaultUrl
```

Voici un exemple.

```powershell
PS C:\Users\Admin\scripts\T2TMovesV2> Get-MigrationEndpoint fabrikam_contoso_1123 | fl Identity, RemoteTenant, ApplicationId, AppSecretKeyVaultUrl


Identity             : fabrikam_contoso_1123
RemoteTenant         : contoso.onmicrosoft.com
ApplicationId        : s93mf93-das9-dq24-dq234-dada9033904m
AppSecretKeyVaultUrl : https://cross-tenantmyvaultformoves.vault.azure.net:443/certificates/Contoso-Fabrikam-cert/ae79348mx94384c288c5a3dfsioepw308

```

#### <a name="source-tenant"></a>Client source

**Relation organisationnelle**

Vérifiez que l’objet de relation d’organisation a été créé et configuré à l’aide de cette commande.

```powershell
Get-OrganizationRelationship | fl name, MailboxMoveEnabled, MailboxMoveCapability, MailboxMovePublishedScopes, OAuthApplicationId
```
Voici un exemple.

```powershell
PS C:\Users\Admin\scripts\T2TMovesV2> Get-OrganizationRelationship | fl name, MailboxMoveEnabled, MailboxMoveCapability, MailboxMovePublishedScopes, OAuthApplicationId


Name                       : fabrikam_contoso_001
MailboxMoveEnabled         : True
MailboxMoveCapability      : RemoteOutbound
MailboxMovePublishedScopes : {MigScope}
OAuthApplicationId         : sd9890342-3243-3242-fe3w2-fsdade93m0
```

### <a name="move-mailboxes-back-to-the-original-source"></a>Déplacer les boîtes aux lettres vers la source d’origine

Si une boîte aux lettres revient au locataire source d’origine, le même ensemble d’étapes et de scripts doit être exécuté dans les deux nouveaux clients source et cible. L’objet de relation organisationnelle existant sera mis à jour ou ajouté, non recréé.

## <a name="prepare-target-user-objects-for-migration"></a>Préparer les objets utilisateur cible pour la migration

Les utilisateurs qui migrent doivent être présents dans le client cible et le système Exchange Online (en tant que MailUsers) marqués avec des attributs spécifiques pour permettre le déplacement entre clients. Le système ne bascule pas pour les utilisateurs qui ne sont pas correctement configurés dans le client cible. La section suivante décrit en détail les conditions requises pour les objets MailUser pour le client cible.

### <a name="prerequisites"></a>Conditions préalables
  
Vous devez vous assurer que les objets et attributs suivants sont définis dans l’organisation cible.  

1. Pour les boîtes aux lettres déplacées à partir d’une organisation source, vous devez mettre en service un objet MailUser dans l’organisation cible : 
   - Le MailUser cible doit avoir les attributs suivants de la boîte aux lettres source ou être affecté au nouvel objet User :
      - ExchangeGUID (transit direct depuis la source vers la cible) : le GUID de la boîte aux lettres doit correspondre. Le processus de déplacement ne se poursuit pas s’il n’est pas présent sur l’objet cible. 
      - ArchiveGUID (transit direct depuis la source vers la cible) : le GUID d’archivage doit correspondre. Le processus de déplacement ne se poursuit pas s’il n’est pas présent sur l’objet cible. (Ceci est uniquement requis si l’archivage de la boîte aux lettres source est activé). 
      - LegacyExchangeDN (Flow As proxyAddress, "x500 : <LegacyExchangeDN> ") : le legacyExchangeDN doit être présent sur le MailUser cible en tant que x500 : ProxyAddress. Les processus de déplacement ne continueront pas si cela n’est pas présent sur l’objet cible. 
      - UserPrincipalName : l’UPN s’aligne sur la nouvelle identité de l’utilisateur ou la nouvelle société cible (par exemple, user@northwindtraders.onmicrosoft.com). 
      - SMTPAddress principal : l’adresse SMTP principale s’aligne sur la nouvelle société de l’utilisateur (par exemple, user@northwind.com). 
      - TargetAddress/ExternalEmailAddress – MailUser fait référence à la boîte aux lettres actuelle de l’utilisateur, hébergée dans le client source (par exemple, user@contoso.onmicrosoft.com). Lors de l’affectation de cette valeur, vérifiez que vous avez ou que vous affectez également la propriété PrimarySMTPAddress ou que cette valeur définit la propriété PrimarySMTPAddress qui provoque des échecs de déplacement. 
      - Vous ne pouvez pas ajouter d’adresses proxy SMTP héritées de la boîte aux lettres source pour cibler MailUser. Par exemple, vous ne pouvez pas gérer contoso.com sur l’unité MEU dans les objets client fabrikam.onmicrosoft.com). Les domaines sont associés à un seul client Azure AD ou Exchange Online.
 
    Exemple d’objet MailUser **cible** :
 
    | Attribut             | Valeur                                                                                                                    |
    |-----------------------|--------------------------------------------------------------------------------------------------------------------------|
    | Alias                 | LaraN                                                                                                                    |
    | RecipientType         | MailUser                                                                                                                 |
    | RecipientTypeDetails  | MailUser                                                                                                                 |
    | UserPrincipalName     | LaraN@northwintraders \. onmicrosoft.com                                                                                    |
    | PrimarySmtpAddress    | Lara \. Newton@northwind.com                                                                                                |
    | ExternalEmailAddress  | SMTP : LaraN@contoso \. onmicrosoft.com                                                                                       |
    | ExchangeGuid          | 1ec059c7-8396-4d0b-af4e-d6bd4c12a8d8                                                                                     |
    | LegacyExchangeDN      | /o = First Organization/ou = groupe d’administration Exchange                                                                   |
    |                       | (FYDIBOHF23SPDLT)/CN = RECIPIENTS/CN = 74e5385fce4b46d19006876949855035Lara                                                  |
    | EmailAddresses        | x500:/o = First Organization/ou = Exchange administrative Group (FYDIBOHF23SPDLT)/CN = RECIPIENTS/CN = d11ec1a2cacd4f81858c8190  |
    |                       | 7273f1f9-Lara                                                                                                            |
    |                       | SMTP : LaraN@northwindtraders \. onmicrosoft.com                                                                              |
    |                       | SMTP : Lara \. Newton@northwind.com                                                                                           |
    |||

   Exemple d’objet de boîte aux lettres **source** :

   | Attribut             | Valeur                                                                    |
   |-----------------------|--------------------------------------------------------------------------|
   | Alias                 | LaraN                                                                    |
   | RecipientType         | UserMailbox                                                              |
   | RecipientTypeDetails  | UserMailbox                                                              |
   | UserPrincipalName     | LaraN@contoso \. onmicrosoft.com                                            |
   | PrimarySmtpAddress    | Lara \. Newton@contoso.com                                                  |
   | ExchangeGuid          | 1ec059c7-8396-4d0b-af4e-d6bd4c12a8d8                                     |
   | LegacyExchangeDN      | /o = First Organization/ou = groupe d’administration Exchange                   |
   |                       | (FYDIBOHF23SPDLT)/CN = RECIPIENTS/CN = d11ec1a2cacd4f81858c81907273f1f9Lara  |
   | EmailAddresses        | SMTP : LaraN@contoso \. onmicrosoft.com 
   |                       | SMTP : Lara \. Newton@contoso.com          |
   |||

   - Des attributs supplémentaires peuvent être inclus dans la réécriture d’Exchange hybride. Si ce n’est pas le cas, ils doivent être inclus. 
   - msExchBlockedSendersHash – réécrit des données d’expéditeurs bloqués et bloqués en ligne à partir de clients vers Active Directory en local.
   - msExchSafeRecipientsHash – réécrit des données d’expéditeurs bloqués et bloqués en ligne à partir de clients vers Active Directory en local.
   - msExchSafeSendersHash – réécrit des données d’expéditeurs bloqués et bloqués en ligne à partir de clients vers Active Directory en local.

2. Si la boîte aux lettres source se trouve sur LitigationHold et que la taille des éléments récupérables de la boîte aux lettres source est supérieure à la taille de la base de données par défaut (30 Go), le déplacement ne se poursuit pas car le quota cible est inférieur à la taille de la boîte aux lettres source. Vous pouvez mettre à jour l’objet MailUser cible afin de faire passer les indicateurs de boîte aux lettres ELC de l’environnement source à la cible, ce qui déclenche le système cible afin de développer le quota du MailUser à 100 Go, ce qui permet le déplacement vers la cible. Ces instructions ne fonctionnent que pour une identité hybride exécutant Azure AD Connect, car les commandes de marquage des indicateurs ELC ne sont pas exposées aux administrateurs clients.

    >[!Note]
    > EXEMPLE, AUCUNE GARANTIE<br/>Ce script suppose une connexion à la boîte aux lettres source (pour obtenir les valeurs sources) et à la cible Active Directory locale (pour horodater l’objet ADUser). Si la source est en litige ou si la récupération d’élément unique est activée, définissez-la sur le compte de destination.  Cela augmente la taille de la benne du compte de destination à 100 Go.

    ```powershell
    $ELCValue = 0 
    if ($source.LitigationHoldEnabled) {$ELCValue = $ELCValue + 8} if ($source.SingleItemRecoveryEnabled) {$ELCValue = $ELCValue + 16} if ($ELCValue -gt 0) {Set-ADUser -Server $domainController -Identity $destination.SamAccountName -Replace @{msExchELCMailboxFlags=$ELCValue}} 
    ```
3. Les locataires cibles non hybrides peuvent modifier le quota sur le dossier éléments récupérables pour le MailUsers avant la migration en exécutant la commande suivante pour activer la conservation pour litige sur l’objet MailUser et augmenter le quota à 100 Go : `Set-MailUser -EnableLitigationHoldForMigration $TRUE` . Remarque cela ne fonctionnera pas pour les clients hybrides.

4. Les utilisateurs de l’organisation cible doivent disposer d’une licence avec les abonnements Exchange Online appropriés applicables à l’organisation. Vous pouvez appliquer une licence avant le déplacement d’une boîte aux lettres, mais uniquement une fois que le MailUser cible est correctement configuré avec des adresses ExchangeGUID et proxy. L’application d’une licence avant l’application de la ExchangeGUID entraînera la mise en service d’une nouvelle boîte aux lettres dans l’organisation cible. 

    > [!Note]
    > Lorsque vous appliquez une licence sur une boîte aux lettres ou un objet MailUser, tous les types SMTP proxyAddresses sont nettoyés afin de s’assurer que seuls les domaines vérifiés sont inclus dans le groupe Exchange EmailAddresses. 

5. Vous devez vous assurer que la MailUser cible n’a pas de ExchangeGuid précédent qui ne correspond pas à la source ExchangeGuid. Cela peut se produire si l’unité MEU cible était précédemment sous licence pour Exchange Online et qu’une boîte aux lettres a été configurée. Si la MailUser cible était déjà sous licence ou avait un ExchangeGuid qui ne correspond pas à la source ExchangeGuid, vous devez effectuer un nettoyage de l’unité MEU Cloud. Pour ces extension messagerie de Cloud, vous pouvez exécuter la `Set-User <identity> -PermanentlyClearPreviousMailboxInfo` commande. 

    > [!Caution]
    > Ce processus est irréversible. Si l’objet dispose d’une boîte aux lettres softDeleted, il ne peut pas être restauré après cette étape. Une fois l’effacement activé, vous pouvez synchroniser le ExchangeGuid correct vers l’objet cible et Mme connecter la boîte aux lettres source à la boîte aux lettres cible nouvellement créée. (Faites référence à un blog EHLO sur le nouveau paramètre.) 
 
    Recherchez les objets qui étaient auparavant des boîtes aux lettres à l’aide de cette commande.

    ```powershell
    Get-User <identity> | select Name, *recipient* | ft -a**.
    ```
    Voici un exemple. 

    ```powershell
    PS demo> get-user John@northwindtraders.com |select name, *recipient*| ft -AutoSize 
 
    Name        PreviousRecipientTypeDetails     RecipientType RecipientTypeDetails 
    ----       ---------------------------- ------------- -------------------- 
    John       UserMailbox                  MailUser      MailUser 
    ```   
 
    Effacez la boîte aux lettres supprimée (récupérable) à l’aide de cette commande.

    ````
    Set-User <identity> -PermanentlyClearPreviousMailboxInfo
    ```` 

    Voici un exemple.

    ```powershell
    PS demo> Set-User John@northwindtraders.com -PermanentlyClearPreviousMailboxInfo Confirm 
    Are you sure you want to perform this action? 
    Delete all existing information about user “John@northwindtraders.com"?. This operation will clear existing values from Previous home MDB and Previous Mailbox GUID of the user. After deletion, reconnecting to the previous mailbox that existed in the cloud will not be possible and any content it had will be unrecoverable PERMANENTLY. 
    Do you want to continue? 
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [?] Help (default is "Y"): Y 
    ```

## <a name="perform-mailbox-migrations"></a>Effectuer des migrations de boîtes aux lettres

Les migrations de boîtes aux lettres Exchange interclientes sont envoyées en tant que lots de migration initiés à partir du client cible. Cela est similaire à la façon dont fonctionnent les lots de migrations embarqués lors de la migration d’Exchange local vers Microsoft 365. 

### <a name="create-migration-batches"></a>Créer des lots de migration

Voici un exemple de cmdlet de lot de migration pour lancer des déplacements.

```powershell
New-MigrationBatch -Name T2Tbatch-testforignitedemo -SourceEndpoint target_source_7977 -CSVData ([System.IO.File]::ReadAllBytes('users.csv')) -Autostart -TargetDeliveryDomain targetformoves.onmicrosoft.com -AutoComplete

Identity                   Status  Type               TotalCount
--------                   ------  ----               ----------
T2Tbatch-testforignitedemo Syncing ExchangeRemoteMove 1

```

> [!Note]
> L’adresse de messagerie dans le fichier CSV doit être celle qui est spécifiée dans le client cible, et non le client source.

L’envoi de lots de migration est également pris en charge à partir du nouveau centre d’administration Exchange lors de la sélection de l’option de client intersites.
 
#### <a name="update-on-premises-mailusers"></a>Mettre à jour MailUsers en local

Une fois que la boîte aux lettres passe de la source à la cible, vous devez vous assurer que les utilisateurs de messagerie locaux, source et cible, sont mis à jour avec le nouvel targetAddress. Dans les exemples, le targetDeliveryDomain utilisé dans le déplacement est **contoso \. onmicrosoft.com**. Mettez à jour les utilisateurs de messagerie à l’aide de ce targetAddress.
 
## <a name="frequently-asked-questions"></a>Foire aux questions
 
**Faut-il mettre à jour RemoteMailboxes dans la source en local après le déplacement ?**
 
Oui, vous devez mettre à jour le targetAddress (RemoteRoutingAddress/ExternalEmailAddress) des utilisateurs locaux de la source lorsque la boîte aux lettres du client source passe au client cible.  Alors que le routage du courrier peut suivre les redirections entre plusieurs utilisateurs de messagerie avec différents targetAddresses, des recherches de disponibilité pour les utilisateurs de messagerie doivent cibler l’emplacement de l’utilisateur de la boîte aux lettres. Les recherches de disponibilité ne redirigeront pas plusieurs redirections. 
 
**Le contenu du dossier de conversation teams migre-t-il le client ?** 

Non, le contenu du dossier de conversation Teams ne migre pas les clients intersites. 
 
**Comment puis-je voir les déplacements intersites, pas mes déplacements d’intégration et de par débarquement ?**

Utilisez le `-flags` paramètre. Voici un exemple.

```powershell
Get-MoveRequest -Flags "CrossTenant" 
```
 
**Pouvez-vous fournir des exemples de scripts pour copier les attributs utilisés lors des tests ?**

> [!Note]
> EXEMPLE, AUCUNE GARANTIE<br/>Ce script suppose une connexion à la boîte aux lettres source (pour obtenir les valeurs sources) et aux services de domaine Active Directory locaux cibles (pour horodater l’objet ADUser). Si la source est en litige ou si la récupération d’élément unique est activée, définissez-la sur le compte de destination.  Cela augmente la taille de la benne du compte de destination à 100 Go.

```powershell
#Dumps out the test mailboxes from SourceTenant 
#Note, the filter applied on GetMailbox is for an attribute set on CA1 = “ProjectKermit” 
#These are the ‘target’ users to be moved to the Northwind org tenant #################################################################  
$outFile = "$home\desktop\UserListToImport.csv" 
$outArray = @() 
#output the test objects 
$Mailboxes = get-mailbox -filter "CustomAttribute1 -like ‘ProjectKermit'" -resultsize unlimited  
#created these mailboxes in adv using separate scripts but you get the idea on how to define the user list to move 
Foreach ($i in $Mailboxes)  
{ 
    $user = get-Recipient $i.alias 
    $myobj = New-Object System.Object 
    $myObj | Add-Member -type NoteProperty -name primarysmtpaddress -value $i.PrimarySMTPAddress 
    $myObj | Add-Member -type NoteProperty -name alias -value $i.alias 
    $myObj | Add-Member -type NoteProperty -name FirstName -value $User.FirstName 
    $myObj | Add-Member -type NoteProperty -name LastName -value $User.LastName 
    $myObj | Add-Member -type NoteProperty -name DisplayName -value $User.DisplayName 
    $myObj | Add-Member -type NoteProperty -name Name -value $i.Name 
    $myObj | Add-Member -type NoteProperty -name SamAccountName -value $i.SamAccountName 
    $myObj | Add-Member -type NoteProperty -name legacyExchangeDN -value $i.legacyExchangeDN    $myObj | Add-Member -type NoteProperty -name ExchangeGuid -value $i.ExchangeGuid 
    $outArray += $myObj 
} 
$outArray | Export-CSV $outfile -notypeinformation  
################################################################# 
#Copy the file $outfile to the desktop of the target on-premises 
#then run the below to create MEU in Target 
#################################################################  
$ImportUserList = import-csv "$home\desktop\UserListToImport.csv" 
$pwstr = "Something 98053 Random!!"; 
$pw = new-object "System.Security.SecureString"; 
for ($i=0; $i -lt $pwstr.Length; $i++) {$pw.AppendChar($pwstr[$i])} foreach ($user in $ImportUserList) { 
     $tmpUser = $null 
    $UPNSuffix = "@northwindtraders.com"    $UPN = $user.Alias+$upnsuffix 
    $tmpUser = New-MailUser -organization -UserPrincipalName $upn -ExternalEmailAddress $user.primarysmtpaddress -FirstName $user.FirstName ` 
                 -LastName $user.LastName -SamAccountName $user.SamAccountName -ResetPasswordOnNextLogon $false ` 
                 -Alias $user.alias -PrimarySmtpAddress $UPN -Name $User.Name -DisplayName $user.DisplayName ` 
                 -OrganizationalUnit "OU=ContosoUsers,OU=MLB,DC=ContosoLab,DC=net" -Password $pw       $x500 = "x500:" + $user.legacyExchangeDN 
    $tmpUser | Set-MailUser -ExchangeGuid $user.ExchangeGuid -EmailAddresses @{Add=$x500} -CustomAttribute1 "ProjectKermit" 
}  
################################################################# 
# On AADSync machine, run AADSync 
#################################################################  
Start-ADSyncSyncCycle 
 
#AADSync and FWDSync will create the target MEUs in the Target tenant 
```
**Comment accéder à Outlook le jour 1 après le déplacement de la boîte aux lettres d’utilisation ?**

Étant donné qu’un seul client peut être propriétaire d’un domaine, l’ancien SMTPAddress principal n’est pas associé à l’utilisateur dans le client cible lorsque le déplacement de boîte aux lettres est terminé ; uniquement les domaines associés au nouveau client. Outlook utilise le nouvel UPN de l’utilisateur pour s’authentifier auprès du service et le profil Outlook s’attend à trouver le SMTPAddress primaire hérité correspondant à la boîte aux lettres dans le système cible. Étant donné que l’adresse héritée ne se trouve pas dans le système cible, le profil Outlook ne se connecte pas pour trouver la boîte aux lettres nouvellement déplacée. 

Pour ce déploiement initial, les utilisateurs doivent reconstruire leur profil avec leur nouveau nom d’utilisateur principal, leur adresse SMTP principale et le contenu OST de nouvelle synchronisation. 

> [!Note]
> Planifiez-la en fonction de vos utilisateurs pour qu’ils soient terminés. Vous devez tenir compte de la capacité et de l’utilisation du réseau lors de la création des profils client Outlook, ainsi que dans les fichiers OST et OAB suivants. 
 
**Quels sont les rôles RBAC Exchange dont je dois être membre pour configurer ou terminer un déplacement entre clients ?**
 
Il s’agit d’une matrice de rôles basée sur l’hypothèse de droits délégués lors de l’exécution d’un déplacement de boîte aux lettres. Actuellement, deux rôles sont requis :  

- Le premier rôle concerne une tâche de configuration unique qui établit l’autorisation de transfert de contenu à l’intérieur ou à l’extérieur de votre limite client/organisation. Le fait de déménager des données de votre contrôle organisationnel est une préoccupation essentielle pour toutes les sociétés, nous avons opté pour le rôle le plus élevé de l’administrateur de l’organisation (OrgAdmin). Ce rôle doit modifier ou configurer un nouveau OrganizationRelationship qui définit le-MailboxMoveCapability avec l’organisation distante. Seul le OrgAdmin peut modifier le paramètre MailboxMoveCapability, tandis que d’autres attributs de l’OrganizationRelationhip peuvent être gérés par l’administrateur du partage fédéré. 
 
- Le rôle de l’exécution des commandes de déplacement réel peut être délégué à une fonction de niveau inférieur. Le rôle de déplacement de boîtes aux lettres est affecté à la possibilité de déplacer des boîtes aux lettres dans ou vers l’extérieur de l’organisation à l’aide du `-RemoteTenant` paramètre.  

**Comment puis-je cibler l’adresse SMTP sélectionnée pour targetAddress (TargetDeliveryDomain) sur la boîte aux lettres convertie (vers la conversion MailUser) ?**
 
La boîte aux lettres Exchange se déplace à l’aide de la fonction targetAddress de la boîte aux lettres source d’origine lors de la conversion en MailUser en fonction de la correspondance d’une adresse de messagerie (proxyAddress) sur l’objet cible. Le processus prend la valeur-TargetDeliveryDomain transmise à la commande de déplacement, puis recherche un proxy correspondant pour ce domaine sur le côté cible. Lorsque nous trouvons une correspondance, le proxyAddress correspondant est utilisé pour définir l’ExternalEmailAddress (targetAddress) sur l’objet boîte aux lettres converti (maintenant MailUser).
 
**Quelle est la transition des autorisations de boîte aux lettres ?**

Les autorisations de boîte aux lettres incluent l’accès envoyer de la part de et de la boîte aux lettres : 

- Envoyer de la part de (AD : publicDelegates) stocke le DN des destinataires ayant accès à la boîte aux lettres d’un utilisateur en tant que délégué. Cette valeur est stockée dans Active Directory et ne se déplace actuellement pas dans le cadre de la transition de boîte aux lettres. Si la boîte aux lettres source a publicDelegates définie, vous devez remarquer le publicDelegates sur la boîte aux lettres cible une fois que la conversion de l’unité MEU vers la boîte aux lettres est terminée dans l’environnement cible à l’aide de la `Set-Mailbox <principle> -GrantSendOnBehalfTo <delegate>` commande. 
 
- Les autorisations de boîte aux lettres qui sont stockées dans la boîte aux lettres seront déplacées avec la boîte aux lettres lorsque le principal et le délégué seront déplacés vers le système cible. Par exemple, l’utilisateur TestUser_7 bénéficie de l’autorisation FullAccess sur la boîte aux lettres TestUser_8 dans le client SourceCompany.onmicrosoft.com. Une fois le déplacement de la boîte aux lettres terminé vers TargetCompany.onmicrosoft.com, les mêmes autorisations sont configurées dans l’annuaire cible. Vous trouverez ci-dessous des exemples d’utilisation de *Get-MailboxPermission* pour les TestUser_7 dans les clients source et cible. Les cmdlets Exchange sont précédées de source et cible en conséquence. 
 
Voici un exemple de la sortie de l’autorisation de boîte aux lettres avant un déplacement. 

```powershell
PS C:\DEMO Get-SourceMailboxPermission testuser_7 |ft -AutoSize User, AccessRights, IsInherited, Deny
User                                             AccessRights                                                            IsInherited Deny
----                                             ------------                                                            ----------- ----
NT AUTHORITY\SELF                                {FullAccess, ReadPermission}                                            False       False
TestUser_8@SourceCompany.onmicrosoft.com         {FullAccess}                                                            False       False....
```
Voici un exemple de la sortie de l’autorisation de boîte aux lettres après le déplacement. 

```powershell
C:\DEMO> Get-TargetMailboxPermission testuser_7 | ft -AutoSize User, AccessRights, IsInherited, Deny
User                                             AccessRights                                                            IsInherited Deny
----                                             ------------                                                            ----------- ----
NT AUTHORITY\SELF                                {FullAccess, ReadPermission}                                            False       FalseTestUser_8@TargetCompany.onmicrosoft.com         {FullAccess}                                                            False       False
```
 
> [!Note]
> Les autorisations de calendrier et de boîte aux lettres entre les clients ne sont pas prises en charge. Vous devez organiser les principaux et les délégués en lots de déplacement consolidés afin que ces boîtes aux lettres connectées soient simultanément transférées à partir du client source. 
 
## <a name="known-issues"></a>Problèmes connus 

-  **Problème : les archives développées automatiquement ne peuvent pas être migrées.** La fonctionnalité de migration entre les clients prend en charge les migrations de la boîte aux lettres principale et de la boîte aux lettres d’archivage pour un utilisateur spécifique. Si, en revanche, l’utilisateur dans la source dispose d’un archivage développé automatiquement (plus d’une boîte aux lettres d’archivage), la fonctionnalité ne peut pas migrer les archives supplémentaires.

- **Problème : les MailUsers de Cloud avec un protocole SMTP proxyAddress Block Mme se déplace en arrière-plan.** Lors de la création d’objets MailUser de client cible, vous devez vous assurer que toutes les adresses proxy SMTP appartiennent à l’organisation cliente cible. S’il existe un proxyAddress SMTP sur l’utilisateur de messagerie cible qui n’appartient pas au client local, la conversion de MailUser en boîte aux lettres est bloquée. Cela est dû à notre assurance que les objets de boîte aux lettres peuvent uniquement envoyer des messages à partir de domaines pour lesquels le client fait autorité (domaines réclamés par le client) : 
- 
   - Lorsque vous synchronisez des utilisateurs sur site à l’aide d’Azure AD Connect, vous configurez des objets MailUser sur site avec ExternalEmailAddress pointant vers le client source où la boîte aux lettres existe (laran@contoso \. onmicrosoft.com) et vous marquez le PrimarySmtpAddress comme un domaine qui réside dans le client cible (Lara.Newton@northwind \. com). Ces valeurs sont synchronisées avec le client et un utilisateur de messagerie approprié est mis en service et prêt pour la migration. Un exemple d’objet est illustré ici.
     ```powershell
     target/AADSynced user] PS C> Get-MailUser laran | select ExternalEmailAddress, EmailAddresses   
     ExternalEmailAddress               EmailAddresses 
     --------------------               -------------- 
     SMTP:laran@contoso.onmicrosoft.com {SMTP:lara.newton@northwind.com} 
     ```

   > [!Note]
   > L’adresse *\. com contoso. onmicrosoft* n’est *pas* présente dans le tableau EmailAddresses/proxyAddresses.

- **Problème : les objets MailUser avec des adresses SMTP principales « externes » sont modifiés/réinitialisés sur les domaines « internes » demandés par l’entreprise**

   Les objets MailUser sont des pointeurs vers des boîtes aux lettres non locales. Dans le cas de migrations de boîtes aux lettres interclientes, nous utilisons les objets MailUser pour représenter la boîte aux lettres source (à partir de la perspective de l’organisation cible) ou la boîte aux lettres cible (du point de vue de l’organisation source). Le MailUsers aura un ExternalEmailAddress (targetAddress) qui pointe vers l’adresse SMTP de la boîte aux lettres réelle (ProxyTest \@ fabrikam \. onmicrosoft.com) et une adresse primarySMTP qui représente l’adresse SMTP affichée de l’utilisateur de boîte aux lettres dans l’annuaire. Certaines organisations choisissent d’afficher l’adresse SMTP principale en tant qu’adresse SMTP externe, et non en tant qu’adresse dont le client local est propriétaire (par exemple, fabrikam.com plutôt que contoso.com).  Toutefois, une fois qu’un objet de plan de service Exchange est appliqué au MailUser via des opérations de gestion des licences, l’adresse SMTP principale est modifiée pour apparaître sous la forme d’un domaine vérifié par l’organisation locale (contoso.com). Il existe deux raisons possibles :
   
   - Lorsqu’un plan de service Exchange est appliqué à un MailUser, le processus Azure AD commence à appliquer le nettoyage des proxys afin de s’assurer que l’organisation locale ne peut pas envoyer de courrier, d’usurper ou de courrier à partir d’un autre client. Toute adresse SMTP sur un objet destinataire avec ces plans de service sera supprimée si l’adresse n’est pas vérifiée par l’organisation locale. Comme dans l’exemple, le \. domaine com Fabikam n’est pas vérifié par le \. client onmicrosoft.com contoso, de sorte que le nettoyage supprime ce \. domaine com fabrikam. Si vous souhaitez conserver ce domaine externe sur MailUser, avant la migration ou après la migration, vous devez modifier vos processus de migration afin de supprimer les licences à la fin du déplacement ou avant de vous assurer que les utilisateurs disposent de la personnalisation externe attendue. Vous devez vous assurer que l’objet boîte aux lettres est correctement concédé sous licence pour ne pas affecter le service de messagerie.<br/><br/>Un exemple de script permettant de supprimer les plans de service sur un MailUser dans le \. client onmicrosoft.com contoso est illustré ici.

    ```powershell
    $LO = New-MsolLicenseOptions -AccountSkuId "contoso:ENTERPRISEPREMIUM" DisabledPlans 
    "LOCKBOX_ENTERPRISE","EXCHANGE_S_ENTERPRISE","INFORMATION_BARRIERS","MIP_S_CLP2","
    MIP_S_CLP1","MYANALYTICS_P2","EXCHANGE_ANALYTICS","EQUIVIO_ANALYTICS","THREAT_INTE
    LLIGENCE","PAM_ENTERPRISE","PREMIUM_ENCRYPTION" 
    Set-MsolUserLicense -UserPrincipalName proxytest@contoso.com LicenseOptions $lo 
    ```

       Les résultats dans l’ensemble des ServicePlans attribués sont indiqués ici.

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
 
       La PrimarySMTPAddress de l’utilisateur n’est plus nettoyée. Le domaine fabrikam.com n’est pas détenu par le client contoso.onmicrosoft.com et sera conservé comme adresse SMTP principale affichée dans l’annuaire.

       Voici un exemple.

    ```powershell
    get-recipient proxytest | ft -a userprin*, primary*, external*   
    PrimarySmtpAddress        ExternalDirectoryObjectId               ExternalEmailAddress 
    ------------------        -------------------------               -------------------- 
    proxytest@fabrikam.com    e2513482-1d5b-4066-936a-cbc7f8f6f817    SMTP:proxytest@fabrikam.com 
    ```

   - Lorsque msExchRemoteRecipientType est défini sur 8 (DeprovisionMailbox), pour les MailUsers sur site qui sont migrées vers le client cible, la logique de purge du proxy dans Azure supprime les domaines non détenus et réinitialise l’primarySMTP sur un domaine appartenant. En effaçant msExchRemoteRecipientType dans la MailUser locale, la logique de nettoyage du proxy ne s’applique plus. <br/><br>Vous trouverez ci-dessous l’ensemble complet des plans de service possibles qui incluent Exchange Online.

   | Nom                                              |
   |---------------------------------------------------|
   | Stockage eDiscovery avancé (500 Go)               |
   | Référentiel sécurisé client                                  |
   | Protection contre la perte de données                              |
   | Services de licence d’accès client Exchange Enterprise (EOP, DLP)       |
   | Exchange Essentials                               |
   | Exchange Foundation                               |
   | Exchange Online (P1)                              |
   | Exchange Online (plan 1)                          |
   | Exchange Online (plan 2)                          |
   | Archivage Exchange Online pour Exchange Online     |
   | Archivage Exchange Online pour Exchange Server     |
   | Complément utilisateur inactif Exchange Online              |
   | Exchange Online Kiosk                             |
   | Exchange Online Multi-Geo                         |
   | Exchange Online (plan 1)                            |
   | POP Exchange Online                               |
   | Exchange Online Protection                        |
   | Barrières des informations                              |
   | Protection des informations pour Office 365 – Premium   |
   | Protection des informations pour Office 365 – Standard  |
   | Insights par MyAnalytics                           |
   | Audit avancé Microsoft 365                   |
   | Microsoft Bookings                                |
   | Centre d’affaires Microsoft                         |
   | Microsoft MyAnalytics (complet)                      |
   | Office 365 Advanced eDiscovery                    |
   | Microsoft Defender pour Office 365 (plan 1)    |
   | Microsoft Defender pour Office 365 (plan 2)    |
   | Office 365 Privileged Access Management           |
   | Chiffrement Premium dans Office 365                  |
    
