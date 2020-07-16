---
title: Test des classifieurs intégrés à l’aide d’étiquettes de rétention (aperçu)
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: None
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Microsoft 365 est fourni avec un certain nombre de classifieurs intégrés que vous pouvez utiliser pour identifier et étiqueter le contenu au sein de votre organisation. Cette rubrique vous explique comment vous préparer à l’utilisation de ces classifieurs.
ms.openlocfilehash: 1d645cc79075c41ce94b0f9b4fc347450a8df8c6
ms.sourcegitcommit: 9af890ef1b1c95bfc7cc52f7f4e395b62dc5263f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2020
ms.locfileid: "45146218"
---
# <a name="testing-built-in-classifiers-using-retention-labels-preview"></a>Test des classifieurs intégrés à l’aide d’étiquettes de rétention (aperçu)

Microsoft a formé et testé cinq classifieurs qui peuvent vous aider à identifier certaines catégories de contenu. Ces classifieurs s’affichent dans le `Ready to use` groupe par défaut et ont été formés à l’aide d’exemples de jeux de données très volumineux.

> [!IMPORTANT]
> Avant d’utiliser des classifieurs intégrés dans votre flux de travail de classification et d’étiquetage, vous devez le tester par rapport à un échantillon du contenu de votre organisation que vous jugez adapté à la catégorie afin de vérifier que ses prévisions de classification répondent à vos attentes.

Pour plus d’informations sur les classifieurs dotés de la formation, voir [Getting Started with trainable Classifiers (Preview)](classifier-getting-started-with.md).

Microsoft 365 est fourni avec cinq classifieurs intégrés recommandés :

> [!CAUTION]
> Nous déprécions le **langage inconvenant** classifieur intégré, car il génère un grand nombre de faux positifs. Ne l’utilisez pas et, si vous l’utilisez, vous devez déconnecter vos processus d’entreprise. Nous vous recommandons d’utiliser à la place les classifieurs intégrés de **menace**, de **blasphème**et de **harcèlement** .

- **CV**: détecte les éléments qui sont des comptes textuels des qualifications personnelles, éducatives, qualifications professionnelles, expérience professionnelle et autres informations d’identification personnelle d’un demandeur.
- **Code source**: détecte les éléments qui contiennent un ensemble d’instructions et d’instructions écrites dans les 25 principaux langages de programmation informatique utilisés sur GitHub

  |**Nom de la langue**|||||
  |---------|---------|---------|---------|---------|
  |3.0|C        |C#       |C++     |Clojure  |
  |CoffeeScript|CSS     |Activer       |Haskell |HTML     |
  |Java     |JavaScript|Privilège      |MATLAB   |Objective-C|
  |Langage     |PHP      |Python   |R        |Ruby     |
  |Scalaire    |Shell    |Rapide    |6,7      |Script vim|

> [!NOTE]
> Le code source est formé pour détecter si la majorité du texte est du code source. Il ne détecte pas le texte de code source qui est intercalé en texte brut.

- **Harcèlement**: détecte une catégorie spécifique d’éléments de texte de langue choquants liés à un comportement offensant ciblant une ou plusieurs personnes en fonction des caractéristiques suivantes : race, ethnique, religion, origine nationale, sexe, orientation sexuelle, âge, handicap
- **Blasphème**: détecte une catégorie spécifique d’éléments de texte en langue choquante qui contiennent des expressions qui déportent la plupart des utilisateurs
- **Menace**: détecte une catégorie spécifique d’éléments de texte de langue offensant liés aux menaces pour valider la violence ou causer des dommages ou dégâts physiques à une personne ou à une propriété.

> [!IMPORTANT]
> Veuillez noter que le langage offensant, le harcèlement, le catégoriseur et les classifieurs de menaces ne fonctionnent qu’avec le texte pouvant faire l’objet d’une recherche. De plus, les normes linguistiques et culturelles changent en permanence, et à la lumière de ces réalités, Microsoft se réserve le droit de mettre à jour ces classifieurs à sa discrétion. Alors que les classifieurs peuvent aider votre organisation à surveiller les autres langues choquantes et autres, les classifieurs ne traitent pas les conséquences de ces langues et ne sont pas destinés à fournir aux seuls moyens de surveillance ou de réponse à l’utilisation de ces langues. Votre organisation, et non Microsoft ou ses filiales, reste responsable de toutes les décisions relatives à la surveillance, à l’application, au blocage, à la suppression et à la rétention de tout contenu identifié par un classificateur pré-formé.

## <a name="how-to-verify-that-a-built-in-classifier-will-meet-your-needs"></a>Comment vérifier qu’un classifieur intégré répond à vos besoins

1. Collecter les éléments de contenu de test jetables qui vous intéressent dans la catégorie du classifieur intégré (correspondances positives) et ceux qui ne doivent pas être inclus (correspondances négatives) dans la catégorie que vous testez.

   > [!IMPORTANT]
   > Les éléments de l’exemple ne doivent pas être chiffrés et doivent être en anglais.

2. Créez un dossier SharePoint Online dédié ; Patientez au moins une heure pour que le dossier soit ajouté à l’index de recherche. Notez l’URL du dossier.

3. Connectez-vous au centre de conformité Microsoft 365 avec l’accès administrateur de conformité ou au rôle d’administrateur de sécurité et ouvrez l’onglet stratégies de gestion des enregistrements du **Centre de conformité Microsoft 365**  >  **Records management (preview)**  >  **Label policies** .

4. Choisissez `Auto-apply a label` .

5. Choisissez `Choose a label to auto-apply` .

6. Choisissez `Create new labels` et créez une étiquette à utiliser uniquement avec ce test. Dans ce cas, conservez la `Retention` valeur `off` . Vous ne souhaitez pas activer une rétention ou d’autres actions. Dans ce cas, vous utiliserez l’étiquette de rétention simplement comme étiquette de texte, sans appliquer les actions. Par exemple, vous pouvez créer une étiquette de rétention nommée « SourceCode classificateur test » sans action, puis appliquer automatiquement cette étiquette de rétention au contenu dont le code source est classifieur comme condition. Pour en savoir plus sur les étiquettes de rétention, voir [en savoir plus sur les stratégies de rétention et les étiquettes de conservation](retention.md).
  
7. Choisissez `Auto-apply a label` , puis `Choose a label to auto-apply` . Pour en savoir plus sur l’utilisation d’une étiquette basée sur une condition, consultez la rubrique [Configuration des conditions d’application automatique des étiquettes de rétention](apply-retention-labels-automatically.md#configuring-conditions-for-auto-apply-retention-labels).

8. Choisissez votre étiquette de test dans la liste, puis choisissez `Next` .

9. Choisissez `Apply label to content that matches a trainable classifier` .

   ![sélection du classifieur comme condition](../media/classifier-pre-trained-apply-label-match-trainable-classifier.png)

10. Choisissez votre classifieur dans la liste, dans ce cas.`Source Code`

11. Nommez la stratégie, par exemple « code source-test de classificateur intégré ».

12. Choisissez `Let me choose specific locations` .

13. Désactivez tous les emplacements sauf `SharePoint sites` et choisissez `Choose sites` .

14. Entrez l’URL du site à partir de l’étape 2.

15. Terminez l’Assistant et choisissez`Auto-apply`

16. Placez les éléments de test dans le dossier SharePoint Online dédié.

17. Autorisez l’application de l’étiquette sur une heure.

18. Vérifiez les propriétés des documents pour l’étiquette afin de déterminer si le classifieur a inclus et exclu le contenu de test comme vous le souhaitez.

19. Passez en revue les éléments qui ont été étiquetés.

20. Supprimez le contenu et la stratégie d’étiquette si vous avez fini votre test.

Voir aussi :

- [Prise en main des classificateurs pouvant être formés (préversion)](classifier-getting-started-with.md)
- [En savoir plus sur les stratégies et les balises de rétention](retention.md)
- [Application automatique d’une étiquette de rétention pour conserver ou supprimer du contenu](apply-retention-labels-automatically.md)
