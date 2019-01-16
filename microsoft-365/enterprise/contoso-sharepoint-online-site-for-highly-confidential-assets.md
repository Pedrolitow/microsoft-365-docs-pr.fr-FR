---
title: Site SharePoint Online pour les biens numériques hautement confidentielles de la société Contoso
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/01/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
description: 'Résumé : Comment Contoso implémenté un site SharePoint Online pour hautement régulées données pour faciliter la collaboration entre ses recherches équipes.'
ms.openlocfilehash: 697ddb27b56fd529e9c73b89d9f07b8731ad76c3
ms.sourcegitcommit: e491c4713115610cbe13d2fbd0d65e1a41c34d62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "26867430"
---
# <a name="sharepoint-online-site-for-highly-confidential-digital-assets-of-the-contoso-corporation"></a>Site SharePoint Online pour les biens numériques hautement confidentielles de la société Contoso

 **Résumé :** Comment Contoso implémenté un site SharePoint Online pour les données hautement régulés pour faciliter la collaboration entre des équipes de recherche.
  
Actifs les plus importants de Contoso sont la propriété intellectuelle sous la forme de secrets commerciaux, tels que des techniques de fabrication propriétaires et les spécifications pour les produits qui se trouvent dans le développement de conception. Ces ressources sont au format numérique, à l’origine stockée en tant que fichiers sur un site SharePoint Server 2016. Lorsque Contoso déployé Microsoft 365 pour entreprises, qu’ils veulent effectuer la transition entre les équipes de recherche dans Paris, Moscou, New York, Pékin et Bangalore leurs ressources numériques locaux vers le nuage pour faciliter l’accès et de collaboration plus ouverte. 
  
Toutefois, en raison de leur nature confidentielle, accès à ces fichiers doit être :

- Limitée à l’ensemble des personnes qui sont autorisés à afficher ou modifier les, avec des autorisations en cours pour le site gérée uniquement par les administrateurs SharePoint. 
- Protégé avec Data Loss Prevention (DLP) pour empêcher les utilisateurs de les distribuer en dehors du site.
- Pour empêcher les utilisateurs non autorisés d’accéder à leur contenu, même s’ils sont en dehors du site, les listes de contrôle d’accès chiffré et protégé avec.

Sécurité et SharePoint des administrateurs de Contoso de l’informatique a décidé d’utiliser un [site SharePoint Online pour régulé hautement des données](teams-sharepoint-online-sites-highly-regulated-data.md).
  
Contoso a utilisé ces étapes pour créer et sécuriser un sites d’équipe SharePoint Online pour leurs équipes de recherche.

## <a name="step-1-reviewed-and-verified-the-members-of-research-team-groups"></a>Étape 1 : Révisé et vérifié les membres des groupes de l’équipe de recherche

Les administrateurs informatiques de Contoso effectuée un examen de l’ensemble des groupes de sécurité pour leurs équipes de recherche. Supprimés, toute personne qui n’a pas un enquêteur ou n’était pas nécessaire de l’accès aux ressources de recherche. 

Ils également et créé ces nouveaux groupes de sécurité :

- **Administrateurs de la recherche**  L’ensemble du groupe Administrateurs SharePoint qui ont un contrôle total sur le site, notamment la possibilité de modifier les autorisations.
- **Membres de la recherche**  L’ensemble des groupes de sécurité pour les équipes de recherche dans le monde entier.
- **Visionneuses de la recherche**  L’ensemble de la gestion des utilisateurs, telles que les dirigeants de l’entreprise de recherche, qui peut afficher les biens sur le site.

## <a name="step-2-created-an-isolated-sharepoint-online-team-site"></a>Étape 2 : Création d’un site d’équipe SharePoint Online isolé 

Les administrateurs Contoso SharePoint tout d’abord créés un nouveau site d’équipe nommé **recherche**. Ils configurés, puis :

- Le niveau d’autorisation contrôle total à utiliser le groupe SharePoint propriétaires de recherche, qui est le groupe de sécurité **Administrateurs de la recherche** en tant que membre
- Le niveau d’autorisation Modifier pour utiliser le groupe SharePoint des membres de recherche, dont le groupe de sécurité **Membres de recherche** en tant que membre
- Le niveau d’autorisation en lecture à utiliser le groupe SharePoint visiteurs de recherche, qui est le groupe de sécurité des **Visionneuses de la recherche** en tant que membre

Voici les niveaux d’autorisation SharePoint qui en résulte, les groupes SharePoint et leurs membres.

![](./media/contoso-sharepoint-online-site-for-highly-confidential-assets/spo-permissions.png)

Ensuite, ils configuré des restrictions supplémentaires pour le site.

Pour les détails de configuration, voir [déploiement d’un site d’équipe SharePoint Online isolé](https://docs.microsoft.com/office365/enterprise/deploy-an-isolated-sharepoint-online-team-site).

## <a name="step-3-configured-the-site-for-a-restrictive-office-365-label-dlp-policy"></a>Étape 3 : Configurer le site d’une étiquette d’Office 365 restrictif stratégie DLP

Tout d’abord, les administrateurs Contoso appliqué l’étiquette de Office 365 **Hautement confidentielles** sur le site de **recherche** .

Ensuite, ils créé une nouvelle stratégie Office 365 DLP nommé **recherche** qui :

- Utilise l’étiquette d’Office 365 **Hautement confidentielles** . 
- Est appliquée au site de **recherche** .
- Empêche les utilisateurs de partager des documents.

Pour les détails de configuration, voir [fichiers protéger SharePoint Online avec Office 365 étiquettes et DLP](https://docs.microsoft.com/office365/enterprise/protect-sharepoint-online-files-with-office-365-labels-and-dlp).

## <a name="step-4-created-an-azure-information-protection-sub-label-for-the-site"></a>Étape 4 : Créé une étiquette sous-sites Azure la Protection des informations pour le site

Les administrateurs Contoso créés une nouvelle étiquette de sous-sites Azure Information Protection nommé **recherche** de l’étiquette **Hautement confidentielles** par défaut d’une stratégie sur lesquelles porte qui :

- Nécessite un chiffrement.
- Autorise l’accès complet par les membres du groupe de sécurité **Membres de la recherche** .
- Permet un accès en lecture par les membres du groupe de sécurité **Des visionneuses de recherche** .

Ensuite, ils déploiement le client Azure la Protection des informations sur les périphériques de membres de l’équipe.

Pour les détails de configuration, voir [fichiers protéger SharePoint Online avec Azure la Protection des informations](https://docs.microsoft.com/office365/enterprise/protect-sharepoint-online-files-with-azure-information-protection). 

Voici la configuration du site de **recherche** pour les biens hautement confidentielles qui en résulte.

![](./media/contoso-sharepoint-online-site-for-highly-confidential-assets/final-config.png)

## <a name="step-5-migrated-the-on-premises-sharepoint-research-data"></a>Étape 5 : Migrer les données de recherche SharePoint local

Les administrateurs de Contoso déplacement que tous les locaux de recherche les fichiers dans le site de SharePoint Server 2016 locale aux dossiers dans le nouveau site SharePoint Online **Research** .

## <a name="step-6-trained-their-users"></a>Étape 6 : Former les utilisateurs 

Le personnel de sécurité Contoso formé les équipes de recherche dans un cours obligatoire qui les pas à pas :

- Comment accéder à nouveau site SharePoint Online **Research** et ses fichiers existants.
- Création de nouveaux fichiers sur le site et chargement de nouveaux fichiers stockés localement.
- Une démonstration de la stratégie DLP empêche les fichiers partagés en externe.
- Découvrez comment utiliser le client de la Protection des informations Azure pour étiqueter les fichiers de recherche avec l’étiquette d’une **recherche** .
- Une démonstration de l’étiquette de sous-sites de **recherche** protège un fichier même si elle est une fuite d’à partir du site.

Le résultat final est un environnement sécurisé dans lequel les chercheurs peuvent collaborer au sein de l’organisation dans un environnement sécurisé. 

Si un document de recherche avec l’étiquette de sous-sites de **recherche** est perdue à partir du site de **recherche** , il est chiffré et accessibles uniquement aux membres des groupes de sécurité **Membres de recherche** et les **Visionneuses de recherche** avec les informations d’identification valides.

## <a name="next-step"></a>Étape suivante

[Déployez](deploy-microsoft-365-enterprise.md) Microsoft 365 Entreprise dans votre organisation.

