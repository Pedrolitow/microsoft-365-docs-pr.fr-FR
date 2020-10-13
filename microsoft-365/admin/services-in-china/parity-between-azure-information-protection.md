---
title: Parité entre Azure information protection pour Office 365 géré par 21Vianet et offres commerciales
f1.keywords:
- NOCSH
ms.author: sharik
author: skjerland
manager: mnirkhe
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
description: En savoir plus sur Azure information protection pour Office 365 géré par 21Vianet et sur la façon de le configurer pour les clients en Chine.
monikerRange: o365-21vianet
ms.openlocfilehash: ca30811e77f686b92b8cdd13d624182eb0d3039e
ms.sourcegitcommit: 9a764c2aed7338c37f6e92f5fb487f02b3c4dfa1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "48445578"
---
# <a name="parity-between-azure-information-protection-for-office-365-operated-by-21vianet-and-commercial-offerings"></a>Parité entre Azure information protection pour Office 365 géré par 21Vianet et offres commerciales

Alors que notre objectif est de fournir toutes les fonctionnalités et fonctionnalités commerciales pour les clients en Chine avec notre offre Azure information protection pour Office 365 gérée par 21Vianet, il existe des fonctionnalités manquantes que nous souhaitons mettre en évidence.

La liste suivante inclut les lacunes existantes entre Azure information protection pour Office 365 géré par 21Vianet et nos offres commerciales depuis le 1er juillet 2019 :

- La gestion des droits relatifs à l’information (IRM) est prise en charge uniquement pour les applications Microsoft 365 pour entreprise (Build 11731,10000 ou version ultérieure). Office 2010, Office 2013 et les autres versions d’Office 2016 ne sont pas prises en charge.

- La migration à partir d’Active Directory Rights Management Services (AD RMS) vers Azure information protection n’est pas disponible actuellement.
  
- Le partage des courriers électroniques protégés vers les utilisateurs dans le Cloud commercial est pris en charge.
  
- Le partage de documents et de pièces jointes de courrier électronique à des utilisateurs dans le Cloud commercial n’est pas disponible actuellement. Cela inclut les utilisateurs d’Office 365 gérés par 21Vianet dans le Cloud commercial, les utilisateurs non-Office 365 gérés par 21Vianet dans le nuage commercial et les utilisateurs disposant d’une licence RMS pour personnes.
  
- La gestion des droits relatifs à l’information avec SharePoint (sites et bibliothèques protégés par IRM) n’est pas disponible actuellement.
  
- Le connecteur Rights Management n’est pas disponible actuellement.
  
- L’extension de l’appareil mobile pour AD RMS n’est pas disponible actuellement.

## <a name="configuring-azure-information-protection-for-customers-in-china"></a>Configuration d’Azure information protection pour les clients en Chine

### <a name="enable-rights-management-for-the-tenant"></a>Activer la gestion des droits pour le client

Pour que le chiffrement fonctionne correctement, le RMS doit être activé pour le client.

- Vérifiez si le RMS est activé :
  1. Lancez PowerShell en tant qu’administrateur.
  2. Si le module AIPService n’est pas installé, exécutez  `Install-Module AipService` .
  3. Importez le module à l’aide du `Import-Module AipService` .
  4. Connectez-vous au service à l’aide de  `Connect-AipService -environmentname azurechinacloud` .
  5. Exécutez  `(Get-AipServiceConfiguration).FunctionalState`   et vérifiez si l’État est  `Enabled` .

- Si l’état de fonctionnement est  `Disabled` , exécuter  `Enable-AipService` .

### <a name="dns-configuration-for-encryption-windows"></a>Configuration DNS pour le chiffrement (Windows)

Pour que le chiffrement fonctionne correctement, les applications clientes Office doivent se connecter à l’instance chinoise du service et des données d’amorçage à partir de là. Pour rediriger les applications clientes vers l’instance de service appropriée, l’administrateur client doit configurer un enregistrement SRV DNS avec des informations sur l’URL Azure RMS. Sans l’enregistrement DNS SRV, l’application cliente tente de se connecter à l’instance de cloud public par défaut et échoue.

En outre, l’hypothèse est que les utilisateurs se connectent avec un nom d’utilisateur basé sur le domaine appartenant au client (par exemple, `joe@contoso.cn` ) et non sur le `onmschina` nom d’utilisateur (par exemple, `joe@contoso.onmschina.cn` ). Le nom de domaine du nom d’utilisateur est utilisé pour la redirection DNS vers l’instance de service correcte.

- Obtenir l’ID RMS :
  1. Lancez PowerShell en tant qu’administrateur.
  2. Si le module AIPService n’est pas installé, exécutez  `Install-Module AipService` .
  3. Connectez-vous au service à l’aide de  `Connect-AipService -environmentname azurechinacloud` .
  4. Exécutez  `(Get-AipServiceConfiguration).RightsManagementServiceId`   pour obtenir l’ID RMS.

- Connectez-vous à votre fournisseur DNS, accédez aux paramètres DNS du domaine, puis ajoutez un nouvel enregistrement SRV.
  - Service = `_rmsredir`
  - Protocole = `_http`
  - Nom = `_tcp`
  - Target =  `[GUID].rms.aadrm.cn`   (où GUID est l’ID RMS)
  - Priorité, poids, secondes, durée de vie = valeurs par défaut

- Associez le domaine personnalisé au client dans le [portail Azure](https://portal.azure.cn/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Domains). Cette opération ajoute une entrée dans DNS, qui peut prendre plusieurs minutes pour être vérifiée après l’ajout de la valeur aux paramètres DNS.

- Connectez-vous au centre d’administration Microsoft 365 avec les informations d’identification d’administrateur global correspondantes et ajoutez le domaine (par exemple, `contoso.cn` ) pour la création de l’utilisateur. Dans le processus de vérification, des modifications DNS supplémentaires peuvent être nécessaires. Une fois la vérification terminée, les utilisateurs peuvent être créés.

### <a name="dns-configuration-for-encryption-mac-ios-android"></a>Configuration DNS pour le chiffrement (Mac, iOS, Android)

- Connectez-vous à votre fournisseur DNS, accédez aux paramètres DNS du domaine, puis ajoutez un nouvel enregistrement SRV.
  - Service = `_rmsdisco`
  - Protocole = `_http`
  - Nom = `_tcp`
  - Cible = `api.aadrm.cn`
  - Port = `80`
  - Priorité, poids, secondes, durée de vie = valeurs par défaut
