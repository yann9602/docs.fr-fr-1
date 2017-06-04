---
title: "Lambda Expressions in PLINQ and TPL | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Func delegate, creating with lambda expression"
  - "Action delegate, creating with lambda expression"
  - "lambda expressions, with Action and Func"
ms.assetid: 645b2c17-29d0-4ffa-8684-430743cc2f2d
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# Lambda Expressions in PLINQ and TPL
La bibliothèque parallèle de tâches contient de nombreuses méthodes qui prennent l'une des familles de délégués <xref:System.Func%601?displayProperty=fullName> ou <xref:System.Action?displayProperty=fullName> comme paramètres d'entrée.  Vous utilisez ces délégués pour passer votre logique de programme personnalisée à la boucle, tâche ou requête parallèle.  Les exemples de code de TPL et PLINQ utilisent des expressions lambda pour créer des instances de ces délégués sous forme de blocs de code incorporé.  Cette rubrique fournit une brève introduction à Func et Action et vous montre comment utiliser des expressions lambda dans la bibliothèque parallèle de tâches et PLINQ.  
  
 **Remarque** Pour plus d'informations sur les délégués en général, consultez [Délégués](../Topic/Delegates%20\(C%23%20Programming%20Guide\).md) et [Delegates](../Topic/Delegates%20\(Visual%20Basic\).md).  Pour plus d'informations sur les expressions lambda en C\# et [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)], consultez [Expressions lambda](../Topic/Lambda%20Expressions%20\(C%23%20Programming%20Guide\).md) et [Lambda Expressions](../Topic/Lambda%20Expressions%20\(Visual%20Basic\).md).  
  
## Délégué Func  
 Un délégué `Func` encapsule une méthode qui retourne une valeur.  Dans une signature Func, le dernier ou le plus à droite des paramètres de type spécifie toujours le type de retour.  Une cause fréquente entraînant des erreurs du compilateur est la tentative de passer deux paramètres d'entrée au type <xref:System.Func%602?displayProperty=fullName> ; en fait ce type prend en charge un seul paramètre d'entrée.  La bibliothèque de classes .NET Framework définit 17 versions de `Func` : <xref:System.Func%601?displayProperty=fullName>, <xref:System.Func%602?displayProperty=fullName>, <xref:System.Func%603?displayProperty=fullName> et ainsi de suite, jusqu'à <xref:System.Func%6017?displayProperty=fullName>.  
  
## Délégué Action  
 Un délégué <xref:System.Action?displayProperty=fullName> encapsule une méthode \(Sub en [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]\) qui ne retourne pas de valeur ou retourne [void](../Topic/void%20\(C%23%20Reference\).md).  Dans une signature de type Action, les paramètres de type représentent uniquement des paramètres d'entrée.  Comme pour Func, la bibliothèque de classes .NET Framework définit 17 versions d'Action, d'une version sans paramètre de type jusqu'à une version avec 16 paramètres de type.  
  
## Exemple  
 L'exemple suivant de la méthode <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=fullName> indique comment exprimer les délégués Func et Action à l'aide d'expressions lambda.  
  
 [!code-csharp[System.Threading.Tasks.Parallel#02](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.parallel/cs/parallelforeach.cs#02)]
 [!code-vb[System.Threading.Tasks.Parallel#02](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.parallel/vb/parallelforeach.vb#02)]  
  
## Voir aussi  
 [Parallel Programming](../../../docs/standard/parallel-programming/index.md)