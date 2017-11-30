---
title: "Comment : accéder aux membres d'un objet (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- members [Visual Basic], accessing
- object variables [Visual Basic], accessing members
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 85fa4932b449bf7b9ecb3902fc17fd954ea8cfac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-members-of-an-object-visual-basic"></a>Comment : accéder aux membres d'un objet (Visual Basic)
Lorsque vous disposez d’une variable objet qui fait référence à un objet, vous souhaitez souvent travailler avec les membres de cet objet, comme ses méthodes, propriétés, champs et des événements. Par exemple, après avoir créé un nouveau <xref:System.Windows.Forms.Form> de l’objet, vous souhaiterez peut-être définir son <xref:System.Windows.Forms.Control.Text%2A> propriété ou l’appel de ses <xref:System.Windows.Forms.Control.Focus%2A> (méthode).  
  
## <a name="accessing-members"></a>L’accès aux membres  
 Vous accéder aux membres d’un objet via la variable qui fait référence à celui-ci.  
  
#### <a name="to-access-members-of-an-object"></a>Pour accéder aux membres d’un objet  
  
-   Utilisez l’opérateur d’accès aux membres (`.`) entre le nom de variable objet et le nom du membre.  
  
    ```  
    currentText = newForm.Text  
    ```  
  
     Si le membre est [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), vous n’avez pas besoin d’une variable pour y accéder.  
  
## <a name="accessing-members-of-an-object-of-known-type"></a>L’accès aux membres d’un objet de Type connu  
 Si vous connaissez le type d’un objet au moment de la compilation, vous pouvez utiliser *liaison anticipée* pour une variable qui fait référence à celui-ci.  
  
#### <a name="to-access-members-of-an-object-for-which-you-know-the-type-at-compile-time"></a>Pour accéder aux membres d’un objet dont vous connaissez le type au moment de la compilation  
  
1.  Déclarez la variable objet comme étant du type de l’objet que vous prévoyez d’affecter à la variable.  
  
    ```  
    Dim extraForm As System.Windows.Forms.Form  
    ```  
  
     Avec `Option Strict On`, vous pouvez affecter uniquement <xref:System.Windows.Forms.Form> objets (ou objets d’un type dérivé <xref:System.Windows.Forms.Form>) à `extraForm`. Si vous avez défini une classe ou une structure avec une étendue `CType` conversion <xref:System.Windows.Forms.Form>, vous pouvez également affecter cette classe ou structure `extraForm`.  
  
2.  Utilisez l’opérateur d’accès aux membres (`.`) entre le nom de variable objet et le nom du membre.  
  
    ```  
    extraForm.Show()  
    ```  
  
     Vous pouvez accéder à toutes les méthodes et propriétés spécifiques à la <xref:System.Windows.Forms.Form> (classe), quel que soit ce que le `Option Strict` paramètre est.  
  
## <a name="accessing-members-of-an-object-of-unknown-type"></a>L’accès aux membres d’un objet de Type inconnu  
 Si vous ne connaissez pas le type d’un objet au moment de la compilation, vous devez utiliser *liaison tardive* pour n’importe quelle variable qui fait référence à celui-ci.  
  
#### <a name="to-access-members-of-an-object-for-which-you-do-not-know-the-type-at-compile-time"></a>Pour accéder aux membres d’un objet pour lequel vous ignorez le type au moment de la compilation  
  
1.  Déclarez la variable objet de la [Type de données d’objet](../../../../visual-basic/language-reference/data-types/object-data-type.md). (Déclaration d’une variable en tant que `Object` est identique à la déclarer comme <xref:System.Object?displayProperty=nameWithType>.)  
  
    ```  
    Dim someControl As Object  
    ```  
  
     Avec `Option Strict On`, vous pouvez accéder uniquement aux membres qui sont définis sur la <xref:System.Object> classe.  
  
2.  Utilisez l’opérateur d’accès aux membres (`.`) entre le nom de variable objet et le nom du membre.  
  
    ```  
    someControl.GetType()  
    ```  
  
     Pour pouvoir accéder aux membres de n’importe quel objet que vous assignez à la variable objet, vous devez définir `Option Strict Off`. Dans ce cas, le compilateur ne peut pas garantir qu’un membre donné est exposé par l’objet que vous affectez à la variable. Si l’objet n’expose pas un membre de tenter d’y accéder, un <xref:System.MemberAccessException> cette exception est levée.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Object>  
 <xref:System.Windows.Forms.Form>  
 <xref:System.MemberAccessException>  
 [Variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Déclaration des variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [Object (type de données)](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [Option Strict (instruction)](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
