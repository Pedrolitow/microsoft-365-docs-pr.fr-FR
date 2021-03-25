---
title: Créer des règles de détection personnalisées dans Microsoft Defender ATP
ms.reviewer: ''
description: Découvrez comment créer des règles de détection personnalisées basées sur des requêtes de repérage avancé
keywords: détections personnalisées, créer, gérer, alertes, modifier, exécuter à la demande, fréquence, intervalle, règles de détection, repérage avancé, recherche, requête, actions de réponse, mdatp, microsoft defender atp
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: lomayor
author: lomayor
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.date: 09/20/2020
ms.technology: mde
ms.openlocfilehash: fc4c15d2e391176ed0b4420c13fb865674da0361
ms.sourcegitcommit: 2a708650b7e30a53d10a2fe3164c6ed5ea37d868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2021
ms.locfileid: "51163586"
---
# <a name="create-custom-detection-rules"></a>Créer des règles de détection personnalisées

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-assignaccess-abovefoldlink)

Les règles de [](advanced-hunting-overview.md) détection personnalisées conçues à partir de requêtes de repérage avancées vous permet de surveiller de manière proactive différents événements et états système, y compris les activités suspectées de violation et les appareils mal configurés. Vous pouvez les configurer pour qu’ils s’exécutent à intervalles réguliers, générant des alertes et prenant des mesures de réponse chaque fois qu’il existe des correspondances.

Lisez cet article pour découvrir comment créer des règles de détection personnalisées. Vous pouvez [également consulter l’affichage et la gestion des règles existantes.](custom-detections-manage.md)

> [!NOTE]
> Pour créer ou gérer des détections personnalisées, [votre rôle](user-roles.md#create-roles-and-assign-the-role-to-an-azure-active-directory-group) doit avoir l’autorisation gérer les **paramètres de** sécurité.

## <a name="1-prepare-the-query"></a>1. Préparez la requête.

Dans le Centre de sécurité Microsoft Defender, allez à **la** recherche avancée et sélectionnez une requête existante ou créez une nouvelle requête. Lorsque vous utilisez une nouvelle requête, exécutez la requête pour identifier les erreurs et comprendre les résultats possibles.

>[!IMPORTANT]
>Pour empêcher le service de renvoyer trop d’alertes, chaque règle est limitée à générer seulement 100 alertes chaque fois qu’elle s’exécute. Avant de créer une règle, modifiez votre requête afin d’éviter les alertes pour une activité normale au quotidien.

### <a name="required-columns-in-the-query-results"></a>Colonnes requises dans les résultats de la requête

Pour utiliser une requête pour une règle de détection personnalisée, la requête doit renvoyer les colonnes suivantes :

- `Timestamp`
- `DeviceId`
- `ReportId`

Les requêtes simples, telles que celles qui n’utilisent pas l’opérateur ou l’opérateur pour personnaliser ou agréger les résultats, retournent généralement `project` `summarize` ces colonnes courantes.

Il existe plusieurs façons de s’assurer que les requêtes plus complexes retournent ces colonnes. Par exemple, si vous préférez agréger et compter par , vous pouvez toujours retourner et en les obtenant à partir de l’événement le plus récent `DeviceId` `Timestamp` impliquant chaque `ReportId` appareil.

L’exemple de requête ci-dessous compte le nombre d’appareils uniques ( ) avec détections antivirus et utilise cette méthode pour rechercher uniquement les appareils ayant plus de `DeviceId` cinq détections. Pour renvoyer la dernière `Timestamp` et la `ReportId` correspondante, elle utilise `summarize` l’opérateur avec la `arg_max` fonction.

```kusto
DeviceEvents
| where Timestamp > ago(7d)
| where ActionType == "AntivirusDetection"
| summarize (Timestamp, ReportId)=arg_max(Timestamp, ReportId), count() by DeviceId
| where count_ > 5
```

> [!TIP]
> Pour de meilleures performances de requête, définissez un filtre d’heure qui correspond à la fréquence d’exécution prévue pour la règle. Étant donné que l’utilisation la moins fréquente est toutes les 24 heures, le filtrage de la journée passée couvrira toutes les nouvelles données.

## <a name="2-create-a-new-rule-and-provide-alert-details"></a>2. Créez une règle et fournissez des détails sur l’alerte.

Avec la requête dans l’éditeur  de requête, sélectionnez Créer une règle de détection et spécifiez les détails d’alerte suivants :

- **Nom de la détection**: nom de la règle de détection
- **Fréquence**: intervalle d’exécution de la requête et d’action. [Voir les conseils supplémentaires ci-dessous](#rule-frequency)
- **Titre de l’alerte**: titre affiché avec les alertes déclenchées par la règle
- **Gravité :** risque potentiel du composant ou de l’activité identifié par la règle. [En savoir plus sur les gravités des alertes](alerts-queue.md#severity)
- **Catégorie :** type de composant ou d’activité de menace, le cas caser. [En savoir plus sur les catégories d’alertes](alerts-queue.md#understanding-alert-categories)
- **MITRE ATT&techniques CK**: une ou plusieurs techniques d’attaque identifiées par la règle, telles que documentées dans l’infrastructure MITRE ATT&CK. Cette section n’est pas disponible avec certaines catégories d’alertes, telles que les programmes malveillants, les ransomware, les activités suspectes et les logiciels indésirables
- **Description :** plus d’informations sur le composant ou l’activité identifié par la règle 
- **Actions recommandées**: actions supplémentaires que les répondeurs peuvent prendre en réponse à une alerte

Pour plus d’informations sur l’affichage des détails des alertes, consultez [la file d’attente des alertes.](alerts-queue.md)

### <a name="rule-frequency"></a>Fréquence des règles

Une fois enregistrée, une nouvelle règle de détection personnalisée s’exécute immédiatement et recherche les correspondances des 30 derniers jours de données. La règle s’exécute à nouveau à intervalles fixes et durées de recherche en fonction de la fréquence que vous choisissez :

- **Toutes les 24 heures**: s’exécute toutes les 24 heures, en vérifiant les données des 30 derniers jours
- **Toutes les 12 heures**: s’exécute toutes les 12 heures, en vérifiant les données des dernières 24 heures
- **Toutes les 3 heures :** s’exécute toutes les 3 heures, en vérifiant les données des 6 dernières heures
- **Toutes les heures**: s’exécute toutes les heures, en vérifiant les données des dernières 2 heures

> [!IMPORTANT]
> Lors de la modification d’une requête déjà programmée en tant que détection personnalisée, l’exécution immédiate suivante aura une fenêtre de recherche de 30 jours, exactement comme si une nouvelle requête avait été créée. Les modifications apportées à un grand nombre de requêtes, et avec des filtres de temps supérieurs à la durée de recherche par défaut pour la fréquence sélectionnée, peuvent avoir un impact sur la consommation globale du quota de recherche avancée et entraîner l’épuisement du quota quotidien.

> [!TIP]
> Faire correspondre les filtres d’heure de votre requête à la durée de la recherche. Les résultats en dehors de la durée de la recherche sont ignorés.

Sélectionnez la fréquence qui correspond à la fréquence à laquelle vous souhaitez surveiller les détections et prenez en compte la capacité de votre organisation à répondre aux alertes.

## <a name="3-choose-the-impacted-entities"></a>3. Choisissez les entités impactées.

Identifiez les colonnes dans les résultats de votre requête où vous vous attendez à trouver l’entité principale affectée ou concernée. Par exemple, une requête peut renvoyer des ID d’appareil et d’utilisateur. L’identification de l’entité principale concernée par l’identification de ces colonnes permet au service d’agréger les alertes pertinentes, de corréler les incidents et les actions de réponse cible.

Vous ne pouvez sélectionner qu’une seule colonne pour chaque type d’entité. Les colonnes qui ne sont pas renvoyées par votre requête ne peuvent pas être sélectionnées.

## <a name="4-specify-actions"></a>4. Spécifiez les actions.

Votre règle de détection personnalisée peut prendre automatiquement des mesures sur des fichiers ou des appareils renvoyés par la requête.

### <a name="actions-on-devices"></a>Actions sur les appareils

Ces actions sont appliquées aux appareils dans la `DeviceId` colonne des résultats de la requête :

- **Isoler l’appareil**: applique une isolation complète du réseau, ce qui empêche l’appareil de se connecter à n’importe quelle application ou service, à l’exception du service Defender for Endpoint. [En savoir plus sur l’isolation des appareils](respond-machine-alerts.md#isolate-devices-from-the-network)
- **Collecter un package d’examen**: collecte des informations sur l’appareil dans un fichier ZIP. [En savoir plus sur le package d’examen](respond-machine-alerts.md#collect-investigation-package-from-devices)
- **Exécuter une analyse antivirus**: effectue une analyse complète de l’Antivirus Microsoft Defender sur l’appareil
- **Lancer une enquête**: lance une [enquête automatisée](automated-investigations.md) sur l’appareil
- **Restreindre l’exécution de** l’application : définit des restrictions sur l’appareil pour autoriser uniquement l’exécution des fichiers signés avec un certificat émis par Microsoft. [En savoir plus sur la restriction de l’exécution de l’application](respond-machine-alerts.md#restrict-app-execution)

### <a name="actions-on-files"></a>Actions sur les fichiers

Ces actions sont appliquées aux fichiers dans la ou `SHA1` la colonne des résultats de la requête `InitiatingProcessSHA1` :

- **Autoriser/Bloquer**: ajoute automatiquement le [](manage-indicators.md) fichier à votre liste d’indicateurs personnalisés afin qu’il soit toujours autorisé à s’exécuter ou bloqué. Vous pouvez définir l’étendue de cette action afin qu’elle soit prise uniquement sur les groupes d’appareils sélectionnés. Cette étendue est indépendante de l’étendue de la règle.
- **Fichier de mise en** quarantaine : supprime le fichier de son emplacement actuel et place une copie en quarantaine

### <a name="actions-on-users"></a>Actions sur les utilisateurs

- **Marquez l’utilisateur comme** compromis : définit le niveau de risque de l’utilisateur sur « élevé » dans Azure Active Directory, déclenchant les stratégies de protection des [identités correspondantes.](https://docs.microsoft.com/azure/active-directory/identity-protection/overview-identity-protection#risk-levels)

## <a name="5-set-the-rule-scope"></a>5. Définissez l’étendue de la règle.

Définissez l’étendue pour spécifier les appareils couverts par la règle :

- Tous les appareils
- Groupes d’appareils spécifiques

Seules les données des appareils dans l’étendue seront interrogés. En outre, des actions seront prises uniquement sur ces appareils.

## <a name="6-review-and-turn-on-the-rule"></a>6. Examinez et allumez la règle.

Après avoir passé en revue la règle, **sélectionnez Créer** pour l’enregistrer. La règle de détection personnalisée s’exécute immédiatement. Il s’exécute à nouveau en fonction de la fréquence configurée pour vérifier les correspondances, générer des alertes et prendre des mesures de réponse.

Vous pouvez [afficher et gérer des règles de détection personnalisées,](custom-detections-manage.md)vérifier leurs précédentes séries et passer en revue les alertes qu’elles ont déclenchées. Vous pouvez également exécuter une règle à la demande et la modifier.

## <a name="related-topics"></a>Voir aussi

- [Afficher et gérer des règles de détection personnalisées](custom-detections-manage.md)
- [Vue d’ensemble des détections personnalisées](overview-custom-detections.md)
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Découvrir le langage de requête de repérage avancé](advanced-hunting-query-language.md)
- [Afficher et organiser les alertes](alerts-queue.md)
