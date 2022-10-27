---
title: Définir vos offres de service Bookings
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
ms.assetid: 4a1c391e-524f-48e0-bef8-185df3a9634b
description: Instructions pour entrer des informations sur les offres de service, notamment le nom du service, la description, l’emplacement, la durée et la tarification. Vous pouvez également étiqueter les employés qualifiés pour fournir le service.
ms.openlocfilehash: b598992d04663d8589a237f8f088c87a65265498
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68720435"
---
# <a name="define-your-service-offerings-in-bookings"></a>Définir vos offres de service dans Bookings

Lorsque vous définissez vos offres de service dans Microsoft Bookings, vous définissez un nom de service, une description, un emplacement (choisir si vous souhaitez vous rencontrer en personne ou une réunion en ligne), la durée, les rappels par défaut aux clients et au personnel, les notes internes sur le service et la tarification. Vous pouvez également étiqueter les employés qualifiés pour fournir le service. Ensuite, lorsque les clients viennent sur le site web de votre entreprise pour prendre rendez-vous, ils peuvent voir exactement quels types de rendez-vous sont disponibles, choisir la personne qu’ils souhaitent fournir le service et combien leur service coûtera.

Vous pouvez également ajouter des informations personnalisées et des URL aux e-mails de confirmation et aux rappels que vous envoyez quand quelqu’un réserve un service via votre page de réservation.

## <a name="watch-create-a-new-service"></a>Regarder : Créer un service

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWuKXH]

## <a name="steps"></a>Étapes

1. Dans Microsoft 365, sélectionnez le lanceur d’applications, puis **Bookings**.

2. Accédez à Vos **services** **de calendrier** >  et sélectionnez **Ajouter un nouveau service**.

3. Dans la page **Détails de base** , ajoutez vos sélections.

   **Nom du service** : entrez le nom de votre service. Il s’agit du nom qui apparaîtra dans le menu déroulant de la page Calendrier. Ce nom apparaît également lorsque quelqu’un ajoute manuellement un rendez-vous sur la page Calendrier, et il apparaît sous forme de vignette sur la page libre-service.

   **Description** : la description que vous entrez est celle qui s’affiche lorsqu’un utilisateur clique sur l’icône d’informations dans la page libre-service.

   **Emplacement par défaut** : cet emplacement est celui qui sera affiché sur les e-mails de confirmation et de rappel pour le personnel et les clients, et il sera affiché sur l’événement de calendrier créé pour la réservation.

   **Ajouter une réunion en ligne** : ce paramètre active ou désactive les réunions en ligne pour chaque rendez-vous, via Teams ou Skype, selon celui que vous configurez comme client par défaut pour le membre du personnel.

   - Activé:
     - Un lien vers une réunion Teams ou Skype, propre à la réservation, sera ajouté à l’événement de calendrier sur les calendriers du personnel et des clients, ainsi que des informations de connexion.
     - Le lien pour rejoindre la réunion sera ajouté à tous les e-mails de confirmation et de rappel, comme indiqué dans l’exemple suivant :

       :::image type="content" source="media/bookings-teams-meeting-link.jpg" alt-text="Exemple de lien pour rejoindre une réunion Teams dans Bookings.":::

       > [!NOTE]
       > Les réunions Teams peuvent être jointes via l’application mobile Teams, l’application de bureau Teams, dans un navigateur web ou via la connexion téléphonique. Nous vous recommandons vivement d’activer Teams comme service de réunion en ligne par défaut pour votre locataire, pour une expérience optimale lors de la réservation de rendez-vous virtuels.

   - Handicapés:
     - Les rendez-vous ne contiennent pas d’option de réunion, et tous les champs relatifs à la réunion qui s’affichent lorsque **l’option Ajouter une réunion en ligne** est activée ne s’affichent pas.

   **Durée** : durée pendant laquelle toutes les réunions seront réservées. L’heure est bloquée à partir de l’heure de début, qui est sélectionnée lors de la réservation. Le temps de rendez-vous complet sera bloqué sur les calendriers du personnel.

   **Temps de mémoire tampon** : l’activation de ce paramètre permet d’ajouter du temps supplémentaire au calendrier du personnel chaque fois qu’un rendez-vous est pris.

   Le temps sera bloqué sur le calendrier du personnel et aura un impact sur les informations de disponibilité. Cela signifie que si un rendez-vous se termine à 15h00 et que 10 minutes de temps tampon ont été ajoutées à la fin de la réunion, le calendrier du personnel s’affiche comme occupé et non réservable jusqu’à 15h10. Cela peut être utile si votre personnel a besoin de temps avant une réunion pour se préparer, comme un médecin qui examine le tableau d’un patient ou un conseiller financier qui prépare les renseignements pertinents sur les comptes. Il peut également être utile après une réunion, par exemple quand quelqu’un a besoin de temps pour se rendre à un autre endroit.

   **Prix non défini** : sélectionnez les options de prix qui s’afficheront sur la page Self-Service. Si **l’option Prix non défini** est sélectionnée, aucun prix ou référence au coût ou à la tarification n’apparaît.

   **Remarques** : ce champ apparaît dans l’événement de réservation pour le personnel réservé, ainsi que dans l’événement qui apparaît sous l’onglet Calendrier de l’application web Bookings.

   **Nombre maximal de participants par événement** : ce paramètre vous permet de créer des services qui nécessitent la possibilité pour plusieurs personnes de réserver la même heure de rendez-vous et le même personnel (par exemple, une classe de fitness). Le créneau horaire de rendez-vous pour le service, le personnel et le temps sélectionnés seront disponibles pour réserver jusqu’à ce que le nombre maximal de participants, spécifié par vous, soit atteint. La capacité de rendez-vous actuelle et les participants peuvent être affichés sous l’onglet Calendrier de l’application web Bookings.

   :::image type="content" source="media/bookings-maximum-attendees.jpg" alt-text="Exemple de définition du nombre maximal de participants dans Bookings":::

   **Laisser le client gérer sa réservation** : ce paramètre détermine si le client peut modifier ou annuler sa réservation, à condition qu’elle ait été réservée via l’onglet Calendrier de l’application web Bookings.

   - Activé:

     Le bouton **Gérer Booking** apparaît dans l’e-mail de confirmation du client. Lorsque ce bouton est sélectionné par le client, trois options s’affichent :

     - **Reporter** La sélection de cette option permet à l’utilisateur d’accéder à une page de Self-Service spécifique au service, où il peut sélectionner une nouvelle heure et/ou une nouvelle date pour le même service et le même membre du personnel de la réservation d’origine. Notez que même si le membre du personnel d’origine est attaché à la réservation replanifiée par défaut, l’utilisateur a également la possibilité de changer le membre du personnel.
     - **Annuler la réservation** Cela annule la réservation et la supprime du calendrier du personnel.
     - **Nouvelle réservation** Cette option permet à l’utilisateur d’accéder à la page Self-Service avec tous les services et le personnel répertoriés pour la planification d’une nouvelle réservation.

        :::image type="content" source="media/bookings-manage-booking-button.jpg" alt-text="Bouton Gérer les réservations dans Bookings.":::

      Nous vous recommandons de ne laisser ce paramètre activé que si vous êtes à l’aise avec les clients qui accèdent à la page Self-Service.

   - Handicapés:

     L’utilisateur n’a pas la possibilité de replanifier ou d’annuler sa réservation lorsqu’il réserve via l’onglet Calendrier de l’application web Bookings. Toutefois, lors de la réservation via la page Self-Service, les clients disposent toujours du bouton **Gérer la réservation** et de toutes ses options, même si ce paramètre est désactivé.

     Nous vous recommandons de désactiver ce paramètre si vous souhaitez limiter l’accès à la page Self-Service. En outre, nous vous suggérons d’ajouter du texte à vos e-mails de confirmation et de rappel qui indique à vos clients comment apporter des modifications à leur réservation par d’autres moyens, par exemple en appelant le bureau ou en envoyant un e-mail au support technique.

4. Dans la page **Options de disponibilité** , vous pouvez voir les options que vous avez sélectionnées dans votre **page Réservation** pour votre stratégie de planification et la disponibilité de votre personnel. Pour plus d’informations, consultez [Définir vos stratégies de planification](set-scheduling-policies.md).

5. **Prix par défaut**  Il s’agit du prix qui s’affichera sur la page Self-Service. Si **l’option Prix non défini** est sélectionnée, aucun prix ou référence au coût ou à la tarification n’apparaît.

6. **Notes** Ce champ apparaît dans l’événement de réservation pour le personnel réservé, ainsi que dans l’événement qui apparaît sous l’onglet Calendrier de l’application web Bookings.

7. **Les champs personnalisés** peuvent être utiles lors de la collecte des informations nécessaires chaque fois que le rendez-vous spécifique est réservé. Par exemple, le fournisseur d’assurance avant une visite à la clinique, le type de prêt pour les consultations de prêt, la majeure d’étude pour les conseils universitaires ou la pièce d’identité du candidat pour les entrevues avec les candidats. Ces champs s’affichent dans la page Booking lorsque vos clients réservent des rendez-vous avec vous et votre personnel.

   L’adresse e-mail, le numéro de téléphone, l’adresse et les notes du client sont des champs non amovibles, mais vous pouvez les rendre facultatifs en désélectionnant **Obligatoire** en regard de chaque champ.

8. Dans la page **Rappels et confirmations** , vous pouvez configurer des rappels et des notifications que vous envoyez. Les rappels et les notifications sont envoyés aux clients, aux membres du personnel ou aux deux, à un moment spécifié avant le rendez-vous. Plusieurs messages peuvent être créés pour chaque rendez-vous, selon vos préférences.

   :::image type="content" source="media/bookings-remind-confirm-2.png" alt-text="Un e-mail de confirmation de Bookings.":::

   Vous pouvez inclure tout texte supplémentaire que vous souhaitez ici, comme des informations sur la replanification ou ce que les clients doivent apporter pour le rendez-vous. Voici un exemple de texte personnalisé ajouté à l’e-mail de confirmation d’origine, vu dans le champ **Informations supplémentaires pour Email Confirmation** :

   :::image type="content" source="media/bookings-additional-info.jpg" alt-text="Informations supplémentaires dans un e-mail Bookings.":::

9. **Activer les notifications par SMS pour votre client** Si cette option est sélectionnée, les SMS sont envoyés au client, mais uniquement s’il l’accepte.

   - Zone d’inscription sur la page de réservation et de Self-Service manuelles :

     :::image type="content" source="media/bookings-opt-In-boc.jpg" alt-text="Zone d’inscription dans Bookings.":::

   - Les notifications par SMS se présentent comme suit (notez que les notifications SMS ne sont actuellement disponibles que dans Amérique du Nord) :

     :::image type="content" source="media/bookings-text-notifications.jpg" alt-text="Notification par SMS de Bookings.":::

10. Les **options de planification par défaut** sont activées par défaut. Désactivez le bouton bascule si vous souhaitez personnaliser la façon dont les clients réservent un membre du personnel particulier.

11. **Options de publication** Indiquez si ce service doit apparaître comme pouvant être réservé dans la page Self-Service, ou si vous souhaitez qu’il soit réservé uniquement sous l’onglet Calendrier de l’application web Bookings.
