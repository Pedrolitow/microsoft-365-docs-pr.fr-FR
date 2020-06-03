---
title: Créer et gérer des règles de détection personnalisées dans Microsoft Threat Protection
description: Découvrez comment créer et gérer des règles de détection personnalisées sur la base de requêtes de chasse avancées.
keywords: chasse de menace, recherche de menace, recherche de menace informatique, protection contre les menaces Microsoft, Microsoft 365, MTP, M365, recherche, requête, télémétrie, détections personnalisées, règles, schéma, Kusto, Microsoft 365, protection contre les menaces Microsoft, RBAC, autorisations, Microsoft Defender ATP
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: lomayor
author: lomayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.openlocfilehash: 1a84c568d1411cf21c23e59cabad955c40c18ac6
ms.sourcegitcommit: 7bb3d8a93a85246172e2499d6c58c390e46f5bb9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "44498362"
---
# <a name="create-and-manage-custom-detections-rules"></a>Créer et gérer des règles de détection personnalisées

**S’applique à :**
- Protection Microsoft contre les menaces

Les règles de détection personnalisées générées à partir de requêtes de [chasse avancées](advanced-hunting-overview.md) vous permettent de surveiller de manière proactive différents événements et États du système, y compris l’activité de violation présumée et les points de terminaison mal configurés. Vous pouvez les configurer pour qu’elles s’exécutent à intervalles réguliers, générant des alertes et en prenant des mesures de réponse chaque fois qu’il y a des correspondances.

## <a name="required-permissions-for-managing-custom-detections"></a>Autorisations requises pour la gestion des détections personnalisées

Pour gérer les détections personnalisées, vous devez disposer de l’un des rôles suivants :

- **Administrateur de sécurité** — le rôle d’administrateur de sécurité ou d’administrateur de sécurité est un [rôle Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles#security-administrator) pour la gestion de différents paramètres de sécurité dans le centre de sécurité Microsoft 365 et divers portails et services.

- **Opérateur de sécurité** : le rôle opérateur de sécurité est un [rôle Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles#security-administrator) pour la gestion des alertes et dispose d’un accès global en lecture seule sur les fonctionnalités liées à la sécurité, y compris toutes les informations du centre de sécurité Microsoft 365. Ce rôle est suffisant pour la gestion des détections personnalisées uniquement si le contrôle d’accès basé sur un rôle (RBAC) est désactivé dans Microsoft Defender ATP. Si RBAC est configuré, vous avez également besoin de l’autorisation **gérer les paramètres de sécurité** pour Microsoft Defender ATP.

Pour gérer les autorisations requises, un **administrateur général** peut effectuer les opérations suivantes :

- Attribuez le rôle **administrateur** de sécurité ou **opérateur de sécurité** dans le [Centre d’administration Microsoft 365](https://admin.microsoft.com/) sous **rôles**de l’administrateur de la  >  **sécurité**.
- Vérifiez les paramètres RBAC pour Microsoft Defender ATP dans le [Centre de sécurité Microsoft Defender](https://securitycenter.windows.com/) **sous**  >  **Permissions**  >  **rôles**des autorisations. Sélectionnez le rôle correspondant pour attribuer l’autorisation **gérer les paramètres de sécurité** .

> [!NOTE]
> Pour gérer les détections personnalisées, les **opérateurs de sécurité** doivent disposer de l’autorisation **gérer les paramètres de sécurité** dans Microsoft Defender ATP si le RBAC est activé.

## <a name="create-a-custom-detection-rule"></a>Créer une règle de détection personnalisée
### <a name="1-prepare-the-query"></a>1. Préparez la requête.

Dans le centre de sécurité Microsoft 365, accédez à la **chasse avancée** et sélectionnez une requête existante ou créez une nouvelle requête. Lors de l’utilisation d’une nouvelle requête, exécutez la requête pour identifier les erreurs et comprendre les résultats possibles.

#### <a name="required-columns-in-the-query-results"></a>Colonnes requises dans les résultats de la requête
Pour créer une règle de détection personnalisée, la requête doit renvoyer les colonnes suivantes :

- `Timestamp`
- Une des colonnes suivantes de l’appareil, de l’utilisateur ou de la boîte aux lettres :
    - `DeviceId`
    - `DeviceName`
    - `RemoteDeviceName`
    - `RecipientEmailAddress`
    - `SenderFromAddress`(adresse d’expéditeur ou de chemin d’accès de retour)
    - `SenderMailFromAddress`(adresse de l’expéditeur affichée par le client de messagerie)
    - `RecipientObjectId`
    - `AccountObjectId`
    - `AccountSid`
    - `AccountUpn`
    - `InitiatingProcessAccountSid`
    - `InitiatingProcessAccountUpn`
    - `InitiatingProcessAccountObjectId`
>[!NOTE]
>Une prise en charge des entités supplémentaires sera ajoutée au fur et à mesure que de nouvelles tables seront ajoutées au [schéma de chasse avancé](advanced-hunting-schema-tables.md).

Les requêtes simples, telles que celles qui n’utilisent pas l' `project` `summarize` opérateur ou pour personnaliser ou agréger des résultats, renvoient généralement ces colonnes communes.

Il existe plusieurs façons de s’assurer que les requêtes plus complexes renvoient ces colonnes. Par exemple, si vous préférez agréger et dénombrer par entité sous une colonne telle que `DeviceId` , vous pouvez toujours renvoyer `Timestamp` en récupérant l’événement le plus récent impliquant chaque `DeviceId` .

La requête d’exemple ci-dessous compte le nombre d’appareils uniques ( `DeviceId` ) avec des détections d’antivirus et utilise ce nombre pour rechercher uniquement les appareils comportant plus de cinq détections. Pour renvoyer le dernier `Timestamp` , il utilise l' `summarize` opérateur avec la `arg_max` fonction.

```kusto
DeviceEvents
| where ActionType == "AntivirusDetection"
| summarize Timestamp = max(Timestamp), count() by DeviceId, SHA1, InitiatingProcessAccountObjectId 
| where count_ > 5
```
### <a name="2-create-new-rule-and-provide-alert-details"></a>2. créer une règle et fournir des détails d’alerte.

À l’aide de la requête dans l’éditeur de requête, sélectionnez **créer une règle de détection** et spécifiez les détails d’alerte suivants :

- **Nom** de la détection : nom de la règle de détection
- **Fréquence** : intervalle d’exécution de la requête et d’exécution de l’action. [Consultez les conseils supplémentaires ci-dessous.](#rule-frequency)
- **Titre** de l’alerte — titre affiché avec des alertes déclenchées par la règle
- **Gravité** — risque potentiel de l’activité ou du composant identifié par la règle
- **Catégorie** — composant de menace ou activité identifiée par la règle
- **Mitre att&CK techniques** : une ou plusieurs techniques d’attaque identifiées par la règle comme indiqué dans la [Mitre att&CK Framework](https://attack.mitre.org/). Cette section ne s’applique pas et est masquée pour certaines catégories d’alertes, y compris les programmes malveillants, les ransomware, les activités suspectes et les logiciels indésirables.
- **Description** : plus d’informations sur le composant ou l’activité identifié par la règle 
- **Actions recommandées** : actions supplémentaires que les répondeurs peuvent entreprendre en réponse à une alerte

#### <a name="rule-frequency"></a>Fréquence de la règle
Une fois enregistrée, une règle de détection personnalisée nouvelle ou modifiée s’exécute et recherche des correspondances des données des 30 derniers jours. La règle s’exécute à nouveau à intervalles fixes et lookback durées en fonction de la fréquence choisie :

- **Toutes les 24 heures** – s’exécute toutes les 24 heures, vérification des données des 30 derniers jours
- **Toutes les 12 heures** — s’exécute toutes les 12 heures, en vérifiant les données des 24 dernières heures
- **Toutes les 3 heures** — s’exécute toutes les 3 heures, en vérifiant les données des 6 dernières heures
- **Toutes les heures** — s’exécute toutes les heures, en vérifiant les données des 2 dernières heures

Sélectionnez la fréquence correspondant à la fréquence à laquelle vous souhaitez surveiller les détections et tenez compte de la capacité de votre organisation à répondre aux alertes.

### <a name="3-choose-the-impacted-entities"></a>3. Choisissez les entités concernées.
Identifiez les colonnes de vos résultats de requête où vous vous attendez à trouver l’entité principale affectée ou concernée. Par exemple, une requête peut renvoyer des adresses d’expéditeur ( `SenderFromAddress` ou `SenderMailFromAddress` ) et de destinataire ( `RecipientEmailAddress` ). L’identification de l’une de ces colonnes qui représente l’entité affectée principale aide le service à agréger les alertes appropriées, à corréler les incidents et à cibler les actions de réponse.

Vous pouvez sélectionner une seule colonne pour chaque type d’entité (boîte aux lettres, utilisateur ou appareil). Les colonnes qui ne sont pas renvoyées par votre requête ne peuvent pas être sélectionnées.

### <a name="4-specify-actions"></a>4. spécifiez les actions.
Votre règle de détection personnalisée peut effectuer automatiquement des actions sur les appareils, les fichiers ou les utilisateurs qui sont renvoyés par la requête.

#### <a name="actions-on-devices"></a>Actions sur les appareils
Ces actions sont appliquées aux appareils dans la `DeviceId` colonne des résultats de la requête :
- **Appareil isolé** : utilise Microsoft Defender ATP pour appliquer l’isolement réseau complet, ce qui empêche l’appareil de se connecter à une application ou à un service. [En savoir plus sur l’isolation de l’ordinateur Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/respond-machine-alerts#isolate-machines-from-the-network)
- **Package d’enquête de collecte** — recueille des informations sur les périphériques dans un fichier zip. [En savoir plus sur le package d’enquête Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/respond-machine-alerts#collect-investigation-package-from-machines)
- **Exécuter l’analyse antivirus** : effectue une analyse complète de l’antivirus Windows Defender sur l’appareil.
- **Lancer une enquête** : lance une [enquête automatisée](mtp-autoir.md) sur l’appareil.
- **Limiter l’exécution de l’application** : définit des restrictions sur l’appareil pour autoriser uniquement les fichiers signés avec un certificat émis par Microsoft à exécuter. [En savoir plus sur les restrictions d’application avec Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/respond-machine-alerts#restrict-app-execution)

#### <a name="actions-on-files"></a>Actions sur les fichiers
Lorsque cette option est sélectionnée, vous pouvez choisir d’appliquer l’action de **mise en quarantaine** sur les fichiers dans la `SHA1` colonne,, `InitiatingProcessSHA1` `SHA256` ou `InitiatingProcessSHA256` des résultats de la requête. Cette action supprime le fichier de son emplacement actuel et place une copie en quarantaine.

#### <a name="actions-on-users"></a>Actions sur les utilisateurs
Lorsque cette option est sélectionnée, l’action **marquer l’utilisateur comme compromis** est effectuée sur les utilisateurs dans la `AccountObjectId` `InitiatingProcessAccountObjectId` colonne, ou `RecipientObjectId` des résultats de la requête. Cette action définit le niveau de risque de l’utilisateur sur « élevé » dans Azure Active Directory, en déclenchant des [stratégies de protection des identités](https://docs.microsoft.com/azure/active-directory/identity-protection/overview-identity-protection)correspondantes.

> [!NOTE]
> L’action autoriser ou bloquer pour les règles de détection personnalisées n’est pas prise en charge actuellement sur la protection contre les menaces Microsoft.

### <a name="5-set-the-rule-scope"></a>5. définir l’étendue de la règle.
Définissez l’étendue pour spécifier les appareils couverts par la règle. L’étendue influe sur les règles qui vérifient les périphériques et n’affecte pas les règles qui vérifient uniquement les boîtes aux lettres et les comptes d’utilisateur ou les identités.

Lors de la définition de l’étendue, vous pouvez sélectionner :

- Tous les appareils
- Groupes d’appareils spécifiques

Seules les données provenant d’appareils dans l’étendue seront interrogées. En outre, les actions ne seront effectuées que sur ces appareils.

### <a name="6-review-and-turn-on-the-rule"></a>6. Vérifiez et activez la règle.
Après avoir examiné la règle, cliquez sur **créer** pour l’enregistrer. La règle de détection personnalisée s’exécute immédiatement. Il s’exécute à nouveau en fonction de la fréquence configurée pour vérifier les correspondances, générer des alertes et prendre des mesures de réponse.

## <a name="manage-existing-custom-detection-rules"></a>Gérer les règles de détection personnalisées existantes
Vous pouvez afficher la liste des règles de détection personnalisées existantes, vérifier leurs exécutions précédentes et examiner les alertes qu’elles ont déclenchées. Vous pouvez également exécuter une règle à la demande et la modifier.

### <a name="view-existing-rules"></a>Afficher les règles existantes

Pour afficher toutes les règles de détection personnalisées existantes, **accédez à recherche**  >  **personnalisée**pour la recherche. La page répertorie toutes les règles avec les informations d’exécution suivantes :

- **Dernière exécution** : lors de la dernière exécution d’une règle pour rechercher les correspondances des requêtes et générer des alertes
- **État de la dernière exécution** : indique si une règle a été exécutée avec succès
- **Exécution suivante** : exécution planifiée suivante
- **État** : indique si une règle a été activée ou désactivée

### <a name="view-rule-details-modify-rule-and-run-rule"></a>Afficher les détails de la règle, modifier la règle et exécuter la règle

Pour afficher des informations détaillées sur une **règle de détection**personnalisée, sélectionnez le nom de la règle dans la liste des règles de recherche  >  **personnalisée**. Cette opération ouvre une page sur la règle de détection personnalisée avec des informations générales sur la règle, notamment les détails de l’alerte, l’état d’exécution et l’étendue. Il fournit également la liste des alertes déclenchées et des actions déclenchées.

![Page des détails de la règle de détection personnalisée](../../media/custom-detection-details.png)<br>
*Détails de la règle de détection personnalisée*

Vous pouvez également effectuer les actions suivantes sur la règle à partir de cette page :

- **Exécuter** : exécuter la règle immédiatement. Cela réinitialise également l’intervalle de la prochaine exécution.
- **Modifier** : modifier la règle sans modifier la requête
- **Requête modifier** : modifier la requête dans la recherche avancée
- **Activer**  /  **Désactiver** : activer la règle ou l’arrêter de s’exécuter
- **Supprimer** : désactiver la règle et la supprimer

### <a name="view-and-manage-triggered-alerts"></a>Afficher et gérer les alertes déclenchées

Dans l’écran détails de la**règle (recherche**  >  **personnalisée**  >  de recherche **[nom de la règle]**), accédez à **alertes déclenchées** pour afficher la liste des alertes générées par correspondance à la règle. Sélectionnez une alerte pour afficher des informations détaillées sur cette alerte et effectuez les actions suivantes sur cette alerte :

- Gérer l’alerte en définissant son état et sa classification (alerte true ou false)
- Liaison de l’alerte à un incident
- Exécuter la requête qui a déclenché l’alerte sur la chasse avancée

### <a name="review-actions"></a>Examiner les actions
Dans l’écran**Détails de la règle (recherche**  >  **personnalisée**  >  de recherche **[nom de la règle]**), accédez à **actions déclenchées** pour afficher la liste des actions effectuées en fonction des correspondances avec la règle.

>[!TIP]
>Pour afficher rapidement des informations et agir sur un élément d’un tableau, utilisez la colonne de sélection [&#10003;] à gauche du tableau.

## <a name="related-topic"></a>Voir aussi
- [Vue d’ensemble des détections personnalisées](custom-detections-overview.md)
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Découvrir le langage de requête de repérage avancé](advanced-hunting-query-language.md)