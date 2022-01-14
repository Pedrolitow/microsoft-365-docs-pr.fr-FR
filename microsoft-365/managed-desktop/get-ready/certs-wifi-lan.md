---
title: Préparer les certificats et les profils réseau pour le Bureau géré Microsoft
description: Exigences en matière de certificats et connectivité Wi-Fi
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: 69cea241c81130fdee2ae734c372981e0349ab64
ms.sourcegitcommit: a6651b841f111ea2776cab88bf2c80f805fa8e09
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2022
ms.locfileid: "62035593"
---
# <a name="prepare-certificates-and-network-profiles-for-microsoft-managed-desktop"></a>Préparer les certificats et les profils réseau pour le Bureau géré Microsoft  
 
L’authentification basée sur les certificats est une exigence courante pour les clients qui utilisent Microsoft Manged Desktop. Vous pouvez exiger des certificats pour accéder Wi-Fi réseau privé ou réseau, pour vous connecter à des solutions VPN ou pour accéder aux ressources internes de votre organisation.   
 
Étant donné que les appareils Microsoft Manged Desktop sont joints à Azure Active Directory (Azure AD) et sont gérés par Microsoft Intune, vous devez déployer ces certificats à l’aide d’un certificat SCEP (Simple Certificate Enrollment Protocol) ou PKCS (Public Key Cryptography Standard) intégrée à Intune.    
 
## <a name="certificate-requirements"></a>Spécifications des certificats 
 
Les certificats racine sont requis pour déployer des certificats via une infrastructure SCEP ou PKCS. D’autres applications et services de votre organisation peuvent nécessiter le déploiement de certificats racines sur Microsoft Manged Desktop appareils.    
 
Avant de déployer des certificats SCEP ou PKCS sur Microsoft Manged Desktop, vous devez rassembler les conditions requises pour chaque service nécessitant un certificat d’utilisateur ou d’appareil dans votre organisation. Pour faciliter cette activité, vous pouvez utiliser l’un des modèles de planification suivants :  
 
- [Modèle de certificat PKCS](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/managed-desktop/get-ready/downloads/PKCS-certificate-template.xlsx) 
- [Modèle de certificat SCEP](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/managed-desktop/get-ready/downloads/SCEP-certificate-template.xlsx)

  
## <a name="wi-fi-connectivity-requirements"></a>Wi-Fi connectivité requise

Pour permettre à un appareil d’être automatiquement fourni avec la configuration Wi-Fi requise pour votre réseau d’entreprise, vous devrez peut-être utiliser Wi-Fi profil de configuration. Vous pouvez configurer des Microsoft Manged Desktop pour déployer ces profils sur vos appareils. Si la sécurité de votre réseau nécessite que les appareils font partie du domaine local, vous devrez peut-être également évaluer votre infrastructure réseau Wi-Fi pour vous assurer qu’elle est compatible avec les appareils Microsoft Manged Desktop (les appareils Microsoft Manged Desktop sont joints à Azure AD uniquement). 
 
Avant de déployer une configuration Wi-Fi sur Microsoft Manged Desktop, vous devez rassembler les besoins de votre organisation pour chaque Wi-Fi réseau. Pour faciliter cette activité, vous pouvez utiliser ce modèle [de profil WiFi.](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/managed-desktop/get-ready/downloads/WiFi-profile-template.xlsx)
 
 
## <a name="wired-connectivity-requirements-and-8021x-authentication"></a>Exigences de connectivité câblé et authentification 802.1x 
 
Si vous utilisez l’authentification 802.1x pour sécuriser l’accès à partir d’appareils à votre réseau local( LAN), vous devrez fournir les détails de configuration requis à Microsoft Manged Desktop périphériques. Microsoft Manged Desktop périphériques exécutant Windows 10, version 1809 ou une ultérieure prise en charge du déploiement d’une configuration 802.1x via le fournisseur de services de configuration WiredNetwork(CSP). Pour plus d’informations, voir la documentation [du programme CSP WiredNetwork.](/windows/client-management/mdm/wirednetwork-csp) 
 
Avant de déployer un profil de configuration de réseau câblé sur Microsoft Manged Desktop, rassemblez les exigences de votre organisation pour votre réseau d’entreprise câblé. Pour ce faire, procédez comme suit : 
 
 
1. Connectez-vous à un appareil sur qui votre profil 802.1x existant est configuré et qui est connecté au réseau local.  
2. Ouvrez une invite de commandes avec des informations d’identification administratives. 
3. Recherchez le nom de l’interface LAN en exécutant **l’interface netsh afficher l’interface**. 
4. Exporte le fichier XML de profil LAN en exécutant **netsh lan export profile folder=.  Interface="interface_name »**. 
5. Si vous devez tester votre profil exporté sur un appareil Microsoft Manged Desktop, exécutez **netsh lan add profile filename="PATH_AND_FILENAME.xml » interface="INTERFACE_NAME »**. 
 
 
## <a name="deploy-certificate-infrastructure"></a>Déployer l’infrastructure de certificats  
 
Si vous avez déjà une infrastructure SCEP ou PKCS avec Intune et que cette approche répond à vos besoins, vous pouvez également l’utiliser pour Microsoft Manged Desktop. Si aucune infrastructure SCEP ou PKCS n’existe déjà, vous devez en préparer une.  
 
Pour plus d’informations, consultez [Configurer un profil de certificat pour vos appareils dans Microsoft Intune](/intune/certificates-configure). 
 
 
 
## <a name="deploy-a-lan-profile"></a>Déployer un profil LAN 
 
Une fois que votre profil laN a été exporté, vous pouvez préparer la stratégie pour Microsoft Manged Desktop en suivant les étapes suivantes :   
 
1. Créez un profil personnalisé dans Microsoft Intune profil laN à l’aide des paramètres suivants (voir Utiliser des paramètres personnalisés pour Windows 10 [appareils dans Intune).](/intune/custom-settings-windows-10) Dans **OMA-URI Paramètres,** **sélectionnez** Ajouter, puis entrez les valeurs suivantes : 
    - Name: *Modern Workplace-Windows 10 LAN Profile* 
    - Description : entrez une description qui donne une vue d’ensemble du paramètre et tout autre détail important. 
    - OMA-URI (sensible à la cas) : Enter *./Device/Vendor/MSFT/WiredNetwork/LanXML*
    - Type de données : **sélectionnez Chaîne (fichier XML).** 
    - XML personnalisé : Télécharger fichier XML exporté.
2. Affectez le profil personnalisé aux *appareils d’espace de travail modernes : groupe de* test.
3. Faites les tests nécessaires à l’aide d’un appareil qu’il se place dans le groupe de déploiement Test. Si l’opération réussit, affectez le profil personnalisé aux appareils d’espace de travail modernes *(* First , *Modern Workplace Devices – Fast*, and Modern Workplace Devices – *Larges* groupes.
 
## <a name="deploy-certificates-and-wi-fivpn-profile"></a>Déployer des certificats et un profil Wi-Fi/VPN 
 
 
Pour déployer des certificats et des profils, suivez les étapes suivantes :

1. Créez un profil pour chacun des certificats racines et intermédiaires (voir [Créer des profils de certificats de confiance.](/intune/protect/certificates-configure#step-3-create-trusted-certificate-profiles) Chacun de ces profils doit avoir une description qui inclut une date d’expiration au format JD/MM/AAA. **Les profils de certificat doivent avoir une date d’expiration.**
2. Créez un profil pour chaque certificat SCEP ou PKCS (voir Créer un profil de certificat [SCEP](/intune/protect/certificates-scep-configure#create-a-scep-certificate-profile) ou Créer un profil de certificat [PKCS).](/intune/protect/certficates-pfx-configure#create-a-pkcs-certificate-profile)Chacun de ces profils doit avoir une description qui inclut une date d’expiration au format JJ/MM/AAAA. **Les profils de certificat doivent avoir une date d’expiration.**
3. Créez un profil pour chaque réseau WiFi d’entreprise (voir [paramètres Wi-Fi pour Windows 10 et les appareils ultérieurs).](/intune/wi-fi-settings-windows)
4. Créez un profil pour chaque VPN d’entreprise (voir Windows 10 et Windows paramètres de périphérique holographique pour ajouter des connexions VPN à l’aide [d’Intune).](/intune/vpn-settings-windows-10)
5. Affectez les profils aux *appareils d’espace de travail modernes : groupe de* test.
6. Faites les tests nécessaires à l’aide d’un appareil qu’il se place dans le groupe de déploiement Test. Si l’opération réussit, affectez le profil personnalisé aux appareils d’espace de travail modernes *(* First , *Modern Workplace Devices – Fast*, and Modern Workplace Devices – *Larges* groupes.

 
## <a name="steps-to-get-ready-for-microsoft-managed-desktop"></a>Étapes pour vous préparer à la Microsoft Manged Desktop

1. Examinez [Configuration requise pour le Bureau géré Microsoft](prerequisites.md).
2. Exécutez les [outils d’évaluation de la préparation](readiness-assessment-tool.md).
1. Achetez [Portail d’entreprise](../get-started/company-portal.md).
1. Passez en revue les [prérequis pour les comptes invités](guest-accounts.md).
1. Vérifiez la[configuration réseau](network.md).
1. Préparer les certificats et les profils réseau (cet article).
1. [Préparer l’accès utilisateur aux données](authentication.md).
1. [Préparer les applications](apps.md).
1. [Préparer les lecteurs mappés](mapped-drives.md).
1. [Préparer les ressources d’impression](printing.md).
1. [noms d’appareil](address-device-names.md) d’une adresse.
