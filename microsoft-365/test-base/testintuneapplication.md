---
title: Tester votre application Intune sur la base de test
description: Comment tester votre application Intune
search.appverid: MET150
author: Tinacyt
ms.author: tinachen
manager: rshastri
audience: Software-Vendor
ms.topic: troubleshooting
ms.date: 04/11/2022
ms.service: test-base
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: Tinacyt
f1.keywords: NOCSH
ms.openlocfilehash: 2fbe3a21762f6bf048d5f35485a359389df93ce2
ms.sourcegitcommit: eb81b49205cbc66b021326b8e2c00a8336b4a2fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/11/2022
ms.locfileid: "67315983"
---
# <a name="test-your-intune-application-on-test-base"></a>Tester votre application Intune sur la base de test 
  > [!Note] 
  > Ce guide vous guidera pour charger votre package de format intunewin dans la base de test. Pour obtenir des instructions générales sur le chargement du package de base de test, reportez-vous à ce [document](https://microsoft.sharepoint.com/:w:/t/AzureSUVPCoreTeam/EeHQIT3qA0FKqBDWI5TzmzgBiH2Syz39o5VbY2kdugMn4A?e=Rk1KD9).

## <a name="intunewin-upload-flow"></a>Flux de chargement Intunewin
Afin d’activer davantage l’utilisation commerciale, Test Base a commencé à prendre en charge le format intunewin pour les professionnels de l’informatique qui gèrent les applications pour leurs applications dans Intune en tant que format de package d’intégration standard. Le flux de chargement intunewin offre l’expérience permettant aux professionnels de l’informatique de réutiliser leurs packages de format intunewin, qui contiennent les applications qu’ils ont déployées sur leurs appareils finaux via MEM/Intune pour intégrer rapidement leurs applications et tester les configurations sur La base de test. 

**Conditions préalables**
  - Actuellement, Test Base prend en charge la synchronisation via le même abonnement entre le compte Intune et le compte de base de test (vous n’avez pas besoin d’un compte Intune pour charger votre package Intunewin. Toutefois, si vous souhaitez synchroniser la configuration Intune pour les applications correspondantes du fichier Intunewin à partir de Intune, vous devez vous assurer que votre Intune  est créé sous le même abonnement que votre compte de base de test).
  - Packages Intunewin à charger. 

**Flux de chargement de fichier Intunwin (synchronisé avec Intune compte)** <br/>
En tant que client Intune qui dispose d’un package Intune, qui a déjà été intégré à Intune portail. Le client peut intégrer le package intunewin (contenant une application avec/sans dépendances d’applications préinstalles gérées dans Intune) au service de base de test. (via Intune compte, qui dispose de l’autorisation appropriée pour synchroniser les informations d’application Intune).

**Étape de préparation**
1. Connectez-vous avec votre compte de base de test.
2. Préparez votre package Intunewin.
3. Commencez le chargement en cliquant sur le lien « Créer un package avec Intune App », comme ci-dessous.
    
    > [!div class="mx-imgBorder"] 
    > ![Commencer à créer un package avec Intune application](Media/testintuneapplication01.png) 


**Étape 1 : Définir le contenu**
1. Chargez le package intunewin que vous choisissez.
2. Accordez le jeton en cliquant sur le lien ci-dessous « Accorder le jeton et sélectionner l’application ».
3. Après la synchronisation automatique avec votre compte Intune, vous êtes répertorié avec l’application de vos applications sous votre compte Intune. Choisissez l’application correspondant à votre package Intunewin chargé, puis cliquez sur « Sélectionner ».
    
    > [!div class="mx-imgBorder"] 
    > ![Charger le package Intune](Media/testintuneapplication02.png) 


5. Dans la page Étape 1, vous verrez les dépendances répertoriées dans la section Dépendances. Vous pouvez choisir de charger le fichier d’installation de la dépendance ou de le supprimer de cette étape (si vous envisagez de gérer la dépendance à l’étape 3 en fournissant automatiquement les fichiers binaires associés). Les dépendances sélectionnées dans cette section seront préinstallées de la même façon qu’elles seront installées via Intune.
    
    > [!div class="mx-imgBorder"] 
    > ![Charger le package de dépendances](Media/testintuneapplication03.png) 


**Étape 2 : Configurer le test**
1. Sélectionnez PowerShell.
2. Sélectionnez Out of Box.


**Étape 3 : Modifier le package**
1. Vérifiez que les scripts générés automatiquement sont correctement étiquetés.
2. Si vous avez correctement synchronisé la configuration à partir de Intune, vous devriez voir que les commandes d’installation/désinstallation de l’application de test ont été ajoutées dans les scripts d’installation/désinstallation. Les commandes de la dépendance **qui a été chargée** doivent également être insérées dans l’arborescence de l’Explorateur de packages pour révision.
3. Vérifiez que les fichiers binaires d’application de test sont déplacés sous le dossier **bin** .
4. Vérifiez les fichiers binaires de **dépendances qui ont été chargés** placés sous le dossier **guid** .
5. Vous pouvez modifier les scripts en fonction des besoins et les enregistrer.
    > [!Note] 
    > Si le package de dépendances n’a pas été chargé, test base ne génère pas de commandes d’installation/désinstallation pour celui-ci.


**Étape 4 : Tester la matrice**
1. Vérifiez les sélections par défaut présentes dans la liste du système d’exploitation pour les types de test correspondants.
    - La base de test prend en charge la sélection de plusieurs mises à jour cumulatives Windows **à partir de Windows 10 1909, sauf Windows 10 2004**, mais Intune application Win est affectée avec une version de versions égales ou supérieures à **Windows 10 1607**.
    - La liste du système d’exploitation inclut par défaut tous les systèmes d’exploitation pris en charge par la base de test, ce qui est supérieur au système d’exploitation minimal spécifié pour l’application Win Intune.
2. Les utilisateurs sont autorisés à modifier la sélection du système d’exploitation en fonction des besoins.


**Étape 5 : Vérifier + publier** <br/>
Passez en revue la configuration après laquelle le package a pu être publié.<br/><br/>


**Flux de chargement de fichier Intunwin (impossible de synchroniser avec Intune compte)** <br/>
En tant que client de base de test disposant d’un package intunewin autonome. Le client peut intégrer le package intunewin (contenant une application avec/sans dépendances d’applications préinstallées gérées dans Intune) sans avoir besoin d’obtenir l’autorisation accordée sur Intune compte pour terminer le processus d’intégration.

**Étape de préparation**
1. Connectez-vous avec votre compte de base de test.
2. Préparez votre package Intunewin.
3. Commencez le chargement en cliquant sur le lien « Créer un package avec Intune App », comme ci-dessous.
    
    > [!div class="mx-imgBorder"] 
    > ![Créer un package avec Intune App](Media/testintuneapplication04.png) 


**Étape 1 : Définir le contenu**
1. Chargez le package intunewin.
2. Spécifiez toutes les informations en fonction de vos préférences.


**Étape 2 : Configurer le test**
1. Sélectionnez PowerShell.
2. Sélectionnez Out of Box.


**Étape 3 : Modifier le package**
1. Vérifiez que les scripts sont correctement étiquetés.
2. Comme aucune commande d’installation/désinstallation n’est synchronisée à partir du compte Intune correspondant, vous devez fournir tous les scripts (installer/désinstaller/lancer/fermer) par vous-même.
3. Vérifiez que les fichiers binaires d’application de test sont déplacés sous le dossier bin.
4. Vous pouvez modifier les scripts en fonction des besoins et les enregistrer.


**Étape 4 : Tester la matrice**
1. Aucune version du système d’exploitation par défaut n’est présélectionnée.
2. Les utilisateurs sont autorisés à effectuer leur propre sélection sur les systèmes d’exploitation à planifier.


**Étape 5 : Vérifier + publier** <br/>
Passez en revue la configuration après laquelle le package a pu être publié.




