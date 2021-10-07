---
title: Formation sur le marquage et la pertinence dans Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: Découvrez les étapes à suivre pour baliser, puis travailler avec un exemple de formation de 40 fichiers pendant la phase de formation Pertinence de Advanced eDiscovery.
ms.openlocfilehash: c21ec89896dbd67bd348abd317d1389f8e105fda
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60202990"
---
# <a name="tagging-and-relevance-training-in-advanced-ediscovery"></a>Formation sur le marquage et la pertinence dans Advanced eDiscovery
  
Cet article décrit la procédure d’emploi du module de formation Pertinence dans Advanced eDiscovery.
  
Une fois l’évaluation Advanced eDiscovery terminée et que vous entrez dans la phase de formation Pertinence, un échantillon de formation de 40 fichiers est ajouté à l’onglet Balise pour le marquage.
  
## <a name="performing-relevance-training"></a>Formation sur la pertinence

1. Dans **l’onglet \> Balise** de pertinence, le volet Marquage s’affiche par défaut dans le volet gauche et les exemples de fichiers s’affichent, un par un pour le marquage.

    ![Panneau balise de pertinence.](../media/0cf19ab4-b427-4a7f-8749-0f4ed9afaf58.png)
  
    Dans **l’onglet** Balise, le nom complet du fichier s’affiche. Cela peut être le chemin d’accès, l’objet de l’e-mail, le titre ou le nom défini par l’utilisateur. L’ID, le chemin d’accès au fichier ou le chemin de texte peuvent être copiés en cliquant avec le bouton droit sur le chemin d’accès du fichier.

    Les  statistiques de marquage de l’onglet Balise indiquent le numéro d’exemple de fichier (en haut du volet gauche), le nombre de fichiers actuellement affichés en dehors du nombre total de fichiers dans l’exemple (en bas du volet droit) et le nombre total actuel de fichiers marqués dans l’exemple (en bas du volet gauche), qui change à mesure que vous marquez des fichiers. Cela s’applique à tout marquage de pertinence effectué, que ce soit lors de l’évaluation, de l’entraînement, du rattrapage ou du test.

    Les icônes indiquant l’existence de commentaires, de balises et de fichiers de famille sont affichées dans l’affichage fichier dans une barre au-dessus du fichier.

2. Déterminez la pertinence du fichier pour le problème de cas et marquez-le à l’aide des boutons d’icône d’option de marquage ou des raccourcis clavier, comme indiqué dans le tableau suivant :

   |**Option de marquage**|**Description**|**Raccourci clavier**|**Raccourci clavier de marquage en bloc (pour plusieurs problèmes)**|
   |-----|-----|-----|-----|
   |R  <br/> |Pertinent  <br/> |Z  <br/> |`Shift + Z`  <br/> |
   |NR  <br/> |Non pertinent  <br/> |X  <br/> |`Shift + X`  <br/> |
   |Ignorer  <br/> |Ignorer  <br/> |C  <br/> |`Shift + A`  <br/> |
   |||||

   - Lorsque plusieurs problèmes existent pour un fichier, après avoir balisé un problème, la sélection passe au problème suivant (le cas cas).  

   - Les mots clés définis par l’administrateur ou le gestionnaire de cas lors de la mise en surbrillance des mots clés (mots clés de configuration de pertinence mis en surbrillance) s’affichent (dans les couleurs spécifiées) pour vous aider à identifier les fichiers pertinents lors du \> marquage. Si un mot clé a un double soulignement, vous pouvez cliquer dessus pour afficher une info-conseil avec la description du mot clé.

     Éventuellement, dans **l’onglet Balise,** cliquez sur **Paramètres de** balise pour définir les options suivantes :

      ![Paramètres de balise de pertinence.](../media/533e89fa-7eb4-409e-ab07-f5aab9296dd8.png)
  
   - **Balise** en bloc : utilisez cette option pour affecter  plusieurs problèmes à un fichier en sélectionnant Tout pour définir la balise pour  le fichier sélectionné pour tous les problèmes (remplace les problèmes déjà marqués) ou en sélectionnant Le reste pour appliquer la balise aux problèmes non retardés restants. L’option sélectionnée reste en vigueur pour tous les cas de cet utilisateur jusqu’à ce qu’il soit modifié par cet utilisateur (le paramètre est par utilisateur pour tous les cas de l’utilisateur).

   - **Balise automatique**: cochez cette case pour définir d’autres problèmes pour un fichier comme non pertinents après un marquage pertinent unique.

   - **Avance automatique**: cochez cette case pour déplacer la sélection de fichier affichée vers le fichier suivant lors du marquage du dernier ou seul problème non retardé.

    Les fichiers ignorés ne seront pas pris en compte à des fins d’entraînement de pertinence et de score de pertinence.

3. Les commentaires en texte libre, associés à un fichier,  peuvent être consultables et modifiés via l’option Commentaire dans la liste modifiable du volet gauche. (facultatif)

4. Pour afficher les recommandations en matière  de marquage, sélectionnez l’option Recommandations en matière de marquage dans la liste de listes de gauche du volet.

5. Une fois que vous avez terminé le marquage de tous les fichiers de la liste et que vous êtes prêt à calculer les résultats, cliquez sur **Calculer.** **L’onglet** Suivi s’affiche.  

## <a name="working-with-the-sample-files-list"></a>Travailler avec la liste d’exemples de fichiers

La liste des exemples de fichiers vous permet d’afficher une liste des fichiers dans un exemple de formation et d’effectuer différentes actions sur un ou plusieurs fichiers. Dans **l’onglet** Balise de pertinence, le volet gauche des exemples de fichiers affiche une liste d’exemples de fichiers à traiter avec des processus d’évaluation, de formation, de rattrapage et \> d’incohérences.  
  
1. Dans **l’onglet \> Balise de** pertinence, sélectionnez les exemples de fichiers dans la liste de listes de listes listes de gauche du volet. Les exemples de fichiers sont répertoriés dans le volet gauche.

    ![Liste d’exemples de fichiers de balise de pertinence.](../media/fd058bdd-645a-4af1-a1eb-bff08581cb18.png)
  
2. Sélectionnez un exemple ou un numéro de fichier spécifique en entrant ou en sélectionnant son numéro dans les **zones** Exemple **ou** Fichier.

   - Un numéro de séquence de fichier est répertorié dans la colonne gauche de la liste des fichiers affichée sous **l’onglet Balise.** En cliquant sur l’en-tête, l’ordre d’origine affiché des fichiers revient à son ordre d’origine.

   - Un clic sur une ligne de fichier affiche son contenu dans le volet droit.

   - Naviguez entre les fichiers de l’exemple actuel à l’aide des options de la barre de menus inférieure. En outre, des raccourcis clavier de navigation sont disponibles :
  
     - Pour aller au premier fichier de l’exemple : `Shift + Ctrl + <`

     - Pour aller au fichier précédent dans l’exemple : `Shift + <`

     - Pour passer au fichier suivant dans l’exemple : `Shift + >`

     - Pour aller au dernier fichier de l’exemple : `Shift + Ctrl + >`
