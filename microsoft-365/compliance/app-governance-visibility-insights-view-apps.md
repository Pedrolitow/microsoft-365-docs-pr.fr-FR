---
title: Afficher vos applications
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.collection: m365-security-compliance
localization_priority: Priority
search.appverid:
- MOE150
- MET150
description: Affichez vos applications.
ms.openlocfilehash: 8e9ac5fda62e015bc1e2a5df11b618afa508a4a4
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58574411"
---
# <a name="view-your-apps"></a>Afficher vos applications

>*[Guide de sécurité et conformité pour les licences Microsoft 365](https://aka.ms/ComplianceSD).*

La gouvernance des applications Microsoft vous permet d’obtenir rapidement des insights approfondis sur les applications Microsoft 365 dans votre client. Par exemple, vous pouvez voir :

- Une liste des applications compatibles OAuth dans le client qui utilisent l’API Microsoft Graph, ainsi que les métadonnées d’application et les données d’utilisation pertinentes.
- Détails de l’application avec des informations et des insights plus approfondis en sélectionnant une application dans la liste.

## <a name="getting-a-list-of-all-the-apps-in-your-tenant"></a>Obtention d’une liste de toutes les applications de votre client

Pour obtenir un résumé des applications de votre client, accédez à **Centre de conformité Microsoft 365 > Gouvernance des applications > Applications**.

![Page récapitulative de l’application MAPG dans le Centre de conformité Microsoft 365.](..\media\manage-app-protection-governance\mapg-cc-apps.png)

>[!Note]
> Votre compte de connexion doit avoir l’un des [ces rôles](app-governance-get-started.md#administrator-roles) pour afficher les données de gouvernance des applications.
>

Vous verrez une liste d’applications et cette information :

- Nom de l'application
- Éditeur
- Certification M365

  Indique si l’application est compatible avec les technologies Microsoft, conforme aux meilleures pratiques de sécurité des applications cloud et prise en charge par Microsoft.

- Dernière modification

  Indique la date à laquelle la gouvernance de l’application a été installée dans le client si cette date est plus récente que la date à laquelle l’application a été modifiée pour la dernière fois.

- Date d’installation
- Niveau de privilège
- Nombre d’utilisateurs
- Accès aux données

  Somme du chargement et du téléchargement des données de l’application dans le client au cours du dernier jour, ainsi que la modification apportée le jour précédent.

La gouvernance des applications trie la liste des applications par **Nom d’application** par défaut. Pour trier la liste en fonction d’un autre attribut d’application, sélectionnez le nom de l’attribut.

Vous pouvez également sélectionner **Recherche** pour rechercher une application par nom.

## <a name="getting-detailed-information-on-an-app"></a>Obtention d’informations détaillées sur une application

Pour plus d’informations sur une application spécifique dans votre client, accédez à **Centre de conformité Microsoft 365 > Gouvernance des applications > Page Applications > *nom de l’application***.

![Volet des détails de l’application de gouvernance des applications dans le Centre de conformité Microsoft 365](..\media\manage-app-protection-governance\mapg-cc-apps-app.png)

Le volet détails de l’application fournit des informations supplémentaires sur ces onglets :

| Nom de l’onglet | Description |
|:-------|:-----|
| Détails | Consultez des données supplémentaires sur l’application, telles que la date du premier consentement et l’ID d’application. Pour afficher les propriétés de l’application telles qu’inscrites dans Azure AD, sélectionnez **Afficher l’application dans Azure AD**. |
| Utilisation |Consultez les données auxquelles l’application accède dans le client et tracez l’utilisation des données pour les ressources SharePoint et Exchange. |
| Utilisateurs | Consultez la liste des utilisateurs qui utilisent l’application, s’il s’agit d’un compte prioritaire et la quantité de données téléchargées et chargées. |
| Autorisations | Consultez un résumé des autorisations accordées et utilisées par l’application, ainsi que la liste des autorisations spécifiques. Pour plus d’informations, consultez la [référence des autorisations Microsoft Graph](/graph/permissions-reference). |
|||

Pour une application activée, il existe également un contrôle **Désactiver l’application** pour désactiver l’utilisation de l’application sélectionnée et un contrôle **Activer l’application** pour activer l’utilisation de l’application désactivée. Ces actions nécessitent ces rôles d’administrateur :

- Administrateur de conformité
- Administrateur général
- Administrateur de sécurité
- Opérateur de sécurité

## <a name="next-step"></a>Étape suivante

[Déterminez la posture de conformité globale de votre application](app-governance-visibility-insights-compliance-posture.md).
