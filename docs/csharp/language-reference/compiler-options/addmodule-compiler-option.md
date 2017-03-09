---
title: "/addmodule (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/addmodule"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/addmodule compiler option [C#]"
  - "-addmodule compiler option [C#]"
  - "addmodule compiler option [C#]"
ms.assetid: ed604546-0dc2-4bd4-9a3e-610a8d973e58
caps.latest.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 13
---
# /addmodule (C# Compiler Options)
Cette option ajoute un module créé avec le commutateur target:module à la compilation actuelle.  
  
## Syntaxe  
  
```  
/addmodule:file[;file2]  
```  
  
## Arguments  
 `file`, `file2`  
 est le fichier de sortie qui contient des métadonnées.  Le fichier ne peut pas contenir un manifeste d'assembly.  Pour importer plusieurs fichiers, séparez les noms de fichiers par une virgule ou un point\-virgule.  
  
## Notes  
 Tous les modules ajoutés par **\/addmodule** doivent se trouver dans le même répertoire que le fichier de sortie au moment de l'exécution.  Vous pouvez donc spécifier un module dans n'importe quel répertoire au moment de la compilation, mais le module doit se trouver dans le répertoire de l'application au moment de l'exécution.  Si le module n'est pas dans le répertoire de l'application au moment de l'exécution, vous obtiendrez <xref:System.TypeLoadException>.  
  
 `file` ne peut pas contenir un assembly.  Si par exemple le fichier de sortie a été créé avec [\/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), ses métadonnées peuvent être importées avec **\/addmodule**.  
  
 Si le fichier de sortie a été créé avec une option **\/target** autre que **\/target:module**, ses métadonnées ne peuvent pas être importées avec **\/addmodule**, mais peuvent l'être avec [\/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md).  
  
 Cette option du compilateur n'est pas disponible dans Visual Studio ; un projet ne peut pas référencer un module.  Par ailleurs, cette option du compilateur ne peut pas être modifiée par programme.  
  
## Exemple  
 Compilez le fichier source `input.cs` et ajoutez les métadonnées de `metad1.netmodule` et `metad2.netmodule` pour produire `out.exe` :  
  
```  
csc /addmodule:metad1.netmodule;metad2.netmodule /out:out.exe input.cs  
```  
  
## Voir aussi  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Comment : modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/fr-fr/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [Assemblys multifichiers](../Topic/Multifile%20Assemblies.md)   
 [Comment : générer un assembly multifichier](../Topic/How%20to:%20Build%20a%20Multifile%20Assembly.md)