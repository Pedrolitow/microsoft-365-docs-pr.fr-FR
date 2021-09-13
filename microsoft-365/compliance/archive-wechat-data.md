---
title: Configurer un connecteur pour archiver les données WeChat dans Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
description: Configurer et utiliser un connecteur dans le Centre de conformité Microsoft 365 pour importer et archiver des données WeChat dans Microsoft 365.
ms.openlocfilehash: 486340571c9650f9d10d367f056eeaa5a92aba55
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59209431"
---
# <a name="set-up-a-connector-to-archive-wechat-data"></a>Configurer un connecteur pour archiver les données WeChat

Utilisez le connecteur TeleMessage dans le Centre de conformité Microsoft 365 pour importer et archiver les appels, conversations, pièces jointes, fichiers et messages rappelés weChat et WeCom. Après avoir configuré et configuré un connecteur, il se connecte au compte TeleMessage de votre organisation et importe la communication mobile des employés à l’aide de l’archiveur WeChat TeleMessage dans les boîtes aux lettres de Microsoft 365.

Une fois que les données du connecteur d’archivage WeChat sont stockées dans les boîtes aux lettres des utilisateurs, vous pouvez appliquer des fonctionnalités de conformité Microsoft 365 telles que la conservation pour litige, eDiscovery, l’archivage In-Place, l’audit, la conformité des communications et les stratégies de rétention Microsoft 365 aux données de communication WeChat. Par exemple, vous pouvez effectuer une recherche dans la communication WeChat à l’aide de la recherche de contenu ou associer la boîte aux lettres contenant les données du connecteur de l’archiveur WeChat à un dépositaire dans un cas Advanced eDiscovery dossier. L’utilisation d’un connecteur d’archivage WeChat pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux réglementations de gouvernance d’entreprise et aux stratégies réglementaires.

## <a name="overview-of-archiving-wechat-communication-data"></a>Vue d’ensemble de l’archivage des données de communication WeChat

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur pour archiver les données de communications WeChat dans Microsoft 365.

![Flux de travail d’archivage pour les données de l’archiveur WeChat.](../media/WeChatConnectorWorkflow.png)

1. Votre organisation travaille avec TeleMessage pour configurer un connecteur d’archivage WeChat.

2. En temps réel, les données WeChat de votre organisation sont copiées sur le site TeleMessage.

3. Le connecteur d’archivage WeChat que vous créez dans le Centre de conformité Microsoft 365 se connecte au site TeleMessage tous les jours et transfère les messages électroniques des 24 heures précédentes vers une zone stockage Azure sécurisée dans Microsoft Cloud.

4. Le connecteur importe les éléments de communication mobile dans la boîte aux lettres d’un utilisateur spécifique. Un nouveau dossier nommé Archiveur WeChat sera créé dans la boîte aux lettres de l’utilisateur spécifique et les éléments y seront importés. Le connecteur est mappage à l’aide de la valeur de la propriété *d’adresse* de messagerie de l’utilisateur. Chaque message électronique contient cette propriété, qui est remplie avec l’adresse e-mail de chaque participant du message électronique. Outre le mappage automatique des utilisateurs à l’aide de la valeur de la propriété *d’adresse* de messagerie de l’utilisateur, vous pouvez également définir un mappage personnalisé en chargeant un fichier de mappage CSV. Ce fichier de mappage doit contenir le numéro mobile de l’utilisateur et l’adresse Microsoft 365 boîte aux lettres correspondante pour chaque utilisateur. Si vous activez le mappage utilisateur automatique et fournissez un mappage personnalisé, pour chaque élément de courrier électronique, le connecteur examinera d’abord le fichier de mappage personnalisé. S’il ne trouve pas un utilisateur Microsoft 365 valide qui correspond au numéro de téléphone mobile d’un utilisateur, le connecteur utilise la propriété d’adresse de messagerie de l’utilisateur de l’élément de courrier. Si le connecteur ne trouve pas d’utilisateur Microsoft 365 valide dans le fichier de mappage personnalisé ou dans la propriété d’adresse de messagerie de *l’utilisateur* de l’élément de courrier, l’élément n’est pas importé.

## <a name="before-you-set-up-a-connector"></a>Avant de configurer un connecteur

- Travaillez avec TeleMessage pour configurer un connecteur d’archivage WeChat. Pour plus d’informations, voir [Activating the TeleMessage WeChat Archiver for Microsoft 365](https://www.telemessage.com/microsoft-365-activation-for-wechat-archiver/).

- Configurer un connecteur TeleMessage pour Microsoft 365 et obtenir un compte d’administration d’entreprise valide. Pour plus d’informations, [voir Order Microsoft 365 Mobile Archiving](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-microsoft-365/).

- Enregistrez tous les utilisateurs qui nécessitent l’archivage WeChat dans le compte TeleMessage avec la même adresse de messagerie que celle utilisée pour le compte Microsoft 365 utilisateur.

- Vous devez installer l’application Tencent WeCom sur les téléphones mobiles des utilisateurs de votre organisation et l’activer. L’application WeCom permet aux utilisateurs de communiquer et de discuter avec d’autres utilisateurs WeChat et WeCom.

- L’utilisateur qui crée un connecteur d’archivage WeChat dans le Centre de conformité Microsoft 365 doit avoir le rôle Importation/Exportation de boîte aux lettres dans Exchange Online. Cela est nécessaire pour ajouter des connecteurs dans la page **Connecteurs de données** dans le centre de conformité. Par défaut, ce rôle n’est affecté à aucun groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle Importation/Exportation de boîte aux lettres au groupe de rôles Gestion de l’organisation dans Exchange Online. Vous pouvez également créer un groupe de rôles, attribuer le rôle Importation/Exportation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, voir les [sections](/Exchange/permissions-exo/role-groups#modify-role-groups) Créer des groupes de rôles ou Modifier des groupes de rôles dans l’article « Gérer les groupes de rôles dans Exchange Online ». [](/Exchange/permissions-exo/role-groups#create-role-groups)

- Ce connecteur de données est disponible dans Cloud de la communauté du secteur public environnements dans le cloud Microsoft 365 gouvernement américain. Les applications et services tiers peuvent impliquer le stockage, la transmission et le traitement des données client de votre organisation sur des systèmes tiers qui sont en dehors de l’infrastructure Microsoft 365 et qui, par conséquent, ne sont pas couverts par les engagements en matière de conformité et de protection des données Microsoft 365. Microsoft ne fait aucune représentation que l’utilisation de ce produit pour se connecter à des applications tierces implique que ces applications tierces sont conformes FEDRAMP.

## <a name="create-a-wechat-archiver-connector"></a>Créer un connecteur d’archivage WeChat

Suivez les étapes de cette section pour créer un connecteur d’archivage WeChat dans le Centre de conformité Microsoft 365. Le connecteur utilise les informations que vous fournissez pour vous connecter au site TeleMessage et transférer les données de communications WeChat vers les boîtes aux lettres utilisateur correspondantes dans Microsoft 365.

1. Go to <https://compliance.microsoft.com> and then click Data **connectors**  >  **WeChat Archiver**.

2. Dans la page description du produit **Archiveur WeChat,** cliquez sur **Ajouter un connecteur**

3. Dans la page **Conditions d’utilisation,** cliquez sur **Accepter.**

4. Dans la page **Connexion à TeleMessage,** sous l’étape 3, entrez les informations requises dans les zones suivantes, puis cliquez sur **Suivant**.

    - **Nom d’utilisateur**: votre nom d’utilisateur TeleMessage.

    - **Mot de** passe : votre mot de passe TeleMessage.

5. Une fois le connecteur créé, vous pouvez fermer la fenêtre pop-up et passer à la page suivante.

6. Dans la page **Mappage des utilisateurs,** activez le mappage utilisateur automatique. Vous pouvez également charger un fichier CSV de mappage utilisateur personnalisé.

7. Cliquez **sur** Suivant, examinez vos paramètres, puis cliquez sur **Terminer** pour créer le connecteur.

8. Go to the **Connectors** tab on **Data connectors** page to see the progress of the import process for the new connector.

## <a name="known-issues"></a>Problèmes détectés

- Pour l’instant, l’importation de pièces jointes ou d’éléments dont la taille est supérieure à 10 Mo n’est pas prise en charge. La prise en charge des éléments plus volumineux sera disponible à une date ultérieure.
