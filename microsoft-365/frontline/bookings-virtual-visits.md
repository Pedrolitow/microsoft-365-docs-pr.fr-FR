---
title: Rendez-vous virtuels avec Microsoft Teams et l’application Bookings
author: lanachin
ms.author: v-lanachin
manager: samanro
audience: ITPro
ms.topic: article
ms.service: microsoft-365-frontline
search.appverid: ''
searchScope:
- Microsoft Teams
- Microsoft Cloud for Healthcare
- Microsoft Cloud for Retail
f1.keywords:
- NOCSH
ms.localizationpriority: high
ms.collection:
- microsoftcloud-healthcare
- microsoftcloud-retail
- m365solution-healthcare
- m365solution-scenario
- m365-frontline
ms.reviewer: ''
description: Découvrez comment planifier, gérer et effectuer des rendez-vous virtuels à l’aide de l’application Bookings dans Teams.
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.openlocfilehash: ef4ca09cac8cc411e6b9b33b32b27c01265ddccf
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2022
ms.locfileid: "66992400"
---
# <a name="virtual-appointments-with-microsoft-teams-and-the-bookings-app"></a>Rendez-vous virtuels avec Microsoft Teams et l’application Bookings

## <a name="overview"></a>Vue d’ensemble

L’[application Bookings](https://support.microsoft.com/office/what-is-bookings-42d4e852-8e99-4d8f-9b70-d7fc93973cb5) dans Microsoft Teams offre aux organisations un moyen simple de planifier et de gérer des rendez-vous virtuels pour le personnel et les participants. Utilisez-le pour planifier des rendez-vous tels que des visites médicales, des consultations financières, des entretiens, le support client, des installations virtuelles et des consultations, des heures de bureau de formation, etc.

L’application Bookings facilite la gestion des demandes de planification complexes de n’importe quelle organisation. Les planificateurs peuvent gérer plusieurs calendriers de service et de personnel, ainsi que des communications avec les participants internes et externes, d’une seule expérience.

Les rendez-vous virtuels sont organisés par le biais de réunions Microsoft Teams, qui offrent des fonctionnalités de vidéoconférence robustes. Par exemple, un médecin peut partager son écran et passer en revue les résultats des tests avec un patient. Ou bien, un conseiller bancaire peut demander des signatures électroniques sur des documents, ce qui lui permet de fermer des transactions à distance.

Chaque rendez-vous virtuel inclut un lien de réunion Teams qui est envoyé aux participants par e-mail où ils peuvent facilement participer à partir d’un navigateur web ou dans Teams sur n’importe quel appareil. Les rappels par e-mail automatisés permettent de réduire les absences et d’améliorer l’engagement des clients et des clients.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4TQop]

Avec Bookings, vous bénéficiez d’une expérience adaptée à votre secteur d’activité. Voici quelques exemples de la façon dont vous pouvez l’utiliser dans votre organisation :

|Secteur d’activité | Exemples |
|---------|---------|
|Services financiers    |  Rendez-vous virtuels pour les ventes à distance et le service<br/>Planifiez et gérez des rendez-vous pour les gestionnaires de relations bancaires, les conseillers financiers et les ajusteurs de revendications, pour n’en nommer que quelques-uns, afin de servir vos clients avec une efficacité et une commodité accrues.  |
|Commerce   | Ajustements et consultations virtuels <br/>Planifiez et gérez les rendez-vous de vos associés commerciaux, experts en produits et consultants en conception afin d’effectuer des montages virtuels et des consultations avec les clients.   |
|Santé   |  Rendez-vous virtuels pour les soins aux patients <br/>Planifiez et gérez les rendez-vous pour que les membres de votre équipe de soins rencontrent des patients ou d’autres prestataires de santé pour discuter des soins médicaux.   |

Cet article vous donne une vue d’ensemble de la planification, de la gestion et de la réalisation de rendez-vous virtuels à l’aide de l’application Bookings dans Teams.

## <a name="before-you-get-started"></a>Avant de commencer

Si vous êtes administrateur, consultez [Gérer l’application Bookings dans Teams](/microsoftteams/bookings-app-admin?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json) pour en savoir plus sur les conditions préalables à l’utilisation de l’application Bookings dans Teams, comment contrôler l’accès à Bookings dans votre organisation, ainsi que les paramètres de stratégie et d’administration recommandés.

N’oubliez pas que seuls les planificateurs de votre organisation doivent avoir installé l’application Bookings dans Teams. Le personnel qui effectue ou participe à des rendez-vous virtuels n’a pas besoin de l’application. Ils rejoignent des rendez-vous à partir de leur calendrier Teams ou Outlook ou en utilisant le lien de la réunion dans leur e-mail de confirmation de réservation.

## <a name="set-up-a-new-booking-calendar"></a>Configurer un nouveau calendrier de réservation

### <a name="create-the-booking-calendar"></a>Créer le calendrier de réservation

Dans Teams, accédez à **Bookings** > **Démarrage**, puis sélectionnez **Nouveau calendrier de réservation**. Remplissez le formulaire et veillez à choisir le type d’entreprise approprié pour votre organisation.

:::image type="content" source="media/bookings-virtual-visits-new-booking-calendar.png" alt-text="Capture d’écran de l’écran nouveau calendrier de réservation montrant les types d’entreprises":::

Si vous êtes une grande organisation, envisagez de créer plusieurs calendriers de réservation si vous souhaitez que les participants reçoivent un e-mail de réservation d’un service spécifique plutôt que de votre organisation globale.
Pour en savoir plus, consultez [Créer un calendrier Bookings](https://support.microsoft.com//office/create-a-bookings-calendar-921cfd26-a24d-4aca-9004-561594112148).

> [!NOTE]
> Si ce n’est pas votre première fois dans l’application Bookings ou si vous souhaitez travailler dans un calendrier de réservation existant, dans Bookings, sélectionnez la flèche déroulante en regard du nom de votre organisation, puis choisissez **Calendrier de réservation existant**. À partir de là, vous pouvez rechercher celui que vous voulez.

### <a name="add-staff"></a>Ajouter du personnel

Dans le calendrier de réservation, accédez à **Plus d’options** (...) > **Paramètres**, puis sélectionnez **Personnel**. Ajoutez des membres du personnel et attribuez un rôle à chaque personne que vous ajoutez. Vous pouvez ajouter jusqu’à 100 membres du personnel à un calendrier de réservation.

L’application Bookings s’intègre à Outlook. Après avoir ajouté du personnel, vous pourrez afficher la disponibilité de son calendrier et planifier des réservations pour lui. Pour en savoir plus, consultez [Ajouter du personnel et afficher un calendrier Bookings](https://support.microsoft.com/office/add-staff-and-view-a-bookings-calendar-6c579f61-8adb-4514-9458-021de2023fa0).  

### <a name="create-appointment-types"></a>Créer des types de rendez-vous

Créez des types de rendez-vous spécifiques pour représenter les services offerts par votre organisation et adapter l’expérience de réservation. Les planificateurs peuvent ensuite utiliser le type de rendez-vous pour planifier un rendez-vous.

Dans le calendrier de réservation, accédez à **Plus d’options** (...) > **Paramètres**, sélectionnez **Types de rendez-vous**, puis **sélectionnez Ajouter un type de rendez-vous**. Entrez un nom&mdash;, par exemple ouverture de compte, renouvellement de prescription, consultation sur les prêts, préparation&mdash;de la taxe et toute autre information et paramètres souhaités.

Les informations que vous ajoutez sont incluses dans la confirmation par e-mail envoyée aux participants chaque fois que ce type de rendez-vous est réservé. Vous pouvez définir des rappels par e-mail et d’autres options, par exemple si les participants peuvent [participer à partir d’un navigateur de bureau ou mobile](browser-join.md) sans avoir à télécharger Teams.

Si vous êtes administrateur de Bookings, vous pouvez lier jusqu’à quatre formulaires que les participants peuvent remplir chaque fois que ce type de rendez-vous est réservé. Par exemple, vous pouvez demander aux participants de remplir un formulaire d’inscription avant de rejoindre un rendez-vous. Pour lier un formulaire, choisissez **Lier un formulaire**. Entrez l’URL du formulaire, puis choisissez **Lien**. (S’il s’agit de la première fois que vous liez un formulaire, vous êtes invité à créer un groupe Microsoft 365 pour stocker des formulaires. Choisissez **Créer un groupe** pour créer le groupe. Vous ne devez effectuer cette opération qu’une seule fois pour le calendrier de réservation.)

Lorsque vous utilisez des formulaires, gardez à l’esprit que :

- Pour apporter des modifications à un formulaire déjà lié à un type de rendez-vous, sélectionnez le formulaire dans le type de rendez-vous ou dans le groupe Microsoft 365 à [https://forms.office.com](https://forms.office.com).
- Le chargement de fichiers dans des formulaires contenant une [question de chargement de fichiers](https://support.microsoft.com/office/add-questions-that-allow-for-file-uploads-6a75a658-c02b-450e-b119-d068f3cba4cf) est pris en charge lorsque tous les participants proviennent de la même organisation.

Lorsqu’un planificateur utilise le type de rendez-vous pour planifier un rendez-vous, il peut choisir d’inclure le formulaire, de le supprimer ou d’ajouter d’autres formulaires que vous avez liés au type de rendez-vous. Les participants doivent remplir le formulaire avant de rejoindre le rendez-vous.

> [!NOTE]
> Si vous êtes un professionnel de la santé, toutes les informations fournies par vous ou les patients dans Teams (y compris l’application Formulaires, l’application Bookings, les enregistrements de réunion si activés par vous ou tout autre service de rendez-vous virtuel Teams) nécessaires à la continuité des dossiers médicaux ou à la rétention doivent être téléchargées, copiées et/ou notifiées directement dans ces dossiers par vous. Ce service ne tient pas de dossiers médicaux juridiques ou de dossiers désignés.

Pour plus d’informations, consultez [Créer un type de rendez-vous](https://support.microsoft.com/office/create-an-appointment-type-810eac77-6a65-4dc8-964d-c00eadf43887).

## <a name="schedule-an-appointment"></a>Planifier un rendez-vous

Dans le calendrier de réservation, sélectionnez **Nouvelle réservation**. Sélectionnez un type de rendez-vous, puis renseignez les informations pertinentes.

Cela inclut les informations de contact du participant, le membre du personnel qui fournira le service, les notes internes que seul le personnel peut voir, les rappels par e-mail et si le participant peut participer à partir d’un navigateur mobile. Si un formulaire est lié au type de rendez-vous, vous pouvez choisir de l’inclure, de le supprimer ou d’ajouter d’autres formulaires liés.

La confirmation par e-mail envoyée au participant inclut le lien de réunion et une pièce jointe afin qu’il puisse ajouter le rendez-vous virtuel à son calendrier. Le personnel reçoit également une confirmation par e-mail et une invitation à une réunion. Si un formulaire a été inclus dans le rendez-vous, les administrateurs et planificateurs bookings peuvent voir si le formulaire a été rempli par le participant avant le rendez-vous et peut afficher la réponse du participant.

Pour plus d’informations, consultez [Planifier une réservation dans l’application Réservations Teams](https://support.microsoft.com/office/schedule-a-booking-in-the-teams-bookings-app-e275049d-0d0f-4161-8526-461a9f29439f).

## <a name="conduct-an-appointment"></a>Mener un rendez-vous

Dans votre calendrier Teams ou Outlook, accédez à la réservation, puis sélectionnez **Rejoindre** ou le lien de réunion Teams. Vérifiez vos paramètres audio et vidéo, puis sélectionnez **Rejoindre maintenant**. Pour plus d’informations, consultez [Effectuer un rendez-vous Bookings](https://support.microsoft.com/office/conduct-a-bookings-appointment-a86a4007-e26c-4909-9893-f7036e2747cd).

## <a name="monitor-appointments-and-get-real-time-status-updates"></a>Surveiller les rendez-vous et obtenir des mises à jour d’état en temps réel

L’[affichage file d’attente](https://support.microsoft.com/office/queue-view-in-bookings-3eea2840-a1e0-4bcd-8e09-d3cf51c184d6) dans Bookings fournit à votre personnel un tableau de bord pour surveiller tous les rendez-vous virtuels de la journée, avec des mises à jour en temps réel. Pour voir la file d’attente, accédez à l’onglet **File d’attente** dans Bookings.

:::image type="content" source="media/bookings-virtual-visits-queue.png" alt-text="Capture d’écran de l’affichage file d’attente dans l’application Bookings dans Teams" lightbox="media/bookings-virtual-visits-queue.png":::

À partir de la file d’attente, les planificateurs peuvent ajouter une nouvelle réservation, afficher les détails de rendez-vous pertinents et voir les états des rendez-vous tout au long de la journée. Lorsqu’un patient rejoint la salle d’attente, l’état change et son temps d’attente s’affiche et fait l’objet d’un suivi. La vue s’actualise automatiquement avec des mises à jour codées en couleurs afin que les modifications puissent être facilement identifiées.

Le personnel peut même rejoindre et gérer les rendez-vous directement à partir de la file d’attente.

> [!NOTE]
> Actuellement, l’application Bookings prend en charge l’ajout d’un maximum de 100 employés par calendrier de réservation. Si vous avez utilisé les API Graph pour configurer et ajouter du personnel à un calendrier de réservation, cette limite peut ne pas être appliquée. Dans ce scénario, l’onglet **File d’attente** ne peut pas afficher le contenu des calendriers qui ont plus de 100 employés. Pour une expérience optimale, nous vous recommandons d’ajouter pas plus de 100 personnes à un calendrier de réservation. Nous nous efforçons de résoudre cette limitation dans les versions ultérieures.

## <a name="additional-capabilities-with-the-bookings-web-app"></a>Fonctionnalités supplémentaires avec l’application web Bookings

L’application web Bookings vous offre des fonctionnalités supplémentaires. Par exemple, vous pouvez publier une page de réservation en ligne libre-service où les personnes peuvent planifier des rendez-vous avec votre personnel. Pour accéder à l’application web Bookings, accédez à **Plus d’options** (...) > **ouvrir l’application web Bookings**.

Pour en savoir plus, consultez [Microsoft Bookings](/microsoft-365/bookings/bookings-overview).

## <a name="get-insight-into-virtual-appointments-usage"></a>Obtenir des informations sur l’utilisation des rendez-vous virtuels

Le [rapport d’utilisation des visites virtuelles](virtual-visits-usage-report.md) dans le Centre d’administration Microsoft Teams donne aux administrateurs une vue d’ensemble de l’activité des rendez-vous virtuels Teams dans votre organisation. Le rapport présente des analyses détaillées pour les rendez-vous virtuels, y compris les rendez-vous Bookings.

Vous pouvez afficher des indicateurs clés telles que le temps d’attente dans la salle d’attente et la durée du rendez-vous. Utilisez ces informations pour obtenir des informations sur les tendances d’utilisation afin de vous aider à optimiser les rendez-vous virtuels afin d’obtenir de meilleurs résultats métier.

## <a name="related-articles"></a>Articles connexes

- [Gérer l’expérience de jointure pour les rendez-vous virtuels Teams sur les navigateurs](browser-join.md)

- [Rapport d’utilisation des visites virtuelles Teams](virtual-visits-usage-report.md)

- [Prise en main de Teams pour les organismes de santé](teams-in-hc.md)

- [Documentation d’aide sur l’application Bookings dans Teams](https://support.microsoft.com/office/what-is-bookings-42d4e852-8e99-4d8f-9b70-d7fc93973cb5)