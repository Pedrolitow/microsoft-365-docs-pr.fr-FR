---
title: À propos de l’essai Microsoft Defender pour Office 365
f1.keywords: ''
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: overview
ms.prod: m365-security
ms.technology: mdo
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
ROBOTS: NOINDEX, NOFOLLOW
description: Les administrateurs peuvent en savoir plus sur le mode d’essai de Microsoft Defender pour Office 365
ms.openlocfilehash: 9cce1e910f5497ce2dfe265923f66e87306fb90e
ms.sourcegitcommit: fa90763559239c4c46c5e848939126763879d8e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/13/2022
ms.locfileid: "66773254"
---
# <a name="about-the-microsoft-defender-for-office-365-trial"></a>À propos de l’essai Microsoft Defender pour Office 365

> [!IMPORTANT]
> Commencez rapidement avec notre [playbook d’évaluation](trial-playbook-defender-for-office-365.md) facile à utiliser pour Microsoft Defender pour Office 365. Ce playbook vous aidera à tirer le meilleur parti de votre version d’évaluation gratuite en vous montrant comment protéger votre organisation avec Microsoft Defender pour Office 365.

Microsoft Defender pour Office 365 protège votre organisation contre les menaces malveillantes qui sont posées par les e-mails, les liens (URL) et les outils de collaboration. Defender pour Office 365 inclut :

- **Stratégies de protection contre les menaces** : définissez des stratégies de protection contre les menaces pour définir le niveau de protection approprié pour votre organisation.
- **Rapports** : affichez des rapports en temps réel pour surveiller les performances de Defender pour Office 365 dans votre organisation.
- **Fonctionnalités de recherche et de réponse aux menaces** : utilisez des outils de pointe pour étudier, comprendre, simuler et prévenir les menaces.
- **Fonctionnalités automatisées d’investigation et de réponse** : gagnez du temps pour investiguer et atténuer les menaces.

Une version d’évaluation Microsoft Defender pour Office 365 est un moyen simple de tester les fonctionnalités de Defender pour Office 365 Plan 2 gratuitement, après seulement quelques clics. Ces fonctionnalités de haut niveau sont décrites dans le tableau suivant :

|Fonctionnalité|Description|
|---|---|
|[Paramètres exclusifs dans les stratégies anti-hameçonnage](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)|Obtenez la protection de l’emprunt d’identité utilisateur, la protection de l’emprunt d’identité de domaine, l’intelligence de boîte aux lettres et les seuils avancés de hameçonnage.|
|[Pièces jointes fiables](safe-attachments.md)|Inspectez les pièces jointes et autres fichiers dans un environnement de détonation contrôlé pour intercepter les programmes malveillants nouveaux et évasifs.|
|[Liens fiables](safe-links.md)|Effectuez des vérifications du temps de clic pour vous assurer que les URL susceptibles d’avoir réussi l’inspection initiale n’ont pas été armées.|
|[Suivis des menaces](threat-trackers.md)<sup>\*</sup>|Utilisez des widgets et des vues informatifs pour identifier les problèmes de cybersécurité susceptibles d’avoir un impact sur votre organisation.|
|[Explorateur de menaces](threat-explorer.md)<sup>\*</sup>|Recherchez des informations en quasi temps réel sur les menaces dans votre e-mail Office 365.|
|[Investigation et réponse automatisées (AIR)](office-365-air.md)<sup>\*</sup>|Localisez et corrigez automatiquement les objets de menace à mesure que des alertes sont déclenchées.|
|[Formation à la simulation d’attaque](attack-simulation-training.md)<sup>\*</sup>|Formez vos utilisateurs pour identifier les attaques par hameçonnage et répondre de manière appropriée.|
|[Vues de campagne](campaigns.md)<sup>\*</sup>|Examinez et répondez à une activité de messagerie malveillante à grande échelle.|
|[Rapports utilisant des fonctionnalités de Defender pour Office 365](view-reports-for-mdo.md)|Affichez des rapports, notamment l’état de la protection contre les menaces, la protection contre les menaces d’URL, la latence du courrier, etc.|
|[Protection de compte prioritaire](/microsoft-365/admin/setup/priority-accounts)<sup>\*</sup>|Les utilisateurs que vous identifiez en tant que comptes Priority sont marqués dans les alertes, les rapports et les enquêtes afin qu’ils se distinguent. Vous pouvez également utiliser la balise Priority dans les filtres.|

<sup>\*</sup>Cette fonctionnalité est exclusive à Defender pour Office 365 Plan 2.

## <a name="set-up-a-defender-for-office-365-trial"></a>Configurer une version d’évaluation Defender pour Office 365

Une version d’évaluation permet aux organisations de configurer et de configurer facilement les fonctionnalités de Defender pour Office 365. Pendant l’installation, les stratégies qui sont exclusives aux Defender pour Office 365 (en particulier, [les pièces jointes sécurisées pour les messages électroniques, les liens](safe-attachments.md) [sécurisés pour les messages électroniques et Microsoft Teams](safe-links.md), et la protection de l’emprunt d’identité [dans les stratégies anti-hameçonnage](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)) sont appliquées à l’aide du modèle Standard pour les [stratégies de sécurité prédéfinies](preset-security-policies.md).

Par défaut, ces stratégies sont étendues à tous les utilisateurs de l’organisation, mais pendant ou après la configuration de la version d’évaluation, vous pouvez modifier l’attribution de stratégie à des utilisateurs spécifiques.

> [!NOTE]
> Vos stratégies anti-courrier indésirable existantes sont probablement configurées avec le **dossier Déplacer le message vers le courrier indésirable Email** pour le verdict de courrier indésirable à haut niveau de confiance dans les stratégies anti-courrier indésirable. Le modèle Standard pour les stratégies de sécurité prédéfinies utilise le **message de mise en quarantaine** de l’action pour le courrier indésirable à haut niveau de confiance, et les stratégies de sécurité prédéfinies sont toujours appliquées avant les stratégies anti-courrier indésirable personnalisées ou la stratégie anti-courrier indésirable par défaut. Pour plus d’informations sur les paramètres par défaut, Standard et Strict, consultez [Paramètres recommandés pour EOP et Microsoft Defender pour Office 365 sécurité](recommended-settings-for-eop-and-office365.md).

D’autres charges de travail sont également disponibles pour la protection (par exemple, [pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams](mdo-for-spo-odb-and-teams.md) et [liens sécurisés pour les applications Office prises en charge](safe-links.md#safe-links-settings-for-office-apps).

Pendant la configuration de l’essai, la fonctionnalité de réponse qui est exclusive à Defender pour Office 365 Plan 2 (par exemple, [AIR](office-365-air.md) et [l’Explorateur de menaces](threat-explorer.md) est également configurée pour l’ensemble de l’organisation. Aucune étendue de stratégie n’est requise.

## <a name="licensing"></a>Licences

Dans le cadre de la configuration de l’essai, les licences Defender pour Office 365 sont automatiquement appliquées à l’organisation. Les licences sont gratuites pendant les 90 premiers jours.

La carte de licence pour l’essai affiche les informations suivantes :

:::image type="content" source="../../media/mdo-trial-licensing-card.png" alt-text="La carte de licence dans la version d’évaluation Microsoft Defender pour Office 365" lightbox="../../media/mdo-trial-licensing-card.png":::

- **Section Type d’utilisation** :
  - **Version d’évaluation** : nombre de licences d’essai Defender pour Office 365 disponibles pour vous.

    > [!NOTE]
    > Dans d’autres emplacements, vous pouvez voir la valeur 300 pour le nombre de licences d’évaluation disponibles. Cette valeur est incorrecte (sauf si votre organisation compte exactement 300 utilisateurs). Le nombre de licences d’évaluation disponibles correspond à la taille de votre organisation, et non à la valeur arbitraire 300.

  - **Payé** : nombre de licences Defender pour Office 365 payantes (le cas échéant).

- **Section Utilisation** : nombre d’utilisateurs couverts par Defender pour Office 365 stratégies.
  - **Détection & réponse uniquement** : nombre total d’utilisateurs inclus dans les scénarios suivants :
    - Pendant la version d’évaluation, vous avez étendu les stratégies à des utilisateurs spécifiques.
    - Vous avez des stratégies personnalisées qui sont limitées à des utilisateurs spécifiques.
  - **Protection complète** : nombre total d’utilisateurs protégés par Defender pour Office 365 fonctionnalités du plan 2 (AIR, Explorateur de menaces, entraînement de simulation d’attaque, etc.).

Pour plus d’informations sur la tarification, consultez [Microsoft Defender pour Office 365](https://www.microsoft.com/security/business/siem-and-xdr/microsoft-defender-office-365).

## <a name="permissions"></a>Autorisations

Pour démarrer ou mettre fin à la version d’évaluation, vous devez être membre des rôles **Administrateur général** ou **Administrateur de sécurité** dans Azure Active Directory. Pour plus d’informations, voir [à propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md)

## <a name="additional-information"></a>Informations supplémentaires

Une fois la version d’évaluation démarrée, la disponibilité des modifications et des mises à jour peut prendre jusqu’à 2 heures. De plus, les administrateurs doivent se déconnecter et se reconnecter pour voir les modifications.

## <a name="availability"></a>Disponibilité

La version d’évaluation Defender pour Office 365 est progressivement déployée pour les clients existants qui répondent à des critères spécifiques et qui n’ont pas de licences Defender pour Office 365 Plan 2 existantes (incluses dans leur abonnement ou en tant que module complémentaire).

## <a name="terms-and-conditions"></a>Conditions générales

Pour plus d’informations, consultez [Microsoft Defender pour Office 365 conditions d’évaluation &](defender-for-office-365-trial-terms-and-conditions.md) conditions.

## <a name="frequently-asked-questions"></a>Foire aux questions

### <a name="q-how-do-i-extend-the-trial"></a>Q : Comment faire prolonger l’essai?

R : Consultez [Étendre votre version d’évaluation](/microsoft-365/commerce/try-or-buy-microsoft-365#extend-your-trial).

### <a name="q-what-happens-to-my-data-after-the-trial-expires"></a>Q : Qu’advient-il de mes données après l’expiration de la version d’évaluation ?

R : Une fois votre version d’évaluation expirée, vous aurez accès à vos données d’évaluation (données des fonctionnalités de Defender pour Office 365 que vous n’ayez pas précédemment) pendant 30 jours. Après cette période de 30 jours, toutes les stratégies et données associées à l’essai Defender pour Office 365 sont supprimées.

### <a name="q-how-many-times-can-i-use-the-defender-for-office-365-trial-in-my-organization"></a>Q : Combien de fois puis-je utiliser la version d’évaluation Defender pour Office 365 dans mon organisation ?

R : Un maximum de 2 fois. Si votre premier essai expire, vous devez attendre au moins 30 jours après la date d’expiration avant de pouvoir vous inscrire à nouveau à l’essai Defender pour Office 365. Après votre deuxième essai, vous ne pouvez pas vous inscrire à une autre version d’évaluation.

## <a name="learn-more-about-defender-for-office-365"></a>En savoir plus sur Defender pour Office 365

Defender pour Office 365 aide les organisations à sécuriser leur entreprise en offrant une gamme complète de fonctionnalités.

Vous pouvez également en savoir plus sur Defender pour Office 365 dans ce [guide interactif](https://aka.ms/MS365D.InteractiveGuide).

:::image type="content" source="../../media/microsoft-defender-for-office-365.png" alt-text="Diagramme conceptuel Microsoft Defender pour Office 365" lightbox="../../media/microsoft-defender-for-office-365.png":::

### <a name="prevention"></a>Prévention

Une pile de filtrage robuste empêche un large éventail d’attaques basées sur le volume et ciblées, notamment la compromission des e-mails professionnels, le hameçonnage des informations d’identification, les ransomware et les programmes malveillants avancés.

- [Stratégies anti-hameçonnage : paramètres exclusifs dans Defender pour Office 365](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
- [Pièces jointes fiables](safe-attachments.md)
- [Liens fiables](safe-links.md)

### <a name="detection"></a>Détection

L’IA de pointe détecte le contenu malveillant et suspect et met en corrélation les modèles d’attaque pour identifier les campagnes conçues pour échapper à la protection.

- [Affichages des campagnes dans Microsoft Defender pour Office 365](campaigns.md)

### <a name="investigation-and-hunting"></a>Investigation et chasse

Les expériences puissantes permettent d’identifier, de hiérarchiser et d’examiner les menaces, avec des fonctionnalités de chasse avancées pour suivre les attaques dans Office 365.

- [Explorateur de menaces et détections en temps réel](threat-explorer.md)
- [Rapports en temps réel dans Defender pour Office 365](view-reports-for-mdo.md)
- [Suivis des menaces - Nouveaux et remarquables](threat-trackers.md)
- Intégration à [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

### <a name="response-and-remediation"></a>Réponse et correction

Les fonctionnalités étendues de réponse aux incidents et d’automatisation améliorent l’efficacité et l’efficacité de votre équipe de sécurité.

- [Investigation et réponse automatisées (AIR) dans Microsoft Defender pour Office 365](office-365-air.md)

### <a name="awareness-and-training"></a>Sensibilisation et formation

Des fonctionnalités de simulation et d’entraînement enrichies, ainsi que des expériences intégrées dans les applications clientes, sensibilisent les utilisateurs.

- [Commencer à utiliser la formation à la simulation d’attaque](attack-simulation-training-get-started.md)

### <a name="security-posture"></a>Posture de sécurité

Les modèles recommandés et les insights de configuration aident les clients à obtenir et à rester sécurisés.

- [Stratégies de sécurité prédéfini dans EOP et Microsoft Defender pour Office 365](preset-security-policies.md)
- [Analyseur de configuration pour les stratégies de protection dans EOP et Microsoft Defender pour Office 365](configuration-analyzer-for-security-policies.md).

## <a name="give-feedback"></a>Envoyer des commentaires

Vos commentaires nous aident à mieux protéger votre environnement contre les attaques avancées. Partagez votre expérience et vos impressions sur les fonctionnalités du produit et les résultats de l’essai.
