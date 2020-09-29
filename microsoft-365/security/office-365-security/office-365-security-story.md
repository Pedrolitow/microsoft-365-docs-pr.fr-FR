---
title: Sécurité Office 365
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: 08/13/2020
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.collection:
- microsoft-365-docs-pr
description: Sécurité dans Office 365, des plans d’EOP à ATP 1 et 2, des configurations de sécurité standard ou rigoureuses, et bien plus, afin que vous puissiez comprendre ce dont vous disposez et comment sécuriser vos propriétés.
ms.openlocfilehash: 680066f58850f59523ae6fb8a8168459dd813fc1
ms.sourcegitcommit: 888b9355ef7b933c55ca6c18639c12426ff3fbde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "48304845"
---
# <a name="office-365-security-outline"></a>Plan de sécurité Office 365

Cet article vous présente vos nouvelles propriétés de sécurité dans le Cloud. Que vous soyez membre d’un centre de sécurité, vous êtes un administrateur de sécurité, ou vous souhaitez un actualisateur, commençons.

> [!CAUTION]
> Salut. Si vous utilisez **Outlook.com**, la **famille Microsoft 365**ou **Microsoft 365 personnel**, et que vous avez besoin de *liens fiables* ou d’informations de *pièces jointes fiables* , ***cliquez sur ce lien***: [sécurité avancée Outlook.com pour les abonnés de Microsoft 365](https://support.microsoft.com/office/advanced-outlook-com-security-for-office-365-subscribers-882d2243-eab9-4545-a58a-b36fee4a46e2). Nos!

## <a name="office-365-security-spelled-out"></a>Sécurité Office 365

Chaque abonnement Office 365 est fourni avec des fonctionnalités de sécurité. Les objectifs et les actions que vous pouvez effectuer dépendent de l’intérêt de ces différents abonnements. Dans la sécurité Office 365, trois services de sécurité (ou produits) principaux sont liés à votre type d’abonnement :

1. Exchange Online Protection (EOP)
1. Protection avancée contre les menaces, plan 1 (ATP P1)
1. Protection avancée contre les menaces, plan 2 (ATP P2)

> [!NOTE]
> Si vous avez acheté votre abonnement et que vous avez besoin de déployer des fonctionnalités de sécurité *dès à présent*, passez aux étapes décrites dans l’article se [protéger contre les menaces](https://docs.microsoft.com/microsoft-365/security/office-365-security/protect-against-threats?view=o365-worldwide) . Si vous débutez avec votre abonnement et que vous aimeriez en obtenir la licence avant de commencer, parcourez la > facturation vos produits dans le [Centre d’administration Microsoft 365](https://admin.microsoft.com/AdminPortal/#/homepage).

La sécurité Office 365 s’appuie sur les protections principales proposées par EOP. EOP est présent dans tout abonnement où se trouvent des boîtes aux lettres Exchange Online (n’oubliez pas que tous les produits de sécurité présentés ici sont basés sur le Cloud).

Vous pouvez être habitué à voir ces trois composants présentés de la manière suivante :

|Exchange Online Protection  | ATP P1 | ATP P2  |
|---------|---------|---------|
|Empêche les attaques connues basées sur un volume et de grandes quantités.    |  Protège le courrier électronique et la collaboration contre les programmes malveillants, les hameçons et les messages électroniques de jour.       | Ajoute une enquête après effraction, une chasse et une réponse, ainsi qu’une automatisation et une simulation (pour la formation).         |

Toutefois, en ce qui concerne l’architecture, nous allons commencer par réfléchir à chaque partie en tant que couches de sécurité cumulatives, chacune avec une mise en évidence de la sécurité. Plus comme ceci :

<!--:::image type="content" source="../../media/tp-EOPATPStack.PNG" alt-text="Placeholder graphic":::-->

:::image type="content" source="../../media/tp_EOPandATPGraphic.png" alt-text="Placeholder graphic":::

Bien que chacun de ces services mette en évidence un objectif spécifique parmi les objectifs de la protection, de la détection, de l’examen et de la réponse, ***tous*** les services peuvent ***effectuer les objectifs*** de protection, de détection, d’analyse et de réponse.

Le cœur de la sécurité Office 365 est la protection EOP. ATP P1 contient EOP. ATP P2 contient P1 et EOP. La structure est cumulative. C’est pourquoi, lors de la configuration de la protection avancée contre les menaces, commencez par EOP et utilisez les couches.

Bien que la configuration de l’authentification de messagerie ait lieu dans le DNS public, il est important de configurer cette fonctionnalité pour la protéger contre l’usurpation d’identité. *Si vous disposez d’EOP,* ***vous devez [configurer l’authentification de messagerie](https://docs.microsoft.com/microsoft-365/security/office-365-security/email-validation-and-authentication?view=o365-worldwide)***.

Si vous avez un Office 365 E3 ou une version inférieure, vous disposez d’EOP, mais avec la possibilité d’acheter une solution de protection avancée contre les menaces P1 via la mise à niveau. Si vous disposez d’Office 365 E5, vous avez déjà ATP P2.

> [!TIP]
> Si votre abonnement n’est ni Office 365 E3 ni E5, vous pouvez toujours vérifier si vous avez la possibilité de procéder à une mise à niveau vers la protection avancée contre les menaces. Si vous êtes intéressé, [cette page Web](https://www.microsoft.com/microsoft-365/exchange/advance-threat-protection#coreui-contentrichblock-x07wids) répertorie les abonnements éligibles pour la mise à niveau de la protection avancée contre les menaces (à la fin de la page).

## <a name="the-office-365-security-ladder-from-eop-to-atp"></a>Échelle de sécurité Office 365 de EOP à la protection avancée contre les menaces

:::image type="content" source="../../media/tp_EOPATPEmailAuth4.gif" alt-text="Placeholder graphic":::

> [!IMPORTANT]
> Découvrez les détails de ces pages : [Exchange Online Protection](https://docs.microsoft.com/microsoft-365/security/office-365-security/exchange-online-protection-overview?view=o365-worldwide)et [Advanced Threat Protection](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-atp?view=o365-worldwide).

Les avantages de l’ajout de plans ATP à la gestion des menaces EOP pures peuvent être difficiles à déterminer à première vue. Pour vous aider à déterminer si un chemin de mise à niveau est approprié pour votre organisation, examinons les fonctionnalités de chaque produit lors de la réalisation des opérations suivantes :

 - prévention et détection des menaces
 - examen en cours
 - face

à partir d' **Exchange Online Protection**:
<p>

|Empêcher/détecter  |Examiner  |Répondre  |
|---------|---------|---------|
| Les technologies sont les suivantes :<ul><li>courrier indésirable</li><li>jouer</li><li>programmes malveillants</li><li>courrier en nombre</li><li>aide à l’usurpation d’identité</li><li>détection de l’emprunt d’identité</li><li>Mise en quarantaine de l’administrateur</li><li>Soumissions d’administrateurs et d’utilisateurs de faux positifs et faux négatifs</li><li>Autoriser/bloquer pour les URL et les fichiers</li><li>Rapports</li></u1>|<li>Recherche de journal d’audit</li><li>Suivi des messages</li>|<li>Purge automatique avec zéro heure (ZAP)</li><li>Perfectionnement et test des listes verte et rouge</li>|

Si vous souhaitez aller plus loin dans EOP, **[accédez à cet article](https://review.docs.microsoft.com/microsoft-365/security/office-365-security/exchange-online-protection-overview?view=o365-21vianet&branch=tp_EOPOverview)**.

Étant donné que ces produits sont cumulatifs, si vous évaluez la protection avancée contre les menaces et décidez de s’y abonner, vous ajouterez ces capacités.

Améliorations apportées par la **protection avancée contre les menaces, plan 1** (à ce jour) :
<p>

|Empêcher/détecter  |Examiner  |Répondre  |
|---------|---------|---------|
| Les technologies incluent tous les éléments dans EOP plus :<u1><li>Pièces jointes fiables</li><li>Liens fiables<li>Protection contre les charges de travail ATP (ex. SharePoint Online, teams, OneDrive entreprise)</li><li>Protection du temps de clic dans les e-mails, les clients Office et les équipes</li><li>Protection contre le hameçonnage (ATP)</li><li>Protection contre l’usurpation d’identité d’utilisateur et de domaine</li><li>Alertes et API d’intégration SIEM pour les alertes</li>|<li>API d’intégration SIEM pour les détections</li><li>**Outil de détection en temps réel**</li><li>Suivi d’URL</li>|<li>Identique</li></u1>

Par conséquent, ATP P1 s’étend sur le côté de la ***protection*** de la maison et ajoute des formes de ***détection***supplémentaires.

ATP P1 ajoute également des **détections en temps réel** pour les enquêtes. Ce nom d’outil de sélection de menace est en gras, car il est clair pour *savoir* si vous avez un service ATP P1. Elle n’apparaît pas dans le service ATP P2.

Améliorations apportées par la **protection avancée contre les menaces, plan 2** (à ce jour) :
<p>

|Empêcher/détecter  |Examiner  |Répondre  |
|---------|---------|---------|
| Les technologies incluent tous les éléments d’EOP et de l’ATP P1 plus :<u1><li>Identique</li>|<li>**Threat Explorer**</li><li>Suivi des menaces</li><li>Vues de campagne</li>|<li>Examen et réponse automatisés (AIR)</li><li>AIR de l’Explorateur de menaces</li><li>AIR pour les utilisateurs compromis</li><li>API d’intégration SIEM pour les enquêtes automatisées</li>

Ainsi, ATP P2 s’étend sur le côté de l' ***enquête et*** de la réponse de la maison, et ajoute un nouveau dosage de la chasse. Traitement.

Dans le service ATP P2, l’outil de chasse principal est appelé « **Explorateur de menaces** » plutôt que des détections en temps réel. Si vous voyez l’Explorateur de menaces lorsque vous accédez au centre de sécurité, c’est que vous êtes dans l’ATP P2.

Pour obtenir des informations détaillées sur les P1 et P2, **[accédez à cet article](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-atp?view=o365-worldwide)**.

> [!TIP]
> EOP et ATP sont également différents en ce qui concerne les utilisateurs finaux. Dans EOP et ATP, le focus est *conscient*, de sorte que ces deux services incluent le *complément Outlook message de rapport* afin que les utilisateurs puissent signaler les courriers électroniques qu’ils détectent comme suspects, pour une analyse plus poussée. <p> Dans le service ATP P2 (qui contient tous les éléments d’EOP et de P1), l’objectif est de suivre une *formation supplémentaire* pour les utilisateurs finals, et le centre d’exploitation de sécurité a accès à un puissant outil *simulateur de menace* , ainsi qu’aux mesures de l’utilisateur final qu’il fournit.

## <a name="office-365-atp-plan-1-vs-plan-2-cheat-sheet"></a>Feuille de triche Office 365 DAV plan 1 vs.

Ce guide de référence rapide vous aidera à comprendre les fonctionnalités fournies avec chaque abonnement ATP. Lorsqu’il est associé à votre connaissance des fonctionnalités EOP, il peut aider les décideurs à déterminer la solution disponible à la décision la plus adaptée à leurs besoins.

|Office 365 – Protection avancée contre les menaces (Plan 1)|Office 365 – Protection avancée contre les menaces (Plan 2)|
|---|---|
|<br/>Fonctionnalités de configuration, de protection et de détection : <ul><li>[Pièces jointes fiables](atp-safe-attachments.md)</li><li>[Liens fiables](atp-safe-links.md)</li><li>[ATP pour SharePoint, OneDrive et Microsoft Teams](atp-for-spo-odb-and-teams.md)</li><li>[ATP Protection anti-hameçonnage](set-up-anti-phishing-policies.md#exclusive-settings-in-atp-anti-phishing-policies)</li><li>[Détections en temps réel](threat-explorer.md)</li></ul>|Fonctionnalités de l’offre Office 365 - Protection avancée contre les menaces (plan 1)<br/>--- plus ---<br/>Fonctionnalités d’automatisation, d’examen, de correction et de formation :</li><li>[Suivi des menaces](threat-trackers.md)</li><li>[Threat Explorer](threat-explorer.md)</li><li>[Examen et réponse automatisés](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-air)</li><li>[Simulateur d’attaques](attack-simulator.md)</li></ul>|
|

- Office 365 – Protection avancée contre les menaces (Plan 2) est inclus dans Office 365 E5, Office 365 a5 et Microsoft 365 E5.

- Le plan 1 Office 365 ATP est incluse dans Microsoft 365 Business Premium.

- Le plan 1 Office 365 ATP et le Plan 2 Office 365 ATP sont, pour certains abonnements, disponibles sous forme de complément. Pour en savoir plus, voici une autre [fonctionnalité de liaison disponible pour tous les plans ATP](https://docs.microsoft.com/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans).

- La fonctionnalité [Documents sécurisés](safe-docs.md) est uniquement disponible pour les utilisateurs ayant des licences Microsoft 365 E5 ou Microsoft 365 E5 Sécurité (non inclus dans les plans Office 365 ATP)

- Si votre abonnement actuel n’inclut pas Office 365 ATP et que vous le souhaitez, [contactez sales pour commencer une version d’évaluation](https://go.microsoft.com/fwlink/p/?LinkId=518644)et découvrez le fonctionnement de l’ATP pour votre organisation.

> [!TIP]
> ***Conseil Insider***. Vous pouvez utiliser la table des matières docs.microsoft.com pour en savoir plus sur EOP et la protection avancée contre les menaces. Accédez aux articles sur la [sécurité d’Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/security-roadmap?view=o365-worldwide) et vous remarquerez que l’organisation de la table des matières commence par l’évaluation et le déploiement (y compris la migration), puis continue à la prévention, la détection, l’enquête et la réponse. <p> Cette structure est divisée de manière à ce que les rubriques relatives à l’administration de la **sécurité** soient suivies par les rubriques **opérations de sécurité** . Si vous êtes un nouveau membre de l’un des rôles de travail, utilisez le lien de ce Conseil et vos connaissances de la table des matières pour en savoir plus sur l’espace. N’oubliez pas d’utiliser les *liens de commentaires* et les *Articles de taux* au fur et à mesure. Les commentaires nous permettent d’améliorer votre offre.
