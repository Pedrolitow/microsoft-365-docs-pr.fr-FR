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
ms.openlocfilehash: efb0d8401cca8fd0e8c2450a5d35788015f37dad
ms.sourcegitcommit: 3dd9944a6070a7f35c4bc2b57df397f844c3fe79
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2020
ms.locfileid: "42073175"
---
# <a name="get-started-with-sensitivity-labels"></a>Prise en main des étiquettes de confidentialité

Pour en savoir plus sur les étiquettes de confidentialité et la façon dont elles peuvent vous aider à protéger les données de votre organisation, voir [Plus d'informations sur les étiquettes de confidentialité](sensitivity-labels.md).

Si vous disposez d'[Azure Information Protection](https://docs.microsoft.com/azure/information-protection/what-is-information-protection), déterminez si vous devez migrer des étiquettes vers la plateforme d’étiquetage unifiée et le type de client d’étiquetage à utiliser :
- [Comment puis-je savoir si mon client utilise la plateforme d’étiquetage unifiée ?](https://docs.microsoft.com/azure/information-protection/faqs#how-can-i-determine-if-my-tenant-is-on-the-unified-labeling-platform)
- [Choisir le client d’étiquetage à utiliser pour des ordinateurs Windows](https://docs.microsoft.com/azure/information-protection/rms-client/use-client#choose-which-labeling-client-to-use-for-windows-computers)

Lorsque vous êtes prêt à protéger les données de votre organisation en utilisant des étiquettes de confidentialité :

1. **Créez les étiquettes.** Créez et nommez vos étiquettes de confidentialité conformément à la taxonomie de classification de votre organisation pour différents niveaux de confidentialité de contenu. Utilisez des noms ou termes courants qui ont du sens pour vos utilisateurs. Si vous n’avez pas encore établi de taxonomie, songez à commencer par des noms d’étiquettes tels que Personnel, Publique, Général, Confidentiel et Très confidentiel. Vous pouvez ensuite employer des sous-étiquettes pour regrouper par catégorie des étiquettes similaires. Lorsque vous créez une étiquette, utilisez le texte d’info-bulle pour aider les utilisateurs à sélectionner les étiquettes appropriées.

2. **Définissez l’incidence possible de chaque étiquette.** Configurez les paramètres de protection que vous voulez associer à chaque étiquette. Par exemple, vous pouvez souhaiter que le contenu ayant un niveau de confidentialité inférieur (tel qu’une étiquette « Général ») puisse comporter un simple en-tête ou pied de page, tandis que le contenu d’un niveau de confidentialité supérieur (tel qu’une étiquette « Confidentiel ») devrait contenir un filigrane, un chiffrement ou l'application de la protection de point de terminaison.

3. **Publiez les étiquettes.** Après avoir configuré vos étiquettes de confidentialité, publiez-les à l’aide d’une stratégie d’étiquette. Déterminez les utilisateurs et les groupes devant utiliser les étiquettes ainsi que les paramètres de stratégie à utiliser. Une étiquette unique est réutilisable : vous la définissez une fois, puis vous l’incluez dans plusieurs stratégies d’étiquette affectées à différents utilisateurs. Par exemple, vous pouvez piloter vos étiquettes de confidentialité en attribuant une stratégie d’étiquette à quelques utilisateurs seulement. Lorsque vous êtes prêt à déployer les étiquettes dans votre organisation, vous pouvez créer une nouvelle stratégie d’étiquette pour vos étiquettes et spécifier cette fois tous les utilisateurs.

Le flux de base des actions de l’administrateur, de l’utilisateur et des applications et services Office liés au fonctionnement des étiquettes de niveau de confidentialité :

![Diagramme illustrant le flux de travail des étiquettes de confidentialité](../media/Sensitivity-label-flow.png)

## <a name="common-scenarios-for-sensitivity-labels"></a>Scénarios courants relatifs aux étiquettes de confidentialité

Utilisez la section de documentation suivante qui vous vient en aide lors du déploiement d’étiquette de confidentialité :

|Je veux...|Documentation|
|----------------|---------------|
|Créer et publier des étiquettes de confidentialité qui me permettent de protéger les données de mon organisation|[Créer et configurer des étiquettes de confidentialité ainsi que leurs stratégies](create-sensitivity-labels.md)|
|Chiffrer les documents et messages électroniques à l’aide d’étiquettes de confidentialité et limiter le nombre de personnes pouvant y accéder et la manière dont elles peuvent utiliser ce contenu |[Restreindre l'accès au contenu grâce à la mise en place d'un chiffrement par les étiquettes de confidentialité](encryption-sensitivity-labels.md)|
|Activer les fonctionnalités de collaboration dans SharePoint (et OneDrive) pour les documents étiquetés à l'aide du chiffrement | [Activer les étiquettes de confidentialité pour les fichiers Office dans SharePoint et OneDrive (préversion publique)](sensitivity-labels-sharepoint-onedrive-files.md)
|Gérer les étiquettes de confidentialité des applications Office pour que le contenu soit étiqueté lors de sa création |[Utiliser les étiquettes de confidentialité dans les applications Office](sensitivity-labels-office-apps.md)|
|Appliquer automatiquement des étiquettes de confidentialité ou recommander l'emploi d'étiquettes par les utilisateurs lorsque du contenu est créé | [Appliquer automatiquement une étiquette de confidentialité à du contenu](apply-sensitivity-label-automatically.md)|
|Utiliser des étiquettes de confidentialité pour protéger du contenu dans Teams et SharePoint |[Utiliser des étiquettes de confidentialité avec Microsoft Teams, les groupes Office 365 et les sites SharePoint (préversion publique)](sensitivity-labels-teams-groups-sites.md)|
|Découvrir, étiqueter et protéger des fichiers stockés dans des banques de données locales |[Déploiement du scanner Azure Information Protection pour classifier et protéger automatiquement des fichiers](https://docs.microsoft.com/azure/information-protection/deploy-aip-scanner)|
|Découvrir, étiqueter et protéger des fichiers stockés dans des banques de données sur le cloud |[Découvrir, classifier, étiqueter et protéger les données réglementées et sensibles stockées dans le cloud](https://docs.microsoft.com/cloud-app-security/best-practices#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)|
|Visualiser la façon dont les étiquettes de confidentialité sont utilisées pour établir un état du déploiement et ajuster la configuration des étiquettes|[Afficher l’utilisation d’étiquettes à l'aide des analyses d’étiquettes](label-analytics.md)|


## <a name="end-user-documentation-for-sensitivity-labels"></a>Documentation sur les étiquettes de confidentialité pour l’utilisateur final

- [Appliquer des étiquettes de confidentialité à vos fichiers et vos e-mails dans Office](https://support.office.com/article/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)

- [Problèmes connus liés aux étiquettes de confidentialité dans Office](https://support.office.com/en-us/article/known-issues-with-sensitivity-labels-in-office-b169d687-2bbd-4e21-a440-7da1b2743edc)

- [Appliquer ou recommander automatiquement des étiquettes de confidentialité pour vos fichiers et e-mails dans Office](https://support.office.com/article/automatically-apply-or-recommend-sensitivity-labels-to-your-files-and-emails-in-office-622e0d9c-f38c-470a-bcdb-9e90b24d71a1)

- [Problèmes connus liés à l’application ou à la recommandation automatique des étiquettes de confidentialité](https://support.office.com/article/known-issues-with-automatically-applying-or-recommending-sensitivity-labels-451698ae-311b-4d28-83aa-a839a66f6efc)


