---
title: Préparer des ressources d’impression pour le Bureau géré Microsoft
description: Étapes importantes pour s’assurer que l’impression fonctionne correctement
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
manager: laurawi
ms.topic: article
ms.openlocfilehash: b6e809505fed8b1f84eb502dc08751ad1f0b587c
ms.sourcegitcommit: 83a40facd66e14343ad3ab72591cab9c41ce6ac0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2021
ms.locfileid: "49841398"
---
# <a name="prepare-printing-resources-for-microsoft-managed-desktop"></a>Préparer des ressources d’impression pour le Bureau géré Microsoft

Lorsque vous êtes prêt à vous inscrire au Bureau géré Microsoft, vous devez évaluer vos besoins d’impression et déterminer l’approche qui convient à votre environnement. Vous avez trois options :
 
- Déployez la solution d’impression universelle Microsoft pour faciliter la découverte des imprimantes pour les appareils Bureau géré Microsoft. Pour plus d’informations, voir [Qu’est-ce que l’impression universelle](https://docs.microsoft.com/universal-print/fundamentals/universal-print-whatis).
- Déployez les imprimantes directement à l’aide d’un script PowerShell personnalisé. Suivez les étapes de la section Configurer [les imprimantes locales.](#set-up-local-printers)
- Utilisez une solution d’impression cloud non Microsoft compatible avec les appareils Windows 10 joints à un domaine Azure Active Directory. La solution doit répondre aux exigences logicielles du Bureau géré Microsoft. Pour plus d’informations, consultez [la version requise de l’application Bureau géré Microsoft.](../service-description/mmd-app-requirements.md)
 
Dans tous les cas, si les pilotes d’imprimante ne sont pas disponibles à partir de Microsoft Update ou du Microsoft Store, vous devez les obtenir vous-même et les empaquetés pour le déploiement sur vos appareils de bureau géré Microsoft avec Microsoft Intune. Pour plus d’informations, [voir Intune Autonome - Gestion des applications Win32](https://docs.microsoft.com/mem/intune/apps/apps-win32-app-management)

## <a name="set-up-local-printers"></a>Configurer des imprimantes locales

Si vous avez décidé de déployer des imprimantes à l’aide d’un script PowerShell personnalisé et que vous avez préparé les ressources d’impression, suivez ces étapes pour déployer des imprimantes partagées :

1.  Accédez au portail Bureau géré Microsoft.
2.  Envoyez une demande  de déploiement d’imprimante étiquetée dans la section > **support technique du** portail d’administration, en fournissant les informations suivantes :
    - Tous les chemins UNC vers les emplacements d’imprimante partagés qui devront être déployés pour les appareils bureau géré Microsoft
    - Groupes d’utilisateurs qui nécessitent l’accès à ces imprimantes partagées
3.  À l’aide du portail d’administration, nous allons vous faire savoir que la demande est terminée. Initialement, nous allons uniquement déployer la configuration sur les appareils du groupe de déploiement Test.
4.  Vous devez tester et vérifier si la configuration fonctionne comme prévu. Répondez à **l’aide de l’onglet Discussion** dans la demande de support pour nous faire savoir quand vous avez terminé vos tests.
5.  Nous allons ensuite déployer la configuration sur les autres groupes de déploiement.
