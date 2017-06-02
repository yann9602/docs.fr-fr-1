---
title: "Transfert de type dans le Common Language Runtime | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "assemblys (.NET Framework), transfert de type"
  - "transfert de type"
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# Transfert de type dans le Common Language Runtime
Le transfert de type vous permet de déplacer un type dans un autre assembly sans avoir à recompiler les applications qui utilisent l'assembly d'origine.  
  
 Par exemple, supposons qu'une application utilise la classe `Example` dans un assembly nommé `Utility.dll`.  Les développeurs de `Utility.dll` peuvent décider de refactoriser l'assembly et, dans le cadre du processus, ils peuvent déplacer la classe `Example` dans un autre assembly.  Si l'ancienne version de `Utility.dll` est remplacée par la nouvelle version de `Utility.dll` et son assembly auxiliaire, l'application qui utilise la classe `Example` échoue, car elle ne peut pas localiser la classe `Example` dans la nouvelle version de `Utility.dll`.  
  
 Les développeurs de `Utility.dll` peuvent éviter ce problème en transférant les demandes pour la classe `Example` à l'aide de l'attribut <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>.  Si l'attribut a été appliqué à la nouvelle version de `Utility.dll`, les demandes pour la classe `Example` sont transférées à l'assembly qui contient maintenant la classe.  L'application existante continue à fonctionner normalement, sans recompilation.  
  
> [!NOTE]
>  Dans le .NET Framework version 2.0, vous ne pouvez pas transférer de types provenant d'assemblys écrits en Visual Basic.  Toutefois, une application écrite en Visual Basic peut utiliser des types transférés.  Autrement dit, si l'application utilise un assembly codé en C\# ou C\+\+ et qu'un type de cet assembly est transféré vers un autre assembly, l'application Visual Basic peut utiliser le type transféré.  
  
## Transfert de types  
 Le transfert d'un type s'effectue en quatre étapes :  
  
1.  Déplacez le code source pour le type de l'assembly d'origine vers l'assembly de destination.  
  
2.  Dans l'assembly où était localisé le type, ajoutez un <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> pour le type qui a été déplacé.  Le code suivant montre l'attribut d'un type nommé `Example` qui a été déplacé.  
  
    ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
    ```  
  
    ```cpp#  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
    ```  
  
3.  Compilez l'assembly qui contient maintenant le type.  
  
4.  Recompilez l'assembly où était localisé le type, avec une référence à l'assembly qui contient maintenant le type.  Par exemple, si vous compilez un fichier C\# à partir de la ligne de commande, utilisez l'option [\/reference \(Import Metadata\)](../Topic/-reference%20\(C%23%20Compiler%20Options\).md) pour spécifier l'assembly qui contient le type.  En C\+\+, utilisez la directive [\#using](../Topic/%23using%20Directive%20\(C++\).md) dans le fichier source pour spécifier l'assembly qui contient le type.  
  
## Voir aussi  
 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>   
 [Type Forwarding \(C\+\+\/CLI\)](../Topic/Type%20Forwarding%20\(C++-CLI\).md)   
 [\#using, directive](../Topic/%23using%20Directive%20\(C++\).md)