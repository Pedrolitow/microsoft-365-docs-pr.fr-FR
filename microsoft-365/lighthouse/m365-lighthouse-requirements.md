---
title: Conditions requises pour Microsoft 365 Lighthouse
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
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
ms.openlocfilehash: 06d5c5bb0de76ecc8ba9fc28677f480f5f4d5561
ms.sourcegitcommit: 339d2c2ffea06726f69429f73c1113c649f37b18
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2022
ms.locfileid: "65023258"
---
# <a name="requirements-for-microsoft-365-lighthouse"></a>Conditions requises pour Microsoft 365 Lighthouse

Microsoft 365 Lighthouse est un portail d’administration qui permet aux fournisseurs de services gérés (MSP) de sécuriser et de gérer des appareils, des données et des utilisateurs à grande échelle pour les clients de petite et moyenne entreprise (SMB).

Les MSP doivent être inscrits au programme fournisseur de solutions Cloud (CSP) en tant que revendeur indirect ou partenaire de facturation directe pour utiliser Lighthouse.

En outre, chaque locataire client MSP doit être éligible à Lighthouse en répondant aux exigences suivantes :

- Doit avoir configuré l’accès délégué pour que le fournisseur de services managés (MSP) puisse gérer le locataire client*
- Doit avoir au moins une licence Microsoft 365 Business Premium, Microsoft 365 E3 ou Windows 365 Affaires
- Ne doit pas avoir plus de 1 000 utilisateurs sous licence

*Des privilèges d’administrateur délégués (DAP) sont nécessaires pour intégrer des clients à Lighthouse. Nous vous recommandons également d’établir des privilèges d’administrateur délégué granulaires (GDAP) avec vos clients pour permettre un accès délégué plus sécurisé. Bien que DAP et GDAP coexistent, GDAP est prioritaire pour les clients où les deux modèles sont en place. Bientôt, les clients disposant uniquement de GDAP (et pas de DAP) pourront intégrer Lighthouse.

## <a name="requirements-for-enabling-device-management"></a>Configuration requise pour l’activation de la gestion des appareils

Pour afficher les appareils clients locataires dans les pages de gestion des appareils, un fournisseur de services mobiles doit :

- Inscrire tous les appareils clients dans Microsoft Endpoint Manager (MEM). Pour plus d’informations, consultez [Inscrire des appareils dans Microsoft Intune](/mem/intune/enrollment/).
- Attribuez des stratégies de conformité à tous les appareils clients. Pour plus d’informations, consultez [Créer une stratégie de conformité dans Microsoft Intune](/mem/intune/protect/create-compliance-policy).

## <a name="requirements-for-enabling-user-management"></a>Configuration requise pour l’activation de la gestion des utilisateurs

Pour que les données client s’affichent dans les rapports sur les pages de gestion des utilisateurs, notamment les utilisateurs à risque, l’authentification multifacteur et la réinitialisation de mot de passe, les locataires clients doivent disposer de licences pour Azure Active Directory Premium P1 ou version ultérieure. Azure AD Premium P1 est inclus avec Microsoft 365 Business Premium et Microsoft 365 E3.

## <a name="requirements-for-enabling-threat-management"></a>Configuration requise pour l’activation de la gestion des menaces

Pour afficher les appareils clients et les menaces sur les pages de gestion des menaces, vous devez inscrire tous les appareils clients clients dans Microsoft Endpoint Manager (MEM) et les protéger en exécutant Antivirus Microsoft Defender.

Pour plus d’informations, consultez [Inscrire des appareils dans Microsoft Intune](/mem/intune/enrollment/).

Antivirus Microsoft Defender fait partie du système d’exploitation Windows et est activé par défaut sur les appareils exécutant Windows 10.

> [!NOTE]
> Si vous utilisez une solution antivirus non-Microsoft et que vous n’êtes pas Antivirus Microsoft Defender, Antivirus Microsoft Defender est désactivé automatiquement. Lorsque vous désinstallez la solution antivirus non Microsoft, Antivirus Microsoft Defender est activé automatiquement pour protéger vos appareils Windows contre les menaces.

## <a name="related-content"></a>Contenu associé

[Configurer Microsoft 365 Lighthouse sécurité du portail](m365-lighthouse-configure-portal-security.md) (article)\
[Vue d’ensemble de la page Conformité de l’appareil dans Microsoft 365 Lighthouse](m365-lighthouse-device-compliance-page-overview.md) (article)\
[Vue d’ensemble de la page Utilisateurs dans Microsoft 365 Lighthouse](m365-lighthouse-users-page-overview.md) (article)\
[Vue d’ensemble de la page gestion des menaces dans Microsoft 365 Lighthouse](m365-lighthouse-threat-management-page-overview.md) (article)\
[MICROSOFT 365 LIGHTHOUSE FAQ](m365-lighthouse-faq.yml) (article)
