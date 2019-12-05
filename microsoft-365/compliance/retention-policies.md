---
title: Vue d’ensemble des stratégies de rétention
ms.author: laurawi
author: laurawi
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Priority
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Une stratégie de rétention vous permet de décider de façon proactive de conserver du contenu, de le supprimer (ou les deux), de conserver du contenu, puis de le supprimer ; d’appliquer une stratégie unique à l’ensemble de l’organisation ou à quelques emplacements ou utilisateurs ; et d’appliquer une stratégie à tout le contenu ou au contenu remplissant certaines conditions.
ms.openlocfilehash: caeec733b3b5722f25210d0d2566e1dd9a5cd95e
ms.sourcegitcommit: 99d759d5c4e7d81266c3ebc087eaa37486cc0bc1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2019
ms.locfileid: "39818986"
---
# <a name="overview-of-retention-policies"></a>Vue d’ensemble des stratégies de rétention

Le volume et la complexité des données (e-mails, documents, messages instantanés et bien plus encore) de la majorité des organisations augmentent quotidiennement. Il est important de gérer et de gouverner efficacement ces informations, car vous devez :
  
- **respecter de façon proactive les réglementations du secteur et les stratégies internes** qui vous obligent à conserver du contenu pendant une période minimale. Par exemple, la loi Sarbanes-Oxley vous oblige à conserver certains types de contenu pendant sept ans ; 
    
- **réduire les risques en cas de litige ou de violation de la sécurité** en supprimant définitivement le contenu ancien qu’il n’est plus obligatoire de conserver ; 
    
- **aider votre organisation à partager efficacement les connaissances et à être plus agile** en vérifiant que vos utilisateurs traitent uniquement le contenu actuel et pertinent pour eux. 
    
Une stratégie de rétention peut vous aider à atteindre ces objectifs. La gestion du contenu nécessite généralement les deux actions suivantes :
  
- **Conservation** du contenu afin que celui-ci ne puisse pas être supprimé définitivement avant la fin de la période de rétention. 
    
- **Suppression** définitive du contenu à la fin de la période de rétention. 
    
Une stratégie de rétention vous permet d’effectuer les actions suivantes :
  
- Décider de façon proactive de conserver du contenu, de le supprimer (ou les deux), de conserver du contenu, puis de le supprimer.
    
- Appliquer une stratégie unique à l’ensemble de l’organisation ou à quelques emplacements ou utilisateurs.
    
- Appliquer une stratégie à tout le contenu ou au contenu remplissant certaines conditions, comme le contenu comportant des mots clés spécifiques ou [des types spécifiques d’informations sensibles](what-the-sensitive-information-types-look-for.md).
    
Lorsque le contenu est soumis à une stratégie de rétention, les utilisateurs peuvent continuer à le modifier et à l’utiliser comme si rien n’avait changé, car le contenu est conservé sur place, à son emplacement d’origine. Mais si quelqu’un modifie ou supprime le contenu qui est soumis à la stratégie, une copie est enregistrée dans un emplacement sécurisé où elle est conservée tant que la stratégie est en vigueur.
  
Enfin, certaines organisations doivent respecter des réglementations telles que la règle 17a-4 de la SEC (Securities and Exchange Commission), stipulant qu’après l’activation d’une stratégie de rétention, celle-ci ne peut pas être désactivée ni rendue moins restrictive. Pour remplir cette obligation, vous pouvez utiliser le verrouillage de conservation. Une fois la stratégie verrouillée, personne ne peut la désactiver ni la rendre moins restrictive, pas même l’administrateur.
  
La création et la gestion des stratégies de rétention s’effectuent sur :

- la page **Stratégies** du [Centre de conformité Microsoft 365](https://compliance.microsoft.com/).
- la page **Rétention** sous **Gouvernance des informations** du [Centre de sécurité &amp;et de conformité Office 365](https://protection.office.com/).
  
## <a name="how-a-retention-policy-works-with-content-in-place"></a>Fonctionnement d’une stratégie de rétention avec du contenu sur place

Lorsque vous incluez un emplacement tel qu’un site ou une boîte aux lettres dans une stratégie de rétention, le contenu reste dans son emplacement d’origine. Les utilisateurs peuvent continuer à traiter leurs documents ou leurs e-mails comme si rien n’avait changé. Cependant, s’ils modifient ou suppriment le contenu inclus dans la stratégie, une copie du contenu tel qu’il était lorsque vous avez appliqué la stratégie est conservée.
  
Concernant les collections de site SharePoint, une copie du contenu d’origine est conservée dans la bibliothèque de conservation et de préservation des documents lorsque les utilisateurs le modifient ou le suppriment. Pour la messagerie et les dossiers publics, la copie est conservée dans le dossier Éléments récupérables. Ces emplacements sécurisés et le contenu conservé ne sont pas visibles à la plupart des utilisateurs. Avec une stratégie de rétention, les utilisateurs peuvent ne pas être conscients que le contenu est soumis à la stratégie.
  
Remarques :
  
- Le contenu de Teams (conversation) est stocké dans Exchange, où la stratégie est appliquée en fonction du type de message (e-mail ou conversation).
    
- Une stratégie de rétention appliquée à un groupe Office 365 inclut la boîte aux lettres de groupe et le site.
    
### <a name="content-in-onedrive-accounts-and-sharepoint-sites"></a>Contenu des comptes OneDrive et des sites SharePoint

Une stratégie de rétention est appliquée au niveau de la collection d’un site. Lorsque vous incluez une collection de sites SharePoint ou un compte OneDrive dans une stratégie de rétention, une bibliothèque de conservation et de préservation est créée, s’il n’en existe pas. Vous pouvez afficher cette bibliothèque sur la page **Site.contents** dans le site de niveau supérieur de la collection de sites. La plupart des utilisateurs ne peuvent pas visualiser la bibliothèque de conservation et de préservation car elle est visible uniquement pour les administrateurs de collection de sites.
  
Si une personne tente de modifier ou de supprimer le contenu dans un site qui est soumis à une stratégie de rétention, la stratégie vérifie d’abord si le contenu a été modifié depuis qu’elle a été appliquée. S’il s’agit du premier changement depuis l’application de la stratégie, la stratégie de rétention copie le contenu dans la bibliothèque de conservation et de préservation, et permet ensuite à la personne de modifier ou de supprimer le contenu d’origine. Tout contenu dans la collection du site peut être copié dans la bibliothèque de conservation et de préservation, même si le contenu ne correspond pas à la requête utilisée par la stratégie de rétention.
  
Ensuite, un travail du minuteur nettoie la bibliothèque de conservation et de préservation des documents. Le travail du minuteur s’exécute périodiquement et compare tout le contenu de la bibliothèque de conservation et de préservation des documents à toutes les requêtes utilisées par les stratégies de rétention sur le site. À moins que le contenu corresponde à au moins une des requêtes, le travail du minuteur supprime définitivement le contenu de la bibliothèque de conservation et de préservation des documents.
  
Le précédent s’applique au contenu qui existe lorsque la stratégie de rétention est appliquée. En outre, tout contenu qui est créé ou ajouté au site après avoir été inclus dans la stratégie sera conservé après la suppression. Toutefois, le nouveau contenu n’est pas copié dans la bibliothèque de conservation et de préservation des documents la première fois qu’il est modifié, uniquement lorsqu’il est supprimé. Pour conserver les versions de tous les fichiers, vous devez activer le contrôle de version (consultez la section ci-après sur le contrôle de version).
  
Notez qu’un utilisateur reçoit une erreur s’il tente de supprimer une bibliothèque, une liste, un dossier ou un site soumis à une stratégie de rétention. Un utilisateur peut supprimer un dossier s’il déplace ou supprime d’abord les fichiers du dossier qui sont soumis à la stratégie. De plus, la bibliothèque de conservation et de préservation est créée uniquement lorsque le premier élément doit être copié dans la bibliothèque, et non lorsque vous créez la stratégie de rétention. Par conséquent, pour tester votre stratégie, vous devez d’abord modifier ou supprimer un document d’un site soumis à la stratégie, puis parcourir la bibliothèque de conservation et de préservation pour afficher la copie conservée.
  
Lorsqu’une stratégie de rétention est affectée à un compte OneDrive ou à un site SharePoint, le contenu suit l’un des deux chemins suivants :

![Diagramme de cycle de vie de contenu dans SharePoint et OneDrive](media/Retention_Diagram_of_retention_flow_in_sites.png)
  
1. **Si le contenu est modifié ou supprimé** pendant la période de rétention, une copie du contenu d’origine tel qu’il existait lors de l’attribution de la stratégie de rétention est créée dans la bibliothèque de conservation et de préservation des documents. Ici, un travail de minuteur s’exécute régulièrement et identifie les éléments dont la période de rétention a expiré, et ces éléments sont déplacés vers la Corbeille second niveau où ils sont ensuite supprimés définitivement au bout de 93 jours. La corbeille second niveau n’est pas visible par les utilisateurs finaux (seule le premier niveau de la corbeille l’est), mais les administrateurs de collection de sites peuvent afficher et restaurer du contenu à partir de cet emplacement.

    > [!NOTE]
    > Nous avons récemment modifié la manière dont le contenu est supprimé de la bibliothèque de conservation et de préservation. Pour éviter toute perte de données par inadvertance, nous ne supprimons plus définitivement le contenu de la bibliothèque de conservation. Au lieu de cela, nous ne supprimons définitivement que le contenu de la corbeille de façon à ce que tout le contenu de la bibliothèque de conservation et de préservation passe transmis par la corbeille second niveau .
    
2. **Si le contenu n’est ni modifié ni supprimé** pendant la période de rétention, il est déplacé vers la Corbeille premier niveau à la fin de la période de rétention. Si un utilisateur supprime le contenu à partir de là ou vide cette Corbeille (action également nommée « purge »), le document est déplacé vers la Corbeille second niveau. La période de rétention de 93 jours concerne tant la corbeille premier niveau que la corbeille second niveau. À la fin des 93 jours, le document est définitivement supprimé de l’emplacement en question (corbeille premier niveau ou second niveau). La Corbeille n’est pas indexée et par conséquent que la recherche n’y trouve pas de contenu. Cela signifie qu’une conservation eDiscovery ne trouve aucun contenu à conserver dans la Corbeille. 
    
### <a name="content-in-mailboxes-and-public-folders"></a>Contenu dans les boîtes aux lettres et les dossiers publics

Pour le courrier, le calendrier et d’autres éléments d’un utilisateur, une stratégie de rétention est appliquée au niveau d’une boîte aux lettres. Pour un dossier public, une stratégie de rétention est appliquée au niveau du dossier, et non au niveau de la boîte aux lettres. Les boîtes aux lettres et les dossiers publics utilisent le dossier Éléments récupérables pour conserver des éléments. Seules les personnes disposant d’autorisations eDiscovery peuvent afficher les éléments dans le dossier Éléments récupérables d’un autre utilisateur.
  
Par défaut, lorsqu’un utilisateur supprime un message d’un dossier autre que le dossier Éléments supprimés, le message est déplacé vers le dossier Éléments supprimés. Lorsqu’une personne supprime un élément dans le dossier Éléments supprimés, le message est déplacé vers le dossier Éléments récupérables. En outre, une personne peut supprimer (récupération possible) un élément (MAJ + SUPPR) dans n’importe quel dossier, ce qui permet d’ignorer le dossier Éléments supprimés et place directement l’élément dans le dossier Éléments récupérables.
  
Un processus évalue régulièrement les éléments du dossier Éléments récupérables. Si un élément ne correspond pas aux règles d’au moins une stratégie de rétention, l’élément est supprimé définitivement (processus également appelé suppression définitive) du dossier Éléments récupérables.
  
Lorsqu’un utilisateur tente de modifier certaines propriétés d’un élément de boîte aux lettres (objet, corps, pièces jointes, expéditeurs et destinataires ou la date d’envoi ou de réception d’un message), une copie de l’élément d’origine est enregistrée dans le dossier Éléments récupérables avant la validation de la modification. Cela se produit à chaque modification ultérieure. À la fin de la période de rétention, les copies présentes dans le dossier Éléments récupérables sont supprimées définitivement.
  
Si un utilisateur quitte votre organisation et que sa boîte aux lettres est incluse dans une stratégie de rétention, la boîte aux lettres devient inactive lorsque le compte d’utilisateur Office 365 est supprimé. Le contenu d’une boîte aux lettres inactive est toujours soumis à une stratégie de rétention placée sur la boîte aux lettres avant que celle-ci ne devienne inactive et ce contenu est disponible pour une recherche eDiscovery. Pour obtenir plus d’informations, consultez l’article [Boîtes aux lettres inactives dans Exchange Online](inactive-mailboxes-in-office-365.md).
  
Lorsqu’une stratégie de rétention est affectée à une boîte aux lettres ou à un dossier public, le contenu suit l’un des deux chemins suivants :

![Diagramme du flux de rétention dans la messagerie et les dossiers publics](media/88f174cc-bbf4-4305-93d7-0515f496c8f9.png)

1. **Si l’élément est modifié ou supprimé définitivement** par l’utilisateur (par MAJ + SUPPR ou supprimé du dossier Éléments supprimés) pendant la période de rétention, l’élément est déplacé (ou copié, dans le cas d’une modification) vers le dossier Éléments récupérables. Ici, un processus s’exécute régulièrement et identifie les éléments dont la période de rétention a expiré, et ces éléments sont supprimés définitivement dans les 14 jours suivant la fin de la période de rétention. Notez que le paramètre par défaut est de 14 jours, mais qu’il peut être configuré sur 30 jours.
    
2. **Si l’élément n’est ni modifié ni supprimé** pendant la période de rétention, ce même processus s’exécute régulièrement sur tous les dossiers de la boîte aux lettres et identifie les éléments dont la période de rétention a expiré. Ceux-ci sont alors supprimés définitivement dans les 14 jours suivant la fin de la période de rétention. Notez que le paramètre par défaut est de 14 jours, mais qu’il peut être configuré jusqu’à 30 jours. 
    
## <a name="how-a-retention-policy-works-with-document-versions-in-a-site-collection"></a>Fonctionnement d’une stratégie de rétention avec les versions d’un document dans un site

Le contrôle de version est une fonctionnalité de toutes les bibliothèques de documents dans SharePoint Online et OneDrive Entreprise. Par défaut, le contrôle de version conserve au moins les 500 versions principales, même si vous pouvez augmenter cette limite. Pour plus d'informations, voir [Activer et configurer le contrôle de version pour une liste ou une bibliothèque](https://support.office.com/article/1555d642-23ee-446a-990a-bcab618c7a37).
  
Une stratégie de maintien (stratégie de rétention qui conserve le contenu au lieu de supprimer uniquement) conserve toutes les versions d’un document dans une collection de sites SharePoint ou un compte OneDrive. Chaque fois qu'un document soumis à une stratégie de rétention ou de conservation est édité, une version est copiée dans la bibliothèque Preservation Hold. Chaque fois qu'un document soumis à une stratégie de rétention ou de conservation est supprimé, toutes les versions sont copiées dans la bibliothèque Preservation Hold si le contrôle de version est activé. Chaque version d’un document dans la bibliothèque Preservation Hold est présente sous la forme d’un élément distinct avec sa propre période de rétention :
  
- Si la stratégie de rétention est basée sur la date de création du contenu, chaque version comporte la même date d’expiration que le document d’origine. Le document d’origine et toutes ses versions expirent en même temps.
    
- Si la stratégie de rétention est basée sur la date de la dernière modification du contenu, chaque version possède sa propre date d’expiration basée sur la date à laquelle le document d’origine a été modifié pour créer cette version. Les documents d’origine et ses versions expirent séparément l’un de l’autre.

> [!NOTE]
> Les versions conservées des documents SharePoint et OneDrive ne sont pas consultables par les outils eDiscovery.

## <a name="retaining-content-for-a-specific-period-of-time"></a>Conservation du contenu pendant une période de temps spécifique

Avec une stratégie de rétention, vous pouvez conserver le contenu indéfiniment ou pour un nombre déterminé de jours, mois ou années. La durée pendant laquelle le contenu est conservé est calculée selon l’ancienneté du contenu, et non à partir du moment où la stratégie de rétention est appliquée. Vous pouvez choisir si l’ancienneté est basée sur la date de création du contenu ou (pour OneDrive et SharePoint) sur la dernière date de modification.
  
Par exemple, si vous souhaitez conserver le contenu d’un site pendant sept ans à compter de sa dernière modification, et qu’un document dans ce site n’a pas été modifié en six ans, le document sera conservé pendant un an de plus uniquement s’il n’est pas modifié. Si le document est modifié de nouveau, l’ancienneté du document est calculée à partir de la nouvelle date de dernière modification, et il sera conservé pendant sept ans supplémentaires.
  
De même, si vous voulez conserver le contenu d’une boîte aux lettres pendant sept ans et qu’un message a été envoyé il y a six ans, le message est conservé pendant un an seulement. Pour le contenu Exchange, l’ancienneté est toujours basée sur la date de réception ou d’envoi (elles sont identiques). La conservation du contenu basée sur la date de la dernière modification s’applique uniquement au contenu de site dans OneDrive et SharePoint.
  
Vous pouvez choisir si vous souhaitez que le contenu soit supprimé de façon définitive à la fin de la période de rétention. Une stratégie de rétention peut également supprimer l’ancien contenu sans le conserver. Voir la section suivante.
  
![Page Paramètres de rétention](media/b05f84e5-fc71-4717-8f7b-d06a29dc4f29.png)
  
## <a name="deleting-content-thats-older-than-a-specific-age"></a>Suppression du contenu antérieur à une date spécifique

Une stratégie de rétention permet à la fois de conserver, puis de supprimer du contenu, ou de supprimer du contenu ancien sans le conserver.
  
Si votre stratégie de rétention supprime du contenu, il est important de comprendre que la période spécifiée pour une stratégie de rétention est calculée en fonction de la date de création ou de modification du contenu, et non de la date d’affectation de la stratégie.
  
![Paramètres de suppression](media/042f9571-96f4-458f-8f38-fad3ed68ed31.png)
  
Par exemple, supposons que vous créez une stratégie de rétention qui supprime le contenu au bout de trois ans, puis que vous affectez cette stratégie à tous les comptes OneDrive, qui contiennent une grande quantité de contenu créé il y a quatre ou cinq ans. Dans ce cas, une grande quantité de contenu est supprimée peu après l’attribution de la stratégie de rétention pour la première fois. Pour cette raison, **une stratégie de rétention qui supprime le contenu peut avoir un impact considérable sur votre contenu**. 
  
Par conséquent, avant d’affecter une stratégie de rétention à un site pour la première fois, vous devez d’abord tenir compte de l’ancienneté du contenu existant et de la façon dont la stratégie peut avoir une incidence sur ce contenu. Vous pouvez également communiquer la nouvelle stratégie à vos utilisateurs avant de l’affecter, pour leur donner le temps d’évaluer les incidences éventuelles. Remarquez cet avertissement qui apparaît lorsque vous examinez les paramètres pour votre stratégie de rétention juste avant de la créer.
  
![Avertissement sur la suppression du contenu](media/59c26b19-3628-4cc1-9a73-a05127a8e81b.png)
  
## <a name="advanced-settings-that-apply-a-policy-only-to-content-that-meets-certain-conditions"></a>Paramètres avancés qui appliquent une stratégie uniquement au contenu répondant à certaines conditions

Une stratégie de rétention peut s’appliquer à tout le contenu des emplacements qui lui est propre, ou vous pouvez choisir d’appliquer une stratégie de rétention uniquement au contenu qui contient des mots clés spécifiques ou [des types spécifiques d’informations sensibles](what-the-sensitive-information-types-look-for.md).
  
![Options avancées de rétention](media/e8d9dd42-c062-4e8b-a2ca-bffe3ea298e0.png)
  
### <a name="retain-content-that-contains-specific-keywords"></a>Conservation du contenu qui contient des mots clés spécifiques

Vous pouvez appliquer une stratégie de rétention uniquement au contenu remplissant certaines conditions, puis mener des actions de rétention seulement sur ce contenu. Les conditions actuellement disponibles prennent en charge l’application d’une stratégie de rétention au contenu comprenant des mots ou des phrases spécifiques. Vous pouvez affiner votre requête à l’aide des opérateurs de recherche tels que AND, OR et NOT. Pour obtenir plus d’informations sur ces opérateurs, consultez l’article [Requêtes par mots clés et conditions de recherche pour la recherche de contenu](keyword-queries-and-search-conditions.md).
  
La prise en charge de l’ajout de propriétés utilisables dans une requête (par exemple, **subject:**) sera bientôt disponible.
  
La rétention basée sur une requête utilise l’index de recherche pour identifier le contenu.
  
![Éditeur de requête](media/2c31b412-922e-4a88-89e4-5175c23d9b5f.png)
  
### <a name="retain-content-that-contains-sensitive-information"></a>Conservation du contenu qui contient des informations sensibles

Vous pouvez également appliquer une stratégie de rétention uniquement au contenu qui contient [des types spécifiques d’informations sensibles](what-the-sensitive-information-types-look-for.md). Par exemple, vous pouvez choisir d’appliquer des exigences de rétention uniques seulement au contenu qui contient des informations d’identification personnelle (PII) telles que les identifiants fiscaux, les numéros de sécurité sociale ou les numéros de passeport.
  
![Page Types d’informations sensibles](media/8b104819-d185-4d58-b6b3-d06e82686a05.png)
  
Remarques :
  
- La rétention avancée des informations sensibles ne s’applique pas aux dossiers publics Exchange ou Skype Entreprise, car ces emplacements ne prennent pas en charge les types d’informations sensibles.
    
- Étant donné qu’Exchange Online utilise les règles de flux de messagerie (également appelées règles de transport) pour identifier les informations sensibles, cette stratégie ne fonctionne que sur les messages en transit, pas sur tous les éléments déjà stockés dans une boîte aux lettres. Pour Exchange Online, cela signifie qu’une stratégie de rétention peut identifier les informations sensibles et mener des actions de rétention uniquement sur les messages reçus **après** l’application de la stratégie à la boîte aux lettres (notez que la rétention basée sur une requête décrite dans la section précédente n’a pas cette limitation, car elle utilise l’index de recherche pour identifier le contenu). 
    
## <a name="applying-a-retention-policy-to-an-entire-organization-or-specific-locations"></a>Application d’une stratégie de rétention à l’ensemble d’une organisation ou des emplacements spécifiques

Vous pouvez facilement appliquer une stratégie de rétention à l’ensemble d’une organisation, des emplacements entiers, ou uniquement à certains emplacements ou utilisateurs.
  
### <a name="org-wide-policy"></a>Stratégie mise en place à l’échelle de l’organisation

L’une des fonctionnalités les plus puissantes d’une stratégie de rétention est que celle-ci s’applique par défaut aux emplacements au sein d’Office 365, notamment :
  
- Messagerie électronique Exchange
    
- Vue d’ensemble des collections de sites SharePoint
    
- Comptes OneDrive
    
- Groupes Office 365 (s’applique au contenu de la boîte aux lettres, du site, des documents. La prise en charge du contenu de planificateur, Yammer, CRM Microsoft Teams, PowerBI, Stream, Exchange et des sites d’équipe SharePoint sera bientôt disponible.)
    
- Dossiers publics Exchange
    
![Option Tous les emplacements](media/c343bd8e-42ac-4f17-a338-36f3c9598a86.png)
  
Voici d’autres fonctionnalités importantes d’une stratégie de rétention mise en place à l’échelle de l’organisation :
  
- Il n’existe aucune limite au nombre de boîtes aux lettres ou de sites que la stratégie peut inclure.
    
- Pour Exchange, toute nouvelle boîte aux lettres créée après l’application de la stratégie hérite automatiquement de la stratégie.
  
### <a name="a-policy-that-applies-to-entire-locations"></a>Une stratégie qui s’applique aux emplacements entiers

Lorsque vous choisissez des emplacements, vous pouvez facilement inclure ou exclure un emplacement entier, tel que la messagerie Exchange ou les comptes OneDrive. Pour ce faire, basculez l’**état** de cet emplacement sur Activé ou Désactivé. 
  
Comme pour une stratégie mise en place à l’échelle de l’organisation, si une stratégie s’applique à n’importe quelle combinaison d’emplacements entiers, il n’existe aucune limite au nombre de boîtes aux lettres ou de sites que la stratégie peut inclure. Par exemple, si une stratégie inclut toute la messagerie Exchange et tous les sites SharePoint, l’ensemble des sites et des boîtes aux lettres est également inclus, quel que soit le nombre. Et pour Exchange, toute nouvelle boîte aux lettres créée après la stratégie hérite automatiquement de la stratégie.
 
![Sélectionner des pages emplacements](media/6ac0c2d6-1abf-4690-b3f6-9ca506887ba3.png)
  
### <a name="a-policy-with-specific-inclusions-or-exclusions"></a>Une stratégie avec des inclusions ou exclusions spécifiques

Vous pouvez également appliquer une stratégie de rétention à des utilisateurs, groupes Office 365 ou sites spécifiques. Pour ce faire, activez le **Statut** de cet emplacement, puis utilisez les liens pour inclure ou exclure des utilisateurs, des groupes Office 365 ou des sites spécifiques. 
  
Cependant, notez que les limites suivantes existent pour une stratégie de rétention qui inclut ou exclut plus de 1 000 emplacements spécifiques :
  
- Une telle stratégie de rétention peut contenir 1 000 boîtes aux lettres et 100 sites au maximum.
    
- Un client peut contenir 10 000 stratégies de rétention au maximum.
    
Bien que ces limites existent, notez que vous pouvez les contourner en appliquant une stratégie mise en place à l’échelle de l’organisation ou une stratégie qui s’applique aux emplacements entiers.
  
### <a name="skype-locations"></a>Emplacements Skype

Contrairement à la messagerie Exchange, vous ne pouvez pas basculer le statut de l’emplacement Skype pour inclure tous les utilisateurs, mais vous pouvez activer cet emplacement, puis sélectionner manuellement les utilisateurs dont vous souhaitez conserver les conversations.
  
Lorsque vous choisissez des utilisateurs de Skype Entreprise, vous pouvez rapidement inclure tous les utilisateurs en activant la case à cocher **Nom** dans l’en-tête de colonne. Toutefois, il est important de comprendre que chaque utilisateur compte comme une inclusion spécifique dans la stratégie. Par conséquent, si vous incluez plus de 1 000 utilisateurs, les limites indiquées dans la section précédente s’appliquent. Le fait de sélectionner tous les utilisateurs Skype ici ne revient pas au même qu’une stratégie à l’échelle de l’organisation qui serait en mesure d’inclure tous les utilisateurs Skype par défaut. 
  
![Page Sélection des utilisateurs Skype](media/f1742493-741a-4142-a564-d7d41ab0236a.png)
  
Notez que **Historique des conversations**, un dossier dans Outlook, est une fonctionnalité qui n’a rien à voir avec l’archivage Skype. La fonctionnalité **Historique des conversations** peut être désactivée par l’utilisateur final, mais l’archivage pour Skype s’effectue en stockant une copie des conversations Skype dans un dossier masqué inaccessible à l’utilisateur, mais disponible pour eDiscovery.

### <a name="teams-locations"></a>Emplacements Teams

Vous pouvez utiliser une stratégie de rétention pour conserver des conversations et des messages de canal dans Teams. Les conversations Teams sont stockées dans un dossier masqué dans la boîte aux lettres de chaque utilisateur inclus dans la conversation, et les messages de canal Teams sont stockés dans un dossier masqué similaire dans la boîte aux lettres de groupe de l’équipe. Toutefois, il est important de comprendre que Teams utilise un service de conversation basé sur Azure qui stocke également ces données. Par défaut, ce service stocke les données indéfiniment. Pour cette raison, nous vous recommandons vivement d’utiliser l’emplacement Teams pour conserver et supprimer des données Teams. Utiliser l’emplacement Teams permet de supprimer définitivement des données à partir de boîtes aux lettres Exchange et du service de conversation basé sur Azure. Pour obtenir plus d’informations, consultez l’article [Présentation de la sécurité et de la conformité dans Microsoft Teams](https://go.microsoft.com/fwlink/?linkid=871258).
  
Les conversations et les messages de canal Teams ne sont pas affectés par les stratégies de rétention appliquées aux boîtes aux lettres d’utilisateur ou de groupe dans les emplacements Exchange ou les groupes Office 365. Même si les conversations et les messages de canal Teams sont stockés dans Exchange, ces éléments sont uniquement affectés par une stratégie de rétention appliquée à l’emplacement Teams.
  
Lorsqu’une stratégie de rétention est affectée à une équipe, les conversations et les messages de canal suivent l’un des deux chemins suivants :

![Diagramme de flux de rétention pour les conversations et messages de canal Teams](media/TeamsRetentionLifecycle.png)

1. **Si une conversation ou un message de canal est modifié ou supprimé** par l’utilisateur pendant la période de rétention, le message est déplacé (ou copié, en cas de modification) dans le dossier SubstrateHolds (qui est un dossier masqué dans chaque boîte aux lettres d’utilisateur ou de groupe) et est stocké dans ce dossier jusqu’à l’expiration de la période de rétention. Les messages sont supprimés définitivement le jour où la période de rétention expire.

2. **Si une conversation ou un message de canal n’est pas supprimé** pendant la période de rétention, le message est déplacé vers le dossier SubstrateHolds dans un délai d’un jour après l’expiration de la période de rétention (cela prend entre 0 et 24 heures). Le message est définitivement supprimé un jour après son déplacement vers le dossier SubstrateHolds. 

> [!NOTE]
> Les messages dans le dossier SubstrateHolds peuvent faire l’objet de recherches par les outils eDiscovery. Une fois un message supprimé définitivement, il n’apparaîtra pas dans les recherches eDiscovery.

Nous cherchons constamment à optimiser les fonctionnalités de rétention dans Teams, et nous envisageons de lancer de nouvelles fonctionnalités au cours des prochains mois. D’ici là, voici quelques limitations importantes dont vous devez tenir compte :
  
- **Teams nécessite une stratégie de rétention distincte**. Lorsque vous créez une stratégie de rétention et basculez sur l’emplacement Teams, tous les autres emplacements sont désactivés. Une stratégie de rétention qui inclut Teams ne peut inclure que Teams et aucun autre emplacement. 
    
- **Teams n’est pas inclus dans une stratégie à l’échelle de l’organisation**. Si vous créez une stratégie à l’échelle de l’organisation, Teams n’est pas inclus, car il nécessite une stratégie de rétention distincte. 
    
- **Teams ne prend pas en charge les rétentions avancées**. Lorsque vous créez une stratégie de rétention, si vous choisissez les [Paramètres avancés qui appliquent une stratégie uniquement au contenu qui répond à certaines conditions](#advanced-settings-that-apply-a-policy-only-to-content-that-meets-certain-conditions), l’emplacement Teams n’est pas disponible. Actuellement, la fonctionnalité de rétention dans Teams s’applique à l’ensemble du contenu des conversations et des messages de canal. 

- **Le contenu de Teams dans les canaux privés n’est pas pris en charge**. Actuellement, les stratégies de rétention créées pour Teams ne s’appliquent pas aux messages de canaux privés. Seuls les messages de canaux standard sont soumis à une stratégie de rétention créée pour Teams. Les stratégies de rétention pour les canaux privés seront bientôt prises en charge. 
    
- **Teams peut prendre jusqu’à trois jours pour nettoyer les messages arrivés à expiration**. Une stratégie de rétention appliquée à Teams supprimera les conversations et les messages de canal à l’expiration de la période de rétention. Toutefois, le nettoyage et la suppression définitive de ces messages peut prendre jusqu’à trois jours. De plus, les conversations et les messages de canal pourront faire l’objet d’une recherche avec les outils eDiscovery entre le moment qui suit l’expiration de la période de rétention et celui où les messages sont supprimés définitivement.

   > [!NOTE]
   > Auparavant, une stratégie de rétention ne pouvait pas supprimer du contenu de Teams qui avait moins de 30 jours, mais nous avons supprimé cette limitation. Vous pouvez désormais choisir le nombre de jours de la période de rétention du contenu de Teams, et ce peut être seulement un jour. Si vous avez une période de rétention d’un jour, il faudra jusqu’à trois jours après l’expiration de la période de rétention avant la suppression définitive des messages.
    
Dans une équipe, les fichiers qui sont partagés au cours d’une conversation sont stockés dans le compte OneDrive de l’utilisateur qui partage le fichier. Les fichiers qui sont chargés dans des canaux sont stockés dans le site SharePoint associé à l’équipe. Par conséquent, pour conserver ou supprimer des fichiers dans une équipe, vous devez créer une stratégie de rétention qui s’applique spécifiquement aux emplacements SharePoint et OneDrive. Pour appliquer une stratégie aux fichiers d’une équipe spécifique, vous pouvez choisir le site SharePoint de l’équipe et les comptes OneDrive des utilisateurs qui font partie de l’équipe.
  
Une stratégie de rétention qui s’applique à Teams peut utiliser le [Verrouillage de conservation](#locking-a-retention-policy).
  
![Emplacements Teams pour les conversations et les messages de canal](media/127345da-e802-4b3a-afc7-6e354dc3f409.png)
  
> [!NOTE]
> Si vous créez des stratégies de rétention pour les emplacements Teams ou Skype au sein de votre organisation, l’une de ces stratégies apparaît comme stratégie de dossier par défaut lorsqu’un utilisateur affiche les propriétés d’un dossier de boîte aux lettres dans le client de bureau Outlook. Il s’agit [d’un problème connu](https://support.microsoft.com/help/4491013/outlook-client-displays-teams-or-skype-for-business-retention-policies)d’affichage incorrect dans Outlook. Ce qui doit s’afficher comme stratégie de dossier par défaut est la stratégie de rétention de boîte aux lettres appliquée au dossier. La stratégie de rétention de Skype ou Teams n’est pas appliquée à la boîte aux lettres de l’utilisateur.  

### <a name="office-365-groups-locations"></a>Emplacements de groupes Office 365

Pour conserver le contenu d'un groupe Office 365, vous devez utiliser l'emplacement des groupes Office 365. Même si un groupe Office 365 possède une boîte aux lettres Exchange, une politique de rétention qui inclut l'ensemble de l'emplacement Exchange n'inclut pas le contenu des boîtes aux lettres du groupe Office 365. Une stratégie de rétention appliquée à un groupe Office 365 inclut la boîte aux lettres de groupe et le site. Une stratégie de rétention appliquée à un groupe Office 365 protège les ressources créées par un groupe Office 365, ce qui inclut Microsoft Teams.

De plus, il n’est pas possible d’utiliser l’emplacement Exchange pour inclure ou exclure une boîte aux lettres de groupe spécifique. Bien que l’emplacement Exchange permette initialement de sélectionner une boîte aux lettres de groupe, lorsque vous essayez d’enregistrer la stratégie de rétention, vous recevez une erreur qui indique que « RemoteGroupMailbox » n’est pas une sélection valide pour l’emplacement Exchange. 

## <a name="excluding-specific-types-of-exchange-items-from-a-retention-policy"></a>Exclusion de types spécifiques d’éléments Exchange d’une stratégie de rétention
À l’aide de PowerShell, vous pouvez exclure des types spécifiques d’éléments Exchange d’une stratégie de rétention. Par exemple, vous pouvez exclure des messages vocaux, des conversations par messagerie instantanée et d’autre contenu Skype Entreprise Online dans les boîtes aux lettres. Vous pouvez également exclure des éléments de calendrier, de note et de tâche. Cette fonctionnalité est disponible uniquement à l’aide de PowerShell ; elle n’est pas disponible dans l’interface utilisateur lorsque vous créez une stratégie de rétention.
  
Pour ce faire, utilisez le paramètre `ExcludedItemClasses` des cmdlets `New-RetentionComplianceRule` et `Set-RetentionComplianceRule`. Pour obtenir plus d’informations sur PowerShell, consultez la section [Trouver les cmdlets PowerShell pour les stratégies de rétention](#find-the-powershell-cmdlets-for-retention-policies) indiquée ci-après.

## <a name="locking-a-retention-policy"></a>Verrouillage d’une stratégie de rétention
Certaines organisations doivent respecter des règles définies par des organismes de réglementation, comme la règle 17a-4 de la SEC (Securities and Exchange Commission), stipulant qu’après l’activation d’une stratégie de rétention, celle-ci ne peut pas être désactivée ni rendue moins restrictive. Grâce au verrouillage de conservation, vous pouvez verrouiller la stratégie afin que personne ne puisse la désactiver ni la rendre moins restrictive, pas même l’administrateur.
  
Après qu’une stratégie a été verrouillée, personne ne peut la désactiver ou en supprimer des emplacements. De plus, il n’est pas possible de modifier ni de supprimer le contenu soumis à la stratégie pendant la période de rétention. Une fois que la stratégie est verrouillée, vous pouvez seulement y ajouter des emplacements ou la prolonger. Une stratégie verrouillée peut être accrue ou étendue, mais pas réduite ni désactivée.
  
Par conséquent, avant de verrouiller une stratégie de rétention, il est **essentiel** de comprendre les exigences de conformité de votre organisation. **Ne verrouillez pas une stratégie** tant que vous n’êtes pas certain qu’elle réponde exactement à vos besoins.

### <a name="lock-a-retention-policy-by-using-powershell"></a>Verrouiller une stratégie de rétention à l’aide de PowerShell
  
Vous pouvez verrouiller une stratégie de rétention à l’aide de PowerShell.

Tout d’abord,[se connecter au Centre de Conformité et Sécurité Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkID=799771).

Ensuite, pour afficher une liste de vos stratégies de rétention et rechercher le nom de la stratégie que vous souhaitez verrouiller, exécutez `Get-RetentionCompliancePolicy`.

![Liste des stratégies de rétention dans PowerShell](media/retention-policy-preservation-lock-get-retentioncompliancepolicy.PNG)

Enfin, pour placer un Verrouillage de Conservation sur la stratégie de rétention, exécutez `Set-RetentionCompliancePolicy` avec le`RestrictiveRetention` paramètre défini sur true. Par exemple :

`Set-RetentionCompliancePolicy -Identity “<Name of Policy>” – RestrictiveRetention $true`

![Paramètre RestrictiveRetention dans PowerShell](media/retention-policy-preservation-lock-restrictiveretention.PNG)

Après avoir exécuté cette applet de commande, vous voyez une invite de confirmation. Sélectionnez **Oui partout**.

![Invite à confirmer que vous souhaitez verrouiller une stratégie de rétention dans PowerShell](media/retention-policy-preservation-lock-confirmation-prompt.PNG)

Un verrouillage de conservation est désormais placé sur la stratégie de rétention. Si vous exécutez `Get-RetentionCompliancePolicy`, le paramètre `RestrictiveRetention` est défini sur true. Par exemple :

`Get-RetentionCompliancePolicy -Identity “<Name of Policy>” |Fl`

![Stratégie verrouillée avec tous les paramètres affichés dans PowerShell](media/retention-policy-preservation-lock-locked-policy.PNG)
  
## <a name="releasing-a-retention-policy"></a>Publication d’une stratégie de rétention

Vous pouvez désactiver ou supprimer une stratégie de rétention à tout moment. Lorsque vous procédez de la sorte, le contenu SharePoint ou OneDrive conservé dans la bibliothèque de conservation n’est pas immédiatement supprimé définitivement. Au lieu de cela, pour éviter la perte accidentelle de données, il existe une période de grâce de 30 jours pendant laquelle l’expiration du contenu de cette stratégie ne se produit pas dans la bibliothèque de conservation de conservation, afin que vous puissiez restaurer tout contenu à partir de cet emplacement, le cas échéant. Vous pouvez également réactiver la stratégie de rétention pendant la période de grâce et aucun contenu ne sera supprimé pour cette stratégie.

Cette période de grâce de 30 jours dans SharePoint et OneDrive correspond à un délai de 30 jours dans Exchange. Pour des informations supplémentaires, consultez [Gestion des boîtes aux lettres avec période de grâce](identify-a-hold-on-an-exchange-online-mailbox.md#managing-mailboxes-on-delay-hold).

## <a name="the-principles-of-retention-or-what-takes-precedence"></a>Principes de rétention et priorité

Il est possible, voire même probable, que le contenu fasse l’objet de plusieurs stratégies de rétention, chacune avec une action (conservation, suppression ou les deux) et une période de rétention différentes. Laquelle est prioritaire ? Au plus haut niveau, sachez que le contenu conservé par une stratégie ne peut pas être supprimé définitivement par une autre stratégie.
  
![Diagramme des principes de rétention](media/1693d6ec-b340-4805-9da3-89aa41bc6afb.png)
  
Pour comprendre comment les différentes stratégies de rétention s’appliquent au contenu, prenez en compte les principes de rétention suivants :
  
1. **La rétention prend le pas sur la suppression.** Supposons qu’une stratégie de rétention stipule de supprimer les messages Exchange au bout de trois ans, et qu’une autre stratégie de rétention stipule de conserver les messages Exchange pendant cinq ans avant de les supprimer. Tout le contenu atteignant l’âge de trois ans est supprimé et masqué à la vue des utilisateurs, mais reste conservé dans le dossier Éléments récupérables jusqu’à ce qu’il atteigne l’âge de cinq ans, moment auquel il est définitivement supprimé. 
    
2. **La période de rétention la plus longue l’emporte.** Si du contenu est soumis à plusieurs stratégies de rétention, il est conservé jusqu’à la fin de la période de rétention la plus longue. 
    
3. **L’inclusion explicite prend le pas sur l’inclusion implicite** Voici ce que cela signifie : 
    
    1. Si une étiquette avec des paramètres de rétention est attribuée manuellement par un utilisateur à un élément tel qu’un courrier électronique Exchange ou un document OneDrive, cette étiquette l’emporte sur toute stratégie appliquée au niveau du site ou de la boîte aux lettres, ainsi que sur une étiquette par défaut attribuée par la bibliothèque de documents. Par exemple, si l’étiquette explicite stipule une période de rétention de dix ans, tandis que la stratégie appliquée au site indique une période de rétention de cinq ans, l’étiquette est prioritaire. Les étiquettes d’application automatique sont considérées comme implicites et non explicites, car Office 365 les applique automatiquement.
    
    2. Si une stratégie de rétention inclut un emplacement spécifique, tel que la boîte aux lettres d’un utilisateur spécifique ou compte OneDrive Entreprise, cette stratégie l’emporte sur une autre stratégie de rétention qui s’applique à l’ensemble des boîtes aux lettres ou des comptes OneDrive Entreprise des utilisateurs, mais n’inclut pas spécifiquement la boîte aux lettres de l’utilisateur en question.
    
4. **La période de suppression la plus courte l’emporte. ** De même, si du contenu est soumis à plusieurs stratégies de suppression (sans aucune rétention), il est supprimé à la fin de la période de rétention la plus courte. 
    
Notez que les principes de rétention opèrent comme un flux de partage du haut vers le bas : si les règles appliquées par toutes les stratégies ou étiquettes sont identiques sur un même niveau, le flux passe au niveau inférieur pour déterminer la règle prioritaire à appliquer.
  
Enfin, une stratégie de rétention ou une étiquette ne peut pas supprimer définitivement du contenu placé en conservation pour eDiscovery. Lorsque cette conservation est levée, le contenu est de nouveau éligible pour le processus de nettoyage décrit ci-dessus.
  
## <a name="use-a-retention-policy-instead-of-these-features"></a>Utilisation d’une stratégie de rétention au lieu de ces fonctionnalités

Une stratégie de rétention unique peut s’appliquer facilement à l’ensemble d’une organisation et à des emplacements entiers dans Office 365, notamment Exchange Online, SharePoint Online, OneDrive Entreprise et Groupes Office 365. Si vous devez conserver ou supprimer du contenu n’importe où dans Office 365, nous vous recommandons d’utiliser une stratégie de rétention. (Vous pouvez également utiliser des étiquettes avec des paramètres de rétention. Pour plus d’informations, voir [vue d’ensemble des étiquettes](labels.md).)
  
Plusieurs autres fonctionnalités étaient auparavant utilisées pour conserver ou supprimer du contenu dans Office 365. Celles-ci sont répertoriées ci-dessous. Ces fonctionnalités continueront de fonctionner parallèlement aux stratégies et étiquettes de rétention. Toutefois, pour la gouvernance des informations, nous vous recommandons d’utiliser une stratégie ou des étiquettes de rétention plutôt que ces fonctionnalités. Une stratégie de rétention est la seule fonctionnalité qui permet de conserver et de supprimer du contenu dans Office 365.
  
### <a name="exchange-online"></a>Exchange Online

- [Gestion des cas eDiscovery dans le Centre de sécurité &amp; conformité Office 365](https://support.office.com/article/edea80d6-20a7-40fb-b8c4-5e8c8395f6da) (conservation eDiscovery) 
    
- [Conservation inaltérable et conservation pour litige](https://go.microsoft.com/fwlink/?linkid=846124) (conservation eDiscovery) 

- [Comment identifier le type de conservation placé sur une boîte aux lettres Exchange Online](identify-a-hold-on-an-exchange-online-mailbox.md)
    
- [Balises de rétention et stratégies de rétention](https://go.microsoft.com/fwlink/?linkid=846125), aussi appelées [gestion des enregistrements de messagerie (MRM)](https://go.microsoft.com/fwlink/?linkid=846126) (suppression uniquement) 
    
### <a name="sharepoint-online-and-onedrive-for-business"></a>Sharepoint Online et OneDrive Entreprise

- [Gestion des cas eDiscovery dans le Centre de sécurité &amp; conformité Office 365](https://support.office.com/article/edea80d6-20a7-40fb-b8c4-5e8c8395f6da) (conservation eDiscovery) 
    
- [Ajout du contenu à un incident et placement des sources en conservation dans le centre eDiscovery](https://support.office.com/article/54d70de9-1ec2-4325-84f3-aeb588554479) (conservation eDiscovery) 
    
- [Vue d’ensemble des stratégies de suppression de documents](https://support.office.com/article/55e8d858-f278-482b-a198-2e62d6a2e6e5) (suppression uniquement) 
    
- [Configuration en place de gestion des enregistrements](https://support.office.com/article/7707a878-780c-4be6-9cb0-9718ecde050a) (rétention) 
    
- [Utilisation de stratégies pour la fermeture et la suppression de sites](https://support.office.com/article/a8280d82-27fd-48c5-9adf-8a5431208ba5) (suppression uniquement) 
    
- [Stratégies de gestion des informations](intro-to-info-mgmt-policies.md) (suppression uniquement) 
    
Si vous avez déjà utilisé des conservations eDiscovery à des fins de gouvernance des informations, il est préférable d’utiliser une stratégie de rétention pour assurer une conformité proactive. Les conservations doivent uniquement être utilisées à des fins d’eDiscovery.
  
### <a name="retention-policies-override-information-management-policies"></a>Les stratégies de rétention remplacent les stratégies de gestion des informations

Sur les sites SharePoint, vous utilisez peut-être des [stratégies de gestion des informations](intro-to-info-mgmt-policies.md) pour conserver le contenu. Si vous appliquez une stratégie de rétention à un site qui utilise déjà des stratégies de type de contenu ou des stratégies de gestion des informations pour une liste ou une bibliothèque, ces stratégies sont ignorées tant que la stratégie de rétention est en vigueur. 
  
## <a name="what-happened-to-preservation-policies"></a>Qu’est-il advenu des stratégies de conservation ?

Si vous utilisiez une stratégie de conservation, celle-ci a été automatiquement convertie en stratégie de rétention qui utilise uniquement l’action de conservation : la stratégie ne supprimera pas le contenu. La stratégie de conservation continue de fonctionner et de conserver votre contenu sans que vous ayez à apporter la moindre modification. Vous trouverez ces stratégies sur la page **Stratégies** du [Centre de conformité Microsoft 365](https://compliance.microsoft.com/) ou sur la page**Rétention** sous **Gouvernance des Informations** du [Centre de sécurité &amp; et de conformité](https://protection.office.com/). Vous pouvez modifier une stratégie de conservation afin de changer la période de rétention, mais vous ne pouvez pas apporter d’autres modifications ; par exemple, vous ne pouvez pas ajouter ou supprimer des emplacements. 
  
## <a name="permissions"></a>Autorisations

Les membres de votre équipe de conformité appelés à créer des stratégies de rétention ont besoin d’autorisations pour accéder au [Centre de sécurité &amp;et de conformité](https://protection.office.com/). Par défaut, votre administrateur locataire a accès à cet emplacement et peut accorder aux responsables de la mise en conformité et à d’autres personnes l’accès au [Centre de sécurité&amp; et de conformité](https://protection.office.com/), sans leur donner toutes les autorisations d’un administrateur locataire. Pour ce faire, nous vous recommandons d’accéder à la page **Autorisations** du [Centre de sécurité&amp; et de conformité](https://protection.office.com/), de modifier le groupe de rôles **Administrateur de conformité** et d’ajouter des membres à ce groupe de rôles. 
  
Pour obtenir plus d’informations, consultez l’article [Octroi de l’accès au Centre de sécurité &amp; conformité Office 365 aux utilisateurs](/security/office-365-security/grant-access-to-the-security-and-compliance-center.md).
  
Ces autorisations sont requises uniquement pour créer et appliquer une stratégie de rétention. L’application d’une stratégie ne nécessite pas d’accès au contenu.
  
## <a name="find-the-powershell-cmdlets-for-retention-policies"></a>Trouver les cmdlets PowerShell pour les stratégies de rétention

Pour utiliser les cmdlets des stratégies de rétention, vous devez effectuer les étapes suivantes :
  
1. [Se connecter au Centre de sécurité &amp; conformité Office 365 à l’aide de PowerShell à distance](https://go.microsoft.com/fwlink/?LinkID=799771&amp;clcid=0x409)
    
2. Utiliser ces [cmdlets du Centre de sécurité &amp; conformité Office 365](https://go.microsoft.com/fwlink/?LinkID=799772&amp;clcid=0x409)
    
## <a name="more-information"></a>Plus d’informations

- [Vue d’ensemble des étiquettes](labels.md)
- [Limites de SharePoint Online](https://docs.microsoft.com/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits)
- [Limites et spécifications de Microsoft Teams](https://docs.microsoft.com/microsoftteams/limits-specifications-teams) 
    
