---
title: "Comment : définir un paramètre pour une procédure (Visual Basic) | Documents Microsoft"
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
- procedure parameters, defining data types for
- procedures, parameters
- procedures, defining
- Visual Basic code, procedures
- procedure parameters, defining
ms.assetid: 7962808d-407e-4e84-984e-43e9857c53c9
caps.latest.revision: 15
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
ms.openlocfilehash: 9fb9ad244499039c1768ff97f071168e0a0842e4
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-define-a-parameter-for-a-procedure-visual-basic"></a>Comment : définir un paramètre pour une procédure (Visual Basic)
A *paramètre* permet au code appelant de passer une valeur à la procédure lorsqu’il l’appelle. Vous déclarez chaque paramètre pour une procédure de la même manière que vous déclarez une variable, en spécifiant son nom et type de données. Vous spécifiez également le mécanisme de passage et si le paramètre est facultatif.  
  
 Pour plus d’informations, consultez [paramètres de procédure et les Arguments](./procedure-parameters-and-arguments.md).  
  
### <a name="to-define-a-procedure-parameter"></a>Pour définir un paramètre de procédure  
  
1.  Dans la déclaration de procédure, ajoutez le nom du paramètre à la liste de paramètres de la procédure, en le séparant des autres paramètres par des virgules.  
  
2.  Déterminez le type de données du paramètre.  
  
3.  Suivre le nom du paramètre avec une `As` clause pour spécifier le type de données.  
  
4.  Choisissez le mécanisme de passage souhaité pour le paramètre. Normalement, vous passez un paramètre par valeur, sauf si vous souhaitez que la procédure puisse modifier sa valeur dans le code appelant.  
  
5.  Faites précéder le nom de paramètre avec [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) pour spécifier le mécanisme de passage. Pour plus d’informations, consultez [différences entre passage d’un Argument par valeur et par référence](./differences-between-passing-an-argument-by-value-and-by-reference.md).  
  
6.  Si le paramètre est facultatif, faites précéder le mécanisme de passage de [facultatif](../../../../visual-basic/language-reference/modifiers/optional.md) et suivez le type de données de paramètre d’un signe égal (`=`) et une valeur par défaut.  
  
     L’exemple suivant définit le contour d’un `Sub` procédure avec trois paramètres. Les deux premiers sont requis et le troisième est facultatif. Les déclarations de paramètre sont séparées dans la liste de paramètres par des virgules.  
  
     [!code-vb[VbVbcnProcedures&#33;](./codesnippet/VisualBasic/how-to-define-a-parameter-for-a-procedure_1.vb)]  
  
     Le premier paramètre accepte un `customer` objet, et `updateCustomer` pouvez mettre directement à jour la variable passée à `c` , car l’argument est passé [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md). La procédure ne peut pas modifier les valeurs des deux derniers arguments parce qu’ils sont passés [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).  
  
     Si le code appelant ne fournit pas une valeur pour le `level` paramètre [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] lui affecte la valeur par défaut 0.  
  
     Si le commutateur de la vérification de type ([Option Strict, instruction](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) est `Off`, le `As` clause est facultative lorsque vous définissez un paramètre. Toutefois, si un paramètre utilise une `As` clause, tous doivent l’utiliser. Si le commutateur de vérification de type est `On`, le `As` clause est requise pour chaque définition de paramètre.  
  
     Spécifier les types de données pour tous les éléments de programmation est appelé *typage fort*. Lorsque vous définissez `Option Strict On`, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] applique un typage fort. Il est fortement recommandé, pour les raisons suivantes :  
  
    -   Il permet la prise en charge IntelliSense pour vos variables et des paramètres. Cela vous permet de voir leurs propriétés et autres membres que vous entrez dans votre code.  
  
    -   Il permet au compilateur d’effectuer la vérification du type. Cela permet d’intercepter les instructions peuvent échouer au moment de l’exécution en raison d’erreurs de dépassement de capacité. Il intercepte également les appels aux méthodes sur les objets qui ne les prennent pas en charge.  
  
    -   Il en résulte une exécution plus rapide de votre code. L’une des raisons sont que si vous ne spécifiez pas un type de données pour un élément de programmation, le [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilateur lui assigne la `Object` type. Votre code compilé peut avoir à convertir entre `Object` et d’autres types de données, ce qui réduit les performances.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures](./index.md)   
 [Procédures Sub](./sub-procedures.md)   
 [Procédures Function](./function-procedures.md)   
 [Comment : passer des Arguments à une procédure](./how-to-pass-arguments-to-a-procedure.md)   
 [Passage des Arguments par valeur et par référence](./passing-arguments-by-value-and-by-reference.md)   
 [Procédures récursives](./recursive-procedures.md)   
 [Surcharge de procédure](./procedure-overloading.md)   
 [Objets et Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [Programmation orientée objet](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)
