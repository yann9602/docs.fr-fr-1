---
title: "Dépannage des tableaux (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- troubleshooting arrays
- arrays [Visual Basic], initialization errors
- troubleshooting Visual Basic, arrays
- arrays [Visual Basic], compilation errors
- arrays [Visual Basic], declaration errors
- arrays [Visual Basic], troubleshooting
ms.assetid: f4e971c7-c0a4-4ed7-a77a-8d71039f266f
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0417ae8d37642a65b14cc81ae9dcf3a3c32d63ce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="troubleshooting-arrays-visual-basic"></a>Dépannage des tableaux (Visual Basic)
Cette page répertorie certains problèmes courants qui peuvent se produire lorsque vous travaillez avec des tableaux.  
  
## <a name="compilation-errors-declaring-and-initializing-an-array"></a>Déclaration et l’initialisation d’un tableau d’erreurs de compilation  
 Erreurs de compilation peuvent se produire à une mauvaise compréhension des règles de déclaration, la création et initialisation des tableaux. Les causes les plus courantes d’erreurs sont les suivants :  
  
-   En fournissant un [nouvel opérateur](../../../../visual-basic/language-reference/operators/new-operator.md) clause après avoir spécifié les longueurs de dimensions dans la déclaration de variable tableau. Les lignes de code suivantes illustrent des déclarations non valides de ce type.  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
-   Pour plus d’informations à un tableau de niveau supérieur d’un tableau en escalier, en spécifiant des longueurs de dimensions. La ligne de code suivant montre une déclaration non valide de ce type.  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
-   L’omission de la `New` mot clé lorsque vous spécifiez les valeurs d’élément. La ligne de code suivant montre une déclaration non valide de ce type.  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
-   En fournissant un `New` clause sans accolades (`{}`). Les lignes de code suivantes illustrent des déclarations non valides de ce type.  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## <a name="accessing-an-array-out-of-bounds"></a>L’accès à un tableau hors limites  
 Le processus d’initialisation d’un tableau assigne une limite supérieure et inférieure à chaque dimension. Tous les accès à un élément du tableau doivent spécifier un index valide, ou un indice, pour chaque dimension. Si un index est inférieur à sa limite inférieure ou au-dessus de sa limite supérieure, une <xref:System.IndexOutOfRangeException> résultats de l’exception. Le compilateur ne peut pas détecter une telle erreur, donc une erreur se produit au moment de l’exécution.  
  
### <a name="determining-bounds"></a>Détermination des limites  
 Si un autre composant passe un tableau à votre code, par exemple en tant qu’argument de procédure, vous ne connaissez pas la taille de ce tableau ou les longueurs de ses dimensions. Vous devez toujours déterminer la limite supérieure de chaque dimension d’un tableau avant de tenter d’accéder aux éléments. Si le tableau a été créé par un moyen autre qu’un [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] `New` clause, la limite inférieure peut avoir une valeur différente de 0, et il est plus sûre pour déterminer ce inférieure.  
  
### <a name="specifying-the-dimension"></a>Spécification de la Dimension  
 Lorsque vous déterminez les limites d’un tableau multidimensionnel, prenez soin la façon dont vous spécifiez la dimension. Le `dimension` les paramètres de la <xref:System.Array.GetLowerBound%2A> et <xref:System.Array.GetUpperBound%2A> méthodes sont basés sur 0, lors de la `Rank` paramètres de la [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] <xref:Microsoft.VisualBasic.Information.LBound%2A> et <xref:Microsoft.VisualBasic.Information.UBound%2A> fonctions sont de base 1.  
  
## <a name="see-also"></a>Voir aussi  
 [Tableaux](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Comment : initialiser une variable tableau en Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
