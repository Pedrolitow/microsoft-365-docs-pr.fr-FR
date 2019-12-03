---
title: Fonctionnalités de sécurité et de conformité de Microsoft 365 Business
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- M365-security-compliance
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
search.appverid:
- BCS160
- MET150
ms.assetid: c123694a-1efb-459e-a8d5-2187975373dc
description: Découvrez les fonctionnalités de sécurité fournies avec Microsoft 365 Business.
ms.openlocfilehash: 98eb0c2015ed6088b2d5e8621c8e72a5b63f2a17
ms.sourcegitcommit: 58a7bd70a4bcf52530baf5f82507fd5dc4455fd9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "39668845"
---
# <a name="microsoft-365-business-security-and-compliance-features"></a>Fonctionnalités de sécurité et de conformité de Microsoft 365 Business

Microsoft 365 Business propose des fonctionnalités de sécurité simplifiées pour vous aider à protéger vos données sur des PC, des téléphones et des tablettes.
    
## <a name="microsoft-365-business-admin-center-security-features"></a>Fonctionnalités de sécurité du centre d’administration de Microsoft 365

[![Étiquette vous informant le centre d’administration est en train de changer et vous pouvez trouver plus de détails à ce sujet à l’adresse aka.ms/aboutM365preview.](media/m365admincenterchanging.png)](https://docs.microsoft.com/office365/admin/microsoft-365-admin-center-preview)

Vous pouvez gérer de nombreuses fonctionnalités de sécurité d’entreprise Microsoft 365 dans le centre d’administration, ce qui vous offre un moyen simple d’activer ou de désactiver ces fonctionnalités. Dans le centre d’administration, vous pouvez effectuer les opérations suivantes :
  
- [Définir les paramètres de gestion des applications pour les appareils Android ou iOS](app-protection-settings-for-android-and-ios.md) . 
    
    Ces paramètres incluent la suppression de fichiers d’un appareil inactif après une période définie, le chiffrement de fichiers de travail, la nécessité pour les utilisateurs de définir un code confidentiel et ainsi de suite.
    
- [Définir les paramètres de protection des applications pour les appareils Windows 10](protection-settings-for-windows-10-devices.md) . 
    
    Ces paramètres peuvent être appliqués aux données de l’entreprise sur des appareils appartenant à une société ou appartenant à un personnel.
    
- [Définir les paramètres de protection des appareils pour les appareils Windows 10](protection-settings-for-windows-10-pcs.md) . 
    
    Vous pouvez activer le chiffrement [BitLocker](https://go.microsoft.com/fwlink/p/?linkid=871405) pour protéger les données en cas de perte ou de vol d’un appareil, et permettre à [Windows exploit Guard](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/enable-exploit-protection) de fournir une protection avancée contre les ransomware. 
    
- [Supprimer les données d'entreprise sur des appareils](remove-company-data.md)
    
    Vous pouvez réeffacer les données d’entreprise à distance si un appareil est perdu, volé ou si un employé quitte votre entreprise.
    
- [Réinitialisez les appareils Windows 10 à leurs paramètres d’usine](reset-devices-to-factory-settings.md) . 
    
    Vous pouvez réinitialiser les appareils Windows 10 sur lesquels des paramètres de protection des appareils sont appliqués.
    
## <a name="additional-security-features"></a>Fonctionnalités de sécurité supplémentaires 

Les fonctionnalités avancées de Microsoft 365 Business sont disponibles pour vous aider à protéger votre entreprise contre les menaces et protéger les informations sensibles.
  
- **[Office 365 Advanced Threat Protection](https://support.office.com/article/e100fe7c-f2a1-4b7d-9e08-622330b83653)**
    
    La protection avancée contre les menaces (ATP) permet de protéger votre activité contre le hameçonnage et les attaques par ransomware sophistiqués conçus pour compromettre les informations des employés ou des clients. Les fonctionnalités sont les suivantes : 
    
  - Analyse avancée des pièces jointes et analyse anti-puissance pour détecter et rejeter les messages dangereux.
    
  - Vérifications automatiques des liens dans les messages électroniques pour évaluer s’ils font partie d’un schéma de hameçonnage. Cela vous permet d’accéder en toute sécurité aux sites Web non sécurisés.

- **[Fonctionnalités complètes d’Intune dans le portail Azure](https://go.microsoft.com/fwlink/p/?linkid=871403)**
    
    L’accès au centre d’administration Intune dans le portail Azure vous permet de configurer des fonctionnalités de sécurité supplémentaires, telles que la gestion des appareils MacOS, iPhone et appareils Android, ainsi que la gestion des appareils avancée pour Windows, qui ne sont pas disponibles auprès de Microsoft. Centre d’administration de l’entreprise 365.
- **Même [accès conditionnel](https://docs.microsoft.com/azure/active-directory/conditional-access/overview) que le plan Azure ad P1**


    L’accès conditionnel peut vous aider à protéger votre organisation contre les risques de connexion, à accéder à des tentatives d’accès à partir d’un réseau ou d’une localisation inattendue, à accéder à des tentatives de types de périphériques risqués, etc. Les stratégies d’accès conditionnel sont appliquées une fois la première authentification terminée, et les signaux de l’événement First Authentication sont utilisés pour déterminer si l’accès tenté doit être approuvé, refusé ou si davantage de preuves (par exemple, une deuxième forme d’identification) est requis.

    Les fonctionnalités d’accès conditionnel sont les suivantes :

    - Accès basé sur le nom d’utilisateur, le groupe et le rôle
    - Accès [basé sur une application](https://docs.microsoft.com/azure/active-directory/conditional-access/app-based-conditional-access) 
    - [Accès en fonction de l’emplacement](https://docs.microsoft.com/azure/active-directory/authentication/howto-registration-mfa-sspr-combined#conditional-access-policies-for-combined-registration);  autoriser uniquement l’accès à partir de plages d’adresses IP approuvées ou de pays spécifiques 
    - Exiger MFA pour Access
    - Bloquer l’accès aux applications qui utilisent [l’authentification héritée](https://docs.microsoft.com/azure/active-directory/conditional-access/block-legacy-authentication)
    - Exiger les applications TP utiliser la [protection des applications Intune](https://docs.microsoft.com/azure/active-directory/conditional-access/app-protection-based-conditional-access)
    - Authentification personnalisée, telle que l’authentification multifacteur (MFA) avec des fournisseurs tiers, par exemple DUO.
   
    Autres fonctionnalités :
    - [Réinitialisation du mot de passe en libre-service](https://docs.microsoft.com/azure/active-directory/authentication/concept-sspr-customization) pour Azure ad hybride
    
## <a name="compliance-features"></a>Fonctionnalités de conformité

Votre abonnement professionnel Microsoft 365 inclut des fonctionnalités qui vous aident à respecter les normes de conformité et de réglementation.

- **[Vue d’ensemble des stratégies de protection contre la perte de données](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e)** (DLP). 
    
    Vous pouvez configurer DLP pour qu’il détecte automatiquement les informations sensibles, telles que les numéros de carte de crédit, les numéros de sécurité sociale, etc., afin d’empêcher leur partage par inadvertance à l’extérieur de votre entreprise.
    
- **[Archivage Exchange Online](https://products.office.com/exchange/microsoft-exchange-online-archiving-email)**
    
    La licence d’archivage Exchange Online permet d’archiver facilement les messages avec la sauvegarde continue des données. Il stocke tous les courriers électroniques d’un utilisateur, y compris les éléments supprimés, si vous en avez besoin plus tard pour la découverte ou la restauration. En outre, vous pouvez utiliser différentes stratégies de rétention pour conserver les données de courrier électronique pour les conservations pour litige, eDiscovery ou pour répondre aux exigences de conformité.
    
- **[Étiquettes de niveau de confidentialité](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels)**

   Microsoft 365 Business inclut toutes les fonctionnalités d' [Azure information Protection Plan 1](https://go.microsoft.com/fwlink/p/?linkid=871407). Grâce à ce plan, vous pouvez créer des **étiquettes de confidentialité** qui vous permettent de contrôler l’accès aux informations sensibles dans les e-mails et les documents, avec des contrôles tels que « ne pas transférer » et « ne pas copier ». Vous pouvez également classer les informations sensibles comme « confidentielles » et spécifier le mode de partage des informations confidentielles à l’extérieur et à l’intérieur de l’entreprise. Le chiffrement au niveau de l’entreprise est facile à appliquer aux e-mails et aux documents afin de garantir la confidentialité de vos informations. Vous pouvez également installer le complément client Azure information protection pour les applications Office. Pour plus d’informations, consultez la rubrique [Azure information protection Unified Labeling client](https://docs.microsoft.com/azure/information-protection/rms-client/unifiedlabelingclient-version-release-history). Pour les étiquettes de sensibilité, installez le **AzInfoProtection_UL. exe**.

Vous pouvez gérer ces fonctionnalités dans le centre &amp; d’administration et de sécurité et dans le centre d’administration Intune. Au fil du temps, les contrôles simplifiés seront ajoutés au centre d’administration de Microsoft 365 Business.
  
    
## <a name="faq"></a>Forum aux questions

 ### <a name="are-these-security-features-available-in-all-markets"></a>Ces fonctionnalités de sécurité sont-elles disponibles sur tous les marchés ?
  
Oui, ces fonctionnalités sont disponibles sur tous les marchés où Microsoft 365 entreprise est vendu.
  
### <a name="how-do-i-find-the-security-amp-compliance-center"></a>Comment puis-je trouver le &amp; Centre de sécurité conformité ?
  
1. [Connectez-vous à Microsoft 365 Business](https://portal.microsoft.com/) à l’aide de vos informations d’identification d’administrateur. 
    
2. Dans le volet de navigation de gauche, localisez les **centres d’administration** et développez-le. 
    
    ![Dans le volet de navigation de gauche, dans le centre d’administration Microsoft 365, sélectionnez centres d’administration.](media/fa4484f8-c637-45fd-a7bd-bdb3abfd6c03.png)
  
3. Choisissez **conformité &amp; de sécurité** pour accéder au &amp; Centre de sécurité conformité.
