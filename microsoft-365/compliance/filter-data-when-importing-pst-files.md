---
title: Filtrer les données lors de l’importation de fichiers PST
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 26af16df-34cd-4f4a-b893-bc1d2e74039e
ms.custom:
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
description: Découvrez comment filtrer des données à l’aide de la fonctionnalité d’importation intelligente dans le service d’importation Microsoft 365 lorsque vous importez des fichiers PST dans Microsoft 365.
ms.openlocfilehash: ce4d85bb88bcd7e36ef1d2c39b0f23eabd38ae7f
ms.sourcegitcommit: 433f5b448a0149fcf462996bc5c9b45d17bd46c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2022
ms.locfileid: "67818366"
---
# <a name="filter-data-when-importing-pst-files"></a>Filtrer les données lors de l’importation de fichiers PST

>*[Guide de sécurité et conformité pour les licences Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Utilisez la nouvelle fonctionnalité d’importation intelligente dans le service d’importation Microsoft 365 pour filtrer les éléments des fichiers PST qui sont réellement importés dans les boîtes aux lettres cibles. Voici le principe de fonctionnement :
  
- Une fois que vous avez créé et envoyé un travail d’importation PST, les fichiers PST sont chargés dans une zone de stockage Azure dans le cloud Microsoft.
  
- Microsoft 365 analyse les données dans les fichiers PST, de manière sécurisée et sécurisée, en identifiant l’âge des éléments de boîte aux lettres et les différents types de messages inclus dans les fichiers PST.
  
- Une fois l’analyse terminée et que les données sont prêtes à être importées, vous avez la possibilité d’importer toutes les données dans les fichiers PST telles quelles ou de supprimer les données importées en définissant des filtres qui contrôlent les données importées. Par exemple, vous pouvez choisir :
  
  - Importez uniquement des éléments d’un certain âge.
  
  - Importez les types de messages sélectionnés.
  
  - Exclure les messages envoyés ou reçus par des personnes spécifiques.
  
- Après avoir configuré les paramètres de filtre, Microsoft 365 importe uniquement les données qui répondent aux critères de filtrage dans les boîtes aux lettres cibles spécifiées dans le travail d’importation.
  
Le graphique suivant montre le processus d’importation intelligente et met en évidence les tâches que vous effectuez et les tâches effectuées par Office 365.
  
![Processus d’importation intelligente dans Office 365.](../media/f2ec309b-11f5-48f2-939c-a6ff72152d14.png)
  
## <a name="create-a-pst-import-job"></a>Créer un travail d’importation PST

- Les étapes décrites dans cette rubrique supposent que vous avez créé un travail d’importation PST dans le service d’importation Office 365 à l’aide du chargement réseau ou de l’expédition de lecteurs. Pour obtenir des instructions pas à pas, consultez l’une des rubriques suivantes :
    
  - [Utiliser le chargement réseau pour importer des fichiers PST dans Office 365](use-network-upload-to-import-pst-files.md)
    
  - [Utiliser l’expédition de disque pour importer des fichiers PST dans Office 365](use-drive-shipping-to-import-pst-files-to-office-365.md)
    
- Une fois que vous avez créé un travail d’importation à l’aide du chargement réseau, l’état du travail d’importation sur la page Importer dans le Centre de sécurité & conformité est défini sur **Analyse en cours**, ce qui signifie que Microsoft 365 analyse les données dans les fichiers PST que vous avez chargés. Cliquez sur **Actualiser**![l’actualisation.](../media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) pour mettre à jour l’état du travail d’importation. 
    
- Pour les travaux d’importation d’expédition de lecteur, les données seront analysées par Microsoft 365 une fois que le personnel du centre de données Microsoft aura reçu votre disque dur et chargé les fichiers PST dans la zone de stockage Azure de votre organisation.
  
## <a name="filter-data-that-gets-imported-to-mailboxes"></a>Filtrer les données importées dans les boîtes aux lettres

Après avoir créé un travail d’importation PST, procédez comme suit pour filtrer les données avant de les importer dans Office 365.
  
1. Accédez à <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portail de conformité Microsoft Purview</a> et connectez-vous à l’aide des informations d’identification d’un compte administrateur dans votre organisation.
    
2. Dans le volet gauche du portail de conformité, cliquez sur Gestion **du cycle de** \> vie des données **Microsoft 365** \> **Import**.
    
    Les travaux d’importation de votre organisation sont répertoriés sous l’onglet **Importation** . La valeur **Analyse terminée** dans la colonne **État** indique les travaux d’importation qui ont été analysés par Microsoft 365 et qui sont prêts à être importés.
    
    ![L’état complet de l’analyse indique que Microsoft 365 a analysé les données dans les fichiers PST.](../media/de5294f4-f0ba-4b92-a48a-a4b32b6da490.png)
  
3. Sélectionnez le travail d’importation à effectuer, puis cliquez sur **Importer pour Office 365**.
  
    Une page volante s’affiche avec des informations sur les fichiers PST et d’autres informations sur la tâche d’importation.

4. Cliquez sur **Importer pour Office 365**.
    
    La page **Filtrez vos données** s’affiche. Il contient des insights sur les données des fichiers PST pour le travail d’importation, y compris des informations sur l’âge des données. 
    
    ![La page Filtrer vos données affiche les insights de données des fichiers PST pour le travail d’importation.](../media/3b537ec0-25a4-45a4-96d5-a429e2a33128.png)
  
5. Selon que vous souhaitez supprimer ou non les données importées dans Microsoft 365, sous **Voulez-vous filtrer vos données ?, effectuez** l’une des opérations suivantes :
  
    a. Cliquez sur **Oui, je veux le filtrer avant d’importer** pour découper les données que vous importez, puis cliquez sur **Suivant**.
  
    La page **Importer des données dans Office 365 page** s’affiche avec des insights détaillés sur les données de l’analyse effectuée par Microsoft 365. 
  
    ![Microsoft 365 affiche des insights détaillés sur les données à partir de son analyse des fichiers PST.](../media/4881205f-0288-4c32-a440-37e2160295f2.png)
  
    Le graphique de cette page montre la quantité de données qui seront importées. Des informations sur chaque type de message trouvé dans les fichiers PST sont affichées dans le graphique. Vous pouvez placer le curseur sur chaque barre pour afficher des informations spécifiques sur ce type de message. Il existe également une liste déroulante avec différentes valeurs d’âge basées sur l’analyse des fichiers PST. Lorsque vous sélectionnez un âge dans la liste déroulante, le graphique est mis à jour pour indiquer la quantité de données importées pour l’âge sélectionné. 
  
    b. Pour configurer des filtres d’ajout afin de réduire la quantité de données importées, cliquez sur **Autres options de filtrage**.
  
    ![Configurez les filtres sur la page Plus d’options pour supprimer les données importées.](../media/3f8d68c3-3fe2-4b4e-9488-b368b98fa9fe.png)
  
    Vous pouvez configurer ces filtres :
  
      - **Âge** : sélectionnez un âge afin que seuls les éléments plus nouveaux que l’âge spécifié soient importés. Consultez la section [Plus d’informations](#more-information) pour obtenir une description de la façon dont Microsoft 365 détermine les compartiments d’âge pour le filtre **Âge** . 
  
      - **Type** : cette section affiche tous les types de messages qui ont été trouvés dans les fichiers PST pour le travail d’importation. Vous pouvez décocher une case en regard d’un type de message que vous souhaitez exclure. Vous ne pouvez pas exclure l’autre type de message. Consultez la section [Plus d’informations](#more-information) pour obtenir la liste des éléments de boîte aux lettres inclus dans la catégorie Autres.
  
      - **Utilisateurs** : vous pouvez exclure les messages envoyés ou reçus par des personnes spécifiques. Pour exclure les personnes qui apparaissent dans le champ From:, To: field, or the Cc: field of messages, cliquez sur **Exclure les utilisateurs** en regard de ce type de destinataire. Tapez l’adresse e-mail (adresse SMTP) de la personne, puis cliquez sur **Ajouter**![une nouvelle icône.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) pour les ajouter à la liste des utilisateurs exclus pour ce type de destinataire, puis cliquez sur **Enregistrer** pour enregistrer la liste des utilisateurs exclus. 
  
        > [!NOTE]
        > Microsoft 365 n’affiche pas les insights de données résultant de la définition du filtre **Personnes**. Toutefois, si vous définissez ce filtre pour exclure les messages envoyés ou reçus par des personnes spécifiques, ces messages seront exclus pendant le processus d’importation réel. 
  
    c. Cliquez sur **Appliquer** dans la page **Autres options de filtrage** pour enregistrer vos paramètres de filtre. 
  
    Les insights de données sur la page **Importer des données vers Office 365** sont mis à jour en fonction de vos paramètres de filtre, y compris la quantité totale de données qui seront importées en fonction des paramètres de filtre. Un résumé des paramètres de filtre s’affiche également. Vous pouvez cliquer sur **Modifier** en regard d’un filtre pour modifier le paramètre si nécessaire. 
  
    ![Les insights de données sont mis à jour en fonction de vos paramètres de filtre.](../media/897e20fb-3b13-44c3-9d56-9f330750f2a3.png)
  
    d. Cliquez sur **Suivant**.
  
    Une page d’état s’affiche montrant vos paramètres de filtre. Là encore, vous pouvez modifier n’importe quel paramètre de filtre.
  
    e. Cliquez sur **Importer des données** pour démarrer l’importation. La quantité totale de données qui seront importées s’affiche. 
  
    Ou
  
    a. Cliquez sur **Non, je veux tout importer** pour importer toutes les données des fichiers PST dans Office 365, puis cliquez sur **Suivant**.
  
    b. Dans la page **Importer des données vers Office 365**, cliquez sur **Importer des données** pour démarrer l’importation. La quantité totale de données qui seront importées s’affiche. 
  
6. Sous l’onglet **Importer**, cliquez sur **Actualiser**![.](../media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) L’état du travail d’importation s’affiche dans la colonne **État** .
  
7. Cliquez sur le travail d’importation pour afficher des informations plus détaillées, telles que l’état de chaque fichier PST et les paramètres de filtre que vous avez configurés.

## <a name="more-information"></a>Plus d’informations

- Comment Microsoft 365 détermine-t-il les incréments pour le filtre d’âge ? Lorsque Microsoft 365 analyse un fichier PST, il examine l’horodatage envoyé ou reçu de chaque élément (si un élément a un horodatage envoyé et reçu, la date la plus ancienne est sélectionnée). Microsoft 365 examine ensuite la valeur d’année de cet horodatage et la compare à la date actuelle pour déterminer l’âge de l’élément. Ces âges sont ensuite utilisés comme valeurs dans la liste déroulante du filtre **Âge** . Par exemple, si un fichier PST contient des messages de 2016, 2015 et 2014, les valeurs du filtre **Âge** sont **1 an**, **2 ans** et **3 ans**.
  
- Le tableau suivant répertorie les types de messages inclus dans la catégorie **Autre** dans le filtre **Type** de la page **Plus d’options** (voir l’étape 5b de la procédure précédente). Actuellement, vous ne pouvez pas exclure les éléments de la catégorie « Autres » lorsque vous importez des fichiers PST dans Office 365. 
  
    |**ID de la classe de message**|**Éléments de boîte aux lettres qui utilisent cette classe de message**|
    |:-----|:-----|
    |Ipm. Activité  <br/> |Entrées de journal  <br/> |
    |Ipm. Document  <br/> |Documents et fichiers (non joints à un e-mail)  <br/> |
    |Ipm. Fichier  <br/> |(identique à IPM. Document)  <br/> |
    |Ipm. Note.IMC.Notification  <br/> |Rapports envoyés par Internet Mail Connect, qui est la passerelle Exchange Server vers Internet  <br/> |
    |Ipm. Note.Microsoft.Fax  <br/> |Télécopie de messages  <br/> |
    |Ipm. Note.Rules.Oof.Template.Microsoft  <br/> |Messages d’autoreply d’absence du bureau  <br/> |
    |Ipm. Note.Rules.ReplyTemplate.Microsoft  <br/> |Réponses envoyées par une règle de boîte de réception  <br/> |
    |Ipm. Ole. Classe  <br/> |Exceptions pour une série périodique  <br/> |
    |Ipm. Recall.Report  <br/> |Rapports de rappel de message  <br/> |
    |Ipm. Distance  <br/> |Messages électroniques distants  <br/> |
    |Ipm. Rapport  <br/> |Rapports d’état d’élément  <br/> |
