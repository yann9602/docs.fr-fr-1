---
title: "An unexpected error has occurred because an operating system resource required for single instance startup cannot be acquired | Microsoft Docs"
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
  - "vbrAppModel_CantGetMemoryMappedFile"
dev_langs: 
  - "VB"
ms.assetid: 0d9f2a30-ff72-4355-8060-744f22339359
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# An unexpected error has occurred because an operating system resource required for single instance startup cannot be acquired
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

L'application n'a pas pu obtenir une ressource nécessaire du système d'exploitation. Ce problème peut avoir certaines des causes suivantes :  
  
-   L'application n'est pas autorisée à créer des objets de système d'exploitation nommés.  
  
-   Le Common Language Runtime n'est pas autorisé à créer des fichiers mappés sur la mémoire.  
  
-   L'application doit accéder à un objet de système d'exploitation, mais un autre processus l'utilise.  
  
### Pour corriger cette erreur  
  
1.  Vérifiez que l'application dispose d'autorisations suffisantes pour créer des objets de système d'exploitation nommés.  
  
2.  Veillez à ce que le Common Language Runtime dispose d'autorisations suffisantes pour créer des fichiers mappés sur la mémoire.  
  
3.  Redémarrez l'ordinateur pour annuler tout processus susceptible d'utiliser la ressource permettant de se connecter à l'application de l'instance d'origine.  
  
4.  Notez les circonstances dans lesquelles l'erreur s'est produite, puis contactez les services de support technique Microsoft  
  
## Voir aussi  
 [Page Application, Concepteur de projets \(Visual Basic\)](/visual-studio/ide/reference/application-page-project-designer-visual-basic)   
 [Principes de base du débogueur](/visual-studio/debugger/debugger-basics)   
 [Nous contacter](/visual-studio/ide/talk-to-us)