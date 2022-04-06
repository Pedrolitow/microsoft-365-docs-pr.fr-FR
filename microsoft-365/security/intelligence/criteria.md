---
title: Comment Microsoft identifie les programmes malveillants et les applications potentiellement indésirables
ms.reviewer: ''
description: Découvrez comment Microsoft examine le logiciel pour les violations de confidentialité et d’autres comportements négatifs, pour déterminer s’il s’agit d’un programme malveillant ou d’une application potentiellement indésirable.
keywords: sécurité, programmes malveillants, menaces de recherche de virus, programmes malveillants de recherche, protection des appareils, infection d’ordinateur, infection de virus, descriptions, correction, dernières menaces, MMdevice, Centre de protection Microsoft contre les programmes malveillants, PUA, applications potentiellement indésirables
ms.prod: m365-security
ms.mktglfcycl: secure
ms.sitesec: library
ms.localizationpriority: medium
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.date: 12/13/2021
search.appverid: met150
ms.technology: m365d
ms.openlocfilehash: 3eb7eefb5309383b46189f784f811224dcfb2b28
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63681884"
---
# <a name="how-microsoft-identifies-malware-and-potentially-unwanted-applications"></a>Comment Microsoft identifie les programmes malveillants et les applications potentiellement indésirables

Microsoft vise à offrir une expérience Windows agréable et productive en travaillant pour vous assurer que vous êtes en sécurité et en contrôle de vos appareils. Microsoft vous protège contre les menaces potentielles en identifiant et en analysant les logiciels et le contenu en ligne. Lorsque vous téléchargez, installez et exécutez des logiciels, nous vérifions la réputation des programmes téléchargés et nous nous assurons que vous êtes protégé contre les menaces connues. Vous êtes également averti des logiciels qui nous sont inconnus.  

Vous pouvez aider Microsoft en [envoyant des logiciels inconnus ou suspects pour analyse](https://www.microsoft.com/wdsi/filesubmission/). Cela permet de s’assurer que les logiciels inconnus ou suspects sont analysés par notre système pour commencer à établir la réputation. [En savoir plus sur l’envoi de fichiers pour analyse](submission-guide.md)

Les sections suivantes fournissent une vue d’ensemble des classifications que nous utilisons pour les applications et des types de comportements qui entraînent cette classification.

>[!NOTE]
> De nouvelles formes de programmes malveillants et d’applications potentiellement indésirables sont développées et distribuées rapidement. La liste suivante n’est peut-être pas exhaustive et Microsoft se réserve le droit d’ajuster, de développer et de mettre à jour ces éléments sans préavis ou annonce.

## <a name="unknown--unrecognized-software"></a>Inconnu – Logiciel non reconnu  

Aucun antivirus ou technologie de protection n’est parfait. Il faut du temps pour identifier et bloquer les sites et applications malveillants, ou faire confiance aux programmes et certificats nouvellement publiés.Avec près de 2 milliards de sites web sur Internet et des logiciels mis à jour et publiés en continu, il est impossible d’avoir des informations sur chaque site et programme.

Pensez aux avertissements inconnus/rarement téléchargés comme un système d’avertissement précoce pour les programmes malveillants potentiellement non détectés. Il existe généralement un délai entre le moment où un nouveau programme malveillant est publié et celui où il est identifié. Tous les programmes rares ne sont pas malveillants, mais le risque dans la catégorie inconnue est beaucoup plus élevé pour l’utilisateur type. Les avertissements pour les logiciels inconnus ne sont pas des blocs. Les utilisateurs peuvent choisir de télécharger et d’exécuter l’application normalement s’ils le souhaitent.

Une fois que suffisamment de données sont rassemblées, les solutions de sécurité de Microsoft peuvent effectuer une détermination. Aucune menace n’est trouvée ou une application ou un logiciel est classé comme programme malveillant ou logiciel potentiellement indésirable.

## <a name="malware"></a>Programme malveillant

Les programmes malveillants sont le nom global des applications et d’autres codes, tels que les logiciels, que Microsoft classe plus  granulairement en tant que logiciels malveillants ou *logiciels indésirables*.

### <a name="malicious-software"></a>Logiciels malveillants

Les logiciels malveillants sont une application ou un code qui compromet la sécurité de l’utilisateur. Les logiciels malveillants peuvent voler vos informations personnelles, verrouiller votre appareil jusqu’à ce que vous payiez une rançon, utiliser votre appareil pour envoyer du courrier indésirable ou télécharger d’autres logiciels malveillants. En règle générale, les logiciels malveillants veulent dupliquer, espionner ou défragmenter les utilisateurs, ce qui les place dans des états vulnérables.

Microsoft classe la plupart des logiciels malveillants dans l’une des catégories suivantes :

* **Backdoor :** Type de programme malveillant qui permet aux pirates informatiques malveillants d’accéder à distance à votre appareil et de le contrôler.

* **Commande et contrôle :** Type de programme malveillant qui infecte votre appareil et établit une communication avec le serveur de commande et de contrôle des pirates informatiques pour recevoir des instructions. Une fois la communication établie, les pirates informatiques peuvent envoyer des commandes qui peuvent voler des données, arrêter et redémarrer l’appareil et perturber les services web.

* **Téléchargeur :** Type de programme malveillant qui télécharge d’autres programmes malveillants sur votre appareil. Il doit se connecter à Internet pour télécharger des fichiers.

* **Dropper :** Type de programme malveillant qui installe d’autres fichiers de programmes malveillants sur votre appareil.Contrairement à un téléchargeur, un lanceur n’a pas besoin de se connecter à Internet pour déposer des fichiers malveillants. Les fichiers déposés sont généralement incorporés dans l’abandon lui-même.

* **Exploit :** Élément de code qui utilise des vulnérabilités logicielles pour accéder à votre appareil et effectuer d’autres tâches, telles que l’installation de programmes malveillants. [Voir plus d’informations sur les exploits](exploits-malware.md).

* **Hacktool :** Type d’outil qui peut être utilisé pour obtenir un accès non autorisé à votre appareil.

* **Virus macro :** Type de programme malveillant qui se propage par le biais de documents infectés, tels que Microsoft Word ou Excel documents. Le virus est exécuté lorsque vous ouvrez un document infecté.

* **Obfuscator :** Type de programme malveillant qui masque son code et son objectif, ce qui rend plus difficile la détection ou la suppression des logiciels de sécurité.

* **Voleur de mot de passe :** Type de programme malveillant qui collecte vos informations personnelles, telles que les noms d’utilisateur et les mots de passe. Il fonctionne souvent avec un keylogger, qui collecte et envoie des informations sur les touches que vous appuyez et les sites web que vous visitez.

* **Ransomware :** Type de programme malveillant qui chiffre vos fichiers ou effectue d’autres modifications qui peuvent vous empêcher d’utiliser votre appareil. Il affiche ensuite une note de rançon qui indique que vous devez payer de l’argent ou effectuer d’autres actions avant de pouvoir utiliser à nouveau votre appareil. [Voir plus d’informations sur les ransomware](/security/compass/human-operated-ransomware).

* **Logiciels de sécurité non malveillants :** Programme malveillant qui prétend être un logiciel de sécurité mais ne fournit aucune protection. Ce type de programme malveillant affiche généralement des alertes sur les menaces inexistantes sur votre appareil. Il tente également de vous convaincre de payer pour ses services.

* **Chevau de France :** Type de programme malveillant qui tente de sembler sans danger. Contrairement à un virus ou à un ver, un chevau de France ne se propage pas seul. Au lieu de cela, il tente de paraître légitime pour insérabler les utilisateurs dans le téléchargement et l’installation. Une fois installés, les chevaux de Recherche effectuent diverses activités malveillantes telles que le vol d’informations personnelles, le téléchargement d’autres programmes malveillants ou l’accès à votre appareil aux personnes malveillantes.

* **Clicker de Chevau de France :** Type de chevau de France qui clique automatiquement sur des boutons ou des contrôles similaires sur des sites web ou des applications. Les attaquants peuvent utiliser ce chevau de France pour cliquer sur des publicités en ligne. Ces clics peuvent fausser des sondages en ligne ou d’autres systèmes de suivi et peuvent même installer des applications sur votre appareil.

* **Ver :** Type de programme malveillant qui se propage à d’autres appareils. Les vers peuvent se propager via le courrier électronique, la messagerie instantanée, les plateformes de partage de fichiers, les réseaux sociaux, les partages réseau et les lecteurs amovibles. Les vers sophistiqués tirez parti des vulnérabilités logicielles pour se propager.

### <a name="unwanted-software"></a>Logiciels indésirables

Microsoft estime que vous devez avoir le contrôle sur votre expérience Windows expérience utilisateur. Les logiciels s’exécutant Windows doivent vous garder le contrôle de votre appareil par le biais de choix informés et de contrôles accessibles. Microsoft identifie les comportements logiciels qui vous garantissent le contrôle. Nous classons les logiciels qui ne montrent pas entièrement ces comportements en tant que « logiciels indésirables ».

#### <a name="lack-of-choice"></a>Manque de choix

Vous devez être informé de ce qui se passe sur votre appareil, y compris le logiciel et s’il est actif.

Les logiciels qui présentent un manque de choix peuvent :

* Ne pas fournir d’informations importantes sur le comportement du logiciel, ainsi que son objectif et son intention.

* Ne pas indiquer clairement quand le logiciel est actif. Il peut également tenter de masquer ou de masquer sa présence.

* Installez, réinstallez ou supprimez des logiciels sans votre autorisation, votre interaction ou votre consentement.

* Installez d’autres logiciels sans indication claire de sa relation avec le logiciel principal.

* Contourner les boîtes de dialogue de consentement de l’utilisateur à partir du navigateur ou du système d’exploitation.

* Faussement être un logiciel de Microsoft.

Le logiciel ne doit pas vous induire en erreur ou vous forcer à prendre des décisions sur votre appareil. Il s’agit d’un comportement qui limite vos choix. Outre la liste précédente, les logiciels qui présentent un manque de choix peuvent :

* Afficher des revendications d’affirmation sur l’état de votre appareil.

* Faites des déclarations erronées ou inexactes sur des fichiers, des entrées de Registre ou d’autres éléments sur votre appareil.

* Affichez les revendications de manière discrète sur l’état de votre appareil et exigez un paiement ou certaines actions en échange de la résolution des problèmes censés.

Les logiciels qui stockent ou transmettent vos activités ou données doivent :

* Notez-le et obtenez votre consentement pour le faire. Le logiciel ne doit pas inclure d’option qui le configure pour masquer les activités associées au stockage ou à la transmission de vos données.

#### <a name="lack-of-control"></a>Manque de contrôle

Vous devez être en mesure de contrôler les logiciels sur votre appareil. Vous devez être en mesure de démarrer, d’arrêter ou de révoquer l’autorisation sur les logiciels.

Les logiciels qui présentent un manque de contrôle peuvent :

* Empêchez ou limitez-vous d’afficher ou de modifier les fonctionnalités ou paramètres du navigateur.

* Ouvrez les fenêtres de navigateur sans autorisation.

* Rediriger le trafic web sans donner de notification et obtenir son consentement.

* Modifiez ou manipulez le contenu de la page web sans votre consentement.

Les logiciels qui modifient votre expérience de navigation doivent uniquement utiliser le modèle d’extensibilité pris en charge par le navigateur pour l’installation, l’exécution, la désactivation ou la suppression. Les navigateurs qui ne fournissent pas de modèles d’extensibilité pris en charge sont considérés comme non extensibles et ne doivent pas être modifiés.

#### <a name="installation-and-removal"></a>Installation et suppression

Vous devez être en mesure de démarrer, d’arrêter ou de révoquer l’autorisation accordée au logiciel. Le logiciel doit obtenir votre consentement avant l’installation et fournir un moyen clair et simple pour l’installer, le désinstaller ou le désactiver.

Les logiciels qui offrent une *expérience d’installation* médiocre peuvent regrouper ou télécharger d’autres « logiciels indésirables » tels que classés par Microsoft.

Les logiciels qui offrent *une expérience de suppression médiocre peuvent* :

* Présentez des invites ou des fenêtres pop-up confuses ou déroutantes lorsque vous essayez de la désinstaller.

* Échec de l’utilisation des fonctionnalités standard d’installation/désinstallation, telles que Ajout/Suppression de programmes.

#### <a name="advertising-and-advertisements"></a>Publicités et publicités

Les logiciels qui promeuvent un produit ou un service en dehors du logiciel lui-même peuvent interférer avec votre expérience informatique. Vous devez avoir le choix et le contrôle clairs lors de l’installation du logiciel qui présente des publicités.

Les publicités présentées par le logiciel doivent :

* Incluez un moyen évident pour les utilisateurs de fermer l’annonce. Le fait de fermer l’annonce ne doit pas ouvrir une autre publicité.

* Incluez le nom du logiciel qui a présenté l’annonce.

Le logiciel qui présente ces publicités doit :

* Fournissez une méthode de désinstallation standard pour le logiciel en utilisant le même nom que celui indiqué dans l’annonce qu’il présente.

Les publicités qui vous sont présentées doivent :

* Être distinguer du contenu du site web.

* Pas d’induire en erreur, de perturber ou de confondre.

* Ne pas contenir de code malveillant.

* Ne pas appeler un téléchargement de fichier.

#### <a name="consumer-opinion"></a>Opinion du consommateur

Microsoft tient à jour un réseau mondial d’analystes et de systèmes d’intelligence dans lequel vous pouvez soumettre [des logiciels pour analyse](https://www.microsoft.com/wdsi/filesubmission). Votre participation permet à Microsoft d’identifier rapidement les nouveaux programmes malveillants. Après analyse, Microsoft crée des informations de sécurité pour les logiciels qui répondent aux critères décrits. Cette veille sur la sécurité identifie le logiciel comme programme malveillant et est disponible pour tous les utilisateurs via Antivirus Microsoft Defender et d’autres solutions anti-programme malveillant Microsoft.

## <a name="potentially-unwanted-application-pua"></a>Application potentiellement indésirable (PUA)

Notre protection PUA vise à protéger la productivité des utilisateurs et à garantir des expériences Windows agréables. Cette protection permet d’offrir des expériences plus productives, performantes Windows agréables. Pour obtenir des instructions sur la façon d’activer la protection PUA dans Chromium de Microsoft Edge et Antivirus Microsoft Defender, voir Détecter et bloquer les [applications potentiellement indésirables](/microsoft-365/security/defender-endpoint/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus).

*Les puA ne sont pas considérées comme des programmes malveillants.*

Microsoft utilise des catégories spécifiques et les définitions de catégorie pour classer les logiciels en tant que PUA.

* **Logiciels publicitaires :** Logiciel qui affiche des publicités ou des promotions, ou vous invite à effectuer des enquêtes pour d’autres produits ou services dans des logiciels autres que lui-même. Cela inclut le logiciel qui insère des publicités dans des pages web.

* **Logiciels (Enterprise** uniquement) : logiciels utilisés pour créer ou télécharger des fichiers ou d’autres fichiers spécifiquement utilisés avec des technologies de partage de fichiers d’égal à égal.

* **Logiciel de cryptomonnaie (Enterprise uniquement)** : logiciel qui utilise les ressources de votre appareil pour l’exploitation des cryptomonnaies.

* **Logiciels de regroupement :** Logiciels qui offrent l’installation d’autres logiciels qui ne sont pas développés par la même entité ou qui ne sont pas requis pour l’utilisation du logiciel. En outre, les logiciels qui offrent d’installer d’autres logiciels éligibles en tant que PUA en fonction des critères décrits dans ce document.

* **Logiciels marketing :** Logiciel qui surveille et transmet les activités des utilisateurs à des applications ou des services autres que lui-même pour la recherche marketing.

* **Logiciels logiciels :** Logiciel qui tente activement d’éviter la détection par les produits de sécurité, y compris les logiciels qui se comportent différemment en présence des produits de sécurité.

* **Mauvaise réputation du secteur :** Logiciels détectés par les fournisseurs de sécurité de confiance avec leurs produits de sécurité. Le secteur de la sécurité est dédié à la protection des clients et à l’amélioration de leur expérience. Microsoft et d’autres organisations du secteur de la sécurité échangent en permanence des connaissances sur les fichiers que nous avons analysés pour offrir aux utilisateurs la meilleure protection possible.

