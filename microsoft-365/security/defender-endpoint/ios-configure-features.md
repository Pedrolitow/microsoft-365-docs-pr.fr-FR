---
title: configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS
description: Décrit comment déployer Microsoft Defender pour point de terminaison sur des fonctionnalités iOS.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, ios, configure, features, ios
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
- m365-security-compliance
ms.topic: conceptual
ms.subservice: mde
ms.openlocfilehash: da6124fcce55bc8fe0f40158f9849a0fd02b40e1
ms.sourcegitcommit: db89873e22a12705ed313964c1bc2fa19d4fe719
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2022
ms.locfileid: "67652485"
---
# <a name="configure-microsoft-defender-for-endpoint-on-ios-features"></a>configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> [!NOTE]
> Defender pour point de terminaison sur iOS utiliserait un VPN pour fournir la fonctionnalité De protection web. Il ne s’agit pas d’un VPN normal et d’un VPN local/auto-bouclage qui ne prend pas le trafic en dehors de l’appareil.

## <a name="conditional-access-with-defender-for-endpoint-on-ios"></a>Accès conditionnel avec Defender pour point de terminaison sur iOS

Microsoft Defender pour point de terminaison sur iOS, ainsi que Microsoft Intune et Azure Active Directory permet d’appliquer la conformité des appareils et les stratégies d’accès conditionnel en fonction du score de risque de l’appareil. Defender pour point de terminaison est une solution MTD (Mobile Threat Defense) que vous pouvez déployer pour tirer parti de cette fonctionnalité via Intune.

Pour plus d’informations sur la configuration de l’accès conditionnel avec Defender pour point de terminaison sur iOS, consultez [Defender pour point de terminaison et Intune](/mem/intune/protect/advanced-threat-protection).

### <a name="jailbreak-detection-by-microsoft-defender-for-endpoint"></a>Détection de jailbreak par Microsoft Defender pour point de terminaison

Microsoft Defender pour point de terminaison a la capacité de détecter les appareils non managés et gérés qui sont jailbreakés. Si un appareil est détecté comme étant jailbreaké, une alerte à risque **élevé** est signalée au portail Microsoft 365 Defender et si l’accès conditionnel est configuré en fonction du score de risque de l’appareil, l’appareil ne peut pas accéder aux données d’entreprise.

## <a name="web-protection-and-vpn"></a>Protection web et VPN

Par défaut, Defender pour point de terminaison sur iOS inclut et active la fonctionnalité de protection web. La [protection web](web-protection-overview.md) permet de sécuriser les appareils contre les menaces web et de protéger les utilisateurs contre les attaques par hameçonnage. Notez que l’anti-hameçonnage et les indicateurs personnalisés (URL et adresses IP) sont pris en charge dans le cadre de la protection web. Le filtrage de contenu web n’est actuellement pas pris en charge sur les plateformes mobiles.

Defender pour point de terminaison sur iOS utilise un VPN pour fournir cette fonctionnalité. Notez qu’il s’agit d’un VPN local et, contrairement au VPN traditionnel, le trafic réseau n’est pas envoyé en dehors de l’appareil.

Bien qu’il soit activé par défaut, il peut arriver que vous deviez désactiver le VPN. Par exemple, vous souhaitez exécuter des applications qui ne fonctionnent pas lorsqu’un VPN est configuré. Dans ce cas, vous pouvez choisir de désactiver le VPN de l’application sur l’appareil en suivant les étapes ci-dessous :

1. Sur votre appareil iOS, **ouvrez** l’application Paramètres, cliquez ou appuyez sur **Général** , puis **sur VPN**.

2. Cliquez ou appuyez sur le bouton « i » pour Microsoft Defender pour point de terminaison.

3. Désactivez **La connexion à la demande** pour désactiver le VPN. 

   :::image type="content" source="images/ios-vpn-config.png" alt-text="Bouton bascule pour l’option connexion de configuration VPN à la demande" lightbox="images/ios-vpn-config.png":::

> [!NOTE]
> La protection web ne sera pas disponible lorsque le VPN est désactivé. Pour réactiver la protection web, ouvrez l’application Microsoft Defender pour point de terminaison sur l’appareil, puis cliquez ou **appuyez sur Démarrer le VPN**.

## <a name="disable-web-protection"></a>Désactiver la protection web

La protection web est l’une des fonctionnalités clés de Defender pour point de terminaison et nécessite un VPN pour fournir cette fonctionnalité. Le VPN utilisé est un VPN local/de bouclage et non un VPN traditionnel, mais il existe plusieurs raisons pour lesquelles les clients peuvent ne pas préférer le VPN. Les clients qui ne souhaitent pas configurer un VPN peuvent désactiver **la protection web** et déployer Defender pour point de terminaison sans cette fonctionnalité. Les autres fonctionnalités de Defender pour point de terminaison continueront de fonctionner.

Cette configuration est disponible à la fois pour les appareils inscrits (GPM) et pour les appareils non inscrits (MAM). Pour les clients disposant de GPM, les administrateurs peuvent configurer la **protection web** via des appareils gérés dans la configuration d’application. Pour les clients sans inscription, à l’aide de LAM, les administrateurs peuvent configurer la **protection web** par le biais d’applications gérées dans la configuration d’application.

### <a name="configure-web-protection"></a>Configurer la protection web

1. **Désactiver la protection web (GPM)** Utilisez les étapes suivantes pour désactiver **la protection web** pour les appareils inscrits.

    - Dans [le Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), accédez **aux** >  stratégies  >  de **configuration d’applications****Ajouter** >  des **appareils gérés**.
    - Donnez à la stratégie un nom, **Platform > iOS/iPadOS**.
    - Sélectionnez Microsoft Defender pour point de terminaison comme application cible.
    - Dans la page Paramètres, sélectionnez Utiliser le concepteur de configuration et ajoutez **WebProtection** comme clé et type valeur **booléen**.
        - Par défaut, **WebProtection= true**.
        - Administration devez rendre **WebProtection = false** pour désactiver la protection web.
        - Defender envoie la pulsation au portail Microsoft 365 Defender chaque fois que l’utilisateur ouvre l’application.
        - Cliquez sur Suivant et affectez ce profil aux appareils/utilisateurs ciblés.

1. **Désactiver la protection web (GAM)** Utilisez les étapes suivantes pour désactiver **la protection web** pour les appareils non inscrits.

    - Dans [le Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), accédez aux stratégies  >  de **configuration d’application** **d’applications** > **Pour ajouter** >  des **applications gérées**.
    - Donner à la stratégie un nom.
    - Sous Sélectionner les applications publiques, choisissez Microsoft Defender pour point de terminaison comme application cible.
    - Dans la page Paramètres, sous Paramètres de configuration général, ajoutez **WebProtection** comme clé et valeur **false**.
        - Par défaut, **WebProtection= true**.
        - Administration devez rendre **WebProtection = false** pour désactiver la protection web.
        - Defender envoie la pulsation au portail Microsoft 365 Defender chaque fois que l’utilisateur ouvre l’application.
        - Cliquez sur Suivant et affectez ce profil aux appareils/utilisateurs ciblés.

## <a name="configure-network-protection"></a>Configurer la protection réseau

>[!NOTE]
>La protection réseau sur Microsoft Defender pour point de terminaison est désormais en préversion publique. Les informations suivantes concernent la préversion du produit qui peut être sensiblement modifiée avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

La protection réseau dans Microsoft Defender pour point de terminaison est activée par défaut. Les administrateurs peuvent utiliser les étapes suivantes pour configurer la prise en charge mam pour la protection réseau sur les appareils iOS.

1. Dans Microsoft Endpoint Manager Administration, accédez aux stratégies de configuration d’applications > App. Créez une stratégie de configuration d’application.
   :::image type="content" source="images/addiosconfig.png" alt-text="Ajouter une stratégie de configuration." lightbox="images/addiosconfig.png":::

2. Fournissez un nom et une description pour identifier de manière unique la stratégie. Cliquez ensuite sur « Sélectionner des applications publiques », puis choisissez « Microsoft Defender » pour la plateforme iOS/IPadOS :::image type="content" source="images/nameiosconfig.png" alt-text="Nommez la configuration." lightbox="images/nameiosconfig.png":::

3. Dans la page Paramètres, ajoutez « DefenderNetworkProtectionEnable » comme clé et valeur « false » pour désactiver la protection réseau. (La protection réseau est activée par défaut) :::image type="content" source="images/addiosconfigvalue.png" alt-text="Ajouter une valeur de configuration." lightbox="images/addiosconfigvalue.png":::

4. Pour d’autres configurations liées à la protection réseau, ajoutez les clés suivantes et la valeur correspondante appropriée.

    |Clé| Par défaut (true-enable, false-disable)|Description|
    |---|---|---|
    |DefenderEndUserTrustFlowEnable| false | Autoriser les utilisateurs à approuver des réseaux et des certificats|
    |DefenderNetworkProtectionAutoRemediation| true |Ce paramètre est utilisé par l’administrateur informatique pour activer ou désactiver les alertes de correction envoyées lorsqu’un utilisateur effectue des activités de correction, telles que le passage à des points d’accès WIFI sécurisés ou la suppression de certificats suspects détectés par Defender|
    |DefenderNetworkProtectionPrivacy| true |Ce paramètre est géré par l’administrateur informatique pour activer ou désactiver la confidentialité dans la protection du réseau|
  
5. Dans la section Affectations, l’administrateur peut choisir des groupes d’utilisateurs à inclure et exclure de la stratégie.
   :::image type="content" source="images/assigniosconfig.png" alt-text="Affectez la configuration." lightbox="images/assigniosconfig.png":::

6. Examinez et créez la stratégie de configuration.

## <a name="co-existence-of-multiple-vpn-profiles"></a>Coexistence de plusieurs profils VPN

Apple iOS ne prend pas en charge plusieurs VPN à l’échelle de l’appareil pour être actifs simultanément. Bien que plusieurs profils VPN puissent exister sur l’appareil, un seul VPN peut être actif à la fois.

## <a name="configure-microsoft-defender-for-endpoint-risk-signal-in-app-protection-policy-mam"></a>Configurer Microsoft Defender pour point de terminaison signal de risque dans la stratégie de protection des applications (GAM)

Microsoft Defender pour point de terminaison pouvez être configuré pour envoyer des signaux de menace à utiliser dans les stratégies de protection des applications (APP, également appelée GAM) sur iOS/iPadOS. Avec cette fonctionnalité, vous pouvez utiliser Microsoft Defender pour point de terminaison pour protéger l’accès aux données d’entreprise contre les appareils non inscrits.

Les étapes de configuration des stratégies de protection des applications avec Microsoft Defender pour point de terminaison sont les suivantes :

1. Configurez la connexion de votre locataire Microsoft Endpoint Manager à Microsoft Defender pour point de terminaison. Dans le [Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), accédez aux connecteurs d’administration  \> des **locataires et aux jetons** \> **Microsoft Defender pour point de terminaison** (sous multiplateforme) ou **Endpoint Security** \> **Microsoft Defender pour point de terminaison** (sous configuration) et activez les bascules sous **Paramètres de stratégie de protection des applications pour iOS**.

2. Sélectionnez Enregistrer. Vous devriez voir que **l’état de la connexion** est maintenant défini sur **Activé**.

3. Créer une stratégie de protection des applications : une fois la configuration de votre connecteur Microsoft Defender pour point de terminaison terminée, accédez à **Applications** \> **Protection d'applications stratégies** (sous Stratégie) pour créer une stratégie ou mettre à jour une stratégie existante.

4. Sélectionnez les paramètres de plateforme, **d’applications, de protection des données et d’accès** requis par votre organisation pour votre stratégie.

5. Dans **les conditions de** **lancement** \> conditionnel de l’appareil, vous trouverez le niveau **de menace maximal autorisé pour l’appareil**. Cette option doit être configurée sur Low, Medium, High ou Secured. Les actions disponibles sont **Bloquer l’accès** ou **réinitialiser les données**. Vous pouvez voir une boîte de dialogue d’information pour vous assurer que votre connecteur est configuré avant que ce paramètre ne prenne effet. Si votre connecteur est déjà configuré, vous pouvez ignorer cette boîte de dialogue.

6. Terminez avec Affectations et enregistrez votre stratégie.

Pour plus d’informations sur la gestion des applications mobiles ou la stratégie de protection des applications, consultez [les paramètres de stratégie de protection des applications iOS](/mem/intune/apps/app-protection-policy-settings-ios).

### <a name="deploying-microsoft-defender-for-endpoint-for-mam-or-on-unenrolled-devices"></a>Déploiement de Microsoft Defender pour point de terminaison pour la gestion des applications mobiles ou sur des appareils non inscrits

Microsoft Defender pour point de terminaison sur iOS active le scénario de stratégie de protection des applications et est disponible dans l’App Store d’Apple. Les utilisateurs finaux doivent installer la dernière version de l’application directement à partir de l’App Store Apple.

## <a name="privacy-controls"></a>Contrôles de confidentialité

Microsoft Defender pour point de terminaison sur iOS active les contrôles de confidentialité pour les administrateurs et les utilisateurs finaux. Cela inclut les contrôles pour les appareils inscrits (GPM) et non inscrits (MAM).
Pour les clients avec GPM, les administrateurs peuvent configurer les contrôles de confidentialité via des appareils gérés dans la configuration d’application. Pour les clients sans inscription, à l’aide de LAM, les administrateurs peuvent configurer les contrôles de confidentialité par le biais d’applications gérées dans la configuration d’application. Les utilisateurs finaux peuvent également configurer les paramètres de confidentialité à partir des paramètres de l’application Defender.

### <a name="configure-privacy-in-phish-alert-report"></a>Configurer la confidentialité dans le rapport d’alerte de hameçonnage

Les clients peuvent désormais activer le contrôle de confidentialité pour le rapport de hameçonnage envoyé par Microsoft Defender pour point de terminaison sur iOS. Cela garantit que le nom de domaine n’est pas envoyé dans le cadre de l’alerte de hameçonnage chaque fois qu’un site web de hameçonnage est détecté et bloqué par Microsoft Defender pour point de terminaison.

1. **Administration Contrôles de confidentialité (GPM) Utilisez les étapes** suivantes pour activer la confidentialité et ne pas collecter le nom de domaine dans le cadre du rapport d’alerte de hameçonnage pour les appareils inscrits.

    - Dans [le Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), accédez **aux** >  stratégies  >  de **configuration d’applications****Ajouter** >  des **appareils gérés**.

    - Donnez un nom à la stratégie, **Platform > iOS/iPadOS**, sélectionnez le type de profil.

    - Sélectionnez **Microsoft Defender pour point de terminaison** comme application cible.

    - Dans la page Paramètres, sélectionnez **Utiliser le concepteur de configuration** et ajoutez **DefenderExcludeURLInReport** comme clé et type valeur **booléen**.

      - Pour activer la confidentialité et ne pas collecter le nom de domaine, entrez la valeur `true` et affectez cette stratégie aux utilisateurs. Par défaut, cette valeur est définie sur `false`.

      - Pour les utilisateurs avec la clé définie comme `true`, l’alerte de hameçonnage ne contient pas les informations de nom de domaine chaque fois qu’un site malveillant est détecté et bloqué par Defender pour point de terminaison.

    - Cliquez sur **Suivant** et affectez ce profil aux appareils/utilisateurs ciblés.

1. **Administration Contrôles de confidentialité (MAM) Utilisez les étapes suivantes** pour activer la confidentialité et ne pas collecter le nom de domaine dans le cadre du rapport d’alerte de hameçonnage pour les appareils non inscrits.

    - Dans [le Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), accédez aux stratégies  >  de **configuration d’application** **d’applications** > **Pour ajouter** >  des **applications gérées**.

    - Donner à la stratégie un nom.

    - Sous Sélectionner les applications publiques, choisissez **Microsoft Defender pour point de terminaison** comme application cible.

    - Dans la page Paramètres, sous  **Paramètres de configuration générale** , ajoutez **DefenderExcludeURLInReport** comme clé et valeur **true**.

      - Pour activer la confidentialité et ne pas collecter le nom de domaine, entrez la valeur `true` et affectez cette stratégie aux utilisateurs. Par défaut, cette valeur est définie sur `false`.

      - Pour les utilisateurs avec la clé définie comme `true`, l’alerte de hameçonnage ne contient pas les informations de nom de domaine chaque fois qu’un site malveillant est détecté et bloqué par Defender pour point de terminaison.

    - Cliquez sur **Suivant** et affectez ce profil aux appareils/utilisateurs ciblés.

1. **Contrôles de confidentialité des utilisateurs finaux** Ces contrôles aident l’utilisateur final à configurer les informations partagées avec son organisation.
    - Pour les appareils supervisés, les contrôles de l’utilisateur final ne sont pas visibles. Administration décide et contrôle les paramètres.
    - Toutefois, pour les appareils non supervisés, le contrôle s’affiche sous **paramètres > confidentialité**
        - Les utilisateurs verront un bouton bascule pour les **informations de site non sécurisées**.
        - Ce bouton bascule est visible uniquement si Administration a défini **DefenderExcludeURLInReport = true**
        - S’il est activé par Administration, les utilisateurs peuvent décider s’ils souhaitent envoyer ou non les informations de site non sécurisées à leur organisation.
        - Par défaut, son paramètre est défini `true`sur , les informations de site non sécurisées sont envoyées.
        - Si l’utilisateur bascule dessus `false`, les détails du site non sécurisé ne sont pas envoyés.

L’activation ou la désactivation des contrôles de confidentialité ci-dessus n’aura pas d’impact sur la vérification de la conformité de l’appareil ou l’accès conditionnel.

## <a name="optional-permissions"></a>Autorisations facultatives

Microsoft Defender pour point de terminaison sur iOS active les **autorisations facultatives** dans le flux d’intégration. Actuellement, les autorisations requises par Defender pour point de terminaison sont obligatoires dans le flux d’intégration. Avec cette fonctionnalité, les administrateurs peuvent déployer Defender pour point de terminaison sur des appareils BYOD sans appliquer **l’autorisation VPN** obligatoire lors de l’intégration. Les utilisateurs finaux peuvent intégrer l’application sans les autorisations obligatoires et passer en revue ultérieurement ces autorisations. Cette fonctionnalité est actuellement présente uniquement pour les appareils inscrits (GPM).

### <a name="configure-optional-permission"></a>Configurer l’autorisation facultative

1. **Administration flux (MDM)** Procédez comme suit pour activer l’autorisation **VPN facultative** pour les appareils inscrits.

    - Dans [le Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), accédez **aux** >  stratégies  >  de **configuration d’applications****Ajouter** >  des **appareils gérés**.

    - Donnez un nom à la stratégie, sélectionnez **Platform > iOS/iPadOS**.

    - Sélectionnez **Microsoft Defender pour point de terminaison** comme application cible.

    - Dans la page Paramètres, **sélectionnez Utiliser le concepteur de configuration** et ajoutez **DefenderOptionalVPN** comme clé et type valeur **booléen**.

      - Pour activer l’autorisation VPN facultative, entrez la valeur `true` sous et affectez cette stratégie aux utilisateurs. Par défaut, cette valeur est définie sur `false`.
      - Pour les utilisateurs avec la clé définie comme `true`, les utilisateurs pourront intégrer l’application sans accorder l’autorisation VPN.

    - Cliquez sur **Suivant** et affectez ce profil aux appareils/utilisateurs ciblés.
1. **Flux de l’utilisateur final** : l’utilisateur installe et ouvre l’application pour démarrer l’intégration.
    - Si l’administrateur dispose d’autorisations facultatives, l’utilisateur peut **ignorer** l’autorisation VPN et terminer l’intégration.
    - Même si l’utilisateur a ignoré le VPN, l’appareil peut être intégré et la pulsation est envoyée.
    - Étant `VPN` désactivé, `Web Protection` ne sera pas actif.
    - Plus tard, l’utilisateur peut activer l’application `Web Protection` à partir de l’application. Cela permet d’installer la configuration VPN sur l’appareil.

> [!NOTE]
>**L’autorisation facultative** est différente de **Désactiver la protection web**. L’autorisation VPN facultative permet uniquement d’ignorer l’autorisation pendant l’intégration, mais elle est disponible pour que l’utilisateur final puisse l’examiner et l’activer ultérieurement. La **désactivation de la protection web** permet aux utilisateurs d’intégrer l’application Defender pour point de terminaison sans protection web. Il ne peut pas être activé ultérieurement.

## <a name="configure-compliance-policy-against-jailbroken-devices"></a>Configurer la stratégie de conformité sur les appareils jailbreakés

Pour empêcher l’accès aux données d’entreprise sur les appareils iOS jailbreakés, nous vous recommandons de configurer la stratégie de conformité suivante sur Intune.

> [!NOTE]
> La détection jailbreak est une fonctionnalité fournie par Microsoft Defender pour point de terminaison sur iOS. Toutefois, nous vous recommandons de configurer cette stratégie en tant que couche supplémentaire de défense contre les scénarios jailbreak.

Suivez les étapes ci-dessous pour créer une stratégie de conformité sur les appareils jailbreakés.

1. Dans [le Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), accédez à Stratégies de **conformité** >  **des appareils** > **Créer une stratégie**. Sélectionnez « iOS/iPadOS » comme plateforme, puis cliquez sur **Créer**.

   :::image type="content" source="images/ios-jb-policy.png" alt-text="Onglet Créer une stratégie" lightbox="images/ios-jb-policy.png":::

1. Spécifiez un nom de la stratégie, par exemple « Stratégie de conformité pour Jailbreak ».

1. Dans la page Paramètres de conformité, cliquez pour développer la section **Intégrité de l’appareil** , puis cliquez sur **Bloquer** pour **les appareils jailbreakés** .

   :::image type="content" source="images/ios-jb-settings.png" alt-text="Onglet Paramètres de conformité" lightbox="images/ios-jb-settings.png":::

1. Dans la section **Actions pour la non-conformité** , sélectionnez les actions en fonction de vos besoins, puis sélectionnez **Suivant**.

   :::image type="content" source="images/ios-jb-actions.png" alt-text="Onglet Actions pour la non-conformité" lightbox="images/ios-jb-actions.png":::

1. Dans la section **Affectations** , sélectionnez les groupes d’utilisateurs que vous souhaitez inclure pour cette stratégie, puis sélectionnez **Suivant**.

1. Dans la section **Vérifier+Créer** , vérifiez que toutes les informations entrées sont correctes, puis sélectionnez **Créer**.

## <a name="configure-custom-indicators"></a>Configurer des indicateurs personnalisés

Defender pour point de terminaison sur iOS permet également aux administrateurs de configurer des indicateurs personnalisés sur les appareils iOS. Pour plus d’informations sur la configuration des indicateurs personnalisés, consultez [Gérer les indicateurs](/microsoft-365/security/defender-endpoint/manage-indicators).

> [!NOTE]
> Defender pour point de terminaison sur iOS prend en charge la création d’indicateurs personnalisés uniquement pour les adresses IP et les URL/domaines.

## <a name="configure-vulnerability-assessment-of-apps"></a>Configurer l’évaluation des vulnérabilités des applications

>[!Note]
>L’évaluation des vulnérabilités des applications sur Microsoft Defender pour point de terminaison pour iOS est désormais en préversion publique. Les informations suivantes concernent la préversion du produit qui peut être sensiblement modifiée avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici. Si vous souhaitez participer à la préversion, partagez votre nom de locataire et votre ID avec nous sur **mdatpmobile@microsoft.com**.

Defender pour point de terminaison sur iOS prend en charge les évaluations des vulnérabilités des applications uniquement pour les appareils inscrits (GPM).

Les administrateurs peuvent utiliser les étapes suivantes pour configurer l’évaluation des vulnérabilités des applications.

### <a name="on-a-supervised-device"></a>Sur un appareil supervisé

1. Vérifiez que l’appareil est configuré en [mode supervisé](ios-install.md#complete-deployment-for-supervised-devices).
1. Pour activer la fonctionnalité dans le Centre d’administration [Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), accédez à **Endpoint Security** >  **Microsoft Defender pour point de terminaison** >  **Enable App Sync pour les appareils iOS/iPadOS**.

     :::image type="content" source="images/tvm-app-sync-toggle.png" alt-text="Basculement de synchronisation d’application" lightbox="images/tvm-app-sync-toggle.png":::

### <a name="on-an-unsupervised-device"></a>Sur un appareil non supervisé

1. Pour activer la fonctionnalité dans le Centre d’administration [Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), accédez à **Endpoint Security** >  **Microsoft Defender pour point de terminaison** >  **Enable App Sync pour les appareils iOS/iPadOS**.

   :::image type="content" source="images/tvm-app-sync-toggle.png" alt-text="Bascule de synchronisation d’application" lightbox="images/tvm-app-sync-toggle.png":::

1. Pour obtenir la liste de toutes les applications, y compris les applications non gérées, activez le bouton bascule **Envoyer des données d’inventaire d’applications complètes sur les appareils de système d’exploitation iOS/iPad personnels**.

    :::image type="content" source="images/tvm-full-app-data.png" alt-text="Données d’application complètes" lightbox="images/tvm-full-app-data.png":::

1. Utilisez les étapes suivantes pour configurer le paramètre de confidentialité.
    - Accédez aux stratégies  > **de configuration d’application** **d’applications** > **Pour ajouter** > **des appareils gérés**.
    - Donnez un nom à la stratégie, **Platform** > **iOS/iPadOS**.
    - Sélectionnez **Microsoft Defender pour point de terminaison** comme application cible.
    - Dans la page Paramètres, sélectionnez Utiliser le concepteur de configuration et ajoutez **DefenderTVMPrivacyMode** comme clé et type valeur en tant que **chaîne**
        - Pour désactiver la confidentialité et collecter la liste des applications installées, entrez la valeur `False` et attribuez cette stratégie aux utilisateurs. 
        - Par défaut, cette valeur est définie pour `True` les appareils non supervisés.
        - Pour les utilisateurs avec la clé définie comme `False`, Defender pour point de terminaison envoie la liste des applications installées sur l’appareil pour l’évaluation des vulnérabilités.
    - Cliquez sur **Suivant** et affectez ce profil aux appareils/utilisateurs ciblés.
    - L’activation ou la désactivation des contrôles de confidentialité ci-dessus n’aura pas d’impact sur la vérification de la conformité de l’appareil ou l’accès conditionnel.
1. Une fois la configuration appliquée, l’utilisateur final doit ouvrir l’application pour **approuver** le paramètre de confidentialité.
    - L’écran d’approbation de la confidentialité s’affiche uniquement pour les appareils non supervisés.
    - Uniquement si l’utilisateur final approuve la confidentialité, les informations de l’application sont envoyées à la console Defender pour point de terminaison.

        :::image type="content" source="images/tvm-user-privacy.png" alt-text="Confidentialité TVM" lightbox="images/tvm-user-privacy.png":::

Une fois que les versions clientes sont déployées sur des appareils iOS cibles, le traitement démarre. Les vulnérabilités détectées sur ces appareils commencent à s’afficher dans le tableau de bord Gestion des vulnérabilités Defender. Le traitement peut prendre quelques heures (au maximum 24 heures). En particulier pour la liste complète des applications à afficher dans l’inventaire logiciel.

## <a name="configure-option-to-send-in-app-feedback"></a>Configurer l’option pour envoyer des commentaires dans l’application

Les clients ont désormais la possibilité de configurer la possibilité d’envoyer des données de commentaires à Microsoft dans l’application Defender pour point de terminaison. Les données de commentaires aident Microsoft à améliorer les produits et à résoudre les problèmes.

> [!NOTE]
> Pour les clients du cloud us Government, la collecte des données de commentaires est **désactivée** par défaut.

Utilisez les étapes suivantes pour configurer l’option permettant d’envoyer des données de commentaires à Microsoft :

1. Dans [Microsoft Endpoint Manager centre d’administration](https://go.microsoft.com/fwlink/?linkid=2109431) et accédez **aux** >  stratégies  >  de **configuration d’applications****Ajouter** >  des **appareils gérés**.

1. Donnez un nom à la stratégie, **Platform > iOS/iPadOS**, sélectionnez le type de profil.

1. Sélectionnez **Microsoft Defender pour point de terminaison** comme application cible.

1. Dans la page Paramètres, sélectionnez **Utiliser le concepteur de configuration** et ajoutez **DefenderSendFeedback** comme clé et type valeur **booléen**.

   - Pour supprimer la possibilité pour les utilisateurs finaux de fournir des commentaires, définissez la valeur et `false` attribuez cette stratégie aux utilisateurs. Par défaut, cette valeur est définie sur `true`. Pour les clients du gouvernement des États-Unis, la valeur par défaut est définie sur « false ».

   - Pour les utilisateurs avec la clé définie comme `true`, il y aura une option pour envoyer des données de commentaires à Microsoft dans l’application (Menu > Aide & commentaires > Envoyer des commentaires à Microsoft)

1. Cliquez sur **Suivant** et affectez ce profil aux appareils/utilisateurs ciblés.

## <a name="report-unsafe-site"></a>Signaler un site non sécurisé

Les sites web de hameçonnage empruntent l’identité de sites web dignes de confiance pour obtenir vos informations personnelles ou financières. Visitez la page [Fournir des commentaires sur la protection réseau](https://www.microsoft.com/wdsi/filesubmission/exploitguard/networkprotection) si vous souhaitez signaler un site web qui pourrait être un site de hameçonnage.
