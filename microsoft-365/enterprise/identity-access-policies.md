---
title: Identité et périphérique courants accéder aux stratégies - Microsoft 365 entreprise | Documents Microsoft
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
ms.openlocfilehash: ab8454c27cd57b6bd5cc8df6e1526ee2950ac998
ms.sourcegitcommit: e491c4713115610cbe13d2fbd0d65e1a41c34d62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "26867474"
---
# <a name="common-identity-and-device-access-policies"></a>Stratégies communes pour les identités et l’accès aux appareils
Cet article décrit commun recommandé de stratégies pour sécuriser l’accès pour le cloud services, y compris les applications locales publiés avec le Proxy d’Application Azure AD. 

Ce guide explique comment déployer les stratégies recommandées dans un environnement nouvellement mis en service. Configuration de ces stratégies dans un environnement de laboratoire distinct vous permet de comprendre et d’évaluer les stratégies recommandées avant le déploiement sur votre environnement de préproduction et de production de zone de transit. Votre environnement nouvellement mis en service peut être uniquement en nuage ou hybrides.  

## <a name="policy-set"></a>Jeu de stratégie 

Le diagramme suivant illustre le jeu de stratégies recommandé. Il indique le niveau de protection chaque stratégie s’applique à et si les stratégies s’appliquent à PC, téléphones et tablettes ou les deux catégories de périphériques. Il indique également où ces stratégies sont configurées.

![Stratégies courantes pour configurer l’accès d’identité et de périphérique](../images/Identity_device_access_policies_byplan.png)


Le reste de cet article explique comment configurer ces stratégies. 

À l’aide de l’authentification multifacteur est recommandé avant inscription périphériques Intune pour l’assurance que le périphérique est en possession de l’utilisateur concerné. Vous devez également inscrire appareils dans Intune avant d’appliquer des stratégies de conformité de périphérique.

Pour donner à temps pour accomplir ces tâches, nous vous recommandons d’implémenter les stratégies de base dans l’ordre indiqué dans ce tableau. Toutefois, les stratégies MFA pour la protection de données sensible et réglementation peuvent être implémentés à tout moment.


|Niveau de protection|Policies|Plus d’informations|
|:---------------|:-------|:----------------|
|**Baseline**|[Exiger MFA lors de la connexion risque est *moyen* ou *élevé*](#require-mfa-based-on-sign-in-risk)| |
|        |[Blocage des clients qui ne prennent pas en charge l’authentification moderne](#block-clients-that-dont-support-modern-authentication)|Les clients qui n’utilisent pas l’authentification moderne peuvent contourner les règles d’accès conditionnel, il est important de bloquer les messages|
|        |[Utilisateurs à haut risque doivent changer le mot de passe](#high-risk-users-must-change-password)|Oblige les utilisateurs à modifier leur mot de passe lors de la connexion en cas de détection d’activités à haut risque pour leur compte|
|        |[Définir des stratégies de protection des applications](#define-app-protection-policies)|Une stratégie par la plate-forme (iOS, Android, Windows).|
|        |[Exiger des applications approuvées](#require-approved-apps)|Applique la protection des applications mobiles pour les téléphones et les tablettes|
|        |[Définir des stratégies de conformité de périphérique](#define-device-compliance-policies)|Une stratégie pour chaque plateforme|
|        |[Exiger compatible PC](#require-compliant-pcs-but-not-compliant-phones-and-tablets)|Applique une gestion Intune de PC|
|**Sensible**|[Exiger MFA lors de la connexion risque est *faible*, *moyen* ou *élevé*](#require-mfa-based-on-sign-in-risk)| |
|         |[Exiger compatible PC *et* appareils mobiles](#require-compliant-pcs-and-mobile-devices)|Applique la gestion Intune pour PC et téléphone/tablettes|
|**Hautement réglementé**|[*Toujours* nécessitent MFA](#require-mfa-based-on-sign-in-risk)|
| | |

## <a name="assigning-policies-to-users"></a>Attribution de stratégies pour les utilisateurs
Avant de configurer des stratégies, identifier les groupes d’Azure Active Directory que vous utilisez pour chaque niveau de protection. En règle générale, la protection planifié s’applique à tout le monde dans l’organisation. Un utilisateur qui est inclus dans la ligne de base et protection sensible comportera toutes les stratégies de base appliqués ainsi que les stratégies sensibles. Protection est cumulative et la stratégie la plus restrictive est appliquée. 

Une pratique recommandée consiste à créer un groupe d’Azure AD à l’exclusion d’accès conditionnel. Ajoutez ce groupe à toutes les règles d’accès conditionnelle sous « Exclure ». Cela vous donne une méthode pour fournir l’accès à un utilisateur pendant que vous résoudre les problèmes d’accès. Il est recommandé comme solution temporaire. Contrôler ce groupe pour que les modifications et vérifiez que le groupe d’exclusion est utilisé uniquement comme prévu. 

Le diagramme suivant fournit un exemple d’affectation de l’utilisateur et d’exclusions.

![Affectation d’utilisateur exemple et des exclusions pour les règles MFA](../images/identity-access-policies-assignment.png)

Dans l’illustration le « équipe de projet secrète supérieure X » est affectée à une stratégie d’accès conditionnel nécessitant MFA *toujours*. Être judicieux lors de l’application des niveaux de protection supérieurs aux utilisateurs. Les membres de l’équipe du projet devront fournir deux formes d’authentification chaque fois qu’ils ouvrent une session, même si elles ne voient pas très régulé de contenu.  

Tous les groupes créés dans le cadre de ces recommandations d’Azure AD doivent être créés en tant que groupes d’Office 365. Il s’agit plus particulièrement important pour le déploiement de la Protection d’informations Azure (AIP) lors de la sécurisation des documents dans SharePoint Online.

![Capture d’écran de création de groupes d’Office 365](../images/identity-device-AAD-groups.png)


## <a name="require-mfa-based-on-sign-in-risk"></a>Exiger MFA basée sur les risques de connexion
Avant d’obliger MFA, utiliser une stratégie d’inscription MFA de Protection d’identité pour enregistrer les utilisateurs pour MFA. Une fois que les utilisateurs sont inscrits, vous pouvez appliquer MFA pour la connexion. Le [travail requis](identity-access-prerequisites.md) inclut l’inscription de tous les utilisateurs avec MFA.

Pour créer une stratégie d’accès conditionnel : 

1. Accédez au [portail Azure](https://portal.azure.com)et connectez-vous avec vos informations d’identification. Une fois que vous avez correctement connecté, vous voyez le tableau de bord Azure.

2. Dans le menu de gauche, choisissez **Azure Active Directory**.

3. Sous la section **Sécurité**, choisissez **Accès conditionnel**.

4. Choisissez **Nouvelle stratégie**.

![Stratégie d’accès conditionnel de base de référence](./media/secure-email/CA-EXO-policy-1.png)

 Le tableau suivant décrit les paramètres de stratégie d’accès conditionnel à implémenter pour cette stratégie.

**Affectations**

|Type|Propriétés|Valeurs|Remarques|
|:---|:---------|:-----|:----|
|Utilisateurs et groupes|Inclure|Sélectionner des utilisateurs et des groupes : sélectionnez un groupe de sécurité spécifique contenant les utilisateurs ciblés|Commencer avec un groupe de sécurité comprenant les utilisateurs pilotes|
||Exclure|Groupe de sécurité d’exception ; comptes de service (identités d’application)|Appartenance modifié de manière temporaire selon les besoins|
|Applications cloud|Inclure|Sélectionnez les applications que vous souhaitez appliquer à cette règle. Par exemple, sélectionnez Office 365 Exchange Online||
|Conditions|Configuré|Oui|Les configurer en fonction de votre environnement et de vos besoins spécifiques|
|Risque de connexion|Niveau de risque||Voir les instructions dans le tableau suivant|

**Risque de connexion**

Appliquer les paramètres en fonction du niveau de protection que vous ciblez.

|Propriété|Niveau de protection|Valeurs|Remarques|
|:---|:---------|:-----|:----|
|Niveau de risque|Baseline|Élevé, moyen|Cocher les deux|
| |Sensible|Élevé, moyen, faible|Cocher les trois|
| |Hautement réglementé| |Laissez toutes les options désactivée pour toujours appliquer MFA|

**Contrôles d’accès**

|Type|Propriétés|Valeurs|Remarques|
|:---|:---------|:-----|:----|
|Accorder|Accorder l'accès|True|Sélectionné|
||Exiger MFA|True|Check|
||Exiger l’appareil doit être marqué comme conforme|False||
||Exiger hybride Azure périphérique joint à AD|False||
||Exiger l’application cliente approuvée|False||
||Demander tous les contrôles sélectionnés|True|Sélectionné|

> [!NOTE]
> Veillez à activer cette stratégie, en cliquant **sur**. Considérez également à l’aide de l’outil [que se passe-t-il si](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-whatif) pour tester la stratégie.



## <a name="block-clients-that-dont-support-modern-authentication"></a>Blocage des clients qui ne prennent pas en charge l’authentification moderne
1. Accédez au [portail Azure](https://portal.azure.com)et connectez-vous avec vos informations d’identification. Une fois que vous avez correctement connecté, vous voyez le tableau de bord Azure.

2. Dans le menu de gauche, choisissez **Azure Active Directory**.

3. Sous la section **Sécurité**, choisissez **Accès conditionnel**.

4. Choisissez **Nouvelle stratégie**.

Le tableau suivant décrit les paramètres de stratégie d’accès conditionnel à implémenter pour cette stratégie.

**Affectations**

|Type|Propriétés|Valeurs|Remarques|
|:---|:---------|:-----|:----|
|Utilisateurs et groupes|Inclure|Sélectionner des utilisateurs et des groupes : sélectionnez un groupe de sécurité spécifique contenant les utilisateurs ciblés|Commencer avec un groupe de sécurité comprenant les utilisateurs pilotes|
||Exclure|Groupe de sécurité d’exception ; comptes de service (identités d’application)|Appartenance modifiée de manière temporaire selon les besoins|
|Applications cloud|Inclure|Sélectionnez les applications que vous souhaitez appliquer à cette règle. Par exemple, sélectionnez Office 365 Exchange Online||
|Conditions|Configuré|Oui|Configurer des applications clientes|
|Applications clientes|Configuré|Oui|Les applications mobiles et les clients de bureau, autres clients (Sélectionner les deux)|

**Contrôles d’accès**

|Type|Propriétés|Valeurs|Remarques|
|:---|:---------|:-----|:----|
|Accorder|Bloquer l’accès|True|Sélectionné|
||Exiger MFA|False||
||Exiger l’appareil doit être marqué comme conforme|False||
||Exiger hybride Azure périphérique joint à AD|False||
||Exiger l’application cliente approuvée|False||
||Demander tous les contrôles sélectionnés|True|Sélectionné|

> [!NOTE]
> Veillez à activer cette stratégie, en cliquant **sur**. Considérez également à l’aide de l’outil [que se passe-t-il si](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-whatif) pour tester la stratégie.



## <a name="high-risk-users-must-change-password"></a>Utilisateurs à haut risque doivent changer le mot de passe
Pour vous assurer que les comptes des compromis tous les utilisateurs à haut risque sont obligés pour effectuer une modification de mot de passe lors de la connexion, vous devez appliquer la stratégie suivante.

Connectez-vous à le [portail Microsoft Azure (http://portal.azure.com) ](http://portal.azure.com/) avec vos informations d’identification d’administrateur, puis accédez à **Azure AD identité Protection > stratégie risque de l’utilisateur**.

**Affectations**

|Type|Propriétés|Valeurs|Remarques|
|:---|:---------|:-----|:----|
|Utilisateurs|Inclure|Tous les utilisateurs|Sélectionné|
||Exclure|Aucune||
|Conditions|Risque de l’utilisateur|Importante|Sélectionné|

**Contrôles**

| Type | Propriétés | Valeurs                  | Remarques |
|:-----|:-----------|:------------------------|:------|
|      | Accès     | Autoriser l'accès            | True  |
|      | Accès     | Exiger le changement du mot de passe | True  |

**Révision :** non applicable

> [!NOTE]
> Veillez à activer cette stratégie, en cliquant **sur**. Également prendre en compte à l’aide de l’outil [que se passe-t-il si](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-whatif) pour tester la stratégie

## <a name="define-app-protection-policies"></a>Définir des stratégies de protection des applications
Stratégies de protection des applications permet de définir les applications qui sont autorisées et les actions qu’elle peut prendre des données de votre organisation. Créer des stratégies de protection à partir du portail Azure Intune application. 

Créer une stratégie pour chaque plateforme :
- iOS
- Android
- Windows 10

Pour créer une nouvelle stratégie de protection d’application, connectez-vous au portail Microsoft Azure avec vos informations d’identification d’administration, puis accédez à **applications mobiles > stratégies de protection des applications**. Cliquez sur **Ajouter une stratégie**.

Il existe de légères différences dans la protection de l’application options de stratégie entre iOS et Android. L’au-dessous stratégie est spécifiquement conçu pour Android. Utilisez cette classe comme un guide pour vos autres stratégies.

La liste des applications recommandée inclut les éléments suivants :
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
||Restreindre les opérations Couper, Copier et Coller avec d’autres applications|Applications avec coller dans géré de stratégie||
||Afficher le contenu web uniquement dans Managed Browser|Non||
||Chiffrer les données de l'application|Oui|Sur iOS, sélectionner l’option Quand l’appareil est verrouillé|
||Désactiver le chiffrement de l’application lorsque le périphérique est activé.|Oui|Désactivez ce paramètre pour éviter la double chiffrement|
||Désactiver la synchronisation des contacts|Non||
||Désactiver l’impression|Non||
|Accès|Exiger un code confidentiel d’accès|Oui||
||Sélectionnez Type|Numérique||
||Autoriser un code PIN simple|Non||
||Longueur du code PIN|6||
||Autoriser une empreinte digitale à la place du code confidentiel|Oui||
||Désactiver le code confidentiel d’application lorsque le code confidentiel du périphérique est géré|Oui||
||Exiger des informations d’identification d’entreprise pour l’accès|Non||
||Revérifier l’exigence d’accès après (minutes)|30||
||Bloquer la capture d’écran et l’Assistant Android|Non|Sur iOS, cette option n’est pas disponible|
|Exigences de sécurité de connexion|Tente de code confidentiel max|5|Réinitialiser le code confidentiel|
||Période de grâce hors connexion|720|Bloquer l’accès|
||Intervalle hors connexion (jours) avant la réinitialisation des données d'application|90|Effacer les données|
||Jailbroken/fait en sorte que les périphériques| |Effacer les données|

Lorsque vous avez terminé, pensez à sélectionner « Créer ». Répétez les étapes ci-dessus en remplaçant la plate-forme sélectionnée (liste déroulante) iOS. Cette opération crée deux stratégies d’application, donc une fois que vous créez la stratégie, puis affecter des groupes à la stratégie et la déployer.

Pour modifier les stratégies et affecter ces stratégies aux utilisateurs, voir [comment créer et affecter des stratégies de protection des applications](https://docs.microsoft.com/intune/app-protection-policies). 

## <a name="require-approved-apps"></a>Exiger des applications approuvées
Pour exiger que les applications approuvées :

1. Accédez au [portail Azure](https://portal.azure.com)et connectez-vous avec vos informations d’identification. Une fois que vous avez correctement connecté, vous voyez le tableau de bord Azure.

2. Dans le menu de gauche, choisissez **Azure Active Directory**.

3. Sous la section **Sécurité**, choisissez **Accès conditionnel**.

4. Choisissez **Nouvelle stratégie**.

5. Entrez un nom de stratégie et choisissez les **Utilisateurs et groupes** auxquels vous souhaitez appliquer la stratégie.

6. Choisissez **Applications cloud**.

7. Choisissez **Sélectionner les applications**, sélectionnez les applications de votre choix dans la liste des **applications dans le nuage** . Par exemple, sélectionnez Office 365 Exchange Online. Choisissez **Sélectionnez** **terminé**.

8. Choisissez **Accorder** dans la section **Contrôles d’accès**.

9. Cliquez sur **accorder l’accès**, sélectionnez **Exiger l’approbation de l’application cliente**. Pour plusieurs contrôles, sélectionnez **Exiger les contrôles sélectionnés**, puis choisissez **Sélectionner**. 

10. Sélectionnez **Create (Créer)**.

## <a name="define-device-compliance-policies"></a>Définir des stratégies de conformité de l’appareil

Stratégies de conformité de l’appareil définissent les exigences qui doivent respecter les appareils afin d’être marqué comme conforme. Créer des stratégies de conformité à partir du portail Azure Intune périphérique. 

Créer une stratégie pour chaque plateforme :
- Android
- Entreprise Android
- iOS
- Mac OS
- Windows Phone 8.1
- Windows 8.1 et versions ultérieures
- Windows 10 et versions ultérieures

Pour créer des stratégies de conformité appareil, connectez-vous au portail Microsoft Azure avec vos informations d’identification d’administration, puis accédez à **Intune > conformité périphérique**. Sélectionnez **créer une stratégie**.

Les paramètres suivants sont recommandés pour Windows 10.

**État de santé : règles d’évaluation de Service de Attestation d’intégrité de Windows**

|Propriétés|Valeurs|Remarques|
|:---------|:-----|:----|
|Exiger BitLocker|Require (Rendre obligatoire)||
|Exiger Secure au démarrage être activé sur l’appareil|Require (Rendre obligatoire)||
|Exiger l’intégrité du code|Require (Rendre obligatoire)||


**Propriétés des appareils**

|Type|Propriétés|Valeurs|Remarques|
|:---|:---------|:-----|:----|
|Version du système d'exploitation|Tous|Non configuré||

Pour toutes les stratégies à prendre en considération ci-dessus déployés, ils doivent être ciblés à des groupes d’utilisateurs. Vous pouvez le faire en créant la stratégie (lors de l’enregistrement) ou version ultérieure en sélectionnant **Gérer un déploiement** dans la section **stratégie** (même niveau qu’Ajouter).

**Sécurité système**

|Type|Propriétés|Valeurs|Remarques|
|:---|:---------|:-----|:----|
|Mot de passe|Exiger un mot de passe pour déverrouiller les appareils mobiles|Require (Rendre obligatoire)||
||Mots de passe simples|Bloc||
||Type de mot de passe|Périphérique par défaut||
||Longueur minimale du mot de passe|6||
||Nombre maximal de minutes d’inactivité avant que le mot de passe|15 |Ce paramètre est pris en charge pour Android versions 4.0 et ultérieure ou KNOX 4.0 et versions ultérieures. Pour les appareils iOS, il est pris en charge pour iOS 8.0 et ci-dessus|
||Expiration du mot de passe (jours)|41||
||Nombre de mots de passe précédents pour empêcher la réutilisation|5||
||Demander le mot de passe lorsque le périphérique retourne à partir de l’état est inactif (Mobile et HOLOGRAPHIQUE)|Require (Rendre obligatoire)|Disponibles pour Windows 10 et versions ultérieures|
|Chiffrement|Chiffrement de stockage des données sur le périphérique|Require (Rendre obligatoire)||
|Sécurité des périphériques|Pare-feu|Require (Rendre obligatoire)||
||Antivirus|Require (Rendre obligatoire)||
||AntiSpyware|Require (Rendre obligatoire)|Ce paramètre nécessite une solution contre les logiciels espions inscrit avec le centre de sécurité Windows|
|Defender|Windows Defender contre les logiciels malveillants|Require (Rendre obligatoire)||
||Version minimale de Windows Defender contre les logiciels malveillants||Uniquement pris en charge pour le bureau Windows 10. Microsoft ne recommande de versions aucuns plus de cinq derrière à partir de la version la plus récente|
||Signature contre les logiciels malveillants Windows Defender à jour|Require (Rendre obligatoire)||
||Protection en temps réel|Require (Rendre obligatoire)|Uniquement pris en charge pour le bureau Windows 10|

**Windows Defender ATP**

|Type|Propriétés|Valeurs|Remarques|
|:---|:---------|:-----|:----|
|Règles contre les menaces avancées Windows Defender|Exiger le périphérique soit au niveau ou sous le score de risque de l’ordinateur|Moyenne||

## <a name="require-compliant-pcs-but-not-compliant-phones-and-tablets"></a>Exiger des PC compatible (mais n’est pas compatibles téléphones et tablettes)
Avant d’ajouter une stratégie pour exiger que les ordinateurs conformes, veillez à inscrire des périphériques pour la gestion de Intune. À l’aide de l’authentification multifacteur est recommandé avant inscription périphériques Intune pour l’assurance que le périphérique est en possession de l’utilisateur concerné. 

Pour exiger que les PC compatible :

1. Accédez au [portail Azure](https://portal.azure.com)et connectez-vous avec vos informations d’identification. Une fois que vous avez correctement connecté, vous voyez le tableau de bord Azure.

2. Dans le menu de gauche, choisissez **Azure Active Directory**.

3. Sous la section **Sécurité**, choisissez **Accès conditionnel**.

4. Choisissez **Nouvelle stratégie**.

5. Entrez un nom de stratégie et choisissez les **Utilisateurs et groupes** auxquels vous souhaitez appliquer la stratégie.

6. Choisissez **Applications cloud**.

7. Choisissez **Sélectionner les applications**, sélectionnez les applications de votre choix dans la liste des **applications dans le nuage** . Par exemple, sélectionnez Office 365 Exchange Online. Choisissez **Sélectionnez** **terminé**.

8. Pour exiger que les PC compatible, mais n’est pas compatibles téléphones et tablettes, choisissez **Conditions** et **plateformes d’appareils**. Choisissez **Sélectionner les plateformes d’appareils** et sélectionnez **Windows** et **Mac OS**.

9. Choisissez **Accorder** dans la section **Contrôles d’accès**.

10. Choisissez **accorder l’accès**, sélectionnez **Exiger le périphérique doit être marqué comme conforme**. Pour plusieurs contrôles, sélectionnez **exiger de tous les contrôles sélectionnés**, puis choisissez **Sélectionner**. 

11. Sélectionnez **Create (Créer)**.

Si votre objectif est d’exiger compatible PC *et* appareils mobiles, n’activez pas les plateformes. Il met en œuvre la conformité pour tous les périphériques. 

## <a name="require-compliant-pcs-and-mobile-devices"></a>Exiger compatible PC *et* appareils mobiles

Pour exiger la conformité pour tous les périphériques :

1. Accédez au [portail Azure](https://portal.azure.com)et connectez-vous avec vos informations d’identification. Une fois que vous avez correctement connecté, vous voyez le tableau de bord Azure.

2. Dans le menu de gauche, choisissez **Azure Active Directory**.

3. Sous la section **Sécurité**, choisissez **Accès conditionnel**.

4. Choisissez **Nouvelle stratégie**.

5. Entrez un nom de stratégie et choisissez les **Utilisateurs et groupes** auxquels vous souhaitez appliquer la stratégie.

6. Choisissez **Applications cloud**.

7. Choisissez **Sélectionner les applications**, sélectionnez les applications de votre choix dans la liste des **applications dans le nuage** . Par exemple, sélectionnez Office 365 Exchange Online. Choisissez **Sélectionnez** **terminé**.

8. Choisissez **Accorder** dans la section **Contrôles d’accès**.

9. Choisissez **accorder l’accès**, sélectionnez **Exiger le périphérique doit être marqué comme conforme**. Pour plusieurs contrôles, sélectionnez **exiger de tous les contrôles sélectionnés**, puis choisissez **Sélectionner**. 

10. Sélectionnez **Create (Créer)**.

Lorsque vous créez cette stratégie, n’activez pas les plateformes. Il met en œuvre des périphériques compatibles.




<!---
#### Data loss prevention
The goal for your device and app management policies is to protect data loss in the event of a lost or stolen device. You can do this by ensuring that access to data is protected by a PIN, that the data is encrypted on the device, and that the device is not compromised.

|Policy recommendation|Description|
|:--------------------|:----------|
|**Require user PC management**|Require users to join their Windows PCs to an Active Directory Domain or enroll their PCs into management with Microsoft Intune or System Center Configuration Manager.|
|**Apply security settings via group policy objects (GPO) or Configuration Manager policies for domain joined PCs**|Deploy policies that configure managed PCs to enable BitLocker, enable anti-virus, and enable firewall.|
|**Require user mobile device management**|Require that user devices used to access email are managed by Intune **or** company email is accessed only through mobile email apps protected by Intune App Protection policies such as Outlook for iOS or Android.|
|**Apply an Intune Device Compliance Policy on managed devices**|Apply an Intune Device Compliance Policy for managed corporate mobile devices and Intune-managed PCs that requires: a PIN with minimum length 6, device encryption, a healthy device (is not jailbroken, rooted; passes health attestation), and, if available, require devices that are **low** risk as determined by a third-party MTP like Lookout or SkyCure.|
|**Apply an Intune App Protection Policy for managed apps running on unmanaged devices**|Apply an Intune App Protection Policy for managed apps running on unmanaged, personal mobile devices to require: a PIN with minimum length 6, device encryption, and that the device is healthy (is not jailbroken, rooted; passes health attestation).|

### User impact

For most organizations, it is important to be able to set user expectations around when and for which conditions they will be expected to sign into Office 365 to access their email.  

Users typically benefit from single sign-on (SSO) except during the following situations:
* When requesting authentication tokens for Exchange Online:
  * Users may be asked to MFA whenever a **medium or above** sign-in risk is detected and users has not yet performed MFA in their current sessions.  
  * Users will be required to either use email apps that support the Intune App Protection SDK or access emails from Intune compliant or AD domain-joined devices.
* When users at risk sign-in, and successfully complete MFA, they will be asked to change their password.

## Sensitive
This section describes the recommendations for the sensitive tier of data, identity, and device protection. These recommendations are for customers who have a subset of data that must be protected at higher levels or require all data to be protected at these higher levels.

You can apply increased protection to all or specific data sets in your Office 365 environment. For example, you can apply policies to ensure sensitive data is only shared between protected apps to prevent data loss. We recommend protecting identities and devices that access sensitive data with comparable levels of security.

### Conditional access policy settings
#### Identity protection

You can give users single sign-on (SSO) experience as described in earlier sections. You only need to intervene when necessary based on [risk events](https://docs.microsoft.com/azure/active-directory/active-directory-reporting-risk-events).   

* Require MFA on **low or above** risk sessions
* Require secure password change for high risk users

>[!IMPORTANT]
>[Password synchronization](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-implement-password-synchronization) and [self-service password reset](https://docs.microsoft.com/azure/active-directory/active-directory-passwords) are required for this policy recommendation.
>

#### Data loss prevention

The goal for these device and app management policies is to protect data loss in the event of a lost or stolen device. You can do this by ensuring that access to data is protected by a PIN, that the data is encrypted on the device, and that the device is not compromised.

|Policy recommendation|Description|
|:--------------------|:----------|
|**Require user PC management**|Require users to join their PCs to an Active Directory Domain or enroll their PCs into management with Intune or Configuration Manager and ensure those devices are compliant with policies before allowing email access.|
|**Apply security settings via group policy objects (GPO) or Configuration Manager policies for domain joined PCs**|Deploy policies that configure managed PCs to enable BitLocker, enable anti-virus, and enable firewall.|
|**Require user mobile device management**|Require that user devices used to access email are managed by Intune **or** company email is accessed only through mobile email apps protected by Intune App Protection policies such as Outlook for iOS or Android.|
|**Apply an Intune Device Compliance Policy on managed devices**|Apply an Intune Device Compliance Policy for managed corporate mobile devices and Intune-managed PCs that requires: a PIN with minimum length 6, device encryption, a healthy device (is not jailbroken, rooted; passes health attestation), and if available, require devices that are **low** risk as determined by a third-party MTP like Lookout or SkyCure.|
|**Apply an Intune App Protection Policy for managed apps running on unmanaged devices**|Apply an Intune App Protection Policy for managed apps running on unmanaged, personal mobile devices to require: a PIN with minimum length 6, device encryption, and that the device is healthy (is not jailbroken, rooted; passes health attestation).|

### User impact
For most organizations, it is important to be able to set expectations for users specific to when and under what conditions they will be expected to sign into Office 365 email.

Users typically benefit from single sign-on (SSO) except under the following situations:
* When requesting authentication tokens for Exchange Online:
  * Users will be asked to MFA whenever a **low or above** sign-in risk is detected and users has not yet performed MFA in their current sessions.  
  * Users will be required to either use email apps that support the Intune App Protection SDK or access emails from Intune compliant or AD domain-joined devices.
* When users at risk sign-in, and successfully complete MFA, they will be asked to change their password.

## Highly regulated
This section describes the recommendations for the highly regulated tier of data, identity, and device protection. These recommendations are for customers who may have a very small amount of data that is highly classified, trade secret, or regulated data. Microsoft provides capabilities to help organizations meet these requirements, including added protection for identities and devices.

### Conditional access policy settings
#### Identity protection

For the highly regulated tier Microsoft recommends enforcing MFA for all new sessions.
* Require MFA for all new sessions
* Require secure password change for **high** risk users

>[!IMPORTANT]
>[Password synchronization](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-implement-password-synchronization) and [self-service password reset](https://docs.microsoft.com/azure/active-directory/active-directory-passwords) are required for this policy recommendation.
>

#### Data Loss Prevention
The goal for these device and app management policies is to prevent data loss in the event of a lost or stolen device. This is done by ensuring that access to data is protected by a PIN, that the data is encrypted on the device, and that the device is not compromised.

For the highly regulated tier, we recommend requiring apps that support Intune App Protection policy running only on Intune compliant or domain-joined devices.

|Policy recommendation|Description|
|:--------------------|:----------|
|**Require user PC management**|Require users to join their Windows PCs to an Active Directory Domain, **or** enroll their PCs into management with Intune or Configuration Manager and ensure those devices are compliant with policies before allowing email access.|
|**Apply security settings via group policy objects (GPO) or Configuration Manager policies for domain joined PCs**|Deploy policies that configure managed PCs to enable BitLocker, enable anti-virus, and enable firewall.|
|**Require user mobile device management**|Require that devices used to access Office 365 email and files are managed by Intune or company email is accessed only through mobile email apps protected by Intune App Protection policies such as Outlook for iOS or Android.|
|**Apply an Intune Device Compliance Policy on managed devices**|Apply an Intune Device Compliance Policy for managed corporate mobile devices and Intune-managed PCs that requires: a PIN with minimum length 6, device encryption, a healthy device (is not jailbroken, rooted; passes health attestation), and, if available, require devices that are Low risk as determined by a third-party MTP like Lookout or SkyCure.|

### User impact
For most organizations, it is important to be able to set expectations for users specific to when and under what conditions they will be expected to sign into Office 365 files.

* Users configured as highly regulated will be required to re-authenticate with MFA after their session expires.
* When users at risk sign-in they will be asked to change their password after completing MFA.
* When requesting authentication tokens for Exchange Online:
  * Users will be asked to perform MFA whenever they begin a new session.  
  * Users will be required to use email apps that support the Intune App Protection SDK
  * Users will be required to access emails from Intune compliant or AD domain-joined devices.
--->
## <a name="next-steps"></a>Étapes suivantes

[Découvrir les recommandations de stratégies pour sécuriser les e-mails](secure-email-recommended-policies.md)
