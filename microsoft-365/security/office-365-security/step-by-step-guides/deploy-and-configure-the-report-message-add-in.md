---
title: Guide pratique pour déployer et configurer le complément de message de rapport
description: Étapes de déploiement et de configuration des compléments de création de rapports de hameçonnage de Microsoft destinés aux administrateurs de sécurité.
search.product: ''
search.appverid: ''
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTBen
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-guidance-templates
ms.topic: how-to
ms.subservice: mdo
ms.openlocfilehash: 99d41e962cf1b3949167e1b1275807d8b7de01ef
ms.sourcegitcommit: 2b89bcff547e00be3d38dc8d1e6cbcf8f41eba42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2022
ms.locfileid: "67596762"
---
# <a name="deploy-and-configure-the-report-message-add-in-to-users"></a>Déployez et configurez le complément de message de rapport pour les utilisateurs.

Le complément d’hameçonnage de message de rapport et de rapport pour Outlook facilite le signalement du hameçonnage à Microsoft et à ses affiliés à des fins d’analyse, ainsi qu’un triage facile pour les administrateurs dans le [portail des soumissions](https://security.microsoft.com/reportsubmission?viewid=user). 

Selon que vous disposez d’une licence pour Defender pour Office 365, vous bénéficiez également de fonctionnalités supplémentaires, telles que les alertes & l’investigation et la réponse automatisées (AIR), ce qui supprimera la charge de travail de votre personnel des opérations de sécurité. Ce guide vous guide tout au long de la configuration du déploiement du complément, comme recommandé par l’équipe Microsoft Defender pour Office 365.

## <a name="choose-between-which-add-in-to-deploy"></a>Choisir entre le complément à déployer

- Le complément Report Phishing offre la possibilité de signaler uniquement les messages de hameçonnage
- Le complément Message de rapport offre la possibilité de signaler les messages indésirables, et non indésirables (faux positifs) et les messages de hameçonnage.


## <a name="what-youll-need"></a>Ce dont vous aurez besoin

-   Exchange Online Protection (certaines fonctionnalités nécessitent Defender pour Office 365 Plan 2)
-   Autorisations suffisantes (administrateur général pour le déploiement de compléments, administrateur de sécurité pour la personnalisation)
- 5 à 10 minutes pour effectuer les étapes ci-dessous

## <a name="deploy-the-add-in-for-users"></a>Déployer le complément pour les utilisateurs

1.  **Connectez-vous** au Centre d'administration Microsoft 365.  https://admin.microsoft.com.
1.  Dans le volet de navigation gauche, **appuyez sur Afficher tout** , **développez Paramètres** et sélectionnez **Applications intégrées**.
1.  Sur la page qui se charge, **appuyez sur Obtenir des applications**.
1.  Dans la page qui s’affiche, dans la zone de recherche en haut à droite, entrez **message** de rapport ou **hameçonnage de rapport**, puis sélectionnez **Rechercher**.
1.  **Appuyez sur Obtenir maintenant sur l’application** choisie dans les résultats de la recherche (l’éditeur est **Microsoft Corporation**).
1.  Dans le menu volant qui s’affiche, sélectionnez sur qui déployer le complément. Si vous testez, vous souhaiterez peut-être utiliser un groupe spécifique, sinon configurez-le pour **l’ensemble de l’organisation** , lorsque vous avez effectué une sélection en appuyant sur **Suivant**.
1.  Passez en revue les autorisations, les informations et les fonctionnalités, puis appuyez sur **Suivant**.
1.  Appuyez sur **Terminer le déploiement** (l’apparition automatique du complément dans les clients Outlook peut prendre 12 à 24 heures).

## <a name="configure-the-add-in-for-users"></a>Configurer le complément pour les utilisateurs
1.  **Connectez-vous** au portail Microsoft Security à l’adresse https://security.microsoft.com.
2.  Dans le volet de navigation gauche, sous **Email & collaboration**, sélectionnez **Stratégies & règles**.
3.  Sélectionnez **Stratégies de menace**.
4.  Sélectionnez **les paramètres de message signalés par l’utilisateur** sous le titre **Autres** .
5.  Vérifiez que le **bouton Message de rapport Microsoft Outlook** est **activé.**
6.  Sous **Envoyer les messages signalés pour** choisir **Microsoft** (recommandé).
7.  Veillez **à ce que les utilisateurs choisissent s’ils souhaitent signaler qu’ils** sont décochés et **qu’ils signalent toujours que le message** est sélectionné.
8.  Appuyez sur **Enregistrer**.

## <a name="optional-steps--configure-notifications"></a>Étapes facultatives : configurer les notifications

1.  Dans la page de configuration des étapes précédentes, sous **l’expérience de création de rapports** utilisateur, configurez le titre et le corps des fenêtres contextuelles avant et après la création de rapports si vous le souhaitez. Les utilisateurs finaux verront la fenêtre contextuelle avant la création de rapports si **demandez-moi avant que la création de rapports** ne soit également activée.
2.  Si vous souhaitez que les notifications proviennent d’une boîte aux lettres interne de l’organisation, **sélectionnez Spécifier Office 365 adresse e-mail à utiliser comme expéditeur** et recherchez une boîte aux lettres valide dans votre organisation à partir de laquelle envoyer les notifications.
3.  **Appuyez sur Personnaliser les notifications** pour configurer le texte envoyé aux utilisateurs déclarants après que l’administrateur a examiné un message signalé à l’aide de Mark & Notify, configurez les options **Phishing**, **Junk** & **No threats** found.
4.  Sous **l’onglet Pied** de page, sélectionnez le pied de page global à envoyer pour les notifications, ainsi que le logo de votre organisation, le cas échéant.


### <a name="further-reading"></a>Lire plus en détail
En savoir plus sur les paramètres de message signalés par l’utilisateur [- Office 365 | Microsoft Docs](../user-submission.md)

Activer le message de rapport ou le complément de hameçonnage [de rapport Activer le message de rapport ou les compléments d’hameçonnage de rapport - Office 365 | Microsoft Docs](../enable-the-report-message-add-in.md)
