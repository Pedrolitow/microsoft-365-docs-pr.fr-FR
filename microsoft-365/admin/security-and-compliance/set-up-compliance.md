---
title: Renforcer la protection contre les menaces pour les Microsoft 365 Business Premium
f1.keywords:
- NOCSH
ms.author: sharik
author: skjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- MiniMaven
- MSB365
- OKR_SMB_M365
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
description: Configurer des fonctionnalités de conformité pour éviter la perte de données et sécuriser les informations sensibles de vos clients et de vos clients.
ms.openlocfilehash: 69960c4f158a30d9d47d749ed1e7eb2d2d74f430
ms.sourcegitcommit: b6ab10ba95e4b986065c51179ead3810cc1e2a85
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2021
ms.locfileid: "61521041"
---
# <a name="set-up-compliance-features"></a>Configurer les fonctionnalités de conformité

Votre Microsoft 365 Business Premium comprend des fonctionnalités pour protéger vos données et appareils, et vous aider à sécuriser vos informations sensibles et vos clients.

## <a name="watch-set-up-dlp-features"></a>Regarder : configurer les fonctionnalités DLP

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE3TGvL?autoplay=false]

Les stratégies de protection contre la perte de données permettent d’identifier et de protéger les informations sensibles de votre entreprise, telles que les numéros de sécurité sociale ou les dossiers médicaux.

1. To get started, go to the [admin center](https://admin.microsoft.com), and select **Setup**.
1. Faites défiler vers le bas **pour configurer la** protection contre la perte de données, puis **sélectionnez Afficher,** puis **Gérer**.
1. Pour modifier une stratégie, sélectionnez-la, sélectionnez **Modifier la stratégie,** puis ce qu’il faut modifier. Par exemple, sélectionnez **Emplacements** pour modifier ce qui est analysé.
1. Pour créer une stratégie, **sélectionnez Créer une stratégie.**
1. Vous pouvez créer une stratégie personnalisée ou commencer par un modèle. Par exemple, pour créer une stratégie  HIPAA, sélectionnez le modèle médical et de santé, puis sélectionnez loi américaine d’assurance maladie **(HIPAA).** Sélectionnez **Suivant**.
1. Examinez vos paramètres, puis sélectionnez **Créer.** Une fois votre stratégie entrée en vigueur, le courrier électronique qui contient les informations sensibles décrites est bloqué et l’expéditeur qui a tenté d’envoyer ces informations voit un message d’avertissement.

Voir [Créer une stratégie DLP à partir](../../compliance/create-a-dlp-policy-from-a-template.md) d’un modèle pour obtenir un exemple sur la façon de configurer une stratégie pour protéger contre la perte de données personnelles. 
  
DLP est livré avec de nombreux modèles de stratégie prêts à l’emploi pour de nombreux paramètres régionaux différents. Par exemple, les données financières en Australie, la Loi canadienne sur les informations personnelles, les données financières américaines, etc. Voir [ce que les modèles de stratégie DLP incluent](../../compliance/what-the-dlp-policy-templates-include.md) pour obtenir une liste complète. Tous ces modèles peuvent être activés de la même façon que l’exemple de modèle PII.
 
## <a name="set-up-email-retention-with-exchange-online-archiving"></a>Configurer la rétention du courrier électronique avec Archivage Exchange Online

 **Archivage Exchange Online** licences permettent de maintenir les normes réglementaires et de conformité en conservant le contenu du courrier électronique pour eDiscovery. Cela permet également de réduire vos risques en cas de poursuites judiciaires et permet de récupérer des données après une violation de la sécurité ou lorsque vous devez récupérer des éléments supprimés. Vous pouvez utiliser la conservation pour litige pour conserver tout le contenu d’un utilisateur ou utiliser des stratégies de rétention pour personnaliser ce que vous souhaitez conserver.
  
**Attente pour litige :** Vous pouvez conserver tout le contenu de la boîte aux lettres, y compris les éléments supprimés, en mettant la boîte aux lettres entière d’un utilisateur en conservation pour litige. 
    
Pour placer une boîte aux lettres en attente pour litige, dans le Centre d’administration :
    
1. Dans le navigation de gauche, allez à **Utilisateurs** \> **actifs.**
    
2. Sélectionnez un utilisateur dont vous souhaitez placer la boîte aux lettres en attente pour litige. Dans le volet utilisateur, développez **Paramètres** de messagerie et, en plus des **paramètres,** choisissez Modifier **Exchange propriétés.**
    
3. Dans la page de boîte aux lettres de l’utilisateur, choisissez ** fonctionnalités de boîte aux lettres ** dans le navigation gauche, puis choisissez le lien Activer sous Attente pour **litige.** 
    
4. Dans la boîte **de dialogue De attente** pour litige, vous pouvez spécifier la durée de la durée de la attente pour litige dans le champ Durée de la durée de la attente **pour** litige. Laissez le champ vide si vous souhaitez placer une attente infinie. Vous pouvez également ajouter des notes et diriger le propriétaire de la boîte aux lettres vers un site web dont vous pourriez avoir besoin pour en savoir plus sur la mise en attente pour litige. \>**Enregistrer**.
    
**Rétention :** Vous pouvez activer des stratégies de rétention personnalisées, par exemple, pour conserver un certain temps ou supprimer définitivement du contenu à la fin de la période de rétention. Pour plus d’informations, voir [Vue d’ensemble des stratégies de rétention.](../../compliance/retention.md)

## <a name="watch-set-up-sensitivity-labels"></a>Regardez : configurer les étiquettes de niveau de sensibilité

Les étiquettes de niveau de sensibilité sont disponibles avec Azure Information Protection (AIP) Plan 1 et vous aident à classer et éventuellement protéger vos documents et e-mails en appliquant des étiquettes. Les étiquettes peuvent être appliquées automatiquement par les administrateurs qui définissent des règles et des conditions, manuellement par les utilisateurs ou à l’aide d’une combinaison dans laquelle des recommandations sont données aux utilisateurs.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE3VRGT?autoplay=false]

1. Dans le Centre [d’administration,](https://admin.microsoft.com)sélectionnez le **Centre d’administration** de conformité.
1. Sélectionnez **Classification,** puis **étiquettes de sensibilité.**
1. Sélectionnez **Créer une étiquette** et, lorsque l’avertissement s’affiche, sélectionnez **Oui.**
1. Examinez vos paramètres, puis sélectionnez **Créer.** Votre étiquette a été créée. Répétez ce processus pour toutes les étiquettes supplémentaires que vous souhaitez.
1. Par défaut, les étiquettes apparaissent Office applications dans cet ordre : **Confidentiel,** **Interne** et **Public**. Pour modifier l’ordre, pour chaque étiquette, sélectionnez les trois points (autres actions), puis déplacez l’étiquette vers le haut ou vers le bas. En règle générale, les autorisations sont répertoriées du niveau d’autorisation le plus bas au niveau le plus élevé.
1. Examinez vos paramètres, puis sélectionnez **Publier.**

Pour que vos étiquettes fonctionnent, chaque utilisateur doit télécharger le client d’étiquetage unifié Azure Information Protection. Recherchez des **AzinfoProtection_UL.exe** sur le web, puis téléchargez-le à partir du Centre de téléchargement Microsoft et exécutez-le sur les ordinateurs de vos utilisateurs.

La prochaine fois que vous ouvrirez un application Office comme Word, vous verrez les étiquettes de niveau de sensibilité qui ont été créées. Pour modifier ou appliquer une étiquette, sélectionnez Sensibilité et choisissez une étiquette.

### <a name="install-the-azure-information-protection-client-manually"></a>Installer manuellement le client Azure Information Protection

Pour installer manuellement le client AIP :

1. Téléchargez **AzinfoProtection_UL.exe** à partir du [Centre de téléchargement Microsoft.](https://www.microsoft.com/download/details.aspx?id=53018)
 
2. Pour vérifier que l’installation a fonctionné, affichez  un document Word et assurez-vous que l’option Sensibilité est disponible sous l’onglet **Accueil.**
<br/>![Onglet Protection dans un document Word.](../../media/word-sensitivity.png)

Pour plus d’informations, voir [Installer le client.](/azure/information-protection/infoprotect-tutorial-step3)