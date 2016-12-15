---
title: "/main (C# Compiler Options) | Microsoft Docs"
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
  - "/main"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "-main compiler option [C#]"
  - "main compiler option [C#]"
  - "/main compiler option [C#]"
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /main (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Cette option spécifie la classe qui contient le point d'entrée au programme, si plusieurs classes contiennent une méthode **Main**.  
  
## Syntaxe  
  
```  
/main:class  
```  
  
## Arguments  
 `class`  
 Le type qui contient la méthode **Main**.  
  
## Notes  
 Si votre compilation comprend plusieurs types avec une méthode [Main](../../../csharp/programming-guide/main-and-command-args/main-and-command-line-arguments.md), vous pouvez spécifier le type contenant la méthode **Main** devant être utilisé comme point d'entrée dans le programme.  
  
 Cette option est valide lors de la compilation d'un fichier .exe.  
  
### Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la page **Propriétés** du projet.  
  
2.  Cliquez sur la page de propriétés **Application**.  
  
3.  Modifiez la propriété **Objet de démarrage**.  
  
     Pour définir cette option du compilateur par programme, consultez <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>  
  
## Exemple  
 Compilez `t2.cs` et `t3.cs`, en spécifiant que la méthode **Main** se trouve dans `Test2` :  
  
```  
csc t2.cs t3.cs /main:Test2  
```  
  
## Voir aussi  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Comment : modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/fr-fr/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)