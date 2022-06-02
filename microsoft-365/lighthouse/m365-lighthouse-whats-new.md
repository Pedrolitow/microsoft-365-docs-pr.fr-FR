---
title: Nouveautés de Microsoft 365 Lighthouse
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: crimora
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Pour les fournisseurs de services gérés (MSP) qui utilisent Microsoft 365 Lighthouse, consultez les éléments ajoutés, modifiés et corrigés dans Microsoft 365 Lighthouse chaque mois.
ms.openlocfilehash: 917c9bcf3629385d1440acc5205507b378da274b
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2022
ms.locfileid: "65840508"
---
# <a name="whats-new-in-microsoft-365-lighthouse"></a>Nouveautés de Microsoft 365 Lighthouse

Nous ajoutons continuellement de nouvelles fonctionnalités à [Microsoft 365 Lighthouse](m365-lighthouse-overview.md), corrigeons les problèmes que nous apprenons et apportons des modifications en fonction de vos commentaires. Passez en revue cet article pour découvrir ce sur quoi nous avons travaillé.

> [!NOTE]
> Certaines fonctionnalités sont déployées à différentes vitesses pour nos clients. Si vous ne voyez pas encore de fonctionnalité, vous devriez la voir bientôt.

## <a name="may-2022"></a>Mai 2022

### <a name="redesigned-left-navigation-pane"></a>Volet de navigation gauche repensé

Nous avons donné une nouvelle apparence au volet de navigation gauche dans Microsoft 365 Lighthouse. Vous remarquerez une conception plus épurée, avec des nœuds de niveau supérieur tels que les locataires, les utilisateurs et les appareils qui s’étendent pour afficher les sous-nœuds associés, tels que les utilisateurs à risque, la conformité des appareils et la gestion des menaces. Ce modèle de navigation s’aligne sur le modèle utilisé par d’autres centres d’administration Microsoft 365.

### <a name="enriched-user-details-pane"></a>Volet Des détails utilisateur enrichis

Nous avons repensé le volet d’informations utilisateur pour inclure plus d’informations utilisateur et d’autres actions que vous pouvez effectuer pour mieux gérer les utilisateurs. Il a maintenant la même apparence que le volet des détails de l’utilisateur dans le Centre d'administration Microsoft 365. Pour accéder au volet d’informations utilisateur dans Microsoft 365 Lighthouse, sélectionnez **Utilisateurs** dans le volet de navigation gauche, puis sélectionnez **Rechercher des utilisateurs** ou **Utilisateurs à risque**. Sélectionnez n’importe quel utilisateur pour ouvrir le volet d’informations.

## <a name="april-2022"></a>Avril 2022

### <a name="delegated-access-type-and-roles-on-tenants-page"></a>Type d’accès délégué et rôles sur la page Locataires

Nous avons mis à jour la page **Locataires** pour répertorier le type d’accès délégué du fournisseur de services managés (MSP) (None, DAP, GDAP ou Both DAP & GDAP) par client sous la colonne **d’accès délégué** . Nous avons également ajouté une nouvelle colonne intitulée **Vos rôles** qui répertorie les rôles DAP et GDAP par client pour un utilisateur connecté. Ces deux améliorations apportées à la page Locataires permettront aux **techniciens** partenaires de comprendre plus facilement quels types d’autorisations administratives déléguées sont disponibles pour chaque client et quels rôles délégués leur ont été explicitement accordés.

Pour en savoir plus, consultez [Vue d’ensemble des autorisations dans Microsoft 365 Lighthouse](m365-lighthouse-overview-of-permissions.md).

## <a name="march-2022"></a>Mars 2022

### <a name="windows-365-business-integration-and-management-actions"></a>Windows 365 Affaires actions d’intégration et de gestion

En fonction des commentaires des utilisateurs, nous avons intégré l’édition Windows 365 Affaires à Microsoft 365 Lighthouse. Cela vous aidera à gérer et à surveiller tous les PC cloud de vos clients à partir d’un emplacement unique. 

En plus de l’intégration à Windows 365 Affaires PC cloud dans Microsoft 365 Lighthouse, vous pouvez désormais effectuer les actions de gestion suivantes :

- Redémarrer
- Reprovisionner
- Renommer
 
Pour en savoir plus sur les nouvelles fonctionnalités, consultez [vue d’ensemble de la page Windows 365 (PC cloud) dans Microsoft 365 Lighthouse](m365-lighthouse-win365-page-overview.md).

### <a name="microsoft-365-lighthouse-partner-amendment"></a>Microsoft 365 Lighthouse modification du partenaire

Maintenant que Microsoft 365 Lighthouse est en disponibilité générale, nous demandons à nos partenaires actuels de signer une modification mise à jour Microsoft 365 Lighthouse partenaire. Tous les Microsoft 365 Lighthouse partenaires qui se sont inscrits au cours de la période de préversion seront invités à conclure ce nouvel accord dans les prochaines semaines. La saisie semi-automatique nécessite des droits d’administrateur général dans le locataire partenaire et doit être effectuée dans les 90 jours pour continuer à accéder au portail Microsoft 365 Lighthouse.

## <a name="february-2022"></a>Février 2022

### <a name="granular-delegated-access-permissions-gdap-roles"></a>Rôles d’autorisations d’accès délégué granulaires (GDAP)

Microsoft 365 Lighthouse inclut désormais la possibilité pour les MSP d’utiliser des rôles GDAP (Granular Delegated Access Permissions). Avec la dernière mise à jour, les MSP peuvent tirer parti des rôles GDAP pour leurs techniciens qui activent le principe de l’accès aux privilèges minimum dans Microsoft 365 Lighthouse. Cette fonctionnalité réduit les risques inhérents aux autorisations étendues du rôle DAP (Delegated Access Permissions) de l’agent Administration en activant des contrôles granulaires sur les données et les paramètres des clients que chaque technicien pourra utiliser.

Pour en savoir plus sur GDAP dans Microsoft 365 Lighthouse, consultez [Configurer la sécurité du portail Microsoft 365 Lighthouse](m365-lighthouse-configure-portal-security.md).

### <a name="capability-to-notify-users-to-act-on-non-compliant-devices"></a>Possibilité d’informer les utilisateurs d’agir sur des appareils non conformes

Dans le cadre de l’étape de référence de conformité des appareils, nous avons ajouté la possibilité d’informer les utilisateurs d’un locataire client d’agir sur des appareils non conformes. Avec cette modification, une fois que vous appliquez l’étape de déploiement de conformité des appareils pour n’importe quel locataire client, la stratégie de conformité de l’appareil créée dans ce locataire envoie automatiquement une notification aux utilisateurs lorsque leur appareil devient non conforme, leur rappelant de prendre les mesures appropriées pour rétablir la conformité de l’appareil.

### <a name="deployment-validation-and-reporting"></a>Validation et création de rapports de déploiement

Microsoft 365 Lighthouse pouvez désormais tester les configurations de locataire pour les étapes de déploiement avec des stratégies d’accès conditionnel.  

Cette nouvelle fonctionnalité fonctionne en détectant les stratégies existantes au sein des locataires que vous gérez et en les comparant à votre plan de déploiement. Microsoft 365 Lighthouse fournit ensuite des désignations d’état pour les étapes de déploiement et les processus d’étape de déploiement pour vous aider à comprendre quels processus de déploiement ont déjà été terminés, ceux qui doivent être traités et où les paramètres prescrits par le plan de déploiement sont égaux, manquants ou en conflit avec les paramètres inclus dans les stratégies existantes. La connaissance de ces informations facilite l’identification, la hiérarchisation et la résolution des conflits de stratégie plus rapidement, plus facilement et plus efficace.

### <a name="deployment-step-to-configure-microsoft-defender-firewall"></a>Étape de déploiement pour configurer Pare-feu Microsoft Defender

Microsoft 365 Lighthouse a ajouté l’étape configurer Pare-feu Microsoft Defender déploiement à sa ligne de base par défaut. Cette étape permet aux MSP de sécuriser les appareils de leur locataire par le biais de la configuration par défaut du pare-feu pour les appareils Windows 10 (et versions ultérieures). Pare-feu Microsoft Defender bloque le trafic réseau non autorisé entrant ou sortant des appareils de votre locataire et réduit le risque de menaces de sécurité réseau. Une fonctionnalité de règles Pare-feu Microsoft Defender est en cours de développement.

Pare-feu Microsoft Defender est activé par défaut sur les appareils Windows 10 (et versions ultérieures). Si ce n’est pas configuré pour votre locataire client, procédez comme suit :

1. Dans la page **Locataires** de Microsoft 365 Lighthouse, sélectionnez le locataire client pour ouvrir la page **Vue d’ensemble** du locataire.
2. Sélectionnez l’onglet **Plan de déploiement** .
3. Dans la liste des étapes de déploiement, sélectionnez **Configurer Pare-feu Microsoft Defender**.
4. Sélectionnez **Vérifier et déployer** pour déployer cette configuration sur le locataire du client. 

### <a name="increase-in-maximum-license-limit"></a>Augmentation de la limite maximale de licence

Nous rendons possible la gestion d’un plus grand nombre de vos clients dans Microsoft 365 Lighthouse en augmentant la limite de licence maximale pour l’intégration des clients. Les clients avec jusqu’à 1 000 licences utilisateur peuvent désormais être intégrés à Microsoft 365 Lighthouse. Nous continuerons d’évaluer cette exigence à l’avenir Microsoft 365 Lighthouse versions.

Pour plus d’informations, consultez [Configuration requise pour Microsoft 365 Lighthouse](m365-lighthouse-requirements.md).

### <a name="support-for-advisor-customers"></a>Prise en charge des clients Conseiller

Nous avons modifié nos exigences d’intégration pour permettre aux locataires clients existants avec des relations Conseiller d’être intégrés à Microsoft 365 Lighthouse. Les clients disposant de contrats de revendeur et d’conseiller peuvent désormais se trouver dans Microsoft 365 Lighthouse s’ils remplissent les conditions requises pour les autorisations d’accès délégué, disposent des licences requises et ne dépassent pas le nombre maximal d’utilisateurs.

Pour plus d’informations, consultez [Configuration requise pour Microsoft 365 Lighthouse](m365-lighthouse-requirements.md).

## <a name="january-2022"></a>Janvier 2022

### <a name="capability-to-review-audit-logs-in-microsoft-365-lighthouse"></a>Possibilité d’examiner les journaux d’audit dans Microsoft 365 Lighthouse

Microsoft 365 Lighthouse inclut désormais la possibilité d’examiner les journaux d’audit. Vous pouvez passer en revue les actions passées pour rechercher des configurations incorrectes et des actions à risque pour la correction, le processus de support et l’enquête de sécurité, former les employés et répondre aux exigences de conformité et d’audit. Avec la dernière mise à jour, vous pouvez :

- Affichez les journaux d’audit pour voir toutes les actions effectuées dans Microsoft 365 Lighthouse y compris ce qui a changé dans quels locataires client, quand et par qui.
- Recherchez et filtrez les journaux d’audit pour rechercher des informations spécifiques.
- Exportez les journaux pour pouvoir les analyser et les conserver.
 
Dans le volet de navigation gauche de Microsoft 365 Lighthouse, sélectionnez **Journaux d’audit**. Vous pouvez également [accéder directement à la page Journaux d’audit pour](https://lighthouse.microsoft.com/#blade/Microsoft_Intune_MTM/Audit.ReactView) la consulter.

## <a name="november-2021"></a>Novembre 2021

### <a name="microsoft-365-services-usage-data"></a>données d’utilisation des services Microsoft 365

Vous pouvez désormais afficher les données d’utilisation des services Microsoft 365 à partir de Microsoft 365 Lighthouse. Comprendre comment les clients utilisent leurs services Microsoft 365 est essentiel pour les aider à tirer le meilleur parti de leurs investissements informatiques. Au lieu d’utiliser plusieurs ressources pour afficher des informations sur les différents services de productivité, de sécurité et de conformité de vos clients, Microsoft 365 Lighthouse les agrège en une vue simple et puissante.  

Ces insights peuvent aider à informer vos engagements clients et à offrir plus de valeur à vos clients en vous permettant de les aider à comprendre les services que leurs utilisateurs utilisent activement et où il peut y avoir des opportunités d’améliorer leur sécurité ou leur productivité. 

Pour plus d’informations, consultez [la page Vue d’ensemble des locataires dans Microsoft 365 Lighthouse : Microsoft 365 carte d’utilisation](m365-lighthouse-tenants-page-overview.md#microsoft-365-usage-card).

### <a name="exchange-online-protection-and-microsoft-365-defender-for-office-365-default-baseline-step"></a>Exchange Online Protection et Microsoft 365 Defender pour Office 365 étape de référence par défaut

Nous avons ajouté une nouvelle étape à la base de référence par défaut pour inclure des conseils pour l’activation des stratégies de sécurité pour Exchange Online Protection (EOP) et Microsoft Defender pour Office 365 (MDO). EOP et MDO aident à protéger les utilisateurs contre le courrier indésirable, le hameçonnage et les courriers malveillants en envoyant les e-mails au dossier de mise en quarantaine ou de courrier indésirable de l’utilisateur (bientôt disponible). Le plan de déploiement vous guide dans la configuration d’EOP et MDO, en développant davantage votre position en matière de sécurité lors de la prochaine révision du plan de déploiement du client.

### <a name="default-tenant-tags"></a>Balises de locataire par défaut

Vous pouvez maintenant désigner certaines balises de locataire par *défaut* à partir du volet **Gérer les étiquettes** de la page **Locataires**. La prochaine fois que vous vous connectez à Microsoft 365 Lighthouse, toutes vos vues et insights seront filtrés par défaut pour afficher uniquement les locataires qui ont une balise par défaut. Les balises par défaut peuvent vous aider à vous concentrer sur les insights pour les locataires clients à priorité élevée.

## <a name="october-2021"></a>Octobre 2021

### <a name="capability-to-filter-by-multiple-tenant-tags"></a>Possibilité de filtrer par plusieurs balises de locataire

Il est désormais possible de filtrer les données par plusieurs balises de locataire en même temps. Cette fonctionnalité peut vous aider à filtrer plus facilement les vues et insights existants disponibles dans Microsoft 365 Lighthouse pour afficher les locataires clients appropriés.

### <a name="capability-to-assign-baseline-configurations-to-specific-azure-active-directory-groups"></a>Possibilité d’affecter des configurations de base de référence à des groupes Azure Active Directory spécifiques

Nous avons ajouté la possibilité d’affecter des configurations de base de référence à des groupes de Azure Active Directory spécifiques (Azure AD) de vos locataires clients à partir de Microsoft 365 Lighthouse. Dans n’importe quelle page d’étape de déploiement, parcourez et sélectionnez les groupes Azure AD spécifiques que vous souhaitez inclure ou exclure, puis déployez les configurations sur votre locataire client.

### <a name="improvements-to-risky-users-page"></a>Page Améliorations apportées aux utilisateurs à risque

Vous pouvez désormais facilement afficher et comprendre les raisons du risque d’un utilisateur à partir de Microsoft 365 Lighthouse. Dans le volet de navigation gauche de Microsoft 365 Lighthouse, sélectionnez **Utilisateurs**, puis l’onglet **Utilisateurs à** risque. Sélectionnez **Afficher les détections de risques** dans la colonne **Détails** de n’importe quel utilisateur. À partir de là, vous pouvez examiner les détails du risque, puis sélectionner **Confirmer que l’utilisateur est compromis** ou **Ignorer le risque utilisateur**. Vous pouvez également confirmer ou ignorer un risque pour plusieurs utilisateurs en même temps à partir de la page **Utilisateurs à risque** . La possibilité d’ignorer le risque d’un utilisateur peut être utile lorsque la réinitialisation du mot de passe n’est pas une option ou si vous pensez que l’utilisateur affecté n’est plus en danger.

### <a name="capability-to-provide-feedback-on-microsoft-365-lighthouse"></a>Possibilité de fournir des commentaires sur Microsoft 365 Lighthouse

Vos commentaires sont importants pour nous. Nous avons donc ajouté de nouvelles fonctionnalités de commentaires qui vous inviteront occasionnellement (au plus une fois par mois) à nous faire part de vos commentaires. Vous pouvez également fournir des commentaires à tout moment en sélectionnant l’icône Commentaires dans le coin supérieur droit de Microsoft 365 Lighthouse.

## <a name="september-2021"></a>Septembre 2021

### <a name="tenant-filter-changes"></a>Modifications du filtre de locataire

Nous avons apporté des modifications à l’expérience de filtrage des locataires pour vous aider à afficher et gérer rapidement les locataires et les balises à partir de n’importe quelle page dans Microsoft 365 Lighthouse. Sélectionnez le filtre Locataires en haut de n’importe quelle page, puis parcourez ou entrez le nom du locataire ou de la balise sur lequel vous souhaitez filtrer.

## <a name="august-2021"></a>Août 2021

### <a name="in-product-email-workflows-to-communicate-with-users"></a>Flux de travail de messagerie dans le produit pour communiquer avec les utilisateurs 

Nous avons facilité la communication avec les utilisateurs de vos locataires clients sur les actions qu’ils doivent effectuer. Dans la liste des utilisateurs non inscrits pour l’authentification multifacteur (MFA) ou la réinitialisation de mot de passe en libre-service, vous pouvez désormais sélectionner un ou plusieurs utilisateurs et leur envoyer un e-mail à l’aide d’un modèle de messagerie téléchargeable.

### <a name="capability-to-take-action-on-noncompliant-devices"></a>Possibilité d’agir sur les appareils non conformes

Nous avons introduit la possibilité de synchroniser ou de redémarrer un ou plusieurs appareils sur plusieurs locataires clients. Cette fonctionnalité permet de s’assurer que les appareils de vos clients sont protégés contre les risques. Pour extraire cette fonctionnalité, sélectionnez **Appareils** dans le volet de navigation gauche dans Microsoft 365 Lighthouse, puis sélectionnez l’onglet **Appareils**. Recherchez les options **De synchronisation** et **de redémarrage** au-dessus de la liste des appareils. Vous pouvez également accéder à ces options à partir du volet détails de l’appareil de n’importe quel appareil.

### <a name="capability-to-monitor-and-manage-windows-365-cloud-pcs"></a>Possibilité de surveiller et de gérer Windows 365 PC cloud

Nous avons ajouté la possibilité de surveiller les connexions locales et de provisionner et de gérer Windows 365 PC cloud sur tous vos locataires clients. La nouvelle page **Windows 365** fournit des informations détaillées sur tous les PC cloud de vos locataires dans un emplacement pratique. 

### <a name="support-for-microsoft-365-e3-customers"></a>Prise en charge des clients Microsoft 365 E3

Nous avons modifié nos exigences d’intégration pour vous permettre d’intégrer Microsoft 365 E3 clients à Microsoft 365 Lighthouse. Pour pouvoir être géré dans Microsoft 365 Lighthouse, chaque client doit répondre aux exigences suivantes :

- Doit disposer d’un accès délégué configuré pour que le fournisseur de services web puisse gérer le locataire client
- Doit avoir au moins une licence Microsoft 365 Business Premium ou Microsoft 365 E3
- Ne doit pas avoir plus de 500 utilisateurs sous licence

Pour plus d’informations sur les exigences, consultez [Configuration requise pour Microsoft 365 Lighthouse](m365-lighthouse-requirements.md).

## <a name="june-2021"></a>Juin 2021

### <a name="capability-to-add-custom-tags-to-customer-tenants"></a>Possibilité d’ajouter des balises personnalisées aux locataires du client

Vous pouvez maintenant créer et appliquer des balises personnalisées aux locataires clients que vous gérez dans Microsoft 365 Lighthouse. Utilisez ces balises pour vous aider à organiser vos locataires ou utilisez-les pour filtrer plus facilement votre liste de locataires afin d’afficher des insights pour les ensembles appropriés de locataires clients. 

### <a name="baselines-to-standardize-your-customer-tenant-deployments"></a>Bases de référence pour normaliser les déploiements de vos locataires clients

Avec la nouvelle fonctionnalité de base de référence, vous pouvez désormais déployer des configurations standard liées à la sécurisation des utilisateurs, des appareils et des données de votre locataire client. La base de référence par défaut contient actuellement les étapes de déploiement suivantes (d’autres seront bientôt disponibles) : 

- Exiger l’authentification multifacteur pour les administrateurs 
- Exiger l’authentification multifacteur pour les utilisateurs 
- Bloquer l’authentification héritée 
- Inscrire des appareils Windows dans Microsoft Endpoint Manager – Azure AD Join 
- Configurer la stratégie av Defender pour les appareils Windows 
- Configurer la stratégie de conformité pour les appareils Windows 

Pour suivre ces étapes de déploiement, sélectionnez **Locataires** dans le volet de navigation gauche dans Microsoft 365 phare, sélectionnez un locataire dans la liste des locataires, puis sélectionnez l’onglet **Plan de** déploiement. 

## <a name="may-2021"></a>Mai 2021

### <a name="enhancements-to-tenants-page"></a>Page Améliorations apportées aux locataires

Nous avons apporté les améliorations suivantes à la page **Locataires** :

- Ajout d’une liste des nombres totaux par problème en haut de la page 
- Possibilité de pointer sur un état dans la colonne **État** de la liste des locataires pour afficher les détails de la restriction 
- Amélioration des étiquettes d’état