---
title: Créer des signatures à l’échelle de l’organisation et des clauses d’exclusion de responsabilité
f1.keywords:
- NOCSH
ms.author: twerner
author: twernermsft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- TRN_M365B
- OKR_SMB_Videos
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 2d75860f-c527-4352-a7f6-73eba54c0c72
description: Apprenez à ajouter une signature électronique, une clause d’exclusion de responsabilité ou une déclaration de divulgation à tous les messages électroniques qui entrent ou sortent de votre organisation.
ms.openlocfilehash: a63f21dff90c70d39e3709d4c34b53d99a315a59
ms.sourcegitcommit: 812aab5f58eed4bf359faf0e99f7f876af5b1023
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2020
ms.locfileid: "42360665"
---
# <a name="create-organization-wide-signatures-and-disclaimers"></a>Créer des signatures à l’échelle de l’organisation et des clauses d’exclusion de responsabilité

 [] Vous pouvez ajouter une signature électronique, une clause d'exclusion de responsabilité ou une déclaration de divulgation aux messages e-mail qui entrent dans votre organisation ou qui en sortent. Vous pouvez configurer celle-ci pour qu'elle s'applique à tous les messages entrants et sortants, comme illustré ci-dessous. Ou vous pouvez l'appliquer à certains messages, comme ceux contenant des mots ou des modèles de texte spécifiques.

 Regardez une courte vidéo sur la création d’une signature électronique à l’échelle de l’entreprise. <br><br>
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1IEWf] 

Si vous avez trouvé cette vidéo utile, consultez les [séries de formations complètes pour les petites entreprises et les nouveaux utilisateurs de Microsoft 365](https://support.office.com/article/6ab4bbcd-79cf-4000-a0bd-d42ce4d12816).

## <a name="create-a-signature-that-applies-to-all-messages"></a>Créer une signature qui s'applique à tous les messages

> [!TIP]
> Les signatures à l’échelle de l’organisation sont appelées « clauses d’exclusion de responsabilité », indépendamment de ce qu’elles incluent. Par exemple, il peut s’agir d’une signature ou de votre adresse, de la clause d’exclusion de responsabilité ou d’autres informations que vous souhaitez.
    
::: moniker range="o365-worldwide"

Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

::: moniker-end

::: moniker range="o365-germany"

Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=848041" target="_blank">https://portal.office.de/adminportal</a>.

::: moniker-end

::: moniker range="o365-21vianet"

Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">https://portal.partner.microsoftonline.cn/adminportal</a>.

::: moniker-end

1. Sélectionnez l’icône ![du lanceur d’applications dans le lanceur d’applications dans Office 365](../../media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png), puis sélectionnez **administrateur**.
   
    Vous ne trouvez pas l’application que vous cherchez ? Dans le Lanceur d’applications, sélectionnez **Toutes les applications** pour afficher une liste alphabétique des applications Office 365 disponibles. À partir de là, vous pouvez rechercher une application spécifique. 
    
2. Sélectionnez **centres d’administration**, puis **Exchange**.
    
3. Sous flux de messagerie, sélectionnez **règles**.
    
4. Sélectionnez l' **+** icône (ajouter), puis **appliquer les clauses d’exclusion de responsabilité**.
    
5. Attribuez un nom à la règle.
    
6. Sous **appliquer cette règle**, sélectionnez **[appliquer à tous les messages]**.
    
    > [!TIP]
    > [Découvrez-en plus](https://docs.microsoft.com/Exchange/policy-and-compliance/mail-flow-rules/signatures#Scoping) sur l'application de conditions si vous ne souhaitez pas appliquer l'exclusion de responsabilité à tous les messages. (Cet article de portée est destiné à Exchange Server, mais il s’applique également à Office 365.) 
  
7. Sous Effectuer les opérations suivantes, laissez **Ajouter l'exclusion de responsabilité** sélectionné. 
    
8.  Sélectionnez **entrer le texte** et tapez votre clause d’exclusion de responsabilité. 
    
    > [!TIP]
    > [Découvrez-en plus](https://docs.microsoft.com/Exchange/policy-and-compliance/mail-flow-rules/signatures#FormatDisclaimer) sur la mise en forme des exclusions de responsabilité. (Cet article de mise en forme est destiné à Exchange Server, mais il s’applique également à Office 365.) 

9. Sélectionnez **Sélectionner un** et sélectionnez **renvoyer** en tant qu’option de secours. Sélectionnez **OK**. Ainsi, si l'exclusion de responsabilité ne peut pas être ajoutée parce que le chiffrement ou un autre paramètre de courrier est activé, elle sera encapsulée dans une enveloppe du message.
    
10. Laissez **Auditer cette règle avec un niveau de gravité** sélectionné. Puis sélectionnez le niveau à utiliser dans le journal des messages : **Faible**, **Moyen** ou **Élevé**. 
    
11. Sélectionnez **Appliquer** pour activer immédiatement l'exclusion de responsabilité, sauf si vous souhaitez la tester au préalable. 
    
12. Sélectionnez **Autres options** pour inclure d'autres conditions ou exceptions. 
    
13. Sélectionnez **Enregistrer** lorsque vous avez terminé. 
    
## <a name="limitations-of-office-365-organization-wide-signatures"></a>Limitations des signatures larges de l’organisation Office 365

Vous ne pouvez pas effectuer les opérations suivantes avec les signatures Office 365 :
  
- Insérer la signature directement sous la dernière adresse de courrier ou de transfert
    
- Afficher les signatures électroniques côté serveur dans les dossiers éléments envoyés des utilisateurs
    
- Incorporer des images dans les signatures de courrier électronique
    
- Ignorer les lignes qui contiennent des variables qui n’ont pas pu être mises à jour (par exemple, parce que la valeur n’a pas été fournie pour un utilisateur)
    
Pour bénéficier de ces fonctionnalités et d’autres fonctionnalités, utilisez un outil tiers. Veuillez effectuer une recherche sur Internet pour le **logiciel de signature électronique**. Un certain nombre de ces fournisseurs sont des partenaires Microsoft Gold et leurs logiciels fournissent ces fonctionnalités. 
  
## <a name="more-resources"></a>Autres ressources

- Pour plus d’informations sur l’utilisation de PowerShell, consultez la rubrique relative aux [clauses d’exclusion de responsabilité, signatures, pieds de page ou en-têtes de message à l’échelle de l’organisation dans Office 365](https://docs.microsoft.com/exchange/security-and-compliance/mail-flow-rules/disclaimers-signatures-footers-or-headers) . 
    

