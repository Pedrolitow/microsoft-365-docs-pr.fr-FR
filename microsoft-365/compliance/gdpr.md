---
title: Règlement général sur la protection des données
description: Conseils techniques de Microsoft concernant le Règlement général sur la protection des données (RGPD)
keywords: Microsoft 365, Microsoft 365 Éducation, documentation Microsoft 365, RGPD
localization_priority: Priority
ms.prod: Microsoft-365-enterprise
ms.topic: article
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection:
- GDPR
- M365-security-compliance
titleSuffix: Microsoft GDPR
ms.openlocfilehash: d64d9b98fe3cf24a14b3f3126ff3f38b1d84087d
ms.sourcegitcommit: 03a83ff76c8162b850c4c552759c49f2a4750574
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2020
ms.locfileid: "41557981"
---
# <a name="general-data-protection-regulation-summary"></a>Sythèse du règlement général sur la protection des données

Le règlement général sur la protection des données (RGPD) présente de nouvelles règles pour les organisations qui offrent des produits et des services aux membres de l’Union européenne (UE), ou qui collectent et analysent des données pour les résidents de l’UE quel que soit l’endroit où vous vous trouvez et celui où se trouve votre entreprise.<br><br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWrOQI] 

Ce document vous apporte des informations pour vous aider à honorer vos droits et à respecter les obligations en vertu du RGPD lorsque vous utilisez les produits et services Microsoft. Un [plan d’action recommandé pour le RGPD](gdpr-action-plan.md) et les [listes de vérification de préparation sur la responsabilité](gdpr-arc.md) fournissent des ressources supplémentaires pour l’évaluation et la mise en œuvre de la conformité RGPD.

## <a name="terminology"></a>Terminologie

Définitions utiles pour les termes RGPD utilisés dans ce document :

- *Contrôleur de données (contrôleur)*  : la personne morale, l’autorité publique, le service ou tout autre organisme qui, seul ou conjointement avec d’autres entités, détermine les finalités et les moyens de traitement des données personnelles.  
- *Données personnelles* et *personne concernée* : toutes les informations relatives à une personne physique identifiée ou identifiable (personne concernée); une personne physique identifiable est une personne qui peut être identifiée, directement ou indirectement.  
- *Responsable du traitement* : la personne physique ou morale, l’autorité publique, le service ou tout autre organisme qui traite des données à caractère personnel pour le compte de l’entité de contrôle.  
- *Données client* : les données produites et stockées dans les opérations quotidiennes dans le cadre du fonctionnement de votre entreprise.

## <a name="what-is-the-gdpr"></a>Qu’est-ce que le RGPD ?

Le RGPD donne aux personnes les droits de gérer les données personnelles rassemblées par une organisation. Ces droits peuvent être exercés via une demande de la personne concernée (DSR). L’organisation doit fournir des informations opportunes concernant les DSR et les brèches de données, et effectuer des analyses d’impact sur la protection des données (DPIA).

Plusieurs points doivent être pris en considération lors de l’implémentation ou de l’analyse de besoins RGPD.

- Développement ou analyse de votre politique de confidentialité des données de conformité RGPD.
- Analyser la sécurité des données de votre organisation.
- Qui est votre contrôleur de données ?
- Quels sont les processus de sécurité des données que vous devez effectuer ?

Le [plan d’action recommandé pour le RGPD](gdpr-action-plan.md) et les [listes de vérification de préparation sur la responsabilité](gdpr-arc.md) peuvent inviter à d’autres points de réflexion.

Les tâches suivantes sont impliquées pour satisfaire les normes RGPD. Pour plus d’informations sur l’implémentation, suivez les liens de la liste.  

- **[Demandes des personnes concernées (DSR)](gdpr-data-subject-requests.md)**. Une demande officielle d’une personne concernée à un responsable du traitement pour effectuer une action (changement, restriction, accès) sur ses données personnelles.
- **[Notification de violation](gdpr-breach-notification.md)**. En vertu du RGPD, une violation de données personnelles correspond à une violation de la sécurité entraînant la destruction involontaire ou contraire à la loi de données personnelles transmises, stockées ou autrement traitées, ou bien leur perte, modification ou divulgation ou consultation non autorisée.
- **[Analyses d’impact sur la protection des données](gdpr-data-protection-impact-assessments.md)**. Les contrôleurs de données sont requis en vertu du RGPD de préparer une analyse d’impact sur la protection des données pour les opérations de données « susceptibles de générer un risque élevé pour les droits et libertés des personnes physiques ».

Comme indiqué ci-dessus, le plan d’action recommandé pour le RGPD et les listes de vérification de préparation sur la responsabilité fournissent un guide pour l’implémentation ou l’analyse de la conformité RGPD à l’aide de produits et services Microsoft.

## <a name="the-gdpr-in-action"></a>Le RGPD en action

Cette section fournit une description et des points de réflexion sur l’exécution des tâches RGPD mentionnées ci-dessus. L’exécution de ces tâches peut varier en fonction de votre configuration Microsoft.

### <a name="data-subject-request-dsr"></a>Demandes des personnes concernées (DSR)

Les demandes de personnes concernées permettent aux sujets de données d’exercer leurs droits en vertu du RGPD. Le contrôleur se charge de fournir une réponse opportune et cohérente au RGPD. Les questions que vous devez prendre en considération sont indiquées ci-dessous. Pour plus d’informations techniques, reportez-vous à [Demandes des personnes concernées](gdpr-data-subject-requests.md).  

- **Quelles actions seront requises pour effectuer une DSR ?**  : une demande de personne concernée implique six activités : découverte, accès, rectification, restriction, exportation et suppression.
- **Quelles sont vos sources de données ?**  : une grande partie des données d’une organisation est générée dans les [applications Office](https://docs.microsoft.com/microsoft-365/compliance/gdpr-dsr-office365#using-the-content-search-ediscovery-tool-to-respond-to-dsrs) telles qu’Excel et Outlook. Vous pouvez également trouver des données pertinentes pour une DSR dans les [informations](https://docs.microsoft.com/microsoft-365/compliance/gdpr-dsr-office365#part-2-responding-to-dsrs-with-respect-to-insights-generated-by-office-365) générées par les produits et services Microsoft et les [journaux générés par le système](https://docs.microsoft.com/microsoft-365/compliance/gdpr-dsr-office365#part-3-responding-to-dsrs-for-system-generated-logs).
- **Quels types de données doivent faire l’objet d’une recherche ?**  : les données à caractère personnel peuvent se trouver dans les données client, les informations générées par les produits et services Microsoft et les journaux générés par le système.
- **Comment les données à caractère personnel doivent-elles être recherchées ?**  : la recherche de données à caractère personnel peut varier entre les produits et services Microsoft. Les outils de recherche incluent la [recherche de contenu](https://docs.microsoft.com/microsoft-365/compliance/gdpr-dsr-office365#using-the-content-search-ediscovery-tool-to-respond-to-dsrs) ou la capacité [de recherche dans l’application](https://docs.microsoft.com/microsoft-365/compliance/gdpr-dsr-office365#using-in-app-functionality-to-respond-to-dsrs). Les administrateurs peuvent accéder aux [journaux générés par le système](https://docs.microsoft.com/microsoft-365/compliance/gdpr-dsr-office365#part-3-responding-to-dsrs-for-system-generated-logs) associés à l’activité d’un utilisateur.  
- **Dans quels formats est-ce que les données à caractère personnel doivent être disponibles ?**  : Le « droit à la portabilité des données » du RGPD permet à la personne concernée par le traitement des données de demander une copie des données à caractère personnel dans un « format lisible par machine, fréquemment utilisé et structuré » et demander à votre organisation de transmettre ces fichiers à une autre entité de contrôle des données.

### <a name="data-protection-impact-assessment"></a>Analyses d’impact sur la protection des données

En vertu du RGPD, les contrôleurs de données sont requis de préparer une [analyse d’impact sur la protection des données](gdpr-data-protection-impact-assessments.md) (DPIA) pour les opérations « susceptibles de générer un risque élevé pour les droits et libertés des personnes physiques ». Il n’existe aucun élément inhérent aux produits et services Microsoft nécessitant la création d’une DPIA. Cela dépend plutôt des détails de la configuration Microsoft.

Certaines considérations sur la DPIA sont présentées ci-dessous. Une liste de détails devant être pris en compte dans Office est disponible dans [Contenu d’une DPIA](https://docs.microsoft.com/microsoft-365/compliance/gdpr-dpia-office365#part-2--contents-of-a-dpia).

- Quelles activités de données au sein de votre organisation peuvent compromettre la sécurité de vos données à caractère personnel ?
- Votre configuration de produits et services Microsoft sera-t-elle vulnérable à une violation de données ?
- Quand devez-vous mener une DPIA ?

    - Les contrôleurs sont requis d’effectuer une DPIA pour résoudre les problèmes relatifs à la sécurité des données à caractère personnel ou en raison d’une violation de données. Des exemples spécifiques de facteurs de risque dans Office sont traités dans [Déterminer si une analyse d’impact sur la protection des données est nécessaire](https://docs.microsoft.com/microsoft-365/compliance/gdpr-dpia-office365#part-1--determining-whether-a-dpia-is-needed).  

- Qu’est-ce qui est requis pour effectuer une DPIA ?

    Le RGPD impose qu’une DPIA inclut les éléments suivants :  
    - Évaluation du besoin et de la proportionnalité du traitement des données par rapport aux finalités prévues de la DPIA.
    - Évaluation des risques concernant les droits et les libertés des personnes concernées par les données.
    - Les mesures envisagées pour lutter contre les risques, les garanties, les mesures de sécurité et les mécanismes pour assurer la protection des données à caractère personnel et prouver la conformité avec le RGPD.

### <a name="breach-notification"></a>Notification de violation

En tant que responsable du traitement des données, Microsoft s’assure que les clients peuvent répondre aux exigences de notification de violation du RGPD. Les contrôleurs de données sont chargés d'évaluer les risques liés à la confidentialité des données et de déterminer si le contrat de traitement des données d’un client doit être notifié en cas de violation. Microsoft fournit les informations nécessaires pour effectuer cette évaluation. Plus d’informations sur la façon dont Microsoft détecte et répond à une violation des données à caractère personnel dans [Notification des violations de données en vertu du RGPD](gdpr-breach-notification.md). Voici quelques questions liées à la notification de violation :

- Les informations relatives à une violation doivent être communiquées aux personnes concernées par les données
- Comment allez-vous communiquer avec les personnes concernées par les données (courrier électronique, notification écrite, etc.) ?

### <a name="accountability-readiness-checklists-for-the-gdpr"></a>Listes de vérification de préparation sur la responsabilité concernant le RGPD

Ces [listes de vérification](gdpr-arc.md) permettent d’accéder en toute simplicité aux informations dont vous pouvez avoir besoin pour prendre en charge le RGPD lors de l’utilisation de produits Microsoft. Vous pouvez gérer les éléments de cette liste de vérification à l’aide du [Score de conformité Microsoft](compliance-score.md) en indiquant l’ID de contrôle et le titre de contrôle sous Contrôles gérés par le client dans la vignette RGPD.

## <a name="learn-more"></a>En savoir plus

- [Centre de gestion de la confidentialité Microsoft](https://www.microsoft.com/TrustCenter/Privacy/gdpr/default.aspx)
