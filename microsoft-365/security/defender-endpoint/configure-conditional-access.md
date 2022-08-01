---
title: Configurer l’accès conditionnel dans Microsoft Defender pour le point de terminaison
description: Découvrez les étapes à suivre dans Intune, Microsoft 365 Defender et Azure pour implémenter l’accès conditionnel
keywords: accès conditionnel, conditionnel, accès, risque d’appareil, niveau de risque, intégration, intégration intune
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 0c0ae3d155024a6c0cb9efb541218689f8970a12
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2021
ms.locfileid: "61164585"
---
# <a name="configure-conditional-access-in-microsoft-defender-for-endpoint"></a>Configurer l’accès conditionnel dans Microsoft Defender pour le point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Cette section vous guide à travers toutes les étapes à suivre pour implémenter correctement l’accès conditionnel.

## <a name="before-you-begin"></a>Avant de commencer

> [!WARNING]
> Il est important de noter que les Azure AD enregistrés ne sont pas pris en charge dans ce scénario.</br>
> Seuls les appareils inscrits à Intune sont pris en charge.

Vous devez vous assurer que tous vos appareils sont inscrits dans Intune. Vous pouvez utiliser l’une des options suivantes pour inscrire des appareils dans Intune :

- Administrateur informatique : pour plus d’informations sur l’activation de l’inscription automatique, [voir Windows inscription](/intune/windows-enroll#enable-windows-10-automatic-enrollment)
- Utilisateur final : pour plus d’informations sur l’inscription de votre appareil Windows 10 dans Intune, voir Inscrire votre appareil Windows 10 [dans Intune](/intune/quickstart-enroll-windows-device)
- Alternative pour l’utilisateur final : pour plus d’informations sur la jointation d’un domaine Azure AD, voir Comment : planifier votre implémentation Azure AD [joint.](/azure/active-directory/devices/azureadjoin-plan)

Il existe des étapes que vous devrez suivre dans Microsoft 365 Defender, le portail Intune et Azure AD portail.

Il est important de noter les rôles requis pour accéder à ces portails et implémenter l’accès conditionnel :

- **Microsoft 365 Defender** : vous devez vous inscrire au portail avec un rôle d’administrateur général pour activer l’intégration.
- **Intune** : vous devez vous connectez au portail avec des droits d’administrateur de sécurité avec des autorisations de gestion.
- **Azure AD portail :** vous devez vous connectez en tant qu’administrateur général, administrateur de sécurité ou administrateur d’accès conditionnel.

> [!NOTE]
> Vous aurez besoin d’un environnement Microsoft Intune, avec Intune géré et Azure AD joints Windows 10 appareils.

Pour activer l’accès conditionnel, prenez les mesures suivantes :

- Étape 1 : Activer la connexion Microsoft Intune à partir de Microsoft 365 Defender
- Étape 2 : Activer l’intégration de Defender for Endpoint dans Intune
- Étape 3 : Créer la stratégie de conformité dans Intune
- Étape 4 : Attribuer la stratégie 
- Étape 5 : Créer une stratégie d Azure AD’accès conditionnel

### <a name="step-1-turn-on-the-microsoft-intune-connection"></a>Étape 1 : Activer la connexion Microsoft Intune connexion

1. Dans le volet de navigation, **sélectionnez** Paramètres points de terminaison \> **fonctionnalités générales** \>  \>  \> **avancées Microsoft Intune connexion.**
2. Toggle the Microsoft Intune setting to **On**.
3. Cliquez **sur Enregistrer les préférences.**

### <a name="step-2-turn-on-the-defender-for-endpoint-integration-in-intune"></a>Étape 2 : Activer l’intégration de Defender for Endpoint dans Intune

1. Connectez-vous au [Portail Azure](https://portal.azure.com).
2. Sélectionnez **La conformité de** \> **l’appareil Microsoft Defender ATP**.
3. Définissez **Connecter Windows 10.0.15063+** sur Microsoft Defender - Protection avancée contre les **menaces sur « On**».
4. Cliquez sur **Enregistrer**.

### <a name="step-3-create-the-compliance-policy-in-intune"></a>Étape 3 : Créer la stratégie de conformité dans Intune

1. Dans le [portail Azure,](https://portal.azure.com) **sélectionnez Tous les services,** filtrez **sur Intune** et sélectionnez **Microsoft Intune**.
2. Sélectionnez **Stratégies de conformité** \> **des appareils** Créer une \> **stratégie.**
3. Entrez un **nom et** une **description.**
4. Dans **Plateforme,** **sélectionnez Windows 10 et ultérieures.**
5. Dans les paramètres **d’état** de l’appareil, définissez Exiger que l’appareil soit à ou sous le niveau de menace de l’appareil **à** votre niveau préféré :

   - **Sécurisé** : ce niveau est le plus sûr. L’appareil ne peut pas avoir de menaces existantes et accéder aux ressources de l’entreprise. Si des menaces sont détectées, l’appareil est évalué comme non conforme.
   - **Faible**: l’appareil est conforme si seules les menaces de bas niveau existent. Les appareils avec des niveaux de menace moyennes ou élevées ne sont pas conformes.
   - **Moyen**: l’appareil est conforme si les menaces trouvées sur l’appareil sont faibles ou moyennes. Si des menaces de niveau élevé sont détectées, l’appareil est considéré comme non conforme.
   - **Élevé**: ce niveau est le moins sécurisé et autorise tous les niveaux de menace. Ainsi, les appareils dont les niveaux de menace sont élevés, moyens ou faibles sont considérés comme conformes.

6. Sélectionnez **OK,** **puis créez pour** enregistrer vos modifications (et créez la stratégie).

### <a name="step-4-assign-the-policy"></a>Étape 4 : Attribuer la stratégie

1. Dans le [portail Azure,](https://portal.azure.com) **sélectionnez Tous les services,** filtrez **sur Intune** et sélectionnez **Microsoft Intune**.
2. Sélectionnez  \> **stratégies de** conformité des> sélectionnez votre stratégie de conformité Microsoft Defender pour les points de terminaison.
3. Sélectionnez **Devoirs**.
4. Incluez ou excluez vos Azure AD pour leur attribuer la stratégie.
5. Pour déployer la stratégie sur les groupes, sélectionnez **Enregistrer.** Les appareils utilisateur ciblés par la stratégie sont évalués pour la conformité.

### <a name="step-5-create-an-azure-ad-conditional-access-policy"></a>Étape 5 : Créer une stratégie d Azure AD’accès conditionnel

1. Dans le [portail Azure,](https://portal.azure.com)ouvrez **Azure Active Directory** nouvelle stratégie \> **d’accès** \> **conditionnel.**
2. Entrez un nom **de stratégie,** puis sélectionnez **Utilisateurs et groupes.** Utilisez les options Inclure et Exclure pour ajouter vos groupes à la stratégie, puis sélectionnez **Terminé**.
3. Sélectionnez **les applications cloud** et choisissez les applications à protéger. Par exemple, **sélectionnez Sélectionner des applications,** puis **sélectionnez Office 365 SharePoint Online** et **Office 365 Exchange Online**. Sélectionnez **OK** pour enregistrer vos modifications.

4. Sélectionnez **Conditions** \> **Applications clientes** pour appliquer la stratégie aux applications et aux navigateurs. Par exemple, sélectionnez **Oui**, puis activez **Navigateur** et **Applications mobiles et clients de bureau**. Sélectionnez **OK** pour enregistrer vos modifications.

5. Sélectionnez **Accorder pour** appliquer l’accès conditionnel en fonction de la conformité des appareils. Par exemple, **sélectionnez Accorder l’accès** \> **Exiger que l’appareil soit marqué comme conforme.** Choisissez **Sélectionner** pour enregistrer vos changements.

6. Sélectionnez **Activer la** stratégie, puis **Créez pour** enregistrer vos modifications.

Pour plus d’informations, consultez [Appliquer la conformité pour Microsoft Defender pour point de terminaison avec l’accès conditionnel dans Intune](/intune/advanced-threat-protection).

> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-conditionalaccess-belowfoldlink)
