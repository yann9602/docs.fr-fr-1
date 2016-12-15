---
title: "Miscellaneous Data Types (Visual Basic) | Microsoft Docs"
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
  - "Object data type, data types"
  - "data types [Visual Basic], choosing"
ms.assetid: 64c71a12-9057-4dbf-baca-7379c4aada69
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Miscellaneous Data Types (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] met à votre disposition plusieurs types de données qui ne correspondent ni à des nombres ni à des caractères.  Ces types de données correspondent à des données particulières, telles que des valeurs oui\/non, des valeurs date\/heure et des adresses d'objets.  
  
 Pour consulter un tableau présentant une comparaison côte à côte des types de données de [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], consultez [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md).  
  
## Type Boolean  
 Le [Boolean Data Type](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) est une valeur non signée qui est interprétée comme `True` ou `False`.  Sa largeur de données dépend de la plateforme d'implémentation.  Si une variable est destinée à ne contenir que des informations à deux états de type true\/false, yes\/no ou on\/off, déclarez\-la comme `Boolean`.  
  
## Type Date  
 Le [Date Data Type](../../../../visual-basic/language-reference/data-types/date-data-type.md) est une valeur 64 bits qui contient des informations d'horodatage.  Chaque incrément représente 100 nanosecondes du temps écoulé depuis le 1er janvier \(0 heure\) de l'an 1 du calendrier grégorien.  Si une variable peut contenir une valeur de date, une valeur d'heure ou les deux, déclarez\-la comme `Date`.  
  
## Type d'objet  
 [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) est une adresse 32 bits qui pointe vers une instance de l'objet dans votre application ou vers une autre application.  Une variable `Object` peut faire référence à tout objet que votre application reconnaît ou à des données de tout type de données.  Cela inclut *les types valeur*, tels qu' `Integer`, `Boolean`, et des instances de structure, et *les types référence*, qui sont des instances d'objets créés à partir de classes telles qu' `String` et <xref:System.Windows.Forms.Form>, et le tableau de recherches.  
  
 Si une variable stocke un pointeur vers une instance d'une classe que vous ne connaissez pas au moment de la compilation ou si elle peut pointer vers des données de plusieurs types de données, déclarez\-la comme `Object`.  
  
 L'avantage du type de données d' `Object` est que vous pouvez l'utiliser pour stocker des données de n'importe quel type de données.  L'inconvénient est que vous subissez des opérations supplémentaires qui allongent le temps d'exécution et ralentissent votre application.  Si vous utilisez une variable `Object` pour des types valeur, vous subissez des conversions *boxing* et *unboxing*.  Si vous l'utilisez pour des types référence, vous subissez des *liaisons tardives*.  
  
## Voir aussi  
 [Type Characters](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)   
 [Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Numeric Data Types](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)   
 [Character Data Types](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)   
 [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Early and Late Binding](../../../../visual-basic/programming-guide/language-features/early-late-binding/early-and-late-binding.md)