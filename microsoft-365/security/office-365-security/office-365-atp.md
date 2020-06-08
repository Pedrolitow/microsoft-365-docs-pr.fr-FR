---
title: Office 365 – Protection avancée contre les menaces
f1.keywords:
- CSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: 02/24/2020
audience: Admin
ms.topic: hub-page
ms.service: O365-seccomp
localization_priority: Priority
search.appverid:
- MET150
- MOE150
ms.assetid: e100fe7c-f2a1-4b7d-9e08-622330b83653
ms.collection:
- M365-security-compliance
description: Office 365 – Protection avancée contre les menaces inclut des pièces jointes sécurisées, des liens sûrs, des outils anti-hameçonnage avancés, des outils de création de rapports et des fonctionnalités d’intelligence contre les menaces.
ms.openlocfilehash: f0d256a1d181b482516c7be55bca240a55dec567
ms.sourcegitcommit: 2de6e07ec55d78a5c5cf2f45732ae68acf058bcf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2020
ms.locfileid: "44588179"
---
# <a name="office-365-advanced-threat-protection"></a>Office 365 – Protection avancée contre les menaces

> [!IMPORTANT]
> Cet article est destiné aux entreprises qui ont [Office 365 – Protection avancée contre les menaces](https://docs.microsoft.com/office365/servicedescriptions/office-365-advanced-threat-protection-service-description). Si vous utilisez Outlook.com, Microsoft 365 Famille ou Microsoft 365 Personnel et que vous recherchez des informations sur les liens ou pièces jointes fiables dans Outlook, reportez-vous à [Sécurité d’Outlook.com renforcée pour abonnés Microsoft 365](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

## <a name="overview"></a>Vue d’ensemble

Office 365 – Protection avancée contre les menaces (ATP) protège votre organisation contre les menaces malveillantes posées par les messages électroniques, les liens (URL) et les outils de collaboration. PACM inclut ce qui suit :

- **[Stratégies de protection contre les menaces](#configure-atp-policies)**  : définissez des stratégies de protection contre les menaces pour définir le niveau de protection approprié pour votre organisation.

- **[Rapports](#view-office-365-atp-reports)**  : affichez des rapports en temps réel pour contrôler les performances de PACM au sein de votre organisation.

- **[Fonctionnalités de recherche et de réponse aux menaces](#use-threat-investigation-and-response-capabilities)**  : utilisez des outils de pointe pour étudier, comprendre, simuler et prévenir les menaces.

- **[Fonctionnalités automatisées d’enquête et de réponse](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-air)**  : économisez du temps et des efforts pour investiguer et atténuer les menaces.

## <a name="office-365-atp-plan-1-and-plan-2"></a>Office 365 – Protection avancée contre les menaces Plan 1 et Plan 2

Le tableau suivant récapitule les actions incluent dans chaque plan.

|||
|---|---|
|**Office 365 – Protection avancée contre les menaces (Plan 1)**|**Office 365 – Protection avancée contre les menaces (Plan 2)**|
|Fonctionnalités de configuration, de protection et de détection :<br/>• [Pièces jointes fiables](atp-safe-attachments.md)<br/>• [Liens fiables](atp-safe-links.md)<br/>• [PACM pour SharePoint, OneDrive et Microsoft Teams](atp-for-spo-odb-and-teams.md)<br/>• [Protection anti-hameçonnage](set-up-anti-phishing-policies.md#exclusive-settings-in-atp-anti-phishing-policies)<br/>• [Détections en temps réel](threat-explorer.md)|Fonctionnalités de l’offre Office 365 - Protection avancée contre les menaces (plan 1)<br/>--- plus ---<br/>Fonctionnalités d’automatisation, d’examen, de correction et de formation :<br/>• [Suivis de menace](threat-trackers.md)<br/>• [Explorateur de menaces](threat-explorer.md)<br/>• [Enquêtes et réponses automatisées](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-air)<br/>• [Simulateur d’attaques](attack-simulator.md)|
|

- Office 365 – Protection avancée contre les menaces (Plan 2) est inclus dans Office 365 E5, Office 365 a5 et Microsoft 365 E5.

- Le plan 1 Office 365 ATP est incluse dans Microsoft 365 Business Premium.

- Le plan 1 Office 365 ATP et le Plan 2 Office 365 ATP sont, pour certains abonnements, disponibles sous forme de complément. Pour plus d’informations, consulter [Disponibilité des fonctionnalités pour les différents plans ATP](https://docs.microsoft.com/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans).

- Si votre abonnement actuel n’inclut pas Office 365 ATP, [contactez le service ventes pour démarrer une version d’évaluation](https://go.microsoft.com/fwlink/p/?LinkId=518644) et consultez l’ATP peut fonctionner pour votre organisation.

## <a name="configure-atp-policies"></a>Configurez des stratégies ATP

Avec Office 365 ATP – Protection avancée contre les menaces, l’équipe de sécurité de votre organisation peut configurer la protection en définissant des stratégies dans le centre de sécurité et de conformité (se référer à la [https://protection.office.com](https://protection.office.com) > **gestion des menaces** > **dans la stratégie**).

> [!TIP]
> Consulter [Se protéger contre les menaces](protect-against-threats.md) pour définir une brève liste de stratégies.

Les stratégies définies pour votre organisation déterminent le comportement et le niveau de protection des menaces prédéfinies. Les options de stratégie sont extrêmement flexibles. Par exemple, l’équipe de sécurité de votre organisation peut affecter une protection affinée contre les menaces au niveau de l’utilisateur, de l’organisation, du destinataire et du domaine. Il est important de revoir vos stratégies régulièrement, car de nouvelles menaces et défis apparaissent quotidiennement.

- **[Pièces jointes fiables ATP](atp-safe-attachments.md)**  : fournit une protection dès le premier jour pour protéger votre système de messagerie, en vérifiant les pièces jointes pour du contenu malveillant. Il achemine les messages et les pièces jointes qui ne comportent pas de signature de virus/programme malveillant vers un environnement spécial, puis utilise les techniques de machine learning et d’analyse pour détecter les intentions malveillantes. Si aucune activité suspecte n’est détectée, le message est transféré vers la boîte aux lettres. Pour plus d’informations, reportez-vous à [Définir des stratégies de pièces jointes fiables Office 365 – Protection avancée contre les menaces](set-up-atp-safe-attachments-policies.md).

- **[Liens fiables ATP](atp-safe-links.md)**  : permet de vérifier les URL au moment du clic, par exemple, dans les messages électroniques et les fichiers Office. La protection est continue et s’applique à l’ensemble de votre environnement de messagerie et Office. Les liens sont numérisés pour chaque clic : les liens fiables restent accessibles et les liens malveillants sont bloqués de façon dynamique. Pour plus d’informations, reportez-vous à [Configurer les stratégies de liens fiables Office 365 – Protection avancée contre les menaces](set-up-atp-safe-links-policies.md).

- **[ATP pour SharePoint, OneDrive, and Microsoft Teams](atp-for-spo-odb-and-teams.md)**  : protège votre organisation lorsque les utilisateurs collaborent et partagent des fichiers, en identifiant et en bloquant les fichiers malveillants dans les sites d’équipe et les bibliothèques de documents. Pour obtenir plus d’informations, consultez l’article [Activer Office 365 ATP pour SharePoint, OneDrive et Microsoft Teams](turn-on-atp-for-spo-odb-and-teams.md).

- **[Protection anti-hameçonnage ATP](set-up-anti-phishing-policies.md#exclusive-settings-in-atp-anti-phishing-policies)**  : détecte les tentatives d’usurpation d’identité entre vos utilisateurs et les domaines internes ou personnalisés. Cela permet d’appliquer des modèles de machine learning et des algorithmes avancés de détection de l’emprunt d’identité pour contrer des attaques par hameçonnage. Pour plus d’informations, voir [Configurer les stratégies anti-hameçonnage de protection avancée contre les menaces dans Office 365](configure-atp-anti-phishing-policies.md).

## <a name="view-office-365-atp-reports"></a>Afficher les rapports d’Office 365 ATP – Protection avancée contre les menaces.

Office 365 ATP – Protection avancée contre les menaces inclut un [tableau de bord avancé de création de rapports](view-reports-for-atp.md) pour contrôler vos performances ATP. Vous pouvez y accéder via **Tableau de bord** > **de rapports** dans le centre de sécurité et conformité.

Les rapports sont mis à jour en temps réel, ce qui vous fournit les informations les plus récentes. Ces rapports fournissent également des recommandations et vous informent contre les menaces imminentes. Les rapports prédéfinis incluent les données suivantes :

- [Threat Explorer (et détections en temps réel)](threat-explorer.md)

- [Rapport sur l’état de la protection contre les menaces](view-reports-for-atp.md#threat-protection-status-report)

- [Rapport sur les types de fichiers ATP](view-reports-for-atp.md#atp-file-types-report)

- [Rapport de destruction de message ATP](view-reports-for-atp.md#atp-message-disposition-report)

- ... et bien plus encore.

## <a name="use-threat-investigation-and-response-capabilities"></a>Utilisation de l’examen des menaces et des fonctionnalités de réponse

Office 365 – Protection avancée contre les menaces Plan 2 inclut des [outils examen des menaces et des fonctionnalités de réponse](office-365-ti.md) qui permettent à l’équipe de sécurité de votre organisation d’anticiper, de comprendre et de prévenir les attaques malveillantes.

- **[Les suivis de menace](threat-trackers.md)** fournissent la dernière intelligence sur les problèmes de sécurité sur Internet. Par exemple, vous pouvez afficher des informations sur les derniers programmes malveillants et prendre des contre-mesures avant qu’ils ne deviennent réellement une menace pour votre organisation. Les suivis disponibles incluent des [suivis important](threat-trackers.md#noteworthy-trackers), des [suivis de tendances](threat-trackers.md#trending-trackers),des [requêtes suivies](threat-trackers.md#tracked-queries) et des [requêtes enregistrées](threat-trackers.md#saved-queries).

- **[Threat Explorer (ou détections en temps réel)](threat-explorer.md)** (également appelé Explorer) est un rapport en temps réel qui vous permet d’identifier et d’analyser les menaces récentes. Vous pouvez configurer Explorer pour afficher des données pour les périodes personnalisées.

- **[Simulateur d’attaques](attack-simulator.md)** vous permet d’exécuter des scénarios d’attaques réalistes au sein de votre organisation afin d’identifier les vulnérabilités. Des simulations des types d'attaques actuels sont disponibles, notamment des attaques de récupération des informations d'identification et de connexion par hameçonnage et des attaques par pulvérisation de mots de passe et par mot de passe par force brute.

## <a name="save-time-with-automated-investigation-and-response"></a>Gagner du temps avec l’examen et la réponse automatisé

(**NOUVEAU !**) Lorsque vous effectuez des recherches sur une attaque potentielle de sécurité sur Internet, le temps est essentiel. Plus vous pourrez identifier et atténuer les menaces rapidement, mieux votre organisation se portera. [Examen et réponse automatique aux incidents](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-air) (AIR) inclut un ensemble de règles de sécurité qui peuvent être lancées automatiquement, par exemple lorsqu’une alerte est déclenchée, ou manuellement, par exemple à partir d’un affichage dans Explorer. Réponse automatique aux incidents permet à votre équipe spécialisée dans les opérations de sécurité d’économiser du temps et des efforts pour réduire efficacement les menaces. Pour en savoir plus, voir [Air dans Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-air).

## <a name="permissions-required-to-use-atp-features"></a>Autorisations requises pour utiliser les fonctionnalités ATP

Pour accéder aux fonctionnalités ATP dans le Centre de sécurité et conformité, vous devez disposer d’un rôle approprié. Le tableau ci-après inclut des exemples :

|Rôle ou groupe de rôles|Ressources pour en savoir plus|
|---------|---------|
|Administrateur général (peut être affecté dans Azure Active Directory ou dans le centre de sécurité et conformité) |[À propos des rôles d’administrateur Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles)|
|Administrateur de sécurité (peut être affecté dans Azure Active Directory ou le centre de sécurité et conformité) |[Autorisations des rôles d’administrateur dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles)<br><br/>[Autorisations dans le centre de conformité et de sécurité](permissions-in-the-security-and-compliance-center.md)|
|Gestion de l’organisation Exchange Online (elle est affectée à Exchange Online)|[Autorisations dans Exchange Online](https://docs.microsoft.com/exchange/permissions-exo/permissions-exo)<br><br> [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell)|
|Rechercher et vider (cette opération est attribuée uniquement dans le centre de conformité et sécurité) |[Autorisations dans le Centre de sécurité et de conformité] (permissions-in-the-security-and-compliance-center.md|

Pour en savoir plus, consultez [Autorisations dans le Centre de sécurité et de conformité](permissions-in-the-security-and-compliance-center.md).

## <a name="get-office-365-atp"></a>Obtenir Office 365 ATP – Protection avancée contre les menaces

Office 365 ATP – Protection avancée contre les menaces est inclus dans certains abonnements, tels que Microsoft 365 E5, Office 365 E5, Office 365 A5 et Microsoft 365 Business Premium. Si votre abonnement n’inclut pas Office 365 – Protection avancée contre les menaces, vous pouvez acheter ATP Plan 1 ou ATP Plan 2 en tant que composant additionnel de certains abonnements. Pour en savoir plus, consultez les ressources suivantes :

- [Disponibilité d’Office 365 – Protection avancée contre les menaces](https://docs.microsoft.com/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#office-365-advanced-threat-protection-atp-availability) pour obtenir la liste des abonnements incluant les plans de protection avancée contre les menaces.

- [Disponibilité des fonctionnalités pour les différents plans Protection avancée contre les menaces (ATP)](https://docs.microsoft.com/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans) pour obtenir la liste des fonctionnalités incluses dans les Plans 1 et 2.

- [Obtenir la version appropriée d’Office 365 – Protection avancée contre les menaces](https://products.office.com/exchange/advance-threat-protection#pmg-allup-content) pour comparer les plans et acheter Office 365 ATP – Protection avancée contre les menaces.

- [Démarrez une version d’essai gratuite](https://go.microsoft.com/fwlink/p/?LinkID=698279)

## <a name="new-features-in-office-365-atp"></a>Nouvelles fonctionnalités d’Office 365 – Protection avancée contre les menaces

Les nouvelles fonctionnalités sont ajoutées à Office 365 – Protection avancée contre les menaces en continu. Pour en savoir plus, consultez les ressources suivantes :

- La [Feuille de route Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=advanced%2Cthreat%2Cprotection) fournit la liste des nouvelles fonctionnalités de développement et de déploiement.

- La [Description du service Office 365 – Protection avancée contre les menaces](https://docs.microsoft.com/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#whats-new-in-office-365-advanced-threat-protection-atp) décrit les fonctionnalités et la disponibilité des plans de protection avancée contre les menaces.

## <a name="see-also"></a>Voir aussi

- [Protection Microsoft contre les menaces](../mtp/microsoft-threat-protection.md)

- [Examen et réponses automatisés (AIR) dans Protection Microsoft contre les menaces](../mtp/mtp-autoir.md)
