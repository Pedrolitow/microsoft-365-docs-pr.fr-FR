---
title: Soumission des messages indésirables, légitimes ou des tentatives de hameçonnage à Microsoft pour analyse
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: dad30e2f-93fe-4d21-9a36-21c87ced85c1
ms.collection:
- M365-security-compliance
description: 'Vous et vos utilisateurs pouvez soumettre des messages indésirables faux positifs et faux positifs à Microsoft pour analyse. '
ms.openlocfilehash: 27e0698d1ad7d05adfa69e18e9b5b21edb74b1eb
ms.sourcegitcommit: fce0d5cad32ea60a08ff001b228223284710e2ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "42893645"
---
# <a name="submit-spam-non-spam-and-phishing-scam-messages-to-microsoft-for-analysis"></a>Soumission des messages indésirables, légitimes ou des tentatives de hameçonnage à Microsoft pour analyse

Il peut être frustrant lorsque les utilisateurs de votre organisation reçoivent des courriers indésirables (spam) ou des messages frauduleux de hameçonnage dans leur boîte de réception, ou s’ils ne reçoivent pas de message électronique légitime, car il est marqué comme courrier indésirable. Nous ajustons constamment les filtres de courrier indésirable pour qu’ils soient plus précis. Vous et vos utilisateurs pouvez aider ce processus en envoyant des messages indésirables faux positifs et faux positifs à Microsoft pour analyse. Un « faux négatif » est un message de courrier indésirable qui aurait dû être considéré comme du courrier indésirable. Un « faux positif » est un message électronique légitime identifié de manière incorrecte comme courrier indésirable.

> [!NOTE]
> En raison du volume élevé des envois que nous recevons, il se peut que nous ne parvenons pas à répondre à toutes les demandes d’analyse.

Les administrateurs peuvent envoyer des courriers électroniques, des URL et des pièces jointes à Microsoft à des fins de révision. Consultez la rubrique [envois administratifs dans Office 365 ATP](admin-submission.md).

## <a name="submit-junk-or-phishing-messages-that-passed-through-the-spam-filters"></a>Soumettre des courriers indésirables ou des tentatives de hameçonnage passés à travers les filtres de courrier indésirable

Si vous recevez un message transmis par le biais de filtres de courrier indésirable qui doivent être considérés comme des courriers indésirables ou des tentatives de hameçonnage, vous pouvez envoyer le message « faux Negative » à l’analyse du courrier indésirable Microsoft et aux équipes d’analyse du hameçonnage Microsoft, selon le cas. Les analystes examineront le message et l’ajouteront aux filtres à l’échelle du service s’il répond aux critères de classification.

Pour plus de paramètres de courrier indésirable qui s’appliquent à l’ensemble de l’organisation, consultez la rubrique [protection contre le courrier indésirable dans Office 365](anti-spam-protection.md). Cet article contient des conseils pour éviter les faux négatifs.

Vous pouvez soumettre des courriers indésirables en procédant comme suit :

- Pour les utilisateurs d’Outlook et d’Outlook sur le Web, utilisez le complément de message de rapport pour Microsoft Outlook. Pour plus d’informations sur l’installation et l’utilisation de cet outil, voir [activer le complément de message de rapport](enable-the-report-message-add-in.md).

- Vous pouvez également utiliser la messagerie électronique pour soumettre des messages à Microsoft qui doivent être classés comme courriers indésirables ou frauduleux, comme décrit dans la procédure suivante.

### <a name="use-email-to-submit-junk-spam-or-phishing-scam-messages-to-microsoft"></a>Utilisation de la messagerie pour soumettre des courriers indésirables (spam) ou des tentatives de hameçonnage à Microsoft 

Pour soumettre un courrier indésirable ou une tentative de hameçonnage à Microsoft, procédez comme suit :

1. Créez un message électronique vide.

2. Adressez le message à l’équipe Microsoft qui examine les messages, comme suit :

   - Pour les messages indésirables : junk@office365.microsoft.com

   - Pour les messages d’hameçonnage : phish@office365.microsoft.com

3. Copiez et collez le message d’hameçonnage ou de courrier indésirable dans le nouveau message en tant que pièce jointe.

   > [!NOTE]
   > * Vous pouvez joindre plusieurs messages dans le nouveau message. Assurez-vous que tous les messages sont du même type : les messages de hameçonnage ou les messages électroniques de courrier indésirable. <br/><br/>* Laissez le corps du nouveau message vide. <br/><br/>* Utilisez les formats. MSG (format Outlook par défaut) ou. eml (Outlook sur le format Web par défaut) pour les messages joints.

4. Cliquez sur **Envoyer**.

## <a name="submit-messages-that-were-tagged-as-junk-but-should-have-been-allowed-through"></a>Soumission de messages marqués comme courrier indésirable mais qui auraient dû être transmis 

Si un message a été identifié de manière incorrecte comme courrier indésirable, vous pouvez envoyer le message « faux positif » à l’équipe d’analyse du courrier indésirable de Microsoft. Les analystes vont évaluer et analyser le message. Selon les résultats de l'analyse, les règles de filtrage de contenu du courrier indésirable du service peuvent être ajustées pour autoriser le message.

Les administrateurs peuvent examiner davantage d’informations sur les paramètres du courrier indésirable qui s’appliquent à une organisation entière. Consultez la rubrique [créer des listes d’expéditeurs approuvés dans Office 365](create-safe-sender-lists-in-office-365.md). Ces informations sont utiles si vous disposez d'un contrôle de niveau administrateur et si vous souhaitez éviter les faux positifs ou les faux négatifs.

Vous pouvez envoyer des messages de courrier non indésirable de la manière suivante :

- Si vous utilisez l’action **déplacer le message vers le dossier courrier indésirable** lorsque vous configurez vos filtres de contenu (il s’agit de l’action par défaut), les utilisateurs peuvent publier des messages faux positifs dans le dossier courrier indésirable Outlook ou Outlook sur le Web (anciennement Outlook Web App).

  - Les utilisateurs d’Outlook peuvent émettre des messages faux positifs à l’aide du menu contextuel **légitime** . Toutefois, ils doivent envoyer le message à Microsoft par courrier électronique, comme illustré dans la procédure décrite dans cet article.

  - Les utilisateurs d’Outlook sur le Web peuvent émettre des messages faux positifs et les envoyer à Microsoft pour analyse à l’aide de l’action **marquer comme légitime** . Pour plus d’informations sur la procédure à suivre, consultez la rubrique signaler des courriers [indésirables et des escroqueries par hameçonnage dans Outlook sur le Web ](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md).

- Si vous utilisez l’action **mettre en quarantaine** au lieu de l’action déplacer le **message vers le dossier courrier indésirable** lorsque vous configurez vos filtres de contenu :

  - Les administrateurs peuvent libérer des messages de courrier indésirable mis en quarantaine et les signaler comme faux positifs à partir du Centre d'administration Exchange. Pour plus d’informations, consultez la rubrique [gestion des messages et des fichiers mis en quarantaine en tant qu’administrateur dans Office 365](manage-quarantined-messages-and-files.md).

  - Les utilisateurs peuvent publier leurs propres messages indésirables mis en quarantaine et les signaler comme faux positifs par le biais des canaux suivants :

  - L'interface utilisateur du centre d'administration Exchange (EAC). Pour plus d’informations, voir [Find and Release Quarantined Messages (End Users)](find-and-release-quarantined-messages-as-a-user.md).

  - Les messages de notification de courrier indésirable pour les utilisateurs finaux (s'ils sont activés par votre administrateur).

- Vous pouvez également utiliser la messagerie pour envoyer à Microsoft des messages qui ne devraient pas être classés comme courrier indésirable. Lorsque vous procédez ainsi, veillez à suivre les étapes de la procédure ci-dessous.

### <a name="use-email-to-submit-false-positive-messages"></a>Utilisation du courrier électronique pour soumettre des messages faux positifs

Utilisez la même procédure que celle décrite dans la section [utiliser le courrier électronique pour soumettre des courriers indésirables (spam) ou des tentatives de hameçonnage à Microsoft](#use-email-to-submit-junk-spam-or-phishing-scam-messages-to-microsoft) , mais envoyez le message à not_junk@office365.microsoft.com.

## <a name="spam-evaluation-and-rules-deployment"></a>Évaluation du courrier indésirable et déploiement des règles

L’équipe analyse du courrier indésirable examine les messages que vous envoyez et ajuste les filtres de courrier indésirable pour éviter les futurs courriers indésirables. Par conséquent, les filtres de courrier indésirable d’Office 365 areconstantly perfectionnés. Les éléments soumis sont évalués au niveau réseau. Les soumissions de faux positifs sont examinées et évaluées pour les éventuels ajustements de règle afin d’autoriser les messages futurs via les filtres de courrier indésirable. Par conséquent, vous et tous les clients qui utilisent le réseau global sont des avantages pour le service de faux positifs, ainsi que des faux négatifs (courrier indésirable non filtré). L’équipe de courrier indésirable examine les indicateurs dans chaque message envoyé, par exemple :

- Adresse de l'expéditeur

- Adresse IP d'expédition

- Mots clés

- Expressions

- Fréquence de transmission

- Autres tendances et modèles

Après avoir examiné ces informations, l’équipe de courrier indésirable peut modifier les couches de filtrage du courrier indésirable du service. Pour plus d’informations sur l’équipe de courrier indésirable, vous pouvez regarder la vidéo en anglais uniquement suivante :

[Vidéo de l’équipe de courrier indésirable Microsoft Exchange](https://youtu.be/-TpX_-GMC7o?hd=1)

L'évaluation du courrier indésirable est un processus permanent qui s'applique quels que soient la langue et le jeu de caractères d'origine. Lorsque le message de courrier indésirable est vague ou manque de texte dans la ligne d'objet ou le corps, l'équipe de courrier indésirable s'appuie sur d'autres caractéristiques du message pour effectuer le filtrage. Cela signifie qu'après que l'équipe de courrier indésirable a balisé un message donné comme courrier indésirable et apporté les modifications nécessaires à sa base de règles, ce message reste bloqué jusqu'à ce que ses caractéristiques aient été suffisamment modifiées pour échapper à nos filtres. De nouvelles règles de courrier indésirable sont déployées en permanence. Les périodes pour les règles relatives aux soumissions individuelles dépendent de la quantité et de la qualité des soumissions. Comme les nouvelles règles de courrier indésirable sont définies globalement pour tous les utilisateurs, les diverses soumissions de courrier indésirable n'entraînent pas toutes l'introduction de nouvelles règles de courrier indésirable.
