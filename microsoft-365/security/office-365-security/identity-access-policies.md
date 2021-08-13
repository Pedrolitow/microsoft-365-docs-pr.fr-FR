---
title: 'Stratégies d’accès aux identités et appareils courantes : Microsoft 365 pour les | Documents Microsoft'
description: Décrit les stratégies et configurations courantes d’accès aux identités et appareils recommandées.
ms.author: josephd
author: JoeDavies-MSFT
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
ms.technology: mdo
ms.openlocfilehash: 564747e31f7ab412d14790e42e6c8e901e382de4e08834b9a5b2f7c775454c74
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53816966"
---
# <a name="common-identity-and-device-access-policies"></a>Stratégies communes pour les identités et l’accès aux appareils

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- Azure

Cet article décrit les stratégies recommandées courantes pour sécuriser l’accès aux services cloud Microsoft 365, y compris les applications sur site publiées avec le proxy d’application Azure Active Directory (Azure AD).

Ce guide explique comment déployer les stratégies recommandées dans un environnement nouvellement mis en service. La configuration de ces stratégies dans un environnement de laboratoire distinct vous permet de comprendre et d’évaluer les stratégies recommandées avant de mettre en place le déploiement dans vos environnements de préproduction et de production. Votre environnement nouvellement provisioné peut être cloud uniquement ou hybride pour refléter vos besoins d’évaluation.

## <a name="policy-set"></a>Ensemble de stratégies

Le diagramme suivant illustre l’ensemble recommandé de stratégies. Il indique à quel niveau de protection chaque stratégie s’applique et si les stratégies s’appliquent aux PC, téléphones et tablettes, ou aux deux catégories d’appareils. Il indique également l’endroit où vous configurez ces stratégies.

[![Stratégies courantes pour la configuration de l’accès aux identités et aux appareils](../../media/microsoft-365-policies-configurations/identity-device-access-policies-byplan.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/microsoft-365-policies-configurations/identity-device-access-policies-byplan.png)

Voici un résumé PDF d’une page avec des liens vers les stratégies individuelles :

[![Image miniature de la protection des identités et des appareils pour le Microsoft 365 de données](../../media/microsoft-365-policies-configurations/MSFT-cloud-architecture-identity-device-protection-handout.png)](../../downloads/MSFT-cloud-architecture-identity-device-protection-handout.pdf) <br> [Affichage au format PDF](../../downloads/MSFT-cloud-architecture-identity-device-protection-handout.pdf) \| [Téléchargement au format PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/MSFT-cloud-architecture-identity-device-protection-handout.pdf)

Le reste de cet article explique comment configurer ces stratégies.

> [!NOTE]
> Il est recommandé d’exiger l’utilisation de l’authentification multifacteur (MFA) avant d’inscrire des appareils dans Intune pour garantir que l’appareil est en possession de l’utilisateur prévu. Vous devez inscrire des appareils dans Intune avant de pouvoir appliquer des stratégies de conformité des appareils.

Pour vous donner le temps d’effectuer ces tâches, nous vous recommandons d’implémenter les stratégies de référence dans l’ordre répertorié dans ce tableau. Toutefois, les stratégies mfa pour les niveaux de protection sensibles et hautement réglementés peuvent être implémentées à tout moment.

|Niveau de protection|Politiques|Plus d’informations|Licence|
|---|---|---|---|
|**Baseline**|[Exiger l’mf lorsque le risque de se connecte *est moyen* ou *élevé*](#require-mfa-based-on-sign-in-risk)||Microsoft 365 E5 ou Microsoft 365 E3 avec le module de sécurité E5|
||[Bloquer les clients ne prenant pas en charge l’authentification moderne](#block-clients-that-dont-support-multi-factor)|Les clients qui n’utilisent pas l’authentification moderne peuvent contourner les stratégies d’accès conditionnel, il est donc important de les bloquer.|Microsoft 365 E3 ou E5|
||[Les utilisateurs à risque élevé doivent modifier leur mot de passe](#high-risk-users-must-change-password)|Oblige les utilisateurs à modifier leur mot de passe lors de la signature si une activité à risque élevé est détectée pour leur compte.|Microsoft 365 E5 ou Microsoft 365 E3 avec le module de sécurité E5|
||[Appliquer la protection des données APP (Application Protection Policies)](#apply-app-data-protection-policies)|Une stratégie Intune App Protection par plateforme (Windows, iOS/iPadOS, Android).|Microsoft 365 E3 ou E5|
||[Exiger la protection des applications et des applications approuvées](#require-approved-apps-and-app-protection)|Applique la protection des applications mobiles pour les téléphones et les tablettes à l’aide d’iOS, iPadOS ou Android.|Microsoft 365 E3 ou E5|
||[Définir des stratégies de conformité des appareils](#define-device-compliance-policies)|Une stratégie pour chaque plateforme.|Microsoft 365 E3 ou E5|
||[Exiger des PC conformes](#require-compliant-pcs-but-not-compliant-phones-and-tablets)|Applique la gestion Intune des PC à l’aide Windows macOS.|Microsoft 365 E3 ou E5|
|**Sensible**|[Exiger l' intermédiaire lorsque le risque de se connecte *est faible,* *moyen* ou *élevé*](#require-mfa-based-on-sign-in-risk)||Microsoft 365 E5 ou Microsoft 365 E3 avec le module de sécurité E5|
||[Exiger des PC et *des appareils* mobiles conformes](#require-compliant-pcs-and-mobile-devices)|Applique la gestion Intune pour les PC (Windows ou macOS) et les téléphones ou tablettes (iOS, iPadOS ou Android).|Microsoft 365 E3 ou E5|
|**Hautement réglementé**|[*Toujours exiger* l’mf d’fa](#assigning-policies-to-groups-and-users)||Microsoft 365 E3 ou E5|
|

## <a name="assigning-policies-to-groups-and-users"></a>Affectation de stratégies à des groupes et des utilisateurs

Avant de configurer des stratégies, identifiez les groupes Azure AD que vous utilisez pour chaque niveau de protection. En règle générale, la protection de référence s’applique à tous les membres de l’organisation. Toutes les stratégies de référence, ainsi que les stratégies sensibles, seront appliquées à un utilisateur inclus pour la protection de référence et la protection sensible. La protection est cumulative et la stratégie la plus restrictive est appliquée.

Une pratique recommandée consiste à créer un groupe Azure AD pour l’exclusion de l’accès conditionnel. Ajoutez ce groupe à toutes vos stratégies  d’accès conditionnel dans la valeur **Exclure** du paramètre Utilisateurs et groupes de la section **Affectations.** Cela vous donne une méthode pour fournir l’accès à un utilisateur pendant que vous dépanner les problèmes d’accès. Il est recommandé comme solution temporaire uniquement. Surveillez ce groupe pour les modifications et assurez-vous que le groupe d’exclusion est utilisé uniquement comme prévu.

Voici un exemple d’affectation de groupe et d’exclusions pour exiger l’ation de l’ation de la MFA.

![Exemples d’attribution de groupe et d’exclusions pour les stratégies mfa](../../media/microsoft-365-policies-configurations/identity-access-policies-assignment.png)

Voici les résultats :

- Tous les utilisateurs sont tenus d’utiliser l’mfmf lorsque le risque de se connecte est moyen ou élevé.

- Les membres du groupe Personnel de direction sont tenus d’utiliser l’mfmf lorsque le risque de se connecte est faible, moyen ou élevé.

  Dans ce cas, les membres du groupe Personnel exécutif correspondent à la fois aux stratégies d’accès conditionnel de référence et sensibles. Les contrôles d’accès pour les deux stratégies sont combinés, ce qui, dans ce cas, équivaut à la stratégie d’accès conditionnel sensible.

- Les membres du groupe Top Secret Project X sont toujours tenus d’utiliser l’mf.

  Dans ce cas, les membres du groupe Top Secret Project X correspondent à la fois aux stratégies d’accès conditionnel de référence et hautement réglementées. Les contrôles d’accès pour les deux stratégies sont combinés. Étant donné que le contrôle d’accès pour la stratégie d’accès conditionnel hautement réglementé est plus restrictif, il est utilisé.

Soyez prudent lorsque vous appliquez des niveaux de protection plus élevés aux groupes et aux utilisateurs. Par exemple, les membres du groupe Top Secret Project X doivent utiliser l’mf à chaque fois qu’ils se connectent, même s’ils ne travaillent pas sur le contenu hautement réglementé pour Project X.

Tous les groupes Azure AD créés dans le cadre de ces recommandations doivent être créés Microsoft 365 groupes. Ceci est important pour le déploiement d’étiquettes de sensibilité lors de la sécurisation des documents Microsoft Teams et SharePoint.

![Exemple de création d’Microsoft 365 groupe](../../media/microsoft-365-policies-configurations/identity-device-AAD-groups.png)

## <a name="require-mfa-based-on-sign-in-risk"></a>Exiger l’mf en fonction du risque de la sign-in

Vous devez demander à vos utilisateurs de s’inscrire à l’ation MFA avant d’en exiger l’utilisation. Si vous avez des licences Microsoft 365 E5, Microsoft 365 E3 avec le module de sécurité E5, des Office 365 avec EMS E5 ou des licences Azure AD Premium P2 individuelles, vous pouvez utiliser la stratégie d’inscription MFA avec Azure AD Identity Protection pour exiger que les utilisateurs s’inscrivent à l’mf. Le [travail prérequis](identity-access-prerequisites.md) inclut l’inscription de tous les utilisateurs avec mfa.

Une fois que vos utilisateurs sont inscrits, vous pouvez exiger l' approbation de l' approbation de l’mf pour vous inscrire avec une nouvelle stratégie d’accès conditionnel.

1. Accédez au [portail Azure](https://portal.azure.com) et connectez-vous avec vos informations d’identification.
2. Dans la liste des services Azure, choisissez **Azure Active Directory**.
3. Dans la **liste Gérer,** choisissez **Sécurité,** puis accès **conditionnel.**
4. Choisissez **Nouvelle stratégie** et tapez le nom de la nouvelle stratégie.

Les tableaux suivants décrivent les paramètres de stratégie d’accès conditionnel pour exiger une mfmf en fonction du risque de la sign-in.

Dans la section **Affectations** :

|Paramètre|Propriétés|Valeurs|Remarques|
|---|---|---|---|
|Utilisateurs et groupes|Inclure|**Sélectionnez utilisateurs et groupes > utilisateurs et groupes**: sélectionnez des groupes spécifiques contenant des comptes d’utilisateurs ciblés.|Commencez par le groupe qui inclut les comptes d’utilisateurs pilotes.|
||Exclure|**Utilisateurs et groupes**: sélectionnez votre groupe d’exceptions d’accès conditionnel ; comptes de service (identités d’application).|L’appartenance doit être modifiée selon les besoins, de manière temporaire.|
|Applications ou actions cloud|**Applications cloud > Include**|**Sélectionner des applications**: sélectionnez les applications à appliquer à cette stratégie. Par exemple, sélectionnez Exchange Online.||
|Conditions|||Configurez des conditions spécifiques à votre environnement et à vos besoins.|
||Risque de connexion||Consultez les instructions du tableau suivant.|
|

### <a name="sign-in-risk-condition-settings"></a>Paramètres de condition de risque de la signature

Appliquez les paramètres de niveau de risque en fonction du niveau de protection que vous ciblez.

|Niveau de protection|Valeurs de niveau de risque requises|Opération|
|---|---|---|
|Baseline|Élevé, moyen|Vérifiez les deux.|
|Sensible|Élevé, moyen, faible|Vérifiez les trois.|
|Hautement réglementé||Laissez toutes les options désactivées pour toujours appliquer l’personnalisation MFA.|
|

Dans la section **Contrôles d’accès** :

|Paramètre|Propriétés|Valeurs|Opération|
|---|---|---|---|
|Accorder|**Grant access**||Sélectionner|
|||**Exiger une authentification multifacteur**|Chèque|
||**Demander tous les contrôles sélectionnés**||Sélectionner|
|

Sélectionnez **Sélectionner** pour enregistrer les **paramètres** d’octroi.

Enfin, **sélectionnez Activer** pour **activer la stratégie,** puis sélectionnez **Créer.**

Envisagez également d’utiliser [l’outil What if](/azure/active-directory/active-directory-conditional-access-whatif) pour tester la stratégie.

## <a name="block-clients-that-dont-support-multi-factor"></a>Bloquer les clients qui ne sont pas en charge multi-facteur

Utilisez les paramètres de ces tableaux pour une stratégie d’accès conditionnel afin de bloquer les clients qui ne peuvent pas prendre en charge l’authentification multifacteur.

Consultez [cet article pour](../../enterprise/microsoft-365-client-support-multi-factor-authentication.md) obtenir la liste des clients dans Microsoft 365 qui ne prisent en charge l’authentification multifacteur.

Dans la section **Affectations** :

|Paramètre|Propriétés|Valeurs|Remarques|
|---|---|---|---|
|Utilisateurs et groupes|Inclure|**Sélectionnez utilisateurs et groupes > utilisateurs et groupes**: sélectionnez des groupes spécifiques contenant des comptes d’utilisateurs ciblés.|Commencez par le groupe qui inclut les comptes d’utilisateurs pilotes.|
||Exclure|**Utilisateurs et groupes**: sélectionnez votre groupe d’exceptions d’accès conditionnel ; comptes de service (identités d’application).|L’appartenance doit être modifiée selon les besoins, de manière temporaire.|
|Applications ou actions cloud|**Applications cloud > Include**|**Sélectionner des applications**: sélectionnez les applications correspondant aux clients qui ne la prisent pas en charge de l’authentification moderne.||
|Conditions|**Applications clientes**|Choisir **Oui** pour **configurer** <p> Effacer les coches pour les **applications** mobiles et de navigateur **et les clients de bureau**||
|

Dans la section **Contrôles d’accès** :

|Paramètre|Propriétés|Valeurs|Opération|
|---|---|---|---|
|Accorder|**Bloquer l’accès**||Sélectionner|
||**Demander tous les contrôles sélectionnés**||Sélectionner|
|

Sélectionnez **Sélectionner** pour enregistrer les **paramètres** d’octroi.

Enfin, **sélectionnez Activer** pour **activer la stratégie,** puis sélectionnez **Créer.**

Envisagez d’utiliser [l’outil What if](/azure/active-directory/active-directory-conditional-access-whatif) pour tester la stratégie.

Par Exchange Online, vous pouvez utiliser des stratégies d’authentification pour désactiver l’authentification de [base,](/exchange/clients-and-mobile-in-exchange-online/disable-basic-authentication-in-exchange-online)ce qui force toutes les demandes d’accès client à utiliser l’authentification moderne.

## <a name="high-risk-users-must-change-password"></a>Les utilisateurs à risque élevé doivent modifier leur mot de passe

Pour vous assurer que les comptes compromis de tous les utilisateurs à risque élevé sont obligés d’effectuer une modification de mot de passe lors de la signature, vous devez appliquer la stratégie suivante.

Connectez-vous au [portail Microsoft Azure (https://portal.azure.com)](https://portal.azure.com/) avec vos informations d’identification d’administrateur, puis accédez à **Azure AD Identity Protection > Stratégie d’utilisateur à risque**.

Dans la section **Affectations** :

|Type|Propriétés|Valeurs|Opération|
|---|---|---|---|
|Utilisateurs|Inclure|**Tous les utilisateurs**|Sélectionner|
|Risque de l’utilisateur|**High**||Sélectionner|
|

Dans la deuxième section **Affectations** :

|Type|Propriétés|Valeurs|Opération|
|---|---|---|---|
|Access|**Autoriser l’accès**||Sélectionner|
|||**Exiger le changement du mot de passe**|Chèque|
|

Choisissez **Terminé** pour enregistrer les **paramètres Access.**

Enfin, **sélectionnez Sur** pour **Appliquer la stratégie,** puis sélectionnez **Enregistrer.**

Envisagez d’utiliser [l’outil What if](/azure/active-directory/active-directory-conditional-access-whatif) pour tester la stratégie.

Utilisez cette stratégie conjointement avec configurer la protection par mot de passe [Azure AD,](/azure/active-directory/authentication/concept-password-ban-bad)qui détecte et bloque les mots de passe faibles connus, leurs variantes et d’autres termes faibles propres à votre organisation. L’utilisation de la protection par mot de passe Azure AD garantit que les mots de passe modifiés sont forts.

## <a name="apply-app-data-protection-policies"></a>Appliquer des stratégies de protection des données APP

Les API définissent les applications autorisées et les actions qu’elles peuvent prendre avec les données de votre organisation. Les choix disponibles dans APP permettent aux organisations d’adapter la protection à leurs besoins spécifiques. Pour certains, il n’est peut-être pas évident de savoir quels paramètres de stratégie sont nécessaires pour implémenter un scénario complet. Pour aider les organisations à hiérarchiser le renforcement des points de terminaison des clients mobiles, Microsoft a introduit la taxonomie pour son infrastructure de protection des données d’APPLICATION pour la gestion des applications mobiles iOS et Android.

L’infrastructure de protection des données APP est organisée en trois niveaux de configuration distincts, chacun d’eux s’axant sur le niveau précédent :

- **Enterprise protection** des données de base (niveau 1) garantit que les applications sont protégées par un code confidentiel et chiffrées et effectue des opérations de effacement sélective. Pour les appareils Android, ce niveau valide l’attestation d’appareil Android. Il s’agit d’une configuration de niveau d’entrée qui fournit un contrôle de protection des données similaire dans Exchange Online stratégies de boîte aux lettres et introduit le service it et la population d’utilisateurs dans APP.
- **Enterprise protection améliorée des** données (niveau 2) introduit des mécanismes de prévention des fuites de données d’APPLICATION et des exigences minimales du système d’exploitation. Il s’agit de la configuration applicable à la plupart des utilisateurs mobiles accédant aux données scolaires ou professionnels.
- **Enterprise protection élevée des** données (niveau 3) introduit des mécanismes de protection des données avancés, une configuration améliorée du code confidentiel et la protection contre les menaces app Mobile. Cette configuration est souhaitable pour les utilisateurs qui accèdent à des données à risque élevé.

Pour voir les recommandations spécifiques pour chaque niveau de configuration et les applications minimales qui doivent être protégées, consultez l’infrastructure de protection des données à l’aide de stratégies [de protection des applications.](/mem/intune/apps/app-protection-framework)

En utilisant les principes décrits dans les configurations d’identité et d’accès aux appareils, les [niveaux](microsoft-365-policies-configurations.md)de protection de base et sensibles sont étroitement mapés avec les paramètres de protection des données améliorées d’entreprise de niveau 2. Le niveau de protection hautement réglementé est étroitement mapré avec les paramètres de protection des données élevées d’entreprise de niveau 3.

|Niveau de protection|Stratégie de protection des applications|Plus d’informations|
|---|---|---|
|Baseline|[Niveau 2 - Protection améliorée des données](/mem/intune/apps/app-protection-framework#level-2-enterprise-enhanced-data-protection)|Les paramètres de stratégie appliqués au niveau 2 incluent tous les paramètres de stratégie recommandés pour le niveau 1 et ajoutent ou mettent uniquement à jour les paramètres de stratégie ci-dessous pour implémenter davantage de contrôles et une configuration plus sophistiquée que le niveau 1.|
|Sensible|[Niveau 2 - Protection améliorée des données](/mem/intune/apps/app-protection-framework#level-2-enterprise-enhanced-data-protection)|Les paramètres de stratégie appliqués au niveau 2 incluent tous les paramètres de stratégie recommandés pour le niveau 1 et ajoutent ou mettent uniquement à jour les paramètres de stratégie ci-dessous pour implémenter davantage de contrôles et une configuration plus sophistiquée que le niveau 1.|
|Hautement réglementé|[Niveau 3 de protection des données d’entreprise élevé](/mem/intune/apps/app-protection-framework#level-3-enterprise-high-data-protection)|Les paramètres de stratégie appliqués au niveau 3 incluent tous les paramètres de stratégie recommandés pour les niveaux 1 et 2 et ajoutent ou mettent uniquement à jour les paramètres de stratégie ci-dessous pour implémenter davantage de contrôles et une configuration plus sophistiquée que le niveau 2.|
|

Pour créer une stratégie de protection des applications pour chaque plateforme (iOS et Android) dans Microsoft Endpoint Manager à l’aide des paramètres de l’infrastructure de protection des données, vous pouvez :

1. Créez manuellement les stratégies en suivant les étapes de la procédure de création et de déploiement des stratégies de protection des applications [avec Microsoft Intune](/mem/intune/apps/app-protection-policies).
2. Importez l’exemple [de modèles JSON d’Infrastructure](https://github.com/microsoft/Intune-Config-Frameworks/tree/master/AppProtectionPolicies) de configuration de la stratégie de protection des applications Intune avec les [scripts PowerShell d’Intune.](https://github.com/microsoftgraph/powershell-intune-samples)

## <a name="require-approved-apps-and-app-protection"></a>Exiger des applications approuvées et la protection des applications

Pour appliquer les stratégies de protection des applications que vous avez appliquées dans Intune, vous devez créer une stratégie d’accès conditionnel pour exiger des applications clientes approuvées et les conditions définies dans les stratégies de protection des applications.

L’application de stratégies de protection d’APPLICATION nécessite un ensemble de stratégies décrites dans la stratégie Exiger la protection des applications pour l’accès aux applications [cloud avec l’accès conditionnel.](/azure/active-directory/conditional-access/app-protection-based-conditional-access) Ces stratégies sont incluses dans cet ensemble recommandé de stratégies de configuration des identités et des accès.

Pour créer la stratégie d’accès conditionnel qui nécessite une protection des applications et des applications approuvées, suivez « Étape 1 : Configurer une stratégie d’accès conditionnel Azure AD pour Microsoft 365 » dans le scénario [1](/azure/active-directory/conditional-access/app-protection-based-conditional-access#scenario-1-office-365-apps-require-approved-apps-with-app-protection-policies): les applications Microsoft 365 nécessitent des applications approuvées avec des stratégies de protection des applications, ce qui permet de Outlook pour iOS et Android, mais empêche les clients Exchange ActiveSync OAuth de se connecter à Exchange Online.

   > [!NOTE]
   > Cette stratégie garantit que les utilisateurs mobiles peuvent accéder à Office points de terminaison à l’aide des applications applicables.

Si vous activez l’accès mobile à Exchange Online, implémentez les [clients Block ActiveSync,](secure-email-recommended-policies.md#block-activesync-clients)ce qui empêche les clients Exchange ActiveSync utilisant l’authentification de base de se connecter à Exchange Online. Cette stratégie n’est pas illustré dans l’illustration en haut de cet article. Il est décrit et présenté dans les recommandations de stratégie [pour la sécurisation du courrier électronique.](secure-email-recommended-policies.md)

Pour créer la stratégie d’accès conditionnel qui nécessite Edge pour iOS et Android, suivez « Étape 2 : Configurer une stratégie d’accès conditionnel Azure AD pour Microsoft 365 » dans le scénario [2](/azure/active-directory/conditional-access/app-protection-based-conditional-access#scenario-2-browser-apps-require-approved-apps-with-app-protection-policies): les applications de navigateur nécessitent des applications approuvées avec des stratégies de protection des applications, ce qui permet à Edge pour iOS et Android, mais empêche les autres navigateurs web d’appareils mobiles de se connecter aux points de terminaison Microsoft 365.

 Ces stratégies exploitent les contrôles d’octroi [Exiger une application cliente approuvée](/azure/active-directory/conditional-access/concept-conditional-access-grant#require-approved-client-app) et Exiger la stratégie de protection des [applications.](/azure/active-directory/conditional-access/concept-conditional-access-grant#require-app-protection-policy)

Enfin, le blocage de l’authentification héritée pour d’autres applications clientes sur les appareils iOS et Android garantit que ces clients ne peuvent pas contourner les stratégies d’accès conditionnel. Si vous êtes en train de suivre les instructions de cet article, vous avez déjà configuré des clients Block qui ne sont pas pris en charge par [l’authentification moderne.](#block-clients-that-dont-support-multi-factor)

<!---
With Conditional Access, organizations can restrict access to approved (modern authentication capable) iOS and Android client apps with Intune app protection policies applied to them. Several Conditional Access policies are required, with each policy targeting all potential users. Details on creating these policies can be found in [Require app protection policy for cloud app access with Conditional Access](/azure/active-directory/conditional-access/app-protection-based-conditional-access).

1. Follow "Step 1: Configure an Azure AD Conditional Access policy for Microsoft 365" in [Scenario 1: Microsoft 365 apps require approved apps with app protection policies](/azure/active-directory/conditional-access/app-protection-based-conditional-access#scenario-1-office-365-apps-require-approved-apps-with-app-protection-policies), which allows Outlook for iOS and Android, but blocks OAuth capable Exchange ActiveSync clients from connecting to Exchange Online.

   > [!NOTE]
   > This policy ensures mobile users can access all Office endpoints using the applicable apps.

2. If enabling mobile access to Exchange Online, implement [Block ActiveSync clients](secure-email-recommended-policies.md#block-activesync-clients), which prevents Exchange ActiveSync clients leveraging basic authentication from connecting to Exchange Online.

   The above policies leverage the grant controls [Require approved client app](/azure/active-directory/conditional-access/concept-conditional-access-grant#require-approved-client-app) and [Require app protection policy](/azure/active-directory/conditional-access/concept-conditional-access-grant#require-app-protection-policy).

3. Disable legacy authentication for other client apps on iOS and Android devices. For more information, see [Block clients that don't support modern authentication](#block-clients-that-dont-support-modern-authentication).
-->

## <a name="define-device-compliance-policies"></a>Définir des stratégies de conformité des appareils

Les stratégies de conformité des appareils définissent les exigences que les appareils doivent respecter pour être déterminés comme conformes. Vous créez des stratégies de conformité des appareils Intune à partir du centre d Microsoft Endpoint Manager’administration.

Vous devez créer une stratégie pour chaque plateforme pc, téléphone ou tablette :

- Administrateur d’appareil Android
- Android Enterprise
- iOS/iPadOS
- macOS
- Windows 8.1 et ultérieures
- Windows 10 et ultérieures

Pour créer des stratégies de conformité des appareils, connectez-vous au  [Centre d’administration Microsoft Endpoint Manager](https://endpoint.microsoft.com) avec vos informations d’identification d’administrateur, puis accédez aux stratégies de conformité \> **des** \> **appareils.** Sélectionnez **Créer une stratégie.**

Pour que les stratégies de conformité des appareils soient déployées, elles doivent être affectées à des groupes d’utilisateurs. Vous affectez une stratégie après l’avoir créé et l’enregistrer. Dans le Centre d’administration, sélectionnez la stratégie, puis **sélectionnez Affectations.** Après avoir sélectionné les groupes à recevoir,  sélectionnez Enregistrer pour enregistrer cette affectation de groupe et déployer la stratégie.

Pour obtenir des instructions pas à pas sur la création de stratégies de conformité dans Intune, voir Créer une stratégie de conformité [Microsoft Intune](/mem/intune/protect/create-compliance-policy) la documentation Intune.

### <a name="recommended-settings-for-ios"></a>Paramètres recommandés pour iOS

iOS/iPadOS prend en charge plusieurs scénarios d’inscription, dont deux sont couverts dans le cadre de cette infrastructure :

- [Inscription d’appareils pour les](/mem/intune/enrollment/ios-enroll) appareils personnels : ces appareils sont personnels et utilisés à la fois pour un usage personnel et personnel.
- [L’inscription](/mem/intune/enrollment/device-enrollment-program-enroll-ios) automatisée supervisée des appareils d’entreprise : ces appareils sont des appareils d’entreprise, associés à un seul utilisateur et utilisés exclusivement à des usages personnels et non à des usages personnels.

L’infrastructure de configuration de la sécurité iOS/iPadOS est organisée en plusieurs scénarios de configuration distincts, fournissant des conseils pour les appareils personnels et supervisés.

Pour les appareils personnels :

- Sécurité de base (niveau 1) : Microsoft recommande cette configuration en tant que configuration de sécurité minimale pour les appareils personnels où les utilisateurs accèdent aux données scolaires ou professionnels. Pour ce faire, appliquez des stratégies de mot de passe, des caractéristiques de verrouillage de l’appareil et désactivez certaines fonctions d’appareil (par exemple, des certificats non sécurisés).
- Sécurité renforcée (niveau 2) : Microsoft recommande cette configuration pour les appareils où les utilisateurs accèdent à des informations sensibles ou confidentielles. Cette configuration permet d’adopter des contrôles de partage de données. Cette configuration s’applique à la plupart des utilisateurs mobiles accédant à des données scolaires ou de travail sur un appareil.
- Haute sécurité (niveau 3) : Microsoft recommande cette configuration pour les appareils utilisés par des utilisateurs ou des groupes spécifiques à risque élevé (les utilisateurs qui gèrent des données hautement sensibles lorsque la divulgation non autorisée entraîne une perte matérielle considérable pour l’organisation). Cette configuration permet de renforcer les stratégies de mot de passe, de désactiver certaines fonctions d’appareil et d’appliquer des restrictions de transfert de données supplémentaires.

Pour les appareils supervisés :

- Sécurité de base (niveau 1) : Microsoft recommande cette configuration comme configuration de sécurité minimale pour les appareils supervisés où les utilisateurs accèdent aux données scolaires ou professionnels. Pour ce faire, appliquez des stratégies de mot de passe, des caractéristiques de verrouillage de l’appareil et désactivez certaines fonctions d’appareil (par exemple, des certificats non sécurisés).
- Sécurité renforcée (niveau 2) : Microsoft recommande cette configuration pour les appareils où les utilisateurs accèdent à des informations sensibles ou confidentielles. Cette configuration édicte des contrôles de partage de données et bloque l’accès aux périphériques USB. Cette configuration s’applique à la plupart des utilisateurs mobiles accédant à des données scolaires ou de travail sur un appareil.
- Haute sécurité (niveau 3) : Microsoft recommande cette configuration pour les appareils utilisés par des utilisateurs ou des groupes spécifiques à risque élevé (les utilisateurs qui gèrent des données hautement sensibles lorsque la divulgation non autorisée entraîne une perte matérielle considérable pour l’organisation). Cette configuration permet de renforcer les stratégies de mot de passe, de désactiver certaines fonctions d’appareil, d’appliquer des restrictions de transfert de données supplémentaires et d’installer des applications via le programme d’achat en volume d’Apple.

À l’aide des principes décrits dans les configurations d’identité et d’accès aux appareils, les [niveaux](microsoft-365-policies-configurations.md)de protection de référence et sensibles sont étroitement mapés avec les paramètres de sécurité améliorés de niveau 2. Le niveau de protection hautement réglementé est étroitement map avec les paramètres de sécurité élevée de niveau 3.

|Niveau de protection  |Stratégie d’appareil |Plus d’informations  |
|---------|---------|---------|
|Baseline     |Sécurité renforcée (niveau 2)         |Les paramètres de stratégie appliqués au niveau 2 incluent tous les paramètres de stratégie recommandés pour le niveau 1 et ajoutent ou mettent uniquement à jour les paramètres de stratégie ci-dessous pour implémenter davantage de contrôles et une configuration plus sophistiquée que le niveau 1.         |
|Sensible     |Sécurité renforcée (niveau 2)         |Les paramètres de stratégie appliqués au niveau 2 incluent tous les paramètres de stratégie recommandés pour le niveau 1 et ajoutent ou mettent uniquement à jour les paramètres de stratégie ci-dessous pour implémenter davantage de contrôles et une configuration plus sophistiquée que le niveau 1.         |
|Hautement réglementé     |Sécurité élevée (niveau 3)         |Les paramètres de stratégie appliqués au niveau 3 incluent tous les paramètres de stratégie recommandés pour les niveaux 1 et 2 et ajoutent ou mettent uniquement à jour les paramètres de stratégie ci-dessous pour implémenter davantage de contrôles et une configuration plus sophistiquée que le niveau 2.         |

Pour voir les recommandations spécifiques en matière de conformité et de restriction d’appareil pour chaque niveau de configuration, consultez l’infrastructure de configuration de sécurité [iOS/iPadOS.](/mem/intune/enrollment/ios-ipados-configuration-framework)

### <a name="recommended-settings-for-android"></a>Paramètres recommandés pour Android

Android Enterprise plusieurs scénarios d’inscription, dont deux sont couverts dans le cadre de cette infrastructure :

- [Profil Enterprise](/intune/android-work-profile-enroll) travail Android : ce modèle d’inscription est généralement utilisé pour les appareils personnels, où le service juridique souhaite fournir une frontière de séparation claire entre les données personnelles et les données personnelles. Les stratégies contrôlées par le personnel de l’information garantissent que les données de travail ne peuvent pas être transférées dans le profil personnel.
- [Android Enterprise](/intune/android-fully-managed-enroll) entièrement gérés : ces appareils sont gérés par l’entreprise, associés à un seul utilisateur et utilisés exclusivement à des usages personnels et non à des usages personnels.

L’infrastructure Enterprise de configuration de la sécurité Android est organisée en plusieurs scénarios de configuration distincts, fournissant des conseils pour les scénarios de profil de travail et les scénarios entièrement gérés.

Pour les appareils Enterprise profils de travail Android :

- Sécurité de base du profil professionnel (niveau 1) : Microsoft recommande cette configuration en tant que configuration de sécurité minimale pour les appareils personnels où les utilisateurs accèdent aux données scolaires ou professionnels. Cette configuration introduit des exigences de mot de passe, sépare les données personnelles et de travail, et valide l’attestation d’appareil Android.
- Profil professionnel haute sécurité (niveau 3) : Microsoft recommande cette configuration pour les appareils utilisés par des utilisateurs ou des groupes spécifiques à risque élevé (les utilisateurs qui gèrent des données hautement sensibles lorsque la divulgation non autorisée entraîne une perte matérielle considérable pour l’organisation). Cette configuration introduit la protection contre les menaces mobiles ou Microsoft Defender pour le point de terminaison, définit la version minimale d’Android, met en place des stratégies de mot de passe plus puissantes et limite davantage la séparation personnelle et le travail.

Pour les appareils android Enterprise entièrement gérés :

- Sécurité de base entièrement gérée (niveau 1) : Microsoft recommande cette configuration comme configuration de sécurité minimale pour un appareil d’entreprise. Cette configuration s’applique à la plupart des utilisateurs mobiles accédant aux données scolaires ou professionnels. Cette configuration introduit des exigences de mot de passe, définit la version minimale d’Android et applique certaines restrictions d’appareil.
- Sécurité améliorée entièrement gérée (niveau 2) : Microsoft recommande cette configuration pour les appareils où les utilisateurs accèdent à des informations sensibles ou confidentielles. Cette configuration permet de renforcer les stratégies de mot de passe et de désactiver les fonctionnalités utilisateur/compte.
- Haute sécurité entièrement gérée (niveau 3) : Microsoft recommande cette configuration pour les appareils utilisés par des utilisateurs ou des groupes spécifiques à risque élevé (les utilisateurs qui gèrent des données hautement sensibles lorsque la divulgation non autorisée entraîne une perte matérielle considérable pour l’organisation). Cette configuration augmente la version minimale d’Android, introduit la protection contre les menaces mobiles ou Microsoft Defender pour le point de terminaison et applique des restrictions supplémentaires sur les appareils.

À l’aide des principes décrits dans les configurations d’identité et d’accès aux appareils, les [niveaux](microsoft-365-policies-configurations.md)de protection de référence et sensibles sont étroitement mapés avec la sécurité de base de niveau 1 pour les appareils personnels et les paramètres de sécurité améliorés de niveau 2 pour les appareils entièrement gérés. Le niveau de protection hautement réglementé est étroitement map avec les paramètres de sécurité élevée de niveau 3.

Pour les appareils Enterprise profils de travail Android :

|Niveau de protection  |Stratégie d’appareil |Plus d’informations  |
|---------|---------|---------|
|Baseline     |Profil professionnel : sécurité de base (niveau 1)      |N/A         |
|Sensible     |Profil professionnel : sécurité de base (niveau 1)         |N/A         |
|Baseline     |Gestion complète : sécurité renforcée (niveau 2)       |Les paramètres de stratégie appliqués au niveau 2 incluent tous les paramètres de stratégie recommandés pour le niveau 1 et ajoutent ou mettent uniquement à jour les paramètres de stratégie ci-dessous pour implémenter davantage de contrôles et une configuration plus sophistiquée que le niveau 1.         |
|Sensible     |Gestion complète : sécurité renforcée (niveau 2)         |Les paramètres de stratégie appliqués au niveau 2 incluent tous les paramètres de stratégie recommandés pour le niveau 1 et ajoutent ou mettent uniquement à jour les paramètres de stratégie ci-dessous pour implémenter davantage de contrôles et une configuration plus sophistiquée que le niveau 1.         |
|Hautement réglementé     |Sécurité élevée (niveau 3)         |Les paramètres de stratégie appliqués au niveau 3 incluent tous les paramètres de stratégie recommandés pour les niveaux 1 et 2 et ajoutent ou mettent uniquement à jour les paramètres de stratégie ci-dessous pour implémenter davantage de contrôles et une configuration plus sophistiquée que le niveau 2.         |

Pour voir les recommandations spécifiques en matière de conformité et de restriction d’appareil pour chaque niveau de configuration, consultez l’infrastructure de configuration de sécurité [Enterprise Android.](/mem/intune/enrollment/android-configuration-framework)

### <a name="recommended-settings-for-windows-10-and-later"></a>Paramètres recommandés pour Windows 10 et ultérieures

Les paramètres suivants sont recommandés pour les PC exécutant Windows 10 et ultérieurs, comme configuré à l’étape 2 : **Paramètres** de conformité , du processus de création de stratégie.

Pour plus **d'> Windows d’évaluation du service d’attestation** d’état d'> Windows, consultez ce tableau.

|Propriétés|Valeur|Opération|
|---|---|---|
|Exiger BitLocker|Require (Rendre obligatoire)|Sélectionner|
|Exiger que le démarrage sécurisé soit activé sur l’appareil|Require (Rendre obligatoire)|Sélectionner|
|Exiger l’intégrité du code|Require (Rendre obligatoire)|Sélectionner|
|

Pour les **propriétés d’appareil,** spécifiez les valeurs appropriées pour les versions de système d’exploitation en fonction de vos stratégies informatiques et de sécurité.

Pour la **conformité configuration Manager,** sélectionnez **Exiger**.

Pour **la sécurité du** système, consultez ce tableau.

|Type|Propriétés|Valeur|Opération|
|---|---|---|---|
|Mot de passe|Exiger un mot de passe pour déverrouiller les appareils mobiles|Require (Rendre obligatoire)|Sélectionner|
||Mots de passe simples|Bloquer|Sélectionner|
||Type de mot de passe|Par défaut de l’appareil|Sélectionner|
||Longueur minimale du mot de passe|6 |Type|
||Nombre maximal de minutes d’inactivité avant que le mot de passe ne soit requis|15|Type <p> Ce paramètre est pris en charge pour les versions Android 4.0 et supérieures ou KNOX 4.0 et versions ultérieures. Pour les appareils iOS, il est pris en charge pour iOS 8.0 et les appareils supérieurs.|
||Expiration du mot de passe (jours)|41|Type|
||Nombre de mots de passe précédents pour empêcher la réutilisation|5 |Type|
||Exiger un mot de passe lorsque l’appareil revient d’un état inactif (mobile et holographique)|Require (Rendre obligatoire)|Disponible pour les Windows 10 et ultérieures|
|Chiffrement|Chiffrement du stockage des données sur l’appareil|Require (Rendre obligatoire)|Sélectionner|
|Sécurité des appareils|Pare-feu|Require (Rendre obligatoire)|Sélectionner|
||Antivirus|Require (Rendre obligatoire)|Sélectionner|
||Antispyware|Require (Rendre obligatoire)|Sélectionner <p> Ce paramètre nécessite une solution anti-logiciel espion inscrite auprès Sécurité Windows Center.|
|Defender|Logiciel anti-programme malveillant Microsoft Defender|Require (Rendre obligatoire)|Sélectionner|
||Version minimale du logiciel anti-programme malveillant Microsoft Defender||Type <p> Uniquement pris en charge pour Windows 10 bureau. Microsoft recommande de ne pas avoir plus de cinq versions en retard par rapport à la version la plus récente.|
||Signature du logiciel anti-programme malveillant Microsoft Defender à jour|Require (Rendre obligatoire)|Sélectionner|
||Protection en temps réel|Require (Rendre obligatoire)|Sélectionner <p> Uniquement pris en charge pour Windows 10 bureau|
|

#### <a name="microsoft-defender-for-endpoint"></a>Microsoft Defender pour point de terminaison

|Type|Propriétés|Valeur|Opération|
|---|---|---|---|
|Règles Microsoft Defender pour les points de terminaison dans le Centre d Microsoft Endpoint Manager’administration Microsoft Defender|[Exiger que l’appareil soit au niveau ou sous le score de risque de l’ordinateur](/mem/intune/protect/advanced-threat-protection-configure#create-and-assign-compliance-policy-to-set-device-risk-level)|Moyen|Sélectionner|
|

## <a name="require-compliant-pcs-but-not-compliant-phones-and-tablets"></a>Exiger des PC conformes (mais pas des téléphones et des tablettes conformes)

Avant d’ajouter une stratégie pour exiger des PC conformes, veillez à inscrire vos appareils pour la gestion dans Intune. L’utilisation de l’authentification multifacteur est recommandée avant d’inscrire des appareils dans Intune pour vous assurer que l’appareil est en possession de l’utilisateur prévu.

Pour exiger des PC conformes :

1. Accédez au [portail Azure](https://portal.azure.com) et connectez-vous avec vos informations d’identification.
2. Dans la liste des services Azure, choisissez **Azure Active Directory**.
3. Dans la **liste Gérer,** choisissez **Sécurité,** puis accès **conditionnel.**
4. Choisissez **Nouvelle stratégie** et tapez le nom de la nouvelle stratégie.

5. Sous **Affectations,** sélectionnez **Utilisateurs et groupes** et incluez à qui vous souhaitez que la stratégie s’applique. Excluez également votre groupe d’exclusions d’accès conditionnel.

6. Sous **Affectations,** choisissez **applications ou actions cloud.**

7. For **Include**, choose **Select apps > Select**, and then select the desired apps from the Cloud **apps** list. Par exemple, sélectionnez Office 365. Sélectionnez **Sélectionner** lorsque vous avez terminé.

8. Pour exiger des PC conformes (mais pas des téléphones et des **tablettes conformes), sous Affectations,** sélectionnez **Conditions > plateformes d’appareils.** Sélectionnez **Oui** **pour configurer**. Choose  **Select device platforms,** select **Yes** and select **Any device** and under Exclude select **iOS** and **Android,** and then choose **Done**.

9. Sous **Contrôles d’accès,** choisissez **Accorder** .

10. Choisissez **Accorder l’accès,** puis vérifiez **Exiger que l’appareil soit marqué comme conforme.** Pour plusieurs contrôles, **sélectionnez Exiger tous les contrôles sélectionnés.** Lorsque vous avez terminé, **sélectionnez Sélectionner.**

11. Sélectionnez **Activer** **pour activer la stratégie,** puis sélectionnez **Créer.**

> [!NOTE]
> Assurez-vous que votre appareil est conforme avant d’activer cette stratégie. Sinon, vous risquez d’être verrouillé et ne pourront pas modifier cette stratégie tant que votre compte d’utilisateur n’aura pas été ajouté au groupe d’exclusions d’accès conditionnel.

## <a name="require-compliant-pcs-and-mobile-devices"></a>Exiger des PC et *des appareils* mobiles conformes

Pour exiger la conformité pour tous les appareils :

1. Accédez au [portail Azure](https://portal.azure.com) et connectez-vous avec vos informations d’identification.
2. Dans la liste des services Azure, choisissez **Azure Active Directory**.
3. Dans la **liste Gérer,** choisissez **Sécurité,** puis accès **conditionnel.**
4. Choisissez **Nouvelle stratégie** et tapez le nom de la nouvelle stratégie.

5. Sous **Affectations,** sélectionnez **Utilisateurs et groupes** et incluez à qui vous souhaitez que la stratégie s’applique. Excluez également votre groupe d’exclusions d’accès conditionnel.

6. Sous **Affectations,** choisissez **applications ou actions cloud.**

7. For **Include**, choose **Select apps > Select**, and then select the desired apps from the Cloud **apps** list. Par exemple, sélectionnez Office 365. Sélectionnez **Sélectionner** lorsque vous avez terminé.

8. Sous **Contrôles d’accès,** choisissez **Accorder** .

9. Choisissez **Accorder l’accès,** puis vérifiez **Exiger que l’appareil soit marqué comme conforme.** Pour plusieurs contrôles, **sélectionnez Exiger tous les contrôles sélectionnés.** Lorsque vous avez terminé, **sélectionnez Sélectionner.**

10. Sélectionnez **Activer** **pour activer la stratégie,** puis sélectionnez **Créer.**

> [!NOTE]
> Assurez-vous que votre appareil est conforme avant d’activer cette stratégie. Sinon, vous risquez d’être verrouillé et ne pourront pas modifier cette stratégie tant que votre compte d’utilisateur n’aura pas été ajouté au groupe d’exclusions d’accès conditionnel.

## <a name="next-step"></a>Étape suivante

[![Étape 3 : Stratégies pour les utilisateurs invités et externes](../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-3.png)](identity-access-policies-guest-access.md)

[En savoir plus sur les recommandations de stratégie pour les utilisateurs invités et externes](identity-access-policies-guest-access.md)