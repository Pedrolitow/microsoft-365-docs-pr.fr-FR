---
title: Vue d’ensemble des modèles prédéfinis dans Microsoft Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.custom: intro-overview
ms.service: microsoft-syntex
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Découvrez les modèles prédéfinis dans Microsoft Syntex.
ms.openlocfilehash: 0ec44b2f7b0b0360eedceadb71ddf9abdc6e2941
ms.sourcegitcommit: 87283bb02ca750286f7c069f811b788730ed5832
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68659146"
---
# <a name="overview-of-prebuilt-models-in-microsoft-syntex"></a>Vue d’ensemble des modèles prédéfinis dans Microsoft Syntex

En plus des [modèles personnalisés](model-types-overview.md#custom-models), Microsoft Syntex fournit des *modèles prédéfinis* pour automatiser l’extraction des informations.

Les modèles prédéfinis sont préconfigurés pour reconnaître les documents et les informations structurées dans les documents. Au lieu d’avoir à créer un modèle personnalisé à partir de zéro, vous pouvez itérer sur un modèle préentraîné existant pour ajouter des champs spécifiques qui répondent aux besoins de votre organisation. 

Les modèles prédéfinis utilisent la reconnaissance optique de caractères (OCR) combinée à des modèles deep learning pour identifier et extraire des champs de texte et de données prédéfinis communs à des types de documents spécifiques. Vous commencez par analyser l’un de vos fichiers par rapport au modèle prédéfini. Vous sélectionnez ensuite les champs détectés qui sont pertinents pour votre objectif. Si le modèle ne détecte pas les champs dont vous avez besoin, vous pouvez analyser à nouveau à l’aide d’un autre fichier.

Comme les autres modèles, les modèles prédéfinis sont créés et gérés dans le [centre de contenu](create-a-content-center.md). Lorsqu’il est appliqué à une bibliothèque de documents SharePoint, le modèle est associé à un type de contenu et comporte des colonnes pour stocker les informations extraites. 

Une fois que vous avez publié votre modèle, utilisez le centre de contenu pour l’appliquer à toute bibliothèque de documents SharePoint à laquelle vous avez accès.  

## <a name="available-prebuilt-models"></a>Modèles prédéfinis disponibles

Actuellement, deux modèles prédéfinis sont disponibles : [les factures](prebuilt-model-invoice.md) et [les reçus](prebuilt-model-receipt.md).

- Le *modèle de factures* analyse et extrait les informations clés des factures de vente. L’API analyse les factures dans différents formats et [extrait des informations clés sur les factures](/azure/applied-ai-services/form-recognizer/concept-invoice#field-extraction) , telles que le nom du client, l’adresse de facturation, la date d’échéance et le montant dû.

- Le *modèle de reçus* analyse et extrait les informations clés des reçus. L’API analyse les reçus imprimés et manuscrits et [extrait les informations de reçu clé](/azure/applied-ai-services/form-recognizer/concept-receipt#field-extraction) telles que le nom du commerçant, le numéro de téléphone du commerçant, la date de transaction, la taxe et le total de la transaction.

D’autres modèles prédéfinis seront disponibles dans les versions ultérieures.

## <a name="requirements"></a>Conditions requises

Pour plus d’informations sur les exigences à prendre en compte lors du choix de ce modèle, consultez [Configuration requise et limitations des modèles dans Microsoft Syntex](requirements-and-limitations.md). 

## <a name="see-also"></a>Voir aussi

[Utiliser un modèle prédéfini pour extraire des informations à partir de factures](prebuilt-model-invoice.md)

[Utiliser un modèle prédéfini pour extraire des informations des reçus](prebuilt-model-receipt.md)

 

