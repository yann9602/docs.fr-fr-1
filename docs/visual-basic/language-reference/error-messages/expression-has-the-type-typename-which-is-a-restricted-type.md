---
title: "Le type de l’expression est «&lt;typename&gt;» qui est un type restreint et ne peut pas être utilisé pour accéder aux membres hérités de &quot;Object&quot; ou &quot;ValueType&quot; | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc31393
- vbc31393
dev_langs:
- VB
helpviewer_keywords:
- BC31393
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
caps.latest.revision: 6
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
ms.openlocfilehash: aaedfd825889498159f92cbd1d615cc0064973d3
ms.lasthandoff: 03/13/2017

---
# <a name="expression-has-the-type-39lttypenamegt39-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-39object39-or-39valuetype39"></a>Le type de l’expression est «&lt;typename&gt;» qui est un type restreint et ne peut pas être utilisé pour accéder aux membres hérités de 'Object' ou 'ValueType'
Une expression correspond à un type qui ne peut pas être boxed par le common language runtime (CLR) mais accède à un membre qui nécessite une conversion boxing.  
  
 *Conversion boxing* fait référence au traitement nécessaire pour convertir un type en `Object` ou, éventuellement, pour <xref:System.ValueType>.</xref:System.ValueType> Le common language runtime ne peut pas zone certains types de structure, par exemple <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>et <xref:System.TypedReference>.</xref:System.TypedReference> </xref:System.RuntimeArgumentHandle> </xref:System.ArgIterator>  
  
 Cette expression tente d’utiliser le type restreint pour appeler une méthode héritée <xref:System.Object>ou <xref:System.ValueType>, telles que <xref:System.Object.GetHashCode%2A>ou <xref:System.Object.ToString%2A>.</xref:System.Object.ToString%2A> </xref:System.Object.GetHashCode%2A> </xref:System.ValueType> </xref:System.Object> Pour accéder à cette méthode, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] a tenté une conversion boxing implicite qui provoque cette erreur.  
  
 **ID d’erreur :** BC31393  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Recherchez l’expression évaluée comme étant le type cité.  
  
2.  Localisez la partie de votre instruction qui essaie d’appeler la méthode héritée <xref:System.Object>ou <xref:System.ValueType>.</xref:System.ValueType> </xref:System.Object>  
  
3.  Réécrivez l’instruction pour éviter l’appel de méthode.  
  
## <a name="see-also"></a>Voir aussi  
 [Conversions implicites et explicites](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
