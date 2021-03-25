---
title: Configurer l’accès conditionnel dans Microsoft Defender ATP
description: Découvrez les étapes à suivre dans Intune, le Centre de sécurité Microsoft Defender et Azure pour implémenter l’accès conditionnel
keywords: accès conditionnel, conditionnel, accès, risque d’appareil, niveau de risque, intégration, intégration intune
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 0185d7875ac149909ef088d041383a1cf36a8a3a
ms.sourcegitcommit: 2a708650b7e30a53d10a2fe3164c6ed5ea37d868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2021
ms.locfileid: "51165860"
---
# <a name="configure-conditional-access-in-microsoft-defender-for-endpoint"></a>Configurer l’accès conditionnel dans Microsoft Defender pour le point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-assignaccess-abovefoldlink)

Cette section vous guide à travers toutes les étapes à suivre pour implémenter correctement l’accès conditionnel.

### <a name="before-you-begin"></a>Avant de commencer
>[!WARNING]
>Il est important de noter que les appareils enregistrés dans Azure AD ne sont pas pris en charge dans ce scénario.</br>
>Seuls les appareils inscrits à Intune sont pris en charge.


Vous devez vous assurer que tous vos appareils sont inscrits dans Intune. Vous pouvez utiliser l’une des options suivantes pour inscrire des appareils dans Intune :


- Administrateur informatique : pour plus d’informations sur l’activation de l’inscription automatique, voir [Inscription Windows](https://docs.microsoft.com/intune/windows-enroll#enable-windows-10-automatic-enrollment)
- Utilisateur final : pour plus d’informations sur l’inscription de votre appareil Windows 10 dans Intune, voir Inscrire votre appareil [Windows 10 dans Intune](https://docs.microsoft.com/intune/quickstart-enroll-windows-device)
- Alternative pour l’utilisateur final : pour plus d’informations sur la jointation d’un domaine Azure AD, voir Comment : planifier votre implémentation de jointage [Azure AD.](https://docs.microsoft.com/azure/active-directory/devices/azureadjoin-plan)



Vous devez suivre les étapes à suivre dans le Centre de sécurité Microsoft Defender, le portail Intune et le portail Azure AD.

Il est important de noter les rôles requis pour accéder à ces portails et implémenter l’accès conditionnel :
- **Centre de sécurité Microsoft Defender** : vous devez vous inscrire au portail avec un rôle d’administrateur général pour activer l’intégration.
- **Intune** : vous devez vous connectez au portail avec des droits d’administrateur de sécurité avec des autorisations de gestion. 
- **Portail Azure AD** : vous devez vous inscrire en tant qu’administrateur général, administrateur de sécurité ou administrateur d’accès conditionnel.


> [!NOTE]
> Vous aurez besoin d’un environnement Microsoft Intune, avec des appareils Windows 10 gérés par Intune et joints à Azure AD.

Pour activer l’accès conditionnel, prenez les mesures suivantes :
- Étape 1 : Activer la connexion Microsoft Intune à partir du Centre de sécurité Microsoft Defender
- Étape 2 : Activer l’intégration de Defender for Endpoint dans Intune
- Étape 3 : Créer la stratégie de conformité dans Intune
- Étape 4 : Attribuer la stratégie 
- Étape 5 : Créer une stratégie d’accès conditionnel Azure AD


### <a name="step-1-turn-on-the-microsoft-intune-connection"></a>Étape 1 : Activer la connexion Microsoft Intune
1. Dans le volet de navigation, sélectionnez **Paramètres**  >  **avancés fonctionnalités**  >  **Microsoft Intune connexion**.
2. Basculez le paramètre Microsoft Intune sur **Sur**.
3. Cliquez **sur Enregistrer les préférences.**


### <a name="step-2-turn-on-the-defender-for-endpoint-integration-in-intune"></a>Étape 2 : Activer l’intégration de Defender for Endpoint dans Intune
1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Sélectionnez **La conformité de**  >  **l’appareil Microsoft Defender ATP**.
3. Définissez **Connecter des appareils Windows 10.0.15063+** à Microsoft Defender - Protection avancée contre les **menaces sur Le .**
4. Cliquez sur **Enregistrer**.


### <a name="step-3-create-the-compliance-policy-in-intune"></a>Étape 3 : Créer la stratégie de conformité dans Intune
1. Dans le [portail Azure,](https://portal.azure.com) **sélectionnez Tous les services,** filtrez **sur Intune** et **sélectionnez Microsoft Intune.**
2. Sélectionnez **Stratégies de conformité**  >  **des appareils** Créer une  >  **stratégie.**
3. Entrez un **nom et** une **description.**
4. Dans **Plateforme,** **sélectionnez Windows 10 et les ultérieures.**
5. Dans les paramètres **d’état** de l’appareil, définissez Exiger que l’appareil soit à ou sous le niveau de menace de l’appareil **à** votre niveau préféré :

   - **Sécurisé :** ce niveau est le plus sécurisé. L’appareil ne peut pas avoir de menaces existantes et accéder aux ressources de l’entreprise. Si des menaces sont trouvées, l’appareil est évalué comme non conforme.
   - **Faible**: l’appareil est conforme si seules les menaces de bas niveau existent. Les appareils avec des niveaux de menace moyennes ou élevées ne sont pas conformes.
   - **Moyen**: l’appareil est conforme si les menaces trouvées sur l’appareil sont faibles ou moyennes. Si des menaces de haut niveau sont détectées, l’appareil est déterminé comme non conforme.
   - **Élevé**: ce niveau est le moins sécurisé et autorise tous les niveaux de menace. Ainsi, les appareils dont les niveaux de menace sont élevés, moyens ou faibles sont considérés comme conformes.

6. Sélectionnez **OK,** **puis créez pour** enregistrer vos modifications (et créez la stratégie).

### <a name="step-4-assign-the-policy"></a>Étape 4 : Attribuer la stratégie
1. Dans le [portail Azure,](https://portal.azure.com) **sélectionnez Tous les services,** filtrez **sur Intune** et **sélectionnez Microsoft Intune.**
2. Sélectionnez   >  **stratégies de** conformité des> sélectionnez votre stratégie de conformité Microsoft Defender ATP.
3. Sélectionnez **Devoirs**.
4. Incluez ou excluez vos groupes Azure AD pour leur attribuer la stratégie.
5. Pour déployer la stratégie sur les groupes, sélectionnez **Enregistrer.** Les appareils utilisateur ciblés par la stratégie sont évalués pour la conformité.

### <a name="step-5-create-an-azure-ad-conditional-access-policy"></a>Étape 5 : Créer une stratégie d’accès conditionnel Azure AD
1. Dans le [portail Azure,](https://portal.azure.com)ouvrez la nouvelle stratégie d’accès conditionnel **Azure Active**  >    >  **Directory.**
2. Entrez un nom **de stratégie,** puis sélectionnez **Utilisateurs et groupes.** Utilisez les options Inclure ou Exclure pour ajouter vos groupes pour la stratégie, puis sélectionnez **Terminé.**
3. Sélectionnez **les applications cloud** et choisissez les applications à protéger. Par exemple, **sélectionnez Sélectionner des applications,** puis **Sélectionnez Office 365 SharePoint Online** et **Office 365 Exchange Online.** Sélectionnez **OK** pour enregistrer vos modifications.

4. Sélectionnez **Conditions**  >  **Applications clientes** pour appliquer la stratégie aux applications et aux navigateurs. Par exemple, sélectionnez **Oui,** puis **activez** les applications mobiles **et de navigateur, ainsi que les clients de bureau.** Sélectionnez **OK** pour enregistrer vos modifications.

5. Sélectionnez **Accorder pour** appliquer l’accès conditionnel en fonction de la conformité des appareils. Par exemple, **sélectionnez Accorder l’accès**  >  **Exiger que l’appareil soit marqué comme conforme.** Sélectionnez **Sélectionner** pour enregistrer vos modifications.

6. Sélectionnez **Activer la** stratégie, puis **Créez pour** enregistrer vos modifications.

Pour plus d’informations, voir [Activer Microsoft Defender ATP avec accès conditionnel dans Intune.](https://docs.microsoft.com/intune/advanced-threat-protection)

>Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-conditionalaccess-belowfoldlink)
