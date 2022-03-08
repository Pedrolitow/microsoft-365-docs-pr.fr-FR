---
title: Ajuster les paramètres après l’inscription
description: Comment exclure certains comptes Microsoft
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: a5ff8a9a662eb442b7a18726463f14e914d4a133
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63317540"
---
# <a name="adjust-settings-after-enrollment"></a>Ajuster les paramètres après l’inscription

Une fois que vous avez terminé l’inscription Microsoft Manged Desktop, certains paramètres de gestion devront peut-être être ajustés. Pour vérifier et ajuster si nécessaire, suivez les étapes suivantes :

1. Examinez les paramètres Microsoft Intune et Azure Active Directory décrits dans la section suivante.
2. Si l’un des éléments s’applique à votre environnement, ajustez-le comme décrit.
3. Si vous souhaitez vérifier que tous les paramètres sont corrects, vous pouvez réexécuter [](https://aka.ms/mmdart) l’outil d’évaluation de la disponibilité pour vous assurer qu’aucun conflit n’entre en Microsoft Manged Desktop.

> [!NOTE]
> À mesure que vos opérations se poursuivent au cours des mois suivants, si vous az apporté des modifications après l’inscription à des stratégies dans Microsoft Intune, Azure Active Directory ou Microsoft 365 qui affectent Microsoft Manged Desktop, il est possible que Microsoft Manged Desktop pouvez arrêter de fonctionner correctement. Pour éviter les problèmes avec le service, vérifiez les paramètres spécifiques [décrits](../get-ready/readiness-assessment-fix.md) dans Résoudre les problèmes trouvés par l’outil d’évaluation de la disponibilité avant de modifier les stratégies répertoriées ici. Vous pouvez également réexécuter l’outil d’évaluation de la préparation à tout moment.

## <a name="microsoft-intune-settings"></a>Microsoft Intune paramètres

| Setting | Description |
| ------ | ------ |
| Profil Autopilot Deployment | Si vous utilisez des stratégies Autopilot, mettez à jour chacune d’elles pour exclure le groupe Modern **Workplace Devices -All** Azure AD group. <br><br> **Pour mettre à jour les stratégies Autopilot :** <br><br> Sous **Affectations**, dans les groupes **exclus,** sélectionnez le groupe Appareils de l’espace de travail **moderne -Tous** Azure AD créé lors de l’Microsoft Manged Desktop inscription. <br><br> Microsoft Manged Desktop également créé un profil Autopilot, dont le nom doit être « Espace de travail moderne » (profil **Autopilot De l’espace** de travail moderne). Lorsque vous mettez à jour vos propres profils Autopilot,  veillez à ne pas exclure le groupe Modern **Workplace Devices -All** Azure AD du profil **Autopilot** Workplace moderne créé par Microsoft Manged Desktop. |
| Stratégies d’accès conditionnel | Si vous créez des stratégies d’accès conditionnel relatives à Azure AD, Microsoft Intune ou Microsoft 365 Defender pour le point de terminaison après Microsoft Manged Desktop inscription, excluez les comptes de service Espace de travail **modernes** Azure AD groupe à partir de ces groupes. Pour plus d’informations, voir [Accès conditionnel : utilisateurs et groupes](/azure/active-directory/conditional-access/concept-conditional-access-users-groups). Microsoft Manged Desktop des stratégies d’accès conditionnel distinctes pour restreindre l’accès à ces comptes. <br><br> **Pour passer en revue la stratégie Microsoft Manged Desktop’accès conditionnel (Espace de travail moderne – Station de travail sécurisée) :** <br><br> Accédez à Microsoft Endpoint Manager et accédez à **Accès conditionnel** dans **Sécurité des points de terminaison**. Ne modifiez pas les stratégies Azure AD d’accès conditionnel créées par Microsoft Manged Desktop dont le nom indique « Espace de travail moderne ». |
| Authentification multifacteur | Si vous créez des exigences d’authentification multifacteur dans les stratégies d’accès conditionnel liées à Azure AD, Intune ou Microsoft 365 Defender pour le point de terminaison après l’inscription à Microsoft Manged Desktop, excluez le groupe Azure AD Comptes de service Workplace modernes de ces **derniers**. Pour plus d’informations, voir [Accès conditionnel : utilisateurs et groupes](/azure/active-directory/conditional-access/concept-conditional-access-users-groups). Microsoft Manged Desktop des stratégies d’accès conditionnel distinctes pour restreindre l’accès aux membres de ce groupe. <br><br> **Pour passer en revue la Microsoft Manged Desktop d’accès conditionnel (Espace de travail moderne -) :** <br><br> Accédez à Microsoft Endpoint Manager et accédez à **Accès conditionnel** dans **Sécurité des points de terminaison**.
| Windows 10 sonnerie de mise à jour | Pour les Windows 10 de sonnerie de mise à jour que vous avez créées, excluez le groupe Modern **Workplace Devices -All** Azure AD de chaque stratégie. Pour plus d’informations, voir [Créer et affecter des anneaux de mise à jour](/mem/intune/protect/windows-10-update-rings#create-and-assign-update-rings). <br><br> Microsoft Manged Desktop vous aurez également créé des stratégies de sonnerie de mise à jour, dont le nom sera « Espace de travail moderne ». Par exemple : <ul><li>Stratégie de mise à jour de l’espace de travail moderne [large]</li><li>Stratégie de mise à jour de l’espace de travail moderne [Rapide]</li><li>Stratégie de mise à jour de l’espace de travail moderne [Premier]</li><li>Stratégie de mise à jour de l’espace de travail moderne [Test]</li></ul> <br>Lorsque vous mettez à jour vos propres stratégies, assurez-vous que vous *n’excluez* pas le groupe Modern **Workplace Devices -All** Azure AD de ceux Microsoft Manged Desktop créés. |

## <a name="azure-active-directory-settings"></a>Azure Active Directory paramètres

Réinitialisation du mot de passe en libre-service : si vous utilisez la réinitialisation du mot de passe en libre-service pour tous les utilisateurs, ajustez l’affectation pour exclure Microsoft Manged Desktop comptes de service.

**Pour ajuster cette affectation :**

1. Créer un groupe Azure AD pour tous les utilisateurs à *l’exception Microsoft Manged Desktop* comptes de service
1. Utilisez ce groupe pour l’affectation au lieu de « tous les utilisateurs ».

Pour vous aider à rechercher et exclure les comptes de service, voici un exemple de requête dynamique que vous pouvez utiliser :

```Console
(user.objectID -ne null) and (user.userPrincipalName -ne "MSADMIN@TENANT.onmicrosoft.com") and (user.userPrincipalName -ne "MSADMININT@TENANT.onmicrosoft.com") and (user.userPrincipalName -ne "MWAAS_SOC_RO@TENANT.onmicrosoft.com") and (user.userPrincipalName -ne "MWAAS_WDGSOC@TENANT.onmicrosoft.com") and (user.userPrincipalName -ne "MSTEST@TENANT.onmicrosoft.com")
```

Dans cette requête, remplacez-la `@TENANT` par votre nom de domaine client.

## <a name="steps-to-get-started-with-microsoft-managed-desktop"></a>Étapes de mise en Microsoft Manged Desktop

1. Accéder au[Portail d’administration](access-admin-portal.md).
1. [Ajouter et vérifier des contacts d’administrateur dans le portail d’administration](add-admin-contacts.md).
1. Ajuster les paramètres après l’inscription (cet article).
1. Déployez et affectez le[Portail d’entreprise Intune](company-portal.md).
1. [Attribuer des licences](assign-licenses.md).
1. [Déployer des applications](deploy-apps.md).
1. [Préparez les appareils](prepare-devices.md).
1. Configurez l’[Expérience de première exécution avec Autopilot et la page d’état d’inscription](esp-first-run.md).
1. [Activer les fonctionnalités de support utilisateur](enable-support.md).
1. [Préparez vos utilisateurs à utiliser des appareils](get-started-devices.md).
1. [Démarrage avec le contrôle d’application](get-started-app-control.md).
