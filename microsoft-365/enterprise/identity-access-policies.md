---
title: Stratégies d’identité et d’accès aux appareils courantes-Microsoft 365 pour les entreprises | Microsoft docs
description: Décrit les stratégies et les configurations d’identité et d’accès aux appareils courantes.
ms.author: josephd
author: JoeDavies-MSFT
manager: Laurawi
ms.prod: microsoft-365-enterprise
ms.topic: article
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
ms.openlocfilehash: 8c4b136f30da0499b31102683f1a903e71813142
ms.sourcegitcommit: 27daadad9ca0f02a833ff3cff8a574551b9581da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "47547220"
---
# <a name="common-identity-and-device-access-policies"></a>Stratégies communes pour les identités et l’accès aux appareils

Cet article décrit les stratégies recommandées courantes pour sécuriser l’accès aux services Cloud de Microsoft 365, notamment les applications locales publiées avec le proxy d’application Azure Active Directory (Azure AD). 

Ce guide explique comment déployer les stratégies recommandées dans un environnement nouvellement mis en service. La configuration de ces stratégies dans un environnement de laboratoire distinct vous permet de comprendre et d’évaluer les stratégies recommandées avant de mettre en place le déploiement dans vos environnements de pré-production et de production. Votre environnement nouvellement configuré peut être en nuage seul ou hybride pour refléter vos besoins d’évaluation.  

## <a name="policy-set"></a>Jeu de stratégie 

Le diagramme suivant illustre l’ensemble de stratégies recommandé. Elle indique le niveau de protection auquel chaque stratégie s’applique et indique si les stratégies s’appliquent aux PC, téléphones et tablettes, ou aux deux catégories d’appareils. Il indique également l’emplacement où vous configurez ces stratégies.

[ ![ Stratégies courantes de configuration de l’identité et de l’accès aux appareils](../media/microsoft-365-policies-configurations/Identity_device_access_policies_byplan.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/microsoft-365-policies-configurations/Identity_device_access_policies_byplan.png) 
 [voir une version plus grande de cette image](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/microsoft-365-policies-configurations/Identity_device_access_policies_byplan.png)

Le reste de cet article explique comment configurer ces stratégies. 

>[!Note]
>Il est recommandé d’exiger l’utilisation de l’authentification multifacteur (MFA) avant d’inscrire des appareils dans Intune afin de s’assurer que l’appareil est en possession de l’utilisateur prévu. Vous devez inscrire des appareils dans Intune pour pouvoir appliquer des stratégies de conformité des appareils.
>

Pour vous donner le temps de réaliser ces tâches, nous vous recommandons de mettre en œuvre les stratégies de base dans l’ordre indiqué dans le tableau ci-dessous. Toutefois, les stratégies de MFA pour des niveaux de protection sensibles et hautement réglementés peuvent être implémentées à tout moment.

|Niveau de protection|Stratégies|Plus d’informations|
|:---------------|:-------|:----------------|
|**Baseline**|[Exiger l’authentification multifacteur lorsque le risque de connexion est *moyen* ou *élevé*](#require-mfa-based-on-sign-in-risk)| |
|        |[Bloquer les clients ne prenant pas en charge l’authentification moderne](#block-clients-that-dont-support-modern-authentication)|Les clients qui n’utilisent pas l’authentification moderne peuvent contourner des stratégies d’accès conditionnel, c’est pourquoi il est important de les bloquer.|
|        |[Les utilisateurs à risque élevé doivent modifier leur mot de passe](#high-risk-users-must-change-password)|Force les utilisateurs à modifier leur mot de passe lors de la connexion en cas de détection d’une activité à haut risque pour leur compte.|
|        |[Appliquer des stratégies de protection des données d’application](#apply-app-data-protection-policies)|Une stratégie de protection des applications Intune par plateforme (Windows, iOS/iPados, Android).|
|        |[Exiger les applications approuvées et la protection des applications](#require-approved-apps-and-app-protection)|Applique la protection des applications mobiles pour les téléphones et les tablettes à l’aide d’iOS, de iPados ou Android.|
|        |[Définir les stratégies de conformité des appareils](#define-device-compliance-policies)|Une stratégie pour chaque plateforme.|
|        |[Exiger des PC conformes](#require-compliant-pcs-but-not-compliant-phones-and-tablets)|Applique la gestion Intune des PC à l’aide de Windows ou de MacOS.|
|**Sensible**|[Exiger l’authentification multifacteur lorsque le risque de connexion est *faible*, *moyen*ou *élevé*](#require-mfa-based-on-sign-in-risk)| |
|         |[Exiger des PC conformes *et des* appareils mobiles](#require-compliant-pcs-and-mobile-devices)|Applique la gestion d’Intune pour les PC (Windows ou MacOS) et les téléphones ou tablettes (iOS, iPados ou Android).|
|**Hautement réglementé**|[*Toujours* exiger l’authentification multifacteur](#require-mfa-based-on-sign-in-risk)|
| | | |

## <a name="assigning-policies-to-groups-and-users"></a>Affectation de stratégies à des groupes et à des utilisateurs

Avant de configurer des stratégies, identifiez les groupes Azure AD que vous utilisez pour chaque niveau de protection. En règle générale, la protection de base s’applique à tous les employés de l’organisation. Toutes les stratégies de base, ainsi que les stratégies sensibles, sont appliquées à un utilisateur qui est inclus à la fois pour la protection de référence et la protection sensible. La protection est cumulative et la stratégie la plus restrictive est appliquée. 

Une pratique recommandée consiste à créer un groupe Azure AD pour l’exclusion d’accès conditionnel. Ajoutez ce groupe à toutes vos stratégies d’accès conditionnel dans la section **exclure** du paramètre **utilisateurs et groupes** de la section **affectations** . Cela vous permet de fournir un accès à un utilisateur pendant que vous dépannez les problèmes d’accès. Il s’agit d’une solution temporaire uniquement. Surveillez ce groupe pour les modifications et assurez-vous que le groupe d’exclusion n’est utilisé que comme prévu. 

Voici un exemple d’affectations et d’exclusions de groupe pour l’authentification MFA.

![Exemple d’affectations et d’exclusions de groupe pour les stratégies MFA](../media/microsoft-365-policies-configurations/identity-access-policies-assignment.png)

Voici les résultats :

- Tous les utilisateurs doivent utiliser MFA lorsque le risque de connexion est moyen ou élevé.

- Les membres du groupe Executive staff doivent utiliser l’authentification multifacteur lorsque le risque de connexion est faible, moyen ou élevé.

  Dans ce cas, les membres du groupe Executive staff correspondent à la fois aux stratégies d’accès conditionnel de base et sensibles. Les contrôles d’accès pour les deux stratégies sont combinés, ce qui est dans ce cas l’équivalent de la stratégie d’accès conditionnel sensible.

- Les membres du groupe top secret Project X doivent toujours utiliser l’authentification multifacteur

  Dans ce cas, les membres du groupe Project secret supérieur X correspondent à la fois aux stratégies de ligne de base et aux stratégies d’accès conditionnel hautement réglementées. Les contrôles d’accès pour les deux stratégies sont combinés. Étant donné que le contrôle d’accès pour la stratégie d’accès conditionnel hautement réglementé est plus restrictif, il est utilisé.

Soyez vigilant lorsque vous appliquez des niveaux de protection plus élevés aux groupes et aux utilisateurs. Par exemple, les membres du groupe top secret Project X devront utiliser MFA à chaque fois qu’ils se connectent, même s’ils ne travaillent pas sur le contenu hautement réglementé pour Project X.  

Tous les groupes Azure AD créés dans le cadre de ces recommandations doivent être créés en tant que groupes Microsoft 365. Ceci est important pour le déploiement des étiquettes de sensibilité lors de la sécurisation des documents dans Microsoft teams et SharePoint.

![Capture d’écran pour la création de groupes Microsoft 365](../media/microsoft-365-policies-configurations/identity-device-AAD-groups.png)

## <a name="require-mfa-based-on-sign-in-risk"></a>Exiger une authentification multifacteur basée sur le risque de connexion

Vos utilisateurs doivent s’inscrire pour l’authentification multifacteur avant d’exiger leur utilisation. Si vous avez Microsoft 365 E5, Microsoft 365 E3 avec l’identité & le module complémentaire protection contre les menaces, Office 365 avec EMS E5 ou des licences Azure AD Premium P2 individuelles, vous pouvez utiliser la stratégie d’inscription MFA avec Azure AD Identity Protection pour exiger que les utilisateurs s’inscrivent à l’authentification multifacteur. Le [travail requis](identity-access-prerequisites.md) inclut l’inscription de tous les utilisateurs avec authentification multifacteur.

Une fois que vous avez enregistré vos utilisateurs, vous pouvez exiger l’authentification MFA pour la connexion avec une nouvelle stratégie d’accès conditionnel.

1. Accédez au [portail Azure](https://portal.azure.com) et connectez-vous avec vos informations d’identification.
2. Dans la liste des services Azure, sélectionnez **Azure Active Directory**.
3. Dans la liste **gérer** , choisissez **sécurité**, puis **accès conditionnel**.
4. Choisissez **nouvelle stratégie** et tapez le nom de la nouvelle stratégie.

Le tableau suivant décrit les paramètres de stratégie d’accès conditionnel pour exiger la fonction MFA en fonction du risque de connexion.

Dans la section **affectations** :

|Paramètres|Propriétés|Valeurs|Remarques|
|:---|:---------|:-----|:----|
|Utilisateurs et groupes|Inclure| **Sélectionnez utilisateurs et groupes > utilisateurs et groupes**: sélectionnez des groupes spécifiques contenant des comptes d’utilisateurs ciblés. |Commencez par le groupe qui inclut les comptes d’utilisateur pilote.|
||Exclure| **Utilisateurs et groupes**: sélectionnez votre groupe d’exceptions d’accès conditionnel ; comptes de service (identités d’application).|L’appartenance doit être modifiée en fonction de vos besoins et de manière temporaire.|
|Actions ou applications Cloud| **Les applications Cloud > incluent** | **Sélectionnez applications**: sélectionnez les applications auxquelles appliquer cette stratégie. Par exemple, sélectionnez Exchange Online.||
|Conditions| | |Configurez les conditions propres à votre environnement et à vos besoins.|
||Risque de connexion||Consultez les conseils dans le tableau suivant.|
|||||

**Paramètres de la condition de risque de connexion**

Appliquez les paramètres de niveau de risque en fonction du niveau de protection que vous ciblez.

|Niveau de protection|Valeurs de niveau de risque requises|Action|
|:---------|:-----|:----|
|Baseline|Élevé, moyen|Cochez les deux.|
|Sensible|Élevé, moyen, faible|Sélectionnez les trois.|
|Hautement réglementé| |Laissez toutes les options désactivées pour toujours appliquer l’authentification multifacteur.|
||||

Dans la section **contrôles d’accès** :

|Paramètres|Propriétés|Valeurs|Action|
|:---|:---------|:-----|:----|
|Accorder|**Grant access**| | Sélectionner |
|||**Exiger l’authentification multifacteur**| Vérifier |
||**Demander tous les contrôles sélectionnés** ||Sélectionner|
|||||

Choisissez **Sélectionner** pour enregistrer les paramètres de **concession** .

Enfin, sélectionnez **activé** pour **activer la stratégie**, puis **créer**.

Vous pouvez également utiliser l’outil [What If](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-whatif) pour tester la stratégie.

## <a name="block-clients-that-dont-support-modern-authentication"></a>Bloquer les clients ne prenant pas en charge l’authentification moderne

Utilisez les paramètres de ces tableaux pour une stratégie d’accès conditionnel afin de bloquer les clients qui ne prennent pas en charge l’authentification moderne.

Consultez [cet article](microsoft-365-client-support-modern-authentication.md) pour obtenir la liste des clients de Microsoft 365 qui effectuent une authentification moderne suppport.

Dans la section **affectations** :

|Paramètres|Propriétés|Valeurs|Remarques|
|:---|:---------|:-----|:----|
|Utilisateurs et groupes|Inclure| **Sélectionnez utilisateurs et groupes > utilisateurs et groupes**: sélectionnez des groupes spécifiques contenant des comptes d’utilisateurs ciblés. |Commencez par le groupe qui inclut les comptes d’utilisateur pilote.|
||Exclure| **Utilisateurs et groupes**: sélectionnez votre groupe d’exceptions d’accès conditionnel ; comptes de service (identités d’application).|L’appartenance doit être modifiée en fonction de vos besoins et de manière temporaire.|
|Actions ou applications Cloud|**Les applications Cloud > incluent**| **Sélectionnez applications**: sélectionnez les applications correspondant aux clients qui ne prennent pas en charge l’authentification moderne.||
|Conditions| **Applications clientes** | Choisissez **Oui** pour **configurer** <br> Désactivez les cases à cocher pour le **navigateur** et **les applications mobiles et les clients de bureau** | |
||||

Dans la section **contrôles d’accès** :

|Paramètres|Propriétés|Valeurs|Action|
|:---|:---------|:-----|:----|
|Accorder|**Bloquer l’accès**| | Sélectionner |
||**Demander tous les contrôles sélectionnés** ||Sélectionner|
|||||

Choisissez **Sélectionner** pour enregistrer les paramètres de **concession** .

Enfin, sélectionnez **activé** pour **activer la stratégie**, puis **créer**.

Envisagez d’utiliser l’outil [What If](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-whatif) pour tester la stratégie.

## <a name="high-risk-users-must-change-password"></a>Les utilisateurs à risque élevé doivent modifier leur mot de passe

Pour vous assurer que tous les comptes compromis par les utilisateurs à haut risque sont obligés d’effectuer une modification de mot de passe lors de la connexion, vous devez appliquer la stratégie suivante.

Connectez-vous au [portail Microsoft Azure (https://portal.azure.com)](https://portal.azure.com/) avec vos informations d’identification d’administrateur, puis accédez à **Azure AD Identity Protection > Stratégie d’utilisateur à risque**.

Dans la section **affectations** :

|Type|Propriétés|Valeurs|Action|
|:---|:---------|:-----|:----|
|Utilisateurs|Inclure|**Tous les utilisateurs**|Sélectionner|
|Risque de l’utilisateur| **High**||Sélectionner|
|||||

Dans la deuxième section **affectations** :

| Type | Propriétés | Valeurs                  | Action |
|:-----|:-----------|:------------------------|:------|
| Access | **Autoriser l’accès** |  | Sélectionner  |
|      |     | **Exiger le changement du mot de passe** | Vérifier  |
|||||

Sélectionnez **Terminer** pour enregistrer les paramètres d' **accès** .

Enfin, sélectionnez **activé** pour **appliquer la stratégie**, puis **Enregistrer**.

Envisagez d’utiliser l’outil [What If](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-whatif) pour tester la stratégie.

Utilisez cette stratégie conjointement à la [configuration de la protection par mot de passe Azure ad](https://docs.microsoft.com/azure/active-directory/authentication/concept-password-ban-bad), qui détecte et bloque les mots de passe faibles connus et leurs variantes, ainsi que d’autres termes faibles propres à votre organisation. L’utilisation de la protection par mot de passe Azure AD garantit que les mots de passe modifiés sont forts.

## <a name="apply-app-data-protection-policies"></a>Appliquer des stratégies de protection des données d’application

Les stratégies de protection des applications (APP) définissent les applications autorisées et les actions qu’elles peuvent effectuer sur les données de votre organisation. Les choix disponibles dans l’application permettent aux organisations de personnaliser la protection en fonction de leurs besoins spécifiques. Pour certains, il se peut que les paramètres de stratégie requis pour implémenter un scénario complet ne soient pas évidents. Pour aider les organisations à hiérarchiser le renforcement des points de terminaison des clients mobiles, Microsoft a introduit la taxonomie de son application Data Protection Framework pour iOS et Android Mobile App Management. 

L’infrastructure Data Protection Framework est organisée en trois niveaux de configuration distincts, chaque niveau étant créé à partir du niveau précédent : 

- La **protection des données de base d’entreprise** (niveau 1) garantit que les applications sont protégées par un code confidentiel et qu’elles sont chiffrées et effectue des opérations de réinitialisation sélective. Pour les appareils Android, ce niveau valide l’attestation d’appareil Android. Il s’agit d’une configuration de niveau d’entrée qui fournit un contrôle de protection des données similaire dans les stratégies de boîte aux lettres Exchange Online et l’affiche, ainsi que la population de l’utilisateur vers l’application. 
- **Enterprise Enhanced Data Protection** (niveau 2) présente les mécanismes de prévention des fuites de données d’application et les exigences minimales en matière de système d’exploitation. Il s’agit de la configuration applicable à la plupart des utilisateurs mobiles qui accèdent aux données professionnelles ou scolaires. 
- **Enterprise High Data Protection** (niveau 3) présente des mécanismes avancés de protection des données, une configuration de code confidentiel améliorée et une défense contre les menaces pour les applications mobiles. Cette configuration est souhaitable pour les utilisateurs qui accèdent à des données à haut risque. 

Pour voir les recommandations spécifiques pour chaque niveau de configuration et les applications minimales à protéger, examinez [Data Protection Framework à l’aide de stratégies de protection des applications](https://docs.microsoft.com/mem/intune/apps/app-protection-framework). 

À l’aide des principes décrits dans les [configurations d’identité et d’accès aux appareils](microsoft-365-policies-configurations.md), les niveaux de protection de base et sensibles sont mappés en étroite collaboration avec les paramètres de protection avancée des données de niveau 2 entreprise. Le niveau de protection hautement réglementé est étroitement associé aux paramètres de protection des données élevés de niveau 3.

|Niveau de protection |Stratégie de protection des applications  |Plus d’informations  |
|---------|---------|---------|
|Baseline     | [Niveau 2 protection des données améliorée](https://docs.microsoft.com/mem/intune/apps/app-protection-framework#level-2-enterprise-enhanced-data-protection)        | Les paramètres de stratégie appliqués au niveau 2 incluent tous les paramètres de stratégie recommandés pour le niveau 1 et ajoutent ou met à jour uniquement les paramètres de stratégie ci-dessous pour implémenter davantage de contrôles et une configuration plus sophistiquée que le niveau 1.         |
|Sensible     | [Niveau 2 protection des données améliorée](https://docs.microsoft.com/mem/intune/apps/app-protection-framework#level-2-enterprise-enhanced-data-protection)        | Les paramètres de stratégie appliqués au niveau 2 incluent tous les paramètres de stratégie recommandés pour le niveau 1 et ajoutent ou met à jour uniquement les paramètres de stratégie ci-dessous pour implémenter davantage de contrôles et une configuration plus sophistiquée que le niveau 1.        |
|Hautement réglementé     | [Niveau 3 entreprise protection élevée des données](https://docs.microsoft.com/mem/intune/apps/app-protection-framework#level-3-enterprise-high-data-protection)        | Les paramètres de stratégie appliqués au niveau 3 incluent tous les paramètres de stratégie recommandés pour le niveau 1 et 2 et ajoutent ou met à jour uniquement les paramètres de stratégie ci-dessous pour implémenter davantage de contrôles et une configuration plus sophistiquée que le niveau 2.        |

Pour créer une stratégie de protection des applications pour chaque plateforme (iOS et Android) dans le gestionnaire de points de terminaison de Microsoft à l’aide des paramètres Data Protection Framework, vous pouvez effectuer les opérations suivantes :

1. Créez manuellement les stratégies en suivant les étapes de la [procédure de création et de déploiement des stratégies de protection des applications avec Microsoft Intune](https://docs.microsoft.com/mem/intune/apps/app-protection-policies). 
2. Importez les modèles JSON de l’exemple de [configuration de stratégie de protection des applications Intune App](https://github.com/microsoft/Intune-Config-Frameworks/tree/master/AppProtectionPolicies) avec les [scripts PowerShell d’Intune](https://github.com/microsoftgraph/powershell-intune-samples).

## <a name="require-approved-apps-and-app-protection"></a>Exiger les applications approuvées et la protection des applications

Pour appliquer les stratégies de protection des applications que vous avez appliquées dans Intune, vous devez créer une stratégie d’accès conditionnel pour exiger les applications client approuvées et les conditions définies dans les stratégies de protection des applications. 

L’application des stratégies de protection des applications nécessite un ensemble de stratégies décrit dans in [require application protection Policy for Cloud App Access with ConditionalAttribute Access](https://docs.microsoft.com/azure/active-directory/conditional-access/app-protection-based-conditional-access). Ces stratégies sont incluses dans cet ensemble recommandé de stratégies de configuration des identités et des accès.

Pour créer la stratégie d’accès conditionnel qui requiert les applications approuvées et la protection de l’application, suivez « étape 1 : configurer une stratégie d’accès conditionnel Azure AD pour Microsoft 365 » dans le [scénario 1 : les applications microsoft 365 nécessitent des applications approuvées avec des stratégies de protection des applications](https://docs.microsoft.com/azure/active-directory/conditional-access/app-protection-based-conditional-access#scenario-1-office-365-apps-require-approved-apps-with-app-protection-policies), ce qui permet à Outlook pour iOS et Android de se connecter à Exchange Online.

   > [!NOTE]
   > Cette stratégie permet aux utilisateurs mobiles d’accéder à tous les points de terminaison Office à l’aide des applications applicables.

Si vous activez l’accès mobile à Exchange Online, implémentez [bloquer les clients ActiveSync](secure-email-recommended-policies.md#block-activesync-clients), ce qui empêche les clients Exchange ActiveSync qui utilisent l’authentification de base de se connecter à Exchange Online. Cette stratégie n’est pas représentée dans l’illustration en haut de cet article. Elle est décrite et illustrée dans la rubrique [recommandations de stratégie pour la sécurisation des courriers électroniques](secure-email-recommended-policies.md).

 Ces stratégies exploitent les contrôles d’octroi [nécessitent une application client approuvée](https://docs.microsoft.com/azure/active-directory/conditional-access/concept-conditional-access-grant#require-approved-client-app) et [nécessitent une stratégie de protection des applications](https://docs.microsoft.com/azure/active-directory/conditional-access/concept-conditional-access-grant#require-app-protection-policy).

Enfin, le blocage de l’authentification héritée pour d’autres applications clientes sur les appareils iOS et Android garantit que ces clients ne peuvent pas contourner les stratégies d’accès conditionnel. Si vous suivez les instructions de cet article, vous avez déjà configuré [bloquer les clients qui ne prennent pas en charge l’authentification moderne](#block-clients-that-dont-support-modern-authentication).

<!---
With Conditional Access, organizations can restrict access to approved (modern authentication capable) iOS and Android client apps with Intune app protection policies applied to them. Several Conditional Access policies are required, with each policy targeting all potential users. Details on creating these policies can be found in [Require app protection policy for cloud app access with Conditional Access](https://docs.microsoft.com/azure/active-directory/conditional-access/app-protection-based-conditional-access).

1. Follow "Step 1: Configure an Azure AD Conditional Access policy for Microsoft 365" in [Scenario 1: Microsoft 365 apps require approved apps with app protection policies](https://docs.microsoft.com/azure/active-directory/conditional-access/app-protection-based-conditional-access#scenario-1-office-365-apps-require-approved-apps-with-app-protection-policies), which allows Outlook for iOS and Android, but blocks OAuth capable Exchange ActiveSync clients from connecting to Exchange Online.

   > [!NOTE]
   > This policy ensures mobile users can access all Office endpoints using the applicable apps.

2. If enabling mobile access to Exchange Online, implement [Block ActiveSync clients](secure-email-recommended-policies.md#block-activesync-clients), which prevents Exchange ActiveSync clients leveraging basic authentication from connecting to Exchange Online.

   The above policies leverage the grant controls [Require approved client app](https://docs.microsoft.com/azure/active-directory/conditional-access/concept-conditional-access-grant#require-approved-client-app) and [Require app protection policy](https://docs.microsoft.com/azure/active-directory/conditional-access/concept-conditional-access-grant#require-app-protection-policy).

3. Disable legacy authentication for other client apps on iOS and Android devices. For more information, see [Block clients that don't support modern authentication](#block-clients-that-dont-support-modern-authentication).
-->

## <a name="define-device-compliance-policies"></a>Définir des stratégies de conformité des appareils

Les stratégies de conformité des appareils définissent les exigences auxquelles les périphériques doivent répondre pour être considérées comme conformes. Vous créez des stratégies de conformité d’appareil Intune à partir du centre d’administration du gestionnaire de points de terminaison Microsoft.

Vous devez créer une stratégie pour chaque PC, téléphone ou plateforme de tablette :

- Administrateur d’appareils Android
- Android Enterprise
- iOS/iPad
- macOS
- Windows 8,1 et versions ultérieures
- Windows 10 et versions ultérieures

Pour créer des stratégies de conformité des appareils, connectez-vous au [Centre d’administration du gestionnaire de points de terminaison Microsoft](https://endpoint.microsoft.com) avec vos informations d’identification d’administrateur, puis accédez à périphériques stratégies de conformité des **appareils**  >  **Compliance policies**  >  **Policies**. Sélectionnez **créer une stratégie**.

Pour que les stratégies de conformité des appareils soient déployées, elles doivent être affectées à des groupes d’utilisateurs. Vous affectez une stratégie après l’avoir créée et enregistrée. Dans le centre d’administration, sélectionnez la stratégie, puis sélectionnez **affectations**. Après avoir sélectionné les groupes pour lesquels vous souhaitez recevoir la stratégie, sélectionnez **Enregistrer** pour enregistrer l’affectation de groupe et déployer la stratégie.

Pour obtenir des instructions pas à pas sur la création de stratégies de conformité dans Intune, voir [Create a Compliance Policy in Microsoft Intune](https://docs.microsoft.com/mem/intune/protect/create-compliance-policy) dans la documentation Intune.

### <a name="recommended-settings-for-windows-10-and-later"></a>Paramètres recommandés pour Windows 10 et versions ultérieures

Les paramètres suivants sont recommandés pour les PC exécutant Windows 10 et versions ultérieures, comme configuré à l' **étape 2 : paramètres de conformité**, du processus de création de la stratégie.

Pour l’intégrité de l' **appareil > les règles d’évaluation du service d’attestation d’intégrité Windows**, consultez ce tableau.

|Propriétés|Valeur|Action|
|:---------|:-----|:----|
|Exiger BitLocker|Require (Rendre obligatoire)| Sélectionner |
|Exiger l’activation du démarrage sécurisé sur l’appareil|Require (Rendre obligatoire)| Sélectionner |
|Exiger l’intégrité du code|Require (Rendre obligatoire)| Sélectionner |
||||

Pour les **Propriétés du périphérique**, spécifiez les valeurs appropriées pour les versions du système d’exploitation en fonction de vos stratégies de sécurité et informatique.

Pour **la conformité de Configuration Manager**, sélectionnez **exiger**.

Pour la **sécurité du système**, reportez-vous à ce tableau.

|Type|Propriétés|Valeur|Action|
|:---|:---------|:-----|:----|
|Password|Exiger un mot de passe pour déverrouiller les appareils mobiles|Require (Rendre obligatoire)| Sélectionner |
||Mots de passe simples|Bloquer|Sélectionner|
||Type de mot de passe|Valeur par défaut du périphérique|Sélectionner|
||Longueur minimale du mot de passe|6 |Type|
||Nombre maximal de minutes d’inactivité avant que le mot de passe ne soit requis|15 |Type <br>Ce paramètre est pris en charge pour Android versions 4,0 et supérieures ou KNOX 4,0 et versions ultérieures. Pour les appareils iOS, il est pris en charge pour iOS 8,0 et versions ultérieures.|
||Expiration du mot de passe (jours)|41|Type|
||Nombre de mots de passe précédents pour empêcher la réutilisation|5 |Type|
||Exiger un mot de passe lorsque l’appareil revient de l’état inactif (mobile et holographique)|Require (Rendre obligatoire)|Disponible pour Windows 10 et versions ultérieures|
|Chiffrement|Chiffrement du stockage des données sur l’appareil|Require (Rendre obligatoire)|Sélectionner|
|Sécurité de l’appareil|-|Require (Rendre obligatoire)|Sélectionner|
||Antivirus|Require (Rendre obligatoire)|Sélectionner|
||Logiciel anti-espion|Require (Rendre obligatoire)|Sélectionner <br> Ce paramètre nécessite une solution de protection contre les logiciels espions inscrite auprès du centre de sécurité Windows.|
|Defender|Logiciel anti-programme malveillant Microsoft Defender|Require (Rendre obligatoire)|Sélectionner|
||Version minimale du logiciel anti-programme malveillant de Microsoft Defender||Type <br> Uniquement pris en charge pour les ordinateurs de bureau Windows 10. Microsoft recommande une version qui n’est pas plus de cinq par rapport à la version la plus récente.|
||Mise à jour de la signature du logiciel anti-programme malveillant Microsoft Defender|Require (Rendre obligatoire)|Sélectionner|
||Protection en temps réel|Require (Rendre obligatoire)|Sélectionner <br>Prise en charge uniquement pour les ordinateurs de bureau Windows 10|
|||||

**Microsoft Defender - PACM**

|Type|Propriétés|Valeur|Action|
|:---|:---------|:-----|:----|
|Règles de protection avancée contre les menaces Microsoft Defender|Exiger que l’appareil soit au ou sous le score de risque machine|Moyen|Sélectionner|
|||||

## <a name="require-compliant-pcs-but-not-compliant-phones-and-tablets"></a>Exiger des PC conformes (mais pas les téléphones et les tablettes conformes)

Avant d’ajouter une stratégie pour exiger des PC conformes, veillez à inscrire les appareils pour la gestion dans Intune. L’utilisation de l’authentification multifacteur est recommandée avant l’inscriptions de périphériques dans Intune pour garantir que l’appareil est en possession de l’utilisateur prévu. 

Pour exiger des PC conformes :

1. Accédez au [portail Azure](https://portal.azure.com) et connectez-vous avec vos informations d’identification.
2. Dans la liste des services Azure, sélectionnez **Azure Active Directory**.
3. Dans la liste **gérer** , choisissez **sécurité**, puis **accès conditionnel**.
4. Choisissez **nouvelle stratégie** et tapez le nom de la nouvelle stratégie.

5. Sous **affectations**, choisissez **utilisateurs et groupes** et indiquez les personnes auxquelles la stratégie doit s’appliquer. Excluez également votre groupe d’exclusion d’accès conditionnel.

6. Sous **affectations**, sélectionnez **applications ou actions Cloud**.

7. Pour **inclure**, choisissez **sélectionner les applications > sélectionnez**, puis sélectionnez les applications souhaitées dans la liste **applications Cloud** . Par exemple, sélectionnez Exchange Online. Choisissez **Sélectionner** lorsque vous avez fini.

8. Pour exiger des PC conformes (mais pas les téléphones et les tablettes conformes), sous **affectations**, choisissez **conditions > plateformes d’appareils**. Sélectionnez **Oui** pour **configurer**. Sélectionnez  **Sélectionner les plateformes**de l’appareil, sélectionnez **Windows** et **MacOS**, puis sélectionnez **OK**.

9. Sous **contrôles d’accès**, sélectionnez **accorder** .

10. Sélectionnez **accorder l’accès** , puis vérifiez **que l’option exiger le périphérique est marquée comme conforme**. Pour plusieurs contrôles, sélectionnez **l’option exiger tous les contrôles sélectionnés**. Lorsque vous avez terminé, choisissez **Sélectionner**. 

10. Sélectionnez **activé** pour **activer la stratégie**, puis **créer**.

>[!Note]
>Assurez-vous que votre appareil est conforme avant d’activer cette stratégie. Dans le cas contraire, vous pourriez être verrouillé et ne pourrez pas modifier cette stratégie tant que votre compte d’utilisateur n’a pas été ajouté au groupe d’exclusion d’accès conditionnel.
>

## <a name="require-compliant-pcs-and-mobile-devices"></a>Exiger des PC conformes *et des* appareils mobiles

Pour exiger la conformité de tous les périphériques, procédez comme suit :

1. Accédez au [portail Azure](https://portal.azure.com) et connectez-vous avec vos informations d’identification.
2. Dans la liste des services Azure, sélectionnez **Azure Active Directory**.
3. Dans la liste **gérer** , choisissez **sécurité**, puis **accès conditionnel**.
4. Choisissez **nouvelle stratégie** et tapez le nom de la nouvelle stratégie.

5. Sous **affectations**, choisissez **utilisateurs et groupes** et indiquez les personnes auxquelles la stratégie doit s’appliquer. Excluez également votre groupe d’exclusion d’accès conditionnel.

6. Sous **affectations**, sélectionnez **applications ou actions Cloud**.

7. Pour **inclure**, choisissez **sélectionner les applications > sélectionnez**, puis sélectionnez les applications souhaitées dans la liste **applications Cloud** . Par exemple, sélectionnez Exchange Online. Choisissez **Sélectionner** lorsque vous avez fini.

8. Sous **contrôles d’accès**, sélectionnez **accorder** .

9. Sélectionnez **accorder l’accès** , puis vérifiez **que l’option exiger le périphérique est marquée comme conforme**. Pour plusieurs contrôles, sélectionnez **l’option exiger tous les contrôles sélectionnés**. Lorsque vous avez terminé, choisissez **Sélectionner**. 

10. Sélectionnez **activé** pour **activer la stratégie**, puis **créer**.

>[!Note]
>Assurez-vous que votre appareil est conforme avant d’activer cette stratégie. Dans le cas contraire, vous pourriez être verrouillé et ne pourrez pas modifier cette stratégie tant que votre compte d’utilisateur n’a pas été ajouté au groupe d’exclusion d’accès conditionnel.
>

## <a name="next-step"></a>Étape suivante

![Étape 3 : stratégies pour les utilisateurs invités et externes](../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-3.png)


[En savoir plus sur les recommandations de stratégie pour les utilisateurs invités et externes](identity-access-policies-guest-access.md)
