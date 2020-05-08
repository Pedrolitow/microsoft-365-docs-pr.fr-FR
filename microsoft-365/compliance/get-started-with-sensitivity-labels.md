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
ms.openlocfilehash: f024995f63af19efa410cdb02a1f8c8d110902eb
ms.sourcegitcommit: 7ff75a0f45371b247d975fc61cfa286f5b6f42f6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "44140990"
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

2. **Définissez l’incidence possible de chaque étiquette.** Configurez les paramètres de protection que vous voulez associer à chaque étiquette. Par exemple, vous pouvez souhaiter que le contenu ayant un niveau de confidentialité inférieur (tel qu’une étiquette « Général ») puisse comporter un simple en-tête ou pied de page, tandis que le contenu d’un niveau de confidentialité supérieur (tel qu’une étiquette « Confidentiel ») devrait contenir un filigrane, un chiffrement ou l'application de la protection de point de terminaison.

3. **Publiez les étiquettes.** Après avoir configuré vos étiquettes de confidentialité, publiez-les à l’aide d’une stratégie d’étiquette. Déterminez les utilisateurs et les groupes devant utiliser les étiquettes ainsi que les paramètres de stratégie à utiliser. Une étiquette unique est réutilisable : vous la définissez une fois, puis vous l’incluez dans plusieurs stratégies d’étiquette affectées à différents utilisateurs. Par exemple, vous pouvez piloter vos étiquettes de confidentialité en attribuant une stratégie d’étiquette à quelques utilisateurs seulement. Lorsque vous êtes prêt à déployer les étiquettes dans votre organisation, vous pouvez créer une nouvelle stratégie d’étiquette pour vos étiquettes et spécifier cette fois tous les utilisateurs.

Flux de base pour le déploiement et l'application d'étiquettes de confidentialité :

![Diagramme illustrant le flux de travail des étiquettes de confidentialité](../media/Sensitivity-label-flow.png)

## <a name="subscription-and-licensing-requirements-for-sensitivity-labels"></a>Configuration requise pour les abonnements et les licences pour les étiquettes de confidentialité

Différents abonnements prennent en charge les étiquettes de confidentialité et les conditions requises pour les licences des utilisateurs dépendent des fonctionnalités utilisées.

Pour afficher les options de licence permettant à vos utilisateurs de bénéficier des fonctionnalités de conformité de Microsoft 365 à partir du 1er avril 2020, voir les [Conseils de licence Microsoft 365 pour la sécurité & la conformité](https://aka.ms/ComplianceSD). Pour les étiquettes de confidentialité, voir la section sur la [Protection des informations](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection) et le fichier PDF ou Excel associé à télécharger.

## <a name="permissions-required-to-create-and-manage-sensitivity-labels"></a>Autorisations nécessaires pour la création et la gestion d'étiquettes de confidentialité

Les membres de votre équipe de conformité qui créeront des étiquettes de confidentialité ont besoin d’autorisations dans le Centre de conformité Microsoft 365, le Centre de sécurité Microsoft 365 ou le Centre de sécurité et conformité. 

Par défaut, les administrateurs généraux de votre client ont accès à ces centres d’administration et pourront accorder l’accès aux responsables de la conformité et à d’autres personnes sans leur octroyer toutes les autorisations d’un administrateur de clients. Pour accorder cet accès administrateur délégué limité, allez à la page **Autorisations** de l’un de ces centres d’administration, puis d’ajouter des membres au groupe de rôles **Administrateur des données de conformité**, **Administrateur de la conformité** ou **Administrateur de la sécurité**.

À défaut d'utiliser les rôles, vous pouvez créer un groupe de rôles, puis ajouter les rôles d'**Administrateur d'étiquettes de confidentialité** ou de **Configuration d'organisation** à ce groupe. Pour un rôle en lecture seule, utilisez le **Lecteur d’étiquettes de confidentialité**. Pour obtenir des instructions, reportez-vous à la rubrique [Octroi de l’accès au Centre de sécurité et conformité Office 365 aux utilisateurs](https://docs.microsoft.com/microsoft-365/security/office-365-security/grant-access-to-the-security-and-compliance-center).

Ces autorisations sont seulement nécessaires pour créer et configurer des étiquettes de confidentialité et leurs stratégies d’étiquette. Elles ne sont pas requises pour l'application d'étiquettes dans des applications ou des services.

> [!NOTE]
> Le **Lecteur d’étiquette de confidentialité** est un nouveau rôle qui prenait uniquement en charge les cmdlets d’étiquetage PowerShell au tout début. La prise en charge des centres d’étiquetage des administrateurs est désormais étendue aux clients.

## <a name="common-scenarios-for-sensitivity-labels"></a>Scénarios courants relatifs aux étiquettes de confidentialité

Utilisez la section de documentation suivante qui vous vient en aide lors du déploiement d’étiquette de confidentialité :

|Je veux...|Documentation|
|----------------|---------------|
|Créer et publier des étiquettes de confidentialité qui me permettent de protéger les données de mon organisation|[Créer et configurer des étiquettes de confidentialité ainsi que leurs stratégies](create-sensitivity-labels.md)|
|Chiffrer des documents et messages électroniques à l’aide d’étiquettes de confidentialité et limiter l’accès à ces contenus ainsi que leur utilisation |[Restreindre l'accès au contenu grâce à la mise en place d'un chiffrement par les étiquettes de confidentialité](encryption-sensitivity-labels.md)|
|Activer les fonctionnalités de collaboration dans SharePoint (et OneDrive) pour les documents étiquetés à l'aide du chiffrement | [Activer les étiquettes de confidentialité pour les fichiers Office dans SharePoint et OneDrive](sensitivity-labels-sharepoint-onedrive-files.md)
|Gérer les étiquettes de confidentialité des applications Office pour que le contenu soit étiqueté lors de sa création |[Utiliser les étiquettes de confidentialité dans les applications Office](sensitivity-labels-office-apps.md)|
|Appliquer automatiquement des étiquettes de confidentialité aux documents et messages électroniques | [Appliquer automatiquement une étiquette de confidentialité à du contenu](apply-sensitivity-label-automatically.md)|
|Utiliser des étiquettes de confidentialité pour protéger du contenu dans Teams et SharePoint |[Utiliser des étiquettes de confidentialité avec Microsoft Teams, les Groupes Microsoft 365 et les sites SharePoint (préversion publique)](sensitivity-labels-teams-groups-sites.md)|
|Découvrir, étiqueter et protéger des fichiers stockés dans des banques de données situées dans les locaux |[Déploiement du scanner Azure Information Protection pour classifier et protéger automatiquement des fichiers](https://docs.microsoft.com/azure/information-protection/deploy-aip-scanner)|
|Découvrir, étiqueter et protéger des fichiers stockés sur le cloud|[Découvrir, classifier, étiqueter et protéger les données réglementées et sensibles stockées dans le cloud](https://docs.microsoft.com/cloud-app-security/best-practices#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)|
|Appliquer et afficher les étiquettes de confidentialité dans Power BI et protéger les rapports téléchargés|[Protection des données dans Power BI (version d’évaluation)](https://docs.microsoft.com/power-bi/admin/service-security-data-protection-overview)|
|Visualiser la façon dont les étiquettes de confidentialité sont utilisées pour établir un état du déploiement et ajuster la configuration des étiquettes|[Afficher l’utilisation d’étiquettes à l'aide des analyses d’étiquettes](label-analytics.md)|


## <a name="end-user-documentation-for-sensitivity-labels"></a>Documentation sur les étiquettes de confidentialité pour l’utilisateur final

La documentation la plus efficace pour l’utilisateur final est une aide personnalisée en fonction des instructions que vous fournissez pour les noms d’étiquette et des configurations que vous choisissez. Toutefois, vous pouvez utiliser les ressources suivantes pour afficher des instructions de base :   

- [Appliquer des étiquettes de confidentialité à vos fichiers et vos e-mails dans Office](https://support.office.com/article/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)
    - [Problèmes connus liés aux étiquettes de confidentialité dans Office](https://support.office.com/fr-FR/article/known-issues-with-sensitivity-labels-in-office-b169d687-2bbd-4e21-a440-7da1b2743edc)

- [Appliquer ou recommander automatiquement des étiquettes de confidentialité pour vos fichiers et e-mails dans Office](https://support.office.com/article/automatically-apply-or-recommend-sensitivity-labels-to-your-files-and-emails-in-office-622e0d9c-f38c-470a-bcdb-9e90b24d71a1)
    - [Problèmes connus liés à l’application ou à la recommandation automatique des étiquettes de confidentialité](https://support.office.com/article/known-issues-with-automatically-applying-or-recommending-sensitivity-labels-451698ae-311b-4d28-83aa-a839a66f6efc)

- [Guide de l’utilisateur pour l’étiquetage unifié d’Azure Information Protection](https://docs.microsoft.com/azure/information-protection/rms-client/clientv2-user-guide)


