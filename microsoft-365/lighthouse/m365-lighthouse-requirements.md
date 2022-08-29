---
title: Conditions requises pour Microsoft 365 Lighthouse
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: crimora
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Pour les fournisseurs de services gérés (MSP), obtenez une liste des conditions requises pour utiliser Microsoft 365 Lighthouse.
ms.openlocfilehash: 6ed55b436d110c43ce0a87d12049988105c79c48
ms.sourcegitcommit: d1f51dbd12ceffe6a6aeebffde0f9a744486f2d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/23/2022
ms.locfileid: "67417431"
---
# <a name="requirements-for-microsoft-365-lighthouse"></a>Conditions requises pour Microsoft 365 Lighthouse

Microsoft 365 Lighthouse est un portail d’administration qui permet aux fournisseurs de services gérés (MSP) de sécuriser et de gérer des appareils, des données et des utilisateurs à grande échelle pour les clients de petite et moyenne entreprise (SMB).

Les fournisseurs de solutions cloud doivent être inscrits au programme fournisseur de solutions cloud (CSP) en tant que revendeur indirect ou partenaire de facturation directe pour utiliser Lighthouse.

En outre, chaque locataire client MSP doit être éligible à Lighthouse en répondant aux exigences suivantes :

- Doit avoir configuré l’accès délégué pour que le fournisseur de services managés (MSP) puisse gérer le locataire client*
- Doit avoir au moins une Microsoft 365 Business Premium, Microsoft 365 E3, Microsoft 365 E5, Windows 365 Affaires ou licence Microsoft Defender pour entreprises
- Ne doit pas avoir plus de 2 500 utilisateurs sous licence

 \*Des privilèges délégués granulaires Administration (GDAP) plus une relation de revendeur indirect ou une relation de privilèges délégués Administration (DAP) sont nécessaires pour intégrer des clients à Lighthouse. Si DAP et GDAP coexistent dans un locataire client, les autorisations GDAP sont prioritaires pour les techniciens MSP dans les groupes de sécurité compatibles GDAP. Bientôt, les clients ayant des relations GDAP uniquement (sans relations de revendeur indirect) pourront intégrer Lighthouse.

## <a name="requirements-for-enabling-device-management"></a>Configuration requise pour l’activation de la gestion des appareils

Pour afficher les appareils clients locataires dans les pages de gestion des appareils, un fournisseur de services mobiles doit :

- Inscrire tous les appareils clients dans Microsoft Endpoint Manager (MEM). Pour plus d’informations, consultez [Inscrire des appareils dans Microsoft Intune](/mem/intune/enrollment/).
- Attribuez des stratégies de conformité à tous les appareils clients. Pour plus d’informations, consultez [Créer une stratégie de conformité dans Microsoft Intune](/mem/intune/protect/create-compliance-policy).

## <a name="requirements-for-enabling-user-management"></a>Configuration requise pour l’activation de la gestion des utilisateurs

Pour que les données client s’affichent dans les rapports sur les pages de gestion des utilisateurs, notamment les utilisateurs à risque, l’authentification multifacteur et la réinitialisation de mot de passe, les locataires clients doivent disposer de licences pour Azure Active Directory Premium P1 ou version ultérieure. Azure AD Premium P1 est inclus avec Microsoft 365 Business Premium et Microsoft 365 E3. Azure AD Premium P2 est inclus avec Microsoft 365 E5.

## <a name="requirements-for-enabling-threat-management"></a>Configuration requise pour l’activation de la gestion des menaces

Pour afficher les appareils clients et les menaces sur les pages de gestion des menaces, vous devez inscrire tous les appareils clients clients dans Microsoft Endpoint Manager (MEM) et les protéger en exécutant l’Antivirus Microsoft Defender.

Pour plus d’informations, consultez [Inscrire des appareils dans Microsoft Intune](/mem/intune/enrollment/).

L’Antivirus Microsoft Defender fait partie du système d’exploitation Windows et est activé par défaut sur les appareils exécutant Windows 10.

> [!NOTE]
> Si vous utilisez une solution antivirus non-Microsoft et non l’antivirus Microsoft Defender, l’antivirus Microsoft Defender est automatiquement désactivé. Lorsque vous désinstallez la solution antivirus non Microsoft, l’antivirus Microsoft Defender est activé automatiquement pour protéger vos appareils Windows contre les menaces.

## <a name="related-content"></a>Contenu associé

[Configurer Microsoft 365 Lighthouse sécurité du portail](m365-lighthouse-configure-portal-security.md) (article)\
[Vue d’ensemble de la page Conformité de l’appareil dans Microsoft 365 Lighthouse](m365-lighthouse-device-compliance-page-overview.md) (article)\
[Vue d’ensemble de la page Utilisateurs dans Microsoft 365 Lighthouse](m365-lighthouse-users-page-overview.md) (article)\
[Vue d’ensemble de la page gestion des menaces dans Microsoft 365 Lighthouse](m365-lighthouse-threat-management-page-overview.md) (article)\
[MICROSOFT 365 LIGHTHOUSE FAQ](m365-lighthouse-faq.yml) (article)
