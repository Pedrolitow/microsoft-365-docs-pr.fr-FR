---
title: Sécurité Office 365, Microsoft Defender pour Office 365, EOP, MSDO
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: 08/13/2020
audience: Admin
ms.topic: overview
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: La sécurité dans Office 365, d’EOP à Defender pour les plans 1 et 2 Office 365, les configurations de sécurité standard et stricte, et bien plus encore. Comprenez ce que vous avez et comment sécuriser vos propriétés.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 68570cedd0696510f2181edcea7ef149ace606e3
ms.sourcegitcommit: a1846b1ee2e4fa397e39c1271c997fc4cf6d5619
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2021
ms.locfileid: "50166416"
---
# <a name="office-365-security-overview"></a>Vue d’ensemble de la sécurité Office 365

**S’applique à**
- [Exchange Online Protection](https://go.microsoft.com/fwlink/?linkid=2148611)
- [Microsoft Defender pour Office 365 plan 1 et plan 2](https://go.microsoft.com/fwlink/?linkid=2148715)


Cet article vous présente vos nouvelles propriétés de sécurité dans le Cloud. Que vous faites partie d’un centre des opérations de sécurité, que vous débutiez en tant qu’administrateur de sécurité dans l’espace ou que vous vouliez un actualiseur, nous allons commencer.

> [!CAUTION]
> Si vous utilisez **Outlook.com,** **Microsoft 365 Famille** ou **Microsoft 365 Personnel** et que vous avez besoin de liens sécurisés ou d’informations de pièces *jointes sécurisées,* cliquez sur ce lien : Sécurité Outlook.com avancée pour les abonnés [Microsoft 365.](https://support.microsoft.com/office/advanced-outlook-com-security-for-office-365-subscribers-882d2243-eab9-4545-a58a-b36fee4a46e2) 

## <a name="office-365-security-spelled-out"></a>Sécurité Office 365

Chaque abonnement Office 365 est livré avec des fonctionnalités de sécurité. Les objectifs et les actions que vous pouvez prendre dépendent de l’objectif de ces différents abonnements. Dans la sécurité Office 365, il existe trois principaux services de sécurité (ou produits) liés à votre type d’abonnement :

1. Exchange Online Protection (EOP)
1. Microsoft Defender pour Office 365 Plan 1 (Defender pour Office P1)
1. Microsoft Defender pour Office 365 Plan 2 (Defender pour Office P2)

> [!NOTE]
> Si vous avez acheté votre abonnement et que vous devez déployer des fonctionnalités de sécurité immédiatement, passez aux étapes de l’article Protéger [contre les menaces.](protect-against-threats.md) Si vous débutez dans votre abonnement et que vous souhaitez connaître votre licence avant de commencer, accédez à Facturation > Vos produits dans le Centre d’administration [Microsoft 365.](https://admin.microsoft.com/AdminPortal/#/homepage)

La sécurité Office 365 s’appuie sur les protections de base offertes par EOP. EOP est présent dans n’importe quel abonnement où des boîtes aux lettres Exchange Online sont disponibles (n’oubliez pas que tous les produits de sécurité abordés ici sont basés sur le cloud).

Vous êtes peut-être habitué à voir ces trois composants abordés de cette façon :

|Exchange Online Protection|Microsoft Defender pour Office 365 P1|Microsoft Defender pour Office 365 P2|
|---|---|---|
|Empêche les attaques connues, larges et basées sur un volume.|Protège le courrier électronique et la collaboration contre les programmes malveillants, le hameçonnage et la compromission de la messagerie professionnelle.|Ajoute l’examen, le recherche et la réponse après violation, ainsi que l’automatisation et la simulation (pour la formation).|
|

Toutefois, en termes d’architecture, nous allons commencer par penser à chaque élément comme des couches cumulatives de sécurité, chacune avec une importance particulière pour la sécurité. Voici quelques-unes des informations ci-après :

<!--:::image type="content" source="../../media/tp-EOPATPStack.PNG" alt-text="Placeholder graphic":::-->

:::image type="content" source="../../media/tp_GraphicEOPATPP1P2_2.png" alt-text="EOP et Microsoft Defender pour Office 365 et leurs relations les uns avec les autres avec l’accentuation du service, y compris une note pour l’authentification de messagerie.":::

Bien que chacun de ces services met l’accent sur l’objectif de protéger, détecter, examiner et répondre,***** tous _ les services peuvent effectuer *___* n’importe quel * des objectifs de protection, de détection, d’examen et de réponse.

Le cœur de la sécurité Office 365 est la protection EOP. Microsoft Defender pour Office 365 P1 contient EOP. Defender pour Office 365 P2 contient P1 et EOP. La structure est cumulative. C’est pourquoi, lors de la configuration de ce produit, vous devez commencer par EOP et travailler sur Defender pour Office 365.

Bien que la configuration de l’authentification de messagerie a lieu dans le DNS public, il est important de configurer cette fonctionnalité pour vous protéger contre l’usurpation d’identité. *Si vous avez EOP, vous* ***devez configurer [l’authentification de messagerie.](email-validation-and-authentication.md)***

Si vous avez un Office 365 E3 ou une version inférieure, vous avez EOP, mais avec la possibilité d’acheter defender autonome pour Office 365 P1 via une mise à niveau. Si vous avez Office 365 E5, vous avez déjà Defender pour Office 365 P2.

> [!TIP]
> Si votre abonnement n’est ni Office 365 E3 ni E5, vous pouvez toujours vérifier si vous avez la possibilité de mettre à niveau vers Microsoft Defender pour Office 365 P1. Si vous êtes intéressé, cette page [web](https://www.microsoft.com/microsoft-365/exchange/advance-threat-protection#coreui-contentrichblock-x07wids) répertorie les abonnements éligibles pour la mise à niveau de Microsoft Defender pour Office 365 P1 (vérifiez la fin de la page pour l’impression fine).

## <a name="the-office-365-security-ladder-from-eop-to-microsoft-defender-for-office-365"></a>La sécurité Office 365 va de EOP à Microsoft Defender pour Office 365

![EOP et Microsoft Defender pour Office 365 et leur accent sur la sécurité, en allant de Protéger et détecter pour examiner et répondre. La configuration de l’authentification de messagerie (au moins DKIM et DMARC) doit être définie pour EOP et en place.](../../media/tp_EOPATPP1P2Take6.gif#lightbox)

> [!IMPORTANT]
> Découvrez les détails sur ces pages : [Exchange Online Protection](exchange-online-protection-overview.md)et Defender pour Office [365.](office-365-atp.md)

Ce qui rend l’ajout de plans Microsoft Defender pour Office 365 un avantage à la gestion pure des menaces EOP peut être difficile à voir à première vue. Pour savoir si un chemin de mise à niveau est le bon pour votre organisation, examinons les fonctionnalités de chaque produit en ce qui concerne :

- prévention et détection des menaces ;
- investigation
- réponse

à partir **d’Exchange Online Protection**:
<p>

|Empêcher/détecter|Examiner|Répondre|
|---|---|---|
|Les technologies sont les suivantes :<ul><li>courrier indésirable</li><li>phish</li><li>programme malveillant</li><li>courrier en bloc</li><li>veille contre l’usurpation d’informations</li><li>détection de l’emprunt d’identité</li><li>Mise en quarantaine de l’administrateur</li><li>Envois d’administrateurs et d’utilisateurs de faux positifs et de faux négatifs</li><li>Autoriser/bloquer les URL et les fichiers</li><li>Rapports</li></u1>|<li>Recherche de journal d’audit</li><li>Suivi des messages</li>|<li>Purge automatique d’heure zéro (ZAP)</li><li>Affinement et test des listes d’autoriser et de bloquer</li>|
|

Si vous souhaitez vous lancer dans EOP, **[repérez cet article.](exchange-online-protection-overview.md)**

Étant donné que ces produits sont cumulatifs, si vous évaluez Microsoft Defender pour Office 365 P1 et décidez de vous y abonner, vous ajouterez ces capacités.

Gains avec **Defender pour Office 365, Plan 1** (à ce jour) :
<p>

|Empêcher/détecter|Examiner|Répondre|
|---|---|---|
|Les technologies incluent tout ce qui se trouve dans EOP plus :<u1><li>Pièces jointes fiables</li><li>Liens fiables<li>Protection Microsoft Defender pour Office 365 pour les charges de travail (par exemple, SharePoint Online, Teams, OneDrive Entreprise)</li><li>Protection au moment du clic dans le courrier électronique, les clients Office et Teams</li><li>anti-hameçonnage dans Defender pour Office 365</li><li>Protection contre l’emprunt d’identité d’utilisateur et de domaine</li><li>Alertes et API d’intégration SIEM pour les alertes</li>|<li>API d’intégration SIEM pour les détections</li><li>**Outil de détection en temps réel**</li><li>Suivi d’URL</li>|<li>Identique</li></u1>

Ainsi, Microsoft Defender pour Office 365 P1 s’étend du côté ***prévention** _ de la maison et ajoute des formulaires supplémentaires de détection __*_**.

Microsoft Defender pour Office 365 P1 ajoute également des **détections** en temps réel pour les enquêtes. Le nom de cet outil de recherche de menaces est en gras, car il est évident de savoir que vous avez Defender pour Office 365 P1.  Il n’apparaît pas dans Defender pour Office 365 P2.

Gains avec **Defender pour Office 365, Plan 2** (à ce jour) :
<p>

|Empêcher/détecter|Examiner|Répondre|
|---|---|---|
|Les technologies incluent tout ce qui se trouve dans EOP et Microsoft Defender pour Office 365 P1 et :<u1><li>Identique</li>|<li>**Threat Explorer**</li><li>Suivi des menaces</li><li>Affichages des campagnes</li>|<li>Examen et réponse automatisés (AIR)</li><li>AIR de l’Explorateur de menaces</li><li>AIR pour les utilisateurs compromis</li><li>API d’intégration SIEM pour les examens automatisés</li>

Ainsi, Microsoft Defender pour Office 365  P2 développe sur le côté examen et réponse de la maison, et ajoute une nouvelle force de chasse. Automation.

Dans Microsoft Defender pour Office 365 P2,  l’outil de repérage principal est appelé Explorateur de menaces plutôt que les détections en temps réel. Si vous voyez l’Explorateur de menaces lorsque vous accédez au Centre de sécurité, vous êtes dans Microsoft Defender pour Office 365 P2.

Pour obtenir les détails de Microsoft Defender pour Office 365 P1 et P2, **[retentez dans cet article.](office-365-atp.md)**

> [!TIP]
> EOP et Microsoft Defender pour Office 365 sont également différents en ce qui concerne les utilisateurs finaux. Dans EOP et Defender pour Office 365 P1, l’accent est mis sur la sensibilisation. Par ailleurs, ces deux services incluent le module de rapport du *message outlook* afin que les utilisateurs peuvent signaler des messages électroniques qu’ils trouvent suspects, pour une analyse plus approfondie. <p> Dans Defender pour Office 365 P2 (qui contient tous les éléments  dans EOP et P1), l’accent est  mis sur une formation supplémentaire pour les utilisateurs finaux, de sorte que le Centre des opérations de sécurité a accès à un puissant outil simulateur de menaces et aux mesures qu’il fournit aux utilisateurs finaux.

## <a name="microsoft-defender-for-office-365-plan-1-vs-plan-2-cheat-sheet"></a>Microsoft Defender pour Office 365 Plan 1 et plan 2 feuille de tri

Cette référence rapide vous aidera à comprendre les fonctionnalités de chaque abonnement Microsoft Defender pour Office 365. Combiné à vos connaissances des fonctionnalités EOP, il peut aider les décideurs d’entreprise à déterminer ce que Microsoft Defender pour Office 365 est le mieux pour leurs besoins.

|Defender pour Office 365 Plan 1|Defender pour Office 365 Plan 2|
|---|---|
|Fonctionnalités de configuration, de protection et de détection : <ul><li>[Pièces jointes fiables](atp-safe-attachments.md)</li><li>[Liens fiables](atp-safe-links.md)</li><li>[Pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams](atp-for-spo-odb-and-teams.md)</li><li>[Protection anti-hameçonnage dans Defender pour Office 365](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)</li><li>[Détections en temps réel](threat-explorer.md)</li></ul>|Fonctionnalités de Defender pour Office 365 Plan 1 <p> --- plus --- <p> Fonctionnalités d’automatisation, d’examen, de correction et de formation : <ul><li>[Suivi des menaces](threat-trackers.md)</li><li>[Threat Explorer](threat-explorer.md)</li><li>[Examen et réponse automatisés](office-365-air.md)</li><li>[Simulateur d’attaques](attack-simulator.md)</li></ul>|
|

- Microsoft Defender pour Office 365 Plan 2 est inclus dans Office 365 E5, Office 365 A5 et Microsoft 365 E5.

- Microsoft Defender pour Office 365 Plan 1 est inclus dans Microsoft 365 Business Premium.

- Microsoft Defender pour Office 365 Plan 1 et Defender pour Office 365 Plan 2 sont disponibles en tant que modules pour certains abonnements. Pour en savoir plus, voici un autre lien disponibilité des fonctionnalités dans [les plans Microsoft Defender pour Office 365.](https://docs.microsoft.com/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans)

- La fonctionnalité [Documents sécurisés](safe-docs.md) est uniquement disponible pour les utilisateurs ayant des licences Microsoft 365 E5 ou Microsoft 365 E5 Sécurité (non inclus dans les offres Microsoft Defender pour Office 365)

- Si votre abonnement actuel n’inclut pas Microsoft Defender pour [](https://go.microsoft.com/fwlink/p/?LinkId=518644)Office 365 et que vous le souhaitez, contactez les commerciaux pour démarrer une version d’essai et découvrez comment Microsoft Defender pour Office 365 peut fonctionner dans votre organisation.

> [!TIP]
> ***Conseil d’initié** _. Vous pouvez utiliser la table docs.microsoft.com des matières pour en savoir plus sur EOP et Microsoft Defender pour Office 365. Revenir à cette page, vue d’ensemble de la sécurité [Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security)et vous remarquerez que la table des matières est présente dans la barre latérale. Il commence par le déploiement (y compris la migration), puis se poursuit dans la prévention, la détection, l’examen et la réponse. <p> Cette structure est divisée de sorte que les rubriques _ *Administration* de la sécurité * soient suivies des **rubriques** Opérations de sécurité. Si vous êtes un nouveau membre de l’un ou l’autre des rôles, utilisez le lien de ce conseil et vos connaissances de la table des matières pour découvrir l’espace. N’oubliez pas *d’utiliser des liens de commentaires* et *d’évaluer les articles* à mesure que vous allez. Les commentaires nous aident à améliorer ce que nous vous proposons.

## <a name="where-to-go-next"></a>Où aller ensuite

Si vous êtes un administrateur de sécurité, vous devrez peut-être configurer DKIM ou DMARC pour votre messagerie. Vous pouvez déployer des prér ments de sécurité stricts pour vos utilisateurs prioritaires ou rechercher les nouveautés du produit. Ou si vous êtes avec les opérations de sécurité, vous pouvez tirer parti des détections en temps réel ou de l’Explorateur de menaces pour examiner et répondre, ou entraîner la détection de l’utilisateur final à l’aide du Simulateur d’attaques. Dans les deux cas, voici quelques recommandations supplémentaires à prendre en charge.

[Authentification de messagerie, y compris SPF, DKIM et DMARC (avec des liens vers la configuration des trois)](email-validation-and-authentication.md)

[Consultez les configurations « de](recommended-settings-for-eop-and-office365-atp.md) base » recommandées spécifiques et utilisez leurs [prérets recommandés pour configurer rapidement des stratégies de sécurité](preset-security-policies.md)

Faire le point [sur les nouveautés de Microsoft Defender pour Office 365 (y](whats-new-in-office-365-atp.md) compris les développements EOP)

[Utiliser l’Explorateur de menaces ou les détections en temps réel](threat-explorer.md)

Utiliser [le Simulateur d’attaques dans Microsoft Defender pour Office 365](attack-simulator.md)
