---
title: Créer des signatures et des clauses d’exclusion de responsabilité à l’échelle de l’organisation
f1.keywords:
- NOCSH
ms.author: twerner
author: twernermsft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- TRN_M365B
- OKR_SMB_Videos
- seo-marvel-may2020
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 2d75860f-c527-4352-a7f6-73eba54c0c72
description: Gérez les signatures électroniques, y compris les clauses d’exclusion de responsabilité juridiques ou les déclarations de divulgation pour tous les messages électroniques entrants ou qui quittent votre organisation.
ms.openlocfilehash: 566cf595365a578f0e92d7e41e8ed7c7764c0cf4
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60197797"
---
# <a name="create-organization-wide-signatures-and-disclaimers"></a>Créer des signatures et des clauses d’exclusion de responsabilité à l’échelle de l’organisation

 Vous pouvez gérer les signatures électroniques en ajoutant une signature électronique, une clause d’exclusion de responsabilité juridique ou une déclaration de divulgation aux messages électroniques qui entrent dans votre organisation ou en quittent. Vous pouvez configurer celle-ci pour qu'elle s'applique à tous les messages entrants et sortants, comme illustré ci-dessous. Ou vous pouvez l'appliquer à certains messages, comme ceux contenant des mots ou des modèles de texte spécifiques.

## <a name="watch-create-a-company-wide-email-signature"></a>Regarder : Créer une signature électronique à l’échelle de l’entreprise
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1IEWf] 

Si vous avez trouvé cette vidéo utile, consultez les [séries de formations complètes pour les petites entreprises et les nouveaux utilisateurs de Microsoft 365](../../business-video/index.yml).

## <a name="create-a-signature-that-applies-to-all-messages"></a>Créer une signature qui s'applique à tous les messages

> [!TIP]
> Les signatures à l’échelle de l’organisation sont appelées « clauses d’exclusion de responsabilité », indépendamment de ce qu’elles incluent. Par exemple, il peut s’agir simplement d’une signature ou inclure votre adresse, une clause d’exclusion de responsabilité juridique ou d’autres informations de votre part.
    
::: moniker range="o365-worldwide"

Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

::: moniker-end

::: moniker range="o365-germany"

Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=848041" target="_blank">https://portal.office.de/adminportal</a>.

::: moniker-end

::: moniker range="o365-21vianet"

Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">https://portal.partner.microsoftonline.cn/adminportal</a>.

::: moniker-end

1. Sélectionnez le lanceur d’applications ![ L’icône du lanceur d’applications, ](../../media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) puis sélectionnez **Administrateur.**
   
    Vous ne trouvez pas l'application que vous cherchez ? Dans le lanceur d’applications, sélectionnez **Toutes les applications** pour voir une liste alphabétique des applications à votre disposition. À partir de là, vous pouvez rechercher une application spécifique. 
    
2. Sélectionnez **Centres d’administration,** puis **sélectionnez Exchange**.
    
3. Sous Flux de messagerie, sélectionnez **Règles.**
    
4. Sélectionnez **+** l’icône (Ajouter) et choisissez **Appliquer les clauses d’exclusion de responsabilité.**
    
5. Attribuez un nom à la règle.
    
6. Sous **Appliquer cette règle,** **sélectionnez [Appliquer à tous les messages]**.
    
    > [!TIP]
    > [Découvrez-en plus](/Exchange/policy-and-compliance/mail-flow-rules/signatures#Scoping) sur l'application de conditions si vous ne souhaitez pas appliquer l'exclusion de responsabilité à tous les messages. (Cet article s’applique aux Exchange Server, mais il s’applique également aux Microsoft 365.) 
  
7. Sous Effectuer les opérations suivantes, laissez **Ajouter l'exclusion de responsabilité** sélectionné. 
    
8.  Sélectionnez **Entrer du texte** et tapez votre clause d’exclusion de responsabilité. 
    
    > [!TIP]
    > [Découvrez-en plus](/Exchange/policy-and-compliance/mail-flow-rules/signatures#FormatDisclaimer) sur la mise en forme des exclusions de responsabilité. (Cet article de mise en forme est Exchange Server, mais il s’applique également à Microsoft 365.) 

9. **Sélectionnez-en un** et **choisissez Wrap** en tant qu’option de retour. Sélectionnez **OK**. Ainsi, si l'exclusion de responsabilité ne peut pas être ajoutée parce que le chiffrement ou un autre paramètre de courrier est activé, elle sera encapsulée dans une enveloppe du message.
    
10. Laissez **Auditer cette règle avec un niveau de gravité** sélectionné. Puis sélectionnez le niveau à utiliser dans le journal des messages : **Faible**, **Moyen** ou **Élevé**. 
    
11. Sélectionnez **Appliquer** pour activer immédiatement l'exclusion de responsabilité, sauf si vous souhaitez la tester au préalable. 
    
12. Sélectionnez **Autres options** pour inclure d'autres conditions ou exceptions. 
    
13. Sélectionnez **Enregistrer** lorsque vous avez terminé. 
    
## <a name="limitations-of-organization-wide-signatures"></a>Limitations des signatures à l’échelle de l’organisation

Vous ne pouvez pas faire les choses suivantes lors de la gestion des signatures électroniques dans Microsoft 365 :
  
- Insérez la signature directement sous la dernière réponse ou envoi d’e-mail
    
- Afficher les signatures de courrier côté serveur dans les dossiers Éléments envoyés des utilisateurs
    
- Incorporer des images dans des signatures électroniques
    
- Ignorer les lignes qui contiennent des variables qui n’ont pas pu être mises à jour (par exemple, parce que la valeur n’a pas été fournie pour un utilisateur)
    
Pour obtenir ces fonctionnalités et d’autres fonctionnalités de gestion des signatures électroniques, utilisez un outil tiers. Veuillez effectuer une recherche sur Internet pour le logiciel **de signature électronique.** Un certain nombre de ces fournisseurs sont des partenaires Microsoft Gold et leurs logiciels fournissent ces fonctionnalités. 
  
## <a name="more-resources"></a>Plus de ressources

Pour plus d’informations sur l’utilisation de PowerShell, voir les clauses d’exclusion de [responsabilité, les signatures,](/exchange/security-and-compliance/mail-flow-rules/disclaimers-signatures-footers-or-headers)les pieds de bas de gamme ou les en-têtes de message à l’échelle de l’Exchange Online .

## <a name="related-content"></a>Contenu associé

[Migrer le courrier électronique et les contacts vers Microsoft 365](migrate-email-and-contacts-admin.md) (vidéo)\
[Paramètres de messagerie de l’utilisateur](../email/office-365-user-email-settings.md) (article)\
[Vue d’ensemble du centre d’administration Microsoft 365](../../business-video/admin-center-overview.md) (vidéo)

