---
title: Isolation et contrôle d’accès dans Microsoft 365
ms.author: robmazz
author: robmazz
manager: scotv
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
f1.keywords:
- NOCSH
description: 'Résumé : Explication de l’isolation et du contrôle d’accès dans les différentes applications de Microsoft 365.'
ms.openlocfilehash: 7d978a4b5d864c9130fae3a61c11c0becb5e6870
ms.sourcegitcommit: e9323a90a1156c10b037abca3e16d7367ef92dd7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67570312"
---
# <a name="isolation-and-access-control-in-microsoft-365"></a>Isolation et contrôle d’accès dans Microsoft 365

Azure Active Directory (Azure AD) et Microsoft 365 utilisent un modèle de données très complexe qui inclut des dizaines de services, des centaines d’entités, des milliers de relations et des dizaines de milliers d’attributs. À un niveau élevé, Azure AD et les répertoires de service sont les conteneurs de locataires et de destinataires qui sont synchronisés à l’aide de protocoles de réplication basés sur l’état. Outre les informations d’annuaire contenues dans Azure AD, chacune des charges de travail de service dispose de sa propre infrastructure de services d’annuaire.
 
![Synchronisation des données client Microsoft 365.](../media/office-365-isolation-tenant-data-sync.png)

Dans ce modèle, il n’existe aucune source unique de données d’annuaire. Des systèmes spécifiques possèdent des éléments de données individuels, mais aucun système ne contient toutes les données. Les services Microsoft 365 collaborent avec Azure AD dans ce modèle de données. Azure AD est le « système de vérité » pour les données partagées, qui est généralement des données petites et statiques utilisées par chaque service. Le modèle fédéré utilisé dans Microsoft 365 et Azure AD fournit la vue partagée des données.

Microsoft 365 utilise à la fois le stockage physique et le stockage cloud Azure. Exchange Online (y compris Exchange Online Protection) et Skype Entreprise utiliser leur propre stockage pour les données client. SharePoint Online utilise à la fois le stockage SQL Server et stockage Azure, d’où la nécessité d’une isolation supplémentaire des données client au niveau du stockage.

## <a name="exchange-online"></a>Exchange Online

Exchange Online stocke les données client dans les boîtes aux lettres. Les boîtes aux lettres sont hébergées dans des bases de données estensible Storage Engine (ESE) appelées bases de données de boîtes aux lettres. Cela inclut les boîtes aux lettres utilisateur, les boîtes aux lettres liées, les boîtes aux lettres partagées et les boîtes aux lettres de dossiers publics. Les boîtes aux lettres utilisateur incluent du contenu Skype Entreprise enregistré, tel que les historiques de conversation.

Le contenu de la boîte aux lettres de l’utilisateur inclut :

- E-mails et pièces jointes
- Calendrier et informations de disponibilité
- Contacts
- Tâches
- Remarques
- Groupes
- Données d’inférence

Chaque base de données de boîte aux lettres dans Exchange Online contient des boîtes aux lettres de plusieurs locataires. Un code d’autorisation sécurise chaque boîte aux lettres, y compris dans une location. Par défaut, seul l’utilisateur affecté a accès à une boîte aux lettres. La liste de contrôle d’accès (ACL) qui sécurise une boîte aux lettres contient une identité authentifiée par Azure AD au niveau du locataire. Les boîtes aux lettres de chaque locataire sont limitées aux identités authentifiées auprès du fournisseur d’authentification du locataire, qui inclut uniquement les utilisateurs de ce locataire. Le contenu du locataire A ne peut en aucune façon être obtenu par les utilisateurs du locataire B, sauf approbation explicite par le locataire A.

## <a name="skype-for-business"></a>Skype Entreprise

Skype Entreprise stocke les données à différents endroits :

- Les informations d’utilisateur et de compte, qui incluent les points de terminaison de connexion, les ID de locataire, les plans de numérotation, les paramètres d’itinérance, l’état de présence, les listes de contacts, etc., sont stockées dans les serveurs Skype Entreprise Active Directory et dans différents serveurs de base de données Skype Entreprise. Les listes de contacts sont stockées dans la boîte aux lettres Exchange Online de l’utilisateur si l’utilisateur est activé pour les deux produits, ou sur Skype Entreprise serveurs si ce n’est pas le cas. Skype Entreprise serveurs de base de données n’est pas partitionné par locataire, mais l’isolation multilocataire des données est appliquée via le contrôle d’accès en fonction du rôle (RBAC).
- Le contenu de la réunion et les données chargées sont stockés sur des partages DFS (Distributed File System). Ce contenu peut également être archivé dans Exchange Online s’il est activé. Les partages DFS ne sont pas partitionnées par locataire. le contenu est sécurisé avec des listes de contrôle d’accès et la mutualisation est appliquée via RBAC.
- Les enregistrements de détails des appels, qui sont l’historique des activités, tels que l’historique des appels, les sessions de messagerie instantanée, le partage d’application, l’historique de messagerie instantanée, etc., peuvent également être stockés dans Exchange Online, mais la plupart des enregistrements de détails des appels sont temporairement stockés sur les serveurs d’enregistrement des détails des appels (CDR). Le contenu n’est pas partitionné par locataire, mais la mutualisation est appliquée via RBAC.

## <a name="sharepoint-online"></a>SharePoint Online

SharePoint Online dispose de plusieurs mécanismes indépendants qui assurent l’isolation des données. Il stocke les objets sous forme de code abstrait dans les bases de données d’application. Par exemple, lorsqu’un utilisateur charge un fichier sur SharePoint Online, le fichier est désassemblé, traduit en code d’application et stocké dans plusieurs tables sur plusieurs bases de données.

Si un utilisateur peut accéder directement au stockage contenant les données, le contenu n’est pas interprétable pour un être humain ou tout autre système que SharePoint Online. Ces mécanismes incluent le contrôle d’accès de sécurité et les propriétés. Toutes les ressources SharePoint Online sont sécurisées par le code d’autorisation et la stratégie RBAC, y compris au sein d’une location. La liste de contrôle d’accès (ACL) qui sécurise une ressource contient une identité authentifiée au niveau du locataire. Les données SharePoint Online pour un locataire sont limitées aux identités authentifiées par le fournisseur d’authentification pour le locataire.

En plus des listes de contrôle d’accès, une propriété de niveau locataire qui spécifie le fournisseur d’authentification (qui est l’Azure AD propre au locataire) est écrite une seule fois et ne peut pas être modifiée une fois définie. Une fois que la propriété de locataire du fournisseur d’authentification a été définie pour un locataire, elle ne peut pas être modifiée à l’aide d’API exposées à un locataire.

Un *SubscriptionId* unique est utilisé pour chaque locataire. Tous les sites clients appartiennent à un locataire et se voient attribuer un *SubscriptionId* unique au locataire. La propriété *SubscriptionId* d’un site est écrite une seule fois et est permanente. Une fois attribué à un locataire, un site ne peut pas être déplacé vers un autre locataire. *SubscriptionId* est la clé utilisée pour créer l’étendue de sécurité pour le fournisseur d’authentification et est lié au locataire.

SharePoint Online utilise SQL Server et Stockage Azure pour le stockage de métadonnées de contenu. La clé de partition du magasin de contenu est *SiteId* dans SQL. Lors de l’exécution d’une requête SQL, SharePoint Online utilise un *ID de site* vérifié dans le cadre d’une vérification *SubscriptionId* au niveau du locataire.

SharePoint Online stocke le contenu de fichier chiffré dans les objets blob Microsoft Azure. Chaque batterie de serveurs SharePoint Online a son propre compte Microsoft Azure et tous les objets blob enregistrés dans Azure sont chiffrés individuellement avec une clé stockée dans le magasin de contenu SQL. Clé de chiffrement protégée dans le code par la couche d’autorisation et non exposée directement à l’utilisateur final. SharePoint Online dispose d’une surveillance en temps réel pour détecter quand une requête HTTP lit ou écrit des données pour plusieurs locataires. *L’ID d’abonnement* de l’identité de la demande est suivi par rapport à *l’SubscriptionId* de la ressource accessible. Les demandes d’accès aux ressources de plusieurs locataires ne doivent jamais se produire par les utilisateurs finaux. Les demandes de service dans un environnement multilocataire sont la seule exception. Par exemple, l’analyseur de recherche extrait les modifications de contenu d’une base de données entière en même temps. Cela implique généralement d’interroger des sites de plusieurs locataires dans une seule demande de service, ce qui est fait pour des raisons d’efficacité.

## <a name="teams"></a>Teams

Vos données Teams sont stockées différemment, en fonction du type de contenu. 

Consultez la [session d’atelier Ignite sur l’architecture De Microsoft Teams](https://channel9.msdn.com/Events/Ignite/Microsoft-Ignite-Orlando-2017/BRK3071) pour une discussion approfondie.

### <a name="core-teams-customer-data"></a>Données client Core Teams

Si votre locataire est approvisionné en Australie, au Canada, dans l’Union européenne, en France, en Allemagne, en Inde, au Japon, en Afrique du Sud, en Corée du Sud, en Suisse (y compris le Liechtenstein), aux Émirats arabes unis, au Royaume-Uni ou au États-Unis, Microsoft stocke les données client suivantes au repos uniquement dans cet emplacement :

- Conversations Teams, conversations d’équipe et de canal, images, messages vocaux et contacts.
- contenu du site SharePoint Online et fichiers stockés dans ce site ;
- Fichiers chargés sur OneDrive pour le travail ou l’école.

#### <a name="chat-channel-messages-team-structure"></a>Conversation, messages de canal, structure d’équipe

Chaque équipe de Teams est soutenue par un groupe Microsoft 365 et son site SharePoint et sa boîte aux lettres Exchange. Les conversations privées (y compris les conversations de groupe), les messages envoyés dans le cadre d’une conversation dans un canal et la structure des équipes et des canaux sont stockés dans un service de conversation s’exécutant dans Azure. Les données sont également stockées dans un dossier masqué dans les boîtes aux lettres d’utilisateur et de groupe pour activer Information Protection fonctionnalités.

#### <a name="voicemail-and-contacts"></a>Messagerie vocale et contacts

Les messages vocaux sont stockés dans Exchange. Les contacts sont stockés dans le magasin de données cloud exchange. Exchange et le magasin cloud Exchange fournissent déjà la résidence des données dans chacune des zones géographiques du centre de données dans le monde entier. Pour toutes les équipes, la messagerie vocale et les contacts sont stockés dans le pays pour l’Australie, le Canada, la France, l’Allemagne, l’Inde, le Japon, les Émirats arabes unis, le Royaume-Uni, l’Afrique du Sud, la Corée du Sud, la Suisse (y compris le Liechtenstein) et le États-Unis. Pour tous les autres pays, les fichiers sont stockés aux États-Unis, en Europe ou Asia-Pacific emplacement en fonction de l’affinité client.

#### <a name="images-and-media"></a>Images et médias

Les médias utilisés dans les conversations (à l’exception des GIF Giphy qui ne sont pas stockés mais qui sont un lien de référence vers l’URL du service Giphy d’origine, Giphy est un service non Microsoft) sont stockés dans un service multimédia Basé sur Azure qui est déployé aux mêmes emplacements que le service de conversation.

#### <a name="files"></a>Fichiers

Les fichiers (y compris OneNote et Wiki) que quelqu’un partage dans un canal sont stockés dans le site SharePoint de l’équipe. Les fichiers partagés dans une conversation privée ou une conversation pendant une réunion ou un appel sont chargés et stockés dans le compte OneDrive professionnel ou scolaire de l’utilisateur qui partage le fichier. Exchange, SharePoint et OneDrive fournissent déjà la résidence des données dans chacune des zones géographiques du centre de données dans le monde entier. Par conséquent, pour les clients existants, tous les fichiers, blocs-notes OneNote, contenu wiki Teams et boîtes aux lettres qui font partie de l’expérience Teams sont déjà stockés dans l’emplacement en fonction de l’affinité de votre locataire. Les fichiers sont stockés dans le pays pour l’Australie, le Canada, la France, l’Allemagne, l’Inde, le Japon, les Émirats arabes unis, le Royaume-Uni, l’Afrique du Sud, la Corée du Sud et la Suisse (y compris le Liechtenstein). Pour tous les autres pays, les fichiers sont stockés aux États-Unis, en Europe ou en Asie-Pacifique en fonction de l’affinité de locataire.
