---
title: Définir vos offres de service Bookings
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.localizationpriority: medium
ms.assetid: 4a1c391e-524f-48e0-bef8-185df3a9634b
description: Instructions pour entrer des informations sur les offres de service, notamment le nom du service, la description, l’emplacement, la durée et la tarification. Vous pouvez également marquer les employés qui sont qualifiés pour fournir le service.
ms.openlocfilehash: 0c302e8d84274fa2df8eea27362407ded4a468e3
ms.sourcegitcommit: db1e48af88995193f15bbd5962f5101a6088074b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2022
ms.locfileid: "65637778"
---
# <a name="define-your-service-offerings-in-bookings"></a>Définir vos offres de service dans Bookings

Lorsque vous définissez vos offres de service dans Microsoft Bookings, vous définissez un nom de service, une description, un emplacement (choisissez si vous souhaitez vous rencontrer en personne ou avoir une réunion en ligne), la durée, les rappels par défaut aux clients et au personnel, les notes internes sur le service et la tarification. Vous pouvez également marquer les employés qui sont qualifiés pour fournir le service. Ensuite, lorsque les clients viennent sur votre site web d’entreprise pour réserver un rendez-vous, ils peuvent voir exactement quels types de rendez-vous sont disponibles, choisir la personne qu’ils veulent fournir le service, et combien leur service va coûter.

Vous pouvez également ajouter des informations personnalisées et des URL à la confirmation par e-mail et aux rappels que vous envoyez lorsque quelqu’un réserve un service via votre page de réservation.

## <a name="create-the-service-details"></a>Créer les détails du service

1. Dans Microsoft 365, sélectionnez le lanceur d’applications, puis sélectionnez **Bookings**.

2. Accédez à **Vos** **calendarServices** >  et **sélectionnez Ajouter un nouveau service**.

3. Dans la page **Informations de base** , ajoutez vos sélections.

   **Nom du service** : entrez le nom de votre service. Il s’agit du nom qui s’affiche dans le menu déroulant de la page Calendrier. Ce nom s’affiche également lorsque quelqu’un ajoute manuellement un rendez-vous sur la page Calendrier et qu’il apparaît sous forme de vignette sur la page libre-service.

   **Description** : la description que vous entrez s’affiche lorsqu’un utilisateur clique sur l’icône d’informations sur la page libre-service.

   **Emplacement par défaut** : cet emplacement s’affiche sur les e-mails de confirmation et de rappel pour le personnel et les clients, et il s’affiche sur l’événement de calendrier créé pour la réservation.

   **Ajouter une réunion en ligne** : ce paramètre active ou désactive les réunions en ligne pour chaque rendez-vous, via Teams ou Skype, selon celui que vous configurez comme client par défaut pour le membre du personnel.

   - Activé:
     - Un lien vers une réunion Teams ou Skype, propre à la réservation, sera ajouté à l’événement de calendrier sur les calendriers du personnel et des clients, ainsi que des informations de connexion.
     - Le lien pour participer à la réunion sera ajouté à tous les e-mails de confirmation et de rappel, comme illustré dans l’exemple suivant :

       :::image type="content" source="media/bookings-teams-meeting-link.jpg" alt-text="Exemple de lien pour rejoindre Teams réunion dans Bookings.":::

       > [!NOTE]
       > Teams réunions peuvent être jointes via l’application mobile Teams, l’application de bureau Teams, dans un navigateur web ou via la connexion téléphonique. Nous vous recommandons vivement d’activer Teams en tant que service de réunion en ligne par défaut pour votre locataire, pour une expérience optimale de réservation de rendez-vous virtuels.

   - Handicapés:
     - Rendez-vous ne contient pas d’option de réunion, et tous les champs liés à la réunion qui s’affichent lorsque **l’option Ajouter une réunion en ligne** est activée ne s’affichent pas.

   **Durée** : il s’agit de la durée pendant laquelle toutes les réunions seront réservées. L’heure est bloquée à partir de l’heure de début, qui est sélectionnée lors de la réservation. Le temps de rendez-vous complet sera bloqué dans les calendriers du personnel.

   Durée de la **mémoire tampon** : l’activation de ce paramètre permet d’ajouter du temps supplémentaire au calendrier du personnel chaque fois qu’un rendez-vous est réservé.

   L’heure sera bloquée dans le calendrier du personnel et aura un impact sur les informations de disponibilité. Cela signifie que si un rendez-vous se termine à 15h00 et que 10 minutes de temps tampon ont été ajoutées à la fin de la réunion, le calendrier du personnel s’affiche comme occupé et non réservé jusqu’à 15h10. Cela peut s’avérer utile si votre personnel a besoin de temps avant une réunion pour se préparer, par exemple un médecin qui examine le dossier d’un patient ou un conseiller financier qui prépare les informations de compte pertinentes. Il peut également être utile après une réunion, par exemple lorsque quelqu’un a besoin de temps pour se rendre à un autre emplacement.

   **Prix non défini** : sélectionnez les options de prix qui s’affichent sur la page Self-Service. Si **le prix non défini** est sélectionné, aucun prix ou référence au coût ou à la tarification n’apparaît.

   **Remarques** : ce champ apparaît dans l’événement de réservation pour le personnel réservé, ainsi que sur l’événement qui apparaît sous l’onglet Calendrier dans l’application web Bookings.

   **Nombre maximal de participants par événement** : ce paramètre vous permet de créer des services qui nécessitent la possibilité pour plusieurs personnes de réserver le même temps de rendez-vous et le même personnel (par exemple, un cours de fitness). L’emplacement d’heure de rendez-vous pour le service, le personnel et l’heure sélectionnés sera disponible pour réserver jusqu’à ce que le nombre maximal de participants, spécifié par vous, soit atteint. La capacité de rendez-vous actuelle et les participants peuvent être affichés sous l’onglet Calendrier de l’application web Bookings.

   :::image type="content" source="media/bookings-maximum-attendees.jpg" alt-text="Exemple de définition du nombre maximal de participants dans Bookings":::

   **Laissez le client gérer sa réservation** : ce paramètre détermine si le client peut modifier ou annuler sa réservation, à condition qu’elle ait été réservée sous l’onglet Calendrier de l’application web Bookings.

   - Activé:

     Le bouton **Gérer la réservation** s’affiche dans l’e-mail de confirmation du client. Lorsque ce bouton est sélectionné par le client, trois options s’affichent :

     - **Reporter** Si vous sélectionnez cette option, l’utilisateur accède à une page Self-Service spécifique au service, où il peut sélectionner une nouvelle heure et/ou une nouvelle date pour le même service et le même membre du personnel dans la réservation d’origine. Notez que même si le membre du personnel d’origine est attaché à la réservation replanifiée par défaut, l’utilisateur a également la possibilité de modifier le membre du personnel.
     - **Annuler la réservation** Cela annule la réservation et la supprime du calendrier du personnel.
     - **Nouvelle réservation** Cette option permet à l’utilisateur d’accéder à la page Self-Service avec tous les services et le personnel répertoriés, pour planifier une nouvelle réservation.

        :::image type="content" source="media/bookings-manage-booking-button.jpg" alt-text="Bouton Gérer Bookings dans Bookings.":::

      Nous vous recommandons de laisser ce paramètre activé uniquement si vous êtes à l’aise avec les clients qui accèdent à la page Self-Service.

   - Handicapés:

     L’utilisateur n’a pas la possibilité de replanifier ou d’annuler sa réservation lorsqu’il réserve via l’onglet Calendrier de l’application web Bookings. Toutefois, lors de la réservation via la page Self-Service, les clients disposent toujours du bouton **Gérer la réservation** et de toutes ses options, même lorsque ce paramètre est désactivé.

     Nous vous recommandons de désactiver ce paramètre si vous souhaitez limiter l’accès à la page Self-Service. En outre, nous vous suggérons d’ajouter du texte à vos e-mails de confirmation et de rappel qui indiquent à vos clients comment apporter des modifications à leur réservation par d’autres moyens, par exemple en appelant le bureau ou en envoyant un e-mail au support technique.

4. Dans la page **Options de disponibilité** , vous pouvez voir les options que vous avez sélectionnées dans votre **page Booking** pour votre stratégie de planification et la disponibilité de votre personnel. Pour plus d’informations, consultez [Définir vos stratégies de planification](set-scheduling-policies.md).

5. **Prix par défaut**  Il s’agit du prix qui s’affiche sur la page Self-Service. Si **le prix non défini** est sélectionné, aucun prix ou référence au coût ou à la tarification n’apparaît.

6. **Notes** Ce champ apparaît dans l’événement de réservation pour le personnel réservé, ainsi que dans l’événement qui apparaît sous l’onglet Calendrier de l’application web Bookings.

7. **Les champs personnalisés** peuvent être utiles lors de la collecte d’informations nécessaires chaque fois que le rendez-vous spécifique est réservé. Il peut s’agir, par exemple, d’un fournisseur d’assurance avant une visite à la clinique, d’un type de prêt pour les consultations sur les prêts, d’une grande partie de l’étude pour les conseils universitaires ou d’un ID de candidat pour les entrevues de candidats. Ces champs s’affichent sur la page Booking lorsque vos clients réservent des rendez-vous avec vous et votre personnel.

   L’e-mail, le numéro de téléphone, l’adresse et les notes du client sont des champs non amovibles, mais vous pouvez les rendre facultatifs en désélectionnant **Obligatoire** à côté de chaque champ.

8. Dans la page **Rappels et confirmations** , vous pouvez configurer les rappels et les notifications que vous envoyez. Les rappels et les notifications sont envoyés aux clients, aux membres du personnel ou aux deux, à une heure spécifiée avant le rendez-vous. Plusieurs messages peuvent être créés pour chaque rendez-vous, en fonction de vos préférences.

   :::image type="content" source="media/bookings-remind-confirm-2.png" alt-text="Un e-mail de confirmation de Bookings.":::

   Vous pouvez inclure tout texte supplémentaire que vous souhaitez ici, par exemple des informations sur le replanification ou sur ce que les clients doivent apporter pour le rendez-vous. Voici un exemple de texte personnalisé ajouté à l’e-mail de confirmation d’origine, vu dans le champ **Informations supplémentaires sur la confirmation par e-mail** :

   :::image type="content" source="media/bookings-additional-info.jpg" alt-text="Informations supplémentaires dans un e-mail Bookings.":::

9. **Activer les notifications par SMS pour votre client** S’il est sélectionné, SMS messages sont envoyés au client, mais uniquement s’ils y sont abonnés.

   - Zone d’acceptation sur la page de réservation manuelle et de Self-Service :

     :::image type="content" source="media/bookings-opt-In-boc.jpg" alt-text="Zone d’adhésion dans Bookings.":::

   - Les notifications par SMS se présentent comme suit (notez que SMS notifications ne sont actuellement disponibles que dans Amérique du Nord) :

     :::image type="content" source="media/bookings-text-notifications.jpg" alt-text="Notification de texte de Bookings.":::

10. Les **options de planification par défaut** sont activées par défaut. Désactivez le bouton bascule si vous souhaitez personnaliser la façon dont les clients réservent un membre du personnel en particulier.

11. **Options de publication** Choisissez si ce service doit apparaître comme pouvant être réservé sur la page Self-Service, ou pour rendre le service accessible uniquement sous l’onglet Calendrier dans l’application web Bookings.
