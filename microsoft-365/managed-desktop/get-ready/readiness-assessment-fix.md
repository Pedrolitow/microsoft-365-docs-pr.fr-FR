---
title: Résoudre les problèmes détectés par l’outil de préparation et d’évaluation
description: Actions détaillées à prendre pour chaque problème trouvé par l’outil
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: f1af39a9b2a09908ecf5f5ff15b9fd6d764459d6
ms.sourcegitcommit: 7ecd10b302b3b3dfa4ba3be3a6986dd3c189fbff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/21/2021
ms.locfileid: "49921857"
---
# <a name="fix-issues-found-by-the-readiness-assessment-tool"></a>Résoudre les problèmes détectés par l’outil de préparation et d’évaluation

Pour chaque vérification, l’outil signalera l’un des quatre résultats possibles :


|Résultat  |Signification  |
|---------|---------|
|Prêt     | Aucune action n’est requise avant de terminer l’inscription.        |
|Avis    | Suivez les étapes de l’outil ou de cet article pour une expérience de l’inscription et pour les utilisateurs. Vous *pouvez terminer* l’inscription, mais vous devez résoudre ces problèmes avant de déployer votre premier appareil.        |
|Non prêt | *L’inscription échoue si vous ne corrigez pas ces problèmes.* Suivez les étapes de l’outil ou de cet article pour les résoudre.        |
|Erreur | Le rôle Azure Active Director (AD) que vous utilisez ne peut pas exécuter cette vérification. |

> [!NOTE]
> Les résultats signalés par cet outil reflètent l’état de vos paramètres uniquement au moment où vous l’avez utilisé. Si vous a apporté ultérieurement des modifications aux stratégies dans Microsoft Intune, Azure Active Directory ou Microsoft 365, les éléments qui étaient « prêts » peuvent devenir « Non prêts ». Pour éviter les problèmes liés aux opérations bureau géré Microsoft, vérifiez les paramètres spécifiques décrits dans cet article avant de modifier les stratégies.

## <a name="microsoft-intune-settings"></a>Paramètres Microsoft Intune

Vous pouvez accéder aux paramètres Intune dans le Centre d’administration Microsoft Endpoint [Manager.](https://endpoint.microsoft.com)

### <a name="autopilot-deployment-profile"></a>Profil Autopilot Deployment

Vous ne devez pas avoir de profils Autopilot existants qui ciblent des groupes affectés ou dynamiques avec des appareils Bureau géré Microsoft. Bureau géré Microsoft utilise Autopilot pour mettre en service de nouveaux appareils.

**Non prêt**

Vous avez un profil Autopilot qui est affecté à tous les appareils. Pour obtenir la procédure à suivre, voir Inscrire des [appareils Windows dans Intune à l’aide de Windows Autopilot.](https://docs.microsoft.com/mem/autopilot/enrollment-autopilot) Après l’inscription au Bureau géré Microsoft, définissez votre stratégie Autopilot pour exclure le groupe Modern **Workplace Devices -All** Azure AD.

**Avis**

Assurez-vous que vos profils Autopilot ciblent un groupe Azure AD affecté ou dynamique qui n’inclut pas les appareils bureau géré Microsoft. Pour obtenir la procédure à suivre, voir Inscrire des [appareils Windows dans Intune à l’aide de Windows Autopilot.](https://docs.microsoft.com/mem/autopilot/enrollment-autopilot) Après l’inscription au Bureau géré Microsoft, définissez vos profils Autopilot pour exclure le groupe Modern **Workplace Devices -All** Azure AD.


### <a name="certificate-connectors"></a>Connecteurs de certificat

Si vous avez des connecteurs de certificat qui seront utilisés par les appareils que vous souhaitez inscrire dans Bureau géré Microsoft, les connecteurs ne doivent pas avoir d’erreurs. Une seule des conseils suivants s’applique à votre situation, donc vérifiez-les attentivement.

**Avis**

Aucun connecteur de certificat n’est présent. Il est possible que vous n’avez pas besoin de connecteurs, mais vous devez évaluer si vous en avez besoin pour la connectivité réseau sur vos appareils bureau géré Microsoft. Pour plus d’informations, voir [Préparer les certificats et les profils réseau pour bureau géré Microsoft.](certs-wifi-lan.md)

**Avis**

Au moins un connecteur de certificat présente une erreur. Si vous avez besoin de ce connecteur pour fournir des certificats aux appareils de bureau géré Microsoft, vous devez résoudre l’erreur. Pour plus d’informations, voir [Préparer les certificats et les profils réseau pour bureau géré Microsoft.](certs-wifi-lan.md)


**Avis**

Vous avez au moins un connecteur de certificat et aucune erreur n’est signalée. Toutefois, en vue du déploiement, vous devrez peut-être créer un profil pour réutiliser le connecteur pour les appareils bureau géré Microsoft. Pour plus d’informations, voir [Préparer les certificats et les profils réseau pour bureau géré Microsoft.](certs-wifi-lan.md)


### <a name="conditional-access-policies"></a>Stratégies d’accès conditionnel

Les stratégies d’accès conditionnel dans votre organisation Azure AD ne doivent pas cibler de comptes de service Microsoft Manage Desktop.

**Non prêt**

Vous avez au moins une stratégie d’accès conditionnel qui cible tous les utilisateurs. Modifiez la stratégie pour cibler un groupe Azure AD spécifique qui n’inclut pas le groupe Azure AD de comptes de service Bureau géré Microsoft qui sera créé lors de l’inscription. Pour obtenir la procédure à suivre, [voir Accès conditionnel : utilisateurs et groupes.](https://docs.microsoft.com/azure/active-directory/conditional-access/concept-conditional-access-users-groups)

**Avis**

Assurez-vous que toutes les stratégies d’accès conditionnel que vous avez excluent le groupe Azure AD Comptes de **service** Workplace modernes. Pour obtenir la procédure à suivre, [voir Ajuster l’accès conditionnel.](https://docs.microsoft.com/microsoft-365/managed-desktop/get-started/conditional-access) Le **groupe Azure** AD Comptes de service De l’espace de travail moderne est un groupe dynamique que nous créons pour le service lorsque vous vous inscrivez. Vous devez revenir pour exclure ce groupe après l’inscription. Pour plus d’informations sur ces comptes de service, voir [procédures d’exploitation standard.](../service-description/operations-and-monitoring.md#standard-operating-procedures)

**Error**

Le rôle Administrateur Intune n’a pas les autorisations suffisantes pour cette vérification. Vous aurez également besoin de l’un de ces rôles Azure AD pour exécuter cette vérification :

- Lecteur de sécurité
- Administrateur de sécurité
- Administrateur d’accès conditionnel
- Lecteur général
- Administrateur d’appareils


### <a name="device-compliance-policies"></a>Stratégies de conformité des appareils

Les stratégies de conformité des appareils Intune dans votre organisation Azure AD peuvent avoir un impact sur les appareils de bureau géré Microsoft.

**Non prêt**

Vous avez au moins une stratégie de conformité qui cible tous les utilisateurs. Bureau géré Microsoft inclut des stratégies de conformité qui cibleront vos appareils bureau géré Microsoft.  Modifiez la stratégie pour cibler un groupe Azure AD spécifique qui n’inclut pas d’utilisateurs ou d’appareils de bureau géré Microsoft. Pour obtenir la procédure à [suivre, voir Créer une stratégie de conformité dans Microsoft Intune.](https://docs.microsoft.com/mem/intune/protect/create-compliance-policy)

**Avis**

Assurez-vous que les stratégies de conformité dont vous avez besoin ne ciblent pas les utilisateurs du Bureau géré Microsoft. Pour obtenir la procédure à [suivre, voir Créer une stratégie de conformité dans Microsoft Intune.](https://docs.microsoft.com/mem/intune/protect/create-compliance-policy)



### <a name="device-configuration-profiles"></a>Profils de configuration d’appareil

Les profils de configuration d’appareil Intune dans votre organisation Azure AD ne doivent pas cibler d’utilisateurs ou d’appareils de bureau Microsoft Manage.

**Non prêt**

Vous avez au moins un profil de configuration qui cible tous les utilisateurs, tous les appareils ou les deux. Réinitialisez le profil pour cibler un groupe Azure AD spécifique qui n’inclut aucun appareil de bureau géré Microsoft. Pour connaître la procédure à [suivre, voir Créer un profil avec des paramètres personnalisés dans Microsoft Intune.](https://docs.microsoft.com/mem/intune/configuration/custom-settings-configure)

**Avis**

Assurez-vous que les stratégies de configuration dont vous avez besoin n’incluent pas d’appareils ou d’utilisateurs de bureau géré Microsoft. Pour connaître la procédure à [suivre, voir Créer un profil avec des paramètres personnalisés dans Microsoft Intune.](https://docs.microsoft.com/mem/intune/configuration/custom-settings-configure)



### <a name="device-type-restrictions"></a>Restrictions de type d’appareil

Les appareils de bureau géré Microsoft doivent être autorisés à s’inscrire dans Intune.

**Non prêt**

Vous disposez actuellement d’au moins une stratégie de restriction d’inscription configurée pour empêcher les appareils Windows de s’inscrire dans Intune. Suivez les [étapes](https://docs.microsoft.com/mem/intune/enrollment/enrollment-restrictions-set) de la procédure de définition des restrictions d’inscription pour chaque stratégie de restriction d’inscription qui cible les utilisateurs du Bureau géré Microsoft et modifiez le paramètre **Windows (MDM)** sur **Autoriser**. Toutefois, vous pouvez définir tous **les appareils** **Windows (MDM)** personnels sur **Bloquer**. 


### <a name="enrollment-status-page"></a>Page État de l’inscription

La page Statut de l’inscription (ESP) est actuellement activée. Si vous avez l’intention de participer à la prévisualisation publique bureau géré Microsoft de cette fonctionnalité, vous pouvez ignorer cet élément. Pour plus d’informations, voir l’expérience de première expérience avec [Autopilot et la page État de l’inscription.](../get-started/esp-first-run.md)

**Non prêt**

Vous avez le profil esp par défaut définie sur **Afficher l’avancement de la configuration de l’application et du profil.** Désactivez ce paramètre ou assurez-vous que les affectations à un groupe Azure AD n’incluent pas d’appareils de bureau géré Microsoft en suivant les étapes de la page Configurer l’état [d’inscription.](https://docs.microsoft.com/mem/intune/enrollment/windows-enrollment-status)

**Avis**

Assurez-vous que les profils qui ont le paramètre Afficher l’application et l’avancement de **la configuration** de profil ne sont affectés à aucun groupe Azure AD qui inclut les appareils bureau géré Microsoft. Pour plus d’informations, voir [Configurer la page État de l’inscription.](https://docs.microsoft.com/mem/intune/enrollment/windows-enrollment-status)

### <a name="microsoft-store-for-business"></a>Microsoft Store pour Entreprises

Nous utilisons Microsoft Store pour Entreprises et déployons l’application Portail d’entreprise sur le Bureau géré Microsoft pour permettre aux utilisateurs d’installer éventuellement certaines applications, telles que Microsoft Project et Microsoft Visio (lorsque cela est autorisé).

**Non prêt**

Microsoft Store pour Entreprises n’est pas activé ou n’est pas synchronisé avec Intune. Pour plus d’informations, voir Comment gérer les applications achetées en volume à partir du Microsoft Store pour Entreprises avec [Microsoft Intune](https://docs.microsoft.com/mem/intune/apps/windows-store-for-business) et installer le portail d’entreprise [Intune sur les appareils.](../get-started/company-portal.md)

### <a name="multifactor-authentication"></a>Authentification multifacteur

L’authentification multifacteur ne doit pas être appliquée aux comptes de service Bureau géré Microsoft.


**Non prêt**

Certaines stratégies d’authentification multifacteur sont définies comme **requises** pour les stratégies d’accès conditionnel qui sont attribuées à tous les utilisateurs. Modifiez la stratégie pour utiliser une affectation qui cible un groupe Azure AD spécifique qui n’inclut aucun compte de service Bureau géré Microsoft. Pour plus d’informations, voir [Stratégies d’accès conditionnel](#conditional-access-policies) et [Accès conditionnel : exiger l' approbation de mfa pour tous les utilisateurs.](https://docs.microsoft.com/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa)

**Avis**

Assurez-vous que les stratégies d’accès conditionnel qui nécessitent une authentification multifacteur excluent le groupe Espace de **travail moderne -Tout** Azure AD. Pour plus d’informations, voir [Stratégies d’accès conditionnel](#conditional-access-policies) et [Accès conditionnel : exiger l' approbation de mfa pour tous les utilisateurs.](https://docs.microsoft.com/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa) Le groupe Espace de travail moderne **-** Tout Azure AD est un groupe dynamique que nous créons lorsque vous vous inscrivez au Bureau géré Microsoft. Vous devez donc revenir pour exclure ce groupe après l’inscription.

**Error**

Le rôle Administrateur Intune n’a pas les autorisations suffisantes pour cette vérification. Vous aurez également besoin de l’un de ces rôles Azure AD pour exécuter cette vérification :

- Lecteur de sécurité
- Administrateur de sécurité
- Administrateur d’accès conditionnel
- Lecteur général
- Administrateur d’appareils


### <a name="powershell-scripts"></a>Scripts PowerShell

Windows PowerShell scripts ne peuvent pas être affectés d’une manière qui ciblerait les appareils bureau géré Microsoft.  

**Avis**

Assurez-vous que Windows PowerShell scripts de votre organisation Azure AD ne ciblent aucun utilisateur ou appareil de bureau Microsoft Manage. N’affectez pas de script PowerShell pour cibler tous les utilisateurs, tous les appareils ou les deux. Modifiez la stratégie pour utiliser une affectation qui cible un groupe Azure AD spécifique qui n’inclut pas d’appareils ou d’utilisateurs de bureau géré Microsoft. Pour plus d’informations, [voir Utiliser des scripts PowerShell sur les appareils Windows 10 dans Intune.](https://docs.microsoft.com/mem/intune/apps/intune-management-extension)

### <a name="region"></a>Région

Votre région doit être prise en charge par Bureau géré Microsoft.

**Non prêt**

Votre région d’organisation Azure AD n’est actuellement pas prise en charge par bureau géré Microsoft. Pour plus d’informations, voir les régions et les langues de Bureau géré [Microsoft.](../service-description/regions-languages.md)

**Avis**

Un ou plusieurs des pays où se trouve votre organisation Azure AD ne sont pas pris en charge par Bureau géré Microsoft. Pour plus d’informations, voir les régions et les langues de Bureau géré [Microsoft.](../service-description/regions-languages.md)


### <a name="security-baselines"></a>Bases de référence de sécurité

Les stratégies de base de sécurité ne doivent cibler aucun appareil bureau géré Microsoft.

**Non prêt**

Vous avez un profil de base de sécurité qui cible tous les utilisateurs, tous les appareils ou les deux. Modifiez la stratégie pour utiliser une affectation qui cible un groupe Azure AD spécifique qui n’inclut aucun appareil bureau géré Microsoft. Pour obtenir la procédure à suivre, voir Utiliser les lignes de base de sécurité pour configurer des appareils [Windows 10 dans Intune.](https://docs.microsoft.com/mem/intune/protect/security-baselines)

**Avis**

Assurez-vous que toutes les stratégies de base de sécurité que vous avez excluent les appareils bureau géré Microsoft. Pour obtenir la procédure à suivre, voir Utiliser les lignes de base de sécurité pour configurer des appareils [Windows 10 dans Intune.](https://docs.microsoft.com/mem/intune/protect/security-baselines) Le groupe Modern **Workplace Devices -All** Azure AD est un groupe dynamique que nous créons lorsque vous vous inscrivez au Bureau géré Microsoft. Vous devez donc revenir pour exclure ce groupe après l’inscription.


### <a name="windows-apps"></a>Applications Windows

Examinez les applications que vous souhaitez que vos utilisateurs de bureau géré Microsoft utilisent.

**Avis**

Vous devez préparer un inventaire des applications que vous souhaitez que vos utilisateurs de bureau géré Microsoft utilisent. Étant donné que ces applications doivent être déployées par Intune, évaluez la réutilisation des applications Intune existantes. Envisagez d’utiliser le portail d’entreprise (voir Installer le portail d’entreprise [Intune](https://docs.microsoft.com/microsoft-365/managed-desktop/get-started/company-portal) sur les appareils et la page État de l’inscription (ESP) pour distribuer des applications à vos utilisateurs. Pour plus d’informations, voir [Applications dans Bureau](apps.md) géré Microsoft et Expérience de première utilisation avec Autopilot et la page État de [l’inscription.](https://docs.microsoft.com/microsoft-365/managed-desktop/get-started/esp-first-run)

Vous pouvez demander à votre représentant de compte Microsoft une requête dans Microsoft Endpoint Configuration Manager pour identifier les applications qui sont prêtes à migrer vers Intune ou qui ont besoin d’ajustement.


### <a name="windows-hello-for-business"></a>Windows Hello Entreprise

Bureau géré Microsoft requiert l’activé de Windows Hello Entreprise.

**Non prêt**

Windows Hello Entreprise est désactivé. Activez-la en suivant les étapes de [création d’une stratégie Windows Hello Entreprise](https://docs.microsoft.com/mem/intune/protect/windows-hello#create-a-windows-hello-for-business-policy)

**Avis**

Windows Hello Entreprise n’est pas installé. Activez-la en suivant les étapes [de création d’une stratégie Windows Hello Entreprise.](https://docs.microsoft.com/mem/intune/protect/windows-hello#create-a-windows-hello-for-business-policy)


### <a name="windows-10-update-rings"></a>Anneaux de mise à jour Windows 10

Votre stratégie « Anneau de mise à jour Windows 10 » dans Intune ne doit cibler aucun appareil bureau géré Microsoft.

**Non prêt**

Vous avez une stratégie de « sonnerie de mise à jour » qui cible tous les appareils, tous les utilisateurs ou les deux. Modifiez la stratégie pour utiliser une affectation qui cible un groupe Azure AD spécifique qui n’inclut aucun appareil bureau géré Microsoft. Pour obtenir la procédure à suivre, voir Gérer les mises à jour [logicielles Windows 10 dans Intune.](https://docs.microsoft.com/mem/intune/protect/windows-update-for-business-configure)

**Avis**

Assurez-vous que toutes les stratégies de sonnerie de mise à jour que vous avez excluent le **groupe Modern Workplace Devices -All** Azure AD. Si vous avez affecté des groupes d’utilisateurs Azure AD à ces stratégies, assurez-vous que les stratégies de sonnerie de mise à jour que vous avez également exclues du groupe Espace de travail moderne **-Tous** les groupes Azure AD à qui vous ajoutez vos utilisateurs de bureau géré Microsoft (ou un groupe équivalent). Pour obtenir la procédure à suivre, voir Gérer les mises à jour [logicielles Windows 10 dans Intune.](https://docs.microsoft.com/mem/intune/protect/windows-update-for-business-configure) Les appareils d’espace de travail modernes **-All** et **Modern Workplace -All** Azure AD groups are groups that we create when you enroll in Microsoft Managed Desktop, so you’ll have to come back to exclude this group after enrollment.


## <a name="azure-active-directory-settings"></a>Paramètres Azure Active Directory

Vous pouvez accéder aux paramètres Azure Active Directory sur le [portail Azure.](https://portal.azure.com)

### <a name="intune-enrollment"></a>Inscription à Intune

Les appareils Windows 10 de votre organisation Azure AD doivent pouvoir s’inscrire automatiquement dans Intune.

**Avis**

Assurez-vous que **l’étendue utilisateur de la** gestion des données est définie sur **Tout** ou **partie,** et non **sur Aucune.** Si vous **en** choisissez un, revenir après l’inscription et  sélectionner le groupe Espace de travail moderne **-Tout** Azure AD pour les groupes ou un groupe équivalent ciblant tous vos utilisateurs de bureau géré Microsoft.  Voir [Configurer l’inscription pour les appareils Windows à l’aide de Microsoft Intune.](https://docs.microsoft.com/mem/intune/enrollment/windows-enroll#enable-windows-10-automatic-enrollment)


### <a name="ad-hoc-subscriptions"></a>Abonnements ad hoc

Indique comment vérifier un paramètre qui (s’il a la valeur « false ») risque d’empêcher Enterprise State Roaming de fonctionner correctement.

**Avis**

**Assurez-vous que AllowAdHocSubscriptions** est définie sur **True**. Dans le cas contraire, enterprise State Roaming risque de ne pas fonctionner. Pour plus d’informations, [voir Set-MsolCompanySettings.](https://docs.microsoft.com/powershell/module/msonline/set-msolcompanysettings?view=azureadps-1.0)


### <a name="enterprise-state-roaming"></a>Itinérance du statut Entreprise

L’itinérance de l’état d’entreprise doit être activée.

**Avis**

Assurez-vous que l’itinérance de l’état d’entreprise est activée pour **Tous** ou pour **les groupes sélectionnés.** Pour plus d’informations, voir [Activer l’itinérance de l’état d’entreprise dans Azure Active Directory.](https://docs.microsoft.com/azure/active-directory/devices/enterprise-state-roaming-enable)

### <a name="licenses"></a>Licences

Un certain nombre de licences sont requises pour utiliser bureau géré Microsoft.

**Non prêt**

Vous n’avez pas toutes les licences dont vous avez besoin pour utiliser Bureau géré Microsoft. Pour plus d’informations, voir [Les technologies bureau](../intro/technologies.md) géré Microsoft et plus [d’informations sur les licences.](prerequisites.md#more-about-licenses)


### <a name="security-account-names"></a>Noms de compte de sécurité

Certains noms de compte de sécurité peuvent être en conflit avec ceux créés par Bureau géré Microsoft.

**Non prêt**

Vous avez au moins un nom de compte qui entrera en conflit avec ceux créés par Bureau géré Microsoft. Travaillez avec votre représentant de compte Microsoft pour exclure ces noms de comptes.


### <a name="security-administrator-roles"></a>Rôles d’administrateur de sécurité

Les utilisateurs ayant certains rôles de sécurité doivent avoir ces rôles attribués dans Microsoft Defender pour point de terminaison.

**Avis**

Si vous avez des utilisateurs affectés à l’un de ces rôles dans votre organisation Azure AD, assurez-vous qu’ils ont également ces rôles attribués dans Microsoft Defender for Endpoint. Dans le cas contraire, les administrateurs ayant ces rôles ne pourront pas accéder au portail d’administration.

- Opérateur de sécurité
- Lecteur général

Pour plus d’informations, voir [Créer et gérer des rôles pour le contrôle d’accès basé sur les rôles.](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/user-roles)


### <a name="security-default"></a>Sécurité par défaut

Les paramètres de sécurité par défaut dans Azure Active Directory empêcheront Le Bureau géré Microsoft de gérer vos appareils.

**Non prêt**

Les paramètres de sécurité par défaut sont désactivés. Désactiver les paramètres de sécurité par défaut et configurer des stratégies d’accès conditionnel. Pour plus d’informations, voir [Stratégies d’accès conditionnel courantes.](https://docs.microsoft.com/azure/active-directory/conditional-access/concept-conditional-access-policy-common)

### <a name="self-service-password-reset"></a>Réinitialisation du mot de passe en libre-service

La réinitialisation du mot de passe en libre-service (SSPR) peut être activée pour tous les utilisateurs de bureau géré Microsoft, à l’exception des comptes de service Bureau géré Microsoft. Pour plus d’informations, voir didacticiel : permettre aux utilisateurs de déverrouiller leur compte ou de réinitialiser leurs mots de passe à l’aide de la réinitialisation du mot de passe [libre-service Azure Active Directory.](https://docs.microsoft.com/azure/active-directory/authentication/tutorial-enable-sspr)

**Avis**

Assurez-vous que le  paramètre SSPR sélectionné inclut les utilisateurs de bureau géré Microsoft, mais exclut les comptes de service Bureau géré Microsoft. Les comptes de service Bureau géré Microsoft ne peuvent pas fonctionner comme prévu lorsque SSPR est activé.  


### <a name="standard-user-role"></a>Rôle d’utilisateur standard

À part les utilisateurs qui se voit attribuer des rôles Azure AD d’administrateur général et d’administrateur d’appareil, les utilisateurs du Bureau géré Microsoft sont des utilisateurs standard sans privilèges d’administrateur local. Un rôle d’utilisateur standard est attribué à tous les autres utilisateurs lorsqu’ils démarrent leur appareil Bureau géré Microsoft.

**Avis**

Une fois inscrits, les utilisateurs du Bureau géré Microsoft ne pourront pas avoir de privilèges d’administrateur local sur leurs appareils de bureau géré Microsoft.

## <a name="microsoft-365-apps-for-enterprise"></a>Applications Microsoft 365 for entreprise

### <a name="onedrive"></a>OneDrive

Le **paramètre Autoriser la synchronisation uniquement sur les PC joints à** des domaines spécifiques entre en conflit avec bureau géré Microsoft. Vous pouvez accéder aux paramètres OneDrive dans le Centre [d’administration OneDrive.](https://admin.onedrive.com)

**Avis**

Vous utilisez le paramètre Autoriser la synchronisation uniquement sur les **PC joints à des domaines spécifiques.** Ce paramètre ne fonctionne pas avec bureau géré Microsoft. Désactivez ce paramètre, puis définissez OneDrive pour utiliser une stratégie d’accès conditionnel. Voir [Planifier un déploiement d’accès conditionnel pour](https://docs.microsoft.com/azure/active-directory/conditional-access/plan-conditional-access) obtenir de l’aide.

