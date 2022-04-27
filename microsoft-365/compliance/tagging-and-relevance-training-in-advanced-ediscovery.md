---
title: Formation sur l’étiquetage et la pertinence dans eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
titleSuffix: Office 365
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: 8576cc86-d51b-4285-b54b-67184714cc62
ROBOTS: NOINDEX, NOFOLLOW
description: Découvrez les étapes à suivre pour étiqueter, puis utiliser un exemple de formation de 40 fichiers pendant l’étape de formation pertinence d’eDiscovery (Premium).
ms.openlocfilehash: 3e2deb66658aacc8fdd50f2dea5ba082afb8a5e6
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090382"
---
# <a name="tagging-and-relevance-training-in-ediscovery-premium"></a>Formation sur l’étiquetage et la pertinence dans eDiscovery (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]
  
Cet article décrit la procédure d’utilisation du module de formation Pertinence dans Microsoft Purview eDiscovery (Premium).
  
Une fois l’évaluation terminée dans eDiscovery (Premium) et que vous entrez dans l’étape de formation Pertinence, un exemple d’apprentissage de 40 fichiers est introduit dans l’onglet Balise pour le balisage.
  
## <a name="performing-relevance-training"></a>Exécution d’une formation sur la pertinence

1. Dans l’onglet **Balise de pertinence\>**, le volet De balisage est affiché par défaut dans le volet gauche et les exemples de fichiers sont affichés, un par un pour le balisage.

    ![Panneau Balise de pertinence.](../media/0cf19ab4-b427-4a7f-8749-0f4ed9afaf58.png)
  
    Sous l’onglet **Étiquette** , le nom d’affichage du fichier s’affiche. Il peut s’agir du chemin d’accès, de l’objet de l’e-mail, du titre ou du nom défini par l’utilisateur. L’ID, le chemin d’accès au fichier ou le chemin de texte peuvent être copiés en cliquant avec le bouton droit sur le chemin d’accès du fichier.

    Les statistiques de balisage de l’onglet **Balise** affichent le numéro d’échantillon de fichier (en haut du volet gauche), le numéro du fichier actuellement affiché sur le nombre total de fichiers dans l’exemple (en bas du volet droit) et le nombre total actuel de fichiers étiquetés dans l’exemple (en bas du volet gauche), qui change à mesure que vous balisez des fichiers. Cela s’applique à tout balisage de pertinence effectué, que ce soit dans l’évaluation, l’entraînement, le rattrapage ou le test.

    Les icônes indiquant l’existence de commentaires, d’étiquettes et de fichiers familiaux sont affichées dans l’affichage des fichiers dans une barre au-dessus du fichier.

2. Déterminez la pertinence du fichier pour le problème de cas et étiquetez le fichier à l’aide des boutons d’icône d’option de balisage ou des raccourcis clavier, comme indiqué dans le tableau suivant :

   |**Option d’étiquetage**|**Description**|**Raccourci clavier**|**Raccourci clavier de balisage en bloc (pour plusieurs problèmes)**|
   |-----|-----|-----|-----|
   |R  <br/> |Pertinent  <br/> |Z  <br/> |`Shift + Z`  <br/> |
   |NR  <br/> |Non pertinent  <br/> |X  <br/> |`Shift + X`  <br/> |
   |Ignorer  <br/> |Ignorer  <br/> |C  <br/> |`Shift + A`  <br/> |
   |||||

   - Lorsque plusieurs problèmes existent pour un fichier, après avoir marqué un problème, la sélection passe au problème suivant (le cas échéant).  

   - Les mots clés qui ont été définis par l’administrateur ou le gestionnaire de cas lors de la mise en surbrillance des mots clés (mots clés mis en surbrillance pour la configuration \> de la pertinence) s’affichent (dans des couleurs spécifiées) pour vous aider à identifier les fichiers pertinents lors du balisage. Si un mot clé a un double soulignement, vous pouvez cliquer dessus pour afficher une info-bulle avec la description du mot clé.

     Si vous le souhaitez, sous l’onglet **Étiquette** , cliquez sur **Paramètres de** balise pour définir les options suivantes :

      ![Paramètres de balise de pertinence.](../media/533e89fa-7eb4-409e-ab07-f5aab9296dd8.png)
  
   - **Balise en bloc** : utilisez cette option pour attribuer plusieurs problèmes à un fichier en sélectionnant **Tout** pour définir la balise du fichier sélectionné pour tous les problèmes (remplace les problèmes déjà marqués) ou en sélectionnant **Le reste** pour appliquer la balise aux autres problèmes non étiquetés. L’option sélectionnée reste en vigueur pour tous les cas de cet utilisateur jusqu’à ce qu’elle soit modifiée par cet utilisateur (le paramètre est par utilisateur pour tous les cas de l’utilisateur).

   - **Balise automatique** : activez cette case à cocher pour définir d’autres problèmes pour un fichier comme non pertinents après un balisage approprié unique.

   - **Avance automatique** : activez cette case à cocher pour déplacer la sélection du fichier affiché vers le fichier suivant lors de l’étiquetage du dernier ou du seul problème non étiqueté.

    Les fichiers ignorés ne seront pas pris en compte à des fins de formation de pertinence et de scoring de pertinence.

3. Les commentaires en texte libre, associés à un fichier, peuvent être affichés et modifiés via l’option **Commentaire** dans la liste déroulante du volet gauche. (facultatif)

4. Vous pouvez consulter les instructions relatives au balisage en sélectionnant l’option Instructions de **balisage** dans la liste déroulante du volet gauche.

5. Une fois que vous avez terminé de marquer tous les fichiers de la liste et que vous êtes prêt à calculer les résultats, cliquez sur **Calculer**. L’onglet **Suivi** s’affiche.  

## <a name="working-with-the-sample-files-list"></a>Utilisation de la liste d’exemples de fichiers

La liste d’exemples de fichiers vous permet d’afficher une liste des fichiers dans un exemple d’apprentissage et d’effectuer différentes actions sur un ou plusieurs fichiers. Sous l’onglet **Balise de pertinence**\>, le volet de gauche **exemples de fichiers** affiche une liste d’exemples de fichiers à traiter avec des processus d’évaluation, d’entraînement, de rattrapage et d’incohérences.
  
1. Sous l’onglet **Balise de pertinence\>**, sélectionnez les exemples de fichiers dans la liste déroulante du volet gauche. Les exemples de fichiers sont répertoriés dans le volet gauche.

    ![Liste d’exemples de fichiers de balise de pertinence.](../media/fd058bdd-645a-4af1-a1eb-bff08581cb18.png)
  
2. Sélectionnez un exemple ou un numéro de fichier spécifique en entrant ou en sélectionnant son numéro dans les zones **Exemple** ou **Fichier** .

   - Un numéro de séquence de fichiers est répertorié dans la colonne de gauche de la liste de fichiers affichée sous l’onglet **Étiquette** . En cliquant sur l’en-tête, l’ordre d’origine affiché des fichiers revient à son ordre d’origine.

   - Cliquer sur une ligne de fichier affiche son contenu dans le volet droit.

   - Naviguez entre les fichiers de l’exemple actuel à l’aide des options de barre de menus inférieures. En outre, des raccourcis clavier de navigation sont disponibles :
  
     - Pour accéder au premier fichier de l’exemple : `Shift + Ctrl + <`

     - Pour accéder au fichier précédent dans l’exemple : `Shift + <`

     - Pour accéder au fichier suivant dans l’exemple : `Shift + >`

     - Pour accéder au dernier fichier de l’exemple : `Shift + Ctrl + >`
