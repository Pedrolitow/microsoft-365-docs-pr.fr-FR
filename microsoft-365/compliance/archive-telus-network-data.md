---
title: Configuration d’un connecteur pour l’archivage des données de réseau TELUS dans Microsoft 365
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
ROBOTS: NOINDEX, NOFOLLOW
description: Les administrateurs peuvent configurer un connecteur de télémessage pour importer et archiver des données SMS à partir du réseau TELUS dans Microsoft 365. Cela vous permet d’archiver des données provenant de sources de données tierces dans Microsoft 365 de sorte que vous puissiez utiliser les fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer les données tierces de votre organisation.
ms.openlocfilehash: f52ead856aeaabdf229a4798359042fd2651f777
ms.sourcegitcommit: b144e8ba1ab0c40fa7e0e8e893b5cb44aa2d8243
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2020
ms.locfileid: "47282656"
---
# <a name="set-up-a-connector-to-archive-telus-network-data-preview"></a>Configuration d’un connecteur pour l’archivage des données de réseau TELUS (aperçu)

Utilisez le connecteur de Télémessage dans le centre de conformité Microsoft 365 pour importer et archiver des données SMS (Short Messaging Service) à partir du réseau TELUS de votre organisation. Une fois que vous avez configuré et configuré un connecteur, celui-ci se connecte au réseau TELUS de votre organisation une fois par jour et importe les données SMS vers des boîtes aux lettres dans Microsoft 365.

Une fois les messages SMS stockés dans les boîtes aux lettres des utilisateurs, vous pouvez appliquer les fonctionnalités de conformité de Microsoft 365 telles que la conservation pour litige, la recherche de contenu et les stratégies de rétention de Microsoft 365 aux données TELUS. Par exemple, vous pouvez rechercher des messages SMS TELUS à l’aide de la recherche de contenu ou associer la boîte aux lettres qui contient les données TELUS à un dépositaire dans un cas avancé de découverte électronique. L’utilisation d’un connecteur réseau TELUS pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à respecter les stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-telus-network-data"></a>Vue d’ensemble de l’archivage des données de réseau TELUS

La vue d’ensemble suivante décrit le processus d’utilisation d’un connecteur pour archiver les données réseau TELUS dans Microsoft 365.

![Flux de travail d’archivage réseau TELUS](../media/TelusNetworkConnectorWorkflow.png)

1. Votre organisation utilise TeleMessage et TELUS pour configurer un connecteur réseau TELUS. Pour plus d’informations, consultez la rubrique [TELUS Network archiver](https://www.telemessage.com/office365-activation-for-telus-network-archiver/).

2. Une fois toutes les 24 heures, les messages SMS provenant du réseau TELUS de votre organisation sont copiés sur le site de Télémessage.

3. Le connecteur réseau TELUS que vous créez dans le centre de conformité Microsoft 365 se connecte au site de Télémessage quotidiennement et transfère les messages SMS des dernières 24 heures vers un emplacement de stockage Azure sécurisé dans le Cloud Microsoft. Le connecteur convertit également le contenu des messages SMS au format d’un message électronique.

4. Le connecteur importe les éléments de communication mobile vers la boîte aux lettres d’un utilisateur spécifique. Un nouveau dossier nommé **TELUS SMS Network archiver** est créé dans la boîte aux lettres de l’utilisateur spécifique et les éléments y sont importés. Le connecteur effectue le mappage à l’aide de la valeur de la propriété de l' *adresse de messagerie de l’utilisateur* . Chaque message SMS contient cette propriété, qui est renseignée avec l’adresse de messagerie de chaque participant du message SMS.

   Outre le mappage utilisateur automatique à l’aide de la valeur de la propriété d' *adresse de messagerie* de l’utilisateur, vous pouvez également implémenter un mappage personnalisé en téléchargeant un fichier de mappage CSV. Ce fichier de mappage contient le numéro de téléphone mobile et l’adresse de messagerie Microsoft 365 correspondante pour les utilisateurs de votre organisation. Si vous activez le mappage utilisateur et le mappage personnalisés, pour chaque élément TELUS, le connecteur examine d’abord le fichier de mappage personnalisé. S’il ne trouve pas un utilisateur Microsoft 365 valide correspondant au numéro de téléphone mobile d’un utilisateur, le connecteur utilise les valeurs de la propriété adresse de messagerie de l’élément qu’il tente d’importer. Si le connecteur ne trouve pas d’utilisateur Microsoft 365 valide dans le fichier de mappage personnalisé ou dans la propriété adresse de messagerie de l’élément TELUS, l’élément n’est pas importé.

## <a name="before-you-begin"></a>Avant de commencer

La plupart des étapes d’implémentation nécessaires à l’archivage des données réseau TELUS sont externes à Microsoft 365 et doivent être effectuées avant de pouvoir créer un connecteur dans le centre de conformité.

- Commandez le [service TELUS Network archiver à partir du Télémessage](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365) et obtenez un compte d’administration valide pour votre organisation. Vous devez vous connecter à ce compte lorsque vous créez le connecteur dans le centre de conformité.

- Obtenez votre compte réseau TELUS et les informations de contact de facturation pour pouvoir remplir les formulaires d’intégration de Télémessage et commander le service d’archivage de messages à partir de TELUS.

- Inscrivez tous les utilisateurs qui requièrent l’archivage réseau SMS TELUS dans le compte de Télémessage. Lors de l’inscription des utilisateurs, veillez à utiliser la même adresse de messagerie que celle utilisée pour leur compte Microsoft 365.

- Vos employés doivent posséder des téléphones mobiles appartenant à une entreprise et appartenant à une entreprise sur le réseau mobile theTELUS. Les messages d’archivage dans Microsoft 365 ne sont pas disponibles pour les appareils appartenant à un employé ou ne disposez pas de vos propres appareils (BYOD).

- Votre organisation doit consentir à autoriser le service d’importation Office 365 à accéder aux données de boîte aux lettres dans votre organisation. Vous devrez fournir ce consentement lors de la création du connecteur. Pour accepter cette demande, accédez à [cette page](https://login.microsoftonline.com/common/oauth2/authorize?client_id=570d0bec-d001-4c4e-985e-3ab17fdc3073&response_type=code&redirect_uri=https://portal.azure.com/&nonce=1234&prompt=admin_consent), connectez-vous à l’aide des informations d’identification d’un administrateur général Office 365, puis acceptez la demande. Vous devez effectuer cette étape avant de pouvoir créer un connecteur réseau TELUS.

- L’utilisateur qui crée un connecteur réseau TELUS doit disposer du rôle d’exportation d’importation de boîte aux lettres dans Exchange Online. Cela est nécessaire pour ajouter des connecteurs dans la page **connecteurs de données** dans le centre de conformité Microsoft 365. Par défaut, ce rôle n’est affecté à aucun groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle exportation d’importation de boîte aux lettres au groupe de rôles gestion de l’organisation dans Exchange Online. Vous pouvez aussi créer un groupe de rôles, attribuer le rôle d’exportation d’importation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, reportez-vous aux sections [créer des groupes de rôles](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#create-role-groups) ou modifier des [groupes](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#modify-role-groups) de rôles dans l’article « gérer des groupes de rôles dans Exchange Online ».

## <a name="create-a-telus-network-connector"></a>Créer un connecteur réseau TELUS

Une fois que vous avez terminé les conditions préalables décrites dans la section précédente, vous pouvez créer un connecteur réseau TELUS dans le centre de conformité Microsoft 365. Le connecteur utilise les informations que vous fournissez pour vous connecter au site de Télémessage et transférer les messages SMS vers les boîtes aux lettres utilisateur correspondantes dans Microsoft 365.

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com/) , puis cliquez sur **connecteurs de données**  >  **TELUS réseau**.

2. Sur la page Description du produit **réseau TELUS** , cliquez sur **Ajouter un connecteur** .

3. Sur la page **conditions de service** , cliquez sur **accepter**.

4. Sur la page **connexion à un message** , sous étape 3, entrez les informations requises dans les zones suivantes, puis cliquez sur **suivant**.

   - **Nom d’utilisateur :** Nom d’utilisateur de votre Télémessage.

   - **Mot de passe :** Mot de passe de votre Télémessage.

5. Une fois le connecteur créé, vous pouvez fermer la fenêtre contextuelle et passer à la page suivante.

6. Sur la page mappage de l' **utilisateur** , activez mappage utilisateur automatique, puis cliquez sur **suivant**. Si vous avez besoin d’un mappage personnalisé, téléchargez un fichier CSV, puis cliquez sur **suivant**.

7. Fournissez le consentement de l’administrateur, puis cliquez sur **suivant**.

   Pour fournir le consentement de l’administrateur, vous devez être connecté avec les informations d’identification d’un administrateur général Office 365, puis accepter la demande de consentement. Si vous n’êtes pas connecté en tant qu’administrateur général, vous pouvez accéder à [cette page](https://login.microsoftonline.com/common/oauth2/authorize?client_id=570d0bec-d001-4c4e-985e-3ab17fdc3073&response_type=code&redirect_uri=https://portal.azure.com/&nonce=1234&prompt=admin_consent) et vous connecter à l’aide des informations d’identification d’administrateur général pour accepter la demande.

8. Vérifiez vos paramètres, puis cliquez sur **Terminer** pour créer le connecteur.

9. Accédez à l’onglet Connecteurs de la page **connecteurs de données** pour voir la progression du processus d’importation pour le nouveau connecteur.

## <a name="known-issues"></a>Problèmes connus

- Le connecteur n’importe pas d’élément d’une taille supérieure à 10 Mo.
