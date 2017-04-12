---
title: "Nothing et les chaînes en Visual Basic | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 56fc47ba2523825224aae3264e965d462cf4c3b6
ms.lasthandoff: 03/13/2017

---
# <a name="nothing-and-strings-in-visual-basic"></a>Nothing et les chaînes en Visual Basic
Le [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] runtime et le [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] évaluer `Nothing` différemment lorsqu’il s’agit de chaînes.  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a>Runtime Visual Basic et le .NET Framework  
 Prenons l'exemple suivant :  
  
 [!code-vb[VbVbalrStrings&#47;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/nothing-and-strings_1.vb)]  
  
 Le [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] runtime prend généralement la valeur `Nothing` comme une chaîne vide (« »). Le [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] ne supprime pas, toutefois et lève une exception lorsqu’une tentative est faite pour effectuer une opération de chaîne sur `Nothing`.  
  
## <a name="see-also"></a>Voir aussi  
 [Introduction aux chaînes en Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
