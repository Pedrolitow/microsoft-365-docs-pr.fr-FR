---
title: Conditions préalables à l’implémentation des stratégies d’accès aux identités et aux appareils-Microsoft 365 pour les entreprises | Microsoft docs
description: Décrit les conditions préalables avant d’implémenter les stratégies et les configurations d’accès aux identités et aux appareils.
ms.author: josephd
author: JoeDavies-MSFT
manager: Laurawi
ms.prod: microsoft-365-enterprise
ms.topic: article
ms.date: 09/01/2020
f1.keywords:
- NOCSH
ms.reviewer: martincoetzer
ms.custom:
- it-pro
- goldenconfig
ms.collection:
- M365-identity-device-management
- M365-security-compliance
ms.openlocfilehash: a5a9e6f5d1eb5188a6370cda0c988d2f1dda84cc
ms.sourcegitcommit: cd17328baa58448214487e3e68c37590ab9fd08d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "48399637"
---
# <a name="prerequisite-work-for-implementing-identity-and-device-access-policies"></a>Tâches préalables à l’implémentation de stratégies d’accès aux identités et aux appareils

Cet article décrit les conditions préalables qui doivent être implémentées pour pouvoir déployer les stratégies d’identité et d’accès aux appareils recommandées. Cet article décrit également les configurations de client de plateforme par défaut recommandées pour fournir la meilleure expérience d’authentification unique (SSO) à vos utilisateurs, ainsi que les conditions préalables techniques pour l’accès conditionnel.

## <a name="prerequisites"></a>Conditions préalables

Avant d’implémenter les stratégies d’identité et d’accès aux appareils recommandées, votre organisation doit respecter plusieurs conditions préalables pour ces modèles d’identité et d’authentification pour Microsoft 365 et Office 365 :

- Cloud uniquement
- Authentification hybride avec authentification par hachage de mot de passe (hachage)
- Hybride avec authentification directe (directe)
- Fédération

Le tableau suivant détaille les fonctionnalités prérequises et leur configuration qui s’appliquent à tous les modèles d’identité, sauf indication contraire. 

| Configuration | Exceptions |
| :------------- | :-----------: |
|  [Configurez hachage](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization).  Cette option doit être activée pour détecter les informations d’identification divulguées et agir sur celles-ci pour un accès conditionnel basé sur les risques. **Remarque :** Ceci est obligatoire, que votre organisation utilise l’authentification fédérée ou non. | Cloud uniquement |
| [Activer l’authentification unique transparente](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso) pour authentifier automatiquement les utilisateurs lorsqu’ils se trouvent sur leur organisation périphériques connectés au réseau de votre organisation. | Cloud uniquement et fédéré  |
| [Configurer des réseaux nommés](https://docs.microsoft.com/azure/active-directory/active-directory-known-networks-azure-portal). Azure AD Identity Protection collecte et analyse toutes les données de session disponibles pour générer un indice de risque. Nous vous recommandons de spécifier les plages d’adresses IP publiques de votre organisation pour votre réseau dans la configuration de réseaux Azure AD appelée Networks. Le trafic provenant de ces plages reçoit une note de risque réduite et le trafic en provenance de l’extérieur de l’environnement de l’organisation reçoit un score de risque plus élevé. | |
|[Inscrivez tous les utilisateurs pour la réinitialisation du mot de passe en libre-service (SSPR) et l’authentification multifacteur (MFA)](https://docs.microsoft.com/azure/active-directory/authentication/concept-registration-mfa-sspr-converged). Nous vous recommandons d’enregistrer les utilisateurs pour l’authentification multifacteur Azure à l’avance. Azure AD Identity Protection utilise l’authentification multifacteur Azure pour effectuer une vérification de sécurité supplémentaire. De plus, pour l’expérience de connexion optimale, nous recommandons aux utilisateurs d’installer l' [application Microsoft Authenticator](https://docs.microsoft.com/azure/active-directory/user-help/microsoft-authenticator-app-how-to) et l’application portail d’entreprise Microsoft sur leurs appareils. Ceux-ci peuvent être installés à partir de l’App Store pour chaque plateforme. | |
| [Activer l’inscription automatique d’appareil pour les ordinateurs Windows associés à un domaine](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-automatic-device-registration-setup). L’accès conditionnel garantit que les appareils qui se connectent aux applications sont joints à un domaine ou conformes. Pour le prendre en charge sur les ordinateurs Windows, l’appareil doit être inscrit auprès d’Azure AD.  Cet article explique comment configurer l’inscription automatique des appareils. | Cloud uniquement |
| **Préparer votre équipe de support**. Mettez un plan en place pour les utilisateurs qui ne parviennent pas à effectuer l’authentification multifacteur. Il est possible de les ajouter à un groupe d’exclusion de stratégie ou d’enregistrer de nouvelles informations MFA pour ceux-ci. Avant d’effectuer l’une ou l’autre de ces modifications de sécurité, vous devez vous assurer que l’utilisateur réel effectue la demande. Exiger que les responsables des utilisateurs facilitent l’approbation est une étape efficace. | |  
| [Configurer la réécriture du mot de passe dans AD local](https://docs.microsoft.com/azure/active-directory/active-directory-passwords-getting-started). L’écriture différée de mot de passe permet à Azure AD de demander aux utilisateurs de modifier leurs mots de passe locaux lorsqu’une compromission de compte à haut risque est détectée. Vous pouvez activer cette fonctionnalité à l’aide d’Azure AD Connect de l’une des deux manières suivantes : activer l' **écriture différée du mot de passe** dans l’écran des fonctionnalités facultatives de l’Assistant Installation d’Azure ad Connect ou l’activer via Windows PowerShell. | Cloud uniquement |
| [Configurer la protection par mot de passe Azure ad](https://docs.microsoft.com/azure/active-directory/authentication/concept-password-ban-bad). La protection par mot de passe Azure AD détecte et bloque les mots de passe faibles connus et leurs variantes, et peut également bloquer d’autres termes faibles définis par votre organisation. Les listes générales par défaut de mots de passe interdits sont automatiquement appliquées à tous les utilisateurs d’un client Azure AD. Vous pouvez définir d’autres entrées dans une liste personnalisée de mots de passe interdits. Lorsque les utilisateurs modifient ou réinitialisent leurs mots de passe, ces listes sont vérifiées de façon à garantir l’utilisation de mots de passe forts. |  |
| [Activer la protection des identités Azure Active Directory](https://docs.microsoft.com/azure/active-directory/identity-protection/overview-identity-protection). Azure AD Identity Protection vous permet de détecter les vulnérabilités potentielles affectant les identités de votre organisation et de configurer une stratégie de correction automatisée sur un risque de connexion faible, moyen et élevé et un risque utilisateur.  | |
| **Activer l’authentification moderne** pour [Exchange Online](https://docs.microsoft.com/Exchange/clients-and-mobile-in-exchange-online/enable-or-disable-modern-authentication-in-exchange-online) et [Skype entreprise Online](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx). L’authentification moderne est une condition préalable à l’utilisation de l’authentification multifacteur. L’authentification moderne est activée par défaut pour les clients Office 2016 et 2019, SharePoint et OneDrive entreprise. |  |
|||

## <a name="recommended-client-configurations"></a>Configurations clientes recommandées
Cette section décrit les configurations de client de plateforme par défaut recommandées pour fournir la meilleure expérience SSO à vos utilisateurs, ainsi que les conditions préalables techniques pour l’accès conditionnel.

### <a name="windows-devices"></a>Appareils Windows
Nous vous recommandons d’utiliser Windows 10 (version 2004 ou ultérieure), car Azure est conçu pour offrir une expérience SSO sans complication possible pour les versions locale et Azure AD. Les appareils professionnels ou scolaires doivent être configurés pour rejoindre Azure AD directement ou si l’organisation utilise une jointure de domaine Active Directory sur site, ces appareils doivent être [configurés pour s’inscrire automatiquement à Azure ad](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-automatic-device-registration-setup).

Pour les appareils Windows BYOD, les utilisateurs peuvent utiliser **Ajouter un compte professionnel ou scolaire**. Notez que les utilisateurs du navigateur Google Chrome sur les appareils Windows 10 doivent [installer une extension](https://chrome.google.com/webstore/detail/windows-10-accounts/ppnbnpeolgkicgegkbkbjmhlideopiji?utm_source=chrome-app-launcher-info-dialog) pour obtenir la même expérience de connexion uniforme que les utilisateurs de Microsoft Edge. De plus, si votre organisation a des appareils Windows 8 ou 8,1, vous pouvez installer Microsoft Workplace join pour les ordinateurs autres que Windows 10. [Téléchargez le package pour enregistrer](https://www.microsoft.com/download/details.aspx?id=53554) les appareils auprès d’Azure ad.

### <a name="ios-devices"></a>Périphériques iOS
Nous vous recommandons d’installer l' [application Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) sur les appareils utilisateur avant de déployer des stratégies d’accès conditionnel ou mfa. Au minimum, l’application doit être installée lorsque les utilisateurs sont invités à inscrire leur appareil auprès d’Azure AD en ajoutant un compte professionnel ou scolaire, ou lorsqu’ils installent l’application portail d’entreprise Intune pour inscrire leur appareil dans la gestion. Cela dépend de la stratégie d’accès conditionnel configurée.

### <a name="android-devices"></a>Périphériques Android
Nous recommandons aux utilisateurs d’installer l' [application portail d’entreprise Intune](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal&hl=en) et l' [application Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) avant de déployer des stratégies d’accès conditionnel ou lorsque cela est requis lors de certaines tentatives d’authentification. Une fois l’application installée, les utilisateurs peuvent être invités à s’inscrire auprès d’Azure AD ou à inscrire leurs appareils auprès d’Intune. Cela dépend de la stratégie d’accès conditionnel configurée.

Nous recommandons également que les appareils appartenant à l’Organisation soient standardisés sur les OEM et les versions qui prennent en charge Android pour le travail ou Samsung Knox pour autoriser les comptes de messagerie, être gérés et protégés par la stratégie MDM de Intune.


### <a name="recommended-email-clients"></a>Clients de messagerie recommandés
Les clients de messagerie suivants prennent en charge l’authentification moderne et l’accès conditionnel. 

|Plate-forme|Client|Version/Notes|
|:-------|:-----|:------------|
|**Windows**|Outlook|2019, 2016, 2013 <BR> [Activer l’authentification moderne](https://docs.microsoft.com/microsoft-365/admin/security-and-compliance/enable-modern-authentication), les [mises à jour requises](https://support.office.com/article/Outlook-Updates-472c2322-23a4-4014-8f02-bbc09ad62213)|
|**iOS**|Outlook pour iOS|[La plus récente](https://itunes.apple.com/us/app/microsoft-outlook-email-and-calendar/id951937596?mt=8)|
|**Android**|Outlook pour Android|[La plus récente](https://play.google.com/store/apps/details?id=com.microsoft.office.outlook&hl=en)|
|**macOS**|Outlook|2019 et 2016|
|**Linux**|Non prise en charge||
|||

### <a name="recommended-client-platforms-when-securing-documents"></a>Plateformes clientes recommandées pour sécuriser des documents

Les clients suivants sont recommandés lorsqu’une stratégie de documents sécurisés a été appliquée.

|Plate-forme|Word/Excel/PowerPoint|OneNote|Application OneDrive|Application SharePoint|[Client de synchronisation OneDrive](https://docs.microsoft.com/onedrive/enable-conditional-access)|
|:-------|:-----|:------------|:-------|:-------------|:-----|
|Windows 8.1|Pris en charge|Pris en charge|N/A|N/A|Pris en charge|
|Windows 10|Pris en charge|Pris en charge|N/A|N/A|Pris en charge|
|Android|Pris en charge|Pris en charge|Pris en charge|Pris en charge|N/A|
|iOS|Pris en charge|Pris en charge|Pris en charge|Pris en charge|N/A|
|macOS|Pris en charge|Pris en charge|N/A|N/A|Non prise en charge|
|Linux|Non pris en charge|Non pris en charge|Non pris en charge|Non pris en charge|Non pris en charge|

### <a name="microsoft-365-client-support"></a>Prise en charge du client Microsoft 365

Pour plus d’informations sur la prise en charge des clients dans Microsoft 365, consultez les articles suivants :

- [Prise en charge des applications clientes Microsoft 365-accès conditionnel](../../enterprise/microsoft-365-client-support-conditional-access.md)
- [Prise en charge des applications clientes Microsoft 365-authentification moderne](../../enterprise/microsoft-365-client-support-modern-authentication.md)

## <a name="protecting-administrator-accounts"></a>Protection des comptes administrateurs

Pour Microsoft 365 E3 ou E5 ou avec des licences Azure AD Premium P1 ou P2 distinctes, vous pouvez exiger l’authentification MFA pour les comptes administrateur avec une stratégie d’accès conditionnel créée manuellement. Pour plus d’informations, consultez la rubrique [accès conditionnel : exiger l’authentification multifacteur pour les administrateurs](https://docs.microsoft.com/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa) .

Pour les éditions de Microsoft 365 ou Office 365 qui ne prennent pas en charge l’accès conditionnel, vous pouvez activer les [paramètres de sécurité par défaut](https://docs.microsoft.com/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) pour exiger l’authentification multifacteur pour tous les comptes.

Voici quelques recommandations supplémentaires :

- Utilisez [Azure ad Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/privileged-identity-management/pim-getting-started) pour réduire le nombre de comptes d’administration persistants. 
- [Utilisez la gestion des accès privilégiés](../../compliance/privileged-access-management-overview.md) pour protéger votre organisation contre les violations susceptibles d’utiliser des comptes d’administrateur privilégié existants avec un accès permanent aux données sensibles ou l’accès aux paramètres de configuration critiques. 
- Créez et utilisez des comptes distincts auxquels sont attribués des [rôles d’administrateur Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles) *uniquement pour l’administration*. Les administrateurs doivent avoir leur propre compte d’utilisateur pour une utilisation normale non administrative et n’utiliser un compte d’administrateur que si nécessaire pour effectuer une tâche associée à leur rôle ou fonction. 
- Suivez les [meilleures pratiques en matière](https://docs.microsoft.com/azure/active-directory/admin-roles-best-practices) de sécurisation des comptes privilégiés dans Azure ad.

## <a name="next-step"></a>Étape suivante

[![Étape 2 : configurer les stratégies d’accès conditionnel d’identité et d’accès courantes](../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-2.png)](identity-access-policies.md)

[Configurer les stratégies courantes d’identité et d’accès aux appareils](identity-access-policies.md)
