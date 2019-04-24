---
title: Stratégies recommandées pour la sécurisation des e-mails -Microsoft 365 Entreprise | Microsoft Docs
description: Décrit les recommandations de Microsoft sur l’application de stratégies et de configurations liées aux e-mails.
author: brendacarter
manager: laurawi
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
ms.openlocfilehash: 78defc7ad5da788ae49195f6c0027f3639d50f3e
ms.sourcegitcommit: 81273a9df49647286235b187fa2213c5ec7e8b62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "32291113"
---
# <a name="policy-recommendations-for-securing-email"></a>Recommandations de stratégies pour sécuriser les e-mails
Cet article explique comment implémenter les stratégies d'identité et d'accès aux appareils recommandées pour protéger les clients de messagerie et de messagerie de l'organisation qui prennent en charge l'authentification moderne et l'accès conditionnel. Ce guide s'appuie sur les [stratégies courantes d'identité et d'accès aux appareils](identity-access-policies.md) et présente également quelques recommandations supplémentaires.


Ces recommandations sont basées sur trois niveaux de sécurité et de protection différents, qui peuvent être appliqués en fonction de la granularité de vos besoins: **ligne de base**, **sensibles**et **hautement réglementés**. Vous trouverez plus d’informations sur ces niveaux de sécurité et les systèmes d’exploitation clients recommandés auxquels cet article fait référence dans la [présentation des configurations et des stratégies de sécurité recommandées](microsoft-365-policies-configurations.md).

Ces recommandations nécessitent que vos utilisateurs utilisent des clients de messagerie modernes, notamment Outlook pour iOS et Android sur des appareils mobiles. Outlook pour iOS et Android prend en charge les meilleures fonctionnalités d'Office 365. Ces applications Outlook mobiles sont également conçues avec des fonctionnalités de sécurité qui prennent en charge l'utilisation mobile et fonctionnent conjointement avec d'autres fonctionnalités de sécurité Cloud Microsoft. Pour plus d'informations, consultez la rubrique [Outlook pour iOS et Android Forum aux questions](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-faq).

## <a name="updating-common-policies-to-include-email"></a>Mise à jour de stratégies communes pour inclure le courrier électronique
Le diagramme suivant illustre les stratégies courantes d'identité et d'accès aux appareils et indique quelles stratégies doivent être mises à jour pour protéger le courrier électronique. Notez l'ajout d'une nouvelle règle pour Exchange Online afin de bloquer les clients ActiveSync. Cela force l'utilisation d'Outlook Mobile.

![Résumé des mises à jour de stratégie pour la protection de la messagerie](../images/identity-access-ruleset-mail.png)

Si vous avez inclus Exchange Online et Outlook dans l'étendue des stratégies lors de leur configuration, il vous suffit de créer la nouvelle stratégie pour bloquer les clients ActiveSync. Passez en revue les stratégies répertoriées dans le tableau suivant et effectuez les ajouts recommandés, ou confirmez que ceux-ci sont déjà inclus. Chaque règle lie les instructions de configuration associées dans l'article [Common Identity and Device Access Policies](identity-access-policies.md) . 

|Niveau de protection|Stratégies|Plus d’informations|
|:---------------|:-------|:----------------|
|**Baseline**|[Exiger l'authentification multiFACTEUR lorsque le risque de connexion est *moyen* ou *élevé*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Inclure Exchange Online dans l'affectation d'applications Cloud|
|        |[Bloquer les clients qui ne prennent pas en charge l'authentification moderne](identity-access-policies.md#block-clients-that-dont-support-modern-authentication)|Inclure Exchange Online dans l'affectation d'applications Cloud|
|        |[Définir les stratégies de protection des applications](identity-access-policies.md#high-risk-users-must-change-password)|Assurez-vous qu'Outlook est inclus dans la liste des applications. Veillez à mettre à jour la stratégie pour chaque plateforme (iOS, Android, Windows)|
|        |[Exiger les applications approuvées](identity-access-policies.md#require-approved-apps)|Inclure Exchange Online dans la liste des applications Cloud|
|        |[Exiger des PC conformes](identity-access-policies.md#require-compliant-pcs-but-not-compliant-phones-and-tablets)|Inclure Exchange Online dans la liste des applications Cloud|
|        |[Bloquer les clients ActiveSync](#block-activesync-clients)|Ajouter cette nouvelle stratégie| 
|**Sensible**|[Exiger l'authentification multiFACTEUR lorsque le risque de connexion est *faible*, *moyen* ou *élevé*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)| Inclure Exchange Online dans l'affectation d'applications Cloud|
|         |[Exiger des PC conformes *et des* appareils mobiles](identity-access-policies.md#require-compliant-pcs-and-mobile-devices)|Inclure Exchange Online dans la liste des applications Cloud|
|**Hautement réglementé**|[*Toujours* exiger l'authentification multifacteur](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Inclure Exchange Online dans l'affectation d'applications Cloud|

## <a name="block-activesync-clients"></a>Bloquer les clients ActiveSync
Cette stratégie empêche les clients ActiveSync de contourner les autres règles d'accès conditionnel. La configuration de la règle s'applique uniquement aux clients ActiveSync. En sélectionnant **exiger l'application cliente approuvée**, cette stratégie bloque les clients ActiveSync. Pour configurer cette stratégie:

1. Accédez au [portail Azure](https://portal.azure.com) et connectez-vous avec vos informations d’identification. Une fois connecté, le tableau de bord Azure s'affiche.

2. Dans le menu de gauche, choisissez **Azure Active Directory**.

3. Sous la section **Sécurité**, choisissez **Accès conditionnel**.

4. Choisissez **Nouvelle stratégie**.

5. Entrez un nom de stratégie et choisissez les **Utilisateurs et groupes** auxquels vous souhaitez appliquer la stratégie.

6. Choisissez **Applications cloud**.

7. Sélectionnez **Sélectionner les applications**, sélectionnez **Office 365 Exchange Online**. Choisissez **Sélectionner** et **Terminer**.

8. Choisissez **conditions**, puis **applications clientes**.

9. Pour **configurer**, sélectionnez **Oui**. Vérifiez uniquement les éléments suivants: les **applications mobiles et les clients de bureau** et **les clients Exchange ActiveSync**. Sélectionnez **Done (OK)**.

10. Choisissez **Accorder** dans la section **Contrôles d’accès**.

11. Sélectionnez **accorder l'accès**, sélectionnez **demander une application client approuvée**.  Pour plusieurs contrôles, sélectionnez **exiger les contrôles sélectionnés**, puis choisissez **Sélectionner**. 

12. Sélectionnez **Créer**.

## <a name="setup-office-365-message-encryption"></a>Configurer le chiffrement de messages Office 365
Avec les nouvelles fonctionnalités de chiffrement de messages Office 365 (OME), qui tirent parti des fonctionnalités de protection d'Azure information protection, votre organisation peut facilement partager le courrier électronique protégé avec n'importe quel appareil. Les utilisateurs peuvent envoyer et recevoir des messages protégés avec d'autres organisations Office 365, ainsi que des clients non-Office 365 à l'aide de Outlook.com, Gmail et autres services de messagerie.

Pour plus d'informations, reportez-vous à la rubrique [set up New Office 365 message Encryption Capabilities](https://support.office.com/article/set-up-new-office-365-message-encryption-capabilities-7ff0c040-b25c-4378-9904-b1b50210d00e). 



## <a name="next-steps"></a>Étapes suivantes

[En savoir plus sur les recommandations de stratégies pour sécuriser les sites et les fichiers SharePoint](sharepoint-file-access-policies.md)
