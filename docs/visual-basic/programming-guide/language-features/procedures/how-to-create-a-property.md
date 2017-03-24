---
title: "How to: Create a Property (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "procedures, defining"
  - "Visual Basic code, procedures"
  - "Visual Basic code, properties"
  - "properties [Visual Basic]"
ms.assetid: 4d229712-6be8-4c5c-bac5-06995ce9185a
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# How to: Create a Property (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Entourez une définition de propriété entre une instruction `Property` et une instruction `End Property`.  Dans cette définition, définissez une procédure `Get` ou une procédure `Set`, ou les deux.  L'intégralité du code de cette propriété doit se trouver dans ces procédures.  
  
 La procédure `Get` récupère la valeur de la propriété et la propriété `Set` stocke une valeur.  Si vous souhaitez spécifier un accès en lecture\/écriture, vous devez définir les deux procédures.  `Get` doit être défini pour une propriété en lecture seule, et `Set` pour une propriété en écriture seule.  
  
### Pour créer une propriété  
  
1.  En dehors d'une propriété ou d'une procédure, utilisez une [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md), suivie d'une instruction `End Property`.  
  
2.  Si la propriété prend des paramètres, faites suivre le mot clé `Property` du nom de la procédure, puis de la liste de paramètres entre parenthèses.  
  
3.  Faites suivre les parenthèses d'une clause `As` pour spécifier le type de données de la valeur de la propriété.  Vous devez spécifier le type de données, même pour une propriété en écriture seule.  
  
4.  Ajoutez les procédures `Get` et `Set`, selon le cas.  Reportez\-vous aux instructions suivantes.  
  
### Pour créer une procédure Get qui récupère une valeur de propriété  
  
1.  Entre les instructions `Property` et `End Property`, écrivez une [Get Statement](../../../../visual-basic/language-reference/statements/get-statement.md), suivie d'une instruction `End Get` Il n'est pas nécessaire de définir de paramètre pour la procédure `Get`.  
  
2.  Placez les instructions de code pour récupérer la valeur de la propriété entre les instructions `Get` et `End Get` Ce code peut inclure d'autres calculs et des manipulations de données en plus de la génération et du retour de la valeur de la propriété.  
  
3.  Utilisez une instruction `Return` pour retourner la valeur de la propriété au code appelant.  
  
 Vous devez écrire une procédure `Get` pour une propriété en lecture\-écriture et pour une propriété en lecture seule.  Vous ne devez pas définir de procédure `Get` pour une propriété en écriture seule.  
  
### Pour créer une procédure Set qui écrit la valeur d'une propriété  
  
1.  Entre les instructions `Property` et `End Property`, écrivez une [Set Statement](../../../../visual-basic/language-reference/statements/set-statement.md), suivie d'une instruction `End Set`  
  
2.  Dans l'instruction `Set`, faites suivre le mot clé `Set` d'une liste de paramètres entre parenthèses.  Cette liste de paramètres doit inclure au moins un paramètre de valeur pour la valeur transférée par le code appelant.  Le nom par défaut pour ce paramètre de valeur est `Value`, mais vous pouvez utiliser un nom différent selon le cas.  Le paramètre de valeur doit avoir le même type de données que la propriété elle\-même.  
  
3.  Placez les instructions de code pour stocker une valeur dans la propriété entre les instructions `Set` et `End Set`.  Ce code peut inclure d'autres calculs et des manipulations de données en plus de la validation et du stockage de la valeur de la propriété.  
  
4.  Utilisez le paramètre de la valeur pour accepter la valeur fournie par le code appelant.  Vous pouvez stocker cette valeur directement dans une instruction d'assignation ou l'utiliser dans une expression pour calculer la valeur interne à stocker.  
  
 Vous devez écrire une procédure `Set` pour une propriété en lecture\-écriture et pour une propriété en écriture seule.  Vous ne devez pas définir de procédure `Set` pour une propriété en lecture seule.  
  
## Exemple  
 L'exemple suivant crée une propriété en lecture\/écriture qui stocke un nom complet comme deux noms constitutifs, le prénom et le nom.  Lorsque le code appelant lit `fullName`, la procédure `Get` combine les deux noms constitutifs et retourne le nom complet.  Lorsque le code appelant assigne un nouveau nom complet, la procédure `Set` tente de le décomposer en deux noms constitutifs.  S'il ne trouve pas d'espace, il le stocke en tant que prénom.  
  
 [!code-vb[VbVbcnProcedures#8](./codesnippet/VisualBasic/how-to-create-a-property_1.vb)]  
  
 L'exemple suivant montre des appels typiques aux procédures Property de `fullName`.  Le premier appel définit la valeur de propriété et le deuxième appel la récupère.  
  
 [!code-vb[VbVbcnProcedures#9](./codesnippet/VisualBasic/how-to-create-a-property_2.vb)]  
  
## Voir aussi  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procédures de propriété](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Differences Between Properties and Variables in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)   
 [How to: Declare a Property with Mixed Access Levels](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)   
 [How to: Call a Property Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-a-property-procedure.md)   
 [How to: Declare and Call a Default Property in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)   
 [How to: Put a Value in a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-put-a-value-in-a-property.md)   
 [How to: Get a Value from a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-get-a-value-from-a-property.md)