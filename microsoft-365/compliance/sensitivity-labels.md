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
localization_priority: Priority
ms.collection:
- M365-security-compliance
- SPO_Content
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Utilisez les étiquettes de confidentialité de Microsoft Information Protection (MIP) pour classifier et protéger le contenu sensible.
ms.custom:
- seo-marvel-apr2020
- seo-marvel-jun2020
ms.openlocfilehash: 2121c58b0105519d5dacda0c0bb39a102cf8d299
ms.sourcegitcommit: 070724118be25cd83418d2a56863da95582dae65
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2021
ms.locfileid: "50407260"
---
# <a name="learn-about-sensitivity-labels"></a>En savoir plus sur les étiquettes de niveau de confidentialité

>*[Guide de sécurité et conformité pour les licences Microsoft 365](https://aka.ms/ComplianceSD).*

Pour mener à bien leur travail, les membres de votre organisation collaborent avec d’autres personnes internes ou externes à votre organisation. Cela signifie que le contenu n’est plus protégé par un pare-feu : il peut se déplacer partout, sur les appareils, applications et services. Dans ce cas, vous devez sécuriser et protéger l’itinérance, tout en respectant les stratégies métier et de conformité de votre organisation.

Les étiquettes de confidentialité de la solution Microsoft Information Protection vous permettent de classifier et protéger les données de votre organisation, tout en veillant à ce que la productivité des utilisateurs et leur aptitude à collaborer ne soient pas compromises.

Exemple illustrant les étiquettes de confidentialité disponibles dans Excel à partir de l’onglet **Accueil** du ruban. Dans cet exemple, l’étiquette appliquée affiche dans la barre d’état :

![Étiquette de confidentialité dans le ruban Excel et sur la barre d’état](../media/Sensitivity-label-in-Excel.png)

Pour appliquer des étiquettes de confidentialité, les utilisateurs doivent être connectés avec leur compte Microsoft 365 professionnel ou scolaire.

> [!NOTE]
> Les étiquettes de confidentialité sont nouvellement pris en charge pour les clients du gouvernement américain (GCC et GCC-H). Pour plus d’informations, consultez les notes de publication pour Microsoft 365 Apps for enterprise, [Version 2101 : 26 janvier](https://docs.microsoft.com/officeupdates/current-channel#version-2101-january-26).
>
> Pour le client d’étiquettes et le scanneur Azure Information Protection unifiés, consultez la [Description du service public premium Azure Information Protection](https://docs.microsoft.com/enterprise-mobility-security/solutions/ems-aip-premium-govt-service-description).

Vous pouvez utiliser les étiquettes de niveau de confidentialité aux fins suivantes :
  
- **Fournir des paramètres de protection qui incluent le chiffrement et les marquages de contenu.** Par exemple, appliquez une étiquette « Confidentiel » à un document ou un message électronique, et cette étiquette chiffre le contenu et applique un filigrane « Confidentiel ». Les marquages de contenu comprennent les en-têtes et les pieds de page, ainsi que les filigranes, et le chiffrement peut également limiter les mesures autorisées que les utilisateurs peuvent prendre sur le contenu.

- **Protéger le contenu dans les applications Office sur différents appareils et plateformes.** Pris en charge par Word, Excel, PowerPoint et Outlook sur les applications Office pour ordinateur de bureau et Office sur le web. Pris en charge sur Windows, macOS, iOS et Android.

- **Protéger le contenu dans les services et les applications tiers** à l’aide de Microsoft Cloud App Security. Avec Cloud App Security (CAS), vous pouvez détecter, classer, étiqueter et protéger le contenu dans les services tiers et applications tierces, comme SalesForce, Box ou Dropbox, même si l’application tierce ou le service tiers ne lit pas ou ne prend pas en charge les étiquettes de niveau de confidentialité.

- **Protégez les conteneurs** qui incluent Teams, les groupes Microsoft 365 et les sites SharePoint. Par exemple, définissez les paramètres de confidentialité, l’accès des utilisateurs externes et le partage externe, ainsi que l’accès à partir d’appareils non gérés.

- **Étendre les étiquettes de confidentialité à Power BI** : lorsque vous activez cette fonctionnalité, vous pouvez appliquer et afficher les étiquettes dans Power BI et protéger les données lorsqu’elles sont enregistrées en dehors du service.

- **Étendre les étiquettes de confidentialité aux ressources dans Azure Purview** : lorsque vous activez cette fonctionnalité, actuellement en préversion, vous pouvez appliquer des étiquettes de confidentialité à des ressources tels que des colonnes SQL, des fichiers dans le Stockage Blob Azure, etc. 

- **Étendre les étiquettes de confidentialité à des applications et services tiers.** Grâce à l'utilisation du SDK Microsoft informations Protection, des applications tierces peuvent lire des étiquettes de confidentialité et appliquer des paramètres de protection.

- **Classifier du contenu sans utiliser les paramètres de protection.** Vous pouvez également simplement affecter une étiquette en tant que résultat d’une classification de contenu. Cette action fournit aux utilisateurs un mappage visuel de classification des noms d’étiquettes de votre organisation et ils peuvent utiliser les étiquettes pour générer des rapports d’usage et afficher les données d’activité pour votre contenu sensible. En se basant sur ces informations, vous pouvez toujours choisir d’appliquer les paramètres de protection plus tard.

Dans tous ces cas, les étiquettes de confidentialité dans Microsoft 365 peuvent vous aider à effectuer les actions adéquates sur le contenu approprié. Ces dernières vous permettent de classifier des données dans toute votre organisation et d’appliquer des paramètres de protection basés sur cette classification.

Pour plus d’informations sur ces actions et d’autres scénarios pris en charge par les étiquettes de confidentialité, consultez [Scénarios courants pour les étiquettes de confidentialité](get-started-with-sensitivity-labels.md#common-scenarios-for-sensitivity-labels). De nouvelles fonctionnalités sont constamment développées qui prennent en charge les étiquettes de confidentialité. Vous trouverez donc peut-être utile de faire référence à la [Feuille de route Microsoft 365](https://aka.ms/MIPC/Roadmap).

## <a name="what-a-sensitivity-label-is"></a>Qu’est-ce qu’une étiquette de confidentialité ?

Lorsque vous attribuez une étiquette de confidentialité à du contenu, elle ressemble à un cachet appliqué et est :

- **Personnalisables.** Propres aux besoins de votre organisation et de votre activité, vous pouvez créer des catégories pour différents niveaux de contenu sensible dans votre organisation. Par exemple, vous pouvez commencer par utiliser des étiquettes telles que Personnel, Public, Général, Confidentiel et Hautement confidentiel.

- **Texte en clair.** Une étiquette étant stockée sous forme de texte clair dans les métadonnées pour les fichiers et les courriers, les applications et services tiers peuvent la lire, puis appliquer leurs propres actions de protection, le cas échéant.

- **Permanentes.** Une étiquette étant stockée dans des métadonnées pour des fichiers et des courriers, l’étiquette circule avec le contenu, peu importe l’emplacement d’enregistrement ou de stockage. L’identification d’étiquette unique devient la base pour l’application et le respect des stratégies que vous configurez.

Lorsqu’elle est affichée par les utilisateurs, l’étiquette de confidentialité ressemble à une balise sur les applications qu’ils utilisent et elle peut facilement être intégrée à son flux de travail existant.

Chaque élément qui prend en charge les étiquettes de confidentialité peut se voir appliquer une étiquette de confidentialité unique. Les documents et les e-mails peuvent se voir appliquer à la fois une étiquette de confidentialité et une [étiquette de rétention](retention.md#retention-labels).

> [!div class="mx-imgBorder"]
> ![Étiquette de confidentialité appliquée à un e-mail](../media/Sensitivity-label-on-email.png)

## <a name="what-sensitivity-labels-can-do"></a>Fonction des étiquettes de niveau de confidentialité

Une fois qu’une étiquette de confidentialité est appliquée à un e-mail ou un document, tout paramètre de protection relatif à cette étiquette sont appliqués au contenu. Vous pouvez configurer une étiquette de confidentialité pour :

- **Chiffrer** des courriers électroniques et des documents pour empêcher l’accès à ces données par des personnes non autorisées. Vous pouvez en outre choisir les utilisateurs ou le groupe autorisés à effectuer telle ou telle action et la durée de l’autorisation. Par exemple, vous pouvez décider d’autoriser tous les utilisateurs de votre organisation à modifier un document tandis qu’un groupe spécifique d’une autre organisation peut uniquement l’afficher. Par ailleurs, au lieu d’autorisations définies par l'administrateur, vous pouvez autoriser vos utilisateurs à attribuer des autorisations au contenu lorsqu’ils appliquent l’étiquette. 
    
    Pour plus d’informations sur les paramètres de **Chiffrement** lorsque vous créez ou modifiez une étiquette de confidentialité, voir [Restreindre l’accès au contenu en utilisant le chiffrement dans les étiquettes de confidentialité](encryption-sensitivity-labels.md).

- **Marquer le contenu** lorsque vous utilisez des applications Office, en ajoutant filigranes, pieds de page ou en-têtes à des e-mails ou des documents comportant l’étiquette. Vous pouvez appliquer des filigranes aux documents, mais pas aux e-mails. Exemple d’en-tête et de filigrane :
    
    ![Filigrane et en-tête appliqués au document](../media/Sensitivity-label-watermark-header.png)
    
    Avez-vous besoin de vérifier la date de l’application des marques de contenu ? Veuillez consulter la section [Délai de marquage et de chiffrage de contenus par les applications Office](sensitivity-labels-office-apps.md#when-office-apps-apply-content-marking-and-encryption).
    
    Certaines applications, mais pas toutes, prennent en charge les marquages dynamiques à l’aide de variables. Par exemple, vous pouvez insérer le nom d’étiquette ou le nom du document dans l’en-tête, le pied de page ou le filigrane. Pour plus d’informations, consultez[Marquages dynamiques avec des variables](sensitivity-labels-office-apps.md#dynamic-markings-with-variables).
    
    Longueurs de chaînes : les filigranes sont limités à 255 caractères. Les en-têtes et les pieds de page sont limités à 1 024 caractères, sauf dans Excel. Excel présente une limite totale de 255 caractères pour les en-têtes et les pieds de page, mais cette limite inclut des caractères qui ne sont pas visibles, tels que des codes de mise en forme. Si cette limite est atteinte, la chaîne entrée n’apparaît pas dans Excel.

- **Protégez du contenu dans des conteneurs tels que des sites et des groupes** lorsque vous activez la fonctionnalité à [utiliser des étiquettes de confidentialité avec Microsoft Teams, les Groupes Microsoft 365 et les sites SharePoint](sensitivity-labels-teams-groups-sites.md).
    
    Vous ne pouvez pas configurer les paramètres de protection pour les groupes et les sites tant que vous n’activez pas cette fonctionnalité. Cette configuration d’étiquettes ne permet pas aux documents ni aux e-mails d’être automatiquement étiquetés. En lieu et place, les paramètres d’étiquette protègent le contenu en contrôlant l’accès au conteneur dans lequel le contenu est stocké. Ces paramètres incluent les paramètres de confidentialité, l’accès des utilisateurs externes et le partage externe, ainsi que l’accès à partir d’appareils non gérés.

- **Appliquer automatiquement l’étiquette aux fichiers et e-mails ou recommandez une étiquette.** Choisissez comment identifier les informations sensibles que vous voulez étiqueter. L'étiquette peut être appliquée automatiquement, ou vous pouvez inviter les utilisateurs à appliquer l’étiquette que vous recommandez. Si vous recommandez une étiquette, l’invite affiche le texte de votre choix. Par exemple :
    
    ![Invitation de mise à attribuer une étiquette requise](../media/Sensitivity-label-Prompt-for-required-label.png)
    
    Pour plus d’informations sur les paramètres d' **Étiquetage automatique pour les fichiers et e-mails** lorsque vous créez ou modifiez une étiquette de confidentialité, consultez [Appliquer automatiquement une étiquette de confidentialité à du contenu](apply-sensitivity-label-automatically.md) pour les applications Office et [Étiqueter automatiquement vos données dans Azure Preview](https://docs.microsoft.com/azure/purview/create-sensitivity-label).

### <a name="label-scopes"></a>Étendues des étiquettes

Lorsque vous créez une étiquette de confidentialité, vous êtes invité à configurer son étendue qui détermine deux aspects :
- Les paramètres d’étiquette que vous pouvez configurer pour cette étiquette
- L’emplacement où l’étiquette sera visible par les utilisateurs

Cette configuration d’étendue vous permet d’utiliser des étiquettes de confidentialité qui s’appliquent uniquement aux documents et e-mails et qui ne peuvent pas être sélectionnées pour les conteneurs. Il en va de même pour les étiquettes de confidentialité qui sont uniquement destinées aux conteneurs et qui ne peuvent pas être sélectionnées pour les documents et les courriers électroniques. Nouveauté actuellement en préversion : vous pouvez également sélectionner l’étendue des ressources Azure Purview :

![Options d’étendue des étiquettes de confidentialité](../media/sensitivity-labels-scopes.png)

Par défaut, l’étendue **Fichiers et e-mails** est toujours sélectionnée. Les autres étendues sont sélectionnées par défaut lorsque les fonctionnalités sont activées pour votre client :

- **Groupes et sites** : [activer les étiquettes de confidentialité pour les conteneurs et synchroniser les étiquettes](sensitivity-labels-teams-groups-sites.md#how-to-enable-sensitivity-labels-for-containers-and-synchronize-labels)

- **Ressources Azure Purview (préversion)**  : [Étiqueter automatiquement le contenu dans Azure Purview](https://go.microsoft.com/fwlink/?linkid=2148989)

Si vous modifiez les valeurs par défaut pour que toutes les étendues ne soient pas sélectionnées, vous verrez la première page des paramètres de configuration des étendues que vous n’avez pas sélectionnées, mais vous ne pourrez pas configurer les paramètres. Par exemple, si l’étendue des fichiers et e-mails n’est pas sélectionnée, vous ne pouvez pas sélectionner les options de la page suivante :

![Options non disponibles pour les étiquettes de confidentialité](../media/sensitivity-labels-unavailable-settings.png)

Pour ces pages dont les options ne sont pas disponibles, sélectionnez **Suivant** pour continuer. Vous pouvez également sélectionner **Retour** pour modifier l’étendue de l’étiquette.

### <a name="label-priority-order-matters"></a>Priorité des étiquettes (l’ordre est important)

Lorsque vous créez vos étiquettes de confidentialité dans votre centre d’administration, elles apparaissent dans une liste située sous l’onglet **Sensibilité** de la page **Étiquettes**. Dans cette liste, l’ordre des étiquettes est important car il reflète leur priorité. Vous souhaitez que votre étiquette de sensibilité la plus restrictive, comme l’étiquette Hautement confidentiel, apparaisse en **bas** de la liste, et que la moins restrictive, telle que l’étiquette Public, apparaisse en **haut**.

Vous pouvez appliquer une seule étiquette de confidentialité à un élément tel qu’un document, un e-mail ou un conteneur. Si vous définissez une option obligeant vos utilisateurs à fournir une justification pour la modification d'une étiquette vers une classification plus faible, l’ordre de cette liste identifie les classifications les moins élevées. Cette option ne s’applique toutefois pas aux sous-étiquettes.

Cependant, l’ordre des sous-étiquettes est utilisé avec l'[étiquetage automatique](apply-sensitivity-label-automatically.md). Lorsque vous configurez les étiquettes pour les appliquer automatiquement ou en tant que recommandation, plusieurs correspondances peuvent se produire pour plus d'une étiquette. Pour déterminer l’étiquette à appliquer ou à recommander, l’ordre d’étiquettes est utilisé : la dernière étiquette de confidentialité est sélectionnée, puis, le cas échéant, la dernière sous-étiquette.

![Option de création d’une sous-étiquette](../media/Sensitivity-label-sublabel-options.png)

### <a name="sublabels-grouping-labels"></a>Sous-étiquettes (regroupement d’étiquettes)

Avec les sous-étiquettes, vous pouvez regrouper une ou plusieurs étiquettes sous une étiquette parent que les utilisateurs pourront voir dans une application Office. Par exemple, sous Confidentiel, votre organisation peut utiliser plusieurs étiquettes différentes pour certains types de cette classification. Dans cet exemple, l’étiquette parent Confidentiel est tout simplement une étiquette de texte sans aucun paramètre de protection. Comme elle comporte des sous-étiquettes, elle ne peut pas être appliquée au contenu. Les utilisateurs doivent d’abord choisir Confidentiel pour afficher les sous-étiquettes, puis choisir une sous-étiquette à appliquer au contenu.

Les sous-étiquettes sont simplement un moyen de présenter des étiquettes à des utilisateurs dans des groupes logiques. Les sous-étiquettes n’héritent pas des paramètres de leur étiquette parent. Lorsque vous publiez une sous-étiquette pour un utilisateur, celui-ci peut ensuite l’appliquer au contenu, mais il ne peut pas uniquement employer l’étiquette parente.

Ne choisissez pas une étiquette parent en tant qu’étiquette par défaut ou configurez une étiquette parent pour qu’elle soit automatiquement appliquée (ou recommandée). Dans le cas contraire, l’étiquette parent ne sera pas appliquée au contenu.

Exemple d’affichage de sous-étiquettes pour les utilisateurs :

![Sous-étiquettes regroupées dans le ruban](../media/Sensitivity-label-grouped-labels2.png)

### <a name="editing-or-deleting-a-sensitivity-label"></a>Modification ou suppression d’une étiquette de niveau de confidentialité

Si vous supprimez une étiquette de confidentialité à partir de votre Centre d'administration, celle-ci n’est pas automatiquement supprimée du contenu et les paramètres de protection restent appliqués au contenu sur lequel l'étiquette a été appliquée.

Si vous modifiez une étiquette de sensibilité, la version de celle-ci qui était appliquée au contenu reste appliquée.

## <a name="what-label-policies-can-do"></a>Fonction des stratégies d’étiquette

Après avoir créé vos étiquettes de confidentialité, vous devez les publier afin qu’elles soient disponibles pour les personnes et les services de votre organisation. Les étiquettes de confidentialité peuvent ensuite être appliquées aux documents et aux e-mails Office, ainsi qu’à d’autres éléments qui prennent en charge les étiquettes de confidentialité. 

Contrairement aux étiquettes de rétention qui sont publiées dans des emplacements comme les boîtes aux lettres Exchange, les étiquettes de confidentialité sont publiées pour les utilisateurs ou les groupes. Les applications qui prennent en charge les étiquettes de confidentialité peuvent ensuite les afficher à ces utilisateurs et groupes sous forme d’étiquettes appliquées ou d’étiquettes qu’ils peuvent appliquer.

Lorsque vous configurez une stratégie d’étiquette, vous pouvez :

- **Sélectionnez les utilisateurs et les groupes pouvant voir les étiquettes.** Les étiquettes peuvent être publiées vers un utilisateur ou un groupe de sécurité à extension de courrier, à un groupe de distribution ou à un groupe Microsoft 365 (pouvant avoir [l’appartenance dynamique](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-create-rule)) dans Azure AD.

- **Appliquez une étiquette par défaut** à tous les nouveaux documents et e-mails créés par les utilisateurs et groupes inclus dans la stratégie d’étiquettes, ainsi que des étiquettes par défaut identiques ou différentes aux conteneurs (si vous avez [activé les étiquettes de confidentialité pour Microsoft Teams, les groupes Microsoft 365 et les sites SharePoint](sensitivity-labels-teams-groups-sites.md)). Les utilisateurs peuvent toujours modifier l’étiquette par défaut s’il ne s’agit pas de l’étiquette appropriée pour leur document ou leur courrier électronique. 
    
    Utilisez une étiquette par défaut pour définir des paramètres de protection de base à appliquer à votre contenu. Il faut noter que, sans formation des utilisateurs ou autres contrôles, ce paramètre peut également entraîner un étiquetage incorrect. Il est déconseillé de sélectionner une étiquette qui applique un chiffrement comme étiquette par défaut pour les documents. Par exemple, de nombreuses organisations doivent envoyer et partager des documents avec des utilisateurs externes qui ne possèdent peut-être pas des applications qui prennent en charge le chiffrement ou qui n’utilisent pas un compte pouvant être autorisé. Pour plus d’informations sur ce scénario, consultez [Partage de documents chiffrés avec des utilisateurs externes](sensitivity-labels-office-apps.md#sharing-encrypted-documents-with-external-users).

- **Demander une justification pour une modification d'étiquette.** Si un utilisateur tente de supprimer une étiquette ou de la remplacer par une étiquette ayant un rang inférieur, vous pouvez exiger que l'utilisateur justifie cette action. Par exemple, un utilisateur ouvre un document étiqueté Confidentiel (rang 3) et remplace cette étiquette par avec une autre nommée Public (rang 1). Les administrateurs peuvent lire le motif de justification ainsi que le changement d’étiquette dans [explorateur des activités](data-classification-activity-explorer.md).

    ![Invite de saisie d’une justification par les utilisateurs](../media/Sensitivity-label-justification-required.png)

- **Exigez que les utilisateurs appliquent une étiquette** avec une option pour les e-mails et les documents, et une autre pour les conteneurs. Également connues sous le nom d'étiquetage obligatoire, ces options permettent d’assurer qu’une étiquette soit appliquée avant que les utilisateurs puissent enregistrer des documents, envoyer des e-mails, ainsi que créer des groupes ou des sites.
    
    Pour les documents et les e-mails, une étiquette peut être attribuée manuellement par l’utilisateur, automatiquement suite à une condition que vous configurez, ou être attribuée par défaut (l'option d’étiquette par défaut précédemment décrite). Un exemple d’invite présenté dans Outlook lorsqu’un utilisateur doit attribuer une étiquette :

    ![Invite demandant à l’utilisateur Outlook d’appliquer l’étiquette requise](../media/sensitivity-labels-mandatory-prompt-aipv2-outlook.PNG)
    
    > [!NOTE]
    > L’étiquetage obligatoire des documents et e-mails n’est pas disponible dans toutes les applications ou sur toutes les plateformes. Pour plus d’informations, consultez [Demander aux utilisateurs d'appliquer une étiquette à leurs e-mails et documents](sensitivity-labels-office-apps.md#require-users-to-apply-a-label-to-their-email-and-documents).
    
    Pour les conteneurs, une étiquette doit être attribuée au moment de la création du groupe ou du site.
    
    Envisagez d’utiliser cette option pour vous permettre d'augmenter la couverture d’étiquetage. Il faut noter que, sans formation des utilisateurs, ces paramètres peuvent entraîner un étiquetage incorrect. De plus, sauf si vous avez également défini une étiquette correspondante par défaut, l’étiquetage obligatoire risque de contrarier vos utilisateurs qui reçoivent de fréquentes invites.

- **Fournir un lien d’aide vers une page d’aide personnalisée.** Si vos utilisateurs ne sont pas sûrs de comprendre la signification ou l'utilisation de vos étiquettes de confidentialité, vous pouvez fournir une URL de type En savoir plus, qui apparaît en bas du menu **Etiquettes de confidentialité** dans les applications Office :

    ![Lien En savoir plus sur le bouton Niveau de confidentialité dans le ruban](../media/Sensitivity-label-learn-more.png)

Les nouvelles étiquettes de confidentialité s’affichent dans les applications Office des utilisateurs, après la création d’une stratégie d’étiquettes les attribuant aux utilisateurs et aux groupes. Veuillez patienter jusqu’à 24 heures pour que les modifications s’appliquent dans votre organisation.

Vous pouvez créer et publier autant d’étiquettes de confidentialité que vous le souhaitez, à une exception près : si l’étiquette applique le chiffrement, vous pouvez créer jusqu’à 500 étiquettes. Toutefois, dans le but de diminuer les frais généraux de l’administration et de réduire la complexité pour vos utilisateurs, tentez d’utiliser un nombre minimal d’étiquettes. Les déploiements en temps réel ont démontré l’efficacité notable d’une réduction lorsque les utilisateurs ont plus de cinq étiquettes principales ou plus de cinq sous-étiquettes par étiquette principale.

### <a name="label-policy-priority-order-matters"></a>Stratégie de priorité des étiquettes (l’ordre est important)

Pour rendre vos étiquettes de confidentialité accessibles aux utilisateurs, vous devez les publier dans une stratégie de confidentialité d’étiquette qui apparaît dans une liste sous l’onglet **Stratégies de confidentialité** sur la page **Stratégies d’étiquettes**. À l’instar des étiquettes de confidentialité (voir la section [Priorité des étiquettes (l’ordre est important)](#label-priority-order-matters)), l’ordre des stratégies d’étiquette de confidentialité est important, car il reflète leur priorité. La stratégie d’étiquette dont la priorité est la plus faible est affichée **en haut**, et celle dont la priorité est la plus haute est affichée **en bas**.

Une stratégie d’étiquette comprend les éléments suivants :

- un groupe d’étiquettes.
- les utilisateurs et les groupes auxquels la stratégie sera attribuée avec des étiquettes.
- l’étendue de la stratégie et des paramètres de stratégie pour cette étendue (comme l’étiquette par défaut pour les fichiers et les e-mails).

Vous pouvez inclure un utilisateur dans différentes stratégies d’étiquette, et celui-ci pourra voir toutes les étiquettes de confidentialité de ces stratégies. Toutefois, un utilisateur n'obtient les paramètres de stratégie qu'à partir de la stratégie d’étiquette dont la priorité est la plus élevée.

Si vous ne voyez pas l'étiquette ou le paramètre de stratégie d’étiquette attendu pour un utilisateur ou un groupe, vérifiez l’ordre des stratégies d’étiquette de confidentialité. Pour réorganiser les stratégies d’étiquette, sélectionnez une stratégie d’étiquette de confidentialité > sélectionnez les points de suspension sur la droite > **Descendre** ou **Monter**.

![Option déplacer dans la page pour les stratégies d’étiquette de confidentialité](../media/sensitivity-label-policy-priority.png)

Si vous utilisez des étiquettes de rétention en plus des étiquettes de confidentialité, il est important de ne pas oublier l'aspect prioritaire des stratégies d’étiquette de confidentialité, mais pas pour les [étiquettes de rétention](retention.md#the-principles-of-retention-or-what-takes-precedence).

## <a name="sensitivity-labels-and-azure-information-protection"></a>Étiquettes de niveau de confidentialité et étiquettes Azure Information Protection

Si vous avez déployé des étiquettes à l’aide d’Azure Information Protection, consultez les sections suivantes pour obtenir de l'aide avant de commencer à utiliser les étiquettes de confidentialité.

### <a name="azure-information-protection-labels"></a>Étiquettes Azure Information Protection

> [!NOTE]
> La gestion d’étiquetage pour les étiquettes Azure Information Protection dans le Portail Microsoft Azure fera l’objet d’un retrait le **31 mars 2021**. Pour plus d’informations, consultez l’[avis de dépréciation](https://techcommunity.microsoft.com/t5/azure-information-protection/announcing-timelines-for-sunsetting-label-management-in-the/ba-p/1226179) officiel.

Si vous utilisez des étiquettes Azure Information Protection car votre client n’est pas encore sur la [plateforme d’étiquetage unifié](https://docs.microsoft.com/azure/information-protection/faqs#how-can-i-determine-if-my-tenant-is-on-the-unified-labeling-platform), nous vous recommandons d’éviter la création d'étiquettes de confidentialité tant que l’étiquetage unifié n’est pas activé. Dans ce scénario, les étiquettes que vous voyez dans le portail Microsoft Azure sont les étiquettes Azure Information Protection au lieu des étiquettes de confidentialité. Ces étiquettes peuvent être utilisées par le client Azure Information Protection (classique) sur des ordinateurs Windows, mais ne peuvent pas être utilisées par des appareils exécutant macOS, iOS ou Android. Pour résoudre ce problème, [migrez ces étiquettes](/azure/information-protection/configure-policy-migrate-labels) vers les étiquettes de confidentialité. 

Les métadonnées appliquées par ces jeux d’étiquettes sont compatibles. Vous ne devez donc pas attribuer de nouveau libellé aux documents et courriers électroniques lorsque la migration est terminée.

### <a name="azure-information-protection-clients"></a>Clients Azure Information Protection

Lorsque vous utilisez des étiquettes de confidentialité dans les Applications Microsoft 365 pour les entreprises sur des ordinateurs Windows, vous avez le choix entre utiliser un client Azure Information Protection ou utiliser l'étiquetage intégré à Office.

L’étiquetage intégré est désactivé par défaut dans ces applications lorsque le client Azure Information Protection est installé. Pour plus d'informations, y compris sur la façon de modifier de comportement par défaut, voir [Client d’étiquetage intégré Office et client Azure Information Protection](sensitivity-labels-office-apps.md#office-built-in-labeling-client-and-the-azure-information-protection-client).

Même lorsque vous utilisez l'étiquetage intégré dans les applications Office, vous pouvez également utiliser le client d'étiquetage unifié Azure Information Protection avec des étiquettes de confidentialité pour les éléments suivants :

- Un scanneur pour découvrir les informations sensibles stockées localement, puis, éventuellement, étiqueter ce contenu

- Options de cliquer avec le bouton droit dans l’Explorateur de fichiers pour que les utilisateurs puissent appliquer des étiquettes à tous les types de fichiers

- Visionneuse pour afficher des fichiers chiffrés pour du texte, des images ou des documents PDF

- Module PowerShell pour découvrir des informations sensibles dans des fichiers locaux, et appliquer ou supprimer des étiquettes et un chiffrement à partir de ces fichiers.

Si vous débutez sur Azure Information Protection, ou si vous êtes un client Azure Information Protection existant et que vous venez de migrer vos étiquettes, voir [Choisir le client d’étiquetage à utiliser pour les ordinateurs Windows](https://docs.microsoft.com/azure/information-protection/rms-client/use-client#choose-which-labeling-client-to-use-for-windows-computers) dans la documentation Azure Information Protection.

## <a name="sensitivity-labels-and-microsoft-cloud-app-security"></a>Étiquettes de confidentialité et Microsoft Cloud App Security

Grâce à l'utilisation de Cloud App Security (CAS), vous pouvez explorer, classifier, étiqueter et protéger le contenu dans des applications et services tiers, tels que SalesForce, Box ou Dropbox. 

Cloud App Security fonctionne avec les étiquettes de confidentialité et les étiquettes d’Azure Information Protection :

- Si les centres d’administration de l'étiquetage ont une ou plusieurs étiquettes de confidentialité [publiées](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy) vers au moins un utilisateur : les étiquettes de confidentialité sont utilisées.

- Si les étiquettes de confidentialité des centres d’administration de l'étiquetage ne sont pas publiées : les étiquettes Azure Information Protection sont utilisées.

Pour obtenir des instructions sur l’utilisation de Cloud App Security avec ces étiquettes, voir [Intégration d'Azure Information Protection](https://docs.microsoft.com/cloud-app-security/azip-integration).

## <a name="sensitivity-labels-and-the-microsoft-information-protection-sdk"></a>Les étiquettes de confidentialité et Microsoft Information Protection SDK

Une étiquette de confidentialité étant stockée sous forme de texte clair dans les métadonnées d’un document, les applications et services tiers peuvent lire et écrire dans ces métadonnées d'étiquetage pour compléter votre déploiement d’étiquetage. Par ailleurs, les développeurs de logiciels peuvent utiliser le kit de développement logiciel (SDK) [Microsoft Information Protection](https://docs.microsoft.com/information-protection/develop/overview#microsoft-information-protection-sdk) pour prendre en charge les fonctionnalités d’étiquetage et de chiffrement sur plusieurs plateformes. Pour en savoir plus, voir [l'annonce de la disponibilité générale sur le blog de la Communauté technique](https://techcommunity.microsoft.com/t5/Microsoft-Information-Protection/Microsoft-Information-Protection-SDK-Now-Generally-Available/ba-p/263144). 

Vous pouvez également en savoir plus sur les [solutions de partenaires intégrées à Microsoft Information Protection](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Microsoft-Information-Protection-showcases-integrated-partner/ba-p/262657).

## <a name="deployment-guidance"></a>Instructions de déploiement

Pour la planification et les instructions relatives au déploiement, notamment les informations relatives aux licences, les autorisations, la stratégie de déploiement, une liste de scénarios pris en charge et la documentation de l’utilisateur final, consultez [Prise en main des étiquettes de confidentialité](get-started-with-sensitivity-labels.md).
