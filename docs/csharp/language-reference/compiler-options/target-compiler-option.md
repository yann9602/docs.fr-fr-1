---
title: "/target (C# Compiler Options) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/target"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "target compiler options [C#]"
  - "/target compiler options [C#]"
  - "assemblies [C#], compiling"
  - "-target compiler options [C#]"
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
caps.latest.revision: 22
caps.handback.revision: 22
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /target (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

L'option du compilateur **\/target** peut être spécifiée selon l'une des quatre formes suivantes :  
  
 [\/target:appcontainerexe](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md)  
 Pour créer un fichier .exe pour les applications [!INCLUDE[win8_appname_long](../../../csharp/includes/win8_appname_long_md.md)].  
  
 [\/target:exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md)  
 Pour créer un fichier .exe.  
  
 [\/target:library](../../../csharp/language-reference/compiler-options/target-library-compiler-option.md)  
 Pour créer une bibliothèque de code.  
  
 [\/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md)  
 Pour créer un module.  
  
 [\/target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)  
 Pour créer un programme Windows.  
  
 [\/target:winmdobj](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md)  
 Pour créer un fichier de l'intermédiaire .winmdobj.  
  
 Avec l'option **\/target**, un manifeste d'assembly .NET Framework est placé dans un fichier de sortie, sauf si vous spécifiez **\/target:module**.  Pour plus d'informations, consultez [Assemblys dans le Common Language Runtime](../Topic/Assemblies%20in%20the%20Common%20Language%20Runtime.md) et [Attributs communs](../Topic/Common%20Attributes%20\(C%23%20and%20Visual%20Basic\).md).  
  
 Le manifeste d'assembly est placé dans le premier fichier de sortie .exe dans la compilation ou dans le premier fichier DLL, s'il n'existe aucun fichier de sortie .exe.  Par exemple, dans la ligne de commande suivante, le manifeste sera placé dans `1.exe` :  
  
```  
csc /out:1.exe t1.cs /out:2.netmodule t2.cs  
```  
  
 Le compilateur ne crée qu'un seul manifeste d'assembly par compilation.  Le manifeste d'assembly contient les informations sur tous les fichiers d'une compilation.  Tous les fichiers de sortie sauf ceux qui sont créés avec **\/target:module** peuvent contenir un manifeste d'assembly.  Lors de la production de plusieurs fichiers de sortie sur la ligne de commande, un seul manifeste d'assembly peut être créé, et il doit aller dans le premier fichier de sortie spécifié sur la ligne de commande.  Peu importe la nature du premier fichier de sortie \(**\/target:exe**, **\/target:winexe**, **\/target:library** ou **\/target:module**\), tous les autres fichiers de sortie générés au cours de la même compilation doivent être des modules \(**\/target:module**\).  
  
 Pour la création d'un assembly, vous pouvez indiquer que tout ou partie de votre code est conforme à CLS avec l'attribut <xref:System.CLSCompliantAttribute>.  
  
```  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 Pour plus d'informations sur la configuration de cette option du compilateur par programme, consultez <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## Voir aussi  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Comment : modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/fr-fr/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [\/subsystemversion \(Specify minimum subsystem version\)](../../../csharp/language-reference/compiler-options/subsystemversion-compiler-option.md)