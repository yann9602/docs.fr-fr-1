---
title: "Guide pratique pour modifier le fichier de configuration de l’ordinateur pour activer la prise en charge IPv6"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 5611b677-b9cc-43b8-a434-60e18d89aada
caps.latest.revision: 18
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 6a23a2690b0df30eaa815d0b321200af3a3403e5
ms.contentlocale: fr-fr
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-modify-the-computer-configuration-file-to-enable-ipv6-support"></a>Guide pratique pour modifier le fichier de configuration de l’ordinateur pour activer la prise en charge IPv6
L’exemple de code suivant montre comment modifier le fichier de configuration (*machine.config*) d’un ordinateur pour activer la prise en charge d’IPv6. Le fichier *machine.config* est stocké dans le dossier *%Windir%\Microsoft.NET\Framework*, situé dans le répertoire d’installation de Windows. Il y a un fichier *machine.config* distinct dans les dossiers sous *%Windir%\Microsoft.NET\Framework* pour chaque version de .NET Framework installée sur l’ordinateur (par exemple, *C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config*).  
  
 Ces paramètres peuvent également être effectués dans le fichier de configuration de l'application, qui est prioritaire sur le fichier de configuration de votre ordinateur.  
  
 Pour .NET Framework version 1.1 ou antérieure, la valeur du commutateur de configuration **ipv6 enabled** spécifie si les membres de la classe <xref:System.Net.Dns?displayProperty=fullName> retournent des adresses IPv6.  
  
 Pour .NET Framework version 2.0 ou ultérieure, si Windows prend en charge le protocole IPv6, tous les membres de la classe <xref:System.Net.Dns?displayProperty=fullName> (par exemple, la méthode <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=fullName>) retournent des adresses IPv6 avec une limitation. Les membres obsolètes de la classe <xref:System.Net.Dns?displayProperty=fullName> (par exemple, la méthode <xref:System.Net.Dns.Resolve%2A?displayProperty=fullName>) lisent et reconnaissent la valeur dans le fichier de configuration.  
  
> [!NOTE]
>  Pour .NET Framework version 2.0 ou ultérieure, IPv6 est activé par défaut. Pour .NET Framework version 1.1 ou antérieure, IPv6 est désactivé par défaut.  
  
## <a name="example"></a>Exemple  
  
```xml  
<system.net>  
    …………  
    <settings>  
        …………  
        <ipv6 enabled="true"/>   
    ……………  
    </settings>  
    ………………  
<system.net>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Adressage IPv6](../../../docs/framework/network-programming/ipv6-addressing.md)   
 [Schéma des paramètres réseau](../../../docs/framework/configure-apps/file-schema/network/index.md)   
 [\<ipv6>, élément (paramètres réseau)](../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)

