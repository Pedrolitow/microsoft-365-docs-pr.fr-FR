---
title: Paramètres de gestion des risques internes
description: En savoir plus sur les paramètres de gestion des risques internes dans Microsoft Purview
keywords: Microsoft 365, Microsoft Purview, risque interne, gestion des risques, conformité
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
- highpri
- tier1
- purview-compliance
- m365solution-insiderrisk
- m365initiative-compliance
- highpri
ms.custom: admindeeplinkCOMPLIANCE
ms.openlocfilehash: 1d38fceba4d01d184ae5e451fdecaeb030450259
ms.sourcegitcommit: e7dbe3b0d97cd8c64b5ae15f990d5e4b1dc9c464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2022
ms.locfileid: "68688365"
---
# <a name="get-started-with-insider-risk-management-settings"></a>Prise en main des paramètres de gestion des risques internes

>[!IMPORTANT]
>Gestion des risques internes Microsoft Purview met en corrélation différents signaux pour identifier les risques internes potentiels malveillants ou par inadvertance, tels que le vol d’adresses IP, les fuites de données et les violations de sécurité. La gestion des risques internes permet aux clients de créer des stratégies pour gérer la sécurité et la conformité. Conçu avec la confidentialité par défaut, les utilisateurs sont pseudonymisés par défaut, et des contrôles d’accès en fonction du rôle et des journaux d’audit sont en place pour garantir la confidentialité au niveau de l’utilisateur.

Les paramètres de gestion des risques internes s’appliquent à toutes les stratégies de gestion des risques internes, quel que soit le modèle que vous choisissez lors de la création d’une stratégie. Les paramètres sont configurés à l’aide du contrôle **Paramètres des risques internes** situé en haut de toutes les pages de gestion des risques internes. Ces paramètres contrôlent les composants de stratégie pour les domaines suivants :

- [Confidentialité](#privacy)
- [Indicateurs](#indicators)
- [Délais de la stratégie](#policy-timeframes)
- [Détections intelligentes](#intelligent-detections)
- [Exporter des alertes](#export-alerts)
- [Groupes d’utilisateurs prioritaires (préversion)](#priority-user-groups-preview)
- [Ressources physiques prioritaires (préversion)](#priority-physical-assets-preview)
- [Flux Power Automate (préversion)](#power-automate-flows-preview)
- [Microsoft Teams (préversion)](#microsoft-teams-preview)
- [Analyse](#analytics)
- [notifications Administration](#admin-notifications)

Avant de commencer à créer des stratégies de gestion des risques internes, il est important de comprendre ces paramètres et de choisir les niveaux de configuration les mieux adaptés aux besoins de conformité de votre organisation.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="privacy"></a>Confidentialité

La protection de la confidentialité des utilisateurs disposant de correspondances de stratégie est importante et peut favoriser l'objectivité dans les examens et analyses de données pour les alertes de risque internes. Pour les utilisateurs avec une correspondance de stratégie de risque interne, vous pouvez choisir l’un des paramètres suivants :

- **Afficher les versions anonymisées des noms d’utilisateur** : les noms des utilisateurs sont rendus anonymes pour empêcher les administrateurs, les enquêteurs de données et les réviseurs de voir qui est associé aux alertes de stratégie. Par exemple, un utilisateur « Grace à Taylor » apparaît avec un pseudonyme aléatoire tel que « AnonIS8-988 » dans toutes les zones de l’expérience de gestion des risques internes. Le choix de ce paramètre permet d'anonymiser tous les utilisateurs ayant des correspondances de stratégie actuelle et passée et s’applique à toutes les stratégies. Les informations de profil utilisateur dans l’alerte de risque interne et les détails du cas ne sont pas disponibles lorsque cette option est choisie. Toutefois, les noms d’utilisateur s’affichent lors de l’ajout de nouveaux utilisateurs à des stratégies existantes ou lors de l’affectation d’utilisateurs à de nouvelles stratégies. Si vous choisissez de désactiver ce paramètre, les noms d’utilisateur s’affichent pour tous les utilisateurs qui ont des correspondances de stratégie actuelles ou passées.

    >[!IMPORTANT]
    >Pour maintenir l’intégrité référentielle pour les utilisateurs qui ont des alertes ou des cas de risque interne dans Microsoft 365 ou d’autres systèmes, l’anonymisation des noms d’utilisateur n’est pas conservée pour les alertes exportées. Les alertes exportées affichent les noms d’utilisateur pour chaque alerte.

- **Ne pas afficher les versions anonymisées des noms d’utilisateur** : les noms d’utilisateur sont affichés pour toutes les correspondances de stratégie actuelles et passées pour les alertes et les cas. Les informations de profil utilisateur (nom, titre, alias et organisation ou service) sont affichées pour l’utilisateur pour toutes les alertes et tous les cas de gestion des risques internes.

![Paramètres de confidentialité de la gestion des risques internes.](../media/insider-risk-settings-privacy.png)

## <a name="indicators"></a>Indicateurs

Les modèles de stratégie de risque interne définissent le type d’activités à risque que vous souhaitez détecter et examiner. Chaque modèle de stratégie est basé sur des indicateurs spécifiques qui correspondent à des déclencheurs et des activités à risque spécifiques. Tous les indicateurs globaux sont désactivés par défaut et vous devez sélectionner un ou plusieurs indicateurs pour configurer une stratégie de gestion des risques internes.

Les signaux sont collectés et les alertes sont déclenchées par des stratégies lorsque les utilisateurs effectuent des activités liées aux indicateurs. La gestion des risques internes utilise différents types d’événements et d’indicateurs pour collecter des signaux et créer des alertes :

- **Déclenchement d’événements** : événements qui déterminent si un utilisateur est actif dans une stratégie de gestion des risques internes. Si un utilisateur est ajouté à une stratégie de gestion des risques internes n’a pas d’événement déclencheur, l’activité de l’utilisateur n’est pas évaluée par la stratégie. Par exemple, l’utilisateur A est ajouté à une stratégie créée à partir du modèle de stratégie *Vol de données par les utilisateurs sortants* et la stratégie et le connecteur Microsoft 365 HR sont correctement configurés. Tant que l’utilisateur A n’a pas une date d’arrêt signalée par le connecteur RH, les activités de l’utilisateur A ne sont pas évaluées par cette stratégie de gestion des risques internes pour les risques. Un autre exemple d’événement déclencheur est si un utilisateur a une alerte de stratégie DLP *de gravité élevée* lors de l’utilisation de *stratégies de fuites de données* .
- **Indicateurs de paramètres globaux** : les indicateurs activés dans les paramètres globaux pour la gestion des risques internes définissent à la fois les indicateurs disponibles pour la configuration dans les stratégies et les types de signaux d’activité utilisateur collectés par la gestion des risques internes. Par exemple, si un utilisateur copie des données vers des services de stockage cloud personnels ou des appareils de stockage portables et que ces indicateurs sont sélectionnés uniquement dans les paramètres globaux, cette activité sera disponible pour révision dans l’Explorateur d’activités. Toutefois, étant donné que cette activité n’a pas été définie dans une stratégie de gestion des risques internes, un score de risque n’est pas attribué à l’activité ou ne génère pas d’alerte.
- **Indicateurs de stratégie** : les indicateurs inclus dans les stratégies de gestion des risques internes sont utilisés pour déterminer un score de risque pour un utilisateur dans l’étendue. Les indicateurs de stratégie sont activés à partir des indicateurs définis dans les paramètres globaux et ne sont activés qu’après qu’un événement de déclenchement s’est produit pour un utilisateur.  Voici quelques exemples d’indicateurs de stratégie lorsqu’un utilisateur copie des données vers des services de stockage cloud personnels ou des appareils de stockage portables, si un compte d’utilisateur est supprimé d’Azure Active Directory ou si un utilisateur partage des fichiers et dossiers internes avec des parties externes non autorisées.

Certains indicateurs de stratégie et séquences peuvent également être utilisés pour personnaliser les événements de déclenchement pour des modèles de stratégie spécifiques. Lorsqu’ils sont configurés dans l’Assistant Stratégie pour les *modèles Fuites de données générales* ou *Fuites de données par les utilisateurs prioritaires* , ces indicateurs ou séquences vous offrent plus de flexibilité et de personnalisation pour vos stratégies et lorsque les utilisateurs sont dans l’étendue d’une stratégie. En outre, vous pouvez définir des seuils d’activité individuels pour ces indicateurs de déclenchement pour un contrôle plus précis dans une stratégie.

Les indicateurs de stratégie sont segmentés dans les domaines suivants. Vous pouvez choisir les indicateurs pour activer et personnaliser les limites d’événements d’indicateur pour chaque niveau d’indicateur lors de la création d’une stratégie de risque interne :

- **Indicateurs Office** : ceux-ci incluent des indicateurs de stratégie pour les sites SharePoint, Microsoft Teams et la messagerie électronique.
- **Indicateurs d’appareil** : il s’agit notamment d’indicateurs de stratégie pour l’activité, comme le partage de fichiers sur le réseau ou avec des appareils. Les indicateurs incluent les activités impliquant tous les types de fichiers, à l’exception de l’activité de fichiers exécutables (.exe) et de bibliothèque de liens dynamiques (.dll). Si vous sélectionnez *Indicateurs* d’appareil, l’activité est traitée pour les appareils avec Windows 10 build 1809 ou une version ultérieure et macOS (trois dernières versions publiées). Pour les appareils Windows et macOS, vous devez d’abord intégrer les appareils au portail de conformité. Les indicateurs d’appareil incluent également la détection de signal de navigateur pour aider votre organisation à détecter et à agir sur les signaux d’exfiltration pour les fichiers non exécutables affichés, copiés, partagés ou imprimés dans Microsoft Edge et Google Chrome. Pour plus d’informations sur la configuration des appareils Windows pour l’intégration avec les risques internes, consultez la section [Activer les indicateurs d’appareil et intégrer des appareils Windows](insider-risk-management-settings.md#OnboardDevices) dans cet article. Pour plus d’informations sur la configuration des appareils macOS pour l’intégration avec les risques internes, consultez la section Activer les indicateurs d’appareil et intégrer des appareils macOS dans cet article. Pour plus d’informations sur la détection des signaux du navigateur, consultez [En savoir plus sur et configurer la détection des signaux du navigateur de gestion des risques internes](insider-risk-management-browser-support.md).
- Indicateur de violation de stratégie de **sécurité (préversion)** : il s’agit des indicateurs de Microsoft Defender pour point de terminaison liés à l’installation de logiciels non approuvés ou malveillants ou au contournement des contrôles de sécurité. Pour recevoir des alertes dans la gestion des risques internes, vous devez disposer d’une licence Defender pour point de terminaison active et de l’intégration des risques internes activée. Pour plus d’informations sur la configuration de Defender pour point de terminaison pour l’intégration de la gestion des risques internes, consultez [Configurer des fonctionnalités avancées dans Microsoft Defender pour point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/advanced-features\#share-endpoint-alerts-with-microsoft-compliance-center).
- **Indicateurs d’accès aux dossiers médicaux (préversion)** : ceux-ci incluent des indicateurs de stratégie pour l’accès aux dossiers médicaux des patients. Par exemple, les tentatives d’accès aux dossiers médicaux des patients dans vos journaux système de dossiers médicaux électroniques (DME) peuvent être partagées avec les stratégies de gestion des risques internes en matière de santé. Pour recevoir ces types d’alertes dans la gestion des risques internes, vous devez disposer d’un connecteur de données spécifique aux soins de santé et du connecteur de données RH configuré.
- **Indicateurs d’accès physique (préversion)** : ceux-ci incluent des indicateurs de stratégie pour l’accès physique aux ressources sensibles. Par exemple, les tentatives d’accès à une zone restreinte dans vos journaux système de badging physique peuvent être partagées avec des stratégies de gestion des risques internes. Pour recevoir ces types d’alertes dans la gestion des risques internes, vous devez avoir des ressources physiques prioritaires activées dans la gestion des risques internes et le [connecteur de données de badging physique](import-physical-badging-data.md) configuré. Pour en savoir plus sur la configuration de l’accès physique, consultez la [section Accès physique prioritaire](#priority-physical-assets-preview) dans cet article.
- **indicateurs Microsoft Defender for Cloud Apps (préversion)** : ceux-ci incluent des indicateurs de stratégie provenant d’alertes partagées de Defender for Cloud Apps. La détection des anomalies activée automatiquement dans Defender for Cloud Apps commence immédiatement à détecter et à rassembler les résultats, en ciblant de nombreuses anomalies comportementales sur vos utilisateurs et les machines et appareils connectés à votre réseau. Pour inclure ces activités dans les alertes de stratégie de gestion des risques internes, sélectionnez un ou plusieurs indicateurs dans cette section. Pour en savoir plus sur l’analytique et la détection des anomalies de Defender for Cloud Apps, consultez [Obtenir l’analyse comportementale et la détection des anomalies](/cloud-app-security/anomaly-detection-policy).
- **Boosters de score de risque** : il s’agit notamment d’augmenter le score de risque pour une activité supérieure à l’activité habituelle de l’utilisateur pendant une journée ou pour les utilisateurs dont les cas précédents ont été résolus en tant que violation de stratégie. L’activation des rappels de score de risque augmente les scores de risque et la probabilité d’alertes pour ces types d’activités. Pour les activités qui dépassent l’activité habituelle de l’utilisateur pendant un jour, les scores sont augmentés si l’activité détectée s’écarte du comportement typique de l’utilisateur. Pour les utilisateurs dont les cas précédents ont été résolus en tant que violation de stratégie, les scores sont augmentés si un utilisateur a eu plusieurs cas précédemment résolus en tant que violation de stratégie confirmée. Les rappels de score de risque ne peuvent être sélectionnés que si un ou plusieurs indicateurs sont sélectionnés.

Dans certains cas, vous pouvez limiter les indicateurs de stratégie de risque interne appliqués aux stratégies de risque interne de votre organisation. Vous pouvez désactiver les indicateurs de stratégie pour des domaines spécifiques en les désactivant de toutes les stratégies de risque interne dans les paramètres globaux. Les événements de déclenchement peuvent uniquement être modifiés pour les stratégies créées à partir des *modèles Fuites de données générales* ou *Fuites de données par les utilisateurs prioritaires* . Les stratégies créées à partir de tous les autres modèles n’ont pas d’indicateurs ou d’événements de déclenchement personnalisables.

Pour définir les indicateurs de stratégie de risque interne activés dans toutes les stratégies de risque interne, accédez à **Paramètres de** >  risque interne **Indicateurs** et sélectionnez un ou plusieurs indicateurs de stratégie. Les indicateurs sélectionnés dans la page Paramètres **des indicateurs** ne peuvent pas être configurés individuellement lors de la création ou de la modification d’une stratégie de risque interne dans l’Assistant Stratégie.

> [!NOTE]
> Plusieurs heures peuvent être nécessaires pour que les nouveaux utilisateurs ajoutés manuellement s’affichent dans le **tableau de bord Utilisateurs**. L’affichage des activités des 90 jours précédents de ces utilisateurs peut prendre jusqu’à 24 heures. Pour afficher les activités des utilisateurs ajoutés manuellement, sélectionnez l’utilisateur dans le **tableau de bord Utilisateurs** et ouvrez **l’onglet Activité de l’utilisateur** dans le volet d’informations.

### <a name="enable-device-indicators-and-onboard-windows-devices"></a>Activer les indicateurs d’appareil et intégrer des appareils Windows
<a name="OnboardDevices"> </a>

Pour activer la détection des activités à risque sur les appareils Windows et inclure des indicateurs de stratégie pour ces activités, vos appareils Windows doivent répondre aux exigences suivantes et vous devez effectuer les étapes d’intégration suivantes.

#### <a name="step-1-prepare-your-endpoints"></a>Étape 1 : Préparer vos points de terminaison

Assurez-vous que les appareils Windows 10 que vous prévoyez de créer des rapports dans la gestion des risques internes répondent à ces exigences.

1. Doit être en cours d’exécution Windows 10 build x64 1809 ou ultérieure et doit avoir installé la [mise à jour Windows 10 (build du système d’exploitation 17763.1075)](https://support.microsoft.com/help/4537818/windows-10-update-kb4537818) à partir du 20 février 2020.
2. Le compte d’utilisateur utilisé pour se connecter à l’appareil Windows 10 doit être un compte Azure Active Directory (AAD) actif. L’appareil Windows 10 peut être [AAD](/azure/active-directory/devices/concept-azure-ad-join), AAD hybride ou joint à Active Directory, ou inscrit dans AAD.
3. Installez le navigateur Microsoft Edge sur l’appareil de point de terminaison pour détecter les actions relatives à l’activité de chargement dans le cloud. [Télécharger le nouveau Microsoft Edge sur la base de chrome](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium).

#### <a name="step-2-onboarding-devices"></a>Étape 2 : Intégration des appareils
<a name="OnboardStep2"> </a>

Vous devez activer la surveillance des appareils et intégrer vos points de terminaison avant de pouvoir détecter les activités de gestion des risques internes sur un appareil. Les deux actions sont effectuées dans le portail de conformité Microsoft Purview.

Lorsque vous souhaitez intégrer des appareils qui n’ont pas encore été intégrés, vous allez télécharger le script approprié et le déployer comme indiqué dans les étapes suivantes.

Si vous avez déjà intégré des appareils à [Microsoft Defender pour point de terminaison](/windows/security/threat-protection/), ils apparaissent déjà dans la liste des appareils gérés. Suivez [l’étape 3 : Si vous avez intégré des appareils à Microsoft Defender pour point de terminaison](insider-risk-management-settings.md#OnboardStep3) dans la section suivante.

Dans ce scénario de déploiement, vous allez intégrer des appareils qui n’ont pas encore été intégrés et vous souhaitez simplement détecter les activités à risque internes sur Windows 10 appareils.

1. Ouvrez le [Portail de conformité Microsoft Purview](https://compliance.microsoft.com).
2. Ouvrez la page des paramètres du portail de conformité et choisissez **Intégrer des appareils**.

   > [!NOTE]
   > Bien que l’activation de l’intégration des appareils dure généralement environ 60 secondes, patientez jusqu’à 30 minutes avant de contacter le support Microsoft.

3. Sélectionnez **Gestion des appareils** pour ouvrir la liste des **Appareils**. La liste est vide tant que vous n’avez pas intégré de périphériques.
4. Sélectionnez **Intégration** pour lancer le processus d’intégration.
5. Choisissez la façon dont vous souhaitez déployer sur ces appareils supplémentaires dans la liste **Méthode de déploiement** , puis **téléchargez le package**.
6. Suivez les procédures appropriées dans [Outils et méthodes d’intégration pour les ordinateurs Windows 10](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints). Ce lien vous dirige vers une page d’accueil dans laquelle vous pouvez accéder aux procédures Microsoft Defender pour point de terminaison qui correspondent au package de déploiement que vous avez sélectionné à l’étape 5 :
    - Intégrer les ordinateurs Windows 10 utilisant une stratégie de groupe
    - Intégrer les ordinateurs Windows à l’aide du gestionnaire de configuration de point de terminaison Microsoft
    - Intégrer les ordinateurs Windows 10 à l’aide des outils de gestion des appareils mobiles
    - Intégrer les ordinateurs Windows 10 utilisant un script local
    - Intégrer les ordinateurs virtuels d’infrastructure de bureau virtuel (VDI) non persistants.

Une fois que vous avez terminé et que le point de terminaison est intégré, il doit être visible dans la liste des appareils et le point de terminaison commence à signaler les journaux d’activité d’audit à la gestion des risques internes.

> [!NOTE]
> Cette expérience est sous l’application de la licence. Sans la licence requise, les données ne sont pas visibles ni accessibles.

#### <a name="step-3-if-you-have-devices-onboarded-into-microsoft-defender-for-endpoint"></a>Étape 3 : Si vous avez intégré des appareils à Microsoft Defender pour point de terminaison
<a name="OnboardStep3"> </a>

Si Microsoft Defender pour point de terminaison est déjà déployé et que des points de terminaison sont signalés, tous ces points de terminaison apparaissent dans la liste des appareils gérés. Vous pouvez continuer à intégrer de nouveaux appareils à la gestion des risques internes pour étendre la couverture à l’aide de la section [Étape 2 : Intégration des appareils](insider-risk-management-settings.md#OnboardStep2) .

1. Ouvrez le [Portail de conformité Microsoft Purview](https://compliance.microsoft.com).
2. Ouvrez la page des paramètres du portail de conformité et choisissez **Activer la surveillance des appareils**.
3. Sélectionnez **Gestion des appareils** pour ouvrir la liste des **Appareils**. Vous devez voir la liste des appareils qui signalent déjà Microsoft Defender pour point de terminaison.
4. Choisissez **Intégration** si vous avez besoin d’intégrer d’autres appareils.
5. Choisissez le mode de déploiement que vous souhaitez déployer sur ces appareils supplémentaires dans la liste **Méthode de déploiement** , puis **Téléchargez le package**.
6. Suivez les procédures appropriées dans [Outils et méthodes d’intégration pour les ordinateurs Windows 10](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints). Ce lien vous dirige vers une page d’accueil dans laquelle vous pouvez accéder aux procédures Microsoft Defender pour point de terminaison qui correspondent au package de déploiement que vous avez sélectionné à l’étape 5 :
    - Intégrer les ordinateurs Windows 10 utilisant une stratégie de groupe
    - Intégrer les ordinateurs Windows à l’aide du gestionnaire de configuration de point de terminaison Microsoft
    - Intégrer les ordinateurs Windows 10 à l’aide des outils de gestion des appareils mobiles
    - Intégrer les ordinateurs Windows 10 utilisant un script local
    - Intégrer les ordinateurs virtuels d’infrastructure de bureau virtuel (VDI) non persistants.

Une fois que vous avez terminé et que le point de terminaison est intégré, il doit être visible sous la table **Appareils** et le point de terminaison commence à signaler les journaux d’activité d’audit à la gestion des risques internes.

> [!NOTE]
>Cette expérience est sous l’application de la licence. Sans la licence requise, les données ne sont pas visibles ni accessibles.

### <a name="enable-device-indicators-and-onboard-macos-devices"></a>Activer les indicateurs d’appareil et intégrer des appareils macOS

Les appareils macOS (Catalina 10.15 ou version ultérieure) peuvent être intégrés à Microsoft 365 pour prendre en charge les stratégies de gestion des risques internes à l’aide de Intune ou JAMF Pro. Pour plus d’informations et pour obtenir des conseils de configuration, consultez [Vue d’ensemble des appareils macOS dans Microsoft 365 (préversion).](device-onboarding-macos-overview.md)

### <a name="indicator-level-settings-preview"></a>Paramètres au niveau de l’indicateur (préversion)

Lors de la création d’une stratégie dans l’Assistant Stratégie, vous pouvez configurer la façon dont le nombre quotidien d’événements à risque doit influencer le score de risque pour les alertes de risque interne. Ces paramètres d’indicateur vous aident à contrôler la façon dont le nombre d’occurrences d’événements à risque dans votre organisation doit affecter le score de risque, et donc la gravité de l’alerte associée, pour ces événements. Si vous préférez, vous pouvez également choisir de conserver les niveaux de seuil d’événement par défaut recommandés par Microsoft pour tous les indicateurs activés.

Par exemple, vous décidez d’activer les indicateurs SharePoint dans les paramètres de stratégie de risque interne et de **définir des seuils personnalisés pour les** événements SharePoint lors de la configuration des indicateurs pour une nouvelle stratégie de *risque interne Fuites de données* . Dans l’Assistant Stratégie de risque interne, vous configurez trois niveaux d’événements quotidiens différents pour chaque indicateur SharePoint afin d’influencer le score de risque pour les alertes associées à ces événements.

![Paramètres d’indicateur personnalisés de gestion des risques internes.](../media/insider-risk-custom-indicators.png)

Pour le premier niveau d’événement quotidien, vous définissez le seuil à *10 événements ou plus par jour* pour un impact inférieur sur le score de risque pour les événements, *20 événements ou plus par jour* pour un impact moyen sur le score de risque pour les événements, et *30 événements ou plus par jour* , un impact plus élevé sur le score de risque pour les événements. Ces paramètres signifient en fait :

- Si 1 à 9 événements SharePoint se produisent après le déclenchement de l’événement, les scores de risque sont peu affectés et ont tendance à ne pas générer d’alerte.
- Si 10 à 19 événements SharePoint se produisent après un événement déclencheur, le score de risque est intrinsèquement inférieur et les niveaux de gravité des alertes ont tendance à être bas.
- Si 20 à 29 événements SharePoint se produisent après un déclenchement, le score de risque est intrinsèquement plus élevé et les niveaux de gravité des alertes ont tendance à être à un niveau moyen.
- Si au moins 30 événements SharePoint se produisent après un déclenchement, le score de risque est intrinsèquement plus élevé et les niveaux de gravité des alertes ont tendance à être élevés.

Une autre option pour les seuils de stratégie consiste à affecter l’événement déclencheur de stratégie à une activité supérieure à la quantité habituelle d’activité quotidienne pour les utilisateurs. Au lieu d’être défini par des paramètres de seuil spécifiques, chaque seuil est personnalisé dynamiquement pour les activités anormales détectées pour les utilisateurs de stratégie dans l’étendue. Si l’activité de seuil pour les activités anormales est prise en charge pour un indicateur individuel, vous pouvez sélectionner **Activité est au-dessus de l’activité habituelle de l’utilisateur pour la journée** dans l’Assistant Stratégie pour cet indicateur. Si cette option n’est pas répertoriée, le déclenchement d’activité anormale n’est pas disponible pour l’indicateur. Si **l’activité se trouve au-dessus de l’activité habituelle de l’utilisateur pour le jour, l’option** est répertoriée pour un indicateur, mais n’est pas sélectionnable, vous devez activer cette option dans **paramètres de** >  risque insider **Indicateurs de stratégie**.

## <a name="policy-timeframes"></a>Délais de la stratégie

Les délais de stratégie vous permettent de définir les périodes passées et futures qui sont déclenchées après les correspondances de stratégie basées sur les événements et les activités des modèles de stratégie de gestion des risques internes. Selon le modèle de stratégie que vous choisissez, les délais de stratégie suivants sont disponibles :

- **Fenêtre d’activation** : disponible pour tous les modèles de stratégie, la *fenêtre Activation* est le nombre défini de jours pendant lesquels la fenêtre s’active **après** un événement de déclenchement. La fenêtre s’active pendant 1 à 30 jours après qu’un événement de déclenchement se produit pour tout utilisateur affecté à la stratégie. Par exemple, vous avez configuré une stratégie de gestion des risques internes et défini la *fenêtre Activation* sur 30 jours. Plusieurs mois se sont écoulés depuis que vous avez configuré la stratégie, et un événement de déclenchement se produit pour l’un des utilisateurs inclus dans la stratégie. L’événement de déclenchement active la *fenêtre Activation* et la stratégie est active pour cet utilisateur pendant 30 jours après que l’événement de déclenchement s’est produit.
- **Détection d’activité passée** : disponible pour tous les modèles de stratégie, la *détection d’activité passée* est le nombre défini de jours pendant lesquels la fenêtre s’active **avant** un événement de déclenchement. La fenêtre s’active pendant 0 à 90 jours avant qu’un événement de déclenchement ne se produise pour tout utilisateur affecté à la stratégie. Par exemple, vous avez configuré une stratégie de gestion des risques internes et défini la *détection de l’activité passée* sur 90 jours. Plusieurs mois se sont écoulés depuis que vous avez configuré la stratégie, et un événement de déclenchement se produit pour l’un des utilisateurs inclus dans la stratégie. L’événement déclencheur active la *détection de l’activité passée* et la stratégie collecte les activités historiques de cet utilisateur pendant 90 jours avant l’événement de déclenchement.

![Paramètres de délai de gestion des risques internes.](../media/insider-risk-settings-timeframes.png)

## <a name="intelligent-detections"></a>Détections intelligentes

Les paramètres de détection intelligente permettent d’affiner la façon dont les détections d’activités à risque sont traitées pour les alertes. Dans certaines circonstances, vous devrez peut-être définir des types de fichiers à ignorer, ou vous souhaitez appliquer un niveau de détection pour les événements quotidiens afin d’augmenter les scores de risque pour les utilisateurs. Utilisez ces paramètres pour contrôler les exclusions de type de fichier, améliorer le score de risque pour les activités inhabituelles et les limites de volume de fichiers.

### <a name="file-activity-detection"></a>Détection de l’activité de fichier

Pour exclure des types de fichiers spécifiques de toutes les stratégies de gestion des risques internes, entrez des extensions de type de fichier séparées par des virgules. Par exemple, pour exclure certains types de fichiers musicaux des correspondances de stratégie, vous pouvez entrer *aac,mp3,wav,wma* dans le champ **exclusions de type de fichier**. Les fichiers avec ces extensions sont ignorés par toutes les stratégies de gestion des risques internes.

### <a name="alert-volume"></a>Volume d’alerte

Les activités des utilisateurs détectées par les stratégies de risque interne se voient attribuer un score de risque spécifique, qui à son tour détermine la gravité de l’alerte (faible, moyen, élevé). Par défaut, nous allons générer un certain nombre d’alertes de gravité faible, moyenne et élevée, mais vous pouvez augmenter ou diminuer le volume en fonction de vos besoins. Pour ajuster le volume d’alertes pour toutes les stratégies de gestion des risques internes, choisissez l’un des paramètres suivants :

- **Moins d’alertes** : vous verrez toutes les alertes de gravité élevée, moins d’alertes de gravité moyenne et aucune alerte de gravité faible. Ce niveau de paramètre signifie que vous risquez de manquer des vrais positifs.
- **Volume par défaut** : vous verrez toutes les alertes de gravité élevée et une quantité équilibrée d’alertes de gravité moyenne et faible.
- **Autres alertes** : vous verrez toutes les alertes de gravité moyenne et élevée et la plupart des alertes de gravité faible. Ce niveau de paramètre peut entraîner davantage de faux positifs.

### <a name="microsoft-defender-for-endpoint-alert-statuses"></a>Microsoft Defender pour point de terminaison état des alertes

[Microsoft Defender pour point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) est une plateforme de sécurité de point de terminaison d’entreprise conçue pour aider les réseaux d’entreprise à prévenir, détecter, examiner et répondre aux menaces avancées. Pour avoir une meilleure visibilité des violations de sécurité dans votre organisation, vous pouvez importer et filtrer les alertes Defender pour point de terminaison pour les activités utilisées dans les stratégies créées à partir de modèles de stratégie de violation de sécurité de gestion des risques internes.

Selon les types de signaux qui vous intéressent, vous pouvez choisir d’importer des alertes dans la gestion des risques internes en fonction de l’état de tri des alertes Defender pour point de terminaison. Vous pouvez définir un ou plusieurs des états de tri des alertes suivants dans les paramètres globaux à importer :

- Inconnu
- Nouveau
- En cours
- Résolu

Les alertes de Defender pour point de terminaison sont importées quotidiennement. En fonction de l’état de tri que vous choisissez, vous pouvez voir plusieurs activités utilisateur pour la même alerte lorsque l’état de triage change dans Defender pour point de terminaison.

Par exemple, si vous sélectionnez *Nouveau*, *En cours* et *Résolu* pour ce paramètre, lorsqu’une alerte Microsoft Defender pour point de terminaison est générée et que l’état est *Nouveau*, une activité d’alerte initiale est importée pour l’utilisateur à risque interne. Lorsque l’état de triage de Defender pour point de terminaison passe à *En cours*, une deuxième activité pour cette alerte est importée pour l’utilisateur à risque interne. Lorsque l’état final du triage Defender pour point de terminaison *résolu* est défini, une troisième activité pour cette alerte est importée pour l’utilisateur à risque interne. Cette fonctionnalité permet aux enquêteurs de suivre la progression des alertes Defender pour point de terminaison et de choisir le niveau de visibilité requis par leur investigation.

> [!IMPORTANT]
> Microsoft Defender pour point de terminaison doit être configuré dans votre organisation et vous devez activer Microsoft Defender pour point de terminaison pour l’intégration de la gestion des risques internes dans le Centre de sécurité Microsoft Defender pour importer les alertes de violation de la sécurité. Pour plus d’informations sur la configuration de Microsoft Defender pour point de terminaison pour l’intégration de la gestion des risques internes, consultez [Configurer des fonctionnalités avancées dans Defender pour le point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/advanced-features\#share-endpoint-alerts-with-microsoft-compliance-center).

### <a name="domains"></a>Domaines

Les paramètres de domaine vous aident à définir des niveaux de risque pour les activités dans des domaines spécifiques. Ces activités incluent le partage de fichiers, l’envoi de messages électroniques, le téléchargement ou le chargement de contenu. En spécifiant des domaines dans ces paramètres, vous pouvez augmenter ou diminuer le score de risque pour l’activité qui a lieu avec ces domaines.

Utilisez Ajouter un domaine pour définir un domaine pour chacun des paramètres de domaine. En outre, vous pouvez utiliser des caractères génériques pour aider à faire correspondre des variantes de domaines racines ou de sous-domaines. Par exemple, pour spécifier sales.wingtiptoys.com et support.wingtiptoys.com, vous utilisez l’entrée générique « *.wingtiptoys.com » pour faire correspondre ces sous-domaines (et tout autre sous-domaine au même niveau). Pour spécifier des sous-domaines multiniveaux pour un domaine racine, vous devez cocher la case **Inclure des sous-domaines multiniveaux** .

Pour chacun des paramètres de domaine suivants, vous pouvez entrer jusqu’à 500 domaines :

- **Domaines non autorisés :** En spécifiant des domaines non autorisés, l’activité qui a lieu avec ces domaines aura des scores *de risque plus élevés* . Voici quelques exemples d’activités impliquant le partage de contenu avec quelqu’un (comme l’envoi d’e-mails à une personne avec une adresse gmail.com) et lorsque les utilisateurs téléchargent du contenu sur un appareil à partir de l’un de ces domaines non autorisés.
- **Domaines autorisés :** Certaines activités liées aux domaines autorisés sont ignorées par vos stratégies et ne génèrent pas d’alertes. Ces activités sont les suivantes :

    - Email envoyées à des domaines externes
    - Fichiers, dossiers, sites partagés avec des domaines externes
    - Fichiers chargés vers des domaines externes (à l’aide du navigateur Microsoft Edge)

    En spécifiant les domaines autorisés dans les paramètres, cette activité avec ces domaines est traitée de la même manière que l’activité de l’organisation interne. Par exemple, les domaines ajoutés ici à des activités peuvent impliquer le partage de contenu avec une personne extérieure à votre organisation (par exemple, l’envoi d’e-mails à une personne avec une adresse gmail.com).

- **Domaines tiers :** Si votre organisation utilise des domaines tiers à des fins professionnelles (par exemple, le stockage cloud), incluez-les ici afin que vous puissiez recevoir des alertes relatives à l’activité liée à l’indicateur d’appareil *Utiliser un navigateur pour télécharger du contenu à partir d’un site tiers*.
 
### <a name="sensitive-info-types-exclusion"></a>Exclusion des types d’informations sensibles

En excluant les types d’informations sensibles, vous pouvez spécifier les types mappés aux indicateurs et déclencheurs impliquant des activités liées aux fichiers pour Point de terminaison, SharePoint, Teams, OneDrive et Exchange. Pour les fichiers qui contiennent des types d’informations sensibles identifiés ici, ils seront évalués en tant qu’activités impliquant du contenu lié aux types d’informations sensibles. Pour obtenir la liste complète, consultez [Définitions d’entité de type d’informations sensibles](sensitive-information-type-entity-definitions.md).

Vous pouvez sélectionner les types d’informations sensibles à exclure de la liste de tous les types disponibles (out-of-box et custom) disponibles dans le locataire. La gestion des risques internes exclut plusieurs types d’informations sensibles par défaut, tels que le numéro de routage ABA. Vous pouvez choisir jusqu’à 100 types d’informations sensibles à exclure.

> [!NOTE]
> La liste d’exclusion des types d’informations sensibles est prioritaire sur la liste de [contenu prioritaire](insider-risk-management-policies.md#prioritize-content-in-policies) .

Pour ajouter des types d’informations sensibles à exclure, procédez comme suit :

1. Dans le portail de conformité, accédez à Gestion **des** >  risques internes **Paramètres** > **Détections intelligentes**. 
2. Dans la section **Types d’informations sensibles** , sélectionnez **Ajouter des types d’informations sensibles à exclure**.
3. Dans le volet **Ajouter ou modifier un type d’informations sensibles** , sélectionnez les types que vous souhaitez exclure.
4. Sélectionnez **Ajouter** accepter les modifications ou **Annuler** pour ignorer les modifications. 

Pour supprimer une exclusion de type d’informations sensibles, sélectionnez l’exclusion et **Supprimer**.

### <a name="file-path-exclusions"></a>Exclusions de chemin d’accès de fichier

En définissant des chemins d’accès de fichier à exclure, les activités des utilisateurs qui correspondent à des indicateurs spécifiques et qui se produisent dans ces emplacements de chemin d’accès de fichier ne génèrent pas d’alertes de stratégie. Par exemple, la copie ou le déplacement de fichiers vers un dossier système ou un chemin de partage réseau. Vous pouvez entrer jusqu’à 500 chemins d’accès de fichiers pour exclusion.

Pour ajouter des chemins d’accès de fichier à exclure, procédez comme suit :

1. Dans le portail de conformité, accédez à Gestion **des** >  risques internes **Paramètres** > **Détections intelligentes**. 
2. Dans la section **Exclusion du chemin d’accès** au fichier, sélectionnez **Ajouter des chemins d’accès de fichiers à exclure**.
3. Dans le volet **Ajouter un chemin d’accès de fichier** , entrez un chemin d’accès de partage réseau ou d’appareil exact à exclure du scoring des risques. Vous pouvez également utiliser * et *([0-9]) pour indiquer des dossiers et des sous-dossiers spécifiques à exclure.
4. Sélectionnez **Ajouter des chemins d’accès de fichier** à exclure pour configurer les exclusions de chemin d’accès de fichier ou **Fermer** pour ignorer les modifications. 

Pour supprimer une exclusion de chemin d’accès de fichier, sélectionnez l’exclusion de chemin d’accès de fichier, puis sélectionnez **Supprimer**.

### <a name="default-file-path-exclusions"></a>Exclusions de chemin d’accès de fichier par défaut

Par défaut, plusieurs chemins d’accès aux fichiers sont automatiquement exclus de la génération d’alertes de stratégie. Les activités de ces chemins de fichier sont généralement sans gravité et peuvent potentiellement augmenter le volume d’alertes non exploitables. Si nécessaire, vous pouvez annuler la sélection de ces exclusions de chemin d’accès de fichier par défaut afin d’activer le scoring des risques pour les activités dans ces emplacements.

Les exclusions de chemin d’accès de fichier par défaut sont les suivantes :

- \Users\\\*\AppData
- \Users\\\*\AppData\Local
- \Users\\\*\AppData\Local\Roaming
- \Users\\\*\AppData\Local\Local\Temp

Les caractères génériques dans ces chemins indiquent que tous les niveaux de dossier entre \Users et \AppData sont inclus dans l’exclusion. Par exemple, les activités dans *C:\Users\Test1\AppData\Local* et *C:\Users\Test2\AppData\Local*, *C:\Users\Test3\AppData\Local* (et ainsi de suite) sont toutes incluses et non évaluées pour les risques dans le cadre de la sélection d’exclusion *\Users\\\*\AppData\Local* .

### <a name="site-exclusions"></a>Exclusions de site

Configurez des exclusions d’URL de site pour empêcher les activités à risque potentielles qui se produisent dans SharePoint (et les sites SharePoint associés aux sites de canal d’équipe) de générer des alertes de stratégie. Vous pouvez envisager d’exclure les sites et les canaux qui contiennent des fichiers et des données non sensibles qui peuvent être partagés avec les parties prenantes ou le public. Vous pouvez entrer jusqu’à 500 chemins d’URL de site à exclure.

Pour ajouter des chemins d’URL de site à exclure, procédez comme suit :

1. Dans le portail de conformité, accédez à Gestion **des** >  risques internes **Paramètres** > **Détections intelligentes**.
2. Dans la section **Exclusion de l’URL du site** , sélectionnez **Ajouter ou modifier des sites SharePoint**.
3. Dans le volet **Ajouter ou modifier des sites SharePoint** , entrez ou recherchez le site SharePoint à exclure du scoring de risque. Vous verrez uniquement les sites SharePoint auxquels vous êtes autorisé à accéder.
4. Sélectionnez **Ajouter** pour configurer les exclusions d’URL de site ou **Annuler** pour ignorer les modifications.

Pour modifier les chemins d’URL de site à exclure, procédez comme suit :

1. Dans le portail de conformité, accédez à Gestion **des** >  risques internes **Paramètres** > **Détections intelligentes**.
2. Dans la section **Exclusion de l’URL du site** , sélectionnez **Ajouter ou modifier des sites SharePoint**.
3. Dans le volet **Ajouter ou modifier des sites SharePoint** , entrez ou recherchez le site SharePoint à exclure du scoring de risque. Vous verrez uniquement les sites SharePoint auxquels vous êtes autorisé à accéder.
4. Sélectionnez **Modifier** pour configurer les exclusions d’URL de site ou **Annuler** pour ignorer les modifications.

Pour supprimer une exclusion d’URL de site, sélectionnez l’exclusion d’URL du site, puis **sélectionnez Supprimer**.

### <a name="keyword-exclusion"></a>Exclusion de mot clé

Configurez des exclusions pour les mots clés qui apparaissent dans les noms de fichiers, les chemins d’accès aux fichiers ou les lignes d’objet des messages électroniques. Cela permet aux organisations qui doivent réduire le bruit d’alerte potentiel en raison de l’indicateur de termes bénins spécifiés pour votre organisation. Ces activités liées aux fichiers ou aux sujets de courrier contenant le mot clé sont ignorées par vos stratégies de gestion des risques internes et ne génèrent pas d’alertes. Vous pouvez entrer jusqu’à 500 mots clés à exclure. 

Utilisez le champ **Exclure uniquement s’il ne contient pas** de champ pour définir des regroupements spécifiques de termes à ignorer pour l’exclusion, par exemple, si vous souhaitez exclure le mot clé « training », mais pas exclure « formation de conformité », vous devez entrer « conformité » (ou « formation de conformité ») dans l’exclusion **uniquement s’il ne contient pas** le champ et « training » dans le champ **Mais ne contient** pas.

Si vous souhaitez simplement exclure des termes autonomes spécifiques, entrez les termes dans le **champ Mais ne contient** que.

Pour ajouter des mots clés autonomes à exclure, procédez comme suit :

1. Dans le portail de conformité, accédez à Gestion **des** >  risques internes **Paramètres** > **Détections intelligentes**.
2. Dans la section **Exclusion de mot clé** , entrez les mots clés autonomes dans le champ **Mais ne contient** pas.
3. Sélectionnez **Enregistrer** pour configurer les exclusions de mot clé.

Pour supprimer un mot clé autonome à exclure, procédez comme suit :

1. Dans le portail de conformité, accédez à Gestion **des** >  risques internes **Paramètres** > **Détections intelligentes**. 
2. Dans la section **Exclusion de mot clé** , sélectionnez le *X* pour le mot clé autonome spécifique dans le champ **Mais ne contient** . Répétez cette opération si nécessaire pour supprimer plusieurs mots clés.
3. Sélectionnez **Enregistrer** pour supprimer les exclusions de mot clé.

## <a name="export-alerts"></a>Exporter des alertes

Les informations d’alerte de gestion des risques internes sont exportables vers les solutions SIEM (Security Information and Event Management) et SOAR (Security Orchestration Automated Response) à l’aide du [schéma d’API Activité de gestion Office 365](/office/office-365-management-api/office-365-management-activity-api-schema#security-and-compliance-alerts-schema). Vous pouvez utiliser les API d’activité de gestion Office 365 pour exporter des informations d’alerte vers d’autres applications que votre organisation peut utiliser pour gérer ou agréger des informations sur les risques internes. Les informations d’alerte sont exportées et disponibles toutes les 60 minutes via les API d’activité de gestion Office 365.

Si votre organisation utilise Microsoft Sentinel, vous pouvez également utiliser le connecteur de données de gestion des risques internes prête à l’emploi pour importer des informations d’alerte de risque interne dans Sentinel. Pour plus d’informations, consultez [Gestion des risques internes (IRM) (préversion)](/azure/sentinel/data-connectors-reference#microsoft-365-insider-risk-management-irm-preview) dans l’article Microsoft Sentinel.

>[!IMPORTANT]
>Pour maintenir l’intégrité référentielle pour les utilisateurs qui ont des alertes ou des cas de risque interne dans Microsoft 365 ou d’autres systèmes, l’anonymisation des noms d’utilisateur n’est pas conservée pour les alertes exportées. Les alertes exportées affichent les noms d’utilisateur pour chaque alerte.

Pour utiliser les API pour passer en revue les informations d’alerte de risque interne :

1. Activez Office 365 prise en charge de l’API Activité de gestion dans **Paramètres** >  **de gestion des** >  risques internes **Alertes d’exportation**. Par défaut, ce paramètre est désactivé pour votre organisation Microsoft 365.
2. Filtrez les activités d’audit Office 365 *courantes par SecurityComplianceAlerts*.
3. Filtrez *SecurityComplianceAlerts* par la catégorie *InsiderRiskManagement* .

![Paramètres d’alerte d’exportation de gestion des risques internes.](../media/insider-risk-settings-export.png)

Les informations d’alerte contiennent des informations provenant du schéma d’alerte de sécurité et de conformité et du schéma commun de l’API activité de gestion Office 365.

Les champs et valeurs suivants sont exportés pour les alertes de gestion des risques internes pour le schéma d’alerte Sécurité & Conformité :

| **Paramètre d’alerte** | **Description** |
|:------------------|:----------------|
| AlertType | Le type de l’alerte est *Personnalisé*.  |
| AlertId | GUID de l’alerte. Les alertes de gestion des risques internes sont mutables. À mesure que l’état de l’alerte change, un nouveau journal avec le même Id d’alerte est généré. Cet Id d’alerte peut être utilisé pour mettre en corrélation les mises à jour d’une alerte. |
| Catégorie | La catégorie de l’alerte est *InsiderRiskManagement*. Cette catégorie peut être utilisée pour distinguer ces alertes des autres alertes de sécurité & conformité. |
| Comments | Commentaires par défaut pour l’alerte. Les valeurs sont *Nouvelle alerte* (journalisée lors de la création d’une alerte) et *Alerte mise à jour* (journalisée en cas de mise à jour d’une alerte). Utilisez alertID pour mettre en corrélation les mises à jour d’une alerte. |
| Données | Les données de l’alerte incluent l’ID utilisateur unique, le nom d’utilisateur principal et la date et l’heure (UTC) auxquelles l’utilisateur a été déclenché dans une stratégie. |
| Nom | Nom de la stratégie de gestion des risques internes qui a généré l’alerte. |
| PolicyId | GUID de la stratégie de gestion des risques internes qui a déclenché l’alerte. |
| Severity | Gravité de l’alerte. Les valeurs sont *High*, *Medium* ou *Low*. |
| Source | Source de l’alerte. La valeur est *Office 365 Security & Compliance*. |
| État | État de l’alerte. Les valeurs sont *Actif* (*Révision des besoins* dans le risque interne), *Examen* (*Confirmé* dans le risque interne), *Résolu* (*Résolu* dans le risque interne), *Ignoré* (*Ignoré* dans le risque interne). |
| Version | Version du schéma d’alerte de sécurité et de conformité. |

Les champs et valeurs suivants sont exportés pour les alertes de gestion des risques internes pour le [schéma commun de l’API Activité de gestion Office 365](/office/office-365-management-api/office-365-management-activity-api-schema#common-schema).

- UserId
- ID
- RecordType
- CreationTime
- Opération
- OrganizationId
- UserType
- UserKey

## <a name="priority-user-groups-preview"></a>Groupes d’utilisateurs prioritaires (préversion)

Les utilisateurs de votre organisation peuvent avoir différents niveaux de risque en fonction de leur position, de leur niveau d’accès aux informations sensibles ou de leur historique des risques. La hiérarchisation de l’examen et du scoring des activités de ces utilisateurs peut vous aider à alerter sur les risques potentiels susceptibles d’avoir des conséquences plus élevées pour votre organisation. Les groupes d’utilisateurs prioritaires dans la gestion des risques internes permettent de définir les utilisateurs de votre organisation qui ont besoin d’une inspection plus approfondie et d’un scoring de risque plus sensible. Associés aux violations de stratégie de *sécurité par les utilisateurs prioritaires et aux* *fuites de données par les modèles de stratégie d’utilisateurs prioritaires* , les utilisateurs ajoutés à un groupe d’utilisateurs prioritaires ont une probabilité accrue d’alertes à risque interne et d’alertes avec des niveaux de gravité plus élevés.

![Paramètres de groupe d’utilisateurs prioritaires de gestion des risques internes.](../media/insider-risk-settings-priority-users.png)

Au lieu d’être ouverts à l’examen de tous les analystes et enquêteurs, les groupes d’utilisateurs prioritaires peuvent également avoir besoin de limiter les activités de révision à des utilisateurs spécifiques ou à des groupes de rôles à risque internes. Vous pouvez choisir d’affecter des utilisateurs individuels et des groupes de rôles pour examiner les utilisateurs, les alertes, les cas et les rapports pour chaque groupe d’utilisateurs prioritaire. Les groupes d’utilisateurs prioritaires peuvent avoir des autorisations de révision attribuées aux groupes de rôles intégrés gestion *des risques internes*, *analystes de gestion des risques internes et enquêteurs* de *gestion des risques internes* , à un ou plusieurs de ces groupes de rôles, ou à une sélection personnalisée d’utilisateurs.

Par exemple, vous devez vous protéger contre les fuites de données pour un projet hautement confidentiel où les utilisateurs ont accès à des informations sensibles. Vous choisissez de créer un groupe d’utilisateurs *prioritaires d’utilisateurs* de *projet confidentiels* pour les utilisateurs de votre organisation qui travaillent sur ce projet. En outre, ce groupe d’utilisateurs prioritaire ne doit pas avoir d’utilisateurs, d’alertes, de cas et de rapports associés au groupe visibles par tous les administrateurs, analystes et enquêteurs de gestion des risques internes par défaut. Dans **Paramètres**, vous créez le groupe *Utilisateurs prioritaires du projet confidentiel* et affectez deux utilisateurs en tant que réviseurs qui peuvent afficher les données relatives aux groupes. À l’aide de l’Assistant Stratégie et du modèle de stratégie *Fuites de données par les utilisateurs prioritaires* , vous créez une stratégie et affectez le groupe Utilisateurs prioritaires du *projet confidentiel* à la stratégie. Les activités examinées par la stratégie pour les membres du groupe d’utilisateurs prioritaires du *projet confidentiel* sont plus sensibles aux risques et les activités de ces utilisateurs seront plus susceptibles de générer une alerte et d’avoir des alertes avec des niveaux de gravité plus élevés.

### <a name="create-a-priority-user-group"></a>Créer un groupe d’utilisateurs prioritaires

Pour créer un groupe d’utilisateurs prioritaires, vous allez utiliser des contrôles de définition dans la solution **de gestion des risques internes** dans le portail de conformité Microsoft Purview. Pour créer un groupe d’utilisateurs prioritaire, vous devez être membre du groupe de rôles *Gestion des risques internes* ou *Gestion des risques internes Administration*.

Pour créer un groupe d’utilisateurs prioritaire, procédez comme suit :

1. Dans la [portail de conformité Microsoft Purview](https://compliance.microsoft.com), accédez à **Gestion des risques internes** et sélectionnez **Paramètres des risques internes**.
2. Sélectionnez la page **Groupes d’utilisateurs prioritaires (préversion).**
3. Dans la page **Groupes d’utilisateurs prioritaires (préversion),** sélectionnez **Créer un groupe d’utilisateurs prioritaires** pour démarrer l’Assistant Création de groupe.
4. Dans la page **Nom et description** , renseignez les champs suivants :
    - **Nom (obligatoire)** : entrez un nom convivial pour le groupe d’utilisateurs prioritaire. Vous ne pouvez pas modifier le nom du groupe d’utilisateurs prioritaire une fois que vous avez terminé l’Assistant.
    - **Description (facultatif)** : entrez une description pour le groupe d’utilisateurs prioritaire.
5. Sélectionnez **Suivant** pour continuer.
6. Dans la page **Choisir des membres** , sélectionnez **Choisir les membres** à rechercher et sélectionnez les comptes d’utilisateur à extension messagerie inclus dans le groupe ou cochez la case **Sélectionner tout** pour ajouter tous les utilisateurs de votre organisation au groupe. Sélectionnez **Ajouter** pour continuer ou **Annuler** pour fermer sans ajouter d’utilisateurs au groupe.
7. Sélectionnez **Suivant** pour continuer.
8. Dans la page **Choisir qui peut afficher ce groupe** , vous devez définir qui peut examiner les utilisateurs, les alertes, les cas et les rapports pour le groupe d’utilisateurs prioritaire. Au moins un groupe de rôles de gestion des risques internes ou d’utilisateur doit être attribué. Sélectionnez **Choisir des utilisateurs et des groupes de rôles** , puis sélectionnez les utilisateurs ou les groupes de rôles de gestion des risques internes que vous souhaitez attribuer au groupe d’utilisateurs prioritaire. Sélectionnez **Ajouter** pour affecter les utilisateurs ou groupes de rôles sélectionnés au groupe.
9. Sélectionnez Suivant pour continuer.
10. Dans la page **Révision** , passez en revue les paramètres que vous avez choisis pour le groupe d’utilisateurs prioritaire. Sélectionnez les liens **Modifier** pour modifier l’une des valeurs du groupe ou sélectionnez **Envoyer** pour créer et activer le groupe d’utilisateurs prioritaire.
11. Dans la page de confirmation, sélectionnez **Terminé** pour quitter l’Assistant.

### <a name="update-a-priority-user-group"></a>Mettre à jour un groupe d’utilisateurs prioritaires

Pour mettre à jour un groupe d’utilisateurs prioritaires existant, vous allez utiliser des contrôles de définition dans la solution **de gestion des risques internes** dans le portail de conformité Microsoft Purview. Pour mettre à jour un groupe d’utilisateurs prioritaire, vous devez être membre du groupe de rôles *Gestion des risques internes* ou *Gestion des risques internes Administration*.

Effectuez les étapes suivantes pour modifier un groupe d’utilisateurs prioritaire :

1. Dans la [portail de conformité Microsoft Purview](https://compliance.microsoft.com), accédez à **Gestion des risques internes** et sélectionnez **Paramètres des risques internes**.
2. Sélectionnez la page **Groupes d’utilisateurs prioritaires (préversion).**
3. Sélectionnez le groupe d’utilisateurs prioritaire que vous souhaitez modifier, puis sélectionnez **Modifier le groupe**.
4. Dans la page **Nom et description** , mettez à jour le champ Description si nécessaire. Vous ne pouvez pas mettre à jour le nom du groupe d’utilisateurs prioritaire. Sélectionnez **Suivant** pour continuer.
5. Dans la page **Choisir des membres** , ajoutez de nouveaux membres au groupe à l’aide du contrôle **Choisir des membres** . Pour supprimer un utilisateur du groupe, sélectionnez le « X » en regard de l’utilisateur que vous souhaitez supprimer. Sélectionnez **Suivant** pour continuer.
6. Dans la page **Choisir qui peut afficher ce groupe** , ajoutez ou supprimez des utilisateurs ou des groupes de rôles qui peuvent examiner les utilisateurs, les alertes, les cas et les rapports pour le groupe d’utilisateurs prioritaires.
7. Sélectionnez **Suivant** pour continuer.
8. Dans la page **Révision** , passez en revue les paramètres de mise à jour que vous avez choisis pour le groupe d’utilisateurs prioritaire. Sélectionnez les liens **Modifier** pour modifier l’une des valeurs du groupe ou sélectionnez **Envoyer** pour mettre à jour le groupe d’utilisateurs prioritaire.
9. Dans la page de confirmation, sélectionnez **Terminé** pour quitter l’Assistant.

### <a name="delete-a-priority-user-group"></a>Supprimer un groupe d’utilisateurs prioritaires

Pour supprimer un groupe d’utilisateurs prioritaires existant, vous allez utiliser des contrôles de définition dans la solution **de gestion des risques internes** dans le portail de conformité Microsoft Purview. Pour supprimer un groupe d’utilisateurs prioritaire, vous devez être membre du groupe de rôles *Gestion des risques internes* ou *Gestion des risques internes Administration*.

> [!IMPORTANT]
> La suppression d’un groupe d’utilisateurs prioritaires le supprime de toute stratégie active à laquelle il est affecté. Si vous supprimez un groupe d’utilisateurs prioritaire qui est affecté à une stratégie active, la stratégie ne contiendra aucun utilisateur dans l’étendue et sera effectivement inactive et ne créera pas d’alertes.

Pour supprimer un groupe d’utilisateurs prioritaire, procédez comme suit :

1. Dans la [portail de conformité Microsoft Purview](https://compliance.microsoft.com), accédez à **Gestion des risques internes** et sélectionnez **Paramètres des risques internes**.
2. Sélectionnez la page **Groupes d’utilisateurs prioritaires (préversion).**
3. Sélectionnez le groupe d’utilisateurs prioritaire que vous souhaitez modifier, puis sélectionnez **Supprimer** dans le menu du tableau de bord.
4. Dans la boîte de dialogue **Supprimer** , sélectionnez **Oui** pour supprimer le groupe d’utilisateurs prioritaire ou sélectionnez **Annuler** pour revenir au tableau de bord.

## <a name="priority-physical-assets-preview"></a>Ressources physiques prioritaires (préversion)

L’identification de l’accès aux ressources physiques prioritaires et la corrélation de l’activité d’accès aux événements utilisateur sont un composant important de votre infrastructure de conformité. Ces ressources physiques représentent des emplacements prioritaires dans votre organisation, tels que des bâtiments d’entreprise, des centres de données ou des salles de serveurs. Les activités à risque internes peuvent être associées à des utilisateurs travaillant pendant des heures inhabituelles, à la tentative d’accès à ces zones sensibles ou sécurisées non autorisées, et à des demandes d’accès à des zones de haut niveau sans besoins légitimes.

Avec les ressources physiques prioritaires activées et le [connecteur de données de badging physique](import-physical-badging-data.md) configuré, la gestion des risques internes intègre les signaux de vos systèmes de contrôle physique et d’accès à d’autres activités à risque utilisateur. En examinant les modèles de comportement dans les systèmes d’accès physique et en corrélant ces activités avec d’autres événements à risque internes, la gestion des risques internes peut aider les enquêteurs et les analystes de conformité à prendre des décisions de réponse plus éclairées pour les alertes. L’accès aux ressources physiques prioritaires est noté et identifié dans les insights différemment de l’accès aux ressources non prioritaires.

Par exemple, votre organisation dispose d’un système de badging pour les utilisateurs qui régit et approuve l’accès physique aux zones de projet normales de travail et sensibles. Vous avez plusieurs utilisateurs qui travaillent sur un projet sensible et ces utilisateurs retourneront dans d’autres zones de votre organisation une fois le projet terminé. À mesure que le projet sensible approche de l’achèvement, vous souhaitez vous assurer que le travail du projet reste confidentiel et que l’accès aux zones du projet est étroitement contrôlé.

Vous choisissez d’activer le connecteur de données de badging physique dans Microsoft 365 pour importer les informations d’accès à partir de votre système de badging physique et spécifier les ressources physiques prioritaires dans la gestion des risques internes. En important les informations de votre système de badging et en corrélant les informations d’accès physique avec d’autres activités à risque identifiées dans la gestion des risques internes, vous remarquez que l’un des utilisateurs du projet accède aux bureaux du projet après les heures de travail normales et qu’il exporte également de grandes quantités de données vers un service de stockage cloud personnel à partir de son espace de travail normal. Cette activité d’accès physique associée à l’activité en ligne peut indiquer un éventuel vol de données et les enquêteurs de conformité et les analystes peuvent prendre les mesures appropriées en fonction des circonstances pour cet utilisateur.

![Ressources physiques prioritaires de gestion des risques internes.](../media/insider-risk-settings-priority-assets.png)

### <a name="configure-priority-physical-assets"></a>Configurer des ressources physiques prioritaires

Pour configurer les ressources physiques prioritaires, vous allez configurer le connecteur de badging physique et utiliser les contrôles de définition dans la solution **de gestion des risques internes** dans le portail de conformité Microsoft Purview. Pour configurer des ressources physiques prioritaires, vous devez être membre du groupe de rôles *Gestion des risques internes* ou *Gestion des risques internes Administration*.

Effectuez les étapes suivantes pour configurer les ressources physiques prioritaires :

1. Suivez les étapes de configuration pour la gestion des risques internes dans l’article [Prise en main de la gestion des risques internes](insider-risk-management-configure.md) . À l’étape 3, veillez à configurer le connecteur De badging physique.

    > [!IMPORTANT]
    > Pour que les stratégies de gestion des risques internes utilisent et mettent en corrélation les données de signal liées aux utilisateurs sortants et arrêtés avec les données d’événements de vos plateformes de contrôle physique et d’accès, vous devez également configurer le connecteur Microsoft 365 HR. Si vous activez le connecteur De badging physique sans activer le connecteur Microsoft 365 HR, les stratégies de gestion des risques internes traitent uniquement les événements pour les activités d’accès physique pour les utilisateurs de votre organisation.

2. Dans la [portail de conformité Microsoft Purview](https://compliance.microsoft.com), accédez à **Gestion des risques internes** et sélectionnez Paramètres  >  des **risques internes****Ressources physiques prioritaires**.
3. Dans la page **Ressources physiques prioritaires** , vous pouvez ajouter manuellement les ID de ressources physiques que vous souhaitez détecter les événements de ressources importés par le connecteur de badging physique, ou importer un fichier .csv de tous les ID de ressources physiques importés par le connecteur de badging physique : a) Pour ajouter manuellement des ID de ressources physiques, choisissez **Ajouter des ressources physiques prioritaires**, entrez un ID de ressource physique,  puis sélectionnez **Ajouter**. Entrez d’autres ID de ressource physique, puis sélectionnez **Ajouter des ressources physiques prioritaires** pour enregistrer toutes les ressources entrées.
    b) Pour ajouter une liste d’ID de ressources physiques à partir d’un fichier .csv, choisissez **Importer des ressources physiques prioritaires**. Dans la boîte de dialogue de l’Explorateur de fichiers, sélectionnez le fichier .csv que vous souhaitez importer, puis sélectionnez **Ouvrir**. Les ID de ressource physique des fichiers .csv sont ajoutés à la liste.
4. Accédez à la page **Indicateurs de** stratégie dans **Paramètres**.
5. Dans la page **Indicateurs de** stratégie, accédez à la section **Indicateurs d’accès physique** et cochez la case **Accès physique après l’arrêt ou l’échec de l’accès à la ressource sensible**.
6. Sélectionnez **Enregistrer** pour configurer et quitter.

### <a name="delete-a-priority-physical-asset"></a>Supprimer une ressource physique prioritaire

Pour supprimer une ressource physique prioritaire existante, vous allez utiliser des contrôles de définition dans la solution de gestion des risques internes dans le portail de conformité Microsoft Purview. Pour supprimer une ressource physique prioritaire, vous devez être membre du groupe de rôles Gestion des risques internes ou Gestion des risques internes Administration.

> [!IMPORTANT]
> La suppression d’une ressource physique prioritaire la retire de l’examen par toute stratégie active à laquelle elle a été précédemment incluse. Les alertes générées par les activités associées à la ressource physique prioritaire ne sont pas supprimées.

Effectuez les étapes suivantes pour supprimer une ressource physique prioritaire :

1. Dans la [portail de conformité Microsoft Purview](https://compliance.microsoft.com), accédez à **Gestion des risques internes** et sélectionnez Paramètres  >  des **risques internes****Ressources physiques prioritaires**.
2. Dans la page **Ressources physiques prioritaires** , sélectionnez la ressource que vous souhaitez supprimer.
3. Sélectionnez **Supprimer** dans le menu Action pour supprimer la ressource.

## <a name="power-automate-flows-preview"></a>Flux Power Automate (préversion)

[Microsoft Power Automate](/power-automate/getting-started) est un service de flux de travail qui automatise les actions entre les applications et les services. En utilisant des flux à partir de modèles ou créés manuellement, vous pouvez automatiser les tâches courantes associées à ces applications et services. Lorsque vous activez les flux Power Automate pour la gestion des risques internes, vous pouvez automatiser les tâches importantes pour les cas et les utilisateurs. Vous pouvez configurer des flux Power Automate pour récupérer des informations sur les utilisateurs, les alertes et les cas, et partager ces informations avec les parties prenantes et d’autres applications, ainsi que pour automatiser les actions dans la gestion des risques internes, telles que la publication de notes de cas. Les flux Power Automate s’appliquent aux cas et à tout utilisateur dans l’étendue d’une stratégie.

Les clients disposant d’abonnements Microsoft 365 qui incluent la gestion des risques internes n’ont pas besoin de licences Power Automate supplémentaires pour utiliser les modèles Power Automate de gestion des risques internes recommandés. Ces modèles peuvent être personnalisés pour prendre en charge votre organisation et couvrir les principaux scénarios de gestion des risques internes. Si vous choisissez d’utiliser les fonctionnalités Power Automate Premium dans ces modèles, de créer un modèle personnalisé à l’aide du connecteur Microsoft Purview ou d’utiliser des modèles Power Automate pour d’autres domaines de conformité dans Microsoft 365, vous aurez peut-être besoin de licences Power Automate supplémentaires.

Les modèles Power Automate suivants sont fournis aux clients pour prendre en charge l’automatisation des processus pour les utilisateurs et les cas de gestion des risques internes :

- **Avertir les utilisateurs lorsqu’ils sont ajoutés à une stratégie de risque interne** : ce modèle s’adresse aux organisations qui ont des stratégies internes, des exigences de confidentialité ou réglementaires qui doivent être avertis lorsqu’ils sont soumis à des stratégies de gestion des risques internes. Lorsque ce flux est configuré et sélectionné pour un utilisateur dans la page **Utilisateurs** , les utilisateurs et leurs responsables reçoivent un message électronique lorsque l’utilisateur est ajouté à une stratégie de gestion des risques internes. Ce modèle prend également en charge la mise à jour d’une liste SharePoint hébergée sur un site SharePoint pour faciliter le suivi des détails des messages de notification, tels que la date/heure et le destinataire du message. Si vous avez choisi d’anonymiser les utilisateurs dans **les paramètres de confidentialité**, les flux créés à partir de ce modèle ne fonctionnent pas comme prévu afin que la confidentialité de l’utilisateur soit conservée. Les flux Power Automate utilisant ce modèle sont disponibles dans le **tableau de bord Utilisateurs**.
- **Demander des informations aux RH ou à l’entreprise sur un utilisateur dans un cas de risque interne** : lorsqu’ils agissent sur un cas, les analystes et enquêteurs du risque interne peuvent avoir besoin de consulter les RH ou d’autres parties prenantes pour comprendre le contexte des activités du cas. Lorsque ce flux est configuré et sélectionné pour un cas, les analystes et les enquêteurs envoient un message électronique aux parties prenantes rh et métier configurées pour ce flux. Chaque destinataire reçoit un message avec des options de réponse préconfigurées ou personnalisables. Lorsque les destinataires sélectionnent une option de réponse, la réponse est enregistrée sous forme de note de cas et inclut des informations sur le destinataire et la date/heure. Si vous avez choisi d’anonymiser les utilisateurs dans **les paramètres de confidentialité**, les flux créés à partir de ce modèle ne fonctionnent pas comme prévu afin que la confidentialité de l’utilisateur soit conservée. Les flux Power Automate utilisant ce modèle sont disponibles dans le **tableau de bord Cas**.
- **Avertir le responsable lorsqu’un utilisateur a une alerte de risque interne** : certaines organisations peuvent avoir besoin d’une notification de gestion immédiate lorsqu’un utilisateur a une alerte de gestion des risques internes. Lorsque ce flux est configuré et sélectionné, le responsable de l’utilisateur de cas reçoit un e-mail contenant les informations suivantes sur toutes les alertes de cas :
    - Stratégie applicable pour l’alerte
    - Date/heure de l’alerte
    - Niveau de gravité de l’alerte

    Le flux met automatiquement à jour les notes de cas indiquant que le message a été envoyé et que le flux a été activé. Si vous avez choisi d’anonymiser les utilisateurs dans **les paramètres de confidentialité**, les flux créés à partir de ce modèle ne fonctionnent pas comme prévu afin que la confidentialité de l’utilisateur soit conservée. Les flux Power Automate utilisant ce modèle sont disponibles dans le **tableau de bord Cas**.
- **Créer un enregistrement pour un cas de risque interne dans ServiceNow** : ce modèle est destiné aux organisations qui souhaitent utiliser leur solution ServiceNow pour suivre les cas de gestion des risques internes.  Dans un cas, les analystes des risques internes et les enquêteurs peuvent créer un enregistrement pour le cas dans ServiceNow. Vous pouvez personnaliser ce modèle pour remplir les champs sélectionnés dans ServiceNow en fonction des besoins de votre organisation. Les flux Power Automate utilisant ce modèle sont disponibles dans le **tableau de bord Cas**. Pour plus d’informations sur les champs ServiceNow disponibles, consultez l’article de [référence serviceNow Connector](/connectors/service-now/) .

### <a name="create-a-power-automate-flow-from-insider-risk-management-template"></a>Créer un flux Power Automate à partir d’un modèle de gestion des risques internes

Pour créer un flux Power Automate à partir d’un modèle de gestion des risques internes recommandé, vous allez utiliser les contrôles de paramètres dans la solution **de gestion des risques internes** dans le portail de conformité Microsoft Purview ou l’option **Gérer les flux Power Automate** du contrôle **Automatiser** lorsque vous travaillez directement dans les **tableaux de bord** **Cas** ou Utilisateurs.

Pour créer un flux Power Automate dans la zone des paramètres, vous devez être membre du groupe de rôles *Gestion des risques internes* ou *Gestion des risques internes Administration*. Pour créer un flux Power Automate avec l’option **Gérer les flux Power Automate** , vous devez être membre d’au moins un groupe de rôles de gestion des risques internes.

Effectuez les étapes suivantes pour créer un flux Power Automate à partir d’un modèle de gestion des risques internes recommandé :

1. Dans la [portail de conformité Microsoft Purview](https://compliance.microsoft.com), accédez à **Gestion des risques internes** et sélectionnez **Paramètres des risques** >  internes **Flux Power Automate**. Vous pouvez également accéder à partir des pages de **tableaux de bord** **Cas** ou Utilisateurs en choisissant **Automatiser** > **gérer les flux Power Automate**.
2. Dans la page **Flux Power Automate** , sélectionnez un modèle recommandé dans la section **Modèles de gestion des risques internes que vous pouvez aimer** de la page.
3. Le flux répertorie les connexions incorporées nécessaires pour le flux et notera si les états de connexion sont disponibles. Si nécessaire, mettez à jour toutes les connexions qui ne sont pas affichées comme disponibles. Cliquez sur **Continuer**.
4. Par défaut, les flux recommandés sont préconfigurés avec les champs de données de service de gestion des risques internes et Microsoft 365 recommandés pour effectuer la tâche affectée pour le flux. Si nécessaire, personnalisez les composants de flux à l’aide du contrôle **Afficher les options avancées** et en configurant les propriétés disponibles pour le composant de flux.
5. Si nécessaire, ajoutez d’autres étapes au flux en sélectionnant le bouton **Nouvelle étape** . Dans la plupart des cas, cela ne doit pas être nécessaire pour les modèles par défaut recommandés.
6. Sélectionnez **Enregistrer le brouillon** pour enregistrer le flux pour une configuration ultérieure ou sélectionnez **Enregistrer** pour terminer la configuration du flux.
7. Sélectionnez **Fermer** pour revenir à la page **de flux Power Automate** . Le nouveau modèle est répertorié sous la forme d’un flux sous les onglets **Mes flux** et est automatiquement disponible dans la liste déroulante **Automatiser** le contrôle lors de l’utilisation de cas de gestion des risques internes pour l’utilisateur qui crée le flux.

> [!IMPORTANT]
> Si d’autres utilisateurs de votre organisation ont besoin d’accéder au flux, le flux doit être partagé.

### <a name="create-a-custom-power-automate-flow-for-insider-risk-management"></a>Créer un flux Power Automate personnalisé pour la gestion des risques internes

Certains processus et flux de travail de votre organisation peuvent être en dehors des modèles de flux de gestion des risques internes recommandés et vous devrez peut-être créer des flux Power Automate personnalisés pour les zones de gestion des risques internes. Les flux Power Automate sont flexibles et prennent en charge une personnalisation étendue, mais certaines étapes doivent être prises pour s’intégrer aux fonctionnalités de gestion des risques internes.

Effectuez les étapes suivantes pour créer un modèle Power Automate personnalisé pour la gestion des risques internes :

1. **Vérifiez votre licence de flux Power Automate** : pour créer des flux Power Automate personnalisés qui utilisent des déclencheurs de gestion des risques internes, vous avez besoin d’une licence Power Automate. Les modèles de flux de gestion des risques internes recommandés ne nécessitent pas de licence supplémentaire et sont inclus dans votre licence de gestion des risques internes.
2. **Créer un flux automatisé** : créez un flux qui effectue une ou plusieurs tâches après son déclenchement par un événement de gestion des risques internes. Pour plus d’informations sur la création d’un flux automatisé, consultez [Créer un flux dans Power Automate](/power-automate/get-started-logic-flow).
3. **Sélectionnez le connecteur Microsoft Purview** : recherchez et sélectionnez le connecteur Microsoft Purview. Ce connecteur permet des déclencheurs et des actions de gestion des risques internes. Pour plus d’informations sur les connecteurs, consultez l’article [Vue d’ensemble des informations de référence](/connectors/connector-reference/) sur les connecteurs.
4. **Choisissez des déclencheurs de gestion des risques internes pour votre flux** : la gestion des risques internes dispose de deux déclencheurs disponibles pour les flux Power Automate personnalisés :
    - **Pour un cas de gestion des risques internes sélectionné** : les flux avec ce déclencheur peuvent être sélectionnés dans la page du tableau de bord Cas de gestion des risques internes.
    - **Pour un utilisateur de gestion des risques internes sélectionné** : les flux avec ce déclencheur peuvent être sélectionnés dans la page du tableau de bord Utilisateurs de gestion des risques internes.
5. Choisir des actions de gestion des risques internes pour votre flux : vous pouvez choisir parmi plusieurs actions pour la gestion des risques internes à inclure dans votre flux personnalisé :
    - Obtenir une alerte de gestion des risques internes
    - Obtenir un cas de gestion des risques internes
    - Obtenir un utilisateur de gestion des risques internes
    - Obtenir des alertes de gestion des risques internes pour un cas
    - Ajouter une note de cas de gestion des risques internes

### <a name="share-a-power-automate-flow"></a>Partager un flux Power Automate

Par défaut, les flux Power Automate créés par un utilisateur sont uniquement disponibles pour cet utilisateur. Pour que d’autres utilisateurs de gestion des risques internes aient accès à un flux et utilisent un flux, le flux doit être partagé par le créateur du flux. Pour partager un flux, vous allez utiliser les contrôles de paramètres de la **solution de gestion des risques internes** dans le portail de conformité Microsoft Purview ou l’option **Gérer les flux Power Automate** du contrôle Automatiser lorsque vous travaillez directement dans les pages du **tableau de bord** **Cas** ou Utilisateurs. Une fois que vous avez partagé un flux, toutes les personnes avec lesquelles il a été partagé peuvent accéder au flux dans la liste déroulante **Automatiser** le contrôle dans les **tableaux de bord** **Cas** et Utilisateur.

Pour partager un flux Power Automate dans la zone des paramètres, vous devez être membre du groupe de rôles *Gestion des risques internes* ou *Gestion des risques internes Administration*. Pour partager un flux Power Automate avec l’option **Gérer les flux Power Automate** , vous devez être membre d’au moins un groupe de rôles de gestion des risques internes.

Effectuez les étapes suivantes pour partager un flux Power Automate :

1. Dans la [portail de conformité Microsoft Purview](https://compliance.microsoft.com), accédez à **Gestion des risques internes** et sélectionnez **Paramètres des risques** >  internes **Flux Power Automate**. Vous pouvez également accéder à partir des pages de **tableaux de bord** **Cas** ou Utilisateurs en choisissant **Automatiser** > **gérer les flux Power Automate**.
2. Dans la page **Flux Power Automate** , sélectionnez l’onglet **Mes flux** ou **Flux d’équipe** .
3. Sélectionnez le flux à partager, puis **sélectionnez Partager** dans le menu d’options de flux.
4. Dans la page de partage de flux, entrez le nom de l’utilisateur ou du groupe que vous souhaitez ajouter en tant que propriétaire du flux.
5. Dans la boîte de dialogue **Connexion utilisée** , sélectionnez **OK** pour confirmer que l’utilisateur ou le groupe ajouté aura un accès complet au flux.

### <a name="edit-a-power-automate-flow"></a>Modifier un flux Power Automate

Pour modifier un flux, vous allez utiliser les contrôles de paramètres de la solution **de gestion des risques internes** dans le portail de conformité Microsoft Purview ou l’option **Gérer les flux Power Automate** du contrôle **Automatiser** lorsque vous travaillez directement dans les **tableaux de bord** **Cas** ou Utilisateurs.

Pour modifier un flux Power Automate dans la zone paramètres, vous devez être membre du groupe de rôles *Gestion des risques internes* ou *Gestion des risques internes Administration*. Pour modifier un flux Power Automate avec l’option **Gérer les flux Power Automate** , vous devez être membre d’au moins un groupe de rôles de gestion des risques internes.

Effectuez les étapes suivantes pour modifier un flux Power Automate :

1. Dans la [portail de conformité Microsoft Purview](https://compliance.microsoft.com), accédez à **Gestion des risques internes** et sélectionnez **Paramètres des risques** >  internes **Flux Power Automate**. Vous pouvez également accéder à partir des pages de **tableaux de bord** **Cas** ou Utilisateurs en choisissant **Automatiser** > **gérer les flux Power Automate**.
2. Dans la page **Flux Power Automate** , sélectionnez un flux à modifier, puis sélectionnez **Modifier** dans le menu de contrôle de flux.
3. Sélectionnez les **points** >  de suspension **Paramètres** pour modifier un paramètre de composant de flux ou les **points de** >  suspension **Supprimer** pour supprimer un composant de flux.
4. Sélectionnez **Enregistrer** , puis **Fermer** pour terminer la modification du flux.

### <a name="delete-a-power-automate-flow"></a>Supprimer un flux Power Automate

Pour supprimer un flux, vous allez utiliser les contrôles de paramètres de la solution **de gestion des risques internes** dans le portail de conformité Microsoft Purview ou l’option **Gérer les flux Power Automate** du contrôle **Automatiser** lorsque vous travaillez directement dans les **tableaux de bord** **Cas** ou Utilisateurs. Lorsqu’un flux est supprimé, il est supprimé en tant qu’option pour tous les utilisateurs.

Pour supprimer un flux Power Automate dans la zone des paramètres, vous devez être membre du groupe de rôles *Gestion des risques internes* ou *Gestion des risques internes Administration*. Pour supprimer un flux Power Automate avec l’option **Gérer les flux Power Automate** , vous devez être membre d’au moins un groupe de rôles de gestion des risques internes.

Effectuez les étapes suivantes pour supprimer un flux Power Automate :

1. Dans la [portail de conformité Microsoft Purview](https://compliance.microsoft.com), accédez à **Gestion des risques internes** et sélectionnez **Paramètres des risques** >  internes **Flux Power Automate**. Vous pouvez également accéder à partir des pages de **tableaux de bord** **Cas** ou Utilisateurs en choisissant **Automatiser** > **gérer les flux Power Automate**.
2. Dans la page **Flux Power Automate** , sélectionnez un flux à supprimer, puis sélectionnez **Supprimer** dans le menu de contrôle de flux.
3. Dans la boîte de dialogue de confirmation de suppression, sélectionnez **Supprimer** pour supprimer le flux ou **annuler** pour quitter l’action de suppression.

## <a name="microsoft-teams-preview"></a>Microsoft Teams (préversion)

Les analystes et enquêteurs de conformité peuvent facilement utiliser Microsoft Teams pour collaborer sur les cas de gestion des risques internes. Ils peuvent coordonner et communiquer avec d’autres parties prenantes dans Microsoft Teams pour :

- Coordonner et examiner les activités de réponse pour les cas dans les canaux Teams privés
- Partager et stocker en toute sécurité des fichiers et des preuves liés à des cas individuels
- Suivre et examiner les activités de réponse des analystes et des enquêteurs

Une fois Que Microsoft Teams est activé pour la gestion des risques internes, une équipe Microsoft Teams dédiée est créée chaque fois qu’une alerte est confirmée et qu’un cas est créé. Par défaut, l’équipe inclut automatiquement tous les membres des groupes de rôles *Insider Risk Management*, *Insider Risk Management Analysts* et *Insider Risk Management Investigate (* jusqu’à 100 utilisateurs initiaux). Des contributeurs d’organisation supplémentaires peuvent être ajoutés à l’équipe après sa création et le cas échéant. Pour les cas existants créés avant l’activation de Microsoft Teams, les analystes et les enquêteurs peuvent choisir de créer une équipe Microsoft Teams lorsqu’ils travaillent dans un cas si nécessaire.  Une fois que vous avez résolu le cas associé dans la gestion des risques internes, l’équipe est automatiquement archivée (déplacée vers masquée et en lecture seule).

Pour plus d’informations sur l’utilisation des équipes et des canaux dans Microsoft Teams, consultez [Vue d’ensemble des équipes et des canaux dans Microsoft Teams](/MicrosoftTeams/teams-channels-overview).

L’activation de la prise en charge de Microsoft Teams pour les cas est rapide et facile à configurer. Pour activer Microsoft Teams pour la gestion des risques internes, procédez comme suit :

1. Dans le [portail de conformité Microsoft Purview](https://compliance.microsoft.com), accédez à **Gestion des risques internes Paramètres de** > **risque interne**.
2. Sélectionnez la page **Microsoft Teams** .
3. Activez l’intégration de Microsoft Teams pour la gestion des risques internes.
4. Sélectionnez **Enregistrer** pour configurer et quitter.

![Gestion des risques internes Microsoft Teams.](../media/insider-risk-settings-teams.png)

### <a name="create-a-microsoft-teams-team-for-existing-cases"></a>Créer une équipe Microsoft Teams pour les cas existants

Si vous activez la prise en charge de Microsoft Teams pour la gestion des risques internes une fois que vous avez des cas existants, vous devez créer manuellement une équipe pour chaque cas en fonction des besoins. Après avoir activé la prise en charge de Microsoft Teams dans les paramètres de gestion des risques internes, les nouveaux cas créent automatiquement une nouvelle équipe Microsoft Teams.

Les utilisateurs doivent être autorisés à créer des groupes Microsoft 365 dans votre organisation pour créer une équipe Microsoft Teams à partir d’un cas. Pour plus d’informations sur la gestion des autorisations pour Groupes Microsoft 365, consultez [Gérer qui peut créer Groupes Microsoft 365](../solutions/manage-creation-of-groups.md).

Pour créer une équipe pour un cas, vous allez utiliser le contrôle Créer une équipe Microsoft lorsque vous travaillez directement dans un cas existant. Effectuez les étapes suivantes pour créer une équipe :

1. Dans la [portail de conformité Microsoft Purview](https://compliance.microsoft.com), accédez à **Cas** **de gestion des** >  risques internes et sélectionnez un cas existant.
2. Dans le menu d’action de cas, sélectionnez **Créer une équipe Microsoft**.
3. Dans le champ **Nom** de l’équipe, entrez un nom pour la nouvelle équipe Microsoft Teams.
4. Sélectionnez **Créer une équipe Microsoft** , puis **sélectionnez Fermer**.

En fonction du nombre d’utilisateurs affectés aux groupes de rôles de gestion des risques internes, l’ajout de tous les enquêteurs et analystes à l’équipe Microsoft Teams pour un cas peut prendre 15 minutes.

## <a name="analytics"></a>Analyse

L’analyse des risques internes vous permet d’effectuer une évaluation des risques internes potentiels au sein de votre organisation sans aucune configuration de stratégie des risques internes. Cette évaluation peut permettre à votre organisation d’identifier des zones potentielles plus élevées de risque utilisateur et vous aider à déterminer le type et l’étendue des stratégies de gestion des risques internes que vous pouvez envisager de configurer. Les analyses analytiques offrent les avantages suivants pour votre organisation :

- Facile à configurer : pour commencer à utiliser les analyses analytiques, vous pouvez sélectionner Exécuter l’analyse lorsque vous y êtes invité par la recommandation d’analyse ou accéder à Paramètres  >  de **risque internes****Analytics** et activer l’analyse.
- Confidentialité par conception : les résultats et les insights de l’analyse sont retournés en tant qu’activité utilisateur agrégée et anonymisée, les noms d’utilisateur individuels ne sont pas identifiables par les réviseurs.
- Comprendre les risques potentiels à l’aide d’insights consolidés : les résultats de l’analyse peuvent vous aider à identifier rapidement les zones de risque potentielles pour vos utilisateurs et la stratégie la mieux adaptée à l’atténuation de ces risques.

Regardez la [vidéo Insider Risk Management Analytics](https://www.youtube.com/watch?v=5c0P5MCXNXk) pour comprendre comment l’analytique peut accélérer l’identification des risques internes potentiels et vous aider à prendre rapidement des mesures.

Analytics analyse les événements d’activité à risque provenant de plusieurs sources pour aider à identifier des insights sur les zones de risque potentielles. Selon votre configuration actuelle, l’analytique recherche les activités à risque éligibles dans les domaines suivants :

- **Journaux d’audit Microsoft 365** : inclus dans toutes les analyses, il s’agit de la source principale pour identifier la plupart des activités potentiellement risquées.
- **Exchange Online** : inclus dans toutes les analyses, l’activité Exchange Online permet d’identifier les activités où les données des pièces jointes sont envoyées par e-mail à des contacts ou services externes.
- **Azure Active Directory** : inclus dans toutes les analyses, l’historique Azure Active Directory permet d’identifier les activités à risque associées aux utilisateurs avec des comptes d’utilisateur supprimés.
- **Connecteur de données RH Microsoft 365** : s’il est configuré, les événements du connecteur RH permettent d’identifier les activités à risque associées aux utilisateurs qui ont des dates de démission ou d’arrêt à venir.

Les insights d’analyse des analyses sont basés sur les mêmes signaux d’activité à risque que les stratégies de gestion des risques internes et les résultats des rapports basés sur des activités utilisateur uniques et séquentiels. Toutefois, le scoring des risques pour l’analytique est basé sur jusqu’à 10 jours d’activité, tandis que les stratégies de risque interne utilisent l’activité quotidienne pour les insights. Lorsque vous activez et exécutez l’analytique dans votre organisation pour la première fois, les résultats de l’analyse s’affichent pendant une journée. Si vous laissez l’analytique activée, vous verrez les résultats de chaque analyse quotidienne ajoutées aux rapports d’insights pour une plage maximale des 10 jours d’activité précédents.

### <a name="enable-analytics-and-start-your-scan"></a>Activer l’analytique et démarrer votre analyse

Pour activer l’analytique des risques internes, vous devez être membre du groupe de rôles *Gestion des risques internes*, *Gestion des risques internes Administration* ou *Administrateur général Microsoft 365*.
Effectuez les étapes suivantes pour activer l’analytique des risques internes :

1. Dans la [portail de conformité Microsoft Purview](https://compliance.microsoft.com), accédez à **Gestion des risques internes**.
2. Sélectionnez **Exécuter l’analyse** sur la carte **Rechercher les risques internes dans votre organisation sous** l’onglet **Vue d’ensemble** de la gestion des risques internes. Cela active l’analyse analytique pour votre organisation. Vous pouvez également activer l’analyse dans votre organisation en accédant à **Paramètres** >  de risque internes **Analytics** et en activant **Analyser l’activité utilisateur de votre locataire pour identifier les risques internes potentiels**.
3. Dans le volet **Détails de l’analyse** , sélectionnez **Exécuter l’analyse** pour démarrer l’analyse de votre organisation. Les résultats de l'analyse analytique peuvent prendre jusqu'à 48 heures avant que les informations ne soient disponibles sous forme de rapports pour examen.

![Paramètres d’analyse de la gestion des risques internes.](../media/insider-risk-settings-analytics-enable.png)

### <a name="viewing-analytics-insights-and-creating-new-policies"></a>Affichage des insights d’analyse et création de nouvelles stratégies

Une fois la première analyse analytique terminée pour votre organisation, les membres du groupe de rôles *Insider Risk Management Administration* reçoivent automatiquement une notification par e-mail et peuvent afficher les insights et recommandations initiaux pour les activités potentiellement risquées de vos utilisateurs. Les analyses quotidiennes continuent, sauf si vous désactivez l’analytique pour votre organisation. Email notifications aux administrateurs sont fournies pour chacune des trois catégories dans l’étendue pour l’analytique (fuites de données, vol et exfiltration) après la première instance d’activité dans votre organisation. Email notifications ne sont pas envoyées aux administrateurs pour la détection d’activité de suivi résultant des analyses quotidiennes. Si l’analytique dans **la gestion des** >  risques internes **Paramètres** > **l’analytique** est désactivée, puis réactivé dans votre organisation, les notifications automatiques par e-mail sont réinitialisées et les e-mails sont envoyés aux membres du groupe de rôles *Insider Risk Management Administration* pour obtenir de nouveaux insights d’analyse.

Pour afficher les risques potentiels pour votre organisation, accédez à l’onglet **Vue d’ensemble** et sélectionnez **Afficher les résultats** sur la carte **Analyse des risques internes** . Si l’analyse de votre organisation n’est pas terminée, vous verrez un message indiquant que l’analyse est toujours active.

![Carte de rapport prêt pour l’analytique de gestion des risques internes.](../media/insider-risk-analytics-ready-card.png)

Pour les analyses terminées, vous verrez les risques potentiels découverts dans votre organisation, ainsi que des insights et des recommandations pour y remédier. Les risques identifiés et les insights spécifiques sont inclus dans les rapports regroupés par zone, le nombre total d’utilisateurs présentant des risques identifiés, le pourcentage de ces utilisateurs ayant des activités potentiellement risquées et une stratégie de risque interne recommandée pour aider à atténuer ces risques. Les rapports sont les suivants :

- **Insights sur les fuites de données** : activités pour tous les utilisateurs qui peuvent inclure un surpartage accidentel d’informations en dehors de votre organisation ou des fuites de données par des utilisateurs ayant une intention malveillante.
- **Insights sur le vol de données** : activités pour les utilisateurs sortants ou les utilisateurs avec des comptes Azure Active Directory supprimés qui peuvent inclure le partage à risque d’informations en dehors de votre organisation ou le vol de données par des utilisateurs ayant une intention malveillante.
- **Principaux insights d’exfiltration** : activités de tous les utilisateurs qui peuvent inclure le partage de données en dehors de votre organisation.

![Rapport de vue d’ensemble de l’analytique de gestion des risques internes.](../media/insider-risk-analytics-overview.png)

Pour afficher plus d’informations sur un insight, sélectionnez **Afficher les détails** afin d’afficher le volet d’informations de l’insight. Le volet d’informations inclut les résultats complets des insights, une recommandation de stratégie de risque interne et le bouton **Créer une stratégie** pour vous aider à créer rapidement la stratégie recommandée. Si vous sélectionnez Créer une stratégie, vous accédez à l’Assistant Stratégie et sélectionne automatiquement le modèle de stratégie recommandé lié à l’insight. Par exemple, si l’insight analytique concerne l’activité de *fuite de données* , le modèle de stratégie *Fuites de données générales* est pré-sélectionné dans l’Assistant Stratégie pour vous.

![Rapport d’analyse des détails de la gestion des risques internes.](../media/insider-risk-analytics-details.png)

### <a name="turn-off-analytics"></a>Désactiver l’analytique

Pour désactiver l’analyse des risques internes, vous devez être membre du groupe de rôles *Gestion des risques internes*, *Gestion des risques internes Administration* ou *Administrateur général* Microsoft 365. Une fois que vous avez désactivé l’analytique, les rapports d’insights analytiques restent statiques et ne sont pas mis à jour pour les nouveaux risques.

Effectuez les étapes suivantes pour désactiver l’analyse des risques internes :

1. Dans la [portail de conformité Microsoft Purview](https://compliance.microsoft.com), accédez à **Gestion des risques internes**.
2. Sélectionnez Paramètres  > **de risque internes****Page Analytique**.
3. Dans la page **Analytique** , désactivez **Analyser l’activité utilisateur de votre locataire pour identifier les risques internes potentiels**.

## <a name="admin-notifications"></a>notifications Administration

Administration notifications envoient automatiquement une notification par e-mail aux groupes de rôles de gestion des risques internes sélectionnables. Vous pouvez activer les notifications et affecter les groupes de rôles qui recevront les notifications pour les scénarios suivants :

- Envoyez un e-mail de notification lorsque la première alerte est générée pour une nouvelle stratégie. Les stratégies sont vérifiées toutes les 24 heures pour les alertes de première fois et les notifications ne sont pas envoyées sur les alertes suivantes pour la stratégie.
- Envoyez un e-mail quotidien lorsque de nouvelles alertes de gravité élevée sont générées. Les stratégies sont vérifiées toutes les 24 heures pour détecter les alertes de gravité élevée.
- Envoyer un e-mail hebdomadaire résumant les stratégies qui ont des avertissements non résolus

Si vous avez activé l’analytique de la gestion des risques internes pour votre organisation, les membres du groupe de rôles *Gestion des risques internes Administration* reçoivent automatiquement une notification par e-mail pour les informations analytiques initiales concernant les fuites de données, le vol et les activités d’exfiltration.

Si vous préférez désactiver les notifications d’administration et d’analytique, procédez comme suit :

1. Dans le [portail de conformité Microsoft Purview](https://compliance.microsoft.com), accédez à **Gestion des risques internes Paramètres de** > **risque interne**.
2. Sélectionnez la page **notifications Administration**.
3. Décochez la case pour les options suivantes, le cas échéant :
    - **Envoyer un e-mail de notification lorsque la première alerte est générée pour une nouvelle stratégie**
    - **Envoyer une notification par e-mail lorsqu’un nouvel insight est disponible dans Analytics**
    - **Envoyer une notification par e-mail quand Analytics est désactivé**

4. Sélectionnez **Enregistrer** pour configurer et quitter.

## <a name="inline-alert-customization-preview"></a>Personnalisation de l’alerte inline (préversion)

La personnalisation des alertes inline vous permet d’ajuster rapidement une stratégie de gestion des risques internes directement à partir du **tableau de bord alerte** lors de l’examen de l’alerte. Des alertes sont générées lorsqu’une activité atteint les seuils configurés dans la stratégie associée. Pour réduire le nombre d’alertes que vous recevez de cette activité, vous pouvez modifier les seuils de l’activité ou supprimer complètement l’activité de la stratégie.

Vous pouvez activer la personnalisation des alertes inline pour permettre aux utilisateurs affectés aux groupes de rôles *Analystes de gestion des risques* *internes et Enquêteurs en gestion des risques internes* de modifier les seuils de stratégie et de désactiver des indicateurs spécifiques. Si la personnalisation des alertes inline n’est pas activée, seuls les utilisateurs affectés aux groupes de rôles *Insider Risk Management Administration* ou *Insider Risk Management* peuvent modifier ces conditions de stratégie. La personnalisation des alertes inline est prise en charge pour les alertes quel que soit l’état actuel de l’alerte, ce qui permet aux analystes et aux enquêteurs de mettre à jour les stratégies des alertes *ignorées* et *résolues* si nécessaire.

Effectuez les étapes suivantes pour activer la personnalisation des alertes inline :

1. Dans le [portail de conformité Microsoft Purview](https://compliance.microsoft.com), accédez à **Gestion des risques internes Paramètres de** > **risque interne**.
2. Sélectionnez la page **Personnalisation de l’alerte inline (préversion).**
3. Activez la personnalisation des alertes inline pour la gestion des risques internes.
4. Sélectionnez **Enregistrer** pour configurer et quitter.

> [!NOTE]
> L’activation de la personnalisation des alertes inline prend environ une heure avant d’être disponible dans les alertes de stratégie nouvelles et existantes.

Lorsqu’il est activé, les analystes et les enquêteurs peuvent sélectionner **Réduire les alertes pour cette activité** pour une alerte dans le **tableau de bord Alerte** et peuvent afficher les détails de l’activité et des indicateurs associés à l’alerte. En outre, les seuils de stratégie actuels sont affichés pour le nombre d’événements utilisés pour créer des alertes de gravité faible, moyenne et élevée. Si **l’option Réduire les alertes pour cette activité** est sélectionnée et qu’une modification de stratégie précédente a été apportée pour modifier le seuil ou a supprimé l’indicateur associé, un message de notification détaillant les modifications précédentes apportées à la stratégie s’affiche.

Les analystes et les enquêteurs peuvent choisir parmi les options suivantes dans le volet **Réduire les alertes pour cette activité afin** de modifier rapidement la stratégie qui a créé l’alerte :

- **Réduire les alertes à l’aide des seuils recommandés par Microsoft** : nous augmenterons automatiquement les seuils de la stratégie pour vous. Vous serez en mesure de passer en revue les nouveaux paramètres de seuil recommandés avant de modifier la stratégie.
- **Réduisez les alertes en choisissant vos propres seuils** : vous pouvez augmenter manuellement les seuils pour ce type d’activité pour les alertes actuelles et futures. Vous serez en mesure de passer en revue les paramètres de seuil actuels et de configurer les nouveaux paramètres de seuil avant de modifier la stratégie.
- **Arrêter d’obtenir des alertes pour cette activité** : cela supprime cet indicateur de la stratégie et cette activité n’est plus détectée par la stratégie. Cela s’applique à tous les indicateurs, que l’indicateur soit basé sur des seuils.

Après avoir choisi une option, les analystes et les enquêteurs peuvent choisir deux options pour mettre à jour la stratégie :

- **Enregistrer et ignorer l’alerte** : enregistre les modifications apportées à la stratégie et met à jour l’état de l’alerte sur *Résolu*.
- **Enregistrer uniquement** : enregistre les modifications apportées à la stratégie, mais l’état de l’alerte reste le même.