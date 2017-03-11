---
title: "/nowin32manifest (Visual Basic) | Microsoft Docs"
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
  - "/nowin32manifest compiler option [Visual Basic]"
  - "nowin32manifest compiler option [Visual Basic]"
  - "-nowin32manifest compiler option [Visual Basic]"
ms.assetid: c0528aae-83b3-4425-99f0-19448e9843e3
caps.latest.revision: 7
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 7
---
# /nowin32manifest (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Ordonne au compilateur pour ne pas incorporer de manifeste de l'application dans le fichier exécutable.  
  
## Syntaxe  
  
```  
/nowin32manifest  
```  
  
## Notes  
 Lorsque cette option est utilisée, l'application est sujette à virtualisation dans Windows Vista, sauf si vous fournissez un manifeste d'application dans un fichier de ressources Win32 ou au cours d'une étape de génération ultérieure.  Pour plus d'informations sur la virtualisation, consultez [ClickOnce Deployment on Windows Vista](/visual-studio/deployment/clickonce-deployment-on-windows-vista).  
  
 Pour plus d'informations sur la création de manifestes, consultez [\/win32manifest](../../../visual-basic/reference/command-line-compiler/win32manifest.md).  
  
## Voir aussi  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Page Application, Concepteur de projets \(Visual Basic\)](/visual-studio/ide/reference/application-page-project-designer-visual-basic)