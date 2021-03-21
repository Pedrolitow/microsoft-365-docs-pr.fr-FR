---
title: Résoudre les problèmes détectés par l’outil de préparation et d’évaluation
description: Actions détaillées à prendre pour chaque problème trouvé par l’outil
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: 75c2967037ae83abca2aaa3cd02d1f6b2ae14caa
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50925915"
---
# <a name="fix-issues-found-by-the-readiness-assessment-tool"></a>Résoudre les problèmes détectés par l’outil de préparation et d’évaluation

Pour chaque vérification, l’outil signalera l’un des quatre résultats possibles :


|Résultat  |Signification  |
|---------|---------|
|Prêt     | Aucune action n’est requise avant de terminer l’inscription.        |
|Avertissement    | Suivez les étapes de l’outil ou de cet article pour une expérience de l’inscription et pour les utilisateurs. Vous *pouvez terminer* l’inscription, mais vous devez résoudre ces problèmes avant de déployer votre premier appareil.        |
|Non prêt | *L’inscription échoue si vous ne corrigez pas ces problèmes.* Suivez les étapes de l’outil ou de cet article pour les résoudre.        |
|Erreur | Le rôle Azure Active Directory (AD) que vous utilisez ne peut pas exécuter cette vérification. |

> [!NOTE]
> Les résultats signalés par cet outil reflètent l’état de vos paramètres uniquement au moment où vous l’avez utilisé. Si vous a apporté ultérieurement des modifications aux stratégies dans Microsoft Intune, Azure Active Directory ou Microsoft 365, les éléments qui étaient « prêts » peuvent devenir « Non prêts ». Pour éviter les problèmes liés aux opérations bureau géré Microsoft, vérifiez les paramètres spécifiques décrits dans cet article avant de modifier les stratégies.

## <a name="microsoft-intune-settings"></a>Paramètres Microsoft Intune

Vous pouvez accéder aux paramètres Intune dans le Centre d’administration Microsoft Endpoint [Manager.](https://endpoint.microsoft.com)

### <a name="autopilot-deployment-profile"></a>Profil Autopilot Deployment

Vous ne devez pas avoir de profils Autopilot existants qui ciblent des groupes affectés ou dynamiques avec des appareils Bureau géré Microsoft. Bureau géré Microsoft utilise Autopilot pour mettre en service de nouveaux appareils.

**Non prêt**

Vous avez un profil Autopilot qui est affecté à tous les appareils. Pour obtenir la procédure à suivre, voir [Inscrire des appareils Windows dans Intune à l’aide de Windows Autopilot.](/mem/autopilot/enrollment-autopilot) Après l’inscription au Bureau géré Microsoft, définissez votre stratégie Autopilot pour exclure le groupe Modern **Workplace Devices -All** Azure AD.

**Avertissement**

Assurez-vous que vos profils Autopilot ciblent un groupe Azure AD affecté ou dynamique qui n’inclut pas les appareils bureau géré Microsoft. Pour obtenir la procédure à suivre, voir [Inscrire des appareils Windows dans Intune à l’aide de Windows Autopilot.](/mem/autopilot/enrollment-autopilot) Après l’inscription au Bureau géré Microsoft, définissez vos profils Autopilot pour exclure le groupe Modern **Workplace Devices -All** Azure AD.


### <a name="certificate-connectors"></a>Connecteurs de certificat

Si vous avez des connecteurs de certificat qui seront utilisés par les appareils que vous souhaitez inscrire dans Bureau géré Microsoft, les connecteurs ne doivent pas avoir d’erreurs. Une seule des conseils suivants s’applique à votre situation, donc vérifiez-les attentivement.

**Avertissement**

Aucun connecteur de certificat n’est présent. Il est possible que vous n’avez pas besoin de connecteurs, mais vous devez évaluer si vous en avez besoin pour la connectivité réseau sur vos appareils bureau géré Microsoft. Pour plus d’informations, voir [Préparer les certificats et les profils réseau pour le Bureau géré Microsoft.](certs-wifi-lan.md)

**Avertissement**

Au moins un connecteur de certificat présente une erreur. Si vous avez besoin de ce connecteur pour fournir des certificats aux appareils de bureau géré Microsoft, vous devez résoudre l’erreur. Pour plus d’informations, voir [Préparer les certificats et les profils réseau pour le Bureau géré Microsoft.](certs-wifi-lan.md)


**Avertissement**

Vous avez au moins un connecteur de certificat et aucune erreur n’est signalée. Toutefois, en vue du déploiement, vous devrez peut-être créer un profil pour réutiliser le connecteur pour les appareils bureau géré Microsoft. Pour plus d’informations, voir [Préparer les certificats et les profils réseau pour le Bureau géré Microsoft.](certs-wifi-lan.md)


### <a name="conditional-access-policies"></a>Stratégies d’accès conditionnel

Les stratégies d’accès conditionnel ne doivent pas empêcher le Bureau géré Microsoft de gérer votre organisation Azure AD (client) dans Intune et Azure AD.

**Non prêt**

Vous avez au moins une stratégie d’accès conditionnel qui cible tous les utilisateurs. Lors de l’inscription, nous allons exclure les comptes du service Bureau géré Microsoft des stratégies d’accès conditionnel pertinentes et appliquer de nouvelles stratégies d’accès conditionnel pour restreindre l’accès à ces comptes. Après l’inscription, vous pouvez consulter la stratégie d’accès conditionnel bureau géré Microsoft dans Microsoft Endpoint Manager. Pour plus d’informations sur ces comptes de service, voir [procédures d’exploitation standard.](../service-description/operations-and-monitoring.md#standard-operating-procedures)

**Avertissement**

Vous avez des stratégies d’accès conditionnel qui pourraient empêcher Bureau géré Microsoft de gérer le service Bureau géré Microsoft. Lors de l’inscription, nous allons exclure les comptes du service Bureau géré Microsoft des stratégies d’accès conditionnel pertinentes et appliquer de nouvelles stratégies d’accès conditionnel pour restreindre l’accès à ces comptes. Pour plus d’informations sur ces comptes de service, voir [procédures d’exploitation standard.](../service-description/operations-and-monitoring.md#standard-operating-procedures)

**Error**

Le rôle d’administrateur Intune n’a pas les autorisations suffisantes pour cette vérification. Vous aurez également besoin de l’un de ces rôles Azure AD pour exécuter cette vérification :

- Lecteur de sécurité
- Administrateur de sécurité
- Administrateur d’accès conditionnel
- Lecteur général
- Administrateur d’appareils


### <a name="device-compliance-policies"></a>Stratégies de conformité des appareils

Les stratégies de conformité des appareils Intune dans votre organisation Azure AD peuvent avoir un impact sur les appareils de bureau géré Microsoft.

**Non prêt**

Vous avez au moins une stratégie de conformité qui cible tous les utilisateurs. Bureau géré Microsoft inclut des stratégies de conformité qui cibleront vos appareils bureau géré Microsoft.  Modifiez la stratégie pour cibler un groupe Azure AD spécifique qui n’inclut pas d’utilisateurs ou d’appareils de bureau géré Microsoft. Pour obtenir la procédure à [suivre, voir Créer une stratégie de conformité dans Microsoft Intune.](/mem/intune/protect/create-compliance-policy)

**Avertissement**

Assurez-vous que les stratégies de conformité dont vous avez besoin ne ciblent pas les utilisateurs du Bureau géré Microsoft. Pour obtenir la procédure à [suivre, voir Créer une stratégie de conformité dans Microsoft Intune.](/mem/intune/protect/create-compliance-policy)



### <a name="device-configuration-profiles"></a>Profils de configuration d’appareil

Les profils de configuration d’appareil Intune dans votre organisation Azure AD ne doivent pas cibler d’utilisateurs ou d’appareils de bureau Microsoft Manage.

**Non prêt**

Vous avez au moins un profil de configuration qui cible tous les utilisateurs, tous les appareils ou les deux. Réinitialisez le profil pour cibler un groupe Azure AD spécifique qui n’inclut aucun appareil de bureau géré Microsoft. Pour connaître la procédure à [suivre, voir Créer un profil avec des paramètres personnalisés dans Microsoft Intune.](/mem/intune/configuration/custom-settings-configure)

**Avertissement**

Assurez-vous que les stratégies de configuration dont vous avez besoin n’incluent pas d’appareils ou d’utilisateurs de bureau géré Microsoft. Pour connaître la procédure à [suivre, voir Créer un profil avec des paramètres personnalisés dans Microsoft Intune.](/mem/intune/configuration/custom-settings-configure)



### <a name="device-type-restrictions"></a>Restrictions de type d’appareil

Les appareils de bureau géré Microsoft doivent être autorisés à s’inscrire dans Intune.

**Non prêt**

Vous disposez actuellement d’au moins une stratégie de restriction d’inscription configurée pour empêcher les appareils Windows de s’inscrire dans Intune. Suivez les [étapes](/mem/intune/enrollment/enrollment-restrictions-set) de la procédure de définition des restrictions d’inscription pour chaque stratégie de restriction d’inscription qui cible les utilisateurs du Bureau géré Microsoft et modifiez le paramètre **Windows (MDM)** sur **Autoriser**. Toutefois, vous pouvez définir tous **les appareils** **Windows (MDM)** personnels sur **Bloquer**. 


### <a name="enrollment-status-page"></a>Page État de l’inscription

La page d’état d’inscription (ESP) est actuellement activée. Si vous avez l’intention de participer à la prévisualisation publique bureau géré Microsoft de cette fonctionnalité, vous pouvez ignorer cet élément. Pour plus d’informations, voir l’expérience de première expérience avec [Autopilot et la page État de l’inscription.](../get-started/esp-first-run.md)

**Non prêt**

Vous avez le profil esp par défaut définie sur **Afficher l’avancement de la configuration de l’application et du profil.** Désactivez ce paramètre ou assurez-vous que les affectations à un groupe Azure AD n’incluent pas d’appareils de bureau géré Microsoft en suivant les étapes de la page Configurer l’état [d’inscription.](/mem/intune/enrollment/windows-enrollment-status)

**Avertissement**

Assurez-vous que les profils qui ont le paramètre Afficher l’application et l’avancement de **la configuration** de profil ne sont affectés à aucun groupe Azure AD qui inclut les appareils bureau géré Microsoft. Pour plus d’informations, voir [Configurer la page État de l’inscription.](/mem/intune/enrollment/windows-enrollment-status)

### <a name="microsoft-store-for-business"></a>Microsoft Store pour Entreprises

Nous utilisons Microsoft Store pour Entreprises et déployons l’application Portail d’entreprise sur le Bureau géré Microsoft pour permettre aux utilisateurs d’installer éventuellement certaines applications, telles que Microsoft Project et Microsoft Visio (lorsque cela est autorisé).

**Non prêt**

Microsoft Store pour Entreprises n’est pas activé ou n’est pas synchronisé avec Intune. Pour plus d’informations, voir Comment gérer les applications achetées en volume à partir du Microsoft Store pour Entreprises avec [Microsoft Intune](/mem/intune/apps/windows-store-for-business) et installer le portail d’entreprise [Intune sur les appareils.](../get-started/company-portal.md)

### <a name="multifactor-authentication"></a>Authentification multifacteur

L’authentification multifacteur ne doit pas empêcher Le Bureau géré Microsoft de gérer votre organisation Azure AD (client) dans Intune et Azure AD.


**Non prêt**

Certaines stratégies d’authentification  multifacteur sont définies comme requises pour les stratégies d’accès conditionnel qui sont affectées à tous les utilisateurs. Lors de l’inscription, nous allons exclure les comptes du service Bureau géré Microsoft des stratégies d’accès conditionnel pertinentes et appliquer de nouvelles stratégies d’accès conditionnel pour restreindre l’accès à ces comptes. Pour plus d’informations sur ces comptes de service, voir [procédures d’exploitation standard.](../service-description/operations-and-monitoring.md#standard-operating-procedures)

**Avertissement**

Vous avez besoin d’une authentification multifacteur sur les stratégies d’accès conditionnel qui pourraient empêcher Microsoft Managed Desktop de gérer le service Bureau géré Microsoft. Lors de l’inscription, nous allons exclure les comptes du service Bureau géré Microsoft des stratégies d’accès conditionnel pertinentes et appliquer de nouvelles stratégies d’accès conditionnel pour restreindre l’accès à ces comptes. Pour plus d’informations sur ces comptes de service, voir [procédures d’exploitation standard.](../service-description/operations-and-monitoring.md#standard-operating-procedures)

**Error**

Le rôle d’administrateur Intune n’a pas les autorisations suffisantes pour cette vérification. Vous aurez également besoin de l’un de ces rôles Azure AD pour exécuter cette vérification :

- Lecteur de sécurité
- Administrateur de sécurité
- Administrateur d’accès conditionnel
- Lecteur général
- Administrateur d’appareils


### <a name="powershell-scripts"></a>Scripts PowerShell

Windows PowerShell scripts ne peuvent pas être affectés d’une manière qui ciblerait les appareils bureau géré Microsoft.  

**Avertissement**

Assurez-vous que Windows PowerShell scripts de votre organisation Azure AD ne ciblent aucun utilisateur ou appareil de bureau Microsoft Manage. N’affectez pas de script PowerShell pour cibler tous les utilisateurs, tous les appareils ou les deux. Modifiez la stratégie pour utiliser une affectation qui cible un groupe Azure AD spécifique qui n’inclut pas d’appareils ou d’utilisateurs de bureau géré Microsoft. Pour plus d’informations, [voir Utiliser des scripts PowerShell sur les appareils Windows 10 dans Intune.](/mem/intune/apps/intune-management-extension)

### <a name="region"></a>Région

Votre région doit être prise en charge par Bureau géré Microsoft.

**Non prêt**

Votre région d’organisation Azure AD n’est actuellement pas prise en charge par bureau géré Microsoft. Pour plus d’informations, voir les régions et les langues de Bureau géré [Microsoft.](../service-description/regions-languages.md)

**Avertissement**

Un ou plusieurs des pays où se trouve votre organisation Azure AD ne sont pas pris en charge par Bureau géré Microsoft. Pour plus d’informations, voir les régions et les langues de Bureau géré [Microsoft.](../service-description/regions-languages.md)


### <a name="security-baselines"></a>Bases de référence de sécurité

Les stratégies de base de sécurité ne doivent cibler aucun appareil bureau géré Microsoft.

**Non prêt**

Vous avez un profil de base de sécurité qui cible tous les utilisateurs, tous les appareils ou les deux. Modifiez la stratégie pour utiliser une affectation qui cible un groupe Azure AD spécifique qui n’inclut aucun appareil bureau géré Microsoft. Pour obtenir la procédure à suivre, voir Utiliser les lignes de base de sécurité pour configurer des appareils [Windows 10 dans Intune.](/mem/intune/protect/security-baselines) Lors de l’inscription, nous appliquons une nouvelle ligne de base de sécurité à tous les appareils bureau géré Microsoft. Après l’inscription, vous pouvez consulter la stratégie de base de sécurité du Bureau géré Microsoft dans la zone de stratégie de **configuration** de Microsoft Endpoint Manager.

**Avertissement**

Assurez-vous que toutes les stratégies de base de sécurité que vous avez excluent les appareils bureau géré Microsoft. Pour obtenir la procédure à suivre, voir Utiliser les lignes de base de sécurité pour configurer des appareils [Windows 10 dans Intune.](/mem/intune/protect/security-baselines) Lors de l’inscription, nous appliquons une nouvelle ligne de base de sécurité à tous les appareils bureau géré Microsoft. Le groupe Modern **Workplace Devices -All** Azure AD est un groupe dynamique que nous créons lorsque vous vous inscrivez au Bureau géré Microsoft. Vous devez donc revenir pour exclure ce groupe après l’inscription. 


### <a name="windows-apps"></a>Applications Windows

Examinez les applications que vous souhaitez que vos utilisateurs de bureau géré Microsoft utilisent.

**Avertissement**

Vous devez préparer un inventaire des applications que vous souhaitez que vos utilisateurs de bureau géré Microsoft utilisent. Étant donné que ces applications doivent être déployées par Intune, évaluez la réutilisation des applications Intune existantes. Envisagez d’utiliser le portail d’entreprise (voir Installer le portail d’entreprise [Intune](../get-started/company-portal.md) sur les appareils et la page État de l’inscription (ESP) pour distribuer des applications à vos utilisateurs. Pour plus d’informations, voir [Applications dans Bureau](apps.md) géré Microsoft et Expérience de première utilisation avec Autopilot et la page État de [l’inscription.](../get-started/esp-first-run.md)

Vous pouvez demander à votre représentant de compte Microsoft une requête dans Microsoft Endpoint Configuration Manager pour identifier les applications qui sont prêtes à migrer vers Intune ou qui ont besoin d’ajustement.


### <a name="windows-hello-for-business"></a>Windows Hello Entreprise

Bureau géré Microsoft requiert l’activé de Windows Hello Entreprise.

**Non prêt**

Windows Hello Entreprise est désactivé. Activez-la en suivant les étapes de [création d’une stratégie Windows Hello Entreprise](/mem/intune/protect/windows-hello#create-a-windows-hello-for-business-policy)

**Avertissement**

Windows Hello Entreprise n’est pas installé. Activez-la en suivant les étapes [de création d’une stratégie Windows Hello Entreprise.](/mem/intune/protect/windows-hello#create-a-windows-hello-for-business-policy)


### <a name="windows-10-update-rings"></a>Anneaux de mise à jour Windows 10

Votre stratégie « Anneau de mise à jour Windows 10 » dans Intune ne doit cibler aucun appareil bureau géré Microsoft.

**Non prêt**

Vous avez une stratégie de « sonnerie de mise à jour » qui cible tous les appareils, tous les utilisateurs ou les deux. Modifiez la stratégie pour utiliser une affectation qui cible un groupe Azure AD spécifique qui n’inclut aucun appareil bureau géré Microsoft. Pour obtenir la procédure à suivre, voir Gérer les mises à jour [logicielles Windows 10 dans Intune.](/mem/intune/protect/windows-update-for-business-configure)

**Avertissement**

Assurez-vous que les stratégies de sonnerie de mise à jour que vous avez excluent le **groupe Modern Workplace Devices -All** Azure AD. Si vous avez affecté des groupes d’utilisateurs Azure AD à ces stratégies, assurez-vous que toutes les stratégies de sonnerie de mise à jour que vous avez également exclues du groupe Espace de travail moderne **-Tout** Azure AD à qui vous ajoutez vos utilisateurs de bureau géré Microsoft (ou un groupe équivalent). Pour obtenir la procédure à suivre, voir Gérer les mises à jour [logicielles Windows 10 dans Intune.](/mem/intune/protect/windows-update-for-business-configure) Les appareils d’espace de travail modernes **-All** et **Modern Workplace -All** Azure AD groups are groups that we create when you enroll in Microsoft Managed Desktop, so you’ll have to come back to exclude this group after enrollment.


## <a name="azure-active-directory-settings"></a>Paramètres Azure Active Directory

Vous pouvez accéder aux paramètres Azure Active Directory sur le [portail Azure.](https://portal.azure.com)

### <a name="intune-enrollment"></a>Inscription à Intune

Les appareils Windows 10 de votre organisation Azure AD doivent pouvoir s’inscrire automatiquement dans Intune.

**Avertissement**

Assurez-vous que **l’étendue utilisateur de la** gestion des données est définie sur **Tout** ou **partie,** et non **sur Aucune.** Si vous **en** choisissez un, revenir après l’inscription et  sélectionner le groupe Espace de travail moderne **-Tout** Azure AD pour les groupes ou un groupe équivalent ciblant tous vos utilisateurs de bureau géré Microsoft.  Voir [Configurer l’inscription pour les appareils Windows à l’aide de Microsoft Intune.](/mem/intune/enrollment/windows-enroll#enable-windows-10-automatic-enrollment)


### <a name="ad-hoc-subscriptions"></a>Abonnements ad hoc

Indique comment vérifier un paramètre qui (s’il a la valeur « false ») risque d’empêcher Enterprise State Roaming de fonctionner correctement.

**Avertissement**

**Assurez-vous que AllowAdHocSubscriptions** est définie sur **True**. Sinon, Enterprise State Roaming risque de ne pas fonctionner. Pour plus d’informations, [voir Set-MsolCompanySettings](/powershell/module/msonline/set-msolcompanysettings?view=azureadps-1.0).


### <a name="enterprise-state-roaming"></a>Itinérance du statut Entreprise

L’itinérance de l’état d’entreprise doit être activée.

**Avertissement**

Assurez-vous que l’itinérance de l’état d’entreprise est activée pour **Tous** ou pour **les groupes sélectionnés.** Pour plus d’informations, voir [Activer l’itinérance de l’état d’entreprise dans Azure Active Directory.](/azure/active-directory/devices/enterprise-state-roaming-enable)

### <a name="licenses"></a>Licences

Un certain nombre de licences sont requises pour utiliser bureau géré Microsoft.

**Non prêt**

Vous n’avez pas toutes les licences dont vous avez besoin pour utiliser Bureau géré Microsoft. Pour plus d’informations, voir [Les technologies bureau géré Microsoft](../intro/technologies.md) et en savoir plus sur les [licences.](prerequisites.md#more-about-licenses)


### <a name="microsoft-managed-desktop-service-accounts"></a>Comptes de service Bureau géré Microsoft

Certains noms de compte peuvent être en conflit avec les noms de compte créés par Le Bureau géré Microsoft pour gérer le service Bureau géré Microsoft.

**Non prêt**

Vous avez au moins un nom de compte qui entrera en conflit avec les noms de compte créés par Bureau géré Microsoft. Travaillez avec votre représentant de compte Microsoft pour exclure ces noms de comptes. Nous ne listons pas les noms de comptes publiquement pour minimiser les risques de sécurité. 


### <a name="security-administrator-roles"></a>Rôles d’administrateur de sécurité

Les utilisateurs ayant certains rôles de sécurité doivent avoir ces rôles attribués dans Microsoft Defender pour point de terminaison.

**Avertissement**

Si vous avez des utilisateurs affectés à l’un de ces rôles dans votre organisation Azure AD, assurez-vous qu’ils ont également ces rôles attribués dans Microsoft Defender for Endpoint. Dans le cas contraire, les administrateurs ayant ces rôles ne pourront pas accéder au portail d’administration.

- Opérateur de sécurité
- Lecteur général

Pour plus d’informations, voir Créer et gérer des rôles pour le contrôle [d’accès basé sur les rôles.](/windows/security/threat-protection/microsoft-defender-atp/user-roles)


### <a name="security-default"></a>Sécurité par défaut

Les paramètres de sécurité par défaut dans Azure Active Directory empêcheront bureau géré Microsoft de gérer vos appareils.

**Non prêt**

Les paramètres de sécurité par défaut sont désactivés. Désactiver les paramètres de sécurité par défaut et configurer des stratégies d’accès conditionnel. Pour plus d’informations, voir [Stratégies d’accès conditionnel courantes.](/azure/active-directory/conditional-access/concept-conditional-access-policy-common)

### <a name="self-service-password-reset"></a>Réinitialisation du mot de passe en libre-service

La réinitialisation du mot de passe en libre-service (SSPR) peut être activée pour tous les utilisateurs de bureau géré Microsoft, à l’exception des comptes de service Bureau géré Microsoft. Pour plus d’informations, voir didacticiel : permettre aux utilisateurs de déverrouiller leur compte ou de réinitialiser leurs mots de passe à l’aide de la réinitialisation du mot de passe [libre-service Azure Active Directory.](/azure/active-directory/authentication/tutorial-enable-sspr)

**Avertissement**

Assurez-vous que le  paramètre SSPR sélectionné inclut les utilisateurs de bureau géré Microsoft, mais exclut les comptes de service Bureau géré Microsoft. Les comptes de service Bureau géré Microsoft ne peuvent pas fonctionner comme prévu lorsque SSPR est activé.  


### <a name="standard-user-role"></a>Rôle d’utilisateur standard

À part les utilisateurs qui se voit attribuer des rôles Azure AD d’administrateur général et d’administrateur d’appareil, les utilisateurs du Bureau géré Microsoft sont des utilisateurs standard sans privilèges d’administrateur local. Un rôle d’utilisateur standard est attribué à tous les autres utilisateurs lorsqu’ils démarrent leur appareil Bureau géré Microsoft.

**Avertissement**

Les utilisateurs du Bureau géré Microsoft ne pourront pas avoir de privilèges d’administrateur local sur leurs appareils de bureau géré Microsoft après s’être inscrits.

## <a name="microsoft-365-apps-for-enterprise"></a>Applications Microsoft 365 pour les grandes entreprises

### <a name="onedrive"></a>OneDrive

Le **paramètre Autoriser la synchronisation uniquement sur les PC joints à** des domaines spécifiques entre en conflit avec bureau géré Microsoft. Vous pouvez accéder aux paramètres OneDrive dans le Centre [d’administration OneDrive.](https://admin.onedrive.com)

**Avertissement**

Vous utilisez le paramètre Autoriser la synchronisation uniquement sur les **PC joints à des domaines spécifiques.** Ce paramètre ne fonctionne pas avec bureau géré Microsoft. Désactivez ce paramètre, puis définissez OneDrive pour utiliser une stratégie d’accès conditionnel. Pour obtenir [de l’aide, voir](/azure/active-directory/conditional-access/plan-conditional-access) Planifier un déploiement d’accès conditionnel.