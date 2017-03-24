---
title: "/recurse (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/recurse"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/recurse compiler option [C#]"
  - "recurse compiler option [C#]"
  - "-recurse compiler option [C#]"
ms.assetid: 4e8212e5-04e3-45b1-8a42-41bc50e683b0
caps.latest.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 12
---
# /recurse (C# Compiler Options)
L'option \/recurse permet de compiler des fichiers de code source dans tous les répertoires enfants du répertoire spécifié \(dir\) ou du répertoire du projet.  
  
## Syntaxe  
  
```  
/recurse:[dir\]file  
```  
  
## Arguments  
 `dir` \(facultatif\)  
 Répertoire dans lequel vous voulez commencer la recherche.  Si ce répertoire n'est pas spécifié, la recherche commence dans le répertoire du projet.  
  
 `file`  
 Le ou les fichiers à rechercher.  Les caractères génériques sont autorisés.  
  
## Notes  
 L'option **\/recurse** permet de compiler des fichiers de code source dans tous les répertoires enfants du répertoire spécifié \(`dir`\) ou du répertoire du projet.  
  
 Vous pouvez utiliser des caractères génériques dans un nom de fichier pour compiler tous les fichiers correspondants dans le répertoire du projet sans utiliser **\/recurse**.  
  
 Cette option du compilateur n'est pas disponible dans Visual Studio et ne peut pas être modifiée par programme.  
  
## Exemple  
 Compile tous les fichiers C\# qui se trouvent dans le répertoire actif :  
  
```  
csc *.cs  
```  
  
 Compile tous les fichiers C\# du répertoire dir1\\dir2 et de tous les sous\-répertoires qui se situent en dessous de celui\-ci, puis génère dir2.dll :  
  
```  
csc /target:library /out:dir2.dll /recurse:dir1\dir2\*.cs  
```  
  
## Voir aussi  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Comment : modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/fr-fr/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)