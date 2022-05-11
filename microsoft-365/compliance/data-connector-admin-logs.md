---
title: Utiliser le journal d’administration des connecteurs de données pour afficher l’état de l’importation de données
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
description: Découvrez comment accéder aux journaux d’administration et les afficher pour les connecteurs de données afin d’obtenir des informations d’état pour les données importées par le connecteur.
ms.openlocfilehash: de8b1de56b5e44ad199db942c3d385dcc05e1160
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2022
ms.locfileid: "65320882"
---
# <a name="view-admin-logs-for-data-connectors"></a>Afficher les journaux d’administration pour les connecteurs de données

Après avoir créé un connecteur de données pour importer des données non Microsoft dans Microsoft Purview, vous pouvez surveiller l’état d’importation quotidien du connecteur en téléchargeant les journaux d’administration du connecteur de données.

> [!IMPORTANT]
> La journalisation d’audit doit être activée pour que votre organisation puisse afficher le journal d’administration. Elle est activée par défaut pour les organisations Microsoft 365 et Office 365, mais nous vous recommandons vivement de vérifier l’état d’audit de votre organisation. Pour obtenir des instructions pour vérifier l’état de l’audit, cliquez ici. Pour obtenir des instructions pour activer l’audit manuellement, cliquez ici. Une fois l’audit activé, l’enregistrement des événements d’importation peut prendre jusqu’à 48 heures. Nous vous recommandons vivement d’activer l’audit avant la configuration d’un connecteur. Une fois qu’un connecteur est configuré, la génération de journaux contenant le résumé de l’état de l’importation peut prendre jusqu’à 72 heures.

## <a name="before-you-view-admin-logs"></a>Avant d’afficher les journaux d’administration

- L’audit doit être activé pour que votre organisation génère et affiche le journal d’administration de votre organisation. L’audit est activé par défaut dans Microsoft Purview. Toutefois, nous vous recommandons de vérifier l’état d’audit de votre organisation. Pour obtenir des instructions, consultez [Vérifier l’état d’audit de votre organisation](turn-audit-log-search-on-or-off.md#verify-the-auditing-status-for-your-organization). Si vous devez activer l’audit pour votre organisation, consultez [Activer l’audit](turn-audit-log-search-on-or-off.md#turn-on-auditing).

- Une fois l’audit activé, la génération de journaux d’administration pour les connecteurs de données peut prendre jusqu’à 48 heures. Nous vous recommandons d’activer l’audit avant de créer des connecteurs de données.

- Une fois qu’un connecteur de données est créé, la génération de journaux d’administration contenant le résumé de l’état de l’importation peut prendre jusqu’à 72 heures.

- Les journaux d’administration sont disponibles pour les sept derniers jours.

## <a name="download-admin-logs-for-data-connectors"></a>Télécharger les journaux d’administration pour les connecteurs de données

1. Accédez, <https://compliance.microsoft.com/> puis cliquez sur **Connecteurs de données**.

2. Cliquez sur l’onglet **Mes connecteurs** , puis sélectionnez un connecteur de données pour afficher la page volante, qui contient des informations et des propriétés sur le connecteur de données.

3. Sous **Journaux d’administration**, cliquez sur le lien **Télécharger le journal** pour ouvrir un journal d’administration.

   ![Journaux d’activité des administrateurs affichés dans la page de menu volant du connecteur de données.](..\media\Data-connector-admin-logs1.png)

4. Affichez les informations d’état d’importation suivantes dans le journal d’administration :

    - **Heure de fin de l’importation** : horodatage (en UTC) lorsque le connecteur termine l’importation à partir de la source de données et que tous les événements ci-dessous sont calculés/mis à jour par rapport à l’importation.
    - **Éléments disponibles à partir de la source** : nombre d’éléments qui ont été téléchargés par connecteur à partir de la source de données.
    - **Éléments disponibles pour l’importation** : nombre d’éléments qui étaient disponibles pour l’importation par connecteur après le fanout. Fanout représente l’acte d’écrire un message à tous les participants associés (expéditeur, destinataire, etc.).
    - **Éléments importés avec succès** : nombre d’éléments qui ont été importés avec succès par connecteur dans les boîtes aux lettres des utilisateurs après le fanout.
    - **Éléments partiellement importés** : nombre d’éléments qui ont été importés avec succès par connecteur dans les boîtes aux lettres des utilisateurs après le fanout, mais dont les pièces jointes ont été supprimées.
    - **Éléments ignorés** : nombre d’éléments qui ont été ignorés d’être importés dans les boîtes aux lettres des utilisateurs après le fanout, car il s’agit d’éléments en double.
    - **Échec des éléments** : nombre d’éléments qui n’ont pas pu être importés dans les boîtes aux lettres des utilisateurs après le fanout en raison d’erreurs (comme le mappage d’utilisateurs, la taille d’élément dépassée, etc.). L’événement est journalisé une fois par utilisateur pour les échecs de mappage d’utilisateur.

    > [!NOTE]
    > Les éléments disponibles pour l’importation doivent être une somme d’éléments importés avec succès, partiellement importés, ignorés et ayant échoué.

    - Résumé des détails de l’élément ayant échoué :
      - **ID d’élément** : identificateur unique de l’élément
      - **ID d’utilisateur source : ID** d’utilisateur dans l’application source
      - **ID d’utilisateur M365** – Nom d’utilisateur principal dans M365
      - **Raison de l’échec** : indique la raison pour laquelle le connecteur n’a pas pu importer l’élément

      S’il n’y a aucun élément ingéré un jour donné, le message ci-dessous est présent dans le fichier journal :

      Aucun élément ingéré à la date en *mm/dd/aaaa*.

> [!NOTE]
> Si aucun élément n’est importé un jour donné, le journal d’administration contient le message suivant : `No items ingested on mm/dd/yyyy.`
