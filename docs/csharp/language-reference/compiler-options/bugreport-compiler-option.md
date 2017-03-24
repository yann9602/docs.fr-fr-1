---
title: "/bugreport (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/bugreport"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/bugreport compiler option [C#]"
  - "-bugreport compiler option [C#]"
  - "bugreport compiler option [C#]"
ms.assetid: f39665e3-4f6f-4357-88a2-3274c7bec0c1
caps.latest.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 20
---
# /bugreport (C# Compiler Options)
Spécifie que les informations de débogage doivent être placées dans un fichier pour analyse ultérieure.  
  
## Syntaxe  
  
```  
/bugreport:file  
```  
  
## Arguments  
 `file`  
 Le nom du fichier dans lequel vous voulez intégrer le rapport de bogue.  
  
## Notes  
 L'option **\/bugreport** spécifie que les informations suivantes doivent être placées dans `file` :  
  
-   une copie de tous les fichiers de code source dans la compilation ;  
  
-   une liste des options du compilateur utilisées dans la compilation ;  
  
-   les informations de version concernant votre compilateur, votre runtime et votre système d'exploitation ;  
  
-   les assemblys et modules référencés enregistrés en tant que chiffres hexadécimaux, sauf les assemblys qui sont fournis avec le .NET Framework et le Kit de développement logiciel \(SDK\) ;  
  
-   les résultats de la compilation, le cas échéant ;  
  
-   une description du problème, qui vous sera demandée ;  
  
-   une description de vos suggestions de résolution du problème, qui vous sera demandée.  
  
 Si cette option est utilisée avec **\/errorreport:prompt** ou **\/errorreport:send**, les informations figurant dans le fichier seront envoyées à Microsoft Corporation.  
  
 Parce qu'une copie de tous les fichiers de code source sera placée dans `file`, vous pouvez souhaiter reproduire l'erreur de code suspecte dans le programme le plus court possible.  
  
 Cette option du compilateur n'est pas disponible dans Visual Studio et ne peut pas être modifiée par programme.  
  
 Remarquez que le contenu du fichier généré expose le code source, ce qui pourrait entraîner une divulgation d'informations non voulue.  
  
## Voir aussi  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [\/errorreport \(Set Error Reporting Behavior\)](../../../csharp/language-reference/compiler-options/errorreport-compiler-option.md)   
 [Comment : modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/fr-fr/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)