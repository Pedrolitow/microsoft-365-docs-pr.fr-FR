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
ms.service: O365-seccomp
localization_priority: Normal
ms.assetid: d6a87ce8-2c22-433a-b430-5eab14f6afdc
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent consulter les questions fréquemment posées et les réponses sur les tâches d’administration déléguée dans Microsoft 365 pour les partenaires et les revendeurs Microsoft.
ms.openlocfilehash: 3efadc8793778bfabe10922e8e29044747d60ad0
ms.sourcegitcommit: 787b198765565d54ee73972f664bdbd5023d666b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "46866694"
---
# <a name="delegated-administration-faq"></a>FAQ sur l’administration déléguée

Cet article fournit des questions fréquemment posées et des réponses sur les tâches d’administration déléguée dans Microsoft 365 pour les partenaires et les revendeurs Microsoft. L’administration déléguée offre la possibilité de gérer les paramètres d’Exchange Online Protection (EOP) pour d’autres clients (sociétés).

## <a name="im-a-reseller-and-i-need-to-manage-my-customer-tenants-how-does-this-work"></a>Je suis revendeur et je dois gérer mes locataires de clients. Comment cela fonctionne-t-il ?

Si vous êtes un partenaire ou un revendeur Microsoft et que vous êtes inscrit en tant que conseiller Microsoft, vous pouvez demander des fonctionnalités d' _administration déléguée_ dans l’organisation Microsoft 365 de votre client.

L’administration déléguée vous permet de gérer Microsoft 365 (y compris les paramètres EOP) comme si vous étiez administrateur au sein de cette organisation. Les étapes de configuration de l’administration déléguée sont décrites dans la liste suivante :

1. Inscrivez-vous pour devenir [partenaire Microsoft Office 365](https://aka.ms/cloudbenefits).

2. Inscrivez-vous à l’administration déléguée. Avant de pouvoir commencer à administrer le client d’un client, il doit vous autoriser en tant qu’administrateur délégué. Pour obtenir leur approbation, vous devez d'abord [leur envoyer une offre d'administration déléguée](https://support.microsoft.com/office/26530dc0-ebba-415b-86b1-b55bc06b073e). Vous pouvez également proposer une administration déléguée à votre client ultérieurement.

3. Créez le compte d’administrateur délégué en suivant les étapes décrites dans [Ajouter, modifier ou supprimer un partenaire conseiller d’abonnement](https://docs.microsoft.com/microsoft-365/admin/misc/add-partner).

Pour plus d’informations sur la configuration de l’administration déléguée, reportez-vous à [partenaires : créer votre entreprise et administrer votre abonnement partenaire](https://support.microsoft.com/office/30dd1681-47e0-4cbc-abfe-a222cd111319) .

## <a name="im-a-customer-not-a-reseller-how-can-set-up-delegated-administrator-for-my-subtenants"></a>Je suis un client, et non un revendeur. Comment configurer l’administrateur délégué pour mes sous-clients ?

L’administration déléguée est uniquement disponible pour les revendeurs et les partenaires. Toutefois, il existe un exemple de script PowerShell qui vous aidera à appliquer des stratégies à vos sous-clients (sociétés). Pour plus d'informations, voir [Exemple de script pour l'application de paramètres EOP à plusieurs locataires](sample-script-for-applying-eop-settings-to-multiple-tenants.md).

## <a name="can-i-prevent-my-subtenant-admin-from-modifying-my-policy"></a>Puis-je empêcher mon administrateur de sous-client de modifier ma stratégie ?

Non. Microsoft 365 ne dispose actuellement pas de cette fonctionnalité.

## <a name="can-i-get-consolidated-reporting-across-all-of-my-subtenants"></a>Puis-je obtenir la création de rapports consolidés sur tous mes sous-clients ?

La création de rapports consolidés dans les sociétés que vous gérez n’est pas disponible dans les rapports du centre d’administration Microsoft 365. Toutefois, vous pouvez obtenir des rapports à l’aide de [Microsoft Graph](https://docs.microsoft.com/graph/overview).
