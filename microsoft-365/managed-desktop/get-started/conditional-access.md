---
title: Ajustement de l’accès conditionnel
description: Procédure d’exclusion de certains comptes Microsoft
keywords: Microsoft Managed Desktop, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.openlocfilehash: 1b91186837ad558965d675f82d013a7081c7c7ec
ms.sourcegitcommit: 3d37043c0447359c952dc99026c219dd69f6fb8d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2019
ms.locfileid: "38012461"
---
# <a name="adjust-conditional-access"></a>Ajustement de l’accès conditionnel

Si vous utilisez des stratégies d' [accès conditionnel](https://docs.microsoft.com/azure/active-directory/conditional-access/overview) dans votre organisation, vous devez les définir pour exclure certains comptes afin que le bureau géré Microsoft puisse fonctionner correctement.

Pour cela, procédez comme suit:

1. Reportez-vous à la section « étapes de restauration » de la rubrique [How to : plan Your ConditionalAttribute Access Deployment in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/conditional-access/plan-conditional-access#rollback-steps).
2. Suivez les étapes ci-dessous pour exclure le groupe de *comptes de service d’espace de travail moderne* pour toutes les stratégies.


Si vous rencontrez des difficultés avec l’accès conditionnel, contactez le [support](../working-with-managed-desktop/admin-support.md)d’administration.

## <a name="steps-to-get-started-with-microsoft-managed-desktop"></a>Étapes de prise en main de Microsoft Managed Desktop

1. [Ajouter et vérifier des contacts d’administration dans le portail d’administration](add-admin-contacts.md)
2. Ajuster l’accès conditionnel (cette rubrique)
3. [Attribuer des licences](assign-licenses.md)
4. [Déployer le portail d’entreprise Intune](company-portal.md)
5. [Activer l’itinérance de l’état d’entreprise](enterprise-state-roaming.md)
6. [Configurer les appareils](set-up-devices.md)
7. [Préparer vos utilisateurs à l’utilisation des appareils](get-started-devices.md)
8. [Déployer des applications](deploy-apps.md)