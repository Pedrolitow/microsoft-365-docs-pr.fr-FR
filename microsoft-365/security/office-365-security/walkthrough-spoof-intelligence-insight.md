---
title: Procédure pas à pas-usurpation d’aide
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: overview
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: 59a3ecaf-15ed-483b-b824-d98961d88bdd
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent découvrir le fonctionnement de l’aide à la décision, notamment comment déterminer rapidement les expéditeurs qui envoient légitimement des messages électroniques non authentifiés.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 5995095e442bbcd07ddf4538b67be6e1b14fd8f1
ms.sourcegitcommit: 815229e39a0f905d9f06717f00dc82e2a028fa7c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "48844211"
---
# <a name="walkthrough---defender-for-office-365-spoof-intelligence-insight-in-microsoft-365"></a>Procédure pas à pas-Defender pour Office 365 usurpation d’aide à la décision dans Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Dans les organisations Microsoft 365 avec Defender pour Office 365, vous pouvez utiliser la fonction d’aide à la décision pour déterminer rapidement les expéditeurs qui envoient légitimement des messages électroniques non authentifiés. En leur permettant d’envoyer des messages falsifiés, vous pouvez réduire le risque de faux positifs pour vos utilisateurs. Vous pouvez également utiliser le gestionnaire d’aide à la décision pour surveiller et gérer les paires de domaines autorisées afin de fournir une couche de sécurité supplémentaire et empêcher les messages non sécurisés d’arriver dans votre organisation.

Si vous débutez avec des [rapports et des informations dans le centre de sécurité & conformité](reports-and-insights-in-security-and-compliance.md), il peut vous aider à vous rendre compte d’un tableau de bord jusqu’à une analyse et des actions recommandées.

Cette procédure pas à pas est l’une des suivantes pour le centre de conformité & la sécurité. Pour savoir comment naviguer dans les rapports et les informations, consultez les procédures pas à pas dans la section Rubriques connexes.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Centre de conformité et sécurité sur <https://protection.office.com/>. Pour accéder directement à la page du **tableau de bord de sécurité** , utilisez <https://protection.office.com/searchandinvestigation/dashboard> .

  Vous pouvez afficher le centre d’aide à la décision à partir de plusieurs tableaux de bord dans le centre de conformité & Compliance Center. Quel que soit le tableau de bord que vous examinez, le détail fournit les mêmes détails et vous permet d’effectuer rapidement les mêmes tâches.

- Des autorisations doivent vous être attribuées avant de pouvoir effectuer les procédures décrites dans cette rubrique. Pour utiliser la fonction d’aide à la décision, vous devez être membre de l’un des groupes de rôles suivants :

  - **Gestion de l’organisation** ou **Administrateur de sécurité** dans le [Centre de sécurité et de conformité](permissions-in-the-security-and-compliance-center.md).
  - **Gestion de l’organisation** ou **Gestion de l’hygiène** dans [Exchange Online](https://docs.microsoft.com/Exchange/permissions-exo/permissions-exo#role-groups).
  - **Lecteur de sécurité** dans le [Centre de conformité et sécurité](permissions-in-the-security-and-compliance-center.md).
  - **Gestion de l’organisation en affichage seul** dans [Exchange Online](https://docs.microsoft.com/Exchange/permissions-exo/permissions-exo#role-groups).

- Vous activez et désactivez l’intelligence contre les usurpations dans les stratégies de hameçonnage dans Microsoft Defender pour Office 365. Pour plus d’informations, reportez-vous à la rubrique [configure anti-phishing Policies in Microsoft Defender for Office 365 dans microsoft 365](configure-atp-anti-phishing-policies.md).

- Dans les organisations Microsoft 365 avec des boîtes aux lettres Exchange Online et dans un environnement Exchange Online Protection (EOP) autonome sans boîte aux lettres Exchange Online, vous pouvez utiliser l’intelligence des usurpations pour surveiller et gérer les expéditeurs auxquels vous envoyez des messages non authentifiés. Si vous souhaitez en savoir plus, consultez l’article [Configurer la veille contre l’usurpation d’identité dans Microsoft 365](learn-about-spoof-intelligence.md).

## <a name="open-the-spoof-intelligence-insight-in-the-security--compliance-center"></a>Ouvrir la vue d’aide à la décision dans le centre de sécurité & conformité

1. Dans le centre de sécurité & conformité, accédez au tableau de bord **gestion des menaces** \> **.**

2. Dans la ligne **Insights** , recherchez l’un des éléments suivants :

   - L' **intelligence d’usurpation d’identité est activée** : elle est appelée **domaines falsifiés dont l’authentification a échoué au cours des 30 derniers jours**. Valeur par défaut.

   - L' **intelligence d’usurpation d’identité est désactivée** : l’aperçu de l’option **activer la protection contre les usurpations**

3. Le tableau de bord affiche des informations comme celles-ci :

   ![Capture d’écran d’un aperçu d’aide à la décision](../../media/28aeabac-c1a1-4d16-9fbe-14996f742a9a.png)

   Cette vue comprend deux modes :

   - **Mode aperçu**. Si aucune stratégie de falsification n’est activée, le service d’aide à la décision indique le nombre de messages ayant été affectés par nos capacités d’aide à la falsification au cours des 30 derniers jours.

   - **Mode d’action**. Si aucune stratégie de falsification n’est activée, le service d’aide à la décision indique le nombre de messages qui  *auraient*  été affectés par nos capacités d’aide à la falsification au cours des 30 derniers jours.

   Dans les deux cas, les domaines usurpés affichés dans la vue sont divisés en deux catégories : les paires de domaines **suspects** et les **paires de domaines non suspectes**. Ces catégories sont encore subdivisées en trois compartiments différents que vous pouvez examiner.

   Une **paire de domaine** est une combinaison de l’adresse de l’expéditeur et de l’infrastructure d’envoi :

   - L’adresse de l’expéditeur correspond à l’adresse de messagerie de l’expéditeur qui est affichée dans les clients de messagerie. Cette adresse indique l’auteur de l’e-mail. Autrement dit, elle indique la boîte aux lettres de la personne ou du système responsable de la rédaction du message. Cette adresse est également appelée `5322.From` adresse.

   - L’infrastructure d’envoi, ou expéditeur, est le domaine de l’organisation de la recherche DNS inverse (enregistrement PTR) de l’adresse IP d’envoi. Si l’adresse IP d’envoi n’a pas d’enregistrement PTR, l’expéditeur est identifié par l’adresse IP d’envoi avec le masque de sous-réseau 255.255.255.0 dans la notation CIDR (/24). Par exemple, si l’adresse IP est 192.168.100.100, l’adresse IP complète de l’expéditeur est 192.168.100.100/24.

   Les **paires de domaines suspectes** sont les suivantes :

   - **Usurpation de confiance élevée** : Microsoft 365 a reçu des signaux forts que ces domaines sont suspects, selon les modèles d’envoi historique et le score de réputation des domaines. Microsoft 365 est hautement sûr que les domaines usurpent l’identité et que les messages envoyés à partir de ces domaines sont moins susceptibles d’être légitimes.

   - **Usurpation de confiance modérée** : Microsoft 365 a reçu des signaux modérés signalant que ces domaines sont suspects, en fonction des modèles d’envoi historiques et du score de réputation des domaines. Office 365 est modérément convaincu que les domaines sont des usurpations et que les messages envoyés à partir de ces domaines sont légitimes. Ce compartiment a plus de chances de contenir des faux positifs (FPs) que le compartiment d’usurpation de confiance élevée.

   - **Paires de domaines non suspectes** (y compris l' **usurpation d’identité** ) : les usurpations d’identité sont des domaines dont l’authentification explicite a [échoué,](how-office-365-uses-spf-to-prevent-spoofing.md) [DKIM](use-dkim-to-validate-outbound-email.md), [DMARC](use-dmarc-to-validate-email.md)) mais qui ont transmis nos contrôles d’authentification de messagerie implicites ( [authentification composite](email-validation-and-authentication.md#composite-authentication)). Par conséquent, Microsoft 365 a récupéré le courrier en votre nom et aucune action de détection d’usurpation d’identité n’a été effectuée sur le message.

### <a name="view-detailed-information-about-suspicious-domain-pairs-from-the-spoof-intelligence-insight"></a>Afficher des informations détaillées sur les paires de domaines suspectes à partir de l’aide à la décision

1. Sur la vue d’aide à la décision, cliquez sur l’une des paires de domaines (élevée, modérée ou de récupération).

   La page **usurpation** d’aide s’affiche, indiquant la liste des expéditeurs qui envoient des messages non authentifiés dans votre organisation. Les informations de cette page vous permettent de déterminer si des messages falsifiés sont autorisés ou si vous devez effectuer des actions supplémentaires. Vous pouvez trier les informations par nombre de messages, la date de la dernière détection de l’usurpation, et bien plus encore. (Cliquez sur les en-têtes de colonne, par exemple **nombre de messages** ou **Dernière vue** , par exemple).

2. Sélectionnez un élément dans le tableau pour ouvrir un volet de détails qui contient des informations détaillées sur la paire de domaines, notamment la raison pour laquelle nous l’avons détectée, ce que vous devez faire, un résumé de domaine, des données WhoIs sur l’expéditeur et des e-mails similaires que nous avons vus dans votre client du même expéditeur. À partir de là, vous pouvez également choisir d’ajouter ou de supprimer la paire de domaine de la liste des expéditeurs approuvés **AllowedToSpoof** .

   ![Capture d’écran d’un domaine dans le volet d’informations d’aide à la décision](../../media/03ad3e6e-2010-4e8e-b92e-accc8bbebb79.png)

### <a name="add-or-remove-a-domain-from-the-allowedtospoof-safe-sender-list"></a>Ajouter ou supprimer un domaine de la liste des expéditeurs approuvés AllowedToSpoof

Vous ajoutez ou supprimez un domaine de la liste des expéditeurs approuvés AllowedToSpoof tout en vérifiant la paire de domaines dans le volet d’informations de la vue d’aide à la décision. Définissez simplement le bouton bascule en conséquence.

Cela modifie la combinaison de paires de domaines unique du domaine usurpé et de l’infrastructure d’envoi et ne fournit pas de couverture pour l’ensemble du domaine usurpé ou l’infrastructure d’envoi isolée.

Par exemple, si vous ajoutez la paire de domaines suivante à la liste verte de l’expéditeur « AllowedToSpoof » :  *domaine usurpé*  « gmail.com » et l' *infrastructure d’envoi* « TMS *. mx.com »,* seul le courrier de cette paire de domaines sera autorisé à usurper. Les autres expéditeurs qui tentent d’usurper « gmail.com » et d’autres domaines que « tms.mx.com » tentent d’usurper continueront à être protégés par l’intelligence des usurpations d’identité.

## <a name="related-topics"></a>Voir aussi

[Protection contre l’usurpation d’identité dans Microsoft 365](anti-spoofing-protection.md)
