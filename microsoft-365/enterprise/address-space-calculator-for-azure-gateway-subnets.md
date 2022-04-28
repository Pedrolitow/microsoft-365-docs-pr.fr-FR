---
title: Calculatrice d’espace d’adressage pour les sous-réseaux de passerelle Azure
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 01/07/2021
audience: ITPro
ms.topic: landing-page
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- seo-marvel-apr2020
description: 'Résumé : Calculer l’espace d’adressage d’un sous-réseau de passerelle Azure avec C3, Python ou PowerShell.'
ms.openlocfilehash: a19233b6ec68c92dbf65ecb6a73fc1a0a16e6d31
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65094877"
---
# <a name="address-space-calculator-for-azure-gateway-subnets"></a>Calculatrice d’espace d’adressage pour les sous-réseaux de passerelle Azure

Un réseau virtuel dans les services d’infrastructure Azure connecté à d’autres réseaux doit avoir un sous-réseau de passerelle. Les meilleures pratiques pour définir le sous-réseau de passerelle sont les suivantes :

- La longueur de préfixe du sous-réseau de passerelle peut avoir une longueur maximale de préfixe de 29 (par exemple, 10.119.255.248/29), mais la recommandation actuelle est que vous utilisiez une longueur de préfixe de 27 (par exemple, 10.119.255.224/27).
- Lorsque vous définissez l’espace d’adressage du sous-réseau de passerelle, utilisez la dernière partie de l’espace d’adressage du réseau virtuel.

Pour la deuxième recommandation, vous pouvez déterminer l’espace d’adressage du sous-réseau de passerelle en définissant les bits utilisés pour le sous-réseau de passerelle sur 0 et les bits restants dans l’espace d’adressage du réseau virtuel sur 1. Pour calculer rapidement l’espace d’adressage du sous-réseau de passerelle sans avoir à convertir en binaire et revenir en décimal, vous pouvez utiliser une application console écrite en C# ou Python ou avec un bloc de commandes PowerShell.

Cet article contient des blocs de code C#, Python et PowerShell qui calculent l’espace d’adressage du sous-réseau de passerelle en fonction des valeurs de w.x.y.z/n pour le préfixe d’adresse de réseau virtuel et la longueur du préfixe de sous-réseau de passerelle.

## <a name="c-code-block"></a>Bloc de code C#

Utilisez ce bloc de code pour créer une application console en C#.

```c#
using System; 
using System.Collections.Generic; 
using System.Linq; 
using System.Text; 
using System.Threading.Tasks; 
 
namespace ConsoleApplication1 
{ 
    class Program 
    { 
        static void Main(string[] args) 
        { 
            // Declare variables. 
            const long wOctet = 16777216;  
            const long xOctet = 65536; 
            const long yOctet = 256; 
            double D; 
            int w, x, y, z, vnetPrefLen, gwPrefLen; 
            long d, w2, x2, y2, z2; 
             
 
            // Get the five values needed from the keyboard. 
            Console.WriteLine("**************************************************************************"); 
            Console.WriteLine("*** Gateway subnet address space calculator for Azure virtual networks ***");             
            Console.WriteLine("**************************************************************************");  
            Console.WriteLine(); 
            Console.WriteLine("Please supply your virtual network address space in the form of w.x.y.z/n."); 
            Console.WriteLine(); 
            Console.WriteLine("w="); 
            w = Convert.ToInt32(Console.ReadLine()); 
            Console.WriteLine("x="); 
            x = Convert.ToInt32(Console.ReadLine()); 
            Console.WriteLine("y="); 
            y = Convert.ToInt32(Console.ReadLine()); 
            Console.WriteLine("z="); 
            z = Convert.ToInt32(Console.ReadLine()); 
            Console.WriteLine("n="); 
            vnetPrefLen = Convert.ToInt32(Console.ReadLine()); 
            Console.WriteLine(); 
            Console.WriteLine("Now supply the prefix length of your gateway subnet:"); 
            gwPrefLen = Convert.ToInt32(Console.ReadLine()); 
            Console.WriteLine(); 
 
            // Perform the calculation. 
            D = w * wOctet + x * xOctet + y * yOctet + z; 
            for (int i = vnetPrefLen + 1; i < gwPrefLen + 1; i++) 
            { 
                D = D + Math.Pow(2, 32 - i); 
            } 
            d = Convert.ToInt64(D); 
            w2 = d / wOctet; 
            x2 = (d - w2 * wOctet) / xOctet;  
            y2 = (d - w2 * wOctet - x2 * xOctet) / yOctet; 
            z2 = d - w2 * wOctet - x2 * xOctet - y2 * yOctet; 
             
            // Display the result.             
            Console.WriteLine("**************************************************************************");  
            Console.WriteLine("For the Azure virtual address space {0}.{1}.{2}.{3}/{4}", w, x, y, z, vnetPrefLen); 
            Console.WriteLine("and gateway prefix length of {0}, the gateway subnet address space is:", gwPrefLen); 
            Console.WriteLine(); 
            Console.WriteLine("{0}.{1}.{2}.{3}/{4}", w2, x2, y2, z2, gwPrefLen); 
            Console.WriteLine(); 
            Console.WriteLine("Press ENTER to quit."); 
            Console.ReadLine(); 
        } 
    } 
} 
```

## <a name="python-code-block"></a>Bloc de code Python

Utilisez ce bloc de code pour créer une application console dans Python.

```python
import math 
# Collect the values of w.x.y.z/n for your VNet address space and g, the prefix length of your gateway subnet 
print("**************************************************************************")  
print("*** Gateway subnet address space calculator for Azure virtual networks ***")  
print("**************************************************************************\n")   
print("Please supply your virtual network address space in the form of w.x.y.z/n.");  
w=int(input("w = ")) 
x=int(input("x = ")) 
y=int(input("y = ")) 
z=int(input("z = ")) 
n=int(input("n = ")) 
print("")  
g=int(input("Now supply the prefix length of your gateway subnet: ")) 
print("")  
 
# Calculate  
wOctet = 16777216  
xOctet = 65536  
yOctet = 256  
D = w * wOctet + x * xOctet + y * yOctet + z 
for index in range(n + 1,g + 1): 
    D += 2**(32 - index)  
 
w2 = math.floor(D / wOctet)  
x2 = math.floor((D - w2 * wOctet) / xOctet) 
y2 = math.floor((D - w2 * wOctet - x2 * xOctet) / yOctet) 
z2 = D - w2 * wOctet - x2 * xOctet - y2 * yOctet  
 
# Display the result  
gwAddrPref= "Your gateway address prefix is: " + str(w2) + "." + str(x2) + "." + str(y2) + "." + str(z2) + "/" + str(g)  
print(gwAddrPref) 
```


## <a name="powershell-command-block"></a>Bloc de commande PowerShell

Renseignez les valeurs et exécutez le bloc de commandes résultant dans une fenêtre PowerShell ou dans l’environnement de script intégré PowerShell (ISE).

```powershell
# Specify the values of w.x.y.z/n for your VNet address space and g, the prefix length of your gateway subnet: 
$w= 
$x= 
$y= 
$z= 
$n= 
$g= 
# Calculate 
$wOctet = 16777216 
$xOctet = 65536 
$yOctet = 256 
[long]$D = $w * $wOctet + $x * $xOctet + $y * $yOctet + $z; 
for ($i = $n + 1; $i -lt $g + 1; $i++) 
{ 
$D = $D + [math]::pow(2, 32 - $i) 
} 
$w2 = [math]::floor($D / $wOctet) 
$x2 = [math]::floor( ($D - $w2 * $wOctet) / $xOctet ) 
$y2 = [math]::floor( ($D - $w2 * $wOctet - $x2 * $xOctet) / $yOctet ) 
$z2 = $D - $w2 * $wOctet - $x2 * $xOctet - $y2 * $yOctet 
# Display the result 
$dx= [string]$w2 + "." + [string]$x2 + "." + [string]$y2 + "." + [string]$z2 + "/" + [string]$g 
Write-Host "Your gateway address prefix is: " $dx
```
    
## <a name="related-topics"></a>Voir aussi

[Gestion de Microsoft 365 à l’aide de PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)