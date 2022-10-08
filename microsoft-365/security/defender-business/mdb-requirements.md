---
title: Configuration requise pour Microsoft Defender pour entreprises
description: Microsoft Defender pour entreprises la configuration requise pour les licences, le matériel et les logiciels
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.service: microsoft-365-security
ms.subservice: mdb
ms.localizationpriority: medium
ms.date: 09/14/2022
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- m365-security
- m365solution-mdb-setup
- highpri
- tier1
ms.openlocfilehash: 549f1c2151d6fe38f81a5d34d873df7d800f48c8
ms.sourcegitcommit: 0283c436f3ba61a708b52b57a1955f5ea74376a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2022
ms.locfileid: "68096388"
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
| Abonnement | Microsoft 365 Business Premium ou Defender entreprise (autonome). Découvrez [comment obtenir Defender entreprise](get-defender-business.md).  |
| Datacenter | L’un des emplacements de centre de données suivants : <ul><li>Union européenne</li><li>Royaume-Uni</li><li>États-Unis</li></ul> |
| Comptes d’utilisateur |<ul><li>Les comptes d’utilisateur sont créés dans le Centre d'administration Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com)).</li><li>Les licences pour Defender Entreprise (ou Microsoft 365 Business Premium) sont attribuées dans le Centre d'administration Microsoft 365.</li></ul>Pour obtenir de l’aide sur cette tâche, consultez [Ajouter des utilisateurs et attribuer des licences](mdb-add-users.md). |
| Autorisations  | Pour vous inscrire à Defender entreprise, vous devez être un Administration global.<br/><br/>Pour accéder au portail Microsoft 365 Defender, l’un des rôles suivants doit être attribué [aux utilisateurs dans Azure AD](mdb-roles-permissions.md) :<ul><li>Lecteur de sécurité</li><li>Administrateur de la sécurité</li><li>Administrateur global</li></ul>Pour en savoir plus, consultez [Rôles et autorisations dans Defender entreprise](mdb-roles-permissions.md). |
| Configuration requise pour le navigateur | Microsoft Edge ou Google Chrome |
| Système d’exploitation d’appareil client | Pour gérer les appareils dans le portail Microsoft 365 Defender, vos appareils doivent exécuter l’un des systèmes d’exploitation suivants : <ul><li>Windows 10 ou 11 Entreprises</li><li>Windows 10 ou 11 professionnels</li><li>Windows 10 ou 11 Entreprise</li><li>Mac (les trois versions les plus actuelles sont prises en charge)</li></ul>Vérifiez que [KB5006738](https://support.microsoft.com/topic/october-26-2021-kb5006738-os-builds-19041-1320-19042-1320-and-19043-1320-preview-ccbce6bf-ae00-4e66-9789-ce8e7ea35541) est installé sur les appareils Windows. <br/><br/>Si vous gérez déjà des appareils dans Microsoft Intune, vous pouvez continuer à utiliser le Centre d’administration Microsoft Endpoint Manager.<sup> Dans[](#fn1)</sup> ce cas, les autres systèmes d’exploitation suivants sont pris en charge : <ul><li>iOS et iPadOS</li><li>Système d’exploitation Android</li></ul> |
| Configuration requise pour le serveur | Si vous envisagez d’intégrer une instance de Windows Server ou Linux Server, vous devez répondre aux exigences suivantes : <ul><li>Le paramètre **des fonctionnalités en préversion** est activé. Dans le portail Microsoft 365 Defender ( [https://security.microsoft.com](https://security.microsoft.com)), accédez à **Paramètres** > **Endpoints** > **Général** > **Fonctions avancées** > **Fonctions de prévisualisation**.</li><li>L’étendue de mise en œuvre de Windows Server est activée. Dans le portail Microsoft 365 Defender, accédez à **l’étendue d’application** de **la gestion de la configuration** >  des **paramètres** > **des points de terminaison** > . Sélectionnez **Utiliser MDE pour appliquer les paramètres de configuration de sécurité à partir de MEM**, sélectionnez  **Windows Server**, puis **sélectionnez Enregistrer**.</li><li>Les points de terminaison Linux Server répondent aux [conditions préalables pour Microsoft Defender pour point de terminaison sur Linux](../defender-endpoint/microsoft-defender-endpoint-linux.md#prerequisites).</li></ul> |

(<a id="fn1">1</a>) Microsoft Intune n’est pas inclus dans la version autonome de Defender entreprise. Intune peut être ajouté à Defender Entreprise. Intune est inclus dans Microsoft 365 Business Premium.

> [!NOTE]
> [Azure Active Directory (Azure AD)](/azure/active-directory/fundamentals/active-directory-whatis) est utilisé pour gérer les autorisations utilisateur et les groupes d’appareils. Azure AD est inclus dans votre abonnement Defender entreprise. 
> - Si vous n’avez pas d’abonnement Microsoft 365 avant de commencer votre version d’évaluation, Azure AD est approvisionné pour vous pendant le processus d’activation. 
> - Si vous avez un autre abonnement Microsoft 365 lorsque vous démarrez votre version d’évaluation de Defender Entreprise, vous pouvez utiliser votre service Azure AD existant. 

## <a name="next-steps"></a>Prochaines étapes

Passez à [l’étape 2 : Attribuer des rôles et des autorisations dans Defender entreprise](mdb-roles-permissions.md).
 
