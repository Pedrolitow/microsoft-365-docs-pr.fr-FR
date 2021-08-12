---
title: Appliquer automatiquement une étiquette de confidentialité au contenu dans Microsoft 365
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
description: Lorsque vous créez une étiquette de confidentialité, vous pouvez attribuer automatiquement une étiquette aux fichiers et aux courriers électroniques, ou vous pouvez inviter les utilisateurs à sélectionner l’étiquette que vous recommandez.
ms.openlocfilehash: ae51d32343bbcf81d2d659121f475837cf0abe95
ms.sourcegitcommit: 60cc1b2828b1e191f30ca439b97e5a38f48c5169
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2021
ms.locfileid: "53541437"
---
# <a name="apply-a-sensitivity-label-to-content-automatically"></a>Appliquer automatiquement une étiquette de confidentialité au contenu

>*[Guide de sécurité et conformité pour les licences Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

> [!NOTE]
> Si vous souhaitez en savoir plus sur l’application automatique des étiquette de confidentialité dans Azure Purview (préversion), consultez l’article [Étiqueter automatiquement votre contenu dans Azure Purview](/azure/purview/create-sensitivity-label).

Lorsque vous créez une étiquette de confidentialité, vous pouvez attribuer automatiquement cette étiquette au contenu lorsque celle-ci répond aux conditions que vous spécifiez.

La possibilité d’appliquer automatiquement des étiquettes à du contenu est importante pour les raisons suivantes :

- Vous n’avez pas besoin de former vos utilisateurs pour leur apprendre à utiliser chacune de vos classifications.

- Vous n’avez pas à dépendre des utilisateurs pour classer correctement tout le contenu.

- Vos utilisateurs n’ont plus besoin de connaître vos stratégies. À la place, ils peuvent porter leur attention sur leur travail.

Lorsque le contenu est étiqueté manuellement, l’étiquette n’est jamais remplacée par l’étiquetage automatique. Toutefois, l’étiquetage automatique peut remplacer une [étiquette de priorité inférieure](sensitivity-labels.md#label-priority-order-matters) qui a été appliquée automatiquement.

Deux méthodes s’offrent à vous pour appliquer automatiquement une étiquette de confidentialité au contenu dans Microsoft 365 :

- **Étiquetage côté client lorsque les utilisateurs modifient des documents ou rédigent des e-mails (lorsqu’ils répondent ou transfèrent un e-mail également)** : utilisez une étiquette configurée pour l’étiquetage automatique des fichiers et des e-mails (cela inclut Word, Excel, PowerPoint et Outlook).

    Cette méthode prend en charge la recommandation d’une étiquette aux utilisateurs ainsi que l’application automatique d’une étiquette. Dans les deux cas, l’utilisateur décide d’accepter ou de refuser l’étiquette afin de garantir l’étiquetage correct du contenu. Cet étiquetage côté client présente un délai minimal pour les documents, car l’étiquette peut être appliquée avant même que le document ne soit enregistré. Cependant, toutes les applications clientes ne prennent pas en charge l’étiquetage automatique. Cette fonctionnalité est prise en charge par le client d’étiquetage unifié Azure Information Protection et par [certaines versions d’Office](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps).

    Pour des instructions de configuration, consultez l’article [Comment configurer l’étiquetage automatique pour les applications Office](#how-to-configure-auto-labeling-for-office-apps) sur cette page.

- **Étiquetage côté service lorsque le contenu est déjà enregistré (dans SharePoint ou dans OneDrive) ou est envoyé par e-mail (traité par Exchange Online)** : utilisez une stratégie d’étiquetage automatique.

    Cette méthode est également appelée étiquetage automatique des données au repos (documents dans SharePoint et dans OneDrive) et des données en transit (e-mails envoyés ou reçus par Exchange). Dans le cas d’Exchange, cela n’inclut pas les e-mails au repos (boîtes aux lettres).

    Comme cet étiquetage est appliqué par les services plutôt que par les applications, vous n’avez pas à vous soucier des applications des utilisateurs et de leur version. Par conséquent, cette fonctionnalité est immédiatement disponible dans toute l’organisation et est appropriée pour l’étiquetage à grande échelle. Les stratégies d’étiquetage automatique ne prennent pas en charge l’étiquetage recommandé, car l’utilisateur n’interagit pas avec le processus d’étiquetage. En effet, l’administrateur exécute les stratégies en mode simulation pour s’assurer que le contenu est correctement étiqueté avant d’appliquer réellement l’étiquette.

    Pour des instructions de configuration, consultez l’article [Configurer les stratégies d’étiquetage automatique pour SharePoint, OneDrive et Exchange](#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange) sur cette page.

    Spécifique à l’étiquetage automatique pour SharePoint et OneDrive :
    - Les fichiers Office sont pris en charge dans Word, PowerPoint et Excel. Le format Open XML est pris en charge (par exemple, .docx et .xlsx), mais pas le format Microsoft Office 97-2003 (par exemple, .doc et .xls).
        - Ces fichiers peuvent être étiquetés automatiquement au repos avant ou après la création des stratégies d’étiquette automatique. Les fichiers ne peuvent pas être étiquetés automatiquement s’ils font partie d’une session ouverte (le fichier est ouvert).
        - Les pièces jointes aux éléments de liste ne sont actuellement pas prises en charge et ne seront pas étiquetées automatiquement.
    - Jusqu’à 25 000 fichiers automatiquement étiquetés dans votre client par jour.
    - Jusqu’à 10 stratégies d’attribution automatique de nom par client, chacune ciblant 10 sites (SharePoint ou OneDrive).
    - Les valeurs existantes pour modifié, modifié par et la date ne sont pas changées du fait des stratégies d’étiquetage automatique pour le mode de simulation et lors de l’application des étiquettes.
    - Lorsque l’étiquette applique le chiffrement, [l’émetteur des droits de gestion et le propriétaire de la gestion des droits](/azure/information-protection/configure-usage-rights#rights-management-issuer-and-rights-management-owner) correspond au dernier compte qui a modifié le fichier.

    Spécifique à l’étiquetage automatique pour Exchange :
    - Contrairement à l’étiquetage manuel ou à l’étiquetage automatique avec les applications Office, les pièces jointes au format PDF ainsi que les pièces jointes Office (fichiers Word, Excel et PowerPoint) sont également analysées pour les conditions que vous spécifiez dans votre stratégie d’étiquetage automatique. Lorsqu’une correspondance est trouvée, l’e-mail est étiqueté, mais pas la pièce jointe.
        - Pour les fichiers PDF, si l’étiquette applique un chiffrement, ces fichiers sont chiffrés lorsque votre client est [activé pour les pièces jointes au format PDF](ome-faq.yml#are-pdf-file-attachments-supported-).
        - Pour ces fichiers Office, le format Open XML est pris en charge (par exemple, .docx et .xlsx), mais pas le format Microsoft Office 97-2003 (par exemple, .doc et .xls). Si l’étiquette applique un chiffrement, ces fichiers sont chiffrés.
    - Si vous disposez de règles de flux de messagerie Exchange ou de stratégies de protection contre la perte de données (DLP) qui appliquent le chiffrement IRM : l’étiquette est appliquée lorsque le contenu est identifié par ces règles ou ces stratégies et par une stratégie d’étiquetage automatique. Si cette étiquette applique le chiffrement, les paramètres IRM des règles de flux de messagerie Exchange ou des stratégies de protection contre la perte de données sont ignorés. Toutefois, si cette étiquette n’applique pas le chiffrement, les paramètres IRM des règles de flux de messagerie ou des stratégies de protection contre la perte de données sont appliqués en plus de l’étiquette.
    - Les e-mails dont le chiffrement IRM n’inclut aucune étiquette sont remplacés par une étiquette avec des paramètres de chiffrement lorsqu’il existe une correspondance à l’aide de l’étiquetage automatique.
    - Les e-mails entrant sont étiquetés lorsqu’il existe une correspondance avec vos conditions d’étiquetage automatique :
        - Si l’étiquette est configurée pour le [chiffrement](encryption-sensitivity-labels.md), celui-ci n’est pas appliqué.
        - Si l’étiquette est configurée pour appliquer des [marquages dynamiques](sensitivity-labels-office-apps.md#dynamic-markings-with-variables), sachez que cela peut donner lieu à des noms de personnes hors de votre organisation.
    - Lorsque l’étiquette applique le chiffrement, [l’émetteur des droits de gestion et le propriétaire de la gestion des droits](/azure/information-protection/configure-usage-rights#rights-management-issuer-and-rights-management-owner) correspond à la personne qui envoie le courrier électronique. Il n’existe actuellement aucun moyen de définir le propriétaire du gestionnaire des droits pour tous les e-mails entrants qui sont automatiquement chiffrés.


## <a name="compare-auto-labeling-for-office-apps-with-auto-labeling-policies"></a>Comparer l’étiquetage automatique pour les applications Office et les stratégies d’étiquetage automatique

Utilisez le tableau suivant pour vous aider à déterminer les différences de comportement de ces deux méthodes d’étiquetage automatiques complémentaires :

|Fonctionnalité ou comportement|Paramètre de l’étiquette : étiquetage automatique des fichiers et des e-mails  |Stratégie : étiquetage automatique|
|:-----|:-----|:-----|
|Dépendance de l’application|[Oui](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps) |Non \* |
|Limiter par emplacement|Non |Oui |
|Conditions : classifieurs formés|Oui |Non |
|Conditions : options de partage et options supplémentaires pour le courrier électronique|Non |Oui |
|Conditions : exceptions|Non |Oui (e-mail uniquement) |
|Recommandations, info-bulle de stratégie et remplacements de l’utilisateur|Oui |Non |
|Mode simulation|Non |Oui |
|Pièces jointes Exchange vérifiées pour les conditions|Non | Oui|
|Appliquer des marquages visuels |Oui |Oui (e-mail uniquement) |
|Remplacer le chiffrement IRM appliqué sans étiquette|Oui, si l’utilisateur dispose du droit d’utilisation minimal d’exportation |Oui (e-mail uniquement) |
|Étiquette du courrier électronique entrant|Non |Oui|

\* L’étiquetage automatique n’est actuellement pas disponible dans toutes les régions. Si votre client ne prend pas en charge cette fonctionnalité, l’onglet Étiquetage automatique n’apparaît pas dans le centre d’étiquettes d’administrateurs.

## <a name="how-multiple-conditions-are-evaluated-when-they-apply-to-more-than-one-label"></a>Comment plusieurs conditions sont évaluées lorsqu’elles s’appliquent à plusieurs étiquettes

Les étiquettes sont classées pour évaluation en fonction de leur position que vous spécifiez dans la stratégie: l’étiquette positionné a tout d’abord la position la plus basse (au moins sensible) et l’étiquette positionnée a dernière position plus élevée (plus sensible). Pour plus d’informations sur la priorité, voir [Priorité étiquettes (ordre aspects importants)](sensitivity-labels.md#label-priority-order-matters).

## <a name="dont-configure-a-parent-label-to-be-applied-automatically-or-recommended"></a>Ne configurez pas une étiquette parent pour l’appliquer automatiquement ou la recommander.

Une étiquette parent (une étiquette comportant des sous-étiquettes) ne peut pas être appliquée au contenu. Assurez-vous de ne pas configurer d’étiquette parent pour qu’elle soit appliquée automatiquement ou recommandée dans les applications Office ; ne sélectionnez pas d’étiquette parent pour une stratégie d’attribution automatique d’étiquette. Dans le cas contraire, l’étiquette parent ne sera pas appliquée au contenu.

Pour utiliser l’étiquetage automatique avec des sous-étiquettes, assurez-vous de publier l’étiquette parent et la sous-étiquette.

Pour en savoir plus sur les étiquettes parents et les sous-étiquettes, consultez la section [Sous-étiquettes (regroupement d’étiquettes)](sensitivity-labels.md#sublabels-grouping-labels).

## <a name="how-to-configure-auto-labeling-for-office-apps"></a>Comment configurer l’étiquetage automatique pour les applications Office

L’étiquetage automatique dans les applications Office pour Windows est pris en charge par le client d’étiquetage unifié Azure Information Protection. Pour l’étiquetage intégré dans les applications Office, cette fonctionnalité est disponible dans [Différentes étapes de disponibilité pour différentes applications](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps).

Les paramètres d’étiquetage automatique des applications Office sont disponibles lorsque vous [créer ou modifier une étiquette de confidentialité](create-sensitivity-labels.md). Assurez-vous que **Fichiers et e-mails** est sélectionné comme étendue de l’étiquette :

![Options d’étendue des étiquettes de confidentialité pour les fichiers et les e-mails](../media/filesandemails-scope-options-sensitivity-label.png)

Lorsque vous parcourez l’Assistant, la page **Étiquetage automatique des fichiers et e-mails** s’affiche. Sur cette page, vous pouvez choisir des options parmi une liste de types d’informations sensibles ou de classifieurs entraînables :

![Conditions de l’étiquetage automatique dans les applications Office](../media/sensitivity-labels-conditions.png)

Lorsqu’une étiquette de confidentialité est appliquée automatiquement, l’utilisateur voit une notification dans son application Office. Par exemple :

![Notification dont un document disposait d’une étiquette appliquée automatiquement](../media/sensitivity-labels-msg-doc-was-auto-labeled.PNG)

### <a name="configuring-sensitive-info-types-for-a-label"></a>Configuration des types d’informations sensibles pour une étiquette

Lorsque vous sélectionnez l’option **types d’informations sensibles**, vous voyez la même liste de types d'informations sensibles que lorsque vous créez une stratégie de protection contre la perte des données (DLP, data loss prevention). Par exemple, vous pouvez appliquer automatiquement une étiquette hautement confidentiel à tout contenu ayant des informations d’identification personnelle (PII) de clients, comme les numéros de carte de crédit ou les numéros de sécurité sociale :

![Types d’informations sensibles pour l’étiquetage automatique dans les applications Office](../media/sensitivity-labels-sensitive-info-types.png)

De même, lorsque vous configurez les stratégies DLP, vous pouvez affiner votre condition en modifiant le nombre d’instances et la précision de correspondance. Par exemple :

![Options de précision de correspondance et de nombre d’instances](../media/sit-confidence-level.png)

Vous pouvez en savoir plus sur ces options de configuration dans la documentation de DLP : [Optimisation des règles pour une correspondance plus facile ou plus difficile](data-loss-prevention-policies.md#tuning-rules-to-make-them-easier-or-harder-to-match).

De même, de même que la configuration de stratégie DLP, vous pouvez choisir si une condition doit détecter tous les types d’informations sensibles ou seulement l’un d’eux. Pour améliorer la flexibilité ou la complexité de vos conditions, vous pouvez ajouter [des groupes et utiliser des opérateurs logiques entre les groupes](data-loss-prevention-policies.md#grouping-and-logical-operators).

> [!NOTE]
> L’étiquetage automatique basé sur des types d’informations sensibles personnalisés s’applique uniquement au contenu nouvellement créé ou modifié dans OneDrive et SharePoint ; pas au contenu existant. Cette limitation s’applique également aux stratégies d’étiquetage automatique.

### <a name="configuring-trainable-classifiers-for-a-label"></a>Configuration des classifieurs pouvant être formés pour une étiquette

Cette option est actuellement en préversion. Si vous utilisez cette option, assurez-vous d’avoir publié dans votre client au moins une autre étiquette de confidentialité configurée pour l’étiquetage automatique et [l’option Types d’informations sensibles](#configuring-sensitive-info-types-for-a-label).

Lorsque vous sélectionnez l’option **Classifieurs pouvant être formés**, sélectionnez un ou plusieurs classifieurs pouvant être formés prédéfinis. Si vous avez créé vos propres classifieurs pouvant être formés personnalisés, vous pouvez également les sélectionner :

![Options pour les classifieurs pouvant être formés et les étiquettes de confidentialité](../media/sensitivity-labels-classifers.png)

Pour plus d’informations sur ces classifieurs, voir [En savoir plus sur les classifieurs de formation](classifier-learn-about.md).

Pendant la période de préversion pour cette option, les applications suivantes prennent en charge les classifieurs pouvant être formés pour les étiquettes de confidentialité :

- Les applications Microsoft 365 pour les entreprises ([anciennement Office 365 ProPlus](/deployoffice/name-change)) pour Windows, actuellement en cours de déploiement sur le [Canal actuel](/deployoffice/overview-update-channels#current-channel-overview) dans la version 2006 et les versions ultérieures :
    - Word
    - Excel
    - PowerPoint

- Office pour les applications Web, lorsque vous avez [activé les étiquettes de confidentialité pour les fichiers Office dans SharePoint et OneDrive](sensitivity-labels-sharepoint-onedrive-files.md) :
    - Word
    - Excel
    - PowerPoint
    - Outlook

### <a name="recommend-that-the-user-applies-a-sensitivity-label"></a>Recommander que l’utilisateur applique une étiquette de critère de sensibilité

Si vous le souhaitez, vous pouvez recommander à vos utilisateurs qu’ils appliquent l’étiquette. Cette option permet à vos utilisateurs d’accepter la classification et toute protection associée ou faire disparaitre la valeur recommandée si l’étiquette n’est pas adaptée à leur contenu.

![Option pour recommander une étiquette de confidentialité à des utilisateurs](../media/Sensitivity-labels-Recommended-label-option.png)

Voici un exemple d’une invite du client de l’étiquetage unifié d’Azure Information Protection lorsque vous configurez une condition pour appliquer une étiquette comme action recommandée avec un conseil de stratégie personnalisé. Vous pouvez choisir le texte qui s’affiche dans le conseil de stratégie.

![Invite à appliquer une étiquette recommandée](../media/Sensitivity-label-Prompt-for-required-label.png)

### <a name="when-automatic-or-recommended-labels-are-applied"></a>Quand les étiquettes automatiques ou recommandées sont appliquées

L’implémentation de l’étiquetage automatique et recommandé dans les applications Office varie selon que vous utilisez l’étiquetage intégré à Office ou le client de l’étiquetage unifié d’Azure Information Protection. Toutefois, dans les deux cas :

- Vous ne pouvez pas utiliser l’étiquetage automatique pour les documents et les e-mails qui ont été précédemment étiquetés manuellement ou automatiquement avec un niveau de confidentialité supérieur. N’oubliez pas que vous ne pouvez appliquer qu’une seule étiquette de confidentialité à un document ou un e-mail (en plus d’une seule étiquette de rétention).

- Vous ne pouvez pas utiliser l’étiquetage recommandé pour les documents ou e-mails qui ont été précédemment étiquetés avec un niveau de confidentialité supérieur. Lorsque le contenu est déjà étiqueté avec un niveau de confidentialité supérieur, l’utilisateur ne voit pas l’invite avec la recommandation et le conseil de stratégie.

Spécifique à l’étiquetage intégré :

- Les applications Office ne prennent pas toutes en charge l’étiquetage automatique (et recommandé). Pour plus d’informations, voir [Prise en charge des fonctionnalités d’étiquettes de confidentialité dans les applications](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps).

- Pour les étiquettes recommandées dans les versions de bureau de Word, le contenu sensible ayant déclenché la recommandation est signalé de sorte que les utilisateurs puissent examiner et supprimer le contenu sensible au lieu d’appliquer l’étiquette de confidentialité recommandée.

- Pour plus d’informations sur l’application de ces étiquettes dans les applications Office, les captures d’écran et la détection d’informations sensibles, voir [Appliquer ou recommander automatiquement des étiquettes de confidentialité à vos fichiers et e-mails dans Office](https://support.office.com/fr-FR/article/automatically-apply-or-recommend-sensitivity-labels-to-your-files-and-emails-in-office-622e0d9c-f38c-470a-bcdb-9e90b24d71a1).

Spécifique au client d’étiquetage unifié Azure Information Protection :

-  L’étiquetage automatique et recommandé s’applique à Word, Excel et PowerPoint lors de l’enregistrement d’un document et à Outlook lorsque vous envoyez un courrier électronique.

- Pour qu’Outlook prenne en charge l’étiquetage recommandé, vous devez commencer par configurer un [paramètre de stratégie avancé](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#enable-recommended-classification-in-outlook).

- Les informations sensibles peuvent être détectées dans le corps de texte dans les documents et les courriers électroniques, ainsi que dans les en-têtes et pieds de page, mais pas dans la ligne d’objet ni dans les pièces jointes du courrier électronique.

## <a name="how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange"></a>Configurer les stratégies d’étiquetage automatique pour SharePoint, OneDrive et Exchange

N’oubliez pas de connaître les conditions préalables avant de configurer les stratégies d’attribution automatique d’étiquette.

### <a name="prerequisites-for-auto-labeling-policies"></a>Conditions préalables pour les stratégies d’étiquetage automatique

- Mode de simulation :
    - L’audit pour Microsoft 365 doit être activé. Si vous devez activer l’audit ou si vous ne savez pas celui-ci est déjà activé, consultez l’article [Activer ou désactiver la recherche dans un journal d’audit](turn-audit-log-search-on-or-off.md).
    - Pour afficher le contenu d’un fichier ou d’un e-mail en mode Source, vous devez disposer du rôle de **Visionneuse de contenu de l’Explorateur de contenu**. Par défaut, les administrateurs généraux n’ont pas ce rôle. Si vous n’avez pas cette autorisation, le volet Aperçu ne s’affiche pas lorsque vous sélectionnez un élément dans l’onglet **Éléments correspondants**.

- Pour étiqueter automatiquement des fichiers dans SharePoint et OneDrive :
    - Vous avez [activé les étiquettes de confidentialité pour les fichiers Office dans SharePoint et OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).
    - Lors de l’exécution de la stratégie d’étiquetage automatique, le fichier ne doit pas être ouvert par un autre processus ni un autre utilisateur. Un fichier examiné pour la modification est inclus dans cette catégorie.

- Si vous envisagez d’utiliser des [types d’informations sensibles personnalisés](sensitive-information-type-learn-about.md) plutôt que les types de sensibilité prédéfinis :
    - Les types d’informations de confidentialité personnalisées s’appliquent uniquement au contenu ajouté ou modifié dans SharePoint ou OneDrive une fois les types d’informations de confidentialité personnalisés créés.
    - Pour tester de nouveaux types d’informations sensibles personnalisés, créez-les avant de créer votre stratégie d’étiquetage automatique, puis créez de nouveaux documents avec des exemples de données pour pouvoir les tester.

- Une ou plusieurs étiquettes de confidentialité [créées et publiées](create-sensitivity-labels.md) (à au moins un utilisateur) que vous pouvez sélectionner pour vos stratégies d’étiquetage automatique. Pour ces étiquettes :
    - Cela n’a pas d’importance si le paramètre d’étiquetage automatique dans les applications Office est activé ou désactivé, car ce paramètre d’étiquette complète les stratégies d’étiquetage automatique, comme expliqué dans l’introduction.
    - Si les étiquettes que vous souhaitez utiliser pour l’étiquetage automatique sont configurées pour utiliser les marquages visuels (en-têtes, pieds de page, filigranes), notez que ceux-ci ne sont pas appliqués aux documents.
    - Si les étiquettes appliquent le [chiffrement](encryption-sensitivity-labels.md) :
        - Lorsque la stratégie d’étiquetage automatique inclut des emplacements pour SharePoint ou OneDrive, vous devez configurer l’étiquette pour le paramètre **Attribuer des autorisations maintenant**.
        - Lorsque la stratégie d’étiquetage automatique s’applique uniquement à Exchange, vous pouvez configurer l’étiquette pour **Attribuer des autorisations maintenant** ou **Autoriser les utilisateurs à attribuer des autorisations** (pour les options Ne pas transférer ou Chiffrer uniquement).

### <a name="learn-about-simulation-mode"></a>En savoir plus sur le mode simulation

Le mode simulation est propre aux stratégies d’étiquetage automatique et est intégré au flux de travail. Vous ne pourrez étiqueter automatiquement les documents et les courriers que lorsque votre stratégie aura exécuté au moins une simulation.

Flux de travail pour une stratégie d’étiquetage automatique :

1. Créer et configurer une stratégie d’étiquetage automatique.

2. Exécutez la stratégie en mode de simulation, ce qui peut prendre 48 heures.

3. Examinez les résultats et, si nécessaire, affinez votre stratégie. Réexécutez le mode de simulation et attendez sa fin.

4. Répétez l’étape 3 si besoin.

5. Déployez en production.

Le déploiement simulé s’exécute comme le paramètre WhatIf pour PowerShell. Vous voyez les résultats signalés comme si la stratégie d’étiquetage automatique avait appliqué l’étiquette sélectionnée en utilisant les règles que vous avez définies. Vous pouvez ensuite affiner vos règles de précision si nécessaire et exécuter de nouveau la simulation. Cependant, comme l’étiquetage automatique pour Exchange s’applique aux courriers envoyés et reçus, plutôt qu’aux courriers stockés dans les boîtes aux lettres, ne vous attendez pas à ce que les résultats des courriers dans une simulation soient cohérents, sauf si vous êtes en mesure d’envoyer et de recevoir exactement les mêmes courriers électroniques.

Le mode simulation vous permet également d’augmenter progressivement l’étendue de votre stratégie d’étiquetage automatique avant de procéder au déploiement. Par exemple, vous pouvez commencer avec un seul emplacement, comme un site SharePoint, avec une seule bibliothèque de documents. Ensuite, avec des modifications itératives, augmentez l’étendue sur plusieurs sites, puis sur un autre emplacement, comme OneDrive.

Enfin, vous pouvez utiliser le mode simulation pour fournir une approximation du temps nécessaire à l’exécution de votre stratégie d’étiquetage automatique et pour vous aider à planifier et à programmer l’exécution sans le mode simulation.

### <a name="creating-an-auto-labeling-policy"></a>Création d’une stratégie d’étiquetage automatique

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com/), accédez aux étiquettes de confidentialité :

    - **Solutions** > **Information protection**

    Si vous ne voyez pas immédiatement cette option, sélectionnez tout d’abord **Tout afficher**.

2. Sélectionnez l’onglet **Étiquetage automatique** :

    ![Onglet étiquetage automatique](../media/auto-labeling-tab.png)

    > [!NOTE]
    > Si vous ne voyez pas l’onglet **Étiquetage automatique**, cette fonctionnalité n’est pas disponible dans votre pays ou région.

3. Sélectionnez **+ créer une stratégie d’étiquetage automatique**. Cette opération démarre l’Assistant Nouvelle stratégie :

    ![Assistant Nouvelle stratégie pour l’étiquetage automatique](../media/auto-labeling-wizard.png)

4. Pour la page **Choisir les informations auxquelles vous souhaitez appliquer cette étiquette** : sélectionnez un modèle, par exemple, **Financier** or **Confidentialité**. Vous pouvez affiner votre recherche à l’aide du menu déroulant **Afficher les options pour**. Vous pouvez également sélectionner **Stratégie personnalisée** si les modèles ne répondent pas à vos besoins. Sélectionnez **Suivant**.

5. Pour la page **Nommer votre stratégie d’étiquetage automatique** : donnez un nom unique et éventuellement une description pour vous aider à identifier l’étiquette, les emplacements et les conditions appliqués automatiquement qui identifient le contenu à étiqueter.

6. Pour la page **Choisir les emplacements dans lesquels vous souhaitez appliquer l’étiquette** : sélectionner et spécifier les emplacements pour Exchange, les sites SharePoint et OneDrive. Ensuite, sélectionnez **Suivant**.

    ![Choisir la page emplacements auto-labelingwizard](../media/locations-auto-labeling-wizard.png)

    Vous devez spécifier des sites SharePoint et des comptes OneDrive individuels. Pour OneDrive, l’URL du compte d’un utilisateur OneDrive est au format suivant : `https://<tenant name>-my.sharepoint.com/personal/<user_name>_<tenant name>_com`

    Par exemple, pour un utilisateur du client contoso dont le nom d’utilisateur est « rsimone » : `https://contoso-my.sharepoint.com/personal/rsimone_contoso_onmicrosoft_com`

    Pour vérifier la syntaxe de votre client et identifier les URL des utilisateurs, voir [Obtenir la liste de toutes les URL OneDrive utilisateur de votre organisation](/onedrive/list-onedrive-urls).

7. Pour la **configurer les règles courantes ou avancées** page : conservez la valeur par défaut de **règles courantes** pour définir des règles qui identifient le contenu à étiqueter dans tous les emplacements sélectionnés. Si vous avez besoin de règles différentes pour chaque emplacement, sélectionnez **Paramètres avancés**. Ensuite, sélectionnez **Suivant**.

    Les règles utilisent des conditions qui incluent des types d’informations sensibles et des options de partage :
    - Vous pouvez sélectionner des types d’informations sensibles intégrés et personnalisés.
    - Pour les options partagées, vous pouvez choisir **uniquement avec des personnes au sein de mon organisation** ou **avec des personnes extérieures à mon organisation**.

    Si votre seul emplacement est **Exchange**, ou si vous sélectionnez **Paramètres avancés**, vous pouvez sélectionner des conditions supplémentaires :
    - L’adresse IP de l’expéditeur est
    - Le domaine du destinataire est
    - Le destinataire est
    - L’extension du fichier de pièce jointe est
    - La pièce jointe est protégée par mot de passe
    - Le contenu de la pièce jointe n’a pas pu être analysé
    - L’analyse du contenu de la pièce jointe n’a pas été terminée
    - L’en-tête correspond aux modèles
    - L’objet correspond aux modèles
    - L'adresse du destinataire contient les mots
    - L’adresse du destinataire correspond aux modèles
    - L’adresse de l’expéditeur correspond aux modèles
    - Le domaine de l’expéditeur est
    - Le destinataire est membre de
    - L’expéditeur est

    Pour chacune de ces conditions, vous pouvez ensuite spécifier des exceptions.

8. Selon vos choix précédents, vous aurez maintenant la possibilité de créer des règles à l’aide de conditions et d’exceptions.

    Les options de configuration pour les types d’informations sensibles sont identiques à celles que vous sélectionnez pour l’étiquetage automatique pour les applications Office. Si vous souhaitez en savoir plus, consultez l’article [Configuration des types d’informations sensibles pour une étiquette](#configuring-sensitive-info-types-for-a-label).

    Lorsque vous avez défini toutes les règles dont vous avez besoin et confirmé que leur état est activé, sélectionnez **suivant** pour passer à la sélection automatique d’une étiquette.

11. Pour la page **Choisir une étiquette à appliquer automatiquement** : sélectionnez **+ Choisir une étiquette**, puis, sélectionnez une étiquette dans le volet **Choisir une étiquette de confidentialité**, et enfin, sélectionnez **Suivant**.

12. Pour les **décidez si vous voulez tester la stratégie maintenant ou plus tard** page : sélectionnez **exécuter la stratégie en mode de simulation** si vous êtes prêt à exécuter la stratégie d’attribution automatique d’étiquette maintenant, en mode de simulation. Dans le cas contraire, sélectionnez **Stratégie désactivée**. Sélectionnez **suivant** :

    ![Tester l’Assistant attribution automatique d’étiquette de stratégie](../media/simulation-mode-auto-labeling-wizard.png)

13. Pour la page **Résumé** : consultez la configuration de votre stratégie d’étiquetage automatique et apportez les modifications nécessaires, puis terminez l’Assistant.

Désormais, sur la page **Protection des informations**  >  onglet **Etiquetage automatique**, vous pouvez voir votre stratégie d’attribution automatique dans les sections **Simulation** ou **Désactivée**, selon que vous avez choisi de l’exécuter en mode de simulation ou non. Sélectionnez votre stratégie pour afficher les détails de la configuration et de son état (par exemple, **La simulation de stratégie est en cours d’exécution**). Pour les stratégies en mode simulation, sélectionnez l’onglet **éléments correspondants** pour afficher les messages électroniques ou les documents correspondants aux règles que vous avez spécifiées.

Vous pouvez modifier votre stratégie directement à partir de cette interface :

- Pour une stratégie dans la section **Désactivé**, sélectionnez le bouton **Modifier la stratégie**.

- Pour la stratégie dans la section de la **simulation** de, sélectionnez l’option **modifier la stratégie** en haut de la page, sous l’un des onglets suivants :

    ![Modifier les options d’une stratégie d’étiquetage automatique](../media/auto-labeling-edit.png)

    Lorsque vous êtes prêt à exécuter la stratégie sans simulation, sélectionnez l’option **Activer la stratégie**.

Vos stratégies automatiques fonctionnent en continu jusqu’à leur suppression. Par exemple, les documents nouveaux et modifiés sont inclus dans les paramètres de la stratégie actuelle.

Vous pouvez également afficher les résultats de votre stratégie d’étiquetage automatique à l’aide de l’[explorateur de contenu](data-classification-content-explorer.md) lorsque vous disposez des [autorisations](data-classification-content-explorer.md#permissions) appropriées :
- La **visionneuse de liste de l’Explorateur de contenu** vous permet de voir l’étiquette d’un fichier, mais pas le contenu du fichier.
- La **visionneuse de contenu de l’Explorateur de contenu** vous permet de voir le contenu du fichier.

> [!TIP]
> Vous pouvez également utiliser l’Explorateur de contenu pour identifier les emplacements qui ont des documents contenant des informations sensibles, mais qui ne sont pas étiquetés. À l’aide de ces informations, songez à ajouter ces emplacements à votre stratégie d’étiquetage automatique, et incluez les types d’informations sensibles identifiés comme règles.

### <a name="use-powershell-for-auto-labeling-policies"></a>Utiliser PowerShell pour les stratégies d’étiquetage automatique

Vous pouvez utiliser l’[Interface PowerShell du Centre de sécurité et conformité](/powershell/exchange/scc-powershell) pour créer et configurer les stratégies d’étiquetage automatique. Cela signifie que vous pouvez créer des scripts pour une prise en charge complète de la création et de la maintenance de vos stratégies d’étiquetage automatique, ce qui permet également de spécifier plus efficacement plusieurs URL pour les emplacements OneDrive et SharePoint.

Avant d’exécuter les commandes dans PowerShell, vous devez tout d’abord vous [connecter au Centre de sécurité et conformité PowerShell](/powershell/exchange/connect-to-scc-powershell).

Pour créer une stratégie d’étiquetage automatique :

```powershell
New-AutoSensitivityLabelPolicy -Name <AutoLabelingPolicyName> -SharePointLocation "<SharePointSiteLocation>" -ApplySensitivityLabel <Label> -Mode TestWithoutNotifications
```
Cette commande crée une stratégie d’étiquetage automatique pour un site SharePoint que vous spécifiez. Pour un emplacement OneDrive, utilisez plutôt le paramètre *OneDriveLocation*.

Pour ajouter des sites à une stratégie d’étiquetage automatique existante :

```powershell
$spoLocations = @("<SharePointSiteLocation1>","<SharePointSiteLocation2>")
Set-AutoSensitivityLabelPolicy -Identity <AutoLabelingPolicyName> -AddSharePointLocation $spoLocations -ApplySensitivityLabel <Label> -Mode TestWithoutNotifications
```

Cette commande spécifie les URL SharePoint supplémentaires dans une variable qui est ensuite ajoutée à une stratégie d’étiquetage automatique existante. Pour ajouter à la place des emplacements OneDrive, utilisez le paramètre *AddOneDriveLocation* avec une variable différente, comme *$OneDriveLocations*.

Pour créer une règle de stratégie d’étiquetage automatique :

```powershell
New-AutoSensitivityLabelRule -Policy <AutoLabelingPolicyName> -Name <AutoLabelingRuleName> -ContentContainsSensitiveInformation @{"name"= "a44669fe-0d48-453d-a9b1-2cc83f2cba77"; "mincount" = "2"} -Workload SharePoint
```

Pour une stratégie d’étiquetage automatique existante, cette commande crée une règle de stratégie afin de détecter les informations sensibles de type **Numéro de sécurité sociale américain (SSN)**, dont l’ID d’entité est a44669fe-0d48-453d-a9b1-2cc83f2cba77. Pour trouver les ID d’entité d’autres types d’informations sensibles, voir [Définitions des entités de types d’informations sensibles](sensitive-information-type-entity-definitions.md).

Pour plus d’informations sur les applets de commande PowerShell qui prennent en charge les stratégies d’étiquetage automatique, leurs paramètres disponibles et quelques exemples, voir l’aide des applet de commande suivantes :

- [Get-AutoSensitivityLabelPolicy](/powershell/module/exchange/get-autosensitivitylabelpolicy)
- [New-AutoSensitivityLabelPolicy](/powershell/module/exchange/new-autosensitivitylabelpolicy)
- [New-AutoSensitivityLabelRule](/powershell/module/exchange/new-autosensitivitylabelrule)
- [Remove-AutoSensitivityLabelPolicy](/powershell/module/exchange/remove-autosensitivitylabelpolicy)
- [Remove-AutoSensitivityLabelRule](/powershell/module/exchange/remove-autosensitivitylabelrule)
- [Set-AutoSensitivityLabelPolicy](/powershell/module/exchange/set-autosensitivitylabelpolicy)
- [Set-AutoSensitivityLabelRule](/powershell/module/exchange/set-autosensitivitylabelrule)

## <a name="tips-to-increase-labeling-reach"></a>Conseils pour augmenter la portée de l’étiquetage

Bien que l’étiquetage automatique soit l’une des méthodes les plus efficaces pour classifier, étiqueter et protéger les fichiers Office appartenant à votre organisation, vérifiez si vous pouvez le compléter avec l’une des méthodes supplémentaires pour augmenter votre portée d’étiquetage :

- Lorsque vous utilisez le[Client d’étiquetage unifié Azure Information Protection](/azure/information-protection/rms-client/aip-clientv2) :

    - Pour les fichiers des magasins de données locaux tels que les partages réseau et les bibliothèques SharePoint Server : utilisez le [scanneur](/azure/information-protection/deploy-aip-scanner) pour découvrir des informations sensibles dans ces fichiers et les étiqueter de manière appropriée. Si vous envisagez de migrer ou de charger ces fichiers vers SharePoint dans Microsoft 365, utilisez le scanneur pour étiqueter les fichiers avant de les déplacer vers le cloud.

    - Si vous avez utilisé une autre solution d’étiquetage avant d’utiliser des étiquettes de confidentialité : utilisez PowerShell et [un paramètre avancé pour réutiliser les étiquettes](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#migrate-labels-from-secure-islands-and-other-labeling-solutions) à partir de ces solutions.

- Encouragez [d’étiquetage manuel](https://support.microsoft.com/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9) après avoir fourni aux utilisateurs une formation sur les étiquettes de confidentialité à appliquer. Lorsque vous êtes certain que les utilisateurs comprennent quelle étiquette appliquer, envisagez de configurer une étiquette par défaut et l’étiquetage obligatoire en tant que [paramètres de stratégie](sensitivity-labels.md#what-label-policies-can-do).

Par ailleurs, envisagez [de marquer nouveaux fichiers comme sensibles par défaut](/sharepoint/sensitive-by-default) dans SharePoint pour empêcher les invités d’accéder aux fichiers nouvellement ajoutés jusqu’à ce qu’au moins une stratégie DLP analyse le contenu du fichier.
