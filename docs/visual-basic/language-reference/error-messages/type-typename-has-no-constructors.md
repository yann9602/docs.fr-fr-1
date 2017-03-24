---
title: "Type &quot;&lt;typename&gt;&quot; n’a aucun constructeur | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30251
- vbc30251
dev_langs:
- VB
helpviewer_keywords:
- BC30251
ms.assetid: aff3e1df-abe6-4bc0-9abc-a1e70514c561
caps.latest.revision: 9
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
ms.openlocfilehash: 505e3bbdfa830394efcea7226897ec0d3e6d2b02
ms.lasthandoff: 03/13/2017

---
# <a name="type-39lttypenamegt39-has-no-constructors"></a>Type '&lt;typename&gt;' a pas de constructeurs
Un type ne prend pas en charge un appel à `Sub New()`. L'une des causes probables est un fichier compilateur ou binaire endommagé.  
  
 **ID d’erreur :** BC30251  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Si le type se trouve dans un projet différent ou dans un fichier référencé, réinstallez le projet ou le fichier.  
  
2.  Si le type se trouve dans le même projet, recompilez l'assembly contenant le type.  
  
3.  Si l'erreur se produit à nouveau, réinstallez le compilateur [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
4.  Si l'erreur persiste, rassemblez des informations sur ses circonstances et avertissez les services de support technique Microsoft.  
  
## <a name="see-also"></a>Voir aussi  
 [Objets et Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [Nous contacter](https://docs.microsoft.com/visualstudio/ide/talk-to-us)
