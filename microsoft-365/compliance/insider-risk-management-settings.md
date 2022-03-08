---
title: Paramètres de gestion des risques internes
description: En savoir plus sur les paramètres de gestion des risques internes dans Microsoft 365
keywords: Microsoft 365, gestion des risques internes, gestion des risques, conformité
ms.localizationpriority: medium
ms.service: O365-seccomp
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection:
- m365-security-compliance
- m365solution-insiderrisk
- m365initiative-compliance
ms.custom: admindeeplinkCOMPLIANCE
ms.openlocfilehash: 62616ed20513ee023986525b4f097c96ae3107ba
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63330606"
---
# <a name="get-started-with-insider-risk-management-settings"></a>Prise en charge des paramètres de gestion des risques internes

Les paramètres de gestion des risques internes s’appliquent à toutes les stratégies de gestion des risques internes, quel que soit le modèle que vous choisissez lors de la création d’une stratégie. Paramètres sont configurés à l’aide du contrôle des **paramètres** des risques internes situé en haut de toutes les pages de gestion des risques internes. Ces paramètres contrôlent les composants de stratégie pour les domaines suivants :

- Confidentialité
- Indicateurs
- Chronologies des stratégies
- Détections intelligentes
- Exporter des alertes
- Groupes d’utilisateurs prioritaires (aperçu)
- Ressources physiques prioritaires (prévisualisation)
- Power Automate flux de données (prévisualisation)
- Microsoft Teams (aperçu)
- Analyse

Avant de commencer et de créer des stratégies de gestion des risques internes, il est important de comprendre ces paramètres et de choisir les niveaux de configuration les mieux conformes aux besoins de conformité de votre organisation.

## <a name="privacy"></a>Confidentialité

La protection de la confidentialité des utilisateurs disposant de correspondances de stratégie est importante et peut favoriser l'objectivité dans les examens et analyses de données pour les alertes de risque internes. Pour les utilisateurs avec une correspondance de stratégie de risque interne, vous pouvez choisir l’un des paramètres suivants :

- **Afficher les versions anonymisées** des noms d’utilisateur : les noms des utilisateurs sont rendus anonymes pour empêcher les administrateurs, les enquêteurs de données et les réviseurs de voir qui est associé aux alertes de stratégie. Par exemple, un utilisateur « Grace à Taylor » apparaît avec un pseudonyme aléatoire tel que « AnonIS8-988 » dans toutes les zones de l’expérience de gestion des risques internes. Le choix de ce paramètre permet d'anonymiser tous les utilisateurs ayant des correspondances de stratégie actuelle et passée et s’applique à toutes les stratégies. Les informations de profil utilisateur dans l’alerte de risque interne et les détails du cas ne seront pas disponibles lorsque cette option sera choisie. Toutefois, les noms d’utilisateur s’affichent lors de l’ajout de nouveaux utilisateurs à des stratégies existantes ou lors de l’affectation d’utilisateurs à de nouvelles stratégies. Si vous choisissez de désactiver ce paramètre, les noms d’utilisateur s’affichent pour tous les utilisateurs qui ont des correspondances de stratégie actuelles ou passées.

    >[!IMPORTANT]
    >Pour maintenir l’intégrité référence pour les utilisateurs qui ont des alertes ou des cas de risque internes dans Microsoft 365 ou d’autres systèmes, l’anonymisation des noms d’utilisateurs n’est pas conservée pour les alertes exportées. Les alertes exportées affichent les noms d’utilisateur de chaque alerte.

- **N’affichez pas les versions rendues anonymes** des noms d’utilisateur : les noms d’utilisateur sont affichés pour toutes les correspondances de stratégie actuelles et passées pour les alertes et les cas. Les informations de profil utilisateur (nom, titre, alias et organisation ou service) s’affichent pour l’utilisateur pour tous les cas et alertes de gestion des risques internes.

![Paramètres de confidentialité de la gestion des risques internes.](../media/insider-risk-settings-privacy.png)

## <a name="indicators"></a>Indicateurs

Les modèles de stratégie de risque interne définissent le type d’activités de risque que vous souhaitez détecter et examiner. Chaque modèle de stratégie est basé sur des indicateurs spécifiques qui correspondent à des déclencheurs et des activités de risque spécifiques. Tous les indicateurs sont désactivés par défaut et vous devez sélectionner un ou plusieurs indicateurs de stratégie avant de configurer une stratégie de gestion des risques internes.

Les alertes sont déclenchées par des stratégies lorsque les utilisateurs effectuent des activités liées à des indicateurs de stratégie qui répondent à un seuil requis. La gestion des risques internes utilise deux types d’indicateurs :

- **Déclenchement d’événements** : événements qui déterminent si un utilisateur est actif dans une stratégie de gestion des risques internes. Si un utilisateur est ajouté à une stratégie de gestion des risques internes n’a pas d’événement déclencheur, l’activité de l’utilisateur n’est pas évaluée par la stratégie. Par exemple, l’utilisateur A est ajouté à une stratégie créée à  partir du vol de données en dévolant au modèle de stratégie des utilisateurs et la stratégie et le connecteur rh Microsoft 365 sont correctement configurés. Tant que l’utilisateur A n’a pas de date de résiliation signalée par le connecteur RH, les activités de l’utilisateur A ne sont pas évaluées par cette stratégie de gestion des risques internes pour les risques. Un autre exemple d’événement déclencheur est si un utilisateur a une  alerte de stratégie DLP de gravité élevée lors de l’utilisation de *stratégies de fuite de* données.
- **Indicateurs de stratégie :** indicateurs inclus dans les stratégies de gestion des risques internes utilisées pour déterminer un score de risque pour un utilisateur dans l’étendue. Ces indicateurs de stratégie sont activés uniquement après qu’un événement déclencheur s’est produit pour un utilisateur. Voici quelques exemples d’indicateurs de stratégie lorsqu’un utilisateur copie des données vers des services de stockage cloud personnels ou des périphériques de stockage portables, si un compte d’utilisateur est supprimé de Azure Active Directory ou si un utilisateur partage des fichiers et dossiers internes avec des parties externes non autorisées.

Certains indicateurs de stratégie peuvent également être utilisés pour personnaliser des événements de déclenchement pour des modèles de stratégie spécifiques. Lorsqu’ils sont configurés dans l’Assistant Stratégie pour les *fuites de données générales* ou les fuites de données par modèles d’utilisateurs prioritaires, ces indicateurs vous offrent plus de flexibilité et de personnalisation pour vos stratégies et lorsque les *utilisateurs* sont dans l’étendue d’une stratégie. En outre, vous pouvez définir des seuils d’activité individuels pour ces indicateurs de déclenchement pour un contrôle plus fin dans une stratégie.

Les indicateurs de stratégie sont segmentés dans les zones suivantes. Vous pouvez choisir les indicateurs à activer et personnaliser les limites des événements d’indicateurs pour chaque niveau d’indicateur lors de la création d’une stratégie de risque interne :

- **Office suivants** : il s’agit notamment d’indicateurs de stratégie pour SharePoint sites, Microsoft Teams et la messagerie électronique.
- **Indicateurs d’appareil** : il s’agit notamment d’indicateurs de stratégie pour les activités telles que le partage de fichiers sur le réseau ou avec des appareils. Les indicateurs incluent les activités impliquant tous les types de fichiers, à l’exception de l’activité des fichiers exécutables (.exe) et des bibliothèques de liens dynamiques (.dll). Si vous sélectionnez Indicateurs d’appareil *,* l’activité est traitée pour les appareils avec Windows 10 Build 1809 ou ultérieure et les appareils macOS (État 10.15 ou ultérieur). Pour les Windows et macOS, vous devez d’abord intégrer les appareils au centre de conformité. Les indicateurs de périphérique incluent également la détection du signal du navigateur pour aider votre organisation à détecter et à agir sur les signaux d’exfiltration pour les fichiers non exécutables qui sont consultables, copiés, partagés ou imprimés dans Microsoft Edge et Google Chrome. Pour plus d’informations sur la configuration des Windows pour l’intégration aux risques internes, consultez la section Activer les indicateurs d’appareil et intégrer Windows [appareils](insider-risk-management-settings.md#OnboardDevices) dans cet article. Pour plus d’informations sur la configuration des appareils macOS pour l’intégration aux risques internes, voir la section Activer les indicateurs d’appareil et les appareils macOS intégrés dans cet article. Pour plus d’informations sur la détection du signal du navigateur, voir [Découvrir et configurer](insider-risk-management-browser-support.md) la détection du signal du navigateur de gestion des risques internes.
- **Indicateur de violation** de la stratégie de sécurité (prévisualisation) : il s’agit des indicateurs de Microsoft Defender pour le point de terminaison liés à l’installation de logiciels non désapprouvés ou malveillants ou au contournement des contrôles de sécurité. Pour recevoir des alertes dans la gestion des risques internes, vous devez avoir activé une licence Active Defender for Endpoint et l’intégration des risques internes. Pour plus d’informations sur la configuration de Defender pour Endpoint pour l’intégration de la gestion des risques internes, voir Configurer des fonctionnalités avancées [dans Microsoft Defender pour Endpoint](/windows/security/threat-protection/microsoft-defender-atp/advanced-features\#share-endpoint-alerts-with-microsoft-compliance-center).
- **Indicateurs d’accès aux dossiers médicaux (prévisualisation)** : il s’agit des indicateurs de stratégie pour l’accès aux dossiers médicaux du patient. Par exemple, les tentatives d’accès aux dossiers médicaux des patients dans les journaux de votre système emr peuvent être partagées avec les stratégies de santé de gestion des risques internes. Pour recevoir ces types d’alertes dans la gestion des risques internes, vous devez avoir configuré un connecteur de données spécifiques à la santé et le connecteur de données RH.
- **Indicateurs d’accès physique (aperçu)** : il s’agit des indicateurs de stratégie pour l’accès physique aux biens sensibles. Par exemple, les tentatives d’accès à une zone restreinte dans les journaux de votre système de gestion des risques internes peuvent être partagées avec les stratégies de gestion des risques internes. Pour recevoir ces types d’alertes dans la gestion des risques internes, les ressources physiques prioritaires doivent être activées dans la gestion des risques internes et le connecteur de données de mauvaise [gestion physique configuré](import-physical-badging-data.md) . Pour en savoir plus sur la configuration de l’accès physique, consultez la [section Accès physique prioritaire](#priority-physical-assets-preview) dans cet article.
- **Indicateurs Microsoft Defender pour les applications cloud (prévisualisation)** : il s’agit des indicateurs de stratégie provenant d’alertes partagées de Defender pour les applications cloud. La détection des anomalies activée automatiquement dans Defender pour les applications cloud commence immédiatement à détecter et à rassembler les résultats, en ciblant de nombreuses anomalies comportementales au sein de vos utilisateurs et des ordinateurs et périphériques connectés à votre réseau. Pour inclure ces activités dans les alertes de stratégie de gestion des risques internes, sélectionnez un ou plusieurs indicateurs dans cette section. Pour en savoir plus sur l’analyse de Defender for Cloud Apps et la détection des anomalies, voir [Obtenir l’analyse comportementale et la détection des anomalies](/cloud-app-security/anomaly-detection-policy).
- Score de risque : il s’agit notamment d’augmenter le score de risque pour l’activité supérieure à l’activité habituelle de l’utilisateur pour une journée ou pour les **utilisateurs** dont les cas précédents ont été résolus comme une violation de stratégie. L’activation des score de risque augmente les scores de risque et la probabilité d’alertes pour ces types d’activités. Pour les activités supérieures à l’activité habituelle de l’utilisateur pendant une journée, les scores sont élevés si l’activité détectée dévie du comportement classique de l’utilisateur. Pour les utilisateurs dont les cas précédents ont été résolus en tant que violation de stratégie, les scores sont élevés si un utilisateur a précédemment résolu plusieurs cas en tant que violation de stratégie confirmée. Les score de risque ne peuvent être sélectionnés que si un ou plusieurs indicateurs sont sélectionnés.

Dans certains cas, vous pouvez limiter les indicateurs de stratégie de risque interne qui sont appliqués aux stratégies de risques internes dans votre organisation. Vous pouvez désactiver les indicateurs de stratégie pour des zones spécifiques en les désactivant de toutes les stratégies de risque internes. Le déclenchement d’événements ne peut être modifié que pour les *stratégies créées* à partir des fuites de données *générales ou des fuites de données par des modèles* d’utilisateurs prioritaires. Les stratégies créées à partir de tous les autres modèles n’ont pas d’indicateurs ou d’événements déclencheurs personnalisables.

Pour définir les indicateurs de stratégie de risque internes activés dans toutes les stratégies de risque internes, accédez à **Paramètres** >  des risques **internesIndicateurs** et sélectionnez un ou plusieurs indicateurs de stratégie. Les indicateurs sélectionnés dans la page Paramètres des indicateurs ne peuvent pas être configurés individuellement lors de la création ou de la modification d’une stratégie de risque interne dans l’Assistant Stratégie.

> [!NOTE]
> L’affichage des nouveaux utilisateurs ajoutés manuellement dans le tableau de bord Utilisateurs peut prendre plusieurs **heures**. L’affichage des activités des 90 jours précédents de ces utilisateurs peut prendre jusqu’à 24 heures. Pour afficher les activités des utilisateurs ajoutés manuellement, sélectionnez l’utilisateur dans le tableau de  bord Utilisateurs et ouvrez l’onglet Activité de l’utilisateur dans le volet d’informations.

### <a name="enable-device-indicators-and-onboard-windows-devices"></a>Activer les indicateurs d’appareil et les appareils Windows intégrés
<a name="OnboardDevices"> </a>

Pour activer la surveillance des activités de risque sur les appareils Windows et inclure des indicateurs de stratégie pour ces activités, vos appareils Windows doivent répondre aux exigences suivantes et vous devez effectuer les étapes d’intégration suivantes.

#### <a name="step-1-prepare-your-endpoints"></a>Étape 1 : Préparer vos points de terminaison

Assurez-vous que les Windows 10 que vous prévoyez de signaler dans la gestion des risques internes répondent à ces exigences.

1. Doit être en cours d’exécution Windows 10 x64 build 1809 ou ultérieure et avoir installé la mise à jour [Windows 10 (os Build 17763.1075)](https://support.microsoft.com/help/4537818/windows-10-update-kb4537818) à partir du 20 février 2020.
2. Le compte d’utilisateur utilisé pour se connecter à Windows 10 appareil doit être un compte Azure Active Directory (AAD) actif. L Windows 10 appareil peut être [AAD, un](/azure/active-directory/devices/concept-azure-ad-join) AAD hybride ou joint à Active Directory ou être AAD enregistré.
3. Installez le navigateur Microsoft Edge sur l’appareil de point de terminaison pour surveiller les actions de l’activité de chargement dans le cloud. [Télécharger le nouveau Microsoft Edge sur la base de chrome](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium).

#### <a name="step-2-onboarding-devices"></a>Étape 2 : Intégration d’appareils
<a name="OnboardStep2"> </a>

Vous devez activer la surveillance des appareils et intégrer vos points de terminaison avant de pouvoir surveiller les activités de gestion des risques internes sur un appareil. Les deux actions sont prises dans le portail Microsoft 365 conformité.

Lorsque vous souhaitez intégrer des appareils qui n’ont pas encore été intégrés, vous devez télécharger le script approprié et le déployer comme indiqué dans les étapes suivantes.

Si vous avez déjà des appareils intégrés à [Microsoft Defender pour le](/windows/security/threat-protection/) point de terminaison, ils apparaissent déjà dans la liste des appareils gérés. Suivez [l’étape 3 : si vous avez des appareils intégrés à Microsoft Defender pour endpoint](insider-risk-management-settings.md#OnboardStep3) dans la section suivante.

Dans ce scénario de déploiement, vous allez intégrer des appareils qui n’ont pas encore été intégrés et vous souhaitez simplement surveiller les activités de risque internes sur Windows 10 appareils.

1. Ouvrez le [Centre de conformité Microsoft 365](https://compliance.microsoft.com).
2. Ouvrez la page Paramètres du centre de conformité et sélectionnez **Appareils intégrés**.

   > [!NOTE]
   > Bien que l’activation de l’intégration des appareils dure généralement environ 60 secondes, patientez jusqu’à 30 minutes avant de contacter le support Microsoft.

3. Sélectionnez **Gestion des appareils** pour ouvrir la liste des **Appareils**. La liste est vide tant que vous n’avez pas intégré de périphériques.
4. Sélectionnez **Intégration** pour lancer le processus d’intégration.
5. Choisissez la façon dont vous souhaitez déployer ces autres appareils dans la liste des méthodes **de déploiement,** puis **téléchargez le package**.
6. Suivez les procédures appropriées dans [Outils et méthodes d’intégration pour les ordinateurs Windows 10](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints). Ce lien vous dirige vers une page d’accueil dans laquelle vous pouvez accéder aux procédures Microsoft Defender pour point de terminaison qui correspondent au package de déploiement que vous avez sélectionné à l’étape 5 :
    - Intégrer les ordinateurs Windows 10 utilisant une stratégie de groupe
    - Intégrer les ordinateurs Windows à l’aide du gestionnaire de configuration de point de terminaison Microsoft
    - Intégrer les ordinateurs Windows 10 à l’aide des outils de gestion des appareils mobiles
    - Intégrer les ordinateurs Windows 10 utilisant un script local
    - Intégrer les ordinateurs virtuels d’infrastructure de bureau virtuel (VDI) non persistants.

Une fois terminé et le point de terminaison intégré, il doit être visible dans la liste des appareils et le point de terminaison commence à signaler les journaux d’activité d’audit à la gestion des risques internes.

> [!NOTE]
> Cette expérience est sous l’application de la licence. Sans la licence requise, les données ne sont pas visibles ni accessibles.

#### <a name="step-3-if-you-have-devices-onboarded-into-microsoft-defender-for-endpoint"></a>Étape 3 : Si vous avez des appareils intégrés à Microsoft Defender pour le point de terminaison
<a name="OnboardStep3"> </a>

Si Microsoft Defender pour le point de terminaison est déjà déployé et que des points de terminaison sont connectés, tous ces points de terminaison apparaissent dans la liste des appareils gérés. Vous pouvez continuer à intégrer de nouveaux appareils dans la gestion des risques internes pour étendre la couverture à l’aide de la section [Étape 2 : Intégration des appareils](insider-risk-management-settings.md#OnboardStep2) .

1. Ouvrez le [Centre de conformité Microsoft 365](https://compliance.microsoft.com).
2. Ouvrez la page Paramètres du centre de conformité et sélectionnez **Activer la surveillance d’appareils**.
3. Sélectionnez **Gestion des appareils** pour ouvrir la liste des **Appareils**. Vous devriez voir la liste des appareils qui sont déjà signalés dans Microsoft Defender pour le point de terminaison.
4. Choisissez **l’intégration** si vous avez besoin d’intégrer davantage d’appareils.
5. Choisissez la façon dont vous souhaitez déployer ces autres appareils dans la liste des méthodes **de déploiement,** puis **téléchargez le package**.
6. Suivez les procédures appropriées dans [Outils et méthodes d’intégration pour les ordinateurs Windows 10](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints). Ce lien vous dirige vers une page d’accueil dans laquelle vous pouvez accéder aux procédures Microsoft Defender pour point de terminaison qui correspondent au package de déploiement que vous avez sélectionné à l’étape 5 :
    - Intégrer les ordinateurs Windows 10 utilisant une stratégie de groupe
    - Intégrer les ordinateurs Windows à l’aide du gestionnaire de configuration de point de terminaison Microsoft
    - Intégrer les ordinateurs Windows 10 à l’aide des outils de gestion des appareils mobiles
    - Intégrer les ordinateurs Windows 10 utilisant un script local
    - Intégrer les ordinateurs virtuels d’infrastructure de bureau virtuel (VDI) non persistants.

Une fois terminé et le point de terminaison intégré, il doit être visible sous la table **Appareils** et le point de terminaison commence à signaler les journaux d’activité d’audit à la gestion des risques internes.

> [!NOTE]
>Cette expérience est sous l’application de la licence. Sans la licence requise, les données ne sont pas visibles ni accessibles.

### <a name="enable-device-indicators-and-onboard-macos-devices"></a>Activer les indicateurs d’appareil et les appareils macOS intégrés

Les appareils macOS (Contrôle 10.15 ou ultérieur) peuvent être intégrés à Microsoft 365 pour prendre en charge les stratégies de gestion des risques internes à l’aide d’Intune ou de JAMF Pro. Pour plus d’informations et des conseils de configuration, voir Intégrer des appareils [macOS Microsoft 365 vue d’ensemble (prévisualisation).](device-onboarding-macos-overview.md)

### <a name="indicator-level-settings-preview"></a>Paramètres de niveau indicateur (aperçu)

Lorsque vous créez une stratégie dans l’Assistant Stratégie, vous pouvez configurer la façon dont le nombre quotidien d’événements de risque doit influencer le score de risque pour les alertes de risque internes. Ces paramètres d’indicateur vous aident à contrôler la façon dont le nombre d’occurrences d’événements de risque dans votre organisation doit affecter le score de risque, ainsi que la gravité de l’alerte associée, pour ces événements. Si vous préférez, vous pouvez également choisir de conserver les niveaux de seuil d’événement par défaut recommandés par Microsoft pour tous les indicateurs activés.

Par exemple, vous décidez d’activer les indicateurs SharePoint dans les paramètres de stratégie de risque interne et de définir des seuils personnalisés pour les événements SharePoint lors de la configuration d’indicateurs  pour une nouvelle stratégie de fuites de données de risques internes. Dans l’Assistant Stratégie de risque interne, vous configurez trois niveaux d’événements quotidiens différents pour chaque indicateur SharePoint afin d’influencer le score de risque pour les alertes associées à ces événements.

![Paramètres d’indicateurs personnalisés de gestion des risques internes.](../media/insider-risk-custom-indicators.png)

Pour le premier niveau d’événement quotidien, vous définissez le seuil à *10* événements ou plus par jour pour un impact inférieur sur le score de risque pour les événements, *20* événements ou plus par jour pour un impact moyen sur le score de risque pour les événements et *30* événements ou plus par jour un impact plus élevé sur le score de risque pour les événements. Ces paramètres signifient effectivement :

- Si 1 à 9 événements de SharePoint ont lieu après le déclenchement de l’événement, les scores de risque sont peu touchés et ont tendance à ne pas générer d’alerte.
- Si 10 à 19 événements SharePoint ont lieu après un événement déclencheur, le score de risque est intrinsèquement inférieur et les niveaux de gravité des alertes tendront à être à un niveau faible.
- Si 20 à 29 événements SharePoint ont lieu après un déclenchement, le score de risque est intrinsèquement plus élevé et les niveaux de gravité des alertes ont tendance à se trouver à un niveau moyen.
- Si au moins 30 événements SharePoint ont lieu après un déclenchement, le score de risque est intrinsèquement plus élevé et les niveaux de gravité des alertes ont tendance à se trouver à un niveau élevé.

## <a name="policy-timeframes"></a>Délais de la stratégie

Les délais de stratégie vous permettent de définir les périodes passées et futures qui sont déclenchées après les correspondances de stratégie basées sur les événements et les activités des modèles de stratégie de gestion des risques internes. En fonction du modèle de stratégie que vous choisissez, les délais de stratégie suivants sont disponibles :

- **Fenêtre d’activation** : disponible pour tous les modèles de stratégie, la fenêtre *Activation* est le nombre défini de jours d’activation de la fenêtre **après un événement** déclencheur. La fenêtre s’active pendant 1 à 30 jours après qu’un événement déclencheur se produit pour tout utilisateur affecté à la stratégie. Par exemple, vous avez configuré une stratégie de gestion des risques internes et définissez la fenêtre *d’activation* sur 30 jours. Plusieurs mois se sont écoulés depuis la configuration de la stratégie et un événement déclencheur se produit pour l’un des utilisateurs inclus dans la stratégie. L’événement déclencheur active la fenêtre *Activation* et la stratégie est active pour cet utilisateur pendant 30 jours après que l’événement déclencheur s’est produit.
- **Détection des activités passées** : disponible pour tous les modèles  de stratégie, la détection d’activité passée est le nombre défini de  jours d’activation de la fenêtre avant un événement déclencheur. La fenêtre s’active pendant 0 à 90 jours avant qu’un événement déclencheur ne se produise pour tout utilisateur affecté à la stratégie. Par exemple, vous avez configuré une stratégie de gestion des risques internes et définissez la détection des activités *passées* sur 90 jours. Plusieurs mois se sont écoulés depuis la configuration de la stratégie et un événement déclencheur se produit pour l’un des utilisateurs inclus dans la stratégie. L’événement déclencheur active la détection  de l’activité passée et la stratégie collecte les activités historiques de cet utilisateur pendant 90 jours avant l’événement déclencheur.

![Paramètres de délai de gestion des risques internes.](../media/insider-risk-settings-timeframes.png)

## <a name="intelligent-detections"></a>Détections intelligentes

Les paramètres de détection intelligent permettent d’affiner la façon dont les détections des activités à risque sont traitées pour les alertes. Dans certains cas, vous devrez peut-être définir des types de fichiers à ignorer ou appliquer un niveau de détection pour les événements quotidiens afin d’améliorer les scores de risque pour les utilisateurs. Utilisez ces paramètres pour contrôler les exclusions de types de fichiers, l’augmentation du score de risque pour les activités inhabituelles et les limites de volume de fichiers.

### <a name="file-type-exclusions"></a>Exclusions de types de fichiers

Pour exclure des types de fichiers spécifiques de toutes les correspondances de stratégie de gestion des risques internes, entrez des extensions de type de fichier séparées par des virgules. Par exemple, pour exclure certains types de fichiers musicaux des correspondances de stratégie, vous pouvez entrer *aac,mp3,wav,wma* dans le champ **exclusions de type de fichier**. Les fichiers avec ces extensions seront ignorés par toutes les stratégies de gestion des risques internes.

### <a name="minimum-number-of-daily-events-to-boost-score-for-unusual-activity"></a>Nombre minimal d’événements quotidiens pour améliorer le score d’activité inhabituelle

Avec ce paramètre, vous définissez le nombre d’événements quotidiens requis pour augmenter le score de risque pour une activité considérée comme inhabituelle pour un utilisateur. Par exemple, supposons que vous en entrez 25 pour ce groupe de risques. Si un utilisateur a en moyenne 10 téléchargements de fichiers au cours des 30 derniers jours, mais qu’une stratégie détecte qu’il a téléchargé 20 fichiers un jour, le score de cette activité n’est pas accru même s’il est inhabituel pour cet utilisateur, car le nombre de fichiers téléchargés ce jour-là est inférieur au nombre que vous avez entré pour ce groupe de risques.

### <a name="alert-volume"></a>Volume d’alerte

Les activités des utilisateurs détectées par les stratégies de risque internes se voit attribuer un score de risque spécifique, qui à son tour détermine la gravité de l’alerte (faible, moyenne, élevée). Par défaut, nous allons générer une certaine quantité d’alertes de gravité faible, moyenne et élevée, mais vous pouvez augmenter ou diminuer le volume en fonction de vos besoins. Pour ajuster le volume des alertes pour toutes les stratégies de gestion des risques internes, choisissez l’un des paramètres suivants :

- **Moins d’alertes** : vous verrez toutes les alertes de gravité élevée, moins d’alertes de gravité moyenne et aucune alerte de faible gravité. Ce niveau de paramètre signifie que vous pouvez manquer certains vrais positifs.
- **Volume par défaut** : vous verrez toutes les alertes de gravité élevée et une quantité équilibrée d’alertes de gravité moyenne et faible.
- **Plus d’alertes** : vous verrez toutes les alertes de gravité moyenne et élevée, ainsi que la plupart des alertes de faible gravité. Ce niveau de paramètre peut entraîner davantage de faux positifs.

### <a name="microsoft-defender-for-endpoint-preview"></a>Microsoft Defender pour point de terminaison (prévisualisation)

[Microsoft Defender pour point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) est une plateforme de sécurité de point de terminaison d’entreprise conçue pour aider les réseaux d’entreprise à prévenir, détecter, examiner et répondre aux menaces avancées. Pour avoir une meilleure visibilité des violations de sécurité dans votre organisation, vous pouvez importer et filtrer les alertes Defender for Endpoint pour les activités utilisées dans les stratégies créées à partir de modèles de stratégie de violation de sécurité de gestion des risques internes.

Selon les types de signaux qui vous intéressent, vous pouvez choisir d’importer des alertes dans la gestion des risques internes en fonction de l’état de triage des alertes Defender for Endpoint. Vous pouvez définir un ou plusieurs des états de tri d’alerte suivants dans les paramètres globaux à importer :

- Inconnu
- Nouveau
- En cours
- Résolu

Les alertes de Defender for Endpoint sont importées quotidiennement. En fonction de l’état de tri que vous choisissez, vous pouvez voir plusieurs activités utilisateur pour la même alerte lorsque l’état de triage change dans Defender pour le point de terminaison.

Par exemple, si vous sélectionnez *Nouveau, En* cours et  Résolu pour ce paramètre, lorsqu’une alerte Microsoft Defender pour le point de terminaison est générée et que l’état est *Nouveau, une* activité d’alerte initiale est importée pour l’utilisateur en cas de risque interne. Lorsque l’état de triage Defender pour le point de terminaison passe à En *cours*, une deuxième activité pour cette alerte est importée pour l’utilisateur en cas de risque interne. Lorsque l’état de triage Final Defender pour le  point de terminaison est résolu, une troisième activité de cette alerte est importée pour l’utilisateur en cas de risque interne. Cette fonctionnalité permet aux enquêteurs de suivre la progression des alertes defender pour point de terminaison et de choisir le niveau de visibilité nécessaire à leur examen.

> [!IMPORTANT]
> Microsoft Defender pour point de terminaison doit être configuré dans votre organisation et vous devez activer Microsoft Defender pour point de terminaison pour l’intégration de la gestion des risques internes dans le Centre de sécurité Microsoft Defender pour importer les alertes de violation de la sécurité. Pour plus d’informations sur la configuration de Microsoft Defender pour point de terminaison pour l’intégration de la gestion des risques internes, consultez [Configurer des fonctionnalités avancées dans Defender pour le point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/advanced-features\#share-endpoint-alerts-with-microsoft-compliance-center).

### <a name="domains"></a>Domaines

Les paramètres de domaine vous aident à définir des niveaux de risque pour les activités sur des domaines spécifiques. Ces activités incluent le partage de fichiers, l’envoi de messages électroniques, le téléchargement ou le téléchargement de contenu. En spécifiant des domaines dans ces paramètres, vous pouvez augmenter ou diminuer le score de risque pour l’activité qui a lieu avec ces domaines.

Utilisez Ajouter un domaine pour définir un domaine pour chacun des paramètres de domaine. En outre, vous pouvez utiliser des caractères génériques pour vous aider à trouver des variantes de domaines racines ou de sous-domaines. Par exemple, pour spécifier sales.wingtiptoys.com et support.wingtiptoys.com, utilisez l’entrée générique « *.wingtiptoys.com » pour faire correspondre ces sous-domaine (et tout autre sous-domaine du même niveau). Pour spécifier des sous-domaines à plusieurs niveaux pour un domaine racine, vous devez cocher la case Inclure les **sous-domaines** à plusieurs niveaux.

Pour chacun des paramètres de domaine suivants, vous pouvez entrer jusqu’à 500 domaines :

- **Domaines nonallés :** En spécifiant des domaines nonallés, l’activité qui a lieu avec ces domaines aura des *scores* de risque plus élevés. Voici quelques exemples d’activités impliquant le partage de contenu avec quelqu’un (par exemple, l’envoi de courriers électroniques à une personne avec une adresse gmail.com) et lorsque les utilisateurs téléchargent du contenu sur un appareil à partir de l’un de ces domaines nonallés.
- **Domaines autorisés :** Certaines activités liées aux domaines autorisés sont ignorées par vos stratégies et ne génèrent pas d’alertes. Ces activités sont les suivantes :

    - Courrier électronique envoyé à des domaines externes
    - Fichiers, dossiers, sites partagés avec des domaines externes
    - Fichiers téléchargés vers des domaines externes (à l’aide Microsoft Edge navigateur)

    En spécifiant les domaines autorisés dans les paramètres, cette activité avec ces domaines est traitée de la même manière que l’activité interne de l’organisation. Par exemple, les domaines ajoutés ici méritent à des activités peuvent impliquer le partage de contenu avec une personne extérieure à votre organisation (par exemple, l’envoi de courriers électroniques à une personne avec gmail.com adresse).

- **Domaines tiers :** Si votre organisation utilise des domaines tiers à des fins professionnelles (telles que le stockage cloud), *incluez-les* ici pour recevoir des alertes d’activité liées à l’indicateur d’appareil Utilisez un navigateur pour télécharger du contenu à partir d’un site tiers.

## <a name="export-alerts"></a>Exporter des alertes

Les informations sur les alertes de gestion des risques internes peuvent être exportées vers des solutions DE réponse automatisée d’orchestration de sécurité et d’orchestration de la sécurité (SIEM) à l’aide du schéma [de l’API activité](/office/office-365-management-api/office-365-management-activity-api-schema#security-and-compliance-alerts-schema) de gestion Office 365. Vous pouvez utiliser les API activité de gestion Office 365 pour exporter des informations d’alerte vers d’autres applications que votre organisation peut utiliser pour gérer ou regrouper des informations sur les risques internes. Les informations d’alerte sont exportées et disponibles toutes les 60 minutes via Office 365 API Activité de gestion.

Si votre organisation utilise Microsoft Sentinel, vous pouvez également utiliser le connecteur de données de gestion des risques internes out-of-the-box pour importer des informations d’alerte de risque interne dans Sentinel. Pour plus d’informations, [voir Microsoft 365 Insider Risk Management (IRM) (Preview)](/azure/sentinel/data-connectors-reference#microsoft-365-insider-risk-management-irm-preview) dans l’article Microsoft Sentinel.

>[!IMPORTANT]
>Pour maintenir l’intégrité référence pour les utilisateurs qui ont des alertes ou des cas de risque internes dans Microsoft 365 ou d’autres systèmes, l’anonymisation des noms d’utilisateurs n’est pas conservée pour les alertes exportées. Les alertes exportées affichent les noms d’utilisateur de chaque alerte.

Pour utiliser les API pour passer en revue les informations d’alerte de risque interne :

1. Activez Office 365 prise en charge de l’API  >  Activité de gestion des données dans la gestion des risques internes **Paramètres** >  **Exporter les alertes**. Par défaut, ce paramètre est désactivé pour votre Microsoft 365 organisation.
2. Filtrez les activités d Office 365 audit courantes par *SecurityComplianceAlerts*.
3. *Filtrez SecurityComplianceAlerts par* catégorie *InsiderRiskManagement*.

![Paramètres d’alerte d’exportation de gestion des risques internes.](../media/insider-risk-settings-export.png)

Les informations d’alerte contiennent des informations provenant du schéma d’alerte de sécurité et de conformité et du schéma commun Office 365'API Activité de gestion.

Les champs et valeurs suivants sont exportés pour les alertes de gestion des risques internes pour le schéma d’alerte de sécurité & conformité :

| **Paramètre d’alerte** | **Description** |
|:------------------|:----------------|
| AlertType | Le type de l’alerte est *Personnalisé*.  |
| AlertId | GUID de l’alerte. Les alertes de gestion des risques internes sont mutables. À mesure que l’état de l’alerte change, un nouveau journal avec le même ID d’alerte est généré. Ce AlertID peut être utilisé pour corréler les mises à jour d’une alerte. |
| Catégorie | La catégorie de l’alerte *est InsiderRiskManagement*. Cette catégorie peut être utilisée pour distinguer ces alertes des autres alertes de sécurité & conformité. |
| Commentaires | Commentaires par défaut pour l’alerte. Les valeurs *sont Nouvelle* alerte (consignée lors de la création d’une alerte) et Alerte mise à *jour (* consignée lorsqu’une alerte est mise à jour). Utilisez alertID pour corréler les mises à jour d’une alerte. |
| Données | Les données de l’alerte incluent l’ID d’utilisateur unique, le nom d’utilisateur principal et la date et l’heure (UTC) à laquelle l’utilisateur a été déclenché dans une stratégie. |
| Nom | Nom de la stratégie de gestion des risques internes qui a généré l’alerte. |
| PolicyId | GUID de la stratégie de gestion des risques internes qui a déclenché l’alerte. |
| Severity | Gravité de l’alerte. Les valeurs *sont Élevée*, *Moyenne* ou *Faible*. |
| Source | Source de l’alerte. La valeur est Office 365 *security & compliance*. |
| Statut | État de l’alerte. Les valeurs sont *actives* *(révision* nécessaire en cas de risque *interne), Examen* *(confirmé* dans le risque interne), *Résolu* *(résolu* en cas de risque *interne), Rejeté* *(rejeté* dans le risque interne). |
| Version | Version du schéma d’alerte de sécurité et de conformité. |

Les champs et valeurs suivants sont exportés pour les alertes de gestion des risques internes pour le schéma commun de [l’API Activité Office 365 gestion des informations](/office/office-365-management-api/office-365-management-activity-api-schema#common-schema).

- UserId
- ID
- RecordType
- CreationTime
- Opération
- OrganizationId
- UserType
- UserKey

## <a name="priority-user-groups-preview"></a>Groupes d’utilisateurs prioritaires (aperçu)

Les utilisateurs de votre organisation peuvent avoir différents niveaux de risque en fonction de leur position, du niveau d’accès aux informations sensibles ou de l’historique des risques. La priorité de l’examen et de l’notation des activités de ces utilisateurs peut vous aider à vous alerter sur les risques potentiels qui peuvent avoir des conséquences plus élevées pour votre organisation. Les groupes d’utilisateurs prioritaires dans la gestion des risques internes vous aident à définir les utilisateurs de votre organisation qui ont besoin d’une inspection plus approfondie et d’un score de risque plus sensible. Associées aux *violations* de stratégie de sécurité par les utilisateurs prioritaires et aux fuites de données par des *modèles* de stratégie utilisateurs prioritaires, les utilisateurs ajoutés à un groupe d’utilisateurs prioritaires ont une probabilité accrue d’alertes à risque internes et d’alertes avec des niveaux de gravité plus élevés.

![Paramètres de groupe d’utilisateurs prioritaires pour la gestion des risques internes.](../media/insider-risk-settings-priority-users.png)

Au lieu d’être ouverts à la révision par tous les analystes et enquêteurs, les groupes d’utilisateurs prioritaires peuvent également avoir besoin de restreindre les activités de révision à des utilisateurs spécifiques ou à des groupes de rôles à risque interne. Vous pouvez choisir d’affecter des utilisateurs individuels et des groupes de rôles pour passer en revue les utilisateurs, les alertes, les cas et les rapports pour chaque groupe d’utilisateurs prioritaires. Les groupes d’utilisateurs prioritaires peuvent avoir des autorisations de révision attribuées aux groupes de rôles intégrés Gestion des risques *internes, Analystes* de gestion des risques internes et Enquêteurs de gestion des risques internes, un ou plusieurs de ces groupes de rôles, ou à une sélection personnalisée d’utilisateurs.

Par exemple, vous devez vous protéger contre les fuites de données pour un projet hautement confidentiel dans lequel les utilisateurs ont accès à des informations sensibles. Vous choisissez de créer un *groupe d’utilisateurs Project*  priorité Utilisateurs confidentiels pour les utilisateurs de votre organisation qui travaillent sur ce projet. En outre, ce groupe d’utilisateurs prioritaires ne doit pas avoir d’utilisateurs, d’alertes, de cas et de rapports associés à un groupe visibles par tous les administrateurs, analystes et enquêteurs de gestion des risques internes par défaut. Dans **Paramètres**, vous créez le groupe Confidentiel *Project* Utilisateurs prioritaires et affectez deux utilisateurs en tant que réviseurs qui peuvent afficher les données liées aux groupes. À l’aide de l’Assistant Stratégie et des fuites de données par modèle de stratégie utilisateurs prioritaires,  vous créez une stratégie et affectez le groupe d’utilisateurs de priorité *Utilisateurs* Project Confidentiel à la stratégie. Les activités examinées par la stratégie pour les membres du  groupe d’utilisateurs prioritaire Project Les utilisateurs prioritaires sont plus sensibles aux risques et les activités de ces utilisateurs seront plus susceptibles de générer une alerte et d’avoir des alertes avec des niveaux de gravité plus élevés.

### <a name="create-a-priority-user-group"></a>Créer un groupe d’utilisateurs prioritaire

Pour créer un nouveau groupe d’utilisateurs prioritaires, vous utiliserez les contrôles de paramètre dans **la solution de** gestion des risques internes dans le Centre de conformité Microsoft 365. Pour créer un groupe d’utilisateurs prioritaires, vous devez être membre  du groupe de rôles Gestion des risques internes ou Administrateur de la gestion *des* risques internes.

Pour créer un groupe d’utilisateurs prioritaire, complétez les étapes suivantes :

1. Dans la [Centre de conformité Microsoft 365](https://compliance.microsoft.com), sélectionnez **Gestion** des risques internes et sélectionnez **Paramètres des risques internes**.
2. Sélectionnez la page **Groupes d’utilisateurs prioritaires (prévisualisation** ).
3. Dans la page **Groupes d’utilisateurs prioritaires (prévisualisation),** sélectionnez Créer un groupe d’utilisateurs prioritaire pour démarrer l’Assistant Création de groupe.
4. Dans la page **Nom et description** , complétez les champs suivants :
    - **Nom (obligatoire)** : entrez un nom convivial pour le groupe d’utilisateurs prioritaire. Vous ne pouvez pas modifier le nom du groupe d’utilisateurs prioritaires après avoir terminé l’Assistant.
    - **Description (facultative)** : entrez une description du groupe d’utilisateurs prioritaire.
5. Sélectionnez **Suivant** pour continuer.
6. Dans **la page Choisir** des membres,  sélectionnez Choisir les membres à rechercher et sélectionnez les comptes d’utilisateurs à messagerie inclus dans le groupe  ou activez la case à cocher Sélectionner tout pour ajouter tous les utilisateurs de votre organisation au groupe. **Sélectionnez Ajouter** pour continuer ou **Annuler** pour fermer sans ajouter d’utilisateurs au groupe.
7. Sélectionnez **Suivant** pour continuer.
8. Dans la page **Choisir qui** peut afficher ce groupe, vous devez définir qui peut passer en revue les utilisateurs, les alertes, les cas et les rapports pour le groupe d’utilisateurs prioritaire. Au moins un utilisateur ou un groupe de rôles de gestion des risques internes doit être affecté. **Sélectionnez Choisir les utilisateurs et les groupes** de rôles, puis sélectionnez les utilisateurs ou les groupes de rôles de gestion des risques internes que vous souhaitez affecter au groupe d’utilisateurs prioritaires. **Sélectionnez Ajouter** pour affecter les utilisateurs ou groupes de rôles sélectionnés au groupe.
9. Sélectionnez Suivant pour continuer.
10. Dans la page **Révision** , examinez les paramètres que vous avez choisis pour le groupe d’utilisateurs prioritaire. Sélectionnez **les liens modifier** pour modifier les valeurs de groupe ou sélectionnez **Envoyer** pour créer et activer le groupe d’utilisateurs prioritaire.
11. Dans la page de confirmation, **sélectionnez Terminé** pour quitter l’Assistant.

### <a name="update-a-priority-user-group"></a>Mettre à jour un groupe d’utilisateurs prioritaires

Pour mettre à jour un groupe d’utilisateurs prioritaires existant, vous utiliserez des contrôles de paramètres dans **la solution de** gestion des risques internes dans le Centre de conformité Microsoft 365. Pour mettre à jour un groupe d’utilisateurs prioritaires, vous devez  être membre du groupe de rôles Gestion des risques internes ou Administrateur de la gestion *des* risques internes.

Pour modifier un groupe d’utilisateurs prioritaires, complétez les étapes suivantes :

1. Dans la [Centre de conformité Microsoft 365](https://compliance.microsoft.com), sélectionnez **Gestion** des risques internes et sélectionnez **Paramètres des risques internes**.
2. Sélectionnez la page **Groupes d’utilisateurs prioritaires (prévisualisation** ).
3. Sélectionnez le groupe d’utilisateurs prioritaire à modifier, puis **sélectionnez Modifier le groupe**.
4. Dans la page **Nom et description** , mettez à jour le champ Description si nécessaire. Vous ne pouvez pas mettre à jour le nom du groupe d’utilisateurs prioritaire. Sélectionnez **Suivant** pour continuer.
5. Dans la page **Choisir des membres** , ajoutez de nouveaux membres au groupe à l’aide du **contrôle Choisir les membres** . Pour supprimer un utilisateur du groupe, sélectionnez le « X » en côté de l’utilisateur que vous souhaitez supprimer. Sélectionnez **Suivant** pour continuer.
6. Dans **la page** Choisir qui peut afficher ce groupe, ajoutez ou supprimez des utilisateurs ou des groupes de rôles qui peuvent passer en revue des utilisateurs, des alertes, des cas et des rapports pour le groupe d’utilisateurs prioritaire.
7. Sélectionnez **Suivant** pour continuer.
8. Dans la page **Révision** , examinez les paramètres de mise à jour que vous avez choisis pour le groupe d’utilisateurs prioritaire. Sélectionnez **les liens modifier** pour modifier les valeurs de groupe ou **sélectionnez Envoyer** pour mettre à jour le groupe d’utilisateurs prioritaires.
9. Dans la page de confirmation, **sélectionnez Terminé** pour quitter l’Assistant.

### <a name="delete-a-priority-user-group"></a>Supprimer un groupe d’utilisateurs prioritaire

Pour supprimer un groupe d’utilisateurs prioritaires existant, vous utiliserez des contrôles de paramètres dans **la solution de** gestion des risques internes dans le Centre de conformité Microsoft 365. Pour supprimer un groupe d’utilisateurs prioritaires, vous devez être membre  du groupe de rôles Gestion des risques internes ou Administrateur de la gestion *des* risques internes.

> [!IMPORTANT]
> La suppression d’un groupe d’utilisateurs prioritaires le supprime de toute stratégie active à laquelle il est affecté. Si vous supprimez un groupe d’utilisateurs prioritaire affecté à une stratégie active, la stratégie ne contiendra aucun utilisateur dans l’étendue et sera effectivement inactive et ne créera pas d’alertes.

Pour supprimer un groupe d’utilisateurs prioritaires, vous devez effectuer les étapes suivantes :

1. Dans la [Centre de conformité Microsoft 365](https://compliance.microsoft.com), sélectionnez **Gestion** des risques internes et sélectionnez **Paramètres des risques internes**.
2. Sélectionnez la page **Groupes d’utilisateurs prioritaires (prévisualisation** ).
3. Sélectionnez le groupe d’utilisateurs prioritaire à modifier, puis **sélectionnez Supprimer** dans le menu tableau de bord.
4. Dans la **boîte de dialogue** Supprimer, sélectionnez **Oui** pour supprimer le groupe d’utilisateurs prioritaire ou sélectionnez **Annuler** pour revenir au tableau de bord.

## <a name="priority-physical-assets-preview"></a>Ressources physiques prioritaires (prévisualisation)

L’identification de l’accès aux ressources physiques prioritaires et la mise en corrélation de l’activité d’accès aux événements utilisateur est un composant important de votre infrastructure de conformité. Ces biens physiques représentent des emplacements prioritaires dans votre organisation, tels que des bâtiments d’entreprise, des centres de données ou des salles de serveurs. Les activités à risque internes peuvent être associées à des utilisateurs travaillant pendant des heures inhabituelles, à la tentative d’accès à ces zones sensibles ou sécurisées non autorisées, et à des demandes d’accès à des zones de haut niveau sans besoins légitimes.

Une fois que les ressources physiques de priorité sont activées et que le connecteur de données de [badging](import-physical-badging-data.md) physique est configuré, la gestion des risques internes intègre les signaux de vos systèmes de contrôle physique et d’accès à d’autres activités de risque utilisateur. En examinant les modèles de comportement entre les systèmes d’accès physique et en corrélant ces activités avec d’autres événements de risque internes, la gestion des risques internes peut aider les enquêteurs et les analystes de conformité à prendre des décisions de réponse plus éclairées pour les alertes. L’accès aux ressources physiques prioritaires est marqué et identifié dans les informations différemment de l’accès aux biens non prioritaires.

Par exemple, votre organisation dispose d’un système de mauvaise gestion pour les utilisateurs qui surveille et approuve l’accès physique aux zones de projet normales et sensibles. Plusieurs utilisateurs travaillent sur un projet sensible et ces utilisateurs reviennent à d’autres zones de votre organisation une fois le projet terminé. Lorsque le projet sensible est sur le point d’être terminé, vous souhaitez vous assurer que le travail du projet reste confidentiel et que l’accès aux zones de projet est étroitement contrôlé.

Vous choisissez d’activer le connecteur de données de badging physique dans Microsoft 365 pour importer les informations d’accès à partir de votre système de mauvaise gestion physique et spécifier les ressources physiques prioritaires dans la gestion des risques internes. En important des informations à partir de votre système de corruption et en corrélant les informations d’accès physique avec d’autres activités de risque identifiées dans la gestion des risques internes, vous remarquez qu’un des utilisateurs du projet accède aux bureaux du projet après des heures de travail normales et exporte également de grandes quantités de données vers un service de stockage cloud personnel à partir de leur zone de travail normale. Cette activité d’accès physique associée à l’activité en ligne peut pointer vers un vol possible de données et les enquêteurs et analystes de conformité peuvent prendre les mesures appropriées selon les circonstances de cet utilisateur.

![Ressources physiques prioritaires pour la gestion des risques internes.](../media/insider-risk-settings-priority-assets.png)

### <a name="configure-priority-physical-assets"></a>Configurer les ressources physiques prioritaires

Pour configurer les ressources physiques prioritaires, vous devez configurer le connecteur de gestion des problèmes physiques et utiliser les contrôles de paramètre dans **la solution de** gestion des risques internes dans le Centre de conformité Microsoft 365. Pour configurer les ressources physiques prioritaires, vous devez être membre du groupe de rôles Gestion des risques internes ou Administrateur de la gestion *des risques internes*.

Pour configurer les ressources physiques prioritaires, complétez les étapes suivantes :

1. Suivez les étapes de configuration pour la gestion des risques internes dans l’article Prise [en charge de la gestion des risques internes](insider-risk-management-configure.md) . À l’étape 3, veillez à configurer le connecteur de badging physique.

    > [!IMPORTANT]
    > Pour que les stratégies de gestion des risques internes utilisent et corrélent les données de signal liées aux utilisateurs qui quittent et se terminent par des données d’événement à partir de vos plateformes de contrôle physique et d’accès, vous devez également configurer le connecteur RH Microsoft 365. Si vous activez le connecteur de badging physique sans activer le connecteur RH Microsoft 365, les stratégies de gestion des risques internes ne traitera que les événements des activités d’accès physique pour les utilisateurs de votre organisation.

2. Dans la [Centre de conformité Microsoft 365](https://compliance.microsoft.com), sélectionnez **Gestion** des risques internes et sélectionnez Les **paramètres** >  des risques **internesPriorité des biens physiques**.
3. Dans **la page Ressources** physiques prioritaires, vous pouvez ajouter manuellement les ID d’actifs physiques que vous souhaitez surveiller pour les événements de bien importés par le connecteur de badging physique ou importer un fichier .csv de tous les ID de biens physiques importés par le connecteur de badging physique : a) Pour ajouter manuellement des ID de ressources physiques, choisissez Ajouter des ressources physiques **prioritaires,**  entrez un ID de bien physique, puis sélectionnez **Ajouter**. Entrez d’autres ID de ressources physiques, puis sélectionnez **Ajouter** des ressources physiques de priorité pour enregistrer tous les biens entrés.
    b) Pour ajouter une liste d’ID de ressources physiques à partir d’un fichier .csv, choisissez Importer des ressources physiques **prioritaires**. Dans la boîte de dialogue Explorateur de fichiers, sélectionnez le .csv que vous souhaitez importer, puis sélectionnez **Ouvrir**. Les ID de ressources physiques des fichiers .csv sont ajoutés à la liste.
4. Accédez à la page **Indicateurs de stratégie** **dans Paramètres**.
5. Dans la page **Indicateurs de** stratégie, accédez à la section Indicateurs d’accès physique et cochez la case accès physique après l’arrêt ou l’échec de l’accès aux **biens sensibles**.
6. **Sélectionnez Enregistrer** pour configurer et quitter.

### <a name="delete-a-priority-physical-asset"></a>Supprimer un bien physique prioritaire

Pour supprimer un bien physique de priorité existant, vous utiliserez des contrôles de paramètre dans la solution de gestion des risques internes dans le Centre de conformité Microsoft 365. Pour supprimer un bien physique prioritaire, vous devez être membre du groupe de rôles Gestion des risques internes ou Administrateur de la gestion des risques internes.

> [!IMPORTANT]
> La suppression d’un bien physique prioritaire le supprime de l’examen par toute stratégie active à laquelle il était précédemment inclus. Les alertes générées par les activités associées au bien physique de priorité ne sont pas supprimées.

Pour supprimer un bien physique prioritaire, vous devez effectuer les étapes suivantes :

1. Dans la [Centre de conformité Microsoft 365](https://compliance.microsoft.com), sélectionnez **Gestion** des risques internes et sélectionnez Les **paramètres** >  des risques **internesPriorité des biens physiques**.
2. Dans la page **Ressources physiques prioritaires** , sélectionnez le bien à supprimer.
3. **Sélectionnez Supprimer** dans le menu Action pour supprimer le bien.

## <a name="power-automate-flows-preview"></a>Power Automate flux de données (prévisualisation)

[Microsoft Power Automate](/power-automate/getting-started) est un service de flux de travail qui automatise les actions entre les applications et les services. En utilisant des flux à partir de modèles ou créés manuellement, vous pouvez automatiser les tâches courantes associées à ces applications et services. Lorsque vous activez Power Automate de gestion des risques internes, vous pouvez automatiser des tâches importantes pour les cas et les utilisateurs. Vous pouvez configurer des flux Power Automate pour récupérer des informations sur les utilisateurs, les alertes et les cas, et partager ces informations avec les parties prenantes et d’autres applications, ainsi qu’automatiser les actions de gestion des risques internes, telles que la publication dans des notes de cas. Power Automate flux sont applicables pour les cas et tout utilisateur dans l’étendue d’une stratégie.

Les clients  titulaires Microsoft 365 abonnements qui incluent la gestion des risques internes n’ont pas besoin de licences Power Automate supplémentaires pour utiliser les modèles recommandés de gestion des risques internes Power Automate. Ces modèles peuvent être personnalisés pour prendre en charge votre organisation et couvrir les principaux scénarios de gestion des risques internes. Si vous choisissez d’utiliser des fonctionnalités Power Automate premium dans ces modèles, de créer un modèle personnalisé à l’aide du connecteur de conformité Microsoft 365 ou d’utiliser des modèles Power Automate pour d’autres domaines de conformité dans Microsoft 365, vous aurez peut-être besoin de plus de licences Power Automate.

Les modèles de Power Automate suivants sont fournis aux clients pour prendre en charge l’automatisation des processus pour les utilisateurs et les cas de gestion des risques internes :

- Informez les utilisateurs **lorsqu’ils** sont ajoutés à une stratégie de risque interne : ce modèle est pour les organisations qui ont des stratégies internes, la confidentialité ou des exigences réglementaires que les utilisateurs doivent être avertis lorsqu’ils sont soumis à des stratégies de gestion des risques internes. Lorsque ce flux est configuré et sélectionné pour un utilisateur dans **la page** Utilisateurs, les utilisateurs et leurs responsables sont envoyés par courrier électronique lorsque l’utilisateur est ajouté à une stratégie de gestion des risques internes. Ce modèle prend également en charge la mise à jour d’une liste SharePoint hébergée sur un site SharePoint pour vous aider à suivre les détails des messages de notification tels que la date/l’heure et le destinataire du message. Si vous avez choisi d’anonymiser les **utilisateurs dans les paramètres** de confidentialité, les flux créés à partir de ce modèle ne fonctionneront pas comme prévu afin que la confidentialité de l’utilisateur soit conservée. Power Automate flux à l’aide de ce modèle sont disponibles dans le tableau **de bord Utilisateurs**.
- Demander des informations auprès des ressources humaines ou de l’entreprise sur un utilisateur dans un cas de risque interne : lors de l’action sur un cas, les analystes et enquêteurs des risques internes peuvent avoir besoin de consulter les ressources humaines ou d’autres parties prenantes pour comprendre le contexte des activités du cas. Lorsque ce flux est configuré et sélectionné pour un cas, les analystes et enquêteurs envoient un message électronique aux parties prenantes et aux ressources humaines configurées pour ce flux. Chaque destinataire reçoit un message avec des options de réponse pré-configurées ou personnalisables. Lorsque les destinataires sélectionnent une option de réponse, la réponse est enregistrée en tant que note de cas et inclut les informations de destinataire et de date/heure. Si vous avez choisi d’anonymiser les **utilisateurs dans les paramètres** de confidentialité, les flux créés à partir de ce modèle ne fonctionneront pas comme prévu afin que la confidentialité de l’utilisateur soit conservée. Power Automate flux à l’aide de ce modèle sont disponibles dans le tableau de bord **Cas**.
- **Avertir le responsable lorsqu’un utilisateur** a une alerte de risque interne : certaines organisations peuvent avoir besoin d’une notification de gestion immédiate lorsqu’un utilisateur a une alerte de gestion des risques internes. Lorsque ce flux est configuré et sélectionné, le responsable de l’utilisateur du cas est envoyé un message électronique avec les informations suivantes sur toutes les alertes de cas :
    - Stratégie applicable pour l’alerte
    - Date/heure de l’alerte
    - Niveau de gravité de l’alerte

    Le flux met automatiquement à jour les notes de cas que le message a été envoyé et que le flux a été activé. Si vous avez choisi d’anonymiser les **utilisateurs dans les paramètres** de confidentialité, les flux créés à partir de ce modèle ne fonctionneront pas comme prévu afin que la confidentialité de l’utilisateur soit conservée. Power Automate flux à l’aide de ce modèle sont disponibles dans le tableau de bord **Cas**.
- **Créez un enregistrement pour les cas de risque internes dans ServiceNow :** ce modèle est conçu pour les organisations qui souhaitent utiliser leur solution ServiceNow pour suivre les cas de gestion des risques internes.  Dans un cas, les analystes et enquêteurs des risques internes peuvent créer un enregistrement pour le cas dans ServiceNow. Vous pouvez personnaliser ce modèle pour remplir les champs sélectionnés dans ServiceNow en fonction des besoins de votre organisation. Power Automate flux à l’aide de ce modèle sont disponibles dans le tableau de bord **Cas**. Pour plus d’informations sur les champs ServiceNow disponibles, consultez l’article de [référence serviceNow Connector](/connectors/service-now/) .

### <a name="create-a-power-automate-flow-from-insider-risk-management-template"></a>Créer un flux de Power Automate à partir du modèle de gestion des risques internes

Pour créer un flux Power Automate à partir d’un modèle de gestion des risques internes recommandé, vous allez utiliser les contrôles de paramètres dans **la solution de** gestion des risques internes dans le Centre de conformité Microsoft 365 ou l’option Gérer les flux **Power Automate** à partir du contrôle **Automatiser** lorsque vous travaillez directement dans les tableaux **de bord Cas** **ou Utilisateurs**.

Pour créer un flux Power Automate dans la zone des paramètres, vous devez être membre du groupe de rôles  Gestion des risques internes  ou Administrateur de la gestion des risques internes. Pour créer un flux Power Automate avec l’option Gérer Power Automate **flux**, vous devez être membre d’au moins un groupe de rôles de gestion des risques internes.

Pour créer un flux de Power Automate à partir d’un modèle de gestion des risques internes recommandé, complétez les étapes suivantes :

1. Dans la [Centre de conformité Microsoft 365](https://compliance.microsoft.com), sélectionnez **Gestion** des risques internes et sélectionnez **Paramètres** >  des risques internes **Power Automate flux**. Vous pouvez également accéder à partir des pages **de tableaux** de bord Cas ou **Utilisateurs** en choisissant **AutomateManage** >  **Power Automate flux**.
2. Dans la page **Power Automate flux**, sélectionnez un modèle recommandé dans les **modèles** de gestion des risques internes que vous souhaitez peut-être voir dans la section de la page.
3. Le flux répertorie les connexions incorporées nécessaires au flux et note si les états de connexion sont disponibles. Si nécessaire, mettez à jour les connexions qui ne sont pas affichées comme disponibles. Cliquez sur **Continuer**.
4. Par défaut, les flux recommandés sont pré-configurés avec les champs recommandés de gestion des risques internes et de données de service Microsoft 365 requis pour effectuer la tâche affectée au flux. Si nécessaire, personnalisez les composants de flux à l’aide du contrôle Afficher les **options** avancées et en configurant les propriétés disponibles pour le composant de flux.
5. Si nécessaire, ajoutez d’autres étapes au flux en sélectionnant le **bouton Nouvelle étape** . Dans la plupart des cas, cela ne doit pas être nécessaire pour les modèles par défaut recommandés.
6. **Sélectionnez Enregistrer le brouillon** pour enregistrer le flux pour une configuration supplémentaire ou sélectionnez **Enregistrer** pour terminer la configuration du flux.
7. **Sélectionnez Fermer** pour revenir à **la page Power Automate flux**. Le nouveau modèle est répertorié sous la forme d’un flux  sous les onglets Mes flux et est automatiquement disponible à partir du contrôle de listes de listes d’attente **Automatiser** lorsque vous travaillez avec des cas de gestion des risques internes pour l’utilisateur qui crée le flux.

> [!IMPORTANT]
> Si d’autres utilisateurs de votre organisation ont besoin d’accéder au flux, le flux doit être partagé.

### <a name="create-a-custom-power-automate-flow-for-insider-risk-management"></a>Créer un flux de Power Automate personnalisé pour la gestion des risques internes

Certains processus et flux de travail pour votre organisation peuvent se trouver en dehors des modèles de flux de gestion des risques internes recommandés et vous devrez peut-être créer des flux de Power Automate personnalisés pour les domaines de gestion des risques internes. Power Automate sont flexibles et prendre en charge une personnalisation étendue, mais il existe des étapes à suivre pour intégrer les fonctionnalités de gestion des risques internes.

Pour créer un modèle d’Power Automate personnalisé pour la gestion des risques internes, complétez les étapes suivantes :

1. **Vérifiez votre Power Automate de flux** : pour créer des flux Power Automate personnalisés qui utilisent des déclencheurs de gestion des risques internes, vous aurez besoin d’une licence Power Automate personnalisée. Les modèles de flux de gestion des risques internes recommandés ne nécessitent pas de licences supplémentaires et sont inclus dans le cadre de votre licence de gestion des risques internes.
2. **Créez un flux automatisé** : créez un flux qui effectue une ou plusieurs tâches après qu’il a été déclenché par un événement de gestion des risques internes. Pour plus d’informations sur la création d’un flux automatisé, voir [Créer un flux dans Power Automate](/power-automate/get-started-logic-flow).
3. **Sélectionnez le connecteur Microsoft 365 conformité :** recherchez et sélectionnez le connecteur Microsoft 365 conformité. Ce connecteur active les déclencheurs et actions de gestion des risques internes. Pour plus d’informations sur les connecteurs, consultez l’article [de présentation de référence du](/connectors/connector-reference/) connecteur.
4. **Choisissez les déclencheurs de gestion des risques internes pour** votre flux : la gestion des risques internes a deux déclencheurs disponibles pour les flux Power Automate personnalisés :
    - **Pour un cas de gestion des** risques internes sélectionné : les flux avec ce déclencheur peuvent être sélectionnés dans la page du tableau de bord Cas de gestion des risques internes.
    - **Pour un utilisateur de gestion des** risques internes sélectionné : les flux avec ce déclencheur peuvent être sélectionnés dans la page du tableau de bord Utilisateurs de gestion des risques internes.
5. Choisissez les actions de gestion des risques internes pour votre flux : vous pouvez choisir parmi plusieurs actions pour la gestion des risques internes à inclure dans votre flux personnalisé :
    - Obtenir une alerte de gestion des risques internes
    - Obtenir un cas de gestion des risques internes
    - Obtenir un utilisateur de gestion des risques internes
    - Obtenir des alertes de gestion des risques internes pour un cas
    - Ajouter une note de cas de gestion des risques internes

### <a name="share-a-power-automate-flow"></a>Partager un flux Power Automate de données

Par défaut, les flux Power Automate créés par un utilisateur sont uniquement disponibles pour cet utilisateur. Pour que d’autres utilisateurs de gestion des risques internes ont accès et utilisent un flux, le flux doit être partagé par le créateur du flux. Pour partager un flux, vous allez utiliser les contrôles de paramètres de la **solution** de gestion des risques internes dans le Centre de conformité Microsoft 365 ou l’option Gérer les flux **Power Automate** à partir du contrôle Automatiser lorsque vous travaillez directement dans  **les pages de** tableau de bord Cas ou Utilisateurs. Une fois que vous avez partagé un flux, toutes les personnes avec qui il a été partagé peuvent accéder au flux dans la zone de contrôle **Automatiser** dans les tableaux de bord Cas et **Utilisateur**.

Pour partager un flux Power Automate dans la zone des paramètres, vous devez être membre du groupe de rôles  Gestion des risques internes  ou Administrateur de la gestion des risques internes. Pour partager un flux Power Automate avec **l’option Gérer** les flux Power Automate, vous devez être membre d’au moins un groupe de rôles de gestion des risques internes.

Pour partager un flux de Power Automate, complétez les étapes suivantes :

1. Dans la [Centre de conformité Microsoft 365](https://compliance.microsoft.com), sélectionnez **Gestion** des risques internes et sélectionnez **Paramètres** >  des risques internes **Power Automate flux**. Vous pouvez également accéder à partir des pages **de tableaux** de bord Cas ou **Utilisateurs** en choisissant **AutomateManage** >  **Power Automate flux**.
2. Dans la page **Power Automate flux**, sélectionnez **l’onglet Mes flux ou** **Flux d’équipe**.
3. Sélectionnez le flux à partager, puis **sélectionnez Partager dans** le menu options de flux.
4. Sur la page de partage de flux, entrez le nom de l’utilisateur ou du groupe que vous souhaitez ajouter en tant que propriétaire du flux.
5. Dans la **boîte de dialogue Connexion utilisée** , sélectionnez **OK** pour reconnaître que l’utilisateur ou le groupe ajouté aura un accès total au flux.

### <a name="edit-a-power-automate-flow"></a>Modifier un flux Power Automate de données

Pour modifier un flux, vous allez utiliser les contrôles de paramètres de **la solution de** gestion des risques internes dans le Centre de conformité Microsoft 365 ou l’option Gérer les flux **Power Automate** à partir du contrôle **Automatiser** lorsque vous travaillez directement dans les  tableaux de bord Cas ou **Utilisateurs**.

Pour modifier un flux Power Automate dans la zone des paramètres, vous devez être membre du groupe de rôles  Gestion des risques internes  ou Administrateur de la gestion des risques internes. Pour modifier un flux Power Automate avec l’option Gérer Power Automate **flux**, vous devez être membre d’au moins un groupe de rôles de gestion des risques internes.

Pour modifier un flux de Power Automate, complétez les étapes suivantes :

1. Dans la [Centre de conformité Microsoft 365](https://compliance.microsoft.com), sélectionnez **Gestion** des risques internes et sélectionnez **Paramètres** >  des risques internes **Power Automate flux**. Vous pouvez également accéder à partir des pages **de tableaux** de bord Cas ou **Utilisateurs** en choisissant **AutomateManage** >  **Power Automate flux**.
2. Dans la page **Power Automate flux**, sélectionnez un flux à modifier et sélectionnez **Modifier** dans le menu de contrôle de flux.
3. Sélectionnez **les Paramètres** >  **pour modifier** un paramètre de composant de flux ou **ellipsisDelete** >  pour supprimer un composant de flux.
4. **Sélectionnez Enregistrer**, **puis Fermez** pour terminer la modification du flux.

### <a name="delete-a-power-automate-flow"></a>Supprimer un flux Power Automate de données

Pour supprimer un flux, vous allez utiliser les contrôles de paramètres de **la solution de** gestion des risques internes dans le Centre de conformité Microsoft 365 ou l’option Gérer les flux **Power Automate** à partir du contrôle **Automatiser** lorsque vous travaillez directement dans les  tableaux de bord Cas ou **Utilisateurs**. Lorsqu’un flux est supprimé, il est supprimé en tant qu’option pour tous les utilisateurs.

Pour supprimer un flux Power Automate dans la zone des paramètres, vous devez être membre du groupe de rôles  Gestion des risques internes  ou Administrateur de la gestion des risques internes. Pour supprimer un flux Power Automate avec l’option Gérer **Power Automate flux**, vous devez être membre d’au moins un groupe de rôles de gestion des risques internes.

Pour supprimer un flux de Power Automate, vous devez effectuer les étapes suivantes :

1. Dans la [Centre de conformité Microsoft 365](https://compliance.microsoft.com), sélectionnez **Gestion** des risques internes et sélectionnez **Paramètres** >  des risques internes **Power Automate flux**. Vous pouvez également accéder à partir des pages **de tableaux** de bord Cas ou **Utilisateurs** en choisissant **AutomateManage** >  **Power Automate flux**.
2. Dans la page **Power Automate flux**, sélectionnez un flux à supprimer et sélectionnez **Supprimer** dans le menu de contrôle de flux.
3. Dans la boîte de dialogue de confirmation de suppression, sélectionnez **Supprimer** pour supprimer le flux ou sélectionnez **Annuler** pour quitter l’action de suppression.

## <a name="microsoft-teams-preview"></a>Microsoft Teams (aperçu)

Les analystes et enquêteurs de conformité peuvent facilement utiliser Microsoft Teams pour la collaboration sur les cas de gestion des risques internes. Ils peuvent coordonner et communiquer avec d’autres parties prenantes Microsoft Teams pour :

- Coordonner et examiner les activités de réponse pour les cas dans les canaux Teams privés
- Partager et stocker en toute sécurité des fichiers et des preuves liés à des cas individuels
- Suivre et passer en revue les activités de réponse des analystes et des enquêteurs

Une fois Microsoft Teams pour la gestion des risques internes, une équipe Microsoft Teams dédiée est créée chaque fois qu’une alerte est confirmée et qu’un cas est créé. Par défaut, l’équipe inclut automatiquement tous les membres des groupes de rôles Insider *Risk Management*, *Insider Risk Management Analysts* et *Insider Risk Management Investigators* (jusqu’à 100 utilisateurs initiaux). Des collaborateurs d’organisation supplémentaires peuvent être ajoutés à l’équipe après sa création et selon les cas. Pour les cas existants créés avant d’activer Microsoft Teams, les analystes et enquêteurs peuvent choisir de créer une équipe Microsoft Teams lorsque vous travaillez dans un cas si nécessaire.  Une fois que vous avez résolu le cas associé dans la gestion des risques internes, l’équipe est automatiquement archivée (déplacée vers masquée et en lecture seule).

Pour plus d’informations sur l’utilisation des équipes et des canaux dans Microsoft Teams, voir Vue d’ensemble des équipes et des canaux [dans Microsoft Teams](/MicrosoftTeams/teams-channels-overview).

L’activation Microsoft Teams prise en charge des cas est rapide et facile à configurer. Pour activer Microsoft Teams gestion des risques internes, complétez les étapes suivantes :

1. Dans la [Centre de conformité Microsoft 365](https://compliance.microsoft.com), allez aux paramètres de risque **Insider Risk** **managementInsider** > .
2. Sélectionnez **la Microsoft Teams** page.
3. Activez Microsoft Teams’intégration pour la gestion des risques internes.
4. **Sélectionnez Enregistrer** pour configurer et quitter.

![Gestion des risques internes Microsoft Teams.](../media/insider-risk-settings-teams.png)

### <a name="create-a-microsoft-teams-team-for-existing-cases"></a>Créer une équipe Microsoft Teams pour les cas existants

Si vous activez Microsoft Teams prise en charge de la gestion des risques internes une fois que vous avez des cas existants, vous devez créer manuellement une équipe pour chaque cas si nécessaire. Après avoir Microsoft Teams prise en charge dans les paramètres de gestion des risques internes, de nouveaux cas créent automatiquement une équipe Microsoft Teams interne.

Les utilisateurs doivent être autorisés à créer Microsoft 365 groupes de votre organisation pour créer une équipe Microsoft Teams à partir d’un cas. Pour plus d’informations sur la gestion des autorisations pour Microsoft 365 groupes de gestion, voir Gérer les personnes [autorisées à créer Microsoft 365 groupes](../solutions/manage-creation-of-groups.md).

Pour créer une équipe pour un cas, vous devez utiliser le contrôle Créer une équipe Microsoft lorsque vous travaillez directement dans un cas existant. Pour créer une équipe, complétez les étapes suivantes :

1. Dans la [Centre de conformité Microsoft 365](https://compliance.microsoft.com), sélectionnez un cas existant, puis sélectionnez **Insider Risk** **ManagementCases** > .
2. Dans le menu d’action de cas, **sélectionnez Créer Microsoft Team**.
3. Dans le **champ Nom de l’équipe**, entrez un nom pour la nouvelle Microsoft Teams équipe.
4. **Sélectionnez Créer une équipe Microsoft**, puis **Fermez**.

Selon le nombre d’utilisateurs affectés à des groupes de rôles de gestion des risques internes, l’ajout de tous les enquêteurs et analystes à l’équipe Microsoft Teams pour un cas peut prendre 15 minutes.

## <a name="analytics"></a>Analyse

L’analyse des risques internes vous permet d’effectuer une évaluation des risques internes potentiels au sein de votre organisation sans aucune configuration de stratégie des risques internes. Cette évaluation peut permettre à votre organisation d’identifier des zones potentielles plus élevées de risque utilisateur et vous aider à déterminer le type et l’étendue des stratégies de gestion des risques internes que vous pouvez envisager de configurer. Les analyses d’analyse offrent les avantages suivants pour votre organisation :

- Facile à configurer : pour commencer à utiliser les analyses d’analyse, vous pouvez sélectionner Exécuter l’analyse lorsque vous y êtes invité par la recommandation d’analyse ou passer à **Paramètres** >  des risques **internesAnalytics** et activer l’analyse.
- Confidentialité par conception : les résultats de l’analyse et les informations sont renvoyés en tant qu’activité utilisateur agrégée et rendue anonyme, les noms d’utilisateur individuels ne sont pas identifiables par les réviseurs.
- Comprenez les risques potentiels par le biais d’informations consolidées : les résultats de l’analyse peuvent vous aider à identifier rapidement les zones de risque potentielles pour vos utilisateurs et la stratégie la mieux à même d’atténuer ces risques.

Regardez la vidéo [Analyse de](https://www.youtube.com/watch?v=5c0P5MCXNXk) la gestion des risques internes pour comprendre comment l’analyse peut vous aider à accélérer l’identification des risques internes potentiels et à prendre rapidement des mesures.

L’analyse recherche les événements d’activité à risque provenant de plusieurs sources afin d’identifier les informations sur les zones de risque potentielles. En fonction de votre configuration actuelle, l’analyse recherche les activités de risque éligibles dans les domaines suivants :

- **Microsoft 365 journaux d’audit** : inclus dans toutes les analyses, il s’agit de la source principale permettant d’identifier la plupart des activités potentiellement risquées.
- **Exchange Online** : incluse dans toutes les analyses, l’activité Exchange Online permet d’identifier les activités dans laquelle les données des pièces jointes sont envoyés par courrier électronique à des contacts ou services externes.
- **Azure Active Directory** : inclus dans toutes les analyses, Azure Active Directory’historique permet d’identifier les activités à risque associées aux utilisateurs avec des comptes d’utilisateurs supprimés.
- **Microsoft 365 connecteur** de données RH : s’ils sont configurés, les événements de connecteur RH permettent d’identifier les activités à risque associées aux utilisateurs qui ont des dates de résiliation anticipées ou à venir.

Les analyses des analyses sont basées sur les mêmes signaux d’activité de risque utilisés par les stratégies de gestion des risques internes et signalent les résultats en fonction des activités des utilisateurs à une seule et de la séquence. Toutefois, l’évaluation des risques pour l’analyse est basée sur 30 jours d’activité au plus, tandis que les stratégies de risque internes utilisent l’activité quotidienne pour obtenir des informations. Lorsque vous activez et exécutez l’analyse pour la première fois dans votre organisation, vous voyez les résultats de l’analyse pour une journée. Si vous laissez l’analyse activée, vous verrez les résultats de chaque analyse quotidienne ajoutés aux rapports d’analyse pour une plage maximale des 30 jours d’activité précédents.

### <a name="enable-analytics-and-start-your-scan"></a>Activer l’analyse et démarrer votre analyse

Pour activer l’analyse des risques internes, vous devez être membre du groupe de rôles d’administrateur de gestion des risques *internes,* d’administrateur de gestion des risques internes *ou Microsoft 365 d’administrateur* global.
Pour activer l’analyse des risques internes, vous suivrez les étapes suivantes :

1. Dans la [Centre de conformité Microsoft 365](https://compliance.microsoft.com), allez à **La gestion des risques internes**.
2. **Sélectionnez Exécuter l’analyse** dans **l’analyse des risques** internes dans la carte de votre organisation, sous l’onglet Vue d’ensemble de la gestion **des** risques internes. Cela permet d’analyser l’analyse de votre organisation. Vous pouvez également activer l’analyse dans votre organisation en naviguant vers les **paramètres** >  des risques **internesAnalytics** et en activant **l’analyse de l’activité** utilisateur de votre client pour identifier les risques internes potentiels.
3. Dans le **volet Détails de l’analyse** , **sélectionnez Exécuter l’analyse** pour démarrer l’analyse pour votre organisation. Les résultats de l'analyse analytique peuvent prendre jusqu'à 48 heures avant que les informations ne soient disponibles sous forme de rapports pour examen.

![Paramètres d’analyse de la gestion des risques internes.](../media/insider-risk-settings-analytics-enable.png)

### <a name="viewing-analytics-insights-and-creating-new-policies"></a>Affichage des analyses et création de stratégies

Une fois la première analyse terminée pour votre organisation, vous pouvez afficher les informations et les recommandations concernant les activités potentiellement risquées de vos utilisateurs. Les analyses quotidiennes se poursuivent, sauf si vous la désactiver pour votre organisation. Pour afficher les risques potentiels pour votre organisation, consultez  l’onglet Vue d’ensemble et sélectionnez **Afficher les résultats** sur la carte d’analyse des **risques internes**. Si l’analyse de votre organisation n’est pas terminée, vous verrez un message vous messageant que l’analyse est toujours active.

![Fiche prête pour les rapports d’analyse de la gestion des risques internes.](../media/insider-risk-analytics-ready-card.png)

Pour les analyses terminées, vous verrez les risques potentiels détectés dans votre organisation, ainsi que des informations et des recommandations pour résoudre ces risques. Les risques identifiés et des informations spécifiques sont inclus dans les rapports regroupés par domaine, le nombre total d’utilisateurs avec des risques identifiés, le pourcentage de ces utilisateurs avec des activités potentiellement risquées et une stratégie de risque interne recommandée pour vous aider à atténuer ces risques. Les rapports sont les suivants :

- **Informations sur les fuites** de données : activités pour tous les utilisateurs qui peuvent inclure un partage accidentel d’informations en dehors de votre organisation ou des fuites de données par des utilisateurs malveillants.
- Informations sur le vol de données : activités pour les **utilisateurs** qui quittent ou les utilisateurs ayant des comptes Azure Active Directory supprimés qui peuvent inclure un partage risqué d’informations en dehors de votre organisation ou un vol de données par des utilisateurs malveillants.
- **Informations d’exfiltration principales** : activités de tous les utilisateurs qui peuvent inclure le partage de données en dehors de votre organisation.

![Rapport de vue d’ensemble de l’analyse de la gestion des risques internes.](../media/insider-risk-analytics-overview.png)

Pour afficher plus d’informations pour un aperçu, sélectionnez **Afficher les détails** pour afficher le volet d’informations de l’insight. Le volet d’informations inclut les résultats complets de l’analyse, une recommandation de  stratégie de risque interne et le bouton Créer une stratégie pour vous aider à créer rapidement la stratégie recommandée. La sélection de créer une stratégie vous permet d’utiliser l’Assistant Stratégie et de sélectionner automatiquement le modèle de stratégie recommandé associé à l’aperçu. Par exemple, si l’analyse est pour  l’activité de fuite de données, le modèle de stratégie Général des *fuites* de données sera pré-sélectionné dans l’Assistant Stratégie pour vous.

![Rapport détaillé de l’analyse de la gestion des risques internes.](../media/insider-risk-analytics-details.png)

### <a name="turn-off-analytics"></a>Désactiver l’analyse

Pour désactiver l’analyse des risques internes, vous devez être membre du groupe de rôles d’administrateur de gestion des risques *internes,* d’administrateur de gestion des risques internes ou Microsoft 365 d’administrateur global.  Une fois l’analyse désactivée, les rapports d’analyse restent statiques et ne sont pas mis à jour pour les nouveaux risques.

Pour désactiver l’analyse des risques internes, complétez les étapes suivantes :

1. Dans la [Centre de conformité Microsoft 365](https://compliance.microsoft.com), allez à **La gestion des risques internes**.
2. Sélectionnez **la page Paramètres des risques** >  **internesAnalytics**.
3. Dans la page **Analyse** , désactiver **l’analyse de l’activité utilisateur de votre client pour identifier les risques internes potentiels**.

## <a name="admin-notifications"></a>Notifications de l’administrateur

Les notifications d’administrateur envoient automatiquement une notification par courrier électronique aux utilisateurs inclus dans les groupes de rôles Insider *Risk Management*, *Insider Risk Management Analysts* et *Insider Risk Management Investigators* lorsque la première alerte est générée pour une nouvelle stratégie. Cette option est activée par défaut pour toutes les organisations et les stratégies sont vérifiées toutes les 24 heures pour les alertes de première heure. Les notifications ne sont pas envoyées pour les alertes qui se produisent dans les stratégies après la première alerte.

Si vous préférez désactiver les notifications d’administrateur, complétez les étapes suivantes :

1. Dans la [Centre de conformité Microsoft 365](https://compliance.microsoft.com), allez aux paramètres de risque **Insider Risk** **managementInsider** > .
2. Sélectionnez la page **Notifications de l’administrateur** .
3. Clear the **Send a notification email when the first alert is generated for a new policy** checkbox.
4. **Sélectionnez Enregistrer** pour configurer et quitter.

![Paramètres de notifications de l’administrateur de la gestion des risques internes.](../media/insider-risk-admin-notifications.png)
