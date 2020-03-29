---
title: Appliquer automatiquement une étiquette sensibilité au contenu
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.service: O365-seccomp
ms.date: ''
localization_priority: Priority
ms.collection:
- M365-security-compliance
ms.topic: article
search.appverid:
- MOE150
- MET150
description: Lorsque vous créez une étiquette de critère de diffusion, vous pouvez affecter automatiquement une étiquette à un document ou message électronique ou vous pouvez inviter les utilisateurs pour sélectionner l’étiquette que vous recommandez.
ms.openlocfilehash: 7edfa83648ecb86ab23a898299edb63df851d123
ms.sourcegitcommit: 7eaecb91c7cb1f8679f99882563f5c1149175992
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "43022931"
---
# <a name="apply-a-sensitivity-label-to-content-automatically"></a>Appliquer automatiquement une étiquette sensibilité au contenu

Lorsque vous créez une étiquette de confidentialité, vous pouvez attribuer automatiquement une étiquette au contenu ayant des informations sensibles, ou vous pouvez inviter les utilisateurs à appliquer celle que vous recommandez.

La possibilité d’appliquer automatiquement des étiquettes à du contenu est importante pour les raisons suivantes :

- Vous n’avez pas besoin de former les utilisateurs concernant l’ensemble de vos classifications.

- Vous n’avez pas à dépendre des utilisateurs pour classer correctement tout le contenu.

- Les utilisateurs n’ont plus à connaître les stratégies de gouvernance des données : à la place, ils peuvent se concentrer sur leur travail.

L’étiquetage automatique dans les applications Office pour Windows est pris en charge par le client d’étiquetage unifié Azure Information Protection. Pour l’étiquetage intégré dans les applications Office, cette fonctionnalité est [en mode Aperçu pour certaines applications](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps).

Les paramètres d’étiquetage automatique des applications Office sont disponibles lorsque vous [créer ou modifier une étiquette de confidentialité](create-sensitivity-labels.md) :

![Options d’étiquetage automatique pour les étiquettes de confidentialité](../media/sensitivity-labels-auto-labeling-options.png)

## <a name="how-to-configure-auto-labeling-for-office-apps"></a>Comment configurer l’étiquetage automatique pour les applications Office

L’une des fonctionnalités les plus puissantes des étiquettes de confidentialité est la possibilité d’appliquer celles-ci automatiquement à tout contenu correspondant à des conditions spécifiques. Dans ce cas, les personnes au sein de votre organisation n’ont pas besoin d’appliquer les étiquettes de confidentialité. Office 365 s’en charge à leur place.

Vous pouvez choisir d’appliquer automatiquement des étiquettes de confidentialité au contenu lorsque celui-ci contient des types spécifiques d’informations sensibles. Choisissez parmi une liste de types d’informations ou de classifieurs sensibles :

![Conditions de l’étiquetage automatique dans les applications Office](../media/sensitivity-labels-conditions.png)

> [!NOTE]
> Pour le moment, l’option des **classifieurs** se présente sous la forme d’une version d’évaluation limitée et vous devez envoyer un formulaire à Microsoft pour activer cette fonctionnalité pour votre client. Pour plus d’informations, consultez l’article de blog [annonçant l'étiquetage automatique dans les applications Office à l'aide de classifieurs intégrés (édition limitée)](https://techcommunity.microsoft.com/t5/security-privacy-and-compliance/announcing-automatic-labeling-in-office-apps-using-built-in/ba-p/1192889).

Lorsqu’une étiquette de confidentialité est appliquée automatiquement, les utilisateurs voit une notification dans leur application Office. Par exemple :

![Notification dont un document disposait d’une étiquette appliquée automatiquement](../media/sensitivity-labels-msg-doc-was-auto-labeled.PNG)

### <a name="configuring-sensitive-info-types-for-a-label"></a>Configuration des types d’informations sensibles pour une étiquette

Lorsque vous sélectionnez l’option **types d’informations sensibles**, vous voyez la même liste de types d'informations sensibles que lorsque vous créez une stratégie de protection contre la perte des données (DLP, data loss prevention). Par exemple, vous pouvez appliquer automatiquement une étiquette hautement confidentiel à tout contenu ayant des informations d’identification personnelle (PII) de clients, comme les numéros de carte de crédit ou les numéros de sécurité sociale :

![Types d’informations sensibles pour l’étiquetage automatique dans les applications Office](../media/sensitivity-labels-sensitive-info-types.png)

Après avoir sélectionné vos types d’informations sensibles, vous pouvez affiner votre condition en modifiant le nombre d’instances ou la précision des correspondances. Pour plus d’informations, voir[Optimisation des règles afin de les rendre plus facile ou plus difficile à associer](data-loss-prevention-policies.md#tuning-rules-to-make-them-easier-or-harder-to-match).

De plus, vous pouvez choisir si une condition doit détecter tous les types d’informations sensibles ou seulement l’un d’eux. Pour améliorer la flexibilité ou la complexité de vos conditions, vous pouvez ajouter des groupes et utiliser des opérateurs logiques entre les groupes. Pour plus d’informations, voir [Regroupement et opérateurs logiques](data-loss-prevention-policies.md#grouping-and-logical-operators).

![Options pour le nombre d’instances et la précision des correspondances](../media/Sensitivity-labels-instance-count-match-accuracy.png)

### <a name="configuring-classifers-for-a-label"></a>Configuration des classifieurs pour une étiquette

Lorsque vous sélectionnez l’option **classifieurs**, sélectionnez un ou plusieurs classifieurs prédéfinis :

![Options pour les classifieurs et les étiquettes de sensibilité](../media/sensitivity-labels-classifers.png)

Pour plus d’informations sur ces classifieurs, voir [Prise en main des classifieurs d’entraînement (version d'essai)](classifier-getting-started-with.md).

Pendant la période d’évaluation, les applications suivantes prennent en charge les classifieurs pour les étiquettes de confidentialité :

- Applications de bureau Office 365 ProPlus pour Windows, de [Office Insider](https://office.com/insider) :
    - Word
    - Excel
    - PowerPoint

- Office pour les applications Web, lorsque vous avez [activé les étiquettes de confidentialité pour les fichiers Office dans SharePoint et OneDrive (préversion publique)](sensitivity-labels-sharepoint-onedrive-files.md) :
    - Word
    - Excel
    - PowerPoint
    - Outlook

## <a name="recommend-that-the-user-apply-a-sensitivity-label"></a>Recommandé que l’utilisateur applique une étiquette de critère de diffusion

Si vous le souhaitez, vous pouvez recommander à vos utilisateurs qu’ils appliquent l’étiquette. Cette option permet à vos utilisateurs d’accepter la classification et toute protection associée, ou d’ignorer la recommandation si l’étiquette ne convient pas à leur contenu.

![Option pour recommander une étiquette de confidentialité à des utilisateurs](../media/Sensitivity-labels-Recommended-label-option.png)

Voici un exemple d’une invite de commandes d’Azure Information Protection lorsque vous configurez une condition pour appliquer une étiquette comme action recommandée avec un conseil de stratégie personnalisé. Vous pouvez choisir le texte qui s’affiche dans le conseil de stratégie.

![Invite à appliquer une étiquette recommandée](../media/Sensitivity-label-Prompt-for-required-label.png)

## <a name="how-automatic-or-recommended-labels-are-applied"></a>Comment les étiquettes automatiques ou recommandées sont appliquées

L’implémentation de l’étiquetage automatique et recommandé dans les applications Office varie selon que vous utilisez l’étiquetage intégré à Office ou le client d’étiquetage unifié d’Azure Information Protection. Dans les deux cas, toutefois :

- Vous ne pouvez pas utiliser la classification automatique pour les documents et les e-mails qui ont été précédemment étiquetés manuellement ou automatiquement avec une classification supérieure. N’oubliez pas que vous ne pouvez appliquer qu’une seule étiquette de confidentialité à un document ou un e-mail (en plus d’une seule étiquette de rétention).

- Vous ne pouvez pas utiliser la classification recommandée pour les documents ou e-mails qui ont été étiquetés précédemment avec une classification supérieure. Lorsque le contenu est déjà étiqueté avec une classification supérieure, l'utilisateur ne voit pas l'invite avec la recommandation et le conseil de stratégie.

Spécifique à l’étiquetage intégré :

- Les applications Office ne prennent pas toutes en charge l’étiquetage automatique (et recommandé). Pour plus d’informations, voir [Prise en charge des fonctionnalités d’étiquettes de confidentialité dans les applications](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps).

- Pour les étiquettes recommandées dans les versions de bureau de Word, le contenu sensible ayant déclenché la recommandation est signalé de sorte que les utilisateurs puissent examiner et supprimer le contenu sensible au lieu d’appliquer l’étiquette de confidentialité recommandée.

- Pour plus d’informations sur l’application de ces étiquettes dans les applications Office, les captures d’écran et la détection d’informations sensibles, voir [Appliquer ou recommander automatiquement des étiquettes de confidentialité à vos fichiers et e-mails dans Office](https://support.office.com/en-us/article/automatically-apply-or-recommend-sensitivity-labels-to-your-files-and-emails-in-office-622e0d9c-f38c-470a-bcdb-9e90b24d71a1).

Spécifique au client d’étiquetage unifié Azure Information Protection :

-  L’étiquetage automatique et recommandé s’applique à Word, Excel et PowerPoint lors de l’enregistrement d’un document et à Outlook lorsque vous envoyez un courrier électronique.

- Pour qu’Outlook prenne en charge l’étiquetage recommandé, vous devez commencer par configurer un [paramètre de stratégie avancé](https://docs.microsoft.com/azure/information-protection/rms-client/clientv2-admin-guide-customizations#enable-recommended-classification-in-outlook).

- Les informations sensibles peuvent être détectées dans le corps de texte dans les documents et les courriers électroniques, ainsi que dans les en-têtes et pieds de page, mais pas dans la ligne d’objet ni dans les pièces jointes du courrier électronique.

## <a name="how-multiple-conditions-are-evaluated-when-they-apply-to-more-than-one-label"></a>Comment plusieurs conditions sont évaluées lorsqu’elles s’appliquent à plus d’une étiquette

Les étiquettes sont classées pour évaluation en fonction de leur position que vous spécifiez dans la stratégie: l’étiquette positionné a tout d’abord la position la plus basse (au moins sensible) et l’étiquette positionnée a dernière position plus élevée (plus sensible). Pour plus d’informations sur la priorité, voir [Priorité étiquettes (ordre aspects importants)](sensitivity-labels.md#label-priority-order-matters).

## <a name="dont-configure-a-parent-label-to-be-applied-automatically-or-recommended"></a>Ne configurez pas une étiquette parent pour l’appliquer automatiquement ou la recommander.

Une étiquette parent (une étiquette comportant des sous-étiquettes) ne peut pas être appliquée au contenu. Évitez de configurer une étiquette parent pour l’appliquer automatiquement ou la recommander, car elle ne sera pas appliquée au contenu des applications Office qui utilisent le client d’étiquetage unifié Azure Information Protection. Pour en savoir plus sur les étiquettes parents et les sous-étiquettes, consultez la section [Sous-étiquettes (regroupement d’étiquettes)](sensitivity-labels.md#sublabels-grouping-labels).
