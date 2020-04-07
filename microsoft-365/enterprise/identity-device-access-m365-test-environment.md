---
title: Accès aux identités et appareils pour votre environnement de test Microsoft 365
author: JoeDavies-MSFT
f1.keywords:
- NOCSH
ms.author: josephd
manager: laurawi
ms.date: 04/23/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Créer un environnement Microsoft 365 pour tester l’accès aux identités et appareils.
ms.openlocfilehash: 45749140698553a75df50ed1111cdbfc8eb15684
ms.sourcegitcommit: e525bcf073a61e1350484719a0c3ceb6ff0d8db1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "43153737"
---
# <a name="identity-and-device-access-for-your-microsoft-365-test-environment"></a>Accès aux identités et appareils pour votre environnement de test Microsoft 365

*Ce Guide de Laboratoire Test peut uniquement être utilisé pour les environnements de test Microsoft 365 Entreprise*.

Les [configurations d’accès aux identités et appareils](microsoft-365-policies-configurations.md) sont un ensemble de fonctionnalités et de stratégies d’accès conditionnel permettant de protéger l’accès à tous les services intégrés à Azure Active Directory (Azure AD), parmi lesquels Office 365 et Microsoft Intune dans Microsoft 365 Entreprise.

Pour créer un environnement de test disposant des stratégies suivantes :

1. Configurez votre environnement de test avec les fonctionnalités d’identité et de sécurité requises en fonction du modèle d’identité et de la méthode d’authentification que vous avez choisis :

  - [Cloud uniquement](cloud-only-prereqs-m365-test-environment.md)
  - [Synchronisation de hachage de mot de passe (PHS)](phs-prereqs-m365-test-environment.md)
  - [Authentification directe (PTA)](pta-prereqs-m365-test-environment.md)

2. Utilisez des [stratégies courantes d’accès aux identités et appareils](identity-access-policies.md) pour configurer des stratégies qui respectent des conditions préalables et testent la protection des identités et appareils.

## <a name="see-also"></a>Voir aussi

[Guides de laboratoire de Test Autres identités](m365-enterprise-test-lab-guides.md#identity)

[Étape 2 : Identité](identity-infrastructure.md)

[Guides de laboratoire de test Microsoft 365 Entreprise](m365-enterprise-test-lab-guides.md)

[Déploiement de Microsoft 365 Entreprise](deploy-microsoft-365-enterprise.md)

[Documentation Microsoft 365 Entreprise](https://docs.microsoft.com/microsoft-365-enterprise/)
