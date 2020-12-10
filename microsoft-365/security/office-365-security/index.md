---
title: Sécurité Office 365, Microsoft Defender pour Office 365, EOP, MSDO
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
- M365-security-compliance
- m365initiative-m365-defender
description: La sécurité dans Office 365, de EOP à Defender pour Office 365 prévoit 1 et 2, des configurations de sécurité standard ou rigoureuses, et bien plus encore. Comprendre ce dont vous disposez et comment sécuriser vos propriétés.
ms.openlocfilehash: 84d7dcfc68ce78bfde92f3d7096cd4104355ce94
ms.sourcegitcommit: ee39faf3507d0edc9497117b3b2854955c959c6c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "49616247"
---
# <a name="office-365-security-overview"></a>Vue d’ensemble de la sécurité d’Office 365

Cet article vous présente vos nouvelles propriétés de sécurité dans le Cloud. Que vous soyez membre d’un centre de sécurité, vous êtes un administrateur de sécurité, ou vous souhaitez un actualisateur, commençons.

> [!CAUTION]
> Si vous utilisez **Outlook.com**, la **famille Microsoft 365** ou **Microsoft 365 personnel**, et que vous avez besoin de *liens fiables* ou d’informations de *pièces jointes fiables* , ***cliquez sur ce lien** _ : [sécurité avancée Outlook.com pour les abonnés Microsoft 365](https://support.microsoft.com/office/advanced-outlook-com-security-for-office-365-subscribers-882d2243-eab9-4545-a58a-b36fee4a46e2).

## <a name="office-365-security-spelled-out"></a>Sécurité Office 365

Chaque abonnement Office 365 est fourni avec des fonctionnalités de sécurité. Les objectifs et les actions que vous pouvez effectuer dépendent de l’intérêt de ces différents abonnements. Dans la sécurité Office 365, trois services de sécurité (ou produits) principaux sont liés à votre type d’abonnement :

1. Exchange Online Protection (EOP)
1. Microsoft Defender pour Office 365 plan 1 (Defender pour Office P1)
1. Microsoft Defender pour Office 365 plan 2 (Defender pour Office P2)

> [!NOTE]
> Si vous avez acheté votre abonnement et que vous devez déployer des fonctionnalités de sécurité _right maintenant *, passez aux étapes décrites dans l’article se [protéger contre les menaces](protect-against-threats.md) . Si vous débutez avec votre abonnement et que vous aimeriez en obtenir la licence avant de commencer, parcourez la > facturation vos produits dans le [Centre d’administration Microsoft 365](https://admin.microsoft.com/AdminPortal/#/homepage).

La sécurité Office 365 s’appuie sur les protections principales proposées par EOP. EOP est présent dans tout abonnement où se trouvent des boîtes aux lettres Exchange Online (n’oubliez pas que tous les produits de sécurité présentés ici sont basés sur le Cloud).

Vous pouvez être habitué à voir ces trois composants présentés de la manière suivante :

|Exchange Online Protection|Microsoft Defender pour Office 365 P1|Microsoft Defender pour Office 365 P2|
|---|---|---|
|Empêche les attaques connues basées sur un volume et de grandes quantités.|Protège le courrier électronique et la collaboration contre les programmes malveillants, les hameçons et les messages électroniques de jour.|Ajoute une enquête après effraction, une chasse et une réponse, ainsi qu’une automatisation et une simulation (pour la formation).|
|

Toutefois, en ce qui concerne l’architecture, nous allons commencer par réfléchir à chaque partie en tant que couches de sécurité cumulatives, chacune avec une mise en évidence de la sécurité. Plus comme ceci :

<!--:::image type="content" source="../../media/tp-EOPATPStack.PNG" alt-text="Placeholder graphic":::-->

:::image type="content" source="../../media/tp_GraphicEOPATPP1P2_2.png" alt-text="EOP et Microsoft Defender pour Office 365 et leurs relations les uns avec les autres avec l’accent sur les services, y compris une remarque pour l’authentification de messagerie.":::

Bien que chacun de ces services insiste sur un objectif de la protection, de la détection, de _*_l'_*_ enquête et de la réponse, ***tous** les services peuvent effectuer tous les objectifs de protection, de détection, d’enquête et de réponse.

Le cœur de la sécurité Office 365 est la protection EOP. Microsoft Defender pour Office 365 P1 contient EOP. Defender pour Office 365 P2 contient P1 et EOP. La structure est cumulative. C’est pourquoi, lors de la configuration de ce produit, vous devez commencer avec EOP et travailler sur Defender pour Office 365.

Bien que la configuration de l’authentification de messagerie ait lieu dans le DNS public, il est important de configurer cette fonctionnalité pour la protéger contre l’usurpation d’identité. _Si vous avez un EOP, * ***vous devez [configurer l’authentification de messagerie](email-validation-and-authentication.md)**_.

Si vous avez un Office 365 E3 ou une version inférieure, vous disposez d’EOP, mais avec la possibilité d’acheter un Defender autonome pour Office 365 P1 via la mise à niveau. Si vous disposez d’Office 365 E5, vous disposez déjà de l’offre Defender pour Office 365 P2.

> [!TIP]
> Si votre abonnement n’est ni Office 365 E3 ni E5, vous pouvez toujours vérifier si vous avez la possibilité d’effectuer une mise à niveau vers Microsoft Defender pour Office 365 P1. Si vous êtes intéressé, [cette page Web](https://www.microsoft.com/microsoft-365/exchange/advance-threat-protection#coreui-contentrichblock-x07wids) répertorie les abonnements éligibles pour la mise à niveau de Microsoft Defender pour Office 365 P1 (à la fin de la page pour l’impression fine).

## <a name="the-office-365-security-ladder-from-eop-to-microsoft-defender-for-office-365"></a>Échelle de sécurité Office 365 de EOP à Microsoft Defender pour Office 365

![EOP et Microsoft Defender pour Office 365 et leur impact sur la sécurité, allant de Protect et Detect pour examiner et répondre. La configuration de l’authentification de messagerie (au moins DKIM et DMARC) doit être configurée pour EOP et up.](../../media/tp_EOPATPP1P2Take6.gif#lightbox)

> [!IMPORTANT]
> Découvrez les détails de ces pages : [Exchange Online Protection](exchange-online-protection-overview.md)et [defender for Office 365](office-365-atp.md).

Ce qui rend l’ajout de Microsoft Defender pour Office 365 offre un avantage à la gestion des menaces EOP pures peut être difficile à déterminer à première vue. Pour vous aider à déterminer si un chemin de mise à niveau est approprié pour votre organisation, examinons les fonctionnalités de chaque produit lors de la réalisation des opérations suivantes :

- prévention et détection des menaces
- examen en cours
- face

à partir de _ * Exchange Online Protection * * :
<p>

|Empêcher/détecter|Examiner|Répondre|
|---|---|---|
|Les technologies sont les suivantes :<ul><li>courrier indésirable</li><li>jouer</li><li>programmes malveillants</li><li>courrier en nombre</li><li>aide à l’usurpation d’identité</li><li>détection de l’emprunt d’identité</li><li>Mise en quarantaine de l’administrateur</li><li>Soumissions d’administrateurs et d’utilisateurs de faux positifs et faux négatifs</li><li>Autoriser/bloquer pour les URL et les fichiers</li><li>Rapports</li></u1>|<li>Recherche de journal d’audit</li><li>Suivi des messages</li>|<li>Purge automatique avec zéro heure (ZAP)</li><li>Perfectionnement et test des listes verte et rouge</li>|
|

Si vous souhaitez aller plus loin dans EOP, **[accédez à cet article](exchange-online-protection-overview.md)**.

Étant donné que ces produits sont cumulatifs, si vous évaluez Microsoft Defender pour Office 365 P1 et décidez de s’y abonner, vous ajouterez ces capacités.

Profits with **Defender for Office 365, plan 1** (to date) :
<p>

|Empêcher/détecter|Examiner|Répondre|
|---|---|---|
|Les technologies incluent tous les éléments dans EOP plus :<u1><li>Pièces jointes fiables</li><li>Liens fiables<li>Microsoft Defender pour Office 365 protection des charges de travail (par exemple, SharePoint Online, teams, OneDrive entreprise)</li><li>Protection du temps de clic dans les e-mails, les clients Office et les équipes</li><li>anti-hameçonnage dans Defender pour Office 365</li><li>Protection contre l’usurpation d’identité d’utilisateur et de domaine</li><li>Alertes et API d’intégration SIEM pour les alertes</li>|<li>API d’intégration SIEM pour les détections</li><li>**Outil de détection en temps réel**</li><li>Suivi d’URL</li>|<li>Identique</li></u1>

Par conséquent, Microsoft Defender pour Office 365 P1 se développe sur le côté **_Prevention_* _ de la maison et ajoute des formes de _*_détection_*_ supplémentaires.

Microsoft Defender pour Office 365 P1 ajoute également des *détections en temps réel** pour les enquêtes. Le nom de cet outil de sélection de menace est en gras, car il est clair pour *savoir* si vous avez l’outil Defender pour Office 365 P1. Il n’apparaît pas dans Defender pour Office 365 P2.

Plus-values with **Defender for Office 365, plan 2** (to date) :
<p>

|Empêcher/détecter|Examiner|Répondre|
|---|---|---|
|Les technologies incluent tous les éléments d’EOP et Microsoft Defender pour Office 365 P1 plus :<u1><li>Identique</li>|<li>**Threat Explorer**</li><li>Suivi des menaces</li><li>Vues de campagne</li>|<li>Examen et réponse automatisés (AIR)</li><li>AIR de l’Explorateur de menaces</li><li>AIR pour les utilisateurs compromis</li><li>API d’intégration SIEM pour les enquêtes automatisées</li>

Par conséquent, Microsoft Defender pour Office 365 P2 s’étend sur le côté **_enquête et réponse_* _ de la maison, et ajoute un nouveau dosage de la chasse. Traitement.

Dans Microsoft Defender pour Office 365 P2, l’outil de chasse principal est appelé _ *Threat Explorer** plutôt que les détections en temps réel. Si vous voyez l’Explorateur de menaces lorsque vous accédez au centre de sécurité, c’est que vous êtes dans Microsoft Defender pour Office 365 P2.

Pour obtenir des informations détaillées sur Microsoft Defender pour Office 365 P1 et P2, **[accédez à cet article](office-365-atp.md)**.

> [!TIP]
> EOP et Microsoft Defender pour Office 365 sont également différents quand il s’agit d’utilisateurs finaux. Dans EOP et Defender pour Office 365 P1, le focus est *conscient*, de sorte que ces deux services incluent le *complément Outlook message de rapport* afin que les utilisateurs puissent signaler les e-mails suspects, pour une analyse plus poussée. <p> Dans Defender for Office 365 P2 (qui contient toutes les fonctionnalités d’EOP et de P1), l’objectif est de *poursuivre la formation* pour les utilisateurs finals, de sorte que le Centre des opérations de sécurité ait accès à un puissant outil de *simulateur de menace* et aux mesures de l’utilisateur final qu’il fournit.

## <a name="microsoft-defender-for-office-365-plan-1-vs-plan-2-cheat-sheet"></a>Microsoft Defender pour Office 365 plan 1 vs. plan 2-feuille de triche

Ce guide de référence rapide vous aidera à comprendre les fonctionnalités fournies avec chaque abonnement Microsoft Defender pour Office 365. Lorsqu’il est associé à votre connaissance des fonctionnalités EOP, il peut aider les décideurs à déterminer ce que Microsoft Defender pour Office 365 est le mieux adapté à leurs besoins.

|Defender pour Office 365 plan 1|Defender pour Office 365 plan 2|
|---|---|
|Fonctionnalités de configuration, de protection et de détection : <ul><li>[Pièces jointes fiables](atp-safe-attachments.md)</li><li>[Liens fiables](atp-safe-links.md)</li><li>[ATP pour SharePoint, OneDrive et Microsoft Teams](atp-for-spo-odb-and-teams.md)</li><li>[Protection anti-hameçonnage dans Defender pour Office 365](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)</li><li>[Détections en temps réel](threat-explorer.md)</li></ul>|Fonctionnalités de l’offre Defender pour Office 365 plan 1 <p> --- plus --- <p> Fonctionnalités d’automatisation, d’examen, de correction et de formation : <ul><li>[Suivi des menaces](threat-trackers.md)</li><li>[Threat Explorer](threat-explorer.md)</li><li>[Examen et réponse automatisés](office-365-air.md)</li><li>[Simulateur d’attaques](attack-simulator.md)</li></ul>|
|

- Microsoft Defender pour Office 365 plan 2 est inclus dans Office 365 E5, Office 365 a5 et Microsoft 365 E5.

- Microsoft Defender pour Office 365 plan 1 est inclus dans Microsoft 365 Business Premium.

- Microsoft Defender pour Office 365 plan 1 et Defender for Office 365 plan 2 sont disponibles en tant que complément pour certains abonnements. Pour en savoir plus, voici une autre [fonctionnalité de liaison disponible dans les plans Microsoft Defender pour Office 365](https://docs.microsoft.com/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans).

- La fonctionnalité [documents approuvés](safe-docs.md) est uniquement disponible pour les utilisateurs disposant des licences Microsoft 365 E5 ou Microsoft 365 E5 (non incluses dans les offres Microsoft Defender pour Office 365).

- Si votre abonnement actuel n’inclut pas Microsoft Defender pour Office 365 et que vous le souhaitez, [contactez sales pour commencer une version d’évaluation](https://go.microsoft.com/fwlink/p/?LinkId=518644)et découvrez comment Microsoft Defender pour Office 365 peut fonctionner dans votre organisation.

> [!TIP]
> ***Conseil pour les Insiders** _. Vous pouvez utiliser la table des matières docs.microsoft.com pour en savoir plus sur EOP et Microsoft Defender pour Office 365. Accédez à cette page, [vue d’ensemble de la sécurité Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security), et vous remarquerez que l’organisation de la table des matières est située dans la barre latérale. Il commence par le déploiement (y compris la migration), puis continue à la prévention, la détection, l’enquête et la réponse. <p> Cette structure est divisée de telle sorte que _ rubriques d’administration de la *sécurité** sont suivies par des rubriques relatives aux **opérations de sécurité** . Si vous êtes un nouveau membre de l’un des rôles de travail, utilisez le lien de ce Conseil et vos connaissances de la table des matières pour en savoir plus sur l’espace. N’oubliez pas d’utiliser les *liens de commentaires* et les *Articles de taux* au fur et à mesure. Les commentaires nous permettent d’améliorer votre offre.

## <a name="where-to-go-next"></a>Emplacement suivant

Si vous êtes un administrateur de la sécurité, vous devrez peut-être configurer DKIM ou DMARC pour votre courrier. Vous souhaiterez peut-être déployer des préréglages de sécurité « stricts » pour vos utilisateurs prioritaires ou rechercher les nouveautés du produit. Si vous êtes avec des opérations de sécurité, vous souhaiterez peut-être utiliser des détections en temps réel ou l’Explorateur de menaces pour examiner et répondre, ou pour former une détection d’utilisateur final avec un simulateur d’attaque. Dans les deux cas, voici quelques recommandations supplémentaires sur ce qu’il faut examiner.

[Authentification de messagerie, y compris SPF, DKIM et DMARC (avec des liens vers le programme d’installation de tous les trois)](email-validation-and-authentication.md)

[Voir les configurations « Golden » recommandées spécifiques](recommended-settings-for-eop-and-office365-atp.md) et [utiliser leurs préréglages recommandés pour configurer les stratégies de sécurité rapidement](preset-security-policies.md)

[Découvrez les nouveautés de Microsoft Defender pour Office 365 (y compris les développements EOP)](whats-new-in-office-365-atp.md)

[Utilisation de l’Explorateur de menaces ou des détections en temps réel](threat-explorer.md)

Utiliser un [simulateur d’attaque dans Microsoft Defender pour Office 365](attack-simulator.md)
