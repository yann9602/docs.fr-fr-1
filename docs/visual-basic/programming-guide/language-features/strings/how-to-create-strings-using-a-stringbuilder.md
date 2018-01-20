---
title: "Comment : créer des chaînes à l'aide de StringBuilder en Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9def5da754d9075a8b498ac80e624caae5c97b96
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a>Comment : créer des chaînes à l'aide de StringBuilder en Visual Basic
Cet exemple construit une longue chaîne à partir de plusieurs chaînes plus petites à l’aide de la <xref:System.Text.StringBuilder> classe. Le <xref:System.Text.StringBuilder> classe est plus efficace que la `&=` opérateur pour concaténer plusieurs chaînes.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée une instance de la <xref:System.Text.StringBuilder> (classe), ajoute 1 000 chaînes à cette instance, puis retourne sa représentation sous forme de chaîne.  
  
 [!code-vb[VbVbalrStrings#70](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-strings-using-a-stringbuilder_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de la classe StringBuilder](../../../../standard/base-types/stringbuilder.md)  
 [&= (opérateur)](../../../../visual-basic/language-reference/operators/and-assignment-operator.md)  
 [Chaînes](../../../../visual-basic/programming-guide/language-features/strings/index.md)  
 [Création de chaînes](../../../../standard/base-types/creating-new.md)  
 [Manipulation de chaînes](../../../../standard/base-types/manipulating-strings.md)  
 [Exemples de chaînes](http://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02)
