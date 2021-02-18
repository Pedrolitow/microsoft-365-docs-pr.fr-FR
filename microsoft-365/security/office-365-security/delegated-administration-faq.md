---
title: FAQ sur l'administration déléguée
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: troubleshooting
localization_priority: Normal
ms.assetid: d6a87ce8-2c22-433a-b430-5eab14f6afdc
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent consulter les questions fréquemment posées et les réponses sur les tâches d’administration déléguées dans Microsoft 365 pour les partenaires et revendeurs Microsoft.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 971572f8bff80da6dd63bed8958112332292feb9
ms.sourcegitcommit: 786f90a163d34c02b8451d09aa1efb1e1d5f543c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/18/2021
ms.locfileid: "50288358"
---
# <a name="delegated-administration-faq"></a>FAQ sur l’administration déléguée

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Cet article fournit des questions fréquemment posées et des réponses sur les tâches d’administration déléguées dans Microsoft 365 pour les partenaires et revendeurs Microsoft. L’administration déléguée inclut la possibilité de gérer les paramètres Exchange Online Protection (EOP) pour d’autres clients (sociétés).

## <a name="im-a-reseller-and-i-need-to-manage-my-customer-tenants-how-does-this-work"></a>Je suis revendeur et je dois gérer mes clients. Comment cela fonctionne-t-il ?

Si vous êtes un partenaire ou un revendeur Microsoft et que vous vous êtes inscrit en tant que conseiller Microsoft, vous pouvez demander des fonctionnalités _d’administration_ déléguée dans l’organisation Microsoft 365 de votre client.

L’administration déléguée vous permet de gérer Microsoft 365 (y compris les paramètres EOP) comme si vous étiez un administrateur au sein de cette organisation. Les étapes de configuration de l’administration déléguée sont décrites dans la liste suivante :

1. Inscrivez-vous pour devenir [partenaire Microsoft Office 365](https://aka.ms/cloudbenefits).

2. Inscrivez-vous à l’administration déléguée. Avant de commencer à administrer le client d’un client, il doit vous autoriser en tant qu’administrateur délégué. Pour obtenir leur approbation, vous devez d'abord [leur envoyer une offre d'administration déléguée](https://support.microsoft.com/office/26530dc0-ebba-415b-86b1-b55bc06b073e). Vous pouvez également proposer une administration déléguée à votre client ultérieurement.

3. Créez le compte d’administrateur délégué à l’aide des étapes de [l’étape Ajouter, modifier ou supprimer un partenaire conseiller en abonnement.](../../admin/misc/add-partner.md)

Visitez [les partenaires : développez votre entreprise et administrez](https://support.microsoft.com/office/30dd1681-47e0-4cbc-abfe-a222cd111319) un abonnement partenaire pour plus d’informations sur la façon de configurer l’administration déléguée.

## <a name="im-a-customer-not-a-reseller-how-can-set-up-delegated-administrator-for-my-subtenants"></a>Je suis un client, pas un revendeur. Comment configurer un administrateur délégué pour mes sous-clients ?

L’administration déléguée est uniquement disponible pour les revendeurs et les partenaires. Toutefois, il existe un exemple de script PowerShell qui vous aidera à appliquer des stratégies à vos sous-traitants (sociétés). Pour plus d'informations, voir [Exemple de script pour l'application de paramètres EOP à plusieurs locataires](sample-script-for-applying-eop-settings-to-multiple-tenants.md).

## <a name="can-i-prevent-my-subtenant-admin-from-modifying-my-policy"></a>Puis-je empêcher mon administrateur de sous-site de modifier ma stratégie ?

Non. Microsoft 365 ne dispose pas actuellement de cette fonctionnalité.

## <a name="can-i-get-consolidated-reporting-across-all-of-my-subtenants"></a>Puis-je obtenir des rapports consolidés sur tous mes sous-traitants ?

Les rapports consolidés au sein des entreprises que vous gérez ne sont pas disponibles dans les rapports du Centre d’administration Microsoft 365. Toutefois, vous pouvez obtenir des rapports à [l’aide de Microsoft Graph.](https://docs.microsoft.com/graph/overview)
