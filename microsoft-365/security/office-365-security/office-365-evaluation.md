---
title: Evaluer Microsoft Defender pour Office 365
description: Defender pour Office 365 en mode d’évaluation crée Defender pour Office 365 stratégies de messagerie qui consignent les verdicts, tels que les programmes malveillants, mais n’agissent pas sur les messages.
keywords: évaluer Office 365, Microsoft Defender pour Office 365, l’évaluation d’Office 365, essayer Office 365, Microsoft Defender Microsoft Defender pour point de terminaison
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: 04/21/2021
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 0f5d82e9baaca7209f8a91a7f1984aa38e3102e6
ms.sourcegitcommit: 74518b920b4166adccc10ea1581a62c44bb14edb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2022
ms.locfileid: "66991673"
---
# <a name="evaluate-microsoft-defender-for-office-365"></a>Evaluer Microsoft Defender pour Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

> [!IMPORTANT]
> Microsoft Defender pour Office 365 évaluation est en préversion publique. Cette préversion est fournie sans contrat de niveau de service. Certaines fonctionnalités peuvent ne pas être prises en charge ou avoir des fonctionnalités limitées.

La réalisation d’une évaluation approfondie des produits de sécurité peut vous aider à prendre des décisions éclairées sur les mises à niveau et les achats. Il permet d’essayer les fonctionnalités du produit de sécurité pour évaluer comment il peut aider votre équipe des opérations de sécurité dans leurs tâches quotidiennes.

[L’expérience d’évaluation Microsoft Defender pour Office 365](defender-for-office-365.md) est conçue pour éliminer les complexités de la configuration de l’appareil et de l’environnement afin que vous puissiez vous concentrer sur l’évaluation des fonctionnalités de Microsoft Defender pour Office 365. Avec le mode d’évaluation, tous les messages envoyés à Exchange Online boîtes aux lettres peuvent être évalués sans pointer les enregistrements MX vers Microsoft. La fonctionnalité s’applique uniquement à la protection par e-mail et non aux clients Office comme Word, SharePoint ou Teams.

Si vous n’avez pas encore de licence qui prend en charge Microsoft Defender pour Office 365, vous pouvez démarrer une [évaluation gratuite de 30 jours](https://admin.microsoft.com/AdminPortal/Home#/catalog/offer-details/microsoft-defender-for-office-365-plan-2-/223860DC-15D6-42D9-A861-AE05473069FA) et tester les fonctionnalités dans le portail Microsoft 365 Defender à l’adresse <https://security.microsoft.com>. Vous apprécierez la configuration rapide et vous pourrez facilement la désactiver si nécessaire.

> [!NOTE]
> Si vous êtes dans le portail Microsoft 365 Defender, <https://security.microsoft.com>vous pouvez démarrer une évaluation Defender pour Office 365 ici : Email & mode **d’évaluation** des stratégies de **collaboration** \> **& des** stratégies de **menace** \> de règles \> dans la section **Autres**. Ou, pour accéder directement à la page **du mode Évaluation** , utilisez <https://security.microsoft.com/atpEvaluation>.

## <a name="how-the-evaluation-works"></a>Fonctionnement de l’évaluation

Defender pour Office 365 en mode d’évaluation crée Defender pour Office 365 stratégies de messagerie qui consignent les verdicts, tels que les programmes malveillants, mais n’agissent pas sur les messages. Vous n’êtes pas obligé de modifier la configuration de votre enregistrement MX.

Avec le mode d’évaluation, [les pièces jointes sécurisées, les liens sécurisés](safe-attachments.md) et l’intelligence de [boîte aux lettres dans les stratégies anti-pishing](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) sont configurés en votre nom. [](safe-links.md) Toutes les stratégies Defender pour Office 365 sont créées en mode non-application en arrière-plan et ne sont pas visibles pour vous.

Dans le cadre de la configuration, le mode d’évaluation configure également [le filtrage amélioré pour les connecteurs](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors) (également appelé _liste d’ignorer_). Cette configuration améliore la précision du filtrage en préservant l’adresse IP et les informations de l’expéditeur, qui sont autrement perdues lorsque le courrier passe par une passerelle de sécurité de messagerie (ESG) devant Defender pour Office 365. Le filtrage amélioré pour les connecteurs améliore également la précision de filtrage pour vos stratégies anti-courrier indésirable et anti-hameçonnage Exchange Online Protection (EOP) existantes.

Le filtrage amélioré pour les connecteurs améliore la précision du filtrage, mais peut modifier la livrabilité de certains messages si vous disposez d’un esg devant Defender pour Office 365 et que vous ne contournez actuellement pas le filtrage EOP. L’impact est limité aux stratégies EOP ; Defender pour Office 365 stratégies configurées dans le cadre de l’évaluation sont créées en mode non-application. Pour réduire l’impact potentiel sur la production, vous pouvez contourner la plupart des filtrages EOP en créant une règle de flux de courrier (également appelée règle de transport) pour définir le niveau de confiance du courrier indésirable (SCL) des messages sur -1. Pour plus d’informations, consultez [Utiliser les règles de flux de courrier pour définir le niveau de confiance du courrier indésirable (SCL) dans les messages dans Exchange Online](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).

Lorsque le mode d’évaluation est configuré, vous disposez d’un rapport quotidien avec jusqu’à 90 jours de données quantifiant les messages qui auraient été bloqués si les stratégies avaient été implémentées (par exemple, supprimer, envoyer à un indésirable, mettre en quarantaine). Les rapports sont générés pour toutes les détections Defender pour Office 365 et EOP. Les rapports sont agrégés par technologie de détection (par exemple, emprunt d’identité) et peuvent être filtrés par intervalle de temps. En outre, les rapports de messages peuvent être créés à la demande pour créer des tableaux croisés dynamiques personnalisés ou pour approfondir les messages à l’aide de l’Explorateur.

Avec l’expérience de configuration simplifiée, vous pouvez vous concentrer sur :

- Exécution de l’évaluation
- Obtention d’un rapport détaillé
- Analyse du rapport à des fins d’action
- Présentation du résultat de l’évaluation

## <a name="before-you-begin"></a>Avant de commencer

### <a name="licensing"></a>Licences

Pour accéder à l’évaluation, vous devez respecter les exigences de licence. L’une des licences suivantes fonctionne :

- Microsoft Defender pour Office 365 Plan 1
- Microsoft Defender pour Office 365 Plan 2
- Microsoft 365 E5, Microsoft 365 E5 Security
- Office 365 E5

Si vous n’avez pas l’une de ces licences, vous devez obtenir une licence d’évaluation.

#### <a name="trial"></a>Version d’évaluation

Pour obtenir une licence d’évaluation pour Microsoft Defender pour Office 365, vous devez avoir le **rôle d’administrateur de facturation** ou **d’administrateur général**. Demandez l’autorisation à une personne qui a le rôle d’administrateur général. [En savoir plus sur les abonnements et les licences](../../commerce/licenses/subscriptions-and-licenses.md)

Une fois que vous avez le rôle approprié, le chemin recommandé consiste à obtenir une licence d’essai pour Microsoft Defender pour Office 365 (Plan 2) dans le Centre d'administration Microsoft 365<https://admin.microsoft.com>, puis à accéder aux **services d’achat** de **facturation**\>, puis à rechercher et sélectionner le Microsoft Defender pour Office 365 (Plan 2). Ou, pour accéder directement à la page d’évaluation, utilisez <https://admin.microsoft.com/AdminPortal/Home#/catalog/offer-details/microsoft-defender-for-office-365-plan-2-/223860DC-15D6-42D9-A861-AE05473069FA)> La version d’évaluation inclut une version d’évaluation gratuite de 30 jours pour 25 licences.

Vous disposerez d’une fenêtre de 30 jours avec l’évaluation pour surveiller et signaler les menaces avancées. Vous aurez également la possibilité d’acheter un abonnement payant si vous souhaitez disposer des fonctionnalités de Defender pour Office 365 complètes.

### <a name="roles"></a>Rôles

**Exchange Online rôles** sont nécessaires pour configurer Defender pour Office 365 en mode d’évaluation. L’attribution d’un rôle d’administrateur de conformité ou de sécurité Microsoft 365 ne fonctionnera pas.

- [En savoir plus sur les autorisations dans Exchange Online](/exchange/permissions-exo/permissions-exo)
- [En savoir plus sur l’attribution de rôles d’administrateur](../../admin/add-users/assign-admin-roles.md)

Les rôles suivants sont nécessaires :

|Tâche|Rôle (dans Exchange Online)|
|---|---|
|Obtenir un essai gratuit ou acheter Microsoft Defender pour Office 365 (Plan 2)|Rôle d’administrateur de facturation OU rôle d’administrateur général|
|Créer une stratégie d’évaluation|Rôle Domaines distants et acceptés ; Rôle d’administrateur de sécurité|
|Modifier la stratégie d’évaluation|Rôle Domaines distants et acceptés ; Rôle d’administrateur de sécurité|
|Supprimer la stratégie d’évaluation|Rôle Domaines distants et acceptés ; Rôle d’administrateur de sécurité |
|Afficher le rapport d’évaluation|Rôle d’administrateur de la sécurité OU rôle lecteur Sécurité|

### <a name="enhanced-filtering-for-connectors"></a>Filtrage amélioré pour les connecteurs

Vos stratégies de Exchange Online Protection, telles que la protection en bloc et contre le courrier indésirable, resteront les mêmes. Toutefois, l’évaluation active le filtrage amélioré pour les connecteurs, ce qui peut avoir un impact sur votre flux de courrier et Exchange Online Protection stratégies, sauf si elle est contournée.

Le filtrage amélioré pour les connecteurs permet aux locataires d’utiliser la protection contre l’usurpation d’identité. La lutte contre l’usurpation d’identité n’est pas prise en charge si vous utilisez une passerelle de sécurité de messagerie (ESG) sans avoir activé le filtrage amélioré pour les connecteurs.

### <a name="urls"></a>URL

Les URL seront détonées pendant le flux de messagerie. Si vous ne souhaitez pas que des URL spécifiques soient détonées, gérez votre liste d’URL autorisées de manière appropriée. Pour plus [d’informations, consultez Gérer la liste d’autorisations/blocages du locataire](tenant-allow-block-list.md) .

Les liens d’URL dans les corps des messages électroniques ne sont pas encapsulés pour réduire l’impact sur les clients.

### <a name="email-routing"></a>Email routage

Préparez les détails correspondants dont vous aurez besoin pour configurer la façon dont votre courrier électronique est actuellement acheminé, y compris le nom du connecteur entrant qui achemine votre courrier. Si vous utilisez simplement Exchange Online Protection, vous n’aurez pas de connecteur. [En savoir plus sur le flux de courrier et le routage des e-mails](/office365/servicedescriptions/exchange-online-service-description/mail-flow)

Les scénarios de routage des e-mails pris en charge sont les suivants :

- **Partenaire tiers et/ou fournisseur de services local** : le connecteur entrant que vous souhaitez évaluer utilise un fournisseur tiers et/ou vous utilisez une solution pour la sécurité des e-mails localement.
- **Microsoft Exchange Online Protection uniquement** : le locataire que vous souhaitez évaluer utilise Office 365 pour la sécurité des e-mails et l’enregistrement MX (Mail Exchange) pointe vers Microsoft.

### <a name="email-security-gateway"></a>passerelle de sécurité Email

Si vous utilisez une passerelle de sécurité de messagerie (ESG) tierce, vous devez connaître le nom du fournisseur. Si vous utilisez un esg local ou des fournisseurs non pris en charge, vous devez connaître les adresses IP publiques des appareils.

Les partenaires tiers pris en charge sont les suivants :

- Barracuda
- Ironport
- Mimecast
- Proofpoint
- Sophos
- Symantec
- Trend Micro

### <a name="scoping"></a>Étendue

Vous serez en mesure d’étendre l’évaluation à un connecteur entrant. Si aucun connecteur n’est configuré, l’étendue d’évaluation permet aux administrateurs de collecter des données auprès d’un utilisateur de votre locataire pour évaluer Defender pour Office 365.

## <a name="get-started-with-the-evaluation"></a>Bien démarrer avec l’évaluation

Recherchez la carte de configuration d’évaluation Microsoft Defender pour Office 365 dans le portail Microsoft 365 Defender à partir des points d’accès suivants :

- **Terminaison** \> Gestion \> **des vulnérabilités** **Tableau de bord** (<https://security.microsoft.com/tvm_dashboard>)
- **Email & stratégies de collaboration** \> **& règles** **de menace** \> (<https://security.microsoft.com/threatpolicy>)
- **Rapports** \> **Email & rapports** de collaboration \> **Email & collaboration** (<https://security.microsoft.com/emailandcollabreport>)

## <a name="setting-up-the-evaluation"></a>Configurer l’évaluation

Une fois que vous avez démarré le flux de configuration pour votre évaluation, deux options de routage s’offrent à vous. En fonction des besoins de configuration et d’évaluation du routage du courrier de votre organisation, vous pouvez choisir si vous utilisez un fournisseur de services tiers et/ou local ou uniquement Microsoft Exchange Online.

- Si vous utilisez un partenaire tiers et/ou un fournisseur de services local, vous devez sélectionner le nom du fournisseur dans le menu déroulant. Fournissez les autres détails liés au connecteur.

- Sélectionnez **Microsoft Exchange Online** si l’enregistrement MX pointe vers Microsoft et que vous disposez d’une boîte aux lettres Exchange Online.

Examinez vos paramètres et modifiez-les si nécessaire. Ensuite, **sélectionnez Créer une évaluation**. Vous devez recevoir un message de confirmation pour indiquer que votre configuration est terminée.

Votre rapport d’évaluation Microsoft Defender pour Office 365 est généré une fois par jour. Le remplissage des données peut prendre jusqu’à 24 heures.

### <a name="exchange-mail-flow-rules-optional"></a>Règles de flux de messagerie Exchange (facultatif)

Si vous disposez d’une passerelle existante, l’activation du mode d’évaluation active le filtrage amélioré pour les connecteurs. Cette fonctionnalité améliore la précision du filtrage en modifiant l’adresse IP de l’expéditeur entrant. Cette fonctionnalité peut modifier les verdicts de filtre, et si vous ne contournez pas Exchange Online Protection, cela peut modifier la livrabilité de certains messages. Dans ce cas, vous pouvez ignorer temporairement le filtrage pour analyser l’impact. Pour contourner le filtrage, créez une règle de flux de messagerie (également appelée règle de transport) dans le Centre d’administration Exchange (EAC) à <https://admin.exchange.microsoft.com/#/transportrules> partir de laquelle la liste SCL des messages est -1 (si vous n’en avez pas déjà). Pour obtenir des instructions, consultez [Utiliser des règles de flux de courrier pour définir le niveau de confiance du courrier indésirable dans les messages dans Exchange Online](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).

## <a name="evaluate-capabilities"></a>Évaluer les fonctionnalités

Une fois le rapport d’évaluation généré, déterminez le nombre de liens de menace avancés, de pièces jointes avancées et d’emprunts d’identité potentiels qui ont été identifiés dans les e-mails et les espaces de travail de collaboration de votre organisation.

Une fois la version d’évaluation expirée, vous pouvez continuer à accéder au rapport pendant 90 jours. Toutefois, il ne recueillera plus d’informations. Si vous souhaitez continuer à utiliser Microsoft Defender pour Office 365 après l’expiration de votre version d’évaluation, assurez-vous [d’acheter un abonnement payant pour Microsoft Defender pour Office 365 (Plan 2).](https://admin.microsoft.com/AdminPortal/Home#/catalog/offer-details/microsoft-defender-for-office-365-plan-2-/223860DC-15D6-42D9-A861-AE05473069FA)

Vous pouvez accéder à **Paramètres** pour mettre à jour votre routage ou désactiver votre évaluation à tout moment. Toutefois, vous devez refaire le même processus de configuration si vous décidez de poursuivre votre évaluation après l’avoir désactivée.

## <a name="provide-feedback"></a>Envoyer des commentaires

Vos commentaires nous aident à mieux protéger votre environnement contre les attaques avancées. Partagez votre expérience et vos impressions sur les fonctionnalités du produit et les résultats de l’évaluation.

Sélectionnez **Donner des commentaires** pour nous faire savoir ce que vous pensez.
