---
title: Définir vos offres de services dans Bookings
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
localization_priority: Normal
ms.assetid: 4a1c391e-524f-48e0-bef8-185df3a9634b
description: Instructions pour entrer des informations sur les offres de services, notamment le nom du service, la description, l’emplacement, la durée et la tarification. Vous pouvez également marquer les employés qualifiés pour fournir le service.
ms.openlocfilehash: acf7f7be1a5c5d70215406ec0a3f375eb0dfa89d
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58572358"
---
# <a name="define-your-service-offerings-in-bookings"></a>Définir vos offres de services dans Bookings

Lorsque vous définissez vos offres de services dans Microsoft Bookings, vous définissez un nom de service, une description, un emplacement (indiquez si vous souhaitez vous réunir en personne ou avoir une réunion en ligne), la durée, les rappels par défaut aux clients et au personnel, les notes internes sur le service et les tarifs. Vous pouvez également marquer les employés qualifiés pour fournir le service. Ensuite, lorsque les clients viennent sur votre site web d’entreprise pour réserver un rendez-vous, ils peuvent voir exactement quels types de rendez-vous sont disponibles, choisir la personne à qui ils souhaitent fournir le service et le coût de leur service.

Vous pouvez également ajouter des URL et des informations personnalisées à la confirmation par courrier électronique et aux rappels que vous envoyez lorsque quelqu’un livre un service via votre page de réservation.

## <a name="create-the-service-details"></a>Créer les détails du service

1. Go to the [Manage services page](https://outlook.office.com/bookings/services) and select Add a **service**.

2. **Nom du** service : entrez le nom de votre service. Il s’agit du nom qui apparaîtra dans le menu déroulant de la page Calendrier. Ce nom s’affiche également lorsque quelqu’un ajoute manuellement un rendez-vous sur la page Calendrier et qu’il apparaît sous la page libre-service sous la vignette.

3. **Description**: la description que vous entrez s’affiche lorsqu’un utilisateur clique sur l’icône d’informations sur la page libre-service.

4. **Emplacement par** défaut : cet emplacement s’affiche sur les messages de confirmation et de rappel pour le personnel et les clients, et il s’affiche sur l’événement de calendrier créé pour la réservation.

5. Ajouter une réunion en ligne : ce paramètre active ou désactive les réunions en ligne pour chaque rendez-vous, via Teams ou Skype, selon celui que vous configurez comme client par défaut pour le membre du personnel.

    - Activé :

        - Un lien vers une réunion Teams ou Skype, propre à la réservation, sera ajouté à l’événement de calendrier sur les calendriers du personnel et des clients, ainsi que des informations de connexion.
        - Le lien pour participer à la réunion est ajouté à tous les messages de confirmation et de rappel, comme illustré dans l’exemple suivant :

        :::image type="content" source="media/bookings-teams-meeting-link.jpg" alt-text="Exemple de lien pour rejoindre Teams réunion dans Bookings.":::

        > [!NOTE]
        > Teams réunions peuvent être jointes via l’application mobile Teams, l’application de bureau Teams, dans un navigateur Web ou via le numéro de téléphone. Nous vous recommandons vivement d Teams en tant que service de réunion en ligne par défaut pour votre client, pour une expérience de réservation de rendez-vous virtuels de qualité.

    - Désactivé :
        - Les rendez-vous ne contiennent pas d’option de réunion  et tous les champs relatifs à la réunion qui apparaissent lorsque l’option Ajouter une réunion en ligne est activée ne s’affichent pas.

6. **Durée par** défaut : il s’agit de la durée de réservation de toutes les réunions. L’heure est bloquée à partir de l’heure de début, qui est sélectionnée pendant la réservation. L’heure de rendez-vous complète sera bloquée sur les calendriers du personnel.

7. Temps tampon que votre client ne peut pas réserver : l’activation de ce paramètre permet **d’ajouter** du temps supplémentaire au calendrier du personnel chaque fois qu’un rendez-vous est réservé.

    L’heure sera bloquée sur le calendrier du personnel et aura un impact sur les informations de libre/occupé. Cela signifie que si un rendez-vous se termine à 15 h 00 et que 10 minutes de temps tampon ont été ajoutées à la fin de la réunion, le calendrier du personnel s’affiche comme occupé et non réservé jusqu’à 15 h 10. Cela peut être utile si votre personnel a besoin de temps avant une réunion pour se préparer, tel qu’un médecin qui examine le graphique d’un patient ou un conseiller financier qui prépare les informations de compte pertinentes. Il peut également être utile après une réunion, par exemple lorsque quelqu’un a besoin de temps pour se déplacer vers un autre emplacement.

8. **Laisser le** client gérer sa réservation : ce paramètre détermine si le client peut modifier ou annuler sa réservation, à condition qu’elle a été réservée via l’onglet Calendrier de l’application Web Bookings.

    - Activé :

        Le **bouton Gérer la** réservation apparaît dans l’e-mail de confirmation du client. Lorsque ce bouton est sélectionné par le client, trois options s’affichent :
        - **Reprogrammer** La sélection de cette option amène l’utilisateur vers une page Self-Service spécifique au service, où il peut sélectionner une nouvelle heure et/ou une nouvelle date pour le même service et le même membre du personnel à partir de la réservation d’origine. Notez que même si le membre du personnel d’origine est joint par défaut à la réservation reprogrammée, l’utilisateur a également la possibilité de le modifier.
        - **Annuler la réservation** Cela annule la réservation et la supprime du calendrier du personnel.
        - **Nouvelle réservation** Cette option permet à l’utilisateur d'Self-Service page avec tous les services et le personnel répertoriés, pour planifier une nouvelle réservation.

        :::image type="content" source="media/bookings-manage-booking-button.jpg" alt-text="Bouton Gérer les réservations dans Bookings.":::

        Nous vous recommandons de laisser ce paramètre activé uniquement si vous êtes à l’aise avec les clients qui accèdent à Self-Service page.

    - Désactivé :

        L’utilisateur n’a pas la possibilité de reprogrammer ou d’annuler sa réservation lorsqu’il se réserve sous l’onglet Calendrier de l’application Web Bookings. Toutefois, lors de la réservation via la page  Self-Service, les clients auront toujours le bouton Gérer la réservation et toutes ses options, même lorsque ce paramètre est désactivé.

        Nous vous recommandons de désactiver ce paramètre si vous souhaitez limiter l’accès à Self-Service page. En outre, nous vous suggérons d’ajouter du texte à vos e-mails de confirmation et de rappel qui indique à vos clients comment apporter des modifications à leur réservation par d’autres moyens, par exemple en appelant le bureau ou en appelant le service d’aide.

9. **Nombre maximal de participants par événement** Ce paramètre vous permet de créer des services qui nécessitent la possibilité pour plusieurs personnes de réserver la même heure de rendez-vous et le même personnel (par exemple, un cours de mise en forme). Le créneau horaire du rendez-vous pour le service, le personnel et l’heure sélectionnés pourra être réservé jusqu’à ce que le nombre maximal de participants, spécifié par vous, soit atteint. La capacité actuelle des rendez-vous et les participants peuvent être vus dans l’onglet Calendrier de l’application Web Bookings.

    :::image type="content" source="media/bookings-maximum-attendees.jpg" alt-text="Exemple de définition du nombre maximal de participants dans Bookings.":::

10. **Prix par défaut**  Il s’agit du prix qui s’affiche sur Self-Service page. Si **le prix non définie** est sélectionné, aucun prix ou référence au coût ou à la tarification n’apparaîtra.

11. **Remarques** Ce champ apparaît dans l’événement de réservation pour le personnel réservé, ainsi que dans l’événement qui apparaît sous l’onglet Calendrier dans l’application web Bookings.

12. **Champs personnalisés** Cette section permet d’ajouter ou de supprimer des questions si le client doit y répondre pour pouvoir le faire.

    - Le courrier électronique, le numéro de téléphone, l’adresse et les notes du client sont des champs non amovibles, mais vous pouvez les rendre facultatifs en désélectionner **Obligatoire** à côté de chaque champ.

    - Vous pouvez ajouter une question à choix multiple ou à une réponse texte en sélectionnant **Ajouter une question.**

        Les champs personnalisés peuvent être utiles lors de la collecte d’informations nécessaires chaque fois que le rendez-vous spécifique est réservé. Il peut s’agir, par exemple, d’un fournisseur d’assurance avant une visite à l’emploi, d’un type de prêt pour les prêts, d’études principales pour les conseils scolaires ou d’un ID de candidat à un entretien.

13. **Rappels et confirmations** Les deux types d’e-mails sont envoyés aux clients, aux membres du personnel ou aux deux, à une période spécifiée avant le rendez-vous. Plusieurs messages peuvent être créés pour chaque rendez-vous, selon vos préférences.

    - Les messages de confirmation et de rappel par défaut incluent des informations de base sur le rendez-vous, telles que le nom du client/client, le nom du membre du personnel, le service ou le rendez-vous réservé et l’heure du rendez-vous. Pour les réunions en ligne, un lien pour participer sera également inclus. La possibilité de gérer la réservation peut également être incluse si ce paramètre est activé (comme décrit ci-dessus à l’étape 8).

        :::image type="content" source="media/bookings-remind-confirm.jpg" alt-text="Un e-mail de confirmation de Bookings.":::

    - Si vous le souhaitez, vous pouvez inclure tout texte supplémentaire que vous souhaitez ici, par exemple des informations sur la planification ou sur ce que les clients doivent apporter pour le rendez-vous. Voici un exemple de texte personnalisé ajouté à l’e-mail de confirmation d’origine, visible dans le champ Informations supplémentaires pour la **confirmation du courrier** électronique :

        :::image type="content" source="media/bookings-additional-info.jpg" alt-text="Informations supplémentaires dans un e-mail Bookings.":::

14. **Activer les notifications par SMS pour votre client** S’il est sélectionné, les messages SMS sont envoyés au client, mais uniquement s’il l’a choisi.

    - Zone d’inscription sur la page de réservation Self-Service manuelle :

        :::image type="content" source="media/bookings-opt-In-boc.jpg" alt-text="Zone d’inscription dans Bookings.":::

    - Les notifications par SMS ressembleront à ce qui suit (notez que les notifications par SMS sont actuellement uniquement disponibles en Amérique du Nord) :

        :::image type="content" source="media/bookings-text-notifications.jpg" alt-text="Une notification texte de Bookings.":::

15. **Options de publication** Choisissez si ce service doit être réservé sur la page Self-Service ou s’il doit être réservé uniquement sous l’onglet Calendrier de l’application Web Bookings.

16. **Stratégie de planification** Ce paramètre détermine la façon dont les heures de rendez-vous sont vues et la période pendant laquelle les réservations peuvent être réalisées ou annulées.

17. **Notifications par courrier électronique** Définit le moment où les e-mails sont envoyés au personnel de l’organisation et aux clients ou clients.

18. **Personnel** La sélection de cette case à cocher permet aux clients ou aux clients de choisir un membre du personnel spécifique pour leur rendez-vous.

    - Activé :

        Les clients peuvent choisir parmi tous les membres du personnel affectés au rendez-vous lors de la réservation sur Self-Service page. Si vous sélectionnez l’option **Tout** le monde, Bookings choisira de manière aléatoire un membre du personnel disponible à affecter au rendez-vous.

    - Désactivé :

        Les clients qui effectuent une réservation via la page Self-Service peuvent sélectionner un service, ainsi qu’une heure et une date. Le personnel disponible sera réservé de manière aléatoire. Notez que des membres du personnel spécifiques peuvent toujours être sélectionnés lors de la réservation via l’onglet Calendrier dans l’application Web Bookings.

19. **Disponibilité** Les options suivantes déterminent quand le service peut être réservé :

    - **Réservation possible lorsque le personnel est gratuit** Le service maintient la disponibilité en fonction du moment où le personnel est disponible pendant les heures d’ouverture, sans restrictions de temps supplémentaires.

    - **Heures personnalisées (toutes les semaines périodiques)** Le service dispose d’une couche de disponibilité supplémentaire qui peut être davantage restreinte (en plus de limiter les heures d’ouverture ou les heures de travail). Utilisez cette option lorsque votre service ne peut être fourni ou exécuté qu’à un moment précis.

    - **Définir une disponibilité différente pour une plage de dates** Ce paramètre a une incidence sur la disponibilité à un moment donné, et non sur une base périodique. Par exemple, cela peut être utilisé lorsqu’un ordinateur nécessaire au service est temporairement mis en service et indisponible, ou lorsqu’une organisation est fermée pour un congé.

20. **Affecter du personnel** Sélectionnez le personnel (à condition que vous avez ajouté des membres du personnel à l’onglet Personnel) qui pourra être réservé pour ce service spécifique. Si vous ne sélectionnez aucun personnel individuel, tous les membres du personnel seront affectés au service.