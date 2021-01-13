---
title: Parité entre Azure Information Protection pour Office 365 géré par 21Vianet et les offres commerciales
f1.keywords:
- NOCSH
ms.author: sharik
author: skjerland
ms.reviewer: arthurj
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
ms.openlocfilehash: 50269749b5f4e544263f790ec9c7e4474af57219
ms.sourcegitcommit: 83a40facd66e14343ad3ab72591cab9c41ce6ac0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2021
ms.locfileid: "49840300"
---
# <a name="parity-between-azure-information-protection-for-office-365-operated-by-21vianet-and-commercial-offerings"></a>Parité entre Azure Information Protection pour Office 365 géré par 21Vianet et les offres commerciales

Bien que notre objectif soit de fournir toutes les fonctionnalités commerciales aux clients en Chine avec notre offre Azure Information Protection (AIP) pour Office 365 géré par 21Vianet, il existe certaines fonctionnalités manquantes que nous voulons mettre en évidence.

La liste suivante inclut les lacunes existantes entre Azure Information Protection pour Office 365 géré par 21Vianet et nos offres commerciales depuis janvier 2021 :

- La gestion des droits de l’information (IRM) est prise en charge uniquement pour les applications Microsoft 365 pour les entreprises (build 11731.10000 ou supérieure). Office 2010, Office 2013 et les autres versions d’Office 2016 ne sont pas pris en charge.

- La migration de services AD RMS (Active Directory Rights Management Services) (AD RMS) vers Azure Information Protection n’est actuellement pas disponible.
  
- Le partage de messages électroniques protégés aux utilisateurs dans le cloud commercial est pris en charge.
  
- Le partage de documents et de pièces jointes aux utilisateurs dans le cloud commercial n’est actuellement pas disponible. Cela inclut les utilisateurs d’Office 365 gérés par 21Vianet dans le cloud commercial, les utilisateurs non-Office 365 gérés par les utilisateurs 21Vianet dans le cloud commercial et les utilisateurs titulaires d’une licence RMS pour les particuliers.
  
- Irm avec SharePoint (sites et bibliothèques protégés par IRM) n’est actuellement pas disponible.
  
- L’extension d’appareil mobile pour AD RMS n’est actuellement pas disponible.

- La [visionneuse mobile n’est](/azure/information-protection/rms-client/mobile-app-faq) pas prise en charge par Azure China 21Vianet.

## <a name="configuring-azure-information-protection-for-customers-in-china"></a>Configuration d’Azure Information Protection pour les clients en Chine

### <a name="enable-rights-management-for-the-tenant"></a>Activer la gestion des droits pour le client

Pour que le chiffrement fonctionne correctement, rms doit être activé pour le client.

- Vérifiez si RMS est activé :
  1. Lancez PowerShell en tant qu’administrateur.
  2. Si le module AIPService n’est pas installé, exécutez `Install-Module AipService` .
  3. Importer le module à l’aide `Import-Module AipService` de .
  4. Connectez-vous au service à l’aide `Connect-AipService -environmentname azurechinacloud` de .
  5. Exécutez `(Get-AipServiceConfiguration).FunctionalState` et vérifiez si l’état `Enabled` est .

- Si l’état fonctionnel est `Disabled` , exécutez `Enable-AipService` .

### <a name="dns-configuration-for-encryption-windows"></a>Configuration DNS pour le chiffrement (Windows)

Pour que le chiffrement fonctionne correctement, les applications clientes Office doivent se connecter à l’instance chine du service et s’y connecter. Pour rediriger les applications clientes vers l’instance de service de droite, l’administrateur client doit configurer un enregistrement SRV DNS avec des informations sur l’URL Azure RMS. Sans l’enregistrement SRV DNS, l’application cliente tentera par défaut de se connecter à l’instance de cloud public et échouera.

En outre, l’hypothèse est que les utilisateurs se connectent avec un nom d’utilisateur basé sur le domaine du client (par exemple, ), et non le nom d’utilisateur `joe@contoso.cn` `onmschina` (par exemple, `joe@contoso.onmschina.cn` ). Le nom de domaine du nom d’utilisateur est utilisé pour la redirection DNS vers l’instance de service correcte.

- Obtenez l’ID RMS :
  1. Lancez PowerShell en tant qu’administrateur.
  2. Si le module AIPService n’est pas installé, exécutez `Install-Module AipService` .
  3. Connectez-vous au service à l’aide `Connect-AipService -environmentname azurechinacloud` de .
  4. Exécutez `(Get-AipServiceConfiguration).RightsManagementServiceId` pour obtenir l’ID RMS.

- Connectez-vous à votre fournisseur DNS, accédez aux paramètres DNS du domaine, puis ajoutez un nouvel enregistrement SRV.
  - Service = `_rmsredir`
  - Protocole = `_http`
  - Name = `_tcp`
  - Target = `[GUID].rms.aadrm.cn` (où GUID est l’ID RMS)
  - Priority, Weight, Seconds, TTL = default values

- Associez le domaine personnalisé au client dans [le portail Azure.](https://portal.azure.cn/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Domains) Cela ajoute une entrée dans DNS, qui peut prendre plusieurs minutes pour être vérifiée après avoir ajouté la valeur aux paramètres DNS.

- Connectez-vous au Centre d’administration Microsoft 365 avec les informations d’identification d’administrateur global correspondantes et ajoutez le domaine (par exemple, ) pour la création `contoso.cn` d’utilisateurs. Dans le processus de vérification, des modifications DNS supplémentaires peuvent être nécessaires. Une fois la vérification effectuée, les utilisateurs peuvent être créés.

### <a name="dns-configuration-for-encryption-mac-ios-android"></a>Configuration DNS pour le chiffrement (Mac, iOS, Android)

Connectez-vous à votre fournisseur DNS, accédez aux paramètres DNS du domaine, puis ajoutez un nouvel enregistrement SRV.

- Service = `_rmsdisco`
- Protocole = `_http`
- Name = `_tcp`
- Cible = `api.aadrm.cn`
- Port = `80`
- Priority, Weight, Seconds, TTL = default values

### <a name="aip-client-configuration"></a>Configuration du client AIP

Le client AIP unifié peut être téléchargé à partir du [Centre de téléchargement Microsoft.](https://www.microsoft.com/download/details.aspx?id=53018)

Pour plus d’informations, voir :

- [Documentation Azure Information Protection](/azure/information-protection/)
- [Historique des versions AIP et stratégie de support](/azure/information-protection/rms-client/unifiedlabelingclient-version-release-history)
- [Conditions requises pour le système AIP](/azure/information-protection/requirements)
- [Démarrage rapide d’AIP : déployer le client AIP](/azure/information-protection/quickstart-deploy-client)
- [Guide de l’administrateur AIP](/azure/information-protection/rms-client/clientv2-admin-guide)
- [Guide de l’utilisateur AIP](/azure/information-protection/rms-client/clientv2-user-guide)
- [En savoir plus sur les étiquettes de sensibilité Microsoft 365](/microsoft-365/compliance/sensitivity-labels)

### <a name="aip-apps-configuration-unified-labeling-client-only"></a>Configuration des applications AIP (client d’étiquetage unifié uniquement)

Pour la solution d’étiquetage unifié, les applications AIP sur Windows ont besoin de la clé de Registre suivante pour les faire pointer vers le cloud souverain correct pour Azure Chine :

- Nœud de Registre = `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\MSIP`
- Name = `CloudEnvType`
- Valeur = `6` (valeur par défaut = 0)
- Type = `REG_DWORD`

> [!IMPORTANT]
> Veillez à ne pas supprimer la clé de Registre après une désinstallation. Si la clé est vide, incorrecte ou inexistante, la fonctionnalité se comporte comme la valeur par défaut (valeur par défaut = 0 pour le cloud commercial). Si la clé est vide ou incorrecte, une erreur d’impression est également ajoutée au journal.

### <a name="manage-azure-information-protection-content-scan-jobs"></a>Gérer les travaux d’analyse de contenu Azure Information Protection

Pour gérer vos travaux d’analyse de contenu Azure Information Protection avec un serveur Azure China Scanner, utilisez les cmdlets suivantes au lieu du portail Azure :<br><br>

| Applet de commande | Description |
|--|--|
| [Add-AIPScannerRepository](/powershell/module/azureinformationprotection/add-aipscannerrepository) | Ajoute un nouveau référentiel à votre travail d’analyse de contenu. |
| [Get-AIPScannerContentScanJob](/powershell/module/azureinformationprotection/get-aipscannercontentscanjob) | Obtient des détails sur votre travail d’analyse de contenu. |
| [Get-AIPScannerRepository](/powershell/module/azureinformationprotection/get-aipscannerrepository) | Obtient des détails sur les référentiels définis pour votre travail d’analyse de contenu. |
| [Remove-AIPScannerContentScanJob](/powershell/module/azureinformationprotection/remove-aipscannercontentscanjob) | Supprime votre travail d’analyse de contenu. |
| [Remove-AIPScannerRepository](/powershell/module/azureinformationprotection/remove-aipscannerrepository) | Supprime un référentiel de votre travail d’analyse de contenu. |
| [Set-AIPScannerContentScanJob](/powershell/module/azureinformationprotection/set-aipscannercontentscanjob) | Définit les paramètres de votre travail d’analyse de contenu. |
| [Set-AIPScannerRepository](/powershell/module/azureinformationprotection/set-aipscannerrepository) | Définit les paramètres d’un référentiel existant dans votre travail d’analyse de contenu. |

Pour plus d’informations, voir [Gérer vos travaux d’analyse de contenu à l’aide de PowerShell uniquement.](/azure/information-protection/deploy-aip-scanner-prereqs#use-powershell-with-a-disconnected-computer)