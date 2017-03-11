---
title: "How to: Access Members of an Object (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "members, accessing"
  - "object variables, accessing members"
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 20
---
# How to: Access Members of an Object (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Lorsque vous avez une variable objet qui fait référence à un objet, vous souhaitez souvent travailler avec les membres de cet objet, tels que ses méthodes, propriétés, champs et événements.  Par exemple, une fois que vous avez créé un nouvel objet <xref:System.Windows.Forms.Form>, vous souhaiterez peut\-être définir sa propriété <xref:System.Windows.Forms.Control.Text%2A> ou appeler sa méthode <xref:System.Windows.Forms.Control.Focus%2A>.  
  
## Accès aux membres  
 Vous pouvez accéder aux membres d'un objet par le biais de la variable qui y fait référence.  
  
#### Pour accéder aux membres d'un objet  
  
-   Utilisez l'opérateur d'accès aux membres \(`.`\) entre le nom de variable objet et le nom de membre.  
  
    ```  
    currentText = newForm.Text  
    ```  
  
     Si le membre est [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), vous n'avez pas besoin d'une variable pour y accéder.  
  
## Accès aux membres d'un objet de type connu  
 Si vous connaissez le type d'un objet au moment de la compilation, vous pouvez utiliser la *liaison anticipée* pour une variable qui y fait référence.  
  
#### Pour accéder aux membres d'un objet dont vous connaissez le type au moment de la compilation  
  
1.  Déclarez la variable objet comme étant du type de l'objet que vous envisagez d'assigner à la variable.  
  
    ```  
    Dim extraForm As System.Windows.Forms.Form   
    ```  
  
     Avec `Option Strict On`, vous pouvez affecter uniquement des objets <xref:System.Windows.Forms.Form> \(ou des objets d'un type dérivé de <xref:System.Windows.Forms.Form>\) `extraForm`.  Si vous avez défini une classe ou une structure avec une conversion `CType` étendue à <xref:System.Windows.Forms.Form>, vous pouvez assigner également cette classe ou structure à `extraForm`.  
  
2.  Utilisez l'opérateur d'accès aux membres \(`.`\) entre le nom de variable objet et le nom de membre.  
  
    ```  
    extraForm.Show()  
    ```  
  
     Vous pouvez accéder à toutes les méthodes et propriétés spécifiques à la classe <xref:System.Windows.Forms.Form>, quel que soit le paramètre `Option Strict`.  
  
## Accès aux membres d'un objet de type inconnu  
 Si vous ne connaissez pas le type d'un objet au moment de la compilation, vous devez utiliser la *liaison tardive* pour toute variable qui y fait référence.  
  
#### Pour accéder aux membres d'un objet dont vous ne connaissez pas le type au moment de la compilation  
  
1.  Déclarez la variable objet comme étant de [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).  \(La déclaration d'une variable comme `Object` revient à la déclarer comme <xref:System.Object?displayProperty=fullName>.\)  
  
    ```  
    Dim someControl As Object   
    ```  
  
     Avec `Option Strict On`, vous pouvez accéder uniquement aux membres qui sont définis sur la classe <xref:System.Object>.  
  
2.  Utilisez l'opérateur d'accès aux membres \(`.`\) entre le nom de variable objet et le nom de membre.  
  
    ```  
    someControl.GetType()  
    ```  
  
     Pour être en mesure d'accéder aux membres de tout objet que vous assignez à la variable objet, vous devez définir `Option Strict Off`.  Lorsque vous faites cela, le compilateur ne peut pas garantir qu'un membre donné est exposé par l'objet que vous assignez à la variable.  Si l'objet n'expose pas un membre auquel vous essayez d'accéder, une exception <xref:System.MemberAccessException> est générée.  
  
## Voir aussi  
 <xref:System.Object>   
 <xref:System.Windows.Forms.Form>   
 <xref:System.MemberAccessException>   
 [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Object Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)   
 [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)   
 [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)