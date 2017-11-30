---
title: "Les littéraux XML et les propriétés XML ne sont pas pris en charge dans du code incorporé au sein d'ASP.NET"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31200
- bc31200
helpviewer_keywords: BC31200
ms.assetid: 053e8cba-8584-45cc-9fa0-43d122779772
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 932c36778720718d777412f958c16b4a650e3b5b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="xml-literals-and-xml-properties-are-not-supported-in-embedded-code-within-aspnet"></a>Les littéraux XML et les propriétés XML ne sont pas pris en charge dans du code incorporé au sein d'ASP.NET
Littéraux XML et les propriétés XML ne sont pas prises en charge du code incorporé au sein d’ASP.NET. Pour utiliser les fonctionnalités XML, déplacez le code pour le code-behind.  
  
 Un littéral XML ou une propriété d’axe XML est définie dans le code incorporé (`<%= =>`) dans un fichier ASP.NET.  
  
 **ID d’erreur :** BC31200  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Déplacez le code qui inclut le littéral XML ou une propriété d’axe XML dans un fichier de code-behind ASP.NET.  
  
## <a name="see-also"></a>Voir aussi  
 [Littéraux XML](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Propriétés d’axe XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)
