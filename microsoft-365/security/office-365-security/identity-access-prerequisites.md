---
title: 'Travail prérequis pour l’implémentation de stratégies d’accès aux identités et appareils : Microsoft 365 pour les | Documents Microsoft'
description: Cet article décrit les conditions préalables à respecter pour utiliser les stratégies et configurations d’accès aux identités et appareils.
ms.author: josephd
author: JoeDavies-MSFT
manager: Laurawi
ms.prod: m365-security
ms.topic: article
audience: Admin
f1.keywords:
- NOCSH
ms.reviewer: martincoetzer
ms.custom:
- it-pro
- goldenconfig
ms.collection:
- M365-identity-device-management
- M365-security-compliance
- m365solution-identitydevice
- m365solution-scenario
ms.technology: mdo
ms.openlocfilehash: ba6a12036d6d6e0b53b930e2b1683781a474d186
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2021
ms.locfileid: "60666721"
---
# <a name="prerequisite-work-for-implementing-identity-and-device-access-policies"></a>Travail prérequis pour l’implémentation de stratégies d’accès aux identités et appareils

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- Azure

Cet article décrit les conditions préalables que les administrateurs doivent respecter pour utiliser les stratégies recommandées d’accès aux identités et aux appareils et pour utiliser l’accès conditionnel. Il décrit également les valeurs par défaut recommandées pour configurer les plateformes clientes pour une expérience d' sign-on unique (SSO) de meilleure choix.

## <a name="prerequisites"></a>Configuration requise

Avant d’utiliser les stratégies d’accès aux identités et appareils recommandées, votre organisation doit respecter les conditions préalables. Les exigences sont différentes pour les différents modèles d’identité et d’authentification répertoriés :

- Cloud uniquement
- Hybride avec authentification de synchronisation de hachage de mot de passe (PHS)
- Hybride avec authentification directe (PTA)
- Fédéré

Le tableau suivant détaille les fonctionnalités prérequises et leur configuration qui s’appliquent à tous les modèles d’identité, sauf en cas de remarque.

|Configuration|Exceptions|Licences|
|---|:---:|---|
|[Configurez PHS](/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization).  Cela doit être activé pour détecter les informations d’identification divulguées et agir sur ces informations pour l’accès conditionnel basé sur les risques. **Remarque :** Cette procédure est requise, que votre organisation utilise ou non l’authentification fédérée.|Cloud uniquement|Microsoft 365 E3 ou E5|
|[Activez l' sign-on](/azure/active-directory/connect/active-directory-aadconnect-sso) unique transparente pour connecter automatiquement les utilisateurs lorsqu’ils se connectent sur leurs appareils d’organisation connectés au réseau de votre organisation.|Cloud uniquement et fédéré|Microsoft 365 E3 ou E5|
|[Configurez les emplacements nommés.](/azure/active-directory/reports-monitoring/quickstart-configure-named-locations) Azure AD Identity Protection collecte et analyse toutes les données de session disponibles pour générer un indice de risque. Nous vous recommandons de spécifier les plages IP publiques de votre organisation pour votre réseau dans la configuration Azure AD emplacements nommés. Le trafic provenant de ces plages se voient donner un score de risque réduit et le trafic en provenance de l’extérieur de l’environnement de l’organisation se voient donner un score de risque plus élevé.||Microsoft 365 E3 ou E5|
|Inscrivez tous les utilisateurs pour réinitialiser le mot de passe en [libre-service (SSPR) et l’authentification multifacteur (MFA).](/azure/active-directory/authentication/concept-registration-mfa-sspr-converged) Nous vous recommandons d’inscrire des utilisateurs pour Azure AD l’authentification multifacteur à l’avance. Azure AD Identity Protection utilise l’authentification Azure AD multifacteur pour effectuer une vérification de sécurité supplémentaire. En outre, pour une meilleure expérience de se connectez, nous recommandons aux utilisateurs d’installer l’application [Microsoft Authenticator](/azure/active-directory/user-help/microsoft-authenticator-app-how-to) et l’application Microsoft Portail d'entreprise sur leurs appareils. Celles-ci peuvent être installées à partir de l’App Store pour chaque plateforme.||Microsoft 365 E3 ou E5|
|[Activer l’inscription automatique de l’appareil des ordinateurs Windows domaine.](/azure/active-directory/active-directory-conditional-access-automatic-device-registration-setup) L’accès conditionnel s’assure que les appareils qui se connectent aux applications sont joints au domaine ou conformes. Pour le prendre en charge sur les ordinateurs Windows, l’appareil doit être inscrit auprès d’Azure AD.  Cet article explique comment configurer l’inscription automatique des appareils.|Cloud uniquement|Microsoft 365 E3 ou E5|
|**Préparer votre équipe de support**. Mettez un plan en place pour les utilisateurs qui ne parviennent pas à effectuer l’authentification multifacteur. Il peut s’agit de les ajouter à un groupe d’exclusions de stratégie ou d’enregistrer de nouvelles informations de l’mf pour eux. Avant d’apporter l’une de ces modifications sensibles à la sécurité, vous devez vous assurer que l’utilisateur réel fait la demande. Exiger que les responsables des utilisateurs facilitent l’approbation est une étape efficace.||Microsoft 365 E3 ou E5|
|[Configurer la réécriture du mot de passe dans AD local](/azure/active-directory/active-directory-passwords-getting-started). L’écriture d’écriture Azure AD mot de passe permet aux utilisateurs de modifier leur mot de passe local lorsqu’une compromission de compte à haut risque est détectée. Vous pouvez activer cette fonctionnalité à l’aide de  Azure AD Connecter de deux manières : soit activer l’écriture écriture par mot de passe dans l’écran des fonctionnalités facultatives de la configuration Azure AD Connecter, soit l’activer via Windows PowerShell.|Cloud uniquement|Microsoft 365 E3 ou E5|
|[Configurez Azure AD protection par mot de passe.](/azure/active-directory/authentication/concept-password-ban-bad) La protection par mot de passe Azure AD détecte et bloque les mots de passe faibles connus et leurs variantes, et peut également bloquer d’autres termes faibles définis par votre organisation. Les listes générales par défaut de mots de passe interdits sont automatiquement appliquées à tous les utilisateurs d’un client Azure AD. Vous pouvez définir d’autres entrées dans une liste personnalisée de mots de passe interdits. Lorsque les utilisateurs modifient ou réinitialisent leurs mots de passe, ces listes sont vérifiées de façon à garantir l’utilisation de mots de passe forts.||Microsoft 365 E3 ou E5|
|[Activez Azure Active Directory Identity Protection](/azure/active-directory/identity-protection/overview-identity-protection). Azure AD La protection des identités vous permet de détecter les vulnérabilités potentielles qui affectent les identités de votre organisation et de configurer une stratégie de correction automatisée en cas de risque de communication faible, moyen et élevé pour les utilisateurs.||Microsoft 365 E5 ou Microsoft 365 E3 avec le module de sécurité E5|
|**Activer l’authentification** [moderne pour Exchange Online](/Exchange/clients-and-mobile-in-exchange-online/enable-or-disable-modern-authentication-in-exchange-online) et pour Skype Entreprise [Online.](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx) L’authentification moderne est une condition préalable à l’utilisation de l’authentification multifacteur. L’authentification moderne est activée par défaut Office clients 2016 et 2019, SharePoint et OneDrive Entreprise.||Microsoft 365 E3 ou E5|
|[Activez l’évaluation de l’accès](microsoft-365-continuous-access-evaluation.md) continu Azure AD. L’évaluation de l’accès continu met fin de manière proactive aux sessions utilisateur actives et applique les modifications de stratégie de client en temps quasi réel.||Microsoft 365 E3 ou E5|
|

## <a name="recommended-client-configurations"></a>Configurations clientes recommandées

Cette section décrit les configurations de client de plateforme par défaut que nous vous recommandons pour offrir la meilleure expérience d' cesso à vos utilisateurs, ainsi que les conditions techniques requises pour l’accès conditionnel.

### <a name="windows-devices"></a>Appareils Windows

Nous vous recommandons d’Windows 10 (version 2004 ou ultérieure), car Azure est conçu pour fournir l’expérience d' utilisateur unique la plus fluide possible pour les utilisateurs locaux et Azure AD. Les appareils scolaires ou de travail doivent être configurés pour rejoindre les Azure AD directement ou si l’organisation utilise la jointette de domaine AD sur site, ces appareils doivent être configurés pour s’inscrire automatiquement et silencieusement auprès de [Azure AD](/azure/active-directory/active-directory-conditional-access-automatic-device-registration-setup).

Pour les appareils byod Windows, les utilisateurs peuvent utiliser ajouter un **compte scolaire ou scolaire.** Notez que les utilisateurs du navigateur Google Chrome sur Windows 10 doivent installer une [extension](https://chrome.google.com/webstore/detail/windows-10-accounts/ppnbnpeolgkicgegkbkbjmhlideopiji?utm_source=chrome-app-launcher-info-dialog) pour obtenir la même expérience de Microsoft Edge utilisateurs. En outre, si votre organisation dispose d’appareils Windows 8 ou 8.1 joints à un domaine, vous pouvez installer Microsoft Workplace Join pour les ordinateurs Windows 10 non connectés. [Téléchargez le package pour inscrire les](https://www.microsoft.com/download/details.aspx?id=53554) appareils avec Azure AD.

### <a name="ios-devices"></a>Périphériques iOS

Nous vous recommandons d’installer [l’application Microsoft Authenticator sur](/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) les appareils des utilisateurs avant de déployer des stratégies d’accès conditionnel ou mfa. Au minimum, l’application doit être installée lorsque les utilisateurs sont invités à inscrire leur appareil auprès d’Azure AD en ajoutant un compte scolaire ou scolaire, ou lorsqu’ils installent l’application portail d’entreprise Intune pour inscrire leur appareil à la gestion. Cela dépend de la stratégie d’accès conditionnel configurée.

### <a name="android-devices"></a>Périphériques Android

Nous recommandons aux utilisateurs [d’installer l Portail d'entreprise Intune et](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal&hl=en) l’application Microsoft Authenticator [avant](/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) le déploiement des stratégies d’accès conditionnel ou le cas échéant lors de certaines tentatives d’authentification. Une fois l’application installée, les utilisateurs peuvent être invités à s’inscrire auprès d’Azure AD ou à inscrire leurs appareils auprès d’Intune. Cela dépend de la stratégie d’accès conditionnel configurée.

Nous recommandons également que les appareils dont l’organisation est propriétaire soient normalisés sur les fabricants OEM et les versions qui gèrent Android for Work ou Samsung Knox afin d’autoriser la gestion et la protection des comptes de messagerie par la stratégie de gestion des appareils mobiles Intune.

### <a name="recommended-email-clients"></a>Clients de messagerie recommandés

Les clients de messagerie suivants sont en charge de l’authentification moderne et de l’accès conditionnel.

|Plate-forme|Client|Version/Notes|
|---|---|---|
|**Windows**|Outlook|2019, 2016, 2013 <p> [Activer l’authentification moderne](../../admin/security-and-compliance/enable-modern-authentication.md) <p> [Mises à jour requises](https://support.office.com/article/Outlook-Updates-472c2322-23a4-4014-8f02-bbc09ad62213)|
|**iOS**|Outlook pour iOS|[La plus récente](https://itunes.apple.com/us/app/microsoft-outlook-email-and-calendar/id951937596?mt=8)|
|**Android**|Outlook pour Android|[La plus récente](https://play.google.com/store/apps/details?id=com.microsoft.office.outlook&hl=en)|
|**MacOS**|Outlook|2019 et 2016|
|**Linux**|Non prise en charge||
|

### <a name="recommended-client-platforms-when-securing-documents"></a>Plateformes clientes recommandées pour sécuriser des documents

Les clients suivants sont recommandés lorsqu’une stratégie de documents sécurisés a été appliquée.

|Plate-forme|Word/Excel/PowerPoint|OneNote|Application OneDrive|Application SharePoint|[Client de synchronisation OneDrive](/onedrive/enable-conditional-access)|
|---|---|---|---|---|---|
|Windows 8.1|Pris en charge|Pris en charge|N/A|N/A|Pris en charge|
|Windows 10|Pris en charge|Pris en charge|N/A|N/A|Pris en charge|
|Android|Pris en charge|Pris en charge|Pris en charge|Pris en charge|N/A|
|iOS|Pris en charge|Pris en charge|Pris en charge|Pris en charge|N/A|
|macOS|Pris en charge|Pris en charge|N/A|N/A|Non prise en charge|
|Linux|Non pris en charge|Non pris en charge|Non pris en charge|Non pris en charge|Non pris en charge|
|

### <a name="microsoft-365-client-support"></a>Prise en charge du client Microsoft 365

Pour plus d’informations sur la prise en charge Microsoft 365 client, consultez les articles suivants :

- [Microsoft 365 Prise en charge des applications clientes : accès conditionnel](../../enterprise/microsoft-365-client-support-conditional-access.md)
- [Microsoft 365 Prise en charge des applications client : authentification multifacteur](../../enterprise/microsoft-365-client-support-multi-factor-authentication.md)

## <a name="protecting-administrator-accounts"></a>Protection des comptes d’administrateur

Pour Microsoft 365 E3 ou E5 ou avec des licences Azure AD Premium P1 ou P2 distinctes, vous pouvez exiger l' approbation de la MFA pour les comptes d’administrateur avec une stratégie d’accès conditionnel créée manuellement. Pour [plus d’informations,](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa) voir Accès conditionnel : exiger l' approbation de la MFA pour les administrateurs.

Pour les éditions de Microsoft 365 ou Office 365 qui ne sont pas en charge l’accès conditionnel, vous pouvez activer les [paramètres](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) de sécurité par défaut pour exiger l’mf pour tous les comptes.

Voici quelques recommandations supplémentaires :

- Utilisez [Azure AD Privileged Identity Management](/azure/active-directory/privileged-identity-management/pim-getting-started) pour réduire le nombre de comptes administratifs persistants.
- [Utilisez la](../../compliance/privileged-access-management-overview.md) gestion des accès privilégiés pour protéger votre organisation contre les violations qui peuvent utiliser des comptes d’administrateur privilégiés existants avec un accès permanent aux données sensibles ou à des paramètres de configuration critiques.
- Créez et utilisez des comptes distincts qui sont attribués [Microsoft 365 rôles d’administrateur uniquement](../../admin/add-users/about-admin-roles.md) *pour l’administration.* Les administrateurs doivent avoir leur propre compte d’utilisateur pour une utilisation normale non administrative et utiliser uniquement un compte administratif si nécessaire pour effectuer une tâche associée à leur rôle ou fonction.
- Suivez [les meilleures pratiques pour](/azure/active-directory/admin-roles-best-practices) sécuriser les comptes privilégiés dans Azure AD.

## <a name="next-step"></a>Étape suivante

[![Étape 2 : Configurer les stratégies d’accès conditionnel d’accès et d’identité courantes.](../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-2.png)](identity-access-policies.md)

[Configurer les stratégies communes d’accès aux identités et aux appareils](identity-access-policies.md)