---
title: Ajuster les paramètres après l’inscription
description: Comment exclure certains comptes Microsoft
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: 779aac99a71a15fc204ffc10091459d9a05a0ee0e21166bb1404ad4ad6863c83
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53863941"
---
# <a name="adjust-settings-after-enrollment"></a>Ajuster les paramètres après l’inscription

Une fois que vous avez terminé l’inscription Microsoft Manged Desktop, certains paramètres de gestion devront peut-être être ajustés. Pour vérifier et ajuster si nécessaire, suivez les étapes suivantes :

1. Examinez les Microsoft Intune et Azure Active Directory paramètres décrits dans la section suivante.
2. Si l’un des éléments s’applique à votre environnement, ajustez les modifications décrites.
3. Si vous souhaitez vérifier que tous les paramètres sont [](https://aka.ms/mmdart) corrects, vous pouvez réexécuter l’outil d’évaluation de la disponibilité pour vous assurer qu’aucun conflit n’entre en Microsoft Manged Desktop.

> [!NOTE]
> À mesure que vos opérations se poursuivent au cours des mois suivants, si vous a apporté des modifications après l’inscription à des stratégies en Microsoft Intune, Azure Active Directory ou Microsoft 365 qui affectent Microsoft Manged Desktop, il est possible que Microsoft Manged Desktop ne fonctionne plus correctement. Pour éviter les problèmes avec le service, vérifiez les paramètres spécifiques [décrits](../get-ready/readiness-assessment-fix.md) dans Résoudre les problèmes trouvés par l’outil d’évaluation de la disponibilité avant de modifier les stratégies répertoriées ici. Vous pouvez également réexécuter l’outil d’évaluation de la préparation à tout moment.


## <a name="microsoft-intune-settings"></a>Microsoft Intune paramètres

- Profil autopilot deployment : si vous utilisez des stratégies Autopilot, mettez à jour chacune d’elles pour exclure le groupe Modern **Workplace Devices -All** Azure AD. Pour les mettre à jour, dans la **section** Groupes exclus sous **Affectations,** sélectionnez le groupe Modern **Workplace Devices -All** Azure AD qui a été créé lors de l Microsoft Manged Desktop inscription. Microsoft Manged Desktop également créé un profil Autopilot, dont le nom doit être « Espace de travail moderne » (profil **Autopilot** De l’espace de travail moderne). Lorsque vous mettez à jour vos propres  profils Autopilot, veillez à ne pas exclure le groupe Modern **Workplace Devices -All** Azure AD du profil **Autopilot** Workplace moderne créé par Microsoft Manged Desktop.

- Stratégies d’accès conditionnel : si vous créez des stratégies d’accès conditionnel **liées** à Azure AD, Microsoft Intune ou Microsoft Defender pour le point de terminaison après l’inscription à Microsoft Manged Desktop, excluez-y le groupe Azure AD Comptes de service Espace de travail moderne. Pour obtenir la procédure à suivre, [voir Accès conditionnel : utilisateurs et groupes.](/azure/active-directory/conditional-access/concept-conditional-access-users-groups) Microsoft Manged Desktop des stratégies d’accès conditionnel distinctes pour restreindre l’accès à ces comptes. Pour passer en revue la Microsoft Manged Desktop d’accès conditionnel ( Espace de travail  moderne **–** Station de travail sécurisée), accédez à Microsoft Endpoint Manager et accédez à Accès conditionnel dans **Endpoint Security**. Ne modifiez pas les stratégies d’accès conditionnel Azure AD créées par Microsoft Manged Desktop dont le nom indique « Espace de travail moderne ».

- Authentification multifacteur : si vous créez des exigences d’authentification multifacteur dans les stratégies d’accès conditionnel **liées** à Azure AD, Intune ou Microsoft Defender pour le point de terminaison après l’inscription à Microsoft Manged Desktop, excluez-y le groupe Azure AD Comptes de service Espace de travail moderne. Pour obtenir la procédure à suivre, [voir Accès conditionnel : utilisateurs et groupes.](/azure/active-directory/conditional-access/concept-conditional-access-users-groups) Microsoft Manged Desktop des stratégies d’accès conditionnel distinctes pour restreindre l’accès aux membres de ce groupe. Pour passer en revue la Microsoft Manged Desktop d’accès conditionnel **(** Espace de travail moderne ), accédez à Microsoft Endpoint Manager et accédez à Accès conditionnel **dans** **Endpoint Security**. 

- Windows 10 sonnerie de mise à jour : pour toutes les stratégies de sonnerie de mise à jour Windows 10 que vous avez créées, excluez le groupe Modern **Workplace Devices -All** Azure AD de chaque stratégie. Pour obtenir la procédure à suivre, [voir Créer et affecter des anneaux de mise à jour.](/mem/intune/protect/windows-10-update-rings#create-and-assign-update-rings) Microsoft Manged Desktop aura également créé des stratégies de sonnerie de mise à jour, qui auront toutes le nom « Espace de travail moderne » (par exemple, Stratégie de mise à jour de l’espace de travail moderne **[Large]**, Stratégie de mise à jour de l’espace de travail moderne **[Fast]**, Stratégie de mise à jour de l’espace de travail moderne **[Premier]** et Stratégie de mise à jour de l’espace de travail **moderne [Test]**). Lorsque vous mettez à jour vos  propres stratégies, veillez à ne pas exclure le groupe Modern **Workplace Devices -All** Azure AD de ceux Microsoft Manged Desktop créés.


## <a name="azure-active-directory-settings"></a>Azure Active Directory paramètres

Réinitialisation du mot de passe en libre-service : si vous utilisez la réinitialisation du mot de passe en libre-service pour tous les utilisateurs, ajustez l’affectation pour exclure Microsoft Manged Desktop comptes de service. Pour ajuster cette affectation, créez un groupe dynamique Azure AD pour tous les utilisateurs à l’exception des comptes de service *Microsoft Manged Desktop,* puis utilisez ce groupe pour l’affectation au lieu de « tous les utilisateurs ».

Pour vous aider à rechercher et exclure les comptes de service, voici un exemple de requête dynamique que vous pouvez utiliser :

```Console
(user.objectID -ne null) and (user.userPrincipalName -ne "MSADMIN@TENANT.onmicrosoft.com") and (user.userPrincipalName -ne "MSADMININT@TENANT.onmicrosoft.com") and (user.userPrincipalName -ne "MWAAS_SOC_RO@TENANT.onmicrosoft.com") and (user.userPrincipalName -ne "MWAAS_WDGSOC@TENANT.onmicrosoft.com") and (user.userPrincipalName -ne "MSTEST@TENANT.onmicrosoft.com")
```

Dans cette requête, remplacez @TENANT par votre nom de domaine client.



## <a name="steps-to-get-started-with-microsoft-managed-desktop"></a>Étapes de mise en Microsoft Manged Desktop

1. [Ajouter et vérifier des contacts d’administrateur dans le portail d’administration](add-admin-contacts.md)
2. Ajuster les paramètres après l’inscription (cet article)
3. [Affecter des licences](assign-licenses.md)
4. [Déployer le portail d’entreprise Intune](company-portal.md)
5. [Activer Enterprise State Roaming](enterprise-state-roaming.md)
6. [Configurer les appareils](set-up-devices.md)
7. [Préparer vos utilisateurs à l’utilisation les appareils](get-started-devices.md)
8. [Déployer des applications](deploy-apps.md)