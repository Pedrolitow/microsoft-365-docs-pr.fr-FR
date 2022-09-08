---
title: Prise en main de la gestion du cycle de vie des données
f1.keywords:
- NOCSH
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
- m365initiative-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MET150
description: Étapes normatives pour les administrateurs, les conditions requises de licence et les scénarios courants qui gèrent le cycle de vie des données de votre organisation.
ms.openlocfilehash: 0ed0abe1edee323bfae69836f9db49ca9d7e88e5
ms.sourcegitcommit: 6f36cb8c69090c62a006d461bfc5aa1139cf09a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2022
ms.locfileid: "67631272"
---
# <a name="get-started-with-data-lifecycle-management"></a>Prise en main de la gestion du cycle de vie des données

>*[Guide de sécurité et conformité pour les licences Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Êtes-vous prêt à commencer à gérer le cycle de vie des données de votre organisation en conservant le contenu que vous devez conserver et en supprimant les autres contenus ? Pour commencer, utilisez les conseils suivants pour la gestion du cycle de vie des données Microsoft Purview (anciennement Microsoft Information Governance) :

1. **Comprendre le fonctionnement de la rétention et de la suppression** dans Microsoft 365, puis identifier les charges de travail qui nécessitent une stratégie de rétention et si vous devez créer des étiquettes de rétention pour les exceptions : [En savoir plus sur la rétention](retention.md)
    
    > [!NOTE]
    > Si vous devez gérer des éléments de grande valeur dans le cadre d'exigences commerciales, légales ou réglementaires en matière d'archivage : Utilisez les étiquettes de conservation avec la [gestion des enregistrements](records-management.md) plutôt qu'avec la gestion du cycle de vie des données.

2. **Créez des stratégies de rétention** pour les charges de travail que vous avez identifiées, en spécifiant les paramètres de rétention et les actions requises par les stratégies de votre organisation ou les réglementations du secteur : [Créer des stratégies de rétention](create-retention-policies.md)
    
    Si nécessaire, [créez et appliquez des étiquettes de rétention pour vos exceptions](create-retention-labels-information-governance.md).

3. **Activer l’archivage des boîtes aux lettres** pour fournir aux utilisateurs un espace de stockage de boîte aux [lettres supplémentaire : activer les boîtes aux lettres d’archivage dans Microsoft 365](enable-archive-mailboxes.md)
    
    Si nécessaire pour prendre en charge les boîtes aux lettres d’archivage :
    
    - [Activez l’archivage à extension automatique](enable-autoexpanding-archiving.md) pour les boîtes aux lettres qui ont besoin de plus de 100 Go de stockage.
    
    - Utilisez des [balises de rétention avec une stratégie de rétention de la gestion des enregistrements de messagerie (MRM)](set-up-an-archive-and-deletion-policy-for-mailboxes.md) si vous devez personnaliser la façon dont les messages électroniques sont automatiquement déplacés de la boîte aux lettres principale d’un utilisateur vers sa boîte aux lettres d’archivage, ou si vous devez spécifier des paramètres de rétention et de suppression pour des dossiers spécifiques plutôt que pour la boîte aux lettres entière.

4. **Comprendre et gérer les boîtes aux lettres inactives** qui conservent le contenu des boîtes aux lettres après que les employés ont quitté l’organisation : [En savoir plus sur les boîtes aux lettres inactives](inactive-mailboxes-in-office-365.md)

5. Si vous avez des fichiers PST qui contiennent des données que vous souhaitez régir : **Importez des fichiers PST dans des boîtes aux lettres en ligne** à l’aide du chargement réseau ou de l’expédition de disque : [En savoir plus sur l’importation des fichiers PST de votre organisation](importing-pst-files-to-office-365.md)

## <a name="subscription-and-licensing-requirements"></a>Conditions d’abonnement et de licence

Plusieurs abonnements prennent en charge les fonctionnalités de gestion du cycle de vie des données.

Pour afficher les options de licence permettant à vos utilisateurs de bénéficier des fonctionnalités de conformité de Microsoft Purview, affichez les [Conseils de licence Microsoft 365 pour la sécurité et la conformité](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance). Pour connaître les fonctionnalités répertoriées sur cette page, consultez la section [Gestion du cycle de vie des données Microsoft Purview & Gestion des enregistrements Microsoft Purview](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-data-lifecycle-management--microsoft-purview-records-management) pour connaître les exigences en matière de licences au niveau des fonctionnalités.

## <a name="permissions"></a>Autorisations

Consultez la section suivante pour plus d’informations sur les rôles et les groupes de rôles pour gérer la rétention Microsoft 365.

Pour les autorisations de gestion des boîtes aux lettres pour l'archivage, les boîtes aux lettres inactives et l'importation, celles-ci nécessitent généralement des autorisations Exchange, telles que le rôle Destinataires de courrier. Par défaut, ce rôle est attribué aux groupes de rôles Gestion des destinataires et Gestion de l’organisation. Pour obtenir les autorisations exactes requises pour chaque tâche de gestion, consultez la documentation qui accompagne les instructions de l’administrateur.

### <a name="permissions-for-retention-policies-and-retention-labels"></a>Autorisations pour les stratégies de rétention et les étiquettes de rétention

Les membres de votre équipe de conformité qui vont créer et gérer des stratégies de rétention et des étiquettes de rétention ont besoin d’autorisations sur le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portail de conformité Microsoft Purview</a>. Par défaut, l’administrateur client (administrateur général) a accès à cet emplacement et peut accorder l’accès aux responsables de la conformité et à d’autres personnes sans leur accorder toutes les autorisations d’un administrateur client. Pour accorder des autorisations pour cette administration limitée, nous vous recommandons d’ajouter des utilisateurs au groupe de rôles **Administrateur de conformité**.

Au lieu d'utiliser ce rôle par défaut, vous pouvez créer un nouveau groupe de rôles et ajouter le rôle **Gestion de la rétention** à ce groupe. Pour un rôle en lecture seule, utilisez **View-Only Retention Management**. 

Pour obtenir des instructions pour ajouter des utilisateurs aux rôles par défaut ou créer vos propres groupes de rôles, consultez [Autorisations dans le Portail de conformité Microsoft Purview](microsoft-365-compliance-center-permissions.md).

Ces autorisations ne sont nécessaires que pour créer, configurer et appliquer des politiques de rétention et des étiquettes de rétention. La personne qui configure ces stratégies et étiquettes n’a pas besoin d’avoir un accès au contenu.

## <a name="common-scenarios"></a>Scénarios courants

Utilisez le tableau suivant pour vous aider à mettre en correspondance vos besoins métier avec les scénarios les plus courants de gouvernance des informations.

|Je veux...|Documentation|
|----------------|---------------|
|Conservez ou supprimez efficacement les données pour les services Microsoft 365 : <br />- Exchange  <br />- SharePoint  <br />- OneDrive  <br />- Groupes Microsoft 365 <br />- Teams <br />- Yammer <br />- Skype Entreprise |[Créer et configurer des stratégies de rétention](create-retention-policies.md)|
|Fournir aux utilisateurs un espace de stockage supplémentaire pour leurs boîtes aux lettres |[Activer les boîtes aux lettres d’archivage dans Microsoft 365](enable-archive-mailboxes.md)|
|Conserver les données des boîtes aux lettres après que les employés ont quitté l'organisation |[Créer et gérer les boîtes aux lettres inactives](create-and-manage-inactive-mailboxes.md)|
|Télécharger les données de la boîte aux lettres à partir des fichiers PST |[Utiliser le chargement réseau pour importer des fichiers PST](use-network-upload-to-import-pst-files.md)|


Si vous avez un scénario qui nécessite la gestion des données d'éléments individuels, consultez les [scénarios communs pour la gestion des documents](get-started-with-records-management.md#common-scenarios). 

## <a name="end-user-documentation"></a>Documentation de l’utilisateur final

Consultez la section suivante pour plus d’informations sur la documentation de l’utilisateur final pour prendre en charge la rétention Microsoft 365.

Les fonctionnalités de gestion du cycle de vie des données pour les boîtes aux lettres inactives et l’importation de fichiers PST ne nécessitent pas de documentation de l’utilisateur final, car il s’agit uniquement d’opérations d’administration. Pour aider les utilisateurs à comprendre et à interagir avec leurs boîtes aux lettres d’archivage dans Outlook après avoir activé cette fonctionnalité, voir [Gérer le stockage des e-mails avec des boîtes aux lettres d'archivage en ligne](https://support.microsoft.com/office/manage-email-storage-with-online-archive-mailboxes-1cae7d17-7813-4fe8-8ca2-9a5494e9a721).

### <a name="end-user-documentation-for-retention-and-deletion"></a>Documentation de l’utilisateur final pour la rétention et la suppression

La plupart des stratégies de rétention fonctionnent discrètement en arrière-plan, sans interaction de l'utilisateur, et nécessitent donc peu de documentation pour les utilisateurs. Les stratégies de rétention pour Teams informe les utilisateurs lorsque leurs messages ont été supprimés avec un lien vers [Messages Teams concernant les stratégies de rétention](https://support.microsoft.com/office/teams-messages-about-retention-policies-c151fa2f-1558-4cf9-8e51-854e925b483b).

Toutefois, si vous complétez les stratégies de rétention avec des étiquettes de rétention, ces étiquettes ont une présence d’interface utilisateur dans les applications Microsoft 365. Avant de déployer ces étiquettes sur votre réseau de production, veillez à fournir des informations et des instructions aux utilisateurs finaux et à votre service d'assistance. Pour aider les utilisateurs à appliquer des étiquettes de fidélisation dans SharePoint et OneDrive, voir [Appliquer des étiquettes de fidélisation aux fichiers dans SharePoint ou OneDrive](https://support.microsoft.com/office/apply-retention-labels-to-files-in-sharepoint-or-onedrive-11a6835b-ec9f-40db-8aca-6f5ef18132df).

La documentation la plus efficace pour l'utilisateur final sera toujours constituée de conseils et d'instructions personnalisés que vous fournissez pour les noms et les configurations d'étiquettes de conservation que vous choisissez. Consultez la page suivante et les téléchargements que vous pouvez utiliser pour former vos utilisateurs : [Formation des utilisateurs finaux pour les étiquettes de rétention](https://microsoft.github.io/ComplianceCxE/enduser/retention/).

