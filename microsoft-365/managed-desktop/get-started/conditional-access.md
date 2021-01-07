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
ms.openlocfilehash: e78f0123c909c90ff90be913e8775cc1e5b30313
ms.sourcegitcommit: 3bf4f1c0d3a8515cca651b2a520217195f89457f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2021
ms.locfileid: "49777098"
---
# <a name="adjust-settings-after-enrollment"></a>Ajuster les paramètres après l’inscription

Une fois que vous avez terminé l’enregistrement dans le bureau géré Microsoft, vous devez ajuster les paramètres Microsoft Intune et Azure Active Directory (Azure AD) spécifiés dans cet article pour permettre la gestion et maintenir la sécurité. Définissez les paramètres suivants pour exclure les groupes Azure AD spécifiques qui contiennent des utilisateurs et des appareils de bureau gérés Microsoft. Pour connaître les étapes à suivre pour exclure des groupes, consultez la rubrique [accès conditionnel : utilisateurs et groupes](https://docs.microsoft.com/azure/active-directory/conditional-access/concept-conditional-access-users-groups#exclude-users).

> [!NOTE]
> Si vous effectuez des modifications après l’enregistrement des stratégies dans Microsoft Intune, Azure Active Directory ou Microsoft 365, il est possible que Microsoft Managed Desktop puisse cesser de fonctionner correctement. Pour éviter les problèmes liés aux opérations de bureau géré Microsoft, vérifiez les paramètres spécifiques décrits dans [corriger les problèmes détectés par l’outil d’évaluation de la disponibilité](../get-ready/readiness-assessment-fix.md) avant de modifier des stratégies.


## <a name="microsoft-intune-settings"></a>Paramètres Microsoft Intune

- Profil de déploiement de AutoPilot : pour les profils AutoPilot créés par les administrateurs de votre entreprise, excluez les groupes de **travail modernes-tous les** groupes Azure ad. Pour connaître les étapes à suivre, consultez la rubrique [inscrire des appareils Windows dans Intune à l’aide de Windows AutoPilot](https://docs.microsoft.com/mem/autopilot/enrollment-autopilot). N’excluez pas les **appareils d’espace de travail modernes-tous les** groupes Azure AD de toutes les stratégies de déploiement créées par Microsoft Managed Desktop dont le nom est « moderne Workplace » (par exemple, **Profil AutoPilot de l’espace de travail moderne**). 
- Stratégies d’accès conditionnel : pour les stratégies d’accès conditionnel créées par les administrateurs de votre entreprise, excluez le groupe Azure AD de **comptes de service espace de travail moderne** . Pour connaître les étapes à suivre, consultez la rubrique [accès conditionnel : utilisateurs et groupes](https://docs.microsoft.com/azure/active-directory/conditional-access/concept-conditional-access-users-groups). N’excluez pas les **appareils de travail modernes-tous les** groupes Azure ad des stratégies créées par Microsoft Managed Desktop dont le nom est « moderne Workplace » (par exemple, **Modern Workplace Secure Workstation**).
- Authentification multifacteur : Assurez-vous que toutes les stratégies d’accès conditionnel créées par les administrateurs de votre entreprise qui nécessitent une authentification multifacteur excluent le groupe Azure AD de **comptes de service espace de travail moderne** . Pour plus d’informations, reportez-vous à [stratégies d’accès conditionnel](../get-ready/readiness-assessment-fix.md#conditional-access-policies) et [accès conditionnel : exiger l’authentification multifacteur pour tous les utilisateurs](https://docs.microsoft.com/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa).
- Base de sécurité : pour les stratégies de base de sécurité créées par les administrateurs de votre entreprise, excluez les groupes de **travail modernes-tous les**  groupes Azure ad. Pour connaître les étapes à suivre, voir [Use Security baselines to configure Windows 10 Devices in Intune](https://docs.microsoft.com/mem/intune/protect/security-baselines). N’excluez pas les **appareils de travail modernes-tous les** groupes Azure AD de toutes les stratégies créées par Microsoft Managed Desktop dont le nom est « moderne Workplace » (par exemple, base de sécurité de l' **espace de travail moderne**).
- Sonnerie de mise à jour Windows 10 : pour les stratégies Ring de mise à jour Windows 10 créées par les administrateurs de votre entreprise, excluez les **périphériques Workplace modernes-tous les**  groupes Azure ad. Pour connaître les étapes à suivre, voir [Manage Windows 10 Software Updates in Intune](https://docs.microsoft.com/mem/intune/protect/windows-update-for-business-configure). N’excluez pas les **appareils de travail modernes-tous les** groupes Azure AD de toutes les stratégies créées par le bureau géré Microsoft dont le nom comporte « travail moderne » (par exemple, la stratégie **moderne mise à jour** de l’espace de travail).


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
