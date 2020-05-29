---
title: Présentation des stratégies de rétention pour conserver ou supprimer automatiquement un contenu
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
search.appverid:
- MOE150
- MET150
description: Utiliser une stratégie de rétention vous permet de décider de façon proactive de conserver du contenu, de le supprimer (ou les deux), de conserver du contenu, puis de le supprimer ; d’appliquer une stratégie unique à l’ensemble de l’organisation ou à quelques emplacements ou utilisateurs ; et d’appliquer une stratégie à tout le contenu ou au contenu remplissant des conditions particulières.
ms.openlocfilehash: b91b4be724c3d664cdd237fc01596372a2a6bdcc
ms.sourcegitcommit: 5c96d06496d40d2523edbea336f7355c3c77cc80
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2020
ms.locfileid: "44412813"
---
# <a name="learn-about-retention-policies"></a>Découvrir les stratégies de rétention

>*[Guide de sécurité et conformité pour les licences Microsoft 365](https://aka.ms/ComplianceSD).*

Le volume et la complexité des données e-mails, documents, messages instantanés et autres de la majorité des organisations augmentent quotidiennement. Il est important de gérer et de gouverner efficacement ces informations, car vous devez :
  
- **respecter de façon proactive les réglementations du secteur et les stratégies internes** qui vous obligent à conserver du contenu pendant une période minimale. Par exemple, la loi Sarbanes-Oxley vous oblige à conserver certains types de contenu pendant sept ans. 
    
- **réduire les risques en cas de litige ou de violation de la sécurité** en supprimant définitivement le contenu ancien qu’il n’est plus obligatoire de conserver ; 
    
- **aider votre organisation à partager efficacement les connaissances et à être plus agile** en vérifiant que vos utilisateurs traitent uniquement le contenu actuel et pertinent pour eux. 
    
Une stratégie de rétention peut vous aider à atteindre ces objectifs. La gestion du contenu nécessite généralement les deux actions suivantes :
  
- **Conservation** du contenu afin que celui-ci ne puisse pas être supprimé définitivement avant la fin de la période de rétention. 
    
- **Suppression** définitive du contenu à la fin de la période de rétention. 
    
Une stratégie de rétention vous permet d’effectuer les actions suivantes :
  
- Décider de façon proactive de conserver du contenu, de le supprimer (ou les deux), de conserver du contenu, puis de le supprimer.
    
- Appliquer une stratégie unique à l’ensemble de l’organisation ou à quelques emplacements ou utilisateurs.
    
- Appliquer une stratégie à tout le contenu ou à du contenu qui remplit des conditions spécifiques, comme le contenu comportant des mots clés particuliers ou [des types d’informations sensibles](what-the-sensitive-information-types-look-for.md).
    
Lorsque le contenu est soumis à une stratégie de rétention, les utilisateurs peuvent continuer à le modifier et à l’utiliser comme si rien n’avait changé. Le contenu est conservé sur place, à son emplacement d’origine. Mais si quelqu’un modifie ou supprime le contenu qui est soumis à la stratégie de rétention, une copie du contenu d’origine est enregistrée dans un emplacement sécurisé où elle est conservée tant que la stratégie de rétention pour ce contenu est en vigueur. Pour obtenir plus d’informations, consultez la section [Fonctionnement d’une stratégie de rétention avec du contenu sur place](#how-a-retention-policy-works-with-content-in-place) sur cette page.
  
De plus, certaines organisations doivent se conformer à des réglementations telles que celles de l’organisme fédéral américain de réglementation et de contrôle des marchés financiers (SEC), règlement 17A -4. Le présent règlement exige que lorsqu’une stratégie de rétention est activée, elle ne peut pas être désactivée ou rendue moins restrictive. Pour remplir cette obligation, vous pouvez utiliser le **Verrouillage de conservation**. Une fois la stratégie de rétention verrouillée, personne (pas même l'administrateur) ne peut la désactiver ni la rendre moins restrictive. Pour plus d’informations, voir la section [Utiliser le verrouillage de conservation pour se conformer aux exigences réglementaires](#use-preservation-lock-to-comply-with-regulatory-requirements) sur cette page.

## <a name="how-a-retention-policy-works-with-content-in-place"></a>Fonctionnement d’une stratégie de rétention avec du contenu sur place

Lorsque vous incluez un emplacement tel qu’un site ou une boîte aux lettres dans une stratégie de rétention, le contenu reste dans son emplacement d’origine. Les utilisateurs peuvent continuer à travailler avec leurs documents ou la messagerie comme si rien n’avait changé. Toutefois, s’ils modifient ou suppriment le contenu qui est inclus dans la stratégie de rétention, une copie du contenu est conservée, tel qu’il était lorsque vous avez appliqué la stratégie de rétention.
  
- Pour les sites SharePoint et OneDrive : la copie est conservée dans la bibliothèque de **Conservation et préservation**. Veuillez noter que la bibliothèque de conservation et de préservation des documents utilise un quota de stockage pour le site.

- Pour les messages électroniques et les dossiers publics : la copie est conservée dans le dossier **Éléments récupérables**. 

- Pour le contenu Teams : la copie est conservée dans le dossier Exchange **Éléments récupérables**.

- Pour les groupes Microsoft 365 ([anciennement groupes Office 365](https://techcommunity.microsoft.com/t5/microsoft-365-blog/office-365-groups-will-become-microsoft-365-groups/ba-p/1303601)) : 
    - La boîte aux lettres du groupe est conservée dans le dossier Exchange **Éléments récupérables**.
    - Tout contenu de site est conservé dans la bibliothèque de **Conservation et préservation**.

> [!NOTE]
> La bibliothèque de Conservation et préservation utilise un espace de stockage qui n’est pas exempté du quota de stockage d’un site. Il se peut que vous deviez augmenter votre espace de stockage lorsque vous utilisez des stratégies de rétention pour SharePoint et les groupes Microsoft 365.
> 
Ces emplacements sécurisés et le contenu conservé ne sont pas visibles pour la plupart des utilisateurs. Avec une stratégie de rétention, les personnes n’ont même pas besoin de savoir que leur contenu est soumis à la stratégie.

Pour plus d’informations sur le fonctionnement des stratégies de rétention avec différentes charges de travail, consultez les articles suivants :

- [En savoir plus sur les stratégies de rétention dans SharePoint et OneDrive](retention-policies-sharepoint.md)
- [En savoir plus sur les stratégies de rétention dans Microsoft Teams](retention-policies-teams.md)
- [En savoir plus sur les stratégies de rétention dans Exchange](retention-policies-exchange.md)

## <a name="the-principles-of-retention-or-what-takes-precedence"></a>Principes de rétention et priorité

Il est possible, voire probable, que diverses stratégies de rétention soient appliquées à du contenu, chacune étant associée à une action (conserver, supprimer ou conserver puis supprimer) et à une période de rétention différentes. Quelle stratégie est prioritaire ? Au niveau le plus élevé, soyez certain que le contenu conservé par une stratégie de rétention ne peut pas être supprimé définitivement par une autre.
  
![Diagramme des principes de rétention](../media/1693d6ec-b340-4805-9da3-89aa41bc6afb.png)
  
Pour comprendre comment les différentes stratégies de rétention s’appliquent au contenu, prenez en compte les principes de rétention suivants :
  
1. **La rétention prend le pas sur la suppression.** Supposons qu’une stratégie de rétention est configurée pour supprimer les messages Exchange au bout de trois ans, et qu’une autre stratégie de rétention est configurée pour conserver les messages Exchange pendant cinq ans avant de les supprimer. Tout le contenu atteignant l’âge de trois ans est supprimé et masqué à la vue des utilisateurs, mais reste conservé dans le dossier Éléments récupérables jusqu’à ce qu’il atteigne l’âge de cinq ans, moment auquel il est définitivement supprimé. 
    
2. **La période de rétention la plus longue l’emporte.** Si du contenu est soumis à plusieurs stratégies de rétention, il est conservé jusqu’à la fin de la période de rétention la plus longue. 
    
3. **L’inclusion explicite prend le pas sur l’inclusion implicite** Voici ce que cela signifie : 
    
    1. Si une étiquette de rétention avec des paramètres de rétention est attribuée manuellement par un utilisateur à un élément tel qu’un message Exchange ou un document OneDrive, cette étiquette de rétention l’emporte sur toute stratégie de rétention appliquée au niveau du site ou de la boîte aux lettres, ainsi que sur une étiquette de rétention par défaut attribuée par la bibliothèque de documents. Par exemple, si l’étiquette de rétention explicite est configurée pour conserver le contenu pendant une période de rétention de 10 ans, tandis que la stratégie de rétention appliquée au site est configurée pour conserver le contenu pendant une période de rétention de cinq ans, l’étiquette de rétention est prioritaire. Les étiquettes de rétention d’application automatique sont considérées comme implicites, plutôt qu’explicites, car Microsoft 365 les applique automatiquement.
    
    2. Si une stratégie de rétention inclut un emplacement spécifique, tel que la boîte aux lettres d’un utilisateur spécifique ou compte OneDrive, cette stratégie de rétention l’emporte sur une autre stratégie de rétention qui s’applique à l’ensemble des boîtes aux lettres ou des comptes OneDrive des utilisateurs, mais n’inclut pas spécifiquement la boîte aux lettres de l’utilisateur en question.
    
4. **La période de suppression la plus courte l’emporte** De même, si du contenu est soumis à plusieurs stratégies de rétention qui suppriment du contenu sans aucune période de rétention, celui-ci est supprimé à la fin de la période de rétention la plus courte. 
    
Notez que les principes de rétention opèrent comme un flux de partage du haut vers le bas : si les règles appliquées par toutes les stratégies de rétention ou étiquettes de rétention sont identiques sur un même niveau, le flux passe au niveau inférieur pour déterminer la règle prioritaire à appliquer.
  
Enfin, une stratégie de rétention ou une étiquette de rétention ne peut pas supprimer définitivement du contenu en attente pour eDiscovery. Une fois cette conservation levée, le contenu est de nouveau éligible pour le processus de nettoyage décrit ci-dessus.

## <a name="use-preservation-lock-to-comply-with-regulatory-requirements"></a>Utiliser le verrouillage de conservation pour se conformer aux exigences réglementaires.

Certaines organisations doivent peut-être respecter des règles définies par des organismes de réglementation, comme la règle 17a-4 de la SEC (Securities and Exchange Commission), stipulant qu'après l’activation d’une stratégie de rétention, celle-ci ne peut pas être désactivée ni rendue moins restrictive. 

Le verrouillage de conservation permet à votre organisation de répondre à ces exigences réglementaires, car il verrouille une stratégie de rétention pour que personne, y compris l’administrateur, ne puisse désactiver la stratégie ou la rendre moins restrictive.
  
Lorsqu’une stratégie de rétention est verrouillée :

- Personne ne peut la désactiver
- Vous pouvez ajouter des emplacements, mais pas les supprimer 
- Le contenu soumis à la stratégie ne peut pas être modifié ou supprimé pendant la période de rétention
- Vous pouvez prolonger une période de rétention, mais pas la réduire

En bref, une stratégie de rétention verrouillée peut être accrue ou étendue, mais pas réduite ni désactivée.
  
> [!IMPORTANT]
> Avant de verrouiller une stratégie de rétention, il est essentiel de comprendre l’impact et de confirmer qu’il est exigé que votre organisation respecte des exigences de conformité.

## <a name="releasing-a-retention-policy"></a>Publication d’une stratégie de rétention

La fourniture de votre stratégie de rétention n’offrant pas de verrouillage de conservation, vous pouvez désactiver ou supprimer une stratégie de rétention à tout moment. 

Lorsque vous procédez de la sorte, le contenu SharePoint ou OneDrive conservé dans la bibliothèque de conservation n’est pas immédiatement supprimé définitivement. Au lieu de cela, pour éviter la perte accidentelle de données, il existe une période de grâce de 30 jours pendant laquelle l’expiration du contenu de cette stratégie ne se produit pas dans la bibliothèque de conservation de conservation, afin que vous puissiez restaurer tout contenu à partir de cet emplacement, le cas échéant. De plus, vous ne pouvez pas supprimer manuellement ce contenu au cours de la période de grâce.

Vous pouvez réactiver la stratégie de rétention pendant la période de grâce et aucun contenu ne sera supprimé pour cette stratégie.

Cette période de grâce de 30 jours dans SharePoint et OneDrive correspond à un délai de 30 jours dans Exchange. Pour des informations supplémentaires, consultez [Gestion des boîtes aux lettres avec période de grâce](identify-a-hold-on-an-exchange-online-mailbox.md#managing-mailboxes-on-delay-hold).

## <a name="use-a-retention-policy-instead-of-older-features"></a>Utilisation d’une stratégie de rétention au lieu d’anciennes fonctionnalités

Une stratégie de rétention unique peut s’appliquer facilement à l’ensemble d’une organisation et à des emplacements entiers dans Microsoft 365, notamment Exchange Online, SharePoint Online, OneDrive et Groupes Microsoft 365. Si vous devez conserver ou supprimer du contenu n’importe où dans Microsoft 365, nous vous recommandons d’utiliser une stratégie de rétention et, de manière facultative, de la compléter avec des [étiquettes de rétention](labels.md).
  
Si vous avez déjà utilisé d’autres configurations pour conserver ou supprimer du contenu dans Microsoft 365, celles-ci continueront à fonctionner en parallèle avec les stratégies de rétention et les étiquettes de rétention. Toutefois, nous vous recommandons d’utiliser à l’avenir les stratégies de rétention et les étiquettes de rétention à la place. Elles vous fournissent un mécanisme unique pour gérer de manière centralisée la rétention et la suppression de contenu dans Microsoft 365.

Les fonctionnalités plus anciennes que vous avez peut-être utilisées sont les suivantes :
  
**Anciennes fonctionnalités dans Exchange Online :**

- [Gestion des cas eDiscovery dans le Centre de sécurité &amp; conformité Office 365](https://docs.microsoft.com/microsoft-365/compliance/get-started-core-ediscovery) (conservation eDiscovery) 
    
- [Conservation inaltérable et conservation pour litige](https://go.microsoft.com/fwlink/?linkid=846124) (conservation eDiscovery) 

- [Comment identifier le type de conservation placé sur une boîte aux lettres Exchange Online](identify-a-hold-on-an-exchange-online-mailbox.md)
    
- [Balises de rétention et stratégies de rétention](https://go.microsoft.com/fwlink/?linkid=846125), aussi appelées [gestion des enregistrements de messagerie (MRM)](https://go.microsoft.com/fwlink/?linkid=846126) (suppression uniquement)
    
**Anciennes fonctionnalités dans SharePoint et OneDrive :**

- [Gestion des cas eDiscovery dans le Centre de sécurité &amp; conformité Office 365](https://docs.microsoft.com/microsoft-365/compliance/get-started-core-ediscovery) (conservation eDiscovery) 
    
- [Ajout du contenu à un incident et placement des sources en conservation dans le centre eDiscovery](https://docs.microsoft.com/SharePoint/governance/add-content-to-a-case-and-place-sources-on-hold-in-the-ediscovery-center) (conservation eDiscovery) 
    
- [Stratégies de suppression des documents](https://support.office.com/article/Create-a-document-deletion-policy-in-SharePoint-Server-2016-4fe26e19-4849-4eb9-a044-840ab47458ff) (suppression uniquement)
    
- [Configuration en place de gestion des enregistrements](https://support.office.com/article/7707a878-780c-4be6-9cb0-9718ecde050a) (rétention uniquement) 
    
- [Utilisation de stratégies pour la fermeture et la suppression de sites](https://support.microsoft.com/fr-FR/office/use-policies-for-site-closure-and-deletion-a8280d82-27fd-48c5-9adf-8a5431208ba5) (suppression uniquement) 
    
- [Stratégies de gestion des informations](intro-to-info-mgmt-policies.md) (suppression uniquement)
     
Si vous avez déjà utilisé des conservations eDiscovery à des fins de gouvernance des informations, pour une conformité proactive, utilisez une stratégie de rétention à la place. Utilisez eDiscovery pour les conservations uniquement.
  
### <a name="retention-policies-and-sharepoint-content-type-policies-or-information-management-policies"></a>Stratégies de rétention, stratégies de type de contenu SharePoint ou stratégies de gestion des informations

Si vous avez configuré des sites SharePoint pour des stratégies de type de contenu ou des stratégies de gestion des informations afin de conserver du contenu pour une liste ou une bibliothèque, ces stratégies sont ignorées tant qu’une stratégie de rétention est en vigueur. 
  
### <a name="preservation-policies-are-converted-to-retention-policies"></a>Les stratégies de conservation sont converties en stratégies de rétention

Si vous utilisiez une stratégie de conservation pour conserver des données dans des boîtes aux lettres, des sites OneDrive ou SharePoint ou des dossiers publiques : celle-ci a été automatiquement convertie en stratégie de rétention qui utilise uniquement l’action de conservation : la stratégie ne supprimera pas le contenu. Aucune modification n’est nécessaire de votre part pour obtenir le même résultat que votre stratégie de conservation configurée.

Vous trouverez des stratégies de conservation configurées sur la page **Stratégies** du [Centre de conformité Microsoft 365](https://compliance.microsoft.com/) ou sur la page**Rétention** sous **Gouvernance des Informations** du [Centre de sécurité &amp; et de conformité](https://protection.office.com/). Vous pouvez modifier une stratégie de conservation afin de changer la période de rétention, mais vous ne pouvez pas apporter d’autres modifications ; par exemple, vous ne pouvez pas ajouter ou supprimer des emplacements. 


## <a name="related-information"></a>Informations connexes

- [Créer et configurer des stratégies de rétention](create-retention-policies.md)
- [Découvrir les étiquettes de rétention](labels.md)
- [Limites de SharePoint Online](https://docs.microsoft.com/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits)
- [Limites et spécifications de Microsoft Teams](https://docs.microsoft.com/microsoftteams/limits-specifications-teams) 
- [Se conformer à la réglementation SEC Rule 17 a-4](use-exchange-online-to-comply-with-sec-rule-17a-4.md)
