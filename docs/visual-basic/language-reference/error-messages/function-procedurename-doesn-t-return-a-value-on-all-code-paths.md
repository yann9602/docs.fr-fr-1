---
title: "Function &#39;&lt;procedurename&gt;&#39; doesn&#39;t return a value on all code paths | Microsoft Docs"
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
  - "bc42105"
  - "vbc42105"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC42105"
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Function &#39;&lt;procedurename&gt;&#39; doesn&#39;t return a value on all code paths
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

La fonction '\<NomProcédure\>' ne retourne pas une valeur pour tous les chemins de code.Une instruction 'Return' est\-elle manquante ?  
  
 Une procédure `Function` peut au moins avoir un chemin d'accès par le biais de son code qui ne retourne pas de valeur.  
  
 Vous pouvez retourner une valeur d'une procédure `Function` en utilisant l'une des méthodes suivantes :  
  
-   inclure la valeur dans une instruction Return \([Return Statement](../../../visual-basic/language-reference/statements/return-statement.md)\) ;  
  
-   assigner la valeur au nom de la procédure `Function`, puis exécuter une instruction `Exit Function` ;  
  
-   assigner la valeur au nom de la procédure `Function`, puis exécuter l'instruction `End Function` ;  
  
 Si le contrôle passe à `Exit Function` ou à `End Function` et que vous n'avez assigné aucune valeur au nom de la procédure, la procédure retourne la valeur par défaut du type de données retournées.  Pour plus d'informations, consultez « Behavior » dans [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).  
  
 Par défaut, ce message est un avertissement.  Pour plus d'informations sur le masquage des avertissements ou le traitement des avertissements en tant qu'erreurs, consultez [Configuration d'avertissements en Visual Basic](/visual-studio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d'erreur :** BC42105  
  
### Pour corriger cette erreur  
  
-   Vérifiez la logique de flux de votre contrôle et assurez\-vous que vous assignez une valeur avant chaque instruction qui provoque un retour.  
  
     Il est plus facile de garantir que chaque retour de la procédure retourne une valeur si vous utilisez toujours l'instruction `Return`.  Si vous le faites, la dernière instruction avant `End Function` doit être une instruction `Return`.  
  
## Voir aussi  
 [Function, procédures](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Page Compiler, Concepteur de projets \(Visual Basic\)](/visual-studio/ide/reference/compile-page-project-designer-visual-basic)