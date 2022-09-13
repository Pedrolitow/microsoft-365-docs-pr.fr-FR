---
title: Créer des signatures et des exclusions de responsabilité à l’échelle de l’organisation
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
- highpri
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- VSBFY23
- TRN_M365B
- OKR_SMB_Videos
- seo-marvel-may2020
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- adminvideo
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 2d75860f-c527-4352-a7f6-73eba54c0c72
description: Gérez les signatures par e-mail, y compris les clauses d’exclusion de responsabilité légales ou les déclarations de divulgation pour tous les messages électroniques qui entrent ou quittent votre organisation.
ms.openlocfilehash: 7eebd09d675ec4186a1aeac526176c627367efd4
ms.sourcegitcommit: 37e137535c4f70702afe1a5eeaa899c75ee02cfd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2022
ms.locfileid: "67663342"
---
# <a name="create-organization-wide-signatures-and-disclaimers"></a>Créer des signatures et des exclusions de responsabilité à l’échelle de l’organisation

Consultez [l’aide de Microsoft 365 petite entreprise](https://go.microsoft.com/fwlink/?linkid=2197659) sur YouTube.

 Vous pouvez gérer les signatures par e-mail en ajoutant une signature par e-mail, une clause d’exclusion de responsabilité légale ou une déclaration de divulgation aux messages électroniques qui entrent ou quittent votre organisation. Vous pouvez configurer celle-ci pour qu'elle s'applique à tous les messages entrants et sortants, comme illustré ci-dessous. Ou vous pouvez l'appliquer à certains messages, comme ceux contenant des mots ou des modèles de texte spécifiques.

## <a name="watch-create-a-company-wide-email-signature"></a>Regarder : Créer une signature électronique à l’échelle de l’entreprise
  
Regardez cette vidéo et d’autres encore sont disponibles sur notre [chaîne YouTube](https://go.microsoft.com/fwlink/?linkid=2198031).

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1IEWf] 

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d'administration Microsoft 365</a>, sélectionnez **Exchange**.
1. Sélectionnez **Flux de messagerie**.
1. Sélectionnez **Ajouter +**, puis **Appliquer les exclusions de responsabilité**.
1. Dans la page **Nouvelle règle** , effectuez les étapes. 

Si vous avez trouvé cette vidéo utile, consultez les [séries de formations complètes pour les petites entreprises et les nouveaux utilisateurs de Microsoft 365](../../business-video/index.yml).

## <a name="create-a-signature-that-applies-to-all-messages"></a>Créer une signature qui s'applique à tous les messages

> [!TIP]
> Les signatures à l’échelle de l’organisation sont appelées « clauses d’exclusion de responsabilité », indépendamment de ce qu’elles incluent. Par exemple, il peut s’agir simplement d’une signature, ou également d’une adresse, d’une clause d’exclusion de responsabilité légale ou d’autres informations souhaitées.
    
::: moniker range="o365-worldwide"

Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

::: moniker-end

::: moniker range="o365-21vianet"

Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">https://portal.partner.microsoftonline.cn/adminportal</a>.

::: moniker-end

1. Sélectionnez le lanceur ![d’applications L’icône](../../media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) du lanceur d’applications, puis sélectionnez **Administration**.
   
    Vous ne trouvez pas l'application que vous cherchez ? Dans le lanceur d’applications, sélectionnez **Toutes les applications** pour afficher une liste alphabétique des applications disponibles. À partir de là, vous pouvez rechercher une application spécifique. 
    
2. Sélectionnez **Administration centres**, puis choisissez **Exchange**.
    
3. Sous Flux de messagerie, sélectionnez **Règles**.
    
4. Sélectionnez l’icône **+** (Ajouter), puis **choisissez Appliquer les exclusions de responsabilité**.
    
5. Attribuez un nom à la règle.
    
6. Sous **Appliquer cette règle**, **sélectionnez [Appliquer à tous les messages]**.
    
    > [!TIP]
    > [Découvrez-en plus](/Exchange/policy-and-compliance/mail-flow-rules/signatures#Scoping) sur l'application de conditions si vous ne souhaitez pas appliquer l'exclusion de responsabilité à tous les messages. (Cet article d’étendue concerne Exchange Server, mais il s’applique également à Microsoft 365.) 
  
7. Sous Effectuer les opérations suivantes, laissez **Ajouter l'exclusion de responsabilité** sélectionné. 
    
8.  Sélectionnez **Entrer du texte** et tapez votre exclusion de responsabilité. 
    
    > [!TIP]
    > [Découvrez-en plus](/Exchange/policy-and-compliance/mail-flow-rules/signatures#FormatDisclaimer) sur la mise en forme des exclusions de responsabilité. (Cet article de mise en forme concerne Exchange Server, mais il s’applique également à Microsoft 365.) 

9. **Sélectionnez Sélectionner un** et **choisissez Wrap** comme option de secours. Sélectionnez **OK**. Ainsi, si l'exclusion de responsabilité ne peut pas être ajoutée parce que le chiffrement ou un autre paramètre de courrier est activé, elle sera encapsulée dans une enveloppe du message.
    
10. Laissez **Auditer cette règle avec un niveau de gravité** sélectionné. Puis sélectionnez le niveau à utiliser dans le journal des messages : **Faible**, **Moyen** ou **Élevé**. 
    
11. Sélectionnez **Appliquer** pour activer immédiatement l'exclusion de responsabilité, sauf si vous souhaitez la tester au préalable. 
    
12. Sélectionnez **Autres options** pour inclure d'autres conditions ou exceptions. 
    
13. Sélectionnez **Enregistrer** lorsque vous avez terminé. 
    
## <a name="limitations-of-organization-wide-signatures"></a>Limitations des signatures à l’échelle de l’organisation

Vous ne pouvez pas effectuer les opérations suivantes lors de la gestion des signatures électroniques dans Microsoft 365 :
  
- Insérer la signature directement sous la dernière réponse par e-mail ou transfert
    
- Afficher les signatures de courrier côté serveur dans les dossiers Éléments envoyés des utilisateurs
    
- Incorporer des images dans des signatures par e-mail
    
- Ignorer les lignes qui contiennent des variables qui n’ont pas pu être mises à jour (par exemple, parce que la valeur n’a pas été fournie pour un utilisateur)
    
Pour obtenir ces fonctionnalités et d’autres pour gérer les signatures par e-mail, utilisez un outil tiers. Effectuez une recherche sur Internet du **logiciel de signature par e-mail**. Un certain nombre de ces fournisseurs sont des partenaires Microsoft Gold et leurs logiciels fournissent ces fonctionnalités. 
  
## <a name="more-resources"></a>Plus de ressources

Pour plus d’informations sur l’utilisation de PowerShell, consultez les [clauses d’exclusion de responsabilité, les signatures, les pieds de page ou les en-têtes à l’échelle de l’organisation dans Exchange Online](/exchange/security-and-compliance/mail-flow-rules/disclaimers-signatures-footers-or-headers).

## <a name="related-content"></a>Contenu associé

[Migrer le courrier électronique et les contacts vers Microsoft 365](migrate-email-and-contacts-admin.md) (vidéo)\
[Paramètres de messagerie](../email/office-365-user-email-settings.md) utilisateur (article)\
[Aperçu du centre d'administration de Microsoft 365](Overview of the Microsoft 365 admin center](../admin-overview/admin-center-overview.md) (vidéo)

