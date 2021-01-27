---
title: Prise en charge d’Azure Information Protection pour Office 365 géré par 21Vianet
f1.keywords:
- NOCSH
ms.author: sharik
author: skjerland
manager: scotv
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
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
ms.openlocfilehash: cee50384587ffc3e1e43eb9c6bb07d2e0ced7e13
ms.sourcegitcommit: cbe8724bd71d1c002395d98f1451c5f578c824f9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2021
ms.locfileid: "49988043"
---
# <a name="azure-information-protection-support-for-office-365-operated-by-21vianet"></a>Prise en charge d’Azure Information Protection pour Office 365 géré par 21Vianet

Cet article décrit les différences entre la prise en charge d’Azure Information Protection (AIP) pour Office 365 géré par 21Vianet et les offres commerciales, ainsi que des instructions spécifiques pour configurer AIP pour les clients en Chine, notamment comment installer le scanneur AIP local et gérer les travaux d’analyse de &mdash; contenu.

## <a name="differences-between-aip-for-office-365-operated-by-21vianet-and-commercial-offerings"></a>Différences entre AIP pour Office 365 géré par 21Vianet et les offres commerciales

Bien que notre objectif soit de fournir toutes les fonctionnalités commerciales aux clients en Chine avec notre offre AIP pour Office 365 gérée par 21Vianet, certaines fonctionnalités manquantes sont à mettre en évidence.

La liste suivante inclut les lacunes existantes entre AIP pour Office 365 géré par 21Vianet et nos offres commerciales depuis janvier 2021 :

- La gestion des droits de l’information (IRM) est prise en charge uniquement pour les applications Microsoft 365 pour les entreprises (build 11731.10000 ou supérieure). Office 2010, Office 2013 et les autres versions d’Office 2016 ne sont pas pris en charge.

- La migration de services AD RMS (Active Directory Rights Management Services) (AD RMS) vers AIP n’est actuellement pas disponible.
  
- Le partage de messages électroniques protégés avec des utilisateurs dans le cloud commercial est pris en charge.
  
- Le partage de documents et de pièces jointes de courrier électronique avec des utilisateurs dans le cloud commercial n’est actuellement pas disponible. Cela inclut les utilisateurs d’Office 365 gérés par 21Vianet dans le cloud commercial, les utilisateurs non-Office 365 gérés par les utilisateurs 21Vianet dans le cloud commercial et les utilisateurs titulaires d’une licence RMS pour les particuliers.
  
- Irm avec SharePoint (sites et bibliothèques protégés par IRM) n’est actuellement pas disponible.
  
- L’extension d’appareil mobile pour AD RMS n’est actuellement pas disponible.

- La [visionneuse mobile n’est](/azure/information-protection/rms-client/mobile-app-faq) pas prise en charge par Azure China 21Vianet.

## <a name="configure-aip-for-customers-in-china"></a>Configurer AIP pour les clients en Chine

Pour configurer AIP pour les clients en Chine :
1. [Activez la gestion des droits pour le client.](#step-1-enable-rights-management-for-the-tenant)

2. [Configurer le chiffrement DNS.](#step-2-configure-dns-encryption)

3. [Installez et configurez le client d’étiquetage unifié AIP.](#step-3-install-and-configure-the-aip-unified-labeling-client)

4. [Configurer les applications AIP sur Windows](#step-4-configure-aip-apps-on-windows).

5. [Installez le scanneur AIP local](#step-5-install-the-aip-on-premises-scanner-and-manage-content-scan-jobs)et gérez les travaux d’analyse de contenu. 

### <a name="step-1-enable-rights-management-for-the-tenant"></a>Étape 1 : Activer la gestion des droits pour le client

Pour que le chiffrement fonctionne correctement, RMS doit être activé pour le client.

1. Vérifiez si RMS est activé :

    1. Lancez PowerShell en tant qu’administrateur.
    2. Si le module AIPService n’est pas installé, exécutez `Install-Module AipService` .
    3. Importer le module à l’aide `Import-Module AipService` de .
    4. Connectez-vous au service à l’aide `Connect-AipService -environmentname azurechinacloud` de .
    5. Exécutez `(Get-AipServiceConfiguration).FunctionalState` et vérifiez si l’état `Enabled` est .

2. Si l’état fonctionnel est `Disabled` , exécutez `Enable-AipService` .

### <a name="step-2-configure-dns-encryption"></a>Étape 2 : Configurer le chiffrement DNS

Pour que le chiffrement fonctionne correctement, les applications clientes Office doivent se connecter à l’instance chine du service et s’y connecter. Pour rediriger les applications clientes vers l’instance de service de droite, l’administrateur client doit configurer un enregistrement SRV DNS avec des informations sur l’URL Azure RMS. Sans l’enregistrement SRV DNS, l’application cliente tentera par défaut de se connecter à l’instance de cloud public et échouera.

En outre, l’hypothèse est que les utilisateurs se connectent avec un nom d’utilisateur basé sur le domaine du client (par exemple, ), et non le nom d’utilisateur `joe@contoso.cn` `onmschina` (par exemple, `joe@contoso.onmschina.cn` ). Le nom de domaine du nom d’utilisateur est utilisé pour la redirection DNS vers l’instance de service correcte.

#### <a name="configure-dns-encryption---windows"></a>Configurer le chiffrement DNS - Windows

1. Obtenez l’ID RMS :

    1. Lancez PowerShell en tant qu’administrateur.
    2. Si le module AIPService n’est pas installé, exécutez `Install-Module AipService` .
    3. Connectez-vous au service à l’aide `Connect-AipService -environmentname azurechinacloud` de .
    4. Exécutez `(Get-AipServiceConfiguration).RightsManagementServiceId` pour obtenir l’ID RMS.

2. Connectez-vous à votre fournisseur DNS, accédez aux paramètres DNS du domaine, puis ajoutez un nouvel enregistrement SRV.

    - Service = `_rmsredir`
    - Protocole = `_http`
    - Name = `_tcp`
    - Target = `[GUID].rms.aadrm.cn` (où GUID est l’ID RMS)
    - Priority, Weight, Seconds, TTL = default values

3. Associez le domaine personnalisé au client dans [le portail Azure.](https://portal.azure.cn/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Domains) Cela ajoute une entrée dans DNS, qui peut prendre plusieurs minutes pour être vérifiée après avoir ajouté la valeur aux paramètres DNS.

4. Connectez-vous au Centre d’administration Microsoft 365 avec les informations d’identification d’administrateur global correspondantes et ajoutez le domaine (par exemple, ) pour la création `contoso.cn` d’utilisateurs. Dans le processus de vérification, des modifications DNS supplémentaires peuvent être nécessaires. Une fois la vérification effectuée, les utilisateurs peuvent être créés.

#### <a name="configure-dns-encryption---mac-ios-android"></a>Configurer le chiffrement DNS - Mac, iOS, Android

Connectez-vous à votre fournisseur DNS, accédez aux paramètres DNS du domaine, puis ajoutez un nouvel enregistrement SRV.

- Service = `_rmsdisco`
- Protocole = `_http`
- Name = `_tcp`
- Target = `api.aadrm.cn`
- Port = `80`
- Priority, Weight, Seconds, TTL = default values

### <a name="step-3-install-and-configure-the-aip-unified-labeling-client"></a>Étape 3 : Installer et configurer le client d’étiquetage unifié AIP

Téléchargez le client d’étiquetage unifié AIP à partir du [Centre de téléchargement Microsoft.](https://www.microsoft.com/download/details.aspx?id=53018)

Pour plus d’informations, voir :

- [Documentation AIP](/azure/information-protection/)
- [Historique des versions AIP et stratégie de support](/azure/information-protection/rms-client/unifiedlabelingclient-version-release-history)
- [Conditions requises pour le système AIP](/azure/information-protection/requirements)
- [Démarrage rapide AIP : déployer le client AIP](/azure/information-protection/quickstart-deploy-client)
- [Guide de l’administrateur AIP](/azure/information-protection/rms-client/clientv2-admin-guide)
- [Guide de l’utilisateur AIP](/azure/information-protection/rms-client/clientv2-user-guide)
- [En savoir plus sur les étiquettes de sensibilité Microsoft 365](/microsoft-365/compliance/sensitivity-labels)

### <a name="step-4-configure-aip-apps-on-windows"></a>Étape 4 : Configurer les applications AIP sur Windows

Les applications AIP sur Windows ont besoin de la clé de Registre suivante pour les faire pointer vers le cloud souverain correct pour Azure China :

- Nœud de Registre = `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\MSIP`
- Name = `CloudEnvType`
- Valeur = `6` (valeur par défaut = 0)
- Type = `REG_DWORD`

> [!IMPORTANT]
> Veillez à ne pas supprimer la clé de Registre après une désinstallation. Si la clé est vide, incorrecte ou inexistante, la fonctionnalité se comporte comme la valeur par défaut (valeur par défaut = 0 pour le cloud commercial). Si la clé est vide ou incorrecte, une erreur d’impression est également ajoutée au journal.

### <a name="step-5-install-the-aip-on-premises-scanner-and-manage-content-scan-jobs"></a>Étape 5 : Installer le scanneur AIP local et gérer les travaux d’analyse de contenu

Installez l’analyseur AIP local pour analyser vos partages réseau et de contenu à la recherche de données sensibles, et appliquez des étiquettes de classification et de protection comme configuré dans la stratégie de votre organisation.

Lors de l’installation du scanneur et de la gestion de vos travaux d’analyse de contenu, utilisez les cmdlets suivantes au lieu de l’interface du portail Azure utilisée par les offres commerciales :<br><br>

| Applet de commande | Description |
|--|--|
| [Add-AIPScannerRepository](/powershell/module/azureinformationprotection/add-aipscannerrepository) | Ajoute un nouveau référentiel à votre travail d’analyse de contenu. |
| [Get-AIPScannerContentScanJob](/powershell/module/azureinformationprotection/get-aipscannercontentscanjob) | Obtient des détails sur votre travail d’analyse de contenu. |
| [Get-AIPScannerRepository](/powershell/module/azureinformationprotection/get-aipscannerrepository) | Obtient des détails sur les référentiels définis pour votre travail d’analyse de contenu. |
| [Remove-AIPScannerContentScanJob](/powershell/module/azureinformationprotection/remove-aipscannercontentscanjob) | Supprime votre travail d’analyse de contenu. |
| [Remove-AIPScannerRepository](/powershell/module/azureinformationprotection/remove-aipscannerrepository) | Supprime un référentiel de votre travail d’analyse de contenu. |
| [Set-AIPScannerContentScanJob](/powershell/module/azureinformationprotection/set-aipscannercontentscanjob) | Définit les paramètres de votre travail d’analyse de contenu. |
| [Set-AIPScannerRepository](/powershell/module/azureinformationprotection/set-aipscannerrepository) | Définit les paramètres d’un référentiel existant dans votre travail d’analyse de contenu. |

Pour plus d’informations, consultez l’analyseur d’étiquetage unifié [Azure Information Protection](/azure/information-protection/deploy-aip-scanner) et gérez vos travaux d’analyse de contenu à l’aide de [PowerShell uniquement.](/azure/information-protection/deploy-aip-scanner-prereqs#use-powershell-with-a-disconnected-computer)