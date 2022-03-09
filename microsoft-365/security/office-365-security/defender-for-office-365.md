---
title: Microsoft Defender pour Office 365 - CSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.localizationpriority: high
search.appverid:
- MET150
- MOE150
ms.assetid: e100fe7c-f2a1-4b7d-9e08-622330b83653
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
- intro-overview
description: Microsoft Defender pour Office 365 inclut des pièces jointes sécurisées, des liens fiables, des outils anti-hameçonnage avancés, des outils de création de rapports et des fonctionnalités Threat Intelligence.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: f78194541db8221aad1243966ddee6b6dc071d7d
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63317050"
---
# <a name="microsoft-defender-for-office-365"></a>Microsoft Defender pour Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> Cet article est destiné aux clients professionnels dotés de [Microsoft Defender pour Office 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description). Si vous utilisez Outlook.com, Microsoft 365 Famille ou Microsoft 365 Personnel et que vous recherchez des informations sur les liens ou pièces jointes fiables dans Outlook, reportez-vous à [Sécurité d’Outlook.com renforcée pour abonnés Microsoft 365](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

Microsoft Defender pour Office 365 protège votre organisation contre les menaces malveillantes posées par les messages électroniques, les liens (URL) et les outils de collaboration. Microsoft Defender pour Office 365 inclut :

- **[Stratégies de protection contre les menaces](#configure-microsoft-defender-for-office-365-policies)** : définissez des stratégies de protection contre les menaces pour définir le niveau de protection approprié pour votre organisation.

- **[Rapports](#view-microsoft-defender-for-office-365-reports)** : affichez des rapports en temps réel pour contrôler les performances de Defender pour Office 365 au sein de votre organisation.

- **[Fonctionnalités de recherche et de réponse aux menaces](#use-threat-investigation-and-response-capabilities)** : utilisez des outils de pointe pour étudier, comprendre, simuler et prévenir les menaces.

- **[Fonctionnalités automatisées d’enquête et de réponse](office-365-air.md)** : économisez du temps et des efforts pour investiguer et atténuer les menaces.

## <a name="interactive-guide-to-microsoft-defender-for-office-365"></a>Guide interactif pour Microsoft Defender pour Office 365

Dans ce guide interactif, vous découvrirez comment protéger votre organisation à l’aide de Microsoft Defender pour Office 365. Vous découvrirez comment Defender pour Office 365 peut vous aider à définir les stratégies de protection, analyser les menaces pour votre organisation et répondre aux attaques.

[Consulter le guide interactif](https://aka.ms/MSDO-IG)

## <a name="getting-started"></a>Prise en main

Si vous débutez avec Microsoft Defender pour Office 365 ou que vous apprenez le mieux par la *pratique*, il peut être utile de diviser la configuration initiale de Defender pour Office 365 en plusieurs blocs, d'effectuer des recherches et de consulter des rapports en utilisant cet article comme référence. Voici des blocs logiques de configuration initiale :

- Configurez tous les éléments à l’aide de la fonctionnalité «*anti*» dans le nom.
  - anti-programme malveillant
  - anti-hameçonnage
  - anti-spam
- Configurez tous les éléments avec «*Fiable*» dans le nom.
  - Liens sûrs
  - Pièces jointes fiables
- Protégez les charges de travail (par exemple, SharePoint Online, OneDrive et Teams)
- Protéger avec une purge automatique zéro heure (PAZH).

Pour savoir comment procéder, [cliquez sur ce lien](protect-against-threats.md).

> [!NOTE]
> Microsoft Defender pour Office 365 est disponible en deux types de plans différents. Vous pouvez déterminer si vous avez le **Plan 1** si vous avez des détections en temps réel, et le **Plan 2**, si vous avez l’Explorateur de menaces. Le plan que vous avez influence les outils que vous verrez, alors soyez certain que vous êtes conscient de votre plan au fur et à mesure que vous apprenez.

## <a name="microsoft-defender-for-office-365-plan-1-and-plan-2"></a>Microsoft Defender pour Office 365 Plan 1 et Plan 2

Le tableau suivant récapitule les actions incluent dans chaque plan.

****

|Microsoft Defender pour Office 365 Plan 1|Microsoft Defender pour Office 365 Plan 2|
|---|---|
|Fonctionnalités de configuration, de protection et de détection : <ul><li>[Pièces jointes fiables](safe-attachments.md)</li><li>[Liens fiables](safe-links.md)</li><li>[Pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams](mdo-for-spo-odb-and-teams.md)</li><li>[Protection contre le hameçonnage dans Defender pour Office 365](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)</li><li>[Détections en temps réel](threat-explorer.md)</li></ul>|Fonctionnalités de Microsoft Defender pour Office 365 Plan 1 <p> --- plus --- <p> Fonctionnalités d’automatisation, d’examen, de correction et de formation : <ul><li>[Suivi des menaces](threat-trackers.md)</li><li>[Threat Explorer](threat-explorer.md)</li><li>[Examen et réponse automatisés](office-365-air.md)</li><li>[Formation à la simulation d'attaque](attack-simulation-training.md)</li><li>[Recherche proactive des menaces avec repérage avancé dans Microsoft 365 Defender](../defender/advanced-hunting-overview.md)</li><li>[Examiner les incidents dans Microsoft 365 Defender](../defender/investigate-incidents.md)</li><li>[Examiner les alertes dans Microsoft 365 Defender](../defender/investigate-alerts.md)</li></ul>|


- Microsoft Defender pour Office 365 Plan 2 est inclus dans Office 365 E5, Office 365 A5 et Microsoft 365 E5.

- Microsoft Defender pour Office 365 Plan 1 est inclus dans Microsoft 365 Business Premium.

- Microsoft Defender pour Office 365 Plan 1 et Defender pour Office 365 Plan 2 sont tous deux disponibles sous forme de modules complémentaires pour certains abonnements. Pour en savoir plus, voici un autre lien [Disponibilité des fonctionnalités pour les offres Microsoft Defender pour Office 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans).

- La fonctionnalité [Documents sécurisés](safe-docs.md) est uniquement disponible pour les utilisateurs ayant des licences Microsoft 365 E5 ou Microsoft 365 E5 Sécurité (non inclus dans les offres Microsoft Defender pour Office 365)

- Si votre abonnement actuel n’inclut pas Microsoft Defender pour Office 365 et que vous le souhaitez, [contactez le service commercial pour commencer une version d’évaluation](https://info.microsoft.com/ww-landing-M365SMB-web-contact.html) et découvrez comment Microsoft Defender pour Office 365 peut fonctionner dans votre organisation.

- Les clients Microsoft Defender pour Office 365 P2 ont accès à **l’intégration Microsoft 365 Defender** pour détecter, examiner et répondre efficacement aux incidents et alertes.

## <a name="configure-microsoft-defender-for-office-365-policies"></a>Configurer les stratégies de Microsoft Defender pour Office 365

Avec Microsoft Defender pour Office 365, l’équipe de sécurité de votre organisation peut configurer la protection en définissant des stratégies dans le portail Microsoft 365 Defender à l’adresse <https://security.microsoft.com> sur **E-mail et collaboration**\>**Stratégies et règles**\>**Stratégies de menace**. Vous pouvez également accéder directement à la page **Stratégies de menace** à l’aide de <https://security.microsoft.com/threatpolicy>.

Pour en savoir plus, regardez [cette vidéo](https://www.youtube.com/watch?v=vivvTmWJ_3c).

> [!TIP]
> Consultez [Se protéger contre les menaces](protect-against-threats.md) pour définir une brève liste de stratégies.

## <a name="defender-for-office-365-policies"></a>Stratégies de Defender pour Office 365

Les stratégies définies pour votre organisation déterminent le comportement et le niveau de protection des menaces prédéfinies. Les options de stratégie sont extrêmement flexibles. Par exemple, l’équipe de sécurité de votre organisation peut affecter une protection affinée contre les menaces au niveau de l’utilisateur, de l’organisation, du destinataire et du domaine. Il est important de revoir vos stratégies régulièrement, car de nouvelles menaces et défis apparaissent quotidiennement.

- **[Pièces jointes fiables](safe-attachments.md)** : fournit une protection dès le premier jour pour protéger votre système de messagerie, en vérifiant les pièces jointes pour du contenu malveillant. Il achemine les messages et les pièces jointes qui ne comportent pas de signature de virus/programme malveillant vers un environnement spécial, puis utilise les techniques de machine learning et d’analyse pour détecter les intentions malveillantes. Si aucune activité suspecte n’est détectée, le message est transféré vers la boîte aux lettres. Pour plus d’informations, reportez-vous à [Définir des stratégies de pièces jointes fiables](set-up-safe-attachments-policies.md).

- **[Liens fiables](safe-links.md)** : permet de vérifier les URL au moment du clic, par exemple, dans les messages électroniques et les fichiers Office. La protection est continue et s’applique à l’ensemble de votre environnement de messagerie et Office. Les liens sont numérisés pour chaque clic : les liens fiables restent accessibles et les liens malveillants sont bloqués de façon dynamique. Pour plus d’informations, reportez-vous à [Configurer les stratégies de liens fiables](set-up-safe-links-policies.md).

- **[Pièces jointes fiables pour SharePoint, OneDrive, and Microsoft Teams](mdo-for-spo-odb-and-teams.md)** : protègent votre organisation lorsque les utilisateurs collaborent et partagent des fichiers, en identifiant, puis en bloquant les fichiers malveillants dans les sites d’équipe et les bibliothèques de documents. Pour obtenir plus d’informations, consultez l’article [Activer Defender pour Office 365 pour SharePoint, OneDrive et Microsoft Teams](turn-on-mdo-for-spo-odb-and-teams.md).

- **[Protection anti-hameçonnage dans Defender pour Office 365](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)** : détecte les tentatives d’usurpation d’identité entre vos utilisateurs et les domaines internes ou personnalisés. Cela permet d’appliquer des modèles de machine learning et des algorithmes avancés de détection de l’emprunt d’identité pour contrer des attaques par hameçonnage. Pour plus d’informations, voir [Configurer les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365](configure-mdo-anti-phishing-policies.md).

## <a name="view-microsoft-defender-for-office-365-reports"></a>Afficher les rapports de Microsoft Defender pour Office 365

Microsoft Defender pour Office 365 inclut des [rapports](view-reports-for-mdo.md) pour surveiller les performances de votre Defender pour Office 365. Vous pouvez accéder aux rapports dans le portail Microsoft 365 Defender à <https://security.microsoft.com> sur **Rapports**\>**E-mail et collaboration**\>**E-mail et rapports de collaboration**. Vous pouvez également accéder directement à la page **Rapports d’e-mail et de collaboration** à l’aide de <https://security.microsoft.com/securityreports>.

Les rapports sont mis à jour en temps réel, ce qui vous fournit les informations les plus récentes. Ces rapports fournissent également des recommandations et vous informent contre les menaces imminentes. Les rapports prédéfinis incluent les données suivantes :

- [Threat Explorer (et détections en temps réel)](threat-explorer.md)
- [Rapport sur l’état de la protection contre les menaces](view-reports-for-mdo.md#threat-protection-status-report)
- ... et bien plus encore.

## <a name="use-threat-investigation-and-response-capabilities"></a>Utilisation de l’examen des menaces et des fonctionnalités de réponse

Microsoft Defender pour Office 365 Plan 2 inclut les meilleurs [outils d’examen et de réponse aux menaces](office-365-ti.md) qui permettent à l’équipe de sécurité de votre organisation d’anticiper, de comprendre et de prévenir les attaques malveillantes.

- **[Les suivis de menace](threat-trackers.md)** fournissent la dernière intelligence sur les problèmes de sécurité sur Internet. Par exemple, vous pouvez afficher des informations sur les derniers programmes malveillants et prendre des contre-mesures avant qu’ils ne deviennent réellement une menace pour votre organisation. Les suivis disponibles incluent des [suivis important](threat-trackers.md#noteworthy-trackers), des [suivis de tendances](threat-trackers.md#trending-trackers),des [requêtes suivies](threat-trackers.md#tracked-queries) et des [requêtes enregistrées](threat-trackers.md#saved-queries).

- **[Explorateur de menaces (ou détections en temps réel)](threat-explorer.md)** (également appelé Explorateur) est un rapport en temps réel qui vous permet d’identifier et d’analyser les menaces récentes. Vous pouvez configurer Explorateur pour afficher des données pour des périodes personnalisées.

- **[La formation à la simulation d'attaque](attack-simulation-training.md)** vous permet d'exécuter des scénarios d'attaque réalistes dans votre organisation afin d'identifier les vulnérabilités. Des simulations des types d'attaques actuels sont disponibles, notamment des attaques de récupération des informations d'identification et de connexion par hameçonnage et des attaques par pulvérisation de mots de passe et par mot de passe par force brute.

## <a name="save-time-with-automated-investigation-and-response"></a>Gagner du temps avec l’examen et la réponse automatisé

(**NOUVEAU !**) Lorsque vous effectuez des recherches sur une attaque potentielle de sécurité sur Internet, le temps est essentiel. Plus vous pourrez identifier et atténuer les menaces rapidement, mieux votre organisation se portera. [Examen et réponse automatique aux incidents](office-365-air.md) (AIR) inclut un ensemble de règles de sécurité qui peuvent être lancées automatiquement, par exemple lorsqu’une alerte est déclenchée, ou manuellement, par exemple à partir d’un affichage dans Explorer. Réponse automatique aux incidents permet à votre équipe spécialisée dans les opérations de sécurité d’économiser du temps et des efforts pour réduire efficacement les menaces. Pour en savoir plus, voir [Air dans Office 365](office-365-air.md).

## <a name="permissions-required-to-use-microsoft-defender-for-office-365-features"></a>Autorisations requises pour utiliser les fonctionnalités de Microsoft Defender pour Office 365

Pour accéder aux fonctionnalités de Microsoft Defender pour Office 365, vous devez disposer d’un rôle approprié. Le tableau suivant inclut quelques exemples :

<br>

****

|Rôle ou groupe de rôles|Ressources pour en savoir plus|
|---|---|
|administrateur général (Gestion de l’organisation)|Vous pouvez attribuer ce rôle dans Azure Active Directory ou dans le portail Microsoft 365 Defender. Pour plus d’informations, consultez [Autorisations dans le portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md).|
|Administrateur de sécurité|Vous pouvez attribuer ce rôle dans Azure Active Directory ou dans le portail Microsoft 365 Defender. Pour plus d’informations, consultez [Autorisations dans le portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md).|
|Gestion de l’organisation dans Exchange Online.|[Autorisations dans Exchange Online](/exchange/permissions-exo/permissions-exo) <p> [Exchange Online PowerShell](/powershell/exchange/exchange-online-powershell)|
|Rechercher et vider|Ce rôle est disponible uniquement dans le portail Microsoft 365 Defender ou dans le Centre de conformité Microsoft 365. Pour plus d’informations, consultez [Autorisations dans le portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md) et [Autorisations dans le Centre de conformité Microsoft 365](../../compliance/microsoft-365-compliance-center-permissions.md).|
|||

## <a name="get-microsoft-defender-for-office-365"></a>Obtenir Microsoft Defender pour Office 365

Microsoft Defender pour Office 365 est inclus dans certains abonnements, tels que Microsoft 365 E5, Office 365 E5, Office 365 A5 et Microsoft 365 Business Premium. Si votre abonnement n’inclut pas Defender pour Office 365, vous pouvez acheter Defender pour Office 365 Plan 1 ou Defender pour Office 365 Plan 2 comme module complémentaire pour certains abonnements. Pour en savoir plus, consultez les ressources suivantes :

- [Disponibilité de Microsoft Defender pour Office 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#office-365-advanced-threat-protection-atp-availability) pour une liste des abonnements incluant les offres Defender pour Office 365.

- [Disponibilité des fonctionnalités pour les offres Microsoft Defender pour Office 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans) pour une liste des fonctionnalités incluses dans Plan 1 et Plan 2.

- [Obtenez le bon Microsoft Defender pour Office 365](https://products.office.com/exchange/advance-threat-protection#pmg-allup-content) pour comparer les offres et acheter Defender pour Office 365.

- [Démarrez une version d’essai gratuite](https://go.microsoft.com/fwlink/p/?LinkID=698279)

## <a name="new-features-in-microsoft-defender-for-office-365"></a>Nouvelles fonctionnalités dans Microsoft Defender pour Office 365

De nouvelles fonctionnalités sont ajoutées à Microsoft Defender pour Office 365 en permanence. Pour en savoir plus, consultez les ressources suivantes :

- La [Feuille de route Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=Microsoft%2CDefender%2Cfor%2COffice%2C365) fournit la liste des nouvelles fonctionnalités de développement et de déploiement.

- [Description du service Microsoft Defender pour Office 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#whats-new-in-office-365-advanced-threat-protection-atp) décrit les fonctionnalités et la disponibilité entre les offres Defender pour Office 365.

## <a name="see-also"></a>Voir aussi

- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)
- [Enquêtes et réponses automatisées (AIR) dans Microsoft 365 Defender](../defender/m365d-autoir.md)
