---
title: Stratégies courantes d’identité Confiance nulle et d’accès aux appareils - Microsoft 365 pour les | d’entreprise Microsoft Docs
description: Décrit les configurations et stratégies d’accès aux identités et aux appareils Confiance nulle courantes recommandées.
ms.author: dansimp
author: dansimp
manager: dansimp
ms.service: microsoft-365-security
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
ms.subservice: mdo
search.appverid: met150
ms.openlocfilehash: dd0182bda8e23537a1c7914270037ea61c16feaa
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67686634"
---
# <a name="common-zero-trust-identity-and-device-access-policies"></a>Stratégies d’accès aux identités et aux appareils Confiance nulle courantes

Cet article décrit les stratégies d’accès aux identités et aux appareils Confiance nulle courantes recommandées pour sécuriser l’accès aux services cloud Microsoft 365, notamment les applications locales publiées avec Azure Active Directory (Azure AD) Proxy d'application.

Cette aide explique comment déployer les stratégies recommandées dans un environnement nouvellement approvisionné. La configuration de ces stratégies dans un environnement lab distinct vous permet de comprendre et d’évaluer les stratégies recommandées avant de mettre en lots le déploiement dans vos environnements de préproduction et de production. Votre environnement nouvellement approvisionné peut être cloud uniquement ou hybride pour refléter vos besoins d’évaluation.

## <a name="policy-set"></a>Ensemble de stratégies

Le diagramme suivant illustre l’ensemble de stratégies recommandé. Il indique le niveau de protection auquel chaque stratégie s’applique et si les stratégies s’appliquent aux PC, aux téléphones et tablettes, ou aux deux catégories d’appareils. Il indique également où vous configurez ces stratégies.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-access-policies-byplan.png" alt-text="Stratégies courantes pour configurer Confiance nulle l’identité et l’accès aux appareils." lightbox="../../media/microsoft-365-policies-configurations/identity-device-access-policies-byplan.png":::

<!--

Here's a one-page PDF summary:

[![Thumb image for the Zero Trust identity and device protection for Microsoft 365 handout.](../../media/microsoft-365-policies-configurations/zero-trust-id-device-protection-model-handout-thumbnail.png)](../../downloads/MSFT-cloud-architecture-identity-device-protection-handout.pdf) <br> [View as a PDF](../../downloads/MSFT-cloud-architecture-identity-device-protection-handout.pdf) \| [Download as a PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/MSFT-cloud-architecture-identity-device-protection-handout.pdf)

-->

Le reste de cet article explique comment configurer ces stratégies.

> [!NOTE]
> Il est recommandé d’exiger l’utilisation de l’authentification multifacteur (MFA) avant d’inscrire des appareils dans Intune pour s’assurer que l’appareil est en possession de l’utilisateur prévu. Vous devez inscrire des appareils dans Intune avant de pouvoir appliquer des stratégies de conformité des appareils.

Pour vous donner le temps d’accomplir ces tâches, nous vous recommandons d’implémenter les stratégies de point de départ dans l’ordre répertorié dans ce tableau. Toutefois, les stratégies d’authentification multifacteur pour les niveaux de sécurité d’entreprise et spécialisés peuvent être implémentées à tout moment.

|Niveau de protection|Stratégies|Informations supplémentaires|Licences|
|---|---|---|---|
|**Point de départ**|[Exiger l’authentification multifacteur lorsque le risque de connexion est *moyen* ou *élevé*](#require-mfa-based-on-sign-in-risk)||Microsoft 365 E5 ou Microsoft 365 E3 avec le module complémentaire Sécurité E5|
||[Bloquer les clients ne prenant pas en charge l’authentification moderne](#block-clients-that-dont-support-multi-factor)|Les clients qui n’utilisent pas l’authentification moderne peuvent contourner les stratégies d’accès conditionnel. Il est donc important de les bloquer.|Microsoft 365 E3 ou E5|
||[Les utilisateurs à risque élevé doivent modifier leur mot de passe](#high-risk-users-must-change-password)|Force les utilisateurs à modifier leur mot de passe lors de la connexion si une activité à haut risque est détectée pour leur compte.|Microsoft 365 E5 ou Microsoft 365 E3 avec le module complémentaire Sécurité E5|
||[Appliquer la protection des données des stratégies de protection des applications (APP)](#apply-app-data-protection-policies)|Une stratégie Intune App Protection par plateforme (Windows, iOS/iPadOS, Android).|Microsoft 365 E3 ou E5|
||[Exiger des applications approuvées et une protection des applications](#require-approved-apps-and-app-protection)|Applique la protection des applications mobiles pour les téléphones et les tablettes à l’aide d’iOS, iPadOS ou Android.|Microsoft 365 E3 ou E5|
|**Enterprise**|[Exiger l’authentification multifacteur lorsque le risque de connexion est *faible*, *moyen* ou *élevé*](#require-mfa-based-on-sign-in-risk)||Microsoft 365 E5 ou Microsoft 365 E3 avec le module complémentaire Sécurité E5|
||[Définir des stratégies de conformité des appareils](#define-device-compliance-policies)|Une stratégie pour chaque plateforme.|Microsoft 365 E3 ou E5|
||[Exiger des PC et des appareils mobiles conformes](#require-compliant-pcs-and-mobile-devices)|Applique Intune gestion pour les PC (Windows ou macOS) et les téléphones ou tablettes (iOS, iPadOS ou Android).|Microsoft 365 E3 ou E5|
|**Sécurité spécialisée**|[*Toujours* exiger l’authentification multifacteur](#assigning-policies-to-groups-and-users)||Microsoft 365 E3 ou E5|

## <a name="assigning-policies-to-groups-and-users"></a>Affectation de stratégies à des groupes et des utilisateurs

Avant de configurer des stratégies, identifiez les groupes Azure AD que vous utilisez pour chaque niveau de protection. En règle générale, la protection des points de départ s’applique à tous les membres de l’organisation. Un utilisateur inclus pour le point de départ et la protection d’entreprise aura toutes les stratégies de point de départ appliquées, ainsi que les stratégies d’entreprise. La protection est cumulative et la stratégie la plus restrictive est appliquée.

Une pratique recommandée consiste à créer un groupe Azure AD pour l’exclusion de l’accès conditionnel. Ajoutez ce groupe à toutes vos stratégies d’accès conditionnel dans la valeur **Exclure** du paramètre **Utilisateurs et groupes** dans la section **Affectations** . Cela vous donne une méthode pour fournir l’accès à un utilisateur pendant que vous résolvez les problèmes d’accès. Cette solution est recommandée en tant que solution temporaire uniquement. Surveillez les modifications apportées à ce groupe et assurez-vous que le groupe d’exclusion est utilisé uniquement comme prévu.

Voici un exemple d’affectation de groupe et d’exclusions pour exiger l’authentification multifacteur.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-policies-assignment.png" alt-text="Exemples d’affectation de groupe et d’exclusions pour les stratégies MFA" lightbox="../../media/microsoft-365-policies-configurations/identity-access-policies-assignment.png":::

Voici les résultats :

- Tous les utilisateurs doivent utiliser l’authentification multifacteur lorsque le risque de connexion est moyen ou élevé.

- Les membres du groupe du personnel exécutif doivent utiliser l’authentification multifacteur lorsque le risque de connexion est faible, moyen ou élevé.

  Dans ce cas, les membres du groupe Du personnel exécutif correspondent à la fois au point de départ et aux stratégies d’accès conditionnel d’entreprise. Les contrôles d’accès pour les deux stratégies sont combinés, ce qui dans ce cas équivaut à la stratégie d’accès conditionnel d’entreprise.

- Les membres du groupe Top Secret Project X sont toujours tenus d’utiliser l’authentification multifacteur

  Dans ce cas, les membres du groupe Projet X top secret correspondent à la fois au point de départ et aux stratégies d’accès conditionnel de sécurité spécialisées. Les contrôles d’accès pour les deux stratégies sont combinés. Étant donné que le contrôle d’accès pour la stratégie d’accès conditionnel de sécurité spécialisée est plus restrictif, il est utilisé.

Soyez prudent lors de l’application de niveaux de protection plus élevés aux groupes et aux utilisateurs. Par exemple, les membres du groupe Top Secret Project X doivent utiliser l’authentification multifacteur chaque fois qu’ils se connectent, même s’ils ne travaillent pas sur le contenu de sécurité spécialisé pour Project X.

Tous les groupes Azure AD créés dans le cadre de ces recommandations doivent être créés en tant que groupes Microsoft 365. Cela est important pour le déploiement d’étiquettes de confidentialité lors de la sécurisation des documents dans Microsoft Teams et SharePoint.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-AAD-groups.png" alt-text="Création d’un groupe Microsoft 365" lightbox="../../media/microsoft-365-policies-configurations/identity-device-AAD-groups.png":::

## <a name="require-mfa-based-on-sign-in-risk"></a>Exiger l’authentification multifacteur en fonction du risque de connexion

Vos utilisateurs doivent s’inscrire à l’authentification multifacteur avant d’en exiger l’utilisation. Si vous avez Microsoft 365 E5, Microsoft 365 E3 avec le module complémentaire sécurité E5, Office 365 avec EMS E5 ou des licences de Azure AD Premium P2 individuelles, vous pouvez utiliser la stratégie d’inscription MFA avec Azure AD Identity Protection pour exiger que les utilisateurs s’inscrivent à l’authentification multifacteur. Le [travail requis](identity-access-prerequisites.md) inclut l’inscription de tous les utilisateurs auprès de l’authentification multifacteur.

Une fois vos utilisateurs inscrits, vous pouvez exiger l’authentification multifacteur pour la connexion avec une nouvelle stratégie d’accès conditionnel.

1. Accédez au [portail Azure](https://portal.azure.com) et connectez-vous avec vos informations d’identification.
2. Dans la liste des services Azure, choisissez **Azure Active Directory**.
3. Dans la liste **Gérer** , choisissez **Sécurité**, puis choisissez **Accès conditionnel**.
4. Choisissez **Nouvelle stratégie** et tapez le nom de la nouvelle stratégie.

Les tableaux suivants décrivent les paramètres de stratégie d’accès conditionnel pour exiger l’authentification multifacteur en fonction du risque de connexion.

Dans la section **Affectations** :

|Setting|Propriétés|Valeurs|Remarques|
|---|---|---|---|
|Utilisateurs et groupes|Inclure|**Sélectionner des utilisateurs et des groupes > Utilisateurs et groupes** : sélectionnez des groupes spécifiques contenant des comptes d’utilisateurs ciblés.|Commencez par le groupe qui inclut les comptes d’utilisateur pilotes.|
||Exclure|**Utilisateurs et groupes** : sélectionnez votre groupe d’exceptions d’accès conditionnel ; comptes de service (identités d’application).|L’appartenance doit être modifiée temporairement en fonction des besoins.|
|Applications ou actions cloud|**Applications cloud > Include**|**Sélectionner des applications** : sélectionnez les applications auxquelles vous souhaitez appliquer cette stratégie. Par exemple, sélectionnez Exchange Online.||
|Conditions|||Configurez des conditions spécifiques à votre environnement et à vos besoins.|
||Risque de connexion||Consultez les conseils du tableau suivant.|

### <a name="sign-in-risk-condition-settings"></a>Paramètres de condition de risque de connexion

Appliquez les paramètres de niveau de risque en fonction du niveau de protection que vous ciblez.

|Niveau de protection|Valeurs de niveau de risque nécessaires|Action|
|---|---|---|
|Point de départ|Élevé, moyen|Vérifiez les deux.|
|Entreprise|Élevé, moyen, faible|Vérifiez les trois.|
|Sécurité spécialisée||Laissez toutes les options désactivées pour appliquer toujours l’authentification multifacteur.|

Dans la section **Contrôles d’accès** :

|Setting|Propriétés|Valeurs|Action|
|---|---|---|---|
|Accorder|**Grant access**||Sélectionner|
|||**Exiger l’authentification multifacteur**|Chèque|
||**Demander tous les contrôles sélectionnés**||Sélectionner|

Choisissez **Sélectionner** pour enregistrer les paramètres **d’octroi** .

Enfin, sélectionnez **Activé** pour **activer la stratégie**, puis **choisissez Créer**.

Envisagez également d’utiliser l’outil [What if](/azure/active-directory/active-directory-conditional-access-whatif) pour tester la stratégie.

## <a name="block-clients-that-dont-support-multi-factor"></a>Bloquer les clients qui ne prennent pas en charge multifacteur

Utilisez les paramètres de ces tables pour une stratégie d’accès conditionnel afin de bloquer les clients qui ne prennent pas en charge l’authentification multifacteur.

Consultez [cet article](../../enterprise/microsoft-365-client-support-multi-factor-authentication.md) pour obtenir la liste des clients dans Microsoft 365 qui prennent en charge l’authentification multifacteur.

Dans la section **Affectations** :

|Setting|Propriétés|Valeurs|Remarques|
|---|---|---|---|
|Utilisateurs et groupes|Inclure|**Sélectionner des utilisateurs et des groupes > Utilisateurs et groupes** : sélectionnez des groupes spécifiques contenant des comptes d’utilisateurs ciblés.|Commencez par le groupe qui inclut les comptes d’utilisateur pilotes.|
||Exclure|**Utilisateurs et groupes** : sélectionnez votre groupe d’exceptions d’accès conditionnel ; comptes de service (identités d’application).|L’appartenance doit être modifiée temporairement en fonction des besoins.|
|Applications ou actions cloud|**Applications cloud > Include**|**Sélectionner des applications** : sélectionnez les applications correspondant aux clients qui ne prennent pas en charge l’authentification moderne.||
|Conditions|**Applications clientes**|Choisir **Oui** pour **configurer** <p> Effacer les coches pour les applications **navigateur** et **mobile et les clients de bureau**||

Dans la section **Contrôles d’accès** :

|Setting|Propriétés|Valeurs|Action|
|---|---|---|---|
|Accorder|**Bloquer l’accès**||Sélectionner|
||**Demander tous les contrôles sélectionnés**||Sélectionner|

Choisissez **Sélectionner** pour enregistrer les paramètres **d’octroi** .

Enfin, sélectionnez **Activé** pour **activer la stratégie**, puis **choisissez Créer**.

Envisagez d’utiliser l’outil [What if](/azure/active-directory/active-directory-conditional-access-whatif) pour tester la stratégie.

Pour Exchange Online, vous pouvez utiliser des stratégies d’authentification pour [désactiver l’authentification de base](/exchange/clients-and-mobile-in-exchange-online/disable-basic-authentication-in-exchange-online), ce qui force toutes les demandes d’accès client à utiliser l’authentification moderne.

## <a name="high-risk-users-must-change-password"></a>Les utilisateurs à risque élevé doivent modifier leur mot de passe

Pour vous assurer que les comptes compromis de tous les utilisateurs à haut risque sont obligés d’effectuer une modification de mot de passe lors de la connexion, vous devez appliquer la stratégie suivante.

Connectez-vous au [portail Microsoft Azure (https://portal.azure.com)](https://portal.azure.com/) avec vos informations d’identification d’administrateur, puis accédez à **Azure AD Identity Protection > Stratégie d’utilisateur à risque**.

Dans la section **Affectations** :

|Type|Propriétés|Valeurs|Action|
|---|---|---|---|
|Utilisateurs|Inclure|**Tous les utilisateurs**|Sélectionner|
|Risque de l’utilisateur|**High**||Sélectionner|

Dans la deuxième section **Affectations** :

|Type|Propriétés|Valeurs|Action|
|---|---|---|---|
|Access|**Autoriser l’accès**||Sélectionner|
|||**Exiger le changement du mot de passe**|Chèque|

Choisissez **Terminé** pour enregistrer les paramètres **d’accès** .

Enfin, sélectionnez **Activé** pour **appliquer la stratégie**, puis **sélectionnez Enregistrer**.

Envisagez d’utiliser l’outil [What if](/azure/active-directory/active-directory-conditional-access-whatif) pour tester la stratégie.

Utilisez cette stratégie conjointement avec [Configurer la protection par mot de passe Azure AD](/azure/active-directory/authentication/concept-password-ban-bad), qui détecte et bloque les mots de passe faibles connus et leurs variantes, ainsi que des termes faibles supplémentaires spécifiques à votre organisation. L’utilisation de la protection par mot de passe Azure AD garantit que les mots de passe modifiés sont forts.

## <a name="apply-app-data-protection-policies"></a>Appliquer des stratégies de protection des données APP

Les API définissent les applications autorisées et les actions qu’elles peuvent effectuer avec les données de votre organisation. Les choix disponibles dans APP permettent aux organisations d’adapter la protection à leurs besoins spécifiques. Pour certaines, il peut être difficile d’identifier les paramètres de stratégie nécessaires pour implémenter un scénario complet. Pour aider les organisations à hiérarchiser le renforcement de la sécurité des points de terminaison des clients mobiles, Microsoft a introduit une taxonomie pour son framework de protection des données des stratégies de protection des applications pour la gestion des applications mobiles iOS et Android.

Le framework de protection des données des stratégies de protection des applications est organisé en trois niveaux de configuration distincts, chaque niveau s’appuyant sur le niveau précédent :

- **Niveau 1 : La protection des données de base de l’entreprise** garantit que les applications sont protégées par un code confidentiel et chiffrées et effectue des opérations de réinitialisation sélectives. Pour les appareils Android, ce niveau valide l’attestation des appareils Android. Il s’agit d’une configuration de niveau d’entrée qui fournit un contrôle de protection des données similaire dans les stratégies de boîte aux lettres Exchange Online et présente l’informatique ainsi que le nombre des utilisateurs aux stratégies de protection des applications.
- **Niveau 2 : La protection améliorée des données d’entreprise** introduit des mécanismes de prévention des fuites de données APP et des exigences minimales du système d’exploitation. Il s’agit de la configuration qui s’applique à la plupart des utilisateurs mobiles accédant à des données professionnelles ou scolaires.
- **Niveau 3 : La protection élevée des données d’entreprise** introduit des mécanismes de protection avancée des données, une configuration améliorée du code confidentiel et app mobile threat defense. Cette configuration est souhaitable pour les utilisateurs qui accèdent à des données à risque élevé.

Pour afficher les recommandations spécifiques pour chaque niveau de configuration et les applications minimales à protéger, consultez [Framework de protection des données à l’aide de stratégies de protection des applications](/mem/intune/apps/app-protection-framework).

À l’aide des principes [décrits dans Confiance nulle configurations d’identité et d’accès aux appareils](microsoft-365-policies-configurations.md), les niveaux de point de départ et de protection d’entreprise correspondent étroitement aux paramètres de protection des données améliorés de niveau 2 entreprise. Le niveau de protection de sécurité spécialisé est étroitement lié aux paramètres de protection des données élevées d’entreprise de niveau 3.

|Niveau de protection|Stratégie de protection des applications|Plus d’informations|
|---|---|---|
|Point de départ|[Protection améliorée des données de niveau 2](/mem/intune/apps/app-protection-framework#level-2-enterprise-enhanced-data-protection)|Les paramètres de stratégie appliqués au niveau 2 incluent tous les paramètres de stratégie recommandés pour le niveau 1 et ajoutent ou mettent à jour les paramètres de stratégie ci-dessous pour implémenter plus de contrôles et une configuration plus sophistiquée que le niveau 1.|
|Entreprise|[Protection améliorée des données de niveau 2](/mem/intune/apps/app-protection-framework#level-2-enterprise-enhanced-data-protection)|Les paramètres de stratégie appliqués au niveau 2 incluent tous les paramètres de stratégie recommandés pour le niveau 1 et ajoutent ou mettent à jour les paramètres de stratégie ci-dessous pour implémenter plus de contrôles et une configuration plus sophistiquée que le niveau 1.|
|Sécurité spécialisée|[Protection élevée des données d’entreprise de niveau 3](/mem/intune/apps/app-protection-framework#level-3-enterprise-high-data-protection)|Les paramètres de stratégie appliqués au niveau 3 incluent tous les paramètres de stratégie recommandés pour les niveaux 1 et 2 et ajoutent ou mettent à jour uniquement les paramètres de stratégie ci-dessous pour implémenter plus de contrôles et une configuration plus sophistiquée que le niveau 2.|

Pour créer une stratégie de protection des applications pour chaque plateforme (iOS et Android) au sein de Microsoft Endpoint Manager à l’aide des paramètres de l’infrastructure de protection des données, vous pouvez :

1. Créez manuellement les stratégies en suivant les étapes décrites dans [Comment créer et déployer des stratégies de protection des applications avec Microsoft Intune](/mem/intune/apps/app-protection-policies).
2. Importez l’exemple [Intune modèles JSON de](https://github.com/microsoft/Intune-Config-Frameworks/tree/master/AppProtectionPolicies) l’infrastructure de configuration de stratégie de protection des applications avec les [scripts PowerShell de Intune](https://github.com/microsoftgraph/powershell-intune-samples).

## <a name="require-approved-apps-and-app-protection"></a>Exiger des applications approuvées et une protection d’application

Pour appliquer les stratégies Protection d'applications que vous avez appliquées dans Intune, vous devez créer une stratégie d’accès conditionnel pour exiger des applications clientes approuvées et les conditions définies dans les stratégies de protection des applications.

L’application de stratégies Protection d'applications nécessite un ensemble de stratégies décrites dans [Exiger une stratégie de protection des applications pour l’accès aux applications cloud avec l’accès conditionnel](/azure/active-directory/conditional-access/app-protection-based-conditional-access). Ces stratégies sont incluses dans cet ensemble recommandé de stratégies de configuration d’identité et d’accès.

Pour créer la stratégie d’accès conditionnel qui nécessite des applications approuvées et une protection d’application, suivez les étapes décrites dans [Exiger des applications clientes approuvées ou une stratégie de protection des applications avec des appareils mobiles](/azure/active-directory/conditional-access/howto-policy-approved-app-or-app-protection#require-approved-client-apps-or-app-protection-policy-with-mobile-devices), qui autorise uniquement les comptes au sein d’applications mobiles protégées par des stratégies Protection d'applications à accéder aux points de terminaison Microsoft 365.

   > [!NOTE]
   > Cette stratégie garantit que les utilisateurs mobiles peuvent accéder à tous les points de terminaison Microsoft 365 à l’aide des applications applicables.

Cette stratégie empêche également Exchange ActiveSync clients sur les appareils mobiles de se connecter à Exchange Online. Toutefois, vous pouvez créer une stratégie distincte pour gérer les Exchange ActiveSync sur tous les appareils. Pour plus d’informations, consultez [Bloquer les clients ActiveSync](secure-email-recommended-policies.md#block-activesync-clients), qui empêche Exchange ActiveSync clients tirant parti de l’authentification de base de se connecter à Exchange Online. Cette stratégie n’est pas illustrée dans l’illustration en haut de cet article. Il est décrit et illustré dans les recommandations de stratégie [pour la sécurisation des e-mails](secure-email-recommended-policies.md).

 Cette stratégie tire parti des contrôles d’octroi [exiger une application cliente approuvée](/azure/active-directory/conditional-access/concept-conditional-access-grant#require-approved-client-app) et [exiger une stratégie de protection des applications](/azure/active-directory/conditional-access/concept-conditional-access-grant#require-app-protection-policy).

Enfin, le blocage de l’authentification héritée pour d’autres applications clientes sur des appareils iOS et Android garantit que ces clients ne peuvent pas contourner les stratégies d’accès conditionnel. Si vous suivez les instructions de cet article, vous avez déjà configuré des [clients bloquer qui ne prennent pas en charge l’authentification moderne](#block-clients-that-dont-support-multi-factor).

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

Les stratégies de conformité des appareils définissent les exigences que les appareils doivent remplir pour être déterminées comme conformes. Vous créez Intune stratégies de conformité des appareils à partir du Centre d’administration Microsoft Endpoint Manager.

Vous devez créer une stratégie pour chaque plateforme PC, téléphone ou tablette :

- Administrateur d’appareils Android
- Android Entreprise
- iOS/iPadOS
- macOS
- Windows 8.1 et versions ultérieures
- Windows 10 et versions ultérieures

Pour créer des stratégies de conformité des appareils, connectez-vous au [Centre microsoft Endpoint Manager Administration](https://endpoint.microsoft.com) avec vos informations d’identification d’administrateur, puis accédez aux stratégies de **conformité** \> **des appareils** \> **.** Sélectionner **Créer une stratégie**.

Pour que les stratégies de conformité des appareils soient déployées, elles doivent être affectées à des groupes d’utilisateurs. Vous attribuez une stratégie après avoir créé et enregistré celle-ci. Dans le centre d’administration, sélectionnez la stratégie, puis sélectionnez **Affectations**. Après avoir sélectionné les groupes que vous souhaitez recevoir la stratégie, **sélectionnez Enregistrer** pour enregistrer cette affectation de groupe et déployer la stratégie.

Pour obtenir des instructions pas à pas sur la création de stratégies de conformité dans Intune, consultez [Créer une stratégie de conformité dans Microsoft Intune](/mem/intune/protect/create-compliance-policy) dans la documentation Intune.

### <a name="recommended-settings-for-ios"></a>Paramètres recommandés pour iOS

iOS/iPadOS prend en charge plusieurs scénarios d’inscription, dont deux sont couverts dans le cadre de cette infrastructure :

- [Inscription d’appareils pour les appareils personnels](/mem/intune/enrollment/ios-enroll) : ces appareils sont personnels et utilisés à des fins professionnelles et personnelles.
- [Inscription automatisée supervisée des appareils d’entreprise](/mem/intune/enrollment/device-enrollment-program-enroll-ios) : ces appareils appartiennent à l’entreprise, sont associés à un seul utilisateur et sont utilisés exclusivement à des fins professionnelles et non personnelles.

L’infrastructure de configuration de sécurité iOS/iPadOS est organisée en plusieurs scénarios de configuration distincts, fournissant des conseils pour les appareils personnels et supervisés.

Pour les appareils personnels :

- Sécurité de base (niveau 1) : Microsoft recommande cette configuration comme configuration de sécurité minimale pour les appareils personnels où les utilisateurs accèdent aux données professionnelles ou scolaires. Cela s’effectue en appliquant des stratégies de mot de passe, des caractéristiques de verrouillage d’appareil et en désactivant certaines fonctions d’appareil (par exemple, les certificats non approuvés).
- Sécurité renforcée (niveau 2) : Microsoft recommande cette configuration pour les appareils où les utilisateurs accèdent à des informations sensibles ou confidentielles. Cette configuration enrôle les contrôles de partage de données. Cette configuration s’applique à la plupart des utilisateurs mobiles accédant à des données professionnelles ou scolaires sur un appareil.
- Haute sécurité (niveau 3) : Microsoft recommande cette configuration pour les appareils utilisés par des utilisateurs ou des groupes spécifiques présentant un risque unique élevé (les utilisateurs qui gèrent des données hautement sensibles lorsque la divulgation non autorisée entraîne une perte matérielle considérable pour l’organisation). Cette configuration applique des stratégies de mot de passe plus fortes, désactive certaines fonctions d’appareil et applique des restrictions de transfert de données supplémentaires.

Pour les appareils supervisés :

- Sécurité de base (niveau 1) : Microsoft recommande cette configuration comme configuration de sécurité minimale pour les appareils supervisés où les utilisateurs accèdent aux données professionnelles ou scolaires. Cela s’effectue en appliquant des stratégies de mot de passe, des caractéristiques de verrouillage d’appareil et en désactivant certaines fonctions d’appareil (par exemple, les certificats non approuvés).
- Sécurité renforcée (niveau 2) : Microsoft recommande cette configuration pour les appareils où les utilisateurs accèdent à des informations sensibles ou confidentielles. Cette configuration permet d’effectuer des contrôles de partage de données et de bloquer l’accès aux périphériques USB. Cette configuration s’applique à la plupart des utilisateurs mobiles accédant à des données professionnelles ou scolaires sur un appareil.
- Haute sécurité (niveau 3) : Microsoft recommande cette configuration pour les appareils utilisés par des utilisateurs ou des groupes spécifiques présentant un risque unique élevé (les utilisateurs qui gèrent des données hautement sensibles lorsque la divulgation non autorisée entraîne une perte matérielle considérable pour l’organisation). Cette configuration applique des stratégies de mot de passe plus fortes, désactive certaines fonctions d’appareil, applique des restrictions de transfert de données supplémentaires et exige l’installation d’applications par le biais du programme d’achat en volume d’Apple.

À l’aide des principes [décrits dans Confiance nulle configurations d’identité et d’accès aux appareils](microsoft-365-policies-configurations.md), les niveaux de point de départ et de protection d’entreprise correspondent étroitement aux paramètres de sécurité améliorés de niveau 2. Le niveau de protection de sécurité spécialisé est étroitement lié aux paramètres de sécurité de niveau 3.

|Niveau de protection  |Stratégie d’appareil |Plus d’informations  |
|---------|---------|---------|
|Point de départ     |Sécurité renforcée (niveau 2)         |Les paramètres de stratégie appliqués au niveau 2 incluent tous les paramètres de stratégie recommandés pour le niveau 1 et ajoutent ou mettent à jour les paramètres de stratégie ci-dessous pour implémenter plus de contrôles et une configuration plus sophistiquée que le niveau 1.         |
|Entreprise     |Sécurité renforcée (niveau 2)         |Les paramètres de stratégie appliqués au niveau 2 incluent tous les paramètres de stratégie recommandés pour le niveau 1 et ajoutent ou mettent à jour les paramètres de stratégie ci-dessous pour implémenter plus de contrôles et une configuration plus sophistiquée que le niveau 1.         |
|Sécurité spécialisée     |Haute sécurité (Niveau 3)         |Les paramètres de stratégie appliqués au niveau 3 incluent tous les paramètres de stratégie recommandés pour les niveaux 1 et 2 et ajoutent ou mettent à jour uniquement les paramètres de stratégie ci-dessous pour implémenter plus de contrôles et une configuration plus sophistiquée que le niveau 2.         |

Pour afficher les recommandations spécifiques en matière de conformité des appareils et de restriction d’appareil pour chaque niveau de configuration, passez en revue l’infrastructure de configuration [de sécurité iOS/iPadOS](/mem/intune/enrollment/ios-ipados-configuration-framework).

### <a name="recommended-settings-for-android"></a>Paramètres recommandés pour Android

Android Enterprise prend en charge plusieurs scénarios d’inscription, dont deux sont couverts dans le cadre de ce framework :

- [Profil professionnel Android Entreprise](/intune/android-work-profile-enroll) : ce modèle d’inscription est généralement utilisé pour les appareils personnels, où le service informatique souhaite fournir une limite de séparation claire entre les données professionnelles et personnelles. Les stratégies contrôlées par le service informatique garantissent que les données de travail ne peuvent pas être transférées dans le profil personnel.
- [Appareils Android Enterprise entièrement gérés](/intune/android-fully-managed-enroll) : ces appareils appartiennent à l’entreprise, sont associés à un seul utilisateur et sont utilisés exclusivement à des fins professionnelles et non personnelles.

L’infrastructure de configuration de sécurité Android Enterprise est organisée en plusieurs scénarios de configuration distincts, fournissant des conseils pour le profil professionnel et les scénarios entièrement gérés.

Pour les appareils de profil professionnel Android Entreprise :

- Sécurité renforcée du profil professionnel (niveau 2) : Microsoft recommande cette configuration comme configuration de sécurité minimale pour les appareils personnels où les utilisateurs accèdent aux données professionnelles ou scolaires. Cette configuration introduit des exigences de mot de passe, sépare les données professionnelles et personnelles, et valide l’attestation des appareils Android.
- Sécurité élevée du profil professionnel (niveau 3) : Microsoft recommande cette configuration pour les appareils utilisés par des utilisateurs ou des groupes spécifiques présentant un risque unique élevé (les utilisateurs qui gèrent des données hautement sensibles lorsque la divulgation non autorisée entraîne une perte matérielle considérable pour l’organisation). Cette configuration introduit la protection contre les menaces mobiles ou Microsoft Defender pour point de terminaison, définit la version minimale d’Android, applique des stratégies de mot de passe plus fortes et restreint davantage la séparation professionnelle et personnelle.

Pour les appareils Android Entreprise entièrement gérés :

- Sécurité de base entièrement managée (niveau 1) : Microsoft recommande cette configuration comme configuration de sécurité minimale pour un appareil d’entreprise. Cette configuration s’applique à la plupart des utilisateurs mobiles qui accèdent aux données professionnelles ou scolaires. Cette configuration introduit les exigences de mot de passe, définit la version minimale d’Android et applique certaines restrictions d’appareil.
- Sécurité renforcée entièrement managée (niveau 2) : Microsoft recommande cette configuration pour les appareils où les utilisateurs accèdent à des informations sensibles ou confidentielles. Cette configuration applique des stratégies de mot de passe plus fortes et désactive les fonctionnalités utilisateur/compte.
- Haute sécurité complètement managée (niveau 3) : Microsoft recommande cette configuration pour les appareils utilisés par des utilisateurs ou des groupes spécifiques présentant un risque unique élevé (les utilisateurs qui gèrent des données hautement sensibles lorsque la divulgation non autorisée entraîne une perte matérielle considérable pour l’organisation). Cette configuration augmente la version minimale d’Android, introduit la défense contre les menaces mobiles ou Microsoft Defender pour point de terminaison, et applique des restrictions d’appareil supplémentaires.

À l’aide des principes [décrits dans Confiance nulle configurations d’identité et d’accès aux appareils](microsoft-365-policies-configurations.md), les niveaux de point de départ et de protection d’entreprise correspondent étroitement à la sécurité de base de niveau 1 pour les appareils personnels et aux paramètres de sécurité améliorés de niveau 2 pour les appareils entièrement gérés. Le niveau de protection de sécurité spécialisé est étroitement lié aux paramètres de sécurité de niveau 3.

Pour les appareils de profil professionnel Android Entreprise :

|Niveau de protection  |Stratégie d’appareil |Plus d’informations  |
|---------|---------|---------|
|Point de départ     |Profil professionnel : Sécurité de base (niveau 1)      |S/O         |
|Entreprise     |Profil professionnel : Sécurité de base (niveau 1)         |S/O         |
|Point de départ     |Complètement managé : sécurité renforcée (niveau 2)       |Les paramètres de stratégie appliqués au niveau 2 incluent tous les paramètres de stratégie recommandés pour le niveau 1 et ajoutent ou mettent à jour les paramètres de stratégie ci-dessous pour implémenter plus de contrôles et une configuration plus sophistiquée que le niveau 1.         |
|Entreprise     |Complètement managé : sécurité renforcée (niveau 2)         |Les paramètres de stratégie appliqués au niveau 2 incluent tous les paramètres de stratégie recommandés pour le niveau 1 et ajoutent ou mettent à jour les paramètres de stratégie ci-dessous pour implémenter plus de contrôles et une configuration plus sophistiquée que le niveau 1.         |
|Sécurité spécialisée     |Haute sécurité (Niveau 3)         |Les paramètres de stratégie appliqués au niveau 3 incluent tous les paramètres de stratégie recommandés pour les niveaux 1 et 2 et ajoutent ou mettent à jour uniquement les paramètres de stratégie ci-dessous pour implémenter plus de contrôles et une configuration plus sophistiquée que le niveau 2.         |

Pour afficher les recommandations spécifiques en matière de conformité des appareils et de restriction d’appareil pour chaque niveau de configuration, consultez [Android Enterprise Security Configuration Framework](/mem/intune/enrollment/android-configuration-framework).

### <a name="recommended-settings-for-windows-10-and-later"></a>Paramètres recommandés pour les Windows 10 et versions ultérieures

Les paramètres suivants sont recommandés pour les PC exécutant Windows 10 et versions ultérieures, comme configuré à **l’étape 2 : Paramètres de conformité**, du processus de création de stratégie.

Pour **connaître l’intégrité de l’appareil > règles d’évaluation du service d’attestation d’intégrité Windows**, consultez ce tableau.

|Propriétés|Valeur|Action|
|---|---|---|
|Exiger BitLocker|Require (Rendre obligatoire)|Sélectionner|
|Exiger l’activation du démarrage sécurisé sur l’appareil|Require (Rendre obligatoire)|Sélectionner|
|Exiger l’intégrité du code|Require (Rendre obligatoire)|Sélectionner|

Pour **les propriétés de l’appareil**, spécifiez les valeurs appropriées pour les versions du système d’exploitation en fonction de vos stratégies informatiques et de sécurité.

Pour **Configuration Manager Conformité**, **sélectionnez Exiger**.

Pour **la sécurité du système**, consultez ce tableau.

|Type|Propriétés|Valeur|Action|
|---|---|---|---|
|Password|Exiger un mot de passe pour déverrouiller des appareils mobiles|Require (Rendre obligatoire)|Sélectionner|
||Mots de passe simples|Bloquer|Sélectionner|
||Type de mot de passe|Valeur par défaut de l’appareil|Sélectionner|
||Longueur minimale du mot de passe|6|Type|
||Nombre maximal de minutes d’inactivité avant demande du mot de passe|15|Type <p> Ce paramètre est pris en charge pour les versions Android 4.0 et ultérieures ou KNOX 4.0 et versions ultérieures. Pour les appareils iOS, il est pris en charge pour iOS 8.0 et versions ultérieures.|
||Expiration du mot de passe (jours)|41|Type|
||Nombre de mots de passe précédents avant d’autoriser leur réutilisation|5|Type|
||Exiger un mot de passe lorsque l’appareil retourne un état inactif (Mobile et Holographique)|Require (Rendre obligatoire)|Disponible pour Windows 10 et versions ultérieures|
|Chiffrement|Chiffrement du stockage de données sur l’appareil|Require (Rendre obligatoire)|Sélectionner|
|Sécurité des appareils|Pare-feu|Require (Rendre obligatoire)|Sélectionner|
||Antivirus|Require (Rendre obligatoire)|Sélectionner|
||Logiciel anti-espion|Require (Rendre obligatoire)|Sélectionner <p> Ce paramètre nécessite une solution anti-logiciels espions inscrite auprès de l’application Sécurité Windows.|
|Defender pour le cloud|Logiciel anti-programme malveillant Microsoft Defender|Require (Rendre obligatoire)|Sélectionner|
||Version minimale du logiciel anti-programme malveillant Microsoft Defender||Type <p> Pris en charge uniquement pour Windows 10 bureau. Microsoft recommande des versions qui ne dépassent pas cinq versions par rapport à la version la plus récente.|
||Signature anti-programme malveillant Microsoft Defender à jour|Require (Rendre obligatoire)|Sélectionner|
||Protection en temps réel|Require (Rendre obligatoire)|Sélectionner <p> Uniquement pris en charge pour les Windows 10 et les versions ultérieures du bureau|

#### <a name="microsoft-defender-for-endpoint"></a>Microsoft Defender pour point de terminaison

|Type|Propriétés|Valeur|Action|
|---|---|---|---|
|Microsoft Defender pour point de terminaison règles dans le Centre d’administration Microsoft Endpoint Manager|[Exiger que l’appareil soit au niveau ou sous le score de risque de l’ordinateur](/mem/intune/protect/advanced-threat-protection-configure#create-and-assign-compliance-policy-to-set-device-risk-level)|Moyen|Sélectionner|

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
3. Dans la liste **Gérer** , choisissez **Sécurité**, puis choisissez **Accès conditionnel**.
4. Choisissez **Nouvelle stratégie** et tapez le nom de la nouvelle stratégie.

5. Sous **Affectations**, choisissez **Utilisateurs et groupes** et incluez les personnes auxquelles vous souhaitez appliquer la stratégie. Excluez également votre groupe d’exclusion d’accès conditionnel.

6. Sous **Affectations**, choisissez **Applications cloud ou actions**.

7. Pour **Inclure**, **choisissez Sélectionner les applications > Sélectionner**, puis sélectionnez les applications souhaitées dans la liste **des applications cloud** . Par exemple, sélectionnez Office 365. **Sélectionnez Sélectionner** lorsque vous avez terminé.

8. Sous **Contrôles d’accès**, choisissez **Accorder** .

9. Choisissez **Accorder l’accès** , puis **cochez Exiger que l’appareil soit marqué comme conforme**. Pour plusieurs contrôles, **sélectionnez Exiger tous les contrôles sélectionnés**. Une fois l’opération terminée, **choisissez Sélectionner**.

10. Sélectionnez **Activé** pour **activer la stratégie**, puis **choisissez Créer**.

> [!NOTE]
> Assurez-vous que votre appareil est conforme avant d’activer cette stratégie. Sinon, vous pourriez être verrouillé et ne pourrez pas modifier cette stratégie tant que votre compte d’utilisateur n’a pas été ajouté au groupe d’exclusion d’accès conditionnel.

## <a name="next-step"></a>Étape suivante

[![Étape 3 : Stratégies pour les utilisateurs invités et externes.](../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-3.png#lightbox)](identity-access-policies-guest-access.md)

[En savoir plus sur les recommandations de stratégie pour les utilisateurs invités et externes](identity-access-policies-guest-access.md)
