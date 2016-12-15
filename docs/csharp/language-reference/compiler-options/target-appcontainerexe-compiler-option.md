---
title: "/target:appcontainerexe (Options du compilateur&#160;C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /target:appcontainerexe (Options du compilateur&#160;C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Si vous utilisez l'option du compilateur **\/target:appcontainerexe**, le compilateur crée un fichier exécutable Windows \(.exe\) qui doit être exécuté dans un conteneur d'application.  Cette option équivaut à [\/target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md), mais elle est destinée aux applications [!INCLUDE[win8_appname_long](../../../csharp/includes/win8_appname_long_md.md)].  
  
## Syntaxe  
  
```  
/target:appcontainerexe  
```  
  
## Notes  
 Pour exiger que l'application s'exécute dans un conteneur d'application, cette option définit un bit dans le fichier [Portable Executable](http://go.microsoft.com/fwlink/p/?LinkId=236960) \(PE\).  Lorsque ce bit est défini, une erreur se produit si la méthode CreateProcess tente de lancer l'exécutable en dehors d'un conteneur d'application.  
  
 À moins que vous n'utilisiez l'option [\/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md), le nom du fichier de sortie prend le nom du fichier d'entrée qui contient la méthode [Main](../../../csharp/programming-guide/main-and-command-args/main-and-command-line-arguments.md).  
  
 Lorsque vous spécifiez cette option à une invite de commandes, tous les fichiers jusqu'à l'option **\/out** ou  **\/target** suivante sont utilisés pour créer le fichier exécutable.  
  
### Pour définir cette option du compilateur dans l'IDE  
  
1.  Dans l'**Explorateur de solutions**, ouvrez le menu contextuel de votre projet et choisissez **Propriétés**.  
  
2.  Sous l'onglet **Application**, dans la liste **Type de sortie**, choisissez **Application Windows Store**.  
  
     Cette option est disponible uniquement pour les modèles d'applications [!INCLUDE[win8_appname_long](../../../csharp/includes/win8_appname_long_md.md)].  
  
 Pour plus d'informations sur la façon de définir cette option du compilateur par programme, consultez <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## Exemple  
 La commande suivante compile `filename.cs` dans un fichier exécutable Windows qui peut être exécuté uniquement dans un conteneur d'application.  
  
```  
csc /target:appcontainerexe filename.cs  
```  
  
## Voir aussi  
 [\/target \(Specify Output File Format\)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)   
 [\/target:winexe \(Create a Windows Program\)](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)   
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)