---
title: Microsoft Defender pour Office 365
f1.keywords:
- CSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Priority
search.appverid:
- MET150
- MOE150
ms.assetid: e100fe7c-f2a1-4b7d-9e08-622330b83653
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.custom:
- seo-marvel-apr2020
description: Microsoft Defender pour Office 365 inclut des pièces jointes sécurisées, des liens fiables, des outils anti-hameçonnage avancés, des outils de création de rapports et des fonctionnalités d’intelligence contre les menaces.
ms.openlocfilehash: 86e738fa9390cc40b06c10a27f3198715bb991fd
ms.sourcegitcommit: ee39faf3507d0edc9497117b3b2854955c959c6c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "49614809"
---
# <a name="microsoft-defender-for-office-365"></a>Microsoft Defender pour Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


> [!IMPORTANT]
> Cet article est destiné aux entreprises qui ont [Microsoft Defender pour Office 365](https://docs.microsoft.com/office365/servicedescriptions/office-365-advanced-threat-protection-service-description). Si vous utilisez Outlook.com, Microsoft 365 Famille ou Microsoft 365 Personnel et que vous recherchez des informations sur les liens ou pièces jointes fiables dans Outlook, reportez-vous à [Sécurité d’Outlook.com renforcée pour abonnés Microsoft 365](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

Microsoft Defender pour Office 365 protège votre organisation contre les menaces malveillantes posées par les messages électroniques, les liens (URL) et les outils de collaboration. Defender pour Office 365 inclut :

- **[Stratégies de protection contre les menaces](#configure-microsoft-defender-for-office-365-policies)**  : définissez des stratégies de protection contre les menaces pour définir le niveau de protection approprié pour votre organisation.

- **[Rapports](#view-microsoft-defender-for-office-365-reports)**  : affichez des rapports en temps réel pour contrôler les performances de Defender pour Office 365 au sein de votre organisation.

- **[Fonctionnalités de recherche et de réponse aux menaces](#use-threat-investigation-and-response-capabilities)**  : utilisez des outils de pointe pour étudier, comprendre, simuler et prévenir les menaces.

- **[Fonctionnalités automatisées d’enquête et de réponse](office-365-air.md)**  : économisez du temps et des efforts pour investiguer et atténuer les menaces.

## <a name="getting-started"></a>Prise en main

Si vous débutez sur Microsoft Defender pour Office 365 ou si vous apprenez mieux par la *pratique*, vous pouvez être amené à interrompre la configuration de Defender pour Office 365 initiale en bloc, en examinant et en affichant des rapports à l’aide de cet article comme référence. Voici quelques blocs logiques de configuration précoce :

- Configurez tous les éléments à l’aide de la fonctionnalité «*anti*» dans le nom.
  - anti-programme malveillant
  - anti-hameçonnage
  - anti-spam
- Configurez tous les éléments avec «*Fiable*» dans le nom.
  - Liens fiables
  - pièces jointes fiables
- Protégez les charges de travail (par exemple, SharePoint Online, OneDrive et Teams)
- Protéger avec la purge automatique Zero-Hour

Pour savoir comment procéder, [cliquez sur ce lien](protect-against-threats.md).

> [!NOTE]
> Microsoft Defender pour Office 365 est disponible en deux types de plans différents. Vous pouvez déterminer si vous avez le **Plan 1** si vous avez des détections en temps réel, et le **Plan 2**, si vous avez l’Explorateur de menaces. Le plan que vous avez influence les outils que vous verrez, alors soyez certain que vous êtes conscient de votre plan au fur et à mesure que vous apprenez.

## <a name="microsoft-defender-for-office-365-plan-1-and-plan-2"></a>Microsoft Defender pour Office 365 Plan 1 et Plan 2

Le tableau suivant récapitule les actions incluent dans chaque plan.

****

|Microsoft Defender pour Office 365 Plan 1|Microsoft Defender pour Office 365 Plan 2|
|---|---|
|Fonctionnalités de configuration, de protection et de détection : <ul><li>[Pièces jointes fiables](atp-safe-attachments.md)</li><li>[Liens fiables](atp-safe-links.md)</li><li>[ATP pour SharePoint, OneDrive et Microsoft Teams](atp-for-spo-odb-and-teams.md)</li><li>[Anti-hameçonnage dans la protection de Defender pour Office 365](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)</li><li>[Détections en temps réel](threat-explorer.md)</li></ul>|Fonctionnalités de Microsoft Defender pour Office 365 Plan 1 <br>--- plus ---<br> Fonctionnalités d’automatisation, d’examen, de correction et de formation :<ul><li>[Suivi des menaces](threat-trackers.md)</li><li>[Threat Explorer](threat-explorer.md)</li><li>[Examen et réponse automatisés](office-365-air.md)</li><li>[Simulateur d’attaques](attack-simulator.md)</li><li>[Vues de campagne](campaigns.md)</li></ul>|
|

- Microsoft Defender pour Office 365 Plan 2 est inclus dans Office 365 E5, Office 365 A5, Microsoft 365 E5 Sécurité et Microsoft 365 E5.

- Microsoft Defender pour Office 365 Plan 1 est inclus dans Microsoft 365 Business Premium.

- Microsoft Defender pour Office 365 Plan 1 et Microsoft Defender pour Office 365 Plan 2 sont tous deux disponibles sous forme de modules complémentaires pour certains abonnements. Pour en savoir plus, voir [Disponibilité des fonctionnalités pour les offres Microsoft Defender pour Office 365](https://docs.microsoft.com/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans).

- La fonctionnalité [Documents sécurisés](safe-docs.md) est uniquement disponible pour les utilisateurs ayant des licences Microsoft 365 E5 ou Microsoft 365 E5 Sécurité (non inclus dans les offres Microsoft Defender pour Office 365)

- Si votre abonnement actuel n’inclut pas Microsoft Defender pour Office 365, [contactez le service ventes pour démarrer une version d’évaluation](https://go.microsoft.com/fwlink/p/?LinkId=518644), puis voyez comment Defender pour Office 365 peut fonctionner pour votre organisation.

## <a name="configure-microsoft-defender-for-office-365-policies"></a>Configurer les stratégies de Microsoft Defender pour Office 365

Avec Microsoft Defender pour Office 365 – Protection avancée contre les menaces, l’équipe de sécurité de votre organisation peut configurer la protection en définissant des stratégies dans le Centre de sécurité et de conformité (se référer à la <https://protection.office.com> \> **gestion des menaces** \> **dans la stratégie**).

> [!TIP]
> Consultez [Se protéger contre les menaces](protect-against-threats.md) pour définir une brève liste de stratégies.

## <a name="defender-for-office-365-policies"></a>Stratégies de Defender pour Office 365

Les stratégies définies pour votre organisation déterminent le comportement et le niveau de protection des menaces prédéfinies. Les options de stratégie sont extrêmement flexibles. Par exemple, l’équipe de sécurité de votre organisation peut affecter une protection affinée contre les menaces au niveau de l’utilisateur, de l’organisation, du destinataire et du domaine. Il est important de revoir vos stratégies régulièrement, car de nouvelles menaces et défis apparaissent quotidiennement.

- **[Pièces jointes fiables](atp-safe-attachments.md)**  : fournit une protection dès le premier jour pour protéger votre système de messagerie, en vérifiant les pièces jointes pour du contenu malveillant. Il achemine les messages et les pièces jointes qui ne comportent pas de signature de virus/programme malveillant vers un environnement spécial, puis utilise les techniques de machine learning et d’analyse pour détecter les intentions malveillantes. Si aucune activité suspecte n’est détectée, le message est transféré vers la boîte aux lettres. Pour plus d’informations, reportez-vous à [Définir des stratégies de pièces jointes fiables](set-up-atp-safe-attachments-policies.md).

- **[Liens fiables](atp-safe-links.md)**  : permet de vérifier les URL au moment du clic, par exemple, dans les messages électroniques et les fichiers Office. La protection est continue et s’applique à l’ensemble de votre environnement de messagerie et Office. Les liens sont numérisés pour chaque clic : les liens fiables restent accessibles et les liens malveillants sont bloqués de façon dynamique. Pour plus d’informations, reportez-vous à [Configurer les stratégies de liens fiables](set-up-atp-safe-links-policies.md).

- **[ATP pour SharePoint, OneDrive, and Microsoft Teams](atp-for-spo-odb-and-teams.md)**  : protège votre organisation lorsque les utilisateurs collaborent et partagent des fichiers, en identifiant et en bloquant les fichiers malveillants dans les sites d’équipe et les bibliothèques de documents. Pour obtenir plus d’informations, consultez l’article [Activer Defender pour Office 365 pour SharePoint, OneDrive et Microsoft Teams](turn-on-atp-for-spo-odb-and-teams.md).

- **[Protection anti-hameçonnage dans Defender pour Office 365](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)**  : détecte les tentatives d’usurpation d’identité entre vos utilisateurs et les domaines internes ou personnalisés. Cela permet d’appliquer des modèles de machine learning et des algorithmes avancés de détection de l’emprunt d’identité pour contrer des attaques par hameçonnage. Pour plus d’informations, voir [Configurer les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365](configure-atp-anti-phishing-policies.md).

## <a name="view-microsoft-defender-for-office-365-reports"></a>Afficher les rapports de Microsoft Defender pour Office 365

Microsoft Defender pour Office 365 inclut un [tableau de bord de rapports](view-reports-for-atp.md) avancé pour surveiller les performances de votre Defender pour Office 365. Vous pouvez y accéder via **Tableau de bord** \> **de rapports** dans le Centre de sécurité et de conformité.

Les rapports sont mis à jour en temps réel, ce qui vous fournit les informations les plus récentes. Ces rapports fournissent également des recommandations et vous informent contre les menaces imminentes. Les rapports prédéfinis incluent les données suivantes :

- [Threat Explorer (et détections en temps réel)](threat-explorer.md)

- [Rapport sur l’état de la protection contre les menaces](view-reports-for-atp.md#threat-protection-status-report)

- [Rapport sur les types de fichiers de Defender pour Office 365](view-reports-for-atp.md#defender-for-office-365-file-types-report)

- [Rapport d’actions sur les messages de Defender pour Office 365](view-reports-for-atp.md#defender-for-office-365-message-disposition-report)

- ... et bien plus encore.

## <a name="use-threat-investigation-and-response-capabilities"></a>Utilisation de l’examen des menaces et des fonctionnalités de réponse

Microsoft Defender pour Office 365 Plan 2 inclut les meilleurs [outils d’examen et de réponse aux menaces](office-365-ti.md) qui permettent à l’équipe de sécurité de votre organisation d’anticiper, de comprendre et de prévenir les attaques malveillantes.

- **[Les suivis de menace](threat-trackers.md)** fournissent la dernière intelligence sur les problèmes de sécurité sur Internet. Par exemple, vous pouvez afficher des informations sur les derniers programmes malveillants et prendre des contre-mesures avant qu’ils ne deviennent réellement une menace pour votre organisation. Les suivis disponibles incluent des [suivis important](threat-trackers.md#noteworthy-trackers), des [suivis de tendances](threat-trackers.md#trending-trackers),des [requêtes suivies](threat-trackers.md#tracked-queries) et des [requêtes enregistrées](threat-trackers.md#saved-queries).

- **[Threat Explorer (ou détections en temps réel)](threat-explorer.md)** (également appelé Explorer) est un rapport en temps réel qui vous permet d’identifier et d’analyser les menaces récentes. Vous pouvez configurer Explorer pour afficher des données pour les périodes personnalisées.

- **[Simulateur d’attaques](attack-simulator.md)** vous permet d’exécuter des scénarios d’attaques réalistes au sein de votre organisation afin d’identifier les vulnérabilités. Des simulations des types d'attaques actuels sont disponibles, notamment des attaques de récupération des informations d'identification et de connexion par hameçonnage et des attaques par pulvérisation de mots de passe et par mot de passe par force brute.

## <a name="save-time-with-automated-investigation-and-response"></a>Gagner du temps avec l’examen et la réponse automatisé

(**NOUVEAU !**) Lorsque vous effectuez des recherches sur une attaque potentielle de sécurité sur Internet, le temps est essentiel. Plus vous pourrez identifier et atténuer les menaces rapidement, mieux votre organisation se portera. [Examen et réponse automatique aux incidents](office-365-air.md) (AIR) inclut un ensemble de règles de sécurité qui peuvent être lancées automatiquement, par exemple lorsqu’une alerte est déclenchée, ou manuellement, par exemple à partir d’un affichage dans Explorer. Réponse automatique aux incidents permet à votre équipe spécialisée dans les opérations de sécurité d’économiser du temps et des efforts pour réduire efficacement les menaces. Pour en savoir plus, voir [Air dans Office 365](office-365-air.md).

## <a name="permissions-required-to-use-microsoft-defender-for-office-365-features"></a>Autorisations requises pour utiliser les fonctionnalités de Microsoft Defender pour Office 365

Pour accéder aux fonctionnalités de Microsoft Defender pour Office 365 dans le Centre de sécurité et conformité, vous devez disposer d’un rôle approprié. Le tableau ci-après inclut des exemples :

|Rôle ou groupe de rôles|Ressources pour en savoir plus|
|---|---|
|Administrateur général (peut être affecté dans Azure Active Directory ou dans le centre de sécurité et conformité)|[À propos des rôles d’administrateur Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles)|
|Administrateur de sécurité (peut être affecté dans Azure Active Directory ou le centre de sécurité et conformité)|[Autorisations des rôles d’administrateur dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles) <p> [Autorisations dans le centre de conformité et de sécurité](permissions-in-the-security-and-compliance-center.md)|
|Gestion de l’organisation Exchange Online (elle est affectée à Exchange Online)|[Autorisations dans Exchange Online](https://docs.microsoft.com/exchange/permissions-exo/permissions-exo) <p> [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online-powershell)|
|Rechercher et vider (cette opération est attribuée uniquement dans le centre de conformité et sécurité)|[Autorisations dans le centre de conformité et de sécurité](permissions-in-the-security-and-compliance-center.md)|

Pour en savoir plus, consultez [Autorisations dans le Centre de sécurité et de conformité](permissions-in-the-security-and-compliance-center.md).

## <a name="get-microsoft-defender-for-office-365"></a>Obtenir Microsoft Defender pour Office 365

Microsoft Defender pour Office 365 est inclus dans certains abonnements, tels que Microsoft 365 E5, Office 365 E5, Office 365 A5 et Microsoft 365 Business Premium. Si votre abonnement n’inclut pas Defender pour Office 365, vous pouvez acheter Defender pour Office 365 Plan 1 ou Defender pour Office 365 Plan 2 comme module complémentaire pour certains abonnements. Pour en savoir plus, consultez les ressources suivantes :

- [Disponibilité de Microsoft Defender pour Office 365](https://docs.microsoft.com/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#office-365-advanced-threat-protection-atp-availability) pour une liste des abonnements incluant les offres Defender pour Office 365.

- [Disponibilité des fonctionnalités pour les offres Microsoft Defender pour Office 365](https://docs.microsoft.com/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans) pour une liste des fonctionnalités incluses dans Plan 1 et Plan 2.

- [Obtenez le bon Microsoft Defender pour Office 365](https://products.office.com/exchange/advance-threat-protection#pmg-allup-content) pour comparer les offres et acheter Defender pour Office 365.

- [Démarrez une version d’essai gratuite](https://go.microsoft.com/fwlink/p/?LinkID=698279)

## <a name="new-features-in-microsoft-defender-for-office-365"></a>Nouvelles fonctionnalités dans Microsoft Defender pour Office 365

De nouvelles fonctionnalités sont ajoutées à Microsoft Defender pour Office 365 en permanence. Pour en savoir plus, consultez les ressources suivantes :

- La [Feuille de route Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=advanced%2Cthreat%2Cprotection) fournit la liste des nouvelles fonctionnalités de développement et de déploiement.

- [Description du service Microsoft Defender pour Office 365](https://docs.microsoft.com/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#whats-new-in-office-365-advanced-threat-protection-atp) décrit les fonctionnalités et la disponibilité entre les offres Defender pour Office 365.

## <a name="see-also"></a>Voir aussi

- [Microsoft 365 Defender](../mtp/microsoft-threat-protection.md)

- [Enquêtes et réponses automatisées (AIR) dans Microsoft 365 Defender](../mtp/mtp-autoir.md)
