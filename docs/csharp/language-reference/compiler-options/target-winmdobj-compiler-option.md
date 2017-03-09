---
title: "/target:winmdobj (Options du compilateur&#160;C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: 1819a045-659d-498a-9457-c466e902986f
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# /target:winmdobj (Options du compilateur&#160;C#)
Si vous utilisez l'option du compilateur **\/target:winmdobj**, le compilateur crée un fichier .winmdobj intermédiaire que vous pouvez convertir en fichier binaire \(.winmd\) Windows Runtime.  Le fichier .winmd peut ensuite être consommé par des programmes JavaScript et C\+\+, en plus des programmes en langage managé.  
  
## Syntaxe  
  
```  
/target:winmdobj  
```  
  
## Notes  
 Le paramètre **winmdobj** signale au compilateur qu'un module intermédiaire est requis.  En réponse, Visual Studio compile la bibliothèque de classes C\# comme fichier .winmdobj.  Le fichier .winmdobj peut ensuite être acheminé via l'outil d'exportation <xref:Microsoft.Build.Tasks.WinMDExp> pour produire un fichier de métadonnées Windows \(.winmd\).  Le fichier .winmd contient à la fois le code de la bibliothèque d'origine et les métadonnées WinMD utilisées par JavaScript ou C\+\+ et par le Windows Runtime.  
  
 La sortie d'un fichier qui est compilé à l'aide de l'option du compilateur **\/target:winmdobj** est conçue pour être utilisée uniquement comme entrée pour l'outil d'exportation WimMDExp ; le fichier .winmdobj proprement dit n'est pas référencé directement.  
  
 À moins que vous n'utilisiez l'option [\/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md), le fichier de sortie adopte le nom du premier fichier d'entrée.  Une méthode [Main](../../../csharp/programming-guide/main-and-command-args/main-and-command-line-arguments.md) n'est pas nécessaire.  
  
 Si vous spécifiez l'option \/target:winmdobj à une invite de commandes, tous les fichiers jusqu'à l'option **\/out** ou [\/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) suivante sont utilisés pour créer le programme Windows.  
  
### Pour définir cette option du compilateur dans l'IDE de Visual Studio pour une application Windows Store  
  
1.  Dans l'**Explorateur de solutions**, ouvrez le menu contextuel de votre projet et choisissez **Propriétés**.  
  
2.  Sélectionnez l'onglet **Application**.  
  
3.  Dans la liste **Type de sortie**, choisissez **Fichier WinMD**.  
  
     L'option **Fichier WinMD** est disponible uniquement pour les modèles d'applications [!INCLUDE[win8_appname_long](../../../csharp/includes/win8-appname-long-md.md)].  
  
 Pour plus d'informations sur la façon de définir cette option du compilateur par programme, consultez <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## Exemple  
 La commande suivante compile `filename.cs` dans un fichier .winmdobj intermédiaire.  
  
```  
csc /target:winmdobj filename.cs  
```  
  
## Voir aussi  
 [\/target \(Specify Output File Format\)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)   
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)