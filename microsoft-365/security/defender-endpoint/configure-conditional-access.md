---
title: Configurer l’accès conditionnel dans Microsoft Defender pour point de terminaison
description: Découvrez les étapes à suivre dans Intune, Microsoft 365 Defender et Azure pour implémenter l’accès conditionnel
keywords: accès conditionnel, conditionnel, accès, risque d’appareil, niveau de risque, intégration, intégration intune
ms.service: microsoft-365-security
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
ms.subservice: mde
ms.openlocfilehash: a565fc87c538fa6f9f590a4037ff9c346118c3cf
ms.sourcegitcommit: 437461fa1d38ff9bb95dd8a1c5f0b94e8111ada2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67680172"
---
# <a name="configure-conditional-access-in-microsoft-defender-for-endpoint"></a>Configurer l’accès conditionnel dans Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Cette section vous guide tout au long de toutes les étapes à suivre pour implémenter correctement l’accès conditionnel.

## <a name="before-you-begin"></a>Avant de commencer

> [!WARNING]
> Il est important de noter que les appareils inscrits à Azure AD ne sont pas pris en charge dans ce scénario.</br>
> Seuls Intune appareils inscrits sont pris en charge.

Vous devez vous assurer que tous vos appareils sont inscrits dans Intune. Vous pouvez utiliser l’une des options suivantes pour inscrire des appareils dans Intune :

- It Administration: For more information on how to enable auto-enrollment, see [Windows Enrollment](/intune/windows-enroll#enable-windows-10-automatic-enrollment)
- Utilisateur final : pour plus d’informations sur l’inscription de votre appareil Windows 10 et Windows 11 dans Intune, consultez [Inscrire votre appareil Windows 10 dans Intune](/intune/quickstart-enroll-windows-device)
- Alternative de l’utilisateur final : pour plus d’informations sur la jonction à un domaine Azure AD, consultez [Comment : planifier votre implémentation de jointure Azure AD](/azure/active-directory/devices/azureadjoin-plan).

Il existe des étapes à suivre dans Microsoft 365 Defender, le portail Intune et le portail Azure AD.

Il est important de noter les rôles requis pour accéder à ces portails et implémenter l’accès conditionnel :

- **Microsoft 365 Defender** : vous devez vous connecter au portail avec un rôle d’administrateur général pour activer l’intégration.
- **Intune** : vous devez vous connecter au portail avec des droits d’administrateur de sécurité avec des autorisations de gestion.
- **Portail Azure AD** : vous devez vous connecter en tant qu’administrateur général, administrateur de sécurité ou administrateur d’accès conditionnel.

> [!NOTE]
> Vous aurez besoin d’un environnement Microsoft Intune, avec des appareils Intune managés et joints à Azure AD Windows 10 et Windows 11.

Effectuez les étapes suivantes pour activer l’accès conditionnel :

- Étape 1 : Activer la connexion Microsoft Intune à partir de Microsoft 365 Defender
- Étape 2 : Activer l’intégration de Defender pour point de terminaison dans Intune
- Étape 3 : Créer la stratégie de conformité dans Intune
- Étape 4 : Affecter la stratégie 
- Étape 5 : Créer une stratégie d’accès conditionnel Azure AD

### <a name="step-1-turn-on-the-microsoft-intune-connection"></a>Étape 1 : Activer la connexion Microsoft Intune

1. Dans le volet de navigation, sélectionnez **Paramètres des** \> **points de terminaison Fonctionnalités avancées générales** \>  \>  \> **Microsoft Intune connexion**.
2. Basculez le paramètre Microsoft Intune **sur Activé**.
3. Cliquez sur **Enregistrer les préférences**.

### <a name="step-2-turn-on-the-defender-for-endpoint-integration-in-intune"></a>Étape 2 : Activer l’intégration de Defender pour point de terminaison dans Intune

1. Connectez-vous au [Portail Azure](https://portal.azure.com).
2. Sélectionnez Conformité \> **de l’appareil** **Microsoft Defender ATP**.
3. Définissez **Connect Windows 10.0.15063+ sur Microsoft Defender Advanced Threat Protection** **sur Activé**.
4. Cliquez sur **Enregistrer**.

### <a name="step-3-create-the-compliance-policy-in-intune"></a>Étape 3 : Créer la stratégie de conformité dans Intune

1. Dans le [Portail Azure](https://portal.azure.com), sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
2. Sélectionnez **Stratégie de** **création de stratégies de conformité** \>  \> des appareils.
3. Entrez un **nom** et une **description**.
4. Dans **Plateforme**, sélectionnez **Windows 10 et versions ultérieures**.
5. Dans les paramètres **d’intégrité** de **l’appareil, définissez Exiger que l’appareil soit au niveau de menace de l’appareil ou en dessous de celui-ci** à votre niveau préféré :

   - **Sécurisé** : ce niveau est le plus sûr. L’appareil ne peut pas avoir de menaces existantes et accède toujours aux ressources de l’entreprise. Si des menaces sont détectées, l’appareil est évalué comme non conforme.
   - **Faible** : l’appareil est conforme seulement si les menaces détectées sont de niveau faible. Les appareils présentant des niveaux de menaces moyens ou élevés ne sont pas conformes.
   - **Moyen** : l’appareil est conforme si les menaces détectées sont de niveau faible ou moyen. Si des menaces de niveau élevé sont détectées, l’appareil est considéré comme non conforme.
   - **Élevé** : ce niveau est le moins sécurisé et autorise tous les niveaux de menace. Ainsi, les appareils qui présentent des niveaux de menace élevés, moyens ou faibles sont considérés comme conformes.

6. Sélectionnez **OK**, puis **Créez** pour enregistrer vos modifications (et créez la stratégie).

### <a name="step-4-assign-the-policy"></a>Étape 4 : Affecter la stratégie

1. Dans le [Portail Azure](https://portal.azure.com), sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
2. Sélectionnez **Stratégies** de conformité \> **des appareils**> sélectionnez votre stratégie de conformité Microsoft Defender pour point de terminaison.
3. Sélectionnez **Devoirs**.
4. Incluez ou excluez vos groupes Azure AD pour leur affecter la stratégie.
5. Pour déployer la stratégie sur les groupes, **sélectionnez Enregistrer**. La conformité des appareils utilisateur ciblés par la stratégie est évaluée.

### <a name="step-5-create-an-azure-ad-conditional-access-policy"></a>Étape 5 : Créer une stratégie d’accès conditionnel Azure AD

1. Dans le [Portail Azure](https://portal.azure.com), ouvrez la **nouvelle** stratégie d’accès \> **conditionnel** **Azure Active Directory**\>.
2. Entrez un **nom** de stratégie, puis sélectionnez **Utilisateurs et groupes**. Utilisez les options Inclure et Exclure pour ajouter vos groupes à la stratégie, puis sélectionnez **Terminé**.
3. Sélectionnez **applications cloud** et choisissez les applications à protéger. Par exemple, choisissez **Sélectionner les applications**, puis sélectionnez **Office 365 SharePoint Online** et **Office 365 Exchange Online**. Sélectionnez **OK** pour enregistrer vos modifications.

4. Sélectionnez Les **applications clientes** **conditions** \> pour appliquer la stratégie aux applications et navigateurs. Par exemple, sélectionnez **Oui**, puis activez **Navigateur** et **Applications mobiles et clients de bureau**. Sélectionnez **OK** pour enregistrer vos modifications.

5. Sélectionnez **Accorder** pour appliquer l’accès conditionnel basé sur la conformité des appareils. Par exemple, sélectionnez **Accorder l’accès** \> **Exiger que l’appareil soit marqué comme conforme**. Choisissez **Sélectionner** pour enregistrer vos changements.

6. Sélectionnez **Activer la stratégie**, puis **Créer** pour enregistrer vos changements.

> [!NOTE]
> Vous pouvez utiliser l’application Microsoft Defender pour point de terminaison ainsi que la stratégie d’application cliente approuvée dans Intune pour définir des stratégies de conformité des appareils et d’accès conditionnel. Aucune exclusion n’est requise pour l’application Microsoft Defender pour point de terminaison lors de la configuration de l’accès conditionnel. Bien que Microsoft Defender pour point de terminaison sur Android & iOS (ID d’application - dd47d17a-3194-4d86-bfd5-c6ae6f5651e3) n’est pas une application approuvée, elle a l’autorisation de signaler la posture de sécurité des appareils. Cette autorisation active le flux pour les informations de conformité à l’accès conditionnel.
> Veuillez noter que cette modification sera disponible à compter du 30 septembre 2022.

Pour plus d’informations, consultez [Appliquer la conformité pour Microsoft Defender pour point de terminaison avec l’accès conditionnel dans Intune](/intune/advanced-threat-protection).

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-conditionalaccess-belowfoldlink)
