---
title: Définition de vos offres de service dans bookings
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
localization_priority: Normal
ms.assetid: 4a1c391e-524f-48e0-bef8-185df3a9634b
description: Instructions pour la saisie des informations sur les offres de service, notamment le nom du service, la description, l’emplacement, la durée et les tarifs. Vous pouvez également marquer les employés qui sont qualifiés pour fournir le service.
ms.openlocfilehash: 60b77633b9845b3c269f6773c1fb8a26256fbdc5
ms.sourcegitcommit: 41fd71ec7175ea3b94f5d3ea1ae2c8fb8dc84227
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/09/2020
ms.locfileid: "47419593"
---
# <a name="define-your-service-offerings-in-bookings"></a>Définition de vos offres de service dans bookings

Lorsque vous définissez vos offres de service dans Microsoft bookings, vous définissez, un nom de service, une description, un emplacement (choisissez si vous souhaitez répondre en personne ou avoir une réunion en ligne), la durée, les rappels par défaut pour les clients et le personnel, les notes internes sur le service et les tarifs. Vous pouvez également marquer les employés qui sont qualifiés pour fournir le service. Ensuite, lorsque les clients accèdent à votre site Web d’entreprise pour réserver un rendez-vous, ils peuvent voir exactement quels types de rendez-vous sont disponibles, choisir la personne et le coût de leur service.

Vous pouvez également ajouter des URL et des informations personnalisées à la confirmation et aux rappels que vous envoyez lorsque quelqu’un livre un service via votre page de réservation.

> [!NOTE]
> Bookings est activé par défaut pour les clients qui disposent des abonnements Microsoft 365 Business standard, Microsoft 365 a3 ou Microsoft 365 a5. Bookings est également disponible pour les clients disposant d’Office 365 entreprise E3 et d’Office 365 entreprise E5, mais il est désactivé par défaut. Pour commencer, consultez la rubrique [obtenir l’accès à Microsoft bookings](get-access.md). Pour activer ou désactiver les réservations, reportez-vous à [la rubrique activer ou désactiver des réservations pour votre organisation](turn-bookings-on-or-off.md).

## <a name="create-the-service-details"></a>Créer les détails du service

1. Accédez à la [page gérer les services](https://outlook.office.com/bookings/services) et sélectionnez **Ajouter un service**.

2. **Nom du service**: entrez le nom de votre service. Il s’agit du nom qui apparaîtra dans le menu déroulant de la page calendrier. Ce nom s’affiche également quand quelqu’un ajoute manuellement un rendez-vous sur la page de calendrier et s’affiche sous la forme d’une vignette sur la page libre-service.

3. **Description**: la description que vous entrez est celle qui apparaît lorsqu’un utilisateur clique sur l’icône d’informations dans la page libre-service.

4. **Emplacement par défaut**: cet emplacement sera affiché sur les e-mails de confirmation et de rappel pour le personnel et les clients, et il sera affiché sur l’événement de calendrier créé pour la réservation.

5. **Ajouter une réunion en ligne**: ce paramètre active ou désactive les réunions en ligne pour chaque rendez-vous, par le biais de teams ou de Skype, en fonction de celui que vous configurez comme client par défaut pour le membre du personnel.

    - Activé

        - Un lien vers une réunion teams ou Skype, unique à la réservation, est ajouté à l’événement de calendrier dans les calendriers des utilisateurs et des clients, ainsi que les informations de connexion.
        - Le lien permettant de participer à la réunion est ajouté à tous les e-mails de confirmation et de rappel, comme illustré dans l’exemple suivant :

        :::image type="content" source="media/bookings-teams-meeting-link.jpg" alt-text="Exemple de lien pour participer à une réunion teams dans bookings":::

        > [!NOTE]
        > Les réunions de teams peuvent être jointes via l’application mobile Teams, l’application de bureau Teams, dans un navigateur Web ou via le téléphone. Nous vous recommandons vivement d’activer teams comme service de réunion en ligne par défaut pour votre client, afin que la meilleure expérience en matière de rendez-vous virtuels.

    - Activation
        - Les rendez-vous ne contiennent pas d’option de réunion et tous les champs liés à la réunion qui apparaissent lorsque l’option **Ajouter une réunion en ligne** est activée ne s’affichent pas.

6. **Durée par défaut : durée**pendant laquelle toutes les réunions seront réservées. Le temps est bloqué à partir de l’heure de début, qui est sélectionnée lors de la réservation. L’heure de rendez-vous complète sera bloquée sur les calendriers du personnel.

7. **Temps de la mémoire tampon que votre client ne peut pas livrer**: l’activation de ce paramètre permet d’ajouter du temps supplémentaire au calendrier de l’équipe à chaque fois qu’un rendez-vous est enregistré.

    Le temps sera bloqué sur le calendrier du personnel et influant sur les informations de disponibilité. Cela signifie que si un rendez-vous se termine à 3:00 h et que 10 minutes de temps de la mémoire tampon ont été ajoutées à la fin de la réunion, le calendrier du personnel s’affichera comme étant occupé et non réservables jusqu’à 3:10PM. Cela peut être utile si votre personnel a besoin de temps avant la réunion pour se préparer, comme un médecin examinant le graphique d’un patient ou un conseiller financier qui prépare des informations de compte pertinentes. Elle peut également être utile après une réunion, par exemple lorsqu’une personne a besoin de temps pour se déplacer vers un autre emplacement.

8. **Autoriser le client à gérer sa réservation**: ce paramètre détermine si le client ou notthe peut modifier ou annuler sa réservation, à condition qu’il ait été enregistré dans l’onglet Calendrier de l’application Web bookings.

    - Activé

        Le bouton **gérer la réservation** apparaît dans le message électronique de confirmation du client. Lorsque ce bouton est sélectionné par le client, trois options s’affichent :
        - **Replanifier** La sélection de cette option amène l’utilisateur à une page libre-service spécifique à un service, dans laquelle il peut sélectionner une nouvelle heure et/ou date pour le même service et le même membre du personnel de la réservation d’origine. Notez que même si le membre de l’équipe d’origine est lié à la réservation replanifiée par défaut, l’utilisateur peut également modifier le membre du personnel.
        - **Annuler la réservation** Cette opération annule la réservation et la supprime du calendrier de l’équipe.
        - **Nouvelle réservation** Cette option permet d’afficher l’utilisateur sur la page libre-service avec tous les services et le personnel mentionnés, pour la planification d’une nouvelle réservation.

        :::image type="content" source="media/bookings-manage-booking-button.jpg" alt-text="Bouton gérer les réservations dans bookings":::

        Nous vous recommandons de laisser ce paramètre activé uniquement si vous êtes à l’aise avec les clients qui accèdent à la page libre-service.

    - Activation

        L’utilisateur n’a pas la possibilité de Replanifier ou d’annuler sa réservation lorsqu’il livre l’onglet Calendrier de l’application Web bookings. Toutefois, lorsque vous reportez la page libre-service, les clients disposent toujours du bouton **gérer la réservation** et de toutes ses options, même si ce paramètre est désactivé.

        Nous vous recommandons de désactiver ce paramètre si vous souhaitez limiter l’accès à la page libre-service. De plus, nous vous suggérons d’ajouter du texte à vos courriers de confirmation et de rappel qui indiquent à vos clients comment effectuer des modifications à leur réservation par d’autres moyens, par exemple en appelant le bureau ou en utilisant l’assistance technique.

9. **Nombre maximal d’participants par événement** Ce paramètre vous permet de créer des services qui nécessitent la possibilité pour plusieurs personnes de réserver le même temps de rendez-vous et le même personnel (par exemple, une classe de pertinence). Le créneau horaire de rendez-vous pour le service, le personnel et le temps de rendez-vous sélectionné sera disponible jusqu’à ce que le nombre maximal de participants, spécifié par vous, ait été atteint. La capacité et les participants actuels des rendez-vous peuvent être affichés dans l’onglet Calendrier de l’application Web bookings.

    :::image type="content" source="media/bookings-maximum-attendees.jpg" alt-text="Exemple de définition des participants maximaux dans les réservations":::

10. **Prix par défaut**  Il s’agit du prix qui s’affiche sur la page libre-service. Si le champ **prix non défini** est sélectionné, aucun prix ou référence à un coût ou une tarification n’apparaît.

11. **Remarques** Ce champ apparaît dans l’événement de réservation pour le personnel réservé, ainsi que sur l’événement qui s’affiche sous l’onglet Calendrier de l’application Web bookings.

12. **Champs personnalisés** Cette section permet d’ajouter ou de supprimer des questions si le client doit répondre à une demande afin d’effectuer la réservation.

    - Le courrier, le numéro de téléphone, l’adresse et les notes du client sont des champs non amovibles, mais vous pouvez les rendre facultatifs en désélectionnant l’option **obligatoire** en regard de chaque champ.

    - Vous pouvez ajouter une question à choix multiple ou réponse de texte en sélectionnant **Ajouter une question**.

        Les champs personnalisés peuvent être utiles lors de la collecte des informations nécessaires à chaque fois que le rendez-vous spécifique est enregistré. Il s’agit par exemple du fournisseur d’assurance avant une visite de Clinic, du type de prêt pour les consultations de prêts, de la majeureté de l’étude pour un conseiller universitaire ou de l’ID du postulant pour les entretiens candidats.

13. **Rappels et confirmations** Les deux types de courriers électroniques sont envoyés aux clients, aux membres du personnel ou aux deux, à une période spécifiée avant le rendez-vous. Plusieurs messages peuvent être créés pour chaque rendez-vous, en fonction de vos préférences.

    - Les e-mails de confirmation et de rappel par défaut incluent des informations de base sur le rendez-vous, telles que le nom du client/client, le nom du membre du personnel, le service ou le rendez-vous enregistré et l’heure du rendez-vous. Pour les réunions en ligne, un lien vers une jointure sera également inclus. La possibilité de gérer la réservation peut également être incluse, si ce paramètre est activé (comme décrit ci-dessus à l’étape 8).

        :::image type="content" source="media/bookings-remind-confirm.jpg" alt-text="Courrier électronique de confirmation à partir de livres":::

    - Si vous le souhaitez, vous pouvez inclure le texte supplémentaire que vous souhaitez ici, par exemple des informations sur la replanification ou les clients qui doivent apporter le rendez-vous. Voici un exemple de texte personnalisé ajouté au message électronique de confirmation d’origine, affiché dans le champ de **confirmation informations supplémentaires pour le courrier** :

        :::image type="content" source="media/bookings-additional-info.jpg" alt-text="Informations supplémentaires dans un message électronique bookings":::

14. **Activer les notifications par SMS pour votre client** Si cette option est sélectionnée, les messages SMS sont envoyés au client, mais uniquement s’ils s’abonnent.

    - Zone opt-in de la réservation manuelle et de la page libre-service :

        :::image type="content" source="media/bookings-opt-In-boc.jpg" alt-text="Zone d’abonnement dans bookings":::

    - Les notifications par SMS se présenteront comme suit (Notez que les notifications SMS sont actuellement disponibles uniquement en Amérique du Nord) :

        :::image type="content" source="media/bookings-text-notifications.jpg" alt-text="Une notification textuelle à partir de livres":::

15. **Options de publication** Indiquez si ce service doit apparaître sous la forme réservables dans la page libre-service ou pour que le service réservables uniquement sous l’onglet Calendrier au sein de l’application Web bookings.

16. **Stratégie de planification** Ce paramètre détermine la manière dont les heures de rendez-vous sont affichées, ainsi que la période pendant laquelle les réservations peuvent être effectuées ou annulées.

17. **Notifications par courrier électronique** Définit quand les courriers électroniques sont envoyés au personnel de l’organisation et aux clients ou clients.

18. **Personnel** Cette case à cocher permet aux clients ou aux clients de choisir un membre du personnel spécifique pour leur rendez-vous.

    - Activé

        Les clients peuvent choisir parmi tous les collaborateurs affectés au rendez-vous lors de la réservation sur la page libre-service. La sélection de l’option **tout le monde** permettra aux réservations de choisir un membre du personnel disponible au hasard pour l’attribuer au rendez-vous.

    - Activation

        Les clients qui effectuent une réservation via la page libre-service peuvent sélectionner un service et une heure et une date. Le personnel disponible sera enregistré au hasard. Notez que certains membres du personnel peuvent toujours être sélectionnés lors de la réservation via l’onglet Calendrier de l’application Web bookings.

19. **Disponibilité** Les options suivantes déterminent le moment où le service peut être enregistré :

    - **Réservables lorsque le personnel est libre** Le service maintient la disponibilité en fonction du moment où le personnel est disponible pendant les heures d’ouverture, sans restrictions de temps supplémentaires.

    - **Heures personnalisées (toutes les semaines)** Le service dispose d’une couche supplémentaire de disponibilité qui peut être encore plus restreinte (en plus des heures d’ouverture ou des heures de travail du personnel). Utilisez cette option lorsque votre service peut uniquement être fourni ou effectué à un moment donné.

    - **Définir une disponibilité différente pour une plage de dates** Ce paramètre influe sur la disponibilité à un moment spécifique, au lieu d’une base récurrente. Par exemple, il peut être utilisé lorsqu’un ordinateur requis pour le service est temporairement en service et indisponible, ou lorsqu’une organisation est fermée pendant un congé.

20. **Affecter du personnel** Sélectionnez le personnel (à condition que vous ayez ajouté des membres du personnel à l’onglet personnel) qui sera réservables pour ce service spécifique. La sélection d’aucun personnel individuel entraîne l’affectation de tous les membres du personnel au service.