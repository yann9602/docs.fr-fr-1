---
title: "Comment : utiliser le bloc Try-Catch pour intercepter des Exceptions"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, try/catch blocks
- try blocks
- try/catch blocks
- catch blocks
ms.assetid: a3ce6dfd-1f64-471b-8ad8-8cfaf406275d
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5a72a21085c37bed4d84518810f69a013d515189
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2017
---
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a>Guide pratique pour utiliser le bloc try/catch pour intercepter des exceptions

Placez les sections de code qui peuvent lever des exceptions dans un bloc `try` et placez le code qui gère les exceptions dans un bloc `catch`. Le bloc `catch` est une série d’instructions qui commencent par le mot clé `catch`, suivi d’un type d’exception et d’une action à effectuer.

L’exemple de code suivant utilise un bloc `try`/`catch` pour intercepter une exception possible. La méthode `Main` contient un bloc `try` avec une instruction <xref:System.IO.StreamReader> qui ouvre un fichier de données appelé `data.txt` et écrit une chaîne à partir du fichier. À la suite du bloc `try`, un bloc `catch` intercepte toute exception qui résulte du bloc `try`.

 [!code-cpp[CatchException#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception2.cpp#3)]
 [!code-csharp[CatchException#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
 [!code-vb[CatchException#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]  

Le Common Language Runtime intercepte les exceptions qui ne sont pas interceptées par un bloc catch. Selon la configuration du runtime, une boîte de dialogue de débogage s’affiche, le programme s’arrête et une boîte de dialogue s’affiche avec des informations sur l’exception, ou une erreur est imprimée dans STDERR.

> [!NOTE] 
> Presque toutes les lignes de code peuvent provoquer une exception, en particulier les exceptions levées par le Common Language Runtime lui-même, comme <xref:System.OutOfMemoryException>. La plupart des applications n’ont pas à traiter ces exceptions, mais vous devez être conscient de cette possibilité quand vous écrivez des bibliothèques destinées à d’autres utilisateurs. Afin d’obtenir des suggestions pour savoir quand définir du code dans un bloc Try, consultez les [Bonnes pratiques pour les exceptions](best-practices-for-exceptions.md).

## <a name="see-also"></a>Voir aussi  
[Exceptions](index.md)
