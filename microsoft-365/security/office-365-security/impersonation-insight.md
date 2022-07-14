---
title: Perspicacité de l'usurpation d'identité
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: ''
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent découvrir le fonctionnement de l’insight d’emprunt d’identité. Ils peuvent rapidement déterminer les expéditeurs qui envoient légitimement des e-mails dans leur organisation à partir de domaines qui ne passent pas de vérifications d’authentification par e-mail (SPF, DKIM ou DMARC).
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: c54bdbb4ee8c3bf068b40df8cd5ca0a58da2392f
ms.sourcegitcommit: 221212fff9737e0ea386755deb8fed62ae9c254b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/14/2022
ms.locfileid: "66787739"
---
# <a name="impersonation-insight-in-defender-for-office-365"></a>Insight sur l’emprunt d’identité dans Defender pour Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

L’emprunt d’identité est l’endroit où l’expéditeur d’un message électronique ressemble beaucoup à une adresse e-mail réelle ou attendue de l’expéditeur. Les attaquants empruntent souvent l’identité des adresses e-mail de l’expéditeur dans le hameçonnage ou d’autres types d’attaques afin d’obtenir la confiance du destinataire. Il existe essentiellement deux types d’emprunt d’identité :

- **Emprunt d’identité de domaine** : au lieu de lila@contoso.com, l’adresse e-mail de l’expéditeur emprunté est lila@ćóntoso.com.
- **Emprunt d’identité de l’utilisateur** : au lieu de michelle@contoso.com, l’adresse e-mail de l’expéditeur emprunté est rnichell@contoso.com.

L’emprunt d’identité de domaine diffère de [l’usurpation d’identité de domaine](anti-spoofing-protection.md), car le domaine emprunté est généralement un domaine réel inscrit. Les messages des expéditeurs du domaine emprunté peuvent et font souvent passer des vérifications d’authentification par e-mail régulières qui identifieraient autrement les tentatives d’usurpation d’identité (SPF, DKIM et DMARC).

La protection contre l’emprunt d’identité fait partie des paramètres de stratégie anti-hameçonnage qui sont exclusifs à Microsoft Defender pour Office 365. Pour plus d’informations sur ces paramètres, consultez [Les paramètres d’emprunt d’identité dans les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365).

Vous pouvez utiliser l’insight d’emprunt d’identité dans le portail Microsoft 365 Defender pour identifier rapidement les messages provenant d’expéditeurs ou de domaines d’expéditeur empruntés que vous avez configurés pour la protection de l’emprunt d’identité.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Portail Microsoft 365 Defender sur <https://security.microsoft.com>. Pour accéder directement à la page **Anti-hameçonnage** , utilisez <https://security.microsoft.com/antiphishing>. Pour accéder directement à la page **Informations sur l’emprunt d’identité** , utilisez <https://security.microsoft.com/impersonationinsight>.

- Vous devez disposer d’autorisations dans le portail Microsoft 365 Defender avant de pouvoir effectuer les procédures décrites dans cet article :
  - **Gestion de l'organisation**
  - **Administrateur de sécurité**
  - **Lecteur de sécurité**
  - **Lecteur général**

  Pour plus d’informations, consultez [Autorisations dans le portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md).

  **Remarque** : l’ajout d’utilisateurs au rôle Azure Active Directory correspondant dans le Centre d'administration Microsoft 365 donne aux utilisateurs les autorisations requises dans le portail Microsoft 365 Defender _et_ les autorisations pour d’autres fonctionnalités dans Microsoft 365. Pour plus d’informations, consultez la rubrique [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).

- Vous activez et configurez la protection contre l’emprunt d’identité dans les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365. La protection contre l’emprunt d’identité n’est pas activée par défaut. Pour plus d’informations, consultez [Paramètres exclusifs des stratégies anti-hameçonnage dans Microsoft Defender pour Office 365](configure-mdo-anti-phishing-policies.md).

## <a name="open-the-impersonation-insight-in-the-microsoft-365-defender-portal"></a>Ouvrez l’insight d’emprunt d’identité dans le portail Microsoft 365 Defender

1. Dans le portail Microsoft 365 Defender, accédez à <https://security.microsoft.com>Email & Stratégies de **collaboration** \> & stratégies de **menace** \> **de règles** \> **anti-hameçonnage** dans la section **Stratégies**. Pour accéder directement à la page **Anti-hameçonnage** , utilisez <https://security.microsoft.com/antiphishing>.

2. Dans la page **Anti-hameçonnage** , l’insight d’emprunt d’identité se présente comme suit :

   :::image type="content" source="../../media/m365-sc-impersonation-insight.png" alt-text="Informations sur l’emprunt d’identité dans la page de stratégie anti-hameçonnage dans le portail Microsoft 365 Defender." lightbox="../../media/m365-sc-impersonation-insight.png":::

   L’insight a deux modes :

    - **Mode d’insight** : si la protection contre l’emprunt d’identité est activée et configurée dans toutes les stratégies anti-hameçonnage, l’insight affiche le nombre de messages détectés provenant de domaines empruntés et d’utilisateurs emprunts d’identité (expéditeurs) au cours des sept derniers jours. Il s’agit du total de tous les expéditeurs usurpés d’identité détectés à partir de toutes les stratégies anti-hameçonnage.
    - **Que se passe-t-il en mode** : si la protection contre l’emprunt d’identité n’est pas activée et configurée dans des stratégies anti-hameçonnage actives, l’insight vous indique le nombre *de messages* détectés par nos fonctionnalités de protection de l’emprunt d’identité au cours des sept derniers jours.

Pour afficher des informations sur les détections d’emprunt d’identité, cliquez sur **Afficher les emprunts d’identité** dans l’insight d’emprunt d’identité.

## <a name="view-information-about-messages-from-senders-in-impersonated-domains"></a>Afficher des informations sur les messages des expéditeurs dans des domaines empruntés

Dans la page Informations sur l’emprunt **d’identité** qui s’affiche après avoir cliqué sur **Afficher les emprunts d’identité** dans l’insight d’emprunt d’identité, vérifiez que l’onglet **Domaines** est sélectionné. L’onglet Domaines contient les informations **suivantes** :

- **Domaine de l’expéditeur** : domaine d’emprunt d’identité, qui est le domaine utilisé pour envoyer le message électronique.
- **Nombre** de messages : nombre de messages provenant de l’emprunt d’identité du domaine de l’expéditeur au cours des 7 derniers jours.
- **Type d’emprunt d’identité** : cette valeur indique l’emplacement détecté de l’emprunt d’identité (par exemple, **Domaine dans l’adresse**).
- **Domaines empruntés** : domaine emprunté, qui doit ressembler étroitement au domaine configuré pour la protection de l’emprunt d’identité dans la stratégie anti-hameçonnage.
- **Type de domaine** : cette valeur est **domaine d’entreprise** pour les domaines internes ou **domaine personnalisé** pour les domaines personnalisés.
- **Stratégie** : stratégie anti-hameçonnage qui a détecté le domaine emprunté.
- **Autorisé à emprunter l’identité** : l’une des valeurs suivantes :
  - **Oui** : le domaine a été configuré en tant que domaine approuvé (exception pour la protection contre l’emprunt d’identité) dans la stratégie anti-hameçonnage. Les messages des expéditeurs du domaine emprunté ont été détectés, mais autorisés.
  - **Non** : le domaine a été configuré pour la protection contre l’emprunt d’identité dans la stratégie anti-hameçonnage. Des messages provenant d’expéditeurs du domaine emprunté ont été détectés et traités en fonction de l’action pour les domaines empruntés dans la stratégie anti-hameçonnage.

Vous pouvez cliquer sur les en-têtes de colonne sélectionnés pour trier les résultats.

Pour filtrer les résultats, vous pouvez utiliser l’icône ![Rechercher.](../../media/m365-cc-sc-search-icon.png) **Zone de recherche** pour entrer une liste de valeurs séparées par des virgules pour filtrer les résultats.

### <a name="view-details-about-messages-from-senders-in-impersonated-domains"></a>Afficher les détails sur les messages des expéditeurs dans des domaines empruntés

Sous l’onglet **Domaines** de la page Informations sur **l’emprunt d’identité** , sélectionnez l’une des détections d’emprunt d’identité disponibles. Le menu volant des détails qui s’affiche contient les informations et fonctionnalités suivantes :

- **Stratégie d’emprunt d’identité de sélection à modifier** : sélectionnez la stratégie anti-hameçonnage affectée que vous souhaitez modifier. Seules les stratégies où le domaine emprunté est défini dans la stratégie sont disponibles. Reportez-vous à la page précédente pour voir quelle stratégie était réellement responsable de la détection du domaine emprunté (probablement en fonction du destinataire et de la priorité de la stratégie).
- **Ajouter à la liste d’emprunt d’identité autorisée** : utilisez ce bouton bascule pour ajouter ou supprimer l’expéditeur des **domaines et des expéditeurs approuvés** (exceptions d’emprunt d’identité) pour la stratégie anti-hameçonnage que vous avez sélectionnée :
  - Si la valeur **Autorisée à emprunter l’identité** de cette entrée était **Non**, la bascule est désactivée. Pour exempter tous les expéditeurs de ce domaine de l’évaluation par la protection d’emprunt d’identité, faites glisser le bouton bascule sur : ![Activer.](../../media/scc-toggle-on.png). Le domaine est ajouté à la liste **des domaines approuvés dans les paramètres** de protection d’emprunt d’identité de la stratégie anti-hameçonnage.
  - Si la valeur **Autorisée à emprunter l’identité** de cette entrée était **Oui**, le bouton bascule est activé. Pour renvoyer tous les expéditeurs de ce domaine à l’évaluation par la protection d’emprunt d’identité, faites glisser le bouton bascule vers désactivé : ![Désactiver.](../../media/scc-toggle-off.png) Le domaine est supprimé de la liste **des domaines approuvés dans les paramètres** de protection d’emprunt d’identité de la stratégie anti-hameçonnage.
- Pourquoi on a pris ça.
- Ce que vous devez faire.
- Récapitulatif de domaine qui répertorie le domaine emprunté.
- Données WhoIs sur l’expéditeur.
- Lien permettant d’ouvrir [l’Explorateur de menaces](threat-explorer.md) pour afficher des détails supplémentaires sur l’expéditeur.
- Messages similaires du même expéditeur qui ont été remis à votre organisation.

## <a name="view-information-about-messages-from-impersonated-senders"></a>Afficher des informations sur les messages provenant d’expéditeurs usurpés d’identité

Dans la page Informations sur l’emprunt **d’identité** qui s’affiche après avoir cliqué sur **Afficher les emprunts** d’identité dans l’insight d’emprunt d’identité, cliquez sur l’onglet **Utilisateurs** . **L’onglet Utilisateurs** contient les informations suivantes :

- **Expéditeur** : adresse e-mail de l’expéditeur emprunt d’identité qui a envoyé le message électronique.
- **Nombre** de messages : nombre de messages de l’expéditeur emprunt d’identité au cours des 7 derniers jours.
- **Type d’emprunt d’identité** : cette valeur est **l’utilisateur dans le nom d’affichage**.
- **Utilisateurs usurpés** d’identité : adresse e-mail de l’expéditeur emprunt d’identité, qui doit ressembler étroitement à l’utilisateur configuré pour la protection de l’emprunt d’identité dans la stratégie anti-hameçonnage.
- **Type d’utilisateur** : cette valeur affiche le type de protection appliqué (par exemple, **Utilisateur protégé** ou **Intelligence de boîte aux lettres**).
- **Stratégie** : stratégie anti-hameçonnage qui a détecté l’expéditeur emprunt d’identité.
- **Autorisé à emprunter l’identité** : l’une des valeurs suivantes :
  - **Oui** : l’expéditeur a été configuré en tant qu’utilisateur approuvé (exception pour la protection contre l’emprunt d’identité) dans la stratégie anti-hameçonnage. Les messages de l’expéditeur emprunt d’identité ont été détectés, mais autorisés.
  - **Non** : l’expéditeur a été configuré pour la protection contre l’emprunt d’identité dans la stratégie anti-hameçonnage. Les messages de l’expéditeur emprunt d’identité ont été détectés et ont agi en fonction de l’action pour les utilisateurs emprunts d’identité dans la stratégie anti-hameçonnage.

Vous pouvez cliquer sur les en-têtes de colonne sélectionnés pour trier les résultats.

Pour filtrer les résultats, vous pouvez utiliser la zone **d’expéditeur de** filtre pour entrer une liste de valeurs séparées par des virgules pour filtrer les résultats.

### <a name="view-details-about-messages-from-impersonated-senders"></a>Afficher les détails sur les messages provenant d’expéditeurs usurpés d’identité

Sous l’onglet **Utilisateurs** de la page **Informations sur l’emprunt d’identité** , sélectionnez l’une des détections d’emprunt d’identité disponibles. Le menu volant des détails qui s’affiche contient les informations et fonctionnalités suivantes :

- **Stratégie d’emprunt d’identité de sélection à modifier** : sélectionnez la stratégie anti-hameçonnage affectée que vous souhaitez modifier. Seules les stratégies où l’expéditeur emprunté est défini dans la stratégie sont disponibles. Reportez-vous à la page précédente pour voir quelle stratégie était réellement responsable de la détection de l’expéditeur emprunté (probablement en fonction du destinataire et de la priorité de la stratégie).
- **Ajouter à la liste d’emprunt d’identité autorisée** : utilisez ce bouton bascule pour ajouter ou supprimer l’expéditeur des **domaines et des expéditeurs approuvés** (exceptions d’emprunt d’identité) pour la stratégie anti-hameçonnage que vous avez sélectionnée :
  - Si la valeur **Autorisée à emprunter l’identité** de cette entrée était **Non**, la bascule est désactivée. Pour exempter l’expéditeur de l’évaluation par la protection d’emprunt d’identité, faites glisser le bouton bascule sur : ![Activer.](../../media/scc-toggle-on.png). L’expéditeur est ajouté à la liste **des utilisateurs approuvés** dans les paramètres de protection d’emprunt d’identité de la stratégie anti-hameçonnage.
  - Si la valeur **Autorisée à emprunter l’identité** de cette entrée était **Oui**, le bouton bascule est activé. Pour renvoyer l’expéditeur à l’évaluation par la protection d’emprunt d’identité, faites glisser le bouton bascule vers la désactivation : ![Désactiver.](../../media/scc-toggle-off.png) L’expéditeur est supprimé de la liste **des utilisateurs approuvés** dans les paramètres de protection d’emprunt d’identité de la stratégie anti-hameçonnage.
- Pourquoi on a pris ça.
- Ce que vous devez faire.
- Récapitulatif de l’expéditeur qui répertorie l’expéditeur emprunt d’identité.
- Données WhoIs sur l’expéditeur.
- Lien permettant d’ouvrir [l’Explorateur de menaces](threat-explorer.md) pour afficher des détails supplémentaires sur l’expéditeur.
- Messages similaires du même expéditeur qui ont été remis à votre organisation.
