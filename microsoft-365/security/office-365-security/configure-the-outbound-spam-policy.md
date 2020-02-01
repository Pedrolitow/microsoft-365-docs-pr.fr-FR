---
title: Configurer la stratégie anti-courrier indésirable sortant
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 10/02/2019
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: a44764e9-a5d2-4c67-8888-e7fb871c17c7
ms.collection:
- M365-security-compliance
description: Le filtrage du courrier indésirable sortant est toujours activé si vous utilisez le service pour l’envoi de messages sortants, ce qui permet de protéger les organisations utilisant le service ainsi que leurs destinataires.
ms.openlocfilehash: c17772db2a2961cade180a5c1e0403ae8450007f
ms.sourcegitcommit: 1c91b7b24537d0e54d484c3379043db53c1aea65
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "41599561"
---
# <a name="configure-the-outbound-spam-policy"></a>Configurer la stratégie anti-courrier indésirable sortant

Le filtrage du courrier indésirable sortant est toujours activé si vous utilisez le service pour l’envoi de messages sortants, ce qui permet de protéger les organisations utilisant le service ainsi que leurs destinataires. Tout comme le filtrage entrant, le filtrage du courrier indésirable sortant comprend le filtrage des connexions et le filtrage du contenu et permet à certains contrôles spécifiques de gérer les messages sortants. Types de paramètres de stratégie de filtrage du courrier indésirable sortant :

- Valeur par défaut : la stratégie de filtrage du courrier indésirable sortant par défaut est utilisée pour configurer les paramètres de filtrage du courrier indésirable sortant à l’échelle de l’entreprise. Cette stratégie ne peut pas être renommée et est toujours activée.

- Personnalisé : les stratégies personnalisées de filtrage du courrier indésirable sortant peuvent être granulaires et appliquées à des utilisateurs, des groupes ou des domaines spécifiques de votre organisation. Les stratégies personnalisées priment toujours sur la stratégie par défaut. Vous pouvez modifier l’ordre dans lequel vos stratégies personnalisées s’exécutent en modifiant la priorité de chaque stratégie personnalisée ; Toutefois, seule la stratégie dont la priorité est la plus élevée (par exemple, le nombre le plus proche de 0) s’applique si l’utilisateur correspond à plusieurs stratégies.

> [!NOTE]
> Pour plus d’informations sur les [contrôles de courrier indésirable sortants dans Office 365](https://docs.microsoft.com/office365/securitycompliance/outbound-spam-controls). <br><br> Les mises à jour de la stratégie de courrier indésirable sortant sont en cours de déploiement, avec la mise à jour attendue terminée à la fin du 2019 octobre. Pendant ce temps, certaines options ne seront peut-être pas disponibles.  Pour plus d’informations, consultez la feuille de [route Office 365](https://www.microsoft.com/microsoft-365/roadmap?featureid=54125) 

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer
<a name="sectionSection0"> </a>

Durée d’exécution estimée : 5 minutes

Des autorisations doivent vous être attribuées avant de pouvoir exécuter cette procédure. Pour voir les autorisations qui vous sont nécessaires, consultez l'entrée « Anti-spam » dans la rubrique [Autorisations des fonctionnalités dans Exchange Online](https://docs.microsoft.com/exchange/permissions-exo/feature-permissions).

La procédure suivante peut également être exécutée via le service PowerShell à distance. Utilisez la cmdlet [Get-HostedOutboundSpamFilterPolicy](https://docs.microsoft.com/powershell/module/exchange/antispam-antimalware/get-hostedoutboundspamfilterpolicy) pour vérifier vos paramètres et la cmdlet [Set-HostedOutboundSpamFilterPolicy](https://docs.microsoft.com/powershell/module/exchange/antispam-antimalware/set-hostedoutboundspamfilterpolicy) pour modifier les paramètres de votre stratégie anti-courrier indésirable sortant. Pour apprendre à utiliser Windows PowerShell afin d’établir une connexion à Exchange Online Protection, voir [Connexion à Exchange Online Protection à l’aide de Remote PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-eop/connect-to-exchange-online-protection-powershell). Pour apprendre à utiliser Windows PowerShell afin de vous connecter à Exchange Online, consultez la rubrique [Connexion à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).

## <a name="use-the-security-and-compliance-center-scc-to-edit-the-default-outbound-spam-policy"></a>Utiliser le centre de sécurité et de conformité (SCC) pour modifier la stratégie de courrier indésirable sortant par défaut

La procédure suivante vous permet de modifier la stratégie de courrier indésirable sortant par défaut :

### <a name="to-configure-the-default-outbound-spam-policy"></a>Pour configurer la stratégie de courrier indésirable sortant par défaut

1. Dans le SCC, accédez à **protection contre le courrier indésirable** de la **stratégie** \> de **gestion** \> des menaces

2. Développez la section **stratégie de filtrage du courrier indésirable sortant (toujours active)** , puis cliquez sur **modifier la stratégie**.

3. Développez la section **notifications** et activez les cases à cocher suivantes relatives aux messages sortants, puis sélectionnez **Ajouter des personnes** pour ajouter une ou plusieurs adresses de messagerie associées dans la boîte de dialogue associée. (il peut s’agir de listes de distribution si elles sont résolues en tant que destinations SMTP valides) :

   - **Envoyer une copie de tous les messages électroniques sortants suspects à l’adresse ou aux adresses de messagerie suivantes**: ce sont des messages marqués comme courrier indésirable par le filtre (quelle que soit la valeur de contrôle d’accès SCL). Le filtre ne les rejette pas, mais ils sont routés via le pool de remise à risque plus élevé. S'il y a plusieurs adresses, utilisez un point-virgule pour les séparer. Notez que les destinataires spécifiés recevront les messages en tant qu'adresse Cci (les champs De et À correspondent à l'expéditeur et au destinataire initiaux).

   - **Envoyer une notification à l’adresse de messagerie suivante lorsqu’un expéditeur est bloqué envoyer du courrier indésirable sortant**: séparez les adresses multiples par un point-virgule.

   Lorsqu’une quantité importante de courrier indésirable ou d’autres anomalies d’envoi est détectée à partir d’un utilisateur particulier, l’utilisateur est limité à l’envoi de messages électroniques et une notification est envoyée aux adresses de messagerie spécifiées.

   L'administrateur du domaine, spécifié à l'aide de ce paramètre, est informé que l'envoi de messages sortants est bloqué pour cet utilisateur.  Pour savoir à quoi ressemble cette notification, voir [Exemple de notification lorsqu'un expéditeur est bloqué en raison de l'envoi de courrier indésirable sortant](sample-notification-when-a-sender-is-blocked-sending-outbound-spam.md).

   > [NOTE !] Une alerte système est également générée pour indiquer que l’utilisateur a été restreint.  Pour en savoir plus sur l’alerte et sur la façon de récupérer l’utilisateur, consultez la rubrique [Suppression d’un utilisateur du portail utilisateurs restreints après l’envoi du courrier indésirable](removing-user-from-restricted-users-portal-after-spam.md).

4. Développez la section **limites des destinataires** pour spécifier le nombre maximal de destinataires pouvant être envoyés par un utilisateur, par heure pour les destinataires internes et externes, ainsi que le nombre maximal par jour.

    > [NOTE !] Le nombre maximal de toute entrée est 10 000.  Pour plus d’informations, consultez la rubrique [limites de réception et d’envoi dans Exchange Online](https://docs.microsoft.com/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#receiving-and-sending-limits) .

7. Spécifier l' **action** à effectuer lorsqu’un utilisateur dépasse les limites spécifiées.  Les actions possibles sont les suivantes :
    * **Empêcher l’utilisateur d’envoyer des messages jusqu’à la date suivante**.  Une fois qu’une limite d’envoi a été dépassée (interne, externe ou quotidienne), une alerte est générée pour l’administrateur et l’utilisateur ne peut plus envoyer de courriers électroniques avant le jour suivant, en fonction de l’heure UTC. L’administrateur n’a aucun moyen de remplacer ce bloc.

    * **Empêcher l’utilisateur d’envoyer des messages**.  Une fois qu’une limite d’envoi a été dépassée (interne, externe ou quotidienne), une alerte est générée pour l’administrateur et l’utilisateur ne peut plus envoyer de courriers électroniques tant que l’administrateur n’a pas supprimé la restriction.  Dans ce cas, l’utilisateur est mentionné sur la [page utilisateurs restreints](removing-user-from-restricted-users-portal-after-spam.md).  Une fois supprimé de la liste, l’utilisateur ne sera plus restreint pour ce jour.

    * **Aucune action/alerte uniquement**. Une fois qu’une limite d’envoi a été dépassée (interne, externe ou quotidienne), une alerte est générée pour l’administrateur, mais aucune action n’est effectuée pour limiter l’utilisateur.

6. Développez la section **s’applique à** , puis créez une règle basée sur une condition pour spécifier les utilisateurs, les groupes et les domaines auxquels cette stratégie doit être appliquée. Vous pouvez créer plusieurs conditions pour autant qu'elles soient uniques.  Remarque : les utilisateurs doivent remplir toutes les conditions lorsque plusieurs conditions sont spécifiées.  

      * Pour sélectionner des utilisateurs, sélectionnez **l’expéditeur**. Dans la boîte de dialogue suivante, sélectionnez un ou plusieurs expéditeurs de votre organisation dans la liste du sélecteur, puis cliquez sur Ajouter. Pour ajouter des expéditeurs ne figurant pas dans la liste, entrez leurs adresses de messagerie, puis cliquez sur Vérifier les noms. Une fois les sélections effectuées, cliquez sur OK pour revenir à l'écran principal.

      * Pour sélectionner des groupes, sélectionnez **l’expéditeur est membre de**. Ensuite, dans la boîte de dialogue suivante, sélectionnez ou spécifiez les groupes. Cliquez sur ok pour revenir à l'écran principal.

      * Pour sélectionner des domaines, sélectionnez **le domaine de l’expéditeur**. Ensuite, dans la boîte de dialogue suivante, ajoutez les domaines. Cliquez sur ok pour revenir à l'écran principal.

        Vous pouvez créer des exceptions dans la règle. Par exemple, pour filtrer les messages de tous les domaines, sauf un domaine particulier. Cliquez sur Ajouter une exception, puis créez vos conditions d'exception de la même manière que vous avez créé les autres conditions.

        L’application d’une stratégie de courrier indésirable sortant à un groupe est prise en charge uniquement pour les groupes de sécurité à extension messagerie.

7. Cliquez sur **Enregistrer**.

## <a name="to-create-a-custom-policy-for-a-specific-set-of-users"></a>Pour créer une stratégie personnalisée pour un ensemble spécifique d’utilisateurs
1. Dans le SCC, accédez à **protection contre le courrier indésirable** de la **stratégie** \> de **gestion** \> des menaces

2. Cliquez sur le bouton **créer une stratégie sortante** .

3. Développez la section **notifications** et activez les cases à cocher suivantes relatives aux messages sortants, puis sélectionnez **Ajouter des personnes** pour ajouter une ou plusieurs adresses de messagerie associées dans la boîte de dialogue associée.

4. Développez la section **limites des destinataires** pour spécifier le nombre maximal de destinataires pouvant être envoyés par un utilisateur, par heure pour les destinataires internes et externes et un nombre maximal par jour.

7. Spécifier l' **action** à effectuer lorsqu’un utilisateur dépasse les limites spécifiées.

6. Développez la section **s’applique à** et créez une règle basée sur une condition pour spécifier les utilisateurs, les groupes et les domaines auxquels cette stratégie doit être appliquée. Vous pouvez créer plusieurs conditions pour autant qu'elles soient uniques.  

8. Cliquez sur **Enregistrer**

## <a name="for-more-information"></a>Pour plus d'informations

[Suppression d’un utilisateur du portail Utilisateurs restreints après l’envoi d’un courrier indésirable](https://docs.microsoft.com/office365/SecurityCompliance/removing-user-from-restricted-users-portal-after-spam)

[Pool de remise à haut risque pour les messages sortants](high-risk-delivery-pool-for-outbound-messages.md)

[Forum Aux Questions sur la protection anti-courrier indésirable](anti-spam-protection-faq.md)
