---
title: Conditions requises pour Microsoft 365 Lighthouse
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Pour les fournisseurs de services gérés, obtenez la liste des conditions requises pour utiliser Microsoft 365 Lighthouse.
ms.openlocfilehash: 9c87744053ffe3bace90534287cd2b81697f3554
ms.sourcegitcommit: 00f001019c653269d85718d410f970887d904304
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2021
ms.locfileid: "53395189"
---
# <a name="requirements-for-microsoft-365-lighthouse"></a>Conditions requises pour Microsoft 365 Lighthouse

> [!NOTE]
> Les fonctionnalités décrites dans cet article sont en prévisualisation, peuvent faire l’objet de changements et sont disponibles uniquement pour les partenaires qui répondent aux exigences répertoriées dans cet article. Si votre organisation n’a pas de Microsoft 365 Lighthouse, voir [S’inscrire pour Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md).

Microsoft 365 Lighthouse est un portail d’administration qui permet aux fournisseurs de services gérés (MSP) de sécuriser et de gérer les appareils, les données et les utilisateurs à grande échelle pour les petites et moyennes entreprises (SMB).  

Les MSP doivent être inscrits au programme fournisseur de solutions Cloud (CSP) en tant que revendeur indirect ou partenaire de facture directe pour utiliser Microsoft 365 Lighthouse.  

En outre, chaque client MSP doit être éligible Microsoft 365 Lighthouse en suivant les exigences suivantes : 
 
- Privilèges d’administrateur délégués (DAP) pour le MSP 
- Au moins une licence Microsoft 365 Business Premium licence 
- Moins de 500 utilisateurs sous licence  

## <a name="requirements-for-enablingdevice-management"></a>Conditions requises pour l’activation de la gestion des appareils   

Pour afficher les appareils clients sur les pages de gestion des appareils, un MSP doit :    

- Inscrire tous les appareils clients dans Microsoft Endpoint Manager (MEM).Pour plus d’informations, voir [Inscrire des appareils dans Microsoft Intune](/mem/intune/enrollment/).
- Affecter des stratégies de conformité à tous les appareils clients.Pour plus d’informations, [voir Créer une stratégie de conformité dans Microsoft Intune](/mem/intune/protect/create-compliance-policy). 

## <a name="requirements-for-enabling-usermanagement"></a>Conditions requises pour l’activation de la gestion des utilisateurs 

Pour que les données client s’affichent dans les rapports sur les pages de gestion des utilisateurs, y compris les utilisateurs à risque, l’authentification multifacteur et la réinitialisation du mot de passe, les clients doivent avoir des licences pour Azure Active Directory Premium P1 ou une ultérieure. Azure AD Premium P1 est inclus dans Microsoft 365 Business Premium.   

## <a name="requirements-for-enablingthreat-management"></a>Conditions requises pour activer la gestion des menaces 

Pour afficher les appareils client et les menaces sur les pages de gestion des menaces, vous devez inscrire tous les appareils client client dans Microsoft Endpoint Manager (MEM) et les protéger en exécutant Antivirus Microsoft Defender.  

Pour plus d’informations, voir [Inscrire des appareils dans Microsoft Intune](/mem/intune/enrollment/).  

Antivirus Microsoft Defender fait partie du système d Windows d’exploitation et est activé par défaut sur les appareils exécutant Windows 10.  

> [!NOTE] 
> Si vous utilisez une solution antivirus non Microsoft et que vous n’utilisez pas Antivirus Microsoft Defender, Antivirus Microsoft Defender est désactivé automatiquement. Lorsque vous désinstallez la solution antivirus non Microsoft, Antivirus Microsoft Defender est activé automatiquement pour protéger vos appareils Windows contre les menaces.    

## <a name="related-content"></a>Contenu associé   

[Configurer la sécurité Microsoft 365 Lighthouse portail d’entreprise](m365-lighthouse-configure-portal-security.md) (article)\
[Microsoft 365 Lighthouse page de conformité des appareils](m365-lighthouse-device-compliance-page-overview.md) (article)\
[Microsoft 365 Lighthouse de la page Utilisateurs](m365-lighthouse-users-page-overview.md) (article)\
[Microsoft 365 Lighthouse de la page Gestion des menaces](m365-lighthouse-threat-management-page-overview.md) (article)\
[MICROSOFT 365 LIGHTHOUSE FAQ](m365-lighthouse-faq.yml)   (article)

