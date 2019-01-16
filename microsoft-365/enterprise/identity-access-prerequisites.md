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
ms.openlocfilehash: ee517e774e0606c62efdc67d869ad0aca5a41640
ms.sourcegitcommit: e491c4713115610cbe13d2fbd0d65e1a41c34d62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "26867494"
---
# <a name="prerequisite-work-for-implementing-identity-and-device-access-policies"></a>Travail requis pour l’implémentation des stratégies d’accès identité et de périphérique

Cet article décrit les conditions préalables qui doivent être mises en œuvre avant de pouvoir déployer l’identité recommandée et les stratégies d’accès de périphérique. Cet article explique également les configurations de client de plateforme par défaut qu'il est recommandé de fournir la meilleure expérience d’authentification unique pour vos utilisateurs, ainsi que les conditions techniques préalables pour un accès conditionnel.


## <a name="prerequisites"></a>Conditions préalables

Avant d’implémenter les stratégies d’accès périphérique identité recommandée, il existe plusieurs conditions préalables que votre organisation doit respecter. Le tableau suivant détaille les composants requis qui s’appliquent à votre environnement. 


| Configuration | Cloud uniquement | Active Directory avec la synchronisation de hachage de mot de passe |  Authentification directe |  Fédération avec AD FS |
| :------------- | :-----------: | :--------------: | :------------: | :------------: |
|  [Configurer la synchronisation de hachage de mot de passe](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-implement-password-synchronization). Il doit être activé pour détecter des informations d’identification perdues et agir sur eux pour un accès conditionnel en fonction du risque. **Remarque :** Il est nécessaire que votre organisation utilise l’authentification gérée, telles que l’authentification directe (PTA) ou l’authentification fédérée. |    | Oui | Oui | Oui |
| [Activer l’authentification unique transparente](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso) pour vous connecter automatiquement les utilisateurs lorsqu’ils se trouvent sur leurs périphériques connectés à votre réseau d’entreprise de l’entreprise. |  | Oui | Oui |  |
| [Configure nommé réseaux](https://docs.microsoft.com/azure/active-directory/active-directory-known-networks-azure-portal). Protection d’identité AD Azure collecte et analyse de toutes les données de session disponibles pour générer un niveau de risque. Nous vous recommandons de que spécifier les plages IP publiques de votre organisation pour votre réseau dans Azure Active Directory nommé configuration des réseaux. Le trafic en provenance de ces plages reçoit un score de réduction des risques et le trafic à partir de l’extérieur de l’environnement d’entreprise reçoit un score de risque plus élevé. | Oui  | Oui | Oui | Oui |
|[Enregistrer tous les utilisateurs pour réinitialiser le mot de passe libre-service (SSPR) et l’authentification multifacteur (MFA)](https://docs.microsoft.com/azure/active-directory/authentication/concept-registration-mfa-sspr-converged). Nous vous recommandons de que vous inscrivez les utilisateurs pour Azure MFA à l’avance. Protection d’identité AD Azure utilise MFA Azure pour effectuer la vérification de sécurité supplémentaires. En outre, la meilleure expérience de connexion, nous recommandons que les utilisateurs installent l' [application Microsoft authentificateur](https://docs.microsoft.com/azure/active-directory/user-help/microsoft-authenticator-app-how-to) et l’application de portail d’entreprise Microsoft sur leurs appareils. Il peuvent être installés à partir du magasin d’application pour chaque plateforme. | Oui | Oui | Oui | Oui |
| [Activer l’enregistrement automatique des ordinateurs Windows joints au domaine](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-automatic-device-registration-setup). Accès conditionnel vérifiera périphériques qui se connectent aux applications sont conformes ou à un domaine. Pour ce faire sur les ordinateurs Windows, le périphérique doit être enregistré avec Azure AD.  Cet article explique comment configurer l’enregistrement automatiques des périphériques. |   | Oui |  Oui |  Oui |
| **Préparer votre équipe de support technique**. Disposer d’un plan en place pour les utilisateurs qui ne peuvent pas effectuer MFA. Cela peut en les ajoutant à un groupe d’exclusion de stratégie, ou enregistrement de nouvelles informations MFA pour les. Avant d’effectuer une de ces modifications liées à la sécurité, vous devez vous assurer que l’utilisateur réel qui effectue la demande. Nécessitant des responsables des utilisateurs à l’aide de l’approbation est une étape efficace. | Oui | Oui | Oui | Oui |  
| [Écriture différée de mot de passe configurer pour AD sur site](https://docs.microsoft.com/azure/active-directory/active-directory-passwords-getting-started). Écriture différée de mot de passe permet d’Azure AD exiger que les utilisateurs modifier leur mot de passe local lorsqu’une compromission d’un compte à haut risque est détectée. Vous pouvez activer cette fonctionnalité à l’aide d’Azure AD Connect de deux façons : activer **l’Écriture différée de mot de passe** dans l’écran Options de l’Assistant d’installation Azure AD se connecter, soit l’activer via Windows PowerShell. |   | Oui | Oui | Oui |
| [Activer la Protection d’identité Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/identity-protection/enable). Protection d’identité AD Azure vous permet de détecter les vulnérabilités potentielles affectant les identités de votre organisation et de configurer une stratégie de mise à jour automatique à risque faible, moyen et élevé connexion et les risques de l’utilisateur.  | Oui | Oui | Oui | Oui |
| **Activer l’authentification moderne** pour [Exchange Online](https://support.office.com/article/Enable-or-disable-modern-authentication-in-Exchange-Online-58018196-f918-49cd-8238-56f57f38d662) et [Skype pour Business Online](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx). Authentification moderne est une condition préalable à l’aide de l’authentification multifacteur (MFA). Authentification moderne est activée par défaut pour Office 2016 clients SharePoint Online et OneDrive for Business. | Oui | Oui | Oui | Oui |
||||||



## <a name="recommended-client-configurations"></a>Configurations clientes recommandées
Cette section décrit les configurations de client de plateforme par défaut qu'il est recommandé de fournir la meilleure expérience d’authentification unique pour vos utilisateurs, ainsi que les conditions techniques préalables pour un accès conditionnel.

### <a name="windows-devices"></a>Appareils Windows
Nous vous recommandons des 10 Windows (1703 ou version ultérieure), comme Azure est conçu pour fournir l’authentification unique plus lissé expérience possible sur site et Azure AD. Travail ou émis par l’établissement des périphériques doivent être configurés pour participer Azure AD directement ou si les utilisations de l’organisation locale jonction de domaine Active Directory, ces appareils doivent être [configuré pour être automatiquement et en mode silencieux inscrire avec Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-automatic-device-registration-setup).

Pour les appareils BYOD Windows, les utilisateurs peuvent utiliser **Ajouter travail ou de l’école compte**. Notez que les utilisateurs de navigateur Chrome sur Windows 10 besoin pour [installer une extension](https://chrome.google.com/webstore/detail/windows-10-accounts/ppnbnpeolgkicgegkbkbjmhlideopiji?utm_source=chrome-app-launcher-info-dialog) obtenir la même en toute transparence expérience de connexion en tant qu’utilisateurs Edge/Internet Explorer. En outre, si votre organisation dispose de périphériques de Windows 7 à un domaine, vous pouvez installer joindre d’espace de travail Microsoft pour les ordinateurs non Windows 10 [Télécharger le package pour inscrire](https://www.microsoft.com/download/details.aspx?id=53554) les périphériques avec Azure AD.

### <a name="ios-devices"></a>Périphériques iOS
Nous vous recommandons d’installer l' [application Microsoft authentificateur](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) sur les périphériques de l’utilisateur avant de déployer l’accès conditionnel ou stratégies MFA. Au minimum, l’application doit être installée lorsque les utilisateurs sont invités à enregistrer leur appareil avec Azure AD en ajoutant un bureau ou l’école compte ou lors de l’installation de l’application de portail de société Intune d’inscrire leur appareil en gestion. Cela dépend de la stratégie d’accès conditionnel configuré.

### <a name="android-devices"></a>Appareils Android
Nous recommandons aux utilisateurs d’installer l’[application Portail d’entreprise Intune](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal&hl=en) et l’application [Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) avant le déploiement des stratégies d’accès conditionnel ou quand ils y sont invités pendant certaines tentatives d’authentification. Une fois l’application installée, les utilisateurs peuvent être invités à s’inscrire auprès d’Azure AD ou à inscrire leurs appareils auprès d’Intune. Le choix dépend de la stratégie d’accès conditionnel configurée.

Nous vous recommandons également que les périphériques appartenant à l’entreprise (CR) sont normalisés sur les fabricants OEM et les versions qui prennent en charge Android pour le travail ou Samsung Knox à autoriser les comptes de messagerie, gérer et protégé par la stratégie Intune MDM.


### <a name="recommended-email-clients"></a>Clients de messagerie recommandés
Les clients de messagerie suivants prennent en charge l’authentification moderne et accès conditionnel. 

|Plate-forme|Client|Version/Notes|
|:-------|:-----|:------------|
|**Windows**|Outlook|2016, 2013 [Activer l’authentification moderne](https://support.office.com/article/Enable-Modern-Authentication-for-Office-2013-on-Windows-devices-7dc1c01a-090f-4971-9677-f1b192d6c910), [mises à jour requises](https://support.office.com/article/Outlook-Updates-472c2322-23a4-4014-8f02-bbc09ad62213)|
|**iOS**|Outlook pour iOS|[La plus récente](https://itunes.apple.com/us/app/microsoft-outlook-email-and-calendar/id951937596?mt=8)|
|**Android**|Outlook pour Android|[La plus récente](https://play.google.com/store/apps/details?id=com.microsoft.office.outlook&hl=en)|
|**Mac OS**|Outlook|2016|
|**Linux**|Non prise en charge||
|||


### <a name="recommended-client-platforms-when-securing-documents"></a>Plateformes clientes recommandées pour sécuriser des documents
Les clients suivants sont recommandés lorsqu’une stratégie de documents sécurisés a été appliquée.

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

<sup>*</sup>Pour plus d’informations sur l’utilisation d’accès conditionnel avec le [client de synchronisation OneDrive](https://support.office.com/article/Azure-Active-Directory-conditional-access-with-the-OneDrive-sync-client-on-Windows-028d73d7-4b86-4ee0-8fb7-9a209434b04e).

### <a name="office-365-client-support"></a>Prise en charge de client Office 365
Pour plus d’informations sur la prise en charge du client Office 365, voir les articles suivants :
- [Prise en charge des applications Office 365 Client - accès conditionnel](https://docs.microsoft.com/en-us/office365/enterprise/office-365-client-support-conditional-access)
- [Prise en charge des applications Office 365 Client - gestion des applications mobiles](https://docs.microsoft.com/en-us/office365/enterprise/office-365-client-support-mobile-application-management)
- [Support d’application Client Office 365 - authentification moderne](https://docs.microsoft.com/en-us/office365/enterprise/office-365-client-support-modern-authentication)

## <a name="protecting-administrator-accounts"></a>Protection des comptes d’administrateur
Azure AD offre un moyen simple pour commencer la protection de l’accès administrateur avec une stratégie d’accès conditionnel préconfigurée à. Dans Azure AD, accédez à **accès conditionnel** et recherchez cette stratégie — **stratégie de base : nécessitent un MFA pour les administrateurs**. Activez cette stratégie, puis sélectionnez **stratégie utiliser immédiatement**. 

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
- Utiliser des comptes d’administrateur Office 365 uniquement pour l’administration. Administrateurs doivent avoir un autre utilisateur de compte pour une utilisation régulière non administratifs et uniquement utiliser leur compte d’administration lorsque cela est nécessaire pour effectuer une tâche associée à leur fonction. Rôles [d’administrateur Office 365](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d) privilèges nettement plus que les services Office 365.
- Suivez les meilleures pratiques pour la sécurisation des comptes privilégiés dans Azure Active Directory comme décrit dans cet [article](https://docs.microsoft.com/azure/active-directory/admin-roles-best-practices).

## <a name="next-steps"></a>Étapes suivantes

[Configurer l’identité commune et les stratégies d’accès de périphérique](identity-access-policies.md)

