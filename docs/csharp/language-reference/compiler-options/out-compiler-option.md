---
title: "/out (C# Compiler Options) | Microsoft Docs"
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
  - "/out"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/out compiler option [C#]"
  - "out compiler option [C#]"
  - "-out compiler option [C#]"
ms.assetid: 70d91d01-7bd2-4aea-ba8b-4e9807e9caa5
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /out (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

L'option **\/out** spécifie le nom du fichier de sortie.  
  
## Syntaxe  
  
```  
/out:filename  
```  
  
## Arguments  
 `filename`  
 Le nom du fichier de sortie créé par le compilateur.  
  
## Notes  
 Sur la ligne de commande, vous pouvez spécifier plusieurs fichiers de sortie pour la compilation.  Le compilateur s'attend à trouver un ou plusieurs noms de fichiers de code source à la suite de l'option **\/out**.  Tous les fichiers de code source seront alors compilés dans le fichier de sortie spécifié par cette option **\/out**.  
  
 Spécifiez le nom complet et l'extension du fichier que vous voulez créer.  
  
 Si vous ne spécifiez pas le nom du fichier de sortie :  
  
-   Un fichier .exe prendra comme nom le nom du fichier de code source contenant la méthode **Main**.  
  
-   Un .dll ou un .netmodule prendra comme nom celui du premier fichier de code source.  
  
 Un fichier de code source utilisé pour compiler un fichier de sortie ne peut pas être utilisé au cours de la même compilation pour la compilation d'un autre fichier de sortie.  
  
 Lorsque vous générez plusieurs fichiers de sortie dans une compilation de ligne de commande, gardez à l'esprit qu'un seul de ces fichiers peut être un assembly et que seul le premier fichier de sortie spécifié \(implicitement ou explicitement à l'aide de **\/out**\) peut être l'assembly.  
  
 Tous les modules obtenus dans le cadre d'une compilation deviennent des fichiers associés à un assembly quelconque également obtenu dans la compilation.  Utilisez [ildasm.exe](../Topic/Ildasm.exe%20\(IL%20Disassembler\).md) pour afficher le manifeste d'assembly et voir les fichiers associés.  
  
 L'option de compilateur \/out est requise pour qu'un exe puisse être la cible d'un assembly ami.  Pour plus d'informations, consultez [Assemblys friend](../Topic/Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md).  
  
### Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la page **Propriétés** du projet.  
  
2.  Cliquez sur la page de propriétés **Application**.  
  
3.  Modifiez la propriété **Nom de l'assembly**.  
  
     Pour définir cette option du compilateur par programme : <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> est une propriété en lecture seule qui est déterminée par une combinaison du type de projet \(exe, bibliothèque, etc.\) et du nom de l'assembly.  Vous devrez modifier l'une de ces propriétés \(ou les deux\) pour définir le nom du fichier de sortie.  
  
## Exemple  
 Compilez `t.cs` et créez le fichier de sortie `t.exe`, puis générez `t2.cs` et créez le fichier de sortie de module `mymodule.netmodule` :  
  
```  
csc t.cs /out:mymodule.netmodule /target:module t2.cs  
```  
  
## Voir aussi  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Assemblys friend](../Topic/Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)   
 [Comment : modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/fr-fr/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)