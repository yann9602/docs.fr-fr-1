---
title: "Comment&#160;: modifier le fichier de configuration de l’ordinateur pour activer la prise en charge IPv6 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 5611b677-b9cc-43b8-a434-60e18d89aada
caps.latest.revision: 18
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 18
---
# Comment&#160;: modifier le fichier de configuration de l’ordinateur pour activer la prise en charge IPv6
L'exemple de code suivant montre comment modifier le fichier de configuration de l'ordinateur, *machine.config*, pour permettre la prise en charge de IPv6.  Le fichier *machine.config* est stocké dans le dossier de *%Windir%\\Microsoft.NET\\Framework* dans le répertoire où les fenêtres ont été installées.  Il existe un fichier *machine.config* distinct dans les dossiers *%Windir%\\Microsoft.NET\\Framework* pour chaque version du .NET Framework installé sur l'ordinateur \(par exemple, *C:\\WINDOWS\\Microsoft.NET\\Framework\\v2.0.50727\\machine.config*\).  
  
 Ils peuvent également être effectuées dans le fichier de configuration de l'application, qui a priorité sur le fichier de configuration de l'ordinateur.  
  
 Pour le.NET Framework version 1.1 et antérieure, la valeur du commutateur de configuration d' **ipv6 enabled** spécifie si les membres des adresses de IPv6 de retour de classe d' <xref:System.Net.Dns?displayProperty=fullName> .  
  
 Pour le .NET Framework version 2.0 et ultérieure, si les fenêtres IPv6 prend en charge, puis tous les membres de la classe d' <xref:System.Net.Dns?displayProperty=fullName> \(par exemple, la méthode d' <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=fullName> \), retournera des adresses de IPv6 avec une limitation.  Les membres obsolètes de la classe d' <xref:System.Net.Dns?displayProperty=fullName> \(par exemple, la méthode d' <xref:System.Net.Dns.Resolve%2A?displayProperty=fullName> \) indiqueront et peuvent identifier la valeur dans le fichier de configuration.  
  
> [!NOTE]
>  Pour le .NET Framework version 2.0 et ultérieure, IPv6 est activé par défaut.  Pour le.NET Framework version 1.1 et antérieure, IPv6 est désactivé par défaut.  
  
## Exemple  
  
```  
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
  
## Voir aussi  
 [Adressage IPv6](../../../docs/framework/network-programming/ipv6-addressing.md)   
 [Schéma des paramètres réseau](../../../docs/framework/configure-apps/file-schema/network/index.md)   
 [\<ipv6\>, élément \(paramètres réseau\)](../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)