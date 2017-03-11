---
title: "/target:module (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/target:module"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "-target compiler options [C#], /target:module"
  - "target compiler options [C#], /target:module"
  - "/target compiler options [C#], /target:module"
ms.assetid: 9af1e4fa-c749-44e7-ae58-90a3d05d4e72
caps.latest.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 11
---
# /target:module (C# Compiler Options)
Cette option empêche le compilateur de générer un manifeste d'assembly.  
  
## Syntaxe  
  
```  
/target:module  
```  
  
## Notes  
 Par défaut, le fichier de sortie \(créé via la compilation avec cette option\) porte l'extension .netmodule.  
  
 Un fichier dépourvu d'un manifeste d'assembly ne peut pas être chargé par le Common Language Runtime du .NET Framework.  Cependant, un tel fichier peut être incorporé dans le manifeste d'un assembly au moyen de [\/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).  
  
 Si plusieurs modules sont créés dans une seule compilation, les types [internal](../../../csharp/language-reference/keywords/internal.md) d'un module unique seront accessibles aux autres modules dans la compilation.  Lorsque le code d'un module référence des types `internal` dans un autre module, les deux modules doivent être incorporés dans un manifeste d'assembly au moyen de **\/addmodule**.  
  
 La création d'un module n'est pas prise en charge dans l'environnement de développement Visual Studio.  
  
 Pour plus d'informations sur la définition de cette option du compilateur par programme, consultez <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## Exemple  
 Compilez `in.cs` et créez le fichier `in.netmodule` :  
  
```  
csc /target:module in.cs  
```  
  
## Voir aussi  
 [\/target \(Specify Output File Format\)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)   
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)