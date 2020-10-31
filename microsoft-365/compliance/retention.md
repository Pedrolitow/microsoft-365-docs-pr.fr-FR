---
title: En savoir plus sur les stratégies & les étiquettes de rétention pour conserver ou supprimer automatiquement du contenu
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Priority
ms.collection:
- M365-security-compliance
- SPO_Content
- m365solution-mig
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: En savoir plus sur les stratégies de rétention et les étiquettes de rétention, qui permettent de conserver les éléments dont vous avez besoin et de supprimer ceux qui ne vous servent pas.
ms.openlocfilehash: 50bbe9d80b7b0a1b9fa346fd6e5abc8971dadcfb
ms.sourcegitcommit: d578b28ed1886abd083b01b93f01b354067e6d47
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "48804757"
---
# <a name="learn-about-retention-policies-and-retention-labels"></a>En savoir plus sur les stratégies et les étiquettes de rétention

>*[Guide de sécurité et conformité pour les licences Microsoft 365](https://aka.ms/ComplianceSD).*

Le volume et la complexité des données e-mails, documents, messages instantanés et autres de la majorité des organisations augmentent quotidiennement. Il est important de gérer et de gouverner efficacement ces informations, car vous devez :
  
- **respecter de façon proactive les réglementations du secteur et les stratégies internes** qui vous obligent à conserver du contenu pendant une période minimale. Par exemple, la loi Sarbanes-Oxley vous oblige à conserver certains types de contenu pendant sept ans. 

- **réduire les risques en cas de litige ou de violation de la sécurité** en supprimant définitivement le contenu ancien qu’il n’est plus obligatoire de conserver ; 
    
- **aider votre organisation à partager efficacement les connaissances et à être plus agile** en vérifiant que vos utilisateurs traitent uniquement le contenu actuel et pertinent pour eux. 
    
La configuration des paramètres de rétention peut vous aider à atteindre tous ces objectifs. La gestion du contenu nécessite généralement deux actions :
  
- **Conservation** du contenu afin que celui-ci ne puisse pas être supprimé définitivement avant la fin de la période de rétention. 
    
- **Suppression** définitive du contenu à la fin de la période de rétention. 
    

Avec ces deux actions de rétention, vous pouvez configurer les paramètres de rétention pour les résultats suivants :

- Conservation uniquement : conserver le contenu définitivement ou pour une période spécifiée.
- Suppression uniquement : supprimez le contenu après une période spécifiée.
- Conservation puis suppression : conserver le contenu pendant une période spécifiée, puis le supprimer.

Ces paramètres de rétention fonctionnent avec du contenu en place, ce qui vous permet d’éviter les charges liées à la création et à la configuration d’un espace de stockage supplémentaire pour conserver du contenu pour des raisons de conformité. Vous n’avez plus besoin non plus d’implémenter des processus personnalisés pour copier et synchroniser ces données.

## <a name="how-retention-settings-work-with-content-in-place"></a>Fonctionnement des paramètres de rétention avec le contenu en place

Si des paramètres de rétention sont affectés au contenu, celui-ci reste à son emplacement d’origine. Les utilisateurs peuvent continuer à travailler avec leurs documents ou la messagerie comme si rien n’avait changé. Toutefois, s’ils modifient ou suppriment le contenu qui est inclus dans la stratégie de rétention, une copie du contenu est automatiquement conservée, tel qu’il était lorsque vous avez appliqué les paramètres de rétention.
  
- Pour les sites SharePoint et OneDrive : la copie est conservée dans la bibliothèque de **Conservation et préservation** .

- Pour les boîtes aux lettres Exchange : la copie est conservée dans le dossier **Éléments récupérables** . 

- Pour les messages Teams et Yammer : la copie est conservée dans un dossier masqué appelé **SubstrateHolds** sous la forme d’un sous-dossier dans le dossier **Éléments récupérables** de Exchange.

> [!NOTE]
> La bibliothèque de Conservation et préservation utilise un espace de stockage qui n’est pas exempté du quota de stockage d’un site. Il se peut que vous deviez augmenter votre espace de stockage lorsque vous utilisez des paramètres de rétention pour SharePoint et les groupes Microsoft 365.
> 
Ces emplacements sécurisés et le contenu conservé ne sont pas visibles pour la plupart des utilisateurs. Dans la plupart des cas, les personnes n’ont même pas besoin de savoir que leur contenu est soumis aux paramètres de rétention.

Pour plus d’informations sur le fonctionnement des paramètres de rétention en fonction des différentes charges de travail, consultez les articles suivants :

- [En savoir plus sur la rétention dans SharePoint et OneDrive](retention-policies-sharepoint.md)
- [En savoir plus sur la rétention dans Microsoft Teams](retention-policies-teams.md)
- [Découvrir la rétention pour Yammer](retention-policies-yammer.md)
- [Découvrir la rétention pour Exchange](retention-policies-exchange.md)

## <a name="retention-policies-and-retention-labels"></a>Stratégies de rétention et étiquettes de rétention.

Vous pouvez utiliser les stratégies de rétention et les étiquettes de rétention pour affecter vos paramètres de rétention au contenu. 

Utilisez une stratégie de rétention pour attribuer les mêmes paramètres de rétention au contenu au niveau d’un site ou d’une boîte aux lettres, et utiliser une étiquette de rétention pour affecter des paramètres de rétention à l’échelle d’un élément (dossier, document, courrier électronique).

Par exemple, si tous les documents d’un site SharePoint doivent être conservés pendant cinq ans, il est plus efficace de le faire avec une stratégie de rétention que d’appliquer la même étiquette de rétention à tous les documents de ce site. Toutefois, si certains documents de ce site doivent être conservés pendant cinq ans et d’autres pendant dix ans, une stratégie de rétention ne fonctionnera pas. Lorsque vous devez spécifier les paramètres de rétention au niveau de l’élément, utilisez les étiquettes de rétention. 

Contrairement aux stratégies de rétention, les paramètres de rétention des étiquettes de rétention sont conservées avec le contenu s’il est copié ou déplacé vers un autre emplacement Microsoft 365. De plus, les étiquettes de rétention présentent les fonctionnalités suivantes, non prises en charge par les stratégies de rétention : 
 
- Options de démarrage de la période de rétention à partir de la date d’étiquetage du contenu ou en fonction d’un événement, en plus de l’âge du contenu ou du moment de la dernière modification de celui-ci.

- Utilisez [classifieurs entraînables](classifier-learn-about.md) pour identifier le contenu à étiqueter.

- Appliquez une étiquette par défaut pour les documents SharePoint.

- Utilisez [révision avant destruction](disposition-reviews.md) pour réviser le contenu avant sa suppression définitive.

- Marquez le contenu en tant qu’[enregistrement ](records-management.md#records) au niveau des paramètres d’étiquette, et conservez toujours une  [preuve de destruction](disposition.md#disposition-of-records) lorsque le contenu est supprimé à la fin de sa période de rétention.

### <a name="retention-policies"></a>Stratégies de rétention

Les stratégies de rétention peuvent être appliquées aux emplacements suivants :
- Messagerie électronique Exchange
- Site SharePoint
- Comptes OneDrive
- Groupes Microsoft 365
- Skype Entreprise
- Dossiers publics Exchange
- Messages du canal Teams
- Conversations Teams
- Messages communautaires Yammer
- Messages privés Yammer

L’application d’une stratégie unique à plusieurs emplacements, ou à des emplacements ou des utilisateurs spécifiques, est d’une grande efficacité.
    
Vous pouvez également appliquer une stratégie à tout le contenu ou à du contenu qui remplit des conditions spécifiques, comme le contenu comportant des mots clés particuliers ou [des types d’informations sensibles](sensitive-information-type-entity-definitions.md).

#### <a name="use-preservation-lock-to-comply-with-regulatory-requirements"></a>Utiliser le verrouillage de conservation pour se conformer aux exigences réglementaires.

Certaines organisations doivent peut-être respecter des règles définies par des organismes de réglementation, comme la règle 17a-4 de la SEC (Securities and Exchange Commission), stipulant qu'après l’activation d’une stratégie de rétention, celle-ci ne peut pas être désactivée ni rendue moins restrictive. 

Le verrouillage de conservation permet à votre organisation de répondre à ces exigences réglementaires, car il verrouille une stratégie de rétention pour que personne, y compris l’administrateur, ne puisse désactiver la stratégie, la supprimer ou la rendre moins restrictive.
  
Lorsqu’une stratégie de rétention est verrouillée :

- Personne ne peut la désactiver
- Vous pouvez ajouter des emplacements, mais pas les supprimer
- Le contenu soumis à la stratégie ne peut pas être modifié ou supprimé pendant la période de rétention
- Vous pouvez prolonger une période de rétention, mais pas la réduire

En bref, une stratégie de rétention verrouillée peut être accrue ou étendue, mais pas réduite ni désactivée.
  
> [!IMPORTANT]
> Avant de verrouiller une stratégie de rétention, il est essentiel de comprendre l’impact et de confirmer qu’il est exigé que votre organisation respecte des exigences réglementaires. Les administrateurs ne peuvent plus désactiver ou supprimer une stratégie de rétention une fois le verrouillage de conservation appliqué.

Vous pouvez appliquer un verrouillage de conservation une fois la stratégie de rétention créée à l’aide de PowerShell. Des instructions sont incluses dans [Créer et configurer des stratégies de rétention](create-retention-policies.md).

#### <a name="releasing-a-retention-policy"></a>Publication d’une stratégie de rétention

La fourniture de votre stratégie de rétention n’offrant pas de verrouillage de conservation, vous pouvez désactiver ou supprimer une stratégie de rétention à tout moment. 

Lorsque vous procédez de la sorte, le contenu SharePoint ou OneDrive conservé dans la bibliothèque de conservation n’est pas immédiatement supprimé définitivement. Au lieu de cela, pour éviter la perte accidentelle de données, il existe une période de grâce de 30 jours pendant laquelle l’expiration du contenu de cette stratégie ne se produit pas dans la bibliothèque de conservation de conservation, afin que vous puissiez restaurer tout contenu à partir de cet emplacement, le cas échéant. De plus, vous ne pouvez pas supprimer manuellement ce contenu au cours de la période de grâce.

Vous pouvez réactiver la stratégie de rétention pendant la période de grâce et aucun contenu ne sera supprimé pour cette stratégie.

Cette période de grâce de 30 jours dans SharePoint et OneDrive correspond à un délai de 30 jours dans Exchange. Pour des informations supplémentaires, consultez [Gestion des boîtes aux lettres avec période de grâce](identify-a-hold-on-an-exchange-online-mailbox.md#managing-mailboxes-on-delay-hold).

### <a name="retention-labels"></a>Étiquettes de rétention

Utilisez les étiquettes de rétention pour les différents types de contenus nécessitant différents paramètres de rétention. Par exemple :
  
- Formulaires fiscaux qui doivent être conservés pendant une période minimale de temps. 
    
- Documents de presse qui doivent être définitivement supprimés après une date déterminée. 
    
- Recherche concurrentielle qui doit être conservée pour une période spécifique, puis définitivement supprimée. 
    
- Permis de travail qui doivent être enregistrés afin de ne pas être modifiés ou supprimés. 
    
Dans tous ces cas, les étiquettes de rétention vous permettent d’appliquer des paramètres de rétention au niveau de l’élément (document ou courrier électronique).
  
Avec les étiquettes de rétention, vous pouvez effectuer les actions suivantes :
  
- **Permettre aux personnel de votre organisation d’appliquer une étiquette de rétention manuellement** à du contenu dans Outlook, Outlook sur le web, OneDrive, SharePoint et des groupes Microsoft 365. Les utilisateurs savent souvent mieux quel type de contenu ils utilisent, ils peuvent donc le classer et appliquer les paramètres de rétention appropriés. 
    
- **Appliquer automatiquement des étiquettes de rétention au contenu** s’il répond à des conditions spécifiques, comme lorsque le contenu contient : 
    - des types spécifiques d’informations sensibles.
    - des mots clés spécifiques correspondant à une requête que vous créez.
    - Le modèle correspond à un classifieur entraînable.

- **Démarrer la période de rétention à compter de la date d’étiquetage du contenu** pour les documents des sites SharePoint et les comptes OneDrive, ainsi que pour les éléments de courrier à l’exception des éléments de calendrier. Si vous appliquez une étiquette de rétention avec cette configuration à un élément de calendrier, la période de rétention commence à partir de la date d’envoi.

- **Démarrer la période de rétention à la date d’un événement** par exemple, employés quittant l’organisation ou expiration du contrat.

- **Appliquer une étiquette de rétention par défaut à une bibliothèque de documents, un dossier ou un ensemble de documents** dans SharePoint, afin que tous les documents stockés dans cette bibliothèque obtiennent l’étiquette de rétention par défaut.

De plus, les étiquettes de rétention prennent en charge la [gestion des enregistrements](records-management.md) pour les e-mails et les documents dans les applications et les services Microsoft 365. Vous pouvez utiliser une étiquette de rétention pour marquer des éléments comme enregistrement. Lorsque cela se produit et que le contenu reste dans Microsoft 365, l’étiquette place des restrictions supplémentaires sur le contenu qui peuvent être nécessaires pour des raisons réglementaires. Pour obtenir plus d’informations, consultez [Comparer des restrictions relatives aux actions autorisées ou bloquées](records-management.md#compare-restrictions-for-what-actions-are-allowed-or-blocked).

Les étiquettes de rétention, contrairement [aux étiquettes de confidentialité ](sensitivity-labels.md), ne sont pas conservées si le contenu est déplacé en dehors de Microsoft 365.

Il n’y a pas de limite au nombre d’étiquettes de rétention qui sont prises en charge pour un client. Toutefois, le nombre maximal de stratégies prises en charge pour un client est de 10 000, et cela inclut les stratégies qui appliquent les étiquettes (stratégies d’étiquette de rétention et stratégies de rétention qui s’appliquent automatiquement), ainsi que les stratégies de rétention.

#### <a name="classifying-content-without-applying-any-actions"></a>Classification de contenu sans application d’action

Bien que l’objectif principal des étiquettes de rétention soit la conservation ou la suppression de contenu, vous pouvez également les utiliser sans activer de rétention ni d’autres actions. Dans ce cas, vous pouvez utiliser une étiquette de rétention comme une simple étiquette de texte, sans appliquer la moindre action.
  
Par exemple, vous pouvez créer et appliquer une étiquette de rétention appelée « À vérifier », qui ne déclenche aucune action, puis utiliser cette étiquette pour retrouver plus tard le contenu étiqueté.
  
![Paramètres d’étiquettes pour classer uniquement](../media/retention-label-retentionoff.png)

#### <a name="using-a-retention-label-as-a-condition-in-a-dlp-policy"></a>Utilisation d’une étiquette de rétention comme condition dans une stratégie DLP

Vous pouvez spécifier une étiquette de rétention comme condition dans une stratégie de protection contre la perte de données (DLP) pour les documents dans SharePoint. Par exemple, vous pouvez configurer une stratégie DLP pour empêcher le partage de documents hors de l’organisation si une étiquette de rétention spécifique leur est appliquée.

Pour plus d’informations, consultez [Utilisation d’une étiquette de rétention comme condition dans une stratégie DLP](data-loss-prevention-policies.md#using-a-retention-label-as-a-condition-in-a-dlp-policy).

#### <a name="retention-labels-and-policies-that-apply-them"></a>Étiquettes de rétention et stratégies qui les appliquent

Les étiquettes de rétention sont des blocs de construction indépendants et réutilisables. L’objectif principal d’une stratégie de rétention d’étiquette est de regrouper un ensemble d’étiquettes de rétention et de spécifier les emplacements où vous souhaitez voir apparaître ces étiquettes. Les administrateurs et les utilisateurs peuvent ensuite appliquer ces étiquettes au contenu de ces emplacements.
  
![Diagramme des étiquettes, des stratégies d’étiquette et des emplacements](../media/eee42516-adf0-4664-b5ab-76727a9a3511.png)
  
Lorsque vous publiez des étiquettes de rétention, celles-ci sont incluses dans une stratégie d’étiquette de rétention qui les rend disponibles pour les administrateurs et les utilisateurs à sélectionner :

- Une étiquette de conservation peut être incluse dans de nombreuses stratégies d’étiquette de rétention.

- Les stratégies d’étiquette de rétention définissent les emplacements où publier les étiquettes de rétention.

- Un seul emplacement peut être inclus dans de nombreuses stratégies d’étiquette de rétention.

Outre les stratégies d’étiquette de rétention, vous pouvez également créer une ou plusieurs stratégies à application automatique, chacune avec une seule étiquette de rétention. Avec cette stratégie, une étiquette de rétention est appliquée automatiquement lorsque les conditions que vous spécifiez dans la stratégie sont réunies. 

#### <a name="retention-label-policies-and-locations"></a>Stratégies d’étiquette de rétention et emplacements

Différents types d’étiquettes de rétention peuvent être publiés dans différents emplacements, en fonction du descriptif de l’étiquette de rétention.
  
| Si l’étiquette de rétention est... | La stratégie d’étiquette peut être appliquée à... |
|:-----|:-----|
|Publiée pour les administrateurs et les utilisateurs finaux  <br/> |Exchange, SharePoint, OneDrive et Groupes Microsoft 365  <br/> |
|Appliquée automatiquement en fonction des types d’informations sensibles ou des classifieurs entraînables  <br/> |Exchange (toutes les boîtes aux lettres uniquement), SharePoint, OneDrive  <br/> |
|Appliquée automatiquement en fonction d’une requête  <br/> |Exchange, SharePoint, OneDrive et Groupes Microsoft 365  <br/> |
   
Dans Exchange, les étiquettes de rétention à application automatique sont appliquées uniquement aux nouveaux messages envoyés (données en transit) et pas à tous les éléments présents dans la boîte aux lettres (données au repos). Par ailleurs, les étiquettes de rétention à application automatique pour les types d’informations sensibles et les classifieurs entraînables s’appliquent à toutes les boîtes aux lettres. Vous ne pouvez pas sélectionner de boîtes aux lettres spécifiques.
  
Les dossiers publics Exchange, les messages Skype, Teams et Yammer ne prennent pas en charge les étiquettes de rétention. Pour conserver et supprimer du contenu stocké sur ces emplacements, utilisez plutôt les stratégies de rétention.

#### <a name="only-one-retention-label-at-a-time"></a>Une seule étiquette de rétention à la fois

Il n’est possible d’attribuer qu’une seule étiquette de rétention à un courrier électronique ou à un document :
  
- En ce qui concerne les étiquettes de rétention affectées manuellement par les administrateurs ou les utilisateurs finals, ceux-ci peuvent supprimer ou modifier l’étiquette de rétention affectée.
    
- Si une étiquette à application automatique est attribuée à un contenu, elle peut être remplacée par une étiquette de rétention publiée.
    
- Si une étiquette de rétention publiée est attribuée à un contenu, elle ne peut pas être remplacée par une étiquette à application automatique.
    
- S’il existe plusieurs règles qui affectent une étiquette à appliquer automatiquement et que le contenu remplit les critères de plusieurs règles, l’étiquette de rétention de la règle la plus ancienne (par date de création) est affectée.
    
Pour comprendre comment et pourquoi une étiquette de rétention est appliquée plutôt qu’une autre, il est important de comprendre la différence entre l’attribution explicite et l’attribution implicite d’une étiquette :

- Les étiquettes de rétention appliquées à partir d’une stratégie d’étiquette sont attribuées de manière explicite
- Les étiquettes de rétention appliquées automatiquement à partir d’une stratégie d’application automatique sont attribuées implicitement

Une étiquette de rétention attribuée de manière explicite prévaut sur une étiquette de rétention attribuée de manière implicite. Si vous souhaitez en savoir plus, consultez la section de cette page nommée [Principes de rétention et priorité](retention.md#the-principles-of-retention-or-what-takes-precedence).

Pour SharePoint, vous pouvez également attribuer implicitement des étiquettes de rétention lorsque vous configurez une étiquette par défaut pour tout le contenu d’une bibliothèque, d’un dossier ou d’un ensemble de documents SharePoint. Dans ce scénario, les étiquettes appliquées automatiquement sont prioritaires par rapport aux étiquettes par défaut. Cependant, si vous souhaitez en savoir plus sur tous les résultats de l’utilisation d’une étiquette par défaut, veuillez consulter la section [Application d’une étiquette de rétention par défaut à tout le contenu dans une bibliothèque, un dossier ou un ensemble de documents SharePoint](create-apply-retention-labels.md#applying-a-default-retention-label-to-all-content-in-a-sharepoint-library-folder-or-document-set). 

#### <a name="monitoring-retention-labels"></a>Contrôle des étiquettes de conservation

Depuis le centre de conformité Microsoft 365, utilisez l'outil **Aperçu** > **de la classification des données** pour surveiller l'utilisation de vos étiquettes de conservation chez votre locataire et identifier où se trouvent vos articles étiquetés. Pour plus d'informations, notamment sur les conditions préalables importantes, voir [Connaître ses données - Aperçu de la classification des données](data-classification-overview.md).

Vous pouvez ensuite approfondir vos informations à l’aide de [Explorateur de contenu](data-classification-content-explorer.md) et l’[explorateur d'activités](data-classification-activity-explorer.md).

> [!TIP]
>Envisagez d’utiliser d’autres informations sur la classification des données, telles que les classifieurs et les types d’informations sensibles, pour vous aider à identifier le contenu que vous devrez peut-être conserver ou supprimer, ou à gérer comme enregistrements.

Le Centre de sécurité et conformité Office 365 contient des informations de présentation équivalentes pour les étiquettes de rétention de **tableau de bord** > **gouvernance d’informations** , ainsi que des informations plus détaillées de **la gouvernance des informations** > **d’activité des étiquettes** . Pour plus d’informations sur la surveillance des étiquettes de rétention dans cet ancien centre d’administration, voir la documentation suivante :
- [Afficher les rapports de gouvernance des données](view-the-data-governance-reports.md)
- [Afficher l’utilisation d’étiquettes à l'aide des analyses d’étiquettes](label-analytics.md)
- [Afficher l’activité des étiquettes pour les documents](view-label-activity-for-documents.md)

#### <a name="using-content-search-to-find-all-content-with-a-specific-retention-label"></a>Utilisation de la recherche de contenu pour rechercher tout le contenu portant une étiquette de rétention spécifique

Lorsque les étiquettes de rétention sont affectées au contenu par les utilisateurs ou automatiquement, vous pouvez utiliser la recherche de contenu pour rechercher les contenus classés et dotés d’étiquettes de rétention spécifiques.

Lorsque vous créez une recherche de contenu, sélectionnez la condition **Étiquette de rétention** , puis entrez le nom complet ou une partie du nom de l’étiquette de rétention et utilisez un caractère générique. Si vous souhaitez en savoir plus, consultez la page [Requêtes par mots-clés et conditions de recherche pour la recherche de contenu](keyword-queries-and-search-conditions.md).
  
![État des étiquettes de rétention](../media/retention-label-condition.png)


## <a name="compare-capabilities-for-retention-policies-and-retention-labels"></a>Comparer les fonctionnalités des stratégies et des étiquettes de rétention

Utilisez le tableau suivant pour savoir si vous devez utiliser une stratégie ou une étiquette de rétention, selon leurs fonctionnalités.

|Fonctionnalité|Stratégie de rétention |Étiquette de rétention|
|:-----|:-----|:-----|:-----|
|Paramètres de rétention permettant conservation puis suppression, conservation uniquement ou suppression uniquement |Oui |Oui |
|Charges de travail prises en charge : <br />- Exchange <br />- SharePoint <br />- OneDrive <br />- Groupes Microsoft 365 <br />- Skype Entreprise <br />- Teams<br />- Yammer|<br /> Oui <br /> Oui <br /> Oui <br /> Oui <br /> Oui <br /> Oui | <br /> Oui, sauf dossiers publics <br /> Oui <br /> Oui <br /> Oui <br /> Non <br /> Non <br /> Non |
|Rétention appliquée automatiquement | Oui | Oui |
|Rétention appliquée en fonction de conditions <br /> – types d’informations sensibles, requêtes KQL, classificateurs pouvant être formés| Non | Oui |
|Rétention appliquée manuellement | Non | Oui |
|Présence d’interface utilisateur pour les utilisateurs finals | Non | Oui |
|Persiste si le contenu est déplacé | Non | Oui, au sein de votre client Microsoft 365 |
|Déclaration d’un élément comme enregistrement| Non | Oui |
|Démarrer la période de rétention: <br /> - Lors de la création ou de la dernière modification des éléments <br /> - Lorsque vous avez étiqueté ou basé sur un événement | <br />Oui <br />Non | <br />Oui <br /> Oui |
|Révisions avant élimination | Non| Oui |
|Preuve de la destruction pendant 7 ans | Non |Oui, lorsque l’élément est déclaré comme enregistrement|
|Audit des activités administratives| Oui | Oui|
|Identification des éléments soumis à une stratégie de rétention : <br /> - Recherche de contenu <br /> - Page classification des données, explorateur de contenu, explorateur d’activité | <br /> Non <br /> Non | <br /> Oui <br /> Oui|

Notez que vous pouvez utiliser les stratégies de rétention et les étiquettes de rétention comme méthodes de rétention complémentaires. Par exemple :

1. Vous créez et configurez une stratégie de rétention qui supprime automatiquement le contenu cinq ans après sa dernière modification, et l’appliquez à tous les comptes OneDrive.

2. Vous créez et configurez une étiquette de rétention qui conserve du contenu de façon définitive et l’ajoutez à une stratégie d’étiquette que vous publiez sur tous les comptes OneDrive. Vous expliquez aux utilisateurs comment appliquer manuellement cette étiquette à des documents spécifiques, qui ne doivent pas être supprimés automatiquement, même s’ils n’ont pas été modifiés depuis cinq ans.

Pour plus d’informations sur la façon dont les stratégies et les étiquettes de rétention fonctionnent conjointement, et sur la manière de déterminer le résultat de leur combinaison, voir la section suivante, qui explique les principes de la rétention et l’application des priorités.

## <a name="the-principles-of-retention-or-what-takes-precedence"></a>Principes de rétention et priorité

Il est possible, voire probable, que diverses stratégies et étiquettes de rétention soient appliquées à du contenu, chacune étant associée à une action (conserver, supprimer ou conserver puis supprimer) et à une période de rétention différentes. Quelle stratégie est prioritaire ? 

À un niveau élevé, vous pouvez être certain que la rétention a toujours priorité sur la suppression, et que la période de rétention la plus longue prime. 

Toutefois, plusieurs autres facteurs doivent être pris en compte. Vous pouvez donc utiliser le flux suivant pour comprendre le résultat ; chaque niveau permet de départager, du haut vers le bas : si le résultat est déterminé par le premier niveau, il n’est pas nécessaire de passer au niveau suivant, et ainsi de suite. Si le résultat ne peut pas être déterminé par les règles d’un niveau, le flux passe au niveau suivant pour déterminer le résultat pour lequel les paramètres de rétention sont prioritaires.

![Diagramme des principes de rétention](../media/1693d6ec-b340-4805-9da3-89aa41bc6afb.png)
  
Explication pour les quatre niveaux :
  
1. **La rétention prend le pas sur la suppression.** Supposons qu’une stratégie de rétention est configurée pour supprimer les messages Exchange au bout de trois ans, et qu’une autre stratégie de rétention est configurée pour conserver les messages Exchange pendant cinq ans avant de les supprimer. Tout le contenu atteignant l’âge de trois ans est supprimé et masqué à la vue des utilisateurs, mais reste conservé dans le dossier Éléments récupérables jusqu’à ce qu’il atteigne l’âge de cinq ans, moment auquel il est définitivement supprimé. 
2. **La période de rétention la plus longue l’emporte.** Si du contenu est soumis à plusieurs paramètres de rétention pour différentes périodes, il est conservé jusqu’à la fin de la période de rétention la plus longue.
    
3. **L’inclusion explicite prend le pas sur l’inclusion implicite** Voici ce que cela signifie : 
    
    1. Si une étiquette de rétention avec des paramètres de rétention est attribuée manuellement par un utilisateur à un élément tel qu’un message Exchange ou un document OneDrive, cette étiquette de rétention l’emporte sur toute stratégie de rétention appliquée au niveau du site ou de la boîte aux lettres, ainsi que sur une étiquette de rétention par défaut attribuée à la bibliothèque de documents. Par exemple, si l’étiquette de rétention explicite est configurée pour conserver le contenu pendant une période de rétention de dix ans, tandis qu’une stratégie de rétention appliquée au site est configurée pour conserver le contenu pendant une période de rétention de cinq ans, l’étiquette de rétention est prioritaire. Les étiquettes de rétention d’application automatique sont considérées comme implicites, plutôt qu’explicites, car Microsoft 365 les applique automatiquement.
    
    2. Si une stratégie de rétention inclut un emplacement spécifique, tel que la boîte aux lettres d’un utilisateur spécifique ou compte OneDrive, cette stratégie de rétention l’emporte sur une autre stratégie de rétention qui s’applique à l’ensemble des boîtes aux lettres ou des comptes OneDrive des utilisateurs, mais n’inclut pas spécifiquement la boîte aux lettres de l’utilisateur en question.
    
4. **La période de suppression la plus courte l’emporte** De même, si du contenu est soumis à plusieurs paramètres de rétention qui suppriment du contenu sans aucune période de rétention, celui-ci est supprimé à la fin de la période de rétention la plus courte. 

Enfin, une stratégie de rétention ou une étiquette de rétention ne peut pas supprimer définitivement du contenu en attente pour eDiscovery. Une fois cette conservation levée, le contenu est de nouveau éligible pour le processus de nettoyage dans les emplacements sécurisés liés à la charge de travail.

## <a name="auditing-retention-configuration"></a>Audit de la configuration de rétention

Les actions de l'administrateur concernant les politiques de rétention et les étiquettes de rétention sont enregistrées dans le journal d'audit lorsque [l'audit est activé](turn-audit-log-search-on-or-off.md). Par exemple, un événement d’audit est créé lors de la création, la configuration ou la suppression d’une politique de rétention ou d’une étiquette. Pour obtenir la liste complète, voir [Politiques de rétention et activités d’étiquette de rétention](search-the-audit-log-in-security-and-compliance.md#retention-policy-and-retention-label-activities).

## <a name="powershell-cmdlets-for-retention-policies-and-retention-labels"></a>Applets de commande pour les stratégies et étiquettes de rétention

Pour utiliser les applets de commande, vous devez tout d’abord [vous connecter au Centre de sécurité et conformité Office 365 – PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-scc-powershell). Utilisez ensuite l’une des applets de commande suivantes :

- [Get-ComplianceTag](https://docs.microsoft.com/powershell/module/exchange/get-compliancetag)

- [New-ComplianceTag](https://docs.microsoft.com/powershell/module/exchange/new-compliancetag)

- [Remove-ComplianceTag](https://docs.microsoft.com/powershell/module/exchange/remove-compliancetag)

- [Set-ComplianceTag](https://docs.microsoft.com/powershell/module/exchange/set-compliancetag)

- [Enable-ComplianceTagStorage](https://docs.microsoft.com/powershell/module/exchange/enable-compliancetagstorage)

- [Get-ComplianceTagStorage](https://docs.microsoft.com/powershell/module/exchange/get-compliancetagstorage)

- [Get-RetentionCompliancePolicy](https://docs.microsoft.com/powershell/module/exchange/get-retentioncompliancepolicy)

- [New-RetentionCompliancePolicy](https://docs.microsoft.com/powershell/module/exchange/new-retentioncompliancepolicy)

- [Remove-RetentionCompliancePolicy](https://docs.microsoft.com/powershell/module/exchange/remove-retentioncompliancepolicy)

- [Set-RetentionCompliancePolicy](https://docs.microsoft.com/powershell/module/exchange/set-retentioncompliancepolicy)

- [Get-RetentionComplianceRule](https://docs.microsoft.com/powershell/module/exchange/get-retentioncompliancerule)

- [New-RetentionComplianceRule](https://docs.microsoft.com/powershell/module/exchange/new-retentioncompliancerule)

- [Remove-RetentionComplianceRule](https://docs.microsoft.com/powershell/module/exchange/remove-retentioncompliancerule)

- [Set-RetentionComplianceRule](https://docs.microsoft.com/powershell/module/exchange/set-retentioncompliancerule)

## <a name="when-to-use-retention-policies-and-retention-labels-or-ediscovery-holds"></a>Moment d’utilisation des stratégies et étiquettes de rétention ou des conservations eDiscovery 

Bien que les paramètres de rétention et [les conservations que vous créez avec un cas eDiscovery](create-ediscovery-holds.md) peuvent empêcher la suppression définitive de données, ils sont conçus pour des scénarios différents. Pour comprendre les différences et faire votre choix, suivez ces instructions:

- Les paramètres de rétention que vous spécifiez dans les stratégies et les étiquettes de rétention sont conçus pour une stratégie de gestion des informations à long terme pour la conservation ou la suppression des données pour les exigences de conformité. L’étendue est généralement large, avec l’emplacement et le contenu comme focus principal plutôt que les utilisateurs individuels. Le début et la fin de la période de rétention sont configurables, avec l’option de suppression automatique de contenu sans intervention supplémentaire de l’administrateur.

- Les conservations eDiscovery (Core eDiscovery ou Advanced eDiscovery) sont conçues pour une durée limitée afin de conserver les données pour une investigation juridique. L’étendue est spécifique avec le contenu des utilisateurs identifiés comme focus. Le début et la fin de la période de conservation ne sont pas configurables, mais dépendent d’actions d’administrateur individuelles, sans option de suppression automatique de contenu lorsque la conservation est libérée.

Synthèse de la comparaison de la rétention et des conservations:

|Considération|Rétention |Conservations eDiscovery|
|:-----|:-----|:-----|:-----|
|Besoin commercial : |Conformité |Informations juridiques |
|Étendue du temps: |À long terme |Court terme |
|Focus: |Vaste, basé sur le contenu |Spécifique, basé sur l’utilisateur |
|Dates de début et de fin configurables: |Oui |Non |
|Suppression de contenu: |Oui (facultatif) |Non |
|Frais généraux d’administration: |Faible |Élevé |

Si le contenu est soumis à la fois aux paramètres de rétention et à une conservation eDiscovery, la conservation eDiscovery est prioritaire pour la préservation du contenu. De cette façon, les [principes de rétention](#the-principles-of-retention-or-what-takes-precedence) s’élargissent aux conservations eDiscovery parce qu’ils préservent les données jusqu’à ce qu’un administrateur libère manuellement la conservation. Cependant, malgré cette priorité, n’utilisez pas les conservations eDiscovery pour la gestion des informations à long terme. Si vous vous préoccupez de la suppression automatique des données, vous pouvez configurer les paramètres de rétention pour conserver les éléments indéfiniment, ou utiliser [révision des suppressions](disposition.md#disposition-reviews) avec les étiquettes de rétention.

Si vous utilisez des outils eDiscovery plus anciens pour conserver les données, consultez ces ressources:

- Exchange : 
    - [Conservation inaltérable et conservation pour litige](https://go.microsoft.com/fwlink/?linkid=846124)
    - [Comment identifier le type de conservation placé sur une boîte aux lettres Exchange Online](https://docs.microsoft.com/microsoft-365/compliance/identify-a-hold-on-an-exchange-online-mailbox)

- SharePoint et OneDrive: 
    - [Ajouter du contenu à un incident et placer des sources en conservation dans le centre eDiscovery](https://docs.microsoft.com/SharePoint/governance/add-content-to-a-case-and-place-sources-on-hold-in-the-ediscovery-center)

- [Retrait des outils eDiscovery hérités](legacy-ediscovery-retirement.md)

## <a name="use-retention-policies-and-retention-labels-instead-of-older-features"></a>Utilisez des stratégies et étiquettes de rétention plutôt que les anciennes fonctionnalités

Si, dans le cadre de la gouvernance des informations, vous avez besoin de conserver ou de supprimer proactivement du contenu dans Microsoft 365, nous vous recommandons d’utiliser les stratégies de rétention et les étiquettes de rétention plutôt que les anciennes fonctionnalités suivantes.

Si vous utilisez ces fonctionnalités, elles continueront de fonctionner parallèlement aux stratégies et étiquettes de rétention. Toutefois, nous vous recommandons d’utiliser à l’avenir les stratégies de rétention et les étiquettes de rétention à la place. Elles vous fournissent un mécanisme unique pour gérer de manière centralisée la rétention et la suppression de contenu dans Microsoft 365.

**Anciennes fonctionnalités dans Exchange Online :**

- [Balises de rétention et stratégies de rétention](https://go.microsoft.com/fwlink/?linkid=846125), aussi appelées [gestion des enregistrements de messagerie (MRM)](https://go.microsoft.com/fwlink/?linkid=846126) (suppression uniquement)

**Anciennes fonctionnalités dans SharePoint et OneDrive :**

- [Stratégies de suppression des documents](https://support.office.com/article/Create-a-document-deletion-policy-in-SharePoint-Server-2016-4fe26e19-4849-4eb9-a044-840ab47458ff) (suppression uniquement)
    
- [Configuration en place de gestion des enregistrements](https://support.office.com/article/7707a878-780c-4be6-9cb0-9718ecde050a) (rétention uniquement) 
    
- [Utilisation de stratégies pour la fermeture et la suppression de sites](https://support.microsoft.com/fr-FR/office/use-policies-for-site-closure-and-deletion-a8280d82-27fd-48c5-9adf-8a5431208ba5) (suppression uniquement) 
    
- [Stratégies de gestion des informations](intro-to-info-mgmt-policies.md) (suppression uniquement)
     
Si vous avez configuré des sites SharePoint pour des stratégies de type de contenu ou des stratégies de gestion des informations afin de conserver du contenu pour une liste ou une bibliothèque, ces stratégies sont ignorées tant qu’une stratégie de rétention est en vigueur. 

## <a name="related-information"></a>Informations connexes

- [Limites de SharePoint Online](https://docs.microsoft.com/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits)
- [Limites et spécifications de Microsoft Teams](https://docs.microsoft.com/microsoftteams/limits-specifications-teams) 
- [Se conformer à la réglementation SEC Rule 17 a-4](use-exchange-online-to-comply-with-sec-rule-17a-4.md)

## <a name="next-steps"></a>Étapes suivantes

Si vous êtes prêt à créer des stratégies de rétention, voir [Créer et configurer des stratégies de rétention](create-retention-policies.md).

Pour créer et publier des étiquettes de rétention :
- [Créer des étiquettes de rétention et les appliquer dans les applications](create-apply-retention-labels.md)
- [Appliquer automatiquement une étiquette de rétention au contenu](apply-retention-labels-automatically.md)

