---
title: Créer et gérer des règles de détection personnalisées dans Microsoft 365 Defender
description: Découvrez comment créer et gérer des règles de détection personnalisées basées sur des requêtes de repérage avancées
keywords: repérage avancé, repérage de menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, détections personnalisées, règles, schéma, kusto, RBAC, autorisations, Microsoft Defender pour point de terminaison
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- m365initiative-m365-defender
- tier2
ms.topic: article
ms.openlocfilehash: 304883b0d0ba554c5f2f0d4044c03445662d5fe9
ms.sourcegitcommit: ef0c7a914782999d148c79240b2d3f7be53e5690
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2022
ms.locfileid: "68138164"
---
# <a name="create-and-manage-custom-detections-rules"></a>Créer et gérer des règles de détection personnalisées

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender
- Microsoft Defender pour point de terminaison

Les règles de détection personnalisées sont des règles que vous pouvez concevoir et modifier à l’aide de requêtes de [chasse avancées](advanced-hunting-overview.md) . Ces règles vous permettent de surveiller de manière proactive différents événements et états système, y compris les activités suspectes de violation et les points de terminaison mal configurés. Vous pouvez les définir pour qu’ils s’exécutent à intervalles réguliers, en générant des alertes et en effectuant des actions de réponse chaque fois qu’il y a des correspondances.

## <a name="required-permissions-for-managing-custom-detections"></a>Autorisations requises pour la gestion des détections personnalisées

Pour gérer les détections personnalisées, vous devez disposer de l’un des rôles suivants:

- **Administrateur de sécurité** : les utilisateurs disposant de ce [rôle Azure Active Directory](/azure/active-directory/roles/permissions-reference#security-administrator) peuvent gérer les paramètres de sécurité dans le portail Microsoft 365 Defender et d’autres portails et services.

- **Opérateur de sécurité** : les utilisateurs dotés de ce [rôle Azure Active Directory](/azure/active-directory/roles/permissions-reference#security-operator) peuvent gérer les alertes et avoir un accès en lecture seule global aux fonctionnalités liées à la sécurité, y compris toutes les informations du portail Microsoft 365 Defender. Ce rôle est suffisant pour gérer les détections personnalisées uniquement si le contrôle d’accès en fonction du rôle (RBAC) est désactivé dans Microsoft Defender pour point de terminaison. Si vous avez configuré RBAC, vous avez également besoin de l’autorisation **gérer les paramètres de sécurité** pour Defender pour point de terminaison.

Vous pouvez également gérer les détections personnalisées qui s’appliquent aux données de solutions Microsoft 365 Defender spécifiques si vous disposez d’autorisations pour celles-ci. Si vous disposez uniquement d’autorisations de gestion pour Microsoft 365 Defender pour Office, par exemple, vous pouvez créer des détections personnalisées à l’aide `Email` de tables, mais pas `Identity` de tables.  

Pour gérer les autorisations requises, un **administrateur général** peut :

- Attribuez le rôle **d’administrateur de sécurité** ou **d’opérateur de sécurité** dans [Centre d'administration Microsoft 365](https://admin.microsoft.com/) sous Administrateur **de sécurité** **des rôles** > .
- Vérifiez les paramètres RBAC pour Microsoft Defender pour point de terminaison dans [Microsoft 365 Defender](https://security.microsoft.com/) sous **Paramètres des rôles** >  > **d’autorisation**. Sélectionnez le rôle correspondant pour attribuer l’autorisation **gérer les paramètres de sécurité** .

> [!NOTE]
> Pour gérer les détections personnalisées, les **opérateurs de sécurité** ont besoin de l’autorisation **gérer les paramètres de sécurité** dans Microsoft Defender pour point de terminaison si RBAC est activé.

## <a name="create-a-custom-detection-rule"></a>Créer une règle de détection personnalisée
### <a name="1-prepare-the-query"></a>1. Préparez la requête.

Dans le portail Microsoft 365 Defender, accédez à **La chasse avancée** et sélectionnez une requête existante ou créez une nouvelle requête. Lorsque vous utilisez une nouvelle requête, exécutez la requête pour identifier les erreurs et comprendre les résultats possibles.

>[!IMPORTANT]
>Pour empêcher le service de retourner trop d’alertes, chaque règle est limitée à la génération de 100 alertes uniquement chaque fois qu’il s’exécute. Avant de créer une règle, ajustez votre requête pour éviter les alertes pour une activité quotidienne normale.


#### <a name="required-columns-in-the-query-results"></a>Colonnes obligatoires dans les résultats de la requête
Pour créer une règle de détection personnalisée, le de requête doit retourner les colonnes suivantes:

- `Timestamp`— utilisé pour définir l’horodatage des alertes générées
- `ReportId`— active les recherches pour les enregistrements d’origine
- L’une des colonnes suivantes qui identifient des appareils, des utilisateurs ou des boîtes aux lettres spécifiques:
    - `DeviceId`
    - `DeviceName`
    - `RemoteDeviceName`
    - `RecipientEmailAddress`
    - `SenderFromAddress`(expéditeur d’enveloppe ou adresse de chemin d’accès)
    - `SenderMailFromAddress`(adresse de l’expéditeur affichée par le client de messagerie)
    - `RecipientObjectId`
    - `AccountObjectId`
    - `AccountSid`
    - `AccountUpn`
    - `InitiatingProcessAccountSid`
    - `InitiatingProcessAccountUpn`
    - `InitiatingProcessAccountObjectId`

>[!NOTE]
>La prise en charge d’entités supplémentaires sera ajoutée à mesure que de nouvelles tables seront ajoutées au [schéma de chasse avancé](advanced-hunting-schema-tables.md).

Les requêtes simples, telles que celles qui n’utilisent pas le ou `summarize` l’opérateur `project` pour personnaliser ou agréger les résultats, retournent généralement ces colonnes courantes.

Il existe différentes façons de s’assurer que des requêtes plus complexes retournent ces colonnes. Par exemple, si vous préférez agréger et compter par entité sous une colonne telle que `DeviceId`, vous pouvez toujours retourner `Timestamp` et `ReportId` en l’obtenant à partir de l’événement le plus récent impliquant chaque unique `DeviceId`.


> [!IMPORTANT]
> Évitez de filtrer les détections personnalisées à l’aide de la `Timestamp` colonne. Les données utilisées pour les détections personnalisées sont pré-filtrées en fonction de la fréquence de détection.


L’exemple de requête ci-dessous compte le nombre d’appareils uniques (`DeviceId`) avec des détections antivirus et utilise ce nombre pour rechercher uniquement les appareils avec plus de cinq détections. Pour retourner le dernier `Timestamp` et le correspondant `ReportId`, il utilise l’opérateur `summarize` avec la `arg_max` fonction.

```kusto
DeviceEvents
| where ingestion_time() > ago(1d)
| where ActionType == "AntivirusDetection"
| summarize (Timestamp, ReportId)=arg_max(Timestamp, ReportId), count() by DeviceId
| where count_ > 5
```

> [!TIP]
> Pour de meilleures performances de requête, définissez un filtre de temps qui correspond à la fréquence d’exécution prévue pour la règle. Étant donné que l’exécution la moins fréquente est _toutes les 24 heures_, le filtrage du jour précédent couvre toutes les nouvelles données.

### <a name="2-create-new-rule-and-provide-alert-details"></a>2. Créez une règle et fournissez les détails de l’alerte.

Avec la requête dans l’éditeur de requête, sélectionnez **Créer une règle de détection** et spécifiez les détails d’alerte suivants :

- **Nom de la détection** : nom de la règle de détection ; doit être unique
- **Fréquence** : intervalle d’exécution de la requête et d’action. [Consultez les conseils supplémentaires ci-dessous](#rule-frequency)
- **Titre de l’alerte** : titre affiché avec les alertes déclenchées par la règle ; doit être unique
- **Gravité** : risque potentiel du composant ou de l’activité identifié par la règle
- **Catégorie** : composant ou activité de menace identifié par la règle
- **MITRE ATT&techniques CK** : une ou plusieurs techniques d’attaque identifiées par la règle, comme indiqué dans [l’infrastructure MITRE ATT&CK](https://attack.mitre.org/). Cette section est masquée pour certaines catégories d’alertes, notamment les programmes malveillants, les ransomware, les activités suspectes et les logiciels indésirables.
- **Description** : plus d’informations sur le composant ou l’activité identifié par la règle 
- **Actions recommandées** : actions supplémentaires que les répondeurs peuvent effectuer en réponse à une alerte

#### <a name="rule-frequency"></a>Fréquence de la règle
Lorsque vous enregistrez une nouvelle règle, elle s’exécute et vérifie les correspondances des 30 derniers jours de données. La règle s’exécute ensuite à intervalles fixes, en appliquant une durée de recherche en fonction de la fréquence choisie :

- **Toutes les 24 heures** : s’exécute toutes les 24 heures, en vérifiant les données des 30 derniers jours
- **Toutes les 12 heures** : s’exécute toutes les 12 heures, en vérifiant les données des dernières 48 heures
- **Toutes les 3 heures** : s’exécute toutes les 3 heures, en vérifiant les données des 12 dernières heures
- **Toutes les heures** : s’exécute toutes les heures, en vérifiant les données des dernières 4 heures

Lorsque vous modifiez une règle, elle s’exécute avec les modifications appliquées lors de la prochaine exécution planifiée en fonction de la fréquence que vous définissez. La fréquence de la règle est basée sur l’horodatage des événements et non sur l’heure d’ingestion.



>[!TIP]
> Faites correspondre les filtres d’heure de votre requête à la durée de recherche. Les résultats en dehors de la durée de recherche sont ignorés.  

Sélectionnez la fréquence qui correspond à la fréquence à laquelle vous souhaitez surveiller les détections. Tenez compte de la capacité de votre organisation à répondre aux alertes.

### <a name="3-choose-the-impacted-entities"></a>3. Choisissez les entités concernées.
Identifiez les colonnes dans les résultats de votre requête où vous vous attendez à trouver l’entité principale affectée ou affectée. Par exemple, une requête peut retourner des adresses d’expéditeur (`SenderFromAddress` ou `SenderMailFromAddress`) et de destinataire (`RecipientEmailAddress`). Identifier laquelle de ces colonnes représente la principale entité impactée qui aide le service à agréger les alertes pertinentes, à corréler les incidents et à cibler les actions de réponse.

Vous ne pouvez sélectionner qu’une seule colonne pour chaque type d’entité (boîte aux lettres, utilisateur ou appareil). Les colonnes qui ne sont pas retournées par votre requête ne peuvent pas être sélectionnées.

### <a name="4-specify-actions"></a>4. Spécifiez des actions.
Votre règle de détection personnalisée peut effectuer automatiquement des actions sur les appareils, fichiers ou utilisateurs retournés par la requête.

#### <a name="actions-on-devices"></a>Actions sur des appareils
Ces actions sont appliquées aux appareils dans la colonne `DeviceId`des résultats de la requête:
- **Isoler l’appareil** : utilise Microsoft Defender pour point de terminaison pour appliquer une isolation réseau complète, empêchant l’appareil de se connecter à n’importe quelle application ou service. [En savoir plus sur l’isolation Microsoft Defender pour point de terminaison machine](/windows/security/threat-protection/microsoft-defender-atp/respond-machine-alerts#isolate-devices-from-the-network)
- **Collecter le package d’investigation** : collecte les informations sur l’appareil dans un fichier ZIP. [En savoir plus sur le package d’investigation Microsoft Defender pour point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/respond-machine-alerts#collect-investigation-package-from-devices)
- **Exécuter l’analyse antivirus** : effectue une analyse antivirus complète Microsoft Defender sur l’appareil
- **Lancer une enquête** : lance une [enquête automatisée](m365d-autoir.md) sur l’appareil
- **Restreindre l’exécution de l’application** : définit des restrictions sur l’appareil pour autoriser uniquement l’exécution des fichiers signés avec un certificat émis par Microsoft. [En savoir plus sur les restrictions d’application avec Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/respond-machine-alerts#restrict-app-execution)

#### <a name="actions-on-files"></a>Actions sur les fichiers
Une fois sélectionné, vous pouvez choisir d’appliquer l’action de **fichier de mise en quarantaine** sur les fichiers dans la colonne , `InitiatingProcessSHA1``SHA256`ou `InitiatingProcessSHA256` dans la `SHA1`colonne des résultats de la requête. Cette action supprime le fichier de son emplacement actuel et place une copie en quarantaine.

#### <a name="actions-on-users"></a>Actions sur les utilisateurs
Lorsque cette option est sélectionnée, l’action **Marquez l’utilisateur comme compromis** est effectuée sur les utilisateurs de la colonne`AccountObjectId`, `InitiatingProcessAccountObjectId` ou `RecipientObjectId`colonne des résultats de la requête. Cette action définit le niveau de risque des utilisateurs sur « élevé » dans Azure Active Directory, ce qui déclenche les [stratégies de protection des identités correspondantes](/azure/active-directory/identity-protection/overview-identity-protection).

> [!NOTE]
> L’action d’autorisation ou de blocage pour les règles de détection personnalisées n’est actuellement pas prise en charge sur Microsoft 365 Defender.

### <a name="5-set-the-rule-scope"></a>5. Définissez l’étendue de la règle.
Définissez l’étendue pour spécifier les appareils couverts par la règle. L’étendue influence les règles qui vérifient les appareils et n’affecte pas les règles qui vérifient uniquement les boîtes aux lettres et les comptes d’utilisateur ou les identités.

Lorsque vous définissez l’étendue, vous pouvez sélectionner:

- Tous les appareils
- Groupes d’appareils spécifiques

Seules les données des appareils dans l’étendue seront interrogées. En outre, les actions seront effectuées uniquement sur ces appareils.

### <a name="6-review-and-turn-on-the-rule"></a>6. Examinez et activez la règle.
Après avoir examiné la règle, sélectionnez **Créer** pour l’enregistrer. La règle de détection personnalisée s’exécute immédiatement. Il s’exécute à nouveau en fonction de la fréquence configurée pour rechercher des correspondances, générer des alertes et effectuer des actions de réponse.


>[!Important] 
>Les détections personnalisées doivent être régulièrement examinées pour vérifier l’efficacité et l’efficacité. Pour vous assurer que vous créez des détections qui déclenchent des alertes vraies, prenez le temps de passer en revue vos détections personnalisées existantes en suivant les étapes décrites dans [Gérer les règles de détection personnalisées existantes](#manage-existing-custom-detection-rules). <br>  
Vous conservez le contrôle sur l’étendue ou la spécificité de vos détections personnalisées afin que toutes les fausses alertes générées par les détections personnalisées indiquent la nécessité de modifier certains paramètres des règles.


## <a name="manage-existing-custom-detection-rules"></a>Gérer les règles de détection personnalisées existantes
Vous pouvez afficher la liste des règles de détection personnalisées existantes, vérifier leurs exécutions précédentes et passer en revue les alertes qu’elles ont déclenchées. Vous pouvez également exécuter une règle à la demande et la modifier.

>[!TIP]
> Les alertes déclenchées par des détections personnalisées sont disponibles sur les alertes et les API d’incident. Pour plus d’informations, consultez LES [API Microsoft 365 Defender prises en charge](api-supported.md).

### <a name="view-existing-rules"></a>Afficher les règles existantes

Pour afficher toutes les règles de détection personnalisée existantes, accédez aux **règles de détection personnalisée** de **chasse** > . La page répertorie toutes les règles avec les informations d’exécution suivantes:

- **Dernière exécution** : lors de la dernière exécution d’une règle pour rechercher des correspondances de requête et générer des alertes
- **État de la dernière exécution** : indique si une règle s’est exécutée correctement
- **Exécution suivante** : la prochaine exécution planifiée
- **État** : si une règle a été activée ou désactivée

### <a name="view-rule-details-modify-rule-and-run-rule"></a>Afficher les détails de la règle, modifier la règle et exécuter la règle

Pour afficher des informations complètes sur une règle de détection personnalisée, accédez aux **règles de détection personnalisées** de **chasse** > , puis sélectionnez le nom de la règle. Vous pouvez ensuite afficher des informations générales sur la règle, y compris des informations sur son état d’exécution et son étendue. La page fournit également la liste des alertes et actions déclenchées.

:::image type="content" source="../../media/custom-detect-rules-view.png" alt-text="Page détails de la règle de détection personnalisée dans le portail Microsoft 365 Defender" lightbox="../../media/custom-detect-rules-view.png":::<br>
*Détails de la règle de détection personnalisée*

Vous pouvez également effectuer les actions suivantes sur la règle à partir de cette page:

- **Exécuter** : exécutez la règle immédiatement. Cela réinitialise également l’intervalle pour la prochaine exécution.
- **Modifier** : modifier la règle sans modifier la requête
- **Modifier la requête** : modifier la requête dans la chasse avancée
-  /  Activer **Désactiver** : activer la règle ou l’empêcher de s’exécuter
- **Supprimer** : désactivez la règle et supprimez-la

### <a name="view-and-manage-triggered-alerts"></a>Afficher et gérer les alertes déclenchées

Dans l’écran détails de la règle (**détections personnalisées** >  de **chasse** > **[Nom de la règle]**), accédez à **Alertes déclenchées**, qui répertorie les alertes générées par les correspondances avec la règle. Sélectionner une alerte pour afficher des informations détaillées à son sujet et effectuer les actions suivantes:

- Gérer l’alerte en définissant son état et sa classification (alerte vraie ou fausse)
- Lier l’alerte à un incident
- Exécuter la requête qui a déclenché l’alerte en cas de repérage avancé

### <a name="review-actions"></a>Passer en revue les actions
Dans l’écran détails de la règle (**détections personnalisées** >  de **chasse** > **[Nom de la règle]**), accédez à **Actions déclenchées**, qui répertorie les actions effectuées en fonction des correspondances avec la règle.

>[!TIP]
>Pour afficher rapidement des informations et agir sur un élément d’une table, utilisez la colonne de sélection [&#10003;] à gauche de la table.

>[!NOTE]
>Certaines colonnes de cet article peuvent ne pas être disponibles dans Microsoft Defender pour point de terminaison. [Activez Microsoft 365 Defender](m365d-enable.md) pour rechercher des menaces à l’aide de sources de données supplémentaires. Vous pouvez déplacer vos flux de travail de chasse avancés de Microsoft Defender pour point de terminaison vers Microsoft 365 Defender en suivant les étapes de migration [des requêtes de chasse avancées à partir de Microsoft Defender pour point de terminaison](advanced-hunting-migrate-from-mde.md).

## <a name="see-also"></a>Voir aussi
- [Vue d’ensemble des détections personnalisées](custom-detections-overview.md)
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Découvrir le langage de requête de repérage avancé](advanced-hunting-query-language.md)
- [Migrer des requêtes de chasse avancées à partir de Microsoft Defender pour point de terminaison](advanced-hunting-migrate-from-mde.md)
