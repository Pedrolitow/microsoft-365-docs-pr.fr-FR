---
title: Procédure pas à pas-usurpation d’aide
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: overview
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: 59a3ecaf-15ed-483b-b824-d98961d88bdd
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent découvrir comment fonctionne l’aide à la décision. Ils peuvent déterminer rapidement les expéditeurs qui envoient des messages légitimes à leur organisation à partir de domaines qui ne passent pas de vérifications d’authentification de messagerie (SPF, DKIM ou DMARC).
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 665745e940ea9547d57a1d7c47ff54eaae3756b7
ms.sourcegitcommit: 0a8b0186cc041db7341e57f375d0d010b7682b7d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "49659689"
---
# <a name="walkthrough---spoof-intelligence-insight-in-microsoft-defender-for-office-365"></a>Procédure pas à pas-usurpation d’aide à la décision de Microsoft Defender pour Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Dans les organisations Microsoft 365 avec Defender pour Office 365, vous pouvez utiliser la fonction d’aide à la décision pour déterminer rapidement les expéditeurs externes qui envoient des messages électroniques non authentifiés (messages provenant de domaines qui ne passent pas de contrôles SPF, DKIM ou DMARC).

En autorisant les expéditeurs externes connus à envoyer des messages falsifiés à partir d’emplacements connus, vous pouvez réduire les faux positifs (bon message électronique marqué comme incorrect). En surveillant les expéditeurs usurpés autorisés, vous fournissez une couche supplémentaire de sécurité pour empêcher les messages non sécurisés d’arriver dans votre organisation.

Pour plus d’informations sur les rapports et les Insights, voir [rapports et informations dans le centre de sécurité & conformité](reports-and-insights-in-security-and-compliance.md).

Cette procédure pas à pas est l’une des suivantes pour le centre de conformité & la sécurité. Pour savoir comment naviguer dans les rapports et les informations, consultez les procédures pas à pas dans la section [Rubriques connexes](#related-topics) .

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Centre de conformité et sécurité sur <https://protection.office.com/>. Pour accéder directement à la page du **tableau de bord de sécurité** , utilisez <https://protection.office.com/searchandinvestigation/dashboard> .

  Vous pouvez afficher le centre d’aide à la décision à partir de plusieurs tableaux de bord dans le centre de conformité & Compliance Center. Quel que soit le tableau de bord que vous examinez, le détail fournit les mêmes détails et vous permet d’effectuer rapidement les mêmes tâches.

- Pour pouvoir utiliser ce cmdlet, vous devez disposer des autorisations dans le centre de sécurité et conformité Office 365.
  - **Gestion de l'organisation**
  - **Administrateur de la sécurité**
  - **Lecteur de sécurité**
  - **Lecteur global**

  Pour en savoir plus, consultez [Autorisations dans le Centre de sécurité et de conformité](permissions-in-the-security-and-compliance-center.md).

  **Remarque**: l’ajout d’utilisateurs au rôle Azure Active Directory correspondant dans le centre d’administration 365 de Microsoft donne aux utilisateurs les autorisations requises dans le centre de sécurité & conformité _et_ des autorisations pour d’autres fonctionnalités de Microsoft 365. Pour plus d’informations, consultez [À propos des rôles d’administrateur](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles).

- Vous activez et désactivez l’intelligence contre les usurpations dans les stratégies de hameçonnage dans Microsoft Defender pour Office 365. L’intelligence usurpée est activée par défaut. Pour plus d’informations, consultez la rubrique [configure anti-phishing Policies in Microsoft Defender for Office 365](configure-atp-anti-phishing-policies.md).

- Pour surveiller et gérer les expéditeurs qui envoient des messages non authentifiés à l’aide d’une usurpation d’identité, reportez-vous à la rubrique [configure usurpation Intelligence in Microsoft 365](learn-about-spoof-intelligence.md).

## <a name="open-the-spoof-intelligence-insight-in-the-security--compliance-center"></a>Ouvrir la vue d’aide à la décision dans le centre de sécurité & conformité

1. Dans le centre de sécurité & conformité, accédez au tableau de bord **gestion des menaces** \> **.**

2. Dans la ligne **Insights** , recherchez l’un des éléments suivants :

   - **Domaines susceptibles d’être usurpés au cours des sept derniers jours**: cette vue indique que l’intelligence contre l’usurpation d’identité est activée (elle est activée par défaut).
   - **Activer la protection contre les falsifications**: cela indique que l’intelligence d’usurpation d’identité est désactivée et que le fait de cliquer sur le Insight vous permet d’activer l’intelligence usurpée.

3. Le tableau de bord affiche des informations comme celles-ci :

   ![Capture d’écran d’un aperçu d’aide à la décision](../../media/28aeabac-c1a1-4d16-9fbe-14996f742a9a.png)

   Cette vue comprend deux modes :

   - **Mode** d’affichage : si l’aide à l’usurpation d’identité est activée, elle indique le nombre de messages affectés par nos capacités d’aide à la falsification au cours des sept derniers jours.
   - **Quel mode si**: si l’intelligence d’usurpation d’identité est désactivée, le rapport indique le nombre de messages qui *auraient* été affectés par nos capacités d’aide à la falsification au cours des sept derniers jours.

   Dans les deux cas, les domaines usurpés affichés dans la vue sont divisés en deux catégories : les domaines **suspects** et les **domaines non suspects**.

   - Les **domaines suspects** sont les suivants :

     - Usurpation de confiance élevée : selon les modèles d’envoi historique et le score de réputation des domaines, nous sommes très convaincus que les domaines sont des usurpations et les messages provenant de ces domaines sont plus susceptibles d’être malveillants.

     - Usurpation de confiance modérée : basée sur des modèles d’envoi historiques et sur le score de réputation des domaines, nous sommes modérément confiants que les domaines sont des usurpations et que les messages envoyés à partir de ces domaines sont légitimes. Les faux positifs sont plus susceptibles de se situer dans cette catégorie que le taux d’usurpation de confiance élevée.

   **Domaines non suspects**: le domaine a échoué aux vérifications d’authentification de messagerie indéfinies [SPF](how-office-365-uses-spf-to-prevent-spoofing.md), [DKIM](use-dkim-to-validate-outbound-email.md)et [DMARC](use-dmarc-to-validate-email.md)). Toutefois, le domaine a transmis nos vérifications d’authentification de messagerie implicites ([authentification composite](email-validation-and-authentication.md#composite-authentication)). Par conséquent, aucune action de détection d’usurpation d’identité n’a été effectuée sur le message.

### <a name="view-detailed-information-about-suspicious-domains-from-the-spoof-intelligence-insight"></a>Afficher des informations détaillées sur les domaines suspects à partir de l’aide à la décision

1. Sur la page d’aide à la décision, cliquez sur **domaines suspects** ou **domaines non suspects** pour accéder à la page d’aide à la **décision** . La page d’aide à la **décision** contient les informations suivantes :

   - **Domaine usurpé**: domaine de l’utilisateur usurpé affiché dans la zone **de** dans clients de messagerie. Cette adresse est également appelée `5322.From` adresse.
   - **Infrastructure**: également appelée infrastructure d' _envoi_. Domaine trouvé dans une recherche DNS inversée (enregistrement PTR) de l’adresse IP du serveur de messagerie source. Si l’adresse IP source n’a pas d’enregistrement PTR, l’infrastructure d’envoi est identifiée par \<source IP\> /24 (par exemple, 192.168.100.100/24).
   - **Nombre** de messages : nombre de messages de l’infrastructure d’envoi à votre organisation qui contiennent le domaine usurpé spécifié au cours des 7 derniers jours.
   - **Dernière** détection : dernière date à laquelle un message a été reçu de l’infrastructure d’envoi qui contient le domaine usurpé.
   - **Type d’usurpation**: cette valeur est **externe**.
   - **Autorisé à usurper ?**: les valeurs que vous voyez ici sont les suivantes :
     - **Oui**: les messages provenant de la combinaison du domaine de l’utilisateur usurpé et de l’infrastructure d’envoi sont autorisés et ne sont pas traités comme des messages falsifiés.
     - **Non**: les messages provenant de la combinaison de l’infrastructure d’envoi et du domaine de l’utilisateur usurpé sont marqués comme falsifiés. L’action est contrôlée par la stratégie anti-hameçonnage par défaut ou par des stratégies anti-hameçonnage personnalisées (la valeur par défaut est **déplacer le message vers le dossier courrier indésirable**).

     Pour plus d’informations, consultez la rubrique [configure anti-phishing Policies in Microsoft Defender for Office 365](configure-atp-anti-phishing-policies.md).

2. Sélectionnez un élément dans la liste pour afficher les détails relatifs à la paire domaine/envoi d’infrastructure dans un lanceur. Ces informations sont les suivantes :
   - Pourquoi nous avons pris cette explication.
   - Ce que vous devez faire.
   - Un résumé de domaine.
   - Identification des données relatives à l’expéditeur.
   - Messages similaires que nous avons vus dans votre client par le même expéditeur.

   À partir de là, vous pouvez également choisir d’ajouter ou de supprimer la paire domaine/envoi d’infrastructure de la liste **autorisé à usurper** l’expéditeur. Définissez simplement le bouton bascule en conséquence.

   ![Capture d’écran d’un domaine dans le volet d’informations d’aide à la décision](../../media/03ad3e6e-2010-4e8e-b92e-accc8bbebb79.png)

### <a name="adding-a-domain-to-the-allowed-to-spoof-list"></a>Ajout d’un domaine à la liste des autorisations d’usurpation d’identité

L’ajout d’un domaine à la liste autorisé à usurper à partir de l’aide à la décision ne permet que de combiner le domaine usurpé *et* l’infrastructure émettrice. Elle n’autorise pas les messages provenant du domaine usurpé à partir de n’importe quelle source, et ne permet pas non plus d’envoyer des courriers électroniques à partir de l’infrastructure d’envoi de n’importe quel domaine.

Par exemple, vous autorisez le domaine suivant à la liste des autorisations d’usurpation d’identité :

- **Domaine**: gmail.com
- **Infrastructure**: TMS.mx.com

Seul le courrier électronique de ce domaine/cette paire d’infrastructure d’envoi sera autorisé à usurper. Les autres expéditeurs tentant d’usurper gmail.com ne sont pas autorisés. Les messages dans d’autres domaines de tms.mx.com sont vérifiés par l’aide à l’usurpation d’identité.

## <a name="related-topics"></a>Voir aussi

[Protection contre l’usurpation d’identité dans Microsoft 365](anti-spoofing-protection.md)
