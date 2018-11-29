---
title: Demandes des personnes associées aux données pour Visual Studio Family concernant le RGPD
description: Demandes des personnes associées aux données pour Visual Studio Family concernant le RGPD
keywords: Visual Studio, Visual Studio Code, Visual Studio pour Mac, documentation Visual Studio, confidentialité, RGPD
localization_priority: Priority
audience: itpro
ms.prod: visual-studio
ms.topic: article
ms.date: 05/24/2018
author: PoulChapman
ms.author: pchapman
manager: scalla
ms.collection: GDPR
ms.workload:
- multiple
ms.openlocfilehash: 09bba28648cbee6dd32c2005bcb584e97a4c534e
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26867162"
---
# <a name="visual-studio-family-data-subject-requests-for-the-gdpr"></a>Demandes des personnes associées aux données pour Visual Studio Family concernant le RGPD

Le [Règlement général sur la protection des données (RGPD)](https://ec.europa.eu/justice/data-protection/reform/index_en.htm) de l’Union européenne permet aux utilisateurs (désignés dans le règlement comme étant les _personnes associées aux données)_ de gérer leurs données personnelles. Les données personnelles sont définies de manière générale dans le cadre du RGPD comme correspondant aux données associées à une personne physique identifiée ou identifiable. Le RGPD octroie aux personnes associées aux données des droits spécifiques sur leurs données personnelles. Ces droits incluent l’obtention de copies des données personnelles, les demandes de corrections de ces dernières, la restriction de leur traitement, leur suppression ou leur réception dans un format électronique. Toute demande formelle effectuée par une personne associée aux données à un contrôleur de données (un employeur ou tout autre type d’agence ou d’organisation qui contrôle les données personnelles) au sujet de la prise de mesure sur ses données personnelles est appelée _demande de personne associée aux données_ ou DSR. Pour obtenir des informations générales relatives au RGPD, consultez la section [RGPD du portail d’approbation de services](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).

## <a name="products-covered-by-this-guide"></a>Produits couverts par ce guide

Ce guide décrit comment utiliser les outils de Microsoft pour exporter ou supprimer des données personnelles collectées pendant l’utilisation de la session authentifiée (connexion) de Visual Studio, de Visual Studio pour Mac et des extensions Microsoft de ces produits, ainsi que de celles de Visual Studio Code. Ce guide explique également comment effectuer des demandes des personnes associées aux données pour des données personnelles collectées lors de l’utilisation de la communauté de développeurs Visual Studio, NuGet.org et le site web ASP.NET. Ces produits peuvent permettre l’utilisation d’outils et d’extensions autres que Microsoft, pour lesquels Microsoft n’agit pas en qualité de responsable du traitement ou contrôleur des données. Les utilisateurs doivent contacter le fournisseur de ces outils et extensions pour comprendre les stratégies relatives à la collecte et aux données personnelles pour les outils et extensions en question.

## <a name="additional-privacy-information"></a>Informations supplémentaires sur la confidentialité

Les termes du contrat de licence du logiciel Microsoft accompagnant les produits, la [déclaration de confidentialité Microsoft](https://go.microsoft.com/fwlink/?LinkId=660726) et [les engagements Microsoft en vertu du RGPD](https://docs.microsoft.com/legal/gdpr) décrivent nos pratiques en matière de traitement des données.

## <a name="visual-studio-visual-studio-for-mac-and-visual-studio-code"></a>Visual Studio, Visual Studio pour Mac et Visual Studio Code

### <a name="personal-data-we-collect"></a>Données personnelles collectées

En qualité de responsable du traitement de données en vertu du RGPD, Microsoft collecte les données nécessaires auprès des utilisateurs pour améliorer Visual Studio, Visual Studio pour Mac, les extensions Microsoft de ces produits, ainsi que celles de Visual Studio Code. Il existe deux catégories de données : les données client et les journaux générés par le système. Les données client incluent des données de diagnostic utilisateur et des données fonctionnelles nécessaires à ces produits pour effectuer le service qu’ils fournissent. Par exemple, pour offrir aux utilisateurs des expériences personnalisées comme des paramètres d’itinérance, nous devons collecter des données de paramètres et d’informations du compte utilisateur. Les journaux générés par le système correspondant aux données d’utilisation ou de diagnostic utilisées pour vous aider à identifier et à résoudre les problèmes et à améliorer nos produits et services. Elles peuvent également contenir des informations d’identification personnelle sur les utilisateurs finals, comme le nom d’utilisateur. Les journaux générés par le système sont conservés pendant 18 mois maximum. Par exemple, les journaux générés par le système sont conservés pour chaque jour d’utilisation du produit et incluent la date d’utilisation, le produit utilisé (par exemple, « Visual Studio 2017 »), l’action que vous avez effectuée (par exemple, « vs/core/packagecostsummary/solutionload ») et la durée de l’action, comme illustrée dans cet exemple :

```
{Time":"2/23/2018 12:00:00 AM","AppName":"Visual Studio 2017","Action":"vs/core/packagecostsummary/solutionload","Target":"1 times",
"DevicePlatform":"Windows 10 Enterprise","IP":null,"InputMethod":null,
"SearchTerm":null,"SearchResult":null}

{Time":"2/23/2018 12:00:00 AM","AppName":"Visual Studio 2017","Action":"vs/ide/connected/accountmanagement/account","Target":"1 times",
"DevicePlatform": "Windows 10 Enterprise","IP":null,"InputMethod":null,
"SearchTerm":null,"SearchResult":null}

{"Time":"2/27/2018 12:00:00 AM","AppName":"Visual Studio 2017","Action":"vs/core/perf/satellitepagefileusage","Target":"23 times",
"DevicePlatform":"Windows 10 Enterprise","IP":null,"InputMethod":null,
"SearchTerm":null,"SearchResult":null}
```

Pour obtenir plus d’informations, consultez l’article relatif aux [journaux générés par le système et collectés par Visual Studio](https://docs.microsoft.com/visualstudio/ide/diagnostic-data-collection).

Seules les données personnelles associées aux identités authentifiées peuvent être traitées par une DSR. Par conséquent, étant donné que Visual Studio Code ne permet pas de s’identifier, les journaux générés par le système à partir de ce produit ne sont pas associés à une identité authentifiée et ne peuvent pas être pris en charge. Toutefois, certaines extensions Microsoft de Visual Studio Code peuvent fournir des données authentifiées, qui peuvent être traitées par une DSR. Pour obtenir plus d’informations, consultez [RGPD et Visual Studio Code](https://code.visualstudio.com/docs/supporting/faq#_gdpr-and-vs-code). En règle générale, nous ne stockons pas de données pour Visual Studio 2013 et les versions antérieures. Cependant, certaines extensions et certains composants peuvent fournir des données associées à des identités authentifiées pouvant être traitées par une DSR, comme indiqué ci-dessous.

### <a name="how-users-can-control-personal-data"></a>Contrôle des utilisateurs sur leurs données personnelles

Visual Studio 2015 et les versions ultérieures, Visual Studio pour Mac et Visual Studio Code permettent à vos utilisateurs d’arrêter la collecte de données, et vous permettent, en qualité de contrôleur, d’exporter ou de supprimer des données qui ont déjà été collectées.

#### <a name="in-app-settings"></a>Paramètres intégrés à l’application

Les utilisateurs peuvent contrôler les paramètres de confidentialité pour ces produits. Pour obtenir plus d’informations, consultez les articles suivants :

- [Gérer les paramètres de confidentialité dans Visual Studio](https://docs.microsoft.com/visualstudio/ide/visual-studio-experience-improvement-program)
- [Gérer les paramètres de confidentialité dans Visual Studio pour Mac](https://docs.microsoft.com/visualstudio/mac/visual-studio-experience-improvement-program)
- [Désactiver la création de rapports de télémétrie dans Visual Studio Code](https://code.visualstudio.com/docs/supporting/faq#_how-to-disable-telemetry-reporting)

#### <a name="exporting-or-deleting-data"></a>Exportation ou suppression des données

Les contrôleurs peuvent gérer les données client et les journaux générés par le système collectés auprès des personnes associées aux données de deux méthodes distinctes, selon la façon dont le produit Visual Studio Family ou les extensions Microsoft ont été enregistrés. Dans certains cas, les deux méthodes doivent être utilisées. Les deux méthodes permettent aux contrôleurs de télécharger une copie de l’historique de leurs activités gérées par cette méthode. La fermeture d’un compte AAD ou de service Microsoft entraîne la suppression des données client Visual Studio connexes, et l’anonymisation des données d’identification personnelle contenues dans les journaux générés par le système se rapportant à ces produits. Les journaux générés par le système rendus anonymes sont conservés pendant 18 mois maximum.

- Les utilisateurs ayant enregistré un produit Visual Studio Family à l’aide d’un compte lié à un client Azure, par exemple, un compte AAD ou un compte de service Microsoft associé à un abonnement Azure, peuvent suivre les instructions indiquées dans [Demandes des personnes associées aux données pour Azure concernant le RGPD](gdpr-dsr-azure.md).
- Les utilisateurs ayant enregistré un produit Visual Studio Family sans utiliser de compte lié à un client Azure, par exemple de nombreux comptes à l’aide d’un compte de service Microsoft (MSA), peuvent utiliser le [Centre de réponse de confidentialité Microsoft basé sur le web](https://aka.ms/userprivacysite) disponible via leur compte Microsoft afin d’afficher, de contrôler et de supprimer des données d’activité liées à leur compte Microsoft sur plusieurs services Microsoft. Dans ce scénario, l’utilisateur agit en qualité de contrôleur de ses données personnelles.

> [!NOTE]
> Quand le titulaire d’un compte de service Microsoft supprime son compte, toutes ses données d’identification personnelle se rapportant à ces produits sont supprimées, peu importe si le compte est lié à un client Azure ou non, et les journaux générés par le système sont rendus anonymes.

Pour Visual Studio 2013, les données que nous recueillons sont rendues anonymes. Pour Visual Studio 2012 et les versions antérieures, nous supprimons immédiatement les données dès leur réception. Dans les deux cas, il n’y a rien à afficher, à exporter ou à supprimer ultérieurement.

## <a name="visual-studio-developer-community"></a>Communauté de développeurs Visual Studio

Nous prenons en charge les demandes concernant le [Règlement général sur la protection des données (RGPD)](https://ec.europa.eu/justice/data-protection/reform/index_en.htm) par l’intermédiaire du site web [Communauté des développeurs](https://developercommunity.visualstudio.com). Vous pouvez afficher, exporter ou supprimer vos données de commentaires.

### <a name="personal-data-we-collect"></a>Données personnelles collectées

Microsoft collecte des données pour nous aider à reproduire et à résoudre les problèmes que vous signalez au sujet des produits Visual Studio Family. Ces données incluent des données personnelles et des commentaires publics. Les données personnelles incluent :

- les informations de votre profil [Communauté des développeurs](https://developercommunity.visualstudio.com) ;
- les préférences et les notifications ;
- les pièces jointes et les journaux générés par le système fournis lorsque vous avez [signalé un problème dans Visual Studio](https://docs.microsoft.com/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017) ou par l’intermédiaire de [Communauté des développeurs](https://developercommunity.visualstudio.com) ;
- vos votes.

Les commentaires publics incluent les problèmes signalés, les commentaires et les solutions.

### <a name="how-users-can-control-personal-data"></a>Contrôle des utilisateurs sur leurs données personnelles

#### <a name="view"></a>Vue

Pour afficher les données liées à vos commentaires, procédez comme suit :

1. Connectez-vous à [Communauté des développeurs](https://developercommunity.visualstudio.com). Dans le coin supérieur droit, cliquez sur votre profil, puis sélectionnez **Profil et préférences**.
2. Cliquez sur les onglets **Profil**, **Notifications**, **Activité** et **Pièces jointes** pour afficher les données envoyées aux systèmes de commentaires.
   1. **Profil** fait référence à votre profil [Communauté des développeurs](https://developercommunity.visualstudio.com), notamment le nom d’utilisateur, l’adresse e-mail, les informations générales, etc.
   2. **Notifications** vous permet de contrôler les notifications électroniques que vous recevez.
   3. **Activité** vous fournit les éléments de commentaires que vous avez utilisés (publiés, commentés, etc.) et les activités effectuées.
   4. **Pièces jointes** est une liste de l’historique de vos pièces jointes dans un format comme `FileName was attached to the problem "ProblemName" Tue, Apr 10, 18 2:27 PM`.

#### <a name="export"></a>Exporter

Vous pouvez exporter vos données de commentaires dans le cadre de la DSR. Nous allons créer une ou plusieurs archives .zip qui incluent :

- les informations de votre profil [Communauté des développeurs](https://developercommunity.visualstudio.com) ;
- les préférences et les paramètres de notification ;
- les pièces jointes fournies lorsque vous avez [signalé un problème dans Visual Studio](https://docs.microsoft.com/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017) ou par l’intermédiaire de [Communauté des développeurs](https://developercommunity.visualstudio.com).

> [!NOTE]
> Nous excluons les commentaires publics suivants fournis à partir de vos archives : commentaires, solutions et problèmes signalés.

Pour commencer une exportation, procédez comme suit :

1. Connectez-vous à [Communauté des développeurs](https://developercommunity.visualstudio.com). Dans le coin supérieur droit, cliquez sur votre profil, puis sélectionnez **Profil et préférences**.
2. Cliquez sur l’onglet **Confidentialité**, puis cliquez sur **Créer une archive** pour demander l’exportation de vos données.
3. **État d’archivage** est actualisé pour montrer que nous préparons les données. Le délai avant que les données soient disponibles dépend de la quantité de données à exporter.
4. Une fois que les données sont prêtes, nous vous envoyons un e-mail.
5. Cliquez sur **Télécharger l’archive** dans l’e-mail, ou revenez à l’onglet Confidentialité pour télécharger vos données.

> [!NOTE]
> - Nous n’envoyons pas d’e-mail si vous choisissez de ne pas recevoir de notifications dans l’onglet Notifications.
> - Si vous demandez une nouvelle exportation, nous supprimons les anciennes archives et nous en créons de nouvelles.

#### <a name="delete"></a>Supprimer

L’action de suppression permet d’éliminer de [Communauté de développeurs](https://developercommunity.visualstudio.com) les informations suivantes à votre sujet :

- Informations de profil
- Préférences et paramètres de notification
- Pièces jointes fournies lorsque vous avez [signalé un problème dans Visual Studio](https://docs.microsoft.com/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017) ou par l’intermédiaire de [Communauté des développeurs](https://developercommunity.visualstudio.com)
- Vos votes

> [!NOTE]
> Nous ne supprimons pas les informations publiques suivantes, mais les rendons anonymes : vos commentaires, vos solutions, les problèmes que vous avez signalés.
>
> [!IMPORTANT]
> La suppression d’un compte AAD ou de service Microsoft déclenche le processus de suppression de [Communauté des développeurs](https://developercommunity.visualstudio.com).

Pour lancer une suppression, procédez comme suit :

1. Connectez-vous à [Communauté des développeurs](https://developercommunity.visualstudio.com). Dans le coin supérieur droit, cliquez sur votre profil, puis sélectionnez **Profil et préférences**.
2. Cliquez sur l’onglet **Confidentialité**, puis cliquez sur **Supprimer vos données et votre compte** pour lancer la suppression de vos données.
3. Un écran de confirmation s’affiche.
4. Saisissez « supprimer » dans la zone, puis cliquez sur **Supprimer mon compte**.

Lorsque vous cliquez sur **Supprimer mon compte** :

- Vous êtes déconnecté.
- Nous supprimons votre compte [Communauté des développeurs](https://developercommunity.visualstudio.com), vos données personnelles et les pièces jointes.
- Nous rendons anonymes vos commentaires publics. Vos commentaires publics restent disponibles sur Communauté des développeurs et sont indiqués comme provenant d’un utilisateur anonyme.
- Nous ne vous envoyons pas d’e-mail après avoir supprimé votre compte, car vous n’appartenez plus au système.
- Si vous signalez un nouveau problème ou si vous vous connectez à [Communauté des développeurs](https://developercommunity.visualstudio.com), vous êtes identifié comme un nouvel utilisateur.
- Si vous supprimez votre compte à partir de [Communauté des développeurs](https://developercommunity.visualstudio.com), nous ne le supprimons pas d’autres services Microsoft.

## <a name="xamarin-forums-and-bugzilla"></a>Xamarin Forums et Bugzilla

### <a name="personal-data-we-collect"></a>Données personnelles collectées

Par l’intermédiaire de la communauté des utilisateurs [Xamarin Forums](https://forums.xamarin.com) et des sites web de création de rapport de bogues [Xamarin Bugzilla](https://bugzilla.xamarin.com/), Microsoft collecte les données que vous fournissez pour nous aider à reproduire et à résoudre les problèmes que vous rencontrez avec les produits et les services Microsoft. Ces données incluent des données personnelles et des commentaires publics. Les données personnelles collectées sont les données de compte d’utilisateur (par exemple, les noms d’utilisateur et les adresses e-mail associés à vos comptes Forums Xamarin ou Bugzilla), et les commentaires publics collectés incluent les bogues, les problèmes, les commentaires et les solutions que vous fournissez via la communauté Forums Xamarin ou le site web de création de rapport de bogues Xamarin Bugzilla.

### <a name="how-you-can-control-your-data"></a>Contrôler vos données

#### <a name="xamarin-forums"></a>Xamarin Forums

##### <a name="view"></a>Vue

Les utilisateurs disposant de comptes Xamarin Forums actifs peuvent afficher leurs données personnelles et commentaires publics (par exemple, tous leurs threads et billets publiés) à partir de leur compte Xamarin Forums. Les utilisateurs peuvent également modifier leurs données personnelles via leur compte.

##### <a name="export"></a>Exporter

La communauté Xamarin Forums est hébergée par un tiers, Vanilla Forums. Pour demander l’exportation de vos données publiques, les utilisateurs doivent contacter forums@xamarin.com (géré par l’équipe Xamarin). Ensuite, nous communiquerons directement avec Vanilla Forums pour traiter cette demande.

##### <a name="delete"></a>Delete

La communauté Xamarin Forums est hébergée par un tiers, Vanilla Forums. Pour demander la suppression des données personnelles et publiques, les utilisateurs doivent contacter forums@xamarin.com (géré par l’équipe Xamarin). Ensuite, nous traitons manuellement la demande de suppression des données personnelles de l’utilisateur.

#### <a name="bugzilla-for-xamarin"></a>Bugzilla pour Xamarin

##### <a name="view"></a>Vue

Les utilisateurs disposant de comptes Xamarin Bugzilla actifs peuvent afficher tous les bogues qu’ils ont signalés et tous les commentaires qu’ils ont ajoutés sur les bogues en cliquant sur les liens appropriés sur la page d’accueil Xamarin Bugzilla.

##### <a name="export"></a>Exporter

L’exportation des données personnelles n’est pas prise en charge.

##### <a name="delete"></a>Supprimer

Pour demander la suppression des données personnelles utilisées avec le site web de création de rapports Bugzilla de Xamarin, les utilisateurs peuvent fermer leur compte Xamarin Bugzilla en accédant à la [page Préférences des utilisateurs](https://bugzilla.xamarin.com/userprefs.cgi), puis en choisissant l’**onglet Fermer le compte**. Saisissez votre mot de passe Bugzilla et cochez la case indiquant que vous comprenez que cette action permet de supprimer définitivement votre compte.Les commentaires publics (par exemple, les bogues, les problèmes, les commentaires et les solutions) que les utilisateurs ont publiés sur le site Xamarin Bugzilla ne sont pas supprimés à la réception d’une demande de suppression. À la place, les commentaires publics sont rendus anonymes en supprimant l’adresse e-mail et le nom associé aux commentaires publics créés par l’utilisateur ayant envoyé la demande de suppression.

## <a name="nuget"></a>NuGet

Pour obtenir plus d’informations relatives aux DSR pour NuGet.org, consultez l’article [Demandes de données utilisateur NuGet](https://docs.microsoft.com/nuget/policies/data-requests).

## <a name="aspnet"></a>ASP.NET

Pour obtenir plus d’informations relatives aux DSR pour le site web ASP.NET, consultez l’article relatif au [traitement des demandes de personnes associées aux données pour le RGPD et le site web ASP.NET](https://www.asp.net/gdpr).

## <a name="iisnet"></a>IIS.NET

Pour obtenir plus d’informations relatives aux DSR pour le site web IIS.NET, consultez l’article relatif au [traitement des demandes de personnes associées aux données pour le RGPD et le site web IIS.NET](https://www.iis.net/gdpr).

## <a name="other-visual-studio-family-services"></a>Autres services Visual Studio Family

### <a name="surveymonkey"></a>SurveyMonkey

De temps à autre, nous invitons des clients à fournir des commentaires sur ces produits par l’intermédiaire de SurveyMonkey. Ces données sont supprimées dans un délai de 28 jours. Lors du traitement des demandes des personnes associées aux données pour ces produits, si nous avons des réponses de sondage authentifiées, nous les incluons dans l’exportation et la suppression desdites demandes.

### <a name="uservoice"></a>UserVoice

Nous invitons les clients à formuler des suggestions de produit sur les sites UserVoice.com pour ces produits. Ces sites sont gérés indépendamment par UserVoice, et les demandes des personnes associées aux données sont gérées par UserVoice.

- [https://visualstudio.uservoice.com/](https://visualstudio.uservoice.com/)
- [https://aspnet.uservoice.com/](https://aspnet.uservoice.com/)
- [https://xamarin.uservoice.com/](https://xamarin.uservoice.com/)

En ce qui concerne les demandes des personnes concernées relatives à ces données, consultez les instructions d’UserVoice sur [Exporter vos données](https://feedback.uservoice.com/knowledgebase/articles/1850245-export-my-personal-data) ou sur [Supprimer vos données](https://feedback.uservoice.com/knowledgebase/articles/1848856-delete-my-profile-information).

## <a name="learn-more"></a>En savoir plus

- [Engagements du RGDP pris par Microsoft envers les clients de nos produits logiciels d’entreprise généralement disponibles](https://docs.microsoft.com/legal/gdpr)
- [Centre de gestion de la confidentialité Microsoft](https://www.microsoft.com/TrustCenter/Privacy/gdpr/default.aspx)
- [Portail d’approbation de service](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted)
- [Tableau de bord de confidentialité Microsoft](https://account.microsoft.com/privacy)
- [Centre de réponse de confidentialité Microsoft](https://aka.ms/userprivacysite)
- [Demandes des personnes associées aux données pour Azure concernant le RGPD](gdpr-dsr-azure.md)
