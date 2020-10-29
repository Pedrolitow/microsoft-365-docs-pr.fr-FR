---
title: Corriger les problèmes détectés par l’outil d’évaluation de la disponibilité
description: Actions détaillées à effectuer pour chaque problème rencontré par l’outil
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: a6dec9473ee632b74bb79e50156cedff53a3cba3
ms.sourcegitcommit: fa26da0be667d4be0121c52b05488dc76c5d626c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "48795116"
---
# <a name="fix-issues-found-by-the-readiness-assessment-tool"></a>Corriger les problèmes détectés par l’outil d’évaluation de la disponibilité

Pour chaque vérification, l’outil signale l’un des quatre résultats possibles :


|Résultat  |Signification  |
|---------|---------|
|Prêt     | Aucune action n’est requise avant la fin de l’enregistrement.        |
|OpenSSL    | Suivez les étapes décrites dans l’outil ou dans cet article pour obtenir une expérience optimale avec l’enregistrement et pour les utilisateurs. Vous *pouvez* effectuer l’opération d’enregistrement, mais vous devez résoudre ces problèmes avant de déployer votre premier périphérique.        |
|Non prêt | *L’enregistrement échoue si vous ne résolvez pas ces problèmes.* Suivez les étapes décrites dans l’outil ou dans cet article pour les résoudre.        |
|Erreur | Le rôle Azure active Director (AD) que vous utilisez ne dispose pas des autorisations suffisantes pour effectuer cette vérification. |

## <a name="microsoft-intune-settings"></a>Paramètres Microsoft Intune

### <a name="autopilot-deployment-profile"></a>Profil de déploiement de AutoPilot

Vous ne devez pas avoir de profils AutoPilot qui ciblent les groupes affectés ou dynamiques utilisés par le bureau géré Microsoft. Microsoft Managed Desktop utilise AutoPilot pour mettre en service de nouveaux appareils.

**Non prêt**

Vous disposez d’un profil AutoPilot affecté à tous les appareils. Pour connaître les étapes à suivre, consultez la rubrique [inscrire des appareils Windows dans Intune à l’aide de Windows AutoPilot](https://docs.microsoft.com/mem/autopilot/enrollment-autopilot). Après l’enregistrement de bureau géré Microsoft, définissez votre stratégie AutoPilot pour exclure les **périphériques de l’espace de travail modernes-tous les** groupes Azure ad.

**OpenSSL**

Assurez-vous que vos profils AutoPilot ciblent un groupe Azure AD affecté ou dynamique qui n’inclut pas les appareils de bureau géré Microsoft qui seront créés lors de l’enregistrement. Pour connaître les étapes à suivre, consultez la rubrique [inscrire des appareils Windows dans Intune à l’aide de Windows AutoPilot](https://docs.microsoft.com/mem/autopilot/enrollment-autopilot). Après l’enregistrement de bureau géré Microsoft, définissez votre stratégie AutoPilot pour exclure les **périphériques de l’espace de travail modernes-tous les** groupes Azure ad.


### <a name="certificate-connectors"></a>Connecteurs de certificats

Si des connecteurs de certificat sont utilisés par les appareils que vous souhaitez inscrire dans Microsoft Managed Desktop, les connecteurs ne peuvent pas contenir d’erreurs. Seul l’un des avis suivants s’applique à votre situation, vérifiez-le attentivement.

**OpenSSL**

Aucun connecteur de certificat n’est présent. Il est possible que vous n’ayez pas besoin de connecteurs, mais vous devez évaluer si vous aurez besoin d’une partie de la connectivité réseau aux appareils de bureau gérés par Microsoft. Pour plus d’informations, consultez la rubrique [Prepare Certificates and Network profiles for Microsoft Managed Desktop](certs-wifi-lan.md).

**OpenSSL**

Au moins un connecteur de certificat comporte une erreur. Si vous avez besoin de ce connecteur pour la connectivité aux appareils de bureau gérés par Microsoft, vous devez résoudre l’erreur. Pour plus d’informations, consultez la rubrique [Prepare Certificates and Network profiles for Microsoft Managed Desktop](certs-wifi-lan.md).


**OpenSSL**

Vous disposez d’au moins un connecteur de certificat et aucune erreur n’est signalée. Toutefois, vous devrez peut-être créer un profil pour réutiliser le connecteur pour les appareils de bureau gérés par Microsoft. Pour plus d’informations, consultez la rubrique [Prepare Certificates and Network profiles for Microsoft Managed Desktop](certs-wifi-lan.md).


### <a name="conditional-access-policies"></a>Stratégies d’accès conditionnel

Les stratégies d’accès conditionnel dans votre organisation Azure AD ne doivent pas cibler les utilisateurs de bureau Microsoft Manage.

**Non prêt**

Vous disposez d’au moins une stratégie d’accès conditionnel qui cible tous les utilisateurs. Réinitialisez la stratégie pour cibler un groupe Azure AD spécifique qui n’inclut pas le groupe Azure AD des comptes de service de bureau géré Microsoft qui seront créés lors de l’enregistrement. Pour connaître les étapes à suivre, consultez la rubrique [accès conditionnel : utilisateurs et groupes](https://docs.microsoft.com/azure/active-directory/conditional-access/concept-conditional-access-users-groups).

**OpenSSL**

Assurez-vous que toutes les stratégies d’accès conditionnel vous avez exclu le groupe Azure AD comptes de service de l' **espace de travail moderne** . Pour connaître les étapes à suivre, consultez la rubrique [Adjust ConditionalAttribute Access](https://docs.microsoft.com/microsoft-365/managed-desktop/get-started/conditional-access). Le groupe Azure AD de comptes de service de l' **espace de travail moderne** est un groupe dynamique que nous créons pour le service lors de l’inscription. Vous devrez revenir à l’exclusion de ce groupe après l’enregistrement. Pour plus d’informations sur ces comptes de service, consultez la rubrique [Standard Operating Procedures](../service-description/operations-and-monitoring.md#standard-operating-procedures).

**Error**

Le rôle d’administrateur Intune ne dispose pas des autorisations suffisantes pour cette vérification. Vous aurez également besoin de ces rôles Azure AD pour exécuter cette vérification :

- Lecteur de sécurité
- Administrateur de sécurité
- Administrateur d’accès conditionnel
- Lecteur général
- Administrateur de périphériques


### <a name="device-compliance-policies"></a>Stratégies de conformité des appareils

Les stratégies de conformité d’appareil Intune dans votre organisation Azure AD ne doivent pas cibler les utilisateurs de bureau géré Microsoft.

**Non prêt**

Vous avez au moins une stratégie de conformité qui cible tous les utilisateurs. Réinitialisez la stratégie pour cibler un groupe Azure AD spécifique qui n’inclut pas d’utilisateurs de bureau géré Microsoft. Pour connaître les étapes à suivre, voir [Create a Compliance Policy in Microsoft Intune](https://docs.microsoft.com/mem/intune/protect/create-compliance-policy).

**OpenSSL**

Assurez-vous que les stratégies de conformité que vous n’avez pas n’incluent aucun utilisateur de bureau géré Microsoft. Pour connaître les étapes à suivre, voir [Create a Compliance Policy in Microsoft Intune](https://docs.microsoft.com/mem/intune/protect/create-compliance-policy).



### <a name="device-configuration-policies"></a>Stratégies de configuration des appareils

Les stratégies de configuration d’appareil Intune dans votre organisation Azure AD ne doivent pas cibler des utilisateurs ou des appareils de bureau Microsoft.

**Non prêt**

Vous disposez d’au moins une stratégie de configuration qui cible tous les utilisateurs, tous les appareils ou les deux. Réinitialisez la stratégie pour cibler un groupe Azure AD spécifique qui n’inclut pas d’appareils de bureau géré Microsoft. Pour connaître les étapes à suivre, voir [Create a Compliance Policy in Microsoft Intune](https://docs.microsoft.com/mem/intune/configuration/custom-settings-configure).

**OpenSSL**

Assurez-vous que les stratégies de conformité que vous n’avez pas inclues tous les appareils ou les utilisateurs de bureau gérés Microsoft. Pour connaître les étapes à suivre, voir [Create a Compliance Policy in Microsoft Intune](https://docs.microsoft.com/mem/intune/configuration/custom-settings-configure).



### <a name="device-type-restrictions"></a>Restrictions de type de périphérique

Les appareils de bureau gérés Microsoft doivent être autorisés à s’inscrire dans Intune.

**Non prêt**

Suivez les étapes de la procédure [définir les restrictions d’inscriptions](https://docs.microsoft.com/mem/intune/enrollment/enrollment-restrictions-set) pour modifier le paramètre sur **autoriser** .


### <a name="enrollment-status-page"></a>Page d’état d’enregistrement

La page d’état d’enregistrement (ESP) est actuellement activée. Si vous participez à la préversion publique de cette fonctionnalité, vous pouvez ignorer cet élément. Pour plus d’informations, consultez la rubrique relative [à l’expérience de première exécution avec AutoPilot et la page État de l’enregistrement](../get-started/esp-first-run.md).

**Non prêt**

Le profil ESP par défaut est défini pour afficher la progression de la configuration de l' **application et du profil** . Désactivez ce paramètre en suivant les étapes de [la page Configurer l’état de l’inscription](https://docs.microsoft.com/mem/intune/enrollment/windows-enrollment-status).

**OpenSSL**

Assurez-vous que tous les profils dont le paramètre **afficher l’application et la configuration de profil** sont en cours de progression ne sont pas affectés à un groupe Azure ad qui inclut les appareils de bureau gérés par Microsoft. Pour plus d’informations, reportez-vous à [la rubrique Configurer la page État de l’inscription](https://docs.microsoft.com/mem/intune/enrollment/windows-enrollment-status).

### <a name="intune-enrollment"></a>Enregistrement Intune

Les appareils Windows 10 dans votre organisation Azure AD doivent être automatiquement apportés dans Intune.

**Non prêt**

Les utilisateurs de votre organisation Azure AD ne sont pas automatiquement intégrés dans Microsoft Intune. Modifiez l’étendue utilisateur MDM sur **une partie** ou la **totalité** . Si vous choisissez **certaines** , revenez après l’enregistrement et sélectionnez le groupe **moderne espace de travail-tout** Azure AD pour les **groupes** .


### <a name="microsoft-store-for-business"></a>Microsoft Store pour Entreprises

Nous utilisons Microsoft Store pour les entreprises afin que vous puissiez télécharger le portail d’entreprise pour déployer certaines applications, telles que Microsoft Project et Microsoft Visio.

**Non prêt**

Microsoft Store pour les entreprises n’est pas activé ou n’est pas synchronisé avec Intune. Pour plus d’informations, consultez la rubrique [How to Manage volume purchased Apps from the Microsoft Store for Business with Microsoft Intune](https://docs.microsoft.com/mem/intune/apps/windows-store-for-business) and [install Intune Company Portal on on Devices](../get-started/company-portal.md).

### <a name="multi-factor-authentication"></a>Authentification multifacteur

L’authentification multifacteur ne doit pas être appliquée accidentellement aux comptes de service de bureau géré Microsoft.


**Non prêt**

Certaines stratégies d’authentification multifacteur (MFA) sont définies comme « obligatoires » pour les stratégies d’accès conditionnel qui sont affectées à tous les utilisateurs. Modifiez la stratégie de façon à utiliser une affectation ciblant un groupe Azure AD spécifique qui n’inclut aucun périphérique de bureau géré Microsoft. Pour plus d’informations, reportez-vous à [stratégies d’accès conditionnel](#conditional-access-policies) et [accès conditionnel : exiger l’authentification multifacteur pour tous les utilisateurs](https://docs.microsoft.com/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa).

**OpenSSL**

Assurez-vous que toutes les stratégies d’accès conditionnel qui requièrent l’authentification MFA excluent le groupe **de travail moderne-tous les** groupes Azure ad. Pour plus d’informations, reportez-vous à [stratégies d’accès conditionnel](#conditional-access-policies) et [accès conditionnel : exiger l’authentification multifacteur pour tous les utilisateurs](https://docs.microsoft.com/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa). Le groupe de **travail moderne-tous les** groupes Azure AD est un groupe dynamique que nous créons lors de l’inscription au bureau géré Microsoft, de sorte que vous devez revenir à l’exclusion de ce groupe après l’inscription.

**Error**

Le rôle d’administrateur Intune ne dispose pas des autorisations suffisantes pour cette vérification. Vous aurez également besoin de ces rôles Azure AD pour exécuter cette vérification :

- Lecteur de sécurité
- Administrateur de sécurité
- Administrateur d’accès conditionnel
- Lecteur général
- Administrateur de périphériques


### <a name="powershell-scripts"></a>Scripts PowerShell

Les scripts Windows PowerShell ne peuvent pas être affectés de manière à cibler les périphériques de bureau géré Microsoft.  

**OpenSSL**

Assurez-vous que les scripts Windows PowerShell de votre organisation Azure AD ne ciblent pas les utilisateurs ou les appareils de bureau Microsoft. Pour plus d’informations, reportez-vous à [utiliser des scripts PowerShell sur des appareils Windows 10 dans Intune](https://docs.microsoft.com/mem/intune/apps/intune-management-extension).

### <a name="region"></a>Région

Votre région doit être prise en charge par le bureau géré Microsoft.

**Non prêt**

La région de votre organisation Azure AD n’est actuellement pas prise en charge par le bureau géré Microsoft. Pour plus d’informations, voir [régions et langues prises en charge par Microsoft Managed Desktop](../service-description/regions-languages.md).

**OpenSSL**

Un ou plusieurs des pays de votre organisation Azure AD ne sont pas pris en charge par le bureau géré Microsoft. Pour plus d’informations, voir [régions et langues prises en charge par Microsoft Managed Desktop](../service-description/regions-languages.md).


### <a name="security-baselines"></a>Lignes de base de sécurité

Les stratégies de base de sécurité ne doivent pas viser les appareils de bureau gérés Microsoft.

**Non prêt**

Vous disposez d’un profil de base de sécurité ciblant tous les utilisateurs, tous les périphériques ou les deux. Modifiez la stratégie de façon à utiliser une affectation ciblant un groupe Azure AD spécifique qui n’inclut aucun périphérique de bureau géré Microsoft. Pour connaître les étapes à suivre, voir [Use Security baselines to configure Windows 10 Devices in Intune](https://docs.microsoft.com/mem/intune/protect/security-baselines).

**OpenSSL**

Assurez-vous que toutes les stratégies de base de sécurité que vous avez excluent les appareils de bureau gérés Microsoft. Pour connaître les étapes à suivre, voir [Use Security baselines to configure Windows 10 Devices in Intune](https://docs.microsoft.com/mem/intune/protect/security-baselines). Les **appareils de travail modernes-tous les** groupes Azure ad sont un groupe dynamique que nous créons lors de l’inscription au bureau géré Microsoft, de sorte que vous devrez revenir pour exclure ce groupe après l’inscription.


### <a name="windows-apps"></a>Applications Windows

Passez en revue les applications que les utilisateurs de bureau géré Microsoft doivent disposer.

**OpenSSL**

Vous devez préparer un inventaire des applications que vos utilisateurs de bureau géré Microsoft doivent disposer. Assurez-vous que ces applications peuvent être déployées par Intune. Pour plus d’informations, consultez la rubrique [applications in Microsoft Managed Desktop](apps.md).

Vous pouvez demander à votre responsable de compte Microsoft une requête dans le gestionnaire de configuration de point de terminaison Microsoft pour identifier les applications qui sont prêtes à migrer vers Intune ou qui ont besoin d’un ajustement.


### <a name="windows-hello-for-business"></a>Windows Hello Entreprise

Microsoft Managed Desktop requiert l’activation de Windows Hello entreprise.

**Non prêt**

Windows Hello entreprise est désactivé. Activez-le en suivant les étapes de la procédure [créer une stratégie Windows Hello entreprise](https://docs.microsoft.com/mem/intune/protect/windows-hello#create-a-windows-hello-for-business-policy)

**OpenSSL**

Windows Hello entreprise n’est pas configuré. Activez-le en suivant les étapes de la procédure [créer une stratégie Windows Hello entreprise](https://docs.microsoft.com/mem/intune/protect/windows-hello#create-a-windows-hello-for-business-policy).


### <a name="windows-10-update-rings"></a>Sonneries de mise à jour de Windows 10

Votre stratégie « Windows 10 Update Ring » dans Intune ne doit pas cibler les appareils de bureau gérés par Microsoft.

**Non prêt**

Vous disposez d’une stratégie de mise à jour circulaire qui cible tous les périphériques, tous les utilisateurs ou les deux. Modifiez la stratégie de façon à utiliser une affectation ciblant un groupe Azure AD spécifique qui n’inclut aucun périphérique de bureau géré Microsoft. Pour connaître les étapes à suivre, voir [Manage Windows 10 Software Updates in Intune](https://docs.microsoft.com/mem/intune/protect/windows-update-for-business-configure).

**OpenSSL**

Assurez-vous que toutes les stratégies Ring de mise à jour que vous avez excluent le groupe **de travail moderne-tous les** groupes Azure ad. Pour connaître les étapes à suivre, voir [Manage Windows 10 Software Updates in Intune](https://docs.microsoft.com/mem/intune/protect/windows-update-for-business-configure). Les **appareils de travail modernes-tous les** groupes Azure ad sont un groupe dynamique que nous créons lors de l’inscription au bureau géré Microsoft, de sorte que vous devrez revenir pour exclure ce groupe après l’inscription.


## <a name="azure-active-directory-settings"></a>Paramètres Azure Active Directory


### <a name="ad-hoc-subscriptions"></a>Abonnements ad hoc

Indique comment vérifier un paramètre qui (si sa valeur est définie sur "false") peut empêcher le fonctionnement correct de l’état d’entreprise.

**OpenSSL**

Assurez-vous que **AllowAdHocSubscriptions** est défini sur **true** . Dans le cas contraire, l’itinérance de l’état de l’entreprise peut ne pas fonctionner. Pour plus d’informations, consultez la rubrique [Set-MsolCompanySettings](https://docs.microsoft.com/powershell/module/msonline/set-msolcompanysettings?view=azureadps-1.0).


### <a name="enterprise-state-roaming"></a>Itinérance du statut Entreprise

L’itinérance de l’état de l’entreprise doit être activée.

**OpenSSL**

Assurez-vous que l’itinérance de l’état de l’entreprise est activée pour **tous les** groupes ou pour ceux **sélectionnés** . Pour plus d’informations, consultez la rubrique [Enable Enterprise State Roaming in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/devices/enterprise-state-roaming-enable).

### <a name="licenses"></a>Licences

Un certain nombre de licences sont requises pour utiliser Microsoft Managed Desktop.

**Non prêt**

Vous ne disposez pas de toutes les licences dont vous avez besoin pour utiliser le bureau géré Microsoft. Pour plus d’informations, consultez la rubrique [Microsoft Managed Desktop Technologies](../intro/technologies.md) et en [savoir plus sur les licences](prerequisites.md#more-about-licenses).


### <a name="security-account-names"></a>Noms des comptes de sécurité

Certains noms de compte de sécurité peuvent entrer en conflit avec ceux créés par Microsoft Managed Desktop.

**Non prêt**

Vous avez au moins un nom de compte qui sera en conflit avec ceux créés par Microsoft Managed Desktop. Collaborez avec votre représentant Microsoft pour exclure ces noms de compte.


### <a name="security-administrator-roles"></a>Rôles d’administrateur de sécurité

Les utilisateurs disposant de certains rôles de sécurité doivent disposer de ceux qui sont attribués à Microsoft Defender pour le point de terminaison.

**OpenSSL**

Si l’un de ces rôles est affecté dans votre organisation Azure AD, assurez-vous que ces rôles sont également attribués à Microsoft Defender pour le point de terminaison. Dans le cas contraire, les administrateurs disposant de ces rôles ne pourront pas accéder au portail d’administration.

- Lecteur de sécurité
- Opérateur de sécurité
- Lecteur général

Pour plus d’informations, consultez la rubrique [créer et gérer des rôles pour le contrôle d’accès basé sur un rôle](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/user-roles).


### <a name="security-default"></a>Sécurité par défaut

Les paramètres de sécurité par défaut dans Azure Active Directory empêchent Microsoft Managed Desktop de gérer vos appareils.

**Non prêt**

Les paramètres de sécurité par défaut sont activés. Désactivez les paramètres de sécurité par défaut et configurez les stratégies d’accès conditionnel. Pour plus d’informations, consultez la rubrique [stratégies d’accès conditionnel courantes](https://docs.microsoft.com/azure/active-directory/conditional-access/concept-conditional-access-policy-common).

### <a name="self-service-password-reset"></a>Réinitialisation du mot de passe en libre-service

La réinitialisation du mot de passe en libre-service (SSPR) doit être activée.

**Non prêt**

SSPR doit être activé pour tous les utilisateurs. Si ce n’est pas le cas, les comptes de service de bureau géré Microsoft ne peuvent pas fonctionner. Pour plus d’informations, consultez [la rubrique Tutorial : autoriser les utilisateurs à déverrouiller leur compte ou réinitialiser les mots de passe à l’aide de la réinitialisation du mot de passe en libre-service Azure Active Directory](https://docs.microsoft.com/azure/active-directory/authentication/tutorial-enable-sspr).

**OpenSSL**

Assurez-vous que le paramètre **sélectionné** SSPR inclut Microsoft Managed Desktop Devices.

**Error**

Le rôle d’administrateur Intune ne dispose pas des autorisations suffisantes pour cette vérification. Vous aurez également besoin du rôle Azure AD du lecteur de rapports pour exécuter cette vérification.


### <a name="standard-user-role"></a>Rôle d’utilisateur standard

Les utilisateurs de bureau géré Microsoft doivent être des utilisateurs standard sans privilèges d’administrateur local. Ils se verront attribuer un rôle d’utilisateur standard lorsqu’ils démarreront leur périphérique de bureau géré Microsoft.

**OpenSSL**

Les utilisateurs de bureau géré Microsoft ne doivent pas avoir de privilèges d’administrateur local avant l’enregistrement.

## <a name="microsoft-365-apps-for-enterprise"></a>Applications Microsoft 365 for entreprise

### <a name="onedrive-for-business"></a>OneDrive Entreprise

Le paramètre **autoriser la synchronisation uniquement sur des PC joints à des domaines spécifiques** entre en conflit avec le bureau géré Microsoft.

**OpenSSL**

Vous utilisez le paramètre **autoriser la synchronisation uniquement sur des PC joints à des domaines spécifiques** . Ce paramètre ne fonctionne pas avec Microsoft Managed Desktop. Désactivez ce paramètre, puis configurez OneDrive entreprise pour qu’il utilise une stratégie d’accès conditionnel. Voir [planifier un déploiement d’accès conditionnel](https://docs.microsoft.com/azure/active-directory/conditional-access/plan-conditional-access) pour obtenir de l’aide.

