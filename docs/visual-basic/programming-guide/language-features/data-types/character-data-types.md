---
title: "Character Data Types (Visual Basic) | Microsoft Docs"
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
  - "data types [Visual Basic], character"
  - "String data type, character data types"
  - "character data types [Visual Basic]"
  - "Char data type, character data types"
  - "data types [Visual Basic], choosing"
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Character Data Types (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] met à votre disposition des *types de données caractères* permettant de gérer les caractères affichables et imprimables.  Si les deux types reconnaissent les caractères Unicode, `Char` n'accepte qu'un seul caractère, tandis que `String` peut contenir un nombre quelconque de caractères.  
  
 Pour consulter un tableau présentant une comparaison côte à côte des types de données de [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], consultez [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md).  
  
## Type Char  
 Le type de données `Char` est un caractère Unicode à deux octets \(16 bits\) unique.  Si une variable stocke toujours exactement un caractère, déclarez\-la comme `Char`.  Par exemple :  
  
 [!code-vb[VbVbalrCharTypes#1](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/character-data-types_1.vb)]  
  
 Chaque valeur possible dans une variable `Char` ou `String` est un *point de code*, ou code de caractère, dans le jeu de caractères Unicode.  Les caractères Unicode incluent le jeu de caractères ASCII de base, plusieurs autres lettres de l'alphabet, des accents, des symboles monétaires, des fractions, des signes diacritiques ainsi que des symboles mathématiques et techniques.  
  
> [!NOTE]
>  Le jeu de caractères Unicode réserve les points de code D800 à DFFF \(55 296 à 55 551 décimal\) pour les *paires de substitution*, qui requièrent deux valeurs de 16 bits pour représenter un seul point de code.  Une variable `Char` ne peut pas contenir de paire de substitution et une variable `String` utilise deux positions pour contenir une telle paire.  
  
 Pour plus d'informations, consultez [Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md).  
  
## Type String  
 Le type de données `String` est une séquence de zéro ou de plusieurs caractères Unicode à deux octets \(16 bits\).  Si une variable peut contenir un nombre indéfini de caractères, déclarez\-la comme `String`.  Par exemple :  
  
 [!code-vb[VbVbalrCharTypes#2](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/character-data-types_2.vb)]  
  
 Pour plus d'informations, consultez [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md).  
  
## Voir aussi  
 [Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)   
 [Types génériques Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Type Characters](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)