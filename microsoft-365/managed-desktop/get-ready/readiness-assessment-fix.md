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
audience: Admin
ms.openlocfilehash: 5a22996ce9e39dc16191ddddc6aa9393de557bbc
ms.sourcegitcommit: 53acc851abf68e2272e75df0856c0e16b0c7e48d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2021
ms.locfileid: "51579409"
---
# <a name="fix-issues-found-by-the-readiness-assessment-tool"></a>Résoudre les problèmes détectés par l’outil de préparation et d’évaluation

Pour chaque vérification, l’outil signalera l’un des quatre résultats possibles :


|Résultat  |Signification  |
|---------|---------|
|Prêt     | Aucune action n’est requise avant de terminer l’inscription.        |
|Avertissement    | Suivez les étapes de l’outil ou de cet article pour une expérience de l’inscription et pour les utilisateurs. Vous *pouvez terminer* l’inscription, mais vous devez résoudre ces problèmes avant de déployer votre premier appareil.        |
|Non prêt | *L’inscription échoue si vous ne corrigez pas ces problèmes.* Suivez les étapes de l’outil ou de cet article pour les résoudre.        |
|Erreur | Le Azure Active Directory (AD) que vous utilisez ne donne pas l’autorisation suffisante pour exécuter cette vérification. |

> [!NOTE]
> Les résultats signalés par cet outil reflètent l’état de vos paramètres uniquement au moment où vous l’avez utilisé. Si vous a apporté ultérieurement des modifications aux stratégies dans Microsoft Intune, Azure Active Directory ou Microsoft 365, les éléments qui étaient « prêts » peuvent devenir « Non prêts ». Pour éviter les problèmes liés aux Bureau géré Microsoft d’entreprise, vérifiez les paramètres spécifiques décrits dans cet article avant de modifier les stratégies.

## <a name="microsoft-intune-settings"></a>Microsoft Intune paramètres

Vous pouvez accéder aux paramètres Intune à l’Microsoft Endpoint Manager [d’administration.](https://endpoint.microsoft.com)

### <a name="autopilot-deployment-profile"></a>Profil Autopilot Deployment

Vous ne devez pas avoir de profils Autopilot existants qui ciblent des groupes affectés ou dynamiques Bureau géré Microsoft appareils. Bureau géré Microsoft utilise Autopilot pour mettre en service de nouveaux appareils.

**Non prêt**

Vous avez un profil Autopilot qui est affecté à tous les appareils. Pour obtenir la procédure à suivre, voir Inscrire Windows appareils dans Intune à l’aide [Windows Autopilot](/mem/autopilot/enrollment-autopilot). Après Bureau géré Microsoft inscription, définissez votre stratégie Autopilot pour exclure le groupe Modern **Workplace Devices -All** Azure AD.

**Avertissement**

Assurez-vous que vos profils Autopilot ciblent un groupe Azure AD affecté ou dynamique qui n’inclut pas Bureau géré Microsoft appareils. Pour obtenir la procédure à suivre, voir Inscrire Windows appareils dans Intune à l’aide [Windows Autopilot](/mem/autopilot/enrollment-autopilot). Après Bureau géré Microsoft inscription, définissez vos profils Autopilot pour exclure le groupe Modern **Workplace Devices -All** Azure AD.


### <a name="certificate-connectors"></a>Connecteurs de certificat

Si vous avez des connecteurs de certificat qui seront utilisés par les appareils que vous souhaitez inscrire dans Bureau géré Microsoft, les connecteurs ne doivent pas avoir d’erreurs. Une seule des conseils suivants s’applique à votre situation, donc vérifiez-les attentivement.

**Avertissement**

Aucun connecteur de certificat n’est présent. Il est possible que vous n’avez pas besoin de connecteurs, mais vous devez évaluer si vous en avez besoin pour la connectivité réseau sur Bureau géré Microsoft périphériques. Pour plus d’informations, [voir Préparer les certificats et les profils réseau pour Bureau géré Microsoft](certs-wifi-lan.md).

**Avertissement**

Au moins un connecteur de certificat présente une erreur. Si vous avez besoin de ce connecteur pour fournir des certificats aux Bureau géré Microsoft, vous devez résoudre l’erreur. Pour plus d’informations, [voir Préparer les certificats et les profils réseau pour Bureau géré Microsoft](certs-wifi-lan.md).


**Avertissement**

Vous avez au moins un connecteur de certificat et aucune erreur n’est signalée. Toutefois, en vue du déploiement, vous devrez peut-être créer un profil pour réutiliser le connecteur pour Bureau géré Microsoft périphériques. Pour plus d’informations, [voir Préparer les certificats et les profils réseau pour Bureau géré Microsoft](certs-wifi-lan.md).


### <a name="conditional-access-policies"></a>Stratégies d’accès conditionnel

Les stratégies d’accès conditionnel ne doivent pas empêcher Bureau géré Microsoft gestion de votre organisation Azure AD (client) dans Intune et Azure AD.

**Non prêt**

Vous avez au moins une stratégie d’accès conditionnel qui cible tous les utilisateurs. Lors de l’inscription, nous allons exclure Bureau géré Microsoft comptes de service des stratégies d’accès conditionnel pertinentes et appliquer de nouvelles stratégies d’accès conditionnel pour restreindre l’accès à ces comptes. Après l’inscription, vous pouvez consulter la stratégie Bureau géré Microsoft’accès conditionnel dans Microsoft Endpoint Manager. Pour plus d’informations sur ces comptes de service, voir [procédures d’exploitation standard.](../service-description/operations-and-monitoring.md#standard-operating-procedures)

**Avertissement**

Vous avez des stratégies d’accès conditionnel qui pourraient empêcher Bureau géré Microsoft gestion du service Bureau géré Microsoft de gestion. Lors de l’inscription, nous allons exclure Bureau géré Microsoft comptes de service des stratégies d’accès conditionnel pertinentes et appliquer de nouvelles stratégies d’accès conditionnel pour restreindre l’accès à ces comptes. Pour plus d’informations sur ces comptes de service, voir [procédures d’exploitation standard.](../service-description/operations-and-monitoring.md#standard-operating-procedures)

**Erreur**

Le rôle Administrateur Intune n’a pas les autorisations suffisantes pour cette vérification. Vous aurez également besoin de l’un de ces rôles Azure AD pour exécuter cette vérification :

- Lecteur de sécurité
- Administrateur de sécurité
- Administrateur d’accès conditionnel
- Lecteur général
- Administrateur d’appareils


### <a name="device-compliance-policies"></a>Stratégies de conformité des appareils

Les stratégies de conformité des appareils Intune dans votre organisation Azure AD peuvent avoir un impact sur Bureau géré Microsoft appareils.

**Non prêt**

Vous avez au moins une stratégie de conformité qui cible tous les utilisateurs. Bureau géré Microsoft inclut des stratégies de conformité qui cibleront Bureau géré Microsoft appareils mobiles.  Modifiez la stratégie pour cibler un groupe Azure AD spécifique qui n’inclut aucun Bureau géré Microsoft utilisateurs ou appareils. Pour obtenir la procédure à suivre, voir [Créer une stratégie de conformité dans Microsoft Intune](/mem/intune/protect/create-compliance-policy).

**Avertissement**

Assurez-vous que les stratégies de conformité dont vous avez besoin ne ciblent aucune stratégie Bureau géré Microsoft utilisateurs. Pour obtenir la procédure à suivre, voir [Créer une stratégie de conformité dans Microsoft Intune](/mem/intune/protect/create-compliance-policy).



### <a name="device-configuration-profiles"></a>Profils de configuration d’appareil

Les profils de configuration d’appareil Intune dans votre organisation Azure AD ne doivent pas cibler d’utilisateurs ou d’appareils de bureau Microsoft Manage.

**Non prêt**

Vous avez au moins un profil de configuration qui cible tous les utilisateurs, tous les appareils ou les deux. Réinitialisez le profil pour cibler un groupe Azure AD spécifique qui n’inclut aucun Bureau géré Microsoft appareils. Pour connaître la procédure à [suivre, voir Créer un profil avec des paramètres personnalisés dans Microsoft Intune](/mem/intune/configuration/custom-settings-configure).

**Avertissement**

Assurez-vous que les stratégies de configuration dont vous avez besoin n’incluent aucun Bureau géré Microsoft ou utilisateurs. Pour connaître la procédure à [suivre, voir Créer un profil avec des paramètres personnalisés dans Microsoft Intune](/mem/intune/configuration/custom-settings-configure).



### <a name="device-type-restrictions"></a>Restrictions de type d’appareil

Bureau géré Microsoft appareils doivent être autorisés à s’inscrire dans Intune.

**Non prêt**

Vous disposez actuellement d’au moins une stratégie de restriction d’inscription configurée pour empêcher les appareils Windows’inscrire dans Intune. Suivez les [étapes](/mem/intune/enrollment/enrollment-restrictions-set) de la procédure de définition des restrictions d’inscription pour chaque stratégie de restriction d’inscription qui cible les utilisateurs Bureau géré Microsoft et modifiez le paramètre **Windows (MDM)** sur **Autoriser**. Toutefois, vous pouvez définir tous **les** appareils **Windows (MDM)** personnels sur **Bloquer**. 


### <a name="enrollment-status-page"></a>Page État de l’inscription

La page d’état d’inscription (ESP) est actuellement activée. Si vous avez l’intention de participer à la Bureau géré Microsoft prévisualisation publique de cette fonctionnalité, vous pouvez ignorer cet élément. Pour plus d’informations, voir l’expérience de première expérience avec [Autopilot et la page État de l’inscription.](../get-started/esp-first-run.md)

**Non prêt**

Vous avez le profil esp par défaut définie sur **Afficher l’avancement de la configuration de l’application et du profil.** Désactivez ce paramètre ou assurez-vous que les affectations à un groupe Azure AD n’incluent pas d’appareils Bureau géré Microsoft en suivant les étapes de la page Configurer l’état [d’inscription.](/mem/intune/enrollment/windows-enrollment-status)

**Avertissement**

Assurez-vous que les profils qui ont le paramètre Afficher l’application et l’avancement de **la configuration** de profil ne sont affectés à aucun groupe Azure AD qui inclut Bureau géré Microsoft appareils. Pour plus d’informations, voir [Configurer la page État de l’inscription.](/mem/intune/enrollment/windows-enrollment-status)

### <a name="microsoft-store-for-business"></a>Microsoft Store pour Entreprises

Nous utilisons Microsoft Store pour Entreprises et déployons l’application Portail d’entreprise sur Bureau géré Microsoft pour permettre aux utilisateurs d’installer éventuellement certaines applications, telles que Microsoft Project et Microsoft Visio (lorsque cela est autorisé).

**Non prêt**

Microsoft Store pour Entreprises n’est pas activé ou n’est pas synchronisé avec Intune. Pour plus d’informations, voir Comment gérer les applications [achetées](/mem/intune/apps/windows-store-for-business) en volume à partir du Microsoft Store pour Entreprises avec Microsoft Intune et installer Portail d’entreprise Intune [sur les appareils.](../get-started/company-portal.md)

### <a name="multifactor-authentication"></a>Authentification multifacteur

L’authentification multifacteur ne Bureau géré Microsoft pas la gestion de votre organisation Azure AD (client) dans Intune et Azure AD.


**Non prêt**

Certaines stratégies d’authentification  multifacteur sont définies comme requises pour les stratégies d’accès conditionnel qui sont affectées à tous les utilisateurs. Lors de l’inscription, nous allons exclure Bureau géré Microsoft comptes de service des stratégies d’accès conditionnel pertinentes et appliquer de nouvelles stratégies d’accès conditionnel pour restreindre l’accès à ces comptes. Pour plus d’informations sur ces comptes de service, voir [procédures d’exploitation standard.](../service-description/operations-and-monitoring.md#standard-operating-procedures)

**Avertissement**

L’authentification multifacteur est requise sur les stratégies d’accès conditionnel, ce qui peut empêcher Bureau géré Microsoft gestion du service Bureau géré Microsoft de gestion. Lors de l’inscription, nous allons exclure Bureau géré Microsoft comptes de service des stratégies d’accès conditionnel pertinentes et appliquer de nouvelles stratégies d’accès conditionnel pour restreindre l’accès à ces comptes. Pour plus d’informations sur ces comptes de service, voir [procédures d’exploitation standard.](../service-description/operations-and-monitoring.md#standard-operating-procedures)

**Erreur**

Le rôle Administrateur Intune n’a pas les autorisations suffisantes pour cette vérification. Vous aurez également besoin de l’un de ces rôles Azure AD pour exécuter cette vérification :

- Lecteur de sécurité
- Administrateur de sécurité
- Administrateur d’accès conditionnel
- Lecteur général
- Administrateur d’appareils


### <a name="powershell-scripts"></a>Scripts PowerShell

Windows PowerShell scripts ne peuvent pas être affectés d’une manière qui ciblerait Bureau géré Microsoft périphériques.  

**Avertissement**

Assurez-vous que Windows PowerShell scripts de votre organisation Azure AD ne ciblent aucun utilisateur ou appareil de bureau Microsoft Manage. N’affectez pas de script PowerShell pour cibler tous les utilisateurs, tous les appareils ou les deux. Modifiez la stratégie pour utiliser une affectation qui cible un groupe Azure AD spécifique qui n’inclut aucun Bureau géré Microsoft ou utilisateurs. Pour plus d’informations, [voir Utiliser des scripts PowerShell sur des Windows 10 dans Intune.](/mem/intune/apps/intune-management-extension)

### <a name="region"></a>Région

Votre région doit être prise en charge par Bureau géré Microsoft.

**Non prêt**

Votre région d’organisation Azure AD n’est actuellement pas prise en charge par les Bureau géré Microsoft. Pour plus d’informations, [voir Bureau géré Microsoft régions et langues pris en charge.](../service-description/regions-languages.md)

**Avertissement**

Un ou plusieurs des pays où se trouve votre organisation Azure AD ne sont pas pris en charge par Bureau géré Microsoft. Pour plus d’informations, [voir Bureau géré Microsoft régions et langues pris en charge.](../service-description/regions-languages.md)


### <a name="security-baselines"></a>Bases de référence de sécurité

Les stratégies de base de sécurité ne doivent pas cibler Bureau géré Microsoft appareils mobiles.

**Non prêt**

Vous avez un profil de base de sécurité qui cible tous les utilisateurs, tous les appareils ou les deux. Modifiez la stratégie pour utiliser une affectation qui cible un groupe Azure AD spécifique qui n’inclut aucun Bureau géré Microsoft appareils. Pour obtenir la procédure à suivre, voir Utiliser les lignes de base de sécurité [pour configurer Windows 10 appareils mobiles dans Intune.](/mem/intune/protect/security-baselines) Lors de l’inscription, nous appliquons une nouvelle ligne de base de sécurité à tous Bureau géré Microsoft appareils. Après l’inscription, vous pouvez consulter la stratégie de base Bureau géré Microsoft sécurité dans la zone de stratégie de **configuration** de Microsoft Endpoint Manager.

**Avertissement**

Assurez-vous que toutes les stratégies de base de sécurité que vous avez excluent Bureau géré Microsoft appareils. Pour obtenir la procédure à suivre, voir Utiliser les lignes de base de sécurité [pour configurer Windows 10 appareils mobiles dans Intune.](/mem/intune/protect/security-baselines) Lors de l’inscription, nous appliquons une nouvelle ligne de base de sécurité à tous Bureau géré Microsoft appareils. Le groupe Modern **Workplace Devices -All** Azure AD est un groupe dynamique que nous créons lorsque vous vous inscrivez à Bureau géré Microsoft. Vous devez donc revenir pour exclure ce groupe après l’inscription. 


### <a name="windows-apps"></a>Windows applications

Examinez les applications que vous souhaitez Bureau géré Microsoft utilisateurs.

**Avertissement**

Vous devez préparer un inventaire des applications que vous souhaitez que vos Bureau géré Microsoft utilisateurs. Étant donné que ces applications doivent être déployées par Intune, évaluez la réutilisation des applications Intune existantes. Envisagez d’Portail d’entreprise (voir [Install Portail d’entreprise Intune on devices](../get-started/company-portal.md) and Enrollment Status Page (ESP) to distribute apps to your users. Pour plus d’informations, voir [Applications dans Bureau géré Microsoft](apps.md) première expérience d’application avec Autopilot et la page État de [l’inscription.](../get-started/esp-first-run.md)

Vous pouvez demander à votre représentant de compte Microsoft une requête dans Microsoft Endpoint Configuration Manager pour identifier les applications qui sont prêtes à migrer vers Intune ou qui ont besoin d’ajustement.


### <a name="windows-hello-for-business"></a>Windows Hello Entreprise

Bureau géré Microsoft nécessite Windows Hello Entreprise soit activé.

**Non prêt**

Windows Hello Entreprise est désactivé. Activez-la en suivant les étapes de la [stratégie Créer Windows Hello Entreprise](/mem/intune/protect/windows-hello#create-a-windows-hello-for-business-policy)

**Avertissement**

Windows Hello Entreprise n’est pas installé. Activez-la en suivant les étapes de la [Windows stratégie Hello Entreprise.](/mem/intune/protect/windows-hello#create-a-windows-hello-for-business-policy)


### <a name="windows-10-update-rings"></a>Windows 10 sonneries de mise à jour

Votre stratégie « Windows 10 de mise à jour » dans Intune ne doit pas cibler Bureau géré Microsoft périphériques.

**Non prêt**

Vous avez une stratégie de « sonnerie de mise à jour » qui cible tous les appareils, tous les utilisateurs ou les deux. Modifiez la stratégie pour utiliser une affectation qui cible un groupe Azure AD spécifique qui n’inclut aucun Bureau géré Microsoft appareils. Pour obtenir la procédure à [suivre, voir Gérer Windows 10 mises à jour logicielles dans Intune.](/mem/intune/protect/windows-update-for-business-configure)

**Avertissement**

Assurez-vous que les stratégies de sonnerie de mise à jour que vous avez excluent le **groupe Modern Workplace Devices -All** Azure AD. Si vous avez affecté des groupes d’utilisateurs Azure AD à ces stratégies, assurez-vous que les stratégies de sonnerie de mise à jour que vous avez également exclues du groupe Espace de travail moderne **-Tous** les groupes Azure AD à qui vous ajoutez vos utilisateurs Bureau géré Microsoft (ou un groupe équivalent). Pour obtenir la procédure à [suivre, voir Gérer Windows 10 mises à jour logicielles dans Intune.](/mem/intune/protect/windows-update-for-business-configure) Les appareils d’espace de travail modernes **-All** et **Modern Workplace -All** Azure AD groups are groups that we create when you enroll in Bureau géré Microsoft, so you’ll have to come back to exclude this group after enrollment.


## <a name="azure-active-directory-settings"></a>Azure Active Directory paramètres

Vous pouvez accéder aux Azure Active Directory sur le [portail Azure.](https://portal.azure.com)

### <a name="intune-enrollment"></a>Inscription à Intune

Windows 10 appareils de votre organisation Azure AD doivent être en mesure de s’inscrire automatiquement dans Intune.

**Avertissement**

Assurez-vous que **l’étendue utilisateur de la** gestion des données est définie sur **Tout** ou **partie,** et non **sur Aucune.** Si vous **choisissez** Certains, revenir après l’inscription et sélectionner  le groupe Espace de travail moderne **-Tous** les groupes Azure AD pour les groupes ou un groupe équivalent ciblant tous vos utilisateurs Bureau géré Microsoft utilisateurs.  Voir [Configurer l’inscription pour Windows appareils à l’aide de Microsoft Intune](/mem/intune/enrollment/windows-enroll#enable-windows-10-automatic-enrollment).


### <a name="ad-hoc-subscriptions"></a>Abonnements ad hoc

Indique comment vérifier un paramètre qui (s’il est « false ») risque d’empêcher Enterprise’itinérance d’état fonctionne correctement.

**Avertissement**

**Assurez-vous que AllowAdHocSubscriptions** est définie sur **True**. Sinon, Enterprise’itinérance d’état peut ne pas fonctionner. Pour plus d’informations, [voir Set-MsolCompanySettings.](/powershell/module/msonline/set-msolcompanysettings?view=azureadps-1.0)


### <a name="enterprise-state-roaming"></a>Itinérance du statut Entreprise

Enterprise L’itinérance de l’état doit être activée.

**Avertissement**

Assurez-vous que Enterprise l’itinérance de l’état est activé pour **Tous** ou pour **les groupes sélectionnés.** Pour plus d’informations, [voir Enable Enterprise State Roaming dans Azure Active Directory](/azure/active-directory/devices/enterprise-state-roaming-enable).

### <a name="licenses"></a>Licences

Un certain nombre de licences sont requises pour utiliser Bureau géré Microsoft.

**Non prêt**

Vous n’avez pas toutes les licences dont vous avez besoin pour Bureau géré Microsoft. Pour plus d’informations, [voir Bureau géré Microsoft technologies et](../intro/technologies.md) plus [d’informations sur les licences.](prerequisites.md#more-about-licenses)


### <a name="microsoft-managed-desktop-service-accounts"></a>Bureau géré Microsoft de service

Certains noms de compte peuvent être en conflit avec les noms de compte créés Bureau géré Microsoft pour gérer le service Bureau géré Microsoft client.

**Non prêt**

Vous avez au moins un nom de compte qui entrera en conflit avec les noms de compte créés par Bureau géré Microsoft. Travaillez avec votre représentant de compte Microsoft pour exclure ces noms de comptes. Nous ne listons pas les noms de comptes publiquement pour minimiser les risques de sécurité. 


### <a name="security-administrator-roles"></a>Rôles d’administrateur de sécurité

Les utilisateurs ayant certains rôles de sécurité doivent avoir ces rôles attribués dans Microsoft Defender pour point de terminaison.

**Avertissement**

Si vous avez des utilisateurs affectés à l’un de ces rôles dans votre organisation Azure AD, assurez-vous qu’ils ont également ces rôles attribués dans Microsoft Defender for Endpoint. Dans le cas contraire, les administrateurs ayant ces rôles ne pourront pas accéder au portail d’administration.

- Opérateur de sécurité
- Lecteur général

Pour plus d’informations, voir [Créer et gérer des rôles pour le contrôle d’accès basé sur les rôles.](/windows/security/threat-protection/microsoft-defender-atp/user-roles)


### <a name="security-default"></a>Sécurité par défaut

Les paramètres de sécurité par Azure Active Directory empêcheront les Bureau géré Microsoft gérer vos appareils.

**Non prêt**

Les paramètres de sécurité par défaut sont désactivés. Désactiver les paramètres de sécurité par défaut et configurer des stratégies d’accès conditionnel. Pour plus d’informations, voir [Stratégies d’accès conditionnel courantes.](/azure/active-directory/conditional-access/concept-conditional-access-policy-common)

### <a name="self-service-password-reset"></a>Réinitialisation du mot de passe en libre-service

La réinitialisation du mot de passe en libre-service (SSPR) peut être activée pour tous les utilisateurs Bureau géré Microsoft à l’exception Bureau géré Microsoft comptes de service. Pour plus d’informations, voir didacticiel : permettre aux utilisateurs de déverrouiller leur compte ou de réinitialiser leurs mots de passe à l’aide Azure Active Directory réinitialisation du mot de passe [en libre-service.](/azure/active-directory/authentication/tutorial-enable-sspr)

**Avertissement**

Assurez-vous que le  paramètre SSPR sélectionné inclut Bureau géré Microsoft utilisateurs, mais exclut Bureau géré Microsoft comptes de service. Bureau géré Microsoft de service ne peuvent pas fonctionner comme prévu lorsque SSPR est activé.  


### <a name="standard-user-role"></a>Rôle d’utilisateur standard

À part les utilisateurs qui se voit attribuer des rôles Azure AD d’administrateur général et d’administrateur d’appareil, Bureau géré Microsoft utilisateurs seront des utilisateurs standard sans privilèges d’administrateur local. Tous les autres utilisateurs se voit attribuer un rôle d’utilisateur standard lorsqu’ils démarrent Bureau géré Microsoft appareil.

**Avertissement**

Bureau géré Microsoft utilisateurs n’auront pas de privilèges d’administrateur local sur Bureau géré Microsoft appareils après l’inscription.

## <a name="microsoft-365-apps-for-enterprise"></a>Applications Microsoft 365 for entreprise

### <a name="onedrive"></a>OneDrive

La **synchronisation autoriser uniquement sur les PC joints à** un paramètre de domaine spécifique entre en conflit avec Bureau géré Microsoft. Vous pouvez accéder OneDrive paramètres d’accès au [OneDrive’administration.](https://admin.onedrive.com)

**Avertissement**

Vous utilisez le paramètre Autoriser la synchronisation uniquement sur les **PC joints à des domaines spécifiques.** Ce paramètre ne fonctionne pas avec Bureau géré Microsoft. Désactivez ce paramètre et OneDrive à utiliser une stratégie d’accès conditionnel. Pour obtenir [de l’aide, voir](/azure/active-directory/conditional-access/plan-conditional-access) Planifier un déploiement d’accès conditionnel.