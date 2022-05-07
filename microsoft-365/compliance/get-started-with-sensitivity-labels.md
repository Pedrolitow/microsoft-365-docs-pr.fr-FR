---
title: Prise en main des étiquettes de confidentialité
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
- M365-security-compliance
- SPO_Content
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Vous êtes prêt à mettre en place d'étiquettes de confidentialité pour protéger les données de votre organisation, mais vous ne savez pas par où commencer ? Consultez quelques conseils pratiques permettant de vous familiariser lors de votre parcours dans l'univers de l'étiquetage.
ms.openlocfilehash: b0fcf435d7805440e93f0d1248723f4b5599d4a9
ms.sourcegitcommit: 265a4fb38258e9428a1ecdd162dbf9afe93eb11b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2022
ms.locfileid: "65268768"
---
# <a name="get-started-with-sensitivity-labels"></a>Prise en main des étiquettes de confidentialité

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

>*[Guide de sécurité et conformité pour les licences Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Pour en savoir plus sur les étiquettes de confidentialité et la façon dont elles peuvent vous aider à protéger les données de votre organisation, voir [Plus d'informations sur les étiquettes de confidentialité](sensitivity-labels.md).

Si vous avez [Azure Information Protection](/azure/information-protection/what-is-information-protection) et que vous utilisez toujours des étiquettes Azure Information Protection qui ont été gérées à partir du Portail Azure, vous devez migrer ces étiquettes vers la [plateforme d’étiquetage unifiée](/azure/information-protection/faqs#how-can-i-determine-if-my-tenant-is-on-the-unified-labeling-platform). Pour les ordinateurs Windows, vous pouvez ensuite [choisir quel client d'étiquetage utiliser](/azure/information-protection/rms-client/use-client#choose-which-labeling-client-to-use-for-windows-computers) pour vos étiquettes de confidentialité publiées.

Lorsque vous êtes prêt à protéger les données de votre organisation en utilisant des étiquettes de confidentialité :

1. **Créez les étiquettes.** Créez et nommez vos étiquettes de confidentialité conformément à la taxonomie de classification de votre organisation pour différents niveaux de confidentialité de contenu. Utilisez des noms ou termes courants qui ont du sens pour vos utilisateurs. Si vous n’avez pas encore établi de taxonomie, songez à commencer par des noms d’étiquettes tels que Personnel, Publique, Général, Confidentiel et Très confidentiel. Vous pouvez ensuite employer des sous-étiquettes pour regrouper par catégorie des étiquettes similaires. Lorsque vous créez une étiquette, utilisez le texte d’info-bulle pour aider les utilisateurs à sélectionner les étiquettes appropriées.
    
    Pour obtenir des instructions plus détaillées sur la définition d’une taxonomie de classification, téléchargez le Livre blanc « Classification des données et taxonomie de l’étiquette de confidentialité » à partir du [Portail d’approbation de services](https://aka.ms/DataClassificationWhitepaper).

2. **Définissez l’incidence possible de chaque étiquette.** Configurez les paramètres de protection que vous voulez associer à chaque étiquette. Par exemple, vous pouvez souhaiter que le contenu ayant un niveau de confidentialité inférieur (tel qu’une étiquette « Général ») puisse comporter un simple en-tête ou pied de page, tandis que le contenu d’un niveau de confidentialité supérieur (tel qu’une étiquette « Confidentiel ») devrait contenir un filigrane et un chiffrement.

3. **Publiez les étiquettes.** Après avoir configuré vos étiquettes de confidentialité, publiez-les à l’aide d’une stratégie d’étiquette. Déterminez les utilisateurs et les groupes devant utiliser les étiquettes ainsi que les paramètres de stratégie à utiliser. Une étiquette unique est réutilisable : vous la définissez une fois, puis vous l’incluez dans plusieurs stratégies d’étiquette affectées à différents utilisateurs. Par exemple, vous pouvez piloter vos étiquettes de confidentialité en attribuant une stratégie d’étiquette à quelques utilisateurs seulement. Lorsque vous êtes prêt à déployer les étiquettes dans votre organisation, vous pouvez créer une nouvelle stratégie d’étiquette pour vos étiquettes et spécifier cette fois tous les utilisateurs.


> Vous pouvez être éligible à la création automatique d’étiquettes par défaut et à une stratégie d’étiquette par défaut qui s’occupe des étapes 1 à 3 à votre place. Pour plus d'informations, voir [Étiquettes et politiques par défaut pour Microsoft Purview Information Protection](mip-easy-trials.md).

Flux de base pour le déploiement et l'application d'étiquettes de confidentialité :

![Diagramme illustrant le flux de travail des étiquettes de confidentialité.](../media/Sensitivity-label-flow.png)

## <a name="subscription-and-licensing-requirements-for-sensitivity-labels"></a>Configuration requise pour les abonnements et les licences pour les étiquettes de confidentialité

Différents abonnements prennent en charge les étiquettes de confidentialité et les conditions requises pour les licences des utilisateurs dépendent des fonctionnalités utilisées.

Pour afficher les options de licence permettant à vos utilisateurs de bénéficier des fonctionnalités de conformité de Microsoft Purview, affichez les [Conseils de licence Microsoft 365 pour la sécurité et la conformité](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance). Pour les étiquettes de confidentialité, voir la section [Microsoft Purview Information Protection : Sensitivity labeling](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-information-protection-sensitivity-labeling) et le [téléchargement PDF](https://go.microsoft.com/fwlink/?linkid=2139145) associé pour les exigences de licence au niveau des fonctionnalités.

## <a name="permissions-required-to-create-and-manage-sensitivity-labels"></a>Autorisations nécessaires pour la création et la gestion d'étiquettes de confidentialité

Les membres de votre équipe de conformité qui créeront des étiquettes de confidentialité ont besoin d’autorisations sur le portail de conformité Microsoft Purview.

Par défaut, les administrateurs généraux de votre client ont accès à ce centre d’administration et pourront accorder l’accès aux responsables de la conformité et à d’autres personnes sans leur octroyer toutes les autorisations d’un administrateur de client. Pour accorder cet accès administrateur délégué limité, ajoutez des utilisateurs au groupe de rôles **Administrateur des données de conformité**, **Administrateur de la conformité** ou **Administrateur de la sécurité**. 

Au lieu d'utiliser les rôles par défaut, vous pouvez créer un groupe de rôles, puis ajouter les rôles **Administrateur des étiquettes de confidentialité** ou **Configuration d'organisation** à ce groupe. Pour un rôle en lecture seule, utilisez **Lecteur d’étiquettes de confidentialité**. 

> [!NOTE]
> Désormais en préversion, vous pouvez utiliser les groupes de rôles suivants :
> - **Protection des informations**
> - **Administrateurs Information Protection**
> - **Analystes Information Protection**
> - **Enquêteurs Information Protection**
> - **Lecteurs Information Protection**
>
> Pour une explication de chacun d'eux et les nouveaux rôles qu'ils contiennent, sélectionnez un groupe de rôles dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portail de conformité Microsoft Purview</a> > **Permissions et rôles** > **Centre de conformité** > **Rôles**, puis consultez la description dans le volet volant. Ou, voir [Groupes de rôles dans le centre de sécurité et de conformité](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center).

Pour obtenir des instructions pour ajouter des utilisateurs au groupe de rôles par défaut, rôles ou créer vos propres groupes de rôles, consultez [Autorisations dans le portail de conformité Microsoft Purview](microsoft-365-compliance-center-permissions.md).

Ces autorisations sont seulement nécessaires pour créer et configurer des étiquettes de confidentialité et leurs stratégies d’étiquette. Elles ne sont pas requises pour l'application d'étiquettes dans des applications ou des services. Si d’autres autorisations sont nécessaires pour des configurations spécifiques liées aux étiquettes de confidentialité, celles-ci sont répertoriées dans les instructions de documentation qui leur sont propres.

## <a name="deployment-strategy-for-sensitivity-labels"></a>Stratégie de déploiement des étiquettes de confidentialité
Une stratégie réussie pour le déploiement d’étiquettes de confidentialité d’une organisation consiste à créer une équipe opérationnelle virtuelle qui identifie et gère les exigences professionnelles et techniques, les épreuves de vérification technique, les points de contrôle internes et les approbations, ainsi que les déploiements finaux pour l’environnement de production.

En utilisant le tableau de la section suivante, nous vous recommandons d’identifier un ou deux de vos principaux scénarios correspondant aux besoins d’entreprise qui ont le plus d’impact. Une fois ces scénarios déployés, revenez à la liste pour identifier une ou deux prochaines priorités pour le déploiement.

## <a name="common-scenarios-for-sensitivity-labels"></a>Scénarios courants relatifs aux étiquettes de confidentialité

Dans tous les scénarios, vous devez [Créer et configurer des étiquettes de confidentialité et leurs stratégies](create-sensitivity-labels.md).

|Je veux...|Documentation|
|----------------|---------------|
|Gérer les étiquettes de confidentialité des applications Office pour que le contenu soit étiqueté lors de sa création – inclut le support pour l’étiquetage manuel sur toutes les plateformes |[Gérer les étiquettes de confidentialité dans les applications Office](sensitivity-labels-office-apps.md)|
|Étendre l'étiquetage à l'Explorateur de fichiers et à PowerShell avec des fonctionnalités supplémentaires pour les applications Office sur Windows (si nécessaire)|[Client d’étiquetage unifié Azure Information Protection pour Windows](/azure/information-protection/rms-client/aip-clientv2)|
|Chiffrer des documents et messages électroniques à l’aide d’étiquettes de confidentialité et limiter l’accès à ces contenus ainsi que leur utilisation |[Restreindre l'accès au contenu grâce à la mise en place d'un chiffrement par les étiquettes de confidentialité](encryption-sensitivity-labels.md)|
|Activer les étiquettes de confidentialité pour Office sur le web, avec la prise en charge de la co-création, de la découverte électronique, de la protection contre la perte de données, la recherche, même lorsque les documents sont chiffrés. | [Activer les étiquettes de confidentialité pour les fichiers Office dans SharePoint et OneDrive](sensitivity-labels-sharepoint-onedrive-files.md)
|Utiliser la co-édition et l’enregistrement automatique dans les applications de bureau Office lorsque les documents sont chiffrés | [Activer la co-édition pour les fichiers chiffrés avec les étiquettes de confidentialité](sensitivity-labels-coauthoring.md)
|Appliquer automatiquement des étiquettes de confidentialité aux documents et messages électroniques | [Appliquer automatiquement une étiquette de confidentialité à du contenu](apply-sensitivity-label-automatically.md)|
|Utiliser des étiquettes de confidentialité pour protéger du contenu dans Teams et SharePoint |[Utiliser des étiquettes de confidentialité avec Microsoft Teams, les Groupes Microsoft 365 et les sites SharePoint](sensitivity-labels-teams-groups-sites.md)|
|Utiliser des étiquettes de niveau de sensibilité pour configurer le type de lien de partage par défaut pour les sites et les documents individuels SharePoint et OneDrive |[Utilisez les étiquettes de confidentialité pour configurer le type de lien de partage par défaut pour les sites et les documents dans SharePoint et OneDrive](sensitivity-labels-default-sharing-link.md)|
|Appliquer une étiquette de niveau de sensibilité à un modèle de compréhension de document, afin que les documents identifiés dans une bibliothèque SharePoint soient automatiquement classés et protégés |[Appliquer une étiquette de confidentialité à un modèle dans Microsoft SharePoint Syntex](/microsoft-365/contentunderstanding/apply-a-sensitivity-label-to-a-model)|
|Empêcher ou signaler les utilisateurs sur le partage des fichiers ou des courriers électroniques avec une étiquette de confidentialité spécifique |[Utiliser les étiquettes de confidentialité comme condition dans les stratégies de protection contre la perte de données](dlp-sensitivity-label-as-condition.md) |
|Appliquer une étiquette de confidentialité à un fichier lorsque je reçois une alerte indiquant que le contenu contenant des données personnelles est partagé et nécessite une protection| [Examiner et corriger les alertes dans gestion des risques liés à la confidentialité](/privacy/priva/risk-management-alerts)|
|Appliquer une étiquette de rétention pour conserver ou supprimer des fichiers ou des messages électroniques qui ont une étiquette de niveau de sensibilité spécifique|[Application automatique d’une étiquette de rétention pour conserver ou supprimer du contenu](apply-retention-labels-automatically.md) |
|Découvrir, étiqueter et protéger des fichiers stockés dans des banques de données situées dans les locaux |[Déploiement du scanner Azure Information Protection pour classifier et protéger automatiquement des fichiers](/azure/information-protection/deploy-aip-scanner)|
|Découvrir, étiqueter et protéger des fichiers stockés sur le cloud|[Découvrir, classifier, étiqueter et protéger les données réglementées et sensibles stockées dans le cloud](/cloud-app-security/best-practices#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)|
|Appliquer et afficher les étiquettes dans Power BI, et protéger les données lorsqu’elles sont enregistrées en dehors du service.|[Étiquettes de confidentialité dans Power BI](/power-bi/admin/service-security-sensitivity-label-overview)|
|Surveiller et comprendre la manière dont les étiquettes de confidentialité sont utilisées dans mon organisation|[En savoir plus sur la classification des données](data-classification-overview.md)|
|Étendre les étiquettes de confidentialité à des applications et services tiers|[Kit de développement logiciel (SDK) de Microsoft Information Protection](/information-protection/develop/overview#microsoft-information-protection-sdk)|
|Étendre les étiquettes de confidentialité sur le contenu de mes ressources Microsoft Purview Data Map, telles que Azure Blob Storage, Azure Files, Azure Data Lake Storage et les sources de données multi-cloud|[Étiquetage dans Microsoft Purview Data Map](/azure/purview/create-sensitivity-label) |

## <a name="end-user-documentation-for-sensitivity-labels"></a>Documentation sur les étiquettes de confidentialité pour l’utilisateur final

La documentation la plus efficace pour l’utilisateur final est une aide personnalisée en fonction des instructions que vous fournissez pour les noms d’étiquette et des configurations que vous choisissez. Vous pouvez utiliser le paramètre de stratégie d’étiquette **Fournir aux utilisateurs un lien vers une page d’aide personnalisée** pour spécifier un lien interne pour cette documentation. Les utilisateurs peuvent y accéder facilement à partir du bouton **Niveau de confidentialité** :

- Pour l’étiquetage intégré : option du menu **En savoir plus**.
- Pour le client d’étiquetage unifié Azure Information Protection : option du menu **Aide et commentaires** > lien **En savoir plus** dans la boîte de dialogue Microsoft Azure Information Protection.

Pour vous aider à fournir votre documentation personnalisée, consultez la page et les téléchargements suivants que vous pouvez utiliser pour former vos utilisateurs : [Formation de l’utilisateur final pour les étiquettes de confidentialité](https://microsoft.github.io/ComplianceCxE/enduser/sensitivity/). 

Vous pouvez également utiliser les ressources suivantes pour afficher des instructions de base :

- [Appliquer des étiquettes de confidentialité à vos fichiers et vos e-mails dans Office](https://support.microsoft.com/en-us/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)
    - [Problèmes connus liés aux étiquettes de confidentialité dans Office](https://support.microsoft.com/en-us/office/known-issues-with-sensitivity-labels-in-office-b169d687-2bbd-4e21-a440-7da1b2743edc)

- [Appliquer ou recommander automatiquement des étiquettes de confidentialité pour vos fichiers et e-mails dans Office](https://support.office.com/article/automatically-apply-or-recommend-sensitivity-labels-to-your-files-and-emails-in-office-622e0d9c-f38c-470a-bcdb-9e90b24d71a1)
    - [Problèmes connus liés à l’application ou à la recommandation automatique des étiquettes de confidentialité](https://support.office.com/article/known-issues-with-automatically-applying-or-recommending-sensitivity-labels-451698ae-311b-4d28-83aa-a839a66f6efc)

- [Guide de l’utilisateur pour l’étiquetage unifié d’Azure Information Protection](/azure/information-protection/rms-client/clientv2-user-guide)

Si vos étiquettes de confidentialité appliquent le chiffrement pour les documents PDF, ces documents peuvent être ouverts avec Microsoft Edge sur Windows ou Mac. Pour obtenir plus d’informations et connaître des lecteurs alternatifs, consultez [Quels lecteurs PDF sont pris en charge pour les PDF protégés ?](/azure/information-protection/rms-client/protected-pdf-readers#viewing-protected-pdfs-in-microsoft-edge-on-windows-or-mac)
