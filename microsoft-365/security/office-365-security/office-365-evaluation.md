---
title: Évaluer Microsoft Defender pour Office 365
description: Defender pour Office 365 en mode d’évaluation crée des stratégies de messagerie Defender pour Office 365 qui enregistrent les verdicts, tels que les programmes malveillants, mais n’agissent pas sur les messages.
keywords: évaluer Office 365, Microsoft Defender pour Office 365, évaluation d’Office 365, essayer Office 365, Microsoft Defender, ATP
f1.keywords:
- NOCSH
ms.author: ellevin
author: levinec
manager: dansimp
audience: ITPro
ms.topic: article
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 1d16c0afc675ba759e392c9fe9a44c42b89dbad0
ms.sourcegitcommit: 786f90a163d34c02b8451d09aa1efb1e1d5f543c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/18/2021
ms.locfileid: "50287652"
---
# <a name="evaluate-microsoft-defender-for-office-365"></a>Évaluer Microsoft Defender pour Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

> [!IMPORTANT]
> L’évaluation de Microsoft Defender pour Office 365 est en prévisualisation publique. Cette version préliminaire est fournie sans contrat de niveau de service. Certaines fonctionnalités peuvent ne pas être pris en charge ou avoir des fonctionnalités contraintes.

La conduite d’une évaluation complète du produit de sécurité peut vous aider à prendre des décisions éclairées sur les mises à niveau et les achats. Il permet d’essayer les fonctionnalités du produit de sécurité pour évaluer la façon dont il peut aider votre équipe en charge des opérations de sécurité dans ses tâches quotidiennes.

L’expérience d’évaluation de Microsoft Defender pour [Office 365](office-365-atp.md) est conçue pour éliminer la complexité de la configuration de l’appareil et de l’environnement afin que vous pouvez vous concentrer sur l’évaluation des fonctionnalités de la solution de sécurité. Elle s’applique uniquement à la protection de la messagerie et non à SharePoint, aux clients Office ou à Teams.

Si vous n’avez pas encore de licence qui prend en charge Microsoft Defender pour Office 365, vous pouvez démarrer une évaluation gratuite de [30](https://admin.microsoft.com/AdminPortal/Home#/catalog/offer-details/microsoft-defender-for-office-365-plan-2-/223860DC-15D6-42D9-A861-AE05473069FA) jours et tester les fonctionnalités dans le Centre de sécurité & conformité Office 365 ( https://protection.office.com/homepage) . Vous pourrez profiter de la mise en place rapide et la désactiver facilement si nécessaire.

## <a name="how-the-evaluation-works"></a>Fonctionnement de l’évaluation

Defender pour Office 365 en mode d’évaluation crée des stratégies de messagerie Defender pour Office 365 qui enregistrent les verdicts, tels que les programmes malveillants, mais n’agissent pas sur les messages. Vous n’êtes pas obligé de modifier la configuration de votre enregistrement MX.

Avec le mode d’évaluation, les stratégies de pièces [jointes sécurisées,](atp-safe-attachments.md)de liens sécurisés et d’emprunt d’identité [anti-hameçonnage](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) sont définies en votre nom. [](atp-safe-links.md) Toutes les stratégies Defender pour Office 365 sont créées en mode non-application en arrière-plan et ne sont pas visibles pour vous.

Dans le cadre de l’installation, le mode d’évaluation configure également [le filtrage amélioré pour les connecteurs.](https://docs.microsoft.com/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors) Il améliore la précision du filtrage en conservant l’adresse IP et les informations de l’expéditeur, qui sont sinon perdues lorsque le courrier passe par une passerelle de sécurité de messagerie (ESG) devant Defender pour Office 365. Le filtrage amélioré améliore également la précision du filtrage pour vos stratégies anti-courrier indésirable et anti-hameçonnage Exchange Online Protection (EOP).

Pour minimiser l’impact potentiel sur la production sur certains scénarios non pris en cas de problème, vous pouvez contourner tout filtrage EOP en créant une règle de transport pour définir le niveau de confiance du courrier indésirable (SCL) sur -1. Pour plus d’informations, voir Utiliser le EAC pour créer une règle de flux de messagerie qui définit le [SCL d’un message.](use-mail-flow-rules-to-set-the-spam-confidence-level-scl-in-messages.md#use-the-eac-to-create-a-mail-flow-rule-that-sets-the-scl-of-a-message)  

Lorsque le mode d’évaluation est installé, vous avez un rapport mis à jour quotidiennement avec jusqu’à 90 jours de données quantifiant les messages qui auraient été bloqués si les stratégies étaient implémentées (par exemple, supprimer, envoyer au courrier indésirable, mettre en quarantaine). Les rapports sont générés pour toutes les détections Defender pour Office 365 et EOP. Elles sont agrégées par technologie de détection (par exemple, l’emprunt d’identité) et peuvent être filtrées par plage de temps. En outre, les rapports de messages peuvent être créés à la demande pour créer des tableaux croisés dynamiques personnalisés ou pour explorer les messages en profondeur à l’aide de l’Explorateur de menaces.

Grâce à l’expérience de mise en place simplifiée, vous pouvez vous concentrer sur :

- Exécution de l’évaluation
- Obtention d’un rapport détaillé
- Analyse du rapport pour l’action
- Présentation du résultat de l’évaluation

## <a name="before-you-begin"></a>Avant de commencer

### <a name="licensing"></a>Licences

Pour accéder à l’évaluation, vous devez respecter les exigences de licence. L’une des licences suivantes fonctionne :

- Microsoft Defender pour Office 365 Plan 1
- Microsoft Defender pour Office 365 Plan 2
- Microsoft 365 E5, Sécurité Microsoft 365 E5
- Office 365 E5

Si vous n’avez pas l’une de ces licences, vous devez obtenir une licence d’essai.

#### <a name="trial"></a>Version d’évaluation

Pour obtenir une licence d’essai pour Microsoft Defender pour  Office 365, vous devez avoir le rôle d’administrateur de facturation ou d’administrateur **général.** Demander l’autorisation à une personne qui a le rôle d’administrateur global. [En savoir plus sur les abonnements et les licences](https://docs.microsoft.com/microsoft-365/commerce/licenses/subscriptions-and-licenses)

Une fois que vous avez le rôle approprié, le chemin d’accès recommandé consiste à obtenir une licence d’essai pour Microsoft Defender pour Office 365 (Plan 2) dans le Centre d’administration Microsoft 365 en allant à Facturation > Acheter des services. La version d’essai inclut un essai gratuit de 30 jours pour 25 licences. [Obtenez une version d’essai de Microsoft Defender pour Office 365 (Plan 2).](https://admin.microsoft.com/AdminPortal/Home#/catalog/offer-details/microsoft-defender-for-office-365-plan-2-/223860DC-15D6-42D9-A861-AE05473069FA)

Vous aurez une fenêtre de 30 jours avec l’évaluation pour surveiller et signaler les menaces avancées. Vous avez également la possibilité d’acheter un abonnement payant si vous souhaitez les fonctionnalités complètes de Defender pour Office 365.

### <a name="roles"></a>Rôles

Les rôles Exchange Online sont requis pour configurer Defender pour Office 365 en mode d’évaluation.

- [En savoir plus sur les autorisations dans Exchange Online](https://docs.microsoft.com/exchange/permissions-exo/permissions-exo)
- [En savoir plus sur l’attribution de rôles d’administrateur](../../admin/add-users/assign-admin-roles.md)

Les rôles suivants sont nécessaires :

|Tâche|Role|
|---|---|
|Obtenir une version d’essai gratuite ou acheter Microsoft Defender pour Office 365 (Plan 2)|Rôle d’administrateur de facturation OU rôle d’administrateur global|
|Créer une stratégie d’évaluation|Rôle Domaines distants et acceptés ; Rôle d’administrateur de sécurité|
|Modifier la stratégie d’évaluation|Rôle domaines distants et acceptés ; Rôle d’administrateur de sécurité|
|Supprimer la stratégie d’évaluation|Rôle Domaines distants et acceptés ; Rôle d’administrateur de sécurité |
|Afficher le rapport d’évaluation|Rôle d’administrateur de sécurité OU rôle lecteur sécurité|
|


### <a name="enhanced-filtering"></a>Filtrage amélioré

Vos stratégies Exchange Online Protection, telles que la protection en bloc et le courrier indésirable, resteront identiques. La remise des messages reste également la même. Toutefois, l’évaluation permet d’améliorer le filtrage des connecteurs, ce qui aura un impact sur votre flux de messagerie et les stratégies Exchange Online Protection, sauf contournement.

Le filtrage amélioré pour les connecteurs permettra aux locataires d’utiliser la protection contre l’usurpation d’usurpation d’accès. La protection contre l’usurpation d’adresse n’est pas prise en charge si vous utilisez une passerelle de sécurité de messagerie (ESG) sans avoir désactivé le filtrage amélioré pour les connecteurs.

### <a name="urls"></a>URL

Les URL sont détonées pendant le flux de messagerie. Si vous ne souhaitez pas que des URL spécifiques détonent, gérez votre liste d’URL autorisées de manière appropriée. Pour [plus d’informations, voir](tenant-allow-block-list.md) Gérer la liste d’attente des locataires.

Les liens d’URL dans les corps des messages électroniques ne seront pas encapsulés, afin de réduire l’impact sur les clients.

### <a name="email-routing"></a>Routage du courrier électronique

Préparez les détails correspondants dont vous aurez besoin pour configurer la façon dont votre courrier électronique est actuellement acheminé, y compris le nom du connecteur entrant qui a acheminé vos messages. Si vous utilisez simplement Exchange Online Protection, vous n’avez pas de connecteur.  [En savoir plus sur le flux de messagerie et le routage du courrier électronique](https://docs.microsoft.com/office365/servicedescriptions/exchange-online-service-description/mail-flow)

Les scénarios de routage de courrier pris en charge sont les suivants :

- Partenaire tiers et/ou fournisseur de services local : le connecteur entrant que vous souhaitez évaluer utilise un fournisseur tiers **et/ou** vous utilisez une solution pour la sécurité du courrier électronique en local.
- **Microsoft Exchange Online protection** uniquement : le client que vous souhaitez évaluer utilise Office 365 pour la sécurité du courrier électronique et l’enregistrement MX pointe vers Microsoft.

### <a name="email-security-gateway"></a>Passerelle de sécurité du courrier électronique

Si vous utilisez une passerelle de sécurité de messagerie (ESG) tierce, vous devez connaître le nom du fournisseur. Si vous utilisez un fournisseur ESG local ou non pris en charge, vous devez connaître les adresses IP publiques des appareils.

Les partenaires tiers pris en charge sont les suivants :

- Barracuda
- IronPort
- Mimecast
- Proofpoint
- Sophos
- Symantec
- Trend Micro

### <a name="scoping"></a>Étendue

Vous serez en mesure d’élargir l’étendue de l’évaluation à un connecteur entrant. Si aucun connecteur n’est configuré, l’étendue d’évaluation permettra aux administrateurs de collecter des données auprès d’un utilisateur de votre client pour évaluer Defender pour Office 365.

## <a name="get-started-with-the-evaluation"></a>Mise en place de l’évaluation

Recherchez la carte de mise en service d’évaluation de Microsoft Defender pour Office 365 dans le Centre de sécurité & et conformité Office 365 (à partir de trois https://protection.office.com/homepage) points d’accès :

- Tableau de bord de gestion > menaces
- Stratégie de gestion > menaces
- Tableau de bord > rapports

## <a name="setting-up-the-evaluation"></a>Configuration de l’évaluation

Une fois que vous avez commencé le flux de mise en place pour votre évaluation, deux options de routage s’offrent à vous. En fonction des besoins de configuration et d’évaluation du routage du courrier de votre organisation, vous pouvez choisir si vous utilisez un fournisseur de services tiers et/ou local ou uniquement Microsoft Exchange Online.

- Si vous utilisez un partenaire tiers et/ou un fournisseur de services local, vous devez sélectionner le nom du fournisseur dans le menu déroulant. Fournissez les autres détails liés au connecteur.

- Sélectionnez Microsoft Exchange Online si l’enregistrement MX pointe vers Microsoft et si vous avez une boîte aux lettres Exchange Online.

Examinez vos paramètres et modifiez-les si nécessaire. Ensuite, **sélectionnez Créer une évaluation.** Vous devez obtenir un message de confirmation pour indiquer que votre mise en place est terminée.

Votre rapport d’évaluation de Microsoft Defender pour Office 365 est généré une fois par jour. Le traitement des données peut prendre jusqu’à 24 heures.

### <a name="exchange-rules-optional"></a>Règles Exchange (facultatives)

Si vous avez une passerelle existante, l’activation du mode d’évaluation active le filtrage amélioré pour les connecteurs. Cela améliore la précision du filtrage en modifiant l’adresse IP de l’expéditeur entrant. Cela peut modifier les verdicts de filtre et si vous ne contournez pas Exchange Online Protection, cela peut modifier la livrabilité de certains messages. Dans ce cas, vous pouvez ignorer temporairement le filtrage pour analyser l’impact. Pour contourner ce nombre, accédez au Centre d’administration Exchange et créez une stratégie SCL -1 (si vous n’en avez pas déjà). Pour plus d’informations sur les composants de règle et leur fonctionnement, voir Règles de flux de messagerie (règles de transport) dans Exchange Online.

## <a name="evaluate-capabilities"></a>Évaluer les fonctionnalités

Une fois le rapport d’évaluation généré, consultez le nombre de liens vers les menaces avancées, de pièces jointes de menaces avancées et d’emprunts d’identité potentiels identifiés dans les e-mails et les espaces de travail de collaboration de votre organisation.

Une fois la version d’essai expirée, vous pouvez continuer à accéder au rapport pendant 90 jours. Toutefois, il ne collecte plus d’informations. Si vous souhaitez continuer à utiliser Microsoft Defender pour Office 365 après l’expiration de votre version d’essai, assurez-vous d’acheter un abonnement payant pour Microsoft Defender pour [Office 365 (Plan 2).](https://admin.microsoft.com/AdminPortal/Home#/catalog/offer-details/microsoft-defender-for-office-365-plan-2-/223860DC-15D6-42D9-A861-AE05473069FA)

Vous pouvez utiliser **paramètres pour mettre** à jour votre routage ou désactiver votre évaluation à tout moment. Toutefois, vous devez à nouveau passer par le même processus de mise en place si vous décidez de poursuivre votre évaluation après l’avoir désactivée.

## <a name="provide-feedback"></a>Envoyer des commentaires

Vos commentaires nous aident à mieux protéger votre environnement contre les attaques avancées. Partagez votre expérience et vos impressions sur les fonctionnalités du produit et les résultats de l’évaluation.

Sélectionnez **Nous faire part** de vos commentaires pour nous faire part de vos commentaires.
