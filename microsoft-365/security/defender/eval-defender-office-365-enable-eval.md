---
title: Activer l’environnement d’évaluation pour Microsoft Defender pour Office 365 dans votre environnement de production
description: Étapes pour activer Microsoft Defender pour Office 365'évaluation, avec des licences d’évaluation, la gestion des enregistrements MX, & l’audit des domaines acceptés et des connexions entrantes.
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
- zerotrust-solution
ms.topic: how-to
ms.technology: m365d
ms.openlocfilehash: f3298c67421dea921a014bc32e91be8033733183
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2022
ms.locfileid: "66750097"
---
# <a name="enable-the-evaluation-environment"></a>Activer l’environnement d’évaluation

**S’applique à :**
- Microsoft 365 Defender

Cet article est [l’étape 2 sur 3](eval-defender-office-365-overview.md) du processus de configuration de l’environnement d’évaluation pour Microsoft Defender pour Office 365. Pour plus d’informations sur ce processus, consultez [l’article de présentation](eval-defender-office-365-overview.md).

Utilisez les étapes suivantes pour activer l’évaluation de Microsoft Defender pour Office 365.

:::image type="content" source="../../media/defender/m365-defender-office-eval-enable-steps.png" alt-text="Étapes à suivre pour activer Microsoft Defender pour Office 365 dans l’environnement d’évaluation Microsoft Defender" lightbox="../../media/defender/m365-defender-office-eval-enable-steps.png":::


- [Étape 1 : Activer les licences d’évaluation](#step-1-activate-trial-licenses)
- [Étape 2 : Auditer et vérifier l’enregistrement MX public](#step-2-audit-and-verify-the-public-mx-record)
- [Étape 3 : Auditer les domaines acceptés](#step-3-audit-accepted-domains)
- [Étape 4 : Auditer les connecteurs entrants](#step-4-audit-inbound-connectors)
- [Étape 5 : Activer l’évaluation](#step-5-activate-the-evaluation)

## <a name="step-1-activate-trial-licenses"></a>Étape 1 : Activer les licences d’évaluation

Connectez-vous à votre environnement Microsoft Defender pour Office 365 existant ou au portail d’administration des locataires.

1. Accédez au portail d’administration.
2. Sélectionnez Services d’achat à partir du lancement rapide.

   :::image type="content" source="../../media/mdo-eval/1_m365-purchase-services.png" alt-text="Option Acheter des services à cliquer dans le Centre d'administration Microsoft 365" lightbox="../../media/mdo-eval/1_m365-purchase-services.png":::

3. Faites défiler jusqu’à la section Add-On (ou recherchez « Defender ») pour localiser les plans Microsoft Defender pour Office 365.
4. Cliquez sur Détails suivant le plan que vous souhaitez évaluer.

   :::image type="content" source="../../media/mdo-eval/2_mdo-eval-license-details.png" alt-text="Bouton Détails à cliquer" lightbox="../../media/mdo-eval/2_mdo-eval-license-details.png":::

5. Cliquez sur le lien *Démarrer la version d’évaluation gratuite* .

   :::image type="content" source="../../media/mdo-eval/3-m365-purchase-button.png" alt-text="Lien hypertexte Démarrer l’essai gratuit" lightbox="../../media/mdo-eval/3-m365-purchase-button.png":::

6. Confirmez votre demande et cliquez sur le bouton *Essayer maintenant* .

   :::image type="content" source="../../media/mdo-eval/4_mdo-trial-order.png" alt-text="Bouton Essayer maintenant" lightbox="../../media/mdo-eval/4_mdo-trial-order.png":::

## <a name="step-2-audit-and-verify-the-public-mx-record"></a>Étape 2 : Auditer et vérifier l’enregistrement MX public

Pour évaluer efficacement Microsoft Defender pour Office 365, il est important que les e-mails externes entrants soient relayés via l’instance Exchange Online Protection (EOP) associée à votre locataire.

1. Connectez-vous au portail M365 Administration, développez Paramètres et sélectionnez Domaines.
2. Sélectionnez votre domaine de messagerie vérifié, puis cliquez sur Gérer le DNS.
3. Notez l’enregistrement MX généré et affecté à votre locataire EOP.
4. Accédez à votre zone DNS externe (publique) et vérifiez l’enregistrement MX principal associé à votre domaine de messagerie.
    - *Si votre enregistrement MX public correspond actuellement à l’adresse EOP affectée (par exemple, tenant-com.mail.protection.outlook.com), aucune autre modification de routage ne doit être nécessaire*.
    - Si votre enregistrement MX public est actuellement résolu en passerelle SMTP tierce ou locale, des configurations de routage supplémentaires peuvent être nécessaires.
    - Si votre enregistrement MX public est actuellement résolu sur Exchange local, vous êtes peut-être toujours dans un modèle hybride où une boîte aux lettres de destinataire n’a pas encore été migrée vers EXO.

## <a name="step-3-audit-accepted-domains"></a>Étape 3 : Auditer les domaines acceptés

1. Connectez-vous au portail Exchange Online Administration, sélectionnez Flux de messagerie, puis cliquez sur Domaines acceptés.
2. Dans la liste des domaines acceptés qui ont été ajoutés et vérifiés dans votre locataire, notez le **type de domaine** de votre domaine de messagerie principal.
    - Si le type de domaine est défini sur ***Faisant autorité***, il est supposé que toutes les boîtes aux lettres des destinataires de votre organisation résident actuellement dans Exchange Online.
    - Si le type de domaine est défini sur ***Relais interne*** , vous pouvez toujours être dans un modèle hybride où certaines boîtes aux lettres de destinataires résident toujours en local.

## <a name="step-4-audit-inbound-connectors"></a>Étape 4 : Auditer les connecteurs entrants

1. Connectez-vous au portail Exchange Online Administration, sélectionnez Flux de messagerie, puis cliquez sur Connecteurs.
2. Dans la liste des connecteurs configurés, notez les entrées qui proviennent de **l’organisation partenaire** et qui peuvent être corrélées à une passerelle SMTP tierce.
3. Dans la liste des connecteurs configurés, notez les entrées étiquetées **à partir du serveur de messagerie de votre organisation** , ce qui peut indiquer que vous êtes toujours dans un scénario hybride.

## <a name="step-5-activate-the-evaluation"></a>Étape 5 : Activer l’évaluation

Suivez les instructions fournies ici pour activer votre évaluation Microsoft Defender pour Office 365 à partir du portail Microsoft 365 Defender.

1. Connectez-vous à votre locataire avec un compte qui a accès au portail Microsoft 365 Defender.
2. Choisissez si vous souhaitez faire du **portail Microsoft 365 Defender** votre interface par défaut pour l’administration Microsoft Defender pour Office 365 (recommandé).

   :::image type="content" source="../../media/mdo-eval/1_mdo-eval-activate-eval.png" alt-text="Bouton Activer les paramètres pour aboutir à un portail Microsoft 365 Defender centralisé et amélioré pour l’administration" lightbox="../../media/mdo-eval/1_mdo-eval-activate-eval.png":::

3. Dans le menu de navigation, sélectionnez **Stratégies & Règles** sous *Email & Collaboration*.

   :::image type="content" source="../../media/mdo-eval/2_mdo-eval-activate-eval.png" alt-text="Élément de menu Stratégies & règles à cliquer" lightbox="../../media/mdo-eval/2_mdo-eval-activate-eval.png":::

4. Dans le tableau de bord *Stratégies & règles* , cliquez sur **Stratégies de menaces**.

   :::image type="content" source="../../media/mdo-eval/3_mdo-eval-activate-eval.png" alt-text="Élément de menu Stratégies de menace à cliquer" lightbox="../../media/mdo-eval/3_mdo-eval-activate-eval.png":::

5. Faites défiler jusqu’à *Stratégies supplémentaires* et sélectionnez la vignette **Évaluer Defender pour Office 365**.

   :::image type="content" source="../../media/mdo-eval/4_mdo-eval-activate-eval.png" alt-text="Vignette Eval Defender pour Office 365" lightbox="../../media/mdo-eval/4_mdo-eval-activate-eval.png":::

6. Choisissez maintenant si les e-mails externes sont acheminés directement vers Exchange Online ou vers une passerelle ou un service tiers, puis cliquez sur Suivant.

   :::image type="content" source="../../media/mdo-eval/5_mdo-eval-activate-eval.png" alt-text="Volet Paramètres de routage dans le portail Microsoft Defender pour Office 365" lightbox="../../media/mdo-eval/5_mdo-eval-activate-eval.png":::

7. Si vous utilisez une passerelle tierce, sélectionnez le nom du fournisseur dans la liste déroulante, ainsi que le connecteur entrant associé à cette solution. Une fois que vous avez listé vos réponses, cliquez sur Suivant.

   :::image type="content" source="../../media/mdo-eval/6-mdo-eval-activate-eval-settings.png" alt-text="Volet Paramètres tiers ou locaux dans le portail Microsoft Defender pour Office 365" lightbox="../../media/mdo-eval/6-mdo-eval-activate-eval-settings.png":::

8. Passez en revue vos paramètres, puis cliquez sur le bouton **Créer une évaluation** .

   |Avant|Après|
   |:---:|:---:|
   |:::image type="content" source="../../media/mdo-eval/7-mdo-eval-activate-review.png" alt-text="Volet Vérifier vos paramètres dans le portail Microsoft Defender pour Office 365" lightbox="../../media/mdo-eval/7-mdo-eval-activate-review.png":::|:::image type="content" source="../../media/mdo-eval/8-mdo-eval-activate-complete.png" alt-text="Notification d’achèvement de la configuration de l’évaluation dans le portail Microsoft Defender pour Office 365" lightbox="../../media/mdo-eval/8-mdo-eval-activate-complete.png":::|
   |

## <a name="next-steps"></a>Prochaines étapes

Étape 3 sur 3 : Configurer le pilote pour Microsoft Defender pour Office 365

Revenir à la vue d’ensemble [d’Évaluer Microsoft Defender pour Office 365](eval-defender-office-365-overview.md)

Revenir à la vue d’ensemble de [Evaluate et pilot Microsoft 365 Defender](eval-overview.md)
