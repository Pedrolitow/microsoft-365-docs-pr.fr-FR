---
title: Sécurité Office 365, notamment Microsoft Defender pour Office 365 et Exchange Online Protection
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: 07/21/2021
audience: Admin
ms.topic: conceptual
ms.localizationpriority: high
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Security in Office 365, from EOP to Defender for Office 365 Plans 1 and 2, Standard vs. Strict security configurations, and more. Understand what you have, and how to secure your properties.
ms.subservice: mdo
ms.service: microsoft-365-security
adobe-target: true
ms.openlocfilehash: 6a2c9841a894ad46614cca4b1ee768eac1fd2a35
ms.sourcegitcommit: 0af064e8b6778060f1bd365378d69b16fc9949b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2022
ms.locfileid: "67879191"
---
# <a name="microsoft-defender-for-office-365-security-overview"></a>Vue d’ensemble de la sécurité de Microsoft Defender pour Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)

Cet article vous présente vos nouvelles propriétés de sécurité Microsoft Defender pour Office 365 dans le cloud. Que vous fassiez partie d'un Centre d'opérations de sécurité, que vous soyez un administrateur de sécurité débutant dans ce domaine ou que vous souhaitiez rafraîchir vos connaissances, nous allons commencer..

> [!CAUTION]
> Si vous utilisez **Outlook.com**, **Microsoft 365 Famille** ou **Microsoft 365 Personnel** et que vous avez besoin d’informations sur les *Liens fiables* ou *Pièces jointes fiables* ***cliquez sur ce lien*** : [Sécurité Outlook.com renforcée pour abonnés Microsoft 365](https://support.microsoft.com/office/advanced-outlook-com-security-for-office-365-subscribers-882d2243-eab9-4545-a58a-b36fee4a46e2).

## <a name="what-is-defender-for-office-365-security"></a>Présentation de la sécurité de Defender pour Office 365

Tous les abonnements Office 365 offrent des fonctionnalités de sécurité. Les objectifs et les actions que vous pouvez entreprendre dépendent de l'orientation de ces différents abonnements. Dans la sécurité Office 365, trois principaux services de sécurité (ou produits) sont liés à votre type d’abonnement :

1. Exchange Online Protection (EOP)
1. Microsoft Defender pour Office 365 Plan 1 (Defender pour Office P1)
1. Microsoft Defender pour Office 365 Plan 2 (Defender pour Office P2)

> [!NOTE]
> Si vous avez acheté votre abonnement et que vous avez besoin de déployer les fonctionnalités de sécurité *immédiatement*, passez directement aux étapes de l’article [Protéger contre les menaces](protect-against-threats.md). Si vous débutez avec votre abonnement et souhaitez connaître votre licence avant de commencer, parcourez Facturation > Vos produits dans le [Centre d’administration Microsoft 365](https://admin.microsoft.com/AdminPortal/#/homepage).

Les builds de sécurité Office 365 s’appuient sur les principales protections offertes par EOP. EOP est présent dans tous les abonnements où des boîtes aux lettres Exchange Online sont disponibles (n’oubliez pas que tous les produits de sécurité abordés ici sont basés sur le cloud).

Vous avez peut-être l’habitude de voir ces trois composants abordés de cette façon :

|Exchange Online Protection|Microsoft Defender pour Office 365 Plan 1|Microsoft Defender pour Office 365 Plan 2|
|---|---|---|
|Empêche les attaques connues, de grande envergure et basées sur le volume.|Protège la messagerie et la collaboration contre les logiciels malveillants de type « zero-day », le hameçonnage et la compromission de la messagerie professionnelle.|Ajoute des examens après la violation, des recherches et des réponses, ainsi qu’une automatisation et une simulation (pour la formation).|

But in terms of architecture, let's start by thinking of each piece as cumulative layers of security, each with a security emphasis. More like this:

:::image type="content" source="../../media/tp_GraphicEOPATPP1P2_2.png" alt-text="EOP et Microsoft Defender pour Office 365 et leurs relations les uns avec les autres grâce au service et à une note pour l’authentification des messages électroniques" lightbox="../../media/tp_GraphicEOPATPP1P2_2.png":::

Bien que chacun de ces services mette l'accent sur un objectif parmi les suivants : protéger, détecter, examiner et réagir, ***tous** _ les services peuvent effectuer _ *_n'importe quel_** des objectifs de protection, de détection, d'examen et de réaction.

La protection EOP constitue le cœur de la sécurité dans Office 365. Microsoft Defender pour Office 365 Plan 1 contient EOP. Defender pour Office 365 P2 contient P1 et EOP. La structure est cumulée. C’est pourquoi, lors de la configuration de ce produit, vous devez commencer avec EOP et travailler sur Defender pour Office 365.

Though email authentication configuration takes place in public DNS, it's important to configure this feature to help defend against spoofing. *If you have EOP,* ***you should [configure email authentication](email-validation-and-authentication.md)***.

Si vous avez un Office 365 E3, ou une version inférieure, vous avez EOP, mais avec l'option d'acheter Defender pour Office 365 P1 par mise à jour. Si vous avez Office 365 E5, vous avez déjà Defender pour Office 365 P2.

> [!TIP]
> Si votre abonnement n'est ni Office 365 E3 ni E5, vous pouvez toujours vérifier si vous avez la possibilité de passer à Microsoft Defender pour Office 365 P1. Si vous le souhaitez, [cette page web](https://www.microsoft.com/microsoft-365/exchange/advance-threat-protection#coreui-contentrichblock-x07wids) répertorie les abonnements éligibles à la mise à niveau Microsoft Defender pour Office 365 P1 (voir la fin de la page pour savoir si cette version est bien imprimée).

## <a name="the-office-365-security-ladder-from-eop-to-microsoft-defender-for-office-365"></a>Sécurité d’Office 365 EOP à Microsoft Defender pour Office 365

> [!IMPORTANT]
> Découvrez les détails de ces pages : [Exchange Online Protection](exchange-online-protection-overview.md)et [Defender pour Office 365](defender-for-office-365.md).

Ce qui fait de l'ajout des plans Microsoft Defender pour Office 365 un avantage par rapport à la gestion pure des menaces EOP peut être difficile à dire à première vue. Pour vous aider à déterminer si une mise à niveau convient à votre entreprise, examinons les capacités de chaque produit en matière de :

- prévention et détection des menaces
- examen
- réponse

à partir de **Exchange Online Protection**:
<p>

|Prévention/détection|Examiner|Répondre|
|---|---|---|
|Les technologies comprennent :<ul><li>courrier indésirable</li><li>hameçonnage</li><li>programme malveillant</li><li>courrier en nombre</li><li>veille contre l'usurpation d'identité</li><li>détection d’emprunt d’identité</li><li>Mise en quarantaine de l’administrateur</li><li>Envois de faux positifs et de faux négatifs par l’administrateur et l’utilisateur</li><li>Autoriser/Bloquer pour les URL et fichiers</li><li>Rapports</li></ul>|<li>Recherche de journal d’audit</li><li>Suivi des messages</li>|<li>Purge automatique zéro heure (PAZH)</li><li>Affinement et test des listes d’autoriser et de blocage</li>|

Si vous souhaitez approfondir EOP, **[passez à cet article](exchange-online-protection-overview.md)**.

Étant donné que ces produits sont cumulatives, si vous évaluez Microsoft Defender pour Office 365 P1 et que vous décidez de vous y abonner, vous ajouterez ces aptitudes.

Gains avec **Defender pour Office 365, Plan 1** (à ce jour) :
<p>

|Prévention/détection|Examiner|Répondre|
|---|---|---|
|Les technologies incluent tous les avantages EOP ainsi que les avantages suivants :<ul><li>Pièces jointes fiables</li><li>Liens fiables<li>Protection Microsoft Defender pour Office 365 pour les charges de travail (par exemple, SharePoint Online, Teams, OneDrive Entreprise</li><li>Protection par clic dans le courrier électronique, les clients Office et Teams</li><li>Anti-hameçonnage dans Defender pour Office 365</li><li>Protection de l’emprunt d’identité d’utilisateur et de domaine</li><li>Alertes et API d’intégration SIEM pour les alertes</li>|<li>API d’intégration SIEM pour les détections</li><li>**Outil de détection en temps réel**</li><li>traçage d’URL</li>|<li>Identique</li></ul>

Ainsi, Microsoft Defender pour Office 365 P1 s'étend sur le côté ***prévention** _ de la maison, et ajoute des formes supplémentaires de _*_détection_**.

Microsoft Defender pour Office 365 P1 ajoute également des fonctions de **Détection en temps réel** pour les enquêtes. Le nom de cet outil de menace est en gras, car il est clairement utilisé pour *savoir* que vous disposez Defender pour Office 365 P1. Il n'apparaît pas dans Defender pour Office 365 P2.

Gains avec **Defender pour Office 365, Plan 2** (à ce jour) :
<p>

|Prévention/détection|Examiner|Répondre|
|---|---|---|
|Les technologies incluent tous les logiciels EOP, Microsoft Defender pour Office 365 P1 ainsi que :<ul><li>Identique</li>|<li>**Explorateur de menaces**</li><li>Suivi des menaces</li><li>Affichages de campagne</li>|<li>Enquêtes et réponses automatisées (AIR)</li><li>AIR à partir de l’Explorateur de menaces</li><li>Enquêtes et réponses automatisées pour les utilisateurs compromis</li><li>API d’intégration SIEM pour les enquêtes automatisées</li>

So, Microsoft Defender for Office 365 P2 expands on the ***investigation and response*** side of the house, and adds a new hunting strength. Automation.

Dans Microsoft Defender pour Office 365 P2, l’outil de repérage principal de l’**Explorateur de menaces** s’appelle la détection en temps réel. Si l’explorateur des menaces s’affiche lorsque vous accédez au portail Microsoft 365 Defender, vous êtes dans Microsoft Defender pour Office 365 P2.

Pour en savoir plus sur Microsoft Defender pour Office 365 P1 et P2, **[consulter cet article](defender-for-office-365.md)**.

> [!TIP]
> EOP and Microsoft Defender for Office 365 are also different when it comes to end-users. In EOP and Defender for Office 365 P1, the focus is *awareness*, and so those two services include the *Report message Outlook add-in* so users can report emails they find suspicious, for further analysis. <p> Dans Defender pour Office 365 P2 (qui contient tous les éléments dans EOP et P1), le focus est déplacé vers *formation supplémentaires* pour les utilisateurs finaux. Ainsi, le Centre des opérations de sécurité a accès à un puissant outil *Simulateur de menace* et aux mesures qu’il fournit aux utilisateurs finaux.

## <a name="microsoft-defender-for-office-365-plan-1-vs-plan-2-cheat-sheet"></a>Fiche d'information sur Microsoft Defender pour Office 365 Plan 1 vs. Plan 2

Cette référence rapide vous aide à comprendre les fonctionnalités fournies avec chaque abonnement à Microsoft Defender pour Office 365. Combiné à votre connaissance des fonctionnalités de l'EOP, il peut aider les décideurs d'entreprise à déterminer quel Microsoft Defender pour Office 365 est le mieux adapté à leurs besoins.

|Microsoft Defender pour Office 365 Plan 1|Microsoft Defender pour Office 365 Plan 2|
|---|---|
|Fonctionnalités de configuration, de protection et de détection : <ul><li>[Pièces jointes fiables](safe-attachments.md)</li><li>[Liens fiables](safe-links.md)</li><li>[Pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams](mdo-for-spo-odb-and-teams.md)</li><li>[Protection contre le hameçonnage dans Defender pour Office 365](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)</li><li>[Détections en temps réel](threat-explorer.md)</li></ul>|Fonctionnalités de Microsoft Defender pour Office 365 Plan 1 <p> --- plus --- <p> Fonctionnalités d’automatisation, d’examen, de correction et de formation : <ul><li>[Suivi des menaces](threat-trackers.md)</li><li>[Threat Explorer](threat-explorer.md)</li><li>[Examen et réponse automatisés](office-365-air.md)</li><li>[Formation à la simulation d'attaque](attack-simulation-training.md)</li><li>[Recherche proactive des menaces avec repérage avancé dans Microsoft 365 Defender](../defender/advanced-hunting-overview.md)</li><li>[Examiner les incidents dans Microsoft 365 Defender](../defender/investigate-incidents.md)</li><li>[Examiner les alertes dans Microsoft 365 Defender](../defender/investigate-alerts.md)</li></ul>|

- Microsoft Defender pour Office 365 Plan 2 est inclus dans Office 365 E5, Office 365 A5 et Microsoft 365 E5.

- Microsoft Defender pour Office 365 Plan 1 est inclus dans Microsoft 365 Business Premium.

- Microsoft Defender pour Office 365 Plan 1 et Defender pour Office 365 Plan 2 sont tous deux disponibles sous forme de modules complémentaires pour certains abonnements. Pour en savoir plus, voici un autre lien [Disponibilité des fonctionnalités pour les offres Microsoft Defender pour Office 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans).

- La fonctionnalité [Documents sécurisés](safe-docs.md) est uniquement disponible pour les utilisateurs ayant des licences Microsoft 365 A5 ou Microsoft 365 E5 Sécurité (non inclus dans les offres Microsoft Defender pour Office 365)

- Si votre abonnement actuel n’inclut pas Microsoft Defender pour Office 365 et que vous le souhaitez, [contactez le service commercial pour commencer une version d’évaluation](https://info.microsoft.com/ww-landing-M365SMB-web-contact.html) et découvrez comment Microsoft Defender pour Office 365 peut fonctionner dans votre organisation.

- Les clients Microsoft Defender pour Office 365 P2 ont accès à **l’intégration Microsoft 365 Defender** pour détecter, examiner et répondre efficacement aux incidents et alertes.

> [!TIP]
> ***Conseil Insider** _. Vous pouvez utiliser la table des matières Microsoft Docs pour en savoir plus sur EOP et Microsoft Defender pour Office 365. Revenez à cette page, [Vue d’ensemble de la sécurité Office 365](index.yml), vous remarquerez que l’organisation de la table des matières est dans la barre latérale. Elle commence par le déploiement (y compris la migration), puis se poursuit par la prévention, la détection, l'enquête et la réponse. <p> Cette structure est divisée de telle sorte que les rubriques _ *Administration de la sécurité** sont suivies de rubriques **Opérations de sécurité**. Si vous êtes un nouveau membre de l’une des fonctions, utilisez le lien dans ce conseil et vos connaissances de la table des matières pour découvrir l’espace. N'oubliez pas d'utiliser les *liens de commentaires* et d'*évaluer les articles* au fur et à mesure. Vos commentaires nous aident à améliorer ce que nous vous proposons.

## <a name="where-to-go-next"></a>Quelle est la prochaine étape ?

Si vous êtes un administrateur de sécurité, vous devrez peut-être configurer DKIM ou DMARC pour votre courrier. Vous voudrez peut-être déployer des préréglages de sécurité « Strict » pour vos utilisateurs prioritaires, ou rechercher les nouveautés du produit. Si vous travaillez dans le domaine de la sécurité, vous voudrez peut-être utiliser les détections en temps réel ou Explorateur de menaces pour enquêter et réagir, ou former les utilisateurs finaux à la détection avec le Simulateur d'attaque. Dans les deux cas, voici quelques recommandations supplémentaires sur les prochaines étapes à examiner.

[Authentification du courrier électronique, y compris SPF, DKIM et DMARC (avec des liens vers la configuration des trois)](email-validation-and-authentication.md)

[Consultez les configurations « base » recommandées spécifiques ](recommended-settings-for-eop-and-office365.md) et [utilisez les préréglages recommandés pour configurer rapidement les stratégies de sécurité](preset-security-policies.md)

Découvrir les [Nouveautés Microsoft Defender pour Office 365 (y compris les développements EOP)](whats-new-in-defender-for-office-365.md)

[Utiliser l’Explorateur de menaces ou la détection en temps réel](threat-explorer.md)

Utiliser la [Formation de simulation d’attaque](attack-simulation-training.md)
