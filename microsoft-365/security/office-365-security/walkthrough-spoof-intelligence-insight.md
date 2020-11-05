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
description: Les administrateurs peuvent découvrir comment fonctionne l’aide à la décision. Ils peuvent déterminer rapidement les expéditeurs qui envoient des messages légitimes à leur organisation à partir de domaines qui ne passent pas de vérifications d’authentification de messagerie (SPF, DKIM ou DMARC).
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 89a31c6df7c9b6e02f52ea414ceb6334427feab1
ms.sourcegitcommit: d7975c391e03eeb96e29c1d02e77d2a1433ea67c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "48920477"
---
# <a name="walkthrough---spoof-intelligence-insight-in-microsoft-defender-for-office-365"></a>Procédure pas à pas-usurpation d’aide à la décision de Microsoft Defender pour Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Dans les organisations Microsoft 365 avec Defender pour Office 365, vous pouvez utiliser la fonction d’aide à la décision pour déterminer rapidement les expéditeurs qui envoient des messages électroniques non authentifiés (messages provenant de domaines ne passant pas les vérifications SPF, DKIM ou DMARC).

En autorisant les expéditeurs connus à envoyer des messages falsifiés à partir d’emplacements connus, vous pouvez réduire les faux positifs (courrier marqué comme incorrect). En surveillant les expéditeurs usurpés autorisés, vous fournissez une couche supplémentaire de sécurité pour empêcher les messages non sécurisés d’arriver dans votre organisation.

Pour plus d’informations sur les rapports et les Insights, voir [rapports et informations dans le centre de sécurité & conformité](reports-and-insights-in-security-and-compliance.md).

Cette procédure pas à pas est l’une des suivantes pour le centre de conformité & la sécurité. Pour savoir comment naviguer dans les rapports et les informations, consultez les procédures pas à pas dans la section [Rubriques connexes](#related-topics) .

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Centre de conformité et sécurité sur <https://protection.office.com/>. Pour accéder directement à la page du **tableau de bord de sécurité** , utilisez <https://protection.office.com/searchandinvestigation/dashboard> .

  Vous pouvez afficher le centre d’aide à la décision à partir de plusieurs tableaux de bord dans le centre de conformité & Compliance Center. Quel que soit le tableau de bord que vous examinez, le détail fournit les mêmes détails et vous permet d’effectuer rapidement les mêmes tâches.

- Des autorisations doivent vous être attribuées avant de pouvoir effectuer les procédures décrites dans cette rubrique. Pour utiliser la fonction d’aide à la décision, vous devez être membre de l’un des groupes de rôles suivants :

  - **Gestion de l’organisation** ou **Administrateur de sécurité** dans le [Centre de sécurité et de conformité](permissions-in-the-security-and-compliance-center.md).
  - **Gestion de l’organisation** ou **Gestion de l’hygiène** dans [Exchange Online](https://docs.microsoft.com/Exchange/permissions-exo/permissions-exo#role-groups).
  - **Lecteur de sécurité** dans le [Centre de conformité et sécurité](permissions-in-the-security-and-compliance-center.md).
  - **Gestion de l’organisation en affichage seul** dans [Exchange Online](https://docs.microsoft.com/Exchange/permissions-exo/permissions-exo#role-groups).

- Vous activez et désactivez l’intelligence contre les usurpations dans les stratégies de hameçonnage dans Microsoft Defender pour Office 365. Pour plus d’informations, consultez la rubrique [configure anti-phishing Policies in Microsoft Defender for Office 365](configure-atp-anti-phishing-policies.md).

- Pour surveiller et gérer les expéditeurs qui envoient des messages non authentifiés à l’aide d’une usurpation d’identité, reportez-vous à la rubrique [configure usurpation Intelligence in Microsoft 365](learn-about-spoof-intelligence.md).

## <a name="open-the-spoof-intelligence-insight-in-the-security--compliance-center"></a>Ouvrir la vue d’aide à la décision dans le centre de sécurité & conformité

1. Dans le centre de sécurité & conformité, accédez au tableau de bord **gestion des menaces** \> **.**

2. Dans la ligne **Insights** , recherchez l’un des éléments suivants :

   - L' **intelligence d’usurpation d’identité est activée** : elle est appelée **domaines falsifiés dont l’authentification a échoué au cours des 30 derniers jours**. Valeur par défaut.
   - L' **intelligence d’usurpation d’identité est désactivée** : l’aperçu de l’option **activer la protection contre les usurpations**

3. Le tableau de bord affiche des informations comme celles-ci :

   ![Capture d’écran d’un aperçu d’aide à la décision](../../media/28aeabac-c1a1-4d16-9fbe-14996f742a9a.png)

   Cette vue comprend deux modes :

   - **Mode** d’affichage : si l’aide à l’usurpation d’identité est activée, le grand nombre de messages ont été affectés par nos capacités d’aide à la falsification au cours des 30 derniers jours.

   - **Quel mode si** : si l’intelligence d’usurpation d’identité est désactivée, le rapport indique le nombre de messages qui *auraient* été affectés par nos capacités d’aide à la falsification au cours des 30 derniers jours.

   Dans les deux cas, les domaines usurpés affichés dans la vue sont divisés en deux catégories : les paires de domaines **suspects** et les **paires de domaines non suspectes**. Ces catégories sont encore subdivisées en trois compartiments différents que vous pouvez examiner.

   Une **paire de domaine** est une combinaison de l’adresse de l’expéditeur et de l’infrastructure d’envoi :

   - L’adresse de l’expéditeur correspond à l’adresse de messagerie de l’expéditeur affichée dans la zone de dans clients de messagerie. Cette adresse est également appelée `5322.From` adresse.

   - L’infrastructure d’envoi, ou expéditeur, est le domaine de l’organisation de la recherche DNS inverse (enregistrement PTR) de l’adresse IP d’envoi. Si l’adresse IP d’envoi n’a pas d’enregistrement PTR, l’expéditeur est identifié par l’adresse IP d’envoi avec le masque de sous-réseau 255.255.255.0 dans la notation CIDR (/24). Par exemple, si l’adresse IP est 192.168.100.100, l’adresse IP complète de l’expéditeur est 192.168.100.100/24.

   Les **paires de domaines suspectes** sont les suivantes :

   - **Usurpation de confiance élevée** : selon les modèles d’envoi historique et le score de réputation des domaines, nous sommes très convaincus que les domaines sont des usurpations et les messages provenant de ces domaines sont plus susceptibles d’être malveillants.

   - **Usurpation de confiance modérée** : basée sur des modèles d’envoi historiques et sur le score de réputation des domaines, nous sommes modérément confiants que les domaines sont des usurpations et que les messages envoyés à partir de ces domaines sont légitimes. Les faux positifs sont plus susceptibles de se situer dans cette catégorie que le taux d’usurpation de confiance élevée.

   - **Paires de domaines non suspectes** (y compris l' **usurpation d’identité** ) : le domaine a échoué à des vérifications d’authentification de messagerie indéfinies [SPF](how-office-365-uses-spf-to-prevent-spoofing.md), [DKIM](use-dkim-to-validate-outbound-email.md)et [DMARC](use-dmarc-to-validate-email.md)). Toutefois, le domaine a transmis nos vérifications d’authentification de messagerie implicites ([authentification composite](email-validation-and-authentication.md#composite-authentication)). Par conséquent, aucune action de détection d’usurpation d’identité n’a été effectuée sur le message.

### <a name="view-detailed-information-about-suspicious-domain-pairs-from-the-spoof-intelligence-insight"></a>Afficher des informations détaillées sur les paires de domaines suspectes à partir de l’aide à la décision

1. Sur la vue d’aide à la décision, cliquez sur l’une des paires de domaines (élevée, modérée ou de récupération).

   La page **usurpation** d’aide s’affiche. La page affiche la liste des expéditeurs qui envoient des messages non authentifiés dans votre organisation.

   Ces informations vous permettent de déterminer si des messages falsifiés sont autorisés ou si vous devez effectuer des actions supplémentaires.

   Vous pouvez trier les informations par nombre de messages, la date de la dernière détection de l’usurpation, et bien plus encore.

2. Sélectionnez un élément dans le tableau pour ouvrir un volet d’informations contenant des informations détaillées sur la paire de domaines. Ces informations sont les suivantes :
   - Pourquoi nous avons pris cette explication.
   - Ce que vous devez faire.
   - Un résumé de domaine.
   - Identification des données relatives à l’expéditeur.
   - Messages similaires que nous avons vus dans votre client par le même expéditeur.

   À partir de là, vous pouvez également choisir d’ajouter ou de supprimer la paire de domaine de la liste des expéditeurs approuvés **AllowedToSpoof** .

   ![Capture d’écran d’un domaine dans le volet d’informations d’aide à la décision](../../media/03ad3e6e-2010-4e8e-b92e-accc8bbebb79.png)

### <a name="add-or-remove-a-domain-from-the-allowedtospoof-list"></a>Ajouter ou supprimer un domaine de la liste AllowedToSpoof

Vous ajoutez ou supprimez un domaine de la liste AllowedToSpoof (expéditeur fiable) dans le volet d’informations de l’aide à la décision pour la paire de domaines. Définissez simplement le bouton bascule en conséquence.

L’autorisation d’une paire de domaines autorise uniquement la combinaison du domaine usurpé *et* de l’infrastructure d’envoi. Elle n’autorise pas les messages provenant du domaine usurpé à partir de n’importe quelle source, et ne permet pas non plus d’envoyer des courriers électroniques à partir de l’infrastructure d’envoi de n’importe quel domaine.

Par exemple, vous autorisez la paire de domaines suivante à envoyer des messages falsifiés dans votre organisation :

- *Domaine usurpé* : gmail.com "
- *Infrastructure d’envoi* `tms.mx.com` :

Seul le courrier électronique provenant de cette paire de domaines sera autorisé à usurper. Les autres expéditeurs tentant d’usurper gmail.com ne sont pas autorisés. Les messages dans d’autres domaines de tms.mx.com sont vérifiés par l’aide à l’usurpation d’identité.

## <a name="related-topics"></a>Rubriques connexes

[Protection contre l’usurpation d’identité dans Microsoft 365](anti-spoofing-protection.md)
