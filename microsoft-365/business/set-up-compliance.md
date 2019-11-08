---
title: Renforcer la protection contre les menaces pour Microsoft 365 Business
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- M365-identity-device-management
ms.custom:
- MiniMaven
- MSB365
- OKR_SMB_M365
search.appverid:
- BCS160
- MET150
description: Configurez les fonctionnalités de conformité pour empêcher toute perte de données et étiqueter les données sensibles.
ms.openlocfilehash: 5213c55f4a8ce0e223896f1b960847714d6d06cb
ms.sourcegitcommit: 70e920f76526f47fc849df615de4569e0ac2f4be
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38031412"
---
# <a name="set-up-compliance-features"></a>Configurer les fonctionnalités de conformité

Votre entreprise Microsoft 365 est dotée de fonctionnalités pour protéger vos données et périphériques, et vous aider à sécuriser les informations sensibles de vos clients et de vos clients.

## <a name="set-up-dlp-features"></a>Configurer les fonctionnalités DLP

Voir [Create a DLP Policy from a template](https://support.office.com/article/59414438-99f5-488b-975c-5023f2254369) pour obtenir un exemple sur la façon de configurer une stratégie de protection contre les informations d’identification personnelle (PII). 
  
DLP comprend de nombreux modèles de stratégie prêts à l’emploi pour de nombreux paramètres régionaux différents. Par exemple, les données financières de l’Australie, le Canada Personal Information Act, les données financières américaines, etc. Consultez la rubrique relative aux [modèles de stratégie DLP](https://support.office.com/article/c2e588d3-8f4f-4937-a286-8c399f28953a) pour une liste complète. Tous ces modèles peuvent être activés de la même manière que l’exemple de modèle PII. 
  
## <a name="set-up-email-retention-with-exchange-online-archiving"></a>Configurer la rétention du courrier électronique avec archivage Exchange Online

 Les fonctionnalités de licence d' **archivage Exchange Online** permettent de respecter les normes de conformité et de réglementation en conservant le contenu des courriers électroniques pour eDiscovery. Elle contribue également à réduire les risques en cas de poursuite et permet de récupérer les données après une violation de la sécurité ou de récupérer des éléments supprimés. Vous pouvez utiliser la conservation pour litige pour conserver tout le contenu d’un utilisateur ou utiliser des stratégies de rétention pour personnaliser ce que vous souhaitez conserver.
  
**Conservation pour litige :** Vous pouvez conserver tout le contenu des boîtes aux lettres, y compris les éléments supprimés, en mettant la boîte aux lettres entière d’un utilisateur en conservation pour litige. 
    
Pour placer une boîte aux lettres en conservation pour litige, dans le centre d’administration :
    
1. Dans le volet de **navigation de gauche, accédez à** \> utilisateurs **actifs**.
    
2. Sélectionnez un utilisateur dont vous souhaitez placer la boîte aux lettres en conservation pour litige et, dans le volet utilisateur, développez **paramètres de messagerie** , puis en regard de **paramètres supplémentaires** , choisissez **modifier les propriétés Exchange**.
    
3. Sur la page boîte aux lettres de l’utilisateur, choisissez les fonctionnalités de boîte aux lettres * * dans le volet de navigation de gauche, puis cliquez sur le lien **activer** en **conservation pour litige**.
    
4. Dans la boîte de dialogue **conservation pour litige** , vous pouvez spécifier la durée de la conservation pour litige dans le champ Durée de la **conservation pour litige** , laissez le champ vide si vous voulez placer un blocage infini. Vous pouvez également ajouter des notes et diriger le propriétaire de la boîte aux lettres vers un site Web vous devrez peut-être \> en savoir plus sur **la conservation pour**litige.
    
**Rétention :** Vous pouvez activer des stratégies de rétention personnalisées, par exemple, pour conserver un certain temps ou supprimer définitivement le contenu à la fin de la période de rétention. Pour en savoir plus, consultez la rubrique [vue d’ensemble des stratégies de rétention](https://support.office.com/article/5e377752-700d-4870-9b6d-12bfc12d2423).

## <a name="set-up-sensitivity-labels"></a>Configurer les étiquettes de confidentialité

Les étiquettes de confidentialité sont fournies avec Azure information protection (AIP) plan 1 et vous aident à classer et éventuellement protéger vos documents et e-mails en appliquant des étiquettes. Les étiquettes peuvent être appliquées automatiquement par les administrateurs qui définissent des règles et des conditions, manuellement par les utilisateurs ou à l’aide d’une combinaison de recommandations pour les utilisateurs.

Pour configurer les étiquettes de confidentialité, affichez la vidéo [créer et gérer les étiquettes de confidentialité](https://support.office.com/article/2fb96b54-7dd2-4f0c-ac8d-170790d4b8b9) .



### <a name="install-the-azure-information-protection-client-manually"></a>Installation manuelle du client Azure information protection

Pour installer manuellement le client AIP :

1. Téléchargez **AzinfoProtection_UL. exe** à partir du [Centre de téléchargement Microsoft](https://www.microsoft.com/download/details.aspx?id=53018).
 
2. Vous pouvez vérifier que l’installation a fonctionné en affichant un document Word et en vous assurant que l’option de **confidentialité** est disponible sous l’onglet **Accueil** .
<br/>![Onglet protection dans un document Word.](media/word-sensitivity.png)

Pour plus d’informations, consultez [la rubrique installer le client](https://docs.microsoft.com/azure/information-protection/infoprotect-tutorial-step3).
