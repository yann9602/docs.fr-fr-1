---
title: "WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream), m&#233;thode | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "System.IO.WindowsRuntimeStreamExtensions.AsRandomAccessStream"
apilocation: 
  - "System.Runtime.WindowsRuntime.dll"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: dcc72283-caed-49ee-b45d-ccaf94e97129
caps.latest.revision: 12
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 12
---
# WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream), m&#233;thode
\[Pris en charge dans le .NET Framework 4.5.1 et versions ultérieures\]  
  
 Convertit le flux spécifié en flux d'accès aléatoire.  
  
 **Espace de noms :** <xref:System.IO?displayProperty=fullName>   
 **Assembly :** System.Runtime.WindowsRuntime \(dans System.Runtime.WindowsRuntime.dll\)  
  
## Syntaxe  
  
```csharp  
[CLSCompliantAttribute(false)] public static  IRandomAccessStream AsRandomAccessStream(Stream stream)   
```  
  
```vb  
'Declaration <ExtensionAttribute> _ <CLSCompliantAttribute(False)> _ Public Shared Function AsRandomAccessStream ( _         stream As Stream) As IRandomAccessStream   
```  
  
#### Paramètres  
 `stream`  
  
 Type : <xref:System.IO.Stream?displayProperty=fullName>   
 Flux à convertir.  
  
## Valeur de retour  
 Type : [Windows.Storage.Streams.RandomAccessStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.randomaccessstream.aspx)   
 Flux d'accès aléatoire [!INCLUDE[wrt](../../../includes/wrt-md.md)], qui représente le flux converti.  
  
## Exceptions  
  
|Exception|Condition|  
|---------------|---------------|  
|<xref:System.NotSupportedException>|Le flux à convertir ne prend pas en charge la recherche.|  
  
## Notes  
 Cette méthode d'extension est disponible uniquement lorsque vous développez des applications Windows Store.  Cette méthode offre un moyen pratique de travailler avec des flux dans les applications Windows Store.  Le flux .NET Framework à convertir doit prendre en charge la recherche.  Pour plus d'informations, voir la méthode <xref:System.IO.Stream.Seek%2A?displayProperty=fullName>.  
  
> [!IMPORTANT]
>  Cette API est prise en charge dans le .NET Framework 4.5.1 et versions ultérieures, mais pas dans la version 4.5.  
  
## Informations de version  
 **.NET pour les applications du Windows Store**  
  
 Prise en charge dans : Windows 8.1  
  
## Voir aussi  
 <xref:System.IO.WindowsRuntimeStreamExtensions>   
 [Comment : effectuer une conversion entre les flux .NET Framework et les flux Windows Runtime](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)