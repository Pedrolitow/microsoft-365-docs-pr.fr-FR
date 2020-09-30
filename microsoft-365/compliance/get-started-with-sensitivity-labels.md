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
localization_priority: Priority
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Vous êtes prêt à instaurer la mise en place d'étiquettes de confidentialité pour protéger les données de votre organisation, mais vous ne savez pas par où commencer ? Consultez quelques conseils pratiques permettant de vous familiariser lors de votre parcours dans l'univers de l'étiquetage.
ms.openlocfilehash: 94edcb2e430b01ca423e6bb2a7baf51a407a52df
ms.sourcegitcommit: 15be7822220041c25fc52565f1c64d252e442d89
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2020
ms.locfileid: "48295218"
---
# <a name="get-started-with-sensitivity-labels"></a>Prise en main des étiquettes de confidentialité

>*[Guide de sécurité et conformité pour les licences Microsoft 365](https://aka.ms/ComplianceSD).*

Pour en savoir plus sur les étiquettes de confidentialité et la façon dont elles peuvent vous aider à protéger les données de votre organisation, voir [Plus d'informations sur les étiquettes de confidentialité](sensitivity-labels.md).

Si vous disposez d'[Azure Information Protection](https://docs.microsoft.com/azure/information-protection/what-is-information-protection), déterminez si vous devez migrer des étiquettes vers la plateforme d’étiquetage unifiée et le type de client d’étiquetage à utiliser :
- [Comment puis-je savoir si mon client utilise la plateforme d’étiquetage unifiée ?](https://docs.microsoft.com/azure/information-protection/faqs#how-can-i-determine-if-my-tenant-is-on-the-unified-labeling-platform)
- [Choisir le client d’étiquetage à utiliser pour des ordinateurs Windows](https://docs.microsoft.com/azure/information-protection/rms-client/use-client#choose-which-labeling-client-to-use-for-windows-computers)

Lorsque vous êtes prêt à protéger les données de votre organisation en utilisant des étiquettes de confidentialité :

1. **Créez les étiquettes.** Créez et nommez vos étiquettes de confidentialité conformément à la taxonomie de classification de votre organisation pour différents niveaux de confidentialité de contenu. Utilisez des noms ou termes courants qui ont du sens pour vos utilisateurs. Si vous n’avez pas encore établi de taxonomie, songez à commencer par des noms d’étiquettes tels que Personnel, Publique, Général, Confidentiel et Très confidentiel. Vous pouvez ensuite employer des sous-étiquettes pour regrouper par catégorie des étiquettes similaires. Lorsque vous créez une étiquette, utilisez le texte d’info-bulle pour aider les utilisateurs à sélectionner les étiquettes appropriées.
    
    Pour obtenir des instructions plus détaillées sur la définition d’une taxonomie de classification, téléchargez le Livre blanc « Classification des données et taxonomie de l’étiquette de confidentialité » à partir du [Portail d’approbation de services](https://aka.ms/DataClassificationWhitepaper).

2. **Définissez l’incidence possible de chaque étiquette.** Configurez les paramètres de protection que vous voulez associer à chaque étiquette. Par exemple, vous pouvez souhaiter que le contenu ayant un niveau de confidentialité inférieur (tel qu’une étiquette « Général ») puisse comporter un simple en-tête ou pied de page, tandis que le contenu d’un niveau de confidentialité supérieur (tel qu’une étiquette « Confidentiel ») devrait contenir un filigrane et un chiffrement.

3. **Publiez les étiquettes.** Après avoir configuré vos étiquettes de confidentialité, publiez-les à l’aide d’une stratégie d’étiquette. Déterminez les utilisateurs et les groupes devant utiliser les étiquettes ainsi que les paramètres de stratégie à utiliser. Une étiquette unique est réutilisable : vous la définissez une fois, puis vous l’incluez dans plusieurs stratégies d’étiquette affectées à différents utilisateurs. Par exemple, vous pouvez piloter vos étiquettes de confidentialité en attribuant une stratégie d’étiquette à quelques utilisateurs seulement. Lorsque vous êtes prêt à déployer les étiquettes dans votre organisation, vous pouvez créer une nouvelle stratégie d’étiquette pour vos étiquettes et spécifier cette fois tous les utilisateurs.

Flux de base pour le déploiement et l'application d'étiquettes de confidentialité :

![Diagramme illustrant le flux de travail des étiquettes de confidentialité](../media/Sensitivity-label-flow.png)

## <a name="subscription-and-licensing-requirements-for-sensitivity-labels"></a>Configuration requise pour les abonnements et les licences pour les étiquettes de confidentialité

Différents abonnements prennent en charge les étiquettes de confidentialité et les conditions requises pour les licences des utilisateurs dépendent des fonctionnalités utilisées.

Pour afficher les options de licence permettant à vos utilisateurs de bénéficier des fonctionnalités de conformité de Microsoft 365 à partir du 1er avril 2020, voir les [Conseils de licence Microsoft 365 pour la sécurité & la conformité](https://aka.ms/ComplianceSD). Pour les étiquettes de confidentialité, voir la section sur la [Protection des informations](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection) et le fichier PDF ou Excel associé à télécharger.

## <a name="permissions-required-to-create-and-manage-sensitivity-labels"></a>Autorisations nécessaires pour la création et la gestion d'étiquettes de confidentialité

Les membres de votre équipe de conformité qui créeront des étiquettes de confidentialité ont besoin d’autorisations dans le Centre de conformité Microsoft 365, le Centre de sécurité Microsoft 365 ou le Centre de sécurité et conformité. 

Par défaut, les administrateurs généraux de votre client ont accès à ces centres d’administration et pourront accorder l’accès aux responsables de la conformité et à d’autres personnes sans leur octroyer toutes les autorisations d’un administrateur de client. Pour accorder cet accès administrateur délégué limité, ajoutez des utilisateurs au groupe de rôles **Administrateur des données de conformité**, **Administrateur de la conformité** ou **Administrateur de la sécurité**. 

Au lieu d'utiliser les rôles par défaut, vous pouvez créer un groupe de rôles, puis ajouter les rôles **Administrateur des étiquettes de confidentialité** ou **Configuration d'organisation** à ce groupe. Pour un rôle en lecture seule, utilisez le **Lecteur d’étiquettes de confidentialité**. 

Pour obtenir des instructions sur l’ajout d’utilisateurs aux rôles par défaut ou sur la création de vos propres groupes de rôles, veuillez consulter la page [Octroi de l’accès au Centre de sécurité et conformité Office 365 aux utilisateurs](https://docs.microsoft.com/microsoft-365/security/office-365-security/grant-access-to-the-security-and-compliance-center).

Ces autorisations sont seulement nécessaires pour créer et configurer des étiquettes de confidentialité et leurs stratégies d’étiquette. Elles ne sont pas requises pour l'application d'étiquettes dans des applications ou des services. Si d’autres autorisations sont nécessaires pour des configurations spécifiques liées aux étiquettes de confidentialité, celles-ci sont répertoriées dans les instructions de documentation qui leur sont propres.

## <a name="deployment-strategy-for-sensitivity-labels"></a>Stratégie de déploiement des étiquettes de confidentialité
Une stratégie réussie pour le déploiement d’étiquettes de confidentialité d’une organisation consiste à créer une équipe opérationnelle virtuelle qui identifie et gère les exigences professionnelles et techniques, les épreuves de vérification technique, les points de contrôle internes et les approbations, ainsi que les déploiements finaux pour l’environnement de production.

En utilisant le tableau de la section suivante, nous vous recommandons d’identifier un ou deux de vos principaux scénarios correspondant aux besoins d’entreprise qui ont le plus d’impact. Une fois ces scénarios déployés, revenez à la liste pour identifier une ou deux prochaines priorités pour le déploiement.

Vous trouverez d’autres conseils généraux sur le déploiement dans le Guide d’accélération du déploiement de Microsoft 365 Information Protection et de la conformité. Si vous souhaitez obtenir plus d’informations, voir le billet de blog, [Guide d’accélération du déploiement de Microsoft Information Protection et de la conformité](https://techcommunity.microsoft.com/t5/microsoft-security-and/microsoft-information-protection-and-compliance-deployment/ba-p/1403493).

## <a name="common-scenarios-for-sensitivity-labels"></a>Scénarios courants relatifs aux étiquettes de confidentialité

Dans tous les scénarios, vous devez [Créer et configurer des étiquettes de confidentialité et leurs stratégies](create-sensitivity-labels.md).

|Je veux...|Documentation|
|----------------|---------------|
|Gérer les étiquettes de confidentialité des applications Office pour que le contenu soit étiqueté lors de sa création – inclut le support pour l’étiquetage manuel sur toutes les plateformes |[Utiliser les étiquettes de confidentialité dans les applications Office](sensitivity-labels-office-apps.md)|
|Permettre aux utilisateurs d’étiqueter et de protéger des fichiers à partir d’ordinateurs Windows à l’aide des applications Office, de l’Explorateur de fichiers et de PowerShell|[Client d’étiquetage unifié Azure Information Protection pour Windows](https://docs.microsoft.com/azure/information-protection/rms-client/aip-clientv2)|
|Chiffrer des documents et messages électroniques à l’aide d’étiquettes de confidentialité et limiter l’accès à ces contenus ainsi que leur utilisation |[Restreindre l'accès au contenu grâce à la mise en place d'un chiffrement par les étiquettes de confidentialité](encryption-sensitivity-labels.md)|
|Activer les étiquettes de confidentialité pour Office sur le web, avec la prise en charge de la co-création, de la découverte électronique, de la protection contre la perte de données, la recherche, même lorsque les documents sont chiffrés. | [Activer les étiquettes de confidentialité pour les fichiers Office dans SharePoint et OneDrive](sensitivity-labels-sharepoint-onedrive-files.md)
|Appliquer automatiquement des étiquettes de confidentialité aux documents et messages électroniques | [Appliquer automatiquement une étiquette de confidentialité à du contenu](apply-sensitivity-label-automatically.md)|
|Utiliser des étiquettes de confidentialité pour protéger du contenu dans Teams et SharePoint |[Utiliser des étiquettes de confidentialité avec Microsoft Teams, les Groupes Microsoft 365 et les sites SharePoint](sensitivity-labels-teams-groups-sites.md)|
|Empêcher ou signaler les utilisateurs sur le partage des fichiers ou des courriers électroniques avec une étiquette de confidentialité spécifique |[Utiliser les étiquettes de confidentialité comme condition dans les stratégies de protection contre la perte de données (préversion)](dlp-sensitivity-label-as-condition.md) |
|Découvrir, étiqueter et protéger des fichiers stockés dans des banques de données situées dans les locaux |[Déploiement du scanner Azure Information Protection pour classifier et protéger automatiquement des fichiers](https://docs.microsoft.com/azure/information-protection/deploy-aip-scanner)|
|Découvrir, étiqueter et protéger des fichiers stockés sur le cloud|[Découvrir, classifier, étiqueter et protéger les données réglementées et sensibles stockées dans le cloud](https://docs.microsoft.com/cloud-app-security/best-practices#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)|
|Appliquer et afficher les étiquettes de confidentialité dans Power BI et protéger les données lorsqu’elles sont exportées|[Comment appliquer des étiquettes de confidentialité dans Power BI](https://docs.microsoft.com/power-bi/admin/service-security-apply-data-sensitivity-labels)|
|Surveiller et comprendre la manière dont les étiquettes de confidentialité sont utilisées dans mon organisation|[Connaissez vos données : vue d’ensemble de la classification des données](data-classification-overview.md) <br /><br /> [Afficher l’utilisation d’étiquettes à l'aide des analyses d’étiquettes](label-analytics.md)|
|Étendre les étiquettes de confidentialité à des applications et services tiers|[Kit de développement logiciel (SDK) de protection des informations Microsoft](https://docs.microsoft.com/information-protection/develop/overview#microsoft-information-protection-sdk)|

## <a name="end-user-documentation-for-sensitivity-labels"></a>Documentation sur les étiquettes de confidentialité pour l’utilisateur final

La documentation la plus efficace pour l’utilisateur final est une aide personnalisée en fonction des instructions que vous fournissez pour les noms d’étiquette et des configurations que vous choisissez. Toutefois, vous pouvez utiliser les ressources suivantes pour afficher des instructions de base :

- [Appliquer des étiquettes de confidentialité à vos fichiers et vos e-mails dans Office](https://support.microsoft.com/fr-FR/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)
    - [Problèmes connus liés aux étiquettes de confidentialité dans Office](https://support.microsoft.com/fr-FR/office/known-issues-with-sensitivity-labels-in-office-b169d687-2bbd-4e21-a440-7da1b2743edc)

- [Appliquer ou recommander automatiquement des étiquettes de confidentialité pour vos fichiers et e-mails dans Office](https://support.office.com/article/automatically-apply-or-recommend-sensitivity-labels-to-your-files-and-emails-in-office-622e0d9c-f38c-470a-bcdb-9e90b24d71a1)
    - [Problèmes connus liés à l’application ou à la recommandation automatique des étiquettes de confidentialité](https://support.office.com/article/known-issues-with-automatically-applying-or-recommending-sensitivity-labels-451698ae-311b-4d28-83aa-a839a66f6efc)

- [Guide de l’utilisateur pour l’étiquetage unifié d’Azure Information Protection](https://docs.microsoft.com/azure/information-protection/rms-client/clientv2-user-guide)

Si vos étiquettes de confidentialité appliquent le chiffrement pour les documents PDF, ces documents peuvent être ouverts avec Microsoft Edge sur Windows ou Mac. Pour obtenir plus d’informations et connaître des lecteurs alternatifs, consultez [Quels lecteurs PDF sont pris en charge pour les PDF protégés ?](https://docs.microsoft.com/azure/information-protection/rms-client/protected-pdf-readers#viewing-protected-pdfs-in-microsoft-edge-on-windows-or-mac)
