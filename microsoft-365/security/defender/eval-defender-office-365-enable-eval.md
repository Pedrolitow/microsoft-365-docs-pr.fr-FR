---
title: Activer l’environnement d’évaluation de Microsoft Defender pour Office 365 dans votre environnement de production
description: Étapes d’activation de Microsoft Defender pour une évaluation Office 365, avec des licences d’évaluation, la gestion des enregistrement MX, & audit des domaines acceptés et des connexions entrantes.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.date: 07/01/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: how-to
ms.technology: m365d
ms.openlocfilehash: a5a14d507f7cd10ff4f7ab62b552ab256f0e4a5e
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2022
ms.locfileid: "64498998"
---
# <a name="enable-the-evaluation-environment"></a>Activer l’environnement d’évaluation

**S’applique à :**
- Microsoft 365 Defender

Cet article est [l’étape 2 sur 3](eval-defender-office-365-overview.md) dans le processus de configuration de l’environnement d’évaluation de Microsoft Defender pour Office 365. Pour plus d’informations sur ce processus, consultez [l’article de présentation](eval-defender-office-365-overview.md).

Utilisez les étapes suivantes pour activer l’évaluation de Microsoft Defender pour Office 365.

:::image type="content" source="../../media/defender/m365-defender-office-eval-enable-steps.png" alt-text="Étapes permettant d’activer Microsoft Defender pour Office 365 dans l’environnement d’évaluation De Microsoft Defender" lightbox="../../media/defender/m365-defender-office-eval-enable-steps.png":::


- [Étape 1 : Activer les licences d’essai](#step-1-activate-trial-licenses)
- [Étape 2 : Auditer et vérifier l’enregistrement MX public](#step-2-audit-and-verify-the-public-mx-record)
- [Étape 3 : Auditer les domaines acceptés](#step-3-audit-accepted-domains)
- [Étape 4 : Auditer les connecteurs entrants](#step-4-audit-inbound-connectors)
- [Étape 5 : Activer l’évaluation](#step-5-activate-the-evaluation)

## <a name="step-1-activate-trial-licenses"></a>Étape 1 : Activer les licences d’essai

Connectez-vous à votre Microsoft Defender existant pour Office 365 environnement ou portail d’administration des clients.

1. Accédez au portail d’administration.
2. Sélectionnez Acheter des services dans le lancement rapide.

   :::image type="content" source="../../media/mdo-eval/1_m365-purchase-services.png" alt-text="Option Acheter des services sur le Centre d'administration Microsoft 365" lightbox="../../media/mdo-eval/1_m365-purchase-services.png":::

3. Faites défiler vers le bas jusquAdd-On section (ou recherchez « Defender ») pour localiser microsoft Defender Office 365 plans.
4. Cliquez sur Détails à côté du plan que vous souhaitez évaluer.

   :::image type="content" source="../../media/mdo-eval/2_mdo-eval-license-details.png" alt-text="Bouton Détails à cliquer" lightbox="../../media/mdo-eval/2_mdo-eval-license-details.png":::

5. Cliquez sur le *lien Démarrer la version d’essai* gratuite.

   :::image type="content" source="../../media/mdo-eval/3-m365-purchase-button.png" alt-text="Lien hypertexte d’essai gratuit de démarrage" lightbox="../../media/mdo-eval/3-m365-purchase-button.png":::

6. Confirmez votre demande et cliquez sur le *bouton Essayer maintenant* .

   :::image type="content" source="../../media/mdo-eval/4_mdo-trial-order.png" alt-text="Bouton Essayer maintenant" lightbox="../../media/mdo-eval/4_mdo-trial-order.png":::

## <a name="step-2-audit-and-verify-the-public-mx-record"></a>Étape 2 : Auditer et vérifier l’enregistrement MX public

Pour évaluer efficacement Microsoft Defender pour Office 365, il est important que le courrier électronique externe entrant soit relayé via l’instance Exchange Online Protection (EOP) associée à votre client.

1. Connectez-vous au portail d’administration M365, développez Paramètres et sélectionnez Domaines.
2. Sélectionnez votre domaine de courrier vérifié, puis cliquez sur Gérer le DNS.
3. Notez l’enregistrement MX généré et affecté à votre client EOP.
4. Accédez à votre zone DNS externe (publique) et vérifiez l’enregistrement MX principal associé à votre domaine de messagerie.
    - *Si votre enregistrement MX public* correspond actuellement à l’adresse EOP affectée (par exemple, tenant-com.mail.protection.outlook.com), aucune modification de routage supplémentaire ne doit être requise.
    - Si votre enregistrement MX public est actuellement résolu en passerelle SMTP tierce ou locale, des configurations de routage supplémentaires peuvent être nécessaires.
    - Si votre enregistrement MX public est actuellement résolu en Exchange vous êtes peut-être toujours dans un modèle hybride dans lequel certaines boîtes aux lettres de destinataire n’ont pas encore été migrées vers EXO.

## <a name="step-3-audit-accepted-domains"></a>Étape 3 : Auditer les domaines acceptés

1. Log on the Exchange Online Admin Portal, select Mail Flow, and then click Accepted Domains.
2. Dans la liste des domaines acceptés qui ont été ajoutés et vérifiés dans votre client, notez le **type** de domaine pour votre domaine de messagerie principal.
    - Si le type de domaine est définie sur ***Faisant*** autorité, il est supposé que toutes les boîtes aux lettres des destinataires de votre organisation résident actuellement dans Exchange Online.
    - Si le type de domaine est définie sur ***Relais*** interne, il se peut que vous soyez toujours dans un modèle hybride où certaines boîtes aux lettres de destinataire résident toujours en local.

## <a name="step-4-audit-inbound-connectors"></a>Étape 4 : Auditer les connecteurs entrants

1. Log on the Exchange Online Admin Portal, select Mail Flow, and then click Connectors.
2. Dans la liste des connecteurs configurés, notez les entrées provenant de l’organisation partenaire et qui peuvent correspondre à une passerelle SMTP tierce.
3. Dans la liste des connecteurs configurés, notez les entrées étiquetées  à partir du serveur de messagerie de votre organisation qui peuvent indiquer que vous êtes toujours dans un scénario hybride.

## <a name="step-5-activate-the-evaluation"></a>Étape 5 : Activer l’évaluation

Utilisez les instructions ci-après pour activer votre Microsoft Defender pour Office 365'évaluation à partir du portail Microsoft 365 Defender web.

1. Connectez-vous à votre client avec un compte ayant accès au portail Microsoft 365 Defender client.
2. Choisissez si vous souhaitez que le portail **Microsoft 365 Defender soit** votre interface par défaut pour Microsoft Defender pour Office 365'administration (recommandé).

   :::image type="content" source="../../media/mdo-eval/1_mdo-eval-activate-eval.png" alt-text="Le bouton Activer dans Paramètres pour aboutir à un portail d’administration centralisé Microsoft 365 Defender amélioré" lightbox="../../media/mdo-eval/1_mdo-eval-activate-eval.png":::

3. Dans le menu de navigation, sélectionnez **Stratégies & sous** *Collaboration & messagerie* électronique.

   :::image type="content" source="../../media/mdo-eval/2_mdo-eval-activate-eval.png" alt-text="L’élément de menu & stratégies à cliquer" lightbox="../../media/mdo-eval/2_mdo-eval-activate-eval.png":::

4. Dans le tableau *de bord Règles & stratégie* , cliquez sur **Stratégies de menace**.

   :::image type="content" source="../../media/mdo-eval/3_mdo-eval-activate-eval.png" alt-text="L’élément de menu stratégies de menace à cliquer" lightbox="../../media/mdo-eval/3_mdo-eval-activate-eval.png":::

5. Faites défiler vers le bas *jusqu’à Stratégies* supplémentaires et sélectionnez la **vignette Évaluer Defender Office 365'évaluation**.

   :::image type="content" source="../../media/mdo-eval/4_mdo-eval-activate-eval.png" alt-text="Vignette Eval Defender pour Office 365" lightbox="../../media/mdo-eval/4_mdo-eval-activate-eval.png":::

6. Choisissez maintenant si les e-mails externes sont Exchange Online directement ou vers une passerelle ou un service tiers, puis cliquez sur Suivant.

   :::image type="content" source="../../media/mdo-eval/5_mdo-eval-activate-eval.png" alt-text="Volet Paramètres de routage dans le portail Microsoft Defender pour Office 365" lightbox="../../media/mdo-eval/5_mdo-eval-activate-eval.png":::

7. Si vous utilisez une passerelle tierce, sélectionnez le nom du fournisseur dans la liste sortante, ainsi que le connecteur entrant associé à cette solution. Lorsque vous avez répertorié vos réponses, cliquez sur Suivant.

   :::image type="content" source="../../media/mdo-eval/6-mdo-eval-activate-eval-settings.png" alt-text="Volet Paramètres tiers ou local dans le portail Microsoft Defender Office 365 web" lightbox="../../media/mdo-eval/6-mdo-eval-activate-eval-settings.png":::

8. Examinez vos paramètres et cliquez sur le **bouton Créer une** évaluation.

   |Avant|Après|
   |:---:|:---:|
   |:::image type="content" source="../../media/mdo-eval/7-mdo-eval-activate-review.png" alt-text="Volet Passer en revue vos paramètres dans le portail Microsoft Defender Office 365 web" lightbox="../../media/mdo-eval/7-mdo-eval-activate-review.png":::|:::image type="content" source="../../media/mdo-eval/8-mdo-eval-activate-complete.png" alt-text="Notification d’achèvement de l’installation de l’évaluation dans le portail Microsoft Defender Office 365" lightbox="../../media/mdo-eval/8-mdo-eval-activate-complete.png":::|
   |

## <a name="next-steps"></a>Prochaines étapes

Étape 3 sur 3 : Configurer le pilote pour Microsoft Defender pour Office 365

Revenir à la vue d’ensemble [de l’évaluation de Microsoft Defender Office 365](eval-defender-office-365-overview.md)

Revenir à la vue d’ensemble [de l’évaluation et de la Microsoft 365 Defender](eval-overview.md)
