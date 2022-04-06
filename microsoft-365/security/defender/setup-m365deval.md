---
title: Configurer votre laboratoire d Microsoft 365 Defender d’essai ou votre environnement pilote
description: Accéder à Microsoft 365 Defender portail, puis configurer votre environnement de laboratoire d Microsoft 365 Defender d’essai
keywords: Microsoft 365 Defender d’essai, Microsoft 365 Defender programme d’installation pilote, essayez Microsoft 365 Defender, Microsoft 365 Defender de laboratoire d’évaluation
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: lovina-saldanha
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 681d9798c6f16f5829bdb4e5272abc3eac719a59
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2022
ms.locfileid: "64500978"
---
# <a name="set-up-your-microsoft-365-defender-trial-in-a-lab-environment"></a>Configurer votre version d Microsoft 365 Defender d’essai dans un environnement de laboratoire 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender 

Cette rubrique vous guide pour configurer un environnement de laboratoire dédié. Pour plus d’informations sur la configuration d’une version d’évaluation en production, voir le nouveau guide [évaluer et Microsoft 365 Defender](eval-overview.md) pilote. 

## <a name="create-an-office-365-e5-trial-tenant"></a>Créer un client d Office 365 E5 d’essai
>[!NOTE]
>Si vous avez déjà un abonnement Office 365 ou Azure Active Directory, vous pouvez ignorer les étapes Office 365 E5 création du client d’essai.

1. Go to the [Office 365 E5 product portal](https://www.microsoft.com/microsoft-365/business/office-365-enterprise-e5-business-software?activetab=pivot%3aoverviewtab) and select **Free trial**.

   :::image type="content" source="../../media/mtp-eval-9.png" alt-text="Page Office 365 E5 d’essai gratuit" lightbox="../../media/mtp-eval-9.png":::
  
2. Terminez l’inscription de la version d’essai en entrant votre adresse e-mail (personnelle ou d’entreprise). Cliquez **sur Configurer le compte**.

   :::image type="content" source="../../media/mtp-eval-10.png" alt-text="Page de configuration Office 365 E5 d’enregistrement de la version d’essai" lightbox="../../media/mtp-eval-10.png":::

3. Remplissez votre prénom, nom, numéro de téléphone d’entreprise, nom de la société, taille de la société et pays ou région.  

   :::image type="content" source="../../media/mtp-eval-11.png" alt-text="Page Office 365 E5 configuration de l’enregistrement de la version d’essai demandant le nom, le téléphone et les détails de la société" lightbox="../../media/mtp-eval-11.png":::
   
   > [!NOTE]
   > Le pays ou la région que vous définissez ici détermine la région de centre de données dans Office 365 sera hébergée.
  
4. Choisissez votre préférence de vérification : via un SMS ou un appel. Cliquez **sur Envoyer le code de vérification**. 

   :::image type="content" source="../../media/mtp-eval-12.png" alt-text="Page Office 365 E5 configuration de l’enregistrement de la version d’essai demandant la préférence de vérification" lightbox="../../media/mtp-eval-12.png":::

5. Définissez le nom de domaine personnalisé de votre client, puis cliquez sur **Suivant**.

   :::image type="content" source="../../media/mtp-eval-13.png" alt-text="Page Office 365 E5 configuration de l’enregistrement de la version d’essai dans laquelle vous pouvez configurer votre nom de domaine personnalisé" lightbox="../../media/mtp-eval-13.png":::
 
6. Configurer la première identité, qui sera un administrateur général pour le client. Remplissez le **nom et le** mot **de passe**. Cliquez sur **S’inscrire**.

   :::image type="content" source="../../media/mtp-eval-14.png" alt-text="Page Office 365 E5 configuration de l’enregistrement de la version d’essai dans laquelle vous pouvez définir votre identité d’entreprise" lightbox="../../media/mtp-eval-14.png":::

7. Cliquez **sur Passer au programme d’installation** pour terminer Office 365 E5 mise en service du client d’essai.

   :::image type="content" source="../../media/mtp-eval-15.png" alt-text="La page Office 365 E5 configuration de l’enregistrement de la version d’essai vous invite à cliquer sur Le bouton Aller au programme d’installation" lightbox="../../media/mtp-eval-15.png":::

8. Connecter votre domaine d’entreprise au Office 365 client. [Facultatif] Choisissez **Connecter domaine que vous possédez déjà** et tapez votre nom de domaine. Cliquez sur **Suivant**.

   :::image type="content" source="../../media/mtp-eval-16.png" alt-text="La page Office 365 E5 du programme d’installation dans laquelle vous devez personnaliser votre personnalisation de la signature et de la messagerie" lightbox="../../media/mtp-eval-16.png":::
 
9. Ajoutez un enregistrement TXT ou MX pour valider la propriété du domaine. Une fois que vous avez ajouté l’enregistrement TXT ou MX à votre domaine, sélectionnez **Vérifier**.

   :::image type="content" source="../../media/mtp-eval-17.png" alt-text="Page Office 365 E5'installation dans laquelle vous devez ajouter un TXT d’enregistrement MX pour vérifier votre domaine" lightbox="../../media/mtp-eval-17.png":::
 
10. [Facultatif] Créez d’autres comptes d’utilisateur pour votre client. Vous pouvez ignorer cette étape en cliquant sur **Suivant**.

    :::image type="content" source="../../media/mtp-eval-18.png" alt-text="Page Office 365 E5 de configuration dans laquelle vous pouvez ajouter d’autres utilisateurs" lightbox="../../media/mtp-eval-18.png":::
 
11. [Facultatif] Téléchargez Office applications. Cliquez **sur Suivant** pour ignorer cette étape. 

    :::image type="content" source="../../media/mtp-eval-19.png" alt-text="Page Office 365 E5 où vous pouvez installer vos applications Office applications" lightbox="../../media/mtp-eval-19.png":::

12. [Facultatif] Migrer les messages électroniques. Là encore, vous pouvez ignorer cette étape.

    :::image type="content" source="../../media/mtp-eval-20.png" alt-text="Le Office 365 E5 où vous pouvez définir s’il faut migrer ou non des messages électroniques" lightbox="../../media/mtp-eval-20.png":::
 
13. Choisissez des services en ligne. **Sélectionnez Exchange** puis cliquez sur **Suivant**. 

    :::image type="content" source="../../media/mtp-eval-21.png" alt-text="Le Office 365 E5 où vous pouvez choisir vos services en ligne" lightbox="../../media/mtp-eval-21.png":::

14. Ajoutez des enregistrements MX, CNAME et TXT à votre domaine. Lorsque vous avez terminé, sélectionnez **Vérifier**.

    :::image type="content" source="../../media/mtp-eval-22.png" alt-text="Le Office 365 E5 ici, vous pouvez ajouter vos enregistrements DNS" lightbox="../../media/mtp-eval-22.png":::
 
15. Félicitations, vous avez terminé la mise en service de votre Office 365 client.

    :::image type="content" source="../../media/mtp-eval-23.png" alt-text="Page de confirmation Office 365 E5 fin de l’installation" lightbox="../../media/mtp-eval-23.png":::
    

## <a name="enable-microsoft-365-trial-subscription"></a>Activer l Microsoft 365 d’essai

>[!NOTE]
>L’inscription à une version d’essai vous donne 25 licences utilisateur à utiliser pendant un mois. Pour [plus d’informations, voir Essayer ou acheter Microsoft 365 abonnement](../../commerce/try-or-buy-microsoft-365.md).

1. À [partir Administration Microsoft 365, cliquez](https://admin.microsoft.com/) sur **Facturation**, puis accédez à **Acheter des services**.

2. Sélectionnez **Microsoft 365 E5** puis cliquez **sur Démarrer la version d’essai gratuite**. 

   :::image type="content" source="../../media/mtp-eval-24.png" alt-text="Page d Microsoft 365 E5 de démarrage gratuit" lightbox="../../media/mtp-eval-24.png":::

3. Choisissez votre préférence de vérification : via un SMS ou un appel. Une fois que vous avez décidé, entrez le numéro de téléphone, sélectionnez **M’envoyer** un sms ou **m’appeler** en fonction de votre sélection.

   :::image type="content" source="../../media/mtp-eval-25.png" alt-text="La page Microsoft 365 E5 d’essai gratuit de l’application vous demandant des coordonnées pour envoyer du code pour prouver que vous n’êtes pas un robot" lightbox="../../media/mtp-eval-25.png":::
 
4. Entrez le code de vérification, puis cliquez **sur Démarrer votre version d’essai gratuite**.

   :::image type="content" source="../../media/mtp-eval-26.png" alt-text="La page Microsoft 365 E5 d’essai gratuit où vous pouvez remplir le code de vérification envoyé par le système pour prouver que vous n’êtes pas un robot" lightbox="../../media/mtp-eval-26.png":::

5. Cliquez **sur Essayer maintenant** pour confirmer votre Microsoft 365 E5 d’essai.

   :::image type="content" source="../../media/mtp-eval-27.png" alt-text="La page Microsoft 365 E5 d’essai gratuit où vous devez horloger le bouton Essayer maintenant pour démarrer" lightbox="../../media/mtp-eval-27.png":::
 
6. Go to the **Administration Microsoft 365** **CenterUsersActive** >  >  **users**. Sélectionnez votre compte d’utilisateur, sélectionnez Gérer les **licences** de produits, puis remplacez la licence de Office 365 E5 par **Microsoft 365 E5**. Cliquez sur **Enregistrer**.

   :::image type="content" source="../../media/mtp-eval-28.png" alt-text="Page Administration Microsoft 365 centre de données dans laquelle vous pouvez sélectionner la licence Microsoft 365 E5 licence" lightbox="../../media/mtp-eval-28.png":::
 
7. Sélectionnez de nouveau le compte Administrateur général, puis cliquez **sur Gérer le nom d’utilisateur**.

   :::image type="content" source="../../media/mtp-eval-29.png" alt-text="La page Administration Microsoft 365 centre de gestion où vous pouvez sélectionner Compte et Gérer le nom d’utilisateur" lightbox="../../media/mtp-eval-29.png":::

8. [Facultatif] Modifiez le domaine de *onmicrosoft.com* à votre propre domaine, en fonction de ce que vous avez choisi lors des étapes précédentes. Cliquez sur **Enregistrer les modifications**.

   :::image type="content" source="../../media/mtp-eval-30.png" alt-text="Page Administration Microsoft 365 centre de noms dans laquelle vous pouvez modifier vos préférences de domaine" lightbox="../../media/mtp-eval-30.png":::

## <a name="next-step"></a>Étape suivante
|[Phase 3 : Configurer & intégré](config-m365d-eval.md) | Configurez chaque pilier Microsoft 365 Defender pour votre laboratoire d Microsoft 365 Defender ou votre environnement pilote et intégrer vos points de terminaison.
|:-------|:-----|
