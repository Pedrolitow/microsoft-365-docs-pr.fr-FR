---
title: Menaces sans fichier
ms.reviewer: ''
description: En savoir plus sur les catégories de menaces sans fichier et de programmes malveillants qui habitent au pays
keywords: fileless, fileless malware, living off the land,bins, amsi, behavior monitoring, memory scanning, boot sector protection, security, malware, Windows Defender ATP, antivirus, AV, Microsoft Defender ATP, next-generation protection
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
search.appverid: met150
ms.technology: m365d
ms.openlocfilehash: 97545714ff468c7be238585ab5d137a1ac93a5f9
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63681888"
---
# <a name="fileless-threats"></a>Menaces sans fichier

Quelles sont exactement les menaces sans fichier ? Le terme « fileless » suggère qu’une menace n’est pas dans un fichier, par exemple un porte-dérobateur qui réside uniquement dans la mémoire d’un ordinateur. Toutefois, il n’existe aucune définition pour les programmes malveillants sans fichier. Le terme est utilisé à grande étendue, et parfois pour décrire les familles de programmes malveillants qui s’appuient sur des fichiers pour fonctionner.

Les attaques [impliquent plusieurs étapes](https://attack.mitre.org/wiki/ATT&CK_Matrix) pour des fonctionnalités telles que l’exécution, la persistance ou le vol d’informations. Certaines parties de la chaîne d’attaque peuvent être sans fichier, tandis que d’autres peuvent impliquer le système de fichiers sous une forme ou une autre.

Pour plus de clarté, les menaces sans fichier sont regroupées en différentes catégories.

![Diagramme complet des programmes malveillants sans fichier.](../../media/security-intelligence-images/fileless-malware.png)<br>
*Figure 1. Diagramme complet des programmes malveillants sans fichier*

Les menaces sans fichier peuvent être classées par leur point d’entrée, ce qui indique comment les programmes malveillants sans fichier peuvent arriver sur un ordinateur. Ils peuvent arriver par le biais d’une faille de sécurité, d’un matériel compromis ou d’une exécution régulière d’applications et de scripts.

Ensuite, listez la forme du point d’entrée. Par exemple, les attaques peuvent être basées sur des fichiers ou des données réseau, les périphériques PCI sont un type de vecteur matériel et les scripts et les exécutables sont des sous-catégories du vecteur d’exécution.

Enfin, classifiez l’hôte de l’infection. Par exemple, une application Flash peut contenir diverses menaces telles qu’une attaque, un simple exécutable et un microprogramme malveillant provenant d’un périphérique matériel.

La classification vous permet de diviser et de classer les différents types de menaces sans fichier. Certaines sont plus dangereuses, mais aussi plus difficiles à implémenter, tandis que d’autres sont plus couramment utilisées, même si (ou précisément en raison) ne sont pas très avancées.

À partir de cette catégorisation, vous pouvez glean trois principaux types de menaces sans fichier en fonction de la quantité d’empreintes digitales qu’ils peuvent laisser sur les ordinateurs infectés.

## <a name="type-i-no-file-activity-performed"></a>Type I : aucune activité de fichier n’a été effectuée

Un programme malveillant entièrement sans fichier peut être considéré comme n’nécessitant jamais l’écriture d’un fichier sur le disque. Comment un tel programme malveillant infecterait-il un ordinateur en premier lieu ? Par exemple, un ordinateur cible reçoit des paquets réseau malveillants qui exploitent la vulnérabilité DerBlue. La vulnérabilité permet l’installation de la porte dérobée DoublePulsar, qui se retrouve uniquement dans la mémoire du noyau. Dans ce cas, aucun fichier ou aucune donnée n’est écrit sur un fichier.

Un appareil compromis peut également avoir un code malveillant se masquant dans le microprogramme de l’appareil (tel qu’un BIOS), un périphérique USB (comme l’attaque BadUSB) ou dans le microprogramme d’une carte réseau. Tous ces exemples ne nécessitent pas de fichier sur le disque pour s’exécuter et ne peuvent théoriquement fonctionner qu’en mémoire. Le code malveillant survivrait aux redémarrages, aux reformats de disque et aux réinstallations du système d’exploitation.

Les infections de ce type peuvent être particulièrement difficiles à détecter, car la plupart des produits antivirus n’ont pas la possibilité d’inspecter le microprogramme. Dans les cas où un produit a la possibilité d’inspecter et de détecter les microprogrammes malveillants, il existe toujours des défis importants liés à la correction des menaces à ce niveau. Ce type de programme malveillant sans fichier nécessite des niveaux élevés de complexité et dépend souvent d’une configuration matérielle ou logicielle particulière. Il ne s’agit pas d’un vecteur d’attaque qui peut être exploité facilement et de manière fiable. Bien que dangereuses, les menaces de ce type sont rares et peu pratiques pour la plupart des attaques.

## <a name="type-ii-indirect-file-activity"></a>Type II : activité de fichier indirect

Il existe d’autres façons pour les programmes malveillants d’obtenir une présence sans fichier sur un ordinateur sans nécessiter d’efforts d’ingénierie importants. Les programmes malveillants sans fichiers de ce type n’écrivent pas directement des fichiers sur le système de fichiers, mais ils peuvent finir par utiliser des fichiers indirectement. Par exemple, avec les personnes malveillantes du [backdoor Poshspy](https://www.fireeye.com/blog/threat-research/2017/03/dissecting_one_ofap.html) , une commande PowerShell malveillante a été installée dans le référentiel WMI et un filtre WMI a été configuré pour exécuter la commande régulièrement.

Il est possible d’effectuer une telle installation via la ligne de commande sans qu’un porte-dérobateur soit déjà sur le fichier. Le programme malveillant peut être installé et théoriquement exécuté sans toucher au système de fichiers. Toutefois, le référentiel WMI est stocké sur un fichier physique dans une zone de stockage centrale gérée par le Gestionnaire d’objets CIM et contient généralement des données légitimes. Même si la chaîne d’infection utilise techniquement un fichier physique, elle est considérée comme une attaque sans fichier, car le référentiel WMI est un conteneur de données à usages multiples qui ne peut pas être détecté et supprimé.

## <a name="type-iii-files-required-to-operate"></a>Type III : fichiers requis pour fonctionner

Certains programmes malveillants peuvent avoir une sorte de persistance sans fichier, mais pas sans utiliser de fichiers pour fonctionner. Kovter est un exemple de ce scénario, qui crée un handler de verbe ouvert shell dans le Registre pour une extension de fichier aléatoire. L’ouverture d’un fichier avec cette extension entraîne l’exécution d’un script via l’outil légitime mshta.exe.

![Image de la clé de Registre de Kovter.](../../media/security-intelligence-images/kovter-reg-key.png)<br>
*Figure 2. Clé de Registre de Kovter*

Lorsque le verbe ouvert est appelé, la commande associée à partir du Registre est lancée, ce qui entraîne l’exécution d’un petit script. Ce script lit les données d’une autre clé de Registre et les exécute, ce qui conduit à leur tour au chargement de la charge utile finale. Toutefois, pour déclencher le verbe ouvert en premier lieu, Kovter doit déposer un fichier avec la même extension ciblée par le verbe (dans l’exemple ci-dessus, l’extension est .bbf5590fd). Il doit également définir une touche d’accès automatique configurée pour ouvrir ce fichier au démarrage de l’ordinateur.

Kovter est considéré comme une menace sans fichier, car le système de fichiers n’est pas d’une utilisation pratique. Les fichiers avec des extensions aléatoires contiennent des données indésirables qui ne sont pas utilisables pour vérifier la présence de la menace. Les fichiers qui stockent le Registre sont des conteneurs qui ne peuvent pas être détectés et supprimés si du contenu malveillant est présent.

## <a name="categorizing-fileless-threats-by-infection-host"></a>Catégorisation des menaces sans fichier par hôte d’infection

Après avoir décrit les grandes catégories, nous pouvons maintenant nous détailler et fournir une répartition des hôtes d’infection. Cette classification complète couvre le panorama de ce que l’on appelle généralement un programme malveillant sans fichier. Il dirige nos efforts pour la recherche et le développement de nouvelles fonctionnalités de protection qui favorisent les classes d’attaques et garantissent que les programmes malveillants n’ont pas le dessus dans la course aux bras.

### <a name="exploits"></a>Exploits

Basé sur un **fichier (Type** III : exécutable, Flash, Java, documents) : un fichier initial peut exploiter le système d’exploitation, le navigateur, le moteur Java, le moteur Flash, etc. pour exécuter un shellcode et fournir une charge utile en mémoire. Alors que la charge utile n’a pas de fichier, le vecteur d’entrée initial est un fichier.

**Basé sur le** réseau (type I) : une communication réseau qui tire parti d’une vulnérabilité dans l’ordinateur cible peut obtenir l’exécution du code dans le contexte d’une application ou du noyau. Par exemple, WannaCry exploite une vulnérabilité précédemment corrigée dans le protocole SMB pour remettre une porte dérobée dans la mémoire du noyau.

### <a name="hardware"></a>Matériel

**Basé sur l’appareil** (Type I : carte réseau, disque dur) : les appareils tels que les disques durs et les cartes réseau nécessitent des chipsets et des logiciels dédiés pour fonctionner. Les logiciels résidant et s’exécutant dans le microprogramme d’un appareil sont appelés microprogrammes. Bien qu’il s’agit d’une tâche complexe, le microprogramme peut être infecté par un programme malveillant, comme le groupe [d’espions Équation a été détecté](https://www.kaspersky.com/blog/equation-hdd-malware/7623/).

**CPU (** Type I) : les processeurs modernes sont complexes et peuvent inclure des sous-systèmes exécutant le microprogramme à des fins de gestion. Ce microprogramme peut être vulnérable au piratage et autoriser l’exécution de code malveillant qui fonctionnerait à partir de l’UC. En décembre 2017, deux chercheurs ont signalé une vulnérabilité qui peut permettre aux attaquants d’exécuter du code à l’intérieur du moteur de gestion [(ME)](https://en.wikipedia.org/wiki/Intel_Management_Engine) présent dans n’importe quel processeur moderne d’Intel. Pendant ce temps, on a observé que le groupe d’attaquants PARTIEL a la possibilité d’utiliser la technologie [AMT (Active Management Technology)](https://en.wikipedia.org/wiki/Intel_Active_Management_Technology) d’Intel pour effectuer des [communications réseau invisibles](https://cloudblogs.microsoft.com/microsoftsecure/2017/06/07/platinum-continues-to-evolve-find-ways-to-maintain-invisibility/), en contournant le système d’exploitation installé. Me et AMT sont essentiellement des micro-ordinateurs autonomes qui opèrent à l’intérieur de l’UC et fonctionnent à un niveau très faible. Étant donné que l’objectif de ces technologies est de fournir une gestion à distance, elles ont un accès direct au matériel, sont indépendantes du système d’exploitation et peuvent s’exécuter même si l’ordinateur est désactivé.

En plus d’être vulnérables au niveau du microprogramme, les processeurs peuvent être fabriqué à l’aide de porte dérobées insérées directement dans le circuit matériel. Cette attaque a été [menée à bien et a démontré qu’elle était possible](https://www.emsec.rub.de/media/crypto/veroeffentlichungen/2015/03/19/beckerStealthyExtended.pdf) dans le passé. Il [a](https://www.theregister.co.uk/2018/08/10/via_c3_x86_processor_backdoor/) été signalé que certains modèles de processeurs x86 contiennent un cœur d’UC incorporé secondaire de la même façon que risc, qui peut effectivement fournir une porte dérobée par le biais de laquelle les applications régulières peuvent obtenir une exécution privilégiée.

**Usb (** type I) : les périphériques USB de toutes sortes peuvent être reprogrammés avec un microprogramme malveillant capable d’interagir avec le système d’exploitation de manière peu efficace. Par exemple, la [technique BadUSB](https://arstechnica.com/information-technology/2014/07/this-thumbdrive-hacks-computers-badusb-exploit-makes-devices-turn-evil/) permet à une clé USB reprogrammée d’agir comme un clavier qui envoie des commandes à des ordinateurs via des frappes de touches ou comme une carte réseau qui peut rediriger le trafic à volonté.

**BioS (** type I) : un BIOS est un microprogramme qui s’exécute à l’intérieur d’un microprogramme. Il s’exécute lorsqu’un ordinateur est sous tension, initialise le matériel, puis transfère le contrôle au secteur de démarrage. Le BIOS est un composant important qui fonctionne à un niveau faible et s’exécute avant le secteur de démarrage. Il est possible de reprogrammer le microprogramme du BIOS avec du code malveillant, comme cela s’est produit dans le passé avec [mebromi rootkit](https://www.webroot.com/blog/2011/09/13/mebromi-the-first-bios-rootkit-in-the-wild/).

**Basée sur l’hyperviseur** (type I) : les processeurs modernes assurent la prise en charge de l’hyperviseur matériel, ce qui permet au système d’exploitation de créer des machines virtuelles robustes. Une machine virtuelle s’exécute dans un environnement simulé et limité, et n’a en théorie pas connaissance de l’émulation. Un programme malveillant prenant le contrôle d’un ordinateur peut implémenter un petit hyperviseur pour se masquer en dehors du domaine du système d’exploitation en cours d’exécution. Les programmes [malveillants de](http://seclists.org/fulldisclosure/2017/Jun/29) ce type ont été par le passé theorisés et des rootkits d’hyperviseur réels ont été observés, bien que peu d’entre eux soient connus à ce jour.

### <a name="execution-and-injection"></a>Exécution et injection

**Basé sur un fichier** (Type III : exécutables, DLLs, fichiers LNK, tâches programmées) : il s’agit du vecteur d’exécution standard. Un exécutable simple peut être lancé en tant que programme malveillant de première phase pour exécuter une charge utile supplémentaire en mémoire, ou injecté dans d’autres processus d’exécution légitimes.

**Basé sur les** macros (Type III : Office documents) : le langage [VBA](/office/vba/Library-Reference/Concepts/getting-started-with-vba-in-office) est un outil flexible et puissant conçu pour automatiser les tâches de modification et ajouter des fonctionnalités dynamiques aux documents. En tant que tel, il peut être abusé par des personnes malveillantes pour effectuer des opérations malveillantes telles que le décodage, l’exécution ou l’injection d’une charge utile exécutable, ou même implémenter un ransomware entier, comme dans le cas de [qkG](https://blog.trendmicro.com/trendlabs-security-intelligence/qkg-filecoder-self-replicating-document-encrypting-ransomware/). Les macros sont exécutées dans le contexte d’un processus Office (par exemple, Winword.exe) et implémentées dans un langage de script. Il n’existe aucun fichier exécutable binaire qu’un antivirus peut inspecter. Bien Office applications nécessitent le consentement explicite de l’utilisateur pour exécuter des macros à partir d’un document, les personnes malveillantes utilisent des techniques d’ingénierie sociale pour obliger les utilisateurs à autoriser l’exécution des macros.

**Basé** sur des scripts (type II : fichier, service, registre, repo WMI, shell) : les langages de script JavaScript, VBScript et PowerShell sont disponibles par défaut sur Windows plateformes. Les scripts ont les mêmes avantages que les macros, ils sont des fichiers textuels (et non des fichiers exécutables binaires) et s’exécutent dans le contexte de l’interpréteur (comme wscript.exe, powershell.exe), qui est un composant propre et légitime. Les scripts sont polyvalents et peuvent être exécutés à partir d’un fichier (en double-cliquant dessus) ou exécutés directement sur la ligne de commande d’un interpréteur. L’exécution sur la ligne de commande permet aux programmes malveillants d’encoder des scripts malveillants en tant que services de démarrage automatique dans les clés de Registre d’exécution automatique en tant qu’abonnements à des [événements WMI](https://www.fireeye.com/blog/threat-research/2017/03/dissecting_one_ofap.html) à partir du repo WMI.[](https://www.gdatasoftware.com/blog/2014/07/23947-poweliks-the-persistent-malware-without-a-file) En outre, une personne malveillante qui a accédé à un ordinateur infecté peut entrer le script dans l’invite de commandes.

**Disque** (Type II : Enregistrement de démarrage) : l’enregistrement de démarrage est le premier secteur d’un disque ou d’un volume et contient le code exécutable requis pour démarrer le processus de démarrage du système d’exploitation. Les menaces telles [que Petya](https://cloudblogs.microsoft.com/microsoftsecure/2017/06/27/new-ransomware-old-techniques-petya-adds-worm-capabilities/?source=mmpc) sont capables d’infecter l’enregistrement de démarrage en l’aritant avec du code malveillant. Lorsque l’ordinateur démarre, le programme malveillant prend immédiatement le contrôle. L’enregistrement de démarrage réside en dehors du système de fichiers, mais il est accessible par le système d’exploitation. Les produits antivirus modernes ont la possibilité de les analyser et de les restaurer.

## <a name="defeating-fileless-malware"></a>Protection contre les programmes malveillants sans fichier

Chez Microsoft, nous surveillons activement le paysage de sécurité pour identifier les nouvelles tendances des menaces et développer des solutions pour atténuer les classes de menaces. Nous instrumentons des protections durables qui sont efficaces contre un large éventail de menaces. Grâce à l’interface AMSI (AntiMalware Scan Interface), à la surveillance du comportement, à l’analyse de la mémoire et à la protection du secteur de démarrage, [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint) peut inspecter les menaces sans fichier même avec une obfuscation importante. Les technologies d’apprentissage automatique dans le cloud nous permettent de mettre à l’échelle ces protections contre les menaces nouvelles et émergentes.

Pour plus d’informations, voir : Hors de la vue, mais pas invisible : la protection contre les programmes malveillants sans fichier avec la surveillance du comportement[, AMSI](https://cloudblogs.microsoft.com/microsoftsecure/2018/09/27/out-of-sight-but-not-invisible-defeating-fileless-malware-with-behavior-monitoring-amsi-and-next-gen-av/) et l’antivirus de nouvelle génération

## <a name="additional-resources-and-information"></a>Ressources et informations supplémentaires

Découvrez comment déployer [des fonctionnalités de protection contre les menaces dans Microsoft 365 E5](/microsoft-365/solutions/deploy-threat-protection).
