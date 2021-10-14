---
title: Utiliser les rapports et audits de conformité des communications
description: En savoir plus sur l’utilisation des rapports et audits de conformité des communications.
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.SupervisoryReview
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: a36f4ac9cceaefc52e380f28554b5cb6360c00f4
ms.sourcegitcommit: be074f57e33c811bb3857043152825209bc8af07
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2021
ms.locfileid: "60335681"
---
# <a name="use-communication-compliance-reports-and-audits"></a>Utiliser les rapports et audits de conformité des communications

## <a name="reports"></a>Rapports

Le nouveau tableau **de bord Rapports** est l’emplacement central pour afficher tous les rapports de conformité des communications. Les widgets de rapport fournissent un aperçu rapide des informations les plus couramment nécessaires pour une évaluation globale de l’état des activités de conformité des communications. Les informations contenues dans les widgets de rapport ne peuvent pas être exportées. Les rapports détaillés fournissent des informations détaillées sur des domaines spécifiques de conformité des communications et offrent la possibilité de filtrer, de grouper, de trier et d’exporter des informations lors de la révision. 

Pour le filtre de plage de dates, la date et l’heure des événements sont répertoriées au temps universel coordonné (UTC). Lors du filtrage des messages pour les rapports, la date/l’heure locale de l’utilisateur demandeur détermine les résultats en fonction de la conversion de la date/heure locale de l’utilisateur en heure UTC. Par exemple, si un utilisateur de l’heure d’été pacifique (PDT) des États-Unis filtre un rapport du 30/08/2021 au 31/08/2021 à 00:00, le rapport inclut les messages du 30/08/2021 07:00 UTC au 31/08/2021 07:00 UTC. Si le même utilisateur était en heure d’été est (EDT) pour le filtrage à 00:00, le rapport inclut les messages du 30/08/2021 04:00 UTC au 31/08/2021 04:00 UTC.

![Tableau de bord des rapports de conformité des communications.](../media/communication-compliance-reports-dashboard.png)

Le tableau **de bord Rapports contient** les widgets de rapport et les liens de rapports détaillés suivants :

- **Widget de correspondances de stratégie récente** : affiche le nombre de correspondances par stratégie active au fil du temps.
- **Éléments résolus par** widget de stratégie : affiche le nombre d’alertes de correspondance de stratégie résolues par stratégie au fil du temps.
- **Utilisateurs avec la plupart des** widgets de correspondance de stratégie : affiche les utilisateurs (ou les noms d’utilisateur anonymisés) et le nombre de correspondances de stratégie pour une période donnée.
- **Stratégie avec la plupart des widgets** de correspondances : affiche les stratégies et le nombre de correspondances pour une période donnée, classées de la plus haute à la plus faible pour les correspondances.
- **Escalades par** widget de stratégie : affiche le nombre d’escalades par stratégie sur une période donnée.
- **Paramètres** de stratégie et rapport détaillé sur l’état : fournit une analyse détaillée de la configuration et des paramètres de stratégie, ainsi que de l’état général de chacune des stratégies (correspondances et actions) sur les messages. Inclut les informations de stratégie et la façon dont les stratégies sont associées aux utilisateurs et groupes, aux emplacements, aux pourcentages d’avis, aux réviseurs, à l’état et à la dernière modification de la stratégie. Utilisez *l’option* Exporter pour créer un fichier .csv contenant les détails du rapport.
- **Éléments et actions par rapport détaillé de** stratégie : examiner et exporter les éléments correspondants et les actions de correction par stratégie. Inclut les informations de stratégie et la façon dont les stratégies sont associées à :

    - Éléments en correspondance
    - Éléments escalades
    - Éléments résolus
    - Marqué comme conforme
    - Marqué comme non conforme
    - Marqué comme discutable
    - Éléments en attente de révision
    - Notification de l’utilisateur
    - Cas créé

    Utilisez *l’option* Exporter pour créer un fichier .csv contenant les détails du rapport.
- **Rapport détaillé sur l’élément** et les actions par emplacement : examiner et exporter les éléments correspondants et les actions de correction par Microsoft 365 emplacement. Inclut des informations sur la façon dont les plateformes de charge de travail sont associées à :

    - Éléments en correspondance
    - Éléments escalades
    - Éléments résolus
    - Marqué comme conforme
    - Marqué comme non conforme
    - Marqué comme discutable
    - Éléments en attente de révision
    - Notification de l’utilisateur
    - Cas créé

    Utilisez *l’option* Exporter pour créer un fichier .csv contenant les détails du rapport.
- **Activité par rapport détaillé de l’utilisateur** : examiner et exporter les éléments correspondants et les actions de correction par utilisateur. Inclut des informations sur la façon dont les utilisateurs sont associés à :

    - Éléments en correspondance
    - Éléments escalades
    - Éléments résolus
    - Marqué comme conforme
    - Marqué comme non conforme
    - Marqué comme discutable
    - Éléments en attente de révision
    - Notification de l’utilisateur
    - Cas créé

    Utilisez *l’option* Exporter pour créer un fichier .csv contenant les détails du rapport.

- **Type d’informations sensibles par rapport** détaillé d’emplacement (prévisualisation) : examiner et exporter des informations sur la détection des types d’informations sensibles et des sources associées dans les stratégies de conformité des communications. Inclut le total global et la répartition spécifique des instances de types d’informations sensibles dans les sources configurées dans votre organisation. Voici quelques exemples :

    - **Courrier** électronique : types d’informations sensibles détectés dans Exchange messages électroniques.
    - **Teams**: types d’informations sensibles détectés dans Microsoft Teams et les messages de conversation.
    - **Skype Entreprise**: types d’informations sensibles détectés dans Skype pour les communications professionnelles.
    - **Yammer**: types d’informations sensibles détectés dans Yammer boîtes de réception, billets, conversations et réponses.
    - **Sources tierces**: types d’informations sensibles détectés pour les activités associées à des connecteurs tiers configurés dans votre organisation. Pour afficher la répartition des sources tierces pour un type d’informations sensibles spécifique dans le rapport, pointez votre souris sur la valeur du type d’informations sensibles dans la colonne source tierce.
    - **Autres**: types d’informations sensibles utilisés pour le traitement interne du système. La sélection ou la désélection de cette source pour le rapport n’affecte aucune valeur.

    Utilisez *l’option* Exporter pour créer un fichier .csv contenant les détails du rapport. Les valeurs de chaque source tierce sont affichées dans des colonnes distinctes dans .csv fichier.

## <a name="audit"></a>Audit

Dans certains cas, vous devez fournir des informations aux auditeurs de réglementation ou de conformité pour prouver la surveillance des activités et des communications des utilisateurs. Ces informations peuvent être un résumé de toutes les activités associées à une stratégie d’organisation définie ou à chaque modification d’une stratégie de conformité des communications. Les stratégies de conformité des communications ont des pistes d’audit intégrées pour une préparation complète aux audits internes ou externes. Les historiques d’audit détaillés de chaque action de création, de modification et de suppression sont capturés par vos stratégies de communication pour fournir une preuve des procédures de surveillance.

> [!IMPORTANT]
> L’audit doit être activé pour votre organisation avant que les événements de conformité des communications soient enregistrés. Pour activer l’audit, voir [Activer le journal d’audit.](communication-compliance-configure.md#step-2-required-enable-the-audit-log) Lorsque des activités déclenchent des événements capturés dans le journal d’audit Microsoft 365, l’affichage de ces événements dans les stratégies de conformité des communications peut prendre jusqu’à 48 heures.

Pour afficher les activités de mise à jour des **stratégies** de conformité des communications, sélectionnez le contrôle Exporter les mises à jour de stratégie sur la page principale de n’importe quelle stratégie. Les rôles Administrateur *global* ou Administrateur de conformité des *communications* doivent vous être attribués pour exporter les activités de mise à jour. Cette action génère un fichier d’audit au format .csv qui contient les informations suivantes :

|**Field**|**Détails**|
|:-----|:-----|
| **CreationDate** | Date à laquelle l’activité de mise à jour a été effectuée dans une stratégie. |
| **UserIds** | Utilisateur qui a effectué l’activité de mise à jour dans une stratégie. |
| **Operations** | Opérations de mise à jour effectuées sur la stratégie. |
| **AuditData** | Ce champ est la source de données principale pour toutes les activités de mise à jour de stratégie. Toutes les activités de mise à jour sont enregistrées et séparées par des délimiteur de virgule. |

Pour afficher les activités de révision de  la conformité des communications pour une stratégie, sélectionnez le contrôle Des activités de révision de l’exportation dans la **page** Vue d’ensemble d’une stratégie spécifique. Les rôles Administrateur *global* ou Administrateur de conformité des *communications* doivent vous être attribués pour exporter les activités de révision. Cette action génère un fichier d’audit au format .csv qui contient les informations suivantes :

|**Field**|**Détails**|
|:-----|:-----|
| **CreationDate** | Date à laquelle l’activité de révision a été effectuée dans une stratégie. |
| **UserIds** | Utilisateur qui a effectué l’activité de révision dans une stratégie. |
| **Operations** | Les opérations de révision effectuées sur la stratégie. |
| **AuditData** | Ce champ est la source de données principale pour toutes les activités de révision de stratégie. Toutes les activités de révision sont enregistrées et séparées par des délimiteur de virgule. |

Vous pouvez également afficher les activités d’audit dans le journal d’audit unifié ou avec l’cmdlet [PowerShell Search-UnifiedAuditLog.](/powershell/module/exchange/search-unifiedauditlog) Pour en savoir plus sur les stratégies de rétention du journal d’audit, voir [Gérer les stratégies de rétention du journal d’audit.](audit-log-retention-policies.md)

Par exemple, l’exemple suivant renvoie les activités de toutes les activités de révision de surveillance (stratégies et règles) :

```PowerShell
Search-UnifiedAuditLog -StartDate $startDate -EndDate $endDate -RecordType AeD -Operations SupervisoryReviewTag
```

Cet exemple renvoie les activités de mise à jour de vos stratégies de conformité des communications :

```PowerShell
Search-UnifiedAuditLog -StartDate $startDate -EndDate $endDate -RecordType Discovery -Operations SupervisionPolicyCreated,SupervisionPolicyUpdated,SupervisionPolicyDeleted
```

Cet exemple renvoie les activités qui correspondent à vos stratégies de conformité des communications actuelles :

```PowerShell
Search-UnifiedAuditLog -StartDate $startDate -EndDate $endDate -Operations SupervisionRuleMatch
```

Les correspondances de stratégie de conformité des communications sont stockées dans une boîte aux lettres de surveillance pour chaque stratégie. Dans certains cas, vous devrez peut-être vérifier la taille de votre boîte aux lettres de surveillance pour une stratégie afin de vous assurer que vous n’approchez pas la taille de stockage actuelle de 100 Go ou la limite de 1 million de messages. Si la limite de boîte aux lettres est atteinte, les correspondances de stratégie ne sont pas capturées et vous devez créer une stratégie (avec les mêmes paramètres) pour continuer à capturer des correspondances pour les mêmes activités.

Pour vérifier la taille d’une boîte aux lettres de surveillance pour une stratégie, complétez les étapes suivantes :

1. Utilisez la cmdlet [Connecter-ExchangeOnline](/powershell/module/exchange/connect-exchangeonline) dans Exchange Online module PowerShell V2 pour vous connecter à Exchange Online PowerShell à l’aide de l’authentification moderne.
2. Exécutez la commande suivante dans PowerShell :

    ```PowerShell
    ForEach ($p in Get-SupervisoryReviewPolicyV2 | Sort-Object Name)
    {
       "<Name of your communication compliance policy>: " + $p.Name
       Get-MailboxStatistics $p.ReviewMailbox | ft ItemCount,TotalItemSize
    }
    ```
