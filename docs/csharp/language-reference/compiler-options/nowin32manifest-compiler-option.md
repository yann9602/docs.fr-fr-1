---
title: "/nowin32manifest (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/nowin32manifest"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "nowin32manifest compiler option [C#]"
  - "-nowin32manifest compiler option [C#]"
  - "/nowin32manifest compiler option [C#]"
ms.assetid: 6f06365b-b87b-46a2-b187-b3bfeaf4862d
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 13
---
# /nowin32manifest (C# Compiler Options)
Utilisez l'option **\/nowin32manifest** pour indiquer au compilateur de ne pas inclure de manifeste d'application dans le fichier exécutable.  
  
## Syntaxe  
  
```  
/nowin32manifest  
```  
  
## Notes  
 Lorsque cette option est utilisée, l'application est sujette à virtualisation dans Windows Vista, sauf si vous fournissez un manifeste d'application dans un fichier de ressources Win32 ou au cours d'une étape de génération ultérieure.  Pour plus d'informations sur la virtualisation, consultez [New UAC Technologies for Windows Vista](http://msdn.microsoft.com/fr-fr/80efa4c7-3904-45c5-82e8-2d558fe67db9).  
  
 Dans Visual Studio, définissez cette option sur la page de **propriétés Application** en sélectionnant l'option **Créer une application sans fichier manifeste** dans la liste déroulante **Manifeste**.  Pour plus d'informations, consultez [Page Application, Concepteur de projets \(C\#\)](/visual-studio/ide/reference/application-page-project-designer-csharp).  
  
 Pour plus d'informations sur la création de manifestes, consultez [\/win32manifest \(Import a Custom Win32 Manifest File\)](../../../csharp/language-reference/compiler-options/win32manifest-compiler-option.md).  
  
## Voir aussi  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Comment : modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/fr-fr/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)