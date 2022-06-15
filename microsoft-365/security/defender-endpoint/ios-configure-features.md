---
title: configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS
description: Décrit comment déployer Microsoft Defender pour point de terminaison sur iOS fonctionnalités.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, ios, configure, features, ios
ms.prod: m365-security
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
ms.technology: mde
ms.openlocfilehash: 8defbb5d1a72afd13110d3c76a4770e40ac1c469
ms.sourcegitcommit: 66228a5506fdceb4cbf0d55b9de3f2943740134f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2022
ms.locfileid: "66089256"
---
# <a name="configure-microsoft-defender-for-endpoint-on-ios-features"></a>configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> [!NOTE]
> Defender pour point de terminaison sur iOS utiliserait un VPN pour fournir la fonctionnalité De protection web. Il ne s’agit pas d’un VPN normal et d’un VPN local/auto-bouclage qui ne prend pas le trafic en dehors de l’appareil.

## <a name="conditional-access-with-defender-for-endpoint-on-ios"></a>Accès conditionnel avec Defender pour point de terminaison sur iOS

Microsoft Defender pour point de terminaison sur iOS ainsi que Microsoft Intune et Azure Active Directory permet d’appliquer la conformité des appareils et les stratégies d’accès conditionnel en fonction du score de risque de l’appareil. Defender pour point de terminaison est une solution MTD (Mobile Threat Defense) que vous pouvez déployer pour tirer parti de cette fonctionnalité via Intune.

Pour plus d’informations sur la configuration de l’accès conditionnel avec Defender pour point de terminaison sur iOS, consultez [Defender pour point de terminaison et Intune](/mem/intune/protect/advanced-threat-protection).

### <a name="jailbreak-detection-by-microsoft-defender-for-endpoint"></a>Détection de jailbreak par Microsoft Defender pour point de terminaison

Microsoft Defender pour point de terminaison a la capacité de détecter les appareils non managés et gérés qui sont jailbreakés. Si un appareil est détecté comme étant jailbreaké **, une alerte** à haut risque est signalée au portail Microsoft 365 Defender et si l’accès conditionnel est configuré en fonction du score de risque de l’appareil, l’appareil ne peut pas accéder aux données d’entreprise.

## <a name="web-protection-and-vpn"></a>Protection web et VPN

Par défaut, Defender pour point de terminaison sur iOS inclut et active la fonctionnalité de protection web. La [protection web](web-protection-overview.md) permet de sécuriser les appareils contre les menaces web et de protéger les utilisateurs contre les attaques par hameçonnage. Notez que l’anti-hameçonnage et les indicateurs personnalisés (URL et adresses IP) sont pris en charge dans le cadre de la protection web. Le filtrage de contenu web n’est actuellement pas pris en charge sur iOS.

Defender pour point de terminaison sur iOS utilise un VPN pour fournir cette fonctionnalité. Notez qu’il s’agit d’un VPN local et, contrairement au VPN traditionnel, le trafic réseau n’est pas envoyé en dehors de l’appareil.

Bien qu’il soit activé par défaut, il peut arriver que vous deviez désactiver le VPN. Par exemple, vous souhaitez exécuter des applications qui ne fonctionnent pas lorsqu’un VPN est configuré. Dans ce cas, vous pouvez choisir de désactiver le VPN de l’application sur l’appareil en suivant les étapes ci-dessous :

1. Sur votre appareil iOS, ouvrez l’application **Paramètres**, cliquez ou appuyez sur **Général**, puis **sur VPN**.

2. Cliquez ou appuyez sur le bouton « i » pour Microsoft Defender pour point de terminaison.

3. Désactivez **Connecter à la demande** pour désactiver le VPN. 

   :::image type="content" source="images/ios-vpn-config.png" alt-text="Bouton bascule pour l’option de configuration VPN Connecter à la demande" lightbox="images/ios-vpn-config.png":::

> [!NOTE]
> La protection web ne sera pas disponible lorsque le VPN est désactivé. Pour réactiver la protection web, ouvrez l’application Microsoft Defender pour point de terminaison sur l’appareil, puis cliquez ou **appuyez sur Démarrer le VPN**.

## <a name="configure-network-protection"></a>Configurer la protection réseau
>[!NOTE] 
>La protection réseau sur Microsoft Defender pour point de terminaison est désormais en préversion publique. Les informations suivantes concernent la préversion du produit qui peut être sensiblement modifiée avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

La protection réseau dans Microsoft Defender pour point de terminaison est activée par défaut. Les administrateurs peuvent utiliser les étapes suivantes pour configurer la prise en charge de la gestion des applications mobiles pour la protection réseau sur les appareils iOS.

1. Dans Microsoft Endpoint Manager Administration, accédez aux stratégies de configuration d’applications > App. Créez une stratégie de configuration d’application.
   :::image type="content" source="images/addiosconfig.png" alt-text="Ajouter une stratégie de configuration." lightbox="images/addiosconfig.png":::
   
2. Fournissez un nom et une description pour identifier de manière unique la stratégie. Cliquez ensuite sur « Sélectionner des applications publiques », puis choisissez « Microsoft Defender » pour Platform iOS/IPadOS :::image type="content" source="images/nameiosconfig.png" alt-text="Nommez la configuration." lightbox="images/nameiosconfig.png":::
   
3. Dans Paramètres page, ajoutez « DefenderNetworkProtectionEnable » comme clé et valeur « false » pour désactiver la protection réseau. (La protection réseau est activée par défaut) :::image type="content" source="images/addiosconfigvalue.png" alt-text="Ajouter une valeur de configuration." lightbox="images/addiosconfigvalue.png":::
   
4. Pour d’autres configurations liées à la protection réseau, ajoutez les clés suivantes et la valeur correspondante appropriée.

    |Clé| Par défaut (true-enable, false-disable)|Description|
    |---|---|---|
    |DefenderEndUserTrustFlowEnable| false | Autoriser les utilisateurs à approuver des réseaux et des certificats|
    |DefenderNetworkProtectionAutoRemediation| true |Ce paramètre est utilisé par l’administrateur informatique pour activer ou désactiver les alertes de correction envoyées lorsqu’un utilisateur effectue des activités de correction telles que le passage à des points d’accès WIFI sécurisés ou la suppression de certificats suspects détectés par Defender|
    |DefenderNetworkProtectionPrivacy| true |Ce paramètre est géré par l’administrateur informatique pour activer ou désactiver la confidentialité dans la protection du réseau|
  
5. Dans la section Affectations, l’administrateur peut choisir des groupes d’utilisateurs à inclure et exclure de la stratégie.
   :::image type="content" source="images/assigniosconfig.png" alt-text="Affectez la configuration." lightbox="images/assigniosconfig.png":::
   
6. Examinez et créez la stratégie de configuration.

## <a name="co-existence-of-multiple-vpn-profiles"></a>Coexistence de plusieurs profils VPN

Apple iOS ne prend pas en charge plusieurs VPN à l’échelle de l’appareil pour être actifs simultanément. Bien que plusieurs profils VPN puissent exister sur l’appareil, un seul VPN peut être actif à la fois.

## <a name="configure-microsoft-defender-for-endpoint-risk-signal-in-app-protection-policy-mam"></a>Configurer Microsoft Defender pour point de terminaison signal de risque dans la stratégie de protection des applications (GAM)

Microsoft Defender pour point de terminaison pouvez être configuré pour envoyer des signaux de menace à utiliser dans les stratégies de protection des applications (APP, également appelée GAM) sur iOS/iPadOS. Avec cette fonctionnalité, vous pouvez utiliser Microsoft Defender pour point de terminaison pour protéger l’accès aux données d’entreprise contre les appareils non inscrits.

Les étapes de configuration des stratégies de protection des applications avec Microsoft Defender pour point de terminaison sont les suivantes :

1. Configurez la connexion de votre locataire Microsoft Endpoint Manager à Microsoft Defender pour point de terminaison. Dans le [Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), accédez aux connecteurs d’administration  \> des **locataires et aux jetons** \> **Microsoft Defender pour point de terminaison** (sous multiplateforme) ou **Endpoint Security** \> **Microsoft Defender pour point de terminaison** (sous configuration) et activez les boutons bascule sous Paramètres de stratégie de **protection des applications pour iOS**.

2. Sélectionnez Enregistrer. Vous devriez voir que **l’état de la connexion** est maintenant défini sur **Activé**.

3. Créer une stratégie de protection des applications : une fois la configuration de votre connecteur Microsoft Defender pour point de terminaison terminée, accédez à **Applications** \> **Protection d'applications stratégies** (sous Stratégie) pour créer une stratégie ou mettre à jour une stratégie existante.

4. Sélectionnez les paramètres de plateforme, **d’applications, de protection des données et d’accès** requis par votre organisation pour votre stratégie.

5. Dans **les conditions de** **lancement** \> conditionnel de l’appareil, vous trouverez le niveau **de menace maximal autorisé pour l’appareil**. Cette option doit être configurée sur Low, Medium, High ou Secured. Les actions disponibles sont **Bloquer l’accès** ou **réinitialiser les données**. Vous pouvez voir une boîte de dialogue d’information pour vous assurer que votre connecteur est configuré avant que ce paramètre ne prenne effet. Si votre connecteur est déjà configuré, vous pouvez ignorer cette boîte de dialogue.

6. Terminez avec Affectations et enregistrez votre stratégie.

Pour plus d’informations sur la gestion des applications mobiles ou la stratégie de protection des applications, consultez [iOS paramètres de stratégie de protection des applications](/mem/intune/apps/app-protection-policy-settings-ios).

### <a name="deploying-microsoft-defender-for-endpoint-for-mam-or-on-unenrolled-devices"></a>Déploiement de Microsoft Defender pour point de terminaison pour la gestion des applications mobiles ou sur des appareils non inscrits

Microsoft Defender pour point de terminaison sur iOS active le scénario de stratégie de protection des applications et est disponible dans l’App Store d’Apple. Les utilisateurs finaux doivent installer la dernière version de l’application directement à partir de l’App Store Apple.

## <a name="privacy-controls"></a>Contrôles de confidentialité

> [!IMPORTANT]
> Les contrôles de confidentialité pour Microsoft Defender pour point de terminaison sur iOS sont en préversion. Les informations suivantes concernent le produit pré-publié qui peut être considérablement modifié avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

### <a name="configure-privacy-in-phish-alert-report"></a>Configurer la confidentialité dans le rapport d’alerte de hameçonnage

Les clients peuvent désormais activer le contrôle de confidentialité pour le rapport de hameçonnage envoyé par Microsoft Defender pour point de terminaison sur iOS. Cela garantit que le nom de domaine n’est pas envoyé dans le cadre de l’alerte de hameçonnage chaque fois qu’un site web de hameçonnage est détecté et bloqué par Microsoft Defender pour point de terminaison.

Utilisez les étapes suivantes pour activer la confidentialité et ne pas collecter le nom de domaine dans le cadre du rapport d’alerte de hameçonnage.

1. Dans [Microsoft Endpoint Manager centre d’administration](https://go.microsoft.com/fwlink/?linkid=2109431), accédez **aux** >  stratégies  >  de **configuration d’applications****Ajouter** > **des appareils gérés**.

2. Donnez un nom à la stratégie, **Platform > iOS/iPadOS**, sélectionnez le type de profil.

3. Sélectionnez **Microsoft Defender pour point de terminaison** comme application cible.

4. Dans Paramètres page, sélectionnez Utiliser le **concepteur de configuration** et ajoutez **DefenderExcludeURLInReport** comme clé et type valeur **booléen**.

   - Pour activer la confidentialité et ne pas collecter le nom de domaine, entrez la valeur `true` et affectez cette stratégie aux utilisateurs. Par défaut, cette valeur est définie sur `false`.

   - Pour les utilisateurs avec la clé définie comme `true`, l’alerte de hameçonnage ne contient pas les informations de nom de domaine chaque fois qu’un site malveillant est détecté et bloqué par Defender pour point de terminaison.

5. Cliquez sur **Suivant** et affectez ce profil aux appareils/utilisateurs ciblés.

L’activation ou la désactivation des contrôles de confidentialité ci-dessus n’aura pas d’impact sur la vérification de la conformité de l’appareil ou l’accès conditionnel.

## <a name="configure-compliance-policy-against-jailbroken-devices"></a>Configurer la stratégie de conformité sur les appareils jailbreakés

Pour empêcher l’accès aux données d’entreprise sur les appareils iOS jailbreakés, nous vous recommandons de configurer la stratégie de conformité suivante sur Intune.

> [!NOTE]
> La détection de jailbreak est une fonctionnalité fournie par Microsoft Defender pour point de terminaison sur iOS. Toutefois, nous vous recommandons de configurer cette stratégie en tant que couche supplémentaire de défense contre les scénarios jailbreak.

Suivez les étapes ci-dessous pour créer une stratégie de conformité sur les appareils jailbreakés.

1. Dans [Microsoft Endpoint Manager centre d’administration](https://go.microsoft.com/fwlink/?linkid=2109431), accédez à Stratégies de **conformité** ->  **des appareils** -> **pour créer une stratégie**. Sélectionnez « iOS/iPadOS » comme plateforme, puis cliquez sur **Créer**.

   :::image type="content" source="images/ios-jb-policy.png" alt-text="Onglet Créer une stratégie" lightbox="images/ios-jb-policy.png":::

1. Spécifiez un nom de la stratégie, par exemple « Stratégie de conformité pour Jailbreak ».

1. Dans la page Paramètres de conformité, cliquez pour développer la section **Intégrité de l’appareil** , puis cliquez sur **Bloquer** pour **les appareils jailbreakés** .

   :::image type="content" source="images/ios-jb-settings.png" alt-text="Onglet Paramètres de conformité" lightbox="images/ios-jb-settings.png":::

1. Dans la section **Actions pour la non-conformité** , sélectionnez les actions en fonction de vos besoins, puis sélectionnez **Suivant**.

   :::image type="content" source="images/ios-jb-actions.png" alt-text="Onglet Actions pour la non-conformité" lightbox="images/ios-jb-actions.png":::

1. Dans la section **Affectations** , sélectionnez les groupes d’utilisateurs que vous souhaitez inclure pour cette stratégie, puis sélectionnez **Suivant**.

1. Dans la section **Vérifier+Créer** , vérifiez que toutes les informations entrées sont correctes, puis sélectionnez **Créer**.

## <a name="configure-custom-indicators"></a>Configurer des indicateurs personnalisés

Defender pour point de terminaison sur iOS permet également aux administrateurs de configurer des indicateurs personnalisés sur iOS appareils. Pour plus d’informations sur la configuration des indicateurs personnalisés, consultez [Gérer les indicateurs](/microsoft-365/security/defender-endpoint/manage-indicators).

> [!NOTE]
> Defender pour point de terminaison sur iOS prend en charge la création d’indicateurs personnalisés uniquement pour les adresses IP et les URL/domaines.

## <a name="configure-option-to-send-in-app-feedback"></a>Configurer l’option pour envoyer des commentaires dans l’application 

Les clients ont désormais la possibilité de configurer la possibilité d’envoyer des données de commentaires à Microsoft dans l’application Defender pour point de terminaison. Les données de commentaires aident Microsoft à améliorer les produits et à résoudre les problèmes.

> [!NOTE]
> Pour les clients du cloud us Government, la collecte des données de commentaires est **désactivée** par défaut. 

Utilisez les étapes suivantes pour configurer l’option permettant d’envoyer des données de commentaires à Microsoft :

1. Dans [Microsoft Endpoint Manager centre d’administration](https://go.microsoft.com/fwlink/?linkid=2109431), accédez **aux** >  stratégies  >  de **configuration d’applications****Ajouter** > **des appareils gérés**.

1. Donnez un nom à la stratégie, **Platform > iOS/iPadOS**, sélectionnez le type de profil.

1. Sélectionnez **Microsoft Defender pour point de terminaison** comme application cible.

1. Dans Paramètres page, sélectionnez Utiliser le **concepteur de configuration** et ajoutez **DefenderSendFeedback** comme clé et type valeur **booléen**.
   
   - Pour supprimer la possibilité pour les utilisateurs finaux de fournir des commentaires, définissez la valeur et `false` attribuez cette stratégie aux utilisateurs. Par défaut, cette valeur est définie sur `true`. Pour les clients du gouvernement des États-Unis, la valeur par défaut est définie sur « false ».
   
   - Pour les utilisateurs avec la clé définie comme `true`, il y aura une option pour envoyer des données de commentaires à Microsoft dans l’application (Menu > Aide & commentaires > Envoyer des commentaires à Microsoft)

1. Cliquez sur **Suivant** et affectez ce profil aux appareils/utilisateurs ciblés.

## <a name="report-unsafe-site"></a>Signaler un site non sécurisé

Les sites web de hameçonnage empruntent l’identité de sites web dignes de confiance pour obtenir vos informations personnelles ou financières. Visitez la page [Fournir des commentaires sur la protection réseau](https://www.microsoft.com/wdsi/filesubmission/exploitguard/networkprotection) si vous souhaitez signaler un site web qui pourrait être un site de hameçonnage.
