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
ms.openlocfilehash: 88a832f6c4e17756bfb25ef5cb7c4c5ecedaf2c0
ms.sourcegitcommit: 9833f95ab6ab95aea20d68a277246dca2223f93d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2021
ms.locfileid: "49794387"
---
# <a name="adjust-settings-after-enrollment"></a>Ajuster les paramètres après l’inscription

Une fois que vous avez terminé l’inscription au Bureau géré Microsoft, certains paramètres de gestion devront peut-être être ajustés. Pour vérifier et ajuster si nécessaire, suivez les étapes suivantes :

1. Examinez les paramètres Microsoft Intune et Azure Active Directory décrits dans la section suivante.
2. Si l’un des éléments s’applique à votre environnement, ajustez les modifications décrites.
3. Si vous souhaitez vérifier que tous les paramètres sont [](https://aka.ms/mmdart) corrects, vous pouvez réexécuter l’outil d’évaluation de la préparation pour vous assurer qu’aucun conflit n’entre en conflit avec Le Bureau géré Microsoft.

> [!NOTE]
> Comme vos opérations se poursuivent au cours des mois suivants, si vous az apporté des modifications après l’inscription aux stratégies dans Microsoft Intune, Azure Active Directory ou Microsoft 365 qui affectent Bureau géré Microsoft, il est possible que Bureau géré Microsoft cesse de fonctionner correctement. Pour éviter les problèmes avec le service, vérifiez les paramètres spécifiques [décrits](../get-ready/readiness-assessment-fix.md) dans Résoudre les problèmes trouvés par l’outil d’évaluation de la disponibilité avant de modifier les stratégies répertoriées ici. Vous pouvez également réexécuter l’outil d’évaluation de la préparation à tout moment.


## <a name="microsoft-intune-settings"></a>Paramètres Microsoft Intune

- Profil autopilot deployment : si vous utilisez des stratégies Autopilot, mettez à jour chacune d’elles pour exclure le groupe Modern **Workplace Devices -All** Azure AD. Pour les mettre à jour, dans la **section** Groupes exclus sous **Affectations,** sélectionnez le groupe Modern **Workplace Devices -All** Azure AD qui a été créé lors de l’inscription au Bureau géré Microsoft. Bureau géré Microsoft aura également créé un profil Autopilot, dont le nom sera « Espace de travail moderne » (profil **Autopilot** Espace de travail moderne). Lorsque vous mettez à jour vos propres  profils Autopilot, veillez à ne pas exclure le groupe Modern **Workplace Devices -All** Azure AD du profil **Autopilot** Workplace moderne créé par Bureau géré Microsoft.

- Stratégies d’accès conditionnel : pour les stratégies d’accès conditionnel que vous avez **créées,** excluez le groupe Azure AD Comptes de service Workplace modernes. Pour obtenir la procédure à suivre, [voir Accès conditionnel : utilisateurs et groupes.](https://docs.microsoft.com/azure/active-directory/conditional-access/concept-conditional-access-users-groups) Bureau géré Microsoft aura également créé certaines stratégies d’accès conditionnel, qui auront toutes le nom « Espace de travail moderne » (par **exemple,** Station de travail sécurisée de l’espace de travail moderne). Lorsque vous mettez à jour vos  propres stratégies d’accès conditionnel, veillez à ne pas exclure le groupe Modern **Workplace Devices -All** Azure AD des stratégies créées par Bureau géré Microsoft.

- Authentification multifacteur : assurez-vous que vos **stratégies** d’accès conditionnel qui nécessitent une authentification multifacteur excluent le groupe Azure AD Comptes de service Workplace modernes. Pour plus d’informations, voir [Stratégies d’accès conditionnel](../get-ready/readiness-assessment-fix.md#conditional-access-policies) et [Accès conditionnel : exiger l' approbation de mfa pour tous les utilisateurs.](https://docs.microsoft.com/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa)

- Anneau de mise à jour Windows 10 : pour toutes les stratégies d’anneau de mise à jour Windows 10 que vous avez créées, excluez le groupe Modern **Workplace Devices -All** Azure AD de chaque stratégie. Pour obtenir la procédure à suivre, [voir Créer et affecter des anneaux de mise à jour.](https://docs.microsoft.com/mem/intune/protect/windows-10-update-rings#create-and-assign-update-rings) Bureau géré Microsoft aura également créé des stratégies de sonnerie de mise à jour, qui auront toutes le nom « Espace de travail moderne » (par exemple, Stratégie de mise à jour de l’espace de travail moderne **[Large]**, Stratégie de mise à jour de l’espace de travail moderne **[Fast]**, Stratégie de mise à jour de l’espace de travail moderne **[Premier]** et Stratégie de mise à jour de l’espace de travail **moderne [Test]**). Lorsque vous mettez à jour vos  propres stratégies, veillez à ne pas exclure le groupe Modern **Workplace Devices -All** Azure AD de ceux créés par Microsoft Managed Desktop.


## <a name="azure-active-directory-settings"></a>Paramètres Azure Active Directory

Réinitialisation du mot de passe en libre-service : si vous utilisez la réinitialisation du mot de passe en libre-service pour tous les utilisateurs, ajustez l’affectation pour exclure les comptes du service Bureau géré Microsoft. Pour ajuster cette affectation, créez un groupe dynamique Azure AD pour tous les utilisateurs à l’exception des comptes de service *Bureau* géré Microsoft, puis utilisez ce groupe pour l’affectation au lieu de « tous les utilisateurs ».

Pour vous aider à rechercher et exclure les comptes de service, voici un exemple de requête dynamique que vous pouvez utiliser :

```Console
(user.objectID -ne null) and (user.userPrincipalName -ne "MSADMIN@TENANT.onmicrosoft.com") and (user.userPrincipalName -ne "MSADMININT@TENANT.onmicrosoft.com") and (user.userPrincipalName -ne "MWAAS_SOC_RO@TENANT.onmicrosoft.com") and (user.userPrincipalName -ne "MWAAS_WDGSOC@TENANT.onmicrosoft.com") and (user.userPrincipalName -ne "MSTEST@TENANT.onmicrosoft.com")
```

Dans cette requête, remplacez @TENANT par votre nom de domaine client.



## <a name="steps-to-get-started-with-microsoft-managed-desktop"></a>Étapes de mise en place du Bureau géré Microsoft

1. [Ajouter et vérifier des contacts d’administrateur dans le portail d’administration](add-admin-contacts.md)
2. Ajuster les paramètres après l’inscription (cet article)
3. [Affecter des licences](assign-licenses.md)
4. [Déployer le portail d’entreprise Intune](company-portal.md)
5. [Activer Enterprise State Roaming](enterprise-state-roaming.md)
6. [Configurer les appareils](set-up-devices.md)
7. [Préparer vos utilisateurs à l’utilisation les appareils](get-started-devices.md)
8. [Déployer des applications](deploy-apps.md)
