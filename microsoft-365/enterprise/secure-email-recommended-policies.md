---
title: Stratégies recommandées pour la sécurisation des e-mails -Microsoft 365 Entreprise | Microsoft Docs
description: Décrit les recommandations de Microsoft sur l’application de stratégies et de configurations liées aux e-mails.
author: brendacarter
manager: laurawi
ms.prod: microsoft-365-enterprise
ms.topic: article
f1.keywords:
- NOCSH
ms.author: bcarter
ms.reviewer: martincoetzer
ms.custom:
- it-pro
- goldenconfig
ms.collection:
- M365-identity-device-management
- M365-security-compliance
ms.openlocfilehash: 8370744d244ce424fa21e496e8dfd4f470de88e6
ms.sourcegitcommit: 8e8230ceab480a5f1506e31de828f04f5590a350
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/26/2020
ms.locfileid: "42959181"
---
# <a name="policy-recommendations-for-securing-email"></a>Recommandations de stratégies pour sécuriser les e-mails

Cet article explique comment implémenter les stratégies d’identité et d’accès aux appareils recommandées pour protéger les clients de messagerie et de messagerie de l’organisation qui prennent en charge l’authentification moderne et l’accès conditionnel. Ce guide s’appuie sur les [stratégies courantes d’identité et d’accès aux appareils](identity-access-policies.md) et présente également quelques recommandations supplémentaires.

Ces recommandations sont basées sur trois niveaux de sécurité et de protection différents, qui peuvent être appliqués en fonction de la granularité de vos besoins : **ligne de base**, **sensibles**et **hautement réglementés**. Vous trouverez plus d’informations sur ces niveaux de sécurité et les systèmes d’exploitation clients recommandés auxquels cet article fait référence dans la [présentation des configurations et des stratégies de sécurité recommandées](microsoft-365-policies-configurations.md).

Ces recommandations nécessitent que vos utilisateurs utilisent des clients de messagerie modernes, notamment Outlook pour iOS et Android sur des appareils mobiles. Outlook pour iOS et Android prend en charge les meilleures fonctionnalités d’Office 365. Ces applications Outlook mobiles sont également conçues avec des fonctionnalités de sécurité qui prennent en charge l’utilisation mobile et fonctionnent conjointement avec d’autres fonctionnalités de sécurité Cloud Microsoft. Pour plus d’informations, consultez la rubrique [Outlook pour iOS et Android Forum aux questions](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-faq).

## <a name="updating-common-policies-to-include-email"></a>Mise à jour de stratégies communes pour inclure le courrier électronique

Le diagramme suivant illustre les stratégies courantes d’identité et d’accès aux appareils et indique quelles stratégies doivent être mises à jour pour protéger le courrier électronique. Notez l’ajout d’une nouvelle règle pour Exchange Online afin de bloquer les clients ActiveSync. Cela force l’utilisation d’Outlook Mobile.

![Résumé des mises à jour de stratégie pour la protection de la messagerie](../media/identity-access-ruleset-mail.png)

Si vous avez inclus Exchange Online et Outlook dans l’étendue des stratégies lors de leur configuration, il vous suffit de créer la nouvelle stratégie pour bloquer les clients ActiveSync. Passez en revue les stratégies répertoriées dans le tableau suivant et effectuez les ajouts recommandés, ou confirmez que ceux-ci sont déjà inclus. Chaque règle lie les instructions de configuration associées dans l’article [Common Identity and Device Access Policies](identity-access-policies.md) .

|Niveau de protection|Stratégies|Plus d’informations|
|:---------------|:-------|:----------------|
|**Baseline**|[Exiger l’authentification multifacteur lorsque le risque de connexion est *moyen* ou *élevé*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Inclure Exchange Online dans l’affectation d’applications Cloud|
|        |[Bloquer les clients ne prenant pas en charge l’authentification moderne](identity-access-policies.md#block-clients-that-dont-support-modern-authentication)|Inclure Exchange Online dans l’affectation d’applications Cloud|
|        |[Définir les stratégies de protection des applications](identity-access-policies.md#high-risk-users-must-change-password)|Assurez-vous qu’Outlook est inclus dans la liste des applications. Veillez à mettre à jour la stratégie pour chaque plateforme (iOS, Android, Windows)|
|        |[Exiger les applications qui prennent en charge les stratégies de protection des applications Intune](identity-access-policies.md#require-apps-that-support-intune-app-protection-policies)|Inclure Exchange Online dans la liste des applications Cloud|
|        |[Exiger des PC conformes](identity-access-policies.md#require-compliant-pcs-but-not-compliant-phones-and-tablets)|Inclure Exchange Online dans la liste des applications Cloud|
|        |[Bloquer les clients ActiveSync](#block-activesync-clients)|Ajouter cette nouvelle stratégie| 
|**Sensible**|[Exiger l’authentification multifacteur lorsque le risque de connexion est *faible*, *moyen* ou *élevé*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)| Inclure Exchange Online dans l’affectation d’applications Cloud|
|         |[Exiger des PC conformes *et des* appareils mobiles](identity-access-policies.md#require-compliant-pcs-and-mobile-devices)|Inclure Exchange Online dans la liste des applications Cloud|
|**Hautement réglementé**|[*Toujours* exiger l’authentification multifacteur](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Inclure Exchange Online dans l’affectation d’applications Cloud|

## <a name="block-activesync-clients"></a>Bloquer les clients ActiveSync

Cette stratégie empêche les clients ActiveSync de contourner les autres règles d’accès conditionnel. La configuration de la règle s’applique uniquement aux clients ActiveSync. En sélectionnant **[exiger la stratégie de protection des applications](https://docs.microsoft.com/azure/active-directory/conditional-access/concept-conditional-access-grant#require-app-protection-policy)**, cette stratégie bloque les clients ActiveSync. Pour plus d’informations sur la création de cette stratégie, voir [require application protection Policy for Cloud App Access with ConditionalAttribute Access](https://docs.microsoft.com/azure/active-directory/conditional-access/app-protection-based-conditional-access).

1. Suivez « étape 2 : configuration d’une stratégie d’accès conditionnel Azure AD pour Exchange Online avec ActiveSync (EAS) » dans le [scénario 1 : les applications Office 365 nécessitent des applications approuvées avec des stratégies de protection d’application](https://docs.microsoft.com/azure/active-directory/conditional-access/app-protection-based-conditional-access#scenario-1-office-365-apps-require-approved-apps-with-app-protection-policies), ce qui empêche les clients Exchange ActiveSync qui utilisent l’authentification de base de se connecter à Exchange Online.

## <a name="setup-office-365-message-encryption"></a>Configurer le chiffrement de messages Office 365

Avec les nouvelles fonctionnalités de chiffrement de messages Office 365 (OME), qui tirent parti des fonctionnalités de protection d’Azure information protection, votre organisation peut facilement partager le courrier électronique protégé avec n’importe quel appareil. Les utilisateurs peuvent envoyer et recevoir des messages protégés avec d’autres organisations Office 365, ainsi que des clients non-Office 365 à l’aide de Outlook.com, Gmail et autres services de messagerie.

Pour plus d’informations, reportez-vous à la rubrique [set up New Office 365 message Encryption Capabilities](https://support.office.com/article/set-up-new-office-365-message-encryption-capabilities-7ff0c040-b25c-4378-9904-b1b50210d00e).

## <a name="next-steps"></a>Étapes suivantes

[En savoir plus sur les recommandations de stratégies pour sécuriser les sites et les fichiers SharePoint](sharepoint-file-access-policies.md)
