---
title: "Dépannage des tableaux (Visual Basic) | Documents Microsoft"
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
- troubleshooting arrays
- arrays [Visual Basic], initialization errors
- troubleshooting Visual Basic, arrays
- arrays [Visual Basic], compilation errors
- arrays [Visual Basic], declaration errors
- arrays [Visual Basic], troubleshooting
ms.assetid: f4e971c7-c0a4-4ed7-a77a-8d71039f266f
caps.latest.revision: 17
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
ms.openlocfilehash: db38c0c2a4f8b74a6b862f86f426b4d8837f4424
ms.lasthandoff: 03/13/2017

---
# <a name="troubleshooting-arrays-visual-basic"></a>Dépannage des tableaux (Visual Basic)
Cette page répertorie quelques problèmes courants qui peuvent se produire lorsque vous travaillez avec des tableaux.  
  
## <a name="compilation-errors-declaring-and-initializing-an-array"></a>Erreurs de compilation déclarer et initialiser un tableau  
 Erreurs de compilation peuvent survenir à une mauvaise compréhension des règles de déclaration, la création et initialisation des tableaux. Les causes les plus courantes d’erreurs sont les suivants :  
  
-   En fournissant un [nouveau opérateur](../../../../visual-basic/language-reference/operators/new-operator.md) clause après avoir spécifié les longueurs de dimensions dans la déclaration de variable tableau. Les lignes de code suivantes affichent des déclarations non valides de ce type.  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
-   Spécification des longueurs de dimensions plus longtemps que le tableau de niveau supérieur d’un tableau en escalier. La ligne de code suivant montre une déclaration non valide de ce type.  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
-   En omettant le `New` mot clé lorsque vous spécifiez les valeurs d’élément. La ligne de code suivant montre une déclaration non valide de ce type.  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
-   En fournissant un `New` clause sans accolades (`{}`). Les lignes de code suivantes affichent des déclarations non valides de ce type.  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## <a name="accessing-an-array-out-of-bounds"></a>Accès à un tableau hors limites  
 Le processus d’initialisation d’un tableau assigne une limite supérieure et inférieure à chaque dimension. Chaque accès à un élément du tableau doit spécifier un index valide ou un indice, pour chaque dimension. Si un index est inférieure à sa limite inférieure ou supérieure sa limite supérieure, une <xref:System.IndexOutOfRangeException>résultats de l’exception.</xref:System.IndexOutOfRangeException> Le compilateur ne peut pas détecter une telle erreur, donc une erreur se produit au moment de l’exécution.  
  
### <a name="determining-bounds"></a>Détermination des limites  
 Si un autre composant passe un tableau à votre code, par exemple en tant qu’argument de procédure, vous ne connaissez pas la taille de ce tableau ni les longueurs de ses dimensions. Vous devez toujours déterminer la limite supérieure de chaque dimension d’un tableau avant de tenter d’accéder aux éléments. Si le tableau a été créé par un moyen autre qu’un [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] `New` clause, la limite inférieure peut avoir une valeur différente de 0, et il est plus sûre pour déterminer cette limite inférieure.  
  
### <a name="specifying-the-dimension"></a>Spécification de la Dimension  
 Pour déterminer les limites d’un tableau multidimensionnel, veillez à vous spécifiez comment la dimension. Le `dimension` paramètres de le <xref:System.Array.GetLowerBound%2A>et <xref:System.Array.GetUpperBound%2A>méthodes sont basées sur 0 lors de la `Rank` paramètres de le [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] <xref:Microsoft.VisualBasic.Information.LBound%2A>et <xref:Microsoft.VisualBasic.Information.UBound%2A>fonctions sont de base 1.</xref:Microsoft.VisualBasic.Information.UBound%2A> </xref:Microsoft.VisualBasic.Information.LBound%2A> </xref:System.Array.GetUpperBound%2A> </xref:System.Array.GetLowerBound%2A>  
  
## <a name="see-also"></a>Voir aussi  
 [Tableaux](../../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [Comment : initialiser une Variable tableau en Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
