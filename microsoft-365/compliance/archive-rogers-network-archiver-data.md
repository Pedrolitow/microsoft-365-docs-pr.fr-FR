---
title: Configurer un connecteur pour archiver les données du réseau Rogers dans Microsoft 365
description: Les administrateurs peuvent configurer un connecteur TeleMessage pour importer et archiver les données du réseau Rogers dans Microsoft 365. Cela vous permet d’archiver des données à partir de sources de données tierces dans Microsoft 365 afin de pouvoir utiliser des fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer les données tierces de votre organisation.
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- tier3
- purview-compliance
- data-connectors
ms.openlocfilehash: 672cc32a61491960da79c0838f5d07f611e165d5
ms.sourcegitcommit: ab45f2963e0635ff2cb9670f6f7b4c784f6a250e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2022
ms.locfileid: "68814118"
---
# <a name="set-up-a-connector-to-archive-rogers-network-data"></a>Configurer un connecteur pour archiver les données du réseau Rogers

Utilisez le connecteur TeleMessage dans le portail de conformité Microsoft Purview pour importer et archiver des données SMS et MMS à partir du réseau mobile de Rogers. Après avoir configuré et configuré un [connecteur Rogers Network Archiver](https://www.telemessage.com/mobile-archiver/network-archiver/rogers/), il se connecte au réseau mobile Rogers de votre organisation et importe les données SMS et MMS dans les boîtes aux lettres dans Microsoft 365.

Une fois que les données du réseau mobile rogers sont stockées dans les boîtes aux lettres des utilisateurs, vous pouvez appliquer des fonctionnalités Microsoft Purview telles que la conservation pour litige, la recherche de contenu et les stratégies de rétention Microsoft 365 aux données. Par exemple, vous pouvez rechercher des MESSAGES SMS et MMS à partir du réseau mobile de Rogers à l’aide de la recherche de contenu ou d’une recherche associée à un cas Microsoft Purview eDiscovery (Standard). L’utilisation d’un connecteur Rogers Network Archiver pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux réglementations et aux stratégies réglementaires de gouvernance d’entreprise.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="overview-of-archiving-rogers-mobile-network-data"></a>Vue d’ensemble de l’archivage des données du réseau mobile Rogers

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur pour archiver les données SMS et MMS de Rogers dans Microsoft 365.

![Flux de travail d’archivage du réseau Rogers.](../media/RogersNetworkConnectorWorkflow.png)

1. Votre organisation utilise TeleMessage pour configurer un connecteur Rogers Network Archiver. Pour plus d’informations, consultez [Activation de l’archiveur réseau Rogers de télémessage pour Microsoft 365](https://www.telemessage.com/microsoft-365-activation-for-the-rogers-network-archiver/).

2. En temps réel, les données du réseau mobile Rogers de votre organisation sont copiées sur le site TéléMessage.

3. Le connecteur Rogers Network Archiver que vous créez dans le portail de conformité se connecte au site TéléMessage tous les jours et transfère les messages électroniques des dernières 24 heures vers une zone de stockage Azure sécurisée dans le cloud Microsoft.

4. Le connecteur importe les éléments de communication mobiles dans la boîte aux lettres d’un utilisateur spécifique. Un nouveau dossier nommé Rogers SMS/MMS Network Archiver est créé dans la boîte aux lettres de l’utilisateur spécifique et les éléments y sont importés. Le connecteur effectue le mappage à l’aide de la valeur de la propriété *d’adresse Email de l’utilisateur*. Chaque e-mail contient cette propriété, qui est remplie avec l’adresse e-mail de chaque participant du message électronique.

   En plus du mappage automatique des utilisateurs à l’aide de la valeur de la propriété *d’adresse Email de l’utilisateur*, vous pouvez également définir un mappage personnalisé en chargeant un fichier de mappage CSV. Ce fichier de mappage doit contenir le numéro de téléphone mobile de l’utilisateur et l’adresse de boîte aux lettres Microsoft 365 correspondante pour chaque utilisateur. Si vous activez le mappage automatique des utilisateurs et fournissez un mappage personnalisé, pour chaque élément de courrier électronique, le connecteur examine d’abord le fichier de mappage personnalisé. S’il ne trouve pas d’utilisateur Microsoft 365 valide qui correspond au numéro de téléphone mobile d’un utilisateur, le connecteur utilise la propriété d’adresse e-mail de l’utilisateur de l’élément de messagerie. Si le connecteur ne trouve pas d’utilisateur Microsoft 365 valide dans le fichier de mappage personnalisé ou la propriété *d’adresse e-mail de l’utilisateur de l’élément* de messagerie, l’élément n’est pas importé.

## <a name="before-you-set-up-a-connector"></a>Avant de configurer un connecteur

- Commandez le [service Rogers Network Archiver à télémessage](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365/) et obtenez un compte d’administration valide pour votre organisation. Vous devez vous connecter à ce compte lorsque vous créez le connecteur dans le centre de conformité.

- Inscrivez tous les utilisateurs qui nécessitent l’archivage du réseau Rogers dans le compte TéléMessage. Lorsque vous inscrivez des utilisateurs, veillez à utiliser la même adresse e-mail que celle utilisée pour leur compte Microsoft 365.

- Vos employés doivent avoir des téléphones mobiles appartenant à l’entreprise et responsables de l’entreprise sur le réseau mobile O2. L’archivage des messages dans Microsoft 365 n’est pas disponible pour les appareils appartenant aux employés ou « ByOD ( Bring Your Own Devices).

- Obtenez le compte Rogers et les coordonnées de facturation de votre organisation afin de pouvoir remplir les formulaires d’intégration et commander le service d’archivage des messages de Rogers.

- L’utilisateur qui crée un connecteur Rogers Network Archiver à l’étape 3 doit se voir attribuer le rôle de Administration connecteur de données. Ce rôle est requis pour ajouter des connecteurs dans la page **Connecteurs de données** du portail de conformité. Ce rôle est ajouté par défaut à plusieurs groupes de rôles. Pour obtenir la liste de ces groupes de rôles, consultez la section « Rôles dans les portails defender et de conformité » dans [Rôles et groupes de rôles dans les portails de conformité Microsoft 365 Defender et Microsoft Purview](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-defender-and-compliance-portals). Un administrateur de votre organisation peut également créer un groupe de rôles personnalisé, attribuer le rôle de Administration connecteur de données, puis ajouter les utilisateurs appropriés en tant que membres. Pour obtenir des instructions, consultez la section « Créer un groupe de rôles personnalisé » dans [Autorisations dans le portail de conformité Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ce connecteur de données TeleMessage est disponible dans les environnements GCC dans le cloud Microsoft 365 US Government. Les applications et services tiers peuvent impliquer le stockage, la transmission et le traitement des données client de votre organisation sur des systèmes tiers qui se trouvent en dehors de l’infrastructure Microsoft 365 et ne sont donc pas couverts par les engagements de Microsoft Purview et de protection des données. Microsoft ne fait aucune déclaration selon laquelle l’utilisation de ce produit pour se connecter à des applications tierces implique que ces applications tierces sont conformes à FEDRAMP.

## <a name="create-a-rogers-network-archiver-connector"></a>Créer un connecteur Rogers Network Archiver

Une fois que vous avez rempli les conditions préalables décrites dans la section précédente, vous pouvez créer le connecteur Rogers Network Archiver dans le portail de conformité. Le connecteur utilise les informations que vous fournissez pour vous connecter au site TéléMessage et transférer les données SMS/MMS de Rogers vers les boîtes aux lettres utilisateur correspondantes dans Microsoft 365.

1. Accédez à <https://compliance.microsoft.com> , puis sélectionnez **Connecteurs** >  de données **Rogers Network Archiver**.

2. Dans la page de description du produit **Rogers Network Archiver** , sélectionnez **Ajouter un connecteur**.

3. Dans la page **Conditions d’utilisation du service** , sélectionnez **Accepter**.

4. Dans la page **Connexion au télémessage** , sous Étape 3, entrez les informations requises dans les zones suivantes, puis sélectionnez **Suivant**.

    - **Nom d'utilisateur:** Votre nom d’utilisateur TeleMessage.

    - **Mot de passe:** Votre mot de passe de télémessage.

5. Une fois le connecteur créé, vous pouvez fermer la fenêtre contextuelle et accéder à la page suivante.

6. Dans la page **Mappage d’utilisateurs** , activez le mappage automatique des utilisateurs. Pour activer le mappage personnalisé, chargez un fichier CSV qui contient les informations de mappage utilisateur, puis sélectionnez **Suivant**.

7. Passez en revue vos paramètres, puis sélectionnez **Terminer** pour créer le connecteur.

8. Accédez à l’onglet Connecteurs de la page **Connecteurs de données** pour voir la progression du processus d’importation du nouveau connecteur.

## <a name="known-issues"></a>Problèmes connus

- Pour l’instant, nous ne prenons pas en charge l’importation de pièces jointes ou d’éléments d’une taille supérieure à 10 Mo. La prise en charge des éléments plus volumineux sera disponible ultérieurement.
