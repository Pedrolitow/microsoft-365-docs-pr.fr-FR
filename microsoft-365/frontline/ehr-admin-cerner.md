---
title: Rendez-vous virtuels avec Teams – Intégration à Cerner EHR
author: LanaChin
ms.author: v-lanachin
manager: samanro
audience: ITPro
ms.topic: conceptual
ms.service: microsoft-365-frontline
search.appverid: MET150
searchScope:
- Microsoft Teams
- Microsoft Cloud for Healthcare
f1.keywords:
- NOCSH
ms.localizationpriority: high
ms.collection:
- M365-collaboration
- Teams_ITAdmin_Healthcare
- microsoftcloud-healthcare
- m365solution-healthcare
- m365solution-scenario
- m365-frontline
- highpri
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.reviewer: ansantam
description: Découvrez comment intégrer le connecteur DMI Teams pour permettre aux prestataires de santé de votre organisation d’effectuer des rendez-vous virtuels avec des patients ou d’autres fournisseurs dans Teams directement à partir du système DMI Cerner.
ms.openlocfilehash: c04d2840c808fbaa98717a64288df372aeab19cc
ms.sourcegitcommit: 674dfa2cb2f20546d2f7822e09bacf0e12e2718b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68043744"
---
# <a name="virtual-appointments-with-teams---integration-into-cerner-ehr"></a>Rendez-vous virtuels avec Teams – Intégration à Cerner EHR

Le connecteur Dossier médical informatisé (DMI) Microsoft Teams permet aux médecins de lancer facilement un rendez-vous virtuel avec les patients ou de consulter un autre fournisseur dans Microsoft Teams directement à partir du système DMI Cerner. Basé sur le cloud Microsoft 365, Teams permet une collaboration et une communication simples et sécurisées avec les outils de conversation, de vidéo, de voix et de santé dans un hub unique qui prend en charge la conformité avec HIPAA, la certification HITECH, etc.

La plateforme de communication et de collaboration de Teams permet aux médecins de réduire facilement l’encombrement des systèmes fragmentés afin qu’ils puissent se concentrer sur la fourniture des meilleurs soins possibles. Avec le connecteur DSE Teams, vous pouvez :

- Effectuez des rendez-vous virtuels Teams à partir de votre système Cerner DMI avec un flux de travail clinique intégré.
- Permettre aux patients de rejoindre des rendez-vous virtuels Teams à partir de notifications par e-mail ou SMS.
- Affichez les rapports de données de consommation et les informations de qualité des appels personnalisables pour les rendez-vous connectés à un DMI.

Cet article explique comment installer et configurer le connecteur DSE Teams pour qu’il s’intègre à la plateforme Cerner. Il vous donne également une vue d’ensemble de l’expérience de rendez-vous virtuels Teams à partir du système CERNER EHR.

## <a name="before-you-begin"></a>Avant de commencer

> [!NOTE]
> Veillez à parler à votre représentant Cerner et à consulter votre guide d’intégration Cerner avant d’activer l’intégration.

### <a name="prerequisites"></a>Configuration requise

Avant d’intégrer le connecteur DSE Teams dans votre organisation de santé, vous devez disposer des éléments suivants :

- Un abonnement actif à Microsoft Cloud for Healthcare ou un abonnement à l’offre de connecteur autonome DMI Teams.
- Les utilisateurs disposent d’une licence Microsoft 365 ou Office 365 appropriée qui inclut les réunions Teams.
- Teams est adopté et utilisé dans votre organisation de santé.
- Identifié une personne de votre organisation qui est un administrateur général Microsoft 365 ayant accès au [Centre d’administration Teams](https://admin.teams.microsoft.com).
- Vos systèmes répondent à toutes les [exigences en matière de logiciels et de navigateurs](/microsoftteams/hardware-requirements-for-the-teams-app) pour Teams.
- Cerner version novembre 2018 ou ultérieure

## <a name="set-up-the-teams-ehr-connector"></a>Configurer le connecteur DSE Teams

La configuration du connecteur nécessite que vous :

- [Lanciez le portail de configuration du connecteur EHR](#launch-the-ehr-connector-configuration-portal)
- [Entriez les informations de configuration](#enter-configuration-information)
- [Activiez les notifications SMS (facultatif)](#enable-sms-notifications-optional)
- [Passiez en revue et acheviez la configuration](ehr-admin-cerner.md#review-and-finish-the-configuration)

> [!IMPORTANT]
> Ces étapes doivent être effectuées par l’administrateur général Microsoft 365 de votre organisation.  

### <a name="launch-the-ehr-connector-configuration-portal"></a>Lancer le portail de configuration du connecteur EHR

Pour commencer, votre administrateur Microsoft 365 lance le [portail de configuration du connecteur EHR](https://ehrconnector.teams.microsoft.com) et se connecte à l’aide de ses informations d’identification Microsoft.

Votre administrateur Microsoft 365 peut configurer un seul service ou plusieurs services pour tester l’intégration. Configurez l’URL de test et de production dans le portail de configuration. Veillez à tester l’intégration à partir de l’environnement de test Cerner avant de passer en production.

### <a name="enter-configuration-information"></a>Entrer les informations de configuration

Ensuite, pour configurer l’intégration, votre administrateur Microsoft 365 ajoute une URL de base FHIR (Fast Health Interoperability Resources) à partir de Cerner et spécifie l’environnement. Configurez autant d’URL de base FHIR que nécessaire, en fonction des besoins de votre organisation et des environnements que vous souhaitez tester.

:::image type="content" source="media/ehr-admin-cerner-configuration.png" alt-text="Capture d’écran de la page d’informations de configuration du portail de configuration du connecteur EHR Teams." lightbox="media/ehr-admin-cerner-configuration.png":::

- L’URL de base FHIR est une adresse statique qui correspond au point de terminaison de l’API FHIR de votre serveur. Un exemple d’URL est `https://lamnahealthcare.com/fhir/auth/connect-ocurprd-oauth/api/FHDST`.

- Vous pouvez configurer l’intégration pour les environnements de test et de production. Pour la configuration initiale, nous vous encourageons à configurer le connecteur à partir d’un environnement de test avant de passer en production.

Une fois l’URL de base FHIR validée et l’environnement sélectionné, choisissez **Terminé**. Ensuite, ajoutez d’autres URL de base FHIR pour d’autres environnements, si nécessaire.

Dans le cas contraire, sélectionnez **Suivant** pour passer à l’étape suivante.

### <a name="enable-sms-notifications-optional"></a>Activer les notifications SMS (facultatif)

Effectuez cette étape si votre organisation souhaite que Microsoft gère les notifications SMS pour vos patients. Lorsque vous activez les notifications PAR SMS, vos patients reçoivent des messages de confirmation et de rappel pour les rendez-vous planifiés.

Pour activer les notifications SMS, votre administrateur Microsoft 365 effectue les opérations suivantes :

1. Dans la page notifications SMS, cochez les deux cases de consentement pour :

    - Autoriser Microsoft à envoyer des notifications SMS aux patients au nom de votre organisation.
    - Reconnaître que vous allez vous assurer que les participants ont accepté d’envoyer et de recevoir des SMS.

    :::image type="content" source="media/ehr-admin-cerner-sms-notifications.png" alt-text="Capture d’écran de la page de notifications SMS, montrant les cases de consentement à cocher et l’option permettant de générer un numéro de téléphone." lightbox="media/ehr-admin-cerner-sms-notifications.png":::

1. Sous **Vos numéros de téléphone**, **sélectionnez Générer un nouveau numéro de téléphone** pour générer un numéro de téléphone pour votre organisation. Cela démarre le processus de demande et de génération d’un nouveau numéro de téléphone. L’exécution de ce processus peut prendre jusqu’à 2 minutes.

    Une fois le numéro de téléphone généré, il s’affiche à l’écran. Ce numéro sera utilisé pour envoyer des confirmations par SMS et des rappels à vos patients. Le numéro a été fournit, mais n’est pas encore lié à l’URL de base FHIR. C’est ce que vous allez faire à l’étape suivante.

    :::image type="content" source="media/ehr-admin-cerner-phone-number.png" alt-text="Capture d’écran montrant un exemple de numéro de téléphone généré." lightbox="media/ehr-admin-cerner-phone-number.png":::

    Sélectionnez **Terminé**, puis **Suivant**.

1. Pour lier le numéro de téléphone à une URL de base FHIR, sous **Numéro de téléphone** dans la section **configuration SMS** , sélectionnez le numéro. Effectuez cette opération pour chaque URL de base FHIR pour laquelle vous souhaitez activer les notifications SMS.

    :::image type="content" source="media/ehr-admin-cerner-link-phone-number.png" alt-text="Capture d’écran montrant comment lier un numéro de téléphone à une URL de base FHIR." lightbox="media/ehr-admin-cerner-link-phone-number.png":::

    S’il s’agit de la première fois que vous configurez le connecteur, vous verrez l’URL de base FHIR entrée à l’étape précédente. Le même numéro de téléphone peut être lié à plusieurs URL de base FHIR, ce qui signifie que les patients recevront des notifications par SMS du même numéro de téléphone pour différentes organisations et/ou services.

     Sélectionnez **Suivant**.

### <a name="review-and-finish-the-configuration"></a>Passer en revue et terminer la configuration

Vous recevrez des enregistrements d’intégration pour le lancement du patient et du fournisseur. Ces enregistrements sont nécessaires pour terminer la configuration des rendez-vous virtuels dans Cerner. Pour plus d’informations, consultez le guide Teams Telehealth Integration.

> [!NOTE]
> À tout moment, votre administrateur Microsoft 365 peut se connecter au portail de configuration pour afficher les enregistrements d’intégration et modifier les paramètres de configuration, si nécessaire.

## <a name="launch-teams-virtual-appointments"></a>Lancer des rendez-vous virtuels Teams

Une fois les étapes du connecteur EHR et Cerner terminées, votre organisation est prête à prendre en charge les rendez-vous vidéo avec Teams.

### <a name="virtual-appointments-prerequisites"></a>Prérequis pour les rendez-vous virtuels

- Vos systèmes doivent répondre à toutes les [exigences en matière de logiciels et de navigateurs](/microsoftteams/hardware-requirements-for-the-teams-app) pour Teams.
- Vous avez terminé la configuration de l’intégration entre l’organisation Cerner et votre organisation Microsoft 365.

### <a name="provider-experience"></a>Expérience fournisseur

Les prestataires de santé de votre organisation peuvent participer à des rendez-vous à l’aide de Teams à partir du portail PowerChart. Le fournisseur doit accéder au tableau des patients où l’option Teams est disponible.

À partir de là, le fournisseur peut afficher les informations de rendez-vous, participer à des rendez-vous et envoyer le lien de réunion. Après la connexion unique, le fournisseur est directement dirigé vers le rendez-vous virtuel dans Teams.

Principales fonctionnalités de l’expérience fournisseur :

- Les fournisseurs peuvent joindre des rendez-vous à l’aide de navigateurs pris en charge ou de l’application Teams.
- Les fournisseurs peuvent utiliser toutes les fonctionnalités de réunion Teams prises en charge, notamment le partage d’écran, l’arrière-plan personnalisé et l’enregistrement.
- Les fournisseurs peuvent voir les mises à jour en temps réel des patients qui se connectent à un rendez-vous pour un rendez-vous donné dans PowerChart.
- Les informations du fournisseur ne sont pas visibles par les patients pendant le rendez-vous.

> [!NOTE]
> Toutes les informations entrées dans la conversation de réunion nécessaires à la continuité des dossiers médicaux ou à des fins de rétention doivent être téléchargées, copiées et notifiées par le fournisseur de soins de santé. La conversation ne constitue pas un dossier médical légal ou un jeu d’enregistrements désigné. Les messages de la conversation sont stockés en fonction des paramètres créés par l’administrateur Microsoft Teams.

### <a name="patient-experience"></a>Expérience patient

Le connecteur prend en charge les patients qui rejoignent des rendez-vous via un lien dans le SMS. Au moment du rendez-vous, les patients peuvent démarrer un rendez-vous en appuyant sur le lien dans le SMS.

Fonctionnalités clés de l’expérience des patients

- Les patients peuvent rejoindre des rendez-vous à partir de [navigateurs web modernes sur le bureau et les appareils mobiles sans avoir à installer l’application Teams](browser-join.md).
- Les patients peuvent rejoindre des rendez-vous d’un simple clic et sans qu’aucun autre compte ou connexion ne soit requit.
- Les patients ne sont pas tenus de créer un compte Microsoft ou de se connecter pour lancer une visite.
- Les patients sont placés dans une salle d’attente jusqu’à ce que le fournisseur les rejoigne et les admette.
- Les patients peuvent tester leur vidéo et leur micropho*ne dans la salle d’attente avant de rejoindre le rendez-vous.

## <a name="get-insight-into-virtual-appointments-usage"></a>Obtenir des informations sur l’utilisation des rendez-vous virtuels

Le [rapport d’utilisation des visites virtuelles](virtual-visits-usage-report.md) dans le Centre d’administration Microsoft Teams donne aux administrateurs une vue d’ensemble de l’activité des rendez-vous virtuels Teams dans votre organisation. Le rapport présente des analyses détaillées pour les rendez-vous virtuels, y compris les réunions intégrées à la DSE Teams effectuées à partir de votre système DMI.

Vous pouvez afficher des indicateurs clés telles que le temps d’attente dans la salle d’attente et la durée du rendez-vous. Utilisez ces informations pour obtenir des insights sur les tendances d’utilisation afin de vous aider à optimiser les rendez-vous virtuels afin d’obtenir de meilleurs résultats métier.

## <a name="privacy-and-location-of-data"></a>Confidentialité et emplacement des données

L’intégration de Teams aux systèmes DSE optimise la quantité de données utilisées et stockées pendant les flux d’intégration et de rendez-vous virtuels. La solution respecte les principes et les directives générales de Teams en matière de confidentialité et de gestion des données, décrits dans Confidentialité Teams.

Le connecteur DSE Teams ne stocke ni ne transfère les données personnelles identifiables ni les dossiers d’intégrité des patients ou des fournisseurs de soins de santé à partir du système DSE. Les seules données stockées par le connecteur EHR sont l’ID unique de l’utilisateur DSE, qui est utilisé lors de la configuration de réunion Teams.

L’ID unique de l’utilisateur DMI est stocké dans l’une des trois zones géographiques décrites dans [Emplacement de stockage des données client Microsoft 365](/microsoft-365/enterprise/o365-data-locations). Toutes les conversations, enregistrements et autres données partagés dans Teams par les participants à la réunion sont stockés en fonction des stratégies de stockage existantes. Pour en savoir plus sur l’emplacement des données dans Teams, consultez [Emplacement des données dans Teams](/microsoftteams/location-of-data-in-teams).

## <a name="related-articles"></a>Articles connexes

- [Rapport d’utilisation des visites virtuelles Teams](virtual-visits-usage-report.md)
- [Rapport des rendez-vous virtuels du connecteur DMI Teams](ehr-connector-report.md)
- [Prise en main de Teams pour les organismes de santé](teams-in-hc.md)
