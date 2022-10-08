---
title: Gérer l'expérience de participation aux rendez-vous virtuels de Teams sur les navigateurs.
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
- highpri
ms.reviewer: hafarmer
description: Découvrez l'expérience de participation aux rendez-vous virtuels de Teams sur les navigateurs.
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.openlocfilehash: d9a64032610a3ef49b8d8bc5367901be80c7702a
ms.sourcegitcommit: 674dfa2cb2f20546d2f7822e09bacf0e12e2718b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68038838"
---
# <a name="manage-the-join-experience-for-teams-virtual-appointments-on-browsers"></a>Gérer l'expérience de participation aux rendez-vous virtuels de Teams sur les navigateurs.

Microsoft Teams permet aux utilisateurs de rejoindre facilement des rendez-vous virtuels sans avoir à télécharger Teams. Pour une expérience plus transparente, les participants peuvent participer à des rendez-vous tels que des visites médicales et des consultations financières à partir d’un bureau ou d’un navigateur mobile. Les participants n’ont pas besoin d’installer l’application Teams sur leur appareil.

Avec la jonction au navigateur, lorsqu’un participant rejoint un rendez-vous, il n’est pas invité à télécharger Teams. Au lieu de cela, Teams s’ouvre dans un navigateur, où le participant peut sélectionner **Rejoindre maintenant** pour rejoindre la réunion. Avec cette fonctionnalité, gardez à l’esprit que si Teams est déjà installé sur l’appareil, Teams s’ouvre dans un navigateur et non dans l’application.

Actuellement, la jonction au navigateur est disponible pour les rendez-vous planifiés par le biais des éléments suivants :

- [Application Bookings](https://support.microsoft.com/office/what-is-bookings-42d4e852-8e99-4d8f-9b70-d7fc93973cb5)
- Connecteur Microsoft Teams Electronic Health Record (EHR)

  - Intégration à [Cerner EHR](ehr-admin-cerner.md)
  - Intégration à [Epic EHR](ehr-admin-epic.md)

## <a name="set-up-browser-join"></a>Configurer la jonction au navigateur

### <a name="appointments-scheduled-through-the-bookings-app"></a>Rendez-vous planifiés via l’application Bookings

Les planificateurs de votre organisation peuvent activer cette fonctionnalité pour des types de rendez-vous spécifiques et pour des rendez-vous individuels dans l’application Bookings.

Une fois cette fonctionnalité activée, l’e-mail de confirmation ou le sms envoyé aux participants contient un lien de participation à une réunion qui ouvre Teams dans un navigateur de bureau ou mobile. Pour obtenir la liste des navigateurs pris en charge, consultez [Navigateurs pris en charge](#supported-browsers).

#### <a name="turn-on-browser-join-for-an-appointment-type"></a>Activer la jonction au navigateur pour un type de rendez-vous

Dans Bookings, accédez à **Paramètres** > **Types de rendez-vous**, sélectionnez un [type de rendez-vous](https://support.microsoft.com/office/create-an-appointment-type-810eac77-6a65-4dc8-964d-c00eadf43887), puis activez **Autoriser les participants à rejoindre à partir d’un navigateur**. Cela permet la jonction au navigateur pour tous les rendez-vous de ce type.

:::image type="content" source="media/browser-join-bookings-appointment-type.png" alt-text="Capture d'écran du paramètre Autoriser les participants à se joindre à partir d'un navigateur pour les types de rendez-vous dans l'application Bookings.":::

#### <a name="turn-on-browser-join-for-an-individual-appointment"></a>Activer la jonction au navigateur pour un rendez-vous individuel

Dans Bookings, sélectionnez **Nouvelle réservation**, puis activez **Autoriser les participants à se joindre à partir d’un navigateur**.

:::image type="content" source="media/browser-join-bookings-form.png" alt-text="Capture d’écran de l’option Autoriser les participants à se joindre à partir d’un paramètre de navigateur sur le nouveau formulaire de réservation dans l’application Bookings":::

### <a name="appointments-scheduled-through-the-teams-ehr-connector"></a>Rendez-vous planifiés via le connecteur DSE Teams

Aucune configuration n’est nécessaire pour vous ou votre personnel !

**Intégration à Cerner EHR**: le connecteur DSE Teams prend en charge les patients qui rejoignent des rendez-vous virtuels via un lien dans le SMS. Au moment du rendez-vous, les patients peuvent participer en appuyant sur le lien dans le SMS et Teams s’ouvre dans un navigateur.

**Intégration à Epic EHR**: le connecteur DSE Teams prend en charge les patients qui rejoignent des rendez-vous virtuels via MyChart web et mobile. Au moment du rendez-vous, les patients peuvent démarrer le rendez-vous à partir de MyChart à l’aide du bouton **Commencer la visite virtuelle**, et Teams s’ouvre dans un navigateur.

## <a name="supported-browsers"></a>Navigateurs pris en charge

Voici les navigateurs actuellement pris en charge. Nous prenons en charge la dernière version plus deux versions précédentes, sauf indication contraire.

|Plateforme  |Chrome |Safari |Edge (Chromium)|
|---------|:---|:---|:---:|
|Android   | &#x2714; &sup1;      |         |         |
|iOS    |         | &#x2714; &sup1; &sup2; |         |
|macOS     | &#x2714; | &#x2714;|         |
|Windows    | &#x2714; |   | &#x2714; |
|Ubuntu/Linux     | &#x2714;         |     |         |

&sup1; Le partage d’écran sortant n’est pas pris en charge sur iOS ou Android.

&sup2; Les applications iOS sur Safari ne peuvent pas sélectionner les périphériques de microphone et de haut-parleur. Par exemple, les appareils Bluetooth. Il s’agit d’une limitation du système d’exploitation, qui contrôle la sélection de l’appareil par défaut.

## <a name="things-to-consider"></a>Informations importantes

Le membre du personnel qui organise le rendez-vous peut partager son écran depuis son ordinateur de bureau, son téléphone mobile ou son client Web Teams avec un participant qui se joint à lui depuis un ordinateur de bureau ou un navigateur mobile. Toutefois, les participants ne peuvent pas partager leur écran à partir d’un navigateur de bureau ou mobile.

## <a name="related-articles"></a>Articles connexes

- [Rendez-vous virtuels avec Bookings et Teams](bookings-virtual-visits.md)
- [Créer un type de rendez-vous Bookings](https://support.microsoft.com/office/create-an-appointment-type-810eac77-6a65-4dc8-964d-c00eadf43887)
- [Se joindre à un rendez-vous Bookings en tant que participant](https://support.microsoft.com/office/join-a-bookings-appointment-as-an-attendee-95cea12d-2220-421f-a663-6efb20913c7f)
- [Rendez-vous virtuels avec Teams – Intégration à Cerner EHR](ehr-admin-cerner.md)
- [Rendez-vous virtuels avec Teams – Intégration à Epic EHR](ehr-admin-epic.md)
