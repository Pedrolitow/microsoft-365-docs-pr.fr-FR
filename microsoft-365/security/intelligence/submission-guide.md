---
title: Soumettre des fichiers pour analyse par Microsoft
description: Découvrez comment soumettre des fichiers à Microsoft pour analyse des programmes malveillants, comment suivre vos soumissions et détecter les litiges.
ms.reviewer: ''
keywords: sécurité, exemple d’aide sur la soumission, fichier de programmes malveillants, fichier antivirus, fichier de chevaux, envoyer, envoyer à Microsoft, soumettre un échantillon, virus, chevau de chevaux, ver, non détecté, ne détecte pas, e-mail microsoft, programme malveillant de messagerie, je pense qu’il s’agit d’un programme malveillant, je pense qu’il s’agit d’un virus, où puis-je envoyer un virus, est-ce un virus, MSE, ne détecte pas, aucune signature, aucune détection, fichier suspect,  MMPC, Centre de protection Microsoft contre les programmes malveillants, chercheurs, analyste, WDSI, intelligence de la sécurité
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
ms.openlocfilehash: 78f1e00555d36880f24f05d213f42725f4ac0133
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63680245"
---
# <a name="submit-files-for-analysis"></a>Envoyer des fichiers pour analyse

Si vous pensez qu’un fichier est malveillant ou qu’il est détecté de manière incorrecte, vous pouvez nous le soumettre pour analyse. Cette page a des réponses à certaines questions courantes sur la soumission d’un fichier pour analyse.

## <a name="how-do-i-send-a-malware-file-to-microsoft"></a>Comment envoyer un fichier de programmes malveillants à Microsoft ?

Vous pouvez nous envoyer des fichiers que vous pensez être des programmes malveillants ou des fichiers qui ont été détectés de manière incorrecte via le portail de [soumission d’exemples](https://www.microsoft.com/en-us/wdsi/filesubmission).

Nous recevons un grand nombre d’exemples provenant de nombreuses sources. Notre analyse est hiérarchisé par le nombre de détections de fichiers et le type d’envoi. Vous pouvez nous aider à effectuer une analyse rapide en fournissant des informations détaillées sur le produit que vous utilisiez et ce que vous faisiez lorsque vous avez trouvé le fichier.

Une fois que vous vous êtes connecté, vous pourrez suivre vos soumissions.

## <a name="can-i-send-a-sample-by-email"></a>Puis-je envoyer un exemple par courrier électronique ?

Non, nous acceptons uniquement les soumissions par le biais de notre [exemple de portail de soumission](https://www.microsoft.com/en-us/wdsi/filesubmission).

## <a name="can-i-submit-a-sample-without-signing-in"></a>Puis-je envoyer un exemple sans me dédicacer ?

Non. Si vous êtes un client d’entreprise, vous devez vous inscrire afin que nous pouvons hiérarchiser votre soumission de manière appropriée. Si vous rencontrez actuellement une épidémie de virus ou un incident lié à la sécurité, vous devez contacter votre professionnel du support Microsoft désigné ou contacter le Support [Microsoft](https://support.microsoft.com/) pour obtenir une assistance immédiate.

## <a name="what-is-the-software-assurance-id-said"></a>Qu’est-ce que l’ID Software Assurance (SAID) ?

[L’ID Software Assurance (SAID)](https://www.microsoft.com/licensing/licensing-programs/software-assurance-default.aspx) permet aux clients d’entreprise de suivre les droits d’assistance. Le portail de soumission accepte et conserve les informations SAID et permet aux clients  ayant des SAID valides d’effectuer des soumissions prioritaires.

### <a name="how-do-i-dispute-the-detection-of-my-program"></a>Comment puis-je m’en disputer la détection de mon programme ?

[Envoyez le fichier](https://www.microsoft.com/en-us/wdsi/filesubmission) en question en tant que développeur de logiciels. Patientez jusqu’à ce que votre envoi ait une détermination finale.

Si vous n’êtes pas satisfait de notre détermination de la soumission, utilisez le formulaire de contact du développeur fourni avec les résultats de la soumission pour contacter Microsoft. Nous utiliserons les informations que vous fournissez pour examiner plus en détail si nécessaire.

Nous encourageons tous les éditeurs de logiciels et les développeurs à en savoir plus sur la façon [dont Microsoft identifie les programmes malveillants et les logiciels indésirables](criteria.md).

## <a name="how-do-i-track-or-view-past-sample-submissions"></a>Comment suivre ou afficher les soumissions d’exemples passées ?

Vous pouvez suivre vos soumissions via la [page historique des soumissions](https://www.microsoft.com/en-us/wdsi/submissionhistory).

## <a name="what-does-the-submission-status-mean"></a>Que signifie l’état de la soumission ?

Chaque soumission est affichée dans l’un des types d’état suivants :

* Soumis : le fichier a été reçu

* En cours : un analyste a commencé à vérifier le fichier

* Fermé : une détermination finale a été donnée par un analyste

Vous pouvez voir l’état des fichiers que vous nous envoyez sur la [page historique des soumissions](https://www.microsoft.com/en-us/wdsi/submissionhistory).

## <a name="how-does-microsoft-prioritize-submissions"></a>Comment Microsoft hiérarchise-t-il les envois

Le traitement des soumissions prend une ressource d’analyste dédiée. Étant donné que nous recevons régulièrement un grand nombre de soumissions, nous les gérées en fonction d’une priorité. Les facteurs suivants affectent la façon dont nous hiérarchisons les envois :

* Les fichiers répandus qui peuvent avoir un impact sur un grand nombre d’ordinateurs sont classés par ordre de priorité.

* Les clients authentifiés, en particulier les clients d’entreprise ayant des [ID d’assurance logiciel (SAID) valides](https://www.microsoft.com/licensing/licensing-programs/software-assurance-default.aspx), sont prioritaires.

* Les soumissions marquées comme étant prioritaires par les titulaires DE LAS sont immédiatement signalées.

Votre soumission est immédiatement analysée par nos systèmes pour vous fournir la dernière détermination avant qu’un analyste ne commence à gérer votre cas. Notez que le même fichier a peut-être déjà été traitée par un analyste. Pour vérifier les mises à jour de la détermination, sélectionnez rescan sur la page des détails de la soumission.
