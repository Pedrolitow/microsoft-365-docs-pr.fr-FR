---
title: Stratégies d’alerte dans les centres de sécurité et de conformité
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
- MOE150
ms.assetid: 8927b8b9-c5bc-45a8-a9f9-96c732e58264
ms.custom:
- seo-marvel-apr2020
description: Créez des stratégies d’alerte dans le centre de sécurité et conformité dans Office 365 et Microsoft 365 pour surveiller les menaces potentielles, les pertes de données et les problèmes d’autorisations.
ms.openlocfilehash: 5749b38ca9b72c859e9c553ccbb4fe6a44be9754
ms.sourcegitcommit: 29eb89b8ba0628fbef350e8995d2c38369a4ffa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "49682957"
---
# <a name="alert-policies-in-the-security-and-compliance-center"></a>Stratégies d’alerte dans le Centre de sécurité et de conformité

Vous pouvez utiliser les outils de tableau de bord des stratégies et des alertes d’alerte dans les centres de sécurité et de conformité Microsoft 365 pour créer des stratégies d’alerte, puis afficher les alertes générées lorsque les utilisateurs effectuent des activités qui répondent aux conditions d’une stratégie d’alerte. Il existe plusieurs stratégies d’alerte par défaut qui vous aident à surveiller les activités telles que l’attribution de privilèges d’administrateur dans Exchange Online, les attaques de programmes malveillants, les campagnes de hameçonnage et les niveaux inhabituels de suppression de fichiers et de partage externe.

Les stratégies d’alerte vous permettent de catégoriser les alertes déclenchées par une stratégie, d’appliquer la stratégie à tous les utilisateurs de votre organisation, de définir un niveau de seuil pour le déclenchement d’une alerte et de décider s’il faut recevoir des notifications par courrier électronique lorsque des alertes sont déclenchées. Il existe également une page **afficher les alertes** dans le centre de sécurité et conformité où vous pouvez afficher et filtrer des alertes, définir un statut d’alerte pour vous aider à gérer les alertes, puis ignorer les alertes après avoir résolu ou résolu l’incident sous-jacent.

> [!NOTE]
> Les stratégies d’alerte sont disponibles pour les organisations disposant d’un abonnement Microsoft 365 Enterprise, Office 365 Enterprise ou Office 365 gouvernement E1/F1/G1, E3/G3 ou E5/G5. La fonctionnalité avancée est uniquement disponible pour les organisations disposant d’un abonnement E5/G5, ou pour les organisations qui ont un abonnement E1/F1/G1 ou E3/G3 et un abonnement Microsoft Defender pour Office 365 P2 ou une conformité Microsoft 365 E5 ou un abonnement de module complémentaire eDiscovery et d’audit à E5. La fonctionnalité nécessitant un abonnement E5/G5 ou complément est mise en surbrillance dans cette rubrique. Notez également que les stratégies d’alerte sont disponibles dans les environnements Office 365 GCC, GCC High et DoD US Government.

## <a name="how-alert-policies-work"></a>Fonctionnement des stratégies d’alerte

Voici un aperçu rapide du fonctionnement des stratégies d’alerte et des alertes déclenchées lorsque l’activité de l’utilisateur ou de l’administrateur correspond aux conditions d’une stratégie d’alerte.

![Vue d’ensemble du fonctionnement des stratégies d’alerte](../media/e02a622d-b429-448b-8107-dd1a4770b4e0.png)

1. Un administrateur de votre organisation crée, configure et active une stratégie d’alerte à l’aide de la page **stratégies d’alerte** du centre de sécurité et de conformité. Vous pouvez également créer des stratégies d’alerte à l’aide de la cmdlet **New-protectionalert vous permet** dans la sécurité & PowerShell du centre de conformité. Pour créer des stratégies d’alerte, vous devez disposer du rôle gérer les alertes ou configuration de l’organisation dans le centre de sécurité et de conformité.

   > [!NOTE]
   > La création ou la mise à jour d’une stratégie d’alerte prend jusqu’à 24 heures après le déclenchement des alertes par la stratégie. Cela est dû au fait que la stratégie doit être synchronisée avec le moteur de détection d’alerte.

2. Un utilisateur effectue une activité qui correspond aux conditions d’une stratégie d’alerte. Dans le cas d’une attaque par programme malveillant, les messages électroniques infectés envoyés aux utilisateurs de votre organisation déclenchent une alerte.

3. Microsoft 365 génère une alerte qui s’affiche sur la page **afficher les alertes** dans le centre de sécurité & conformité. Par ailleurs, si les notifications par courrier électronique sont activées pour la stratégie d’alerte, Microsoft envoie une notification à une liste de destinataires. Les alertes qu’un administrateur ou d’autres utilisateurs peuvent voir que la page afficher les alertes est déterminée par les rôles attribués à l’utilisateur. Pour plus d’informations, consultez la section [autorisations RBAC requises pour afficher les alertes](#rbac-permissions-required-to-view-alerts) .

4. Un administrateur gère les alertes dans le centre de sécurité et de conformité. La gestion des alertes consiste à affecter un statut d’alerte pour faciliter le suivi et la gestion de toute enquête.

## <a name="alert-policy-settings"></a>Paramètres de stratégie d’alerte

Une stratégie d’alerte est constituée d’un ensemble de règles et de conditions qui définissent l’activité de l’utilisateur ou de l’administrateur qui génère une alerte, la liste des utilisateurs qui déclenchent l’alerte si elles effectuent l’activité, ainsi qu’un seuil qui définit le nombre de fois que l’activité doit avoir lieu avant le déclenchement d’une alerte. Vous pouvez également catégoriser la stratégie et lui attribuer un niveau de gravité. Ces deux paramètres vous aident à gérer les stratégies d’alerte (et les alertes déclenchées lorsque les conditions de la stratégie sont respectées), car vous pouvez filtrer ces paramètres lors de la gestion des stratégies et de l’affichage des alertes dans le centre de sécurité et de conformité. Par exemple, vous pouvez afficher les alertes qui répondent aux conditions de la même catégorie ou afficher les alertes ayant le même niveau de gravité.

Pour afficher et créer des stratégies d’alerte, accédez à, [https://protection.office.com](https://protection.office.com) puis sélectionnez alertes d’alerte des **alertes** \> .

![Dans le centre de sécurité et de conformité, sélectionnez alertes, puis sélectionnez stratégies d’alerte pour afficher et créer des stratégies d’alerte.](../media/09ebd451-8e84-44e1-aefc-63e70bba4d97.png)

Une stratégie d’alerte se compose des paramètres et conditions suivants.

- **Activité suivi de l’alerte** : créez une stratégie pour suivre une activité ou dans certains cas quelques activités associées, ce qui permet de partager un fichier avec un utilisateur externe en le partageant, en affectant des autorisations d’accès ou en créant un lien anonyme. Lorsqu’un utilisateur effectue l’activité définie par la stratégie, une alerte est déclenchée en fonction des paramètres de seuil d’alerte.

    > [!NOTE]
    > Les activités que vous pouvez suivre dépendent de la planification Office 365 Enterprise ou Office 365 pour le gouvernement américain de votre organisation. En règle générale, les activités liées aux campagnes de programmes malveillants et aux attaques de hameçonnage requièrent un abonnement E5/G5 ou un abonnement E1/F1/G1 ou E3/G3 avec un abonnement [pour les compléments Office 365](../security/office-365-security/office-365-atp.md) plan 2.

- **Conditions d’activité** : pour la plupart des activités, vous pouvez définir des conditions supplémentaires qui doivent être remplies pour déclencher une alerte. Les conditions communes incluent des adresses IP (de sorte qu’une alerte est déclenchée lorsque l’utilisateur effectue l’activité sur un ordinateur avec une adresse IP spécifique ou dans une plage d’adresses IP), si une alerte est déclenchée si un utilisateur ou des utilisateurs spécifiques effectuent cette activité, et si l’activité est effectuée sur un nom de fichier ou une URL spécifique. Vous pouvez également configurer une condition qui déclenche une alerte lorsque l’activité est effectuée par un utilisateur de votre organisation. Les conditions disponibles dépendent de l’activité sélectionnée.

- **Lorsque l’alerte est déclenchée** , vous pouvez configurer un paramètre qui définit la fréquence à laquelle une activité peut se produire avant le déclenchement d’une alerte. Cela vous permet de configurer une stratégie pour générer une alerte chaque fois qu’une activité correspond aux conditions de la stratégie, lorsqu’un certain seuil est dépassé, ou lorsque l’activité de l’alerte suivi de l’alerte devient inhabituelle pour votre organisation.

    ![Configurer la façon dont les alertes sont déclenchées, en fonction de la date d’activité, d’un seuil ou d’une activité inhabituelle pour votre organisation](../media/97ee1ed2-e7a9-47a2-a980-5f9f63872c65.png)

    Si vous sélectionnez le paramètre basé sur une activité inhabituelle, Microsoft établit une valeur de base qui définit la fréquence normale de l’activité sélectionnée. Il faut au maximum sept jours pour établir cette ligne de base, pendant laquelle les alertes ne seront pas générées. Une fois la configuration de référence établie, une alerte est déclenchée lorsque la fréquence de l’activité suivie par la stratégie d’alerte dépasse largement la valeur de base. Pour les activités liées à l’audit (telles que les activités de fichiers et de dossiers), vous pouvez établir une ligne de base basée sur un seul utilisateur ou sur tous les utilisateurs de votre organisation ; pour les activités liées aux programmes malveillants, vous pouvez établir une ligne de base basée sur une seule famille de programmes malveillants, un destinataire unique ou tous les messages de votre organisation.

    > [!NOTE]
    > La possibilité de configurer des stratégies d’alerte en fonction d’un seuil ou d’une activité inhabituelle nécessite un abonnement E5/G5 ou un abonnement E1/F1/G1 ou E3/G3 avec un abonnement Microsoft Defender for Office 365 P2, Microsoft 365 E5 Compliance ou Microsoft 365 eDiscovery et un abonnement audit Add-on. Les organisations disposant d’un abonnement E1/F1/G1 et E3/G3 ne peuvent créer que des stratégies d’alerte lorsqu’une alerte est déclenchée à chaque fois qu’une activité se produit.

- **Catégorie d’alerte** : pour faciliter le suivi et la gestion des alertes générées par une stratégie, vous pouvez affecter l’une des catégories suivantes à une stratégie.

  - Protection contre la perte de données

  - Gouvernance des informations

  - Flux de messagerie

  - Autorisations

  - Gestion des menaces

  - Autres

  Lorsqu’une activité correspond aux conditions de la stratégie d’alerte, l’alerte générée est marquée avec la catégorie définie dans ce paramètre. Cela vous permet de suivre et de gérer les alertes qui ont le même paramètre de catégorie sur la page **afficher les alertes** dans le centre de sécurité et de conformité, car vous pouvez trier et filtrer les alertes en fonction de la catégorie.

- **Gravité d’alerte** : similaire à la catégorie d’alerte, vous affectez un attribut de gravité (**faible**, **moyenne**, **haute** ou **informatif**) pour les stratégies d’alerte. Comme la catégorie d’alerte, lorsqu’une activité correspond aux conditions de la stratégie d’alerte, l’alerte générée est marquée avec le même niveau de gravité que celui défini pour la stratégie d’alerte. De nouveau, cela vous permet de suivre et de gérer les alertes qui ont le même paramètre de gravité sur la page **afficher les alertes** . Par exemple, vous pouvez filtrer la liste des alertes afin d’afficher uniquement les alertes dont la gravité est **élevée** .

    > [!TIP]
    > Lors de la configuration d’une stratégie d’alerte, envisagez d’affecter une sévérité supérieure aux activités susceptibles d’avoir des conséquences négatives, telles que la détection de programmes malveillants après livraison aux utilisateurs, l’affichage de données sensibles ou classifiées, le partage de données avec des utilisateurs externes ou d’autres activités susceptibles de provoquer une perte de données ou des menaces de sécurité. Cela peut vous aider à hiérarchiser les alertes et les actions que vous effectuez pour examiner et résoudre les causes sous-jacentes.

- **Notifications par courrier électronique** : vous pouvez configurer la stratégie de sorte que les notifications par courrier électronique soient envoyées (ou non envoyées) à une liste d’utilisateurs lorsqu’une alerte est déclenchée. Vous pouvez également définir une limite de notification quotidienne de sorte qu’une fois le nombre maximal de notifications atteint, aucune notification supplémentaire n’est envoyée pour l’alerte au cours de ce jour. En plus des notifications par courrier électronique, vous ou d’autres administrateurs pouvez afficher les alertes déclenchées par une stratégie sur la page **afficher les alertes** . Envisagez d’activer les notifications par courrier électronique pour les stratégies d’alerte d’une catégorie spécifique ou dont le paramètre de gravité est plus élevé.

## <a name="default-alert-policies"></a>Stratégies d’alerte par défaut

Microsoft propose des stratégies d’alerte intégrées qui permettent d’identifier les autorisations d’administrateur Exchange en cas d’abus, d’activité de programmes malveillants, de menaces externes et internes potentielles et les risques de gouvernance des informations. Sur la page **stratégies d’alerte** , les noms de ces stratégies prédéfinies sont en gras et le type de stratégie est défini sur **système**. Ces stratégies sont activées par défaut. Vous pouvez désactiver ces stratégies (ou de nouveau), configurer une liste de destinataires vers lesquels envoyer des notifications par courrier électronique et définir une limite de notification quotidienne. Les autres paramètres de ces stratégies ne peuvent pas être modifiés.

Le tableau suivant répertorie et décrit les stratégies d’alerte par défaut disponibles et la catégorie à laquelle chaque stratégie est affectée. La catégorie permet de déterminer les alertes qu’un utilisateur peut afficher sur la page afficher les alertes. Pour plus d’informations, consultez la section [autorisations RBAC requises pour afficher les alertes](#rbac-permissions-required-to-view-alerts) .

Le tableau indique également la planification Office 365 entreprise et Office 365 pour le gouvernement américain requis pour chacune d’entre elles. Certaines stratégies d’alerte par défaut sont disponibles si votre organisation dispose de l’abonnement de module complémentaire approprié en plus d’un abonnement E1/F1/G1 ou E3/G3.

| Stratégie d’alerte par défaut | Description | Catégorie | Abonnement entreprise Office 365 |
|:-----|:-----|:-----|:-----|
|**Un clic d’URL potentiellement malveillant a été détecté**|Génère une alerte lorsqu’un utilisateur protégé par [des liens fiables](../security/office-365-security/atp-safe-links.md) dans votre organisation clique sur un lien malveillant. Cet événement est déclenché lorsque les modifications de verdict d’URL sont identifiées par Microsoft Defender pour Office 365 ou lorsque les utilisateurs remplacent les pages de liens fiables (en fonction de la stratégie de liens fiables Microsoft 365 pour votre organisation). Cette stratégie d’alerte a un paramètre de gravité **élevée** . Pour les clients Defender pour Office 365 P2, E5, G5, cette alerte déclenche automatiquement une [enquête et une réponse automatiques dans office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-air). Pour plus d’informations sur les événements qui déclenchent cette alerte, reportez-vous à la rubrique [configurer des stratégies de liens fiables](../security/office-365-security/set-up-atp-safe-links-policies.md).|Gestion des menaces|L’abonnement de compléments E5/G5 ou Defender pour Office 365 P2|
|**Résultat de l’envoi de l’administrateur terminé**|Génère une alerte lorsqu’un [dépôt administrateur](../security/office-365-security/admin-submission.md) termine la nouvelle analyse de l’entité soumise. Une alerte est déclenchée chaque fois qu’un résultat de nouvelle analyse est affiché à partir d’une soumission de l’administrateur. Ces alertes sont destinées à vous rappeler d' [examiner les résultats des envois précédents](https://protection.office.com/reportsubmission), de soumettre les messages signalés par l’utilisateur pour obtenir les dernières vérifications de stratégie et de réanalyser les verdicts, et vous aider à déterminer si les stratégies de filtrage de votre organisation ont l’impact escompté. Cette stratégie a un paramètre de gravité **faible** .|Gestion des menaces|E1/F1, E3 ou E5|
|**Enquête manuelle déclenchée par l’administrateur du courrier électronique**|Génère une alerte lorsqu’un administrateur déclenche l’enquête manuelle d’un e-mail à partir de l’Explorateur de menaces. Pour plus d’informations, reportez-vous à [exemple : un administrateur de sécurité déclenche une enquête à partir de l’Explorateur de menaces] ( https://docs.microsoft.com/microsoft-365/security/office-365-security/automated-investigation-response-office#example-a-security-administrator-triggers-an-investigation-from-threat-explorer) . Cette alerte informe votre organisation que l’enquête a été lancée. L’alerte fournit des informations sur ce qui a été déclenché et inclut un lien vers l’enquête. Cette stratégie a un paramètre de gravité d' **information** .|Gestion des menaces| E5/G5 ou Microsoft Defender pour l’abonnement au complément Office 365 P2| 
|**Création d’une règle de transfert/redirection**|Génère une alerte lorsqu’une personne de votre organisation crée une règle de boîte de réception pour sa boîte aux lettres qui transfère ou redirige les messages vers un autre compte de messagerie. Cette stratégie effectue uniquement le suivi des règles de boîte de réception créées à l’aide d’Outlook sur le Web (anciennement Outlook Web App) ou Exchange Online PowerShell. Cette stratégie a un paramètre de gravité **faible** . Pour plus d’informations sur l’utilisation des règles de boîte de réception pour transférer et rediriger le courrier électronique dans Outlook sur le Web, consultez [la rubrique utiliser des règles dans Outlook sur le Web pour transférer automatiquement des messages vers un autre compte](https://support.office.com/article/1433e3a0-7fb0-4999-b536-50e05cb67fed).|Gestion des menaces|E1/F1/G1, E3/G3 ou E5/G5|
|**recherche de découverte électronique démarrée ou exportée**|Génère une alerte lorsqu’un utilisateur utilise l’outil de recherche de contenu dans le centre de sécurité et de conformité. Une alerte est déclenchée lorsque les activités de recherche de contenu suivantes sont effectuées : <br/><br/>* Une recherche de contenu est démarrée<br/>* Les résultats d’une recherche de contenu sont exportés<br/>* Un rapport de recherche de contenu est exporté<br/><br/>Des alertes sont également déclenchées lorsque les activités de recherche de contenu précédentes sont effectuées en association avec un cas de découverte électronique. Cette stratégie a un paramètre de gravité **moyenne** . Pour plus d’informations sur les activités de recherche de contenu, voir [Search for eDiscovery Activities dans le journal d’audit](search-for-ediscovery-activities-in-the-audit-log.md#ediscovery-activities).|Gestion des menaces|E1/F1/G1, E3/G3 ou E5/G5|
|**Élévation des privilèges d’administrateur Exchange**|Génère une alerte lorsqu’un utilisateur se voit attribuer des autorisations d’administration dans votre organisation Exchange Online. Par exemple, lorsqu’un utilisateur est ajouté au groupe de rôles gestion de l’organisation dans Exchange Online. Cette stratégie a un paramètre de gravité **faible** .|Autorisations|E1/F1/G1, E3/G3 ou E5/G5|
|**Messages électroniques contenant des programmes malveillants supprimés après la remise**|Génère une alerte lorsque des messages contenant des programmes malveillants sont remis à des boîtes aux lettres de votre organisation. Si cet événement se produit, Microsoft supprime les messages infectés des boîtes aux lettres Exchange Online à l’aide de la [purge automatique avec zéro heure](../security/office-365-security/zero-hour-auto-purge.md). Cette stratégie a un paramètre de gravité d' **information** et déclenche automatiquement une [enquête et une réponse automatisées dans Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-air).|Gestion des menaces|E5/G5 ou Microsoft Defender pour l’abonnement au complément Office 365 P2|
|**Messages électroniques contenant des URL d’hameçonnage supprimées après la remise**|Génère une alerte lorsque des messages contenant des hameçons sont remis à des boîtes aux lettres de votre organisation. Si cet événement se produit, Microsoft supprime les messages infectés des boîtes aux lettres Exchange Online à l’aide de la [purge automatique avec zéro heure](../security/office-365-security/zero-hour-auto-purge.md). Cette stratégie a un paramètre de gravité d' **information** et déclenche automatiquement une [enquête et une réponse automatisées dans Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-air).|Gestion des menaces|L’abonnement de compléments E5/G5 ou Defender pour Office 365 P2|
|**Courrier électronique signalé par l’utilisateur comme programme malveillant ou hameçonnage**|Génère une alerte lorsque les utilisateurs de votre organisation signalent des messages en tant que courrier électronique de hameçonnage à l’aide du complément de message de rapport. Cette stratégie a un paramètre de gravité d' **information** . Pour plus d’informations sur ce complément, reportez-vous à [la rubrique utiliser le complément de message de rapport](https://support.office.com/article/b5caa9f1-cdf3-4443-af8c-ff724ea719d2). Pour les clients Defender pour Office 365 P2, E5, G5, cette alerte déclenche automatiquement une [enquête et une réponse automatiques dans office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-air).|Gestion des menaces|E1/F1/G1, E3/G3 ou E5/G5|
|**Limite d’envoi de courrier électronique dépassée**|Génère une alerte lorsqu’une personne de votre organisation a envoyé plus de courriers que ce qui est autorisé par la stratégie de courrier indésirable sortant. Il s’agit généralement d’une indication que l’utilisateur envoie trop de courriers électroniques ou que le compte peut être compromis. Cette stratégie a un paramètre de gravité **moyenne** . Si vous obtenez une alerte générée par cette stratégie d’alerte, il est recommandé de [vérifier si le compte d’utilisateur est compromis](../security/office-365-security/responding-to-a-compromised-email-account.md).|Gestion des menaces|E1/F1/G1, E3/G3 ou E5/G5|
|**Les messages ont été retardés**|Génère une alerte lorsque Microsoft ne peut pas envoyer de messages électroniques à votre organisation locale ou à un serveur partenaire à l’aide d’un connecteur. Dans ce cas, le message est mis en file d’attente dans Office 365. Cette alerte est déclenchée lorsqu’il y a 2 000 messages ou plus qui ont été mis en file d’attente pendant plus d’une heure. Cette stratégie a un paramètre de gravité **élevée** .|Flux de messagerie|E1/F1/G1, E3/G3 ou E5/G5|
|**Campagne anti-programme malveillant détectée après la remise**|Génère une alerte lorsqu’un nombre anormalement élevé de messages contenant des programmes malveillants est remis aux boîtes aux lettres de votre organisation. Si cet événement se produit, Microsoft supprime les messages infectés des boîtes aux lettres Exchange Online. Cette stratégie a un paramètre de gravité **élevée** .|Gestion des menaces|E5/G5 ou Microsoft Defender pour l’abonnement au complément Office 365 P2|
|**Campagne anti-programme malveillant détectée et bloquée**|Génère une alerte lorsqu’un utilisateur a tenté d’envoyer un nombre anormalement élevé de messages électroniques contenant un certain type de programme malveillant aux utilisateurs de votre organisation. Si cet événement se produit, les messages infectés sont bloqués par Microsoft et ne sont pas remis aux boîtes aux lettres. Cette stratégie a un paramètre de gravité **faible** .|Gestion des menaces|L’abonnement de compléments E5/G5 ou Defender pour Office 365 P2|
|**Campagne anti-programme malveillant détectée dans SharePoint et OneDrive**|Génère une alerte lorsqu’un volume inhabituellement élevé de programmes malveillants ou de virus est détecté dans des fichiers situés dans des sites SharePoint ou des comptes OneDrive de votre organisation. Cette stratégie a un paramètre de gravité **élevée** .|Gestion des menaces|L’abonnement de compléments E5/G5 ou Defender pour Office 365 P2|
|**Hameçonnage envoyé en raison du remplacement de client ou d’utilisateur**<sup>1</sup>|Génère une alerte lorsque Microsoft détecte qu’un administrateur ou un remplacement d’utilisateur a autorisé la remise d’un message de hameçonnage à une boîte aux lettres. Voici quelques exemples de remplacements : une boîte de réception ou une règle de flux de messagerie qui autorise les messages provenant d’un expéditeur ou d’un domaine spécifique, ou une stratégie de blocage du courrier indésirable qui autorise les messages provenant d’expéditeurs ou de domaines spécifiques. Cette stratégie a un paramètre de gravité **élevée** .|Gestion des menaces|L’abonnement de compléments E5/G5 ou Defender pour Office 365 P2|
|**Activité de transfert de courrier électronique suspecte**|Génère une alerte lorsqu’une personne de votre organisation a transféré automatiquement le courrier électronique à un compte externe suspect. Il s’agit d’un avertissement précoce pour le comportement pouvant indiquer que le compte est compromis, mais pas suffisamment sérieux pour limiter l’utilisateur. Cette stratégie a un paramètre de gravité **moyenne** . Bien qu’il soit rare, une alerte générée par cette stratégie peut être une anomalie. Il est recommandé de [vérifier si le compte d’utilisateur est compromis](../security/office-365-security/responding-to-a-compromised-email-account.md).|Gestion des menaces|E1/F1/G1, E3/G3 ou E5/G5|
|**Modèles d’envoi de courrier électronique suspects détectés**|Génère une alerte lorsqu’un utilisateur de votre organisation a envoyé un courrier électronique suspect et qu’il n’est pas autorisé à envoyer des courriers électroniques. Il s’agit d’un avertissement précoce pour le comportement qui peut indiquer que le compte est compromis, mais pas suffisamment sérieux pour limiter l’utilisateur. Cette stratégie a un paramètre de gravité **moyenne** . Bien qu’il soit rare, une alerte générée par cette stratégie peut être une anomalie. Toutefois, il est recommandé de [vérifier si le compte d’utilisateur est compromis](../security/office-365-security/responding-to-a-compromised-email-account.md).|Gestion des menaces|E1/F1/G1, E3/G3 ou E5/G5  |
|**Client non autorisé à envoyer des courriers électroniques**|Génère une alerte lorsque la plupart du trafic de messagerie de votre organisation a été détecté comme suspect et que Microsoft a empêché votre organisation d’envoyer des courriers électroniques. Examinez les comptes d’utilisateur et d’administrateur potentiellement compromis, les nouveaux connecteurs ou les relais ouverts, puis contactez le support Microsoft pour débloquer votre organisation. Cette stratégie a un paramètre de gravité **élevée** . Pour plus d’informations sur les raisons pour lesquelles les organisations sont bloquées, voir [corriger les problèmes de remise des messages électroniques pour le code d’erreur 5.7.7 XX dans Exchange Online](https://go.microsoft.com/fwlink/?linkid=2022138).|Gestion des menaces|E1/F1/G1, E3/G3 ou E5/G5|
|**Activité inhabituelle de fichier utilisateur externe**|Génère une alerte lorsqu’un nombre d’activités inhabituellement élevé est effectué sur des fichiers dans SharePoint ou OneDrive par des utilisateurs externes à votre organisation. Cela inclut des activités telles que l’accès aux fichiers, le téléchargement de fichiers et la suppression de fichiers. Cette stratégie a un paramètre de gravité **élevée** .|Gouvernance des informations|E5/G5, Microsoft Defender pour Office 365 P2 ou abonnement au complément Microsoft 365 E5|
|**Volume inhabituel de partage de fichiers externes**|Génère une alerte lorsqu’un nombre anormalement élevé de fichiers dans SharePoint ou OneDrive est partagé avec des utilisateurs extérieurs à votre organisation. Cette stratégie a un paramètre de gravité **moyenne** .|Gouvernance des informations|E5/G5, Defender pour Office 365 P2 ou abonnement au complément Microsoft 365 E5|
|**Volume inhabituel de suppression de fichiers**|Génère une alerte lorsqu’un nombre anormalement élevé de fichiers est supprimé dans SharePoint ou OneDrive pendant une période courte. Cette stratégie a un paramètre de gravité **moyenne** .|Gouvernance des informations|E5/G5, Defender pour Office 365 P2 ou abonnement au complément Microsoft 365 E5|
|**Augmentation inhabituelle d’e-mails signalés comme hameçons**|Génère une alerte lorsqu’il y a une augmentation significative du nombre de personnes au sein de votre organisation à l’aide du complément Report message dans Outlook pour signaler les messages en tant que courriers de hameçonnage. Cette stratégie a un paramètre de gravité **élevée** . Pour plus d’informations sur ce complément, reportez-vous à [la rubrique utiliser le complément de message de rapport](https://support.office.com/article/b5caa9f1-cdf3-4443-af8c-ff724ea719d2).|Gestion des menaces|L’abonnement de compléments E5/G5 ou Defender pour Office 365 P2|
|**Emprunt d’identité d’utilisateur remis à la boîte de réception/dossier**<sup>1,</sup><sup>2</sup>|Génère une alerte lorsque Microsoft détecte qu’un administrateur ou un remplacement d’utilisateur a autorisé la remise d’un message d’hameçonnage par emprunt d’identité d’utilisateur à la boîte de réception (ou à un autre dossier accessible par l’utilisateur) d’une boîte aux lettres. Voici quelques exemples de remplacements : une boîte de réception ou une règle de flux de messagerie qui autorise les messages provenant d’un expéditeur ou d’un domaine spécifique, ou une stratégie de blocage du courrier indésirable qui autorise les messages provenant d’expéditeurs ou de domaines spécifiques. Cette stratégie a un paramètre de gravité **moyenne** .|Gestion des menaces|L’abonnement de compléments E5/G5 ou Defender pour Office 365 P2|
|**Utilisateur non autorisé à envoyer un message électronique**|Génère une alerte lorsqu’une personne de votre organisation est restreinte d’envoyer des messages sortants. Cela se produit généralement lorsqu’un compte est compromis, et que l’utilisateur est affiché sur la page **utilisateurs restreints** dans le centre de sécurité & conformité. (Pour accéder à cette page, accédez à **gestion des menaces > examiner > utilisateurs restreints**). Cette stratégie a un paramètre de gravité **élevée** . Pour plus d’informations sur les utilisateurs avec accès restreint, consultez [la rubrique Suppression d’un utilisateur, d’un domaine ou d’une adresse IP d’une liste rouge après l’envoi de courrier indésirable](https://docs.microsoft.com/office365/securitycompliance/removing-user-from-restricted-users-portal-after-spam).|Gestion des menaces|E1/F1/G1, E3/G3 ou E5/G5|
|||||

> [!NOTE]
> <sup>1</sup> nous avons supprimé temporairement cette stratégie d’alerte par défaut en fonction des commentaires des clients. Nous travaillons sur l’amélioration de l’informatique et la remplacera par une nouvelle version dans un futur proche. En attendant, vous pouvez créer une stratégie d’alerte personnalisée pour remplacer cette fonctionnalité à l’aide des paramètres suivants :<br/>&nbsp; * L’activité est détectée par courrier électronique hameçon au moment de la remise<br/>&nbsp; * Le courrier n’est pas ZAP<br/>&nbsp; * Le sens du message est entrant<br/>&nbsp; * L’état de remise du courrier est remis<br/>&nbsp; * La technologie de détection est la rétention des URL malveillantes, la détonation d’URL, le filtre de hameçonnage avancé, le filtre de hameçonnage général, l’emprunt d’identité de domaine, l’emprunt d’identité d’utilisateur et l’emprunt d’identité de marque<br/><br/>&nbsp;&nbsp;&nbsp;Pour plus d’informations sur la protection anti-hameçonnage dans Office 365, consultez la rubrique [configurer les stratégies anti-hameçonnage et anti-hameçonnage](../security/office-365-security/set-up-anti-phishing-policies.md).<br/><br/><sup>2</sup> pour recréer cette stratégie d’alerte, suivez les instructions de la note de bas de page précédente, mais choisissez emprunt d’identité de l’utilisateur comme seule technologie de détection.

L’activité inhabituelle surveillée par certaines stratégies intégrées est basée sur le même processus que le paramètre de seuil d’alerte précédemment décrit. Microsoft établit une valeur de base qui définit la fréquence normale pour l’activité « normale ». Les alertes sont ensuite déclenchées lorsque la fréquence des activités suivies par la stratégie d’alerte intégrée dépasse largement la valeur de la base.

## <a name="viewing-alerts"></a>Affichage des alertes

Lorsqu’une activité effectuée par les utilisateurs de votre organisation correspond aux paramètres d’une stratégie d’alerte, une alerte est générée et affichée sur la page **afficher les alertes** dans le centre de sécurité et de conformité. En fonction des paramètres d’une stratégie d’alerte, une notification par courrier électronique est également envoyée à une liste d’utilisateurs spécifiés lorsqu’une alerte est déclenchée. Pour chaque alerte, le tableau de bord sur la page **afficher les alertes** affiche le nom de la stratégie d’alerte correspondante, la gravité et la catégorie de l’alerte (définies dans la stratégie d’alerte), ainsi que le nombre de fois qu’une activité a eu lieu et a entraîné la génération de l’alerte. Cette valeur est basée sur le paramètre seuil de la stratégie d’alerte. Le tableau de bord affiche également l’état de chaque alerte. Pour plus d’informations sur l’utilisation de la propriété Status pour gérer les alertes, consultez la section [gestion des alertes](#managing-alerts) .

Pour afficher les alertes, accédez à, [https://protection.office.com](https://protection.office.com) puis sélectionnez **alertes** \> **Afficher** les alertes.

![Dans sécurité et conformité, sélectionnez alertes, puis afficher les alertes pour afficher les alertes.](../media/ec5ea59b-bf61-459f-8b65-970ab4bb8bcc.png)

Vous pouvez utiliser les filtres suivants pour afficher un sous-ensemble de toutes les alertes sur la page **afficher les alertes** .

- **Originaire.** Utilisez ce filtre pour afficher les alertes affectées à un statut particulier. L’État par défaut est **actif**. Vous ou d’autres administrateurs pouvez modifier la valeur d’État.

- **Renvoi.** Utilisez ce filtre pour afficher les alertes qui correspondent au paramètre d’une ou de plusieurs stratégies d’alerte. Ou vous pouvez afficher toutes les alertes pour toutes les stratégies d’alerte.

- **Plage de temps.** Utilisez ce filtre pour afficher les alertes générées dans une plage de date et d’heure spécifique.

- **Respective.** Utilisez ce filtre pour afficher les alertes auxquelles une gravité spécifique a été affectée.

- **Catégories.** Utilisez ce filtre pour afficher les alertes d’une ou de plusieurs catégories d’alerte.

- **Série.** Utilisez ce filtre pour afficher les alertes d’une ou de plusieurs balises utilisateur. Les balises sont reflétées en fonction des boîtes aux lettres ou des utilisateurs balisés qui apparaissent dans les alertes. Pour en savoir plus, consultez la rubrique [balises utilisateur dans Office 356 DAV](..\security\office-365-security\user-tags.md) .

- **Journal.** Utilisez ce filtre pour afficher les alertes déclenchées par les stratégies d’alerte dans le centre de sécurité et de conformité ou les alertes déclenchées par les stratégies de sécurité d’application Cloud d’Office 365, ou les deux. Pour plus d’informations sur les alertes de sécurité d’application Cloud Office 365, consultez la section [affichage des alertes de sécurité des applications Cloud](#viewing-cloud-app-security-alerts) .

> [!IMPORTANT]
> Le filtrage et le tri par les balises utilisateur sont actuellement en préversion publique.
> Il peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies à son propos.

## <a name="alert-aggregation"></a>Agrégation d’alertes

Lorsque plusieurs événements répondant aux conditions d’une stratégie d’alerte se produisent avec une courte période de temps, ils sont ajoutés à une alerte existante par un processus appelé *agrégation d’alertes*. Lorsqu’un événement déclenche une alerte, l’alerte est générée et affichée sur la page **afficher les alertes** et une notification est envoyée. Si le même événement se produit dans l’intervalle d’agrégation, Microsoft 365 ajoute des détails sur le nouvel événement à l’alerte existante au lieu de déclencher une nouvelle alerte. L’objectif de l’agrégation d’alertes est de réduire la « fatigue » de l’alerte et de vous laisser le focus et d’agir sur des alertes moins nombreuses pour le même événement.

La longueur de l’intervalle d’agrégation dépend de votre abonnement Office 365 ou Microsoft 365.

|Abonnement|Intervalle d’agrégation|
|:---------|:---------:|
|Office 365 ou Microsoft 365 E5/G5|1 minute|
|Defender pour Office 365 plan 2 |1 minute|
|E5 complément de conformité ou complément de découverte et d’audit E5|1 minute|
|Office 365 ou Microsoft 365 E1/F1/G1 ou E3/F3/G3|15 minutes|
|Defender pour Office 365 plan 1 ou Exchange Online Protection|15 minutes|
|||

Lorsque des événements correspondant à la même stratégie d’alerte se produisent dans l’intervalle d’agrégation, les détails de l’événement suivant sont ajoutés à l’alerte d’origine. Pour tous les événements, les informations relatives aux événements agrégés s’affichent dans le champ détails et le nombre de fois qu’un événement a eu lieu avec l’intervalle d’agrégation est affiché dans le champ activité/nombre d’accès. Vous pouvez afficher des informations supplémentaires sur toutes les instances d’événements agrégés en affichant la liste des activités.

La capture d’écran suivante montre une alerte avec quatre événements d’agrégation. La liste activité contient des informations sur les quatre messages électroniques pertinents pour l’alerte.

![Exemple d’agrégation d’alertes](../media/AggregatedAlertExample.png)

Gardez les points suivants à l’esprit concernant l’agrégation d’alertes :

- Alertes déclenchées par **une URL potentiellement malveillante cliquez sur was detected** [default Alert Policy](#default-alert-policies) n’est pas regroupé. Cela est dû au fait que les alertes déclenchées par cette stratégie sont uniques pour chaque utilisateur et chaque message électronique.

- Pour l’instant, la propriété d’alerte **nombre d’accès** n’indique pas le nombre d’événements agrégés pour toutes les stratégies d’alerte. Pour les alertes déclenchées par ces stratégies d’alerte, vous pouvez afficher les événements agrégés en cliquant sur **afficher la liste des messages** ou afficher l' **activité** sur l’alerte. Nous travaillons sur le fait que le nombre d’événements agrégés figurant dans la propriété alerte de **nombre d’accès** soit disponible pour toutes les stratégies d’alerte.

## <a name="rbac-permissions-required-to-view-alerts"></a>Autorisations RBAC requises pour afficher les alertes

Les autorisations de contrôle d’accès basé sur un rôle (RBAC) affectées aux utilisateurs de votre organisation déterminent les alertes qu’un utilisateur peut afficher sur la page **afficher les alertes** . Comment cela est-il accompli ? Les rôles de gestion attribués aux utilisateurs (en fonction de leur appartenance à des groupes de rôles dans le centre de sécurité & conformité) déterminent les catégories d’alertes qu’un utilisateur peut afficher sur la page **afficher les alertes** . Voici quelques exemples :

- Les membres du groupe de rôles de gestion des enregistrements peuvent afficher uniquement les alertes générées par les stratégies d’alerte auxquelles la catégorie de **gouvernance information** est attribuée.

- Les membres du groupe de rôles Administrateur de conformité ne peuvent pas afficher les alertes générées par les stratégies d’alerte auxquelles la catégorie de **gestion des menaces** est attribuée.

- Les membres du groupe de rôles gestionnaire de découverte électronique ne peuvent pas afficher les alertes car aucun des rôles attribués ne donne l’autorisation d’afficher les alertes à partir de n’importe quelle catégorie d’alerte.

Cette conception (basée sur les autorisations RBAC) vous permet de déterminer les alertes pouvant être affichées (et gérées) par les utilisateurs en fonction de rôles de travail spécifiques dans votre organisation.

Le tableau suivant répertorie les rôles requis pour afficher les alertes des six catégories d’alertes différentes. La première colonne dans les tableaux répertorie tous les rôles dans le centre de sécurité & conformité.  Une coche indique qu’un utilisateur auquel ce rôle est attribué peut afficher des alertes à partir de la catégorie d’alerte correspondante indiquée dans la ligne supérieure.

Pour voir la catégorie affectée à une stratégie d’alerte par défaut, consultez le tableau de la section [stratégies d’alerte par défaut](#default-alert-policies) .

|Role|Gouvernance des informations|Protection contre la perte de données|Flux de messagerie|Autorisations|Gestion des menaces|Autres|
|:---------|:---------:|:---------:|:---------:|:---------:|:---------:|:---------:|
|Journaux d’audit|||||||
|Gestion des cas|||||||
|Administrateur de conformité|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)||![Coche](../media/checkmark.png)||![Coche](../media/checkmark.png)|
|Recherche de conformité|||||||
|Gestion des appareils|||||||
|Gestion des destructions|||||||
|Gestion de la conformité DLP||![Coche](../media/checkmark.png)|||||
|Exporter|||||||
|Suspension|||||||
|Gérer les alertes||||||![Coche](../media/checkmark.png)|
|Configuration de l’Organisation||||||![Coche](../media/checkmark.png)|
|Aperçu|||||||
|Gestion des enregistrements|![Coche](../media/checkmark.png)||||||
|Gestion de la rétention|![Coche](../media/checkmark.png)||||||
|Révision|||||||
|Déchiffrement RMS|||||||
|Gestion des rôles||||![Coche](../media/checkmark.png)|||
|Recherche et purge|||||||
|Administrateur de sécurité||![Coche](../media/checkmark.png)||![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|
|Lecteur de sécurité||![Coche](../media/checkmark.png)||![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)|![Coche](../media/checkmark.png)
|Vue de service assurance|||||||
|Administrateur de la vérification de surveillance|||||||
|Journaux d'audit en affichage seul|||||||
|Gestion des appareils View-Only|||||||
|Gestion de la conformité View-Only DLP||![Coche](../media/checkmark.png)|||||
|View-Only gérer les alertes||||||![Coche](../media/checkmark.png)|
|Afficher uniquement les destinataires|||![Coche](../media/checkmark.png)||||
|Gestion des enregistrements de View-Only|![Coche](../media/checkmark.png)||||||
|Gestion de la rétention View-Only|![Coche](../media/checkmark.png)||||||
|||||||

> [!TIP]
> Pour afficher les rôles affectés à chacun des groupes de rôles par défaut, exécutez les commandes suivantes dans sécurité & Centre de conformité PowerShell :
> 
> ```powershell
> $RoleGroups = Get-RoleGroup
> ```
> 
> ```powershell
> $RoleGroups | foreach {Write-Output -InputObject `r`n,$_.Name,"-----------------------"; Get-RoleGroup $_.Identity | Select-Object -ExpandProperty Roles}
> ```
> 
> Vous pouvez également afficher les rôles attribués à un groupe de rôles dans le centre de sécurité & conformité. Accédez à la page **autorisations** et sélectionnez un groupe de rôles. Les rôles attribués sont répertoriés sur la page de menu volant.

## <a name="managing-alerts"></a>Gestion des alertes

Une fois les alertes générées et affichées sur la page **afficher les alertes** dans le centre de sécurité et de conformité, vous pouvez les trier, les examiner et les résoudre. Voici quelques tâches que vous pouvez effectuer pour gérer les alertes.

- **Affecter un État à des alertes.** Vous pouvez attribuer l’un des statuts suivants aux alertes : **actif** (valeur par défaut), **investigation**, **résolu** ou **fermé**. Ensuite, vous pouvez filtrer ce paramètre pour afficher les alertes ayant le même paramètre d’État. Ce paramètre d’état permet de suivre le processus de gestion des alertes.

- **Afficher les détails de l’alerte.** Vous pouvez sélectionner une alerte pour afficher une page de menu volant avec des détails sur l’alerte. Les informations détaillées dépendent de la stratégie d’alerte correspondante, mais elle inclut généralement les éléments suivants : nom de l’opération réelle qui a déclenché l’alerte (par exemple, une cmdlet), une description de l’activité qui a déclenché l’alerte, l’utilisateur (ou la liste des utilisateurs) qui a déclenché l’alerte, ainsi que le nom (et le lien) de la stratégie d’alerte correspondante.

  - Nom de l’opération réelle qui a déclenché l’alerte, telle qu’une applet de commande ou une opération de journal d’audit.

  - Description de l’activité qui A déclenché l’alerte.

  - Utilisateur qui a déclenché l’alerte. Cette option est incluse uniquement pour les stratégies d’alerte configurées pour suivre un seul utilisateur ou une seule activité.

  - Nombre de fois que l’activité suivie par l’alerte a été effectuée. Ce nombre peut ne pas correspondre au nombre réel d’alertes associées indiquées sur la page afficher les alertes, car il est possible que d’autres alertes aient été déclenchées.

  - Lien vers une liste d’activités qui inclut un élément pour chaque activité effectuée qui a déclenché l’alerte. Chaque entrée de cette liste identifie le moment où l’activité s’est produite, le nom de l’opération réelle (par exemple, « FileDeleted ») et l’utilisateur qui a effectué l’activité, l’objet (tel qu’un fichier, un cas eDiscovery ou une boîte aux lettres) sur lequel l’activité a été exécutée, et l’adresse IP de l’ordinateur de l’utilisateur. Pour les alertes liées aux programmes malveillants, cette fonction renvoie à une liste de messages.

  - Nom (et lien) de la stratégie d’alerte correspondante.

- **Supprimer les notifications par courrier électronique.** Vous pouvez désactiver (ou supprimer) les notifications par courrier électronique à partir de la page de menu volant pour une alerte. Lorsque vous supprimez des notifications par courrier électronique, Microsoft n’envoie pas de notifications lorsque des activités ou des événements répondent aux conditions de la stratégie d’alerte. Mais des alertes seront déclenchées lorsque les activités effectuées par les utilisateurs correspondront aux conditions de la stratégie d’alerte. Vous pouvez également désactiver les notifications par courrier électronique en modifiant la stratégie d’alerte.

- **Résoudre les alertes.** Vous pouvez marquer une alerte comme étant résolue sur la page de menu volant pour une alerte (qui définit l’état de l’alerte sur **résolu**). Sauf si vous modifiez le filtre, les alertes résolues ne s’affichent pas sur la page **afficher les alertes** .

## <a name="viewing-cloud-app-security-alerts"></a>Affichage des alertes de sécurité des applications Cloud

Les alertes déclenchées par les stratégies de sécurité des applications Cloud d’Office 365 s’affichent désormais sur la page **afficher les alertes** dans le centre de sécurité et de conformité. Cela inclut les alertes déclenchées par les stratégies d’activité et les alertes déclenchées par des stratégies de détection des anomalies dans Office 365 Cloud App Security. Cela signifie que vous pouvez afficher toutes les alertes dans le centre de sécurité et de conformité. Office 365 Cloud App Security est uniquement disponible pour les organisations disposant d’un abonnement Office 365 Enterprise E5 ou Office 365 pour le gouvernement G5 G5. Pour plus d’informations, consultez la rubrique [vue d’ensemble de la sécurité des applications Cloud](https://docs.microsoft.com/cloud-app-security/what-is-cloud-app-security).

Les organisations qui disposent d’une sécurité d’application Cloud Microsoft dans le cadre d’un abonnement Enterprise Mobility + Security E5 ou en tant que service autonome peuvent également consulter les alertes de sécurité des applications Cloud liées aux applications et services Office 365 dans le centre de conformité & Compliance Center.

Pour afficher uniquement les alertes de sécurité des applications Cloud dans le centre de sécurité et de conformité, utilisez le filtre **source** et sélectionnez **sécurité des applications Cloud**.

![Utiliser le filtre source pour afficher uniquement les alertes de sécurité des applications Cloud](../media/FilterCASAlerts.png)

À l’instar d’une alerte déclenchée par une stratégie d’alerte dans le centre de sécurité et de conformité, vous pouvez sélectionner une alerte de sécurité d’application Cloud pour afficher une page de menu volant avec des détails sur l’alerte. L’alerte comprend un lien permettant d’afficher les détails et de gérer l’alerte dans le portail de sécurité de l’application Cloud, ainsi qu’un lien vers la stratégie de sécurité de l’application Cloud correspondante qui a déclenché l’alerte. Consultez la rubrique [Monitor alerts in Cloud App Security](https://docs.microsoft.com/cloud-app-security/monitor-alerts).

![Les détails de l’alerte contiennent des liens vers le portail de sécurité des applications Cloud](../media/CASAlertDetail.png)

> [!IMPORTANT]
> La modification de l’état d’une alerte de sécurité d’application Cloud dans le centre de sécurité et de conformité ne met pas à jour l’état de résolution de la même alerte dans le portail de sécurité des applications Cloud. Par exemple, si vous marquez le statut de l’alerte comme **résolu** dans le centre de sécurité et de conformité, l’état de l’alerte dans le portail de sécurité des applications Cloud est inchangé. Pour résoudre ou faire disparaître une alerte de sécurité d’application Cloud, gérez l’alerte dans le portail de sécurité des applications Cloud.
