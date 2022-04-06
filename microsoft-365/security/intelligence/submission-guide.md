---
title: Envoyer des fichiers pour analyse par Microsoft
description: Découvrez comment envoyer des fichiers à Microsoft pour l’analyse des programmes malveillants, comment suivre vos soumissions et détecter les litiges.
ms.reviewer: ''
keywords: sécurité, exemple d’aide de soumission, fichier de logiciels malveillants, fichier virus, fichier cheval de Troie, envoyer, envoyer à Microsoft, envoyer un exemple, virus, cheval de Troie, ver, non détecté, ne détecte pas, e-mail microsoft, programme malveillant e-mail, je pense que c’est un programme malveillant, je pense que c’est un virus, où puis-je envoyer un virus, est-ce un virus, MSE, ne détecte pas, aucune signature, aucune détection, fichier suspect,  MMPC, Centre de protection Microsoft contre les programmes malveillants, chercheurs, analystes, WDSI, renseignement de sécurité
ms.prod: m365-security
ms.mktglfcycl: secure
ms.sitesec: library
ms.localizationpriority: medium
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
search.appverid: met150
ms.technology: m365d
ms.openlocfilehash: df2ab2b2019bb76af49f00d2751cdc76848705d1
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64663597"
---
# <a name="submit-files-for-analysis"></a>Envoyer des fichiers à analyser

Si vous avez un fichier que vous soupçonnez être un programme malveillant ou est mal détecté, vous pouvez nous le soumettre à des fins d’analyse. Cette page contient des réponses à certaines questions courantes sur l’envoi d’un fichier à des fins d’analyse.

## <a name="how-do-i-send-a-malware-file-to-microsoft"></a>Comment faire envoyer un fichier de programmes malveillants à Microsoft ?

Vous pouvez nous envoyer des fichiers susceptibles d’être des programmes malveillants ou des fichiers qui ont été détectés de manière incorrecte via [l’exemple de portail de soumission](https://www.microsoft.com/wdsi/filesubmission).

Nous recevons un grand nombre d’échantillons provenant de nombreuses sources. Notre analyse est hiérarchisée par le nombre de détections de fichiers et le type de soumission. Vous pouvez nous aider à effectuer une analyse rapide en fournissant des informations détaillées sur le produit que vous utilisiez et ce que vous faisiez lorsque vous avez trouvé le fichier.

Une fois connecté, vous pourrez suivre vos soumissions.

## <a name="can-i-send-a-sample-by-email"></a>Puis-je envoyer un exemple par e-mail ?

Non, nous acceptons uniquement les soumissions par le biais de notre [exemple de portail de soumission](https://www.microsoft.com/wdsi/filesubmission).

## <a name="can-i-submit-a-sample-without-signing-in"></a>Puis-je envoyer un exemple sans me connecter ?

Non. Si vous êtes un client d’entreprise, vous devez vous connecter afin que nous puissions hiérarchiser votre soumission de manière appropriée. Si vous rencontrez actuellement une épidémie de virus ou un incident lié à la sécurité, contactez votre professionnel du support Microsoft désigné ou accédez à [Support Microsoft](https://support.microsoft.com/) pour obtenir de l’aide immédiate.

## <a name="what-is-the-software-assurance-id-said"></a>Qu’est-ce que l’ID Software Assurance (SAID) ?

[L’ID Software Assurance (SAID)](https://www.microsoft.com/licensing/licensing-programs/software-assurance-default.aspx) permet aux clients d’entreprise de suivre les droits de support. Le portail de soumission accepte et conserve les informations SAID et permet aux clients disposant d’un SAID valide d’effectuer des soumissions de priorité plus élevée.

### <a name="how-do-i-dispute-the-detection-of-my-program"></a>Comment faire contester la détection de mon programme ?

[Envoyez le fichier](https://www.microsoft.com/wdsi/filesubmission) en question en tant que développeur de logiciels. Attendez que votre soumission soit définitivement déterminée.

Si vous n’êtes pas satisfait de notre détermination de la soumission, utilisez le formulaire de contact du développeur fourni avec les résultats de la soumission pour contacter Microsoft. Nous utiliserons les informations que vous fournissez pour examiner plus en détail si nécessaire.

Nous encourageons tous les éditeurs et développeurs de logiciels à découvrir [comment Microsoft identifie les programmes malveillants et les logiciels indésirables](criteria.md).

## <a name="how-do-i-track-or-view-past-sample-submissions"></a>Comment faire suivre ou afficher les exemples de soumissions passés ?

Vous pouvez suivre vos soumissions via la [page historique des soumissions](https://www.microsoft.com/wdsi/submissionhistory).

## <a name="what-does-the-submission-status-mean"></a>Que signifie l’état de la soumission ?

Chaque soumission se trouve dans l’un des types d’état suivants :

* Envoyé : le fichier a été reçu

* En cours : un analyste a commencé à vérifier le fichier

* Fermé : une décision finale a été donnée par un analyste

Vous pouvez voir l’état des fichiers que vous nous envoyez sur la [page d’historique des soumissions](https://www.microsoft.com/wdsi/submissionhistory).

## <a name="how-does-microsoft-prioritize-submissions"></a>Comment Microsoft hiérarchise les soumissions

Le traitement des soumissions prend une ressource d’analyste dédiée. Étant donné que nous recevons régulièrement un grand nombre de soumissions, nous les traitons en fonction d’une priorité. Les facteurs suivants affectent la façon dont nous hiérarchisons les soumissions :

* Les fichiers répandus susceptibles d’avoir un impact sur un grand nombre d’ordinateurs sont hiérarchisés.

* Les clients authentifiés, en particulier les clients d’entreprise disposant [d’ID Software Assurance valides, sont prioritaires](https://www.microsoft.com/licensing/licensing-programs/software-assurance-default.aspx).

* Les soumissions marquées comme haute priorité par les titulaires SAID sont immédiatement considérées.

Votre soumission est immédiatement analysée par nos systèmes pour vous donner la dernière détermination avant même qu’un analyste commence à gérer votre cas. Notez que le même fichier a peut-être déjà été traité par un analyste. Pour rechercher les mises à jour de la détermination, sélectionnez Rescan dans la page de détails de la soumission.
