---
title: Fonctionnalités de la mobilité et de la sécurité de base
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
search.appverid:
- MET150
description: La sécurité et la mobilité de base peuvent vous aider à sécuriser et gérer les appareils mobiles.
ms.openlocfilehash: aed4f4c2d252e487d24496ac00f3de24bc57ab55
ms.sourcegitcommit: 27daadad9ca0f02a833ff3cff8a574551b9581da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "47545895"
---
# <a name="capabilities-of-basic-mobility-and-security"></a>Fonctionnalités de la mobilité et de la sécurité de base

La sécurité et la mobilité de base vous permettent de sécuriser et de gérer des appareils mobiles tels que les iPhone, les iPad, les Androids et les téléphones Windows utilisés par les utilisateurs de Microsoft 365 sous licence dans votre organisation. Vous pouvez créer des stratégies de gestion des appareils mobiles avec des paramètres permettant de contrôler l’accès aux courriers et aux documents Microsoft 365 de votre organisation pour les appareils et applications mobiles pris en charge. En cas de perte ou de vol d’un appareil, vous pouvez le réinitialiser à distance pour supprimer les informations sensibles de l’organisation qu’il contient.

## <a name="supported-devices"></a>Appareils pris en charge

Vous pouvez utiliser la mobilité et la sécurité de base pour sécuriser et gérer les appareils suivants.

- iOS 11,0 ou versions ultérieures
    
- Android 5,0 ou versions ultérieures<sup>3</sup>
    
- Windows 8,1<sup>1</sup>
    
- Windows 8,1 RT<sup>1</sup>
    
- Windows 10<sup>2</sup>
    
- Windows 10 Mobile<sup>2</sup>   

<sup>1</sup> Le contrôle d’accès pour les appareils Windows 8,1 RT est limité à Exchange ActiveSync.

<sup>2</sup> Le contrôle d’accès pour les appareils Windows 8,1 RT est limité à Exchange ActiveSync.
Le contrôle d’accès pour Windows 10 nécessite un abonnement à Azure AD Premium et l’appareil doit être joint à Azure Active Directory.

<sup>3</sup> Le contrôle d’accès pour les appareils Windows 8,1 RT est limité à Exchange ActiveSync.
Après le 2020 juin, les versions Android supérieures à 9 ne peuvent pas gérer les paramètres de mot de passe sauf sur les appareils Knox Samsung.

>[!NOTE]
>Les appareils déjà déployés avec des versions antérieures du système d’exploitation continuent de fonctionner même si les fonctionnalités peuvent être modifiées sans préavis.

Si les utilisateurs de votre organisation utilisent des appareils mobiles qui ne sont pas pris en charge par la sécurité et la mobilité de base, vous pouvez bloquer l’accès de l’application Exchange ActiveSync aux courriers électroniques Microsoft 365 afin de renforcer la sécurité des données de votre organisation. Pour connaître les étapes à suivre pour bloquer Exchange ActiveSync, consultez la rubrique [Manage Device Access Settings in Basic Mobility and Security](manage-device-access-settings.md).

## <a name="access-control-for-microsoft-365-email-and-documents"></a>Contrôle d’accès pour les courriers électroniques et les documents Microsoft 365

Les applications prises en charge pour les différents types d’appareils mobiles dans le tableau suivant invitent les utilisateurs à s’inscrire à la mobilité et à la sécurité de base lorsqu’il existe une nouvelle stratégie de gestion des appareils mobiles qui s’applique au périphérique d’un utilisateur et que l’utilisateur n’a pas précédemment inscrit l’appareil. Si l’appareil d’un utilisateur ne correspond pas à une stratégie, en fonction de la configuration de la stratégie, il se peut qu’un utilisateur ne soit pas autorisé à accéder aux ressources de Microsoft 365 dans ces applications, ou qu’il ait accès, mais Microsoft 365 signale une violation de stratégie.

|**Produit**|**iOS 10,0 ou version ultérieure**|**Android 5,0 ou version ultérieure**|
|:-----|:-----|:-----|
|**Exchange** Exchange ActiveSync inclut des applications de messagerie électronique et tierces, telles que l’inversion, qui utilisent Exchange ActiveSync version 14,1 ou une version ultérieure. |Courrier |E-mail |
|**Office**   et **OneDrive entreprise** |Outlook </br>OneDrive </br>Word </br>Excel </br>PowerPoint|**Sur les téléphones et les tablettes**:<br/>Outlook <br/> OneDrive <br/> Word <br/> Excel <br/> PowerPoint <br/> **Sur les téléphones uniquement :** <br/> Office Mobile |

>[!NOTE]
- >La prise en charge d’iOS 10,0 et versions ultérieures inclut les appareils iPhone et iPad.
- >La gestion des périphériques BlackBerry OS n’est pas prise en charge par la gestion des appareils mobiles pour Microsoft 365. Utilisez BlackBerry Business cloud services (BBCS) de BlackBerry pour gérer les périphériques de système d’exploitation BlackBerry. Les périphériques BlackBerry exécutant Android OS sont pris en charge en tant qu’appareils Android standard
- >Les utilisateurs ne seront pas invités à s’inscrire et ne seront pas bloqués ou signalés pour une violation de stratégie s’ils utilisent le navigateur mobile pour accéder aux sites SharePoint de Microsoft 365, des documents dans Office Online ou des courriers électroniques dans Outlook Web App.
    
Le diagramme suivant montre ce qui se passe lorsqu’un utilisateur disposant d’un nouvel appareil se connecte à une application qui prend en charge le contrôle d’accès avec la sécurité et la mobilité de base. L’utilisateur ne peut pas accéder aux ressources Microsoft 365 dans l’application tant qu’il n’a pas inscrit son appareil.

:::image type="content" source="../../media/basic-mobility-security/bms-1-access-control.png" alt-text="Contrôle d’accès de sécurité et de mobilité de base":::

Remarque : les stratégies et les règles d’accès créées dans MDM pour Microsoft 365 Business standard remplaceront les stratégies de boîte aux lettres d’appareil mobile Exchange ActiveSync et les règles d’accès des appareils créées dans le centre d’administration Exchange. Après l’enregistrement d’un appareil dans MDM pour Microsoft 365 Business standard, toute stratégie de boîte aux lettres d’appareil mobile Exchange ActiveSync ou règle d’accès aux appareils appliquée à l’appareil sera ignorée. Pour en savoir plus sur Exchange ActiveSync, consultez la rubrique [Exchange ActiveSync dans Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=524380).

## <a name="policy-settings-for-mobile-devices"></a>Paramètres de stratégie pour les appareils mobiles

Si vous créez une stratégie pour bloquer l’accès avec certains paramètres activés, les utilisateurs ne peuvent pas accéder aux ressources Microsoft 365 lors de l’utilisation d’une application prise en charge répertoriée dans la section [contrôle d’accès pour le courrier électronique et les documents microsoft 365](capabilities.md). 

Les paramètres qui peuvent empêcher les utilisateurs d’accéder aux ressources Microsoft 365 sont les suivants :

- Sécurité
    
- Chiffrement
    
- Débridage
    
- Profil de messagerie géré  

Par exemple, le diagramme suivant montre ce qui se produit lorsqu’un utilisateur disposant d’un appareil inscrit ne respecte pas un paramètre de sécurité dans une stratégie de gestion des appareils mobiles qui s’applique à son appareil. L’utilisateur se connecte à une application qui prend en charge le contrôle d’accès avec la sécurité et la mobilité de base. Ils ne peuvent pas accéder aux ressources Microsoft 365 dans l’application tant que leur appareil n’est pas conforme au paramètre de sécurité.

:::image type="content" source="../../media/basic-mobility-security/bms-2-device-not-compliant.png" alt-text="Message de conformité de base et de sécurité":::

Les sections suivantes répertorient les paramètres de stratégie que vous pouvez utiliser pour sécuriser et gérer les appareils mobiles qui se connectent à vos ressources d’organisation Microsoft 365.

## <a name="security-settings"></a>Paramètres de sécurité

|**Nom du paramètre**|**iOS 7,1 et versions ultérieures**|**Android 5 et versions ultérieures**|**Samsung Knox**|
|:-----|:-----|:-----|:-----|
|Exiger un mot de passe|Oui|Oui|Oui|
|Empêcher l’utilisation de mots de passe simples|Oui|Non|Non|
|Exiger un mot de passe alphanumérique|Oui|Non|Non|
|Longueur minimale du mot de passe |Oui|Oui|Oui|
|Nombre d’échecs de connexion avant la réinitialisation de l’appareil |Oui|Oui|Oui|
|Durée d’inactivité (en minutes) avant le verrouillage de l’appareil |Oui|Oui|Oui|
|Expiration du mot de passe (jours) |Oui|Oui|Oui|
|Conserver l’historique des mots de passe et empêcher leur réutilisation |Oui|Oui|Oui|

## <a name="encryption-settings"></a>Paramètres de chiffrement 

|**Nom du paramètre**|**iOS 7,1 et versions ultérieures**|**Android 5 et versions ultérieures**|**Samsung Knox**|
|:-----|:-----|:-----|:-----|
|Exiger le chiffrement des données sur les appareils<sup>1</sup> |Non|Oui|Oui|

<sup>1</sup> Avec Samsung Knox, vous pouvez également exiger le chiffrement sur les cartes de stockage. 

## <a name="jail-broken-setting"></a>Paramètre de débridage 

|**Nom du paramètre**|**iOS 7,1 et versions ultérieures**|**Android 5 et versions ultérieures**|**Samsung Knox**|
|:-----|:-----|:-----|:-----|
|Impossible de débrider l’appareil ou de l’associer à une racine |Oui|Oui|Oui|

## <a name="managed-email-profile-option"></a>Option de profil de messagerie géré 

L’option suivante permet d’empêcher les utilisateurs d’accéder à leur messagerie Microsoft 365 s’ils utilisent un profil de messagerie créé manuellement. Les utilisateurs d’appareils iOS doivent supprimer leur profil de messagerie créé manuellement pour pouvoir accéder à leur messagerie. Une fois le profil supprimé, un nouveau profil est créé automatiquement sur l’appareil. Pour obtenir des instructions sur la façon dont les utilisateurs finaux peuvent respecter la réglementation, voir [un compte de messagerie existant](https://docs.microsoft.com/intune-user-help/existing-company-email-account-found).

|**Nom du paramètre**|**iOS 7,1 et versions ultérieures**|**Android 5 et versions ultérieures**|**Samsung Knox**|
|:-----|:-----|:-----|:-----|
|Le profil de messagerie est géré |Oui|Non|Non|

## <a name="cloud-settings"></a>Paramètres de cloud 

|**Nom du paramètre**|**iOS 7,1 et versions ultérieures**|**Android 5 et versions ultérieures**|**Samsung Knox**|
|:-----|:-----|:-----|:-----|
|Exiger la sauvegarde chiffrée |Oui|Non|Non|
|Bloquer la sauvegarde sur le cloud |Oui|Non|Non|
|Bloquer la synchronisation de documents |Oui|Non|Non|
|Bloquer la synchronisation de photos  |Oui|Non|Non|
|Autoriser la sauvegarde Google  |S/O|Non|Oui|
|Autoriser la synchronisation automatique des comptes Google  |S/O|Non|Oui|

## <a name="system-settings"></a>Paramètres système 

|**Nom du paramètre**|**iOS 7,1 et versions ultérieures**|**Android 5 et versions ultérieures**|**Samsung Knox**|
|:-----|:-----|:-----|:-----|
|Bloquer la capture d’écran |Oui|Non|Oui|
|Empêcher l’envoi de données de diagnostic à partir de l’appareil |Oui|Non|Oui|

## <a name="application-settings"></a>Paramètres d’application 

|**Nom du paramètre**|**iOS 7,1 et versions ultérieures**|**Android 5 et versions ultérieures**|**Samsung Knox**|
|:-----|:-----|:-----|:-----|
|Bloquer la visioconférence sur l'appareil |Oui|Non|Non|
|Bloquer l’accès au magasin d’applications |Oui|Non|Oui|
|Exiger un mot de passe pour accéder au magasin d’applications |Non|Oui|Oui|

## <a name="device-capabilities-settings"></a>Paramètres de fonctionnalités d’appareil 

|**Nom du paramètre**|**iOS 7,1 et versions ultérieures**|**Android 5 et versions ultérieures**|**Samsung Knox**|
|:-----|:-----|:-----|:-----|
|Bloquer la connexion au stockage amovible |Oui|Oui|Non|
|Bloquer la connexion Bluetooth |Oui|Oui|Non|

## <a name="additional-settings"></a>Paramètres supplémentaires

Vous pouvez définir les paramètres de stratégie supplémentaires suivants à l’aide des applets de commande PowerShell du centre de conformité et de & sécurité. Pour plus d’informations, consultez [la rubrique Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/scc-powershell).

|**Nom du paramètre**|**iOS 7,1 et versions ultérieures**|**Android 5 et versions ultérieures**|
|:-----|:-----|:-----|
|CameraEnabled|Oui|Oui|
|RegionRatings|Oui|Non|
|MoviesRatings|Oui|Non|
|TVShowsRating |Oui|Non|
|AppsRatings |Oui|Non|
|AllowVoiceDialing |Oui|Non|
|AllowVoiceAssistant |Oui|Non|
|AllowAssistantWhileLocked  |Oui|Non|
|AllowPassbookWhileLocked |Oui|Non|
|MaxPasswordGracePeriod |Oui|Non|
|PasswordQuality |Non|Oui|
|SystemSecurityTLS  |Oui|Non|
|WLANEnabled  |Non|Non|

## <a name="settings-supported-by-windows"></a>Paramètres pris en charge par Windows 

Vous pouvez gérer les appareils Windows 10 en les inscrivant en tant qu’appareils mobiles. Après le déploiement d’une stratégie applicable, les utilisateurs disposant de périphériques Windows 10 doivent s’inscrire à la sécurité et à la mobilité de base la première fois qu’ils utilisent l’application de messagerie intégrée pour accéder à leur messagerie Microsoft 365 (nécessite un abonnement Azure AD Premium).

Les paramètres suivants sont pris en charge pour les appareils Windows 10 qui sont déployés en tant qu’appareils mobiles. Ces paramètres ne bloqueront pas les utilisateurs d’accéder aux ressources Microsoft 365.

### <a name="security-settings"></a>Paramètres de sécurité

- Exiger un mot de passe alphanumérique

- Longueur minimale du mot de passe
    
- Nombre d’échecs de connexion avant la réinitialisation de l’appareil
    
- Durée d’inactivité (en minutes) avant le verrouillage de l’appareil
    
- Expiration du mot de passe (jours)
    
- Conserver l’historique des mots de passe et empêcher leur réutilisation   

>[!NOTE]
>Les paramètres suivants qui régulent les mots de passe contrôlent uniquement les comptes Windows locaux. Les comptes Windows fournis par le biais d’un domaine ou d’Azure Active Directory ne sont pas affectés par ces paramètres.

### <a name="system-settings"></a>Paramètres système

Bloquer l’envoi de données de diagnostic à partir de l’appareil.

### <a name="additional-settings"></a>Paramètres supplémentaires

Vous pouvez définir ces paramètres de stratégie supplémentaires à l’aide des applets de commande PowerShell :

- AllowConvenienceLogon
    
- UserAccountControlStatus
    
- FirewallStatus
    
- AutoUpdateStatus
    
- AntiVirusStatus   

- AntiVirusSignatureStatus
    
- SmartScreenEnabled
    
- WorkFoldersSyncUrl
    

## <a name="remotely-wipe-a-mobile-device"></a>Réinitialiser un appareil mobile à distance

En cas de perte ou de vol d’un appareil, vous pouvez supprimer des données organisationnelles sensibles et empêcher l’accès à vos ressources d’organisation Microsoft 365 en procédant à une réinitialisation à partir du centre de conformité & > la gestion des périphériques de **protection contre la perte de données**  >  **Device management**. Vous pouvez effectuer une réinitialisation sélective de l’appareil afin de supprimer uniquement les données de l’organisation, ou effectuer une réinitialisation complète afin de supprimer toutes les informations qu’il contient et restaurer ses paramètres d’origine.

Pour plus d’informations, reportez-vous à [la rubrique réinitialiser un appareil mobile dans la sécurité et la sécurité de base](wipe-mobile-device.md).

## <a name="related-topics"></a>Voir aussi

[Vue d’ensemble de la sécurité et de la mobilité de base pour Microsoft 365](overview.md)

[Créer des stratégies de sécurité des appareils dans la sécurité et la mobilité de base](create-device-security-policies.md)