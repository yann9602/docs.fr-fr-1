---
title: "/target (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "target compiler options [Visual Basic]"
  - "-target compiler options [Visual Basic]"
  - "/target compiler options [Visual Basic]"
ms.assetid: e0954147-548b-461f-9c4b-a8f88845616c
caps.latest.revision: 29
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 29
---
# /target (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Spécifie le format de sortie du compilateur.  
  
## Syntaxe  
  
```  
/target:{exe | library | module | winexe | appcontainerexe | winmdobj}  
```  
  
## Notes  
 Le tableau suivant résume l'effet de l'option `/target`.  
  
|**Option**|**Comportement**|  
|----------------|----------------------|  
|`/target:exe`|Entraîne le compilateur à créer une application console exécutable.<br /><br /> C'est l'option par défaut lorsque vous ne spécifiez pas l'option `/target`.  Le fichier exécutable est créé avec l'extension .exe.<br /><br /> Sauf si vous spécifiez un autre nom avec l'option `/out`, le fichier de sortie prend le nom du fichier d'entrée contenant la procédure `Sub Main`.<br /><br /> Seule une procédure `Sub Main` est requise dans les fichiers du code source compilés dans un fichier  .exe.  Utilisez l'option du compilateur `/main` pour spécifier quelle classe contient la procédure `Sub Main`.|  
|`/target:library`|Provoque la création d'une bibliothèque de liens dynamiques \(DLL\) par le compilateur.<br /><br /> Le fichier bibliothèque de liens dynamiques est créé avec l'extension .dll.<br /><br /> Sauf si vous spécifiez l'option `/out`, le nom du fichier de sortie prend le nom du premier fichier d'entrée.<br /><br /> Une procédure `Sub Main` n'est pas nécessaire lors de la génération d'une DLL.|  
|`/target:module`|Entraîne le compilateur à générer un module qui peut être ajouté à un assembly.<br /><br /> Le fichier de sortie est créé avec une extension .  .netmodule.<br /><br /> Le Common Language Runtime .NET ne peut pas charger un fichier qui ne contient pas d'assembly.  Cependant, un tel fichier peut être incorporé dans le manifeste d'assembly d'un assembly en utilisant l'option `/reference`.<br /><br /> Lorsque le code d'un module référence des types internes dans un autre module, les deux modules doivent être incorporés dans un manifeste d'assembly en utilisant `/reference`.<br /><br /> L'option [\/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) importe des métadonnées à partir d'un module.|  
|`/target:winexe`|Entraîne le compilateur à créer une application Windows exécutable.<br /><br /> Le fichier exécutable est créé avec l'extension .exe.  Une application Windows exécutable est un programme qui fournit une interface utilisateur à partir de la bibliothèque de classe [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] ou avec les API Win32.<br /><br /> Sauf si vous spécifiez un autre nom avec l'option `/out`, le fichier de sortie prend le nom du fichier d'entrée contenant la procédure `Sub Main`.<br /><br /> Seule une procédure `Sub Main` est requise dans les fichiers du code source compilés dans un fichier  .exe.  Dans les cas où votre code possède plusieurs classes avec une procédure `Sub Main`, utilisez l'option du compilateur `/main` pour spécifier quelle classe contient la procédure `Sub Main`.|  
|`/target:appcontainerexe`|Pour créer le compilateur une application Windows exécutable qui doit être exécutée dans un conteneur d'application.  Cette configuration est conçue pour être utilisée pour les applications d' [!INCLUDE[win8_appname_long](../../../csharp/includes/win8-appname-long-md.md)] .<br /><br /> **appcontainerexe** définissant des ensembles d'un bit dans le domaine [Exécutable portable \(PE](http://go.microsoft.com/fwlink/p/?LinkId=236960) de fonctionnalités du fichier.  Ce bit indique que l'application doit être exécutée dans un conteneur d'application.  Lorsque ce bit est défini, une erreur se produit si les tests de méthode d' `CreateProcess` pour exécuter l'application en dehors d'un conteneur d'application.  Hormis cette configuration de bits, **\/target:appcontainerexe** équivaut à **\/target:winexe**.<br /><br /> Le fichier exécutable est créé avec l'extension .exe.<br /><br /> Sauf indication contraire à l'aide de l'option d' `/out` , le nom du fichier de sortie prend le nom du fichier d'entrée qui contient la procédure d' `Sub Main` .<br /><br /> Seule une procédure `Sub Main` est requise dans les fichiers du code source compilés dans un fichier  .exe.  Si votre code contient plusieurs classes qui a une procédure d' `Sub Main` , utilisez l'option du compilateur pour `/main` de spécifier la classe contient la procédure d' `Sub Main`|  
|`/target:winmdobj`|Pour créer le compilateur un fichier intermédiaire que vous pouvez convertir aux fenêtres un fichier \(.winmd\) binaire d'exécution.  Le fichier de .winmd peut être consommé par JavaScript et des programmes C\+\+, en plus de le langage managé programme.<br /><br /> Le fichier intermédiaire est créé avec une extension de .winmdobj.<br /><br /> Sauf indication contraire à l'aide de l'option d' `/out` , le nom du fichier de sortie prend le nom du premier fichier d'entrée.  Une procédure d' `Sub Main` n'est pas obligatoire.<br /><br /> Le fichier de .winmdobj est conçu pour être utilisé comme entrée pour l'outil d'exportation d' <xref:Microsoft.Build.Tasks.WinMDExp> produit un fichier de définition de données \(WinMD\) métadonnées windows.  Le fichier de WinMD a une extension de .winmd et contient le code de la bibliothèque d'origine et les définitions de WinMD qui JavaScript, C\+\+, et l'utilisation d'exécution windows.|  
  
 À moins de spécifier `/target:module`, `/target` fait en sorte qu'un manifeste de l'assembly du [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] soit ajouté à un fichier de sortie.  
  
 Chaque instance de Vbc.exe produit un fichier de sortie au plus.  Si vous spécifiez une option du compilateur \(par exemple, `/out` ou `/target`\) plusieurs fois, c'est la dernière option traitée par le compilateur qui est appliquée.  Le manifeste reçoit les informations sur tous les fichiers d'une compilation.  Tous les fichiers de sortie sauf ceux créés avec `/target:module` peuvent contenir des métadonnées de l'assembly dans le manifeste.  Utilisez [Ildasm.exe \(IL Disassembler\)](../Topic/Ildasm.exe%20\(IL%20Disassembler\).md) pour visualiser les métadonnées dans un fichier de sortie.  
  
 La forme abrégée de `/target` est `/t`.  
  
### Pour définir \/target dans l'IDE de Visual Studio  
  
1.  Sélectionnez un projet dans l'**Explorateur de solutions**.  Dans le menu **Projet**, cliquez sur **Propriétés**.  Pour plus d’informations, consultez [Introduction to the Project Designer](http://msdn.microsoft.com/fr-fr/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
2.  Cliquez sur l'onglet **Application**.  
  
3.  Modifiez la valeur dans la zone **Type d'application**.  
  
## Exemple  
 Le code suivant compile `in.vb`, en créant `in.dll` :  
  
```  
vbc /target:library in.vb  
```  
  
## Voir aussi  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/main](../../../visual-basic/reference/command-line-compiler/main.md)   
 [\/out](../../../visual-basic/reference/command-line-compiler/out.md)   
 [\/reference](../../../visual-basic/reference/command-line-compiler/reference.md)   
 [\/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)   
 [\/moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)   
 [Assemblys et le Global Assembly Cache](../Topic/Assemblies%20and%20the%20Global%20Assembly%20Cache%20\(C%23%20and%20Visual%20Basic\).md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)