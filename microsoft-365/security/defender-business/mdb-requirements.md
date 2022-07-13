---
title: Configuration requise pour Microsoft Defender pour entreprises
description: Microsoft Defender pour entreprises la configuration requise pour les licences, le matériel et les logiciels
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 1114bebe4b57f89989b0e21a3d73a72fd1b3e99e
ms.sourcegitcommit: fa90763559239c4c46c5e848939126763879d8e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/13/2022
ms.locfileid: "66772880"
---
# <a name="microsoft-defender-for-business-requirements"></a>exigences de Microsoft Defender pour entreprises

Cet article décrit les conditions requises pour Defender Entreprise.

## <a name="what-to-do"></a>Procédure

1. [Passez en revue les exigences et assurez-vous de les respecter](#review-the-requirements).
2. [Passez à vos étapes suivantes](#next-steps).


## <a name="review-the-requirements"></a>Consultez la configuration requise

Le tableau suivant répertorie les exigences de base dont vous avez besoin pour configurer et utiliser Defender entreprise.

| Conditions requises | Description |
|:---|:---|
| Abonnement | Microsoft 365 Business Premium ou Defender entreprise (autonome). Découvrez [comment obtenir Defender entreprise](get-defender-business.md).<p>Notez que si vous avez plusieurs abonnements, l’abonnement le plus élevé est prioritaire. Par exemple, si vous avez Microsoft Defender pour point de terminaison plan 2 (abonnement acheté ou d’essai) et que vous obtenez Defender entreprise, Defender pour point de terminaison Plan 2 est prioritaire. Dans ce cas, vous ne verrez pas l’expérience Defender entreprise. Découvrez [ce qui se passe si j’ai une combinaison d’abonnements Microsoft 365 Defender](mdb-faq.yml#what-happens-if-i-have-a-mix-of-microsoft-endpoint-security-subscriptions) ?  |
| Datacenter | L’un des emplacements de centre de données suivants : <ul><li>Union européenne</li><li>Royaume-Uni</li><li>États-Unis</li></ul> |
| Comptes d’utilisateur |<ul><li>Les comptes d’utilisateur sont créés dans le Centre d'administration Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com)).</li><li>Les licences pour Defender Entreprise (ou Microsoft 365 Business Premium) sont attribuées dans le Centre d'administration Microsoft 365.</li></ul>Pour obtenir de l’aide sur cette tâche, consultez [Ajouter des utilisateurs et attribuer des licences](mdb-add-users.md). |
| Autorisations  | Pour vous inscrire à Defender entreprise, vous devez être un Administration global.<p>Pour accéder au portail Microsoft 365 Defender, l’un des rôles suivants doit être attribué [aux utilisateurs dans Azure AD](mdb-roles-permissions.md) :<ul><li>Lecteur de sécurité</li><li>Administrateur de la sécurité</li><li>Administrateur global</li></ul>Pour en savoir plus, consultez [Rôles et autorisations dans Defender entreprise](mdb-roles-permissions.md). |
| Configuration requise pour le navigateur | Microsoft Edge ou Google Chrome |
| Système d’exploitation d’appareil client | Pour gérer les appareils dans le portail Microsoft 365 Defender, vos appareils doivent exécuter l’un des systèmes d’exploitation suivants : <ul><li>Windows 10 ou 11 Entreprises</li><li>Windows 10 ou 11 professionnels</li><li>Windows 10 ou 11 Entreprise</li><li>Mac (les trois versions les plus actuelles sont prises en charge)</li></ul><p>Vérifiez que [KB5006738](https://support.microsoft.com/topic/october-26-2021-kb5006738-os-builds-19041-1320-19042-1320-and-19043-1320-preview-ccbce6bf-ae00-4e66-9789-ce8e7ea35541) est installé sur les appareils Windows. <p>Si vous gérez déjà des appareils dans Microsoft Intune, vous pouvez continuer à utiliser le Centre d’administration Microsoft Endpoint Manager. Dans ce cas, les autres systèmes d’exploitation suivants sont pris en charge : <ul><li>iOS et iPadOS</li><li>Système d’exploitation Android</li></ul> |
| Configuration requise pour le serveur | Si vous envisagez d’intégrer une instance de Windows Server ou Linux Server, vous devez répondre aux exigences suivantes : <ul><li>Le paramètre **des fonctionnalités d’aperçu** est activé. Dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), accédez aux **fonctionnalités d’aperçu** **des fonctionnalités** >  > **avancées générales** > **des** >  points de terminaison des paramètres.</li><li>L’étendue de mise en œuvre de Windows Server est activée. Dans le portail Microsoft 365 Defender, accédez à **l’étendue d’application** de **la gestion de la configuration** >  des **paramètres** > **des points de terminaison** > . Sélectionnez **Utiliser MDE pour appliquer les paramètres de configuration de sécurité à partir de MEM**, sélectionnez  **Windows Server**, puis **sélectionnez Enregistrer**.</li><li>Les points de terminaison Linux Server répondent aux [conditions préalables pour Microsoft Defender pour point de terminaison sur Linux](../defender-endpoint/microsoft-defender-endpoint-linux.md#prerequisites).</li></ul> |

> [!NOTE]
> [Azure Active Directory (Azure AD)](/azure/active-directory/fundamentals/active-directory-whatis) est utilisé pour gérer les autorisations utilisateur et les groupes d’appareils. Azure AD est inclus dans votre abonnement Defender entreprise. 
> - Si vous n’avez pas d’abonnement Microsoft 365 avant de commencer votre version d’évaluation, Azure AD est approvisionné pour vous pendant le processus d’activation. 
> - Si vous avez un autre abonnement Microsoft 365 lorsque vous démarrez votre version d’évaluation de Defender Entreprise, vous pouvez utiliser votre service Azure AD existant. 
> - Si vous utilisez [Microsoft 365 Business Premium](../../business/index.yml) lorsque vous démarrez votre version d’évaluation de Defender Entreprise, vous avez la possibilité de gérer vos appareils à l’aide de Intune.

## <a name="next-steps"></a>Prochaines étapes

Passez à [l’étape 2 : Attribuer des rôles et des autorisations dans Defender entreprise](mdb-roles-permissions.md).
 
