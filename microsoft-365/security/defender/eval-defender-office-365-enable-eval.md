---
title: Activer l’environnement d’évaluation de Microsoft Defender pour Office 365 dans votre environnement de production
description: Étapes pour activer Microsoft Defender pour l’évaluation Office 365, avec des licences d’évaluation, la gestion des enregistrement MX, & audit des domaines acceptés et des connexions entrantes.
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
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-overview
- m365solution-evalutatemtp
ms.topic: how-to
ms.technology: m365d
ms.openlocfilehash: a64f217b88c41ca256d1ee343629741fd2ad880b
ms.sourcegitcommit: 6c342a956b2dbc32be33bac1a23a5038490f1b40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58533146"
---
# <a name="enable-the-evaluation-environment"></a>Activer l’environnement d’évaluation

**S’applique à :**
- Microsoft 365 Defender

Cet article est [l’étape 2 sur 3 dans](eval-defender-office-365-overview.md) le processus de configuration de l’environnement d’évaluation de Microsoft Defender pour Office 365. Pour plus d’informations sur ce processus, voir [l’article de présentation.](eval-defender-office-365-overview.md)

Utilisez les étapes suivantes pour activer l’évaluation de Microsoft Defender pour Office 365.

![Étapes permettant d’activer Microsoft Defender pour Office 365 dans l’environnement d’évaluation de Microsoft Defender](../../media/defender/m365-defender-office-eval-enable-steps.png)

- [Étape 1 : Activer les licences d’essai](#step-1-activate-trial-licenses)
- [Étape 2 : Auditer et vérifier l’enregistrement MX public](#step-2-audit-and-verify-the-public-mx-record)
- [Étape 3 : Auditer les domaines acceptés](#step-3-audit-accepted-domains)
- [Étape 4 : Auditer les connecteurs entrants](#step-4-audit-inbound-connectors)
- [Étape 5 : Activer l’évaluation](#step-5-activate-the-evaluation)

## <a name="step-1-activate-trial-licenses"></a>Étape 1 : Activer les licences d’essai

Connectez-vous à votre Microsoft Defender existant pour Office 365 environnement ou portail d’administration des clients.

1. Accédez au portail d’administration.
2. Sélectionnez Acheter des services dans le lancement rapide.

   :::image type="content" source="../../media/mdo-eval/1_m365-purchase-services.png" alt-text="Cliquez sur Acheter des services dans le volet de navigation de Office 365.":::

3. Faites défiler vers le bas jusquAdd-On section (ou recherchez « Defender ») pour localiser Microsoft Defender Office 365 plans.
4. Cliquez sur Détails à côté du plan que vous souhaitez évaluer.

   :::image type="content" source="../../media/mdo-eval/2_mdo-eval-license-details.png" alt-text="Cliquez ensuite sur le bouton Détails.":::

5. Cliquez sur le *lien Démarrer la version d’essai* gratuite.

   :::image type="content" source="../../media/mdo-eval/3-m365-purchase-button.png" alt-text="Cliquez sur l’essai gratuit Démarrer *lien hypertexte* dans ce panneau.":::

6. Confirmez votre demande et cliquez sur le *bouton Essayer maintenant.*

   :::image type="content" source="../../media/mdo-eval/4_mdo-trial-order.png" alt-text="Cliquez maintenant sur le bouton Essayer maintenant **.":::

## <a name="step-2-audit-and-verify-the-public-mx-record"></a>Étape 2 : Auditer et vérifier l’enregistrement MX public

Pour évaluer efficacement Microsoft Defender pour Office 365, il est important que le courrier électronique externe entrant soit relayé via l’instance Exchange Online Protection (EOP) associée à votre client.

1. Connectez-vous au portail d’administration M365, développez Paramètres et sélectionnez Domaines.
2. Sélectionnez votre domaine de courrier vérifié, puis cliquez sur Gérer le DNS.
3. Notez l’enregistrement MX généré et affecté à votre client EOP.
4. Accédez à votre zone DNS externe (publique) et vérifiez l’enregistrement MX principal associé à votre domaine de messagerie.
    - Si votre enregistrement MX public correspond actuellement à l’adresse EOP affectée *(par exemple, tenant-com.mail.protection.outlook.com),* aucune modification de routage supplémentaire ne doit être requise.
    - Si votre enregistrement MX public est actuellement résolu en passerelle SMTP tierce ou locale, des configurations de routage supplémentaires peuvent être nécessaires.
    - Si votre enregistrement MX public est actuellement résolu en Exchange vous êtes peut-être toujours dans un modèle hybride dans lequel certaines boîtes aux lettres de destinataire n’ont pas encore été migrées vers EXO.

## <a name="step-3-audit-accepted-domains"></a>Étape 3 : Auditer les domaines acceptés

1. Connectez-vous Exchange Online portail d’administration, sélectionnez Flow messagerie, puis cliquez sur Domaines acceptés.
2. Dans la liste des domaines acceptés qui ont été ajoutés et vérifiés dans votre client, notez le **type** de domaine pour votre domaine de messagerie principal.
    - Si le type de domaine est définie sur ***Faisant*** autorité, il est supposé que toutes les boîtes aux lettres des destinataires de votre organisation résident actuellement dans Exchange Online.
    - Si le type de domaine est définie sur ***Relais*** interne, il se peut que vous soyez toujours dans un modèle hybride où certaines boîtes aux lettres de destinataire résident toujours en local.

## <a name="step-4-audit-inbound-connectors"></a>Étape 4 : Auditer les connecteurs entrants

1. Connectez-vous Exchange Online portail d’administration, sélectionnez Flow messagerie, puis cliquez sur Connecteurs.
2. Dans la liste des connecteurs configurés, notez  les entrées provenant de l’organisation partenaire et qui peuvent correspondre à une passerelle SMTP tierce.
3. Dans la liste des connecteurs configurés, notez les entrées étiquetées à partir du serveur de messagerie de votre organisation qui peuvent indiquer que vous êtes toujours dans un scénario hybride. 

## <a name="step-5-activate-the-evaluation"></a>Étape 5 : Activer l’évaluation

Utilisez les instructions ci-après pour activer votre Microsoft Defender pour Office 365 d’évaluation à partir du portail Microsoft 365 Defender web.

1. Connectez-vous à votre client avec un compte ayant accès au portail Microsoft 365 Defender client.
2. Choisissez si vous souhaitez que le portail **Microsoft 365 Defender soit** votre interface par défaut pour Microsoft Defender pour Office 365 administration (recommandé).

   :::image type="content" source="../../media/mdo-eval/1_mdo-eval-activate-eval.png" alt-text="Cliquez sur le bouton Activer les paramètres pour utiliser le portail d’administration centralisé Microsoft 365 Defender amélioré.":::

3. Dans le menu de navigation, sélectionnez **Stratégies & sous** *Email & Collaboration*.

   :::image type="content" source="../../media/mdo-eval/2_mdo-eval-activate-eval.png" alt-text="Voici une image du menu Collaboration & courrier électronique pointant vers stratégies & règles. Cliquez dessus !":::

4. Dans le tableau *de bord Règles & stratégie,* cliquez sur **Stratégies de menace.**

   :::image type="content" source="../../media/mdo-eval/3_mdo-eval-activate-eval.png" alt-text="Image du tableau de bord Règles & stratégie et flèche pointant vers les stratégies de menace. Cliquez ensuite dessus !":::

5. Faites défiler vers le bas *jusqu’à Stratégies* supplémentaires et sélectionnez **la vignette Évaluer Defender Office 365'évaluation.**

   :::image type="content" source="../../media/mdo-eval/4_mdo-eval-activate-eval.png" alt-text="La vignette Eval Defender pour Office 365 qui s’agit d’une version d’essai de 30 jours sur les vecteurs de collaboration & courrier électronique. Cliquez dessus.":::

6. Choisissez maintenant si les e-mails externes sont Exchange Online directement ou vers une passerelle ou un service tiers, puis cliquez sur Suivant.

   :::image type="content" source="../../media/mdo-eval/5_mdo-eval-activate-eval.png" alt-text="Defender for Office 365 évaluera l’envoi de messages à Exchange Online boîtes aux lettres. Donnez des détails sur la façon dont votre courrier est acheminé maintenant, y compris le nom du connecteur sortant qui déroute votre courrier. Si vous utilisez uniquement Exchange Online Protection (EOP), vous n’avez pas de connecteur. Choisissez l’un des fournisseurs tiers ou locaux, ou j’utilise uniquement EOP.":::

7. Si vous utilisez une passerelle tierce, sélectionnez le nom du fournisseur dans la liste sortante avec le connecteur entrant associé à cette solution. Lorsque vous avez répertorié vos réponses, cliquez sur Suivant.

   :::image type="content" source="../../media/mdo-eval/6-mdo-eval-activate-eval-settings.png" alt-text="Dans cette boîte de dialogue, vous choisissez le service fournisseur tiers que votre organisation utilise, ou sélectionnez *Autre*. Dans la boîte de dialogue suivante, sélectionnez le connecteur entrant. Cliquez ensuite sur Suivant.":::

8. Examinez vos paramètres et cliquez sur le bouton Créer **une** évaluation.

   |Avant|Après|
   |:---:|:---:|
   |:::image type="content" source="../../media/mdo-eval/7-mdo-eval-activate-review.png" alt-text="Ce volet dispose d’une zone de drop-down pour passer en revue vos paramètres. Il dispose également d’un lien cliquable pour modifier votre type de routage si nécessaire. Lorsque vous êtes prêt, cliquez sur le grand bouton Bleu Créer l’évaluation.":::|:::image type="content" source="../../media/mdo-eval/8-mdo-eval-activate-complete.png" alt-text="La mise en place est maintenant terminée. Le bouton bleu de cette page indique « Passer à l’évaluation ».":::|
   |

## <a name="next-steps"></a>Prochaines étapes

Étape 3 sur 3 : Configurer le pilote pour Microsoft Defender pour Office 365

Revenir à la vue d’ensemble [de l’évaluation de Microsoft Defender Office 365](eval-defender-office-365-overview.md)

Revenir à la vue d’ensemble [de l’évaluation et de la Microsoft 365 Defender](eval-overview.md)
