---
title: "Comment : créer une propriété (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, properties
- properties [Visual Basic]
ms.assetid: 4d229712-6be8-4c5c-bac5-06995ce9185a
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d140e6a10061f7fabe3d12c6cce5d0c201e103d6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-property-visual-basic"></a>Comment : créer une propriété (Visual Basic)
Vous placez une définition de propriété entre un `Property` instruction et un `End Property` instruction. Dans cette définition, définissez une `Get` procédure, un `Set` procédure, ou les deux. Code de toutes les propriétés se trouve dans ces procédures.  
  
 Le `Get` procédure récupère la valeur de propriété et la `Set` stocke une valeur. Si vous souhaitez que la propriété à accéder en lecture/écriture, vous devez définir les deux procédures. Pour une propriété en lecture seule, vous définissez uniquement `Get`, et pour une propriété en écriture seule, vous définissez uniquement `Set`.  
  
### <a name="to-create-a-property"></a>Pour créer une propriété  
  
1.  En dehors d’une propriété ou une procédure, utilisez un [Property, instruction](../../../../visual-basic/language-reference/statements/property-statement.md), suivi d’un `End Property` instruction.  
  
2.  Si la propriété accepte des paramètres, suivez le `Property` mot clé avec le nom de la procédure, puis la liste de paramètres entre parenthèses.  
  
3.  Suivez les parenthèses d’une `As` clause pour spécifier le type de données de la valeur de propriété. Vous devez spécifier le type de données, même pour une propriété en écriture seule.  
  
4.  Ajouter `Get` et `Set` procédures, comme il convient. Reportez-vous aux instructions suivantes.  
  
### <a name="to-create-a-get-procedure-that-retrieves-a-property-value"></a>Pour créer une procédure Get qui Récupère une valeur de propriété  
  
1.  Entre le `Property` et `End Property` écrire des instructions, une [instruction Get](../../../../visual-basic/language-reference/statements/get-statement.md), suivi d’un `End Get` instruction. Vous n’avez pas besoin définir des paramètres pour le `Get` procédure.  
  
2.  Placez les instructions de code pour récupérer la valeur de propriété entre le `Get` et `End Get` instructions. Ce code peut inclure les autres calculs et des manipulations de données en plus de la génération et du retour de la valeur de propriété.  
  
3.  Utilisez un `Return` instruction pour retourner la valeur de propriété au code appelant.  
  
 Vous devez écrire un `Get` procédure pour une propriété en lecture-écriture et pour une propriété en lecture seule. Vous ne devez pas définir un `Get` procédure pour une propriété en écriture seule.  
  
### <a name="to-create-a-set-procedure-that-writes-a-propertys-value"></a>Pour créer une procédure Set qui écrit une valeur de propriété  
  
1.  Entre le `Property` et `End Property` écrire des instructions, une [instruction Set](../../../../visual-basic/language-reference/statements/set-statement.md), suivi d’un `End Set` instruction.  
  
2.  Dans le `Set` instruction, suivez le `Set` mot clé avec une liste de paramètres entre parenthèses. Cette liste de paramètres doit inclure au moins un paramètre de valeur pour la valeur passée par le code appelant. Le nom par défaut pour ce paramètre de valeur est `Value`, mais vous pouvez utiliser un nom différent si nécessaire. Le paramètre de valeur doit avoir les mêmes type de données en tant que la propriété proprement dite.  
  
3.  Placez les instructions de code pour stocker une valeur dans la propriété entre les `Set` et `End Set` instructions. Ce code peut inclure les autres calculs et des manipulations de données en plus de la validation et le stockage de la valeur de propriété.  
  
4.  Utilisez le paramètre value pour accepter la valeur fournie par le code appelant. Vous pouvez stocker cette valeur directement dans une instruction d’assignation ou utiliser dans une expression pour calculer la valeur interne à stocker.  
  
 Vous devez écrire un `Set` procédure pour une propriété en lecture-écriture et pour une propriété en écriture seule. Vous ne devez pas définir un `Set` procédure pour une propriété en lecture seule.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée une propriété en lecture/écriture qui stocke un nom complet comme deux noms constitutifs, le prénom et le nom de famille. Lorsque le code appelant lit `fullName`, le `Get` procédure combine les deux noms constitutifs et retourne le nom complet. Lorsque le code appelant assigne un nouveau nom complet, le `Set` procédure tente de diviser en deux noms constitutifs. S’il ne trouve pas d’un espace, il les stocke tout comme le prénom.  
  
 [!code-vb[VbVbcnProcedures#8](./codesnippet/VisualBasic/how-to-create-a-property_1.vb)]  
  
 L’exemple suivant montre des appels typiques aux procédures de propriété `fullName`. Le premier appel définit la valeur de propriété, le deuxième appel récupère.  
  
 [!code-vb[VbVbcnProcedures#9](./codesnippet/VisualBasic/how-to-create-a-property_2.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures](./index.md)  
 [Procédures de propriété](./property-procedures.md)  
 [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)  
 [Différences entre les propriétés et les Variables en Visual Basic](./differences-between-properties-and-variables.md)  
 [Guide pratique : déclarer une propriété avec des niveaux d’accès mixtes](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [Guide pratique : appeler une procédure de propriété](./how-to-call-a-property-procedure.md)  
 [Comment : déclarer et appeler une propriété par défaut en Visual Basic](./how-to-declare-and-call-a-default-property.md)  
 [Guide pratique : placer une valeur dans une propriété](./how-to-put-a-value-in-a-property.md)  
 [Guide pratique : obtenir une valeur d’une propriété](./how-to-get-a-value-from-a-property.md)
