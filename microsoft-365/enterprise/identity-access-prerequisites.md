---
title: Travail requis pour l’implémentation des identités et des périphériques accéder aux stratégies - Microsoft 365 entreprise | Documents Microsoft
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
ms.openlocfilehash: e97b16b3520d500737e0b397e8e2a515ecac9b3f
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26867494"
---
# <a name="prerequisite-work-for-implementing-identity-and-device-access-policies"></a>Travail requis pour l’implémentation des stratégies d’accès identité et de périphérique

Cet article décrit les conditions préalables nécessaires mettre en œuvre avant de pouvoir déployer l’identité recommandée et les stratégies d’accès de périphérique. Cet article explique également les configurations de client de plateforme par défaut qu'il est recommandé de fournir la meilleure expérience d’authentification unique pour vos utilisateurs, ainsi que les conditions préalables techniques pour un accès conditionnel.


## <a name="prerequisites"></a>Conditions préalables

Avant d’implémenter les stratégies d’accès périphérique identité recommandée, il existe plusieurs conditions préalables que votre organisation doit respecter. Voir le tableau suivant pour les composants requis qui s’appliquent à votre environnement. 


| Configuration | Cloud uniquement | Active Directory avec la synchronisation de hachage de mot de passe |  Fédération avec AD FS |
| :------------- | :-----------: | :--------------: | :------------: |
|  [Configurer la synchronisation de hachage de mot de passe](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-implement-password-synchronization). Il doit être activé pour détecter les informations d’identification perdues et pour agir sur eux risque en accès conditionnel. **Remarque :** Cela est nécessaire, indépendamment de si votre organisation utilise l’authentification gérée, telles que l’authentification directe (PTA) ou l’authentification fédérée. |    | Oui | Oui |
| [Activer transparente de l’authentification unique](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso) pour vous connecter automatiquement les utilisateurs lorsqu’ils se trouvent sur leurs périphériques connectés à votre réseau d’entreprise de l’entreprise. |  | Oui |  |
| [Configure nommé réseaux](https://docs.microsoft.com/azure/active-directory/active-directory-known-networks-azure-portal). Protection d’identité AD Azure collecte et analyse de toutes les données de session disponibles pour générer un niveau de risque. Nous vous recommandons de que spécifier les plages IP publiques de votre organisation pour votre réseau dans Azure Active Directory nommé configuration des réseaux. Le trafic en provenance de ces plages reçoit un score de réduction des risques, afin que le trafic depuis l’extérieur de l’environnement d’entreprise est considéré comme du score de risque plus élevé. | Oui  | Oui | Oui |
|[Enregistrer tous les utilisateurs pour réinitialiser le mot de passe libre-service (SSPR) et l’authentification multifacteur (MFA)](https://docs.microsoft.com/azure/active-directory/authentication/concept-registration-mfa-sspr-converged). Nous vous recommandons de que vous inscrivez les utilisateurs pour Azure MFA à l’avance. Protection d’identité AD Azure utilise MFA Azure pour effectuer la vérification de sécurité supplémentaires. En outre, la meilleure expérience de connexion, nous recommandons que les utilisateurs installent l' [Application authentificateur de Microsoft](https://docs.microsoft.com/azure/active-directory/user-help/microsoft-authenticator-app-how-to) et l’application de portail d’entreprise Microsoft sur leurs appareils. Il peuvent être installés à partir du magasin d’application pour chaque plateforme. | Oui | Oui | Oui |
| [Activer l’inscription automatique des ordinateurs Windows joints à un domaine](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-automatic-device-registration-setup). L’accès conditionnel permet de vérifier que l’appareil qui se connecte au service est un appareil joint à un domaine ou conforme. Pour le prendre en charge sur les ordinateurs Windows, l’appareil doit être inscrit auprès d’Azure AD.  Cet article explique comment configurer l’inscription automatique des appareils. |   | Oui |  Oui |
| **Préparer votre équipe de support**. Mettez un plan en place pour les utilisateurs qui ne parviennent pas à effectuer l’authentification multifacteur. Il peut s’agir de les ajouter à un groupe d’exclusions de stratégie ou d’inscrire de nouvelles informations d’authentification multifacteur pour eux. Avant d’apporter l’une ou l’autre de ces modifications de sécurité sensibles, vous devez vous assurer que l’utilisateur réel effectue la demande. Exiger que les responsables des utilisateurs facilitent l’approbation est une étape efficace. | Oui | Oui | Oui |
| [Configurer la réécriture du mot de passe dans AD local](https://docs.microsoft.com/azure/active-directory/active-directory-passwords-getting-started). La réécriture du mot de passe permet à Azure AD d’exiger que les utilisateurs changent leurs mots de passe locaux en cas de détection d’un risque élevé de compte compromis. Vous pouvez activer cette fonctionnalité à l’aide d’Azure AD Connect de deux manières. Soit vous activez la réécriture du mot de passe dans l’écran des fonctionnalités facultatives de l’Assistant Installation d’Azure AD Connect, soit vous l’activez par le biais de Windows PowerShell. |   | Oui | Oui |
| [Activer la Protection d’identité Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/identity-protection/enable). Protection d’identité AD Azure vous permet de détecter les vulnérabilités potentielles affectant les identités de votre organisation et de configurer la stratégie de mise à jour automatique à risque faible, moyen et élevé connexion et les risques de l’utilisateur.  | Oui | Oui | Oui |
| **Activer l’authentification moderne** pour [Exchange Online](https://support.office.com/article/Enable-or-disable-modern-authentication-in-Exchange-Online-58018196-f918-49cd-8238-56f57f38d662) et [Skype pour Business Online](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx). Authentification moderne est une condition préalable à l’aide de l’authentification multifacteur (MFA). Authentification moderne est activée par défaut pour Office 2016 clients SharePoint Online et OneDrive for Business. | Oui | Oui | Oui |
|||||



## <a name="recommended-client-configurations"></a>Configurations clientes recommandées
Cette section décrit les configurations clientes de plateforme par défaut que nous vous recommandons pour fournir la meilleure expérience d’authentification unique à vos utilisateurs, ainsi que les prérequis techniques pour l’accès conditionnel.

### <a name="windows-devices"></a>Appareils Windows
Nous vous recommandons d’utiliser Windows 10 (version 1703 ou ultérieure), car Azure est conçu pour fournir l’expérience d’authentification unique la plus fluide possible à la fois en local et pour Azure AD. Les appareils professionnels ou scolaires doivent être configurés pour rejoindre Azure AD directement ou si l’organisation utilise une jonction de domaine AD locale, ces appareils doivent être [configurés pour s’inscrire automatiquement et de manière autonome auprès d’Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-automatic-device-registration-setup).

Pour les appareils Windows BYOD, les utilisateurs peuvent utiliser « Ajouter un compte professionnel ou scolaire ». Notez que les utilisateurs du navigateur Chrome sur Windows 10 doivent [installer une extension](https://chrome.google.com/webstore/detail/windows-10-accounts/ppnbnpeolgkicgegkbkbjmhlideopiji?utm_source=chrome-app-launcher-info-dialog) pour obtenir la même expérience de connexion fluide qu’avec Edge/Internet Explorer. De plus, si votre organisation a des appareils Windows 7 joints à un domaine, vous pouvez installer le package Microsoft Workplace Join pour les ordinateurs non-Windows 10 [pour inscrire](https://www.microsoft.com/download/details.aspx?id=53554) les appareils auprès d’Azure AD.

### <a name="ios-devices"></a>Périphériques iOS
Nous vous recommandons d’installer l' [application Microsoft authentificateur](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) sur les périphériques de l’utilisateur avant de déployer l’accès conditionnel ou stratégies MFA. Au minimum, l’application doit être installée lorsque les utilisateurs êtes invités à enregistrer leur appareil avec Azure AD en ajoutant un travail ou de l’école compte ou lors de l’installation de l’application de portail de société Intune d’inscrire leur appareil en gestion. Cela dépend de la stratégie d’accès conditionnel configuré.

### <a name="android-devices"></a>Appareils Android
Nous recommandons aux utilisateurs d’installer l’[application Portail d’entreprise Intune](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal&hl=en
) et l’application [Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) avant le déploiement des stratégies d’accès conditionnel ou quand ils y sont invités pendant certaines tentatives d’authentification. Une fois l’application installée, les utilisateurs peuvent être invités à s’inscrire auprès d’Azure AD ou à inscrire leurs appareils auprès d’Intune. Le choix dépend de la stratégie d’accès conditionnel configurée.

Nous recommandons également que les appareils d’entreprise soient normalisés sur les fabricants OEM et les versions qui prennent en charge Android for Work ou Samsung Knox pour autoriser les comptes de messagerie à être gérés et protégés par une stratégie de gestion des appareils mobiles (MDM) Intune.


### <a name="recommended-email-clients"></a>Clients de messagerie recommandés
Les clients de messagerie suivants prennent en charge l’authentification moderne et accès conditionnel. 

|Plate-forme|Client|Version/Notes|
|:-------|:-----|:------------|
|**Windows**|Outlook|2016, 2013 [Activer l’authentification moderne](https://support.office.com/article/Enable-Modern-Authentication-for-Office-2013-on-Windows-devices-7dc1c01a-090f-4971-9677-f1b192d6c910), [Mises à jour nécessaires](https://support.office.com/article/Outlook-Updates-472c2322-23a4-4014-8f02-bbc09ad62213)|
|**iOS**|Outlook pour iOS|[La plus récente](https://itunes.apple.com/us/app/microsoft-outlook-email-and-calendar/id951937596?mt=8)|
|**Android**|Outlook pour Android|[La plus récente](https://play.google.com/store/apps/details?id=com.microsoft.office.outlook&hl=en)|
|**Mac OS**|Outlook|2016|
|**Linux**|Non prise en charge||
|||


### <a name="recommended-client-platforms-when-securing-documents"></a>Plateformes clientes recommandées pour sécuriser des documents
Les clients suivants sont recommandés quand une stratégie de sécurisation des documents a été appliquée.

|Plate-forme|Word/Excel/PowerPoint|OneNote|Application OneDrive|Application SharePoint|Client de synchronisation OneDrive|
|:-------|:-----|:------------|:-------|:-------------|:-----|
|Windows 7|Pris en charge|Pris en charge|N/A|N/A|Préversion<sup>*</sup>|
|Windows 8.1|Pris en charge|Pris en charge|N/A|N/A|Préversion<sup>*</sup>|
|Windows 10|Pris en charge|Pris en charge|N/A|N/A|Préversion<sup>*</sup>|
|Windows Phone 10|Non prise en charge|Non pris en charge|Non pris en charge|Non pris en charge|Non pris en charge|
|Android|Pris en charge|Pris en charge|Pris en charge|Pris en charge|N/A|
|iOS|Pris en charge|Pris en charge|Pris en charge|Pris en charge|N/A|
|Mac OS|Préversion publique|Préversion publique|N/A|N/A|Non prise en charge|
|Linux|Non prise en charge|Non pris en charge|Non pris en charge|Non pris en charge|Non pris en charge|

<sup>*</sup>Pour plus d’informations sur l’utilisation d’accès conditionnel avec le [Client de synchronisation OneDrive](https://support.office.com/article/Azure-Active-Directory-conditional-access-with-the-OneDrive-sync-client-on-Windows-028d73d7-4b86-4ee0-8fb7-9a209434b04e).

### <a name="office-365-client-support"></a>Prise en charge de client Office 365
Pour plus d’informations sur la prise en charge du client Office 365, voir les articles suivants :
- [Prise en charge des applications Office 365 Client - accès conditionnel](https://docs.microsoft.com/en-us/office365/enterprise/office-365-client-support-conditional-access)
- [Prise en charge des applications Office 365 Client - gestion des applications mobiles](https://docs.microsoft.com/en-us/office365/enterprise/office-365-client-support-mobile-application-management)
- [Support d’application Client Office 365 - authentification moderne](https://docs.microsoft.com/en-us/office365/enterprise/office-365-client-support-modern-authentication)

## <a name="protecting-administrator-accounts"></a>Protection des comptes d’administrateur
Azure Active Directory offre un moyen simple pour commencer la protection de l’accès administrateur avec une stratégie d’accès conditionnel préconfigurée à. Dans Azure AD, accédez à la lame accès conditionnel et recherchez cette stratégie — **stratégie de base : nécessitent un MFA pour les administrateurs**. Cliquez sur cette stratégie et sélectionnez **stratégie utiliser immédiatement**. 

Cette stratégie nécessite MFA pour les rôles suivants :
- Administrateurs globaux
- Administrateurs SharePoint
- Administrateurs Exchange
- Administrateurs d’accès conditionnel
- Administrateurs de la sécurité

Pour plus d’informations, voir [stratégie de sécurité de base pour les comptes d’administration d’Azure AD](https://cloudblogs.microsoft.com/enterprisemobility/2018/06/22/baseline-security-policy-for-azure-ad-admin-accounts-in-public-preview/).

Recommandations supplémentaires sont les suivantes :
- Gestion des identités Azure AD privilégié permet de réduire le nombre de comptes d’administration permanentes. Voir [Démarrer à l’aide de GIP](https://docs.microsoft.com/en-us/azure/active-directory/privileged-identity-management/pim-getting-started). 
- [Gestion des accès privilégié dans Office 365](https://docs.microsoft.com/en-us/office365/securitycompliance/privileged-access-management-overview) pour protéger votre organisation contre les violations qui peuvent utiliser existant privilégié comptes d’administration avec accès permanent à des données sensibles ou l’accès aux paramètres de configuration critique. 
- Utiliser des comptes d’administrateur Office 365 uniquement pour l’administration. Administrateurs doivent avoir un autre utilisateur de compte pour une utilisation régulière non administratifs et uniquement utiliser leur compte d’administration lorsque cela est nécessaire pour effectuer une tâche associée à leur fonction. Rôles [d’administrateur Office 365](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d) privilèges nettement plus aux services Office 365.
- Suivez les meilleures pratiques pour la sécurisation des comptes privilégiés dans Azure Active Directory comme décrit dans cet [article](https://docs.microsoft.com/azure/active-directory/admin-roles-best-practices).

## <a name="next-steps"></a>Étapes suivantes

[Configurer l’identité commune et les stratégies d’accès de périphérique](identity-access-policies.md)

