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
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
description: Configurer des fonctionnalités de conformité pour éviter la perte de données et sécuriser les informations sensibles de vos clients et de vos clients.
ms.openlocfilehash: e210787718025c5df29af8d4a2283291dcecc2a8
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50912527"
---
# <a name="set-up-compliance-features"></a>Configurer les fonctionnalités de conformité

Votre Abonnement Microsoft 365 Business Premium comprend des fonctionnalités pour protéger vos données et appareils et vous aider à sécuriser les informations sensibles de vos clients et de vos clients.

## <a name="set-up-dlp-features"></a>Configurer les fonctionnalités DLP

Voir [Créer une stratégie DLP à partir](../compliance/create-a-dlp-policy-from-a-template.md) d’un modèle pour obtenir un exemple sur la façon de configurer une stratégie pour protéger contre la perte de données personnelles. 
  
DLP est livré avec de nombreux modèles de stratégie prêts à l’emploi pour de nombreux paramètres régionaux différents. Par exemple, les données financières en Australie, la Loi canadienne sur les informations personnelles, les données financières américaines, etc. Voir [ce que les modèles](../compliance/what-the-dlp-policy-templates-include.md) de stratégie DLP incluent pour obtenir une liste complète. Tous ces modèles peuvent être activés de la même façon que l’exemple de modèle PII. 
  
## <a name="set-up-email-retention-with-exchange-online-archiving"></a>Configurer la rétention du courrier électronique à l’Archivage Exchange Online

 **Archivage Exchange Online** licences permettent de maintenir les normes réglementaires et de conformité en conservant le contenu du courrier électronique pour eDiscovery. Cela permet également de réduire vos risques en cas de poursuites judiciaires et permet de récupérer des données après une violation de la sécurité ou lorsque vous devez récupérer des éléments supprimés. Vous pouvez utiliser la conservation pour litige pour conserver tout le contenu d’un utilisateur ou utiliser des stratégies de rétention pour personnaliser ce que vous souhaitez conserver.
  
**Attente pour litige :** Vous pouvez conserver tout le contenu de la boîte aux lettres, y compris les éléments supprimés, en mettant la boîte aux lettres entière d’un utilisateur en attente pour litige. 
    
Pour placer une boîte aux lettres en attente pour litige, dans le Centre d’administration :
    
1. Dans le navigation de gauche, allez à **Utilisateurs** \> **actifs.**
    
2. Sélectionnez un utilisateur dont vous souhaitez placer la boîte aux lettres en attente pour litige. Dans le volet utilisateur, développez **Paramètres de messagerie,** puis en plus des **paramètres,** choisissez **Modifier les propriétés Exchange**.
    
3. Dans la page de boîte aux lettres de l’utilisateur, choisissez ** fonctionnalités de boîte aux lettres ** dans le navigation gauche, puis choisissez le lien Activer sous Attente pour **litige.** 
    
4. Dans la boîte **de dialogue De attente** pour litige, vous pouvez spécifier la durée de la durée de la attente pour litige dans le champ Durée de la durée de la attente **pour** litige. Laissez le champ vide si vous souhaitez placer une attente infinie. Vous pouvez également ajouter des notes et diriger le propriétaire de la boîte aux lettres vers un site web dont vous pourriez avoir besoin pour en savoir plus sur la mise en attente pour litige. \>**Enregistrer**.
    
**Rétention :** Vous pouvez activer des stratégies de rétention personnalisées, par exemple, pour conserver un certain temps ou supprimer définitivement du contenu à la fin de la période de rétention. Pour plus d’informations, voir [Vue d’ensemble des stratégies de rétention.](../compliance/retention.md)

## <a name="set-up-sensitivity-labels"></a>Configurer les étiquettes de niveau de sensibilité

Les étiquettes de niveau de sensibilité sont disponibles avec Azure Information Protection (AIP) Plan 1 et vous aident à classer et éventuellement protéger vos documents et e-mails en appliquant des étiquettes. Les étiquettes peuvent être appliquées automatiquement par les administrateurs qui définissent des règles et des conditions, manuellement par les utilisateurs ou à l’aide d’une combinaison dans laquelle des recommandations sont données aux utilisateurs.

Pour configurer les étiquettes de niveau de sensibilité, affichez la vidéo créer et gérer [les étiquettes de](https://support.microsoft.com/office/2fb96b54-7dd2-4f0c-ac8d-170790d4b8b9) sensibilité.



### <a name="install-the-azure-information-protection-client-manually"></a>Installer manuellement le client Azure Information Protection

Pour installer manuellement le client AIP :

1. Téléchargez **AzinfoProtection_UL.exe** à partir du [Centre de téléchargement Microsoft.](https://www.microsoft.com/download/details.aspx?id=53018)
 
2. Pour vérifier que l’installation a fonctionné, affichez  un document Word et assurez-vous que l’option Sensibilité est disponible sous l’onglet **Accueil.**
<br/>![Onglet Protection dans un document Word.](../media/word-sensitivity.png)

Pour plus d’informations, voir [Installer le client.](/azure/information-protection/infoprotect-tutorial-step3)