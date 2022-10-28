---
title: Utiliser des rapports et des audits de conformité des communications
description: En savoir plus sur l’utilisation des rapports et des audits de conformité des communications.
keywords: Microsoft 365, Microsoft Purview, conformité, conformité des communications
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
- tier1
- purview-compliance
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: 05822c0d5c3cf31a87a725d47b707482f2040bd3
ms.sourcegitcommit: a20d30f4e5027f90d8ea4cde95d1d5bacfdd2b5e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2022
ms.locfileid: "68768152"
---
# <a name="use-communication-compliance-reports-and-audits"></a>Utiliser des rapports et des audits de conformité des communications

> [!IMPORTANT]
> Conformité des communications Microsoft Purview fournit les outils pour aider les organisations à détecter les violations de conformité réglementaire (par exemple SEC ou FINRA), telles que des informations sensibles ou confidentielles, des propos harcelants ou menaçants, et le partage de contenu pour adultes. Conçu avec la confidentialité par défaut, les noms d’utilisateur sont pseudonymisés par défaut, les contrôles d’accès en fonction du rôle sont intégrés, les enquêteurs sont activés par un administrateur et les journaux d’audit sont en place pour garantir la confidentialité au niveau de l’utilisateur.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="reports"></a>Rapports

Le tableau de bord **Rapports** est l’emplacement central pour afficher tous les rapports de conformité des communications. Pour afficher et gérer les rapports, les utilisateurs doivent être affectés au groupe de rôles *Observateurs de conformité des communications* .

Les widgets de rapport fournissent une vue rapide des insights les plus couramment nécessaires pour une évaluation globale de l’état des activités de conformité des communications. Les informations contenues dans les widgets de rapport ne peuvent pas être exportées. Les rapports détaillés fournissent des informations détaillées relatives à des domaines de conformité de communication spécifiques et offrent la possibilité de filtrer, de regrouper, de trier et d’exporter des informations lors de l’examen.

Pour le filtre de plage de dates, la date et l’heure des événements sont répertoriées dans temps universel coordonné (UTC). Lors du filtrage des messages pour les rapports, la date/heure locale de l’utilisateur demandeur détermine les résultats en fonction de la conversion de la date/heure locale de l’utilisateur au format UTC. Par exemple, si un utilisateur dans l’heure d’été du Pacifique (PDT) filtre un rapport du 30/08/2021 au 31/8/2021 à 00:00, le rapport inclut les messages du 30/08/2021 07:00 UTC au 31/08/2021 07:00 UTC. Si le même utilisateur se trouvait dans l’est des États-Unis (EDT) lors du filtrage à 00h00, le rapport inclut les messages du 30/08/2021 à 04:00 UTC au 31/08/2021 04:00 UTC.

![Tableau de bord des rapports de conformité des communications](../media/communication-compliance-reports-dashboard.png)

Le **tableau de bord Rapports** contient les widgets de rapport et les liens de rapports détaillés suivants :

### <a name="report-widgets"></a>Widgets de rapport

- **Correspondances de stratégie récentes** : affiche le nombre de correspondances par stratégies actives au fil du temps.
- **Éléments résolus par stratégie** : affiche le nombre d’alertes de correspondance de stratégie résolues par les stratégies au fil du temps.
- **Utilisateurs ayant la plus grande correspondance** de stratégie : affiche les utilisateurs (ou les noms d’utilisateur anonymes) et le nombre de correspondances de stratégie pour une période donnée.
- **Stratégie avec le plus de correspondances** : affiche les stratégies et le nombre de correspondances pour une période donnée, classé du plus haut au plus bas pour les correspondances.
- **Escalades par stratégie** : affiche le nombre d’escalades par stratégie au cours d’une période donnée.

### <a name="detailed-reports"></a>Rapports détaillés

Utilisez l’option *Exporter* pour créer un fichier .csv contenant les détails du rapport pour tout rapport détaillé. *L’option Exporter* le rapport prend en charge les téléchargements de fichiers jusqu’à 3 Mo.

- **Paramètres et état** de stratégie : fournit un aperçu détaillé de la configuration et des paramètres de stratégie, ainsi que de l’état général de chacune des stratégies (correspondances et actions) sur les messages. Inclut des informations de stratégie et la façon dont les stratégies sont associées aux utilisateurs et aux groupes, aux emplacements, aux pourcentages de révision, aux réviseurs, à l’état et à la date de la dernière modification de la stratégie. Utilisez l’option *Exporter* pour créer un fichier .csv contenant les détails du rapport.
- **Éléments et actions par stratégie** : examinez et exportez les éléments correspondants et les actions de correction par stratégie. Inclut des informations de stratégie et la façon dont les stratégies sont associées à :

  - Éléments correspondants
  - Éléments escaladés
  - Éléments résolus
  - Étiqueté comme conforme
  - Étiqueté comme non conforme
  - Étiqueté comme douteux
  - Éléments en attente de révision
  - Notification par l’utilisateur
  - Cas créé

- **Élément et actions par emplacement** : examinez et exportez les éléments correspondants et les actions de correction par emplacement Microsoft 365. Inclut des informations sur la façon dont les plateformes de charge de travail sont associées à :

  - Éléments correspondants
  - Éléments escaladés
  - Éléments résolus
  - Étiqueté comme conforme
  - Étiqueté comme non conforme
  - Étiqueté comme douteux
  - Éléments en attente de révision
  - Notification par l’utilisateur
  - Cas créé

- **Activité par utilisateur** : examinez et exportez les éléments correspondants et les actions de correction par utilisateur. Inclut des informations sur la façon dont les utilisateurs sont associés à :

  - Éléments correspondants
  - Éléments escaladés
  - Éléments résolus
  - Étiqueté comme conforme
  - Étiqueté comme non conforme
  - Étiqueté comme douteux
  - Éléments en attente de révision
  - Notification par l’utilisateur
  - Cas créé

- **Type d’informations sensibles par emplacement** (préversion) : passez en revue et exportez des informations sur la détection des types d’informations sensibles et des sources associées dans les stratégies de conformité des communications. Inclut le total global et la répartition spécifique des instances de type d’informations sensibles dans les sources configurées dans votre organisation. Les valeurs de chaque source tierce sont affichées dans des colonnes distinctes dans le fichier .csv. En voici quelques exemples :

  - Email : types **d’informations** sensibles détectés dans les messages électroniques Exchange.
  - **Teams** : types d’informations sensibles détectés dans les canaux et les messages de conversation Microsoft Teams.
  - **Yammer** : types d’informations sensibles détectés dans les boîtes de réception, les publications, les conversations et les réponses Yammer.
  - **Sources tierces** : types d’informations sensibles détectés pour les activités associées aux connecteurs tiers configurés dans votre organisation. Pour afficher la répartition des sources tierces pour un type d’informations sensibles spécifique dans le rapport, placez la souris sur la valeur du type d’informations sensibles dans la colonne Source tierce.
  - **Autres** : types d’informations sensibles utilisés pour le traitement interne du système. La sélection ou la désélection de cette source pour le rapport n’affecte aucune valeur.

### <a name="message-details-report"></a>Rapport des détails du message

Créez des rapports personnalisés et passez en revue les détails des messages contenus dans des stratégies spécifiques sous l’onglet **Stratégies** . Ces rapports peuvent être utilisés pour les révisions de tous les messages et pour créer un instantané de rapport pour l’état des messages pendant une période de temps personnalisable. Après avoir créé un rapport, vous pouvez afficher et télécharger le rapport de détails sous la forme d’un fichier .csv sous l’onglet **Rapports de détails du message** .

![Rapport détaillé des messages de conformité des communications](../media/communication-compliance-message-detail-report.png)

Pour créer un rapport de détails de message, procédez comme suit :

1. Connectez-vous au portail de conformité Microsoft Purview avec un compte membre du groupe de rôles *Enquêteurs de conformité des communications*.
2. Accédez à l’onglet **Stratégies** , sélectionnez une stratégie, puis sélectionnez **Créer un rapport de détails de message**.
3. Dans le volet **Créer un rapport de détails de message** , entrez un nom pour le rapport dans le champ **Nom du** rapport.
4. Dans **Choisir une plage de dates**, sélectionnez une *date de début* et une *date de fin* pour le rapport.
5. Sélectionnez **Créer**.
6. La confirmation de création du rapport s’affiche.

Selon le nombre d’éléments du rapport, le téléchargement du rapport peut prendre quelques minutes ou quelques heures. Vous pouvez vérifier la progression sous l’onglet Rapports de détails du message. L’état du rapport est *En cours* ou *Prêt pour le téléchargement*. Vous pouvez avoir jusqu’à 15 rapports distincts à traiter simultanément. Pour télécharger un rapport, sélectionnez un rapport dans l’état *Prêt pour le téléchargement* , puis sélectionnez **Télécharger le rapport**.

> [!NOTE]
> Si la période sélectionnée ne renvoie aucun résultat de message dans le rapport, il n’y a pas eu de messages pour la période sélectionnée. Le rapport sera vide.

Les rapports de détails des messages contiennent les informations suivantes pour chaque élément de message dans la stratégie :

- **ID de correspondance** : ID unique du message dans la stratégie.
- **Expéditeur** : expéditeur du message.
- **Destinataires** : destinataires inclus pour le message.
- **Date d’envoi** : date d’envoi du message.
- **Date** de correspondance : date à laquelle le message correspondait aux conditions de stratégie.
- **Objet** : objet du message.
- **Contient des pièces jointes** : état des pièces jointes pour le message. Les valeurs sont *Oui* ou *Non*.
- **Nom de la stratégie** : nom de la stratégie associée au message. Cette valeur sera la même pour tous les messages du rapport.
- **État de l’élément** : état de l’élément de message dans la stratégie. Les valeurs sont *En attente* ou *Résolues*.
- **Balises** : balises affectées au message. Les valeurs sont *Douteuses, Conformes* ou *Non conformes*.
- **Correspondances de mot clé** : correspondances de mot clé pour le message.
- **Réviseurs** : réviseurs affectés au message.
- **En attente pendant (jours)** : nombre de jours pendant lesquels le message a été dans un état d’attente. Pour les messages résolus, la valeur est 0.
- **Commentaire pour résolu** : commentaires pour le message entré lorsqu’il est résolu.
- **Date résolue** : date et heure de résolution du message.
- **Dernière mise à jour par** : nom d’utilisateur de la dernière mise à jour.
- **Dernière mise à jour le** : date et heure de la dernière mise à jour du message.
- **Historique des commentaires** : liste de tous les commentaires pour l’alerte de message, y compris l’auteur du commentaire et la date/heure du commentaire.

## <a name="audit"></a>Audit

Dans certains cas, vous devez fournir des informations aux auditeurs réglementaires ou de conformité pour prouver la supervision des activités et des communications des utilisateurs. Ces informations peuvent être un résumé de toutes les activités associées à une stratégie organisationnelle définie ou chaque fois qu’une stratégie de conformité des communications change. Les stratégies de conformité des communications ont des pistes d’audit intégrées pour une préparation complète aux audits internes ou externes. Les historiques d’audit détaillés de chaque action de création, de modification et de suppression sont capturés par vos stratégies de communication pour fournir une preuve des procédures de supervision.

> [!IMPORTANT]
> L’audit doit être activé pour votre organisation avant que les événements de conformité des communications soient enregistrés. Pour activer l’audit, consultez [Activer le journal d’audit](/microsoft-365/compliance/communication-compliance-configure#step-2-required-enable-the-audit-log). Lorsque des activités déclenchent des événements capturés dans le journal d’audit Microsoft 365, il peut s’avérer nécessaire de mettre jusqu’à 48 heures avant que ces événements ne puissent être consultés dans les stratégies de conformité des communications.

Pour afficher les activités de mise à jour de la stratégie de conformité des communications, sélectionnez le contrôle **Exporter les mises à jour** de stratégie dans la page principale de toute stratégie. Les rôles *Administration global* ou Administrateur de conformité des communications doivent vous être *attribués* pour exporter les activités de mise à jour. Cette action génère un fichier d’audit au format .csv qui contient les informations suivantes :

|Champ|Détails|
|---|---|
| **CreationDate** | Date à laquelle l’activité de mise à jour a été effectuée dans une stratégie. |
| **ID utilisateur** | Utilisateur qui a effectué l’activité de mise à jour dans une stratégie. |
| **Operations** | Opérations de mise à jour effectuées sur la stratégie. |
| **AuditData** | Source de données principale pour toutes les activités de mise à jour de stratégie. Toutes les activités de mise à jour sont enregistrées et séparées par des séparateurs de virgules. |

Pour afficher les activités de révision de conformité des communications pour une stratégie, sélectionnez le contrôle **Exporter les activités de révision** dans la page **Vue d’ensemble** d’une stratégie spécifique. Les rôles *Administration globaux* ou *Administrateurs de conformité des communications* doivent vous être attribués pour exporter les activités de révision. Cette action génère un fichier d’audit au format .csv qui contient les informations suivantes :

|Champ|Détails|
|---|---|
| **CreationDate** | Date à laquelle l’activité de révision a été effectuée dans une stratégie. |
| **ID utilisateur** | Utilisateur qui a effectué l’activité de révision dans une stratégie. |
| **Operations** | Passez en revue les opérations effectuées sur la stratégie. |
| **AuditData** | Source de données principale pour toutes les activités de révision de stratégie. Toutes les activités de révision sont enregistrées et séparées par des séparateurs de virgules. |

Vous pouvez également afficher les activités d’audit dans le journal d’audit unifié ou avec l’applet de commande PowerShell [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) . Pour en savoir plus sur les stratégies de rétention des journaux d’audit, consultez [Gérer les stratégies de rétention des journaux d’audit](/microsoft-365/compliance/audit-log-retention-policies).

Par exemple, l’exemple suivant retourne les activités de toutes les activités de révision de surveillance (stratégies et règles) :

```PowerShell
Search-UnifiedAuditLog -StartDate $startDate -EndDate $endDate -RecordType AeD -Operations SupervisoryReviewTag
```

Cet exemple retourne les activités de mise à jour pour vos stratégies de conformité des communications :

```PowerShell
Search-UnifiedAuditLog -StartDate $startDate -EndDate $endDate -RecordType Discovery -Operations SupervisionPolicyCreated,SupervisionPolicyUpdated,SupervisionPolicyDeleted
```

Cet exemple retourne des activités qui correspondent à vos stratégies de conformité des communications actuelles :

```PowerShell
Search-UnifiedAuditLog -StartDate $startDate -EndDate $endDate -Operations SupervisionRuleMatch
```

Les correspondances de stratégie de conformité des communications sont stockées dans une boîte aux lettres de supervision pour chaque stratégie. Dans certains cas, vous devrez peut-être vérifier la taille de votre boîte aux lettres de supervision pour une stratégie pour vous assurer que vous n’approchez pas de la taille de stockage actuelle de 100 Go ou de la limite de 1 million de messages. Si la limite de boîte aux lettres est atteinte, les correspondances de stratégie ne sont pas capturées et vous devez créer une stratégie (avec les mêmes paramètres) pour continuer à capturer les correspondances pour les mêmes activités.

Pour vérifier la taille d’une boîte aux lettres de supervision pour une stratégie, procédez comme suit :

1. [Connectez-vous à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).
2. Exécutez la commande suivante :

    ```PowerShell
    ForEach ($p in Get-SupervisoryReviewPolicyV2 | Sort-Object Name)
    {
       "<Name of your communication compliance policy>: " + $p.Name
       Get-MailboxStatistics $p.ReviewMailbox | ft ItemCount,TotalItemSize
    }
    ```
