---
title: Préparer des ressources d’impression pour le Bureau géré Microsoft
description: Étapes importantes pour garantir le bon fonctionnement de l’impression
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
manager: laurawi
ms.topic: article
ms.openlocfilehash: 1588a2c91bcbe0bd381acb6be4f9bd5562810860
ms.sourcegitcommit: 126d22d8abd190beb7101f14bd357005e4c729f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2020
ms.locfileid: "46530246"
---
# <a name="prepare-printing-resources-for-microsoft-managed-desktop"></a>Préparer des ressources d’impression pour le Bureau géré Microsoft

Lorsque vous êtes prêt à vous inscrire dans le bureau géré Microsoft, vous devez évaluer vos besoins en matière d’impression et déterminer l’approche appropriée pour votre environnement. Trois options s’offrent à vous :
 
- Déployez la solution Microsoft hybride Cloud Print pour permettre aux appareils de bureau gérés Microsoft de découvrir facilement les imprimantes. Pour plus d’informations, consultez la rubrique [deploy Windows Server Hybrid Cloud Print](https://docs.microsoft.com/windows-server/administration/hybrid-cloud-print/hybrid-cloud-print-deploy).
- Déployer des imprimantes directement à l’aide d’un script PowerShell personnalisé. Suivez les étapes de la section [Configuration des imprimantes locales](#set-up-local-printers) pour effectuer cette opération.
- Utilisez une solution d’impression Cloud non Microsoft compatible avec les appareils Windows 10 qui sont joints à un domaine Azure Active Directory. La solution doit répondre à la configuration logicielle requise pour le bureau géré Microsoft. Pour plus d’informations, consultez la rubrique [conditions requises pour les applications de bureau géré Microsoft](../service-description/mmd-app-requirements.md).
 
Dans tous les cas, si les pilotes d’imprimante ne sont pas disponibles à partir de Microsoft Update ou de Microsoft Store, vous devrez les obtenir vous-même et les déployer sur vos appareils de bureau gérés Microsoft avec Microsoft Intune. Pour plus d’informations, consultez la rubrique [Intune standalone-Win32 App Management](https://docs.microsoft.com/mem/intune/apps/apps-win32-app-management)

## <a name="set-up-local-printers"></a>Configurer des imprimantes locales

Si vous avez décidé de déployer des imprimantes à l’aide d’un script PowerShell personnalisé et que vous avez préparé les ressources d’impression, procédez comme suit pour déployer les imprimantes partagées :

1.  Accédez au portail de bureau géré Microsoft.
2.  Soumettez une demande étiquetée *déploiement d’imprimante* dans la section prise en charge des **demandes de support >** du portail d’administration, en fournissant les informations suivantes :
    - Tous les chemins d’accès UNC aux emplacements d’imprimantes partagés qui devront être déployés pour les appareils de bureau gérés par Microsoft
    - Groupes d’utilisateurs qui ont besoin d’accéder à ces imprimantes partagées
3.  À l’aide du portail d’administration, nous vous informerons à la fin de la demande. À l’origine, nous allons déployer la configuration sur des appareils dans le groupe de déploiement de test.
4.  Vous devez tester et confirmer que la configuration fonctionne comme prévu. Répondez-y à l’aide de l’onglet **discussion** de la demande de support pour nous indiquer une fois que vous avez terminé vos tests.
5.  Nous allons ensuite déployer la configuration sur les autres groupes de déploiement.
