---
title: Comment Microsoft identifie les programmes malveillants et les applications potentiellement indésirables
ms.reviewer: ''
description: Découvrez comment Microsoft examine les logiciels pour les violations de la confidentialité et d’autres comportements négatifs, afin de déterminer s’il s’agit de programmes malveillants ou d’une application potentiellement indésirable.
keywords: sécurité, programmes malveillants, menaces de recherche sur les virus, programmes malveillants de recherche, protection des appareils, infection par ordinateur, infection du virus, descriptions, correction, menaces les plus récentes, MMdevice, Centre de protection Microsoft contre les programmes malveillants, PUA, applications potentiellement indésirables
ms.service: microsoft-365-security
ms.mktglfcycl: secure
ms.sitesec: library
ms.localizationpriority: medium
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
ms.topic: conceptual
ms.date: 12/13/2021
search.appverid: met150
ms.openlocfilehash: 8f39e194015b22177f1418449cbef825c45ce1f9
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68633348"
---
# <a name="how-microsoft-identifies-malware-and-potentially-unwanted-applications"></a>Comment Microsoft identifie les programmes malveillants et les applications potentiellement indésirables

Microsoft vise à offrir une expérience Windows agréable et productive en travaillant pour vous assurer que vous êtes en sécurité et dans le contrôle de vos appareils. Microsoft vous aide à vous protéger contre les menaces potentielles en identifiant et en analysant les logiciels et le contenu en ligne. Lorsque vous téléchargez, installez et exécutez des logiciels, nous vérifions la réputation des programmes téléchargés et nous vérifions que vous êtes protégé contre les menaces connues. Vous êtes également averti des logiciels qui nous sont inconnus.  

Vous pouvez aider Microsoft [en soumettant des logiciels inconnus ou suspects à des fins d’analyse](https://www.microsoft.com/wdsi/filesubmission/). Cela permet de s’assurer que les logiciels inconnus ou suspects sont analysés par notre système pour commencer à établir la réputation. [En savoir plus sur l’envoi de fichiers à des fins d’analyse](submission-guide.md)

Les sections suivantes fournissent une vue d’ensemble des classifications que nous utilisons pour les applications et des types de comportements qui mènent à cette classification.

>[!NOTE]
> De nouvelles formes de programmes malveillants et d’applications potentiellement indésirables sont développées et distribuées rapidement. La liste suivante peut ne pas être exhaustive et Microsoft se réserve le droit de les ajuster, de les développer et de les mettre à jour sans préavis ni annonce préalable.

## <a name="unknown--unrecognized-software"></a>Inconnu – Logiciels non reconnus  

Aucune technologie antivirus ou de protection n’est parfaite. Il faut du temps pour identifier et bloquer les sites et applications malveillants, ou approuver les programmes et certificats nouvellement publiés. Avec près de 2 milliards de sites web sur Internet et des logiciels mis à jour et publiés en permanence, il est impossible d’avoir des informations sur chaque site et programme.

Considérez les avertissements inconnus/rarement téléchargés comme un système d’avertissement précoce pour les programmes malveillants potentiellement non détectés. Il y a généralement un délai à partir du moment où un nouveau programme malveillant est publié jusqu’à ce qu’il soit identifié. Tous les programmes rares ne sont pas malveillants, mais le risque dans la catégorie inconnue est beaucoup plus élevé pour l’utilisateur standard. Les avertissements pour les logiciels inconnus ne sont pas des blocs. Les utilisateurs peuvent choisir de télécharger et d’exécuter l’application normalement s’ils le souhaitent.

Une fois que suffisamment de données sont collectées, les solutions de sécurité de Microsoft peuvent effectuer une détermination. Soit aucune menace n’est trouvée, soit une application ou un logiciel est classé comme un programme malveillant ou un logiciel potentiellement indésirable.

## <a name="malware"></a>Programme malveillant

Les programmes malveillants sont le nom général des applications et d’autres codes, tels que les logiciels, que Microsoft classe de manière plus granulaire en tant que *logiciels malveillants* ou *logiciels indésirables*.

### <a name="malicious-software"></a>Logiciels malveillants

Les logiciels malveillants sont une application ou un code qui compromet la sécurité des utilisateurs. Les logiciels malveillants peuvent voler vos informations personnelles, verrouiller votre appareil jusqu’à ce que vous payiez une rançon, utiliser votre appareil pour envoyer du courrier indésirable ou télécharger d’autres logiciels malveillants. En général, les logiciels malveillants veulent tromper, tromper ou frauder les utilisateurs, les plaçant dans des états vulnérables.

Microsoft classe la plupart des logiciels malveillants dans l’une des catégories suivantes :

* **Porte dérobée:** Type de programme malveillant qui permet aux pirates malveillants d’accéder à distance à votre appareil et de le contrôler.

* **Commande et contrôle :** Type de programme malveillant qui infecte votre appareil et établit une communication avec le serveur de commandes et de contrôle des pirates pour recevoir des instructions. Une fois la communication établie, les pirates informatiques peuvent envoyer des commandes qui peuvent voler des données, arrêter et redémarrer l’appareil, et perturber les services web.

* **Downloader:** Type de programme malveillant qui télécharge d’autres programmes malveillants sur votre appareil. Il doit se connecter à Internet pour télécharger des fichiers.

* **Compte-gouttes:** Type de programme malveillant qui installe d’autres fichiers de programmes malveillants sur votre appareil. Contrairement à un téléchargeur, une liste déroulante n’a pas besoin de se connecter à Internet pour supprimer les fichiers malveillants. Les fichiers supprimés sont généralement incorporés dans la liste déroulante elle-même.

* **Exploiter:** Code qui utilise des vulnérabilités logicielles pour accéder à votre appareil et effectuer d’autres tâches, telles que l’installation de programmes malveillants. [Voir plus d’informations sur les exploits](exploits-malware.md).

* **Hacktool:** Type d’outil qui peut être utilisé pour obtenir un accès non autorisé à votre appareil.

* **Virus de macro :** Type de programme malveillant qui se propage par le biais de documents infectés, tels que des documents Microsoft Word ou Excel. Le virus est exécuté lorsque vous ouvrez un document infecté.

* **Obfuscateur :** Type de programme malveillant qui masque son code et son objectif, ce qui rend plus difficile la détection ou la suppression des logiciels de sécurité.

* **Vol de mot de passe :** Type de programme malveillant qui collecte vos informations personnelles, telles que les noms d’utilisateur et les mots de passe. Il fonctionne souvent avec un keylogger, qui collecte et envoie des informations sur les clés que vous appuyez et les sites web que vous visitez.

* **Ransomware:** Type de programme malveillant qui chiffre vos fichiers ou effectue d’autres modifications qui peuvent vous empêcher d’utiliser votre appareil. Il affiche ensuite une note de rançon indiquant que vous devez payer de l’argent ou effectuer d’autres actions avant de pouvoir réutiliser votre appareil. [Voir plus d’informations sur les ransomware](/security/compass/human-operated-ransomware).

* **Logiciels de sécurité non autorisés :** Programmes malveillants qui prétendent être des logiciels de sécurité, mais qui ne fournissent aucune protection. Ce type de programme malveillant affiche généralement des alertes sur les menaces inexistantes sur votre appareil. Il tente également de vous convaincre de payer pour ses services.

* **Trojan:** Type de programme malveillant qui tente d’apparaître inoffensif. Contrairement à un virus ou un ver, un cheval de Troie ne se propage pas seul. Au lieu de cela, il tente d’avoir l’air légitime d’envoyer les utilisateurs en les téléchargeant et en les installant. Une fois installés, les chevaux de Troie effectuent diverses activités malveillantes telles que le vol d’informations personnelles, le téléchargement d’autres programmes malveillants ou l’accès des attaquants à votre appareil.

* **Clicker de Troie :** Type de cheval de Troie qui clique automatiquement sur des boutons ou des contrôles similaires sur des sites web ou des applications. Les attaquants peuvent utiliser ce cheval de Troie pour cliquer sur les publicités en ligne. Ces clics peuvent fausser les sondages en ligne ou d’autres systèmes de suivi et peuvent même installer des applications sur votre appareil.

* **Ver:** Type de programme malveillant qui se propage à d’autres appareils. Les vers peuvent se propager par e-mail, messagerie instantanée, plateformes de partage de fichiers, réseaux sociaux, partages réseau et lecteurs amovibles. Les vers sophistiqués tirent parti des vulnérabilités logicielles pour se propager.

### <a name="unwanted-software"></a>Logiciels indésirables

Microsoft estime que vous devez avoir le contrôle de votre expérience Windows. Les logiciels qui s’exécutent sur Windows doivent vous garder le contrôle de votre appareil par le biais de choix éclairés et de contrôles accessibles. Microsoft identifie les comportements logiciels qui vous permettent de garder le contrôle. Nous classifieons les logiciels qui ne présentent pas entièrement ces comportements comme des « logiciels indésirables ».

#### <a name="lack-of-choice"></a>Manque de choix

Vous devez être averti de ce qui se passe sur votre appareil, y compris ce que fait le logiciel et s’il est actif.

Les logiciels qui présentent un manque de choix peuvent :

* Ne fournissez pas d’avis de premier plan sur le comportement du logiciel, son objectif et son intention.

* Impossible d’indiquer clairement quand le logiciel est actif. Il peut également tenter de masquer ou de masquer sa présence.

* Installez, réinstallez ou supprimez des logiciels sans votre autorisation, votre interaction ou votre consentement.

* Installez d’autres logiciels sans indication claire de sa relation avec le logiciel principal.

* Contourner les dialogues de consentement de l’utilisateur à partir du navigateur ou du système d’exploitation.

* Prétendent faussement être des logiciels de Microsoft.

Les logiciels ne doivent pas vous induire en erreur ou vous forcer à prendre des décisions concernant votre appareil. Il est considéré comme un comportement qui limite vos choix. En plus de la liste précédente, les logiciels qui présentent un manque de choix peuvent :

* Affichez des allégations exagérées sur l’intégrité de votre appareil.

* Faites des revendications trompeuses ou inexactes sur des fichiers, des entrées de Registre ou d’autres éléments sur votre appareil.

* Affichez les revendications de manière alarmante sur l’intégrité de votre appareil et exigez un paiement ou certaines actions en échange de la résolution des problèmes supposés.

Les logiciels qui stockent ou transmettent vos activités ou données doivent :

* Donnez-vous un avis et obtenez le consentement pour le faire. Le logiciel ne doit pas inclure d’option qui le configure pour masquer les activités associées au stockage ou à la transmission de vos données.

#### <a name="lack-of-control"></a>Manque de contrôle

Vous devez être en mesure de contrôler les logiciels sur votre appareil. Vous devez être en mesure de démarrer, d’arrêter ou de révoquer l’autorisation sur les logiciels.

Les logiciels qui présentent un manque de contrôle peuvent :

* Empêchez ou limitez l’affichage ou la modification des fonctionnalités ou des paramètres du navigateur.

* Ouvrez les fenêtres du navigateur sans autorisation.

* Rediriger le trafic web sans donner d’avis et obtenir le consentement.

* Modifiez ou manipulez du contenu de page web sans votre consentement.

Les logiciels qui modifient votre expérience de navigation doivent uniquement utiliser le modèle d’extensibilité pris en charge par le navigateur pour l’installation, l’exécution, la désactivation ou la suppression. Les navigateurs qui ne fournissent pas de modèles d’extensibilité pris en charge sont considérés comme non extensibles et ne doivent pas être modifiés.

#### <a name="installation-and-removal"></a>Installation et suppression

Vous devez être en mesure de démarrer, d’arrêter ou de révoquer l’autorisation accordée aux logiciels. Le logiciel doit obtenir votre consentement avant l’installation, et il doit fournir un moyen clair et simple pour vous de l’installer, de le désinstaller ou de le désactiver.

Les logiciels qui offrent *une expérience d’installation médiocre* peuvent regrouper ou télécharger d’autres « logiciels indésirables » classés par Microsoft.

Les logiciels qui offrent *une expérience de suppression médiocre* peuvent :

* Présentez des invites ou des fenêtres contextuelles déroutantes ou trompeuses lorsque vous essayez de la désinstaller.

* Impossible d’utiliser les fonctionnalités d’installation/désinstallation standard, telles que l’ajout/suppression de programmes.

#### <a name="advertising-and-advertisements"></a>Publicités et publicités

Les logiciels qui promeuvent un produit ou un service en dehors du logiciel lui-même peuvent interférer avec votre expérience informatique. Vous devez disposer d’un choix et d’un contrôle clairs lors de l’installation de logiciels qui présentent des publicités.

Les publicités présentées par les logiciels doivent :

* Incluez un moyen évident pour les utilisateurs de fermer la publicité. L’acte de fermer la publicité ne doit pas ouvrir une autre publicité.

* Incluez le nom du logiciel qui a présenté la publicité.

Le logiciel qui présente ces publicités doit :

* Fournissez une méthode de désinstallation standard pour le logiciel en utilisant le même nom que celui indiqué dans la publicité qu’il présente.

Les publicités qui vous sont présentées doivent :

* Distinguez-vous du contenu du site web.

* Ne vous trompez pas, ne trompez pas ou ne confondez pas.

* Ne contient pas de code malveillant.

* N’appelle pas de téléchargement de fichier.

#### <a name="consumer-opinion"></a>Opinion des consommateurs

Microsoft gère un réseau mondial d’analystes et de systèmes d’intelligence où vous pouvez [soumettre des logiciels à des fins d’analyse](https://www.microsoft.com/wdsi/filesubmission). Votre participation permet à Microsoft d’identifier rapidement les nouveaux programmes malveillants. Après analyse, Microsoft crée des informations de sécurité pour les logiciels qui répondent aux critères décrits. Cette intelligence de sécurité identifie le logiciel comme logiciel malveillant et est disponible pour tous les utilisateurs via Microsoft Defender antivirus et d’autres solutions anti-programme malveillant Microsoft.

## <a name="potentially-unwanted-application-pua"></a>Application potentiellement indésirable (PUA)

Notre protection PUA vise à protéger la productivité des utilisateurs et à garantir des expériences Windows agréables. Cette protection permet d’offrir des expériences Windows plus productives, performantes et agréables. Pour obtenir des instructions sur l’activation de la protection PUA dans Chromium Microsoft Edge et Microsoft Defender Antivirus, consultez [Détecter et bloquer les applications potentiellement indésirables](/microsoft-365/security/defender-endpoint/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus).

*Les applications potentiellement malveillantes ne sont pas considérées comme des programmes malveillants.*

Microsoft utilise des catégories spécifiques et les définitions de catégorie pour classer les logiciels en tant que PUA.

* **Logiciels publicitaires :** Logiciel qui affiche des publicités ou des promotions, ou vous invite à effectuer des enquêtes pour d’autres produits ou services dans des logiciels autres que lui-même. Cela inclut les logiciels qui insèrent des publicités dans des pages web.

* **Logiciel Torrent (Entreprise uniquement) :** Logiciel utilisé pour créer ou télécharger des torrents ou d’autres fichiers spécifiquement utilisés avec les technologies de partage de fichiers d’égal à égal.

* **Logiciel de chiffrement (Entreprise uniquement) :** Logiciel qui utilise les ressources de votre appareil pour extraire des crypto-monnaies.

* **Logiciels de regroupement :** Logiciel qui propose d’installer d’autres logiciels qui ne sont pas développés par la même entité ou qui ne sont pas requis pour l’exécution du logiciel. En outre, les logiciels qui proposent d’installer d’autres logiciels qui sont éligibles en tant que PUA en fonction des critères décrits dans ce document.

* **Logiciel marketing :** Logiciels qui surveillent et transmettent les activités des utilisateurs à des applications ou services autres que lui-même à des fins de recherche marketing.

* **Logiciel d’évasion :** Logiciels qui tentent activement d’échapper à la détection par les produits de sécurité, y compris les logiciels qui se comportent différemment en présence de produits de sécurité.

* **Mauvaise réputation de l’industrie :** Logiciels détectés par les fournisseurs de sécurité approuvés avec leurs produits de sécurité. L’industrie de la sécurité se consacre à la protection des clients et à l’amélioration de leurs expériences. Microsoft et d’autres organisations du secteur de la sécurité échangent en permanence des connaissances sur les fichiers que nous avons analysés pour fournir aux utilisateurs la meilleure protection possible.

