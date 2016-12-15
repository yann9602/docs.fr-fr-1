---
title: "Error Messages (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "errors [Visual Basic]"
  - "error messages"
  - "trappable errors"
  - "errors [Visual Basic], trappable"
ms.assetid: f2dda05b-baef-41f5-8bb1-598bd7cf239f
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Error Messages (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Lorsque vous entrez, compilez, ou exécutez une application Visual Basic, les types suivants d'erreurs peuvent se produire :  
  
1.  Erreurs au moment de le design, qui se produisent lorsque vous écrivez une application dans Visual Studio.  
  
2.  Erreurs de compilation, qui se produisent lorsque vous compilez une application dans Visual Studio ou une invite de commandes.  
  
3.  Erreurs d'exécution, qui se produisent lorsque vous exécutez une application dans Visual Studio ou en tant que fichier exécutable autonome.  
  
 Pour plus d'informations sur la résolution d'une erreur spécifique, consultez l' [Additional Resources for Visual Basic Programmers](../../../visual-basic/getting-started/additional-resources.md).  
  
## Erreurs d'exécution  
 Si les tests d'une application Visual Basic pour effectuer une action que le système ne peut pas exécuter, une erreur d'exécution se produit, et à celle\-ci lève d' [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] un objet d' `Exception` .  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] peut générer des erreurs personnalisées de n'importe quel type de données, parmi lesquels des objets `Exception`, en utilisant l'instruction `Throw`.  Une application peut identifier l'erreur en affichant le numéro et le message d'une exception interceptée.  Si une erreur n'est pas interceptée, l'application se termine.  
  
 Le code peut intercepter et examiner des erreurs d'exécution.  Si vous joignez le code qui génère l'erreur dans un bloc d' `Try` , vous pouvez intercepter toute erreur levée dans un bloc correspondant d' `Catch` .  Pour plus d'informations sur l'interception des erreurs au moment de l'exécution et répondre à elles dans votre code, consultez [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## Erreurs au moment de la compilation  
 Si le compilateur Visual Basic rencontre un problème dans le code, une erreur de compilation se produit.  Dans l'éditeur de code, vous pouvez facilement identifier la ligne de code a provoqué l'erreur car une ligne ondulée apparaît sous cette ligne de code.  Le message d'erreur apparaît si vous indiquez la ligne ondulée ou ouvrez **Liste d'erreurs**, qui indique également d'autres messages.  
  
 Si un identificateur a une ligne ondulée et un trait de soulignement court apparaît sous le caractère le plus à droite, vous pouvez générer un stub pour la classe, le constructeur, une méthode, une propriété, un champ ou l'enum.  Pour plus d'informations, consultez [Générer à partir de l'utilisation](/visual-cpp/misc/generate-from-usage).  
  
 Lors de la résolution des avertissements du compilateur Visual Basic, vous pouvez être en mesure d'écrire le code qui s'exécute plus rapidement et a moins de bogues.  Ces avertissements identifient le code qui peut provoquer des erreurs lorsque l'application est exécutée.  Par exemple, le compilateur vous avertit si vous essayez d'appeler un membre d'une variable objet non assignée, de retour d'une fonction sans définir la valeur de retour, ou d'exécuter un bloc d' `Try` avec les erreurs dans la logique pour intercepter des exceptions.  Pour plus d'informations sur les avertissements, y compris comment les activer en activer et de désactiver, consultez [Configuration d'avertissements en Visual Basic](/visual-studio/ide/configuring-warnings-in-visual-basic).