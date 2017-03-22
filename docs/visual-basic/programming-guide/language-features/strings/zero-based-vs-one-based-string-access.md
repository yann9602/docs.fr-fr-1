---
title: "Vs de base zéro. Accès d’une chaîne de base dans Visual Basic | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
caps.latest.revision: 11
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 6cd2cab888bf336151ed26968119431f4ffc75f4
ms.lasthandoff: 03/13/2017

---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a>Vs de base zéro. Accès d’une chaîne de base dans Visual Basic
Cette rubrique compare comment [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] et [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] permettent d’accéder aux caractères dans une chaîne. Le [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] fournit toujours un accès de base zéro aux caractères d’une chaîne, tandis que [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fournit un accès de base zéro et basé sur un, selon la fonction.  
  
## <a name="one-based"></a>Basé sur un  
 Pour obtenir un exemple d’une base [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] , prenez le `Mid` (fonction). Elle accepte un argument qui indique la position de caractère à laquelle la sous-chaîne doit démarrer, commençant à la position 1. Le [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] <xref:System.String.Substring%2A?displayProperty=fullName>méthode prend un index du caractère dans la chaîne où la sous-chaîne doit démarrer, en commençant à la position 0.</xref:System.String.Substring%2A?displayProperty=fullName> Par conséquent, si vous avez une chaîne « ABCDE », les caractères individuels sont numérotés 1,2,3,4,5 pour la `Mid` (fonction), mais 0,1,2,3,4 pour la <xref:System.String.Substring%2A?displayProperty=fullName>méthode.</xref:System.String.Substring%2A?displayProperty=fullName>  
  
## <a name="zero-based"></a>Base zéro  
 Pour obtenir un exemple de base zéro [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] , prenez le `Split` (fonction). Il fractionne une chaîne et retourne un tableau contenant les sous-chaînes. Le [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] <xref:System.String.Split%2A?displayProperty=fullName>méthode également fractionne une chaîne et retourne un tableau contenant les sous-chaînes.</xref:System.String.Split%2A?displayProperty=fullName> Étant donné que la `Split` (fonction) et <xref:System.String.Split%2A>retour de la méthode [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] tableaux, elles doivent être de base zéro.</xref:System.String.Split%2A>  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A></xref:Microsoft.VisualBasic.Strings.Mid%2A>   
 <xref:Microsoft.VisualBasic.Strings.Split%2A></xref:Microsoft.VisualBasic.Strings.Split%2A>   
 <xref:System.String.Substring%2A></xref:System.String.Substring%2A>   
 <xref:System.String.Split%2A></xref:System.String.Split%2A>   
 [Introduction aux chaînes en Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
