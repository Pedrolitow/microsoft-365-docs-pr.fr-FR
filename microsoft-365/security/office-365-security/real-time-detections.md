---
title: Informations de base sur l’Explorateur de menaces et les détections en temps réel dans Microsoft Defender pour Office 365
f1.keywords:
- NOCSH
ms.author: dansimp
author: MSFTTracyp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.date: 05/05/2021
ms.localizationpriority: medium
ms.collection:
- m365-security
- m365initiative-defender-office365
description: Utilisez l’Explorateur ou les détections en temps réel pour examiner et répondre efficacement aux menaces.
ms.custom:
- seo-marvel-apr2020
ms.subservice: mdo
ms.service: microsoft-365-security
search.appverid: met150
ms.openlocfilehash: 99f6d3b1d556b15c71389bd4cfce86cb0f78fdfd
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68642236"
---
# <a name="explorer-and-real-time-detections"></a>Détections de l’Explorateur et en temps réel

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Contenu de cet article :

- [Différences entre les détections d’Explorateur et en temps réel](#differences-between-explorer-and-real-time-detections)
- [Mise à jour de l’expérience pour les détections d’Explorateur et en temps réel](#updated-experience-for-explorer-and-real-time-detections)
- [Licences et autorisations requises](#required-licenses-and-permissions)

> [!NOTE]
> Il s’agit d’une série de 3 articles sur **l’Explorateur (également appelé Explorateur de menaces),** la **sécurité des e-mails** et **les notions de base des détections en temps réel et de l’Explorateur** (telles que les différences entre les outils et les autorisations nécessaires pour les utiliser). Les deux autres articles de cette série sont [la chasse aux menaces dans l’Explorateur](threat-hunting-in-threat-explorer.md) et [Email la sécurité avec l’Explorateur](email-security-in-microsoft-defender.md).

Cet article explique la différence entre la création de rapports de détections en temps réel et l’Explorateur, l’expérience mise à jour avec l’Explorateur et les détections en temps réel, où vous pouvez basculer entre les expériences anciennes et nouvelles, ainsi que les licences et autorisations requises.

Si votre organisation dispose [d’Microsoft Defender pour Office 365](defender-for-office-365.md) et que vous disposez [des autorisations](#required-licenses-and-permissions), vous pouvez utiliser **l’Explorateur** (également appelé **Explorateur de menaces**) ou **des détections en temps réel** pour détecter et corriger les menaces.

Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à **Email & collaboration**, puis choisissez **Explorer** _ou_ **détections en temps réel**. Pour accéder directement à la page, utilisez <https://security.microsoft.com/threatexplorer> ou <https://security.microsoft.com/realtimereports>.

Avec ces outils, vous pouvez :

- Consultez les programmes malveillants détectés par les fonctionnalités de sécurité de Microsoft 365.
- Affichez l’URL d’hameçonnage et cliquez sur les données de verdict.
- Démarrez un processus d’investigation et de réponse automatisé à partir d’une vue dans l’Explorateur.
- Examinez les e-mails malveillants, et bien plus encore.

Pour plus d’informations, consultez [Email sécurité avec l’Explorateur](email-security-in-microsoft-defender.md).

## <a name="differences-between-explorer-and-real-time-detections"></a>Différences entre les détections d’Explorateur et en temps réel

- *Les détections en temps réel* sont un outil de création de rapports disponible dans Defender pour Office 365 Plan 1. *L’Explorateur de menaces* est un outil de repérage et de correction des menaces disponible dans Defender pour Office 365 Plan 2.
- Le rapport de détections en temps réel vous permet d’afficher les détections en temps réel. L’Explorateur de menaces le fait également, mais il fournit des détails supplémentaires pour une attaque donnée, telles que la mise en surbrillance des campagnes d’attaque, et offre aux équipes chargées des opérations de sécurité la possibilité de corriger les menaces (y compris le déclenchement d’une [investigation automatisée et d’une enquête de réponse](automated-investigation-response-office.md).
- Une vue *Tous les e-mails* est disponible dans l’Explorateur de menaces, mais elle n’est pas incluse dans le rapport de détections en temps réel.
- Des fonctionnalités de filtrage enrichies et des actions de correction sont incluses dans l’Explorateur de menaces. Pour plus d’informations, consultez [Microsoft Defender pour Office 365 Description du service : Disponibilité des fonctionnalités dans Defender pour Office 365 plans](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans).

## <a name="updated-experience-for-explorer-and-real-time-detections"></a>Mise à jour de l’expérience pour les détections d’Explorateur et en temps réel

L’expérience de l’Explorateur de menaces et des détections en temps réel est mise à jour pour s’aligner sur les normes d’accessibilité modernes et optimiser le flux de travail. Pendant un court moment, vous pourrez basculer entre l’ancienne expérience et la nouvelle.  

> [!NOTE]
> Le basculement a un impact uniquement sur votre compte et n’affecte personne d’autre au sein de votre locataire. 

L’Explorateur de menaces et les détections en temps réel sont divisés en vues suivantes :

- *Tous les e-mails* : affiche tous les e-mails analysés par Defender pour Office 365 et contient à la fois des e-mails corrects et malveillants. Cette fonctionnalité est uniquement présente dans l’Explorateur de menaces et n’est pas disponible pour les détections en temps réel. Par défaut, il est défini pour afficher les données pendant deux jours, qui peuvent être étendues jusqu’à 30 jours. Il s’agit également de l’affichage par défaut de l’Explorateur de menaces.  

- *Affichage des programmes malveillants* : affiche les e-mails sur lesquels une menace de programme malveillant a été identifiée. Il s’agit de l’affichage par défaut pour les détections en temps réel et affiche les données pendant deux jours (peuvent être étendues à 30 jours).  

- *Vue hameçonnage* : affiche les e-mails sur lesquels une menace de hameçonnage a été identifiée.

- *Affichage des programmes malveillants de contenu* : affiche les détections malveillantes identifiées dans les fichiers partagés via OneDrive, SharePoint ou Teams. 

Voici les composants courants de ces expériences :

- Filtres

    - Vous pouvez utiliser les différents filtres pour afficher les données en fonction des attributs de messagerie ou de fichier.  

    - Par défaut, le filtre de temps est appliqué aux enregistrements et est appliqué pendant deux jours.  

    - Si vous appliquez plusieurs filtres, ils sont appliqués en mode « AND » et vous pouvez utiliser le filtre avancé pour le remplacer par le mode « OR ».  

    - Vous pouvez utiliser des virgules pour ajouter plusieurs valeurs pour le même filtre.  

    > [!div class="mx-imgBorder"]
    > ![Filtres de l’Explorateur](../../media/explorer-new-experience-filters.png)

- Graphiques

    - Les graphiques fournissent une vue d’agrégation visuelle des données basée sur des filtres. Vous pouvez utiliser différents filtres pour afficher les données selon différentes dimensions.  

    > [!NOTE]
    > Vous ne verrez peut-être aucun résultat en mode graphique, même si vous voyez une entrée dans l’affichage liste. Cela se produit si le filtre ne produit pas de données. Par exemple, si vous avez appliqué la famille de programmes malveillants de filtre, mais que les données sous-jacentes n’ont pas d’e-mails malveillants, vous pouvez voir le message sans données disponibles pour ce scénario.  

    > [!div class="mx-imgBorder"]
    > ![Affichage graphique de l’Explorateur](../../media/explorer-new-experience-export-chart-data.png)

- Grille des résultats  

    - La grille des résultats affiche les résultats de l’e-mail en fonction des filtres que vous avez appliqués.  

    - En fonction de la configuration définie dans votre locataire, les données sont affichées dans le fuseau horaire UTC ou local, avec les informations de fuseau horaire disponibles dans la première colonne.  

    - Vous pouvez accéder à la page d’entité de messagerie individuelle à partir de l’affichage liste en cliquant sur l’icône **Ouvrir dans la nouvelle fenêtre** . 

    - Vous pouvez également personnaliser vos colonnes pour ajouter ou supprimer des colonnes afin d’optimiser votre affichage.

    > [!Note]
    > Vous pouvez basculer entre *l’affichage graphique* et le *mode Liste* pour optimiser votre jeu de résultats.  

    > [!div class="mx-imgBorder"]
    > ![Affichage grille de l’Explorateur](../../media/explorer-new-experience-list-chart-view.png)

- Menu volant détaillé  

    - Vous pouvez cliquer sur des liens hypertexte pour accéder au panneau de synthèse de l’e-mail (entrées dans la colonne Objet), au destinataire ou au menu volant IP.  

    - Le panneau récapitulatif de l’e-mail remplace le menu volant d’e-mail hérité et fournit également un chemin d’accès au panneau d’entité de messagerie.  

    - Les menus volants d’entité individuels tels que l’adresse IP, le destinataire et l’URL reflètent les mêmes informations, mais présentés dans une vue basée sur un onglet unique, avec la possibilité de développer et de réduire les différentes sections en fonction des besoins.  

    - Pour les menus volants comme les URL, vous pouvez cliquer sur **Afficher tous les Email** ou **Afficher tous les clics** pour afficher l’ensemble complet d’e-mails/clics contenant cette URL, ainsi que pour exporter le jeu de résultats.  

- Actions

    - À partir de l’Explorateur de menaces, vous pouvez déclencher des actions de correction telles *que Supprimer un e-mail*. Pour plus d’informations sur la correction, les limites de correction et le suivi de la correction, consultez [Corriger les e-mails malveillants](remediate-malicious-email-delivered-office-365.md).  

- Exporter

    - Vous pouvez cliquer sur **Exporter les données du graphique** pour exporter les détails du graphique. De même, cliquez sur **Exporter la liste de courriers** électroniques pour exporter les détails de l’e-mail.

    - Vous pouvez exporter jusqu’à 200 000 enregistrements pour la liste de courriers électroniques. Toutefois, pour améliorer les performances système et réduire le temps de téléchargement, vous devez utiliser différents filtres de courrier électronique.

    > [!div class="mx-imgBorder"]
    > ![Exporter des données de graphique](../../media/explorer-new-experience-export-chart-data.png)

En plus de ces fonctionnalités, vous obtiendrez également des expériences mises à jour telles que *les URL principales*, *les clics principaux, les utilisateurs* *ciblés les plus* ciblés et *l’origine Email*. *Les URL principales*, *les clics principaux et les utilisateurs* *ciblés* principaux peuvent être filtrés en fonction du filtre que vous appliquez dans l’Explorateur. 

## <a name="required-licenses-and-permissions"></a>Licences et autorisations requises

Vous devez avoir [Microsoft Defender pour Office 365](defender-for-office-365.md) utiliser l’explorateur ou les détections en temps réel :

- L’Explorateur est inclus uniquement dans Defender pour Office 365 Plan 2.
- Le rapport de détections en temps réel est inclus dans Defender pour Office 365 Plan 1.

Les équipes des opérations de sécurité doivent attribuer des licences à tous les utilisateurs qui doivent être protégés par Defender pour Office 365 et être conscients que les détections d’Explorateur et en temps réel affichent les données de détection pour les utilisateurs sous licence.

Pour afficher et utiliser des détections d’Explorateur *ou* en temps réel, vous avez besoin des autorisations suivantes :

- Dans Defender pour Office 365 :
  - Gestion de l’organisation
  - Administrateur de sécurité (cela peut être attribué dans le Centre d’administration Azure Active Directory (<https://aad.portal.azure.com>)
  - Lecteur de sécurité
- Dans Exchange Online :
  - Gestion de l’organisation
  - Gestion de l'organisation en affichage seul
  - Afficher uniquement les destinataires
  - Gestion de la conformité

Pour en savoir plus sur les rôles et les autorisations, consultez les articles suivants :

- [Autorisations dans le Portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md)
- [Autorisations dans Exchange Online](/exchange/permissions-exo/permissions-exo)

## <a name="more-information"></a>Plus d’informations

- [L’Explorateur de menaces collecte les détails de l’e-mail sur la page d’entité de messagerie](mdo-email-entity-page.md)
- [Rechercher et d’examiner l’e-mail malveillant qui a été distribué](investigate-malicious-email-that-was-delivered.md)
- [Afficher les fichiers malveillants détectés dans SharePoint Online, OneDrive et Microsoft Teams](mdo-for-spo-odb-and-teams.md)
- [Rapport sur l’état de la protection contre les menaces](view-email-security-reports.md#threat-protection-status-report)
- [Examen et réponses automatisés dans Protection Microsoft contre les menaces](automated-investigation-response-office.md)
