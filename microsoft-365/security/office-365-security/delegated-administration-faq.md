---
title: FAQ sur l'administration déléguée
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 8/28/2019
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.assetid: d6a87ce8-2c22-433a-b430-5eab14f6afdc
description: Cette rubrique fournit des questions fréquemment posées et des réponses pour les partenaires et les revendeurs Microsoft qui souhaitent effectuer des tâches d’administration déléguées, y compris la possibilité de gérer Exchange Online Protection (EOP) pour d’autres clients (sociétés).
ms.openlocfilehash: b79c0aba026a8d59aac338ceac0f1c4a60d71c4d
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43637651"
---
# <a name="delegated-administration-faq"></a>FAQ sur l’administration déléguée

Cette rubrique fournit des questions fréquemment posées et des réponses pour les partenaires et les revendeurs Microsoft qui souhaitent effectuer des tâches d’administration déléguées, y compris la possibilité de gérer Exchange Online Protection (EOP) pour d’autres clients (sociétés).

**Q. Je suis revendeur et je dois gérer les locataires de mon client. Comment cela fonctionne-t-il ?**

A. Si vous êtes un partenaire ou un revendeur Microsoft et que vous êtes inscrit en tant que conseiller Microsoft, vous pouvez demander l’autorisation d’administrer son client au sein du centre d’administration. Il s’agit de l’administration déléguée, qui vous permet de gérer son client Microsoft 365 (y compris les paramètres EOP) comme si vous étiez administrateur au sein de son organisation. Elle vous permet de gérer son locataire Office 365 (notamment les paramètres EOP) comme si vous étiez administrateur au sein de son organisation Les étapes permettant d'effectuer une administration déléguée sont les suivantes :

1. Inscrivez-vous pour devenir [partenaire Microsoft Office 365](https://aka.ms/cloudbenefits).

2. Inscrivez-vous à l’administration déléguée. Avant que vous puissiez administrer le compte d'un client, celui-ci doit vous fournir les autorisations d'administrateur délégué. Pour obtenir leur approbation, vous devez d'abord [leur envoyer une offre d'administration déléguée](https://support.office.com/article/26530dc0-ebba-415b-86b1-b55bc06b073e). (Vous pouvez également proposer l'administration déléguée à votre client ultérieurement.)

3. Créez le compte d’administrateur délégué en suivant les étapes décrites dans [Ajouter, modifier ou supprimer un partenaire conseiller d’abonnement](https://docs.microsoft.com/office365/admin/misc/add-partner).

Pour plus d’informations sur la configuration de l’administration déléguée, reportez-vous à [partenaires : créer votre entreprise et administrer votre abonnement partenaire](https://support.office.com/article/30dd1681-47e0-4cbc-abfe-a222cd111319) .

**Q. Je suis un client, pas un revendeur, comment puis-je configurer un administrateur délégué pour mes sous-locataires ?**

R. Pour le moment, l'administration déléguée est uniquement disponible pour les revendeurs et les partenaires. Cependant, nous avons fourni un exemple de script Windows PowerShell qui vous aidera à appliquer des stratégies à vos sous-locataires (entreprises). Pour plus d'informations, voir [Exemple de script pour l'application de paramètres EOP à plusieurs locataires](sample-script-for-applying-eop-settings-to-multiple-tenants.md).

**Q. Puis-je empêcher mon administration de sous-locataires de modifier ma stratégie ?**

A. Microsoft 365 ne dispose actuellement pas de cette fonctionnalité.

**Q. Puis-je disposer de la création de rapports consolidés dans l'ensemble de mes sous-locataires ?**

R. La création de rapports consolidés dans les sociétés que vous gérez n’est pas disponible pour les rapports du centre d’administration 365 de Microsoft pour le moment. Toutefois, vous pouvez le faire à l’aide de [Microsoft Graph](https://docs.microsoft.com/graph/overview).
