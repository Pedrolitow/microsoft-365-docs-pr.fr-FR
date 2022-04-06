---
title: 'Stratégies communes d’accès aux appareils et aux identités de confiance zéro : Microsoft 365 pour les | Documents Microsoft'
description: Décrit les stratégies et configurations d’accès aux appareils et aux identités Zero Trust courantes recommandées.
ms.author: dansimp
author: dansimp
manager: dansimp
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
ms.openlocfilehash: 2a12a4198b91ab6ec91e0b49b9de3647e25d0be0
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64473846"
---
# <a name="common-zero-trust-identity-and-device-access-policies"></a>Stratégies courantes d’accès aux appareils et aux identités de confiance zéro

Cet article décrit les stratégies d’accès aux appareils et aux identités Zero Trust recommandées pour sécuriser l’accès aux services cloud Microsoft 365, y compris les applications sur site publiées avec le proxy d’application Azure Active Directory (Azure AD).

Ce guide explique comment déployer les stratégies recommandées dans un environnement nouvellement mis en service. La configuration de ces stratégies dans un environnement de laboratoire distinct vous permet de comprendre et d’évaluer les stratégies recommandées avant de mettre en place le déploiement dans vos environnements de préproduction et de production. Votre environnement nouvellement provisioné peut être cloud uniquement ou hybride pour refléter vos besoins d’évaluation.

## <a name="policy-set"></a>Ensemble de stratégies

Le diagramme suivant illustre l’ensemble recommandé de stratégies. Il indique le niveau de protection auquel chaque stratégie s’applique et si les stratégies s’appliquent aux PC, téléphones et tablettes, ou aux deux catégories d’appareils. Il indique également l’endroit où vous configurez ces stratégies.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-access-policies-byplan.png" alt-text="Stratégies courantes pour la configuration de l’accès aux identités et appareils de confiance zéro." lightbox="../../media/microsoft-365-policies-configurations/identity-device-access-policies-byplan.png":::


<!--

Here's a one-page PDF summary:

[![Thumb image for the Zero Trust identity and device protection for Microsoft 365 handout.](../../media/microsoft-365-policies-configurations/zero-trust-id-device-protection-model-handout-thumbnail.png)](../../downloads/MSFT-cloud-architecture-identity-device-protection-handout.pdf) <br> [View as a PDF](../../downloads/MSFT-cloud-architecture-identity-device-protection-handout.pdf) \| [Download as a PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/MSFT-cloud-architecture-identity-device-protection-handout.pdf)


--> 

Le reste de cet article explique comment configurer ces stratégies.

> [!NOTE]
> Il est recommandé d’exiger l’utilisation de l’authentification multifacteur (MFA) avant d’inscrire des appareils dans Intune pour garantir que l’appareil est en possession de l’utilisateur prévu. Vous devez inscrire des appareils dans Intune avant de pouvoir appliquer des stratégies de conformité des appareils.

Pour vous donner le temps d’effectuer ces tâches, nous vous recommandons d’implémenter les stratégies de point de départ dans l’ordre répertorié dans ce tableau. Toutefois, les stratégies mfa pour les entreprises et les niveaux de protection spécialisés peuvent être implémentées à tout moment.

|Niveau de protection|Stratégies|Informations supplémentaires|Licences|
|---|---|---|---|
|**Point de départ**|[Exiger une mfmf lorsque le risque de se connecte *est moyen* ou *élevé*](#require-mfa-based-on-sign-in-risk)||Microsoft 365 E5 ou Microsoft 365 E3 avec le module de sécurité E5|
||[Bloquer les clients ne prenant pas en charge l’authentification moderne](#block-clients-that-dont-support-multi-factor)|Les clients qui n’utilisent pas l’authentification moderne peuvent contourner les stratégies d’accès conditionnel, il est donc important de les bloquer.|Microsoft 365 E3 ou E5|
||[Les utilisateurs à risque élevé doivent modifier leur mot de passe](#high-risk-users-must-change-password)|Oblige les utilisateurs à modifier leur mot de passe lors de la signature si une activité à risque élevé est détectée pour leur compte.|Microsoft 365 E5 ou Microsoft 365 E3 avec le module de sécurité E5|
||[Appliquer la protection des données des stratégies de protection des applications (APP)](#apply-app-data-protection-policies)|Une stratégie Intune App Protection par plateforme (Windows, iOS/iPadOS, Android).|Microsoft 365 E3 ou E5|
||[Exiger la protection des applications et des applications approuvées](#require-approved-apps-and-app-protection)|Applique la protection des applications mobiles pour les téléphones et les tablettes à l’aide d’iOS, iPadOS ou Android.|Microsoft 365 E3 ou E5|
|**Enterprise**|[Exiger l’mf lorsque le risque de se connecte *est faible*, *moyen* ou *élevé*](#require-mfa-based-on-sign-in-risk)||Microsoft 365 E5 ou Microsoft 365 E3 avec le module de sécurité E5|
||[Définir des stratégies de conformité des appareils](#define-device-compliance-policies)|Une stratégie pour chaque plateforme.|Microsoft 365 E3 ou E5|
||[Exiger des PC et des appareils mobiles conformes](#require-compliant-pcs-and-mobile-devices)|Applique la gestion Intune pour les PC (Windows ou macOS) et les téléphones ou tablettes (iOS, iPadOS ou Android).|Microsoft 365 E3 ou E5|
|**Sécurité spécialisée**|[*Toujours exiger* l’mf d’fa](#assigning-policies-to-groups-and-users)||Microsoft 365 E3 ou E5|

## <a name="assigning-policies-to-groups-and-users"></a>Attribution de stratégies à des groupes et des utilisateurs

Avant de configurer des stratégies, identifiez les groupes Azure AD que vous utilisez pour chaque niveau de protection. En règle générale, la protection de point de départ s’applique à tous les membres de l’organisation. Toutes les stratégies de point de départ, ainsi que les stratégies d’entreprise, seront appliquées à un utilisateur inclus à la fois pour le point de départ et pour la protection de l’entreprise. La protection est cumulative et la stratégie la plus restrictive est appliquée.

Une pratique recommandée consiste à créer un groupe Azure AD pour l’exclusion de l’accès conditionnel. Ajoutez ce groupe à toutes vos stratégies d’accès conditionnel dans la  valeur **Exclure** du paramètre Utilisateurs et groupes de la section **Affectations**. Cela vous donne une méthode pour fournir l’accès à un utilisateur pendant que vous dépanner les problèmes d’accès. Il est recommandé comme solution temporaire uniquement. Surveillez ce groupe pour les modifications et assurez-vous que le groupe d’exclusions est utilisé uniquement comme prévu.

Voici un exemple d’attribution de groupe et d’exclusions pour exiger l’ation MFA.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-policies-assignment.png" alt-text="Exemple d’attribution de groupe et d’exclusions pour les stratégies mfa" lightbox="../../media/microsoft-365-policies-configurations/identity-access-policies-assignment.png":::

Voici les résultats :

- Tous les utilisateurs sont tenus d’utiliser l’mfmf lorsque le risque de se connecte est moyen ou élevé.

- Les membres du groupe Personnel exécutif sont tenus d’utiliser l’mfmf lorsque le risque de se connecte est faible, moyen ou élevé.

  Dans ce cas, les membres du groupe Personnel exécutif correspondent à la fois au point de départ et aux stratégies d’accès conditionnel d’entreprise. Les contrôles d’accès pour les deux stratégies sont combinés, ce qui, dans ce cas, équivaut à la stratégie d’accès conditionnel d’entreprise.

- Les membres du groupe Top Secret Project X sont toujours tenus d’utiliser l’mf.

  Dans ce cas, les membres du groupe Top Secret Project X correspondent à la fois au point de départ et aux stratégies d’accès conditionnel de sécurité spécialisées. Les contrôles d’accès pour les deux stratégies sont combinés. Étant donné que le contrôle d’accès pour la stratégie d’accès conditionnel de sécurité spécialisée est plus restrictif, il est utilisé.

Soyez prudent lorsque vous appliquez des niveaux de protection plus élevés aux groupes et aux utilisateurs. Par exemple, les membres du groupe Top Secret Project X doivent utiliser l’mfmf chaque fois qu’ils se connectent, même s’ils ne travaillent pas sur le contenu de sécurité spécialisé pour Project X.

Tous Azure AD groupes créés dans le cadre de ces recommandations doivent être créés en tant que Microsoft 365 groupes. Ceci est important pour le déploiement d’étiquettes de sensibilité lors de la sécurisation des documents Microsoft Teams et SharePoint.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-AAD-groups.png" alt-text="Création d’Microsoft 365 groupe" lightbox="../../media/microsoft-365-policies-configurations/identity-device-AAD-groups.png":::

## <a name="require-mfa-based-on-sign-in-risk"></a>Exiger l’mf en fonction du risque de la sign-in

Vous devez demander à vos utilisateurs de s’inscrire à l’ation MFA avant d’en exiger l’utilisation. Si vous avez des licences Microsoft 365 E5, Microsoft 365 E3 avec le module de sécurité E5, Office 365 avec EMS E5 ou des licences Azure AD Premium P2 individuelles, vous pouvez utiliser la stratégie d’inscription MFA avec Azure AD Identity Protection pour exiger que les utilisateurs s’inscrivent à l’mf. Le [travail prérequis](identity-access-prerequisites.md) inclut l’inscription de tous les utilisateurs avec l’ation MFA.

Une fois que vos utilisateurs sont inscrits, vous pouvez exiger l’approbation de l’mf pour vous inscrire avec une nouvelle stratégie d’accès conditionnel.

1. Accédez au [portail Azure](https://portal.azure.com) et connectez-vous avec vos informations d’identification.
2. Dans la liste des services Azure, choisissez **Azure Active Directory**.
3. Dans la **liste Gérer** , choisissez **Sécurité**, puis accès **conditionnel**.
4. Choisissez **Nouvelle stratégie** et tapez le nom de la nouvelle stratégie.

Les tableaux suivants décrivent les paramètres de stratégie d’accès conditionnel pour exiger l’mfmf en fonction du risque de la sign-in.

Dans la section **Affectations** :

|Paramètre|Propriétés|Valeurs|Remarques|
|---|---|---|---|
|Utilisateurs et groupes|Inclure|**Sélectionnez utilisateurs et groupes > utilisateurs et groupes** : sélectionnez des groupes spécifiques contenant des comptes d’utilisateurs ciblés.|Commencez par le groupe qui inclut les comptes d’utilisateurs pilotes.|
||Exclure|**Utilisateurs et groupes** : sélectionnez votre groupe d’exceptions d’accès conditionnel . comptes de service (identités d’application).|L’appartenance doit être modifiée selon les besoins, de manière temporaire.|
|Applications ou actions cloud|**Applications cloud > Include**|**Sélectionnez les** applications : sélectionnez les applications à appliquer à cette stratégie. Par exemple, sélectionnez Exchange Online.||
|Conditions|||Configurez des conditions spécifiques à votre environnement et à vos besoins.|
||Risque de connexion||Consultez les instructions du tableau suivant.|

### <a name="sign-in-risk-condition-settings"></a>Paramètres de condition de risque de la signature

Appliquez les paramètres de niveau de risque en fonction du niveau de protection que vous ciblez.

|Niveau de protection|Valeurs de niveau de risque requises|Action|
|---|---|---|
|Point de départ|Élevé, moyen|Vérifiez les deux.|
|Entreprise|Élevé, moyen, faible|Vérifiez les trois.|
|Sécurité spécialisée||Laissez toutes les options désactivées pour toujours appliquer l’personnalisation MFA.|

Dans la section **Contrôles d’accès** :

|Paramètre|Propriétés|Valeurs|Action|
|---|---|---|---|
|Accorder|**Grant access**||Sélectionner|
|||**Exiger l’authentification multifacteur**|Chèque|
||**Demander tous les contrôles sélectionnés**||Sélectionner|

**Sélectionnez Sélectionner** pour enregistrer les **paramètres d’octroi**.

Enfin, **sélectionnez Activer** pour **activer la stratégie**, puis **créez**.

Envisagez également d’utiliser [l’outil What if](/azure/active-directory/active-directory-conditional-access-whatif) pour tester la stratégie.

## <a name="block-clients-that-dont-support-multi-factor"></a>Bloquer les clients qui ne sont pas en charge multi-facteur

Utilisez les paramètres de ces tableaux pour une stratégie d’accès conditionnel afin de bloquer les clients qui ne peuvent pas prendre en charge l’authentification multifacteur.

[Consultez cet article pour](../../enterprise/microsoft-365-client-support-multi-factor-authentication.md) obtenir la liste des clients dans Microsoft 365 qui ne prisent en charge l’authentification multifacteur.

Dans la section **Affectations** :

|Paramètre|Propriétés|Valeurs|Remarques|
|---|---|---|---|
|Utilisateurs et groupes|Inclure|**Sélectionnez utilisateurs et groupes > utilisateurs et groupes** : sélectionnez des groupes spécifiques contenant des comptes d’utilisateurs ciblés.|Commencez par le groupe qui inclut les comptes d’utilisateurs pilotes.|
||Exclure|**Utilisateurs et groupes** : sélectionnez votre groupe d’exceptions d’accès conditionnel . comptes de service (identités d’application).|L’appartenance doit être modifiée selon les besoins, de manière temporaire.|
|Applications ou actions cloud|**Applications cloud > Include**|**Sélectionnez des applications** : sélectionnez les applications correspondant aux clients qui ne permettent pas l’authentification moderne.||
|Conditions|**Applications clientes**|Choisir **Oui** pour **configurer** <p> Effacer les coches pour les **applications** mobiles **et de navigateur et les clients de bureau**||

Dans la section **Contrôles d’accès** :

|Paramètre|Propriétés|Valeurs|Action|
|---|---|---|---|
|Accorder|**Bloquer l’accès**||Sélectionner|
||**Demander tous les contrôles sélectionnés**||Sélectionner|

**Sélectionnez Sélectionner** pour enregistrer les **paramètres d’octroi**.

Enfin, **sélectionnez Activer** pour **activer la stratégie**, puis **créez**.

Envisagez d’utiliser [l’outil What if](/azure/active-directory/active-directory-conditional-access-whatif) pour tester la stratégie.

Par Exchange Online, vous pouvez utiliser des stratégies d’authentification pour désactiver l’authentification de [base, ce](/exchange/clients-and-mobile-in-exchange-online/disable-basic-authentication-in-exchange-online) qui force toutes les demandes d’accès client à utiliser l’authentification moderne.

## <a name="high-risk-users-must-change-password"></a>Les utilisateurs à risque élevé doivent modifier leur mot de passe

Pour vous assurer que tous les comptes compromis par les utilisateurs à risque élevé sont obligés d’effectuer une modification de mot de passe lors de la signature, vous devez appliquer la stratégie suivante.

Connectez-vous au [portail Microsoft Azure (https://portal.azure.com)](https://portal.azure.com/) avec vos informations d’identification d’administrateur, puis accédez à **Azure AD Identity Protection > Stratégie d’utilisateur à risque**.

Dans la section **Affectations** :

|Type|Propriétés|Valeurs|Action|
|---|---|---|---|
|Utilisateurs|Inclure|**Tous les utilisateurs**|Sélectionner|
|Risque de l’utilisateur|**High**||Sélectionner|

Dans la deuxième section **Affectations** :

|Type|Propriétés|Valeurs|Action|
|---|---|---|---|
|Accès|**Autoriser l’accès**||Sélectionner|
|||**Exiger le changement du mot de passe**|Chèque|

Choisissez **Terminé** pour enregistrer les **paramètres Access** .

Enfin, **sélectionnez Sur** pour **Appliquer la stratégie**, puis sélectionnez **Enregistrer**.

Envisagez d’utiliser [l’outil What if](/azure/active-directory/active-directory-conditional-access-whatif) pour tester la stratégie.

Utilisez cette stratégie conjointement avec [configurer la protection Azure AD](/azure/active-directory/authentication/concept-password-ban-bad) mot de passe, qui détecte et bloque les mots de passe faibles connus, leurs variantes et d’autres termes faibles propres à votre organisation. L’Azure AD protection par mot de passe garantit que les mots de passe modifiés sont forts.

## <a name="apply-app-data-protection-policies"></a>Appliquer des stratégies de protection des données APP

Les API définissent les applications autorisées et les actions qu’elles peuvent prendre avec les données de votre organisation. Les choix disponibles dans APP permettent aux organisations d’adapter la protection à leurs besoins spécifiques. Pour certaines, il peut être difficile d’identifier les paramètres de stratégie nécessaires pour implémenter un scénario complet. Pour aider les organisations à hiérarchiser le renforcement de la sécurité des points de terminaison des clients mobiles, Microsoft a introduit une taxonomie pour son framework de protection des données des stratégies de protection des applications pour la gestion des applications mobiles iOS et Android.

Le framework de protection des données des stratégies de protection des applications est organisé en trois niveaux de configuration distincts, chaque niveau s’appuyant sur le niveau précédent :

- **Niveau 1 : Enterprise protection** des données de base garantit que les applications sont protégées par un code confidentiel et chiffrées et effectue des opérations de effacement sélective. Pour les appareils Android, ce niveau valide l’attestation des appareils Android. Il s’agit d’une configuration de niveau d’entrée qui fournit un contrôle de protection des données similaire dans les stratégies de boîte aux lettres Exchange Online et présente l’informatique ainsi que le nombre des utilisateurs aux stratégies de protection des applications.
- **Niveau 2 : Enterprise protection améliorée des** données introduit des mécanismes de prévention des fuites de données d’APPLICATION et des exigences minimales en matière de système d’exploitation. Il s’agit de la configuration qui s’applique à la plupart des utilisateurs mobiles accédant à des données professionnelles ou scolaires.
- **Niveau 3 : Enterprise** protection élevée des données introduit des mécanismes de protection des données avancés, une configuration améliorée du code confidentiel et la protection contre les menaces APP Mobile. Cette configuration est souhaitable pour les utilisateurs qui accèdent à des données à risque élevé.

Pour afficher les recommandations spécifiques pour chaque niveau de configuration et les applications minimales à protéger, consultez [Framework de protection des données à l’aide de stratégies de protection des applications](/mem/intune/apps/app-protection-framework).

À l’aide des principes décrits dans les configurations d’accès aux identités et aux appareils avec confiance zéro, les [niveaux](microsoft-365-policies-configurations.md) de protection de point de départ et de Enterprise sont étroitement mapés avec les paramètres de protection des données améliorés d’entreprise de niveau 2. Le niveau de protection de la sécurité spécialisé est étroitement map avec les paramètres de protection des données élevées d’entreprise de niveau 3.

|Niveau de protection|Stratégie de protection des applications|Plus d’informations|
|---|---|---|
|Point de départ|[Protection améliorée des données de niveau 2](/mem/intune/apps/app-protection-framework#level-2-enterprise-enhanced-data-protection)|Les paramètres de stratégie appliqués au niveau 2 incluent tous les paramètres de stratégie recommandés pour le niveau 1 et ajoutent ou mettent uniquement à jour les paramètres de stratégie ci-dessous pour implémenter davantage de contrôles et une configuration plus sophistiquée que le niveau 1.|
|Entreprise|[Protection améliorée des données de niveau 2](/mem/intune/apps/app-protection-framework#level-2-enterprise-enhanced-data-protection)|Les paramètres de stratégie appliqués au niveau 2 incluent tous les paramètres de stratégie recommandés pour le niveau 1 et ajoutent ou mettent uniquement à jour les paramètres de stratégie ci-dessous pour implémenter davantage de contrôles et une configuration plus sophistiquée que le niveau 1.|
|Sécurité spécialisée|[Niveau 3 de protection des données d’entreprise élevé](/mem/intune/apps/app-protection-framework#level-3-enterprise-high-data-protection)|Les paramètres de stratégie appliqués au niveau 3 incluent tous les paramètres de stratégie recommandés pour les niveaux 1 et 2 et ajoutent ou mettent uniquement à jour les paramètres de stratégie ci-dessous pour implémenter davantage de contrôles et une configuration plus sophistiquée que le niveau 2.|

Pour créer une stratégie de protection des applications pour chaque plateforme (iOS et Android) dans Microsoft Endpoint Manager à l’aide des paramètres de l’infrastructure de protection des données, vous pouvez :

1. Créez manuellement les stratégies en suivant les étapes de la procédure de création et de déploiement des stratégies de protection des applications [avec Microsoft Intune](/mem/intune/apps/app-protection-policies).
2. Importez [l’exemple de modèles JSON De l’infrastructure de configuration de la stratégie intune App Protection](https://github.com/microsoft/Intune-Config-Frameworks/tree/master/AppProtectionPolicies) avec les [scripts PowerShell d’Intune](https://github.com/microsoftgraph/powershell-intune-samples).

## <a name="require-approved-apps-and-app-protection"></a>Exiger des applications approuvées et la protection des applications

Pour appliquer les stratégies de protection des applications que vous avez appliquées dans Intune, vous devez créer une stratégie d’accès conditionnel pour exiger des applications clientes approuvées et les conditions définies dans les stratégies de protection des applications.

L’application de stratégies de protection des applications nécessite un ensemble de stratégies décrites dans La stratégie Exiger la protection des applications pour l’accès aux applications [cloud avec accès conditionnel](/azure/active-directory/conditional-access/app-protection-based-conditional-access). Ces stratégies sont incluses dans cet ensemble recommandé de stratégies de configuration des identités et des accès.

Pour créer la stratégie d’accès conditionnel qui nécessite des applications approuvées et la protection des applications, suivez les étapes de la stratégie Exiger des applications [clientes](/azure/active-directory/conditional-access/howto-policy-approved-app-or-app-protection#require-approved-client-apps-or-app-protection-policy-with-mobile-devices) approuvées ou protection des applications avec des appareils mobiles, qui permet uniquement aux comptes au sein des applications mobiles protégées par les stratégies de protection des applications d’accéder aux points de terminaison Microsoft 365.

   > [!NOTE]
   > Cette stratégie garantit que les utilisateurs mobiles peuvent accéder à Microsoft 365 points de terminaison à l’aide des applications applicables.

Cette stratégie empêche également les clients Exchange ActiveSync appareils mobiles de se connecter à Exchange Online. Toutefois, vous pouvez créer une stratégie distincte pour la gestion des Exchange ActiveSync sur tous les appareils. Pour plus d’informations, voir [Bloquer les clients ActiveSync](secure-email-recommended-policies.md#block-activesync-clients), ce qui empêche les clients Exchange ActiveSync qui exploitent l’authentification de base de se connecter à Exchange Online. Cette stratégie n’est pas illustré dans l’illustration en haut de cet article. Il est décrit et présenté dans les [recommandations de stratégie pour la sécurisation du courrier électronique](secure-email-recommended-policies.md).

 Cette stratégie exploite les contrôles d’octroi Exiger [une application cliente approuvée](/azure/active-directory/conditional-access/concept-conditional-access-grant#require-approved-client-app) et [Exiger une stratégie de protection des applications](/azure/active-directory/conditional-access/concept-conditional-access-grant#require-app-protection-policy).

Enfin, le blocage de l’authentification héritée pour d’autres applications clientes sur les appareils iOS et Android garantit que ces clients ne peuvent pas contourner les stratégies d’accès conditionnel. Si vous êtes en train de suivre les instructions de cet article, vous avez déjà configuré des clients Block qui ne sont pas pris en charge par [l’authentification moderne](#block-clients-that-dont-support-multi-factor).

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

- Administrateur d’appareils Android
- Android Entreprise
- iOS/iPadOS
- macOS
- Windows 8.1 et versions ultérieures
- Windows 10 et versions ultérieures

Pour créer des stratégies de conformité des appareils, connectez-vous au [Centre d’administration Microsoft Endpoint Manager](https://endpoint.microsoft.com) avec vos informations d’identification d’administrateur,  \> puis accédez aux stratégies de conformité **des** \> **appareils**. Sélectionner **Créer une stratégie**.

Pour que les stratégies de conformité des appareils soient déployées, elles doivent être affectées à des groupes d’utilisateurs. Vous affectez une stratégie après l’avoir créé et l’enregistrer. Dans le Centre d’administration, sélectionnez la stratégie, puis **affectations**. Après avoir sélectionné les groupes à recevoir, sélectionnez Enregistrer pour enregistrer cette  affectation de groupe et déployer la stratégie.

Pour obtenir des instructions pas à pas sur la création de stratégies de conformité dans Intune, voir Créer une stratégie de conformité [Microsoft Intune](/mem/intune/protect/create-compliance-policy) la documentation Intune.

### <a name="recommended-settings-for-ios"></a>Paramètres recommandés pour iOS

iOS/iPadOS prend en charge plusieurs scénarios d’inscription, dont deux sont couverts dans le cadre de cette infrastructure :

- [Inscription d’appareils pour les](/mem/intune/enrollment/ios-enroll) appareils personnels : ces appareils sont personnels et utilisés à la fois pour un usage personnel et personnel.
- [Surveillance de](/mem/intune/enrollment/device-enrollment-program-enroll-ios) l’inscription automatisée des appareils pour les appareils d’entreprise : ces appareils sont des appareils d’entreprise, associés à un seul utilisateur et utilisés exclusivement à des usages personnels et non à des usages personnels.

L’infrastructure de configuration de la sécurité iOS/iPadOS est organisée en plusieurs scénarios de configuration distincts, fournissant des conseils pour les appareils personnels et supervisés.

Pour les appareils personnels :

- Sécurité de base (niveau 1) : Microsoft recommande cette configuration comme configuration de sécurité minimale pour les appareils personnels où les utilisateurs accèdent aux données scolaires ou professionnels. Cela s’effectue en appliquant des stratégies de mot de passe, des caractéristiques de verrouillage d’appareil et en désactivant certaines fonctions d’appareil (par exemple, les certificats non approuvés).
- Sécurité renforcée (niveau 2) : Microsoft recommande cette configuration pour les appareils où les utilisateurs accèdent à des informations sensibles ou confidentielles. Cette configuration enrôle les contrôles de partage de données. Cette configuration s’applique à la plupart des utilisateurs mobiles accédant à des données professionnelles ou scolaires sur un appareil.
- Haute sécurité (niveau 3) : Microsoft recommande cette configuration pour les appareils utilisés par des utilisateurs ou des groupes spécifiques à risque élevé (les utilisateurs qui gèrent des données hautement sensibles lorsque la divulgation non autorisée entraîne une perte matérielle considérable pour l’organisation). Cette configuration permet de renforcer les stratégies de mot de passe, de désactiver certaines fonctions d’appareil et d’appliquer des restrictions de transfert de données supplémentaires.

Pour les appareils supervisés :

- Sécurité de base (niveau 1) : Microsoft recommande cette configuration comme configuration de sécurité minimale pour les appareils supervisés où les utilisateurs accèdent aux données scolaires ou professionnels. Cela s’effectue en appliquant des stratégies de mot de passe, des caractéristiques de verrouillage d’appareil et en désactivant certaines fonctions d’appareil (par exemple, les certificats non approuvés).
- Sécurité renforcée (niveau 2) : Microsoft recommande cette configuration pour les appareils où les utilisateurs accèdent à des informations sensibles ou confidentielles. Cette configuration permet d’effectuer des contrôles de partage de données et de bloquer l’accès aux périphériques USB. Cette configuration s’applique à la plupart des utilisateurs mobiles accédant à des données professionnelles ou scolaires sur un appareil.
- Haute sécurité (niveau 3) : Microsoft recommande cette configuration pour les appareils utilisés par des utilisateurs ou des groupes spécifiques à risque élevé (les utilisateurs qui gèrent des données hautement sensibles lorsque la divulgation non autorisée entraîne une perte matérielle considérable pour l’organisation). Cette configuration permet de renforcer les stratégies de mot de passe, de désactiver certaines fonctions d’appareil, d’appliquer des restrictions de transfert de données supplémentaires et d’installer des applications via le programme d’achat en volume d’Apple.

À l’aide des principes décrits dans les configurations d’accès aux identités et aux appareils Avec confiance zéro, les [niveaux](microsoft-365-policies-configurations.md) de protection de point de départ et de Enterprise sont étroitement mapés avec les paramètres de sécurité améliorés de niveau 2. Le niveau de protection de la sécurité spécialisé est étroitement map avec les paramètres de sécurité élevés de niveau 3.

|Niveau de protection  |Stratégie d’appareil |Plus d’informations  |
|---------|---------|---------|
|Point de départ     |Sécurité renforcée (niveau 2)         |Les paramètres de stratégie appliqués au niveau 2 incluent tous les paramètres de stratégie recommandés pour le niveau 1 et ajoutent ou mettent uniquement à jour les paramètres de stratégie ci-dessous pour implémenter davantage de contrôles et une configuration plus sophistiquée que le niveau 1.         |
|Entreprise     |Sécurité renforcée (niveau 2)         |Les paramètres de stratégie appliqués au niveau 2 incluent tous les paramètres de stratégie recommandés pour le niveau 1 et ajoutent ou mettent uniquement à jour les paramètres de stratégie ci-dessous pour implémenter davantage de contrôles et une configuration plus sophistiquée que le niveau 1.         |
|Sécurité spécialisée     |Haute sécurité (Niveau 3)         |Les paramètres de stratégie appliqués au niveau 3 incluent tous les paramètres de stratégie recommandés pour les niveaux 1 et 2 et ajoutent ou mettent uniquement à jour les paramètres de stratégie ci-dessous pour implémenter davantage de contrôles et une configuration plus sophistiquée que le niveau 2.         |

Pour voir les recommandations spécifiques en matière de conformité et de restriction d’appareil pour chaque niveau de configuration, consultez l’infrastructure de configuration de sécurité [iOS/iPadOS](/mem/intune/enrollment/ios-ipados-configuration-framework).

### <a name="recommended-settings-for-android"></a>Paramètres recommandés pour Android

Android Enterprise prend en charge plusieurs scénarios d’inscription, dont deux sont couverts dans le cadre de cette infrastructure :

- [Profil Enterprise travail Android](/intune/android-work-profile-enroll) : ce modèle d’inscription est généralement utilisé pour les appareils personnels, où le service juridique souhaite fournir une frontière de séparation claire entre les données personnelles et les données personnelles. Les stratégies contrôlées par le personnel de l’information garantissent que les données de travail ne peuvent pas être transférées dans le profil personnel.
- [Android Enterprise](/intune/android-fully-managed-enroll) entièrement gérés : ces appareils sont gérés par l’entreprise, associés à un seul utilisateur et utilisés exclusivement à des usages personnels et non à des usages personnels.

L’infrastructure Enterprise de configuration de la sécurité Android est organisée en plusieurs scénarios de configuration distincts, fournissant des conseils pour les profils de travail et les scénarios entièrement gérés.

Pour les appareils Enterprise profils de travail Android :

- Sécurité renforcée du profil professionnel (niveau 2) : Microsoft recommande cette configuration comme configuration de sécurité minimale pour les appareils personnels où les utilisateurs accèdent aux données scolaires ou professionnels. Cette configuration introduit des exigences de mot de passe, sépare les données professionnelles et personnelles, et valide l’attestation des appareils Android.
- Profil professionnel haute sécurité (niveau 3) : Microsoft recommande cette configuration pour les appareils utilisés par des utilisateurs ou des groupes spécifiques à risque élevé (les utilisateurs qui gèrent des données hautement sensibles lorsque la divulgation non autorisée entraîne une perte matérielle considérable pour l’organisation). Cette configuration introduit la protection contre les menaces mobiles ou Microsoft Defender pour le point de terminaison, définit la version minimale d’Android, met en place des stratégies de mot de passe plus puissantes et limite davantage la séparation personnelle et le travail.

Pour les appareils Android Entreprise entièrement gérés :

- Sécurité de base entièrement gérée (niveau 1) : Microsoft recommande cette configuration comme configuration de sécurité minimale pour un appareil d’entreprise. Cette configuration s’applique à la plupart des utilisateurs mobiles accédant aux données scolaires ou professionnels. Cette configuration introduit des exigences de mot de passe, définit la version minimale d’Android et applique certaines restrictions d’appareil.
- Sécurité améliorée entièrement gérée (niveau 2) : Microsoft recommande cette configuration pour les appareils où les utilisateurs accèdent à des informations sensibles ou confidentielles. Cette configuration permet de renforcer les stratégies de mot de passe et de désactiver les fonctionnalités utilisateur/compte.
- Haute sécurité entièrement gérée (niveau 3) : Microsoft recommande cette configuration pour les appareils utilisés par des utilisateurs ou des groupes spécifiques à risque élevé (les utilisateurs qui gèrent des données hautement sensibles lorsque la divulgation non autorisée entraîne une perte matérielle considérable pour l’organisation). Cette configuration augmente la version minimale d’Android, introduit la protection contre les menaces mobiles ou Microsoft Defender pour le point de terminaison et applique des restrictions supplémentaires sur les appareils.

À l’aide des principes décrits dans les configurations d’accès aux identités et aux appareils avec confiance zéro, les [niveaux](microsoft-365-policies-configurations.md) de protection de point de départ et de Enterprise sont étroitement mapés avec la sécurité de base de niveau 1 pour les appareils personnels et les paramètres de sécurité améliorés de niveau 2 pour les appareils entièrement gérés. Le niveau de protection de la sécurité spécialisé est étroitement map avec les paramètres de sécurité élevés de niveau 3.

Pour les appareils Enterprise profils de travail Android :

|Niveau de protection  |Stratégie d’appareil |Plus d’informations  |
|---------|---------|---------|
|Point de départ     |Profil professionnel : sécurité de base (niveau 1)      |N/A         |
|Entreprise     |Profil professionnel : sécurité de base (niveau 1)         |N/A         |
|Point de départ     |Gestion complète : sécurité renforcée (niveau 2)       |Les paramètres de stratégie appliqués au niveau 2 incluent tous les paramètres de stratégie recommandés pour le niveau 1 et ajoutent ou mettent uniquement à jour les paramètres de stratégie ci-dessous pour implémenter davantage de contrôles et une configuration plus sophistiquée que le niveau 1.         |
|Entreprise     |Gestion complète : sécurité renforcée (niveau 2)         |Les paramètres de stratégie appliqués au niveau 2 incluent tous les paramètres de stratégie recommandés pour le niveau 1 et ajoutent ou mettent uniquement à jour les paramètres de stratégie ci-dessous pour implémenter davantage de contrôles et une configuration plus sophistiquée que le niveau 1.         |
|Sécurité spécialisée     |Haute sécurité (Niveau 3)         |Les paramètres de stratégie appliqués au niveau 3 incluent tous les paramètres de stratégie recommandés pour les niveaux 1 et 2 et ajoutent ou mettent uniquement à jour les paramètres de stratégie ci-dessous pour implémenter davantage de contrôles et une configuration plus sophistiquée que le niveau 2.         |

Pour voir les recommandations spécifiques en matière de conformité et de restriction d’appareil pour chaque niveau de configuration, consultez l’infrastructure de configuration de sécurité [Enterprise Android](/mem/intune/enrollment/android-configuration-framework).

### <a name="recommended-settings-for-windows-10-and-later"></a>Paramètres recommandés pour Windows 10 et ultérieures

Les paramètres suivants sont recommandés pour les PC exécutant Windows 10 et ultérieurs, comme configuré à l’étape **2 : Paramètres** de conformité, du processus de création de stratégie.

Pour plus **d'> Windows d’évaluation du service d’attestation** d’état d'> Windows, consultez ce tableau.

|Propriétés|Valeur|Action|
|---|---|---|
|Exiger BitLocker|Require (Rendre obligatoire)|Sélectionner|
|Exiger que le démarrage sécurisé soit activé sur l’appareil|Require (Rendre obligatoire)|Sélectionner|
|Exiger l’intégrité du code|Require (Rendre obligatoire)|Sélectionner|

Pour les **propriétés d’appareil**, spécifiez les valeurs appropriées pour les versions de système d’exploitation en fonction de vos stratégies informatiques et de sécurité.

Pour la **conformité configuration Manager**, sélectionnez **Exiger**.

Pour **la sécurité du** système, consultez ce tableau.

|Type|Propriétés|Valeur|Action|
|---|---|---|---|
|Password|Exiger un mot de passe pour déverrouiller des appareils mobiles|Require (Rendre obligatoire)|Sélectionner|
||Mots de passe simples|Bloquer|Sélectionner|
||Type de mot de passe|Valeur par défaut de l’appareil|Sélectionner|
||Longueur minimale du mot de passe|6 |Type|
||Nombre maximal de minutes d’inactivité avant demande du mot de passe|15 |Type <p> Ce paramètre est pris en charge pour les versions Android 4.0 et supérieures ou KNOX 4.0 et versions ultérieures. Pour les appareils iOS, il est pris en charge pour iOS 8.0 et les appareils supérieurs.|
||Expiration du mot de passe (jours)|41|Type|
||Nombre de mots de passe précédents avant d’autoriser leur réutilisation|5|Type|
||Exiger un mot de passe lorsque l’appareil revient d’un état inactif (mobile et holographique)|Require (Rendre obligatoire)|Disponible pour les Windows 10 et ultérieures|
|Chiffrement|Chiffrement du stockage de données sur l’appareil|Require (Rendre obligatoire)|Sélectionner|
|Sécurité des appareils|Pare-feu|Require (Rendre obligatoire)|Sélectionner|
||Antivirus|Require (Rendre obligatoire)|Sélectionner|
||Logiciel anti-espion|Require (Rendre obligatoire)|Sélectionner <p> Ce paramètre nécessite une solution anti-espion inscrite auprès de l’Sécurité Windows app.|
|Defender pour le cloud|Logiciel anti-programme malveillant Microsoft Defender|Require (Rendre obligatoire)|Sélectionner|
||Version minimale du logiciel anti-programme malveillant Microsoft Defender||Type <p> Uniquement pris en charge pour Windows 10 bureau. Microsoft recommande de ne pas avoir plus de cinq versions en retard par rapport à la version la plus récente.|
||Signature du logiciel anti-programme malveillant Microsoft Defender à jour|Require (Rendre obligatoire)|Sélectionner|
||Protection en temps réel|Require (Rendre obligatoire)|Sélectionner <p> Uniquement pris en charge pour Windows 10 et les ordinateurs de bureau ultérieurs|

#### <a name="microsoft-defender-for-endpoint"></a>Microsoft Defender pour point de terminaison

|Type|Propriétés|Valeur|Action|
|---|---|---|---|
|Règles Microsoft Defender pour les points de terminaison dans le Centre d Microsoft Endpoint Manager’administration Microsoft Defender|[Exiger que l’appareil soit au niveau ou sous le score de risque de l’ordinateur](/mem/intune/protect/advanced-threat-protection-configure#create-and-assign-compliance-policy-to-set-device-risk-level)|Moyen|Sélectionner|

<!--
## Require compliant PCs (but not compliant phones and tablets)

Before adding a policy to require compliant PCs, be sure to enroll your devices for management in Intune. Using multi-factor authentication is recommended before enrolling devices into Intune for assurance that the device is in the possession of the intended user.

To require compliant PCs:

1. Go to the [Azure portal](https://portal.azure.com), and sign in with your credentials.
2. In the list of Azure services, choose **Azure Active Directory**.
3. In the **Manage** list, choose **Security**, and then choose **Conditional Access**.
4. Choose **New policy** and type the new policy's name.

5. Under **Assignments**, choose **Users and groups** and include who you want the policy to apply to. Also exclude your Conditional Access exclusion group.

6. Under **Assignments**, choose **Cloud apps or actions**.

7. For **Include**, choose **Select apps > Select**, and then select the desired apps from the **Cloud apps** list. For example, select Office 365. Choose **Select** when done.

8. To require compliant PCs (but not compliant phones and tablets), under **Assignments**, choose **Conditions > Device platforms**. Select **Yes** for **Configure**. Choose  **Select device platforms**, select **Yes** and select **Any device** and under Exclude select **iOS** and **Android**, and then choose **Done**.

9. Under **Access controls**, choose **Grant** .

10. Choose **Grant access** and then check **Require device to be marked as compliant**. For multiple controls, select **Require all the selected controls**. When complete, choose **Select**.

11. Select **On** for **Enable policy**, and then choose **Create**.

> [!NOTE]
> Make sure that your device is compliant before enabling this policy. Otherwise, you could get locked out and will be unable to change this policy until your user account has been added to the Conditional Access exclusion group.

--> 

## <a name="require-compliant-pcs-and-mobile-devices"></a>Exiger des PC et des appareils mobiles conformes

Pour exiger la conformité pour tous les appareils :

1. Accédez au [portail Azure](https://portal.azure.com) et connectez-vous avec vos informations d’identification.
2. Dans la liste des services Azure, choisissez **Azure Active Directory**.
3. Dans la **liste Gérer** , choisissez **Sécurité**, puis accès **conditionnel**.
4. Choisissez **Nouvelle stratégie** et tapez le nom de la nouvelle stratégie.

5. Sous **Affectations**, sélectionnez **Utilisateurs et groupes** et incluez à qui vous souhaitez que la stratégie s’applique. Excluez également votre groupe d’exclusions d’accès conditionnel.

6. Sous **Affectations**, sélectionnez **Applications ou actions cloud**.

7. For **Include**, choose **Select apps > Select**, and then select the desired apps from the **Cloud apps** list. Par exemple, sélectionnez Office 365. **Sélectionnez Sélectionner** lorsque vous avez terminé.

8. Sous **Contrôles d’accès**, **sélectionnez Accorder** .

9. Choisissez **Accorder l’accès** , puis vérifiez **Exiger que l’appareil soit marqué comme conforme**. Pour plusieurs contrôles, **sélectionnez Exiger tous les contrôles sélectionnés**. Lorsque vous avez terminé, **sélectionnez Sélectionner**.

10. **Sélectionnez Activer** **pour activer la stratégie**, puis sélectionnez **Créer**.

> [!NOTE]
> Assurez-vous que votre appareil est conforme avant d’activer cette stratégie. Dans le cas contraire, vous risquez d’être verrouillé et ne pourront pas modifier cette stratégie tant que votre compte d’utilisateur n’aura pas été ajouté au groupe d’exclusions d’accès conditionnel.

## <a name="next-step"></a>Étape suivante

[![Étape 3 : Stratégies pour les utilisateurs invités et externes.](../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-3.png#lightbox)](identity-access-policies-guest-access.md)

[En savoir plus sur les recommandations de stratégie pour les utilisateurs invités et externes](identity-access-policies-guest-access.md)
