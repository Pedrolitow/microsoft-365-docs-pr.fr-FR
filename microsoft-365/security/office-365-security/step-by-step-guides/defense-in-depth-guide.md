---
title: Prise en main de la configuration approfondie de la défense pour la sécurité des e-mails
description: Conseils de configuration pas à pas sur la façon d’obtenir la valeur de sécurité à partir de Microsoft Defender pour Office 365 lorsque vous disposez d’un filtrage de courrier tiers.
search.product: ''
search.appverid: ''
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: benharri
author: MSFTBen
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-guidance-templates
ms.topic: how-to
ms.technology: mdo
ms.openlocfilehash: cdeaaecbf0f0473b9f066db5d0b87e34d722a6a2
ms.sourcegitcommit: e9323a90a1156c10b037abca3e16d7367ef92dd7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67568336"
---
# <a name="getting-the-best-security-value-from-microsoft-defender-for-office-365-when-you-have-third-party-email-filtering"></a>Obtention de la meilleure valeur de sécurité à partir de Microsoft Defender pour Office 365 lorsque vous disposez d’un filtrage de courrier tiers

Ce guide vous convient si :

- Vous disposez d’une licence pour Microsoft Defender pour Office 365 et hébergez vos boîtes aux lettres dans Office 365
- Vous utilisez également un tiers pour la sécurité de vos e-mails

Les informations ci-dessous détailleront comment tirer le meilleur parti de votre investissement, divisé en étapes faciles à suivre.

## <a name="what-you-will-need"></a>Ce dont vous aurez besoin
-   Boîtes aux lettres hébergées dans Office 365
- Une ou plusieurs des opérations suivantes :
  - Microsoft Defender pour Office 365 Plan 1 pour les fonctionnalités de protection
  - Microsoft Defender pour Office 365 plan 2 pour la plupart des autres fonctionnalités (inclus dans les plans E5)
  - Microsoft Defender pour Office 365 Trial (disponible pour tous les clients au aka.ms/tryMDO)
-   Autorisations suffisantes pour configurer les fonctionnalités décrites ci-dessous

## <a name="step-1--understand-the-value-you-already-have"></a>Étape 1 : comprendre la valeur que vous avez déjà

### <a name="protection-features"></a>Fonctionnalités de protection

-   La protection intégrée offre un niveau de base de protection discrète et inclut les programmes malveillants, zero day (pièces jointes sécurisées) et la protection d’URL (liens sécurisés) dans les e-mails (y compris les e-mails internes), SharePoint Online, OneDrive et Teams. Notez que la protection d’URL fournie dans cet état se fait uniquement via un appel d’API. Il n’inclut pas d’URL ni de réécriture, mais nécessite un client Outlook pris en charge. Vous pouvez créer vos propres stratégies personnalisées pour développer votre protection.

**En savoir plus & regardez une vidéo de vue d’ensemble des liens sécurisés ici :** [Vue d’ensemble des liens sécurisés complets](../safe-links.md)

**En savoir plus sur les pièces jointes sécurisées ici :**  [Pièces jointes sécurisées](../safe-attachments.md) 

### <a name="detection-investigation-response-and-hunting-features"></a>Fonctionnalités de détection, d’investigation, de réponse et de chasse

-   Lorsque des alertes se déclenchent dans Microsoft Defender pour Office 365, elles sont automatiquement corrélées et combinées en incidents pour aider à réduire la fatigue des alertes sur le personnel de sécurité. Air (Automated Investigation and Response) déclenchera des enquêtes pour aider à corriger et à contenir les menaces.

**En savoir plus, regardez une vidéo de vue d’ensemble et commencez ici :** [Réponse aux incidents avec Microsoft 365 Defender](/microsoft-365/security/defender/incidents-overview)

-   Analyse des menaces est notre solution de renseignement sur les menaces détaillée dans le produit par des chercheurs en sécurité Microsoft experts, des rapports détaillés conçus pour vous aider à mettre à jour les derniers groupes de menaces, les techniques d’attaque, la façon de protéger votre organisation avec des indicateurs de compromission (IOC) et bien plus encore.

**En savoir plus, regardez une vidéo de vue d’ensemble et commencez ici :** [Analyse des menaces dans Microsoft 365 Defender](../../defender/threat-analytics.md)

-   L’Explorateur peut être utilisé pour chasser les menaces, visualiser les modèles de flux de messagerie, repérer les tendances et identifier l’impact des modifications que vous apportez lors du paramétrage Defender pour Office 365. Vous pouvez également supprimer rapidement des messages de votre organisation en quelques clics simples.

**En savoir plus et commencer ici :** [Explorateur de menaces et détections en temps réel](../threat-explorer.md)

## <a name="step-2--enhance-the-value-further-with-these-simple-steps"></a>Étape 2 : améliorer davantage la valeur avec ces étapes simples

### <a name="protection-features"></a>Fonctionnalités de protection

-   Envisagez d’activer des stratégies au-delà de la protection intégrée. Activation de la protection du temps de clic ou de l’emprunt d’identité, par exemple, pour ajouter des couches supplémentaires ou combler les lacunes manquantes dans votre protection tierce. Sachez que si vous disposez d’une règle de transport ou d’un filtre de connexion qui remplace les verdicts (cela peut également être appelé SCL-1), vous devez résoudre ce problème avant d’activer d’autres fonctionnalités de protection.

**En savoir plus ici :** [Stratégies anti-hameçonnage](../set-up-anti-phishing-policies.md)

-   Si votre fournisseur de sécurité actuel est configuré pour modifier les messages de *quelque manière* que ce soit, il est important de noter que les signaux d’authentification peuvent avoir un impact sur la capacité de Defender pour Office à vous protéger contre des attaques telles que l’usurpation d’identité. Si votre tiers prend en charge la chaîne de réception authentifiée (ARC), l’activation de cette étape est fortement recommandée dans votre parcours vers le filtrage double avancé. Le déplacement d’une configuration de modification de message vers Defender pour Office 365 est également une alternative.

**En savoir plus ici :** [Utiliser des expéditeurs ARC approuvés pour les appareils et services légitimes entre l’expéditeur et le récepteur](../use-arc-exceptions-to-mark-trusted-arc-senders.md)

-   Le filtrage amélioré pour les connecteurs permet de conserver les informations d’adresse IP et d’expéditeur via le tiers. Cela améliore la précision de la pile de filtrage (protection), les fonctionnalités de post-violation & les améliorations de l’authentification.

**En savoir plus ici :** [Filtrage amélioré pour les connecteurs dans Exchange Online](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors)

-   La protection de compte prioritaire offre une meilleure visibilité pour les comptes dans les outils, ainsi qu’une protection supplémentaire lorsqu’ils sont dans un état de configuration de défense avancée en profondeur.

**En savoir plus ici :** [Protection prioritaire des comptes](protect-your-c-suite-with-priority-account-protection.md)

-   Advanced Delivery doit être configuré pour fournir des simulations de hameçonnage tierces correctement, et si vous disposez d’une boîte aux lettres Opérations de sécurité, envisagez de la définir comme une boîte aux lettres SecOps pour vous assurer que les e-mails *ne sont pas* supprimés de la boîte aux lettres en raison de menaces.

**En savoir plus ici :** [Livraison avancée](../configure-advanced-delivery.md)

-   Les paramètres de messagerie signalés par l’utilisateur peuvent être configurés pour permettre aux utilisateurs de signaler des messages, directement à Microsoft, ou à votre boîte aux lettres personnalisée (pour s’intégrer aux flux de travail de sécurité actuels) ou les deux, le portail des soumissions est également accessible pour trier les faux positifs et les faux négatifs.

**En savoir plus ici :** [Déployer et configurer le complément de message de rapport pour les utilisateurs](deploy-and-configure-the-report-message-add-in.md)

### <a name="detection-investigation-response-and-hunting-features"></a>Fonctionnalités de détection, d’investigation, de réponse et de chasse

-   La chasse avancée peut être utilisée pour rechercher de manière proactive les menaces dans votre organisation, à l’aide de requêtes partagées de la communauté pour vous aider à commencer. Vous pouvez également utiliser des détections personnalisées pour configurer des alertes lorsque des critères personnalisés sont remplis.

**En savoir plus, regardez une vidéo de vue d’ensemble et commencez ici :** [Vue d’ensemble - Repérage avancé](../../defender/advanced-hunting-overview.md)

### <a name="education-features"></a>Fonctionnalités de l’éducation

- Exercice de simulation d'attaque vous permet d’exécuter des scénarios de cyberattaques réalistes mais bénins dans votre organisation. Si vous n’avez pas encore de fonctionnalités de simulation d’hameçonnage de votre fournisseur de sécurité de messagerie principal, les attaques simulées de Microsoft peuvent vous aider à identifier et à trouver des utilisateurs, des stratégies et des pratiques vulnérables. Il s’agit d’une connaissance importante à avoir et à corriger *avant* qu’une attaque réelle n’affecte votre organisation. Après la simulation que nous assignons dans un produit ou une formation personnalisée, nous informons les utilisateurs des menaces qu’ils ont manquées, ce qui réduit le profil de risque de votre organisation. Avec Exercice de simulation d'attaque nous livrons des messages directement dans la boîte de réception, de sorte que l’expérience utilisateur est riche. Cela signifie également qu’aucune modification de sécurité telle que des remplacements n’est nécessaire pour que les simulations soient correctement exécutées.

**Bien démarrer ici :** [Bien démarrer avec la simulation d’attaque](../attack-simulation-training-get-started.md)

**Passez directement à la réalisation d’une simulation ici :** [Comment configurer des attaques automatisées et de l’entraînement dans Exercice de simulation d'attaque](how-to-setup-attack-simulation-training-for-automated-attacks-and-training.md)

## <a name="step-3-and-beyond-becoming-a-dual-use-hero"></a>Étape 3 et au-delà, devenir un héros à double usage

- La plupart des activités de détection, d’investigation, de réponse et de chasse décrites ci-dessus doivent être répétées par vos équipes de sécurité. Ce guide fournit une description détaillée des tâches, de la cadence et des affectations d’équipe que nous recommandons.

**En savoir plus :** [Guide des opérations de sécurité pour Defender pour Office 365](../mdo-sec-ops-guide.md)

- Tenez compte des expériences utilisateur, telles que l’accès à plusieurs quarantaines, ou l’envoi/la création de rapports de faux positifs et de faux négatifs. Vous pouvez marquer les messages détectés par le service tiers avec un en-tête *X* personnalisé, par exemple, pour permettre à Defender pour Office 365 de les détecter et de les mettre en quarantaine via des règles de transport, ce qui donnerait également aux utilisateurs un emplacement unique pour accéder au courrier mis en quarantaine.

**En savoir plus :** [Comment configurer des stratégies et des autorisations de mise en quarantaine](how-to-configure-quarantine-permissions-with-quarantine-policies.md)

- Le guide de migration contient de nombreuses instructions utiles sur la préparation et le réglage de votre environnement pour le préparer pour une migration. Toutefois, la plupart des étapes s’appliquent *également* à un scénario à double utilisation. Ignorez simplement les instructions du commutateur MX dans les étapes finales. 

**Lisez-le ici :** [Migrer d’un service de protection tiers vers Microsoft Defender pour Office 365 - Office 365 | Microsoft Docs](../migrate-to-defender-for-office-365.md)

## <a name="more-information"></a>Informations supplémentaires

[Migrer d’un service de protection tiers vers Microsoft Defender pour Office 365](../migrate-to-defender-for-office-365.md)

[Guide des opérations de sécurité pour Defender pour Office 365](../mdo-sec-ops-guide.md)

[Tirer le meilleur parti de Microsoft Defender pour Office 365 avec Microsoft 365 Defender](https://www.youtube.com/watch?v=Tdz6KfruDGo)
