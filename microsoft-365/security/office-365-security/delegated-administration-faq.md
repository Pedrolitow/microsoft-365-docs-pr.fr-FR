---
title: FAQ sur l'administration déléguée
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.assetid: d6a87ce8-2c22-433a-b430-5eab14f6afdc
ms.custom:
- seo-marvel-apr2020
description: Cette rubrique fournit des questions fréquentes et des réponses pour les partenaires et les revendeurs Microsoft qui souhaitent effectuer des tâches d’administration Microsoft 365 déléguées.
ms.openlocfilehash: d1522973292b290fd9f66f534ca23aeaa55ee756
ms.sourcegitcommit: 93c0088d272cd45f1632a1dcaf04159f234abccd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "44209522"
---
# <a name="delegated-administration-faq"></a>FAQ sur l’administration déléguée

Cette rubrique fournit des questions fréquemment posées et des réponses pour les partenaires et les revendeurs Microsoft qui souhaitent effectuer des tâches d’administration déléguées, y compris la possibilité de gérer Exchange Online Protection (EOP) pour d’autres clients (sociétés).

## <a name="im-a-reseller-and-i-need-to-manage-my-customers-tenants-how-does-this-work"></a>Je suis revendeur et je dois gérer les clients de mon client ; Comment cela fonctionne-t-il ?

Si vous êtes un partenaire ou un revendeur Microsoft et que vous êtes inscrit en tant que conseiller Microsoft, vous pouvez demander l’autorisation d’administrer son client au sein du centre d’administration. Il s’agit de l’administration déléguée, qui vous permet de gérer son client Microsoft 365 (y compris les paramètres EOP) comme si vous étiez administrateur au sein de son organisation. Elle vous permet de gérer son locataire Office 365 (notamment les paramètres EOP) comme si vous étiez administrateur au sein de son organisation Les étapes permettant d'effectuer une administration déléguée sont les suivantes :

1. Inscrivez-vous pour devenir [partenaire Microsoft Office 365](https://aka.ms/cloudbenefits).

2. Inscrivez-vous à l’administration déléguée. Avant que vous puissiez administrer le compte d'un client, celui-ci doit vous fournir les autorisations d'administrateur délégué. Pour obtenir leur approbation, vous devez d'abord [leur envoyer une offre d'administration déléguée](https://support.microsoft.com/office/26530dc0-ebba-415b-86b1-b55bc06b073e). (Vous pouvez également proposer l'administration déléguée à votre client ultérieurement.)

3. Créez le compte d’administrateur délégué en suivant les étapes décrites dans [Ajouter, modifier ou supprimer un partenaire conseiller d’abonnement](https://docs.microsoft.com/office365/admin/misc/add-partner).

Pour plus d’informations sur la configuration de l’administration déléguée, reportez-vous à [partenaires : créer votre entreprise et administrer votre abonnement partenaire](https://support.office.com/article/30dd1681-47e0-4cbc-abfe-a222cd111319) .

## <a name="im-a-customer-not-a-reseller-how-can-set-up-delegated-administrator-for-my-sub-tenants"></a>Je suis un client, et non un revendeur, comment configurer un administrateur délégué pour mes sous-clients ?

Pour le moment, l'administration déléguée est uniquement disponible pour les revendeurs et les partenaires. Cependant, nous avons fourni un exemple de script Windows PowerShell qui vous aidera à appliquer des stratégies à vos sous-locataires (entreprises). Pour plus d'informations, voir [Exemple de script pour l'application de paramètres EOP à plusieurs locataires](sample-script-for-applying-eop-settings-to-multiple-tenants.md).

## <a name="can-i-prevent-my-sub-tenant-admin-from-modifying-my-policy"></a>Puis-je empêcher mon administration de sous-locataires de modifier ma stratégie ?

Microsoft 365 ne dispose actuellement pas de cette fonctionnalité.

## <a name="can-i-get-consolidated-reporting-across-all-of-my-sub-tenants"></a>Puis-je disposer de la création de rapports consolidés dans l’ensemble de mes sous-locataires ?

La création de rapports consolidés dans les sociétés que vous gérez n’est pas disponible pour les rapports du centre d’administration 365 de Microsoft pour le moment. Toutefois, vous pouvez le faire à l’aide de [Microsoft Graph](https://docs.microsoft.com/graph/overview).
