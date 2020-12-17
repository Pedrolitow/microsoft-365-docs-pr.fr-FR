---
title: Évaluation de Microsoft Defender pour Office 365
description: Defender for Office 365 en mode d’évaluation crée des stratégies de messagerie Defender pour Office 365 qui journalisent les verdicts, telles que les programmes malveillants, mais n’agissent pas sur les messages.
keywords: évaluer Office 365, Microsoft Defender pour Office 365, Office 365 évaluation, essayer Office 365, Microsoft Defender, ATP
f1.keywords:
- NOCSH
ms.author: ellevin
author: levinec
manager: dansimp
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: abb33b85717e63cb78a2b1edfd86584fd165a71f
ms.sourcegitcommit: f231eece2927f0d01072fd092db1eab15525bbc2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/17/2020
ms.locfileid: "49701014"
---
# <a name="evaluate-microsoft-defender-for-office-365"></a>Évaluation de Microsoft Defender pour Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

> [!IMPORTANT]
> Évaluer Microsoft Defender pour Office 365 sera bientôt en version préliminaire publique. Cette version d’évaluation est fournie sans contrat de niveau de service. Certaines fonctionnalités peuvent ne pas être prises en charge ou avoir des capacités limitées.

La réalisation d’une évaluation complète des produits de sécurité peut vous aider à prendre des décisions éclairées sur les mises à niveau et les achats. Elle permet de tester les fonctionnalités du produit de sécurité afin d’évaluer la façon dont elle peut aider votre équipe en matière de sécurité dans ses tâches quotidiennes.

L’expérience d’évaluation [de Microsoft Defender pour Office 365](office-365-atp.md) est conçue pour éliminer les complexités de la configuration des appareils et des environnements afin que vous puissiez vous concentrer sur l’évaluation des fonctionnalités de la solution de sécurité. Il s’applique uniquement à la protection de messagerie et non à SharePoint, aux clients office ou à Teams.

Si vous ne disposez pas déjà d’une licence qui prend en charge Microsoft Defender pour Office 365, vous pouvez démarrer une [évaluation gratuite de 30 jours](https://admin.microsoft.com/AdminPortal/Home#/catalog/offer-details/microsoft-defender-for-office-365-plan-2-/223860DC-15D6-42D9-A861-AE05473069FA) et tester les fonctionnalités dans le centre de sécurité & conformité d’Office 365 ( https://protection.office.com/homepage) . Vous bénéficierez de la configuration rapide et vous pourrez la désactiver si nécessaire.

## <a name="how-the-evaluation-works"></a>Fonctionnement de l’évaluation

Defender for Office 365 en mode d’évaluation crée des stratégies de messagerie Defender pour Office 365 qui journalisent les verdicts, telles que les programmes malveillants, mais n’agissent pas sur les messages. Vous n’êtes pas obligé de modifier la configuration de votre enregistrement MX.

Avec le mode d’évaluation, [les pièces jointes fiables, les](atp-safe-attachments.md) [liens fiables](atp-safe-links.md)et les [stratégies d’usurpation d’identité anti-hameçonnage](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) sont configurés en votre nom. Toutes les stratégies Defender pour Office 365 sont créées en mode non-application en arrière-plan et ne sont pas visibles pour vous.

Dans le cadre de la configuration, le mode d’évaluation configure également le [filtrage amélioré pour les connecteurs](https://docs.microsoft.com/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors). Elle améliore la précision de filtrage en conservant les informations d’adresse IP et d’expéditeur, qui sont perdues lorsque le courrier passe par une passerelle de sécurité de messagerie (ESG) devant de l’Office 365. Le filtrage amélioré améliore également la précision de filtrage pour vos stratégies de protection contre le courrier indésirable et anti-hameçonnage Exchange Online (EOP).

Pour limiter l’impact potentiel de la production sur certains scénarios non pris en charge, vous pouvez contourner tout le filtrage EOP en créant une règle de transport pour définir le seuil de probabilité de courrier indésirable sur-1. Pour plus d’informations, consultez [la rubrique utiliser le centre d’administration Exchange pour créer une règle de flux de messagerie qui définit la valeur SCL d’un message](use-mail-flow-rules-to-set-the-spam-confidence-level-scl-in-messages.md#use-the-eac-to-create-a-mail-flow-rule-that-sets-the-scl-of-a-message)   .

Lors de la configuration du mode d’évaluation, un rapport est mis à jour quotidiennement avec un maximum de 90 jours de quantification des messages qui auraient été bloqués si les stratégies étaient implémentées (par exemple, supprimer, envoyer à courrier indésirable, mise en quarantaine). Les rapports sont générés pour tous les virus Defender pour Office 365 et EOP. Ils sont regroupés par technologie de détection (par exemple, emprunt d’identité) et peuvent être filtrés par intervalle de temps. En outre, des rapports de message peuvent être créés à la demande pour créer des tableaux croisés dynamiques personnalisés ou des messages de plongée en profondeur à l’aide de l’Explorateur de menaces.

Avec l’expérience de configuration simplifiée, vous pouvez vous concentrer sur les éléments suivants :

- Exécution de l’évaluation
- Obtention d’un rapport détaillé
- Analyse du rapport pour l’action
- Présentation du résultat de l’évaluation

## <a name="before-you-begin"></a>Avant de commencer

### <a name="licensing"></a>Licence

Pour accéder à l’évaluation, vous devez répondre aux exigences en matière de licences. Les licences suivantes fonctionneront :

- Microsoft Defender pour Office 365 Plan 1
- Microsoft Defender pour Office 365 Plan 2
- Microsoft 365 E5, Microsoft 365 E5 sécurité
- Office 365 E5

Si vous ne disposez pas de l’une de ces licences, vous devez obtenir une licence d’évaluation.

#### <a name="trial"></a>Version d’évaluation

Pour obtenir une licence d’évaluation pour Microsoft Defender pour Office 365, vous devez disposer du rôle d' **administrateur de facturation** ou d' **administrateur général**. Demander l’autorisation d’une personne qui a le rôle d’administrateur global. [En savoir plus sur les abonnements et les licences](https://docs.microsoft.com/microsoft-365/commerce/licenses/subscriptions-and-licenses)

Une fois que vous avez le rôle approprié, le chemin d’accès recommandé consiste à obtenir une licence d’évaluation pour Microsoft Defender pour Office 365 (plan 2) dans le centre d’administration Microsoft 365 en accédant à facturation > achat services. La version d’évaluation inclut un essai gratuit de 30 jours pour 25 licences. [Obtenez une version d’évaluation de Microsoft Defender pour Office 365 (plan 2)](https://admin.microsoft.com/AdminPortal/Home#/catalog/offer-details/microsoft-defender-for-office-365-plan-2-/223860DC-15D6-42D9-A861-AE05473069FA).

Vous disposerez d’une fenêtre de 30 jours avec l’évaluation pour surveiller et créer des rapports sur les menaces avancées. Vous avez également la possibilité d’acheter un abonnement payant si vous souhaitez bénéficier des fonctionnalités complètes de Defender pour Office 365.

### <a name="roles"></a>Rôles

Les rôles Exchange Online sont requis pour configurer Defender pour Office 365 en mode d’évaluation.

- [En savoir plus sur les autorisations dans Exchange Online](https://docs.microsoft.com/exchange/permissions-exo/permissions-exo)
- [En savoir plus sur l’attribution de rôles d’administrateur](https://docs.microsoft.com/microsoft-365/admin/add-users/assign-admin-roles)

Les rôles suivants sont nécessaires :

|Tâche|Role|
|---|---|
|Obtenir une version d’évaluation gratuite ou acheter Microsoft Defender pour Office 365 (plan 2)|Rôle d’administrateur de facturation ou de rôle d’administrateur global|
|Créer une stratégie d’évaluation|Rôle des domaines acceptés et distants ; Rôle d’administrateur de sécurité|
|Modifier la stratégie d’évaluation|Rôle des domaines acceptés et distants ; Rôle d’administrateur de sécurité|
|Supprimer la stratégie d’évaluation|Rôle des domaines acceptés et distants ; Rôle d’administrateur de sécurité |
|Afficher le rapport d’évaluation|Rôle d’administrateur de sécurité ou rôle de lecteur de sécurité|
|


### <a name="enhanced-filtering"></a>Filtrage amélioré

Vos stratégies Exchange Online Protection, telles que la protection en bloc et le courrier indésirable, resteront les mêmes. La remise des messages restera également identique. Toutefois, l’évaluation active le filtrage amélioré pour les connecteurs, ce qui aura un impact sur vos stratégies de flux de messagerie et de protection Exchange Online sauf si elles sont ignorées.

Le filtrage amélioré pour les connecteurs permettra aux clients d’utiliser la protection contre l’usurpation d’identité. La détection d’usurpation d’identité n’est pas prise en charge si vous utilisez une passerelle de sécurité de messagerie (ESG) sans avoir activé le filtrage amélioré pour les connecteurs.

### <a name="urls"></a>URL

Les URL seront détonations pendant le flux de messagerie. Si vous ne voulez pas que des URL spécifiques soient détonations, gérez correctement votre liste d’URL autorisées. Pour plus d’informations [, consultez la rubrique Manage URLs in the client allow/Block List](tenant-allow-block-list.md) .

Les liens URL dans les corps des messages électroniques ne sont pas renvoyés, afin de réduire l’impact sur les clients.

### <a name="email-routing"></a>Routage du courrier électronique

Préparez les détails correspondants dont vous aurez besoin pour configurer la façon dont votre courrier électronique est actuellement routé, y compris le nom du connecteur entrant qui route votre courrier électronique. Si vous utilisez Exchange Online Protection, vous n’aurez pas de connecteur.  [En savoir plus sur le flux de messagerie et le routage](https://docs.microsoft.com/office365/servicedescriptions/exchange-online-service-description/mail-flow) du courrier électronique

Les scénarios de routage de messagerie pris en charge sont les suivants :

- **Partenaire de service tiers et/ou fournisseur local**: le connecteur entrant que vous souhaitez évaluer utilise un fournisseur tiers et/ou vous utilisez une solution pour la sécurité de la messagerie en local.
- **Microsoft Exchange Online Protection uniquement**: le client que vous souhaitez évaluer utilise Office 365 pour la sécurité de messagerie et l’enregistrement MX (mail Exchange) pointe vers Microsoft.

### <a name="email-security-gateway"></a>Passerelle de sécurité de messagerie

Si vous utilisez une passerelle de sécurité de messagerie tierce (ESG), vous devez indiquer le nom du fournisseur. Si vous utilisez un fournisseur ESG local ou non pris en charge, vous devez avoir connaissance des adresses IP publiques pour les appareils.

Les partenaires tiers pris en charge sont les suivants :

- Barracuda
- IronPort
- Mimecast
- Proofpoint
- Sophos
- Donne
- Trend Micro

### <a name="scoping"></a>Étendue

Vous serez en mesure d’étendre l’évaluation à un connecteur entrant. Si aucun connecteur n’est configuré, la portée de l’évaluation permettra aux administrateurs de collecter des données auprès de n’importe quel utilisateur de votre client afin d’évaluer Defender pour Office 365.

## <a name="get-started-with-the-evaluation"></a>Prise en main de l’évaluation

Recherchez la carte de configuration de l’évaluation de Microsoft Defender pour Office 365 dans le centre de sécurité & conformité Office 365 ( https://protection.office.com/homepage) à partir de trois points d’accès) :

- Gestion des menaces > tableau de bord
- Stratégie de > de gestion des menaces
- Tableau de bord > des rapports

## <a name="setting-up-the-evaluation"></a>Configuration de l’évaluation

Une fois que vous avez démarré le flux de configuration de votre évaluation, vous disposez de deux options de routage. En fonction de la configuration du routage du courrier et des besoins d’évaluation de votre organisation, vous pouvez choisir d’utiliser un fournisseur de services tiers et/ou locaux ou uniquement Microsoft Exchange Online.

- Si vous utilisez un partenaire de service tiers et/ou un fournisseur de services local, vous devez sélectionner le nom du fournisseur dans le menu déroulant. Fournissez les autres détails relatifs au connecteur.

- Sélectionnez Microsoft Exchange Online si l’enregistrement MX pointe vers Microsoft et que vous disposez d’une boîte aux lettres Exchange Online.

Vérifiez vos paramètres et modifiez-les si nécessaire. Ensuite, sélectionnez **créer une évaluation**. Vous devriez obtenir un message de confirmation pour indiquer que votre configuration est terminée.

Votre rapport d’évaluation de Microsoft Defender pour Office 365 est généré une fois par jour. Le remplissage des données peut prendre jusqu’à 24 heures.

### <a name="exchange-rules-optional"></a>Règles Exchange (facultatif)

Si vous disposez d’une passerelle existante, vous pouvez contourner le filtrage, car elle active le filtrage amélioré pour les connecteurs et modifie l’adresse IP de l’expéditeur entrant. Pour ignorer, accédez au centre d’administration Exchange et créez une stratégie de SCL-1 (si vous n’en avez pas encore). Pour plus d’informations sur les composants de la règle et leur fonctionnement, consultez la rubrique mail Flow Rules (règles de transport) dans Exchange Online.

## <a name="evaluate-capabilities"></a>Évaluer les fonctionnalités

Une fois le rapport d’évaluation généré, consultez le nombre de liens de menace avancés, de pièces jointes aux menaces avancées et des emprunts d’identité potentiels identifiés dans les espaces de travail des courriers électroniques et de collaboration de votre organisation.

Une fois que la version d’évaluation a expiré, vous pouvez continuer à accéder au rapport pendant 90 jours. Toutefois, aucune information supplémentaire n’est collectée. Si vous souhaitez continuer à utiliser Microsoft Defender pour Office 365 après l’expiration de votre version d’évaluation, vérifiez que vous [achetez un abonnement payant pour Microsoft Defender pour office 365 (plan 2)](https://admin.microsoft.com/AdminPortal/Home#/catalog/offer-details/microsoft-defender-for-office-365-plan-2-/223860DC-15D6-42D9-A861-AE05473069FA).

Vous pouvez accéder aux **paramètres** pour mettre à jour votre routage ou désactiver votre évaluation à tout moment. Toutefois, vous devez repasser par le même processus de configuration si vous décidez de continuer votre évaluation après l’avoir désactivée.

## <a name="provide-feedback"></a>Envoyer des commentaires

Vos commentaires nous aident à mieux protéger votre environnement contre les attaques avancées. Partagez votre expérience et vos impressions sur les capacités du produit et les résultats de l’évaluation.

Sélectionnez **Envoyer des commentaires** pour nous dire ce que vous pensez.
