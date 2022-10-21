---
title: Configuration requise pour Microsoft 365 Lighthouse
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
ms.reviewer: crimora
audience: Admin
ms.topic: article
ms.service: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- scotvorg
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Pour les fournisseurs de services managés (MSP), obtenez la liste des conditions requises pour utiliser Microsoft 365 Lighthouse.
ms.openlocfilehash: ebfe68f7c07b1aabc9d83ef57bd973595309e921
ms.sourcegitcommit: 87283bb02ca750286f7c069f811b788730ed5832
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68662948"
---
# <a name="requirements-for-microsoft-365-lighthouse"></a>Configuration requise pour Microsoft 365 Lighthouse

Microsoft 365 Lighthouse est un portail d’administration qui permet aux fournisseurs de services managés (MSP) de sécuriser et de gérer les appareils, les données et les utilisateurs à grande échelle pour les clients des petites et moyennes entreprises (SMB).

Les msp doivent être inscrits au programme Fournisseur de solutions Cloud (CSP) en tant que revendeur indirect ou partenaire de facturation directe pour utiliser Lighthouse.

En outre, chaque locataire du client MSP doit se qualifier pour Lighthouse en respectant les exigences suivantes :

- L’accès délégué doit être configuré pour que le fournisseur de services managés (MSP) puisse gérer le locataire du client*
- Doit avoir au moins un Microsoft 365 Business Premium, Microsoft 365 E3, Microsoft 365 E5, Windows 365 Affaires ou licence Microsoft Defender pour entreprises
- Ne doit pas avoir plus de 2 500 utilisateurs sous licence

\*Des privilèges Administration délégués granulaires (GDAP) ou une relation de privilèges Administration délégués (DAP) sont nécessaires pour intégrer les clients à Lighthouse. Une relation de revendeur indirect n’est plus nécessaire pour intégrer Lighthouse. Si DAP et GDAP coexistent dans un locataire client, les autorisations GDAP sont prioritaires pour les techniciens MSP dans les groupes de sécurité avec GDAP.

## <a name="requirements-for-enabling-device-management"></a>Configuration requise pour activer la gestion des appareils

Pour afficher les appareils clients sur les pages de gestion des appareils, un MSP doit :

- Inscrire tous les appareils des clients dans Microsoft Endpoint Manager (MEM). Pour plus d’informations, consultez [Inscrire des appareils dans Microsoft Intune](/mem/intune/enrollment/).
- Attribuez des stratégies de conformité à tous les appareils des clients. Pour plus d’informations, consultez [Créer une stratégie de conformité dans Microsoft Intune](/mem/intune/protect/create-compliance-policy).

## <a name="requirements-for-enabling-user-management"></a>Configuration requise pour activer la gestion des utilisateurs

Pour que les données client s’affichent dans les rapports sur les pages de gestion des utilisateurs, notamment les utilisateurs à risque, l’authentification multifacteur et la réinitialisation de mot de passe, les locataires clients doivent disposer de licences pour Azure Active Directory Premium P1 ou une version ultérieure. Azure AD Premium P1 est inclus dans Microsoft 365 Business Premium et Microsoft 365 E3. Azure AD Premium P2 est inclus avec Microsoft 365 E5.

## <a name="requirements-for-enabling-threat-management"></a>Configuration requise pour activer la gestion des menaces

Pour afficher les appareils et les menaces des clients sur les pages de gestion des menaces, vous devez inscrire tous les appareils clients dans Microsoft Endpoint Manager (MEM) et les protéger en exécutant Microsoft Defender Antivirus.

Pour plus d’informations, consultez [Inscrire des appareils dans Microsoft Intune](/mem/intune/enrollment/).

Microsoft Defender Antivirus fait partie du système d’exploitation Windows et est activé par défaut sur les appareils exécutant Windows 10.

> [!NOTE]
> Si vous utilisez une solution antivirus non-Microsoft et non Microsoft Defender Antivirus, Microsoft Defender Antivirus est automatiquement désactivé. Lorsque vous désinstallez la solution antivirus non-Microsoft, Microsoft Defender Antivirus est activé automatiquement pour protéger vos appareils Windows contre les menaces.

## <a name="related-content"></a>Contenu associé

[Configurer Microsoft 365 Lighthouse sécurité du portail](m365-lighthouse-configure-portal-security.md) (article)\
[Vue d’ensemble de la page Conformité des appareils dans Microsoft 365 Lighthouse](m365-lighthouse-device-compliance-page-overview.md) (article)\
[Vue d’ensemble de la page Utilisateurs dans Microsoft 365 Lighthouse](m365-lighthouse-users-page-overview.md) (article)\
[Vue d’ensemble de la page Gestion des menaces dans Microsoft 365 Lighthouse](m365-lighthouse-threat-management-page-overview.md) (article)\
[FAQ Microsoft 365 Lighthouse](m365-lighthouse-faq.yml) (article)
