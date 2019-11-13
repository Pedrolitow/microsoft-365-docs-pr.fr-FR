---
title: Sécuriser les fichiers Teams dans un environnement de développement/test
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/31/2019
audience: ITPro
ms.topic: article
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: O365-seccomp
localization_priority: Priority
search.appverid:
- MET150
ms.assetid: 06af70f3-e7dc-4ee2-a385-fb4d61a5e93b
description: 'Résumé : créez des équipes d’équipes Sensible et Hautement confidentiel dans Microsoft Teams pour les fichiers dans un environnement de développement/test.'
ms.openlocfilehash: f22b3b1fbe07af6866206034ad6c9a90ced8a268
ms.sourcegitcommit: 6dfa646b9de30336dedfd0cac7320c57ad74ae11
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2019
ms.locfileid: "37929261"
---
# <a name="secure-teams-for-files-in-a-devtest-environment"></a>Sécuriser les fichiers Teams dans un environnement de développement/test

Cet article fournit des instructions détaillées pour créer un environnement de développement/test qui inclut les équipes sensibles et hautement confidentielles pour la solution [Sécuriser les fichiers dans Microsoft Teams](secure-files-in-teams.md).
  
![Équipes Sensibles et Hautement confidentielles dans Microsoft Teams pour les fichiers.](../media/sensitive-highly-confidential-teams-dev-test.png)
  
Utilisez cet environnement de développement/test pour expérimenter et affiner les paramètres de vos besoins spécifiques avant de déployer ces types d’équipes en production.
  
## <a name="phase-1-build-out-your-microsoft-365-enterprise-test-environment"></a>Phase 1 : Créer l’environnement de test Microsoft 365 Entreprise.

Si vous souhaitez simplement tester les équipes sensibles et hautement confidentielles de manière rapide avec une configuration minimale, suivez les instructions de [Configuration de base](https://docs.microsoft.com/microsoft-365/enterprise/lightweight-base-configuration-microsoft-365-enterprise).

Si vous voulez tester les équipes sensibles et hautement confidentielles au sein d’une entreprise simulée, suivez les instructions de [Synchronisation de hachage de mot de passe](https://docs.microsoft.com/microsoft-365/enterprise/password-hash-sync-m365-ent-test-environment).

>[!Note]
>Tester les équipes sensibles et hautement confidentielles ne requiert pas d’environnement de test en entreprise simulée, qui utilise un intranet simulé connecté à Internet et la synchronisation d’annuaire pour une forêt Active Directory. Domain Services (AD DS). Ceci est proposé comme option dans cet article afin que vous puissiez tester les équipes sensibles et hautement confidentielles et faire des essais dans un environnement qui représente une organisation classique.
>
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups-and-users"></a>Phase 2 : Création et configuration de vos groupes et utilisateurs Azure Active Directory (AD)

Dans cette phase, vous créez et vous configurez les groupes et les utilisateurs Azure AD de votre organisation fictive.
  
Commencez par créer deux groupes pour une organisation standard avec le portail Microsoft Azure.
  
1. Créez un onglet distinct dans votre navigateur, puis accédez au portail Microsoft Azure sous [https://portal.azure.com](https://portal.azure.com). Si nécessaire, connectez-vous avec les informations d’identification du compte d’administrateur général de votre abonnement ou essai Microsoft 365 E5.
    
2. Dans le portail Azure, cliquez sur **Azure Active Directory > Groupes**.
    
3. Dans le panneau **Groupes - Tous les groupes**, cliquez sur **+ Nouveau groupe**.
    
4. Dans le panneau **Groupe** :
    
  - Sélectionnez **Sécurité** dans **Type de groupe**.
    
  - Tapez **C-Suite** dans le champ **Nom**.
    
  - Sélectionnez **Affecté** dans le champ **Type d’appartenance**.
      
5. Cliquez sur **Créer** et fermez le panneau **Groupe**.
    
6.  Répétez les étapes 3-5 pour un nouveau groupe nommé **Équipe marketing**.
    
Ensuite, configurez l’octroi de licence automatique afin que des licences soient automatiquement attribuées aux membres de vos groupes pour les abonnements Office 365 et EMS.
  
1. Dans le portail Azure, cliquez sur **Azure Active Directory > Licences > Tous les produits**.
    
2. Dans la liste, sélectionnez **Microsoft 365 Entreprise E5**, puis cliquez sur **Attribuer**.
    
3. Dans le panneau **Affecter une licence**, cliquez sur **Utilisateurs et groupes**.
    
4. Dans la liste des groupes, sélectionnez les éléments suivants :
    
  - C-Suite
    
  - Équipe Marketing
    
5. Cliquez sur **Sélectionner**, puis sur **Affecter**.
    
6. Fermez l’onglet du portail Azure dans votre navigateur.
    
Ensuite, [connectez -vous au module PowerShell Azure Active Directory pour le module Graphique](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
Renseignez le nom de votre organisation, votre emplacement et un mot de passe commun, puis exécutez les commandes suivantes à partir de l’invite de commandes PowerShell ou de l’environnement de script intégré (ISE) pour créer des comptes d’utilisateur et les ajouter à leurs groupes :
  
```
$orgName="<organization name, such as contoso for the contoso.onmicrosoft.com trial subscription domain name>"
$location="<the ISO ALPHA2 country code, such as US for the United States>"
$commonPassword="<common password for all the new accounts>"

$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPassword

$groupName="C-Suite"
$userNames=@("CEO","CFO","CIO") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Marketing staff"
$userNames=@("Marketing1", "Marketing2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
```

> [!NOTE]
> L’utilisation ici d’un mot de passe courant est pour l’automatisation et la simplicité de configuration pour un environnement de développement et de test. Bien évidemment, cela est hautement déconseillé pour les abonnements de production. 
  
Utilisez ces étapes pour vérifier que la gestion des licences basée sur un groupe fonctionne correctement.
  
1. Sous l’onglet **Accueil Microsoft Office** de votre navigateur, cliquez sur la vignette **Administration**.
    
2. Sous le nouvel onglet **Centre d’administration Microsoft 365** de votre navigateur, cliquez sur **Utilisateurs**.
    
3. Dans la liste des utilisateurs, cliquez sur **PDG**.
    
4. Dans le volet qui affiche les propriétés du compte d’utilisateur **PDG**, vérifiez que les licences **Microsoft 365 Entreprise E5** lui ont été affectées (dans **Licences de produit**).
    
## <a name="phase-3-create-office-365-retention-labels"></a>Phase 3: Créer des étiquettes de rétention Office 365

Dans cette phase, vous allez créer les étiquettes de rétention correspondant aux différents niveaux de sécurité pour les dossiers de documents du site d’équipe SharePoint sous-jacent.

1. Se connecter au[Centre de conformité Microsoft 365](https://compliance.microsoft.com) avec votre compte d’administrateur général.
    
2. Sous l’onglet **Accueil- Conformité Microsoft 365** de votre navigateur, cliquez sur **Classifications > Étiquettes**.
    
3. Cliquez sur **Étiquettes de rétention > Créer une étiquette**.
    
4. Dans le volet**Nommer votre étiquette**, saisissez**Sensible**dans**Nommer votre étiquette**, puis cliquez sur**Suivant**.

5. Sur le volet**descripteurs de plan fichier**, cliquez sur **suivant**.
    
6. Dans le volet**Paramètres d’étiquette**, définissez, si nécessaire, la**Rétention** sur **Activé** puis cliquez sur **Suivant**.
    
7. Dans le volet **Vérifier vos paramètres**, cliquez sur **Créer l’étiquette**.
    
8. Répétez les étapes 3-7 pour une étiquette de rétention supplémentaire nommée **hautement confidentiel**.
    
9. Dans le volet **Accueil > Étiquettes**, cliquez sur **Publier des étiquettes**.
    
10. Dans le volet **Choisir les étiquettes à publier**, cliquez sur **Choisir les étiquettes à publier**.
    
11. Dans le volet **Choisir des étiquettes**, cliquez sur **Ajouter** et sélectionnez les quatre étiquettes.
    
12. Cliquez sur **Terminé**.
    
13. Dans le volet **Choisir les étiquettes à publier**, cliquez sur **Suivant**.
    
14. Dans le volet **Choisir les emplacements**, cliquez sur **Suivant**.
    
15. Dans le volet **Nom de votre stratégie**, saisissez **Exemple d’organisation** sous **Nom**, puis cliquez sur **Suivant**.
    
16. Dans le volet **Vérifier vos paramètres**, cliquez sur **Publier les étiquettes**, puis sur **Fermer**.
    
## <a name="phase-4-create-your-teams"></a>Phase 4 : créer vos équipes

Au cours de cette phase, vous créez et configurez des équipes sensibles et hautement confidentielles pour votre exemple d’organisation.

### <a name="sensitive-team-for-marketing-campaigns"></a>Équipe sensible pour les campagnes marketing

Pour créer une équipe de niveau sensible pour les membres du groupe marketing afin de collaborer sur des campagnes marketing en cours :

1. [Créez une équipe privée](https://support.office.com//article/create-a-team-from-scratch-174adf5f-846b-4780-b765-de1a0a737e2b) avec le nom **Campagnes marketing**.
2. Ouvrez l’équipe **Campagnes marketing**.
3.  Dans la barre d’outils de l’équipe, cliquez sur **Fichiers**.
4.  Cliquez sur les points de suspension, puis sur **Ouvrir dans SharePoint**.
5.  Dans la barre d’outils du site SharePoint sous-jacent, cliquez sur l’icône Paramètres, puis cliquez sur **Autorisations du site**.
6.  Dans le volet **Autorisations de site**, sous **Paramètres de partage**, cliquez sur **Modifier les paramètres de partage**.
7.  Sous **Autorisations de partage**, sélectionnez **Seuls les propriétaires du site peuvent partager des fichiers, des dossiers et le site**, puis cliquez sur **Enregistrer**.

Ensuite, configurez le dossier de documents du site SharePoint sous-jacent Campagnes marketing avec l’étiquette Sensible.

1.  Sous l’onglet **Campagne marketing - Accueil** de votre navigateur, cliquez sur **Documents**.
2.  Cliquez sur l’icône des paramètres, puis cliquez sur **Paramètres de la bibliothèque**.
3.  Sous **Autorisations et gestion**, cliquez sur **Appliquer l’étiquette aux éléments de cette bibliothèque**.
4.  Dans **Paramètres - Appliquer l’étiquette**, sélectionnez **Sensible**, puis cliquez sur **Enregistrer**. 

Ensuite, configurez une stratégie de protection contre la perte de données qui avertit les utilisateurs quand ils partagent un document sur un site SharePoint sous-jacent avec l’étiquette Sensible, qui inclut le site Campagnes marketing, en dehors de l’organisation.

1. Se connecter au[portail de conformité de Microsoft 365](https://compliance.microsoft.com/) avec votre compte d’administrateur général.
    
2. Sous le nouvel onglet **Conformité Microsoft 365** de votre navigateur, cliquez sur **Stratégie > Protection contre la perte de données**.
    
3. Dans le volet **Accueil > Protection contre la perte de données**, cliquez sur **Créer une stratégie**.
    
4. Dans le volet **Utiliser un modèle ou créer une stratégie personnalisée**, cliquez sur **Personnalisé**, puis sur **Suivant**.
    
5. Dans le volet **Nom de votre stratégie**, saisissez les **sites SharePoint avec étiquette Sensible** sous **Nom**, puis cliquez sur **Suivant**.
    
6. Dans le volet **Choisir des emplacements**, cliquez sur **Me laisser choisir des emplacements spécifiques**, puis cliquez sur **Suivant**.
    
7. Dans la liste des emplacements, désactivez les emplacements **Courrier Exchange**, **Comptes OneDrive** et **Messages de conversations et de canaux Teams**, puis cliquez sur **Suivant**.
    
8. Dans le volet **Personnalisez le type de contenu que vous voulez protéger**, cliquez sur **Modifier**.
    
9. Dans le volet **Choisissez les types de contenu à protéger**, cliquez sur **Ajouter** dans la zone déroulante, puis sélectionnez **Étiquettes de rétention**.
    
10. Dans le volet **Étiquettes de rétention**, cliquez sur **Ajouter**, sélectionnez l’étiquette **Sensible**, puis cliquez sur **Ajouter** et sur **Terminé**.
    
11. Dans le volet **Choisir les types de contenu à protéger**, cliquez sur **Enregistrer**.
    
12. Dans le volet **Personnaliser les types d’informations sensibles que vous souhaitez protéger**, cliquez sur **Suivant**.

13. Dans le volet **Que faire en cas de détection d’informations sensibles ?**, cliquez sur **Personnaliser l’info-bulle et l’e-mail**.
    
14. Dans le volet **Personnaliser les conseils et les notifications par e-mail de la stratégie**, cliquez sur **Personnaliser le texte de l’info-bulle de la stratégie**.
    
15. Dans la zone de texte, tapez ou collez ce qui suit :
    
  - Pour partager un fichier avec un utilisateur extérieur à l’organisation, téléchargez-le et ouvrez-le. Cliquez sur Fichier > Protéger le document > Chiffrer avec mot de passe, puis indiquez un mot de passe fort. Envoyez le mot de passe par e-mail ou un autre moyen de communication.
    
16. Cliquez sur **OK**.
    
17. Dans le volet Office **Que faire en cas de détection d’informations sensibles ?**, cliquez sur **Suivant**.
    
18. Dans le volet **Voulez-vous activer la stratégie ou d’abord effectuer des tests ?**, cliquez sur **Oui, l’activer maintenant**, puis cliquez sur **Suivant**.
    
19. Dans le volet **Vérifier vos paramètres**, cliquez sur **Créer**, puis sur **Fermer**.

Voici la configuration obtenue pour l’équipe Campagnes marketing.

![Configuration pour l’équipe Campagnes marketing.](../media/sensitive-team-config-dev-test.png)
  
### <a name="company-strategy-team-site"></a>Site d’équipe Stratégie d’entreprise

Pour créer une équipe de niveau hautement confidentiel pour les membres de l’équipe de leadership senior afin de collaborer sur la stratégie d’entreprise :

1. [Créez une équipe privée](https://support.office.com//article/create-a-team-from-scratch-174adf5f-846b-4780-b765-de1a0a737e2b) avec le nom **Stratégie d’entreprise**.
2. Ouvrez l’équipe**stratégie d’entreprise** .
3.  Dans la barre d’outils de l’équipe, cliquez sur **Fichiers**.
4.  Cliquez sur les points de suspension, puis sur **Ouvrir dans SharePoint**.
5.  Dans la barre d’outils du site SharePoint sous-jacent, cliquez sur l’icône Paramètres, puis cliquez sur **Autorisations du site**.
6.  Dans le volet **Autorisations de site**, sous **Paramètres de partage**, cliquez sur **Modifier les paramètres de partage**.
7.  Sous **Autorisations de partage**, sélectionnez **Seuls les propriétaires du site peuvent partager des fichiers, des dossiers et le site**.
8.  Désactivez **Autoriser les demandes d’accès**, puis cliquez sur **Enregistrer**.

Ensuite, configurez le dossier de documents du site SharePoint sous-jacent Stratégie d’entreprise avec l’étiquette Hautement confidentiel.

1.  Sous l’onglet **Stratégie de l’entreprise - Accueil** de votre navigateur, cliquez sur **Documents**.
2.  Cliquez sur l’icône des paramètres, puis cliquez sur **Paramètres de la bibliothèque**.
3.  Sous **Autorisations et gestion**, cliquez sur **Appliquer l’étiquette aux éléments de cette bibliothèque**.
4.  Dans **Paramètres - Appliquer une étiquette**, sélectionnez **Hautement confidentiel**, puis cliquez sur **Enregistrer**. 

Ensuite, configurez une stratégie de protection contre la perte de données qui bloque les utilisateurs quand ils partagent un document à l’extérieur de l’organisation sur un site SharePoint sous-jacent avec l’étiquette Hautement confidentiel, qui inclut le site Stratégie de l’entreprise.
  
1. Se connecter au[portail de conformité de Microsoft 365](https://compliance.microsoft.com/) avec votre compte d’administrateur général.
    
2. Sous le nouvel onglet **Conformité Microsoft 365** de votre navigateur, cliquez sur **Stratégie > Protection contre la perte de données**.
    
3. Dans le volet **Accueil > Protection contre la perte de données**, cliquez sur **Créer une stratégie**.
    
4. Dans le volet **Utiliser un modèle ou créer une stratégie personnalisée**, cliquez sur **Personnalisé**, puis sur **Suivant**.
    
5. Dans le volet **Nom de votre stratégie**, saisissez les **Sites SharePoint avec étiquette Hautement confidentiel** sous **Nom**, puis cliquez sur **Suivant**.
    
6. Dans le volet **Choisir des emplacements**, cliquez sur **Me laisser choisir des emplacements spécifiques**, puis cliquez sur **Suivant**.
    
7. Dans la liste des emplacements, désactivez les emplacements **Courrier Exchange**, **Comptes OneDrive** et **Messages de conversations et de canaux Teams**, puis cliquez sur **Suivant**.
    
8. Dans le volet **Personnalisez le type de contenu que vous voulez protéger**, cliquez sur **Modifier**.
    
9. Dans le volet **Choisissez les types de contenu à protéger**, cliquez sur **Ajouter** dans la zone déroulante, puis sélectionnez **Étiquettes de rétention**.
    
10. Dans le volet **Étiquettes de rétention**, cliquez sur **Ajouter**, sélectionnez l’étiquette **Hautement confidentiel**, puis cliquez sur **Ajouter** et sur **Terminé**.
    
11. Dans le volet **Choisir les types de contenu à protéger**, cliquez sur **Enregistrer**.
    
12. Dans le volet **Personnaliser les types d’informations sensibles que vous souhaitez protéger**, cliquez sur **Suivant**.

13. Dans le volet **Que faire en cas de détection d’informations sensibles ?**, cliquez sur **Personnaliser l’info-bulle et l’e-mail**.
    
14. Dans le volet **Personnaliser les conseils et les notifications par e-mail de la stratégie**, cliquez sur **Personnaliser le texte de l’info-bulle de la stratégie**.
    
15. Dans la zone de texte, tapez ou collez ce qui suit :
    
  - Pour partager un fichier avec un utilisateur extérieur à l’organisation, téléchargez-le et ouvrez-le. Cliquez sur Fichier > Protéger le document > Chiffrer avec mot de passe, puis indiquez un mot de passe fort. Envoyez le mot de passe par e-mail ou un autre moyen de communication.
    
16. Cliquez sur **OK**.
    
17. Dans le volet **Voulez-vous activer la stratégie ou d’abord effectuer des tests ?**, cliquez sur **Oui, l’activer maintenant**, puis cliquez sur **Suivant**.

18. Dans le volet **Voulez-vous activer la stratégie ou d’abord effectuer des tests ?**, cliquez sur **Oui, l’activer maintenant**, puis cliquez sur **Suivant**.
    
19. Dans le volet **Vérifier vos paramètres**, cliquez sur **Créer**, puis sur **Fermer**.

Suivez [ces instructions](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels) pour configurer une étiquette de confidentialité avec les paramètres suivants :

- Le nom de l’étiquette est Stratégie de l’entreprise.
- Le chiffrement est activé
- Le groupe Stratégie de l’entreprise possède des autorisations de co-création

Une fois que vous l’avez créée, publiez la nouvelle étiquette. Si vous vous connectez en tant que membre du groupe Stratégie de l’entreprise, la nouvelle étiquette apparaît dans l’option Confidentialité de la barre d’outils Accueil de Word, Excel et PowerPoint. Sélectionnez l’étiquette Stratégie de l’entreprise à partir de l’option Confidentialité pour affecter l’étiquette à un fichier.

Voici la configuration obtenue pour l’équipe Stratégie de l’entreprise.

![Configuration pour l’équipe Stratégie de l’entreprise.](../media/highlyconfidential-team-config-dev-test.png) 

Les fichiers dans la section documents du site SharePoint Stratégie de l’entreprise sous-jacent sont affectés à l’étiquette de rétention Hautement confidentiel et sont soumis à la stratégie DLP configurée. L’étiquette de confidentialité de la Stratégie d’entreprise peut également être attribuée aux fichiers.    
  
## <a name="next-step"></a>Étape suivante

Lorsque vous êtes prêt à procéder au déploiement de production, reportez-vous à [Sécuriser les fichiers dans Microsoft Teams](secure-files-in-teams.md) pour obtenir des informations détaillées et des liens vers des articles de déploiement étape par étape.
  
## <a name="see-also"></a>Voir aussi

[Adoption du cloud et solutions hybrides](https://docs.microsoft.com/office365/enterprise/cloud-adoption-and-hybrid-solutions)
