---
title: Utiliser des connecteurs Power Automate pour créer des flux de travail Bookings
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.localizationpriority: medium
ms.collection:
- Tier1
- scotvorg
description: Utilisez les connecteurs Bookings Power Automate pour créer des workflows personnalisés avec des déclencheurs de rendez-vous.
ms.openlocfilehash: 1c6f0bbcf2aa5ef8fecf410effe7ec4baebaa099
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68736472"
---
# <a name="use-power-automate-connectors-to-build-bookings-workflows"></a>Utiliser des connecteurs Power Automate pour créer des flux de travail Bookings

Microsoft Bookings Connector est conçu pour étendre les rendez-vous Booking avec d’autres fonctionnalités que power platform a à offrir. Si vous avez déjà voulu créer des flux de travail personnalisés pour vos rendez-vous clients professionnels, par exemple en permettant aux clients de réserver une réunion Zoom avec un rendez-vous, d’intégrer un mode de paiement à l’aide de Stripe, de charger des données client dans un système CRM ou d’envoyer des e-mails de bienvenue, Bookings Connector est votre solution Bookings.

## <a name="before-you-begin"></a>Avant de commencer

Les clients qui souhaitent utiliser le connecteur Bookings doivent disposer d’une licence Bookings. Pour plus d’informations sur les licences et les abonnements Microsoft Bookings, consultez [Microsoft Bookings Forum aux questions](bookings-faq.yml#is-bookings-available-for-my-subscription-).

Microsoft Bookings utilise l’authentification Azure Active Directory (AAD). Un compte Microsoft 365 valide garantit que vous êtes authentifié pour utiliser Bookings Connector. Vous devez être connecté pour créer des flux basés sur des rendez-vous.

Pour créer un flux personnalisé qui utilise les rendez-vous Bookings comme déclencheurs, vous devez fournir l’adresse SMTP de l’entreprise Bookings.

![Image d’une adresse SMTP.](media/bookings-teams-smtp.png)

## <a name="get-started-with-connectors"></a>Bien démarrer avec les connecteurs

Voici quelques-uns des flux courants que vous pouvez créer avec Microsoft Bookings Connectors :

### <a name="integration-with-stripe"></a>Intégration à Stripe

Stripe permet aux particuliers et aux entreprises d’accepter des paiements sur Internet. Vous pouvez suivre les clients, les commandes, les factures, etc. Pour plus d’informations, consultez [Stripe | Microsoft Power Automate](https://powerautomate.microsoft.com/connectors/details/shared_stripe/stripe/).

### <a name="integration-with-zoom"></a>Intégration avec Zoom

Le connecteur Réunions Zoom permet d’automatiser les opérations de réunion Zoom. Pour plus d’informations, consultez [Réunions zoom (éditeur indépendant) | Microsoft Power Automate](https://powerautomate.microsoft.com/connectors/details/shared_zoommeetingsip/zoom-meetings-independent-publisher/).

### <a name="integration-with-dynamic-365"></a>Intégration à Dynamic 365

Dynamics 365 Sales Insights permet d’augmenter les ventes à l’aide d’insights basés sur l’intelligence artificielle (IA) qui favorisent l’engagement personnalisé et la prise de décision proactive pour aider à établir des relations. Pour plus d’informations, consultez [Dynamics 365 Sales Insights | Microsoft Power Automate](https://powerautomate.microsoft.com/connectors/details/shared_assistantstudio/dynamics-365-sales-insights/).

Pour tous les connecteurs Bookings disponibles, consultez [Connecteurs pris en charge | Microsoft Power Automate](https://powerautomate.microsoft.com/connectors/).

## <a name="known-issues-and-limitations"></a>Problèmes connus et conseils

- **Seuls les administrateurs peuvent créer des flux à l’aide de déclencheurs de rendez-vous.** Seuls les administrateurs Bookings peuvent créer des déclencheurs de rendez-vous. Si vous êtes un utilisateur et non un administrateur (membre de l’équipe, planificateur, visionneuse, invité), vous devez demander à votre administrateur de créer un flux. Vous pouvez également demander un accès administrateur.

- **Seuls cinq flux peuvent être créés par boîte aux lettres Bookings.** Il s’agit d’une limite au niveau de la boîte aux lettres Bookings et non d’une limite par administrateur. Si vous souhaitez plusieurs actions pour un déclencheur de rendez-vous, vous pouvez ajouter l’action à l’un des flux existants à l’aide du bouton **Ajouter une action** . Pour obtenir de l’aide, contactez d’autres administrateurs Booking.

- **Certains paramètres bookings ne sont pas renseignés.** Motif de l’annulation et notes personnalisées pour les réservations 1:1 ne sont pas renseignées. Le correctif sera bientôt déployé.

- **Les codes d’erreur lors de la création du flux ne sont pas entièrement visibles.** Les erreurs qui peuvent se produire lors de la création d’un flux n’apparaissent pas dans le portail de flux. Le correctif est en cours et sera disponible dans la prochaine version.

## <a name="common-errors-and-remedies"></a>Erreurs courantes et remèdes

Codes d’erreur HTTP lors de la création de flux :

- « 401 » : recherchez les problèmes liés à l’authentification dans votre connexion.
- « 403 » : seuls les administrateurs Bookings peuvent créer des flux de rendez-vous. Consultez le premier problème dans « Problèmes connus et limitations » ci-dessus.
- « 403 » : le domaine d’URL de notification ne fait pas partie de la liste autorisée.
- « 429 » : Plus que le nombre attendu de flux de rendez-vous a été créé pour une entreprise. Consultez la limite de cinq flux par boîte aux lettres Bookings dans « Problèmes connus et limitations » ci-dessus.
- « 500 » : il s’agit d’une erreur de serveur interne. Signalez cette erreur à votre ingénieur du support technique et incluez les détails de l’erreur dans la réponse de création de flux.

## <a name="frequently-asked-questions"></a>Forum Aux Questions

**Comment faire obtenir l’adresse SMTP pour créer un flux basé sur un déclencheur de rendez-vous ?**

Pour créer des flux basés sur un déclencheur de rendez-vous, le créateur doit obtenir l’adresse SMTP de l’entreprise Bookings. Il s’agit de la même adresse SMTP que celle utilisée pour effectuer des appels de graphe. Cela fait également partie de l’URL de la page Bookings.

**Comment puis-je obtenir des données client à partir des réponses du déclencheur de rendez-vous ?**

Pour une réservation 1:1, des champs de niveau supérieur tels que CustomerName, CustomerEmail, etc. sont disponibles. Pour une réservation de groupe, le tableau de clients peut utiliser des champs tels que displayName, l’e-mail des clients, les clients displayName, etc. avec un composant de boucle Power Automate.

**Pourquoi StaffMembers est-il un tableau ?**

Vous pouvez affecter plusieurs membres du personnel en tant qu’hôte. Si votre service n’a qu’un seul membre du personnel affecté en tant qu’hôte, les détails du personnel sont affichés dans le tableau des membres du personnel.

## <a name="related-content"></a>Contenu associé

[Connecteurs Microsoft Power Automate](https://make.preview.powerautomate.com/connectors/shared_microsoftbookings/microsoft-bookings/)\
[Référence Microsoft Bookings (préversion)](/connectors/microsoftbookings/) (article)