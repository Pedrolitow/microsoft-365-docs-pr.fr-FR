---
title: Fonctionnalités Mobility + Security de Base
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier3
- scotvorg
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- MET150
description: Mobilité et sécurité de base vous permet de sécuriser et de gérer les appareils mobiles avec des stratégies qui contrôlent l’accès à la messagerie et aux documents Microsoft 365 de l’organisation.
ms.openlocfilehash: e52fd1cdab5c69badf68d5ffe17bc36196770c6c
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68726836"
---
# <a name="capabilities-of-basic-mobility-and-security"></a>Fonctionnalités Mobility + Security de Base

Mobilité et sécurité de base peuvent vous aider à sécuriser et à gérer les appareils mobiles tels que les iPhones, iPads, Androids et Windows Phone utilisés par les utilisateurs Microsoft 365 sous licence de votre organisation. Vous pouvez créer des stratégies de gestion des appareils mobiles avec des paramètres qui peuvent vous aider à contrôler l’accès à la messagerie et aux documents Microsoft 365 de votre organisation pour les applications et appareils mobiles pris en charge. En cas de perte ou de vol d’un appareil, vous pouvez le réinitialiser à distance pour supprimer les informations sensibles de l’organisation qu’il contient.

## <a name="supported-operating-systems"></a>Systèmes d’exploitation pris en charge

Suivez le guide des systèmes d’exploitation Microsoft Intune pour connaître les systèmes d’exploitation minimum pris en charge pour les appareils par Mobilité et sécurité de base. Pour plus d’informations, consultez [Intune systèmes d’exploitation pris en charge](/mem/intune/fundamentals/supported-devices-browsers).

Vous pouvez utiliser Mobilité et sécurité de base pour sécuriser et gérer les appareils suivants.

- iOS
- Android (y compris Samsung Knox)<sup>1</sup>
- Windows<sup>2, 3</sup>

<sup>1</sup> Après juin 2020, les versions Android ultérieures à la version 9 ne peuvent pas gérer les paramètres de mot de passe, sauf sur les appareils Samsung Knox.

<sup>2</sup> Le contrôle d’accès pour les appareils Windows 8.1 RT est limité à Exchange ActiveSync.

<sup>3</sup> Le contrôle d’accès pour Windows 10 nécessite un abonnement incluant Azure AD Premium et l’appareil doit être joint à Azure Active Directory.

> [!NOTE]
> Les appareils déjà inscrits avec des versions antérieures du système d’exploitation continuent de fonctionner, bien que les fonctionnalités puissent changer sans préavis.

Si des membres de votre organisation utilisent des appareils mobiles qui ne sont pas pris en charge par Mobilité et sécurité de base, vous pouvez bloquer Exchange ActiveSync’accès des applications à la messagerie Microsoft 365 pour ces appareils, afin de sécuriser les données de votre organisation. Pour connaître les étapes à suivre pour bloquer Exchange ActiveSync, consultez [Gérer les paramètres d’accès aux appareils dans Mobilité et sécurité de base](manage-device-access-settings.md).

## <a name="access-control-for-microsoft-365-email-and-documents"></a>Contrôle d’accès pour la messagerie et les documents Microsoft 365

Les applications prises en charge pour les différents types d’appareils mobiles figurant dans le tableau suivant invitent les utilisateurs à s’inscrire dans Mobilité et sécurité de base lorsqu’il existe une nouvelle stratégie de gestion des appareils mobiles qui s’applique à l’appareil d’un utilisateur et que l’utilisateur n’a pas inscrit l’appareil précédemment. Si l’appareil d’un utilisateur n’est pas conforme à une stratégie, selon la façon dont vous définissez la stratégie, un utilisateur peut être bloqué pour accéder aux ressources Microsoft 365 dans ces applications, ou il peut y avoir accès, mais Microsoft 365 signale une violation de stratégie.

|Produit|iOS|Android|
|---|---|---|
|**Exchange** Exchange ActiveSync inclut des applications de messagerie et tierces intégrées, telles que TouchDown, qui utilisent Exchange ActiveSync version 14.1 ou ultérieure.|Courrier|E-mail|
|**Office** et **OneDrive Entreprise**|Outlook </br>OneDrive </br>Word </br>Excel </br>PowerPoint|**Sur les téléphones et tablettes** :<br/>Outlook <br/> OneDrive <br/> Word <br/> Excel <br/> PowerPoint <br/> **Sur les téléphones uniquement :** <br/> Office Mobile|

> [!NOTE]
>
> - La prise en charge d’iOS 10.0 et versions ultérieures inclut les appareils iPhone et iPad.
> - La gestion des appareils de système d’exploitation BlackBerry n’est pas prise en charge par la sécurité de base et la mobilité. Utilisez BlackBerry Business Services cloud (BBCS) de BlackBerry pour gérer les appareils de système d’exploitation BlackBerry. Les appareils Blackberry exécutant le système d’exploitation Android sont pris en charge en tant qu’appareils Android standard
> - Les utilisateurs ne seront pas invités à s’inscrire et ne seront pas bloqués ou signalés pour violation de stratégie s’ils utilisent le navigateur mobile pour accéder aux sites Microsoft 365 SharePoint, aux documents dans Office Online ou aux e-mails dans Outlook Web App.

Le diagramme suivant montre ce qui se passe lorsqu’un utilisateur disposant d’un nouvel appareil se connecte à une application qui prend en charge le contrôle d’accès avec Mobilité et sécurité de base. L’utilisateur ne peut pas accéder aux ressources Microsoft 365 dans l’application tant qu’il n’a pas inscrit son appareil.

:::image type="content" source="../../media/basic-mobility-security/bms-1-access-control.png" alt-text="Contrôle d’accès mobilité et sécurité de base.":::

> [!NOTE]
> Les stratégies et les règles d’accès créées dans Mobilité et sécurité de base pour Microsoft 365 Business Standard remplacent Exchange ActiveSync stratégies de boîte aux lettres des appareils mobiles et les règles d’accès aux appareils créées dans le Centre d’administration Exchange. Une fois qu’un appareil est inscrit dans Mobilité et sécurité de base pour Microsoft 365 Business Standard, toute stratégie de boîte aux lettres d’appareil mobile Exchange ActiveSync ou règle d’accès à l’appareil appliquée à l’appareil est ignorée. Pour en savoir plus sur Exchange ActiveSync, consultez [Exchange ActiveSync dans Exchange Online](/exchange/clients-and-mobile-in-exchange-online/exchange-activesync/exchange-activesync).

## <a name="policy-settings-for-mobile-devices"></a>Paramètres de stratégie pour les appareils mobiles

Si vous créez une stratégie pour bloquer l’accès avec certains paramètres activés, les utilisateurs ne peuvent pas accéder aux ressources Microsoft 365 lors de l’utilisation d’une application prise en charge répertoriée dans [Contrôle d’accès pour la messagerie et les documents Microsoft 365](capabilities.md).

Les paramètres qui peuvent empêcher les utilisateurs d’accéder aux ressources Microsoft 365 se trouvent dans les sections suivantes :

- Sécurité

- Chiffrement

- Débridage

- Profil de messagerie géré

Par exemple, le diagramme suivant montre ce qui se produit lorsqu’un utilisateur disposant d’un appareil inscrit ne respecte pas un paramètre de sécurité dans une stratégie de gestion des appareils mobiles qui s’applique à son appareil. L’utilisateur se connecte à une application qui prend en charge le contrôle d’accès avec Basic Mobility and Security. Ils ne peuvent pas accéder aux ressources Microsoft 365 dans l’application tant que leur appareil n’est pas conforme au paramètre de sécurité.

:::image type="content" source="../../media/basic-mobility-security/bms-2-device-not-compliant.png" alt-text="Message de conformité mobilité et sécurité de base.":::

Les sections suivantes répertorient les paramètres de stratégie que vous pouvez utiliser pour sécuriser et gérer les appareils mobiles qui se connectent à vos ressources d’organisation Microsoft 365.

## <a name="security-settings"></a>Paramètres de sécurité

|Nom du paramètre|iOS|Android|Samsung Knox|
|---|---|---|---|
|Exiger un mot de passe|Oui|Non|Non|
|Empêcher l’utilisation de mots de passe simples|Oui|Non|Non|
|Exiger un mot de passe alphanumérique|Oui|Non|Non|
|Longueur minimale du mot de passe|Oui|Oui|Oui|
|Nombre d’échecs de connexion avant la réinitialisation de l’appareil|Oui|Oui|Oui|
|Durée d’inactivité (en minutes) avant le verrouillage de l’appareil|Oui|Oui|Oui|
|Expiration du mot de passe (jours)|Oui|Oui|Oui|
|Conserver l’historique des mots de passe et empêcher leur réutilisation|Oui|Oui|Oui|

## <a name="encryption-settings"></a>Paramètres de chiffrement

|Nom du paramètre|iOS|Android|Samsung Knox|
|---|---|---|---|
|Exiger le chiffrement des données sur les appareils<sup>1</sup>|Non|Oui|Oui|

<sup>1</sup> Avec Samsung Knox, vous pouvez également exiger le chiffrement sur les cartes de stockage.

## <a name="jail-broken-setting"></a>Paramètre de débridage

|Nom du paramètre|iOS|Android|Samsung Knox|
|---|---|---|---|
|Impossible de débrider l’appareil ou de l’associer à une racine|Oui|Oui|Oui|

## <a name="managed-email-profile-option"></a>Option de profil de messagerie géré

L’option suivante peut empêcher les utilisateurs d’accéder à leur messagerie Microsoft 365 s’ils utilisent un profil de messagerie créé manuellement. Les utilisateurs d’appareils iOS doivent supprimer leur profil de messagerie créé manuellement pour pouvoir accéder à leur messagerie. Une fois le profil supprimé, un nouveau profil est automatiquement créé sur l’appareil. Pour obtenir des instructions sur la façon dont les utilisateurs finaux peuvent se conformer, consultez [Un compte de messagerie existant a été trouvé](/intune-user-help/existing-company-email-account-found).

|Nom du paramètre|iOS|Android|Samsung Knox|
|---|---|---|---|
|Le profil de messagerie est géré|Oui|Non|Non|

## <a name="cloud-settings"></a>Paramètres de cloud

|Nom du paramètre|iOS|Android|Samsung Knox|
|---|---|---|---|
|Exiger la sauvegarde chiffrée|Oui|Non|Non|
|Bloquer la sauvegarde cloud<sup>1</sup>|Oui|Non|Non|
|Bloquer la synchronisation<sup>de documents 1</sup>|Oui|Non|Non|
|Bloquer la synchronisation de photos|Oui|Non|Non|
|Autoriser la sauvegarde Google|S/O|Non|Oui|
|Autoriser la synchronisation automatique du compte Google|S/O|Non|Oui|

<sup>1</sup> Pour fonctionner, ces paramètres nécessitent des appareils iOS supervisés. 

## <a name="system-settings"></a>Paramètres système

|Nom du paramètre|iOS|Android|Samsung Knox|
|---|---|---|---|
|Bloquer la capture d'écran|Oui|Non|Oui|
|Empêcher l’envoi de données de diagnostic à partir de l’appareil|Oui|Non|Oui|

## <a name="application-settings"></a>Paramètres d’application

|Nom du paramètre|iOS|Android|Samsung Knox|
|---|---|---|---|
|Bloquer les vidéoconférences sur l’appareil<sup>1</sup>|Oui|Non|Non|
|Bloquer l’accès au magasin<sup>d’applications 1</sup>|Oui|Non|Oui|
|Exiger un mot de passe en cas d'accès au magasin d'applications|Oui|Non|Non|

<sup>1</sup> Pour fonctionner, ces paramètres nécessitent des appareils iOS supervisés. 

## <a name="device-capabilities-settings"></a>Paramètres de fonctionnalités d’appareil

|Nom du paramètre|iOS|Android|Samsung Knox|
|---|---|---|---|
|Bloquer la connexion au stockage amovible|Non|Non|Oui|
|Bloquer la connexion Bluetooth|Non|Non|Oui|

## <a name="additional-settings"></a>Paramètres supplémentaires

Vous pouvez définir les paramètres de stratégie supplémentaires suivants à l’aide des applets de commande PowerShell security & Compliance. Si vous souhaitez en savoir plus, veuillez consulter l’article [Centre de conformité et sécurité PowerShell](/powershell/exchange/scc-powershell).

|Nom du paramètre|iOS|Android|
|---|---|---|
|CameraEnabled|Oui|Oui|
|RegionRatings|Oui|Non|
|MoviesRatings|Oui|Non|
|TVShowsRating|Oui|Non|
|ApplicationsRatings|Oui|Non|
|AllowVoiceDialing|Oui|Non|
|AllowVoiceAssistant|Oui|Non|
|AllowAssistantWhileLocked|Oui|Non|
|AllowPassbookWhileLocked|Oui|Non|
|MaxPasswordGracePeriod|Oui|Non|
|PasswordQuality|Non|Oui|
|SystemSecurityTLS|Oui|Non|
|WLANEnabled|Non|Non|

## <a name="settings-supported-by-windows"></a>Paramètres pris en charge par Windows

Vous pouvez gérer Windows 10 appareils en les inscrivant en tant qu’appareils mobiles. Une fois qu’une stratégie applicable est déployée, les utilisateurs disposant d’appareils Windows 10 doivent s’inscrire à Mobilité et sécurité de base la première fois qu’ils utilisent l’application de messagerie intégrée pour accéder à leur messagerie Microsoft 365 (nécessite un abonnement Azure AD Premium).

Les paramètres suivants sont pris en charge pour les appareils Windows 10 inscrits en tant qu’appareils mobiles. Ce paramètre n’empêche pas les utilisateurs d’accéder aux ressources Microsoft 365.

### <a name="security-settings"></a>Paramètres de sécurité

- Exiger un mot de passe alphanumérique

- Longueur minimale du mot de passe

- Nombre d’échecs de connexion avant la réinitialisation de l’appareil

- Durée d’inactivité (en minutes) avant le verrouillage de l’appareil

- Expiration du mot de passe (jours)

- Conserver l’historique des mots de passe et empêcher leur réutilisation

> [!NOTE]
> Les paramètres suivants qui régissent les mots de passe contrôlent uniquement les comptes Windows locaux. Les comptes Windows fournis par le biais de la jonction d’un domaine ou d’Azure Active Directory ne sont pas affectés par ces paramètres.

### <a name="system-settings"></a>Paramètres système

Bloquer l’envoi de données de diagnostic à partir de l’appareil.

### <a name="additional-settings"></a>Paramètres supplémentaires

Vous pouvez définir ces paramètres de stratégie supplémentaires à l’aide des applets de commande PowerShell :

- AllowConvenienceLogon

- UserAccountControlStatus

- FirewallStatus

- AutoUpdateStatus

- AntiVirusStatus

- AntiVirusSignatureStatus

- SmartScreenEnabled

- WorkFoldersSyncUrl

## <a name="remotely-wipe-a-mobile-device"></a>Réinitialiser un appareil mobile à distance

Si un appareil est perdu ou volé, vous pouvez supprimer les données organisationnelles sensibles et empêcher l’accès aux ressources de votre organisation Microsoft 365 en effectuant une réinitialisation de **portail de conformité Microsoft Purview** >  **Protection contre la** >  perte **de données Gestion des appareils**. Vous pouvez effectuer une réinitialisation sélective de l’appareil afin de supprimer uniquement les données de l’organisation, ou effectuer une réinitialisation complète afin de supprimer toutes les informations qu’il contient et restaurer ses paramètres d’origine.

Pour plus d’informations, consultez [Réinitialiser un appareil mobile dans Mobilité et sécurité de base](wipe-mobile-device.md).

## <a name="related-content"></a>Contenu associé

[Vue d’ensemble de La mobilité et de la sécurité de base pour Microsoft 365](overview.md) (article)\
[Créer des stratégies de sécurité des appareils dans Mobilité et sécurité de base](create-device-security-policies.md) (article)
