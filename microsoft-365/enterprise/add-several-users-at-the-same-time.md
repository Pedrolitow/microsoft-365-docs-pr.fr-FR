---
title: Ajouter plusieurs utilisateurs en même temps à Microsoft 365 - aide Administration
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365P_AddUsersCSV
- O365M_AddUsersCSV
- O365E_AddUsersCSV
- admindeeplinkMAC
ms.collection:
- scotvorg
search.appverid:
- MET150
- MOP150
- MOE150
- MED150
- GMA150
- MBS150
- GEA150
- BCS160
description: 'Découvrez comment ajouter plusieurs utilisateurs à Microsoft 365 pour les entreprises à partir d’une liste dans une feuille de calcul ou un autre fichier au format CSV. Regardez une vidéo sur YouTube qui explique comment ajouter des comptes à Microsoft 365. À la fin de ce processus, chaque utilisateur disposant d’un compte disposera d’une boîte aux lettres Microsoft 365. '
ms.openlocfilehash: c8453e5634245897a06867b422349c3350de03ae
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68201174"
---
# <a name="add-several-users-at-the-same-time-to-microsoft-365---admin-help"></a>Ajouter plusieurs utilisateurs en même temps à Microsoft 365 - aide Administration

Chaque personne de votre équipe a besoin d’un compte d’utilisateur avant de pouvoir se connecter et accéder aux services Microsoft 365, tels que l’e-mail et Office. Si votre équipe compte de nombreux membres, vous pouvez ajouter tous leurs comptes simultanément à partir d'une feuille de calcul Excel ou d'un autre fichier enregistré au format CSV. [Vous ne savez pas quel format CSV est](add-several-users-at-the-same-time.md#not-sure-what-csv-format-is) ?
  
> [!NOTE]
> Si le nouveau Centre d’administration Microsoft 365 n’est pas celui que vous utilisez, vous pouvez l’activer en sélectionnant le bouton bascule **Essayer le nouveau Centre d’administration** situé en haut de la page d’accueil.

## <a name="add-multiple-users-in-the-microsoft-365-admin-center"></a>Ajouter plusieurs utilisateurs dans le Centre d'administration Microsoft 365

1. Connectez-vous à Microsoft 365 à l’aide de votre compte professionnel ou scolaire.

2. Dans le centre d’administration, choisissez **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**actifs**</a>.

3. Sélectionnez **Ajouter plusieurs utilisateurs**.

4. Dans le panneau **Importer plusieurs utilisateurs**, vous pouvez éventuellement télécharger un exemple de fichier CSV avec ou sans exemple de données inclus.

    Votre feuille de calcul doit inclure **exactement les mêmes en-têtes de colonne** que l’exemple (nom d’utilisateur, prénom, etc.). Si vous utilisez le modèle, ouvrez-le dans un outil d’édition de texte, comme le Bloc-notes, et envisagez de laisser toutes les données de la ligne 1 seules et d’entrer uniquement les données dans les lignes 2 et inférieures.

    Votre feuille de calcul doit également inclure des valeurs pour le nom d'utilisateur (tel que alexandre@contoso.com) et un nom complet (tel que Alexandre Chauvin) pour chaque utilisateur.

  ```
  User Name,First Name,Last Name,Display Name,Job Title,Department,Office Number,Office Phone,Mobile Phone,Fax,Address,City,State or Province,ZIP or Postal Code,Country or Region
  chris@contoso.com,Chris,Green,Chris Green,IT Manager,Information Technology,123451,123-555-1211,123-555-6641,123-555-6700,1 Microsoft way,Redmond,Wa,98052,United States
  ben@contoso.com,Ben,Andrews,Ben Andrews,IT Manager,Information Technology,123452,123-555-1212,123-555-6642,123-555-6700,1 Microsoft way,Redmond,Wa,98052,United States
  david@contoso.com,David,Longmuir,David Longmuir,IT Manager,Information Technology,123453,123-555-1213,123-555-6643,123-555-6700,1 Microsoft way,Redmond,Wa,98052,United States
  cynthia@contoso.com,Cynthia,Carey,Cynthia Carey,IT Manager,Information Technology,123454,123-555-1214,123-555-6644,123-555-6700,1 Microsoft way,Redmond,Wa,98052,United States
  melissa@contoso.com,Melissa,MacBeth,Melissa MacBeth,IT Manager,Information Technology,123455,123-555-1215,123-555-6645,123-555-6700,1 Microsoft way,Redmond,Wa,98052,United States
  
  ```

5. Entrez un chemin d'accès dans la zone, ou choisissez **Parcourir** pour accéder à l'emplacement du fichier CSV, puis sélectionnez **Vérifier**.
  
    S'il existe des problèmes avec le fichier, ceux-ci s'affichent dans le panneau. Vous pouvez également télécharger un fichier journal.

6. Dans la boîte de dialogue **Définir les options utilisateur**, vous pouvez définir le statut de connexion et choisir la licence produit à affecter à tous les utilisateurs.

7. Dans la boîte de dialogue **Affichez vos résultats**, vous pouvez choisir d'envoyer les résultats à vous-même ou à d'autres utilisateurs (les mots de passe seront au format texte brut). En outre, vous pouvez voir combien d'utilisateurs ont été créés et si vous avez besoin d'acheter des licences supplémentaires pour les attribuer à certains des nouveaux utilisateurs.

## <a name="next-steps"></a>Prochaines étapes

- Maintenant que ces personnes ont des comptes, elles doivent [télécharger et installer ou réinstaller Microsoft 365 ou Office 2016 sur un PC ou Mac](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658). Chaque membre de votre équipe peut installer Microsoft 365 sur jusqu’à 5 PC ou Mac.

- Chaque personne peut également [configurer des applications Office et des e-mails sur un appareil mobile](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f) sur jusqu’à 5 tablettes et 5 téléphones, tels que des iPhone, des iPad et des téléphones et tablettes Android. De cette façon, ils peuvent modifier des fichiers Office à partir de n’importe où.

    Consultez [Configurer Microsoft 365 pour les entreprises](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) pour obtenir une liste de bout en bout des étapes de configuration.

## <a name="more-information-about-how-to-add-users-to-microsoft-365"></a>Plus d’informations sur l’ajout d’utilisateurs à Microsoft 365

### <a name="not-sure-what-csv-format-is"></a>Qu'est-ce que le format CSV ?

A CSV file is a file with comma separated values. You can create or edit a file like this with any text editor or spreadsheet program, such as Excel.
  
Vous pouvez télécharger [cet exemple de feuille de calcul](https://www.microsoft.com/download/details.aspx?id=45485) pour commencer. N’oubliez pas que Microsoft 365 requiert des en-têtes de colonne dans la première ligne, donc ne les remplacez pas par autre chose. 
  
Enregistrez le fichier avec un nouveau nom et spécifiez le format CSV.
  
![Image montrant comment enregistrer un fichier dans Excel au format CSV.](../media/35a86ebe-63ab-4b4d-9a92-e177de33ebae.png)
  
When you save the file, you'll probably get a prompt that some features in your workbook will be lost if you save the file in CSV format. This is okay. Click **Yes** to continue.
  
![Image de l’invite que vous pouvez obtenir d’Excel vous demandant si vous souhaitez vraiment enregistrer le fichier au format CSV.](../media/51032a81-690c-45ef-bfc5-09ea7f790e98.png)
  
### <a name="tips-for-formatting-your-spreadsheet"></a>Conseils pour la mise en forme de votre feuille de calcul

- **Ai-je besoin des mêmes en-têtes de colonne que dans l'exemple de feuille de calcul ?** Oui. La première ligne de l'exemple de feuille de calcul inclut les en-têtes de colonne. Ces en-têtes sont obligatoires. Pour chaque utilisateur que vous souhaitez ajouter à Microsoft 365, créez une ligne sous le titre. Si vous ajoutez, modifiez ou supprimez l’un des en-têtes de colonne, Microsoft 365 peut ne pas être en mesure de créer des utilisateurs à partir des informations contenues dans le fichier.

- **What if I don't have all the information required for each user?** The user name and display name are required, and you cannot add a new user without this information. If you don't have some of the other information, such as the fax, you can use a space plus a comma to indicate that the field should remain blank.

- **Quelle est la taille de la feuille de calcul ?** La feuille de calcul doit comporter au moins deux lignes. One is for the column headings (the user data column label) and one for the user. You cannot have more than 251 rows. If you need to import more than 250 users, you can create more than one spreadsheet.

- **Quelles langues puis-je utiliser ?** Lorsque vous créez votre feuille de calcul, vous pouvez entrer des étiquettes de colonne de données utilisateur dans n’importe quelle langue ou caractères, mais vous ne devez pas modifier l’ordre des étiquettes, comme indiqué dans l’exemple. You can then make entries into the fields, using any language or characters, and save your file in a Unicode or UTF-8 format.

- **What if I'm adding users from different countries or regions?** Create a separate spreadsheet for each area. You'll need to step through the Bulk add users wizard which each spreadsheet, giving a single location of all users included in the file that you're working with.

- **Is there a limit to the number of characters I can use?** The following table shows the user data column labels and the maximum character length for each in the sample spreadsheet.

|**Étiquette de colonne des données utilisateur**|**Longueur de caractères maximale**|
|:-----|:-----|
|Nom d'utilisateur (requis)  <br/> |79, y compris le signe at (@), au format name@domain.\<extension\>. L’alias de l’utilisateur ne peut pas dépasser 50 caractères et le nom de domaine ne peut pas dépasser 48 caractères.  <br/> |
|Prénom  <br/> |64  <br/> |
|Nom  <br/> |64  <br/> |
|Nom d'affichage (requis)  <br/> |256  <br/> |
|Poste  <br/> |64  <br/> |
|Service  <br/> |64  <br/> |
|Numéro du bureau  <br/> |128  <br/> |
|Téléphone (bureau)  <br/> |64  <br/> |
|Téléphone mobile  <br/> |64  <br/> |
|Télécopie  <br/> |64  <br/> |
|Adresse  <br/> |1023  <br/> |
|Ville  <br/> |128  <br/> |
|Département ou région  <br/> |128  <br/> |
|Code postal  <br/> |40  <br/> |
|Pays ou région  <br/> |128  <br/> |

### <a name="still-having-problems-when-adding-users-to-microsoft-365"></a>Vous rencontrez toujours des problèmes lors de l’ajout d’utilisateurs à Microsoft 365 ?

- **Double-check that the spreadsheet is formatted correctly.** Check the column headings to make sure they match the headings in the sample file. Make sure you're following the rules for character lengths and that each field is separated by a comma.

- **Si vous ne voyez pas les nouveaux utilisateurs dans Microsoft 365 immédiatement, patientez quelques minutes.** Les modifications apportées à tous les services dans Microsoft 365 peuvent prendre un certain temps. 

## <a name="related-articles"></a>Articles connexes

[Ajouter des utilisateurs individuellement ou en bloc à Microsoft 365](/office365/admin/add-users/add-users)