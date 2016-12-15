---
title: "Troubleshooting Arrays (Visual Basic) | Microsoft Docs"
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
  - "troubleshooting arrays"
  - "arrays [Visual Basic], initialization errors"
  - "troubleshooting Visual Basic, arrays"
  - "arrays [Visual Basic], compilation errors"
  - "arrays [Visual Basic], declaration errors"
  - "arrays [Visual Basic], troubleshooting"
ms.assetid: f4e971c7-c0a4-4ed7-a77a-8d71039f266f
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Troubleshooting Arrays (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Cette page répertorie quelques problèmes courants qui peuvent se produire lors de l'utilisation des tableaux.  
  
## Déclaration d'erreurs de compilation et initialisation d'un tableau  
 Les erreurs de compilation peuvent être dues à une mauvaise compréhension des règles de déclaration, de création et d'initialisation des tableaux.  Les causes d'erreurs les plus courantes sont les suivantes :  
  
-   fournir une clause [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) après avoir spécifié les longueurs de dimension dans la déclaration des variables du tableau.  Les lignes de code suivantes affichent des déclarations non valides de ce type.  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
-   spécifier des longueurs de dimension supérieures au tableau de niveau supérieur d'un tableau en escalier.  La ligne de code suivante affiche une déclaration non valide de ce type ;  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
-   omettre le mot clé `New` lors de la spécification des valeurs d'éléments.  La ligne de code suivante affiche une déclaration non valide de ce type ;  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
-   fournir une clause `New` sans accolades \(`{}`\).  Les lignes de code suivantes affichent des déclarations non valides de ce type.  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## Accès à un tableau hors limites  
 Le processus d'initialisation d'un tableau assigne une limite supérieure et une limite inférieure à chaque dimension.  Chaque accès à un élément du tableau doit spécifier un index ou un indice valide pour chaque dimension.  Si un index est en dessous de sa limite inférieure ou au\-dessus de sa limite supérieure, une d'exception <xref:System.IndexOutOfRangeException> se produit.  Le compilateur ne peut pas détecter une telle erreur, donc une erreur se produit au moment de l'exécution.  
  
### Détermination des limites  
 Si un autre composant passe un tableau à votre code, par exemple en tant qu'argument de procédure, vous ne connaissez pas la taille de ce tableau ou les longueurs de ses dimensions.  Vous devez toujours déterminer la limite supérieure de chaque dimension d'un tableau avant d'essayer d'accéder aux éléments.  Si le tableau a été créé par des moyens autres qu'une clause `New` de [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], la limite inférieure peut avoir une valeur différente de 0 et il est plus sûr de déterminer également cette limite inférieure.  
  
### Spécification de la dimension  
 Lorsque vous déterminez les limites d'un tableau multidimensionnel, veillez à bien spécifier la dimension.  Les paramètres `dimension` des méthodes <xref:System.Array.GetLowerBound%2A> et <xref:System.Array.GetUpperBound%2A> sont de base 0, tandis que les paramètres `Rank` des fonctions <xref:Microsoft.VisualBasic.Information.LBound%2A> et <xref:Microsoft.VisualBasic.Information.UBound%2A> de [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] sont de base 1.  
  
## Voir aussi  
 [Tableaux](../../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [How to: Initialize an Array Variable in Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)