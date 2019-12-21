---
title: Stratégies d’identité et d’accès aux appareils courantes-Microsoft 365 Enterprise | Microsoft docs
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
ms.openlocfilehash: b2e9670d700d8c09caf861f5a24b0570e0f74256
ms.sourcegitcommit: 237589a0c8a24510e5c8f3b8b4747d944ad0afbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "37746550"
---
# <a name="common-identity-and-device-access-policies"></a>Stratégies communes pour les identités et l’accès aux appareils
Cet article décrit les stratégies recommandées courantes pour sécuriser l’accès aux services Cloud, notamment les applications locales publiées avec le proxy d’application Azure AD. 

Ce guide explique comment déployer les stratégies recommandées dans un environnement nouvellement mis en service. La configuration de ces stratégies dans un environnement de laboratoire distinct vous permet de comprendre et d’évaluer les stratégies recommandées avant de mettre en place le déploiement dans vos environnements de pré-production et de production. Votre environnement nouvellement configuré peut être en nuage seul ou hybride.  

## <a name="policy-set"></a>Jeu de stratégie 

Le diagramme suivant illustre l’ensemble de stratégies recommandé. Elle indique le niveau de protection auquel chaque stratégie s’applique et indique si les stratégies s’appliquent aux PC, téléphones et tablettes, ou aux deux catégories d’appareils. Il indique également où ces stratégies sont configurées.

![Stratégies courantes de configuration de l’accès aux appareils et aux identités](../images/Identity_device_access_policies_byplan.png)


Le reste de cet article explique comment configurer ces stratégies. 

L’utilisation de l’authentification multifacteur est recommandée avant l’inscriptions de périphériques dans Intune pour garantir que l’appareil est en possession de l’utilisateur prévu. Vous devez également inscrire les appareils dans Intune avant d’appliquer les stratégies de conformité des appareils.

Pour vous donner le temps de réaliser ces tâches, nous vous recommandons de mettre en œuvre les stratégies de base dans l’ordre indiqué dans le tableau ci-dessous. Toutefois, les stratégies de MFA pour une protection sensible et hautement réglementée peuvent être mises en œuvre à tout moment.


|Niveau de protection|Stratégies|Plus d’informations|
|:---------------|:-------|:----------------|
|**Baseline**|[Exiger l’authentification multifacteur lorsque le risque de connexion est *moyen* ou *élevé*](#require-mfa-based-on-sign-in-risk)| |
|        |[Bloquer les clients ne prenant pas en charge l’authentification moderne](#block-clients-that-dont-support-modern-authentication)|Les clients qui n’utilisent pas l’authentification moderne peuvent contourner les règles d’accès conditionnel, c’est pourquoi il est important de bloquer ces|
|        |[Les utilisateurs à haut risque doivent changer leur mot de passe](#high-risk-users-must-change-password)|Force les utilisateurs à modifier leur mot de passe lors de la connexion en cas de détection d’une activité à haut risque pour leur compte.|
|        |[Définir les stratégies de protection des applications](#define-app-protection-policies)|Une stratégie par plateforme (iOS, Android, Windows).|
|        |[Exiger les applications approuvées](#require-approved-apps)|Applique la protection des applications mobiles pour les téléphones et les tablettes|
|        |[Définir les stratégies de conformité des appareils](#define-device-compliance-policies)|Une stratégie pour chaque plateforme|
|        |[Exiger des PC conformes](#require-compliant-pcs-but-not-compliant-phones-and-tablets)|Applique la gestion Intune des PC|
|**Sensible**|[Exiger l’authentification multifacteur lorsque le risque de connexion est *faible*, *moyen* ou *élevé*](#require-mfa-based-on-sign-in-risk)| |
|         |[Exiger des PC conformes *et des* appareils mobiles](#require-compliant-pcs-and-mobile-devices)|Applique la gestion Intune pour les PC et les téléphones/tablettes|
|**Hautement réglementé**|[*Toujours* exiger l’authentification multifacteur](#require-mfa-based-on-sign-in-risk)|
| | |

## <a name="assigning-policies-to-users"></a>Affectation de stratégies aux utilisateurs
Avant de configurer des stratégies, identifiez les groupes Azure AD que vous utilisez pour chaque niveau de protection. En règle générale, la protection de base s’applique à tous les employés de l’organisation. Toutes les stratégies de base, ainsi que les stratégies sensibles, sont appliquées à un utilisateur qui est inclus à la fois pour la protection de référence et la protection sensible. La protection est cumulative et la stratégie la plus restrictive est appliquée. 

Une pratique recommandée consiste à créer un groupe Azure AD pour l’exclusion d’accès conditionnel. Ajoutez ce groupe à toutes vos règles d’accès conditionnel sous « exclure ». Cela vous permet de fournir un accès à un utilisateur pendant que vous dépannez les problèmes d’accès. Il s’agit d’une solution temporaire uniquement. Surveillez ce groupe pour les modifications et assurez-vous que le groupe d’exclusion n’est utilisé que comme prévu. 

Le diagramme suivant fournit un exemple d’affectations et d’exclusions d’utilisateurs.

![Exemple d’affectations et d’exclusions d’utilisateurs pour les règles MFA](../images/identity-access-policies-assignment.png)

Dans l’illustration, l’équipe « top secret Project X Team » est affectée à une stratégie d’accès conditionnel qui requiert la MFA *Always*. Soyez judicieuses lorsque vous appliquez des niveaux de protection plus élevés aux utilisateurs. Les membres de cette équipe de projet devront fournir deux formulaires d’authentification à chaque fois qu’ils se connectent, même s’ils n’affichent pas de contenu hautement réglementé.  

Tous les groupes Azure AD créés dans le cadre de ces recommandations doivent être créés en tant que groupes Office 365. C’est particulièrement important pour le déploiement d’Azure Information Protection lors de la sécurisation des documents dans SharePoint Online.

![Capture d’écran pour la création de groupes Office 365](../images/identity-device-AAD-groups.png)


## <a name="require-mfa-based-on-sign-in-risk"></a>Exiger une authentification multifacteur basée sur le risque de connexion
Avant d’exiger MFA, utilisez d’abord une stratégie d’inscription MFA de protection des identités pour inscrire les utilisateurs pour MFA. Une fois que les utilisateurs sont inscrits, vous pouvez appliquer l’authentification multifacteur à la connexion. Le [travail requis](identity-access-prerequisites.md) inclut l’inscription de tous les utilisateurs avec authentification multifacteur.

Pour créer une stratégie d’accès conditionnel : 

1. Accédez au [portail Azure](https://portal.azure.com) et connectez-vous avec vos informations d’identification. Une fois connecté, le tableau de bord Azure s’affiche.

2. Dans le menu de gauche, choisissez **Azure Active Directory**.

3. Sous la section **Sécurité**, choisissez **Accès conditionnel**.

4. Choisissez **Nouvelle stratégie**.

![Stratégie d’accès conditionnel de base de référence](./media/secure-email/CA-EXO-policy-1.png)

 Le tableau suivant décrit les paramètres de stratégie d’accès conditionnel à implémenter pour cette stratégie.

**Affectations**

|Type|Propriétés|Valeurs|Remarques|
|:---|:---------|:-----|:----|
|Utilisateurs et groupes|Inclure|Sélectionner des utilisateurs et des groupes : sélectionnez un groupe de sécurité spécifique contenant les utilisateurs ciblés|Commencer avec un groupe de sécurité comprenant les utilisateurs pilotes|
||Exclure|Groupe de sécurité d’exception ; comptes de service (identités d’application)|Appartenance modifiée en fonction de vos besoins temporaires|
|Applications cloud|Inclure|Sélectionnez les applications auxquelles cette règle doit s’appliquer. Par exemple, sélectionnez Office 365 Exchange Online||
|Conditions|Configuré|Oui|Les configurer en fonction de votre environnement et de vos besoins spécifiques|
|Risque de connexion|Niveau de risque||Consultez les conseils dans le tableau suivant.|

**Risque de connexion**

Appliquez les paramètres en fonction du niveau de protection que vous ciblez.

|Propriété|Niveau de protection|Valeurs|Remarques|
|:---|:---------|:-----|:----|
|Niveau de risque|Baseline|Élevé, moyen|Cocher les deux|
| |Sensible|Élevé, moyen, faible|Cocher les trois|
| |Hautement réglementé| |Laissez toutes les options désactivées pour toujours appliquer l’authentification multifacteur|

**Contrôles d’accès**

|Type|Propriétés|Valeurs|Remarques|
|:---|:---------|:-----|:----|
|Accorder|Accorder l'accès|Vrai|Sélectionné|
||Exiger MFA|True|Check|
||Exiger que l’appareil soit marqué comme conforme|False||
||Exiger un appareil joint Azure AD hybride|False||
||Exiger une application client approuvée|False||
||Demander tous les contrôles sélectionnés|True|Sélectionné|

> [!NOTE]
> N’oubliez pas d’activer cette stratégie en sélectionnant **activé**. Vous pouvez également utiliser l’outil [What If](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-whatif) pour tester la stratégie.



## <a name="block-clients-that-dont-support-modern-authentication"></a>Bloquer les clients ne prenant pas en charge l’authentification moderne
1. Accédez au [portail Azure](https://portal.azure.com) et connectez-vous avec vos informations d’identification. Une fois connecté, le tableau de bord Azure s’affiche.

2. Dans le menu de gauche, choisissez **Azure Active Directory**.

3. Sous la section **Sécurité**, choisissez **Accès conditionnel**.

4. Choisissez **Nouvelle stratégie**.

Le tableau suivant décrit les paramètres de stratégie d’accès conditionnel à implémenter pour cette stratégie.

**Affectations**

|Type|Propriétés|Valeurs|Remarques|
|:---|:---------|:-----|:----|
|Utilisateurs et groupes|Include|Sélectionner des utilisateurs et des groupes : sélectionnez un groupe de sécurité spécifique contenant les utilisateurs ciblés|Commencer avec un groupe de sécurité comprenant les utilisateurs pilotes|
||Exclure|Groupe de sécurité d’exception ; comptes de service (identités d’application)|Appartenance modifiée de manière temporaire selon les besoins|
|Applications cloud|Include|Sélectionnez les applications auxquelles cette règle doit s’appliquer. Par exemple, sélectionnez Office 365 Exchange Online||
|Conditions|Configuré|Oui|Configurer les applications clientes|
|Applications clientes|Configuré|Oui|Applications mobiles et clients de bureau, autres clients (sélectionnez les deux)|

**Contrôles d’accès**

|Type|Propriétés|Valeurs|Remarques|
|:---|:---------|:-----|:----|
|Accorder|Bloquer l’accès|Vrai|Sélectionné|
||Exiger MFA|False||
||Exiger que l’appareil soit marqué comme conforme|False||
||Exiger un appareil joint Azure AD hybride|False||
||Exiger une application client approuvée|False||
||Demander tous les contrôles sélectionnés|True|Sélectionné|

> [!NOTE]
> N’oubliez pas d’activer cette stratégie en sélectionnant **activé**. Vous pouvez également utiliser l’outil [What If](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-whatif) pour tester la stratégie.



## <a name="high-risk-users-must-change-password"></a>Les utilisateurs à haut risque doivent changer leur mot de passe
Pour vous assurer que tous les comptes compromis par les utilisateurs à haut risque sont obligés d’effectuer une modification de mot de passe lors de la connexion, vous devez appliquer la stratégie suivante.

Connectez-vous au [portail Microsoft Azure (https://portal.azure.com)](https://portal.azure.com/) avec vos informations d’identification d’administrateur, puis accédez à **Azure AD Identity Protection > Stratégie d’utilisateur à risque**.

**Affectations**

|Type|Propriétés|Valeurs|Remarques|
|:---|:---------|:-----|:----|
|Utilisateurs|Inclure|Tous les utilisateurs|Sélectionné|
||Exclure|Aucune||
|Conditions|Risque de l’utilisateur|Importante|Sélectionné|

**Contrôles**

| Type | Propriétés | Valeurs                  | Remarques |
|:-----|:-----------|:------------------------|:------|
|      | Accès     | Autoriser l'accès            | Vrai  |
|      | Accès     | Exiger le changement du mot de passe | True  |

**Révision :** non applicable

> [!NOTE]
> N’oubliez pas d’activer cette stratégie en sélectionnant **activé**. Vous pouvez également utiliser l’outil [What If](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-whatif) pour tester la stratégie.

## <a name="define-app-protection-policies"></a>Définir les stratégies de protection des applications
Les stratégies de protection des applications définissent les applications autorisées et les actions qu’elles peuvent effectuer sur les données de votre organisation. Créez des stratégies Intune App protection à partir du portail Azure. 

Créez une stratégie pour chaque plateforme :
- iOS
- Android
- Windows 10

Pour créer une stratégie de protection des applications, connectez-vous au portail Microsoft Azure avec vos informations d’identification d’administrateur, puis accédez à >  **applications clientes****stratégies de protection**des applications. Choisissez **créer une stratégie**.

Les options de stratégie de protection des applications présentent de légères différences entre iOS et Android. La stratégie ci-dessous est conçue spécifiquement pour Android. Utilisez-le comme guide pour vos autres stratégies.

La liste d’applications recommandée inclut les éléments suivants :
- PowerPoint
- Excel
- Word
- Microsoft Teams
- Microsoft SharePoint
- Visionneuse Microsoft Visio
- OneDrive
- OneNote
- Outlook

Les tableaux suivants décrivent les paramètres recommandés :

|Type|Propriétés|Valeurs|Remarques|
|:---|:---------|:-----|:----|
|Réadressage des données|Interdire la sauvegarde Android|Oui|Sur iOS, ceci appelle spécifiquement iTunes et iCloud|
||Autoriser l'application à transférer des données vers d'autres applications|Applications gérées par la stratégie||
||Autoriser l'application à recevoir des données d'autres applications|Applications gérées par la stratégie||
||Interdire l’option Enregistrer sous|Oui||
||Sélectionnez dans quels services de stockage les données d'entreprise peuvent être enregistrées|OneDrive entreprise, SharePoint||
||Restreindre les opérations Couper, Copier et Coller avec d’autres applications|Applications gérées par une stratégie avec l’application de collage||
||Afficher le contenu web uniquement dans Managed Browser|Non||
||Chiffrer les données de l'application|Oui|Sur iOS, sélectionner l’option Quand l’appareil est verrouillé|
||Désactiver le chiffrement d’application lorsque l’appareil est activé|Oui|Désactivez ce paramètre pour éviter le double chiffrement|
||Désactiver la synchronisation des contacts|Non||
||Désactiver l’impression|Non||
|Accès|Exiger un code confidentiel d’accès|Oui||
||Sélectionner un type|Numérique||
||Autoriser un code PIN simple|Non||
||Longueur du code PIN|6 ||
||Autoriser une empreinte digitale à la place du code confidentiel|Oui||
||Désactiver le code confidentiel de l’application lorsque le code confidentiel de l’appareil est géré|Oui||
||Exiger des informations d’identification d’entreprise pour l’accès|Non||
||Revérifier l’exigence d’accès après (minutes)|0,30||
||Bloquer la capture d’écran et l’Assistant Android|Non|Sur iOS, cette option n’est pas disponible|
|Exigences en matière de sécurité de connexion|Nombre maximal de tentatives de code confidentiel|disque|Réinitialiser le code confidentiel|
||Période de grâce hors connexion|720|Bloquer l’accès|
||Intervalle hors connexion (jours) avant la réinitialisation des données d'application|90|Effacer les données|
||Un jailbreak/périphériques enracinés| |Effacer les données|

Lorsque vous avez terminé, n’oubliez pas de sélectionner « créer ». Répétez les étapes ci-dessus et remplacez la plateforme sélectionnée (dropdown) par iOS. Cela crée deux stratégies d’application, de sorte qu’une fois la stratégie créée, affectez des groupes à la stratégie et déployez-la.

Pour modifier les stratégies et affecter ces stratégies aux utilisateurs, voir [comment créer et affecter des stratégies de protection des applications](https://docs.microsoft.com/intune/app-protection-policies). 

## <a name="require-approved-apps"></a>Exiger les applications approuvées
Pour exiger des applications approuvées :

1. Accédez au [portail Azure](https://portal.azure.com) et connectez-vous avec vos informations d’identification. Une fois connecté, le tableau de bord Azure s’affiche.

2. Dans le menu de gauche, choisissez **Azure Active Directory**.

3. Sous la section **Sécurité**, choisissez **Accès conditionnel**.

4. Choisissez **Nouvelle stratégie**.

5. Entrez un nom de stratégie et choisissez les **Utilisateurs et groupes** auxquels vous souhaitez appliquer la stratégie.

6. Choisissez **Applications cloud**.

7. Sélectionnez **Sélectionner les applications**, sélectionnez les applications souhaitées dans la liste **applications Cloud** . Par exemple, sélectionnez Office 365 Exchange Online. Choisissez **Sélectionner** et **Terminer**.

8. Sélectionnez **conditions**, sélectionnez **plateformes d’appareils**, puis sélectionnez **configurer** .

9. Sous **inclure**, choisissez **Sélectionner les plateformes**de l’appareil, sélectionnez **Android** et **iOS**. Cliquez **** sur OK **, puis** de nouveau sur Terminer.

10. Choisissez **Accorder** dans la section **Contrôles d’accès**.

11. Sélectionnez **accorder l’accès**, sélectionnez **demander une application client approuvée**. Pour plusieurs contrôles, sélectionnez **exiger les contrôles sélectionnés**, puis choisissez **Sélectionner**. 

12. Sélectionnez **Créer**.

## <a name="define-device-compliance-policies"></a>Définir des stratégies de conformité des appareils

Les stratégies de conformité des appareils définissent les exigences auxquelles les appareils doivent adhérer afin d’être marqués comme étant conformes. Créez des stratégies de conformité d’appareil Intune à partir du portail Azure. 

Créez une stratégie pour chaque plateforme :
- Android
- Android Enterprise
- iOS
- OS
- Ce paramètre est disponible sur les types d’appareils suivants :
- Windows 8,1 et versions ultérieures
- Windows 10 et versions ultérieures

Pour créer des stratégies de conformité des appareils, connectez-vous au portail Microsoft Azure avec vos informations d’identification d’administrateur, puis accédez à **Intune > la conformité des appareils**. Sélectionnez **Créer**.

Les paramètres suivants sont recommandés pour Windows 10.

**Intégrité de l’appareil : règles d’évaluation du service d’attestation d’intégrité Windows**

|Propriétés|Valeurs|Remarques|
|:---------|:-----|:----|
|Exiger BitLocker|Require (Rendre obligatoire)||
|Exiger l’activation du démarrage sécurisé sur l’appareil|Require (Rendre obligatoire)||
|Exiger l’intégrité du code|Require (Rendre obligatoire)||


**Propriétés des appareils**

|Type|Propriétés|Valeurs|Remarques|
|:---|:---------|:-----|:----|
|Version du système d'exploitation|Tous|Non configuré||

Pour que toutes les stratégies ci-dessus soient considérées comme déployées, elles doivent cibler des groupes d’utilisateurs. Pour ce faire, vous pouvez créer la stratégie (à l’enregistrement) ou une version ultérieure en sélectionnant **gérer le déploiement** dans la section **stratégie** (même niveau que ajouter).

**Sécurité système**

|Type|Propriétés|Valeurs|Remarques|
|:---|:---------|:-----|:----|
|Password|Exiger un mot de passe pour déverrouiller les appareils mobiles|Require (Rendre obligatoire)||
||Mots de passe simples|Bloc||
||Type de mot de passe|Valeur par défaut du périphérique||
||Longueur minimale du mot de passe|6 ||
||Nombre maximal de minutes d’inactivité avant que le mot de passe ne soit requis|15 |Ce paramètre est pris en charge pour Android versions 4,0 et supérieures ou KNOX 4,0 et versions ultérieures. Pour les appareils iOS, il est pris en charge pour iOS 8,0 et versions ultérieures.|
||Expiration du mot de passe (jours)|41||
||Nombre de mots de passe précédents pour empêcher la réutilisation|disque||
||Exiger un mot de passe lorsque l’appareil revient de l’état inactif (mobile et holographique)|Require (Rendre obligatoire)|Disponible pour Windows 10 et versions ultérieures|
|Chiffrement|Chiffrement du stockage des données sur l’appareil|Require (Rendre obligatoire)||
|Sécurité de l’appareil|-|Require (Rendre obligatoire)||
||Antivirus|Require (Rendre obligatoire)||
||Logiciel anti-espion|Require (Rendre obligatoire)|Ce paramètre nécessite une solution de protection contre les logiciels espions inscrite auprès du centre de sécurité Windows|
|Defender|Logiciel anti-programme malveillant Windows Defender|Require (Rendre obligatoire)||
||Version minimale du logiciel anti-programme malveillant Windows Defender||Uniquement pris en charge pour les ordinateurs de bureau Windows 10. Microsoft recommande une version qui n’est pas plus de cinq par rapport à la version la plus récente.|
||Mise à jour de la signature du logiciel anti-programme malveillant Windows Defender|Require (Rendre obligatoire)||
||Protection en temps réel|Require (Rendre obligatoire)|Prise en charge uniquement pour les ordinateurs de bureau Windows 10|

**Microsoft Defender - PACM**

|Type|Propriétés|Valeurs|Remarques|
|:---|:---------|:-----|:----|
|Règles de protection avancée contre les menaces Microsoft Defender|Exiger que l’appareil soit au ou sous le score de risque machine|Moyenne||

## <a name="require-compliant-pcs-but-not-compliant-phones-and-tablets"></a>Exiger des PC conformes (mais pas les téléphones et les tablettes conformes)
Avant d’ajouter une stratégie pour exiger des PC conformes, veillez à inscrire les appareils pour la gestion dans Intune. L’utilisation de l’authentification multifacteur est recommandée avant l’inscriptions de périphériques dans Intune pour garantir que l’appareil est en possession de l’utilisateur prévu. 

Pour exiger des PC conformes :

1. Accédez au [portail Azure](https://portal.azure.com) et connectez-vous avec vos informations d’identification. Une fois connecté, le tableau de bord Azure s’affiche.

2. Dans le menu de gauche, choisissez **Azure Active Directory**.

3. Sous la section **Sécurité**, choisissez **Accès conditionnel**.

4. Choisissez **Nouvelle stratégie**.

5. Entrez un nom de stratégie et choisissez les **Utilisateurs et groupes** auxquels vous souhaitez appliquer la stratégie.

6. Choisissez **Applications cloud**.

7. Sélectionnez **Sélectionner les applications**, sélectionnez les applications souhaitées dans la liste **applications Cloud** . Par exemple, sélectionnez Office 365 Exchange Online. Choisissez **Sélectionner** et **Terminer**.

8. Pour exiger des PC conformes, mais pas des téléphones et des tablettes conformes, choisissez des **conditions** et des **plateformes d’appareil**. Sélectionnez **Sélectionner les plateformes** de l’appareil, puis **Windows** et **MacOS**.

9. Choisissez **Accorder** dans la section **Contrôles d’accès**.

10. Sélectionnez **accorder l’accès**, sélectionnez **exiger la conformité de l’appareil pour être marqué comme conforme**. Pour plusieurs contrôles, sélectionnez **exiger tous les contrôles sélectionnés**, puis choisissez **Sélectionner**. 

11. Sélectionnez **Créer**.

Si votre objectif est d’exiger des PC conformes *et des* appareils mobiles, ne sélectionnez pas de plateformes. Cela garantit la conformité de tous les appareils. 

## <a name="require-compliant-pcs-and-mobile-devices"></a>Exiger des PC conformes *et des* appareils mobiles

Pour exiger la conformité de tous les périphériques, procédez comme suit :

1. Accédez au [portail Azure](https://portal.azure.com) et connectez-vous avec vos informations d’identification. Une fois connecté, le tableau de bord Azure s’affiche.

2. Dans le menu de gauche, choisissez **Azure Active Directory**.

3. Sous la section **Sécurité**, choisissez **Accès conditionnel**.

4. Choisissez **Nouvelle stratégie**.

5. Entrez un nom de stratégie et choisissez les **Utilisateurs et groupes** auxquels vous souhaitez appliquer la stratégie.

6. Choisissez **Applications cloud**.

7. Sélectionnez **Sélectionner les applications**, sélectionnez les applications souhaitées dans la liste **applications Cloud** . Par exemple, sélectionnez Office 365 Exchange Online. Choisissez **Sélectionner** et **Terminer**.

8. Choisissez **Accorder** dans la section **Contrôles d’accès**.

9. Sélectionnez **accorder l’accès**, sélectionnez **exiger la conformité de l’appareil pour être marqué comme conforme**. Pour plusieurs contrôles, sélectionnez **exiger tous les contrôles sélectionnés**, puis choisissez **Sélectionner**. 

10. Sélectionnez **Créer**.

Lors de la création de cette stratégie, ne sélectionnez pas de plateformes. Cela met en place des appareils conformes.


## <a name="next-steps"></a>Étapes suivantes

[Découvrir les recommandations de stratégies pour sécuriser les e-mails](secure-email-recommended-policies.md)
