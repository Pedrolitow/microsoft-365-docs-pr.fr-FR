---
title: Utiliser des connecteurs Power Automate pour créer des flux de travail Bookings
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.localizationpriority: medium
description: Utilisez les connecteurs Power Automate Bookings pour créer des flux de travail personnalisés avec des déclencheurs de rendez-vous.
ms.openlocfilehash: ca37f33d77d83fd13f7719edb345c7150d8226c0
ms.sourcegitcommit: 23c7e96d8ec31c676c458e7c71f1cc8a1e40a0e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2022
ms.locfileid: "67360730"
---
# <a name="use-power-automate-connectors-to-build-bookings-workflows"></a>Utiliser des connecteurs Power Automate pour créer des flux de travail Bookings

Microsoft Bookings Connecteur est conçu pour étendre les rendez-vous Booking avec d’autres fonctionnalités que power platform a à offrir. Si vous avez déjà voulu créer des flux de travail personnalisés pour vos rendez-vous clients professionnels, par exemple pour permettre aux clients de réserver une réunion Zoom avec un rendez-vous, intégrer un mode de paiement à l’aide de Stripe, charger des données client sur un système CRM ou envoyer des e-mails de bienvenue, Bookings Connector est votre solution Bookings.

## <a name="before-you-begin"></a>Avant de commencer

Les clients qui souhaitent utiliser bookings Connector doivent disposer d’une licence Bookings. Pour plus d’informations sur les licences et abonnements Microsoft Bookings, consultez [Microsoft Bookings Forum aux questions](bookings-faq.yml#is-bookings-available-for-my-subscription-).

Microsoft Bookings utilise l’authentification Azure Active Directory (AAD). Un compte Microsoft 365 valide garantit que vous êtes authentifié pour utiliser Bookings Connector. Vous devez être connecté pour créer des flux basés sur des rendez-vous.

Pour créer un flux personnalisé qui utilise les rendez-vous Bookings comme déclencheurs, vous devez fournir l’adresse SMTP d’entreprise Bookings.

![Image d’une adresse SMTP.](media/bookings-teams-smtp.png)

## <a name="get-started-with-connectors"></a>Prise en main des connecteurs

Voici quelques-uns des flux courants que vous pouvez créer avec des connecteurs Microsoft Bookings :

### <a name="integration-with-stripe"></a>Intégration à Stripe

Stripe permet aux particuliers et aux entreprises d’accepter des paiements sur Internet. Vous pouvez suivre les clients, les commandes, les factures, etc. Pour plus d’informations, consultez [Stripe | Microsoft Power Automate](https://powerautomate.microsoft.com/connectors/details/shared_stripe/stripe/).

### <a name="integration-with-zoom"></a>Intégration à Zoom

Le connecteur Zoom Meetings permet d’automatiser les opérations de réunion Zoom. Pour plus d’informations, consultez [Les réunions de zoom (éditeur indépendant) | Microsoft Power Automate](https://powerautomate.microsoft.com/connectors/details/shared_zoommeetingsip/zoom-meetings-independent-publisher/).

### <a name="integration-with-dynamic-365"></a>Intégration à Dynamic 365

Dynamics 365 Sales Insights permet d’augmenter les ventes à l’aide d’insights pilotés par l’intelligence artificielle (IA) qui favorisent un engagement personnalisé et une prise de décision proactive pour aider à établir des relations. Pour plus d’informations, consultez [Dynamics 365 Sales Insights | Microsoft Power Automate](https://powerautomate.microsoft.com/connectors/details/shared_assistantstudio/dynamics-365-sales-insights/).

Pour tous les connecteurs Bookings disponibles, consultez les [connecteurs pris en charge | Microsoft Power Automate](https://powerautomate.microsoft.com/connectors/).

## <a name="known-issues-and-limitations"></a>Problèmes connus et conseils

- **Seuls les administrateurs peuvent créer des flux à l’aide de déclencheurs de rendez-vous.** Seuls les administrateurs Bookings peuvent créer des déclencheurs de rendez-vous. Si vous êtes un utilisateur et non un administrateur (membre de l’équipe, planificateur, visionneuse, invité), vous devez demander à votre administrateur de créer un flux. Vous pouvez également demander l’accès administrateur.

- **Seuls cinq flux peuvent être créés par boîte aux lettres Bookings.** Il s’agit d’une limite au niveau de la boîte aux lettres Bookings et non d’une limite par administrateur. Si vous souhaitez plusieurs actions pour un déclencheur de rendez-vous, vous pouvez ajouter l’action à l’un des flux existants avec le bouton **Ajouter une action** . Pour obtenir de l’aide, contactez d’autres administrateurs booking.

- **Certains paramètres Bookings ne sont pas renseignés.** La raison de l’annulation et les notes personnalisées pour les réservations 1:1 ne sont pas remplies. Le correctif sera bientôt déployé.

- **Les codes d’erreur lors de la création du flux ne sont pas entièrement visibles.** Les erreurs qui peuvent se produire lors de la création d’un flux n’apparaissent pas dans le portail de flux. Le correctif est en cours et sera disponible dans la prochaine version.

## <a name="common-errors-and-remedies"></a>Erreurs et recours courants

Codes d’erreur HTTP lors de la création de flux :

- « 401 » : recherchez les problèmes liés à l’authentification dans votre connexion.
- « 403 » : seuls les administrateurs bookings peuvent créer des flux de rendez-vous. Consultez le premier problème dans « Problèmes connus et limitations » ci-dessus.
- '403' : le domaine d’URL de notification ne fait pas partie de la liste autorisée.
- « 429 » : Plus que le nombre attendu de flux de rendez-vous ont été créés pour une entreprise. Consultez la limite de cinq flux par boîte aux lettres Bookings dans « Problèmes connus et limitations » ci-dessus.
- « 500 » : il s’agit d’une erreur de serveur interne. Signalez cette erreur à votre ingénieur du support technique et incluez les détails de l’erreur dans la réponse de création de flux.

## <a name="frequently-asked-questions"></a>Forum Aux Questions

**Comment faire obtenir l’adresse SMTP pour créer un flux basé sur un déclencheur de rendez-vous ?**

Pour créer des flux basés sur un déclencheur de rendez-vous, le créateur doit obtenir l’adresse SMTP de l’entreprise Bookings. Il s’agit de la même adresse SMTP que celle utilisée pour effectuer des appels de graphe. Il s’agit également d’une partie de l’URL de la page Bookings.

**Comment puis-je obtenir des données client à partir des réponses du déclencheur de rendez-vous ?**

Pour une réservation 1:1, des champs de niveau supérieur tels que CustomerName, CustomerEmail, et ainsi de suite, sont disponibles. Pour une réservation de groupe, le tableau de clients peut utiliser des champs tels que displayName, e-mail des clients, displayName des clients, et ainsi de suite avec un composant de boucle d’automatisation de l’alimentation.

**Pourquoi StaffMembers est-il un tableau ?**

Vous pouvez affecter plusieurs membres du personnel en tant qu’hôte. Si un seul membre du personnel est affecté à votre service en tant qu’hôte, les détails du personnel sont affichés dans le tableau des membres du personnel.

## <a name="related-content"></a>Contenu associé

[Connecteurs Microsoft Power Automate](https://make.preview.powerautomate.com/connectors/shared_microsoftbookings/microsoft-bookings/)\
[Microsoft Bookings (préversion) Référence](/connectors/microsoftbookings/) (article)