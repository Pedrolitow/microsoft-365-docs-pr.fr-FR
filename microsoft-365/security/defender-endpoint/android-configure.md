---
title: Configurer Microsoft Defender pour point de terminaison pour des fonctionnalités Android
description: Décrit comment configurer Microsoft Defender pour point de terminaison sur Android
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, mde, android, configuration
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier3
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 7e5e6aa4d16dd18210754fc5349eb2a71269afc6
ms.sourcegitcommit: a20d30f4e5027f90d8ea4cde95d1d5bacfdd2b5e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2022
ms.locfileid: "68769862"
---
# <a name="configure-defender-for-endpoint-on-android-features"></a>Configurer Defender pour point de terminaison pour des fonctionnalités Android

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

## <a name="conditional-access-with-defender-for-endpoint-on-android"></a>Accès conditionnel avec Defender pour point de terminaison sur Android

Microsoft Defender pour point de terminaison sur Android avec Microsoft Intune et Azure Active Directory permet d’appliquer des stratégies de conformité des appareils et d’accès conditionnel en fonction des niveaux de risque de l’appareil. Defender pour point de terminaison est une solution mtd (Mobile Threat Defense) que vous pouvez déployer pour tirer parti de cette fonctionnalité via Intune.

Pour plus d’informations sur la configuration de Defender pour point de terminaison sur Android et l’accès conditionnel, consultez [Defender pour point de terminaison et Intune](/mem/intune/protect/advanced-threat-protection).

## <a name="configure-custom-indicators"></a>Configurer des indicateurs personnalisés

> [!NOTE]
> Defender pour point de terminaison sur Android prend uniquement en charge la création d’indicateurs personnalisés pour les adresses IP et les URL/domaines.

Defender pour point de terminaison sur Android permet aux administrateurs de configurer des indicateurs personnalisés pour prendre également en charge les appareils Android. Pour plus d’informations sur la configuration des indicateurs personnalisés, consultez [Gérer les indicateurs](manage-indicators.md).

## <a name="configure-web-protection"></a>Configurer la protection web
Defender pour point de terminaison sur Android permet aux administrateurs informatiques de configurer la fonctionnalité de protection web. Cette fonctionnalité est disponible dans le centre de Administration Microsoft Endpoint Manager.

La [protection web](web-protection-overview.md) permet de sécuriser les appareils contre les menaces web et de protéger les utilisateurs contre les attaques par hameçonnage. Notez que les indicateurs anti-hameçonnage et personnalisés (URL et adresses IP) sont pris en charge dans le cadre de la protection web. Le filtrage de contenu web n’est actuellement pas pris en charge sur les plateformes mobiles.

> [!NOTE]
> Defender pour point de terminaison sur Android utilise un VPN afin de fournir la fonctionnalité Web Protection. Il ne s’agit pas d’un VPN standard et d’un VPN local/auto-bouclage qui ne prend pas le trafic en dehors de l’appareil.
> Pour plus d’informations, consultez [Configurer la protection web sur les appareils qui exécutent Android](/mem/intune/protect/advanced-threat-protection-manage-android).

## <a name="network-protection"></a>Protection réseau

Cette fonctionnalité offre une protection contre les menaces liées aux Wi-Fi non autorisés et les certificats non autorisés qui sont le principal vecteur d’attaque pour les réseaux Wi-Fi. Les administrateurs peuvent répertorier les certificats d’autorité de certification racine et d’autorité de certification racine privée dans le centre de Administration Microsoft Endpoint Manager et établir une approbation avec des points de terminaison. Il offre à l’utilisateur une expérience guidée pour se connecter à des réseaux sécurisés et l’avertit également si une menace associée est détectée. 

Il inclut plusieurs contrôles d’administration pour offrir de la flexibilité, comme la possibilité de configurer la fonctionnalité à partir du centre de Administration Microsoft Endpoint Manager, ainsi que d’ajouter des certificats approuvés. Les administrateurs peuvent également activer [les contrôles de confidentialité](/microsoft-365/security/defender-endpoint/android-configure#privacy-controls) pour configurer les données envoyées par Defender pour point de terminaison à partir d’appareils Android.

La protection réseau dans Microsoft Defender pour point de terminaison est désactivée par défaut. Les administrateurs peuvent utiliser les étapes suivantes pour **configurer la protection réseau sur les appareils Android.**

1. Dans Microsoft Endpoint Manager Administration, accédez à Applications > Stratégies de configuration des applications. Créez une stratégie de configuration d’application.
    > [!div class="mx-imgBorder"]
    > ![Image montrant comment créer une stratégie.](images/android-mem.png)
1. Fournissez un nom et une description pour identifier la stratégie de manière unique. Sélectionnez **« Android Entreprise »** comme plateforme et **« Profil professionnel appartenant à l’utilisateur uniquement »** comme type de profil et **« Microsoft Defender »** comme application ciblée.
    > [!div class="mx-imgBorder"]
    > ![Image des détails de la stratégie.](images/appconfigdetails.png)
1. Dans la page Paramètres, sélectionnez **« Utiliser le concepteur de configuration »** et ajoutez **« Activer la protection réseau dans Microsoft Defender »** comme clé et la valeur **« 1 »** pour activer la protection réseau. (La protection réseau est activée par défaut)
    > [!div class="mx-imgBorder"]
    > ![Image montrant comment sélectionner activer la stratégie de protection réseau](images/selectnp.png)
    
    > [!div class="mx-imgBorder"]
    > ![Image de l’ajout d’une stratégie de configuration.](images/npvalue.png)
1. Si votre organisation utilise des autorités de certification racines qui peuvent être privées par nature, une confiance explicite doit être établie entre Intune (solution GPM) et les appareils de l’utilisateur afin que Defender ne les détecte pas comme des certificats non autorisés.  

    Pour établir l’approbation pour les autorités de certification racine, utilisez **« Liste de certificats d’autorité de certification approuvée pour la protection réseau »** comme clé et, dans valeur, ajoutez la **« liste séparée par des virgules des empreintes de certificat (SHA 1) ».**
    
    **Exemple de format d’empreinte numérique à ajouter sera** 50 30 06 09 1d 97 d4 f5 ae 39 f7 cb e7 92 7d 7d 65 2d 34 31, 503006091d97d4f5ae39f7cbe7927d7d652d3431 

> [!IMPORTANT]
 > Les caractères d’empreinte sha-1 du certificat doivent être avec un espace blanc sapé ou non séparé.
> Ce format n’est pas valide  
> 50:30:06:09:1d:97:d4:f5:ae:39:f7:cb:e7:92:7d:7d:65:2d:34:31 

Tous les autres caractères de séparation ne sont pas valides. 
    > ![Image of trusted CA certificate.](images/trustca.png)

5. Pour les autres configurations liées à la protection du réseau, ajoutez les clés suivantes et la valeur correspondante appropriée.
<br>

    | Clé de configuration| Description|
    |---|---|
    |Liste de certificats d’autorité de certification approuvée pour la protection réseau|Ce paramètre est géré par un administrateur de sécurité pour établir une approbation pour l’autorité de certification racine et les certificats auto-signés|
    |Activer la protection réseau dans Microsoft Defender|1 - Activer, 0- Désactiver (par défaut) ; Ce paramètre est utilisé par l’administrateur informatique pour activer ou désactiver les fonctionnalités de protection réseau dans l’application Defender|
    |Activer la confidentialité de la protection du réseau|1 - Activer (par défaut) , 0 - Désactiver ; Ce paramètre est géré par les administrateurs informatiques pour activer ou désactiver la confidentialité dans la protection du réseau.|
    |Autoriser les utilisateurs à approuver des réseaux et des certificats|1 - Activer , 0 - Désactiver (par défaut) ; Ce paramètre est utilisé par les administrateurs informatiques pour activer ou désactiver l’expérience de l’utilisateur final dans l’application pour approuver et se méfier des réseaux non sécurisés et suspects et des certificats malveillants.|
    |Correction automatique des alertes de protection réseau|1 - Activer (par défaut) , 0 - Désactiver ; Ce paramètre est utilisé par les administrateurs informatiques pour activer ou désactiver les alertes de correction envoyées lorsqu’un utilisateur effectue des activités de correction, telles que le passage à un Wi-Fi des points d’accès plus sûrs ou la suppression de certificats suspects détectés par Defender|
    |Gérer la détection de la protection réseau pour les réseaux ouverts|0 - Désactiver (par défaut), 1 - Mode Audit ; Ce paramètre est géré par les Administration informatiques pour activer ou désactiver la détection de réseau ouvert|  
    |Gérer la détection de la protection réseau pour les certificats|0 - Désactiver , 1 - Mode Audit (par défaut) , 2 - Activer ; Lorsque la protection réseau est activée, le mode Audit pour la détection de certificat est activé par défaut. En mode audit, les alertes de notification sont envoyées aux administrateurs SOC, mais aucune notification de l’utilisateur final n’est affichée à l’utilisateur quand defender détecte un certificat incorrect. Les administrateurs peuvent toutefois désactiver cette détection avec 0 comme valeur et activer la fonctionnalité complète en définissant 2 comme valeur , lorsque la fonctionnalité est activée avec la valeur 2, les notifications de l’utilisateur final sont envoyées à l’utilisateur lorsque defender détecte un certificat incorrect et que des alertes sont également envoyées au SOC Administration|
6. Ajoutez les groupes requis sur lesquels la stratégie doit être appliquée. Passez en revue et créez la stratégie.

## <a name="privacy-controls"></a>Contrôles de confidentialité

Les contrôles de confidentialité suivants sont disponibles pour configurer les données envoyées par Defender pour point de terminaison à partir d’appareils Android :

|Rapport sur les menaces     |Détails      |
|--------------------|-------------|
|Rapport sur les programmes malveillants |Les administrateurs peuvent configurer le contrôle de confidentialité pour le rapport sur les programmes malveillants : si la confidentialité est activée, Defender pour point de terminaison n’envoie pas le nom de l’application malveillante et d’autres détails de l’application dans le cadre du rapport d’alerte de programme malveillant |
|Rapport de hameçonnage |Les administrateurs peuvent configurer le contrôle de confidentialité pour les rapports d’hameçonnage : si la confidentialité est activée, Defender pour point de terminaison n’envoie pas le nom de domaine et les détails du site web non sécurisé dans le cadre du rapport d’alerte d’hameçonnage |
|Évaluation des vulnérabilités des applications (Android uniquement) |Par défaut, seules les informations sur les applications installées dans le profil professionnel sont envoyées pour l’évaluation des vulnérabilités. Les administrateurs peuvent désactiver la confidentialité pour inclure des applications personnelles|
|Protection réseau (préversion)| Les administrateurs peuvent activer ou désactiver la confidentialité dans la protection du réseau : si cette option est activée, Defender n’envoie pas les détails du réseau.|

### <a name="configure-privacy-alert-report"></a>Configurer le rapport d’alerte de confidentialité
Les administrateurs peuvent désormais activer le contrôle de confidentialité pour le rapport d’hameçonnage, le rapport sur les programmes malveillants et le rapport réseau envoyé par Microsoft Defender pour point de terminaison sur Android. Cela garantit que le nom de domaine, les détails de l’application et les détails du réseau ne sont pas envoyés dans le cadre de l’alerte chaque fois qu’une menace correspondante est détectée.

Administration contrôles de confidentialité (GPM) Suivez les étapes ci-dessous pour activer la confidentialité.

1. Dans le Centre d’administration Microsoft Endpoint Manager, accédez à **Applications > Stratégies de configuration des applications > Ajouter > appareils gérés**.

2. Donnez un **nom à la stratégie, Plateforme > Entreprise Android, sélectionnez le type de profil**.

3. Sélectionnez **Microsoft Defender pour point de terminaison** comme application cible.

4. Dans la page Paramètres, sélectionnez **Utiliser le concepteur de configuration** , puis cliquez sur **Ajouter**. 
5. Sélectionnez le paramètre de confidentialité requis :
    - Masquer les URL dans le rapport
    - Masquer les URL dans le rapport pour le profil personnel
    - Masquer les détails de l’application dans le rapport
    - Masquer les détails de l’application dans le rapport pour le profil personnel
    - Activer la confidentialité de la protection du réseau

6. Pour activer la confidentialité, entrez la valeur entière 1 et affectez cette stratégie aux utilisateurs. Par défaut, cette valeur est définie sur 0 pour MDE dans le profil professionnel et sur 1 pour MDE sur le profil personnel.

7. Passez en revue et affectez ce profil aux appareils/utilisateurs ciblés.

**Contrôles de confidentialité des utilisateurs finaux**

Ces contrôles aident l’utilisateur final à configurer les informations partagées avec son organisation.

1. Pour **le profil professionnel Android Entreprise**, les contrôles de l’utilisateur final ne sont pas visibles. Les administrateurs contrôlent ces paramètres.
2. Pour **le profil personnel Android Entreprise**, le contrôle s’affiche sous **Paramètres> Confidentialité**.
3. Les utilisateurs verront un bouton bascule pour les informations sur les sites non sécurisés, les applications malveillantes et la protection réseau.

Ces bascules ne sont visibles que si elles sont activées par l’administrateur. Les utilisateurs peuvent décider s’ils souhaitent envoyer les informations à leur organisation ou non.

L’activation/désactivation des contrôles de confidentialité ci-dessus n’aura pas d’impact sur la vérification de conformité de l’appareil ou l’accès conditionnel.


## <a name="configure-vulnerability-assessment-of-apps-for-byod-devices"></a>Configurer l’évaluation des vulnérabilités des applications pour les appareils BYOD

À partir de la version 1.0.3425.0303 de Microsoft Defender pour point de terminaison sur Android, vous serez en mesure d’exécuter des évaluations des vulnérabilités du système d’exploitation et des applications installées sur les appareils mobiles intégrés.

> [!NOTE]
> L’évaluation des vulnérabilités fait partie de [Gestion des vulnérabilités Microsoft Defender](../defender-vulnerability-management/defender-vulnerability-management.md) dans Microsoft Defender pour point de terminaison. 

**Remarques sur la confidentialité liée aux applications à partir d’appareils personnels (BYOD) :**

- Pour Android Entreprise avec un profil professionnel, seules les applications installées sur le profil professionnel sont prises en charge.
- Pour les autres modes BYOD, par défaut, l’évaluation des vulnérabilités des applications **n’est pas** activée. Toutefois, lorsque l’appareil est en mode administrateur, les administrateurs peuvent activer explicitement cette fonctionnalité via Microsoft Endpoint Manager pour obtenir la liste des applications installées sur l’appareil. Pour plus d’informations, consultez les détails ci-dessous.

### <a name="configure-privacy-for-device-administrator-mode"></a>Configurer la confidentialité pour le mode Administrateur de l’appareil

Procédez comme suit pour **activer l’évaluation des vulnérabilités des applications** à partir d’appareils en mode **administrateur d’appareil** pour les utilisateurs ciblés. 

> [!NOTE]
> Par défaut, cette option est désactivée pour les appareils inscrits en mode administrateur d’appareil.

1. Dans le [Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) , accédez à **Appareils** >  Profils  > **de configuration****Créer un profil** et entrez les paramètres suivants :

   - **Plateforme** : sélectionnez Administrateur d’appareil Android
   - **Profil** : sélectionnez « Personnalisé », puis cliquez sur Créer.

2. Dans la section **Informations de base** , spécifiez un nom et une description du profil.

3. Dans paramètres **de configuration**, sélectionnez Ajouter un paramètre **OMA-URI** :

   - **Nom** : entrez un nom et une description uniques pour ce paramètre OMA-URI afin de pouvoir le trouver facilement plus tard.
   - OMA-URI : **./Vendor/MSFT/DefenderATP/DefenderTVMPrivacyMode**
   - Type de données : sélectionnez Entier dans la liste déroulante.
   - Valeur : entrez 0 pour désactiver le paramètre de confidentialité (par défaut, la valeur est 1)

4. Cliquez sur **Suivant** et affectez ce profil aux appareils/utilisateurs ciblés.

### <a name="configure-privacy-for-android-enterprise-work-profile"></a>Configurer la confidentialité pour le profil professionnel Android Entreprise

Defender pour point de terminaison prend en charge l’évaluation des vulnérabilités des applications dans le profil professionnel. Toutefois, si vous souhaitez désactiver cette fonctionnalité pour les utilisateurs ciblés, vous pouvez effectuer les étapes suivantes :

1. Dans le [Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), accédez à **Applications Stratégies** >  de **configuration** >  des applications **Ajouter des** > **appareils gérés**.
2. Donnez un nom à la stratégie ; **Plateforme > Android Enterprise**; sélectionnez le type de profil.
3. Sélectionnez **Microsoft Defender pour point de terminaison** comme application cible.
4. Dans la page Paramètres, sélectionnez **Utiliser le concepteur de configuration** et ajoutez **DefenderTVMPrivacyMode** comme clé et type de valeur comme **Entier**
   - Pour désactiver la vulnérabilité des applications dans le profil professionnel, entrez la valeur et `1` affectez cette stratégie aux utilisateurs. Par défaut, cette valeur est définie sur `0`.
   - Pour les utilisateurs dont la clé est définie sur `0`, Defender pour point de terminaison envoie la liste des applications du profil professionnel au service principal pour l’évaluation des vulnérabilités.
5. Cliquez sur **Suivant** et affectez ce profil aux appareils/utilisateurs ciblés.

L’activation ou la désactivation des contrôles de confidentialité ci-dessus n’aura pas d’impact sur la vérification de conformité de l’appareil ou l’accès conditionnel.

## <a name="configure-privacy-for-phishing-alert-report"></a>Configurer la confidentialité pour le rapport d’alerte de hameçonnage

Le contrôle de confidentialité pour le rapport de hameçonnage peut être utilisé pour désactiver la collecte des informations de nom de domaine ou de site web dans le rapport de menaces de hameçonnage. Cela donne aux organisations la possibilité de choisir si elles souhaitent collecter le nom de domaine lorsqu’un site web malveillant ou malveillant est détecté et bloqué par Defender pour point de terminaison.

### <a name="configure-privacy-for-phishing-alert-report-on-android-device-administrator-enrolled-devices"></a>Configurez la confidentialité pour le rapport d’alerte de hameçonnage sur les appareils inscrits par l’administrateur d’appareil Android :

Procédez comme suit pour l’activer pour les utilisateurs ciblés :

1. Dans le [Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) , accédez à **Appareils** >  Profils  > **de configuration****Créer un profil** et entrez les paramètres suivants :

   - **Plateforme** : sélectionnez Administrateur d’appareil Android.
   - **Profil** : sélectionnez « Personnalisé », puis cliquez sur **Créer**.

2. Dans la section **Informations de base** , spécifiez un nom et une description du profil.

3. Dans paramètres **de configuration**, sélectionnez Ajouter un paramètre **OMA-URI** :

   - **Nom** : entrez un nom et une description uniques pour ce paramètre OMA-URI afin de pouvoir le trouver facilement plus tard.
   - OMA-URI : **./Vendor/MSFT/DefenderATP/DefenderExcludeURLInReport**
   - Type de données : sélectionnez Entier dans la liste déroulante.
   - Valeur : entrez 1 pour activer le paramètre de confidentialité. La valeur par défaut est 0.

4. Cliquez sur **Suivant** et affectez ce profil aux appareils/utilisateurs ciblés.

L’utilisation de ce contrôle de confidentialité n’aura pas d’impact sur la vérification de conformité de l’appareil ou l’accès conditionnel.

### <a name="configure-privacy-for-phishing-alert-report-on-android-enterprise-work-profile"></a>Configurer la confidentialité pour le rapport d’alerte de hameçonnage sur le profil professionnel Android Entreprise

Procédez comme suit pour activer la confidentialité pour les utilisateurs ciblés dans le profil professionnel :

1. Dans le [Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), accédez à **Applications Stratégies** >  de **configuration** >  des applications **Ajouter des** > **appareils gérés**.
2. Donnez un nom à la stratégie **, Plateforme > Android Enterprise**, sélectionnez le type de profil.
3. Sélectionnez **Microsoft Defender pour point de terminaison** comme application cible.
4. Dans la page Paramètres, sélectionnez **Utiliser le concepteur de configuration** et ajoutez **DefenderExcludeURLInReport** comme clé et type de **valeur entier.**
   - Entrez **1 pour activer la confidentialité**. La valeur par défaut est 0.
5. Cliquez sur **Suivant** et affectez ce profil aux appareils/utilisateurs ciblés.

L’activation ou la désactivation des contrôles de confidentialité ci-dessus n’aura pas d’impact sur la vérification de conformité de l’appareil ou l’accès conditionnel.

## <a name="configure-privacy-for-malware-threat-report"></a>Configurer la confidentialité pour le rapport sur les menaces de programmes malveillants

Le contrôle de confidentialité pour le rapport sur les menaces de programmes malveillants peut être utilisé pour désactiver la collecte des détails de l’application (informations sur le nom et le package) du rapport sur les menaces de programmes malveillants. Cela donne aux organisations la possibilité de choisir si elles souhaitent collecter le nom de l’application lorsqu’une application malveillante est détectée.

### <a name="configure-privacy-for-malware-alert-report-on-android-device-administrator-enrolled-devices"></a>Configurez la confidentialité pour le rapport d’alerte de programme malveillant sur les appareils inscrits par l’administrateur d’appareil Android :

Procédez comme suit pour l’activer pour les utilisateurs ciblés :

1. Dans le [Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) , accédez à **Appareils** >  Profils  > **de configuration****Créer un profil** et entrez les paramètres suivants :

   - **Plateforme** : sélectionnez Administrateur d’appareil Android.
   - **Profil** : sélectionnez « Personnalisé », puis cliquez sur **Créer**.

2. Dans la section **Informations de base** , spécifiez un nom et une description du profil.

3. Dans paramètres **de configuration**, sélectionnez Ajouter un paramètre **OMA-URI** :

   - **Nom** : entrez un nom et une description uniques pour ce paramètre OMA-URI afin de pouvoir le trouver facilement plus tard.
   - OMA-URI : **./Vendor/MSFT/DefenderATP/DefenderExcludeAppInReport**
   - Type de données : sélectionnez Entier dans la liste déroulante.
   - Valeur : entrez 1 pour activer le paramètre de confidentialité. La valeur par défaut est 0.

4. Cliquez sur **Suivant** et affectez ce profil aux appareils/utilisateurs ciblés.

L’utilisation de ce contrôle de confidentialité n’aura pas d’impact sur la vérification de conformité de l’appareil ou l’accès conditionnel. Par exemple, les appareils avec une application malveillante ont toujours un niveau de risque « Moyen ».

### <a name="configure-privacy-for-malware-alert-report-on-android-enterprise-work-profile"></a>Configurer la confidentialité pour le rapport d’alerte de programme malveillant sur le profil professionnel Android Entreprise

Procédez comme suit pour activer la confidentialité pour les utilisateurs ciblés dans le profil professionnel :

1. Dans le [Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), accédez à **Applications Stratégies** >  de **configuration** >  des applications **Ajouter des** > **appareils gérés**.
2. Donnez un nom à la stratégie **, Plateforme > Android Enterprise**, sélectionnez le type de profil.
3. Sélectionnez **Microsoft Defender pour point de terminaison** comme application cible.
4. Dans la page Paramètres, sélectionnez **Utiliser le concepteur de configuration** et ajoutez **DefenderExcludeAppInReport** comme clé et type de valeur comme **Entier**
   - Entrez **1 pour activer la confidentialité**. La valeur par défaut est 0.
5. Cliquez sur **Suivant** et affectez ce profil aux appareils/utilisateurs ciblés.

L’utilisation de ce contrôle de confidentialité n’aura pas d’impact sur la vérification de conformité de l’appareil ou l’accès conditionnel. Par exemple, les appareils avec une application malveillante ont toujours un niveau de risque « Moyen ».

## <a name="related-topics"></a>Voir aussi

- [Vue d’ensemble de Microsoft Defender pour point de terminaison Android](microsoft-defender-endpoint-android.md)
- [Déployer Microsoft Defender pour point de terminaison Android via Microsoft Intune](android-intune.md)
