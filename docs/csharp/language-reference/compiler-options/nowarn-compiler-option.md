---
title: "/nowarn (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/nowarn"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "nowarn compiler option [C#]"
  - "/nowarn compiler option [C#]"
  - "-nowarn compiler option [C#]"
ms.assetid: 6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4
caps.latest.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 24
---
# /nowarn (C# Compiler Options)
L'option **\/nowarn** permet d'empêcher le compilateur d'afficher un ou plusieurs avertissements.  Séparez les numéros des avertissements par une virgule.  
  
## Syntaxe  
  
```  
/nowarn:number1[,number2,...]  
```  
  
## Arguments  
 `number1`, `number2`  
 Numéro de l'avertissement que le compilateur doit supprimer.  
  
## Notes  
 Il suffit de spécifier la partie numérique de l'identificateur de l'avertissement.  Par exemple, pour supprimer CS0028, spécifiez `/nowarn:28`.  
  
 Le compilateur ignorera en mode silencieux les numéros des avertissements passés à l'option `/nowarn` qui étaient valides dans les versions antérieures, mais qui ont été supprimées du compilateur.  Par exemple, CS0679 était valide dans le compilateur de Visual Studio .NET 2002, mais a été supprimé ultérieurement.  
  
 Les avertissements suivants ne peuvent pas être supprimés par l'option `/nowarn` :  
  
-   Compilateur Warning \(level 1\) CS2002  
  
-   \(Niveau 1\) Avertissement du compilateur CS2023  
  
-   Compilateur Warning \(level 1\) CS2029  
  
### Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la page **Propriétés** du projet.  Pour plus d'informations, consultez [Générer, page du Concepteur de projets \(C\#\)](/visual-studio/ide/reference/build-page-project-designer-csharp).  
  
2.  Cliquez sur la page de propriétés **Générer**.  
  
3.  Modifiez la propriété **Supprimer les avertissements**.  
  
 Pour plus d'informations sur la définition de cette option du compilateur par programme, consultez <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.  
  
## Voir aussi  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Comment : modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/fr-fr/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [C\# Compiler Errors](../../../csharp/language-reference/compiler-messages/index.md)