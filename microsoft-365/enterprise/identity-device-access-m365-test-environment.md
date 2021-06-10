---
title: Accès aux identités et appareils pour votre environnement de test Microsoft 365
author: JoeDavies-MSFT
f1.keywords:
- NOCSH
ms.author: josephd
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Créer un environnement Microsoft 365 pour tester l’accès aux identités et appareils.
ms.openlocfilehash: 5a9e9ef9ea6b8f6dc80aa7fea225f3573b8fcadc
ms.sourcegitcommit: dcb97fbfdae52960ae62b6faa707a05358193ed5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "51197874"
---
# <a name="identity-and-device-access-for-your-microsoft-365-test-environment"></a>Accès aux identités et appareils pour votre environnement de test Microsoft 365

*Ce Guide de laboratoire de test ne peut être utilisé que pour Microsoft 365 pour les environnements de test d’entreprise.*

[Les configurations](../security/office-365-security/microsoft-365-policies-configurations.md) d’accès aux identités et appareils sont un ensemble de configurations recommandées et de stratégies d’accès conditionnel pour protéger l’accès à tous les services intégrés à Azure Active Directory (Azure AD).

Pour créer un environnement de test qui dispose des configurations communes d’accès aux identités et aux appareils :

1. Configurez votre environnement de test avec les fonctionnalités d’identité et de sécurité requises en fonction du modèle d’identité et de la méthode d’authentification que vous avez choisis :

  - [Cloud uniquement](cloud-only-prereqs-m365-test-environment.md)
  - [Synchronisation de hachage de mot de passe (PHS)](phs-prereqs-m365-test-environment.md)
  - [Authentification directe (PTA)](pta-prereqs-m365-test-environment.md)

2. Utilisez [des stratégies](../security/office-365-security/identity-access-policies.md) communes d’accès aux identités et appareils pour configurer les stratégies qui s’appuient sur les conditions préalables configurées pour votre environnement de test et explorer et vérifier la protection des identités et des appareils.

## <a name="see-also"></a>Voir aussi

[Guides de laboratoire de Test Autres identités](m365-enterprise-test-lab-guides.md#identity)

[Feuille de route des identités](identity-roadmap-microsoft-365.md)

[Microsoft 365 pour les entreprises Guides de laboratoire d'essai](m365-enterprise-test-lab-guides.md)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Documentation Microsoft 365 Entreprise](/microsoft-365-enterprise/)
