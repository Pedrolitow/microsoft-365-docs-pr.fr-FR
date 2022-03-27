---
title: Informations de base de l’Explorateur de menaces et des détections en temps réel dans Microsoft Defender Office 365
f1.keywords:
- NOCSH
ms.author: dansimp
author: MSFTTracyp
manager: dansimp
audience: ITPro
ms.topic: article
ms.date: 05/05/2021
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Utilisez les détections de l’Explorateur ou en temps réel pour examiner les menaces et y répondre efficacement.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3b889649de7b56d6a1b5300ff323850a4e555b57
ms.sourcegitcommit: 9c8eca862a2f0fdca7a66c641e382e37fcaefa10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2022
ms.locfileid: "63775359"
---
# <a name="explorer-and-real-time-detections"></a>Détections de l’Explorateur et du temps réel

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Contenu de cet article :

- [Différences entre les détections de l’Explorateur et en temps réel](#differences-between-explorer-and-real-time-detections)
- [Expérience mise à jour pour les détections en temps réel et dans l’Explorateur](#updated-experience-for-explorer-and-real-time-detections)
- [Licences et autorisations requises](#required-licenses-and-permissions)

> [!NOTE]
> Cela fait partie d’une série de **3 articles** sur l’Explorateur (également appelé Explorateur de **menaces****),** la sécurité du courrier **électronique et les** bases de détection en temps réel et de l’Explorateur (telles que les différences entre les outils et les autorisations nécessaires pour les exploiter). Les deux autres articles de cette série sont le recherche de menaces dans [l’Explorateur](threat-hunting-in-threat-explorer.md) et la [sécurité du courrier électronique avec l’Explorateur](email-security-in-microsoft-defender.md).

Cet article explique la différence entre les rapports de détections en temps réel et de l’Explorateur, l’expérience mise à jour avec l’Explorateur et les détections en temps réel où vous pouvez faire bascule entre les anciennes et les nouvelles expériences, ainsi que les licences et autorisations requises.

Si votre organisation dispose de [Microsoft Defender pour Office 365](defender-for-office-365.md) et que vous disposez des [autorisations](#required-licenses-and-permissions), vous pouvez utiliser l’Explorateur **(également** appelé Explorateur de menaces **) ou** les détections en temps réel pour détecter et corriger les **menaces**.

Dans le portail Microsoft 365 Defender à <https://security.microsoft.com>l’adresse , go to **Email & collaboration**, and then choose **Explorer** _or_ **Real-time detections**. Pour aller directement à la page, utilisez ou <https://security.microsoft.com/threatexplorer> <https://security.microsoft.com/realtimereports>.

Avec ces outils, vous pouvez :

- Consultez les programmes malveillants détectés Microsoft 365 fonctionnalités de sécurité.
- Afficher l’URL de hameçonnage et cliquer sur les données de verdict.
- Démarrez un processus d’examen et de réponse automatisé à partir d’un affichage dans l’Explorateur.
- Examinez les e-mails malveillants, et bien plus encore.

Pour plus d’informations, voir [Sécurité du courrier électronique avec l’Explorateur](email-security-in-microsoft-defender.md).

## <a name="differences-between-explorer-and-real-time-detections"></a>Différences entre les détections de l’Explorateur et en temps réel

- *Les détections en temps réel* sont un outil de rapports disponible dans Defender pour Office 365 Plan 1. *L’Explorateur de* menaces est un outil de recherche et de correction des menaces disponible dans Defender Office 365 Plan 2.
- Le rapport de détections en temps réel vous permet d’afficher les détections en temps réel. L’Explorateur de menaces le fait également, mais fournit des détails supplémentaires pour une attaque donnée, comme la mise en surbrillance des campagnes d’attaque, et offre aux équipes des opérations de sécurité la possibilité de corriger les menaces (notamment le déclenchement d’une enquête automatisée sur les enquêtes et les [réponses).](automated-investigation-response-office.md)
- Un *affichage de courrier tout* est disponible dans l’Explorateur de menaces, mais n’est pas inclus dans le rapport de détections en temps réel.
- Des fonctionnalités de filtrage enrichies et des actions de correction sont incluses dans l’Explorateur de menaces. Pour plus d’informations, voir [Microsoft Defender pour la description Office 365 service : disponibilité des fonctionnalités dans Defender pour Office 365 plans](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans).

## <a name="updated-experience-for-explorer-and-real-time-detections"></a>Expérience mise à jour pour les détections en temps réel et dans l’Explorateur

L’expérience de l’Explorateur de menaces et des détections en temps réel est mise à jour pour s’aligner sur les normes d’accessibilité modernes et optimiser le flux de travail. Pendant un court moment, vous pourrez faire bascule entre l’ancienne expérience et la nouvelle.  

> [!NOTE]
> Le basculement n’a d’impact que sur votre compte et n’a d’impact sur personne d’autre au sein de votre client. 

Les détections en temps réel et de l’Explorateur de menaces sont réparties dans les affichages suivants :

- *Tous les e-mails* : affiche tous les e-mails analysés par Defender pour Office 365 et contient des messages électroniques à la fois bons et malveillants. Cette fonctionnalité est uniquement présente dans l’Explorateur de menaces et n’est pas disponible pour les détections en temps réel. Par défaut, elle est définie pour afficher les données de deux jours, qui peuvent être étendues jusqu’à 30 jours. Il s’agit également de l’affichage par défaut de l’Explorateur de menaces.  

- *Affichage des programmes* malveillants : affiche les e-mails sur lesquels une menace de programme malveillant a été identifiée. Il s’agit de l’affichage par défaut pour les détections en temps réel et affiche les données sur deux jours (peut être étendu à 30 jours).  

- *Affichage hameçonnage* : affiche les e-mails sur lesquels une menace de hameçonnage a été identifiée.

- *Affichage des programmes malveillants* de contenu : affiche les détections malveillantes identifiées dans les fichiers partagés OneDrive, SharePoint ou Teams. 

Voici les composants courants de ces expériences :

- Filtres

    - Vous pouvez utiliser les différents filtres pour afficher les données en fonction des attributs de courrier électronique ou de fichier.  

    - Par défaut, le filtre d’heure est appliqué aux enregistrements et est appliqué pendant deux jours.  

    - Si vous appliquez plusieurs filtres, ils sont appliqués en mode « AND » et vous pouvez utiliser le filtre avancé pour le modifier en mode « OR ».  

    - Vous pouvez utiliser des virgules pour ajouter plusieurs valeurs pour le même filtre.  

    > [!div class="mx-imgBorder"]
    > ![Filtres d’explorateur](../../media/explorer-new-experience-filters.png)

- Graphiques

    - Les graphiques fournissent une vue visuelle agrégée des données basées sur des filtres. Vous pouvez utiliser différents filtres pour afficher les données selon différentes dimensions.  

    > [!NOTE]
    > Il se peut que vous ne visiez aucun résultat en affichage graphique même si vous voyez une entrée dans l’affichage Liste. Cela se produit si le filtre ne produit aucune donnée. Par exemple, si vous avez appliqué la famille de programmes malveillants de filtre, mais que les données sous-jacentes ne disposent pas de courriers électroniques malveillants, il se peut que le message ne dispose d’aucune donnée pour ce scénario.  

    > [!div class="mx-imgBorder"]
    > ![Affichage Graphique de l’Explorateur](../../media/explorer-new-experience-export-chart-data.png)

- Grille de résultats  

    - La grille de résultats affiche les résultats des e-mails en fonction des filtres que vous avez appliqués.  

    - En fonction de la configuration définie dans votre client, les données sont affichées dans le fuseau horaire UTC ou local, avec les informations de fuseau horaire disponibles dans la première colonne.  

    - Vous pouvez accéder à la page d’entité de messagerie individuelle à partir de l’affichage Liste en cliquant sur **l’icône Ouvrir dans une nouvelle** fenêtre. 

    - Vous pouvez également personnaliser vos colonnes pour ajouter ou supprimer des colonnes afin d’optimiser votre affichage.

    > [!Note]
    > Vous pouvez faire bascule entre l’affichage *Graphique* et l’affichage *Liste* pour optimiser votre jeu de résultats.  

    > [!div class="mx-imgBorder"]
    > ![Affichage Grille de l’Explorateur](../../media/explorer-new-experience-list-chart-view.png)

- Flyout détaillé  

    - Vous pouvez cliquer sur les liens hypertexte pour obtenir le panneau de synthèse du courrier électronique (entrées dans la colonne Objet), le destinataire ou le flyout IP.  

    - Le panneau de synthèse du courrier électronique remplace le volant de courrier électronique hérité et fournit également un chemin d’accès au panneau d’entité de messagerie.  

    - Les volants d’entité individuels tels que l’ADRESSE IP, le destinataire et l’URL reflètent les mêmes informations, mais présentés dans une vue tabulation unique, avec la possibilité de développer et de réduire les différentes sections en fonction des besoins.  

    - Pour les volants tels que les URL, vous pouvez cliquer  sur Afficher tous les messages électroniques ou Afficher tous les **clics** pour afficher l’ensemble complet des e-mails/clics contenant cette URL, et exporter le jeu de résultats.  

- Actions

    - À partir de l’Explorateur de menaces, vous pouvez déclencher des actions de correction telles *que la suppression d’un e-mail*. Pour plus d’informations sur la correction, les limites de correction et la correction du suivi, voir [Corriger les messages malveillants](remediate-malicious-email-delivered-office-365.md).  

- Exporter

    - Vous pouvez cliquer sur **Exporter les données du graphique** pour exporter les détails du graphique. De même, cliquez sur **Exporter la liste de courriers** électroniques pour exporter les détails des e-mails.

    - Vous pouvez exporter jusqu’à 200 000 enregistrements pour la liste de courriers électroniques. Toutefois, pour améliorer les performances du système et réduire le temps de téléchargement, vous devez utiliser différents filtres de courrier électronique.

    > [!div class="mx-imgBorder"]
    > ![Exporter des données de graphique](../../media/explorer-new-experience-export-chart-data.png)

En plus de ces fonctionnalités, vous obtenez également des expériences mises à jour, telles que les URL principales, les *clics les plus fréquents**, les* *utilisateurs* les plus ciblés et l’origine *de la messagerie*. *Les URL principales*, *les clics les plus fréquents et les utilisateurs* les plus ciblés peuvent être filtrés en fonction du filtre que vous appliquez dans l’Explorateur. 

## <a name="required-licenses-and-permissions"></a>Licences et autorisations requises

Vous devez avoir [Microsoft Defender pour Office 365](defender-for-office-365.md) utiliser l’explorateur ou les détections en temps réel :

- Explorer est inclus uniquement dans Defender pour Office 365 Plan 2.
- Le rapport détections en temps réel est inclus dans Defender pour Office 365 Plan 1.

Les équipes des opérations de sécurité doivent attribuer des licences à tous les utilisateurs qui doivent être protégés par Defender pour Office 365 et sachent que les détections d’Explorateur et en temps réel montrent les données de détection pour les utilisateurs sous licence.

Pour afficher et utiliser les *détections de* l’Explorateur ou en temps réel, vous avez besoin des autorisations suivantes :

- Dans Defender pour Office 365 :
  - Gestion de l’organisation
  - Administrateur de sécurité (peut être affecté dans le Centre d’administration Azure Active Directory de sécurité (<https://aad.portal.azure.com>)
  - Lecteur de sécurité
- Dans Exchange Online :
  - Gestion de l’organisation
  - Afficher uniquement la gestion de l’organisation
  - Afficher uniquement les destinataires
  - Gestion de la conformité

Pour en savoir plus sur les rôles et les autorisations, consultez les articles suivants :

- [Autorisations dans le Portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md)
- [Autorisations dans Exchange Online](/e/exchange/permissions-exo/permissions-exo)

## <a name="more-information"></a>Plus d’informations

- [L’Explorateur de menaces collecte les détails des e-mails sur la page d’entité de messagerie](mdo-email-entity-page.md)
- [Rechercher et d’examiner l’e-mail malveillant qui a été distribué](investigate-malicious-email-that-was-delivered.md)
- [Afficher les fichiers malveillants détectés dans SharePoint Online, OneDrive et Microsoft Teams](mdo-for-spo-odb-and-teams.md)
- [Rapport sur l’état de la protection contre les menaces](view-email-security-reports.md#threat-protection-status-report)
- [Examen et réponses automatisés dans Protection Microsoft contre les menaces](automated-investigation-response-office.md)
