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
search.appverid:
- BCS160
- MET150
description: Configurez Office 365 Advanced Threat Protection et protégez les données sensibles.
ms.openlocfilehash: 53741a7726222bb32329a401953be72257df95cc
ms.sourcegitcommit: 7ac06563c6ff034358e8fd3f9298fc426187ade2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/31/2019
ms.locfileid: "34668383"
---
# <a name="set-up-compliance-features"></a>Configurer les fonctionnalités de conformité

Votre entreprise Microsoft 365 est dotée de fonctionnalités pour protéger vos données et périphériques, et vous aider à sécuriser les informations sensibles de vos clients et de vos clients.

## <a name="set-up-dlp-features"></a>Configurer les fonctionnalités DLP

Voir [Create a DLP Policy from a template](https://support.office.com/article/59414438-99f5-488b-975c-5023f2254369) pour obtenir un exemple sur la façon de configurer une stratégie de protection contre les informations d’identification personnelle (PII). 
  
DLP comprend de nombreux modèles de stratégie prêts à l’emploi pour de nombreux paramètres régionaux différents. Par exemple, les données financières de l’Australie, le Canada Personal Information Act, les données financières américaines, etc. Consultez la rubrique relative aux [modèles de stratégie DLP](https://support.office.com/article/c2e588d3-8f4f-4937-a286-8c399f28953a) pour une liste complète. Tous ces modèles peuvent être activés de la même manière que l’exemple de modèle PII. 
  
## <a name="set-up-email-retention-with-exchange-online-archiving"></a>Configurer la rétention du courrier électronique avec archivage Exchange Online

 Les fonctionnalités de licence d' **archivage Exchange Online** permettent de respecter les normes de conformité et de réglementation en conservant le contenu des courriers électroniques pour eDiscovery. Elle contribue également à réduire les risques en cas de poursuite et permet de récupérer les données après une violation de la sécurité ou de récupérer des éléments supprimés. Vous pouvez utiliser la conservation pour litige pour conserver tout le contenu d’un utilisateur ou utiliser des stratégies de rétention pour personnaliser ce que vous souhaitez conserver.
  
**Conservation pour litige:** Vous pouvez conserver tout le contenu des boîtes aux lettres, y compris les éléments supprimés, en mettant la boîte aux lettres entière d’un utilisateur en conservation pour litige. 
    
Pour placer une boîte aux lettres en conservation pour litige, dans le centre d’administration:
    
1. Dans le volet de navigation de gauche **** \> , accédez à utilisateurs **actifs**.
    
2. Sélectionnez un utilisateur dont vous souhaitez placer la boîte aux lettres en conservation pour litige et, dans le volet utilisateur, développez **paramètres de messagerie** , puis en regard de **paramètres supplémentaires** , choisissez **modifier les propriétés Exchange**.
    
3. Sur la page boîte aux lettres de l’utilisateur, choisissez les fonctionnalités de boîte aux lettres * * dans le volet de navigation de gauche, puis cliquez sur le lien **activer** en **conservation pour litige**.
    
4. Dans la boîte de dialogue **conservation pour litige** , vous pouvez spécifier la durée de la conservation pour litige dans le champ Durée de la **conservation pour litige** , laissez le champ vide si vous voulez placer un blocage infini. Vous pouvez également ajouter des notes et diriger le propriétaire de la boîte aux lettres vers un site Web vous devrez peut-être \> **** en savoir plus sur la conservation pour litige.
    
**Rétention:** Vous pouvez activer des stratégies de rétention personnalisées, par exemple, pour conserver un certain temps ou supprimer définitivement le contenu à la fin de la période de rétention. Pour en savoir plus, consultez la rubrique [vue d’ensemble des stratégies de](https://support.office.com/article/5e377752-700d-4870-9b6d-12bfc12d2423)rétention.

## <a name="set-up-azure-information-protection-features"></a>Configurer les fonctionnalités Azure information protection

Azure information protection (AIP) vous permet de classer et, si vous le souhaitez, de protéger vos documents et vos courriers électroniques, en appliquant des étiquettes. Les étiquettes peuvent être appliquées automatiquement par les administrateurs qui définissent des règles et des conditions, manuellement par les utilisateurs ou à l’aide d’une combinaison de recommandations pour les utilisateurs.

Dans Outlook sur le Web, vous pouvez appliquer les étiquettes et restrictions prédéfinies suivantes à vos courriers électroniques:
  
- **Ne pas transférer**: les destinataires peuvent lire le message, mais ils ne peuvent pas transférer, imprimer ou copier du contenu
    
- **Encrypt**: l’intégralité du message est chiffrée. Les destinataires doivent confirmer leur identité avant d’accéder au contenu chiffré et ne peuvent pas supprimer le chiffrement.
    
- **Confidential**: donne aux employés de votre organisation des autorisations complètes sur le contenu et les pièces jointes de messagerie, mais pas sur les personnes externes à votre organisation. Les propriétaires de données peuvent suivre et révoquer du contenu à tout moment.
    
- **Hautement confidentiel**: cette restriction peut être appliquée aux données hautement confidentielles, ce qui permet aux employés d’afficher, de modifier et de répondre, mais pas de transférer, d’imprimer ou de copier les données. Les propriétaires de données peuvent suivre et révoquer du contenu à tout moment.

### <a name="make-sure-azure-information-protection-is-activated"></a>Vérifier que Azure information protection est activé

Pour vérifier qu’AIP est activé:

1. Connectez-vous à [Azure Portal](https://portal.azure.com/).

2. Sélectionnez **tous les services** et tapez *Azure information protection* dans la **zone de recherche**.

3. Une fois que les résultats s’affichent, cliquez sur le bouton Démarrer en regard d' **Azure information protection** pour en faire un favori et le retrouver facilement plus tard.

4. Sélectionnez **activation de protection** **Azure information protection** \> et assurez-vous que l’État est défini sur activé. 

### <a name="view-the-azure-information-protection-policy-and-default-labels"></a>Afficher la stratégie Azure information protection et les étiquettes par défaut 

Pour afficher et modifier les étiquettes existantes:

1. Dans le tableau de bord Azure information protection **** \> , sélectionnez **étiquettes**classifications. <br/>![Étiquettes standard pour Azure information protection.](media/AIPLabels.png)

2. Vous pouvez choisir n’importe quelle étiquette pour afficher les options, vous pouvez modifier le nom d’affichage, les couleurs, etc.
 
3. Pour créer les vôtres, consultez la rubrique [Modify and Create New labels](https://docs.microsoft.com/azure/information-protection/infoprotect-tutorial-step2) . 

### <a name="install-the-azure-information-protection-client-manually"></a>Installation manuelle du client Azure information protection

Pour installer manuellement le client AIP:

1. Téléchargez **AzInfoProtection. exe** à partir du [Centre de téléchargement Microsoft](https://www.microsoft.com/download/details.aspx?id=53018).
 
2. Vous pouvez vérifier que l’installation a fonctionné en affichant un document Word et en vous assurant que l’option **protéger** est disponible sous l’onglet **Accueil** . <br/>![Onglet protection dans un document Word.](media/Word_Protect.png)

Pour plus d’informations, consultez [la rubrique installer le client](https://docs.microsoft.com/azure/information-protection/infoprotect-tutorial-step3).
