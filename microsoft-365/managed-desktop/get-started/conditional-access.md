---
title: Ajuster les paramètres après l’inscription
description: Procédure d’exclusion de certains comptes Microsoft
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: d7fe410f114d43d4f6c983aaf23d949298635318
ms.sourcegitcommit: 222fb7fe2b26dde3d8591b61cc02113d6135012c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "49760102"
---
# <a name="adjust-settings-after-enrollment"></a>Ajuster les paramètres après l’inscription

Une fois que vous avez terminé l’enregistrement dans le bureau géré Microsoft, vous devez ajuster certains paramètres Microsoft Intune et Azure Active Directory (Azure AD) pour permettre la gestion et assurer la sécurité. Définissez les paramètres suivants pour exclure les groupes Azure AD qui contiennent des utilisateurs et des appareils de bureau gérés Microsoft. Pour connaître les étapes à suivre pour exclure des groupes, consultez la rubrique [accès conditionnel : utilisateurs et groupes](https://docs.microsoft.com/azure/active-directory/conditional-access/concept-conditional-access-users-groups#exclude-users).

> [!NOTE]
> Si vous effectuez des modifications après l’enregistrement des stratégies dans Microsoft Intune, Azure Active Directory ou Microsoft 365, il est possible que Microsoft Managed Desktop puisse cesser de fonctionner correctement. Pour éviter les problèmes liés aux opérations de bureau géré Microsoft, vérifiez les paramètres spécifiques décrits dans [corriger les problèmes détectés par l’outil d’évaluation de la disponibilité](../get-ready/readiness-assessment-fix.md) avant de modifier des stratégies.


## <a name="microsoft-intune-settings"></a>Paramètres Microsoft Intune

- Profil de déploiement de AutoPilot : excluez les **périphériques Workplace modernes-tous les**  groupes Azure ad. Pour connaître les étapes à suivre, consultez la rubrique [inscrire des appareils Windows dans Intune à l’aide de Windows AutoPilot](https://docs.microsoft.com/mem/autopilot/enrollment-autopilot).
- Stratégies d’accès conditionnel : exclure le groupe Azure AD de comptes de service de l' **espace de travail moderne** . Pour connaître les étapes à suivre, consultez la rubrique [accès conditionnel : utilisateurs et groupes](https://docs.microsoft.com/azure/active-directory/conditional-access/concept-conditional-access-users-groups).
- Authentification multifacteur : Assurez-vous que toutes les stratégies d’accès conditionnel nécessitant une authentification multifacteur excluent le groupe Azure AD de **comptes de service espace de travail moderne** . Pour plus d’informations, reportez-vous à [stratégies d’accès conditionnel](../get-ready/readiness-assessment-fix.md#conditional-access-policies) et [accès conditionnel : exiger l’authentification multifacteur pour tous les utilisateurs](https://docs.microsoft.com/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa).
- Ligne de base de sécurité : excluez les **périphériques d’espace de travail modernes-tous les**  groupes Azure ad. Pour connaître les étapes à suivre, voir [Use Security baselines to configure Windows 10 Devices in Intune](https://docs.microsoft.com/mem/intune/protect/security-baselines).
- Anneau de mise à jour Windows 10 : excluez les groupes **de travail modernes-tous les**  groupes Azure ad. Pour connaître les étapes à suivre, voir [Manage Windows 10 Software Updates in Intune](https://docs.microsoft.com/mem/intune/protect/windows-update-for-business-configure).


## <a name="azure-active-directory-settings"></a>Paramètres Azure Active Directory

Réinitialisation du mot de passe en libre-service : choisissez le paramètre **sélectionné** , puis sélectionnez **périphériques Workplace modernes-tous les** groupes Azure ad. Pour plus d’informations, consultez [la rubrique Tutorial : autoriser les utilisateurs à déverrouiller leur compte ou réinitialiser les mots de passe à l’aide de la réinitialisation du mot de passe en libre-service Azure Active Directory](https://docs.microsoft.com/azure/active-directory/authentication/tutorial-enable-sspr).



## <a name="steps-to-get-started-with-microsoft-managed-desktop"></a>Étapes de prise en main de Microsoft Managed Desktop

1. [Ajouter et vérifier des contacts d’administrateur dans le portail d’administration](add-admin-contacts.md)
2. Ajuster les paramètres après l’enregistrement (cet article)
3. [Affecter des licences](assign-licenses.md)
4. [Déployer le portail d’entreprise Intune](company-portal.md)
5. [Activer Enterprise State Roaming](enterprise-state-roaming.md)
6. [Configurer les appareils](set-up-devices.md)
7. [Préparer vos utilisateurs à l’utilisation les appareils](get-started-devices.md)
8. [Déployer des applications](deploy-apps.md)
