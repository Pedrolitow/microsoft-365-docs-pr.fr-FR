---
title: Prise en charge d’Azure Information Protection pour les Office 365 exploités par 21Vianet
f1.keywords:
- NOCSH
ms.author: sharik
author: skjerland
manager: scotv
audience: Admin
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- MET150
- GEU150
- GEA150
description: En savoir plus sur Azure Information Protection (AIP) pour Office 365 géré par 21Vianet et comment le configurer pour les clients en Chine.
monikerRange: o365-21vianet
ms.openlocfilehash: 3b4906844c76293a1163d17d77b009528ef32f12
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64782894"
---
# <a name="azure-information-protection-support-for-office-365-operated-by-21vianet"></a>Prise en charge d’Azure Information Protection pour les Office 365 exploités par 21Vianet

Cet article décrit les différences entre la prise en charge d’Azure Information Protection (AIP) pour les Office 365 exploités par 21Vianet et les offres commerciales, ainsi que des instructions spécifiques pour la configuration d’AIP pour les clients en Chine&mdash;, qui expliquent comment installer le scanneur local AIP et gérer les travaux d’analyse de contenu.

## <a name="differences-between-aip-for-office-365-operated-by-21vianet-and-commercial-offerings"></a>Différences entre AIP pour les Office 365 exploités par 21Vianet et les offres commerciales

Bien que notre objectif soit de fournir toutes les fonctionnalités commerciales aux clients en Chine avec notre AIP pour Office 365 géré par l’offre 21Vianet, nous aimerions mettre en évidence certaines fonctionnalités manquantes.

La liste suivante inclut les écarts existants entre AIP pour Office 365 exploitées par 21Vianet et nos offres commerciales à partir de janvier 2021 :

- le chiffrement services AD RMS (Active Directory Rights Management Services) (AD RMS) est pris en charge uniquement dans Applications Microsoft 365 pour les grandes entreprises (build 11731.10000 ou ultérieure). Office Professionnel Plus ne prend pas en charge AD RMS.

- La migration d’AD RMS vers AIP n’est actuellement pas disponible.
  
- Le partage d’e-mails protégés avec des utilisateurs dans le cloud commercial est pris en charge.
  
- Le partage de documents et de pièces jointes avec des utilisateurs dans le cloud commercial n’est actuellement pas disponible. Cela inclut les Office 365 gérées par 21 utilisateursVianet dans le cloud commercial, les utilisateurs non Office 365 gérés par 21Vianet dans le cloud commercial et les utilisateurs disposant d’une licence RMS for Individuals.
  
- Irm avec SharePoint (sites et bibliothèques protégés par IRM) n’est actuellement pas disponible.
  
- L’extension d’appareil mobile pour AD RMS n’est actuellement pas disponible.

- La [visionneuse mobile](/azure/information-protection/rms-client/mobile-app-faq) n’est pas prise en charge par Azure China 21Vianet.

- La zone AIP du Portail Azure n’est pas disponible pour les clients en Chine. Utilisez [des commandes PowerShell](#step-6-install-the-aip-on-premises-scanner-and-manage-content-scan-jobs) au lieu d’effectuer des actions dans le portail, telles que la gestion et l’exécution de vos travaux d’analyse de contenu.

- Les points de terminaison AIP dans Office 365 gérés par 21Vianet sont différents des points de terminaison requis pour d’autres services cloud. Une connectivité réseau entre les clients et les points de terminaison suivants est requise :
    - Téléchargez les stratégies d’étiquette et d’étiquette : `*.protection.partner.outlook.cn`
    - service Azure Rights Management :`*.aadrm.cn`

## <a name="configure-aip-for-customers-in-china"></a>Configurer AIP pour les clients en Chine

Pour configurer AIP pour les clients en Chine :
1. [Activez Rights Management pour le locataire](#step-1-enable-rights-management-for-the-tenant).

1. [Ajoutez le principal du service de synchronisation Protection des données Microsoft](#step-2-add-the-microsoft-information-protection-sync-service-service-principal).

1. [Configurez le chiffrement DNS](#step-3-configure-dns-encryption).

1. [Installez et configurez le client d’étiquetage unifié AIP](#step-4-install-and-configure-the-aip-unified-labeling-client).

1. [Configurez des applications AIP sur Windows](#step-5-configure-aip-apps-on-windows).

1. [Installez le scanneur local AIP et gérez les travaux d’analyse de contenu](#step-6-install-the-aip-on-premises-scanner-and-manage-content-scan-jobs). 

### <a name="step-1-enable-rights-management-for-the-tenant"></a>Étape 1 : Activer Rights Management pour le locataire

Pour que le chiffrement fonctionne correctement, RMS doit être activé pour le locataire.

1. Vérifiez si RMS est activé :

    1. Lancez PowerShell en tant qu’administrateur.
    2. Si le module AIPService n’est pas installé, exécutez `Install-Module AipService`.
    3. Importez le module à l’aide de `Import-Module AipService`.
    4. Connecter au service à l’aide `Connect-AipService -environmentname azurechinacloud`de .
    5. Exécutez `(Get-AipServiceConfiguration).FunctionalState` et vérifiez si l’état est `Enabled`.

2. Si l’état fonctionnel est `Disabled`, exécutez `Enable-AipService`.

### <a name="step-2-add-the-microsoft-information-protection-sync-service-service-principal"></a>Étape 2 : Ajouter le principal du service de synchronisation Protection des données Microsoft

Le **principal du service de synchronisation Protection des données Microsoft** n’est pas disponible par défaut dans les locataires Azure China et est requis pour Azure Information Protection. Créez ce principal de service manuellement via le module Azure Az PowerShell.

1. Si le module Azure Az n’est pas installé, installez-le ou utilisez une ressource dans laquelle le module Azure Az est préinstallé, comme [Azure Cloud Shell](/azure/cloud-shell/overview). Pour plus d’informations, consultez [Installer le module Azure Az PowerShell](/powershell/azure/install-az-ps).

1. Connecter au service à l’aide de [l’applet de commande Connecter-AzAccount](/powershell/module/az.accounts/Connect-AzAccount) et du nom de l’environnement `azurechinacloud` :

    ```powershell
    Connect-azaccount -environmentname azurechinacloud
    ```

1. Créez manuellement le principal du **service Protection des données Microsoft Sync** à l’aide de l’applet de commande [New-AzADServicePrincipal](/powershell/module/az.resources/new-azadserviceprincipal) et de l’ID `870c4f2e-85b6-4d43-bdda-6ed9a579b725` d’application du service de synchronisation Protection des données Microsoft :

    ```powershell 
    New-AzADServicePrincipal -ApplicationId 870c4f2e-85b6-4d43-bdda-6ed9a579b725
    ```

1. Après avoir ajouté le principal de service, ajoutez les autorisations appropriées requises pour le service.

### <a name="step-3-configure-dns-encryption"></a>Étape 3 : Configurer le chiffrement DNS

Pour que le chiffrement fonctionne correctement, Office applications clientes doivent se connecter à l’instance chine du service et démarrer à partir de là. Pour rediriger des applications clientes vers l’instance de service appropriée, l’administrateur client doit configurer un enregistrement SRV DNS avec des informations sur l’URL Azure RMS. Sans l’enregistrement SRV DNS, l’application cliente tente par défaut de se connecter à l’instance de cloud public et échoue.

En outre, l’hypothèse est que les utilisateurs se connectent avec un nom d’utilisateur basé sur le domaine appartenant au locataire (par exemple, `joe@contoso.cn`), et non le `onmschina` nom d’utilisateur (par exemple, `joe@contoso.onmschina.cn`). Le nom de domaine du nom d’utilisateur est utilisé pour la redirection DNS vers l’instance de service appropriée.

#### <a name="configure-dns-encryption---windows"></a>Configurer le chiffrement DNS - Windows

1. Obtenez l’ID RMS :

    1. Lancez PowerShell en tant qu’administrateur.
    2. Si le module AIPService n’est pas installé, exécutez `Install-Module AipService`.
    3. Connecter au service à l’aide `Connect-AipService -environmentname azurechinacloud`de .
    4. Exécutez cette commande `(Get-AipServiceConfiguration).RightsManagementServiceId` pour obtenir l’ID RMS.

2. Connectez-vous à votre fournisseur DNS, accédez aux paramètres DNS du domaine, puis ajoutez un nouvel enregistrement SRV.

    - Service = `_rmsredir`
    - Protocole = `_http`
    - Name = `_tcp`
    - Target = `[GUID].rms.aadrm.cn` (où GUID est l’ID RMS)
    - Priority, Weight, Seconds, TTL = valeurs par défaut

3. Associez le domaine personnalisé au locataire dans le [Portail Azure](https://portal.azure.cn/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Domains). Cela ajoute une entrée dans DNS, qui peut prendre plusieurs minutes pour être vérifiée après avoir ajouté la valeur aux paramètres DNS.

4. Connectez-vous au Centre d'administration Microsoft 365 avec les informations d’identification d’administrateur général correspondantes et ajoutez le domaine (par exemple, `contoso.cn`) pour la création d’utilisateurs. Dans le processus de vérification, des modifications DNS supplémentaires peuvent être nécessaires. Une fois la vérification effectuée, les utilisateurs peuvent être créés.

#### <a name="configure-dns-encryption---mac-ios-android"></a>Configurer le chiffrement DNS - Mac, iOS, Android

Connectez-vous à votre fournisseur DNS, accédez aux paramètres DNS du domaine, puis ajoutez un nouvel enregistrement SRV.

- Service = `_rmsdisco`
- Protocole = `_http`
- Name = `_tcp`
- Cible = `api.aadrm.cn`
- Port = `80`
- Priority, Weight, Seconds, TTL = valeurs par défaut


### <a name="step-4-install-and-configure-the-aip-unified-labeling-client"></a>Étape 4 : Installer et configurer le client d’étiquetage unifié AIP

Téléchargez et installez le client d’étiquetage unifié AIP à partir du [Centre de téléchargement Microsoft](https://www.microsoft.com/download/details.aspx?id=53018).

Pour plus d’informations, reportez-vous aux rubriques suivantes :

- [Documentation AIP](/azure/information-protection/)
- [Historique des versions AIP et stratégie de support](/azure/information-protection/rms-client/unifiedlabelingclient-version-release-history)
- [Configuration système requise pour AIP](/azure/information-protection/requirements)
- [Démarrage rapide AIP : Déployer le client AIP](/azure/information-protection/quickstart-deploy-client)
- [Guide de l’administrateur AIP](/azure/information-protection/rms-client/clientv2-admin-guide)
- [Guide de l’utilisateur AIP](/azure/information-protection/rms-client/clientv2-user-guide)
- [En savoir plus sur les étiquettes de confidentialité Microsoft 365](../../compliance/sensitivity-labels.md)

### <a name="step-5-configure-aip-apps-on-windows"></a>Étape 5 : Configurer des applications AIP sur Windows

Les applications AIP sur Windows ont besoin de la clé de Registre suivante pour les pointer vers le cloud souverain approprié pour Azure Chine :

- Nœud de Registre = `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\MSIP`
- Name = `CloudEnvType`
- Valeur = `6` (valeur par défaut = 0)
- Type = `REG_DWORD`

> [!IMPORTANT]
> Veillez à ne pas supprimer la clé de Registre après une désinstallation. Si la clé est vide, incorrecte ou inexistante, la fonctionnalité se comporte comme la valeur par défaut (valeur par défaut = 0 pour le cloud commercial). Si la clé est vide ou incorrecte, une erreur d’impression est également ajoutée au journal.

### <a name="step-6-install-the-aip-on-premises-scanner-and-manage-content-scan-jobs"></a>Étape 6 : Installer le scanneur local AIP et gérer les travaux d’analyse de contenu

Installez le scanneur local AIP pour analyser vos partages de réseau et de contenu à la recherche de données sensibles, et appliquer des étiquettes de classification et de protection comme configurés dans la stratégie de votre organisation.

Lors de la configuration et de la gestion de vos travaux d’analyse de contenu, utilisez la procédure suivante au lieu de [l’interface Portail Azure](/azure/information-protection/deploy-aip-scanner-configure-install?tabs=azure-portal-only) utilisée par les offres commerciales.

Pour plus d’informations, consultez [Qu’est-ce qu’Azure Information Protection scanneur d’étiquetage unifié ?](/azure/information-protection/deploy-aip-scanner) et [Gérez vos travaux d’analyse de contenu uniquement à l’aide de PowerShell](/azure/information-protection/deploy-aip-scanner-prereqs#use-powershell-with-a-disconnected-computer).

**Pour installer et configurer votre scanneur** :

1. Connectez-vous à l’ordinateur Windows Server qui exécutera le scanneur. Utilisez un compte disposant de droits d’administrateur local et disposant des autorisations nécessaires pour écrire dans la base de données master SQL Server.

1. Commencez par la fermeture de PowerShell. Si vous avez déjà installé le client et le scanneur AIP, assurez-vous que le service **AIPScanner** est arrêté.

1. Ouvrez une session Windows PowerShell avec l’option **Exécuter en tant qu’administrateur**.

1. Exécutez l’applet de commande [Install-AIPScanner](/powershell/module/azureinformationprotection/Install-AIPScanner), en spécifiant votre instance SQL Server sur laquelle créer une base de données pour le scanneur Azure Information Protection et un nom explicite pour votre cluster de scanneur.

    ```PowerShell
    Install-AIPScanner -SqlServerInstance <name> -Cluster <cluster name>
    ```

    > [!TIP]
    > Vous pouvez utiliser le même nom de cluster dans la commande [Install-AIPScanner](/powershell/module/azureinformationprotection/install-aipscanner) pour associer plusieurs nœuds de scanneur au même cluster. L’utilisation du même cluster pour plusieurs nœuds de scanneur permet à plusieurs scanneurs de fonctionner ensemble pour effectuer vos analyses.
    > 

1. Vérifiez que le service est maintenant installé à l’aide **d’Administrative** **ToolsServices** > .

    Le service installé est nommé **Azure Information Protection Scanner** et est configuré pour s’exécuter à l’aide du compte de service de scanneur que vous avez créé.

1. Obtenez un jeton Azure à utiliser avec votre scanneur. Un jeton Azure AD permet au scanneur de s’authentifier auprès du service Azure Information Protection, ce qui permet au scanneur de s’exécuter de manière non interactive. 

    1. Ouvrez le Portail Azure et créez une application Azure AD pour spécifier un jeton d’accès pour l’authentification. Pour plus d’informations, consultez [Comment étiqueter des fichiers de manière non interactive pour Azure Information Protection](/azure/information-protection/rms-client/clientv2-admin-guide-powershell#how-to-label-files-non-interactively-for-azure-information-protection).
    
        > [!TIP]
        > Lorsque vous créez et configurez Azure AD applications pour la commande [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication), le volet **Demander des autorisations d’API** affiche les **API utilisées par mon organisation** à la place de l’onglet **API Microsoft**. Sélectionnez les **API utilisées par mon organisation** pour sélectionner **Azure Rights Management Services**. 
        >

    1. À partir de l’ordinateur Windows Server, si votre compte de service de scanneur a reçu l’ouverture de session **localement** pour l’installation, connectez-vous avec ce compte et démarrez une session PowerShell. 
    
        Si votre compte de service de scanneur ne peut pas se voir accorder l’ouverture de session **localement** pour l’installation, utilisez le paramètre *OnBehalfOf* avec [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication), comme décrit dans [Comment étiqueter des fichiers de manière non interactive pour Azure Information Protection](/azure/information-protection/rms-client/clientv2-admin-guide-powershell#how-to-label-files-non-interactively-for-azure-information-protection).

    1. [Exécutez Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication), en spécifiant les valeurs copiées à partir de votre application Azure AD :

      ```PowerShell
      Set-AIPAuthentication -AppId <ID of the registered app> -AppSecret <client secret sting> -TenantId <your tenant ID> -DelegatedUser <Azure AD account>
      ```

      Par exemple :

      ```PowerShell
      $pscreds = Get-Credential CONTOSO\scanner
      Set-AIPAuthentication -AppId "77c3c1c3-abf9-404e-8b2b-4652836c8c66" -AppSecret "OAkk+rnuYc/u+]ah2kNxVbtrDGbS47L4" -DelegatedUser scanner@contoso.com -TenantId "9c11c87a-ac8b-46a3-8d5c-f4d0b72ee29a" -OnBehalfOf $pscreds
      Acquired application access token on behalf of CONTOSO\scanner.
      ```

    Le scanneur dispose désormais d’un jeton pour s’authentifier auprès de Azure AD. Ce jeton est valide pendant un an, deux ans ou jamais, en fonction de votre configuration de la clé secrète client **d’application web/API** dans Azure AD. Lorsque le jeton expire, vous devez répéter cette procédure.

1. Exécutez l’applet de commande [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/set-aipscannerconfiguration) pour définir le scanneur pour qu’il fonctionne en mode hors connexion. Exécuter : 

    ```powershell
    Set-AIPScannerConfiguration -OnlineConfiguration Off
    ```

1. Exécutez l’applet [de commande Set-AIPScannerContentScanJob](/powershell/module/azureinformationprotection/set-aipscannercontentscanjob) pour créer un travail d’analyse de contenu par défaut.

    Le seul paramètre requis dans l’applet de commande **Set-AIPScannerContentScanJob** est **Enforce**. Toutefois, vous pouvez définir d’autres paramètres pour votre travail d’analyse de contenu pour le moment. Par exemple :

    ```powershell
    Set-AIPScannerContentScanJob -Schedule Manual -DiscoverInformationTypes PolicyOnly -Enforce Off -DefaultLabelType PolicyDefault -RelabelFiles Off -PreserveFileDetails On -IncludeFileTypes '' -ExcludeFileTypes '.msg,.tmp' -DefaultOwner <account running the scanner>
    ```

    La syntaxe ci-dessus configure les paramètres suivants pendant que vous poursuivez la configuration :

    - Maintient manuellement la *planification de* l’exécution du scanneur
    - Définit les types d’informations à découvrir en fonction de la stratégie d’étiquetage de confidentialité
    - *N’applique pas* de stratégie d’étiquetage de confidentialité
    - Étiquettes automatiques des fichiers en fonction du contenu, à l’aide de l’étiquette par défaut définie pour la stratégie d’étiquetage de confidentialité
    - Ne permet *pas* de réétiqueter des fichiers
    - Conserve les détails du fichier lors de l’analyse et de l’étiquetage automatique, y compris la *date de modification*, *la dernière modification* et *la modification par* les valeurs
    - Définit le scanneur pour exclure les fichiers .msg et .tmp lors de l’exécution
    - Définit le propriétaire par défaut sur le compte que vous souhaitez utiliser lors de l’exécution du scanneur

1. Utilisez l’applet de commande [Add-AIPScannerRepository](/powershell/module/azureinformationprotection/add-aipscannerrepository) pour définir les référentiels que vous souhaitez analyser dans votre travail d’analyse de contenu. Par exemple, exécutez :

    ```powershell
    Add-AIPScannerRepository -OverrideContentScanJob Off -Path 'c:\repoToScan'
    ```
    
    Utilisez l’une des syntaxes suivantes, selon le type de référentiel que vous ajoutez :

    - Pour un partage réseau, utilisez `\\Server\Folder`.
    - Pour une bibliothèque SharePoint, utilisez `http://sharepoint.contoso.com/Shared%20Documents/Folder`.
    - Pour un chemin local : `C:\Folder`
    - Pour un chemin UNC : `\\Server\Folder`

    > [!NOTE]
    > Les caractères génériques ne sont pas pris en charge et les emplacements WebDav ne sont pas pris en charge.
    >
    > Pour modifier le référentiel ultérieurement, utilisez plutôt l’applet de commande [Set-AIPScannerRepository](/powershell/module/azureinformationprotection/set-aipscannerrepository) . 


Suivez les étapes suivantes en fonction des besoins :

- [Exécuter un cycle de découverte et afficher les rapports pour le scanneur](/azure/information-protection/deploy-aip-scanner-manage#run-a-discovery-cycle-and-view-reports-for-the-scanner)
- [Utiliser PowerShell pour configurer le scanneur pour appliquer la classification et la protection](/azure/information-protection/deploy-aip-scanner-configure-install?tabs=azure-portal-only#use-powershell-to-configure-the-scanner-to-apply-classification-and-protection)
- [Utiliser PowerShell pour configurer une stratégie DLP avec le scanneur](/azure/information-protection/deploy-aip-scanner-configure-install?tabs=azure-portal-only#use-powershell-to-configure-a-dlp-policy-with-the-scanner)

Le tableau suivant répertorie les applets de commande PowerShell pertinentes pour installer le scanneur et gérer vos travaux d’analyse de contenu :

| Applet de commande | Description |
|--|--|
| [Add-AIPScannerRepository](/powershell/module/azureinformationprotection/add-aipscannerrepository) | Ajoute un nouveau référentiel à votre travail d’analyse de contenu. |
| [Get-AIPScannerConfiguration](/powershell/module/azureinformationprotection/get-aipscannerconfiguration)|Retourne des détails sur votre cluster. |
| [Get-AIPScannerContentScanJob](/powershell/module/azureinformationprotection/get-aipscannercontentscanjob) | Obtient des détails sur votre travail d’analyse de contenu. |
| [Get-AIPScannerRepository](/powershell/module/azureinformationprotection/get-aipscannerrepository) | Obtient des détails sur les référentiels définis pour votre travail d’analyse de contenu. |
| [Remove-AIPScannerContentScanJob](/powershell/module/azureinformationprotection/remove-aipscannercontentscanjob) | Supprime votre travail d’analyse de contenu. |
| [Remove-AIPScannerRepository](/powershell/module/azureinformationprotection/remove-aipscannerrepository) | Supprime un référentiel de votre travail d’analyse de contenu. |
| [Set-AIPScannerContentScanJob](/powershell/module/azureinformationprotection/set-aipscannercontentscanjob) | Définit les paramètres de votre travail d’analyse de contenu. |
| [Set-AIPScannerRepository](/powershell/module/azureinformationprotection/set-aipscannerrepository) | Définit les paramètres d’un référentiel existant dans votre travail d’analyse de contenu. |
| | |

Pour plus d’informations, reportez-vous aux rubriques suivantes :

- [Qu’est-ce que le scanneur d’étiquetage unifié Azure Information Protection ?](/azure/information-protection/deploy-aip-scanner)
- [Configuration et installation du scanneur d’étiquetage unifié Azure Information Protection (AIP)](/azure/information-protection/deploy-aip-scanner-configure-install?tabs=powershell-only)
- [Gérez vos travaux d’analyse de contenu uniquement à l’aide de PowerShell](/azure/information-protection/deploy-aip-scanner-prereqs#use-powershell-with-a-disconnected-computer).
