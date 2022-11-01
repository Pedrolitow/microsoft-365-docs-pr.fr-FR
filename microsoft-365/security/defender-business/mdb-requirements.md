---
title: Configuration requise pour Microsoft Defender pour entreprises
description: Microsoft Defender pour entreprises configuration requise pour les licences, le matériel et les logiciels
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.service: microsoft-365-security
ms.subservice: mdb
ms.localizationpriority: medium
ms.date: 11/01/2022
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- m365-security
- m365solution-mdb-setup
- highpri
- tier1
ms.openlocfilehash: 364c6181df1723ad553cfa6bb0eab39cf0cb7b2d
ms.sourcegitcommit: 0c72639cc3dc74667a6b14343d303f318e70d457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68804989"
---
# <a name="microsoft-defender-for-business-requirements"></a>Microsoft Defender pour entreprises conditions requises

Cet article décrit la configuration requise pour Defender entreprise.

## <a name="what-to-do"></a>Procédure

1. [Passez en revue les exigences et vérifiez que vous les respectez](#review-the-requirements).
2. [Passez aux étapes suivantes](#next-steps).


## <a name="review-the-requirements"></a>Consultez la configuration requise

Le tableau suivant répertorie les exigences de base dont vous avez besoin pour configurer et utiliser Defender pour les entreprises.

| Conditions requises | Description |
|:---|:---|
| Abonnement | Microsoft 365 Business Premium ou Defender for Business (autonome). Consultez [Comment obtenir Defender pour les entreprises](get-defender-business.md).  |
| Datacenter | L’un des emplacements de centre de données suivants : <ul><li>Union européenne</li><li>Royaume-Uni</li><li>États-Unis</li></ul> |
| Comptes d’utilisateur |<ul><li>Les comptes d’utilisateur sont créés dans le Centre d'administration Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com)).</li><li>Les licences pour Defender for Business (ou Microsoft 365 Business Premium) sont attribuées dans le Centre d'administration Microsoft 365.</li></ul>Pour obtenir de l’aide sur cette tâche, consultez [Ajouter des utilisateurs et attribuer des licences](mdb-add-users.md). |
| Autorisations  | Pour vous inscrire à Defender for Business, vous devez être Administration global.<br/><br/>Pour accéder au portail Microsoft 365 Defender, les utilisateurs doivent avoir l’un des [rôles suivants dans Azure AD](mdb-roles-permissions.md) attribués :<ul><li>Lecteur de sécurité</li><li>Administrateur de la sécurité</li><li>Administrateur global</li></ul>Pour plus d’informations, consultez [Rôles et autorisations dans Defender pour les entreprises](mdb-roles-permissions.md). |
| Configuration requise pour le navigateur | Microsoft Edge ou Google Chrome |
| Système d’exploitation de l’appareil client | Pour gérer des appareils dans le portail Microsoft 365 Defender, vos appareils doivent exécuter l’un des systèmes d’exploitation suivants : <ul><li>Windows 10 ou 11 Business</li><li>Windows 10 ou 11 Professionnel</li><li>Windows 10 ou 11 Entreprise</li><li>Mac (les trois versions les plus actuelles sont prises en charge)</li></ul>Vérifiez que [KB5006738](https://support.microsoft.com/topic/october-26-2021-kb5006738-os-builds-19041-1320-19042-1320-and-19043-1320-preview-ccbce6bf-ae00-4e66-9789-ce8e7ea35541) est installé sur les appareils Windows. <br/><br/>Si vous gérez déjà des appareils dans Microsoft Intune, vous pouvez continuer à utiliser le Centre d’administration Microsoft Endpoint Manager.<sup> [[1](#fn1)]</sup> Dans ce cas, les autres systèmes d’exploitation suivants sont pris en charge : <ul><li>iOS et iPadOS</li><li>Système d’exploitation Android</li></ul> |
| Configuration requise pour le serveur | Pour intégrer un appareil exécutant Windows Server ou Linux Server, vous aurez besoin d’une licence supplémentaire, telle que [Microsoft Defender pour entreprises serveurs](get-defender-business-servers.md) <sup>[[2](#fn2)]</sup> .<br/><br/>Les points de terminaison Windows Server doivent répondre aux [exigences de Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/minimum-requirements#hardware-and-software-requirements), et l’étendue d’application doit être activée.<ol><li>Dans le portail Microsoft 365 Defender, accédez à **Paramètres Points** >  de **terminaison** > **Gestion de la configuration** > **Étendue de mise en application**.</li><li>Sélectionnez **Utiliser MDE pour appliquer les paramètres de configuration de sécurité à partir de MEM**, puis sélectionnez  **Windows Server**. </li><li>Sélectionnez **Enregistrer**.</li></ol>Les points de terminaison de serveur Linux doivent remplir les [conditions préalables pour Microsoft Defender pour point de terminaison sur Linux](../defender-endpoint/microsoft-defender-endpoint-linux.md#prerequisites).|

(<a id="fn1">1</a>) Microsoft Intune n’est pas inclus dans la version autonome de Defender pour les entreprises. Intune peuvent être ajoutés à Defender pour les entreprises. Intune est inclus dans Microsoft 365 Business Premium.

(<a id="fn2">2</a>) Pour intégrer des serveurs, nous vous recommandons d’utiliser [Microsoft Defender pour entreprises serveurs](get-defender-business-servers.md). Vous pouvez également utiliser [Microsoft Defender pour les serveurs](/azure/defender-for-cloud/defender-for-servers-introduction). Toutefois, votre expérience Defender entreprise peut changer lorsque vous ajoutez un plan d’entreprise, tel que Defender pour les serveurs Plan 1 ou Plan 2. Pour plus d’informations, consultez [Que se passe-t-il si j’ai une combinaison d’abonnements de sécurité de point de terminaison Microsoft ?](mdb-faq.yml#what-happens-if-i-have-a-mix-of-microsoft-endpoint-security-subscriptions) et [Intégrer des appareils à Microsoft Defender pour entreprises](mdb-onboard-devices.md).

> [!NOTE]
> [Azure Active Directory (Azure AD)](/azure/active-directory/fundamentals/active-directory-whatis) est utilisé pour gérer les autorisations des utilisateurs et les groupes d’appareils. Azure AD est inclus dans votre abonnement Defender for Business. 
> - Si vous n’avez pas d’abonnement Microsoft 365 avant de commencer votre version d’évaluation, Azure AD sera provisionné pour vous pendant le processus d’activation. 
> - Si vous disposez d’un autre abonnement Microsoft 365 lorsque vous démarrez votre version d’évaluation de Defender for Business, vous pouvez utiliser votre service Azure AD existant. 

## <a name="next-steps"></a>Prochaines étapes

Accédez à [Étape 2 : Attribuer des rôles et des autorisations dans Defender pour les entreprises](mdb-roles-permissions.md).
 
