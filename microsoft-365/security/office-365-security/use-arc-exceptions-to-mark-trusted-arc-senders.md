---
title: Utiliser des expéditeurs ARC approuvés pour les appareils et services légitimes entre l’expéditeur et le récepteur
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: high
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
description: La chaîne de réception authentifiée (ARC) est une authentification par e-mail qui tente de préserver les résultats de l’authentification sur les appareils et les flux de courriers indirects qui se présentent entre l’expéditeur et le destinataire. Voici comment créer des exceptions pour vos expéditeurs ARC approuvés.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 7523a17eb8440d6b567d0414b63153bfc33338a2
ms.sourcegitcommit: 7e551fa4e9b8b25ed62b5f406143b6b1dae08cbf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2022
ms.locfileid: "67107302"
---
# <a name="make-a-list-of-trusted-arc-senders-to-trust-legitimate-indirect-mailflows"></a>Créer une liste d’expéditeurs ARC approuvés pour approuver des flux de courriers indirects *légitimes*

**S’applique à**

- Exchange Online Protection
- Microsoft Defender pour Office 365 : offre 1 et offre 2
- Microsoft 365 Defender

Les mécanismes d’authentification des e-mails tels que [Sender Policy Framework (SPF)](set-up-spf-in-office-365-to-help-prevent-spoofing.md), [DomainKeys Identified Mail (DKIM)](use-dkim-to-validate-outbound-email.md), [Domain-based Message Authentication, Reporting, and Conformance (DMARC)](use-dmarc-to-validate-email.md) sont utilisés pour vérifier la *sécurité* des expéditeurs de courriers électroniques, mais certains services légitimes peuvent apporter des modifications à l’e-mail entre l’expéditeur et le destinataire. **Dans Microsoft 365 Defender, ARC permet de réduire les échecs de remise SPF, DKIM et DMARC qui se produisent en raison de flux de courriers indirects *légitimes*.**

## <a name="authenticated-received-chain-arc-in-microsoft-365-defender-for-office"></a>Chaîne de réception authentifiée (ARC) dans Microsoft 365 Defender pour Office

Les services qui modifient le contenu pendant le transport du message avant la remise à votre organisation peuvent invalider la signature e-mail DKIM et affecter l’authentification du message. Lorsque ces services intermédiaires effectuent de telles actions, ils peuvent utiliser ARC pour fournir des détails sur l’authentification d’origine avant que les modifications ne se produisent, que votre organisation peut ensuite approuver pour vous aider à authentifier le message.  

**Les sealers ARC approuvés permettent aux administrateurs d’ajouter une liste d’intermédiaires *approuvés* dans le portail Microsoft 365 Defender.** Les sealers ARC approuvés permettent à Microsoft d’honorer les signatures ARC de ces intermédiaires approuvés, ce qui empêche ces messages légitimes d’échouer dans la chaîne d’authentification.

> [!NOTE]
> ***Les sealers ARC approuvés sont une liste créée par l’administrateur des domaines intermédiaires qui ont implémenté le sealing ARC.*** Lorsqu’un e-mail est acheminé vers Office 365 et l’intermédiaire approuvé ARC du client Office 365, Microsoft Corporation valide la signature ARC et, en fonction des résultats arc, peut respecter les détails d’authentification fournis.

## <a name="when-to-use-trusted-arc-sealers"></a>Quand utiliser des sealers ARC approuvés?

Une liste de sealers ARC approuvés est nécessaire uniquement lorsque les intermédiaires font partie du flux de messagerie d’une organisation et :

1. Peut modifier l’en-tête ou le contenu de l’e-mail.
2. Peut entraîner l’échec de l’authentification pour d’autres raisons (par exemple, en supprimant des pièces jointes).
 
En ajoutant un sealer ARC approuvé, Office 365 validera et approuvera les résultats d’authentification que le sealer fournit lors de la remise du courrier à votre locataire dans Office 365.

**Les administrateurs doivent ajouter *uniquement des services légitimes* en tant que sealers ARC approuvés.** L’ajout de seuls services que l’organisation utilise et connaît expressément aidera les messages qui doivent d’abord passer par un service pour passer des vérifications d’authentification par e-mail et empêcher l’envoi de messages légitimes au *courrier indésirable* en raison d’échecs d’authentification.

## <a name="steps-to-add-a-trusted-arc-sealer-to-microsoft-365-defender"></a>Étapes d’ajout d’un sealer ARC approuvé à Microsoft 365 Defender

Les sealers ARC approuvés dans le portail Microsoft 365 Defender affichent tous les sealers ARC reconnus et ajoutés à votre client.

**Pour ajouter un nouveau sealer Trusted ARC dans le portail d’administration :**

1. Accédez à la page [des paramètres d’authentification par e-mail](https://security.microsoft.com/authentication?viewid=ARC) .

2. Si c’est la première fois que vous ajoutez un sealer ARC approuvé, cliquez sur le bouton Ajouter.
3. Ajoutez des sealers ARC approuvés dans la zone de texte affichée.
    1. Notez que vous ajoutez les domaines (exemple fabrikam.com).
    1. Le nom de domaine que vous entrez ici *doit* correspondre au domaine indiqué dans la balise de domaine 'd' dans ARC-Seal et les en-têtes ARC-Message-Signature (sur les en-têtes de messagerie du message).
    1. Vous pouvez les voir dans les propriétés du message dans Outlook.

## <a name="steps-to-validate-your-trusted-arc-sealer"></a>Étapes de validation de votre sealer ARC approuvé

S’il existe un joint ARC d’un tiers avant que le message n’atteigne Microsoft 365 Defender, **vérifiez les en-têtes une fois l’e-mail reçu et affichez les derniers en-têtes ARC**.

Dans le dernier ***ARC-Authentication-Results header** _, vérifiez si la validation ARC est répertoriée comme _*pass**.

Un en-tête ARC qui répertorie une 'oda' de 1 indique que l’ARC précédent a été *vérifié*, que le sealer ARC précédent est *approuvé* et que *le résultat de passage* précédent peut être utilisé pour remplacer l’échec DMARC actuel.

**En-tête de passe ARC montrant oda=1**

Consultez les méthodes d’authentification par e-mail à la fin de ce bloc d’en-tête pour le résultat oda.

``
ARC-Authentication-Results: i=2; mx.microsoft.com 1; spf=pass (sender ip is
40.107.65.78) smtp.rcpttodomain=microsoft.com
smtp.mailfrom=sampledoamin.onmicrosoft.com; dmarc=bestguesspass action=none
header.from=sampledoamin.onmicrosoft.com; dkim=none (message not signed);
arc=pass (0 oda=1 ltdi=1
spf=[1,1,smtp.mailfrom=sampledoamin.onmicrosoft.com]
dkim=[1,1,header.d=sampledoamin.onmicrosoft.com]
dmarc=[1,1,header.from=sampledoamin.onmicrosoft.com])
``

Pour vérifier si le résultat ARC a été utilisé pour remplacer un échec DMARC, recherchez le résultat *de compauth* et une *raison de code(130)* dans l’en-tête.

Consultez la dernière entrée de ce bloc d’en-tête pour trouver *compauth* et *raison*.

``
Authentication-Results: spf=fail (sender IP is 51.163.158.241)
smtp.mailfrom=contoso.com; dkim=fail (body hash did not verify)
header.d=contoso.com;dmarc=fail action=none
header.from=contoso.com;compauth=pass reason=130
``

## <a name="powershell-steps-to-add-or-remove-a-trusted-arc-sealer"></a>Étapes PowerShell pour ajouter ou supprimer un sealer ARC approuvé

**Les administrateurs peuvent également configurer des configurations ARC avec Exchange Online PowerShell.**

1. Connectez-vous à Exchange Online PowerShell.
2. Connect-ExchangeOnline
3. Pour ajouter ou mettre à jour un domaine dans un sealer ARC approuvé :
</br>
``
Set-ArcConfig -Identity default -ArcTrustedSealers {a list of arc signing domains split by comma}
``
</br>ou</br>
``
Set-ArcConfig -Identity {tenant name/tenanid}\default -ArcTrustedSealers {a list of arc signing domains split by comma}
``
</br>Vous devez fournir le paramètre d’identité *-Identity* par défaut lors de l’exécution de *Set-ArcConfig*. Les sealers approuvés doivent être mis en correspondance avec la valeur de la balise 'd' dans *l’en-tête ARC-Seal*.

4. Affichez les sealers ARC approuvés :
</br>
``
Get-ArcConfig
`` ou ``
Get-ArcConfig - Organization {tenant name}
``

## <a name="trusted-arc-sealer-mailflow-graphics"></a>Graphiques de flux de courrier du sealer ARC approuvé

Ces diagrammes comparent les opérations de flux de courriers avec et sans sealer ARC approuvé, lors de l’utilisation d’une authentification par e-mail SPF, DKIM et DMARC. Dans les deux graphiques, il existe des services légitimes utilisés par l’entreprise qui doivent intervenir dans le flux de courriers, violant parfois les normes d’authentification par e-mail en modifiant l’envoi d’adresses IP et en écrivant dans l’en-tête de messagerie. **Dans le premier cas, le trafic de flux de courrier indirect illustre le résultat *avant* que les administrateurs n’ajoutent un sealer ARC approuvé.**

:::image type="content" source="../../media/m365d-indirect-traffic-flow-without-trusted-arc-sealer.PNG" alt-text="Dans ce graphique, Contoso publie SPF, DKIM et DMARC dans le cadre de la sécurité de messagerie standard. Un expéditeur utilisant SPF envoie le courrier de l’intérieur de contoso.com à fabrikam.com, et ce courrier passe par un service tiers que Contoso a embauché, et ce service modifie l’adresse IP d’envoi dans l’en-tête de messagerie. Le message échoue SPF en raison de l’adresse IP modifiée et DKIM, car le contenu a été modifié par un tiers, lors de la vérification DNS sur EOP. DMARC échoue en raison des échecs SPF et DKIM. Le message est envoyé au courrier indésirable, en quarantaine ou rejeté.":::

Ici, vous voyez la même organisation **après avoir su créer un sealer ARC approuvé.**

:::image type="content" source="../../media/m365d-indirect-traffic-flow-with-trusted-arc-sealer.PNG" alt-text="Dans le deuxième graphique, la société Contoso avait créé une liste de sealers ARC approuvés. Le même utilisateur envoie un deuxième courrier de contoso.com à fabrikam.com. Le service tiers embauché par Contoso modifie l’adresse IP de l’expéditeur dans l’en-tête du courrier. Mais cette fois, le service a implémenté le sealing ARC, et étant donné que l’administrateur du locataire a déjà ajouté le domaine du tiers aux sealers ARC approuvés, la modification est acceptée. SPF échoue pour la nouvelle adresse IP. DKIM échoue en raison de la modification du contenu. DMARC échoue en raison des échecs antérieurs. Mais ARC reconnaît les modifications, émet une passe et accepte les modifications. L’usurpation d’identité reçoit également une passe. Le message est envoyé à la boîte de réception.":::

## <a name="next-steps-after-you-set-up-arc-for-microsoft-365-defender-for-office"></a>Étapes suivantes : Après avoir configuré ARC pour Microsoft 365 Defender pour Office

Après l’installation, vérifiez vos en-têtes ARC avec [l’analyseur d’en-tête de message](https://mha.azurewebsites.net).

Passez en revue les étapes de configuration [SPF](set-up-spf-in-office-365-to-help-prevent-spoofing.md), [DKIM](use-dkim-to-validate-outbound-email.md) et [DMARC](use-dmarc-to-validate-email.md).
