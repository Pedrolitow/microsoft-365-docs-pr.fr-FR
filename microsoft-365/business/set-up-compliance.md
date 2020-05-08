---
title: Renforcer la protection contre les menaces pour Microsoft 365 Business Premium
f1.keywords:
- NOCSH
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
- seo-marvel-mar
search.appverid:
- BCS160
- MET150
description: Configurez les fonctionnalités de conformité pour empêcher toute perte de données et protéger les informations sensibles de vos clients.
ms.openlocfilehash: a3405207cd7d2d6565807ef0f3a51acbcb80409a
ms.sourcegitcommit: 46644f9778bc70ab6d62783e0a1e60ba2eccc27f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2020
ms.locfileid: "44165734"
---
# <a name="set-up-compliance-features"></a>Configurer les fonctionnalités de conformité

Microsoft 365 Business Premium inclut des fonctionnalités pour protéger vos données et appareils, et vous aider à sécuriser les informations sensibles de vos clients.

## <a name="set-up-dlp-features"></a>Configurer les fonctionnalités DLP

Voir [Create a DLP Policy from a template](https://docs.microsoft.com/microsoft-365/compliance/create-a-dlp-policy-from-a-template) pour obtenir un exemple sur la façon de configurer une stratégie de protection contre les informations d’identification personnelle (PII). 
  
DLP comprend de nombreux modèles de stratégie prêts à l’emploi pour de nombreux paramètres régionaux différents. Par exemple, les données financières de l’Australie, le Canada Personal Information Act, les données financières américaines, etc. Consultez la rubrique relative aux [modèles de stratégie DLP](https://docs.microsoft.com/microsoft-365/compliance/what-the-dlp-policy-templates-include) pour une liste complète. Tous ces modèles peuvent être activés de la même manière que l’exemple de modèle PII. 
  
## <a name="set-up-email-retention-with-exchange-online-archiving"></a>Configurer la rétention du courrier électronique avec archivage Exchange Online

 Les fonctionnalités de licence d' **archivage Exchange Online** permettent de respecter les normes de conformité et de réglementation en conservant le contenu des courriers électroniques pour eDiscovery. Elle permet également de réduire les risques en cas de poursuites, et permet de récupérer les données après une violation de la sécurité ou lorsque vous devez récupérer des éléments supprimés. Vous pouvez utiliser la conservation pour litige pour conserver tout le contenu d’un utilisateur ou utiliser des stratégies de rétention pour personnaliser ce que vous souhaitez conserver.
  
**Conservation pour litige :** Vous pouvez conserver tout le contenu des boîtes aux lettres, y compris les éléments supprimés, en mettant la boîte aux lettres entière d’un utilisateur en conservation pour litige. 
    
Pour placer une boîte aux lettres en conservation pour litige, dans le centre d’administration :
    
1. Dans le volet de **navigation de gauche, accédez à** \> utilisateurs **actifs**.
    
2. Sélectionnez un utilisateur dont vous souhaitez placer la boîte aux lettres en conservation pour litige. Dans le volet utilisateur, développez **paramètres de messagerie**, puis en regard de **paramètres supplémentaires**, choisissez **modifier les propriétés Exchange**.
    
3. Sur la page boîte aux lettres de l’utilisateur, choisissez les fonctionnalités de boîte aux lettres * * dans le volet de navigation de gauche, puis cliquez sur le lien **activer** en **conservation pour litige**.
    
4. Dans la boîte de dialogue **conservation pour litige** , vous pouvez spécifier la durée de la conservation pour litige dans le champ Durée de la **conservation pour litige** . Laissez le champ vide si vous voulez placer un blocage infini. Vous pouvez également ajouter des notes et diriger le propriétaire de la boîte aux lettres vers un site Web vous devrez peut-être en savoir plus sur la suspension pour litige. \>**Enregistrer**.
    
**Rétention :** Vous pouvez activer des stratégies de rétention personnalisées, par exemple, pour conserver un certain temps ou supprimer définitivement le contenu à la fin de la période de rétention. Pour en savoir plus, consultez la rubrique [vue d’ensemble des stratégies de rétention](https://docs.microsoft.com/microsoft-365/compliance/retention-policies).

## <a name="set-up-sensitivity-labels"></a>Configurer les étiquettes de confidentialité

Les étiquettes de confidentialité sont fournies avec Azure information protection (AIP) plan 1 et vous aident à classer et éventuellement protéger vos documents et e-mails en appliquant des étiquettes. Les étiquettes peuvent être appliquées automatiquement par les administrateurs qui définissent des règles et des conditions, manuellement par les utilisateurs ou à l’aide d’une combinaison de recommandations pour les utilisateurs.

Pour configurer les étiquettes de confidentialité, affichez la vidéo [créer et gérer les étiquettes de confidentialité](https://support.office.com/article/2fb96b54-7dd2-4f0c-ac8d-170790d4b8b9) .



### <a name="install-the-azure-information-protection-client-manually"></a>Installation manuelle du client Azure information protection

Pour installer manuellement le client AIP :

1. Téléchargez **AzinfoProtection_UL. exe** à partir du [Centre de téléchargement Microsoft](https://www.microsoft.com/download/details.aspx?id=53018).
 
2. Vous pouvez vérifier que l’installation a fonctionné en affichant un document Word et en vous assurant que l’option de **confidentialité** est disponible sous l’onglet **Accueil** .
<br/>![Onglet protection dans un document Word.](../media/word-sensitivity.png)

Pour plus d’informations, consultez [la rubrique installer le client](https://docs.microsoft.com/azure/information-protection/infoprotect-tutorial-step3).
