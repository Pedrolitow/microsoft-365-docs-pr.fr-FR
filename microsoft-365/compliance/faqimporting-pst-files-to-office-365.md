---
title: FAQ sur l’importation de fichiers PST dans Office 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MED150
- MET150
ms.assetid: 2fe71b05-f5a2-4182-ade7-4dc5cabdfd51
description: 'Forum aux questions pour les administrateurs sur l’utilisation du service d’importation Office 365 pour importer les fichiers PST de votre organisation vers des boîtes aux lettres Office 365. '
ms.openlocfilehash: 31df33ffe2c69478f0304bd27b49254995d8b89c
ms.sourcegitcommit: 1c445d68e54ca4249024ca4bb72460dd6fac0a2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "42170484"
---
# <a name="faq-about-importing-pst-files-to-office-365"></a>FAQ sur l’importation de fichiers PST dans Office 365

**Cet article est destiné aux administrateurs. Voulez-vous importer des fichiers PST dans votre propre boîte aux lettres ? Voir [importer le courrier, les contacts et le calendrier à partir d’un fichier. pst Outlook](https://go.microsoft.com/fwlink/p/?LinkID=785075)**|
   
Voici quelques questions fréquemment posées sur l’utilisation du service d’importation Office 365 pour importer en bloc des fichiers PST dans des boîtes aux lettres Office 365. Pour plus d’informations sur l’importation de fichiers PST, voir [vue d’ensemble de l’importation de fichiers PST dans Office 365](https://support.office.com/article/ba688e0a-0fcb-4bd7-8e57-2b669564ea84).
  
## <a name="using-network-upload-to-import-pst-files"></a>Utilisation du chargement réseau pour importer des fichiers PST

Pour obtenir des instructions pas à pas, consultez la rubrique [utiliser le chargement réseau pour importer des fichiers PST dans Office 365](use-network-upload-to-import-pst-files.md).
  
 **De quelles autorisations a-t-on besoin pour créer des tâches d’importation dans le Service d’importation Office 365 ?**
  
Le rôle Importation/Exportation de boîtes aux lettres doit vous avoir été attribué dans Exchange Online pour pouvoir importer des fichiers PST dans des boîtes aux lettres Office 365. Par défaut, ce rôle n’est affecté à aucun groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle Importation/Exportation de boîte aux lettres au groupe de rôles Gestion de l’organisation. Vous pouvez aussi créer un nouveau groupe de rôles, lui attribuer le rôle Importation/Exportation de boîtes aux lettres, puis vous ajouter, vous ou d’autres utilisateurs, en tant que membre. Pour plus d’informations, consultez les sections « Ajouter un rôle à un groupe de rôles » ou « Créer un groupe de rôles » dans [Gérer les groupes de rôles dans Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=730688).
  
En outre, pour créer des tâches d’importation dans le Centre de sécurité et de conformité, une des conditions suivantes doit être remplie :
  
- Vous devez avoir le rôle de destinataire de courrier dans Exchange Online. Par défaut, ce rôle est assigné aux groupes de rôles Gestion de l’organisation et Gestion des destinataires.
    
    Ou
    
- Vous devez être un administrateur général au sein de votre organisation Office 365.
    
> [!TIP]
> Envisagez de créer un nouveau groupe de rôles dans Exchange Online spécialement conçu pour importer les fichiers PST dans Office 365. Pour obtenir le niveau minimum de privilèges requis pour importer des fichiers PST, affectez les rôles d’importation/exportation de boîte aux lettres et de destinataire de courrier au nouveau groupe de rôles et ajoutez ensuite les membres. 
  
 **Où le chargement réseau est-il disponible ?**
  
Le chargement réseau est actuellement disponible dans les régions suivantes : États-Unis, Canada, Brésil, Royaume-Uni, France, Europe, Inde, Asie de l’est, sud-est, Japon, République de Corée et Australie. Network upload will be available in more regions soon.

> [!NOTE]
> Pour l’instant, le chargement réseau des fichiers PST n’est pas disponible en Allemagne et en Suisse. Ce Forum aux questions sera mis à jour lorsque le téléchargement réseau sera disponible dans ces pays.
  
 **À combien revient l’importation de fichiers PST via le chargement du réseau ?**
  
Using network upload to import PST files is free.
  
Cela veut aussi dire qu’après avoir été supprimés de la zone de stockage Azure, les fichiers PST ne figurent plus dans la liste des fichiers d’une tâche d’importation terminée dans le Centre d’administration Microsoft 365. Même si une tâche d’importation figure toujours dans la page **Importer des données dans Office 365**, il est possible que la liste de fichiers PST soit vide au moment d’afficher les détails d’anciennes tâches d’importation. 
  
 **Quelle version du format de fichier PST est prise en charge pour l’importation dans Office 365 ?**
  
Il existe deux versions du format de fichier PST : ANSI et Unicode. Nous vous recommandons d’importer des fichiers qui utilisent le format de fichier PST Unicode. Cependant, les fichiers qui utilisent le format de fichier PST ANSI, tels que ceux dont la langue utilise un jeu de caractères codés sur deux octets (DBCS), peuvent aussi être importés dans Office 365. Pour plus d’informations sur l’importation de fichiers PST ANSI, reportez-vous à l’étape 4 dans [utiliser le chargement réseau pour importer les fichiers PST de votre organisation dans Office 365](use-network-upload-to-import-pst-files.md#step-4-create-the-pst-import-mapping-file).
  
Par ailleurs, les fichiers PST issus d’Outlook version 2007 et ultérieures peuvent être importés dans Office 365.
  
 **Une fois que mes fichiers PST ont été chargés dans la zone de stockage Azure, pendant combien de temps sont-ils conservés dans Azure avant d’être supprimés ?**
  
Si vous décidez d’importer des fichiers PST avec la méthode du chargement réseau, vous les chargez dans un conteneur d’objets blob Azure nommé **ingestiondata**. Si aucune tâche d’importation n’est en cours sur la page **Importer des fichiers PST** dans le Centre de sécurité et de conformité, tous les fichiers PST du conteneur **ingestiondata** dans Azure sont supprimés 30 jours après la création de la tâche d’importation la plus récente dans le Centre de sécurité et de conformité. Cela veut aussi dire que vous devez créer une nouvelle tâche d’importation dans le Centre de sécurité et de conformité (description à l’étape 5 dans les instructions de chargement réseau) dans les 30 jours de chargement des fichiers PST vers Azure. 
  
Cela veut aussi dire qu’après avoir été supprimés de la zone de stockage Azure, les fichiers PST ne figurent plus dans la liste des fichiers d’une tâche d’importation terminée dans le Centre de sécurité et de conformité. Même si une tâche d’importation figure toujours dans la page **Importer des fichiers PST** dans le Centre de sécurité et de conformité, il est possible que la liste de fichiers PST soit vide au moment d’afficher les détails d’anciennes tâches d’importation. 
  
 **Combien de temps faut-il compter avant qu’un fichier PST soit importé dans une boîte aux lettres ?**
  
Cela dépend de la capacité de votre réseau, mais le chargement de chaque téraoctet (To) de données dans la zone de stockage Azure de votre organisation prend généralement plusieurs heures. Après avoir été copié dans la zone de stockage Azure, un fichier PST est importé dans une boîte aux lettres Office 365 à un débit d’au moins 24 Go par jour. Si cette vitesse ne répond pas à vos besoins, vous pouvez envisager d’autres méthodes de migration des données de courrier vers Office 365. Pour obtenir plus d'informations, consultez l'article [Façons de migrer plusieurs comptes de messagerie vers Office 365](https://support.office.com/article/ways-to-migrate-multiple-email-accounts-to-office-365-0a4913fe-60fb-498f-9155-a86516418842).
  
En présence de plusieurs fichiers PST et de plusieurs boîtes aux lettres cibles, le processus d’importation s’exécute en parallèle ; en d’autres termes, chaque paire PST/boîte aux lettres est importée simultanément. De même, si plusieurs fichiers PST sont importés dans une même boîte aux lettres, ils sont importés simultanément.
  
 **Y a-t-il une limite de taille applicable aux messages lors de l’importation de fichiers PST ?**
  
Oui. Si un fichier PST contient un élément de boîte aux lettres dont la taille est supérieure à 150 Mo, l’élément sera ignoré lors du processus d’importation.
  
 **Les propriétés des messages, comme la date d’envoi ou de réception, la liste de destinataires, etc., sont-elles conservées après l’importation de fichiers PST dans une boîte aux lettres Office 365 ?**
  
Oui. Les métadonnées du message d’origine sont inchangées pendant l’importation.
  
 **Une limite est-elle appliquée au nombre de niveaux d’une hiérarchie de dossiers pour un fichier PST que je souhaite importer dans une boîte aux lettres ?**
  
Oui. Vous ne pouvez pas importer un fichier PST comportant 300 niveaux de dossiers imbriqués ou plus.
  
 **Est-il possible d’utiliser le chargement réseau pour importer des fichiers PST dans une boîte aux lettres inactive Office 365 ?**
  
Oui, cela est désormais possible.
  
 **Est-il possible d’utiliser le chargement réseau pour importer des fichiers PST dans une boîte aux lettres d’archivage en ligne dans un déploiement hybride Exchange ?**
  
Oui, cela est désormais possible. 
  
 **Puis-je utiliser le chargement réseau pour importer des fichiers PST dans des dossiers publics dans Exchange Online ?**
  
Non, vous ne pouvez pas importer des fichiers PST dans des dossiers publics.
  
## <a name="using-drive-shipping-to-import-pst-files"></a>Utilisation de l’expédition de disque pour importer des fichiers PST

Pour obtenir des instructions pas à pas, voir [use Drive Shipping to import PST Files to Office 365](use-drive-shipping-to-import-pst-files-to-office-365.md).
  
 **De quelles autorisations a-t-on besoin pour créer des tâches d’importation dans le Service d’importation Office 365 ?**
  
Le rôle Importation/Exportation de boîtes aux lettres doit vous avoir été attribué pour pouvoir importer des fichiers PST dans des boîtes aux lettres Office 365. Par défaut, ce rôle n’est affecté à aucun groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle Importation/Exportation de boîte aux lettres au groupe de rôles Gestion de l’organisation. Vous pouvez aussi créer un nouveau groupe de rôles, lui attribuer le rôle Importation/Exportation de boîtes aux lettres, puis vous ajouter, vous ou d’autres utilisateurs, en tant que membre. Pour plus d’informations, consultez les sections « Ajouter un rôle à un groupe de rôles » ou « Créer un groupe de rôles » dans [Gérer les groupes de rôles dans Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=730688).
  
En outre, pour créer des tâches d’importation dans le Centre de sécurité et de conformité, une des conditions suivantes doit être remplie :
  
- Vous devez avoir le rôle de destinataire de courrier dans Exchange Online. Par défaut, ce rôle est assigné aux groupes de rôles Gestion de l’organisation et Gestion des destinataires.
    
    Ou
    
- Vous devez être un administrateur général au sein de votre organisation Office 365.
    
> [!TIP]
> Envisagez de créer un nouveau groupe de rôles dans Exchange Online spécialement conçu pour importer les fichiers PST dans Office 365. Pour obtenir le niveau minimum de privilèges requis pour importer des fichiers PST, affectez les rôles d’importation/exportation de boîte aux lettres et de destinataire de courrier au nouveau groupe de rôles et ajoutez ensuite les membres. 
  
 **Où l’expédition de disque est-elle disponible ?**
  
L’expédition de disque est actuellement disponible aux États-Unis, au Canada, au Brésil, au Royaume-Uni, en Europe, en Inde, en Asie de l’Est, en Asie du Sud-Est, au Japon, en République de Corée et en Australie. Ce service sera prochainement disponible dans d’autres régions.

> [!NOTE]
> Pour l’instant, l’expédition vers l’importation de fichiers PST n’est pas disponible en Allemagne et en Suisse. Ce Forum aux questions sera mis à jour lors de la mise à disposition des lecteurs dans ces pays.
  
 **Quels sont les contrats de licences commerciaux qui prennent en charge l’expédition de disque ?**
  
L’expédition de disque en vue de l’importation de fichiers PST dans Office 365 est disponible via le programme Accord Entreprise Microsoft (EA). L’expédition de disque n’est pas disponible dans le cadre d’un Contrat de Fourniture de Produits et de Services Microsoft (MPSA).
  
 **À combien revient l’expédition de disque en vue de l’importation de fichiers PST dans Office 365 ?**
  
L’utilisation du service d’expédition de disque pour importer des fichiers PST dans des boîtes aux lettres Office 365 revient à 2 dollars par Go de données. Par exemple, si vous expédiez un disque dur qui contient 1 000 Go (1 To) de fichiers PST, cela revient à 2 000 dollars. Vous pouvez travailler en collaboration avec un partenaire qui se chargera de payer les frais d’importation. Pour plus d’informations sur la recherche d’un partenaire, consultez [Trouver votre partenaire ou revendeur Office 365](https://go.microsoft.com/fwlink/p/?LinkId=785197).
  
 **Quels types de disque dur est-il possible d’expédier ?**
  
Seuls les lecteurs SSD 2,5 ou 2,5 pouces ou les disques durs internes 3,5 pouces SATA II/III sont pris en charge par le Service d’importation Office 365. Vous pouvez utiliser des disques durs jusqu'à 10 To. Pour les tâches d’importation, uniquement le premier volume de données sur le disque dur est traité. Le volume de données doit être au format NTFS. Lorsque vous copiez des données sur un disque dur, vous pouvez connecter ce dernier directement au moyen d’un connecteur pour SSD de 2,5 pouces ou SATA II/III de 2,5 ou 3,5 pouces, ou vous pouvez le connecter en externe au moyen d’un adaptateur USB externe pour SSD de 2,5 pouces ou SATA II/III de 2,5 ou 3,5 pouces.
  
> [!IMPORTANT]
> Les disques durs externes fournis avec une carte USB intégrée ne sont pas pris en charge par le Service d’importation Office 365. En outre, le disque à l’intérieur du boîtier d’un disque dur externe ne peut pas être utilisé. Veuillez ne pas envoyer de disques durs externes. 
  
 **Combien de disques durs puis-je expédier pour une seule tâche d’importation ?**
  
Vous pouvez expédier au maximum 10 disques durs pour une même tâche d’importation.
  
 **Quel délai faut-il compter entre le moment où j’expédie mon disque dur et le moment où les données sont sur le centre de données Microsoft ?**
  
Cela dépend de plusieurs facteurs, comme votre proximité par rapport au centre de données Microsoft et le type d’expédition choisi pour l’envoi de votre disque dur (livraison le jour suivant, livraison à deux jours ou envoi économique). La plupart des expéditeurs vous communiquent un numéro de suivi pour suivre le statut de votre livraison.
  
 **Une fois mon disque dur arrivé au centre de données de Microsoft, combien de temps faut-il pour charger mon fichiers PST dans Azure ?**
  
Une fois que votre disque dur est reçu dans le centre de données Microsoft, il faut entre 7 et 10 jours ouvrés pour télécharger les fichiers PST dans la zone de stockage Azure de votre organisation. Les fichiers PST seront téléchargés vers un conteneur d’objets BLOB Azure nommé **ingestiondata**. 
  
 **Combien de temps faut-il compter avant qu’un fichier PST soit importé dans une boîte aux lettres ?**
  
Une fois les fichiers PST chargés dans l’espace de stockage Azure, Office 365 analyse les données des fichiers PST (de manière sécurisée) afin d’identifier l’âge des éléments et les différents types de messages contenus dans les fichiers PST. Une fois cette analyse terminée, vous pourrez importer toutes les données des fichiers PST ou définir des filtres qui contrôlent les données importées. Après le démarrage de la tâche d’importation, un fichier PST est importé dans une boîte aux lettres Office 365 à un débit d’au moins 24 Go par jour. Si cette vitesse ne répond à vos besoins, vous pouvez envisager d’autres méthodes d’importation des données de courrier dans Office 365. Pour obtenir plus d'informations, consultez l'article [Façons de migrer plusieurs comptes de messagerie vers Office 365](https://support.office.com/article/ways-to-migrate-multiple-email-accounts-to-office-365-0a4913fe-60fb-498f-9155-a86516418842).
  
En présence de plusieurs fichiers PST et de plusieurs boîtes aux lettres cibles, le processus d’importation s’exécute en parallèle ; en d’autres termes, chaque paire PST/boîte aux lettres est importée simultanément. De même, si plusieurs fichiers PST sont importés dans une même boîte aux lettres, ils sont importés simultanément.
  
 **Une fois que Microsoft a chargé mes fichiers PST dans Azure, pendant combien de temps sont-ils conservés dans Azure avant d’être supprimés ?**
  
Tous les fichiers PST de l’emplacement de stockage Azure de votre organisation (dans un conteneur BLOB nommé **ingestiondata**) sont supprimés 30 jours après la création de la tâche d’importation la plus récente dans la page **Importer les fichiers PST** du centre de sécurité & conformité. 
  
Cela veut aussi dire qu’après avoir été supprimés de la zone de stockage Azure, les fichiers PST ne figurent plus dans la liste des fichiers d’une tâche d’importation terminée dans le Centre de sécurité et de conformité. Même si une tâche d’importation figure toujours dans la page **Importer des fichiers PST** dans le Centre de sécurité et de conformité, il est possible que la liste de fichiers PST soit vide au moment d’afficher les détails d’anciennes tâches d’importation. 
  
 **Quelle version du format de fichier PST est prise en charge pour l’importation dans Office 365 ?**
  
Il existe deux versions du format de fichier PST : ANSI et Unicode. Nous vous recommandons d’importer des fichiers qui utilisent le format de fichier PST Unicode. Cependant, les fichiers qui utilisent le format de fichier PST ANSI, tels que ceux dont la langue utilise un jeu de caractères codés sur deux octets (DBCS), peuvent aussi être importés dans Office 365. Pour plus d’informations sur l’importation de fichiers PST ANSI, reportez-vous à l’étape 3 de la section [use Drive Shipping to import PST Files to Office 365](use-drive-shipping-to-import-pst-files-to-office-365.md#step-3-create-the-pst-import-mapping-file).
  
Par ailleurs, les fichiers PST issus d’Outlook version 2007 et ultérieures peuvent être importés dans Office 365.
  
 **Y a-t-il une limite de taille applicable aux messages lors de l’importation de fichiers PST ?**
  
Oui. Si un fichier PST contient un élément de boîte aux lettres dont la taille est supérieure à 150 Mo, l’élément sera ignoré lors du processus d’importation.
  
 **Les propriétés des messages, comme la date d’envoi ou de réception, la liste de destinataires, etc., sont-elles conservées après l’importation de fichiers PST dans une boîte aux lettres Office 365 ?**
  
Oui. Les métadonnées du message d’origine sont inchangées pendant l’importation
  
 **Une limite est-elle appliquée au nombre de niveaux d’une hiérarchie de dossiers pour un fichier PST que je souhaite importer dans une boîte aux lettres ?**
  
Oui. Vous ne pouvez pas importer un fichier PST comportant 300 niveaux de dossiers imbriqués ou plus.
  
 **Est-il possible d’expédier un disque en vue de l’importation de fichiers PST dans une boîte aux lettres inactive Office 365 ?**
  
Oui, cela est désormais possible.
  
 **Est-il possible d’expédier un disque en vue d’importer des fichiers PST dans une boîte aux lettres d’archivage en ligne dans un déploiement hybride Exchange ?**
  
Oui, cela est désormais possible. 
  
 **Puis-je utiliser l’expédition de disque pour importer des fichiers PST dans des dossiers publics dans Exchange Online ?**
  
Non, vous ne pouvez pas importer des fichiers PST dans des dossiers publics.
  
 **Est-il possible de demander à Microsoft de réinitialiser mon disque dur avant de me le retourner ?**
  
Non, Microsoft ne peut pas réinitialiser les disques durs avant leur renvoi aux clients. Les disques durs vous sont renvoyés en l’état, tels que Microsoft les a reçus.
  
 **Est-il possible de demander à Microsoft de broyer mon disque dur au lieu de me le réexpédier ?**
  
Non, Microsoft ne peut pas détruire votre disque dur. Les disques durs vous sont renvoyés en l’état, tels que Microsoft les a reçus.
  
 **Par quels services de courrier l’expédition de retour est-elle assurée ?**
  
Si vous êtes un client résidant aux États-Unis ou en Europe, Microsoft fera appel à FedEx pour vous retourner le disque dur. Pour toutes les autres régions, Microsoft fait appel à DHL.
  
 **Quel est le coût de l’expédition de retour ?**
  
Les frais d’expédition de retour varient en fonction de votre proximité par rapport au centre de données Microsoft auquel vous avez expédié votre disque dur. Microsoft imputera les frais de retour de votre disque dur sur votre compte FedEx ou DHL. Les frais d’expédition de retour sont à votre charge.
  
 **Est-il possible d’expédier un disque dur à Microsoft en utilisant un service d’expédition de courrier spécial, comme une expédition personnalisée FedEx ?**
  
Oui.
  
 **Y a-t-il des formalités particulières à effectuer pour expédier un disque dur à l’étranger ?**
  
Le disque dur que vous expédiez à Microsoft va peut-être devoir franchir des frontières internationales. Si c’est le cas, il vous appartient de vérifier que le disque dur et les données qu’il contient sont importés et/ou exportés conformément à la législation en vigueur. Avant d’expédier un disque dur, vérifiez auprès de vos conseillers si, du point de vue légal, le disque et les données peuvent être expédiés au centre de données Microsoft spécifié. Vous aurez ainsi la garantie qu’il parviendra à Microsoft dans un délai raisonnable.
