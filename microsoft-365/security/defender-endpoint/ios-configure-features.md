---
title: configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS
description: Décrit comment déployer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, ios, configurer, fonctionnalités, ios
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier3
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 2b0046df2cd01ada1ce2816520c9878858a133f7
ms.sourcegitcommit: a20d30f4e5027f90d8ea4cde95d1d5bacfdd2b5e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2022
ms.locfileid: "68768238"
---
# <a name="configure-microsoft-defender-for-endpoint-on-ios-features"></a>configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> [!NOTE]
> Defender pour point de terminaison sur iOS utilise un VPN afin de fournir la fonctionnalité Web Protection. Il ne s’agit pas d’un VPN standard et d’un VPN local/auto-bouclage qui ne prend pas le trafic en dehors de l’appareil.

## <a name="conditional-access-with-defender-for-endpoint-on-ios"></a>Accès conditionnel avec Defender pour point de terminaison sur iOS

Microsoft Defender pour point de terminaison sur iOS avec Microsoft Intune et Azure Active Directory permet d’appliquer des stratégies de conformité des appareils et d’accès conditionnel en fonction du score de risque de l’appareil. Defender pour point de terminaison est une solution de défense contre les menaces mobiles (MTD) que vous pouvez déployer pour tirer parti de cette fonctionnalité via Intune.

Pour plus d’informations sur la configuration de l’accès conditionnel avec Defender pour point de terminaison sur iOS, consultez [Defender pour point de terminaison et Intune](/mem/intune/protect/advanced-threat-protection).

### <a name="jailbreak-detection-by-microsoft-defender-for-endpoint"></a>Détection de jailbreak par Microsoft Defender pour point de terminaison

Microsoft Defender pour point de terminaison a la capacité de détecter les appareils non gérés et gérés qui sont jailbreakés. Si un appareil est détecté comme étant jailbreaké **, une alerte** à haut risque est signalée au portail Microsoft 365 Defender et si l’accès conditionnel est configuré en fonction du score de risque de l’appareil, l’accès aux données d’entreprise est bloqué.

## <a name="web-protection-and-vpn"></a>Protection web et VPN

Par défaut, Defender pour point de terminaison sur iOS inclut et active la fonctionnalité de protection web. La [protection web](web-protection-overview.md) permet de sécuriser les appareils contre les menaces web et de protéger les utilisateurs contre les attaques par hameçonnage. Notez que les indicateurs anti-hameçonnage et personnalisés (URL et adresses IP) sont pris en charge dans le cadre de la protection web. Le filtrage de contenu web n’est actuellement pas pris en charge sur les plateformes mobiles.

Defender pour point de terminaison sur iOS utilise un VPN pour fournir cette fonctionnalité. Notez qu’il s’agit d’un VPN local et, contrairement au VPN traditionnel, le trafic réseau n’est pas envoyé en dehors de l’appareil.

Bien qu’activé par défaut, il peut arriver que vous deviez désactiver le VPN dans certains cas. Par exemple, vous souhaitez exécuter certaines applications qui ne fonctionnent pas lorsqu’un VPN est configuré. Dans ce cas, vous pouvez choisir de désactiver le VPN à partir de l’application sur l’appareil en suivant les étapes ci-dessous :

1. Sur votre appareil iOS, ouvrez l’application **Paramètres** , cliquez ou appuyez sur **Général** , puis **VPN**.

2. Cliquez ou appuyez sur le bouton « i » pour Microsoft Defender pour point de terminaison.

3. Désactivez **la connexion à la demande** pour désactiver le VPN. 

   :::image type="content" source="images/ios-vpn-config.png" alt-text="Bouton bascule pour l’option connexion à la demande de configuration VPN" lightbox="images/ios-vpn-config.png":::

> [!NOTE]
> La protection web n’est pas disponible lorsque le VPN est désactivé. Pour réactiver la protection web, ouvrez l’application Microsoft Defender pour point de terminaison sur l’appareil, puis cliquez ou appuyez sur **Démarrer le VPN**.

## <a name="disable-web-protection"></a>Désactiver la protection web

La protection web est l’une des principales fonctionnalités de Defender pour point de terminaison et nécessite un VPN pour fournir cette fonctionnalité. Le VPN utilisé est un VPN local/de bouclage et non un VPN traditionnel, mais il existe plusieurs raisons pour lesquelles les clients peuvent ne pas préférer le VPN. Pour les clients qui ne souhaitent pas configurer de VPN, il existe une option permettant de désactiver **la protection web** et de déployer Defender pour point de terminaison sans cette fonctionnalité. Les autres fonctionnalités de Defender pour point de terminaison continueront de fonctionner.

Cette configuration est disponible pour les appareils inscrits (MDM) ainsi que pour les appareils non inscrits (GAM). Pour les clients disposant de mdm, les administrateurs peuvent configurer la **protection web** via des appareils gérés dans la configuration de l’application. Pour les clients sans inscription, à l’aide de gam, les administrateurs peuvent configurer la **protection web** via des applications managées dans la configuration de l’application.

### <a name="configure-web-protection"></a>Configurer la protection web

1. **Désactiver la protection web (MDM)** Procédez comme suit pour désactiver **la protection web** pour les appareils inscrits.

    - Dans le [Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), accédez à **Applications Stratégies** >  de **configuration** >  des applications **Ajouter des** > **appareils gérés**.
    - Donnez un nom à la stratégie, **Plateforme > iOS/iPadOS**.
    - Sélectionnez Microsoft Defender pour point de terminaison comme application cible.
    - Dans la page Paramètres, sélectionnez Utiliser le concepteur de configuration et ajoutez **WebProtection** comme clé et type de valeur en tant que **Chaîne**.
        - Par défaut, **WebProtection= true**.
        - Administration devez définir **WebProtection = false** pour désactiver la protection web.
        - Defender envoie la pulsation au portail Microsoft 365 Defender chaque fois que l’utilisateur ouvre l’application.
        - Cliquez sur Suivant et affectez ce profil aux appareils/utilisateurs ciblés.

1. **Désactiver la protection web (MAM)** Procédez comme suit pour désactiver **la protection web** pour les appareils non inscrits.

    - Dans le [Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), accédez à **Applications Stratégies** >  de **configuration** >  des applications **Ajouter des** > **applications gérées**.
    - Donner à la stratégie un nom.
    - Sous Sélectionner des applications publiques, choisissez Microsoft Defender pour point de terminaison comme application cible.
    - Dans la page Paramètres, sous Paramètres de configuration généraux, ajoutez **WebProtection** comme clé et la valeur **false**.
        - Par défaut, **WebProtection= true**.
        - Administration devez définir **WebProtection = false** pour désactiver la protection web.
        - Defender envoie la pulsation au portail Microsoft 365 Defender chaque fois que l’utilisateur ouvre l’application.
        - Cliquez sur Suivant et affectez ce profil aux appareils/utilisateurs ciblés.

## <a name="configure-network-protection"></a>Configurer la protection réseau


La protection réseau dans Microsoft Defender pour point de terminaison est désactivée par défaut. Les administrateurs peuvent utiliser les étapes suivantes pour configurer la prise en charge de la gestion des applications mobiles pour la protection réseau sur les appareils iOS. (L’inscription de l’appareil d’authentification authentificateur est requise pour la configuration GAM) sur les appareils iOS. L’initialisation de la protection réseau nécessite que l’utilisateur final ouvre l’application une seule fois. 

1. Dans Microsoft Endpoint Manager Administration, accédez à Applications > Stratégies de configuration des applications. Créez une stratégie de configuration d’application.
   :::image type="content" source="images/addiosconfig.png" alt-text="Ajouter une stratégie de configuration." lightbox="images/addiosconfig.png":::

2. Fournissez un nom et une description pour identifier la stratégie de manière unique. Cliquez ensuite sur « Sélectionner les applications publiques », puis choisissez « Microsoft Defender » pour Plateforme iOS/IPadOS :::image type="content" source="images/nameiosconfig.png" alt-text="Nom de la configuration." lightbox="images/nameiosconfig.png":::

3. Dans la page Paramètres, ajoutez « DefenderNetworkProtectionEnable » comme clé et la valeur « true » pour désactiver la protection réseau. (La protection réseau est désactivée par défaut) :::image type="content" source="images/addiosconfigvalue.png" alt-text="Ajoutez une valeur de configuration." lightbox="images/addiosconfigvalue.png":::

4. Pour les autres configurations liées à la protection du réseau, ajoutez les clés suivantes et la valeur correspondante appropriée.

    |Clé| Par défaut (true-enable, false-disable)|Description|
    |---|---|---|
    |DefenderOpenNetworkDetection|0|1- Activer, 0 - Désactiver ; Ce paramètre est géré par les Administration informatiques pour activer ou désactiver les alertes d’information de détection réseau ouvertes sans expérience de détection de l’utilisateur final|
    |DefenderEndUserTrustFlowEnable| false | Autoriser les utilisateurs à approuver des réseaux et des certificats|
    |DefenderNetworkProtectionAutoRemediation| true |Ce paramètre est utilisé par l’administrateur informatique pour activer ou désactiver les alertes de correction qui sont envoyées lorsqu’un utilisateur effectue des activités de correction telles que le basculement vers des points d’accès WIFI plus sûrs ou la suppression de certificats suspects détectés par Defender|
    |DefenderNetworkProtectionPrivacy| true |Ce paramètre est géré par l’administrateur informatique pour activer ou désactiver la confidentialité dans la protection réseau|
  
5. Dans la section Affectations, l’administrateur peut choisir des groupes d’utilisateurs à inclure et à exclure de la stratégie.
   :::image type="content" source="images/assigniosconfig.png" alt-text="Attribuer une configuration." lightbox="images/assigniosconfig.png":::

6. Passez en revue et créez la stratégie de configuration.

## <a name="co-existence-of-multiple-vpn-profiles"></a>Coexistence de plusieurs profils VPN

Apple iOS ne prend pas en charge plusieurs VPN à l’échelle de l’appareil pour être actifs simultanément. Bien que plusieurs profils VPN puissent exister sur l’appareil, un seul VPN peut être actif à la fois.

## <a name="configure-microsoft-defender-for-endpoint-risk-signal-in-app-protection-policy-mam"></a>Configurer Microsoft Defender pour point de terminaison signal de risque dans la stratégie de protection des applications (GAM)

Microsoft Defender pour point de terminaison pouvez être configuré pour envoyer des signaux de menace à utiliser dans les stratégies de protection des applications (APP, également appelée MAM) sur iOS/iPadOS. Avec cette fonctionnalité, vous pouvez également utiliser Microsoft Defender pour point de terminaison pour protéger l’accès aux données d’entreprise à partir d’appareils non inscrits.

Les étapes de configuration des stratégies de protection des applications avec Microsoft Defender pour point de terminaison sont les suivantes :

1. Configurez la connexion à partir de votre locataire Microsoft Endpoint Manager pour Microsoft Defender pour point de terminaison. Dans le [Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), accédez à **Connecteurs d’administration** \> de **locataire** et jetons \> **Microsoft Defender pour point de terminaison** (sous Multiplateforme) ou **Sécurité** \> **des points de terminaison Microsoft Defender pour point de terminaison** (sous Programme d’installation) et activez les bascules sous **Paramètres de stratégie de protection des applications pour iOS**.

2. Sélectionnez Enregistrer. **L’état de la connexion** doit maintenant être défini sur **Activé**.

3. Créer une stratégie de protection des applications : une fois la configuration de votre connecteur Microsoft Defender pour point de terminaison terminée, accédez à **Applications** \> **Protection d'applications stratégies** (sous Stratégie) pour créer une stratégie ou mettre à jour une stratégie existante.

4. Sélectionnez les paramètres de plateforme, **Applications, Protection des données, Conditions d’accès** dont votre organisation a besoin pour votre stratégie.

5. Sous **Lancement** \> conditionnel **Conditions de l’appareil**, vous trouverez le paramètre **Niveau de menace maximal autorisé de l’appareil**. Ce paramètre doit être configuré sur Faible, Moyen, Élevé ou Sécurisé. Les actions disponibles sont **Bloquer l’accès** ou **Réinitialiser les données**. Une boîte de dialogue d’information peut s’afficher pour vous assurer que votre connecteur est configuré avant que ce paramètre ne prenne effet. Si votre connecteur est déjà configuré, vous pouvez ignorer cette boîte de dialogue.

6. Terminez avec Affectations et enregistrez votre stratégie.

Pour plus d’informations sur la gestion des applications mobiles ou la stratégie de protection des applications, consultez [Paramètres de stratégie de protection des applications iOS](/mem/intune/apps/app-protection-policy-settings-ios).

### <a name="deploying-microsoft-defender-for-endpoint-for-mam-or-on-unenrolled-devices"></a>Déploiement de Microsoft Defender pour point de terminaison pour gam ou sur des appareils non inscrits

Microsoft Defender pour point de terminaison sur iOS active le scénario de stratégie de protection des applications et est disponible dans l’App Store d’Apple. Les utilisateurs finaux doivent installer la dernière version de l’application directement à partir de l’App Store d’Apple.

## <a name="privacy-controls"></a>Contrôles de confidentialité

Microsoft Defender pour point de terminaison sur iOS active les contrôles de confidentialité pour les administrateurs et les utilisateurs finaux. Cela inclut les contrôles pour les appareils inscrits (GPM) et non inscrits (GAM).
Pour les clients avec mdm, les administrateurs peuvent configurer les contrôles de confidentialité via des appareils gérés dans la configuration de l’application. Pour les clients sans inscription, à l’aide de GAM, les administrateurs peuvent configurer les contrôles de confidentialité via des applications gérées dans la configuration de l’application. Les utilisateurs finaux auront également la possibilité de configurer les paramètres de confidentialité à partir des paramètres de l’application Defender.

### <a name="configure-privacy-in-phish-alert-report"></a>Configurer la confidentialité dans le rapport d’alerte d’hameçonnage

Les clients peuvent désormais activer le contrôle de confidentialité pour le rapport d’hameçonnage envoyé par Microsoft Defender pour point de terminaison sur iOS. Cela permet de s’assurer que le nom de domaine n’est pas envoyé dans le cadre de l’alerte de hameçonnage chaque fois qu’un site web de hameçonnage est détecté et bloqué par Microsoft Defender pour point de terminaison.

1. **Administration contrôles de confidentialité (GPM)** Suivez les étapes ci-dessous pour activer la confidentialité et ne pas collecter le nom de domaine dans le cadre du rapport d’alerte de hameçonnage pour les appareils inscrits.

    - Dans le [Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), accédez à **Applications Stratégies** >  de **configuration** >  des applications **Ajouter des** > **appareils gérés**.

    - Donnez un nom à la stratégie, **Plateforme > iOS/iPadOS**, sélectionnez le type de profil.

    - Sélectionnez **Microsoft Defender pour point de terminaison** comme application cible.

    - Dans la page Paramètres, sélectionnez **Utiliser le concepteur de configuration** et ajoutez **DefenderExcludeURLInReport** comme clé et type de valeur **booléen**.

      - Pour activer la confidentialité et ne pas collecter le nom de domaine, entrez la valeur et `true` affectez cette stratégie aux utilisateurs. Par défaut, cette valeur est définie sur `false`.

      - Pour les utilisateurs dont la clé est définie sur `true`, l’alerte d’hameçonnage ne contient pas les informations de nom de domaine chaque fois qu’un site malveillant est détecté et bloqué par Defender pour point de terminaison.

    - Cliquez sur **Suivant** et affectez ce profil aux appareils/utilisateurs ciblés.

1. **Administration contrôles de confidentialité (GAM)** Suivez les étapes ci-dessous pour activer la confidentialité et ne pas collecter le nom de domaine dans le cadre du rapport d’alerte de hameçonnage pour les appareils non inscrits.

    - Dans le [Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), accédez à **Applications Stratégies** >  de **configuration** >  des applications **Ajouter des** > **applications gérées**.

    - Donner à la stratégie un nom.

    - Sous Sélectionner des applications publiques, choisissez **Microsoft Defender pour point de terminaison** comme application cible.

    - Dans la page Paramètres, sous  **Paramètres de configuration généraux** , ajoutez **DefenderExcludeURLInReport** comme clé et valeur **true**.

      - Pour activer la confidentialité et ne pas collecter le nom de domaine, entrez la valeur et `true` affectez cette stratégie aux utilisateurs. Par défaut, cette valeur est définie sur `false`.

      - Pour les utilisateurs dont la clé est définie sur `true`, l’alerte d’hameçonnage ne contient pas les informations de nom de domaine chaque fois qu’un site malveillant est détecté et bloqué par Defender pour point de terminaison.

    - Cliquez sur **Suivant** et affectez ce profil aux appareils/utilisateurs ciblés.

1. **Contrôles de confidentialité des utilisateurs finaux** Ces contrôles aident l’utilisateur final à configurer les informations partagées avec son organisation.
    - Pour les appareils supervisés, les contrôles utilisateur final ne sont pas visibles. Administration décidera et contrôlera les paramètres.
    - Toutefois, pour les appareils non supervisés, le contrôle s’affiche sous **Paramètres > Confidentialité**
        - Les utilisateurs voient un bouton bascule pour **Les informations sur les sites non sécurisés**.
        - Ce bouton bascule n’est visible que si Administration a défini **DefenderExcludeURLInReport = true**
        - S’il est activé par Administration, les utilisateurs peuvent décider s’ils souhaitent envoyer les informations de site non sécurisées à leur organisation ou non.
        - Par défaut, sa valeur `true`est , les informations de site non sécurisées sont envoyées.
        - Si l’utilisateur bascule vers `false`, les détails du site non sécurisé ne sont pas envoyés.

L’activation ou la désactivation des contrôles de confidentialité ci-dessus n’aura pas d’impact sur la vérification de conformité de l’appareil ou l’accès conditionnel.

## <a name="optional-permissions"></a>Autorisations facultatives

Microsoft Defender pour point de terminaison sur iOS active les **autorisations facultatives** dans le flux d’intégration. Actuellement, les autorisations requises par Defender pour point de terminaison sont obligatoires dans le flux d’intégration. Avec cette fonctionnalité, les administrateurs peuvent déployer Defender pour point de terminaison sur des appareils BYOD sans appliquer **l’autorisation VPN** obligatoire lors de l’intégration. Les utilisateurs finaux peuvent intégrer l’application sans les autorisations obligatoires et peuvent passer en revue ces autorisations ultérieurement. Cette fonctionnalité est actuellement présente uniquement pour les appareils inscrits (GPM).

### <a name="configure-optional-permission"></a>Configurer l’autorisation facultative

1. **Administration flux (GPM)** Suivez les étapes ci-dessous pour activer l’autorisation **VPN facultative** pour les appareils inscrits.

    - Dans le [Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), accédez à **Applications Stratégies** >  de **configuration** >  des applications **Ajouter des** > **appareils gérés**.

    - Donnez un nom à la stratégie, sélectionnez **Plateforme > iOS/iPadOS**.

    - Sélectionnez **Microsoft Defender pour point de terminaison** comme application cible.

    - Dans la page Paramètres, sélectionnez **Utiliser le concepteur de configuration** et ajoutez **DefenderOptionalVPN** comme clé et type de valeur **booléen**.

      - Pour activer l’autorisation VPN facultative, entrez la valeur et `true` affectez cette stratégie aux utilisateurs. Par défaut, cette valeur est définie sur `false`.
      - Pour les utilisateurs dont la clé est définie sur `true`, les utilisateurs pourront intégrer l’application sans accorder l’autorisation VPN.

    - Cliquez sur **Suivant** et affectez ce profil aux appareils/utilisateurs ciblés.
1. **Flux de l’utilisateur final** : l’utilisateur installe et ouvre l’application pour démarrer l’intégration.
    - Si l’administrateur dispose d’autorisations facultatives, l’utilisateur peut **ignorer** l’autorisation VPN et terminer l’intégration.
    - Même si l’utilisateur a ignoré le VPN, l’appareil sera en mesure de l’intégrer et des pulsations seront envoyées.
    - Étant donné que `VPN` est désactivé, `Web Protection` ne sera pas actif.
    - Plus tard, l’utilisateur peut activer à `Web Protection` partir de l’application. Cette opération installe la configuration VPN sur l’appareil.

> [!NOTE]
>**L’autorisation facultative** est différente de **Désactiver la protection web**. L’autorisation VPN facultative permet uniquement d’ignorer l’autorisation lors de l’intégration, mais elle est disponible pour que l’utilisateur final puisse l’examiner et l’activer ultérieurement. La **fonctionnalité Désactiver la protection web** permet aux utilisateurs d’intégrer l’application Defender pour point de terminaison sans la protection web. Il ne peut pas être activé ultérieurement.

## <a name="configure-compliance-policy-against-jailbroken-devices"></a>Configurer la stratégie de conformité sur les appareils jailbreakés

Pour empêcher l’accès aux données d’entreprise sur les appareils iOS jailbreakés, nous vous recommandons de configurer la stratégie de conformité suivante sur Intune.

> [!NOTE]
> La détection de jailbreak est une fonctionnalité fournie par Microsoft Defender pour point de terminaison sur iOS. Toutefois, nous vous recommandons de configurer cette stratégie comme couche supplémentaire de défense contre les scénarios de jailbreak.

Suivez les étapes ci-dessous pour créer une stratégie de conformité sur les appareils jailbreakés.

1. Dans le [Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), accédez à Stratégies **de conformité** >  **des appareils** > **Créer une stratégie**. Sélectionnez « iOS/iPadOS » comme plateforme, puis cliquez sur **Créer**.

   :::image type="content" source="images/ios-jb-policy.png" alt-text="Onglet Créer une stratégie" lightbox="images/ios-jb-policy.png":::

1. Spécifiez un nom de la stratégie, par exemple « Stratégie de conformité pour Jailbreak ».

1. Dans la page des paramètres de conformité, cliquez pour développer la section **Intégrité de l’appareil** , puis cliquez sur **Bloquer** pour **les appareils jailbreakés** .

   :::image type="content" source="images/ios-jb-settings.png" alt-text="Onglet Paramètres de conformité" lightbox="images/ios-jb-settings.png":::

1. Dans la section **Actions en cas de non-conformité** , sélectionnez les actions en fonction de vos besoins, puis sélectionnez **Suivant**.

   :::image type="content" source="images/ios-jb-actions.png" alt-text="Onglet Actions en cas de non-conformité" lightbox="images/ios-jb-actions.png":::

1. Dans la section **Affectations** , sélectionnez les groupes d’utilisateurs que vous souhaitez inclure pour cette stratégie, puis sélectionnez **Suivant**.

1. Dans la section **Vérifier+créer** , vérifiez que toutes les informations entrées sont correctes, puis sélectionnez **Créer**.

## <a name="configure-custom-indicators"></a>Configurer des indicateurs personnalisés

Defender pour point de terminaison sur iOS permet également aux administrateurs de configurer des indicateurs personnalisés sur les appareils iOS. Pour plus d’informations sur la configuration des indicateurs personnalisés, consultez [Gérer les indicateurs](/microsoft-365/security/defender-endpoint/manage-indicators).

> [!NOTE]
> Defender pour point de terminaison sur iOS prend en charge la création d’indicateurs personnalisés uniquement pour les adresses IP et les URL/domaines.

## <a name="configure-vulnerability-assessment-of-apps"></a>Configurer l’évaluation des vulnérabilités des applications

>[!Note]
>L’évaluation des vulnérabilités des applications sur Microsoft Defender pour point de terminaison pour iOS est désormais en préversion publique. Les informations suivantes concernent la préversion du produit qui peut être considérablement modifié avant sa commercialisation. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici. Si vous souhaitez participer à la préversion, partagez-nous le nom et l’ID de votre locataire sur **mdatpmobile@microsoft.com**.

Defender pour point de terminaison sur iOS prend en charge les évaluations des vulnérabilités des applications uniquement pour les appareils inscrits (GPM).

Les administrateurs peuvent utiliser les étapes suivantes pour configurer l’évaluation des vulnérabilités des applications.

### <a name="on-a-supervised-device"></a>Sur un appareil supervisé

1. Vérifiez que l’appareil est configuré en [mode Supervisé](ios-install.md#complete-deployment-for-supervised-devices).
1. Pour activer la fonctionnalité dans le [Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), accédez à **Sécurité** >  des points de terminaison **Microsoft Defender pour point de terminaison** >  **Activer la synchronisation des applications pour les appareils iOS/iPadOS**.

     :::image type="content" source="images/tvm-app-sync-toggle.png" alt-text="ToggleSup de synchronisation d’application" lightbox="images/tvm-app-sync-toggle.png":::

### <a name="on-an-unsupervised-device"></a>Sur un appareil non supervisé

1. Pour activer la fonctionnalité dans le [Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), accédez à **Sécurité** >  des points de terminaison **Microsoft Defender pour point de terminaison** >  **Activer la synchronisation des applications pour les appareils iOS/iPadOS**.

   :::image type="content" source="images/tvm-app-sync-toggle.png" alt-text="Bouton bascule de synchronisation d’application" lightbox="images/tvm-app-sync-toggle.png":::

1. Pour obtenir la liste de toutes les applications, y compris les applications non gérées, activez le bouton bascule **Envoyer des données d’inventaire d’applications complètes sur les appareils de système d’exploitation iOS/iPad appartenant à l’utilisateur**.

    :::image type="content" source="images/tvm-full-app-data.png" alt-text="Données d’application complètes" lightbox="images/tvm-full-app-data.png":::

1. Procédez comme suit pour configurer le paramètre de confidentialité.
    - Accédez à **Applications Stratégies** > **de configuration** >  d’application **Ajouter des** > **appareils gérés**.
    - Donnez un nom à la stratégie, **Plateforme** > **iOS/iPadOS**.
    - Sélectionnez **Microsoft Defender pour point de terminaison** comme application cible.
    - Dans la page Paramètres, sélectionnez Utiliser le concepteur de configuration et ajoutez **DefenderTVMPrivacyMode** comme clé et type de valeur en tant que **Chaîne**
        - Pour désactiver la confidentialité et collecter la liste des applications installées, entrez la valeur et `False` affectez cette stratégie aux utilisateurs. 
        - Par défaut, cette valeur est définie sur `True` pour les appareils non supervisés.
        - Pour les utilisateurs dont la clé est définie sur `False`, Defender pour point de terminaison envoie la liste des applications installées sur l’appareil à des fins d’évaluation des vulnérabilités.
    - Cliquez sur **Suivant** et affectez ce profil aux appareils/utilisateurs ciblés.
    - L’activation ou la désactivation des contrôles de confidentialité ci-dessus n’aura pas d’impact sur la vérification de conformité de l’appareil ou l’accès conditionnel.
1. Une fois la configuration appliquée, l’utilisateur final doit ouvrir l’application pour **Approuver** le paramètre de confidentialité.
    - L’écran d’approbation de la confidentialité s’affiche uniquement pour les appareils non supervisés.
    - Seulement si l’utilisateur final approuve la confidentialité, les informations de l’application sont envoyées à la console Defender pour point de terminaison.

        :::image type="content" source="images/tvm-user-privacy.png" alt-text="Confidentialité TVM" lightbox="images/tvm-user-privacy.png":::

Une fois que les versions clientes sont déployées sur des appareils iOS cibles, le traitement démarre. Les vulnérabilités détectées sur ces appareils commencent à apparaître dans le tableau de bord gestion des vulnérabilités Defender. Le traitement peut prendre quelques heures (24 heures maximum). En particulier pour la liste complète des applications à afficher dans l’inventaire logiciel.

## <a name="configure-option-to-send-in-app-feedback"></a>Configurer l’option pour envoyer des commentaires dans l’application

Les clients ont désormais la possibilité de configurer la possibilité d’envoyer des données de commentaires à Microsoft dans l’application Defender pour point de terminaison. Les données de commentaires aident Microsoft à améliorer les produits et à résoudre les problèmes.

> [!NOTE]
> Pour les clients cloud du gouvernement des États-Unis, la collecte de données de commentaires est **désactivée** par défaut.

Procédez comme suit pour configurer l’option permettant d’envoyer des données de commentaires à Microsoft :

1. Dans le [Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), accédez à **Applications Stratégies** >  de **configuration** >  des applications **Ajouter des** > **appareils gérés**.

1. Donnez un nom à la stratégie, **Plateforme > iOS/iPadOS**, sélectionnez le type de profil.

1. Sélectionnez **Microsoft Defender pour point de terminaison** comme application cible.

1. Dans la page Paramètres, sélectionnez **Utiliser le concepteur de configuration** et ajoutez **DefenderSendFeedback** comme clé et type de valeur **booléen**.

   - Pour supprimer la possibilité pour les utilisateurs finaux de fournir des commentaires, définissez la valeur sur `false` et affectez cette stratégie aux utilisateurs. Par défaut, cette valeur est définie sur `true`. Pour les clients du gouvernement des États-Unis, la valeur par défaut est définie sur « false ».

   - Pour les utilisateurs dont la clé est définie sur `true`, il existe une option permettant d’envoyer des données de commentaires à Microsoft au sein de l’application (Menu > Aide & Commentaires > Envoyer des commentaires à Microsoft)

1. Cliquez sur **Suivant** et affectez ce profil aux appareils/utilisateurs ciblés.

## <a name="report-unsafe-site"></a>Signaler un site non sécurisé

Les sites web de hameçonnage empruntent l’identité de sites web dignes de confiance dans le but d’obtenir vos informations personnelles ou financières. Visitez la page [Fournir des commentaires sur la protection réseau](https://www.microsoft.com/wdsi/filesubmission/exploitguard/networkprotection) si vous souhaitez signaler un site web qui pourrait être un site d’hameçonnage.
