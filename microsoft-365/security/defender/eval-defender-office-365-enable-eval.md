---
title: Activer l’environnement d’évaluation pour Microsoft Defender pour Office 365 dans votre environnement de production
description: Étapes pour activer Microsoft Defender pour Office 365'évaluation, avec des licences d’évaluation, la gestion des enregistrements MX, & l’audit des domaines acceptés et des connexions entrantes.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.date: 09/01/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- m365solution-scenario
- m365solution-evalutatemtp
- zerotrust-solution
- highpri
- tier1
ms.topic: how-to
ms.openlocfilehash: 2bf372cb9836b5565a5e311a17806d6f52d3945a
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68072962"
---
# <a name="enable-the-evaluation-environment"></a>Activer l’environnement d’évaluation

**S’applique à :**
- Microsoft 365 Defender

Cet article est [l’étape 2 sur 3](eval-defender-office-365-overview.md) du processus de configuration de l’environnement d’évaluation pour Microsoft Defender pour Office 365. Pour plus d’informations sur ce processus, consultez [l’article de présentation](eval-defender-office-365-overview.md).

Utilisez les étapes suivantes pour activer l’évaluation de Microsoft Defender pour Office 365.

:::image type="content" source="../../media/defender/m365-defender-office-eval-enable-steps.png" alt-text="Étapes permettant d’activer Microsoft Defender pour Office 365 dans l’environnement d’évaluation Microsoft Defender." lightbox="../../media/defender/m365-defender-office-eval-enable-steps.png":::

- [Étape 1 : Auditer et vérifier l’enregistrement MX public](#step-1-audit-and-verify-the-public-mx-record)
- [Étape 2 : Auditer les domaines acceptés](#step-2-audit-accepted-domains)
- [Étape 3 : Auditer les connecteurs entrants](#step-3-audit-inbound-connectors)
- [Étape 4 : Activer l’évaluation](#step-4-activate-the-evaluation)

## <a name="step-1-audit-and-verify-the-public-mx-record"></a>Étape 1 : Auditer et vérifier l’enregistrement MX public

Pour évaluer efficacement Microsoft Defender pour Office 365, il est important que l’e-mail externe entrant soit relayé via l’instance Exchange Online Protection (EOP) associée à votre locataire.

1. Dans le portail M365 Administration à <https://admin.microsoft.com>, développez *... Affichez tout* si nécessaire, *développez Paramètres*, puis sélectionnez **Domaines**. Ou, pour accéder directement à la page *Domaines* , utilisez <https://admin.microsoft.com/Adminportal/Home#/Domains>.
2. Dans la page *Domaines* , sélectionnez votre domaine de messagerie vérifié en cliquant n’importe où sur l’entrée autre que la case à cocher.
3. Dans le menu volant des détails du domaine qui s’ouvre, sélectionnez l’onglet **Enregistrements DNS** . Notez l’enregistrement MX généré et affecté à votre locataire EOP.
4. Accédez à votre zone DNS externe (publique) et vérifiez l’enregistrement MX principal associé à votre domaine de messagerie :
    - *Si votre enregistrement MX public correspond actuellement à l’adresse EOP affectée (par exemple, contoso-com.mail.protection.outlook.com), aucune autre modification de routage ne doit être requise*.
    - Si votre enregistrement MX public est actuellement résolu en passerelle SMTP tierce ou locale, des configurations de routage supplémentaires peuvent être nécessaires.
    - Si votre enregistrement MX public est actuellement résolu sur Exchange local, vous êtes peut-être toujours dans un modèle hybride où une boîte aux lettres de destinataire n’a pas encore été migrée vers EXO.

## <a name="step-2-audit-accepted-domains"></a>Étape 2 : Auditer les domaines acceptés

1. Dans le Centre d’administration Exchange (EAC), <https://admin.exchange.microsoft.com>développez le *flux de messagerie*, puis cliquez sur **Domaines acceptés**. Ou, pour accéder directement à la page *Domaines acceptés* , utilisez <https://admin.exchange.microsoft.com/#/accepteddomains>.
2. Dans la page *Domaines acceptés* , notez la valeur du **type de domaine** pour votre domaine de messagerie principal.
    - Si le type de domaine est défini sur **Faisant autorité**, il est supposé que toutes les boîtes aux lettres des destinataires de votre organisation résident actuellement dans Exchange Online.
    - Si le type de domaine est défini sur **InternalRelay** , vous pouvez toujours être dans un modèle hybride où certaines boîtes aux lettres de destinataires résident toujours localement.

## <a name="step-3-audit-inbound-connectors"></a>Étape 3 : Auditer les connecteurs entrants

1. Dans le Centre d’administration Exchange (EAC), <https://admin.exchange.microsoft.com>développez le *flux de messagerie*, puis cliquez sur **Connecteurs**. Ou, pour accéder directement à la page *Connecteurs*, utilisez <https://admin.exchange.microsoft.com/#/connectors>.
2. Dans la page *Connecteurs* , notez les connecteurs avec les paramètres suivants :
   - La valeur **From** est **l’organisation partenaire** qui peut être corrélée à une passerelle SMTP tierce.
   - La valeur **From** est **Votre organisation** qui peut indiquer que vous êtes toujours dans un scénario hybride.

## <a name="step-4-activate-the-evaluation"></a>Étape 4 : Activer l’évaluation

Suivez les instructions fournies ici pour activer votre évaluation Microsoft Defender pour Office 365 à partir du portail Microsoft 365 Defender.

Pour plus d’informations, consultez [Essayer Microsoft Defender pour Office 365](../office-365-security/try-microsoft-defender-for-office-365.md).

1. Dans le portail Microsoft 365 Defender de <https://security.microsoft.com> développer *Email & collaboration*\>, sélectionnez **Stratégies & règles** \> sélectionnez **Stratégies de menace**\>, faites défiler jusqu’à la section *Autres*, puis sélectionnez **Mode d’évaluation**. Ou, pour accéder directement à la page *du mode Évaluation* , utilisez <https://security.microsoft.com/atpEvaluation>.

2. Dans la page *Mode Évaluation* , cliquez sur **Démarrer l’évaluation**.

   :::image type="content" source="../../media/mdo-eval/mdo-eval-activate-eval_05.png" alt-text="Page Mode Évaluation et bouton Démarrer l’évaluation sur lequel cliquer." lightbox="../../media/mdo-eval/mdo-eval-activate-eval_05.png":::

3. Dans la boîte de dialogue *Activer la protection* , sélectionnez **Non, je veux uniquement créer des rapports**, puis cliquez sur **Continuer**.

   :::image type="content" source="../../media/mdo-eval/mdo-eval-activate-eval_06.png" alt-text="La boîte de dialogue Activer la protection et non, je veux uniquement sélectionner l’option de création de rapports." lightbox="../../media/mdo-eval/mdo-eval-activate-eval_06.png":::

4. Dans la boîte de dialogue *Sélectionner les utilisateurs que vous souhaitez inclure* , sélectionnez **Tous les utilisateurs**, puis cliquez sur **Continuer**.

   :::image type="content" source="../../media/mdo-eval/mdo-eval-activate-eval_07.png" alt-text="La boîte de dialogue Sélectionner les utilisateurs que vous souhaitez inclure et l’option Tous les utilisateurs à sélectionner." lightbox="../../media/mdo-eval/mdo-eval-activate-eval_07.png":::

5. Dans la boîte de *dialogue Aide-nous à comprendre votre flux de messagerie* , l’une des options suivantes est automatiquement sélectionnée en fonction de notre détection de l’enregistrement MX pour votre domaine :

   - **J’utilise uniquement Microsoft Exchange Online** : les enregistrements MX de votre domaine pointent vers Microsoft 365. Il n’y a plus rien à configurer, alors cliquez sur **Terminer**.

     :::image type="content" source="../../media/mdo-eval/mdo-eval-activate-eval_08a.png" alt-text="Aide-nous à comprendre votre boîte de dialogue de flux de courrier avec l’option J’utilise uniquement Microsoft Exchange Online sélectionnée." lightbox="../../media/mdo-eval/mdo-eval-activate-eval_08a.png":::

   - **J’utilise un fournisseur de services tiers et/ou local** : dans les écrans à venir, sélectionnez le nom du fournisseur ainsi que le connecteur entrant qui accepte le courrier de cette solution. Vous décidez également si vous avez besoin d’une règle de flux de courrier Exchange Online (également appelée règle de transport) qui ignore le filtrage du courrier indésirable pour les messages entrants à partir du service ou de l’appareil de protection tiers. Lorsque vous avez terminé, cliquez sur **Terminer**.

## <a name="next-steps"></a>Prochaines étapes

Étape 3 sur 3 : Configurer le pilote pour Microsoft Defender pour Office 365

Revenir à la vue d’ensemble [d’Évaluer Microsoft Defender pour Office 365](eval-defender-office-365-overview.md)

Revenir à la vue d’ensemble de [Evaluate et pilot Microsoft 365 Defender](eval-overview.md)
