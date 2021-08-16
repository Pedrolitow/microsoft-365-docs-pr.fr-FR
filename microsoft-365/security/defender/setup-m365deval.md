---
title: Configurer votre laboratoire d Microsoft 365 Defender d’essai ou votre environnement pilote
description: Accéder au Microsoft 365 de sécurité, puis configurer votre environnement de laboratoire Microsoft 365 Defender d’essai
keywords: Microsoft 365 Defender d’essai, Microsoft 365 Defender le programme d’installation pilote, essayez Microsoft 365 Defender, Microsoft 365 Defender de laboratoire d’évaluation
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: v-lsaldanha
author: lovina-saldanha
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: f447e4303e1e7524e8e3f8e10b2f3082ea3316cc4b71253dd2c43834c0003f80
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53902539"
---
# <a name="set-up-your-microsoft-365-defender-trial-in-a-lab-environment"></a>Configurer votre version d Microsoft 365 Defender d’essai dans un environnement de laboratoire 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender 

Cette rubrique vous guide pour configurer un environnement de laboratoire dédié. Pour plus d’informations sur la configuration d’une version d’évaluation en production, voir le nouveau guide Microsoft 365 Defender évaluation et [pilote.](eval-overview.md) 

## <a name="create-an-office-365-e5-trial-tenant"></a>Créer un client d Office 365 E5 d’essai
>[!NOTE]
>Si vous avez déjà un abonnement Office 365 ou Azure Active Directory, vous pouvez ignorer les étapes Office 365 E5 création d’un client d’essai.

1. Go to the [Office 365 E5 product portal](https://www.microsoft.com/microsoft-365/business/office-365-enterprise-e5-business-software?activetab=pivot%3aoverviewtab) and select Free **trial**.

   ![Image of_Office page d’essai gratuit 365 E5](../../media/mtp-eval-9.png)
  
2. Terminez l’inscription de la version d’essai en entrant votre adresse de messagerie (personnelle ou d’entreprise). Cliquez **sur Configurer le compte.**

   ![Image of_Office page de configuration de l’enregistrement de la version d’essai 365 E5](../../media/mtp-eval-10.png)

3. Remplissez votre prénom, nom, numéro de téléphone d’entreprise, nom de société, taille de la société et pays ou région.  

   ![Image of_Office page de configuration de l’enregistrement de la version d’essai 365 E5 demandant le nom, le téléphone et les détails de la société](../../media/mtp-eval-11.png)
   
   > [!NOTE]
   > Le pays ou la région que vous définissez ici détermine la région de centre de données dans Office 365 sera hébergée.
  
4. Choisissez votre préférence de vérification : via un SMS ou un appel. Cliquez **sur Envoyer le code de vérification.** 

   ![Image of_Office page de configuration de l’inscription de la version d’essai 365 E5 demandant les préférences de vérification](../../media/mtp-eval-12.png)

5. Définissez le nom de domaine personnalisé de votre client, puis cliquez sur **Suivant.**

   ![Image of_Office page de configuration de l’inscription de la version d’essai 365 E5 dans laquelle vous pouvez configurer votre nom de domaine personnalisé](../../media/mtp-eval-13.png)
 
6. Configurer la première identité, qui sera un administrateur général pour le client. Remplissez le **nom et le** mot de **passe.** Cliquez sur **S’inscrire**.

   ![Image of_Office page de configuration de l’inscription de la version d’essai 365 E5 dans laquelle vous pouvez définir votre identité professionnelle](../../media/mtp-eval-14.png)

7. Cliquez **sur Passer au programme d’installation** pour terminer Office 365 E5 mise en service du client d’essai.

   ![Image de la page Office 365 E5 d’inscription de la version d’essai, qui vous invite à cliquer sur le bouton Aller au programme d’installation](../../media/mtp-eval-15.png)

8. Connecter votre domaine d’entreprise au Office 365 client. [Facultatif] Choisissez **Connecter domaine que vous possédez déjà** et tapez votre nom de domaine. Cliquez sur **Suivant**.

   ![Image of_Office page d’installation 365 E5 dans laquelle vous devez personnaliser votre connectez-vous et votre courrier électronique](../../media/mtp-eval-16.png)
 
9. Ajoutez un enregistrement TXT ou MX pour valider la propriété du domaine. Une fois que vous avez ajouté l’enregistrement TXT ou MX à votre domaine, sélectionnez **Vérifier**.

   ![Image of_Office page d’installation 365 E5 dans laquelle vous devez ajouter un TXT d’enregistrement MX pour vérifier votre domaine](../../media/mtp-eval-17.png)
 
10. [Facultatif] Créez d’autres comptes d’utilisateur pour votre client. Vous pouvez ignorer cette étape en cliquant sur **Suivant.**

    ![Image of_Office page d’installation 365 E5 dans laquelle vous pouvez ajouter d’autres utilisateurs](../../media/mtp-eval-18.png)
 
11. [Facultatif] Téléchargez Office applications. Cliquez **sur Suivant** pour ignorer cette étape. 

    ![Image of_Office page 365 E5 où vous pouvez installer vos applications Office applications](../../media/mtp-eval-19.png)

12. [Facultatif] Migrer les messages électroniques. Là encore, vous pouvez ignorer cette étape.

    ![Image of_Office 365 E5 dans laquelle vous pouvez définir s’il faut migrer ou non des messages électroniques](../../media/mtp-eval-20.png)
 
13. Choisissez des services en ligne. Sélectionnez **Exchange** puis cliquez sur **Suivant.** 

    ![Image of_Office 365 E5 dans laquelle vous pouvez choisir vos services en ligne](../../media/mtp-eval-21.png)

14. Ajoutez des enregistrements MX, CNAME et TXT à votre domaine. Lorsque vous avez terminé, sélectionnez **Vérifier**.

    ![Image of_Office 365 E5 ici, vous pouvez ajouter vos enregistrements DNS](../../media/mtp-eval-22.png)
 
15. Félicitations, vous avez terminé la mise en service de votre Office 365 client.

    ![Image of_Office page de confirmation de l’achèvement de l’installation 365 E5](../../media/mtp-eval-23.png)

## <a name="enable-microsoft-365-trial-subscription"></a>Activer l Microsoft 365 d’essai

>[!NOTE]
>L’inscription à une version d’essai vous donne 25 licences utilisateur à utiliser pendant un mois. Pour plus d’informations, voir Essayer ou acheter un abonnement [M365.](../../commerce/try-or-buy-microsoft-365.md)

1. À [partir Administration Microsoft 365, cliquez](https://admin.microsoft.com/)sur **Facturation,** puis accédez à Acheter des **services.**

2. Sélectionnez **Microsoft 365 E5** puis cliquez **sur Démarrer la version d’essai gratuite.** 

   ![Image of_Microsoft page d’essai gratuit de démarrage 365 E5](../../media/mtp-eval-24.png)

3. Choisissez votre préférence de vérification : via un SMS ou un appel. Une fois que vous avez décidé, entrez le numéro de téléphone, sélectionnez **M’envoyer** un sms ou **m’appeler** en fonction de votre sélection.

   ![Image of_Microsoft 365 E5 : page d’essai gratuit de démarrage demandant des coordonnées pour envoyer du code pour prouver que vous n’êtes pas un robot](../../media/mtp-eval-25.png)
 
4. Entrez le code de vérification, puis cliquez **sur Démarrer votre version d’essai gratuite.**

   ![Image of_Microsoft 365 E5 Page d’essai gratuit de démarrage dans laquelle vous pouvez remplir le code de vérification envoyé par le système pour prouver que vous n’êtes pas un robot](../../media/mtp-eval-26.png)

5. Cliquez **sur Essayer maintenant** pour confirmer votre Microsoft 365 E5 d’essai.

   ![Image of_Microsoft 365 E5 Démarrage de la page d’essai gratuit où vous devez horloger le bouton Essayer maintenant pour démarrer](../../media/mtp-eval-27.png)
 
6. Go to the **Administration Microsoft 365 Center**  >  **Users**  >  **Active Users**. Sélectionnez votre compte d’utilisateur, sélectionnez Gérer les **licences de** produits, puis remplacez la licence Office 365 E5 par **Microsoft 365 E5**. Cliquez sur **Save (Enregistrer)**.

   ![Image of_Microsoft page du Centre d’administration 365 dans laquelle vous pouvez sélectionner Microsoft 365 E5 licence](../../media/mtp-eval-28.png)
 
7. Sélectionnez de nouveau le compte d’administrateur général, puis cliquez **sur Gérer le nom d’utilisateur.**

   ![Image of_Microsoft page du Centre d’administration 365 dans laquelle vous pouvez sélectionner Compte, puis Gérer le nom d’utilisateur](../../media/mtp-eval-29.png)

8. [Facultatif] Modifiez le domaine de *onmicrosoft.com* à votre propre domaine, en fonction de ce que vous avez choisi lors des étapes précédentes. Cliquez sur **Enregistrer les modifications**.

   ![Image of_Microsoft page du Centre d’administration 365 dans laquelle vous pouvez modifier vos préférences de domaine](../../media/mtp-eval-30.png)



## <a name="next-step"></a>Étape suivante
|[Phase 3 : Configurer & intégré](config-m365d-eval.md) | Configurez chaque pilier Microsoft 365 Defender pour votre laboratoire d Microsoft 365 Defender ou votre environnement pilote et intégrer vos points de terminaison.
|:-------|:-----|
