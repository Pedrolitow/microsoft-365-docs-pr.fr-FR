---
title: Nouveautés de Microsoft 365 Lighthouse
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
ms.reviewer: crimora
audience: Admin
ms.topic: article
ms.service: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- Tier1
- scotvorg
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Pour les fournisseurs de services managés (MSP) utilisant Microsoft 365 Lighthouse, consultez ce qui a été ajouté, modifié et corrigé dans Microsoft 365 Lighthouse chaque mois.
ms.openlocfilehash: 2c63cd304fc8893c5a767212ef540939e9954793
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68735064"
---
# <a name="whats-new-in-microsoft-365-lighthouse"></a>Nouveautés de Microsoft 365 Lighthouse

Nous ajoutons continuellement de nouvelles fonctionnalités à [Microsoft 365 Lighthouse](m365-lighthouse-overview.md), corrigeons les problèmes que nous apprenons et apportons des modifications en fonction de vos commentaires. Consultez cet article pour découvrir ce sur quoi nous avons travaillé.

> [!NOTE]
> Certaines fonctionnalités sont déployées à des vitesses différentes pour nos clients. Si vous ne voyez pas encore de fonctionnalité, vous devriez la voir bientôt.

## <a name="september-2022"></a>Septembre 2022

### <a name="fully-automated-setup-of-microsoft-defender-for-business"></a>Configuration entièrement automatisée de Microsoft Defender pour entreprises

Nous avons ajouté une étape entièrement automatisée à la base de référence par défaut qui vous permet de configurer vos locataires clients avec Microsoft Defender pour entreprises. Cette étape provisionne automatiquement votre locataire pour Microsoft Defender pour entreprises et intègre automatiquement les appareils inscrits Intune à Microsoft Defender pour entreprises.

### <a name="capability-to-filter-the-multifactor-authentication-mfa-list-to-show-relevant-user-accounts"></a>Possibilité de filtrer la liste d’authentification multifacteur (MFA) pour afficher les comptes d’utilisateur pertinents

La page Authentification multifacteur prend désormais en charge le filtrage de la liste des comptes d’utilisateur par type de compte (par exemple, par Administration, membre ou invité). Vous pouvez également exclure d’autres comptes de la liste, comme les comptes de service ou les comptes d’accès d’urgence. Pour accéder à cette fonctionnalité, accédez à **Authentification multifacteur** **des utilisateurs** > , sélectionnez un locataire dans la liste pour ouvrir le volet d’informations du locataire, puis sélectionnez l’onglet **Utilisateurs non inscrits pour l’authentification multifacteur**. Ces fonctionnalités de filtrage et d’exclusion vous aident à vous concentrer sur les comptes d’utilisateur pertinents. 

### <a name="capability-to-act-on-security-incidents-and-alerts"></a>Capacité à agir sur les incidents et les alertes de sécurité

Vous pouvez désormais agir sur les incidents et les alertes affichés sur la page **Incidents et alertes** de **sécurité** >  des appareils. Les actions actuellement prises en charge incluent l’attribution de l’incident ou de l’alerte à vous-même ou la résolution de l’incident ou de l’alerte. 

## <a name="august-2022"></a>Août 2022

### <a name="view-and-manage-inactive-user-accounts"></a>Afficher et gérer les comptes d’utilisateurs inactifs 

Microsoft 365 Lighthouse fournit désormais une liste de tous les comptes d’utilisateur inactifs dans vos locataires gérés. Pour accéder à la liste, sélectionnez **Utilisateurs** > **Utilisateurs Utilisateurs Inactifs** dans le volet de navigation gauche dans Microsoft 365 Lighthouse. Vous pouvez réduire les risques de sécurité en utilisant cette liste pour suivre et nettoyer les comptes qui sont toujours activés, mais qui n’ont pas été utilisés au cours des six derniers mois. 

### <a name="microsoft-edge-policy-deployment"></a>Déploiement de stratégie Microsoft Edge   

Nous avons ajouté une tâche de déploiement de stratégie Microsoft Edge à la base de référence par défaut. Cette tâche de déploiement vous permet de sécuriser les navigateurs de votre locataire client avec les paramètres de sécurité Edge, qui incluent une protection intégrée contre le hameçonnage et les programmes malveillants. Microsoft Edge s’est avéré plus sécurisé que Google Chromium pour les petites et moyennes entreprises disposant d’appareils exécutés Windows 10 ou version ultérieure.

Pour plus d’informations, consultez [Sécurité Microsoft Edge pour votre entreprise](/deployedge/ms-edge-security-for-business).

## <a name="july-2022"></a>Juillet 2022

### <a name="enhanced-baseline-deployment"></a>Déploiement amélioré de la base de référence

Microsoft 365 Lighthouse permet désormais de déployer des bases de référence sur tous vos locataires managés plus rapidement et plus facilement en :

- Détection et signalement automatique de l’état de chaque tâche affectée
- Consolidation des rapports d’état et simplification de la logique qui détermine l’état du déploiement
- Signaler quelles tâches sont terminées et quelles tâches nécessitent votre attention
- Création de rapports sur l’état de déploiement au niveau de l’utilisateur pour les tâches applicables
- Détection des configurations existantes à partir du locataire et comparaison avec la base de référence
- Fournir des détails sur les tâches qui ont été ignorées
- Identification de l’emplacement où des licences supplémentaires sont requises pour effectuer une tâche affectée

## <a name="june-2022"></a>Juin 2022

### <a name="support-for-microsoft-365-e5-customers"></a>Prise en charge des clients Microsoft 365 E5

Nous avons modifié nos exigences d’intégration pour vous permettre d’intégrer Microsoft 365 E5 clients à Microsoft 365 Lighthouse. La liste étendue des licences que Microsoft 365 Lighthouse prend en charge pour l’intégration inclut Microsoft 365 Business Premium, Microsoft 365 E3, Microsoft 365 E5, Microsoft Defender pour entreprises et Windows 365 entreprise. Les clients qui disposent d’au moins l’une de ces licences répondent aux exigences en matière d’autorisations d’accès délégué et ne dépassent pas le nombre maximal d’utilisateurs sous licence peuvent être gérés dans Microsoft 365 Lighthouse.  

Pour obtenir la liste complète des exigences, consultez [Configuration requise pour Microsoft 365 Lighthouse](m365-lighthouse-requirements.md).

### <a name="microsoft-defender-for-business-integration"></a>intégration Microsoft Defender pour entreprises

Microsoft 365 Lighthouse s’intègre désormais à Microsoft Defender pour entreprises pour vous apporter des insights et des fonctionnalités de gestion connexes pour tous vos locataires clients qui ont Microsoft Defender pour entreprises. Pour afficher la liste des appareils clients qui ont été intégrés à Microsoft Defender pour entreprises, sélectionnez **Appareils** dans le volet de navigation gauche de Microsoft 365 Lighthouse. Pour afficher la liste des incidents et des alertes signalés dans vos locataires clients, accédez à **Appareils** > **Sécurité des** appareils, puis sélectionnez l’onglet **Incidents et alertes** .  

Nous avons également ajouté une étape à la base de référence par défaut pour vous aider à configurer Microsoft Defender pour entreprises pour vos locataires clients. Pour voir cette étape, sélectionnez **Lignes de base** dans le volet de navigation gauche de Microsoft 365 Lighthouse ou affichez le plan de déploiement de l’un de vos locataires clients.

### <a name="status-of-quarantined-email-messages"></a>État des messages électroniques mis en quarantaine

Nous avons ajouté de nouvelles fonctionnalités concernant les données de mise en quarantaine des e-mails pour vos locataires gérés. Accessible en sélectionnant **Protection des données** dans le volet de navigation gauche de Microsoft 365 Lighthouse, cette fonctionnalité vous donne une visibilité sur l’état des messages électroniques mis en quarantaine dans vos locataires clients. Vous pouvez voir des informations consolidées sur le nombre total de volumes de quarantaine et des informations détaillées pour chaque locataire géré afin de vous aider à hiérarchiser tous les locataires qui peuvent nécessiter une action.

### <a name="increase-in-maximum-license-limit"></a>Augmentation de la limite maximale de licence

Nous rendons possible la gestion d’un plus grand nombre de vos clients dans Microsoft 365 Lighthouse en augmentant une fois de plus la limite de licence maximale pour l’intégration des clients. Les clients disposant de jusqu’à 2 500 licences utilisateur peuvent désormais être intégrés à Microsoft 365 Lighthouse. Nous continuerons à évaluer cette exigence dans les prochaines versions Microsoft 365 Lighthouse. 

Pour plus d’informations, consultez [Configuration requise pour Microsoft 365 Lighthouse](m365-lighthouse-requirements.md).

## <a name="may-2022"></a>Mai 2022

### <a name="redesigned-left-navigation-pane"></a>Volet de navigation gauche repensé

Nous avons donné au volet de navigation gauche dans Microsoft 365 Lighthouse une nouvelle apparence. Vous remarquerez une conception plus élégante, avec des nœuds de niveau supérieur tels que Locataires, Utilisateurs et Appareils qui s’étendent pour afficher les sous-nœuds associés, tels que les utilisateurs à risque, la conformité des appareils et la gestion des menaces. Ce modèle de navigation s’aligne sur le modèle utilisé par d’autres centres d’administration Microsoft 365.

### <a name="enriched-user-details-pane"></a>Volet d’informations utilisateur enrichi

Nous avons repensé le volet détails de l’utilisateur pour inclure plus d’informations sur l’utilisateur et plus d’actions que vous pouvez effectuer pour mieux gérer les utilisateurs. Il a maintenant la même apparence que le volet d’informations utilisateur dans le Centre d'administration Microsoft 365. Pour accéder au volet d’informations utilisateur dans Microsoft 365 Lighthouse, sélectionnez **Utilisateurs** dans le volet de navigation gauche, puis sélectionnez **Rechercher des utilisateurs** ou **Utilisateurs à risque**. Sélectionnez n’importe quel utilisateur pour ouvrir le volet d’informations.

## <a name="april-2022"></a>Avril 2022

### <a name="delegated-access-type-and-roles-on-tenants-page"></a>Type d’accès délégué et rôles sur la page Locataires

Nous avons mis à jour la page **Locataires** pour répertorier le type d’accès délégué du fournisseur de services managés (MSP) (None, DAP, GDAP ou Both DAP & GDAP) par client sous la colonne **Accès délégué** . Nous avons également ajouté une nouvelle colonne intitulée **Vos rôles** qui répertorie les rôles DAP et GDAP par client pour un utilisateur connecté. Ces deux améliorations apportées à la page Locataires permettront aux **techniciens** MSP de comprendre plus facilement quels types d’autorisations d’administration déléguées sont disponibles pour chaque client et quels rôles délégués leur ont été explicitement accordés.

Pour plus [d’informations, consultez Vue d’ensemble des autorisations dans Microsoft 365 Lighthouse](m365-lighthouse-overview-of-permissions.md).

## <a name="march-2022"></a>Mars 2022

### <a name="windows-365-business-integration-and-management-actions"></a>Windows 365 Affaires actions d’intégration et de gestion

Sur la base des commentaires des utilisateurs, nous avons intégré Windows 365 Affaires dans Microsoft 365 Lighthouse. Cette intégration vous aidera à gérer et à surveiller tous les PC cloud de vos clients à partir d’un emplacement unique. 

En plus de l’intégration à Windows 365 Affaires PC cloud dans Microsoft 365 Lighthouse, vous pouvez désormais effectuer les actions de gestion suivantes :

- Redémarrer
- Reprovisionner
- Renommer
 
Pour en savoir plus sur les nouvelles fonctionnalités, consultez [Vue d’ensemble de la page Windows 365 (PC cloud) dans Microsoft 365 Lighthouse](m365-lighthouse-win365-page-overview.md).

### <a name="microsoft-365-lighthouse-partner-amendment"></a>avenant Microsoft 365 Lighthouse partenaire

Maintenant que Microsoft 365 Lighthouse est en disponibilité générale, nous demandons à nos partenaires actuels de signer un avenant de partenaire Microsoft 365 Lighthouse mis à jour. Tous les partenaires Microsoft 365 Lighthouse qui se sont inscrits pendant la période de préversion seront invités à terminer ce nouvel accord dans les semaines à venir. L’achèvement nécessite des droits d’administrateur général dans le locataire partenaire et doit être effectué dans les 90 jours pour continuer à accéder au portail Microsoft 365 Lighthouse.

## <a name="february-2022"></a>Février 2022

### <a name="granular-delegated-access-permissions-gdap-roles"></a>Rôles GDAP (Granular Delegated Access Permissions)

Microsoft 365 Lighthouse inclut désormais la possibilité pour les msp d’utiliser des rôles GDAP (Granular Delegated Administration Privileges). Avec la dernière mise à jour, les msp peuvent tirer parti des rôles GDAP pour leurs techniciens qui activent le principe de l’accès avec privilège minimum dans Microsoft 365 Lighthouse. Cette fonctionnalité réduit les risques inhérents aux autorisations étendues du rôle DAP (Delegated Access Permissions) de l’agent Administration en activant des contrôles granulaires sur les données et les paramètres des clients avec lesquels chaque technicien sera en mesure de travailler.

Pour en savoir plus sur GDAP dans Microsoft 365 Lighthouse, consultez [Configurer Microsoft 365 Lighthouse sécurité du portail](m365-lighthouse-configure-portal-security.md).

### <a name="capability-to-notify-users-to-act-on-noncompliant-devices"></a>Possibilité d’informer les utilisateurs d’agir sur des appareils non conformes

Dans le cadre de l’étape de base de référence de conformité des appareils, nous avons ajouté la possibilité d’informer les utilisateurs d’un locataire client d’agir sur des appareils non conformes. Avec cette modification, une fois que vous avez appliqué l’étape de déploiement de conformité de l’appareil pour un locataire client, la stratégie de conformité de l’appareil créée dans ce locataire envoie automatiquement une notification aux utilisateurs lorsque leur appareil devient non conforme, leur rappelant de prendre les mesures appropriées pour rétablir la conformité de l’appareil.

### <a name="deployment-validation-and-reporting"></a>Validation et création de rapports de déploiement

Microsoft 365 Lighthouse pouvez désormais tester les configurations de locataire pour les étapes de déploiement avec des stratégies d’accès conditionnel.  

Cette nouvelle fonctionnalité détecte les stratégies existantes au sein des locataires clients que vous gérez et les compare à votre plan de déploiement. Microsoft 365 Lighthouse fournit ensuite des désignations d’état pour les étapes de déploiement et les processus d’étape de déploiement pour vous aider à comprendre quels processus de déploiement ont déjà été effectués, quels sont ceux qui doivent être traités et où les paramètres prescrits par le plan de déploiement sont égaux, manquants ou en conflit avec les paramètres inclus dans les stratégies existantes. La connaissance de ces informations rend l’identification, la hiérarchisation et la résolution des conflits de stratégie plus rapides, plus faciles et plus efficaces.

### <a name="deployment-step-to-configure-microsoft-defender-firewall"></a>Étape de déploiement pour configurer Microsoft Defender Pare-feu

Microsoft 365 Lighthouse a ajouté l’étape Configurer le déploiement du pare-feu Microsoft Defender à sa base de référence par défaut. Cette étape permet aux msp de sécuriser les appareils clients via la configuration de pare-feu par défaut pour les appareils Windows 10 (et versions ultérieures). Microsoft Defender Pare-feu bloque le trafic réseau non autorisé entrant ou sortant des appareils clients et réduit le risque de menaces de sécurité réseau. Une fonctionnalité de règles de pare-feu Microsoft Defender est en cours de développement.

Microsoft Defender Pare-feu est activé par défaut sur les appareils Windows 10 (et versions ultérieures). Si ce n’est pas configuré pour votre locataire client, procédez comme suit :

1. Dans la page **Locataires** de Microsoft 365 Lighthouse, sélectionnez le locataire client pour ouvrir la page **Vue d’ensemble** du locataire.
2. Sélectionnez l’onglet **Plan de déploiement** .
3. Dans la liste des étapes de déploiement, sélectionnez **Configurer Microsoft Defender Pare-feu**.
4. Sélectionnez **Vérifier et déployer** pour déployer cette configuration sur le locataire du client. 

### <a name="increase-in-maximum-license-limit"></a>Augmentation de la limite maximale de licence

Nous rendons possible la gestion d’un plus grand nombre de vos clients dans Microsoft 365 Lighthouse en augmentant la limite de licence maximale pour l’intégration des clients. Les clients disposant de jusqu’à 1 000 licences utilisateur peuvent désormais être intégrés à Microsoft 365 Lighthouse. Nous continuerons à évaluer cette exigence dans les prochaines versions Microsoft 365 Lighthouse.

Pour plus d’informations, consultez [Configuration requise pour Microsoft 365 Lighthouse](m365-lighthouse-requirements.md).

### <a name="support-for-advisor-customers"></a>Support pour les clients advisor

Nous avons modifié nos exigences d’intégration pour permettre aux locataires clients existants avec des relations de conseiller d’être intégrés à Microsoft 365 Lighthouse. Les clients avec des contrats de revendeur et de conseiller peuvent désormais être dans Microsoft 365 Lighthouse s’ils répondent aux exigences en matière d’autorisations d’accès délégué, disposent des licences requises et ne dépassent pas le nombre maximal d’utilisateurs.

Pour plus d’informations, consultez [Configuration requise pour Microsoft 365 Lighthouse](m365-lighthouse-requirements.md).

## <a name="january-2022"></a>Janvier 2022

### <a name="capability-to-view-audit-logs-in-microsoft-365-lighthouse"></a>Possibilité d’afficher les journaux d’audit dans Microsoft 365 Lighthouse

Microsoft 365 Lighthouse inclut désormais la possibilité d’afficher les journaux d’audit. Vous pouvez passer en revue les actions passées pour trouver des configurations incorrectes et des actions risquées pour la correction, prendre en charge les processus et les enquêtes de sécurité, former les employés et répondre aux exigences de conformité et d’audit. Avec la dernière mise à jour, vous pouvez :

- Affichez les journaux d’audit pour voir toutes les actions effectuées dans Microsoft 365 Lighthouse, y compris ce qui a changé dans quel locataire du client, quand il a été modifié et qui l’a modifié.
- Recherchez et filtrez les journaux d’audit pour trouver des informations spécifiques.
- Exportez les journaux pour pouvoir les analyser et les conserver.
 
Dans le volet de navigation gauche de Microsoft 365 Lighthouse, sélectionnez **Journaux d’audit**. Vous pouvez également [accéder directement à la page Journaux d’audit maintenant](https://lighthouse.microsoft.com/#blade/Microsoft_Intune_MTM/Audit.ReactView) pour l’extraire.

## <a name="november-2021"></a>Novembre 2021

### <a name="microsoft-365-services-usage-data"></a>Données d’utilisation des services Microsoft 365

Vous pouvez désormais afficher les données d’utilisation des services Microsoft 365 à partir de Microsoft 365 Lighthouse. Comprendre comment les clients utilisent leurs services Microsoft 365 est essentiel pour les aider à tirer le meilleur parti de leurs investissements informatiques. Au lieu d’utiliser plusieurs ressources pour afficher des informations sur les différents services de productivité, de sécurité et de conformité de vos clients, Microsoft 365 Lighthouse les regroupe en une seule vue simple et puissante.  

Ces insights peuvent vous aider à informer vos engagements clients et à fournir plus de valeur à vos clients en les aidant à comprendre quels services leurs utilisateurs utilisent activement et où il peut y avoir des opportunités d’améliorer leur sécurité ou leur productivité. 

Pour plus d’informations, consultez [Vue d’ensemble de la page Locataires dans Microsoft 365 Lighthouse section Utilisation des services Microsoft 365](m365-lighthouse-tenants-page-overview.md#microsoft-365-services-usage-section).

### <a name="exchange-online-protection-and-microsoft-365-defender-for-office-365-default-baseline-step"></a>Exchange Online Protection et Microsoft 365 Defender pour Office 365 étape de référence par défaut

Nous avons ajouté une nouvelle étape à la base de référence par défaut pour inclure des conseils pour l’activation des stratégies de sécurité pour Exchange Online Protection (EOP) et Microsoft Defender pour Office 365 (MDO). EOP et MDO aident à protéger les utilisateurs contre le courrier indésirable, le hameçonnage et les logiciels malveillants en envoyant les e-mails au dossier de mise en quarantaine ou de courrier indésirable de l’utilisateur (bientôt disponible). Le plan de déploiement vous guide dans la configuration d’EOP et MDO, ce qui étend votre position de sécurité lors de votre prochaine révision du plan de déploiement client.

### <a name="default-tenant-tags"></a>Balises de locataire par défaut

Vous pouvez désormais désigner certaines **étiquettes** de locataire comme balises par *défaut* dans le volet **Gérer les étiquettes** de la page Locataires. Ainsi, la prochaine fois que vous vous connectez à Microsoft 365 Lighthouse, toutes vos vues et insights seront filtrés par défaut pour afficher uniquement les locataires qui ont une balise par défaut. Les balises par défaut peuvent vous aider à vous concentrer sur les insights pour les locataires clients à priorité élevée.

## <a name="october-2021"></a>Octobre 2021

### <a name="capability-to-filter-by-multiple-tenant-tags"></a>Possibilité de filtrer par plusieurs balises de locataire

Il est désormais possible de filtrer les données par plusieurs balises de locataire en même temps. Cette fonctionnalité peut vous aider à filtrer plus facilement les vues et les insights existants disponibles dans Microsoft 365 Lighthouse pour afficher les locataires clients pertinents.

### <a name="capability-to-assign-baseline-configurations-to-specific-azure-active-directory-groups"></a>Possibilité d’affecter des configurations de base à des groupes Azure Active Directory spécifiques

Nous avons ajouté la possibilité d’affecter des configurations de base à des groupes Azure Active Directory (Azure AD) spécifiques de vos locataires clients à partir de Microsoft 365 Lighthouse. À partir de n’importe quelle page d’étape de déploiement, parcourez et sélectionnez les groupes Azure AD spécifiques que vous souhaitez inclure ou exclure, puis déployez les configurations sur votre locataire client.

### <a name="improvements-to-risky-users-page"></a>Page Améliorations apportées aux utilisateurs à risque

Vous pouvez désormais facilement afficher et comprendre les raisons du risque d’un utilisateur à partir de Microsoft 365 Lighthouse. Dans le volet de navigation gauche de Microsoft 365 Lighthouse, sélectionnez **Utilisateurs**, puis sélectionnez l’onglet **Utilisateurs à** risque. Sélectionnez **Afficher les détections de risques** dans la colonne **Détails** pour tout utilisateur. À partir de là, vous pouvez passer en revue les détails du risque, puis sélectionner **Confirmer la compromission de l’utilisateur** ou **Ignorer le risque utilisateur**. Vous pouvez également confirmer ou ignorer un risque pour plusieurs utilisateurs en même temps à partir de la page **Utilisateurs à risque** . La possibilité d’ignorer le risque d’un utilisateur peut être utile lorsque la réinitialisation du mot de passe n’est pas une option ou si vous pensez que l’utilisateur affecté n’est plus en danger.

### <a name="capability-to-provide-feedback-on-microsoft-365-lighthouse"></a>Possibilité de fournir des commentaires sur Microsoft 365 Lighthouse

Vos commentaires sont importants et sont importants pour nous. Nous avons donc ajouté de nouvelles fonctionnalités de commentaires qui vous invitent occasionnellement (pas plus d’une fois par mois) à fournir des commentaires. Vous pouvez également fournir des commentaires à tout moment en sélectionnant l’icône de commentaires dans le coin supérieur droit de Microsoft 365 Lighthouse.

## <a name="september-2021"></a>Septembre 2021

### <a name="tenant-filter-changes"></a>Modifications du filtre de locataire

Nous avons apporté des modifications à l’expérience de filtrage des locataires pour vous aider à afficher et à gérer rapidement les locataires et les étiquettes à partir de n’importe quelle page dans Microsoft 365 Lighthouse. Sélectionnez le filtre **Locataires** en haut d’une page, puis recherchez ou entrez le nom du locataire ou de la balise par lequel vous souhaitez filtrer.

## <a name="august-2021"></a>Août 2021

### <a name="in-product-email-workflows-to-communicate-with-users"></a>Flux de travail de messagerie dans le produit pour communiquer avec les utilisateurs 

Nous avons facilité la communication avec les utilisateurs de vos locataires clients sur les actions qu’ils doivent effectuer. Dans la liste des utilisateurs non inscrits pour l’authentification multifacteur (MFA) ou la réinitialisation de mot de passe en libre-service, vous pouvez désormais sélectionner un ou plusieurs utilisateurs et leur envoyer un e-mail à l’aide d’un modèle d’e-mail téléchargeable.

### <a name="capability-to-take-action-on-noncompliant-devices"></a>Possibilité d’agir sur des appareils non conformes

Nous avons introduit la possibilité de synchroniser ou de redémarrer un ou plusieurs appareils sur plusieurs locataires clients. Cette fonctionnalité permet de s’assurer que les appareils de vos clients sont protégés contre les risques. Pour découvrir cette fonctionnalité, sélectionnez **Appareils** dans le volet de navigation gauche de Microsoft 365 Lighthouse, puis sélectionnez l’onglet **Appareils**. Recherchez les options **Synchroniser** et **redémarrer** au-dessus de la liste des appareils. Vous pouvez également accéder à ces options à partir du volet d’informations de l’appareil de n’importe quel appareil.

### <a name="capability-to-monitor-and-manage-windows-365-cloud-pcs"></a>Possibilité de surveiller et de gérer Windows 365 PC cloud

Nous avons ajouté la possibilité de surveiller les connexions locales et de provisionner et de gérer Windows 365 PC cloud sur tous vos locataires clients. La nouvelle page **Windows 365** fournit des informations détaillées sur tous les PC cloud de vos locataires dans un emplacement pratique. 

### <a name="support-for-microsoft-365-e3-customers"></a>Prise en charge des clients Microsoft 365 E3

Nous avons modifié nos exigences d’intégration pour vous permettre d’intégrer Microsoft 365 E3 clients à Microsoft 365 Lighthouse. Pour pouvoir être géré dans Microsoft 365 Lighthouse, chaque client doit répondre aux exigences suivantes :

- L’accès délégué doit être configuré pour que le MSP puisse gérer le locataire du client
- Doit avoir au moins une licence Microsoft 365 Business Premium ou Microsoft 365 E3
- Ne doit pas avoir plus de 500 utilisateurs sous licence

Pour plus d’informations sur la configuration requise, consultez [Configuration requise pour Microsoft 365 Lighthouse](m365-lighthouse-requirements.md).

## <a name="june-2021"></a>Juin 2021

### <a name="capability-to-add-custom-tags-to-customer-tenants"></a>Possibilité d’ajouter des étiquettes personnalisées aux locataires clients

Vous pouvez maintenant créer et appliquer des étiquettes personnalisées aux locataires clients que vous gérez dans Microsoft 365 Lighthouse. Utilisez ces balises pour vous aider à organiser vos locataires, ou utilisez-les pour filtrer plus facilement votre liste de locataires afin d’afficher des insights pour les ensembles de locataires clients pertinents. 

### <a name="baselines-to-standardize-your-customer-tenant-deployments"></a>Bases de référence pour normaliser les déploiements de locataire client

Avec la nouvelle fonctionnalité de bases de référence, vous pouvez désormais déployer des configurations standard pour sécuriser les utilisateurs, les appareils et les données dans les locataires des clients. La base de référence par défaut contient actuellement les étapes de déploiement suivantes (d’autres seront bientôt disponibles) : 

- Exiger l’authentification multifacteur pour les administrateurs 
- Exiger l’authentification multifacteur pour les utilisateurs 
- Bloquer l’authentification héritée 
- Inscrire des appareils Windows dans Microsoft Endpoint Manager – Azure AD Join 
- Configurer la stratégie Defender AV pour les appareils Windows 
- Configurer la stratégie de conformité pour les appareils Windows 

Pour suivre ces étapes de déploiement, sélectionnez **Locataires** dans le volet de navigation gauche de Microsoft 365 Lighthouse, sélectionnez un locataire dans la liste des locataires, puis sélectionnez l’onglet **Plan de déploiement** . 

## <a name="may-2021"></a>Mai 2021

### <a name="enhancements-to-tenants-page"></a>Page Améliorations apportées aux locataires

Nous avons apporté les améliorations suivantes à la page **Locataires** :

- Ajout d’une liste de nombres totaux par problème en haut de la page 
- Possibilité de pointer sur un état dans la colonne **État** de la liste des locataires pour afficher les détails de la restriction 
- Amélioration des étiquettes d’état