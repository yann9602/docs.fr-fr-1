---
title: "Differences Between Properties and Variables in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "property values"
  - "variables [Visual Basic]"
  - "Visual Basic code, procedures"
  - "values, properties"
  - "variables [Visual Basic], definition"
  - "Visual Basic code, variables"
  - "Visual Basic code, properties"
  - "properties [Visual Basic], values"
  - "properties [Visual Basic], defined"
  - "variables [Visual Basic], and properties"
  - "properties [Visual Basic], and variables"
ms.assetid: 7a03a8be-5381-431f-bd7c-16e887e4e07b
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Differences Between Properties and Variables in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Les variables et propriétés représentent toutes deux des valeurs auxquelles vous pouvez accéder.  Toutefois, elles sont différentes en termes de stockage et d'implémentation.  
  
## Variables  
 Une *variable* correspond directement à un emplacement de mémoire.  Vous définissez une variable avec une instruction de déclaration unique.  Une variable peut être une *variable locale*, définie à l'intérieur d'une procédure et disponible uniquement dans cette procédure, ou ce peut être une *variable membre*, définie par l'utilisateur dans un module, une classe ou une structure, mais pas à l'intérieur d'une procédure.  Une variable membre porte également le nom de *champ*.  
  
## Propriétés  
 Une *propriété* est un élément de données défini sur un module, une classe ou une structure.  Vous définissez une propriété avec un bloc de code placé entre les instructions `Property` et `End Property`.  Le bloc de code contient une procédure `Get`, une procédure `Set`, ou les deux.  Ces procédures sont nommées *procédures property* ou *accesseurs de propriété*.  Outre la récupération ou le stockage de la valeur de la propriété, ils peuvent également effectuer des actions personnalisées, telles que la mise à jour d'un compteur d'accès.  
  
## Différences  
 Le tableau suivant présente certaines différences importantes entre les variables et les propriétés.  
  
|Point de différence|Variable|Propriété|  
|-------------------------|--------------|---------------|  
|Déclaration|Instruction de déclaration unique|Série d'instructions dans un bloc de code|  
|Implémentation|Emplacement de stockage unique|Code exécutable \(procédures property\)|  
|Stockage|Associé directement à la valeur de la variable|En général le stockage interne n'est pas disponible en dehors du module ou de la classe conteneur de la propriété.<br /><br /> La valeur de propriété peut ou ne peut pas exister en tant qu'élément <sup>1</sup> stocké|  
|Code exécutable|Aucun|Doit posséder au moins une procédure|  
|Accès en lecture et en écriture|Lecture\/écriture ou lecture seule|Lecture\/écriture, lecture seule ou écriture seule|  
|Actions personnalisées \(en plus de l'acceptation ou du retour d'une valeur\)|Impossible|Peut être exécuté dans le cadre de la définition ou de la récupération de la valeur d'une propriété|  
  
 <sup>1</sup> contrairement à une variable, la valeur d'une propriété ne peut pas correspondre directement à un élément unique de stockage.  Le stockage peut être fractionné par commodité ou sécurité, ou la valeur peut être stockée dans un formulaire chiffré.  Dans ces cas, la procédure `Get` assemblerait les éléments ou déchiffrerait la valeur stockée, et la procédure `Set` chiffrerait la nouvelle valeur ou la diviserait dans le stockage constitutif.  Une valeur de propriété peut être éphémère, comme l'heure du jour, dans ce cas la procédure `Get` la calcule à la volée chaque fois que vous accédez à la propriété.  
  
## Voir aussi  
 [Procédures de propriété](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md)   
 [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md)   
 [How to: Create a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-create-a-property.md)   
 [How to: Declare a Property with Mixed Access Levels](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)   
 [How to: Call a Property Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-a-property-procedure.md)   
 [How to: Declare and Call a Default Property in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)   
 [How to: Put a Value in a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-put-a-value-in-a-property.md)   
 [How to: Get a Value from a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-get-a-value-from-a-property.md)