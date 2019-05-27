---
title: Préparer les certificats et les profils réseau pour le bureau géré Microsoft
description: certs/WiFi/LAN
keywords: Microsoft Managed Desktop, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.openlocfilehash: 7c260ce7b3fcb488cb22fb054eeb6ba322fee94b
ms.sourcegitcommit: ef1382ca224a0c108df2633a6550786666691e1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2019
ms.locfileid: "34391265"
---
# <a name="prepare-certificates-and-network-profiles-for-microsoft-managed-desktop"></a>Préparer les certificats et les profils réseau pour le bureau géré Microsoft  
 
L’authentification basée sur les certificats est une exigence commune pour les clients qui utilisent Microsoft Managed Desktop. Vous aurez peut-être besoin de certificats pour accéder au réseau Wi-Fi ou LAN, pour vous connecter à des solutions VPN ou pour accéder aux ressources internes de votre organisation.   
 
Étant donné que les appareils de bureau gérés Microsoft sont joints à Azure Active Directory (Azure AD) et gérés par Microsoft Intune, vous devez déployer ces certificats à l’aide d’un protocole SCEP (simple Certificate Cryptography Protocol) ou d’un fichier PKCS (Public Key Cryptography standard). infrastructure de certificat intégrée à Intune.    
 
## <a name="certificate-requirements"></a>Spécifications des certificats 
 
Les certificats racines sont requis pour déployer des certificats via une infrastructure SCEP ou PKCS. D’autres applications et services de votre organisation peuvent nécessiter le déploiement de certificats racines sur vos appareils de bureau gérés par Microsoft.    
 
Avant de déployer les certificats SCEP ou PKCS sur le bureau géré Microsoft, vous devez réunir les conditions requises pour chaque service nécessitant un certificat d’utilisateur ou d’appareil au sein de votre organisation. Pour faciliter cette tâche, vous pouvez utiliser l’un des modèles de planification suivants:  
 
- [Modèle de certificat PKCS](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/managed-desktop/get-ready/downloads/PKCS-certificate-template.xlsx) 
- [Modèle de certificat SCEP](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/managed-desktop/get-ready/downloads/SCEP-certificate-template.xlsx)

>[!NOTE]
>Actuellement, seuls les profils de certificat SCEP sont pris en charge pour le déploiement de profil Wi-Fi sur le bureau géré Microsoft lors de l’utilisation d’un type EAP. Les profils de certificat PKCS ne sont pas pris en charge. Voir [Ajouter des paramètres Wi-Fi pour les appareils Windows 10 dans Intune](https://docs.microsoft.com/intune/wi-fi-settings-windows) pour référence.

  
## <a name="wi-fi-connectivity-requirements"></a>Configuration requise pour la connectivité Wi-Fi

Pour permettre à un périphérique d’être automatiquement fourni avec la configuration Wi-Fi requise pour votre réseau d’entreprise, vous aurez peut-être besoin d’un profil de configuration Wi-Fi. Vous pouvez configurer Microsoft Managed Desktop pour déployer ces profils sur vos appareils. Si votre sécurité réseau requiert que les appareils fassent partie du domaine local, vous devrez peut-être également évaluer votre infrastructure réseau Wi-Fi pour vous assurer qu’elle est compatible avec les appareils de bureau gérés Microsoft (les appareils de bureau gérés par Microsoft sont des membres Azure AD uniquement). 
 
Avant de déployer une configuration Wi-Fi sur des appareils de bureau gérés Microsoft, vous devez recueillir les exigences de votre organisation pour chaque réseau Wi-Fi. Pour faciliter cette tâche, vous pouvez utiliser ce [modèle de profil WiFi](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/managed-desktop/get-ready/downloads/WiFi-profile-template.xlsx).
 
 
## <a name="wired-connectivity-requirements-and-8021x-authentication"></a>Configuration requise pour la connectivité filaire et 802.1 x 
 
Si vous utilisez l’authentification 802.1 x pour sécuriser l’accès à partir des appareils vers votre réseau local (LAN), vous devrez transmettre les détails de configuration requis à vos appareils de bureau gérés par Microsoft. Les appareils de bureau gérés Microsoft exécutant Windows 10, version 1809 ou ultérieure prennent en charge le déploiement d’une configuration 802.1 x via le fournisseur de services de configuration (CSP) WiredNetwork. Pour plus d’informations, consultez la documentation du [fournisseur de services cryptographiques WiredNetwork](https://docs.microsoft.com/windows/client-management/mdm/wirednetwork-csp) . 
 
Avant de déployer un profil de configuration de réseau câblé sur des appareils de bureau gérés par Microsoft, vous devez recueillir les exigences de votre organisation pour votre réseau d’entreprise câblé. Pour ce faire, procédez comme suit : 
 
 
1. Connectez-vous à un appareil sur lequel votre profil 802.1 x existant est configuré et connecté au réseau local.  
2. Ouvrez une invite de commandes avec des informations d’identification d’administration. 
3. Recherchez le nom de l’interface LAN en exécutant **netsh interface show interface**. 
4. Exportez le fichier XML de profil réseau en exécutant le **dossier de profil d’exportation LAN netsh =.  Interface = "INTERFACE_NAME"**. 
5. Si vous avez besoin de tester votre profil exporté sur un périphérique de bureau géré Microsoft, exécutez **netsh LAN Add profile filename = "PATH_AND_FILENAME. xml" interface = "INTERFACE_NAME"**. 
 
 
## <a name="deploy-certificate-infrastructure"></a>Déployer l’infrastructure de certificat  
 
Si vous disposez déjà d’une infrastructure SCEP ou PKCS avec Intune et que cela répond à vos besoins, vous pouvez également l’utiliser pour le bureau géré Microsoft. Si aucune autre infrastructure SCEP ou PKCS n’existe déjà, vous devrez en préparer une.  
 
Pour plus d’informations, reportez-vous à [la rubrique Configure a Certificate Profile for Your Devices in Microsoft Intune](https://docs.microsoft.com/intune/certificates-configure). 
 
 
 
## <a name="deploy-a-lan-profile"></a>Déployer un profil de réseau local 
 
Une fois que votre profil de réseau local a été exporté, vous pouvez préparer la stratégie pour Microsoft Managed Desktop en procédant comme suit:   
 
1. Créez un profil personnalisé dans Microsoft Intune pour le profil de réseau local à l’aide des paramètres suivants (reportez-vous à la rubrique [Use Custom Settings for Windows 10 Devices in Intune](https://docs.microsoft.com/intune/custom-settings-windows-10)). Dans **paramètres OMA-URI personnalisés**, sélectionnez **Ajouter**, puis entrez les valeurs suivantes: 
    - Name: *espace de travail moderne-profil de réseau local Windows 10* 
    - Description: entrez une description qui donne une vue d’ensemble du paramètre, ainsi que d’autres informations importantes. 
    - OMA-URI (respecte la casse): Enter *./Device/Vendor/msft/WiredNetwork/LanXML*
    - Type de données: sélectionnez **chaîne (fichier XML)**. 
    - XML personnalisé: Téléchargez le fichier XML exporté.
2. Soumettez une demande de support aux opérations informatiques de bureau gérées par Microsoft à l’aide du portail d’administration de bureau géré Microsoft pour passer en revue et déployer le profil de configuration sur «ordinateurs à espace de travail moderne – test». Les opérations informatiques de bureau gérées par Microsoft vous informent lorsque la demande est effectuée par le biais de la demande de support dans le portail d’administration.
 
## <a name="deploy-certificates-and-wi-fivpn-profile"></a>Déployer des certificats et un profil Wi-Fi/VPN 
 
 
Pour déployer des certificats et des profils, procédez comme suit:

1. Créez un profil pour chaque certificat racine et intermédiaire (consultez la rubrique [Create Trusted Certificate Profiles](https://docs.microsoft.com/intune/certificates-configure#step-3-create-trusted-certificate-profiles)). Chacun de ces profils doit avoir une description qui inclut une date d’expiration au format JJ/MM/AAAA. **Les profils de certificat sans date d’expiration ne seront pas déployés.**
2. Créez un profil pour chaque certificat SCEP ou PKCS (voir [création d’un profil de certificat SCEP](https://docs.microsoft.com/intune/certificates-scep-configure#create-a-scep-certificate-profile) ou [création d’un profil de certificat PKCS](https://docs.microsoft.com/intune/certficates-pfx-configure#create-a-pkcs-certificate-profile)) chacun de ces profils doit avoir une description qui inclut une date d’expiration au format jj/mm/aaaa. **Les profils de certificat sans date d’expiration ne seront pas déployés.**
3. Créez un profil pour chaque réseau WiFi d’entreprise (voir [paramètres Wi-Fi pour les appareils Windows 10 et versions ultérieures](https://docs.microsoft.com/intune/wi-fi-settings-windows)).
4. Créez un profil pour chaque VPN d’entreprise (voir [paramètres d’appareil holographique Windows 10 et Windows pour ajouter des connexions VPN à l’aide de Intune](https://docs.microsoft.com/intune/vpn-settings-windows-10)).
5. Soumettez une demande de support intitulée «déploiement de certificat» ou «déploiement de profil Wi-Fi» aux opérations informatiques Microsoft gérées à l’aide du portail d’administration de bureau géré Microsoft pour passer en revue et déployer le profil de configuration sur «ordinateurs de travail modernes – test ". Les opérations informatiques de bureau gérées par Microsoft vous informent lorsque la demande a été effectuée par le biais de la demande de support dans le portail d’administration. 
 
 
