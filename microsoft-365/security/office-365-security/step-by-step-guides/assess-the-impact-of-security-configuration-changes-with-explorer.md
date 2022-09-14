---
title: Évaluer l’impact des modifications de configuration de sécurité avec l’Explorateur
description: Exemples et procédure pas à pas de l’utilisation de l’Explorateur pour déterminer l’impact d’un changement de contrôle de sécurité (configuration) dans Microsoft Defender pour Office 365
search.product: ''
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTBen
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-guidance-templates
ms.topic: how-to
ms.technology: mdo
search.appverid: met150
ms.openlocfilehash: 83dae83889862b20bde0a4d00f6a9bb3821bdeea
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67687316"
---
# <a name="assess-the-impact-of-security-configuration-changes-with-explorer"></a>Évaluer l’impact des modifications de configuration de sécurité avec l’Explorateur

Avant d’apporter des modifications à votre configuration de sécurité, telles que des stratégies ou des règles de transport, il est important de comprendre l’impact des modifications afin de pouvoir planifier et garantir une interruption *minimale* de votre organisation.

Ce guide pas à pas vous guide tout au long de l’évaluation d’un changement et de l’exportation des e-mails concernés pour l’évaluation. La procédure peut être appliquée à de nombreuses modifications différentes, en modifiant les critères (filtres) que vous utilisez dans l’Explorateur.

## <a name="what-youll-need"></a>Ce dont vous aurez besoin

- Microsoft Defender pour Office 365 plan 2 (inclus dans le cadre de l’E5).
- Autorisations suffisantes (lecteur de sécurité minimum requis pour l’évaluation via l’Explorateur de menaces).
- 5 à 10 minutes pour effectuer les étapes ci-dessous.

## <a name="assess-changing-normal-confidence-phish-delivery-location-to-quarantine-from-the-junk-email-folder"></a>Évaluer la modification de l’emplacement normal de livraison par hameçonnage en quarantaine (à partir du dossier Courrier indésirable)

1. **Connectez-vous** au portail de sécurité et accédez à l’Explorateur (sous *Email & Collaboration* sur le volet de navigation gauche). <https://security.microsoft.com/threatexplorer>
1. Sélectionnez **Phish** dans la sélection de l’onglet supérieur (*Tous les e-mails* sont l’affichage par défaut).
1. Appuyez sur le bouton **filtre** (par défaut *, Expéditeur*), puis sélectionnez **Niveau de confiance Phish**.
1. Sélectionnez le niveau **de** **confiance Phish** normal.
1. Ajoutez un **filtre** supplémentaire de **l’emplacement de remise d’origine** défini comme **dossier indésirable**.
1. Appuyez sur **Actualiser**. L’Explorateur est désormais filtré pour afficher tous les messages détectés comme hameçonnage *à haut niveau de confiance* et remis au dossier Courrier indésirable en raison des paramètres de la stratégie anti-courrier indésirable.
1. Si vous souhaitez faire pivoter les données affichées dans le graphique, vous pouvez le faire en utilisant le **segment de données en haut à gauche du graphique (action de *remise* par défaut),** en sélectionnant des données utiles telles que l’adresse IP de l’expéditeur ou le **domaine de l’expéditeur** pour repérer les tendances et les principaux expéditeurs affectés.
1. Sous la section du graphique, où les e-mails affectés sont affichés, sélectionnez **Exporter la liste des e-mails**, ce qui générera un fichier CSV pour l’analyse hors connexion. **Il s’agit d’une liste des e-mails qui seraient mis en quarantaine si l’action de hameçonnage était modifiée en quarantaine (modification recommandée pour les présélections standard et strictes).**

## <a name="assess-removing-a-sender--domain-override-removal"></a>Évaluer la suppression d’un expéditeur/suppression de remplacement de domaine

1. **Connectez-vous** au portail de sécurité et accédez à **l’Explorateur** (sous Email & Collaboration sur le volet de navigation gauche). <https://security.microsoft.com/threatexplorer>
1. Sélectionnez **Tous les e-mails s’ils** ne sont pas déjà sélectionnés.
1. Appuyez sur le bouton **filtre** (par défaut *, Expéditeur*) et ajoutez un filtre de domaine d’expéditeur ou d’expéditeur, puis ajoutez l’entrée dans laquelle vous souhaitez évaluer l’impact de la suppression.
1. Développez la plage de dates jusqu’au maximum & **appuyez sur Actualiser** . Vous devez maintenant voir la liste des messages si l’expéditeur/le domaine d’envoi est toujours actif dans la messagerie de votre organisation. Si *ce n’est pas* le cas, vous devrez peut-être ajuster le filtre, ou vous ne recevrez plus de courrier de ce domaine/expéditeur et vous pouvez supprimer l’entrée en toute sécurité.
1. Si le courrier est répertorié, cela signifie que l’entrée est toujours un expéditeur actif. Faire pivoter les données dans le graphique à l’aide du segment de données (action de *remise* par défaut) vers **la technologie de détection**.
1. Le graphique doit être actualisé et, s’il n’affiche désormais aucune donnée, cela signifie que nous n’avons détecté aucune menace sur l’un des messages affichés précédemment, ce qui indique qu’un remplacement n’est pas nécessaire, car il n’existe aucune détection à remplacer.
1. Si des données sont affichées lorsque les données sont segmentées par **la technologie de détection**, cela signifie que la suppression du remplacement *aurait* un impact sur cet expéditeur/domaine en raison de l’action de la pile de protection.
1. Vous devez examiner le courrier plus loin pour déterminer s’il est vraiment malveillant et si l’entrée peut être supprimée, ou s’il s’agit d’un *faux positif* et doit être corrigé afin qu’il ne soit plus correctement détecté comme une menace (l’authentification est la cause la plus importante de faux positifs).

### <a name="further-reading"></a>Lire plus en détail

Envisagez d’utiliser des présélections sécurisées [pour vous assurer que vous disposez toujours des contrôles de sécurité optimaux avec des stratégies de sécurité prédéfinies](/microsoft-365/security/office-365-security/step-by-step-guides/ensuring-you-always-have-the-optimal-security-controls-with-preset-security-policies)

Vous pouvez également gérer les problèmes d’authentification par e-mail avec [spoof intelligence Spoof intelligence insight](/microsoft-365/security/office-365-security/learn-about-spoof-intelligence)

En savoir plus sur l’authentification par e-mail [Email l’authentification dans Exchange Online Protection](/microsoft-365/security/office-365-security/email-validation-and-authentication)
