---
title: "A startup form has not been specified | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrAppModel_NoStartupForm"
dev_langs: 
  - "VB"
ms.assetid: 8e04af49-4bef-49de-a7ec-e407e9873da7
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# A startup form has not been specified
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

L'application utilise la classe <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>, mais ne spécifie pas le formulaire de démarrage.  
  
 Cela peut se produire si la case à cocher **Activer l'infrastructure de l'application** est activée dans le concepteur de projets, mais que le **Formulaire de démarrage** n'a pas été spécifié.  Pour plus d'informations, consultez [Page Application, Concepteur de projets \(Visual Basic\)](/visual-studio/ide/reference/application-page-project-designer-visual-basic).  
  
### Pour corriger cette erreur  
  
1.  Spécifiez un objet de démarrage pour l'application.  
  
     Pour plus d'informations, consultez [Page Application, Concepteur de projets \(Visual Basic\)](/visual-studio/ide/reference/application-page-project-designer-visual-basic).  
  
2.  Substituez la méthode <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> pour affecter le formulaire de démarrage à la propriété <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A>.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A>   
 [Overview of the Visual Basic Application Model](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)