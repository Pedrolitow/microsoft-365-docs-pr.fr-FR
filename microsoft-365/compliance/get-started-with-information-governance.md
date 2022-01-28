---
title: Prise en main de la gouvernance des informations dans Microsoft 365
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
description: Prêt à commencer à régir les données de votre organisation, mais vous ne savez pas par où commencer ? Lisez quelques conseils normatifs pour commencer.
ms.openlocfilehash: 5b30dc870389c06bd006a056127439f1ec18ac65
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2022
ms.locfileid: "62242149"
---
# <a name="get-started-with-information-governance"></a>Prise en main de la gouvernance des informations

>*[Guide de sécurité et conformité pour les licences Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Vous êtes prêt à commencer à gouverner les données de votre organisation en conservant le contenu que vous devez conserver et en supprimant les autres contenus ? Utiliser les instructions suivantes, pour commencer:

1. **Comprendre le fonctionnement de la rétention et de la suppression** dans Microsoft 365, puis identifier les charges de travail qui nécessitent une stratégie de rétention et si vous devez créer des étiquettes de rétention pour les exceptions : [En savoir plus sur la rétention](retention.md)
    
    > [!NOTE]
    > Si vous avez besoin de gérer le cycle de vie d'éléments de grande valeur dans le cadre d'exigences commerciales, légales ou réglementaires en matière d'archivage : utilisez des étiquettes de rétention avec [gestion des enregistrements](records-management.md) plutôt que la gouvernance des informations.

2. **Créez des stratégies de rétention** pour les charges de travail que vous avez identifiées, en spécifiant les paramètres de rétention et les actions requises par les stratégies de votre organisation ou les réglementations du secteur : [Créer des stratégies de rétention](create-retention-policies.md)
    
    Si nécessaire, [créez et appliquez des étiquettes de rétention pour vos exceptions](create-retention-labels-information-governance.md).

3. **Activer l’archivage des boîtes aux lettres** afin de fournir aux utilisateurs un espace de stockage de boîte aux lettres supplémentaire : [Activer les boîtes aux lettres d’archivage dans le centre de conformité](enable-archive-mailboxes.md)
    
    Si nécessaire pour prendre en charge les boîtes aux lettres d’archivage :
    
    - [Activez l’archivage à extension automatique](enable-autoexpanding-archiving.md) pour les boîtes aux lettres qui ont besoin de plus de 100 Go de stockage.
    
    - Utilisez des [balises de rétention avec une stratégie de rétention de la gestion des enregistrements de messagerie (MRM)](set-up-an-archive-and-deletion-policy-for-mailboxes.md) si vous devez personnaliser la façon dont les messages électroniques sont automatiquement déplacés de la boîte aux lettres principale d’un utilisateur vers sa boîte aux lettres d’archivage, ou si vous devez spécifier des paramètres de rétention et de suppression pour des dossiers spécifiques plutôt que pour la boîte aux lettres entière.

4. **Comprendre et gérer les boîtes aux lettres inactives** qui conservent le contenu des boîtes aux lettres après que les employés ont quitté l’organisation : [En savoir plus sur les boîtes aux lettres inactives](inactive-mailboxes-in-office-365.md)

5. Si vous avez des fichiers PST qui contiennent des données que vous souhaitez régir : **Importez des fichiers PST dans des boîtes aux lettres en ligne** à l’aide du chargement réseau ou de l’expédition de disque : [En savoir plus sur l’importation des fichiers PST de votre organisation](importing-pst-files-to-office-365.md)

Indépendamment de ces étapes, **Utilisez des connecteurs pour importer et archiver des données tierces** qui incluent des données à partir de plateformes de réseaux sociaux, de plateformes de messagerie instantanée et de plateformes de collaboration sur des documents. Lorsque ces données sont importées dans des boîtes aux lettres en ligne, elles prennent en charge non seulement la gouvernance des informations du centre de conformité Microsoft 365, mais également d’autres solutions de conformité telles que la conformité des communications, la gestion des risques internes et eDiscovery. Pour plus d’informations, consultez [En savoir plus sur les connecteurs pour les données tierces](archiving-third-party-data.md).

## <a name="subscription-and-licensing-requirements"></a>Conditions d’abonnement et de licence

Un certain nombre d’abonnements différents prennent en charge des fonctionnalités de gouvernance des informations.

Pour afficher les options de licence permettant à vos utilisateurs de bénéficier des fonctionnalités de conformité de Microsoft 365, voir les [Conseils de licence Microsoft 365 pour la sécurité et la conformité](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance). Pour les fonctionnalités répertoriées sur cette page, consultez la section [Gouvernance des informations](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-governance) et le [téléchargement PDF](https://go.microsoft.com/fwlink/?linkid=2139145) associé pour les exigences de licence au niveau des fonctionnalités.

## <a name="permissions"></a>Autorisations

Consultez la section suivante pour plus d’informations sur les rôles et les groupes de rôles pour gérer la rétention Microsoft 365.

Pour les autorisations de gestion des boîtes aux lettres pour l'archivage, les boîtes aux lettres inactives et l'importation, celles-ci nécessitent généralement des autorisations Exchange, telles que le rôle Destinataires de courrier. Par défaut, ce rôle est attribué aux groupes de rôles Gestion des destinataires et Gestion de l’organisation. Pour obtenir les autorisations exactes requises pour chaque tâche de gestion, consultez la documentation qui accompagne les instructions de l’administrateur.

### <a name="permissions-for-retention-policies-and-retention-labels"></a>Autorisations pour les stratégies de rétention et les étiquettes de rétention

Les membres de votre équipe de conformité, appelés à créer et gérer des stratégies et des étiquettes de rétention, ont besoin d’autorisations pour accéder au <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centre de conformité Microsoft 365</a>. Par défaut, votre administrateur client (administrateur général) a accès à cet emplacement et peut accorder aux responsables de la conformité et à d’autres personnes un accès sans leur donner toutes les autorisations d’un administrateur client. Pour accorder des autorisations à cette administration limitée, nous vous recommandons d'ajouter des utilisateurs au groupe de rôles d’administrateur **Administrateur de la conformité**.

Au lieu d'utiliser ce rôle par défaut, vous pouvez créer un nouveau groupe de rôles et ajouter le rôle **Gestion de la rétention** à ce groupe. Pour un rôle en lecture seule, utilisez **View-Only Retention Management**. 

Pour obtenir des instructions pour ajouter des utilisateurs aux rôles par défaut ou créer vos propres groupes de rôles, consultez [Autorisations dans le Centre de conformité Microsoft 365](microsoft-365-compliance-center-permissions.md).

Ces autorisations ne sont nécessaires que pour créer, configurer et appliquer des politiques de rétention et des étiquettes de rétention. La personne qui configure ces stratégies et étiquettes n’a pas besoin d’avoir un accès au contenu.

## <a name="common-scenarios"></a>Scénarios courants

Utilisez le tableau suivant pour vous aider à mettre en correspondance vos besoins métier avec les scénarios les plus courants de gouvernance des informations.

|Je veux...|Documentation|
|----------------|---------------|
|Conservez ou supprimez efficacement les données pour les services Microsoft 365 : <br />- Exchange  <br />- SharePoint  <br />- OneDrive  <br />- Groupes Microsoft 365 <br />- Teams <br />- Yammer <br />- Skype Entreprise |[Créer et configurer des stratégies de rétention](create-retention-policies.md)|
|Fournir aux utilisateurs un espace de stockage supplémentaire pour leurs boîtes aux lettres |[Activer des boîtes aux lettres d’archivage dans le Centre conformité](enable-archive-mailboxes.md)|
|Conserver les données des boîtes aux lettres après que les employés ont quitté l'organisation |[Créer et gérer les boîtes aux lettres inactives](create-and-manage-inactive-mailboxes.md)|
|Télécharger les données de la boîte aux lettres à partir des fichiers PST |[Utiliser le chargement réseau pour importer des fichiers PST](use-network-upload-to-import-pst-files.md)|


Si vous avez un scénario qui nécessite une gestion du cycle de vie pour des éléments individuels, consultez les [Scénarios courants pour la gestion des enregistrements.](get-started-with-records-management.md#common-scenarios) 

## <a name="end-user-documentation"></a>Documentation de l’utilisateur final

Consultez la section suivante pour plus d’informations sur la documentation de l’utilisateur final pour prendre en charge la rétention Microsoft 365.

Les fonctionnalités de gouvernance des informations qui prend en charge la gestion des boîtes aux lettres (archivage, boîtes aux lettres inactives et importation) ne nécessitent généralement pas de documentation de l’utilisateur final.

### <a name="end-user-documentation-for-retention-and-deletion"></a>Documentation de l’utilisateur final pour la rétention et la suppression

La plupart des stratégies de rétention fonctionnent discrètement en arrière-plan, sans interaction de l'utilisateur, et nécessitent donc peu de documentation pour les utilisateurs. Les stratégies de rétention pour Teams informe les utilisateurs lorsque leurs messages ont été supprimés avec un lien vers [Messages Teams concernant les stratégies de rétention](https://support.microsoft.com/office/teams-messages-about-retention-policies-c151fa2f-1558-4cf9-8e51-854e925b483b).

Toutefois, si vous complétez les stratégies de rétention avec des étiquettes de rétention, ces étiquettes ont une présence d’interface utilisateur dans les applications Microsoft 365. Avant de déployer ces étiquettes sur votre réseau de production, veillez à fournir des informations et des instructions aux utilisateurs finaux et à votre service d'assistance. Pour aider les utilisateurs à appliquer des étiquettes de fidélisation dans SharePoint et OneDrive, voir [Appliquer des étiquettes de fidélisation aux fichiers dans SharePoint ou OneDrive](https://support.microsoft.com/office/apply-retention-labels-to-files-in-sharepoint-or-onedrive-11a6835b-ec9f-40db-8aca-6f5ef18132df).

La documentation la plus efficace pour l'utilisateur final sera toujours constituée de conseils et d'instructions personnalisés que vous fournissez pour les noms et les configurations d'étiquettes de conservation que vous choisissez. Consultez la page suivante et les téléchargements que vous pouvez utiliser pour former vos utilisateurs : [Formation des utilisateurs finaux pour les étiquettes de rétention](https://microsoft.github.io/ComplianceCxE/enduser/retention/).

