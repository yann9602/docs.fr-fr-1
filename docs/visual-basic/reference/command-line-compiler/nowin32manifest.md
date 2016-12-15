---
title: "/nowin32manifest (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "/nowin32manifest compiler option [Visual Basic]"
  - "nowin32manifest compiler option [Visual Basic]"
  - "-nowin32manifest compiler option [Visual Basic]"
ms.assetid: c0528aae-83b3-4425-99f0-19448e9843e3
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /nowin32manifest (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

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