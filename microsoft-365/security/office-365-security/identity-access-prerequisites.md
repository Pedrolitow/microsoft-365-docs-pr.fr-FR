---
title: Travail requis pour implémenter des stratégies d’identité et d’accès aux appareils - Microsoft 365 pour les | d’entreprise Microsoft Docs
description: Cet article décrit les prérequis que vous devez remplir pour utiliser Confiance nulle stratégies et configurations d’accès aux identités et aux appareils.
ms.author: dansimp
author: dansimp
manager: dansimp
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
- zerotrust-solution
ms.technology: mdo
ms.openlocfilehash: 6883782a942b7fda8e2dedc721756b59a3e7ede6
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2022
ms.locfileid: "66749987"
---
# <a name="prerequisite-work-for-implementing-zero-trust-identity-and-device-access-policies"></a>Travail requis pour implémenter Confiance nulle stratégies d’identité et d’accès aux appareils

Cet article décrit les prérequis que les administrateurs doivent remplir pour utiliser les stratégies d’identité et d’accès aux appareils Confiance nulle recommandées et pour utiliser l’accès conditionnel. Il décrit également les valeurs par défaut recommandées pour la configuration des plateformes clientes pour la meilleure expérience d’authentification unique (SSO).

## <a name="prerequisites"></a>Conditions préalables

Avant d’utiliser les stratégies d’identité et d’accès aux appareils Confiance nulle recommandées, votre organisation doit respecter les prérequis. Les exigences sont différentes pour les différents modèles d’identité et d’authentification répertoriés :

- Cloud uniquement
- Authentification hybride avec synchronisation de hachage de mot de passe (PHS)
- Hybride avec authentification directe (PTA)
- Fédérés

Le tableau suivant détaille les fonctionnalités requises et leur configuration qui s’appliquent à tous les modèles d’identité, sauf indication contraire.

|Configuration|Exceptions|Licences|
|---|:---:|---|
|[Configurez PHS](/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization).  Cela doit être activé pour détecter les informations d’identification divulguées et agir sur celles-ci pour l’accès conditionnel basé sur les risques. **Note:** Cela est nécessaire, que votre organisation utilise ou non l’authentification fédérée.|Cloud uniquement|Microsoft 365 E3 ou E5|
|[Activez l’authentification unique transparente](/azure/active-directory/connect/active-directory-aadconnect-sso) pour connecter automatiquement les utilisateurs lorsqu’ils se trouvent sur leurs appareils d’organisation connectés à votre réseau d’organisation.|Cloud uniquement et fédéré|Microsoft 365 E3 ou E5|
|[Configurez des emplacements nommés](/azure/active-directory/reports-monitoring/quickstart-configure-named-locations). Azure AD Identity Protection collecte et analyse toutes les données de session disponibles pour générer un indice de risque. Nous vous recommandons de spécifier les plages d’adresses IP publiques de votre organisation pour votre réseau dans la configuration des emplacements nommés Azure AD. Le trafic provenant de ces plages reçoit un score de risque réduit, et le trafic provenant de l’extérieur de l’environnement de l’organisation reçoit un score de risque plus élevé.||Microsoft 365 E3 ou E5|
|[Inscrivez tous les utilisateurs pour la réinitialisation de mot de passe en libre-service (SSPR) et l’authentification multifacteur (MFA).](/azure/active-directory/authentication/concept-registration-mfa-sspr-converged) Nous vous recommandons d’inscrire des utilisateurs pour l’authentification multifacteur Azure AD à l’avance. Azure AD Identity Protection utilise l’authentification multifacteur Azure AD pour effectuer une vérification de sécurité supplémentaire. En outre, pour une expérience de connexion optimale, nous recommandons aux utilisateurs d’installer [l’application Microsoft Authenticator](/azure/active-directory/user-help/microsoft-authenticator-app-how-to) et l’application Microsoft Portail d'entreprise sur leurs appareils. Ceux-ci peuvent être installés à partir de l’App Store pour chaque plateforme.||Microsoft 365 E3 ou E5|
|[Activez l’inscription automatique des appareils des ordinateurs Windows joints à un domaine](/azure/active-directory/active-directory-conditional-access-automatic-device-registration-setup). L’accès conditionnel permet de s’assurer que les appareils qui se connectent à des applications sont joints à un domaine ou conformes. Pour le prendre en charge sur les ordinateurs Windows, l’appareil doit être inscrit auprès d’Azure AD.  Cet article explique comment configurer l’inscription automatique des appareils.|Cloud uniquement|Microsoft 365 E3 ou E5|
|**Préparer votre équipe de support**. Mettez un plan en place pour les utilisateurs qui ne parviennent pas à effectuer l’authentification multifacteur. Il peut s’agir de les ajouter à un groupe d’exclusion de stratégie ou d’inscrire de nouvelles informations d’authentification multifacteur pour eux. Avant d’apporter l’une de ces modifications sensibles à la sécurité, vous devez vous assurer que l’utilisateur réel effectue la demande. Exiger que les responsables des utilisateurs facilitent l’approbation est une étape efficace.||Microsoft 365 E3 ou E5|
|[Configurer la réécriture du mot de passe dans AD local](/azure/active-directory/active-directory-passwords-getting-started). La réécriture du mot de passe permet à Azure AD d’exiger que les utilisateurs modifient leurs mots de passe locaux lorsqu’une compromission de compte à haut risque est détectée. Vous pouvez activer cette fonctionnalité à l’aide d’Azure AD Connect de l’une des deux manières suivantes : activer l’écriture **différée du mot de passe** dans l’écran des fonctionnalités facultatives de l’installation d’Azure AD Connect ou l’activer via Windows PowerShell.|Cloud uniquement|Microsoft 365 E3 ou E5|
|[Configurez la protection par mot de passe Azure AD](/azure/active-directory/authentication/concept-password-ban-bad). La protection par mot de passe Azure AD détecte et bloque les mots de passe faibles connus et leurs variantes, et peut également bloquer d’autres termes faibles définis par votre organisation. Les listes générales par défaut de mots de passe interdits sont automatiquement appliquées à tous les utilisateurs d’un client Azure AD. Vous pouvez définir d’autres entrées dans une liste personnalisée de mots de passe interdits. Lorsque les utilisateurs modifient ou réinitialisent leurs mots de passe, ces listes sont vérifiées de façon à garantir l’utilisation de mots de passe forts.||Microsoft 365 E3 ou E5|
|[Activez Azure Active Directory Identity Protection](/azure/active-directory/identity-protection/overview-identity-protection). Azure AD Identity Protection vous permet de détecter les vulnérabilités potentielles affectant les identités de votre organisation et de configurer une stratégie de correction automatisée en cas de risque de connexion faible, moyenne et élevée et à risque utilisateur.||Microsoft 365 E5 ou Microsoft 365 E3 avec le module complémentaire Sécurité E5|
|**Activez l’authentification moderne** pour [Exchange Online](/Exchange/clients-and-mobile-in-exchange-online/enable-or-disable-modern-authentication-in-exchange-online) et [pour Skype Entreprise Online](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx). L’authentification moderne est un prérequis pour l’utilisation de l’authentification multifacteur. L’authentification moderne est activée par défaut pour les clients Office 2016 et 2019, SharePoint et OneDrive Entreprise.||Microsoft 365 E3 ou E5|
|[Activez l’évaluation de l’accès continu](microsoft-365-continuous-access-evaluation.md) pour Azure AD. L’évaluation continue de l’accès met fin de manière proactive aux sessions utilisateur actives et applique les modifications de stratégie de locataire en quasi-temps réel.||Microsoft 365 E3 ou E5|

## <a name="recommended-client-configurations"></a>Configurations clientes recommandées

Cette section décrit les configurations clientes de plateforme par défaut que nous vous recommandons de fournir à vos utilisateurs la meilleure expérience d’authentification unique, ainsi que les prérequis techniques pour l’accès conditionnel.

### <a name="windows-devices"></a>Appareils Windows

Nous vous recommandons d’Windows 11 ou Windows 10 (version 2004 ou ultérieure), car Azure est conçu pour offrir l’expérience d’authentification unique la plus fluide possible pour Azure AD et en local. Les appareils professionnels ou scolaires doivent être configurés pour rejoindre Azure AD directement ou si l’organisation utilise la jonction de domaine AD locale, ces appareils doivent être [configurés pour s’inscrire automatiquement et silencieusement auprès d’Azure AD](/azure/active-directory/active-directory-conditional-access-automatic-device-registration-setup).

Pour les appareils Windows BYOD, les utilisateurs peuvent utiliser **ajouter un compte professionnel ou scolaire**. Notez que les utilisateurs du navigateur Google Chrome sur les appareils Windows 11 ou Windows 10 doivent [installer une extension](https://chrome.google.com/webstore/detail/windows-10-accounts/ppnbnpeolgkicgegkbkbjmhlideopiji?utm_source=chrome-app-launcher-info-dialog) pour bénéficier de la même expérience de connexion fluide que les utilisateurs de Microsoft Edge. En outre, si votre organisation dispose d’appareils Windows 8 ou 8.1 joints à un domaine, vous pouvez installer Microsoft Workplace Join pour les ordinateurs non Windows 10. [Téléchargez le package pour inscrire les appareils auprès](https://www.microsoft.com/download/details.aspx?id=53554) d’Azure AD.

### <a name="ios-devices"></a>Périphériques iOS

Nous vous recommandons d’installer [l’application Microsoft Authenticator](/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) sur les appareils utilisateur avant de déployer des stratégies d’accès conditionnel ou MFA. Au minimum, l’application doit être installée quand les utilisateurs sont invités à inscrire leur appareil auprès d’Azure AD en ajoutant un compte professionnel ou scolaire, ou lorsqu’ils installent l’application Intune portail d’entreprise pour inscrire leur appareil dans la gestion. Cela dépend de la stratégie d’accès conditionnel configurée.

### <a name="android-devices"></a>Périphériques Android

Nous recommandons aux utilisateurs d’installer [l’application Portail d'entreprise Intune](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal&hl=en) et [l’application Microsoft Authenticator](/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) avant le déploiement des stratégies d’accès conditionnel ou lorsque cela est nécessaire lors de certaines tentatives d’authentification. Une fois l’application installée, les utilisateurs peuvent être invités à s’inscrire auprès d’Azure AD ou à inscrire leurs appareils auprès d’Intune. Cela dépend de la stratégie d’accès conditionnel configurée.

Nous recommandons également que les appareils appartenant à l’organisation soient normalisés sur les OEM et les versions qui prennent en charge Android for Work ou Samsung Knox pour autoriser les comptes de messagerie, être gérés et protégés par Intune stratégie GPM.

### <a name="recommended-email-clients"></a>Clients de messagerie recommandés

Les clients de messagerie suivants prennent en charge l’authentification moderne et l’accès conditionnel.

|Plate-forme|Client|Version/Notes|
|---|---|---|
|**Windows**|Outlook|2019, 2016, 2013 <p> [Activer l’authentification moderne](../../admin/security-and-compliance/enable-modern-authentication.md) <p> [Mises à jour requises](https://support.office.com/article/Outlook-Updates-472c2322-23a4-4014-8f02-bbc09ad62213)|
|**iOS**|Outlook pour iOS|[La plus récente](https://itunes.apple.com/us/app/microsoft-outlook-email-and-calendar/id951937596?mt=8)|
|**Android**|Outlook pour Android|[La plus récente](https://play.google.com/store/apps/details?id=com.microsoft.office.outlook&hl=en)|
|**MacOS**|Outlook|2019 et 2016|
|**Linux**|Non prise en charge||

### <a name="recommended-client-platforms-when-securing-documents"></a>Plateformes clientes recommandées pour sécuriser des documents

Les clients suivants sont recommandés lorsqu’une stratégie de documents sécurisés a été appliquée.

|Plate-forme|Word/Excel/PowerPoint|OneNote|Application OneDrive|Application SharePoint|[Client de synchronisation OneDrive](/onedrive/enable-conditional-access)|
|---|---|---|---|---|---|
|Windows 11 ou Windows 10|Pris en charge|Pris en charge|S/O|S/O|Pris en charge|
|Windows 8.1|Pris en charge|Pris en charge|S/O|S/O|Pris en charge|
|Android|Pris en charge|Pris en charge|Pris en charge|Pris en charge|N/A|
|iOS|Pris en charge|Pris en charge|Pris en charge|Pris en charge|N/A|
|macOS|Pris en charge|Pris en charge|S/O|S/O|Non prise en charge|
|Linux|Non pris en charge|Non pris en charge|Non pris en charge|Non pris en charge|Non pris en charge|

### <a name="microsoft-365-client-support"></a>Prise en charge du client Microsoft 365

Pour plus d’informations sur le support client dans Microsoft 365, consultez les articles suivants :

- [Prise en charge des applications clientes Microsoft 365 - Accès conditionnel](../../enterprise/microsoft-365-client-support-conditional-access.md)
- [Prise en charge des applications clientes Microsoft 365 - Authentification multifacteur](../../enterprise/microsoft-365-client-support-multi-factor-authentication.md)

## <a name="protecting-administrator-accounts"></a>Protection des comptes d’administrateur

Pour Microsoft 365 E3 ou E5 ou avec des licences Azure AD Premium P1 ou P2 distinctes, vous pouvez exiger l’authentification multifacteur pour les comptes d’administrateur avec une stratégie d’accès conditionnel créée manuellement. Pour plus d’informations, consultez [Accès conditionnel : Exiger l’authentification multifacteur pour les administrateurs](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa) .

Pour les éditions de Microsoft 365 ou Office 365 qui ne prennent pas en charge l’accès conditionnel, vous pouvez activer [les paramètres de sécurité par défaut](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) pour exiger l’authentification multifacteur pour tous les comptes.

Voici quelques recommandations supplémentaires :

- Utilisez [Azure AD Privileged Identity Management](/azure/active-directory/privileged-identity-management/pim-getting-started) pour réduire le nombre de comptes d’administration persistants.
- [Utilisez la gestion des accès privilégiés](../../compliance/privileged-access-management-overview.md) pour protéger votre organisation contre les violations qui peuvent utiliser des comptes d’administration privilégiés existants avec un accès permanent aux données sensibles ou l’accès aux paramètres de configuration critiques.
- Créez et utilisez des comptes distincts auxquels des [rôles d’administrateur Microsoft 365 sont attribués](../../admin/add-users/about-admin-roles.md) *uniquement pour l’administration*. Les administrateurs doivent avoir leur propre compte d’utilisateur pour une utilisation non administrative régulière et utiliser uniquement un compte d’administration si nécessaire pour effectuer une tâche associée à leur rôle ou fonction de travail.
- Suivez [les bonnes pratiques](/azure/active-directory/admin-roles-best-practices) pour sécuriser les comptes privilégiés dans Azure AD.

## <a name="next-step"></a>Étape suivante

[![Étape 2 : Configurer les stratégies d’identité et d’accès conditionnel Confiance nulle courantes.](../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-2.png#lightbox)](identity-access-policies.md)

[Configurer les stratégies courantes d’identité Confiance nulle et d’accès aux appareils](identity-access-policies.md)
