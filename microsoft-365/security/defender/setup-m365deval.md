---
title: Configurer votre environnement pilote ou labo d’essai Microsoft 365 Defender
description: Accédez Microsoft 365 Defender portail, puis configurez votre environnement de laboratoire d’essai Microsoft 365 Defender
keywords: Microsoft 365 Defender configuration d’essai, Microsoft 365 Defender configuration pilote, essayez Microsoft 365 Defender, Microsoft 365 Defender configuration du laboratoire d’évaluation
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: lovina-saldanha
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- m365solution-scenario
- m365solution-evalutatemtp
- highpri
- tier1
ms.topic: conceptual
ms.openlocfilehash: 6eafed1510fa478cbb0012437bf5cc7a6254dc98
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68640607"
---
# <a name="set-up-your-microsoft-365-defender-trial-in-a-lab-environment"></a>Configurer votre version d’évaluation Microsoft 365 Defender dans un environnement lab 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender 

Cette rubrique vous guide dans la configuration d’un environnement lab dédié. Pour plus d’informations sur la configuration d’un essai en production, consultez le nouveau guide [Évaluer et piloter Microsoft 365 Defender](eval-overview.md). 

## <a name="create-an-office-365-e5-trial-tenant"></a>Créer un locataire d’essai Office 365 E5
>[!NOTE]
>Si vous disposez déjà d’un abonnement Office 365 ou Azure Active Directory, vous pouvez ignorer les étapes de création du locataire d’essai Office 365 E5.

1. Accédez au [portail de produit Office 365 E5](https://www.microsoft.com/microsoft-365/business/office-365-enterprise-e5-business-software?activetab=pivot%3aoverviewtab) et sélectionnez **Essai gratuit**.

   :::image type="content" source="../../media/mtp-eval-9.png" alt-text="La Office 365 E5 page d’évaluation gratuite" lightbox="../../media/mtp-eval-9.png":::
  
2. Terminez l’inscription de la version d’évaluation en entrant votre adresse e-mail (personnelle ou d’entreprise). Cliquez sur **Configurer le compte**.

   :::image type="content" source="../../media/mtp-eval-10.png" alt-text="Page Office 365 E5 configuration de l’inscription d’essai" lightbox="../../media/mtp-eval-10.png":::

3. Renseignez votre prénom, votre nom, votre numéro de téléphone professionnel, votre nom d’entreprise, votre taille d’entreprise et votre pays ou région.  

   :::image type="content" source="../../media/mtp-eval-11.png" alt-text="Page d’installation de l’inscription Office 365 E5 d’essai demandant le nom, le téléphone et les détails de l’entreprise" lightbox="../../media/mtp-eval-11.png":::
   
   > [!NOTE]
   > Le pays ou la région que vous définissez ici détermine la région du centre de données que votre Office 365 sera hébergée.
  
4. Choisissez votre préférence de vérification : via un SMS ou un appel. Cliquez sur **Envoyer le code de vérification**. 

   :::image type="content" source="../../media/mtp-eval-12.png" alt-text="Page Office 365 E5 configuration de l’inscription d’essai demandant une préférence de vérification" lightbox="../../media/mtp-eval-12.png":::

5. Définissez le nom de domaine personnalisé de votre locataire, puis cliquez sur **Suivant**.

   :::image type="content" source="../../media/mtp-eval-13.png" alt-text="Page Office 365 E5 configuration de l’inscription d’essai où vous pouvez configurer votre nom de domaine personnalisé" lightbox="../../media/mtp-eval-13.png":::
 
6. Configurez la première identité, qui sera un administrateur général pour le locataire. Renseignez le **nom** et le **mot de passe**. Cliquez sur **S’inscrire**.

   :::image type="content" source="../../media/mtp-eval-14.png" alt-text="Page Office 365 E5 configuration de l’inscription d’essai où vous pouvez définir votre identité d’entreprise" lightbox="../../media/mtp-eval-14.png":::

7. Cliquez sur **Accéder au programme d’installation** pour terminer l’approvisionnement du client d’essai Office 365 E5.

   :::image type="content" source="../../media/mtp-eval-15.png" alt-text="La page Office 365 E5 configuration de l’inscription d’essai vous invitant à cliquer sur le bouton Atteindre le programme d’installation" lightbox="../../media/mtp-eval-15.png":::

8. Connectez votre domaine d’entreprise au locataire Office 365. [Facultatif] Choisissez **Connecter un domaine que vous possédez déjà** et tapez votre nom de domaine. Cliquez sur **Suivant**.

   :::image type="content" source="../../media/mtp-eval-16.png" alt-text="Page d’installation Office 365 E5 dans laquelle vous devez personnaliser votre connexion et votre e-mail" lightbox="../../media/mtp-eval-16.png":::
 
9. Ajoutez un enregistrement TXT ou MX pour valider la propriété du domaine. Une fois que vous avez ajouté l’enregistrement TXT ou MX à votre domaine, sélectionnez **Vérifier**.

   :::image type="content" source="../../media/mtp-eval-17.png" alt-text="Page d’installation Office 365 E5 dans laquelle vous devez ajouter un enregistrement TXT de MX pour vérifier votre domaine" lightbox="../../media/mtp-eval-17.png":::
 
10. [Facultatif] Créez d’autres comptes d’utilisateur pour votre locataire. Vous pouvez ignorer cette étape en cliquant sur **Suivant**.

    :::image type="content" source="../../media/mtp-eval-18.png" alt-text="Page d’installation Office 365 E5 où vous pouvez ajouter d’autres utilisateurs" lightbox="../../media/mtp-eval-18.png":::
 
11. [Facultatif] Téléchargez les applications Office. Cliquez sur **Suivant** pour ignorer cette étape. 

    :::image type="content" source="../../media/mtp-eval-19.png" alt-text="Page Office 365 E5 où vous pouvez installer vos applications Office" lightbox="../../media/mtp-eval-19.png":::

12. [Facultatif] Migrer des messages électroniques. Là encore, vous pouvez ignorer cette étape.

    :::image type="content" source="../../media/mtp-eval-20.png" alt-text="Le Office 365 E5 où vous pouvez définir s’il faut ou non migrer des messages électroniques" lightbox="../../media/mtp-eval-20.png":::
 
13. Choisissez services en ligne. Sélectionnez **Exchange** , puis cliquez sur **Suivant**. 

    :::image type="content" source="../../media/mtp-eval-21.png" alt-text="Le Office 365 E5 où vous pouvez choisir votre services en ligne" lightbox="../../media/mtp-eval-21.png":::

14. Ajoutez des enregistrements MX, CNAME et TXT à votre domaine. Une fois l’opération terminée, **sélectionnez Vérifier**.

    :::image type="content" source="../../media/mtp-eval-22.png" alt-text="Le Office 365 E5 ici, vous pouvez ajouter vos enregistrements DNS" lightbox="../../media/mtp-eval-22.png":::
 
15. Félicitations, vous avez terminé l’approvisionnement de votre locataire Office 365.

    :::image type="content" source="../../media/mtp-eval-23.png" alt-text="Page de confirmation de la fin de la configuration Office 365 E5" lightbox="../../media/mtp-eval-23.png":::
    

## <a name="enable-microsoft-365-trial-subscription"></a>Activer l’abonnement d’évaluation Microsoft 365

>[!NOTE]
>L’inscription à une version d’évaluation vous donne 25 licences utilisateur à utiliser pendant un mois. Pour plus d’informations, consultez [Essayer ou acheter un abonnement Microsoft 365](../../commerce/try-or-buy-microsoft-365.md) .

1. Dans [Administration Microsoft 365 Centre](https://admin.microsoft.com/), cliquez sur **Facturation**, puis accédez à **Acheter des services**.

2. Sélectionnez **Microsoft 365 E5**, puis cliquez sur **Démarrer la version d’évaluation gratuite**. 

   :::image type="content" source="../../media/mtp-eval-24.png" alt-text="Page d’évaluation gratuite Microsoft 365 E5 Start" lightbox="../../media/mtp-eval-24.png":::

3. Choisissez votre préférence de vérification : via un SMS ou un appel. Une fois que vous avez choisi, entrez le numéro de téléphone, sélectionnez **Me** texte ou **Appelez-moi** en fonction de votre sélection.

   :::image type="content" source="../../media/mtp-eval-25.png" alt-text="La Microsoft 365 E5 page d’essai gratuit demandant des coordonnées pour envoyer du code pour prouver que vous n’êtes pas un robot" lightbox="../../media/mtp-eval-25.png":::
 
4. Entrez le code de vérification, puis cliquez sur **Démarrer votre version d’évaluation gratuite**.

   :::image type="content" source="../../media/mtp-eval-26.png" alt-text="La Microsoft 365 E5 page d’essai gratuit où vous pouvez remplir le code de vérification que le système a envoyé pour prouver que vous n’êtes pas un robot" lightbox="../../media/mtp-eval-26.png":::

5. Cliquez **sur Essayer maintenant** pour confirmer votre version d’évaluation Microsoft 365 E5.

   :::image type="content" source="../../media/mtp-eval-27.png" alt-text="La page Microsoft 365 E5 Démarrer la version d’évaluation gratuite où vous devez horloger le bouton Essayer maintenant pour démarrer" lightbox="../../media/mtp-eval-27.png":::
 
6. Accédez à l’Administration Microsoft 365 **Utilisateurs actifs** >  **du Centre** > . Sélectionnez votre compte d’utilisateur, sélectionnez **Gérer les licences de produit**, puis remplacez la licence de Office 365 E5 par **Microsoft 365 E5**. Cliquez sur **Enregistrer**.

   :::image type="content" source="../../media/mtp-eval-28.png" alt-text="Page centre Administration Microsoft 365 dans laquelle vous pouvez sélectionner la licence Microsoft 365 E5" lightbox="../../media/mtp-eval-28.png":::
 
7. Sélectionnez à nouveau le compte d’administrateur général, puis cliquez sur **Gérer le nom d’utilisateur**.

   :::image type="content" source="../../media/mtp-eval-29.png" alt-text="Page centre Administration Microsoft 365 dans laquelle vous pouvez sélectionner Compte et Gérer le nom d’utilisateur" lightbox="../../media/mtp-eval-29.png":::

8. [Facultatif] Remplacez le domaine *onmicrosoft.com* par votre propre domaine, en fonction de ce que vous avez choisi lors des étapes précédentes. Cliquez sur **Enregistrer les modifications**.

   :::image type="content" source="../../media/mtp-eval-30.png" alt-text="Page Administration Microsoft 365 Center dans laquelle vous pouvez modifier vos préférences de domaine" lightbox="../../media/mtp-eval-30.png":::

## <a name="next-step"></a>Étape suivante
|[Phase 3 : Configurer & Onboard](config-m365d-eval.md) | Configurez chaque pilier Microsoft 365 Defender pour votre environnement de laboratoire d’essai ou pilote Microsoft 365 Defender et intégrer vos points de terminaison.
|:-------|:-----|
