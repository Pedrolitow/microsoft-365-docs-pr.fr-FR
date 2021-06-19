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
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: ''
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent découvrir le fonctionnement de l’aperçu de l’emprunt d’identité. Ils peuvent rapidement déterminer les expéditeurs qui envoient légitimement des messages électroniques à leurs organisations à partir de domaines qui ne passent pas les vérifications d’authentification du courrier électronique (SPF, DKIM ou DMARC).
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 53baecd100851eb5ab05fe79751961baef3acd5c
ms.sourcegitcommit: c70067b4ef9c6f8f04aca68c35bb5141857c4e4b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "53029668"
---
# <a name="impersonation-insight-in-defender-for-office-365"></a>Aperçu de l’emprunt d’identité dans Defender pour Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!NOTE]
> Les fonctionnalités décrites dans cet article sont en prévisualisation, peuvent faire l’objet de changements et ne sont pas disponibles dans toutes les organisations.

L’emprunt d’identité est l’endroit où l’expéditeur d’un message électronique ressemble beaucoup à une adresse de messagerie d’expéditeur réelle ou attendue. Les personnes malveillantes utilisent souvent l’identité des adresses e-mail des expéditeurs par hameçonnage ou d’autres types d’attaques pour gagner la confiance du destinataire. Il existe fondamentalement deux types d’emprunt d’identité :

- **Emprunt d’identité** de domaine : au lieu de lila@contoso.com, l’adresse e-mail de l’expéditeur dont l’identité a été usurpée est lila@ćóntoso.com.
- **Emprunt d’identité** d’utilisateur : au lieu michelle@contoso.com, l’adresse e-mail de l’expéditeur dont l’identité est usurpée est rnichell@contoso.com.

L’emprunt d’identité de domaine est différent de l’usurpation d’identité de [domaine,](anti-spoofing-protection.md)car le domaine usurpé d’identité est généralement un domaine réel enregistré. Les messages provenant d’expéditeurs dans le domaine dont l’identité est emprunt d’identité peuvent et souvent passer des vérifications d’authentification de courrier électronique régulières qui identifieraient autrement les tentatives d’usurpation d’identité (SPF, DKIM et DMARC).

La protection contre l’emprunt d’identité fait partie des paramètres de stratégie anti-hameçonnage qui sont exclusifs à Microsoft Defender Office 365. Pour plus d’informations sur ces paramètres, voir paramètres d’emprunt d’identité dans les [stratégies anti-hameçonnage](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)dans Microsoft Defender pour Office 365 .

Vous pouvez utiliser l’aperçu de l’emprunt d’identité dans le portail Microsoft 365 Defender pour identifier rapidement les messages provenant d’expéditeurs ou de domaines d’expéditeurs usurpés que vous avez configurés pour la protection contre l’emprunt d’identité.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Portail Microsoft 365 Defender sur <https://security.microsoft.com>. Pour aller directement à l’aperçu de l’emprunt d’identité sur la page **Anti-hameçonnage,** utilisez <https://security.microsoft.com/antiphishing> . Pour aller directement à la page d’informations **sur l’emprunt d’identité,** utilisez <https://security.microsoft.com/impersonationinsight> .

- Des autorisations doivent vous être attribuées dans le portail Microsoft 365 Defender avant de pouvoir suivre les procédures de cet article :
  - **Gestion de l'organisation**
  - **Administrateur de sécurité**
  - **Lecteur sécurité**
  - **Lecteur global**

  Pour plus d’informations, [voir Autorisations dans le portail Microsoft 365 Defender.](permissions-in-the-security-and-compliance-center.md)

  **Remarque**: l’ajout d’utilisateurs au rôle Azure Active Directory correspondant dans le Centre d’administration Microsoft 365 donne aux  utilisateurs les autorisations requises dans le portail Microsoft 365 Defender et les autorisations pour d’autres fonctionnalités dans Microsoft 365. Pour plus d’informations, consultez [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).

- Vous activez et configurez la protection contre l’emprunt d’identité dans les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365. La protection contre l’emprunt d’identité n’est pas activée par défaut. Pour plus d’informations, voir [Configurer des stratégies anti-hameçonnage dans Microsoft Defender pour Office 365](configure-mdo-anti-phishing-policies.md).

## <a name="open-the-impersonation-insight-in-the-microsoft-365-defender-portal"></a>Ouvrez l’aperçu de l’emprunt d’identité dans Microsoft 365 Defender web

1. Dans le portail Microsoft 365 Defender, go to **Email & Collaboration** Policies & \> **Rules** Threat \>  \> **policies** section \> **Anti-phishing**.

2. Dans la page **Anti-hameçonnage,** l’aperçu de l’emprunt d’identité ressemble à ceci :

   ![Informations sur l’usurpation d’identité et la veille contre l’usurpation d’identité sur la page stratégie anti-hameçonnage](../../media/m365-sc-impersonation-and-spoof-intelligence-insight.png)

   L’aperçu a deux modes :

    - **Mode** Insight : si la protection contre l’emprunt d’identité est activée et configurée dans les stratégies anti-hameçonnage, l’aperçu affiche le nombre de messages détectés provenant de domaines dont l’identité a été usurpée et d’utilisateurs (expéditeurs) au cours des sept derniers jours. Il s’agit du total de tous les expéditeurs dont l’identité a été détectée dans toutes les stratégies anti-hameçonnage.
    - Que se passe-t-il si le **mode**: si la protection contre l’emprunt d’identité n’est pas activée et configurée dans les stratégies anti-hameçonnage actives, l’information vous indique le nombre de *messages* détectés par nos fonctionnalités de protection contre l’emprunt d’identité au cours des sept derniers jours.

Pour afficher des informations sur les détections d’emprunt d’identité, cliquez sur Afficher les **emprunts** d’identité dans l’aperçu de l’emprunt d’identité.

   > [!NOTE]
   > Pour plus d’informations sur les informations sur l’usurpation d’informations sur l’intelligence, voir [Spoof intelligence insight in EOP](learn-about-spoof-intelligence.md).

## <a name="view-information-about-messages-from-senders-in-impersonated-domains"></a>Afficher des informations sur les messages provenant d’expéditeurs dans des domaines dont l’identité est usurpée

Dans **la** page Informations sur l’emprunt d’identité qui s’affiche après avoir  cliqué sur Afficher les **emprunts** d’identité dans l’aperçu d’emprunt d’identité, vérifiez que l’onglet Domaines est sélectionné. **L’onglet Domaines** contient les informations suivantes :

- **Domaine de l’expéditeur**: domaine d’emprunt d’identité, qui est le domaine utilisé pour envoyer le message électronique.
- **Nombre de** messages : nombre de messages provenant de l’emprunt d’identité du domaine de l’expéditeur au cours des 7 derniers jours.
- **Type d’emprunt** d’identité : cette valeur indique l’emplacement détecté de l’emprunt d’identité (par exemple, **Domaine dans l’adresse).**
- **Domaine dont** l’identité est usurpée : le domaine dont l’identité doit ressembler étroitement au domaine configuré pour la protection contre l’emprunt d’identité dans la stratégie anti-hameçonnage.
- **Type de domaine**: cette valeur est **le domaine de la** société pour les domaines internes ou le domaine **personnalisé** pour les domaines personnalisés.
- **Stratégie**: stratégie anti-hameçonnage qui a détecté le domaine dont l’identité a été usurpée.
- **Autorisé à usurper l’identité**: l’une des valeurs suivantes :
  - **Oui**: le domaine a été configuré en tant que domaine approuvé (une exception pour la protection contre l’emprunt d’identité) dans la stratégie anti-hameçonnage. Les messages provenant d’expéditeurs dans le domaine dont l’identité a été usurpée ont été détectés, mais autorisés.
  - **Non**: le domaine a été configuré pour la protection contre l’emprunt d’identité dans la stratégie anti-hameçonnage. Les messages provenant d’expéditeurs du domaine dont l’identité a été usurpée ont été détectés et agissent en fonction de l’action pour les domaines dont l’identité est usurpée dans la stratégie anti-hameçonnage.

Vous pouvez cliquer sur les en-tête de colonne sélectionnés pour trier les résultats.

Pour filtrer les résultats, vous pouvez utiliser la zone De recherche icône de recherche pour entrer une liste de valeurs séparées par des virgules ![ ](../../media/m365-cc-sc-search-icon.png)  pour filtrer les résultats.

### <a name="view-details-about-messages-from-senders-in-impersonated-domains"></a>Afficher des détails sur les messages provenant d’expéditeurs dans des domaines dont l’identité est usurpée

Sous **l’onglet Domaines** de **la** page Informations sur l’emprunt d’identité, sélectionnez l’une des détections d’emprunt d’identité disponibles. Le volant de détails qui s’affiche contient les informations et fonctionnalités suivantes :

- **Stratégie d’emprunt d’identité** de sélection à modifier : sélectionnez la stratégie anti-hameçonnage concernée que vous souhaitez modifier. Seules les stratégies où le domaine dont l’identité est définie dans la stratégie sont disponibles. Reportez-vous à la page précédente pour voir quelle stratégie était réellement responsable de la détection du domaine dont l’identité a été usurpée (probablement en fonction du destinataire et de la priorité de la stratégie).
- Ajoutez à la liste des expéditeurs autorisés à usurper l’identité : utilisez ce basculement pour ajouter ou supprimer l’expéditeur des domaines et des expéditeurs de confiance **(exceptions** d’emprunt d’identité) pour la stratégie anti-hameçonnage que vous avez sélectionnée :
  - Si la **valeur Autorisée à usurper l’identité** de cette entrée est **Non,** le basculement est éteint. Pour exempter tous les expéditeurs de ce domaine de l’évaluation par la protection contre l’emprunt d’identité, faites glisser le curseur sur : ![ Basculez sur ](../../media/scc-toggle-on.png) . Le domaine est ajouté à la liste des domaines de confiance dans les **paramètres** de protection contre l’emprunt d’identité de la stratégie anti-hameçonnage.
  - Si la **valeur Autorisée à usurper l’identité** de cette entrée est **Oui,** le basculement est sur. Pour renvoyer tous les expéditeurs de ce domaine à l’évaluation par la protection contre l’emprunt d’identité, faites glisser le curseur sur : ![ Basculez vers le ](../../media/scc-toggle-off.png) large. Le domaine est supprimé de la liste des domaines de confiance dans les **paramètres** de protection contre l’emprunt d’identité de la stratégie anti-hameçonnage.
- Pourquoi nous l’avons capturé.
- Ce que vous devez faire.
- Résumé du domaine qui résume le domaine dont l’identité est emprunt d’identité.
- WhoIs data about the sender.
- Un lien pour ouvrir [l’Explorateur de](threat-explorer.md) menaces pour voir des détails supplémentaires sur l’expéditeur.
- Messages similaires provenant du même expéditeur qui ont été remis à votre organisation.

## <a name="view-information-about-messages-from-impersonated-senders"></a>Afficher des informations sur les messages provenant d’expéditeurs dont l’identité a été usurpée

Dans la page **Informations sur l’emprunt** d’identité qui s’affiche après avoir cliqué sur Afficher les **emprunts** d’identité dans l’aperçu de l’emprunt d’identité, cliquez sur **l’onglet** Utilisateurs. **L’onglet** Utilisateurs contient les informations suivantes :

- **Expéditeur :** adresse de messagerie de l’expéditeur qui a envoyé le message électronique.
- **Nombre de** messages : nombre de messages provenant de l’expéditeur qui usurpe l’identité au cours des 7 derniers jours.
- **Type d’emprunt d’identité**: cette valeur est **Utilisateur dans le nom complet.**
- **Utilisateur** dont l’identité est usurpée : adresse de messagerie de l’expéditeur dont l’identité doit ressembler à celle de l’utilisateur configuré pour la protection contre l’usurpation d’identité dans la stratégie anti-hameçonnage.
- **Type d’utilisateur**: cette valeur indique le type de protection appliqué (par exemple, utilisateur **protégé** ou **Mailbox Intelligence).**
- **Stratégie**: stratégie anti-hameçonnage qui a détecté l’expéditeur dont l’identité a été usurpée.
- **Autorisé à usurper l’identité**: l’une des valeurs suivantes :
  - **Oui**: l’expéditeur a été configuré en tant qu’utilisateur approuvé (une exception pour la protection contre l’emprunt d’identité) dans la stratégie anti-hameçonnage. Les messages provenant de l’expéditeur dont l’identité a été usurpée ont été détectés, mais autorisés.
  - **Non**: l’expéditeur a été configuré pour la protection contre l’emprunt d’identité dans la stratégie anti-hameçonnage. Les messages provenant de l’expéditeur dont l’identité a été usurpée ont été détectés et actionnables en fonction de l’action des utilisateurs usurpés dans la stratégie anti-hameçonnage.

Vous pouvez cliquer sur les en-tête de colonne sélectionnés pour trier les résultats.

Pour filtrer les résultats,  vous pouvez utiliser la zone Filtrer l’expéditeur pour entrer une liste de valeurs séparées par des virgules pour filtrer les résultats.

### <a name="view-details-about-messages-from-impersonated-senders"></a>Afficher les détails des messages provenant d’expéditeurs dont l’identité a été usurpée

Sous **l’onglet** Utilisateurs de **la** page Informations sur l’emprunt d’identité, sélectionnez l’une des détections d’emprunt d’identité disponibles. Le volant de détails qui s’affiche contient les informations et fonctionnalités suivantes :

- **Stratégie d’emprunt d’identité** de sélection à modifier : sélectionnez la stratégie anti-hameçonnage concernée que vous souhaitez modifier. Seules les stratégies dans laquelle l’expéditeur dont l’identité est usurpée sont définies dans la stratégie sont disponibles. Reportez-vous à la page précédente pour voir quelle stratégie était réellement responsable de la détection de l’expéditeur usurpé d’identité (probablement en fonction du destinataire et de la priorité de la stratégie).
- Ajoutez à la liste des expéditeurs autorisés à usurper l’identité : utilisez ce basculement pour ajouter ou supprimer l’expéditeur des domaines et des expéditeurs de confiance **(exceptions** d’emprunt d’identité) pour la stratégie anti-hameçonnage que vous avez sélectionnée :
  - Si la **valeur Autorisée à usurper l’identité** de cette entrée est **Non,** le basculement est éteint. Pour exempter l’expéditeur de l’évaluation par la protection contre l’emprunt d’identité, faites glisser le curseur sur : ![ Basculez sur ](../../media/scc-toggle-on.png) . L’expéditeur est ajouté  à la liste des utilisateurs de confiance dans les paramètres de protection contre l’emprunt d’identité de la stratégie anti-hameçonnage.
  - Si la **valeur Autorisée à usurper l’identité** de cette entrée est **Oui,** le basculement est sur. Pour renvoyer l’expéditeur à l’évaluation par la protection contre l’emprunt d’identité, faites glisser le curseur sur : ![ Basculez vers le ](../../media/scc-toggle-off.png) large. L’expéditeur est supprimé  de la liste des utilisateurs de confiance dans les paramètres de protection contre l’emprunt d’identité de la stratégie anti-hameçonnage.
- Pourquoi nous l’avons capturé.
- Ce que vous devez faire.
- Résumé de l’expéditeur qui résume l’expéditeur dont l’identité a été usurpée.
- WhoIs data about the sender.
- Un lien pour ouvrir [l’Explorateur de](threat-explorer.md) menaces pour voir des détails supplémentaires sur l’expéditeur.
- Messages similaires provenant du même expéditeur qui ont été remis à votre organisation.
