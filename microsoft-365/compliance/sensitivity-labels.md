---
title: En savoir plus sur les étiquettes de niveau de confidentialité
f1.keywords:
- CSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- purview-compliance
- tier1
- highpri
- SPO_Content
- m365solution-mip
- m365initiative-compliance
- highpri
search.appverid:
- MOE150
- MET150
description: Découvrez comment les étiquettes de confidentialité de Microsoft Purview Information Protection peuvent protéger le contenu sensible de votre organisation, où qu’il soit stocké.
ms.custom:
- seo-marvel-apr2020
- seo-marvel-jun2020
ms.openlocfilehash: 6c14a533ecd52eb05f85c16cb562df4c689eabfd
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68626399"
---
# <a name="learn-about-sensitivity-labels"></a>En savoir plus sur les étiquettes de niveau de confidentialité

>*[Guide de sécurité et conformité pour les licences Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

> [!NOTE]
> Si vous recherchez des informations sur les étiquettes de niveau de confidentialité dans vos applications Office, consultez [Appliquer des étiquettes de confidentialité à vos fichiers et vos e-mails dans Office](https://support.microsoft.com/topic/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9).
>
> Les informations sur cette page sont destinées aux administrateurs informatiques qui peuvent créer et configurer ces étiquettes.

To get their work done, people in your organization collaborate with others both inside and outside the organization. This means that content no longer stays behind a firewall—it can roam everywhere, across devices, apps, and services. And when it roams, you want it to do so in a secure, protected way that meets your organization's business and compliance policies.

Les étiquettes de confidentialité de Protection des données Microsoft Purview vous permettent de classifier et protéger les données de votre organisation, tout en veillant à ce que la productivité des utilisateurs et leur aptitude à collaborer ne soient pas compromises.

Exemple illustrant les étiquettes de confidentialité disponibles dans Excel à partir de l’onglet **Accueil** du ruban. Dans cet exemple, l’étiquette appliquée affiche dans la barre d’état :

![Étiquette de confidentialité dans le ruban Excel et sur la barre d’état](../media/Sensitivity-label-in-Excel.png)

Pour appliquer des étiquettes de confidentialité, les utilisateurs doivent être connectés avec leur compte Microsoft 365 professionnel ou scolaire.

> [!NOTE]
> Pour les clients du gouvernement américain, les étiquettes de confidentialité sont prises en charge sur toutes les plateformes.
>
> Si vous utilisez le client d’étiquettes et le scanneur unifiés de Azure Information Protection, consultez la [Description du service public premium Azure Information Protection](/enterprise-mobility-security/solutions/ems-aip-premium-govt-service-description).

Vous pouvez utiliser les étiquettes de niveau de confidentialité aux fins suivantes :
  
- **Fournir des paramètres de protection qui incluent le chiffrement et les marquages de contenu.** Par exemple, appliquez une étiquette « Confidentiel » à un document ou un message électronique, et cette étiquette chiffre le contenu et applique un filigrane « Confidentiel ». Les marquages de contenu comprennent les en-têtes et les pieds de page, ainsi que les filigranes, et le chiffrement peut également limiter les mesures autorisées que les utilisateurs peuvent prendre sur le contenu.

- **Protéger le contenu dans les applications Office sur différents appareils et plateformes.** Pris en charge par Word, Excel, PowerPoint et Outlook sur les applications Office pour ordinateur de bureau et Office sur le web. Pris en charge sur Windows, macOS, iOS et Android.

- **Protect content in third-party apps and services** by using Microsoft Defender for Cloud Apps. With Defender for Cloud Apps, you can detect, classify, label, and protect content in third-party apps and services, such as SalesForce, Box, or DropBox, even if the third-party app or service does not read or support sensitivity labels.

- **Protégez les conteneurs** qui incluent Teams, les groupes Microsoft 365 et les sites SharePoint. Par exemple, définissez les paramètres de confidentialité, l’accès des utilisateurs externes et le partage externe, ainsi que l’accès à partir d’appareils non gérés.

- **Étendre les étiquettes de confidentialité à Power BI** : lorsque vous activez cette fonctionnalité, vous pouvez appliquer et afficher les étiquettes dans Power BI et protéger les données lorsqu’elles sont enregistrées en dehors du service.

- **Étendre les étiquettes de confidentialité aux ressources dans Mappage de données Microsoft Purview** : lorsque vous activez cette fonctionnalité, actuellement en préversion vous pouvez appliquer vos étiquettes de confidentialité aux fichiers et ressources de données schématisées dans Mappage de données Microsoft Purview. Les ressources de données schématisées incluent SQL, Azure SQL, Azure Synapse, Azure Cosmos et AWS RDS.

- **Extend sensitivity labels to third-party apps and services.** Using the Microsoft Information Protection SDK, third-party apps can read sensitivity labels and apply protection settings.

- **Classifier du contenu sans utiliser les paramètres de protection.** Vous pouvez également simplement affecter une étiquette en tant que résultat d’une classification de contenu. Cette action fournit aux utilisateurs un mappage visuel de classification des noms d’étiquettes de votre organisation et ils peuvent utiliser les étiquettes pour générer des rapports d’usage et afficher les données d’activité pour votre contenu sensible. En se basant sur ces informations, vous pouvez toujours choisir d’appliquer les paramètres de protection plus tard.

Dans tous ces cas, les étiquettes de confidentialité de Microsoft Purview peuvent vous aider à prendre les bonnes mesures sur le contenu approprié. Ces dernières vous permettent de classifier des données dans toute votre organisation et d’appliquer des paramètres de protection basés sur cette classification. Cette protection reste ensuite avec le contenu.

Pour plus d’informations sur ces actions et d’autres scénarios pris en charge par les étiquettes de confidentialité, consultez [Scénarios courants pour les étiquettes de confidentialité](get-started-with-sensitivity-labels.md#common-scenarios-for-sensitivity-labels). De nouvelles fonctionnalités sont constamment développées qui prennent en charge les étiquettes de confidentialité. Vous trouverez donc peut-être utile de consulter la [Feuille de route Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap?filters=Microsoft%20Information%20Protection&searchterms=label).

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="what-a-sensitivity-label-is"></a>Qu’est-ce qu’une étiquette de confidentialité ?

Lorsque vous attribuez une étiquette de confidentialité à du contenu, elle ressemble à un cachet appliqué et est :

- **Personnalisables.** Propres aux besoins de votre organisation et de votre activité, vous pouvez créer des catégories pour différents niveaux de contenu sensible dans votre organisation. Par exemple, vous pouvez commencer par utiliser des étiquettes telles que Personnel, Public, Général, Confidentiel et Hautement confidentiel.

- **Clear text.** Because a label is stored in clear text in the metadata for files and emails, third-party apps and services can read it and then apply their own protective actions, if required.

- **Permanentes.** Étant donné que l’étiquette est stockée dans les métadonnées des fichiers et des e-mails, l’étiquette reste avec le contenu, quel que soit l’emplacement où elle est enregistrée ou stockée. L'identification unique d’étiquette devient la base pour appliquer et faire respecter les stratégies que vous configurez.

Lorsqu'elle est visualisée par les utilisateurs de votre organisation, une étiquette de confidentialité s’affiche comme une balise sur les applications qu’ils utilisent et peut être facilement intégrée à leur flux de travail existant.

Chaque élément qui prend en charge les étiquettes de confidentialité peut se voir appliquer une étiquette de confidentialité unique. Les documents et les e-mails peuvent se voir appliquer à la fois une étiquette de confidentialité et une [étiquette de rétention](retention.md#retention-labels).

> [!div class="mx-imgBorder"]
> ![Étiquette de confidentialité appliquée à un e-mail.](../media/Sensitivity-label-on-email.png)

## <a name="what-sensitivity-labels-can-do"></a>Fonction des étiquettes de niveau de confidentialité

After a sensitivity label is applied to an email or document, any configured protection settings for that label are enforced on the content. You can configure a sensitivity label to:

- **Chiffrer** des courriers électroniques et des documents pour empêcher l’accès à ces données par des personnes non autorisées. Vous pouvez en outre choisir les utilisateurs ou le groupe autorisés à effectuer telle ou telle action et la durée de l’autorisation. Par exemple, vous pouvez décider d’autoriser tous les utilisateurs de votre organisation à modifier un document tandis qu’un groupe spécifique d’une autre organisation peut uniquement l’afficher. Par ailleurs, au lieu d’autorisations définies par l'administrateur, vous pouvez autoriser vos utilisateurs à attribuer des autorisations au contenu lorsqu’ils appliquent l’étiquette. 
    
    Pour plus d’informations sur les paramètres de **Chiffrement** lorsque vous créez ou modifiez une étiquette de confidentialité, voir [Restreindre l’accès au contenu en utilisant le chiffrement dans les étiquettes de confidentialité](encryption-sensitivity-labels.md).

- **Marquer le contenu** lorsque vous utilisez des applications Office, en ajoutant filigranes, pieds de page ou en-têtes à des e-mails ou des documents comportant l’étiquette. Vous pouvez appliquer des filigranes aux documents, mais pas aux e-mails. Exemple d’en-tête et de filigrane :
    
    ![Filigrane et en-tête appliqués au document.](../media/Sensitivity-label-watermark-header.png)
    
    Les marquages dynamiques sont également pris en charge à l’aide de variables. Par exemple, vous pouvez insérer le nom d’étiquette ou le nom du document dans l’en-tête, le pied de page ou le filigrane. Pour plus d’informations, consultez[Marquages dynamiques avec des variables](sensitivity-labels-office-apps.md#dynamic-markings-with-variables).
    
    Avez-vous besoin de vérifier la date de l’application des marques de contenu ? Veuillez consulter la section [Délai de marquage et de chiffrage de contenus par les applications Office](sensitivity-labels-office-apps.md#when-office-apps-apply-content-marking-and-encryption).
    
    If you have templates or workflows that are based on specific documents, test those documents with your chosen content markings before you make the label available for users. Some string length restrictions to be aware of:
    
    Les filigranes sont limités à 255 caractères. Les en-têtes et les pieds de page sont limités à 1 024 caractères, sauf dans Excel. Excel présente une limite totale de 255 caractères pour les en-têtes et les pieds de page, mais cette limite inclut des caractères qui ne sont pas visibles, tels que des codes de mise en forme. Si cette limite est atteinte, la chaîne entrée n’apparaît pas dans Excel.

- **Protégez du contenu dans des conteneurs tels que des sites et des groupes** lorsque vous activez la fonctionnalité à [utiliser des étiquettes de confidentialité avec Microsoft Teams, les Groupes Microsoft 365 et les sites SharePoint](sensitivity-labels-teams-groups-sites.md).
    
    Vous ne pouvez pas configurer les paramètres de protection pour les groupes et les sites tant que vous n’activez pas cette fonctionnalité. Cette configuration d’étiquettes ne permet pas aux documents ni aux e-mails d’être automatiquement étiquetés. En lieu et place, les paramètres d’étiquette protègent le contenu en contrôlant l’accès au conteneur dans lequel le contenu est stocké. Ces paramètres incluent les paramètres de confidentialité, l’accès des utilisateurs externes et le partage externe, ainsi que l’accès à partir d’appareils non gérés.

- **Apply the label automatically to files and emails, or recommend a label.** Choose how to identify sensitive information that you want labeled, and the label can be applied automatically, or you can prompt users to apply the label that you recommend. If you recommend a label, the prompt displays whatever text you choose. For example:
    
    ![Invitation de mise à attribuer une étiquette requise.](../media/Sensitivity-label-Prompt-for-required-label.png)
    
    Pour plus d’informations sur les paramètres d’**Étiquetage automatique des fichiers et des courriers** lorsque vous créez ou modifiez une étiquette de confidentialité, consultez [Appliquer automatiquement une étiquette de confidentialité à du contenu](apply-sensitivity-label-automatically.md) pour les applications Office et [Étiquetage dans Mappage de données Microsoft Purview](/azure/purview/create-sensitivity-label).

- **Définir le type de lien de partage par défaut** pour les sites SharePoint et les documents individuels. Pour éviter que les utilisateurs ne partagent trop de documents, définissez [l'étendue et les autorisations par défaut](sensitivity-labels-default-sharing-link.md) pour le partage de documents à partir de SharePoint et OneDrive.

### <a name="label-scopes"></a>Étendues des étiquettes

Lorsque vous créez une étiquette de confidentialité, vous êtes invité à configurer son étendue qui détermine deux aspects :
- Les paramètres d’étiquette que vous pouvez configurer pour cette étiquette
- L’emplacement où l’étiquette sera visible par les utilisateurs

Cette configuration d’étendue vous permet d’utiliser des étiquettes de confidentialité qui s’appliquent uniquement aux éléments tels que les documents et e-mails et qui ne peuvent pas être sélectionnées pour les conteneurs. Il en va de même pour les étiquettes de confidentialité qui sont uniquement destinées aux conteneurs et qui ne peuvent pas être sélectionnées pour les documents et les courriers électroniques. Vous pouvez également sélectionner l’étendue des ressources de données schématisées pour Microsoft Purview Data Map :

![Options d’étendue des étiquettes de confidentialité.](../media/sensitivity-labels-scopes.png)

L’étendue **Éléments** (précédemment nommée **Fichiers et courriers**) est, par défaut, toujours sélectionnée. Les autres étendues sont sélectionnées par défaut lorsque les fonctionnalités sont activées pour votre client :

- **Groupes et sites** : voir [Activer les étiquettes de confidentialité pour les conteneurs et synchroniser les étiquettes](sensitivity-labels-teams-groups-sites.md#how-to-enable-sensitivity-labels-for-containers-and-synchronize-labels)

- **Ressources de données schématisées** : voir [Étiqueter automatiquement votre contenu dans Mappage de données Microsoft Purview](/azure/purview/create-sensitivity-label)

Si vous modifiez les valeurs par défaut pour que toutes les étendues ne soient pas sélectionnées, vous verrez la première page des paramètres de configuration des étendues que vous n’avez pas sélectionnées, mais vous ne pourrez pas configurer les paramètres. Par exemple, si l’étendue des éléments n’est pas sélectionnée, vous ne pouvez pas sélectionner les options de la page suivante :

![Options non disponibles pour les étiquettes de confidentialité.](../media/sensitivity-labels-unavailable-settings.png)

Pour ces pages dont les options ne sont pas disponibles, sélectionnez **Suivant** pour continuer. Vous pouvez également sélectionner **Retour** pour modifier l’étendue de l’étiquette.

### <a name="label-priority-order-matters"></a>Priorité des étiquettes (l’ordre est important)

Lorsque vous créez vos étiquettes de sensibilité dans le portail de conformité Microsoft Purview, elles apparaissent dans une liste sur l'onglet **Sensibilité** de la page **Étiquettes**. Dans cette liste, l’ordre des étiquettes est important car il reflète leur priorité. Vous souhaitez que votre étiquette de sensibilité la plus restrictive, comme l’étiquette Hautement confidentiel, apparaisse en **bas** de la liste, et que la moins restrictive, telle que l’étiquette Public, apparaisse en **haut**.

Vous pouvez appliquer une seule étiquette de confidentialité à un élément tel qu’un document, un e-mail ou un conteneur. Si vous définissez une option obligeant vos utilisateurs à fournir une justification pour la modification d'une étiquette vers une classification plus faible, l’ordre de cette liste identifie les classifications les moins élevées. Toutefois, cette option ne s’applique pas aux sous-étiquettes qui partagent la priorité de leur étiquette parente.

Toutefois, l’ordre des [sous-étiquettes est utilisé avec les stratégies d’étiquetage automatique](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange). Lorsque vous configurez plusieurs stratégies d’étiquetage automatique pour le même emplacement, plusieurs correspondances peuvent se produire pour plusieurs étiquettes. Pour déterminer l’étiquette à appliquer, le classement des étiquettes est utilisé même avec les sous-étiquettes : la dernière étiquette sensible est sélectionnée, puis, le cas échéant, la dernière sous-étiquette.

![Option de création d’une sous-étiquette.](../media/Sensitivity-label-sublabel-options.png)

### <a name="sublabels-grouping-labels"></a>Sous-étiquettes (regroupement d’étiquettes)

With sublabels, you can group one or more labels below a parent label that a user sees in an Office app. For example, under Confidential, your organization might use several different labels for specific types of that classification. In this example, the parent label Confidential is simply a text label with no protection settings, and because it has sublabels, it can't be applied to content. Instead, users must choose Confidential to view the sublabels, and then they can choose a sublabel to apply to content.

Les sous-étiquettes sont simplement un moyen de présenter des étiquettes à des utilisateurs dans des groupes logiques. Les sous-étiquettes n’héritent d’aucun paramètre de leur étiquette parente, à l’exception de leur couleur d’étiquette. Lorsque vous publiez une sous-étiquette pour un utilisateur, cet utilisateur peut ensuite appliquer cette sous-étiquette au contenu et aux conteneurs, mais ne peut pas appliquer uniquement l’étiquette parente.

Ne choisissez pas une étiquette parent en tant qu’étiquette par défaut ou configurez une étiquette parent pour qu’elle soit automatiquement appliquée (ou recommandée). Si c’est le cas, l’étiquette parente ne peut pas être appliquée.

Exemple d’affichage de sous-étiquettes pour les utilisateurs :

![Sous-étiquettes regroupées dans le ruban.](../media/Sensitivity-label-grouped-labels2.png)

### <a name="editing-or-deleting-a-sensitivity-label"></a>Modification ou suppression d’une étiquette de niveau de confidentialité

Si vous supprimez une étiquette de confidentialité à partir de votre Centre d'administration, celle-ci n’est pas automatiquement supprimée du contenu et les paramètres de protection restent appliqués au contenu sur lequel l'étiquette a été appliquée.

Si vous modifiez une étiquette de sensibilité, la version de celle-ci qui était appliquée au contenu reste appliquée.

## <a name="what-label-policies-can-do"></a>Fonction des stratégies d’étiquette

Après avoir créé vos étiquettes de confidentialité, vous devez les publier pour les mettre à disposition des personnes et des services de votre organisation. Les étiquettes de confidentialité peuvent ensuite être appliquées aux documents et aux e-mails Office, ainsi qu’à d’autres éléments qui prennent en charge les étiquettes de confidentialité. 

Contrairement aux étiquettes de rétention qui sont publiées dans des emplacements comme les boîtes aux lettres Exchange, les étiquettes de confidentialité sont publiées pour les utilisateurs ou les groupes. Les applications qui prennent en charge les étiquettes de confidentialité peuvent ensuite les afficher à ces utilisateurs et groupes sous forme d’étiquettes appliquées ou d’étiquettes qu’ils peuvent appliquer.

Lorsque vous configurez une stratégie d’étiquette, vous pouvez :

- **Choose which users and groups see the labels.** Labels can be published to any specific user or email-enabled security group, distribution group, or Microsoft 365 group (which can have [dynamic membership](/azure/active-directory/users-groups-roles/groups-create-rule)) in Azure AD.

- **Spécifiez une étiquette** par défaut pour les documents et les e-mails non étiquetés, les nouveaux conteneurs (lorsque vous avez [activé les étiquettes de sensibilité pour Microsoft Teams, les groupes Microsoft 365 et les sites SharePoint](sensitivity-labels-teams-groups-sites.md)), ainsi qu'une étiquette par défaut pour le [contenu Power BI](/power-bi/admin/service-security-sensitivity-label-default-label-policy). Vous pouvez spécifier la même étiquette pour les quatre types d’éléments ou des étiquettes différentes. Les utilisateurs peuvent modifier l’étiquette de sensibilité par défaut appliquée pour mieux correspondre à la sensibilité de leur contenu ou conteneur.
    
    > [!NOTE]
    > L’étiquetage par défaut des documents existants est récemment pris en charge pour l’étiquetage intégré pour les applications Office. Pour plus d’informations sur le déploiement par application et les versions minimales, consultez le [tableau des fonctionnalités](sensitivity-labels-office-apps.md#sensitivity-label-capabilities-in-word-excel-and-powerpoint) pour Word, Excel et PowerPoint.
    
    Utilisez une étiquette par défaut pour définir des paramètres de protection de base à appliquer à votre contenu. Il faut noter que, sans formation des utilisateurs ou autres contrôles, ce paramètre peut également entraîner un étiquetage incorrect. Il est déconseillé de sélectionner une étiquette qui applique un chiffrement comme étiquette par défaut pour les documents. Par exemple, de nombreuses organisations doivent envoyer et partager des documents avec des utilisateurs externes qui ne possèdent peut-être pas des applications qui prennent en charge le chiffrement ou qui n’utilisent pas un compte pouvant être autorisé. Pour plus d’informations sur ce scénario, consultez [Partage de documents chiffrés avec des utilisateurs externes](sensitivity-labels-office-apps.md#sharing-encrypted-documents-with-external-users).
    
    > [!IMPORTANT]
    > Lorsque vous avez des [sous-étiquettes](#sublabels-grouping-labels), veillez à ne pas configurer l’étiquette parente comme étiquette par défaut.

- **Demander une justification pour une modification d'étiquette.** Si un utilisateur tente de supprimer une étiquette ou de la remplacer par une étiquette ayant un rang inférieur, vous pouvez exiger que l'utilisateur justifie cette action. Par exemple, un utilisateur ouvre un document étiqueté Confidentiel (rang 3) et remplace cette étiquette par avec une autre nommée Public (rang 1). Pour les applications Office, cette invite de justification est déclenchée une fois par session d’application lorsque vous utilisez l’étiquetage intégré et par fichier lorsque vous utilisez le client d’étiquetage unifié Azure Information Protection. Les administrateurs peuvent lire le motif de justification ainsi que le changement d’étiquette dans [explorateur des activités](data-classification-activity-explorer.md).

    ![Invite de saisie d’une justification par les utilisateurs.](../media/Sensitivity-label-justification-required.png)

- **Demandez aux utilisateurs d’appliquer une étiquette** aux documents et aux e-mails, uniquement aux documents, pour les conteneurs et le contenu Power BI. Également connues sous le nom d'étiquetage obligatoire, ces options permettent d’assurer qu’une étiquette soit appliquée avant que les utilisateurs puissent enregistrer des documents, envoyer des e-mails, créer des groupes ou des sites et lorsqu’ils utilisent du contenu non étiqueté pour Power BI.
    
    For documents and emails, a label can be assigned manually by the user, automatically as a result of a condition that you configure, or be assigned by default (the default label option previously described). An example prompt when a user is required to assign a label:

    ![Invite demandant à l’utilisateur Outlook d’appliquer l’étiquette requise.](../media/sensitivity-labels-mandatory-prompt-outlook.png)
    
    Pour plus d’informations sur l’étiquetage obligatoire des documents et des e-mails, consultez [Demander aux utilisateurs d’appliquer une étiquette à leurs e-mails et documents](sensitivity-labels-office-apps.md#require-users-to-apply-a-label-to-their-email-and-documents).
    
    Pour les conteneurs, une étiquette doit être attribuée au moment de la création du groupe ou du site.
    
    Pour plus d’informations sur l’étiquetage obligatoire pour Power BI, consultez [Stratégie d’étiquette obligatoire pour Power BI](/power-bi/admin/service-security-sensitivity-label-mandatory-label-policy).
    
    Envisagez d’utiliser cette option pour vous permettre d'augmenter la couverture d’étiquetage. Il faut noter que, sans formation des utilisateurs, ces paramètres peuvent entraîner un étiquetage incorrect. De plus, sauf si vous avez également défini une étiquette correspondante par défaut, l’étiquetage obligatoire risque de contrarier vos utilisateurs qui reçoivent de fréquentes invites.

- **Provide help link to a custom help page.** If your users aren't sure what your sensitivity labels mean or how they should be used, you can provide a Learn More URL that appears at the bottom of the **Sensitivity label** menu in the Office apps:

    ![Lien En savoir plus sur le bouton Niveau de confidentialité dans le ruban.](../media/Sensitivity-label-learn-more.png)

Les nouvelles étiquettes de confidentialité s’affichent dans les applications Office des utilisateurs, après la création d’une stratégie d’étiquettes les attribuant aux utilisateurs et aux groupes. Veuillez patienter jusqu’à 24 heures pour que les modifications s’appliquent dans votre organisation.

Vous pouvez créer et publier autant d’étiquettes de confidentialité que vous le souhaitez, à une exception près : si l’étiquette applique le chiffrement qui spécifie les utilisateurs et les autorisations, un maximum de 500 étiquettes est pris en charge avec cette configuration. Toutefois, dans le but de diminuer les frais généraux de l’administration et de réduire la complexité pour vos utilisateurs, tentez d’utiliser un nombre minimal d’étiquettes. Les déploiements en temps réel ont démontré l’efficacité notable d’une réduction lorsque les utilisateurs ont plus de cinq étiquettes principales ou plus de cinq sous-étiquettes par étiquette principale.

### <a name="label-policy-priority-order-matters"></a>Stratégie de priorité des étiquettes (l’ordre est important)

Vous mettez vos étiquettes de sensibilité à la disposition des utilisateurs en les publiant dans une stratégie d'étiquettes de sensibilité qui apparaît dans une liste sur la page **Stratégies d'étiquettes**. Tout comme les étiquettes de sensibilité (voir [Priorité des étiquettes (l'ordre est important](#label-priority-order-matters)) ), l'ordre des stratégies d'étiquettes de sensibilité est important car il reflète leur priorité : La stratégie d'étiquetage ayant la priorité la plus faible est affichée en haut de la liste avec le **numéro d'ordre** le plus bas, et la stratégie d'étiquetage ayant la priorité la plus élevée est affichée en bas de la liste avec le **numéro d'ordre le plus** élevé.

Une stratégie d’étiquette comprend les éléments suivants :

- un groupe d’étiquettes.
- les utilisateurs et les groupes auxquels la stratégie sera attribuée avec des étiquettes.
- l’étendue de la stratégie et des paramètres de stratégie pour cette étendue (comme l’étiquette par défaut pour les fichiers et les e-mails).

Vous pouvez inclure un utilisateur dans plusieurs stratégies d’étiquette, et celui-ci pourra voir toutes les étiquettes de confidentialité et paramètres de ces stratégies. En cas de conflit entre les paramètres de plusieurs politiques, les paramètres de la stratégie ayant la priorité la plus élevée (numéro d'ordre le plus élevé) sont appliqués. En d’autres termes, la priorité la plus élevée l’emporte pour chaque paramètre.

Si vous ne voyez pas le comportement du paramètre de stratégie d'étiquette que vous attendez pour un utilisateur ou un groupe, vérifiez l'ordre des stratégies d'étiquette de sensibilité. Vous devrez peut-être déplacer la stratégie vers le bas. Pour réorganiser les stratégies d'étiquetage, sélectionnez une stratégie d'étiquetage de sensibilité > choisissez l'ellipse Actions pour cette entrée > **Déplacer vers le bas** ou **Déplacer vers le haut**. Par exemple :

![Option déplacer dans la page pour les stratégies d’étiquette de confidentialité.](../media/sensitivity-label-policy-priority.png)

Dans notre exemple de capture d'écran qui montre trois stratégies d'étiquetage, tous les utilisateurs se voient attribuer la stratégie d'étiquetage standard, il est donc approprié qu'elle ait la priorité la plus basse (numéro d'ordre le plus bas de 0). Seuls les utilisateurs du département informatique se voient attribuer la deuxième stratégie qui porte le numéro d'ordre 1. Pour ces utilisateurs, s'il y a des conflits de paramètres entre leur stratégie et la stratégie standard, les paramètres de leur stratégie l'emportent car ils ont un numéro d'ordre plus élevé. 

De même pour les utilisateurs du service juridique, qui se voient attribuer la troisième stratégie avec des paramètres distincts. Il est probable que ces utilisateurs aient des paramètres plus stricts, il est donc approprié que leur stratégie ait le numéro d'ordre le plus élevé. Il est peu probable qu'un utilisateur du service juridique fasse partie d'un groupe qui est également affecté à la stratégie du service informatique. Mais si c'est le cas, l'ordre numéro 2 (numéro d'ordre le plus élevé) garantit que les paramètres du département juridique sont toujours prioritaires en cas de conflit.

> [!NOTE]
> N'oubliez pas : en cas de conflit de paramètres pour un utilisateur auquel plusieurs stratégies ont été attribuées, le paramètre de la stratégie attribuée ayant le numéro d'ordre le plus élevé est appliqué.

## <a name="sensitivity-labels-and-azure-information-protection"></a>Étiquettes de niveau de confidentialité et étiquettes Azure Information Protection

Les étiquettes de confidentialité intégrées à Microsoft 365 Apps sur Windows, macOS, iOS et Android s’affichent et se comportent très de la même façon sur ces appareils pour offrir aux utilisateurs une expérience d’étiquetage cohérente. Toutefois, sur les ordinateurs Windows, vous pouvez également utiliser le client [Azure Information Protection (AIP)](/azure/information-protection/rms-client/aip-clientv2). Ce client est maintenant en [mode maintenance](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/announcing-aip-unified-labeling-client-maintenance-mode-and/ba-p/3043613) et, lorsqu’il est installé, il n’est plus le client d’étiquetage par défaut pour les dernières applications Office.

Si vous utilisez le client AIP pour l’étiquetage dans les applications Office, nous vous recommandons de passer à l’étiquetage intégré. Pour plus d’informations, consultez [Migrer le complément Azure Information Protection (AIP) vers l’étiquetage intégré pour les applications Office](sensitivity-labels-aip.md).

### <a name="azure-information-protection-labels"></a>Étiquettes Azure Information Protection

La gestion d’étiquetage pour les étiquettes Azure Information Protection dans le portail Azure a été retiré le **31 mars 2021**. Pour plus d’informations, consultez l’[avis de retrait](https://techcommunity.microsoft.com/t5/azure-information-protection/announcing-timelines-for-sunsetting-label-management-in-the/ba-p/1226179) officiel.

Si votre client n’est pas encore sur la [plateforme d’étiquetage unifié](/azure/information-protection/faqs#how-can-i-determine-if-my-tenant-is-on-the-unified-labeling-platform), vous devez d’abord activer l’étiquette unifiée avant d’utiliser des étiquettes de confidentialité. Pour voir les instructions, consultez [Migration des étiquettes Azure Information Protection vers des étiquettes de confidentialité unifiées](/azure/information-protection/configure-policy-migrate-labels).

## <a name="sensitivity-labels-and-the-microsoft-information-protection-sdk"></a>Les étiquettes de confidentialité et SDK Microsoft Information Protection

Une étiquette de confidentialité étant stockée dans les métadonnées d’un document, les applications et services tiers peuvent lire et écrire dans ces métadonnées d'étiquetage pour compléter votre déploiement d’étiquetage. Par ailleurs, les développeurs de logiciels peuvent utiliser le kit de développement logiciel (SDK) [Microsoft Information Protection](/information-protection/develop/overview#microsoft-information-protection-sdk) pour prendre en charge les fonctionnalités d’étiquetage et de chiffrement sur plusieurs plateformes. Pour en savoir plus, voir [l'annonce de la disponibilité générale sur le blog de la Communauté technique](https://techcommunity.microsoft.com/t5/Microsoft-Information-Protection/Microsoft-Information-Protection-SDK-Now-Generally-Available/ba-p/263144). 

Vous pouvez également en savoir plus sur les [solutions de partenaires intégrées à Protection des données Microsoft Purview](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Microsoft-Information-Protection-showcases-integrated-partner/ba-p/262657).

## <a name="deployment-guidance"></a>Instructions de déploiement

Pour la planification et les instructions relatives au déploiement, notamment les informations relatives aux licences, les autorisations, la stratégie de déploiement, une liste de scénarios pris en charge et la documentation de l’utilisateur final, consultez [Prise en main des étiquettes de confidentialité](get-started-with-sensitivity-labels.md).

Pour découvrir comment utiliser des étiquettes de confidentialité pour se conformer aux réglementations sur la confidentialité des données, consultez [Déployer la protection des informations pour les réglementations de confidentialité des données avec Microsoft 365](../solutions/information-protection-deploy.md).
