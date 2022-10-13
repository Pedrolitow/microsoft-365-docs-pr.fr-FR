---
title: Configurer les options de mise en production standard ou ciblée
f1.keywords:
- CSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- scotvorg
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
- BEA160
- GEA150
ms.assetid: 3b3adfa4-1777-4ff0-b606-fb8732101f47
description: Découvrez comment configurer l’option de mise en production pour les mises à jour de nouveaux produits et fonctionnalités dans le Centre d'administration Microsoft 365.
ms.openlocfilehash: 9cd35f76c839bf234eb434b774e98ef49e7ed095
ms.sourcegitcommit: 04e517c7e00323b5c33d8ea937115725cf2cfd4d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2022
ms.locfileid: "68564167"
---
# <a name="set-up-the-standard-or-targeted-release-options"></a>Configurer les options de mise en production standard ou ciblée

> [!IMPORTANT]
> Les mises à jour Microsoft 365 décrites dans cet article s’appliquent à OneDrive Entreprise, SharePoint Online, Office sur le Web, Centre d'administration Microsoft 365 et certains composants de Exchange Online. Ces options de mise en production sont ciblées et offrent les meilleurs moyens de publier les modifications apportées à Microsoft 365, mais ne peuvent pas être garanties à tout moment ou pour toutes les mises à jour. Actuellement, elles ne s’appliquent pas aux services autres que ceux répertoriés précédemment. Pour plus d’informations sur les options de mise en production pour Microsoft 365 Apps, consultez [Vue d’ensemble des canaux de mise à jour pour Microsoft 365 Apps](/deployoffice/overview-update-channels).

Avec Microsoft 365, vous recevez de nouvelles mises à jour et fonctionnalités de produit à mesure qu’elles deviennent disponibles au lieu d’effectuer des mises à jour coûteuses tous les quelques années. Vous n'avez donc plus besoin de procéder à des mises à jour onéreuses chaque année. De plus, vous pouvez gérer la manière dont votre organisation reçoit ces mises à jour. Par exemple, vous pouvez vous inscrire à une publication anticipée et faire profiter l'ensemble de votre organisation des mises à jour en avance, ou sélectionner un panel restreint d'utilisateurs qui les testeront. Vous pouvez également décider de rester sur le programme de publication standard et recevoir les mises à jour plus tard. Cet article explique les différentes options de mise en production et la façon dont vous pouvez les utiliser pour votre organisation.

## <a name="how-it-works---release-validation"></a>Mode de fonctionnement - Validation de publication

Toute nouvelle version est d’abord testée et validée par l’équipe de fonctionnalités, puis par l’ensemble de l’équipe de fonctionnalités Microsoft 365, suivie de l’ensemble de Microsoft. Un fois les tests et la validation internes accomplis, l'étape suivante consiste en une **publication ciblée** (anciennement nommée First Release) à destination des clients inscrits. À chaque cycle de publication, Microsoft recueille des commentaires, puis valide davantage la qualité en surveillant des métriques d'utilisation clés. Cette validation progressive est en place pour s'assurer que la publication à l'échelle mondiale est aussi robuste que possible. Les publications sont illustrées dans la figure suivante.
  
![Anneaux de validation de mise en production pour Microsoft 365.](../../media/73611ed3-2d8c-4e7b-8074-9f03b239f9ed.png)
  
Pour les mises à jour importantes, les clients sont initialement avertis par la [feuille de route Microsoft 365](https://products.office.com/business/office-365-roadmap). À mesure qu’une mise à jour se rapproche du déploiement, elle est communiquée par le biais de votre [centre de messages Microsoft 365](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/MessageCenter).

> [!NOTE]
> Vous avez besoin d’un compte Microsoft 365 ou Azure AD pour accéder à votre centre de messages via le [centre d’administration](/office365/admin/admin-overview/admin-center-overview). Les utilisateurs du plan d’accueil Microsoft 365 n’ont pas de centre d’administration.

## <a name="standard-release"></a>Publication standard

Il s’agit de l’option par défaut dans laquelle vous et vos utilisateurs recevez les dernières mises à jour lorsqu’ils sont publiés à grande échelle pour tous les clients.
  
Une bonne pratique consiste à laisser la majorité des utilisateurs dans la **version Standard** et les professionnels de l’informatique et les utilisateurs d’alimentation dans la **version ciblée** pour évaluer les nouvelles fonctionnalités et préparer les équipes à prendre en charge les utilisateurs professionnels et les cadres.
  
> [!NOTE]
> Si, après avoir souscrit au programme de publication ciblée, vous décidez de revenir au programme de publication standard, vos utilisateurs risquent de perdre l'accès aux fonctionnalités qui n'ont pas encore atteint le niveau de publication standard.
  
## <a name="targeted-release"></a>Version ciblée

With this option, you and your users can be the first to see the latest updates and help shape the product by providing early feedback. You can choose to have individuals or the entire organization receive updates early.
  
> [!IMPORTANT]
> Les mises à jour d'envergure ou complexes peuvent demander plus de temps avant d'être diffusées, de sorte qu'aucun utilisateur ne soit affecté. Aucune garantie ne peut être apportée quant au calendrier exact des publications. La version ciblée n’est actuellement pas disponible pour les clients disposant du plan Office 365 GCC ou du plan Office 365 GCC High et DoD.
  
### <a name="targeted-release-for-entire-organization"></a>Publication ciblée pour l'organisation entière

Si vous [configurez l’option de mise en production dans le Centre d’administration](#set-up-the-release-option-in-the-admin-center) pour cette option, tous vos utilisateurs bénéficieront de l’expérience de publication ciblée. Aux organisations comptant plus de 300 utilisateurs, nous recommandons d'utiliser un abonnement d'essai pour cette option. Pour plus d'informations sur les abonnements d'essai, veuillez vous adresser à votre contact Microsoft.
  
### <a name="targeted-release-for-selected-users"></a>Publication ciblée pour des utilisateurs sélectionnés

Si vous [configurez l’option de mise en production dans le Centre d’administration](#set-up-the-release-option-in-the-admin-center) pour cette option, vous pouvez définir des utilisateurs spécifiques, généralement des utilisateurs d’alimentation, pour bénéficier d’un accès anticipé aux fonctionnalités et fonctionnalités.

> [!IMPORTANT]
> Certaines fonctionnalités sont déployées uniquement par organisation. Cela signifie que l’ensemble de l’organisation recevra l’accès à la fonctionnalité en même temps. Pour des fonctionnalités comme celle-ci, il n’est pas possible pour les utilisateurs sélectionnés dans le programme de mise en production ciblé d’obtenir la fonctionnalité tôt. Cela signifie que votre organisation ne pourra pas recevoir ces fonctionnalités tôt si vous avez configuré des utilisateurs sélectionnés dans la version ciblée. Pour vous assurer que vous voyez toutes les fonctionnalités dans la version ciblée, vous devez configurer la version ciblée pour l’ensemble de l’organisation ou configurer une organisation de test.
  
## <a name="benefits-of-targeted-release"></a>Avantages de la publication ciblée

La version ciblée permet aux administrateurs, aux responsables des modifications ou à toute autre personne responsable des mises à jour de Microsoft 365 de se préparer aux modifications à venir en les laissant :
  
- tester et valider les nouvelles mises à jour avant qu'elles soient publiées pour tous les utilisateurs au sein de l'organisation ;

- préparer la notification et la documentation à l'adresse des utilisateurs avant la publication des mises à jour à l'échelle mondiale ;

- préparer le support technique interne aux changements à venir ;

- effectuer les contrôles de sécurité et de conformité ;

- utiliser des contrôles de fonctionnalité, le cas échéant, pour contrôler la publication des mises à jour aux utilisateurs finaux.

## <a name="set-up-the-release-option-in-the-admin-center"></a>Configurer l’option de mise en production dans le Centre d’administration

Vous pouvez modifier la façon dont votre organisation reçoit les mises à jour de Microsoft 365 en procédant comme suit. Vous devez être administrateur général dans Microsoft 365 pour accepter.
  
> [!IMPORTANT]
> L’application des modifications ci-dessous dans Microsoft 365 peut prendre jusqu’à 24 heures. Si vous décidez de ne plus participer au programme de publication ciblée après l'avoir activé, vos utilisateurs risquent de perdre l'accès aux fonctionnalités qui n'ont pas encore atteint le niveau de publication planifiée.
  
1. Dans le centre d’administration, accédez au **Paramètres** > **de l’organisation** et, sous <a href="https://go.microsoft.com/fwlink/p/?linkid=2067339" target="_blank">l’onglet **Profil de l’organisation**</a>, choisissez **Préférences de publication**.

5. Pour désactiver la version ciblée, sélectionnez **Version standard**, puis **Enregistrer les modifications**.
    
6. Pour activer la mise en production ciblée pour tous les utilisateurs de votre organisation, sélectionnez **Publication ciblée pour tout le monde**, puis **sélectionnez Enregistrer les modifications**.
    
7. Pour activer la mise en production ciblée pour certaines personnes de votre organisation, sélectionnez **Publication ciblée pour les utilisateurs sélectionnés**, puis **sélectionnez Enregistrer les modifications**.

8. **Choisissez Sélectionner des utilisateurs** pour ajouter des utilisateurs un par un, ou **Charger des utilisateurs** pour les ajouter en bloc.

9. Lorsque vous avez terminé d’ajouter des utilisateurs, **sélectionnez Enregistrer les modifications**.
  
## <a name="next-steps"></a>Prochaines étapes

Découvrez comment [gérer les messages](/office365/admin/manage/message-center) dans votre centre de messages [Microsoft 365](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/MessageCenter) pour recevoir des notifications sur les mises à jour et versions à venir de Microsoft 365.

## <a name="related-content"></a>Contenu associé

[Participer au programme Office Insider](https://insider.office.com/join/windows) (article)
