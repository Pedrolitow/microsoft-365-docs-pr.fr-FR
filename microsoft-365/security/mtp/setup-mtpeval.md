---
title: Configuration de votre laboratoire d’évaluation Microsoft 365 Defender ou de votre environnement pilote
description: Accédez au centre de sécurité Microsoft 365, puis configurez votre environnement de laboratoire de test Microsoft 365 Defender.
keywords: Programme d’installation de la protection contre les menaces Microsoft, programme d’installation pilote de Microsoft Threat Protection, essayez Microsoft Threat Protection, programme d’évaluation de la protection contre les menaces Microsoft
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: w10
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dolmont
author: DulceMontemayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: article
ms.openlocfilehash: 503b7a6a6b3ad6394293e9f70dbdd336f6bee9dd
ms.sourcegitcommit: ce46d1bd67091d4ed0e2b776dfed55e2d88cdbf4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "49131308"
---
# <a name="set-up-your-microsoft-365-defender-trial-lab-environment"></a>Configuration de votre environnement de laboratoire de test Microsoft 365 Defender 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender 


La création d’un laboratoire de test Microsoft 365 Defender ou d’un environnement pilote et son déploiement est un processus en trois phases :

|[![Phase 1 : préparer](../../media/phase-diagrams/prepare.png)](prepare-mtpeval.md)<br/>[Phase 1 : préparer](prepare-mtpeval.md) |![Phase 2 : configurer](../../media/phase-diagrams/setup.png)<br/>Phase 2 : configurer |[![Phase 3 : intégration](../../media/phase-diagrams/onboard.png)](config-mtpeval.md)<br/>[Phase 3 : intégration](config-mtpeval.md) | [![Retour au pilote](../../media/phase-diagrams/backtopilot.png)](mtp-pilot.md)<br/>[Retour au manuel pilote](mtp-pilot.md) |
|--|--|--|--|
||*Vous êtes là !*  | | |


Vous êtes actuellement dans la phase de configuration. Suivez les étapes initiales pour accéder au centre de sécurité Microsoft 365, puis configurez votre laboratoire d’évaluation ou votre environnement pilote.

Inscrivez-vous à un abonnement Office 365 ou Azure Active Directory pour générer un client *. onmicrosoft.com* que vous pouvez utiliser pour vous inscrire à votre licence Microsoft 365 E5. 

>[!NOTE]
>Si vous disposez déjà d’un abonnement Office 365 ou Azure Active Directory existant, vous pouvez ignorer les étapes de création d’une version d’évaluation d’Office 365 E5 ou de client pilote.

Dans cette phase, vous serez guidé pour :
- Créer un client d’évaluation Office 365 E5
- Activer l’abonnement à la version d’évaluation de Microsoft 365


## <a name="create-an-office-365-e5-trial-tenant"></a>Créer un client d’évaluation Office 365 E5
>[!NOTE]
>Si vous disposez déjà d’un abonnement Office 365 ou Azure Active Directory existant, vous pouvez ignorer les étapes de création d’un client d’évaluation d’Office 365 E5.

1. Accédez au [portail produit Office 365 E5](https://www.microsoft.com/microsoft-365/business/office-365-enterprise-e5-business-software?activetab=pivot%3aoverviewtab) et sélectionnez **version d’évaluation gratuite**.

   ![Image of_Office 365 E5 page d’évaluation gratuite](../../media/mtp-eval-9.png)
  
2. Terminez l’enregistrement de la version d’évaluation en saisissant votre adresse de courrier (personnel ou d’entreprise). Cliquez sur **configurer le compte**.

   ![Image of_Office 365 E5 page de configuration de l’enregistrement de la version d’évaluation](../../media/mtp-eval-10.png)

3. Renseignez votre prénom, nom, numéro de téléphone professionnel, nom de la société, taille de la société et pays ou région.  

   ![Image of_Office 365 E5 page de configuration de l’enregistrement de la version d’évaluation demandant des informations sur le nom, le téléphone et la société](../../media/mtp-eval-11.png)
   
   > [!NOTE]
   > Le pays ou la région que vous définissez ici détermine la région de centre de données que votre Office 365 sera hébergée.
  
4. Choisissez vos préférences de vérification : par le biais d’un message texte ou d’un appel. Cliquez sur **Envoyer un code de vérification**. 

   ![Image of_Office 365 E5 page de configuration de l’enregistrement de la version d’évaluation demandant une préférence de vérification](../../media/mtp-eval-12.png)

5. Définissez le nom de domaine personnalisé pour votre client, puis cliquez sur **suivant**.

   ![Image of_Office 365 E5 page de configuration de l’enregistrement d’évaluation où vous pouvez configurer votre nom de domaine personnalisé](../../media/mtp-eval-13.png)
 
6. Configurez la première identité, qui sera un administrateur général pour le client. Indiquez le **nom** et le **mot de passe**. Cliquez sur **Inscription**.

   ![Image of_Office 365 E5 page de configuration de l’enregistrement d’évaluation où vous pouvez définir l’identité de votre entreprise](../../media/mtp-eval-14.png)

7. Cliquez sur **accéder au programme d’installation** pour terminer la mise en service du client version d’évaluation d’Office 365 E5.

   ![Image de la page de configuration de l’inscription à la version d’évaluation d’Office 365 E5 invitant à cliquer sur le bouton Go Setup](../../media/mtp-eval-15.png)

8. Connectez votre domaine d’entreprise au client Office 365. Module Choisissez **connecter un domaine que vous possédez déjà** et tapez votre nom de domaine. Cliquez sur **Suivant**.

   ![Image of_Office 365 E5 page de configuration où vous devez personnaliser votre connexion et votre courrier électronique](../../media/mtp-eval-16.png)
 
9. Ajoutez un enregistrement TXT ou MX pour valider la propriété de domaine. Une fois que vous avez ajouté l’enregistrement TXT ou MX à votre domaine, sélectionnez **vérifier**.

   ![Image of_Office 365 E5 page de configuration où vous devez ajouter un fichier TXT de l’enregistrement MX pour vérifier votre domaine](../../media/mtp-eval-17.png)
 
10. Module Créez des comptes d’utilisateur supplémentaires pour votre client. Vous pouvez ignorer cette étape en cliquant sur **suivant**.

    ![Image of_Office 365 E5 page de configuration où vous pouvez ajouter d’autres utilisateurs](../../media/mtp-eval-18.png)
 
11. Module Téléchargez les applications Office. Cliquez sur **suivant** pour ignorer cette étape. 

    ![Image of_Office 365 E5 page où vous pouvez installer vos applications Office](../../media/mtp-eval-19.png)

12. Module Migrez les messages électroniques. Encore une fois, vous pouvez ignorer cette étape.

    ![Image of_Office 365 E5 où vous pouvez choisir de migrer les messages électroniques ou non](../../media/mtp-eval-20.png)
 
13. Sélectionnez services en ligne. Sélectionnez **Exchange** , puis cliquez sur **suivant**. 

    ![Image of_Office 365 E5 où vous pouvez choisir vos services en ligne](../../media/mtp-eval-21.png)

14. Ajoutez des enregistrements MX, CNAMe et TXT à votre domaine. Lorsque vous avez terminé, sélectionnez **vérifier**.

    ![Image of_Office 365 E5 ici, vous pouvez ajouter vos enregistrements DNS](../../media/mtp-eval-22.png)
 
15. Félicitations, vous avez terminé la mise en service de votre client Office 365.

    ![Image of_Office 365 E5 page de confirmation de l’exécution du programme d’installation](../../media/mtp-eval-23.png)

## <a name="enable-microsoft-365-trial-subscription"></a>Activer l’abonnement à la version d’évaluation de Microsoft 365

>[!NOTE]
>L’inscription à une version d’évaluation vous donne 25 licences utilisateur à utiliser pour un mois. Pour plus d’informations, voir [essayer ou acheter un abonnement M365](https://docs.microsoft.com/microsoft-365/commerce/try-or-buy-microsoft-365#try-or-buy-a-microsoft-365-subscription-1) .

1. Dans le [Centre d’administration Microsoft 365](https://admin.microsoft.com/), cliquez sur **facturation** , puis accédez à **acheter des services**.

2. Sélectionnez **Microsoft 365 E5** , puis cliquez sur **Démarrer la version d’évaluation gratuite**. 

   ![Image of_Microsoft 365 E5 page d’évaluation gratuite Start](../../media/mtp-eval-24.png)

3. Choisissez vos préférences de vérification : par le biais d’un message texte ou d’un appel. Une fois que vous avez décidé, entrez le numéro de téléphone, sélectionnez **me texte** ou **appelez-moi** en fonction de votre sélection.

   ![Image of_Microsoft 365 E5 page d’évaluation gratuite demande de coordonnées pour envoyer du code pour prouver que vous n’êtes pas un robot](../../media/mtp-eval-25.png)
 
4. Entrez le code de vérification, puis cliquez sur **Démarrer votre version d’évaluation gratuite**.

   ![Image of_Microsoft 365 E5 page d’évaluation gratuite où vous pouvez renseigner le code de vérification le système envoyé pour prouver que vous n’êtes pas un automate](../../media/mtp-eval-26.png)

5. Cliquez sur **essayer maintenant** pour confirmer votre version d’évaluation de Microsoft 365 E5.

   ![Image of_Microsoft 365 E5 page de la version d’évaluation gratuite où vous devez pointer le bouton essayer maintenant pour démarrer](../../media/mtp-eval-27.png)
 
6. Accédez au **Centre d’administration Microsoft 365**  >  **utilisateurs**  >  **actifs**. Sélectionnez votre compte d’utilisateur, sélectionnez **gérer les licences de produits**, puis échangez la licence d’Office 365 E5 à **Microsoft 365 E5**. Cliquez sur **Enregistrer**.

   ![Page du centre d’administration de l’image of_Microsoft 365, dans laquelle vous pouvez sélectionner Microsoft 365 E5 licence](../../media/mtp-eval-28.png)
 
7. Sélectionnez à nouveau le compte d’administrateur général, puis cliquez sur **gérer le nom d’utilisateur**.

   ![Page du centre d’administration de l’image of_Microsoft 365, dans laquelle vous pouvez sélectionner un compte, puis gérer le nom d’utilisateur](../../media/mtp-eval-29.png)

8. Module Modifiez le domaine de *onmicrosoft.com* à votre propre domaine, en fonction de ce que vous avez choisi lors des étapes précédentes. Cliquez sur **Enregistrer les modifications**.

   ![Page du centre d’administration de l’image of_Microsoft 365, dans laquelle vous pouvez modifier votre préférence de domaine](../../media/mtp-eval-30.png)



## <a name="next-step"></a>Étape suivante
|[Phase 3 : configurer & Onboard](config-mtpeval.md) | Configurez chaque pilier de Microsoft 365 Defender pour votre laboratoire de test Microsoft 365 Defender ou votre environnement pilote et embarquez vos points de terminaison.
|:-------|:-----|
