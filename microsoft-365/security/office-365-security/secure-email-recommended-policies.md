---
title: Stratégies de messagerie sécurisées recommandées - Microsoft 365 pour les | d’entreprise Microsoft Docs
description: Décrit les recommandations de Microsoft sur l’application de stratégies et de configurations liées aux e-mails.
ms.author: dansimp
author: dansimp
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
- remotework
- m365solution-identitydevice
- m365solution-scenario
- zerotrust-solution
- highpri
ms.technology: mdo
ms.openlocfilehash: 4a63855d25a7ace428fd3fd93e134f4a6ffcbce3
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67482866"
---
# <a name="policy-recommendations-for-securing-email"></a>Recommandations de stratégies pour sécuriser les e-mails

Cet article explique comment implémenter les stratégies d’accès aux identités et aux appareils Confiance nulle recommandées pour protéger les clients de messagerie et de messagerie de l’organisation qui prennent en charge l’authentification moderne et l’accès conditionnel. Cette aide s’appuie sur les stratégies [d’accès aux identités et aux appareils courantes](identity-access-policies.md) et inclut également quelques recommandations supplémentaires.

Ces recommandations sont basées sur trois niveaux de sécurité et de protection différents qui peuvent être appliqués en fonction de la granularité de vos besoins : **point de départ**, **entreprise** et **sécurité spécialisée**. Vous trouverez plus d’informations sur ces niveaux de sécurité et les systèmes d’exploitation clients recommandés auxquels cet article fait référence dans la [présentation des configurations et des stratégies de sécurité recommandées](microsoft-365-policies-configurations.md).

Ces recommandations nécessitent que vos utilisateurs utilisent des clients de messagerie modernes, notamment Outlook pour iOS et Android sur les appareils mobiles. Outlook pour iOS et Android assure la prise en charge des meilleures fonctionnalités de Office 365. Ces applications Outlook mobiles sont également conçues avec des fonctionnalités de sécurité qui prennent en charge l’utilisation mobile et fonctionnent avec d’autres fonctionnalités de sécurité cloud de Microsoft. Pour plus d’informations, consultez [les QUESTIONS fréquentes (FAQ) sur Outlook pour iOS et Android](/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-faq).

## <a name="update-common-policies-to-include-email"></a>Mettre à jour les stratégies courantes pour inclure l’e-mail

Pour protéger les e-mails, le diagramme suivant illustre les stratégies à mettre à jour à partir des stratégies d’accès aux identités et aux appareils courantes.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-ruleset-mail.png" alt-text="Récapitulatif des mises à jour de stratégie pour la protection de l’accès à Microsoft Exchange" lightbox="../../media/microsoft-365-policies-configurations/identity-access-ruleset-mail.png":::

Notez l’ajout d’une nouvelle stratégie pour Exchange Online pour bloquer les clients ActiveSync. Cela force l’utilisation d’Outlook Mobile.

Si vous avez inclus Exchange Online et Outlook dans l’étendue des stratégies lorsque vous les avez configurées, vous devez uniquement créer la stratégie pour bloquer les clients ActiveSync. Passez en revue les stratégies répertoriées dans le tableau suivant et effectuez les ajouts recommandés ou confirmez qu’elles sont déjà incluses. Chaque stratégie est liée aux instructions de configuration associées dans [les stratégies d’accès aux identités et aux appareils courantes](identity-access-policies.md).

|Niveau de protection|Stratégies|Informations supplémentaires|
|---|---|---|
|**Point de départ**|[Exiger l’authentification multifacteur lorsque le risque de connexion est *moyen* ou *élevé*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Inclure Exchange Online dans l’attribution d’applications cloud|
||[Bloquer les clients ne prenant pas en charge l’authentification moderne](identity-access-policies.md#block-clients-that-dont-support-multi-factor)|Inclure Exchange Online dans l’attribution d’applications cloud|
||[Appliquer des stratégies de protection des données APP](identity-access-policies.md#apply-app-data-protection-policies)|Assurez-vous qu’Outlook est inclus dans la liste des applications. Veillez à mettre à jour la stratégie pour chaque plateforme (iOS, Android, Windows)|
||[Exiger des applications approuvées et une protection d’application](identity-access-policies.md#require-approved-apps-and-app-protection)|Inclure Exchange Online dans la liste des applications cloud|
||[Bloquer les clients ActiveSync](#block-activesync-clients)|Ajouter cette nouvelle stratégie|
|**Enterprise**|[Exiger l’authentification multifacteur lorsque le risque de connexion est *faible*, *moyen* ou *élevé*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Inclure Exchange Online dans l’attribution d’applications cloud|
||[Exiger des PC *et* des appareils mobiles conformes](identity-access-policies.md#require-compliant-pcs-and-mobile-devices)|Inclure Exchange Online dans la liste des applications cloud|
|**Sécurité spécialisée**|[*Toujours* exiger l’authentification multifacteur](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Inclure Exchange Online dans l’attribution d’applications cloud|

## <a name="block-activesync-clients"></a>Bloquer les clients ActiveSync

Exchange ActiveSync pouvez être utilisé pour synchroniser les données de messagerie et de calendrier sur les appareils de bureau et mobiles.

Pour les appareils mobiles, les clients Exchange ActiveSync compatibles avec l’authentification moderne qui ne prennent pas en charge Intune stratégies de protection des applications (ou les clients pris en charge qui ne sont pas définis dans la stratégie de protection des applications) et Exchange ActiveSync clients qui utilisent l’authentification de base sont bloqués en fonction de la stratégie d’accès conditionnel créée dans [ Exiger des applications approuvées et une protection d’application](identity-access-policies.md#require-approved-apps-and-app-protection).

Pour bloquer Exchange ActiveSync à l’aide de l’authentification de base sur d’autres appareils, suivez les étapes décrites dans [Bloquer Exchange ActiveSync sur tous les appareils](/azure/active-directory/conditional-access/howto-policy-approved-app-or-app-protection#block-exchange-activesync-on-all-devices), ce qui empêche Exchange ActiveSync clients utilisant l’authentification de base sur les appareils non mobiles de se connecter à Exchange Online.

Vous pouvez également utiliser des stratégies d’authentification pour [désactiver l’authentification de base](/exchange/clients-and-mobile-in-exchange-online/disable-basic-authentication-in-exchange-online), ce qui force toutes les demandes d’accès client à utiliser l’authentification moderne.

## <a name="limit-access-to-exchange-online-from-outlook-on-the-web"></a>Limiter l’accès aux Exchange Online à partir de Outlook sur le web

Vous pouvez limiter la possibilité pour les utilisateurs de télécharger des pièces jointes à partir de Outlook sur le web sur des appareils non gérés. Les utilisateurs de ces appareils peuvent afficher et modifier ces fichiers à l’aide d’Office Online sans fuite ni stockage des fichiers sur l’appareil. Vous pouvez également empêcher les utilisateurs de voir des pièces jointes sur un appareil non managé.

Voici les étapes à effectuer :

1. [Connectez-vous à Exchange Online PowerShell](/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).
2. Si vous n’avez pas encore de stratégie de boîte aux lettres OWA, créez-en une avec l’applet de commande [New-OwaMailboxPolicy](/powershell/module/exchange/new-owamailboxpolicy) .
3. Si vous souhaitez autoriser l’affichage des pièces jointes sans téléchargement, utilisez cette commande :

   ```powershell
   Set-OwaMailboxPolicy -Identity Default -ConditionalAccessPolicy ReadOnly
   ```

4. Si vous souhaitez bloquer les pièces jointes, utilisez cette commande :

   ```powershell
   Set-OwaMailboxPolicy -Identity Default -ConditionalAccessPolicy ReadOnlyPlusAttachmentsBlocked
   ```

5. Dans le Portail Azure, créez une stratégie d’accès conditionnel avec les paramètres suivants :

   **Affectations** \> **Utilisateurs et groupes** : sélectionnez les utilisateurs et groupes appropriés à inclure et à exclure.

   **Affectations** \> **Applications ou actions** \> cloud **Applications** \> cloud **Inclure** \> **Sélectionner des applications** : Sélectionnez **Office 365 Exchange Online**

   **Contrôles** \> d’accès **Session** : Sélectionner **utiliser des restrictions appliquées par l’application**

## <a name="require-that-ios-and-android-devices-must-use-outlook"></a>Exiger que les appareils iOS et Android doivent utiliser Outlook

Pour vous assurer que les utilisateurs d’appareils iOS et Android peuvent uniquement accéder au contenu professionnel ou scolaire à l’aide d’Outlook pour iOS et Android, vous avez besoin d’une stratégie d’accès conditionnel qui cible ces utilisateurs potentiels.

Consultez les étapes de configuration de cette stratégie dans [Gérer l’accès à la collaboration de messagerie à l’aide d’Outlook pour iOS et Android](/mem/intune/apps/app-configuration-policies-outlook#apply-conditional-access).

## <a name="set-up-message-encryption"></a>Configurer le chiffrement des messages

Avec Chiffrement de messages Microsoft Purview, qui tire parti des fonctionnalités de protection dans Azure Information Protection, votre organisation peut facilement partager des e-mails protégés avec n’importe qui sur n’importe quel appareil. Les utilisateurs peuvent envoyer et recevoir des messages protégés avec d’autres organisations Microsoft 365 ainsi que des non-clients à l’aide de Outlook.com, Gmail et d’autres services de messagerie.

Pour plus d’informations, consultez [Configurer de nouvelles fonctionnalités de chiffrement de messages Office 365](../../compliance/set-up-new-message-encryption-capabilities.md).

## <a name="next-steps"></a>Prochaines étapes

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png" alt-text="Stratégies pour les applications cloud Microsoft 365" lightbox="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png":::

Configurer des stratégies d’accès conditionnel pour :

- [Microsoft Teams](teams-access-policies.md)
- [SharePoint](sharepoint-file-access-policies.md)
