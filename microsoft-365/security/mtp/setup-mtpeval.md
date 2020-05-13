---
title: Configurer votre environnement de laboratoire d’évaluation de la protection contre les menaces Microsoft
description: Accédez au centre de sécurité Microsoft 365, puis configurez votre environnement de laboratoire d’évaluation de la protection contre les menaces Microsoft.
keywords: Programme d’installation de la protection contre les menaces Microsoft, essayez le programme d’évaluation de Microsoft Threat Protection.
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
ms.collection: M365-security-compliance
ms.topic: article
ms.openlocfilehash: 117681bd4722615e870594e46d6896e9128d0d0c
ms.sourcegitcommit: 93c0088d272cd45f1632a1dcaf04159f234abccd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "44209222"
---
# <a name="set-up-your-microsoft-threat-protection-trial-lab-environment"></a>Configurer votre environnement de laboratoire d’évaluation de la protection contre les menaces Microsoft 

**S’applique à :**
- Protection Microsoft contre les menaces 


La création d’un environnement de laboratoire de test Microsoft Threat Protection et son déploiement est un processus en trois phases :

<br>
<table border="0" width="100%" align="center">
  <tr style="text-align:center;">
    <td align="center" style="width:25%; border:0;" >
      <a href= "https://docs.microsoft.com/microsoft-365/security/mtp/prepare-mtpeval?view=o365-worldwide"> 
        <img src="../../media/prepare.png" alt="Prepare your Microsoft Threat Protection trial lab environment" title="Préparer votre atelier d’évaluation de la protection contre les menaces Microsoft" />
      <br/>Phase 1 : préparer</a><br>
    </td>
     <td align="center"bgcolor="#d5f5e3">
      <a href="https://docs.microsoft.com/microsoft-365/security/mtp/setup-mtpeval?view=o365-worldwide">
        <img src="../../media/setup.png" alt="Set up your Microsoft Threat Protection trial lab environment" title="Configurer votre atelier d’évaluation de la protection contre les menaces Microsoft" />
      <br/>Phase 2 : configuration</a><br>
    </td>
    <td align="center">
      <a href="https://docs.microsoft.com/microsoft-365/security/mtp/config-mtpeval?view=o365-worldwide">
        <img src="../../media/config-onboard.png" alt="
Configure each Microsoft Threat Protection pillar for your Microsoft Threat Protection trial lab environment and onboard your endpoints" title="
Configurez chaque pilier de protection contre les menaces Microsoft pour votre environnement de laboratoire d’évaluation de la protection contre les menaces Microsoft et embarquez vos points de terminaison." />
      <br/>Phase 3 : configurer & Onboard</a><br>
</td>


  </tr>
</table>

Vous êtes actuellement dans la phase de configuration. Suivez les étapes initiales pour accéder au centre de sécurité Microsoft 365, puis configurez votre environnement de laboratoire d’évaluation.

Inscrivez-vous à un abonnement Office 365 ou Azure Active Directory pour générer un client *. onmicrosoft.com* que vous pouvez utiliser pour vous inscrire à votre licence Microsoft 365 E5. 

>[!NOTE]
>Si vous disposez déjà d’un abonnement Office 365 ou Azure Active Directory existant, vous pouvez ignorer les étapes de création d’un client d’évaluation d’Office 365 E5.

Dans cette phase, vous serez guidé pour :
- Créer un client d’évaluation Office 365 E5
- Activer l’abonnement à la version d’évaluation de Microsoft 365


## <a name="create-an-office-365-e5-trial-tenant"></a>Créer un client d’évaluation Office 365 E5
>[!NOTE]
>Si vous disposez déjà d’un abonnement Office 365 ou Azure Active Directory existant, vous pouvez ignorer les étapes de création d’un client d’évaluation d’Office 365 E5.

1. Accédez au [portail produit Office 365 E5](https://www.microsoft.com/microsoft-365/business/office-365-enterprise-e5-business-software?activetab=pivot%3aoverviewtab) et sélectionnez **version d’évaluation gratuite**.
![Image of_Office 365 E5 page d’évaluation gratuite](../../media/mtp-eval-9.png) <br>
  
2. Terminez l’enregistrement de la version d’évaluation en saisissant votre adresse de courrier (personnel ou d’entreprise). Cliquez sur **configurer le compte**.
![Image of_Office 365 E5 page de configuration de l’enregistrement de la version d’évaluation](../../media/mtp-eval-10.png) <br> 

3. Indiquez votre prénom, nom, numéro de téléphone professionnel, nom de la société, taille de la société et pays ou région.  
<br>![Image of_Office 365 E5 page de configuration de l’enregistrement de la version d’évaluation demandant des informations sur le nom, le téléphone et la société](../../media/mtp-eval-11.png) <br>
>[!NOTE]
>Le pays ou la région que vous définissez ici détermine la région de centre de données que votre Office 365 sera hébergée.
  
4. Choisissez vos préférences de vérification : par le biais d’un message texte ou d’un appel. Cliquez sur **Envoyer un code de vérification**. 
![Image of_Office 365 E5 page de configuration de l’enregistrement de la version d’évaluation demandant une préférence de vérification](../../media/mtp-eval-12.png) <br>

5. Définissez le nom de domaine personnalisé pour votre client, puis cliquez sur **suivant**.
<br>![Image of_Office 365 E5 page de configuration de l’enregistrement d’évaluation où vous pouvez configurer votre nom de domaine personnalisé](../../media/mtp-eval-13.png) <br>
 
6. Configurez la première identité qui sera un administrateur général pour le client. Indiquez le **nom** et le **mot de passe**. Cliquez sur **Inscription**.
![Image of_Office 365 E5 page de configuration de l’enregistrement d’évaluation où vous pouvez définir l’identité de votre entreprise](../../media/mtp-eval-14.png) <br>

7. Cliquez sur **accéder au programme d’installation** pour terminer la mise en service du client version d’évaluation d’Office 365 E5.
<br>![Image de la page de configuration de l’inscription à la version d’évaluation d’Office 365 E5 invitant à cliquer sur le bouton Go Setup](../../media/mtp-eval-15.png) <br>

8. Connectez votre domaine d’entreprise au client Office 365. Module Choisissez **connecter un domaine que vous possédez déjà** et tapez votre nom de domaine. Cliquez sur **Suivant**.
<br>![Image of_Office 365 E5 page de configuration où vous devez personnaliser votre connexion et votre courrier électronique](../../media/mtp-eval-16.png) <br>
 
9. Vous devrez ajouter un enregistrement TXT ou MX pour valider la propriété de domaine. Une fois que vous avez ajouté l’enregistrement TXT ou MX à votre domaine, sélectionnez **vérifier**.
<br>![Image of_Office 365 E5 page de configuration où vous devez ajouter un fichier TXT de l’enregistrement MX pour vérifier votre domaine](../../media/mtp-eval-17.png) <br>
 
10. Module Créez des comptes d’utilisateur supplémentaires pour votre client. Vous pouvez ignorer cette étape en cliquant sur **suivant**.
![Image of_Office 365 E5 page de configuration où vous pouvez ajouter d’autres utilisateurs](../../media/mtp-eval-18.png) <br>
 
11. Module Téléchargez les applications Office. Cliquez sur **suivant** pour ignorer cette étape. 
<br>![Image of_Office 365 E5 page où vous pouvez installer vos applications Office](../../media/mtp-eval-19.png) <br>

12. Module Migrez les messages électroniques. Encore une fois, vous pouvez ignorer cette étape.
<br>![Image of_Office 365 E5 où vous pouvez choisir de migrer les messages électroniques ou non](../../media/mtp-eval-20.png) <br>
 
13. Sélectionnez services en ligne. Sélectionnez **Exchange** , puis cliquez sur **suivant**. 
<br>![Image of_Office 365 E5 où vous pouvez choisir vos services en ligne tels que Microsoft Skype entreprise ou la gestion des appareils Mibile pour Office 365](../../media/mtp-eval-21.png) <br>

14. Ajoutez des enregistrements MX, CNAMe et TXT à votre domaine. Lorsque vous avez terminé, sélectionnez **vérifier**.
<br>![Image of_Office 365 E5 ici, vous pouvez ajouter vos enregistrements DNS](../../media/mtp-eval-22.png) <br>
 
15. Félicitations, vous avez terminé la mise en service de votre client Office 365.
<br>![Image of_Office 365 E5 page de confirmation de l’exécution du programme d’installation](../../media/mtp-eval-23.png) <br>

## <a name="enable-microsoft-365-trial-subscription"></a>Activer l’abonnement à la version d’évaluation de Microsoft 365

>[!NOTE]
>L’inscription à une version d’évaluation vous donne 25 licences utilisateur à utiliser pour un mois. Pour plus d’informations, voir [essayer ou acheter un abonnement M365](https://docs.microsoft.com/microsoft-365/commerce/try-or-buy-microsoft-365?view=o365-worldwide#try-or-buy-a-microsoft-365-subscription-1) .

1. Dans le [Centre d’administration Microsoft 365](https://admin.microsoft.com/), cliquez sur **facturation** , puis accédez à **acheter des services**.

2. Sélectionnez **Microsoft 365 E5** , puis cliquez sur **Démarrer la version d’évaluation gratuite**. 
![Image of_Microsoft 365 E5 page d’évaluation gratuite Start](../../media/mtp-eval-24.png) <br>

3. Choisissez vos préférences de vérification : par le biais d’un message texte ou d’un appel. Une fois que vous avez décidé, entrez le numéro de téléphone, sélectionnez **me texte** ou **appelez-moi** en fonction de votre sélection.
![Image of_Microsoft 365 E5 page d’évaluation gratuite demande de coordonnées pour envoyer du code pour prouver que vous n’êtes pas un robot](../../media/mtp-eval-25.png) <br>
 
4. Entrez le code de vérification, puis cliquez sur **Démarrer votre version d’évaluation gratuite**. 
<br>![Image of_Microsoft 365 E5 page d’évaluation gratuite où vous pouvez renseigner le code de vérification le système envoyé pour prouver que vous n’êtes pas un automate](../../media/mtp-eval-26.png) <br>

5. Cliquez sur **essayer maintenant** pour confirmer votre version d’évaluation de Microsoft 365 E5.
<br>![Image of_Microsoft 365 E5 page de la version d’évaluation gratuite où vous devez pointer le bouton essayer maintenant pour démarrer](../../media/mtp-eval-27.png) <br>
 
6. Accédez au **Centre d’administration Microsoft 365**  >  **utilisateurs**  >  **actifs**. Sélectionnez votre compte d’utilisateur, sélectionnez **gérer les licences de produits**, puis échangez la licence d’Office 365 E5 à **Microsoft 365 E5**. Cliquez sur **Enregistrer**.
![Page du centre d’administration de l’image of_Microsoft 365, dans laquelle vous pouvez sélectionner Microsoft 365 E5 licence](../../media/mtp-eval-28.png) <br>
 
7. Sélectionnez à nouveau le compte d’administrateur général, puis cliquez sur **gérer le nom d’utilisateur**.
<br>![Page du centre d’administration de l’image of_Microsoft 365, dans laquelle vous pouvez sélectionner un compte, puis gérer le nom d’utilisateur](../../media/mtp-eval-29.png) <br>

8. Module Modifiez le domaine de *onmicrosoft.com* à votre propre domaine, en fonction de ce que vous avez choisi lors des étapes précédentes. Cliquez sur **Enregistrer les modifications**.
<br>![Page du centre d’administration de l’image of_Microsoft 365, dans laquelle vous pouvez modifier votre préférence de domaine](../../media/mtp-eval-30.png) <br>



## <a name="next-step"></a>Étape suivante
||| | :-------| :-----| config-Onboard. png) <br>[Phase 3 : configurer & Onboard](config-mtpeval.md) | Configurez chaque pilier de protection contre les menaces Microsoft pour votre environnement de laboratoire de test Microsoft Threat Protection et intégrez vos points de terminaison.
