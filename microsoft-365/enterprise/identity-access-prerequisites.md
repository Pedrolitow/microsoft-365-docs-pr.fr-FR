---
title: Conditions requises pour l'implémentation de stratégies d'accès aux identités et aux appareils-Microsoft 365 Enterprise | Microsoft docs
description: Décrit les recommandations de Microsoft liées à l’application de stratégies et de configurations de l’accès aux identités et aux appareils.
author: BrendaCarter
manager: Laurawi
ms.prod: microsoft-365-enterprise
ms.topic: article
ms.author: bcarter
ms.reviewer: martincoetzer
ms.custom:
- it-pro
- goldenconfig
ms.collection:
- M365-identity-device-management
- M365-security-compliance
ms.openlocfilehash: 2bb13d2af70b90f8c98a4bb902156f840e7f57f1
ms.sourcegitcommit: 81273a9df49647286235b187fa2213c5ec7e8b62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "32289005"
---
# <a name="prerequisite-work-for-implementing-identity-and-device-access-policies"></a>Tâches préalables à l'implémentation de stratégies d'accès aux identités et aux appareils

Cet article décrit les conditions préalables qui doivent être implémentées pour pouvoir déployer les stratégies d'identité et d'accès aux appareils recommandées. Cet article décrit également les configurations de client de plateforme par défaut recommandées pour fournir la meilleure expérience SSO à vos utilisateurs, ainsi que les conditions préalables techniques pour l'accès conditionnel.


## <a name="prerequisites"></a>Conditions préalables

Avant d'implémenter les stratégies d'identité et d'accès aux appareils recommandées, votre organisation doit répondre à plusieurs conditions préalables. Le tableau suivant détaille les éléments prérequis qui s'appliquent à votre environnement. 


| Configuration | Cloud uniquement | Active Directory avec synchronisation de hachage de mot de passe |  Authentification directe |  Fédération avec AD FS |
| :------------- | :-----------: | :--------------: | :------------: | :------------: |
|  ConFigurez la [synchronisation de hachage de mot de passe](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-implement-password-synchronization). Cette option doit être activée pour détecter les informations d'identification divulguées et agir sur celles-ci pour un accès conditionnel basé sur les risques. **Remarque:** Ceci est obligatoire, que votre organisation utilise ou non l'authentification gérée, comme l'authentification directe (directe) ou l'authentification fédérée. |    | Oui | Oui | Oui |
| [Activer l'authentification unique transparente](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso) pour authentifier automatiquement les utilisateurs lorsqu'ils se trouvent sur leurs appareils d'entreprise connectés à votre réseau d'entreprise. |  | Oui | Oui |  |
| [Configurer des réseaux nommés](https://docs.microsoft.com/azure/active-directory/active-directory-known-networks-azure-portal). Azure AD Identity Protection collecte et analyse toutes les données de session disponibles pour générer un indice de risque. Nous vous recommandons de spécifier les plages d'adresses IP publiques de votre organisation pour votre réseau dans la configuration de réseaux Azure AD appelée Networks. Le trafic provenant de ces plages reçoit une note de risque réduite et le trafic en provenance de l'extérieur de l'environnement d'entreprise reçoit un score de risque plus élevé. | Oui  | Oui | Oui | Oui |
|[Inscrivez tous les utilisateurs pour la réinitialisation du mot de passe en libre-service (SSPR) et l'authentification multifacteur (MFA)](https://docs.microsoft.com/azure/active-directory/authentication/concept-registration-mfa-sspr-converged). Nous vous recommandons d'enregistrer les utilisateurs pour Azure MFA à l'avance. Azure AD Identity Protection utilise l’authentification multifacteur Azure pour effectuer une vérification de sécurité supplémentaire. De plus, pour l'expérience de connexion optimale, nous recommandons aux utilisateurs d'installer l' [application Microsoft Authenticator](https://docs.microsoft.com/azure/active-directory/user-help/microsoft-authenticator-app-how-to) et l'application portail d'entreprise Microsoft sur leurs appareils. Ceux-ci peuvent être installés à partir de l'App Store pour chaque plateforme. | Oui | Oui | Oui | Oui |
| [Activer l'inscription automatique d'appareil pour les ordinateurs Windows associés à un domaine](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-automatic-device-registration-setup). L'accès conditionnel garantit que les appareils qui se connectent aux applications sont joints à un domaine ou conformes. Pour le prendre en charge sur les ordinateurs Windows, l’appareil doit être inscrit auprès d’Azure AD.  Cet article explique comment configurer l’inscription automatique des appareils. |   | Oui |  Oui |  Oui |
| **Préparer votre équipe de support**. Mettez un plan en place pour les utilisateurs qui ne parviennent pas à effectuer l’authentification multifacteur. Il est possible de les ajouter à un groupe d'exclusion de stratégie ou d'enregistrer de nouvelles informations MFA pour ceux-ci. Avant d'effectuer l'une ou l'autre de ces modifications de sécurité, vous devez vous assurer que l'utilisateur réel effectue la demande. Exiger que les responsables des utilisateurs facilitent l’approbation est une étape efficace. | Oui | Oui | Oui | Oui |  
| [Configurer la réécriture du mot de passe dans AD local](https://docs.microsoft.com/azure/active-directory/active-directory-passwords-getting-started). L'écriture différée de mot de passe permet à Azure AD de demander aux utilisateurs de modifier leurs mots de passe locaux lorsqu'une compromission de compte à haut risque est détectée. Vous pouvez activer cette fonctionnalité à l'aide d'Azure AD Connect de l'une des deux manières suivantes: activer l' **écriture différée du mot de passe** dans l'écran des fonctionnalités facultatives de l'Assistant Installation d'Azure ad Connect ou l'activer via Windows PowerShell. |   | Oui | Oui | Oui |
| [Activer la protection des identités Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/identity-protection/enable). Azure AD Identity Protection vous permet de détecter les vulnérabilités potentielles affectant les identités de votre organisation et de configurer une stratégie de correction automatisée sur un risque de connexion faible, moyen et élevé et un risque utilisateur.  | Oui | Oui | Oui | Oui |
| **Activer l'authentification moderne** pour [Exchange Online](https://support.office.com/article/Enable-or-disable-modern-authentication-in-Exchange-Online-58018196-f918-49cd-8238-56f57f38d662) et [Skype entreprise Online](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx). L'authentification moderne est une condition préalable à l'utilisation de l'authentification multifacteur (MFA). L'authentification moderne est activée par défaut pour les clients Office 2016, SharePoint Online et OneDrive entreprise. | Oui | Oui | Oui | Oui |
||||||



## <a name="recommended-client-configurations"></a>Configurations clientes recommandées
Cette section décrit les configurations de client de plateforme par défaut recommandées pour fournir la meilleure expérience SSO à vos utilisateurs, ainsi que les conditions préalables techniques pour l'accès conditionnel.

### <a name="windows-devices"></a>Appareils Windows
Nous vous recommandons d’utiliser Windows 10 (version 1703 ou ultérieure), car Azure est conçu pour fournir l’expérience d’authentification unique la plus fluide possible à la fois en local et pour Azure AD. Les appareils professionnels ou scolaires doivent être configurés pour rejoindre Azure AD directement ou si l'organisation utilise une jointure de domaine Active Directory sur site, ces appareils doivent être [configurés pour s'inscrire automatiquement à Azure ad](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-automatic-device-registration-setup).

Pour les appareils Windows BYOD, les utilisateurs peuvent utiliser **Ajouter un compte professionnel ou scolaire**. Notez que les utilisateurs de navigateur chromé sur Windows 10 doivent [installer une extension](https://chrome.google.com/webstore/detail/windows-10-accounts/ppnbnpeolgkicgegkbkbjmhlideopiji?utm_source=chrome-app-launcher-info-dialog) pour obtenir la même expérience de connexion uniforme que les utilisateurs Edge/IE. De plus, si votre organisation a des appareils Windows 7 associés à un domaine, vous pouvez installer Microsoft Workplace join pour les ordinateurs autres que Windows 10 [Téléchargez le package pour enregistrer](https://www.microsoft.com/download/details.aspx?id=53554) les appareils auprès d'Azure ad.

### <a name="ios-devices"></a>Périphériques iOS
Nous vous recommandons d’installer l’[application Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) sur les appareils des utilisateurs avant de déployer l’accès conditionnel ou des stratégies d’authentification multifacteur. Au minimum, l'application doit être installée lorsque les utilisateurs sont invités à inscrire leur appareil auprès d'Azure AD en ajoutant un compte professionnel ou scolaire, ou lorsqu'ils installent l'application portail d'entreprise Intune pour inscrire leur appareil dans la gestion. Le choix dépend de la stratégie d’accès conditionnel configurée.

### <a name="android-devices"></a>Périphériques Android
Nous recommandons aux utilisateurs d’installer l’[application Portail d’entreprise Intune](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal&hl=en) et l’application [Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) avant le déploiement des stratégies d’accès conditionnel ou quand ils y sont invités pendant certaines tentatives d’authentification. Une fois l’application installée, les utilisateurs peuvent être invités à s’inscrire auprès d’Azure AD ou à inscrire leurs appareils auprès d’Intune. Le choix dépend de la stratégie d’accès conditionnel configurée.

Il est également recommandé que les appareils appartenant à une entreprise (COD) soient standardisés sur les OEM et les versions qui prennent en charge Android pour le travail ou Samsung Knox pour autoriser les comptes de messagerie, être gérés et protégés par la stratégie MDM de Intune.


### <a name="recommended-email-clients"></a>Clients de messagerie recommandés
Les clients de messagerie suivants prennent en charge l'authentification moderne et l'accès conditionnel. 

|Plateforme|Client|Version/Notes|
|:-------|:-----|:------------|
|**Windows**|Outlook|2016, 2013 [activer l'authentification moderne](https://support.office.com/article/Enable-Modern-Authentication-for-Office-2013-on-Windows-devices-7dc1c01a-090f-4971-9677-f1b192d6c910), les [mises à jour requises](https://support.office.com/article/Outlook-Updates-472c2322-23a4-4014-8f02-bbc09ad62213)|
|**iOS**|Outlook pour iOS|[La plus récente](https://itunes.apple.com/us/app/microsoft-outlook-email-and-calendar/id951937596?mt=8)|
|**Android**|Outlook pour Android|[La plus récente](https://play.google.com/store/apps/details?id=com.microsoft.office.outlook&hl=en)|
|**OS**|Outlook|2016|
|**Linux**|Non pris en charge||
|||


### <a name="recommended-client-platforms-when-securing-documents"></a>Plateformes clientes recommandées pour sécuriser des documents
Les clients suivants sont recommandés lorsqu'une stratégie de documents sécurisés a été appliquée.

|Plate-forme|Word/Excel/PowerPoint|OneNote|Application OneDrive|Application SharePoint|Client de synchronisation OneDrive|
|:-------|:-----|:------------|:-------|:-------------|:-----|
|Windows 7|Pris en charge|Pris en charge|N/D|S/O|Préversion<sup>*</sup>|
|Windows 8.1|Pris en charge|Pris en charge|N/D|S/O|Préversion<sup>*</sup>|
|Windows 10|Pris en charge|Pris en charge|N/D|S/O|Préversion<sup>*</sup>|
|Windows Phone 10|Non pris en charge|Non pris en charge|Non pris en charge|Non pris en charge|Non pris en charge|
|Android|Pris en charge|Pris en charge|Pris en charge|Pris en charge|S/O|
|iOS|Pris en charge|Pris en charge|Pris en charge|Pris en charge|S/O|
|OS|Préversion publique|Préversion publique|N/D|S/O|Non prise en charge|
|Linux|Non pris en charge|Non pris en charge|Non pris en charge|Non pris en charge|Non pris en charge|

<sup>*</sup>En savoir plus sur l'utilisation de l'accès conditionnel avec le [client de synchronisation OneDrive](https://support.office.com/article/Azure-Active-Directory-conditional-access-with-the-OneDrive-sync-client-on-Windows-028d73d7-4b86-4ee0-8fb7-9a209434b04e).

### <a name="office-365-client-support"></a>Prise en charge de client Office 365
Pour plus d'informations sur la prise en charge du client Office 365, consultez les articles suivants:
- [Prise en charge de l'application cliente Office 365-accès conditionnel](https://docs.microsoft.com/en-us/office365/enterprise/office-365-client-support-conditional-access)
- [Prise en charge de l'application cliente Office 365-gestion des applications mobiles](https://docs.microsoft.com/en-us/office365/enterprise/office-365-client-support-mobile-application-management)
- [Prise en charge des applications clientes Office 365-authentification moderne](https://docs.microsoft.com/en-us/office365/enterprise/office-365-client-support-modern-authentication)

## <a name="protecting-administrator-accounts"></a>Protection des comptes administrateurs
Azure AD offre un moyen simple de commencer la protection de l'accès administrateur avec une stratégie d'accès conditionnel préconfigurée. Dans Azure AD, accédez à **accès conditionnel** et recherchez cette stratégie, **stratégie de base: exiger l'authentification multifacteur pour les administrateurs**. Sélectionnez cette stratégie, puis sélectionnez **utiliser la stratégie immédiatement**. 

Cette stratégie requiert l'authentification multiFACTEUR pour les rôles suivants:
- Administrateurs globaux
- Administrateurs SharePoint
- Administrateurs Exchange
- Administrateurs d'accès conditionnel
- Administrateurs de la sécurité

Pour plus d'informations, consultez la rubrique [stratégie de sécurité de base pour les comptes d'administrateur Azure ad](https://cloudblogs.microsoft.com/enterprisemobility/2018/06/22/baseline-security-policy-for-azure-ad-admin-accounts-in-public-preview/).

Les recommandations supplémentaires sont les suivantes:
- Utilisez Azure AD Privileged Identity Management pour réduire le nombre de comptes d’administrateur permanents. Voir [commencer à utiliser PIM](https://docs.microsoft.com/en-us/azure/active-directory/privileged-identity-management/pim-getting-started). 
- [Utilisez la gestion des accès privilégiés dans Office 365](https://docs.microsoft.com/en-us/office365/securitycompliance/privileged-access-management-overview) pour protéger votre organisation contre les violations susceptibles d'utiliser des comptes d'administrateur privilégié existants avec un accès permanent aux données sensibles ou l'accès aux paramètres de configuration critiques. 
- Utiliser les comptes administrateur uniquement pour l'administration. Les administrateurs doivent disposer d'un compte d'utilisateur distinct pour une utilisation normale non administrative et n'utiliser leur compte d'administrateur que si nécessaire pour effectuer une tâche associée à leur fonction. Les rôles d' [administrateur office 365](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d) ont beaucoup plus de privilèges que les services Office 365.
- Suivez les meilleures pratiques en matière de sécurisation des comptes privilégiés dans Azure AD, comme décrit dans cet [article](https://docs.microsoft.com/azure/active-directory/admin-roles-best-practices).

## <a name="next-steps"></a>Étapes suivantes

[Configurer les stratégies courantes d'identité et d'accès aux appareils](identity-access-policies.md)

