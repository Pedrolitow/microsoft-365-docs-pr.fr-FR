---
title: Fonctionnalités Mobility + Security de Base
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
description: La mobilité et la sécurité de base peuvent vous aider à sécuriser et à gérer les appareils mobiles.
ms.openlocfilehash: 746131e90e207d7b888a3ddcaf4ff0656606a2c7
ms.sourcegitcommit: 8849dd6f80217c29f427c7f008d918f30c792240
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2021
ms.locfileid: "49877115"
---
# <a name="capabilities-of-basic-mobility-and-security"></a>Fonctionnalités Mobility + Security de Base

La mobilité et la sécurité de base peuvent vous aider à sécuriser et gérer les appareils mobiles tels que les iPhone, iPad, Android et Windows Phone utilisés par les utilisateurs sous licence Microsoft 365 de votre organisation. Vous pouvez créer des stratégies de gestion des appareils mobiles avec des paramètres qui peuvent vous aider à contrôler l’accès à la messagerie et aux documents Microsoft 365 de votre organisation pour les appareils mobiles et les applications mobiles pris en charge. En cas de perte ou de vol d’un appareil, vous pouvez le réinitialiser à distance pour supprimer les informations sensibles de l’organisation qu’il contient.

## <a name="supported-devices"></a>Appareils pris en charge

Vous pouvez utiliser la mobilité et la sécurité de base pour sécuriser et gérer les appareils suivants.

- iOS 11.0 ou versions ultérieures

- Android 5.0 ou versions ultérieures<sup>3</sup>

- Windows 8.1<sup>1</sup>

- Windows 8.1 RT<sup>1</sup>

- Windows 10<sup>2</sup>

- Windows 10 Mobile<sup>2</sup>

<sup>1</sup> Le contrôle d’accès pour les appareils Windows 8.1 RT est limité à Exchange ActiveSync.

<sup>2</sup> Le contrôle d’accès pour les appareils Windows 8.1 RT est limité à Exchange ActiveSync.
Le contrôle d’accès pour Windows 10 nécessite un abonnement qui inclut Azure AD Premium et l’appareil doit être joint à Azure Active Directory.

<sup>3</sup> Le contrôle d’accès pour les appareils Windows 8.1 RT est limité à Exchange ActiveSync.
Après juin 2020, les versions d’Android ultérieures à 9 ne peuvent pas gérer les paramètres de mot de passe, sauf sur les appareils Samsung Knox.

>[!NOTE]
>Les appareils déjà inscrits avec des versions antérieures du système d’exploitation continuent de fonctionner même si les fonctionnalités peuvent changer sans préavis.

Si les membres de votre organisation utilisent des appareils mobiles qui ne sont pas pris en charge par la mobilité et la sécurité de base, vous pouvez bloquer l’accès de l’application Exchange ActiveSync à la messagerie Microsoft 365 pour ces appareils, afin de sécuriser les données de votre organisation. Pour obtenir la procédure de blocage Exchange ActiveSync, voir [Gérer les paramètres](manage-device-access-settings.md)d’accès aux appareils dans Basic Mobility and Security .

## <a name="access-control-for-microsoft-365-email-and-documents"></a>Contrôle d’accès pour la messagerie et les documents Microsoft 365

Les applications prise en charge pour les différents types d’appareils mobiles dans le tableau suivant invitent les utilisateurs à s’inscrire à Basic Mobility and Security lorsqu’une nouvelle stratégie de gestion des appareils mobiles s’applique à l’appareil d’un utilisateur et que l’utilisateur ne l’a pas précédemment inscrit. Si l’appareil d’un utilisateur n’est pas conforme à une stratégie, selon la façon dont vous la définissez, il se peut qu’un utilisateur ne puisse pas accéder aux ressources Microsoft 365 dans ces applications, ou qu’il puisse y avoir accès, mais Microsoft 365 signale une violation de stratégie.

|**Produit**|**iOS 10.0 ou une ultérieure**|**Android 5.0 ou version ultérieure**|
|:-----|:-----|:-----|
|**Exchange** Exchange ActiveSync inclut la messagerie électronique intégrée et les applications tierces, telles que TouchDown, qui utilisent Exchange ActiveSync version 14.1 ou ultérieure. |Courrier |E-mail |
|**Office**   et  **OneDrive Entreprise** |Outlook </br>OneDrive </br>Word </br>Excel </br>PowerPoint|**Sur les téléphones et les tablettes**:<br/>Outlook <br/> OneDrive <br/> Word <br/> Excel <br/> PowerPoint <br/> **Sur les téléphones uniquement :** <br/> Office Mobile |

>[!NOTE]
- >La prise en charge d’iOS 10.0 et des versions ultérieures inclut les appareils iPhone et iPad.
- >La gestion des appareils blackBerry OS n’est pas prise en charge par la sécurité et la mobilité de base. Utilisez blackBerry Business Cloud Services (BBCS) de BlackBerry pour gérer les appareils blackBerry OS. Les appareils Blackberry exécutant le système d’exploitation Android sont pris en charge en tant qu’appareils Android standard
- >Les utilisateurs ne seront pas invités à s’inscrire et ne seront pas bloqués ou signalés pour violation de stratégie s’ils utilisent le navigateur mobile pour accéder aux sites SharePoint Microsoft 365, aux documents dans Office Online ou à la messagerie électronique dans Outlook Web App.

Le diagramme suivant illustre ce qui se produit lorsqu’un utilisateur avec un nouvel appareil se connecté à une application qui prend en charge le contrôle d’accès avec Basic Mobility and Security. L’utilisateur ne peut pas accéder aux ressources Microsoft 365 dans l’application jusqu’à ce qu’il inscrive son appareil.

:::image type="content" source="../../media/basic-mobility-security/bms-1-access-control.png" alt-text="Contrôle d’accès de base à la mobilité et à la sécurité":::

> [!NOTE]
> Les stratégies et règles d’accès créées dans Basic Mobility and Security pour Microsoft 365 Business Standard remplaceront Exchange ActiveSync stratégies de boîte aux lettres d’appareil mobile et les règles d’accès aux appareils créées dans le Centre d’administration Exchange. Une fois qu’un appareil est inscrit à Basic Mobility and Security pour Microsoft 365 Business Standard, toute stratégie de boîte aux lettres d’appareil mobile ou règle d’accès aux appareils Exchange ActiveSync appliquée à l’appareil est ignorée. Pour en savoir plus sur Exchange ActiveSync, voir [Exchange ActiveSync dans Exchange Online.](https://go.microsoft.com/fwlink/p/?LinkId=524380)

## <a name="policy-settings-for-mobile-devices"></a>Paramètres de stratégie pour les appareils mobiles

Si vous créez une stratégie pour bloquer l’accès avec certains paramètres désactivés, les utilisateurs ne peuvent pas accéder aux ressources Microsoft 365 lors de l’utilisation d’une application prise en charge répertoriée dans le contrôle Access pour la messagerie et les [documents Microsoft 365.](capabilities.md) 

Les paramètres qui peuvent empêcher les utilisateurs d’accéder aux ressources Microsoft 365 sont disponibles dans les sections suivantes :

- Sécurité

- Chiffrement

- Débridage

- Profil de messagerie géré  

Par exemple, le diagramme suivant montre ce qui se produit lorsqu’un utilisateur disposant d’un appareil inscrit ne respecte pas un paramètre de sécurité dans une stratégie de gestion des appareils mobiles qui s’applique à son appareil. L’utilisateur se signe à une application qui prend en charge le contrôle d’accès avec Basic Mobility and Security. Ils ne peuvent pas accéder aux ressources Microsoft 365 dans l’application tant que leur appareil n’est pas conforme au paramètre de sécurité.

:::image type="content" source="../../media/basic-mobility-security/bms-2-device-not-compliant.png" alt-text="Message de conformité de sécurité et de mobilité de base":::

Les sections suivantes listent les paramètres de stratégie que vous pouvez utiliser pour sécuriser et gérer les appareils mobiles qui se connectent aux ressources de votre organisation Microsoft 365.

## <a name="security-settings"></a>Paramètres de sécurité

|**Nom du paramètre**|**iOS 7.1 et les ultérieures**|**Android 5 et version ultérieure**|**Samsung Knox**|
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

|**Nom du paramètre**|**iOS 7.1 et les ultérieures**|**Android 5 et version ultérieure**|**Samsung Knox**|
|:-----|:-----|:-----|:-----|
|Exiger le chiffrement des données sur les<sup>appareils 1</sup> |Non|Oui|Oui|

<sup>1</sup> Avec Samsung Knox, vous pouvez également exiger le chiffrement sur les cartes de stockage. 

## <a name="jail-broken-setting"></a>Paramètre de débridage 

|**Nom du paramètre**|**iOS 7.1 et les ultérieures**|**Android 5 et version ultérieure**|**Samsung Knox**|
|:-----|:-----|:-----|:-----|
|Impossible de débrider l’appareil ou de l’associer à une racine |Oui|Oui|Oui|

## <a name="managed-email-profile-option"></a>Option de profil de messagerie géré 

L’option suivante peut empêcher les utilisateurs d’accéder à leur messagerie Microsoft 365 s’ils utilisent un profil de messagerie créé manuellement. Les utilisateurs d’appareils iOS doivent supprimer leur profil de messagerie créé manuellement pour pouvoir accéder à leur messagerie. Une fois le profil supprimé, un nouveau profil est créé automatiquement sur l’appareil. Pour obtenir des instructions sur la façon dont les utilisateurs finaux peuvent obtenir la conformité, voir Un compte de [messagerie existant a été trouvé.](https://docs.microsoft.com/intune-user-help/existing-company-email-account-found)

|**Nom du paramètre**|**iOS 7.1 et les ultérieures**|**Android 5 et version ultérieure**|**Samsung Knox**|
|:-----|:-----|:-----|:-----|
|Le profil de messagerie est géré |Oui|Non|Non|

## <a name="cloud-settings"></a>Paramètres de cloud

|**Nom du paramètre**|**iOS 7.1 et les ultérieures**|**Android 5 et version ultérieure**|**Samsung Knox**|
|:-----|:-----|:-----|:-----|
|Exiger la sauvegarde chiffrée |Oui|Non|Non|
|Bloquer la sauvegarde sur le cloud |Oui|Non|Non|
|Bloquer la synchronisation de documents |Oui|Non|Non|
|Bloquer la synchronisation de photos  |Oui|Non|Non|
|Autoriser la sauvegarde Google  |S/O|Non|Oui|
|Autoriser la synchronisation automatique des comptes Google  |S/O|Non|Oui|

## <a name="system-settings"></a>Paramètres système

|**Nom du paramètre**|**iOS 7.1 et les ultérieures**|**Android 5 et version ultérieure**|**Samsung Knox**|
|:-----|:-----|:-----|:-----|
|Bloquer la capture d’écran |Oui|Non|Oui|
|Empêcher l’envoi de données de diagnostic à partir de l’appareil |Oui|Non|Oui|

## <a name="application-settings"></a>Paramètres d’application

|**Nom du paramètre**|**iOS 7.1 et les ultérieures**|**Android 5 et version ultérieure**|**Samsung Knox**|
|:-----|:-----|:-----|:-----|
|Bloquer la visioconférence sur l'appareil |Oui|Non|Non|
|Bloquer l’accès au magasin d’applications |Oui|Non|Oui|
|Exiger un mot de passe pour accéder au magasin d’applications |Non|Oui|Oui|

## <a name="device-capabilities-settings"></a>Paramètres de fonctionnalités d’appareil

|**Nom du paramètre**|**iOS 7.1 et les ultérieures**|**Android 5 et version ultérieure**|**Samsung Knox**|
|:-----|:-----|:-----|:-----|
|Bloquer la connexion au stockage amovible |Oui|Oui|Non|
|Bloquer la connexion Bluetooth |Oui|Oui|Non|

## <a name="additional-settings"></a>Paramètres supplémentaires

Vous pouvez définir les paramètres de stratégie supplémentaires suivants à l’aide des cmdlets PowerShell du Centre de sécurité & conformité. Pour plus d’informations, [voir Centre de sécurité & conformité PowerShell.](https://docs.microsoft.com/powershell/exchange/scc-powershell)

|**Nom du paramètre**|**iOS 7.1 et les ultérieures**|**Android 5 et version ultérieure**|
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

Vous pouvez gérer les appareils Windows 10 en les inscrivant en tant qu’appareils mobiles. Une fois qu’une stratégie applicable est déployée, les utilisateurs ayant des appareils Windows 10 doivent s’inscrire à Basic Mobility and Security la première fois qu’ils utilisent l’application de messagerie intégrée pour accéder à leur messagerie Microsoft 365 (nécessite un abonnement Azure AD Premium).

Les paramètres suivants sont pris en charge pour les appareils Windows 10 inscrits en tant qu’appareils mobiles. Ces paramètres n’empêchera pas les utilisateurs d’accéder aux ressources Microsoft 365.

### <a name="security-settings"></a>Paramètres de sécurité

- Exiger un mot de passe alphanumérique

- Longueur minimale du mot de passe

- Nombre d’échecs de connexion avant la réinitialisation de l’appareil

- Durée d’inactivité (en minutes) avant le verrouillage de l’appareil

- Expiration du mot de passe (jours)

- Conserver l’historique des mots de passe et empêcher leur réutilisation

>[!NOTE]
>Les paramètres suivants qui contrôlent les mots de passe contrôlent uniquement les comptes Windows locaux. Les comptes Windows fournis par le biais de la participation à un domaine ou à Azure Active Directory ne sont pas affectés par ces paramètres.

### <a name="system-settings"></a>Paramètres système

Bloquer l’envoi de données de diagnostic à partir de l’appareil.

### <a name="additional-settings"></a>Paramètres supplémentaires

Vous pouvez définir ces paramètres de stratégie supplémentaires à l’aide des cmdlets PowerShell :

- AllowConvenienceLogon

- UserAccountControlStatus

- FirewallStatus

- AutoUpdateStatus

- AntiVirusStatus

- AntiVirusSignatureStatus

- SmartScreenEnabled

- WorkFoldersSyncUrl

## <a name="remotely-wipe-a-mobile-device"></a>Réinitialiser un appareil mobile à distance

Si un appareil est perdu ou volé, vous pouvez supprimer des données organisationnelles sensibles et empêcher l’accès aux ressources de votre organisation Microsoft 365 en faisant une effacement à partir du Centre de sécurité & conformité > Gestion des appareils de protection contre la perte de  >  données. Vous pouvez effectuer une réinitialisation sélective de l’appareil afin de supprimer uniquement les données de l’organisation, ou effectuer une réinitialisation complète afin de supprimer toutes les informations qu’il contient et restaurer ses paramètres d’origine.

Pour plus d’informations, voir [Effacer un appareil mobile dans Basic Mobility and Security.](wipe-mobile-device.md)

## <a name="related-topics"></a>Rubriques connexes

[Vue d’ensemble de la mobilité et de la sécurité de base pour Microsoft 365](overview.md)

[Créer des stratégies de sécurité des appareils dans Basic Mobility and Security](create-device-security-policies.md)