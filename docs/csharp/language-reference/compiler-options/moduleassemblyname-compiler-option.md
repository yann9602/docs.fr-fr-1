---
title: "/moduleassemblyname (C# Compiler Option) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/moduleassemblyname"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "moduleassemblyname compiler option [C#]"
  - "/moduleassemblyname compiler option [C#]"
  - ".moduleassemblyname compiler option [C#]"
ms.assetid: d464d9b9-f18d-423b-95e9-66c7878fd53a
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /moduleassemblyname (C# Compiler Option)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Spécifie un assembly dont les types non publics peuvent être accédés par un .netmodule.  
  
## Syntaxe  
  
```  
/moduleassemblyname:assembly_name  
```  
  
## Arguments  
 `assembly_name`  
 Le nom de l'assembly dont les types publics le .netmodule peut accéder.  
  
## Notes  
 **\/moduleassemblyname** doit être utilisé lors de la création d'un .netmodule, ainsi que les conditions suivantes sont remplies :  
  
-   Le .netmodule doit accéder aux types non publics d'un assembly existant.  
  
-   Vous connaissez le nom de l'assembly sur lequel le .netmodule est généré.  
  
-   L'assembly référencé existante a accordé l'accès d'assembly ami à l'assembly dans lequel le .netmodule sera généré.  
  
 Pour plus d'informations sur la construction d'un .netmodule, consultez [\/target:module \(Create Module to Add to Assembly\)](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md).  
  
 Pour plus d'informations sur les assemblys friend, consultez [Assemblys friend](../Topic/Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md).  
  
 Cette option n'est pas accessible à partir de l'environnement de développement Visual Studio. Elle est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
 Cette option du compilateur n'est pas disponible dans Visual Studio et ne peut pas être modifiée par programme.  
  
## Exemple  
 Cet exemple génère un assembly avec un type privé, et cela donne l'accès d'assembly friend à un assembly appelé csman\_an\_assembly.  
  
```  
// moduleassemblyname_1.cs  
// compile with: /target:library  
using System;  
using System.Runtime.CompilerServices;  
  
[assembly:InternalsVisibleTo ("csman_an_assembly")]  
  
class An_Internal_Class   
{  
    public void Test()   
    {   
        Console.WriteLine("An_Internal_Class.Test called");   
    }  
}  
```  
  
## Exemple  
 Cet echantillon construit un .netmodule qui accède à un type non public dans l'assembly moduleassemblyname\_1.dll.  En sachant que ce .netmodule est généré dans un assembly nommé csman\_an\_assembly, on peut spécifier **\/moduleassemblyname**, ce qui permet au .netmodule l'accès public dans un assembly qui a accordé l'accès amical à l'assembly csman\_an\_assembly.  
  
```  
// moduleassemblyname_2.cs  
// compile with: /moduleassemblyname:csman_an_assembly /target:module /reference:moduleassemblyname_1.dll  
class B {  
    public void Test() {  
        An_Internal_Class x = new An_Internal_Class();  
        x.Test();  
    }  
}  
```  
  
## Exemple  
 Cet exemple de code génère le csman\_an\_assembly d'assembly, en référençant l'assembly généré précédemment et .netmodule.  
  
```  
// csman_an_assembly.cs  
// compile with: /addmodule:moduleassemblyname_2.netmodule /reference:moduleassemblyname_1.dll  
class A {  
    public static void Main() {  
        B bb = new B();  
        bb.Test();  
    }  
}  
```  
  
  **An\_Internal\_Class.Test appelé**   
## Voir aussi  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Comment : modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/fr-fr/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)