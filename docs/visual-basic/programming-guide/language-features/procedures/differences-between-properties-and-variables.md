---
title: "Différences entre les propriétés et les variables en Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- property values [Visual Basic]
- variables [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- variables [Visual Basic], definition
- Visual Basic code, variables
- Visual Basic code, properties
- properties [Visual Basic], values
- properties [Visual Basic], defined
- variables [Visual Basic], and properties
- properties [Visual Basic], and variables
ms.assetid: 7a03a8be-5381-431f-bd7c-16e887e4e07b
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cb30972e2b49a7005749f57c0223b9fa493cde52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="differences-between-properties-and-variables-in-visual-basic"></a>Différences entre les propriétés et les variables en Visual Basic
Variables et propriétés représentent les valeurs auxquelles vous pouvez accéder. Toutefois, il existe des différences dans le stockage et l’implémentation.  
  
## <a name="variables"></a>Variables  
 A *variable* correspond directement à un emplacement de mémoire. Vous définissez une variable avec une instruction de déclaration unique. Une variable peut être un *variable locale*, défini à l’intérieur d’une procédure et disponible uniquement dans cette procédure, ou il peut être un *variable membre*, définis dans un module, classe ou structure, mais pas à l’intérieur d’une procédure. Une variable membre est également appelée un *champ*.  
  
## <a name="properties"></a>Propriétés  
 A *propriété* est un élément de données défini sur un module, classe ou structure. Vous définissez une propriété avec un bloc de code entre les `Property` et `End Property` instructions. Le bloc de code contient un `Get` procédure, un `Set` procédure, ou les deux. Ces procédures sont appelées *procédures de propriété* ou *les accesseurs de propriété*. En plus de la récupération ou le stockage de la valeur de propriété, ils peuvent également effectuer des actions personnalisées, telles que la mise à jour d’un compteur d’accès.  
  
## <a name="differences"></a>Différences  
 Le tableau suivant présente des différences importantes entre les variables et propriétés.  
  
|Point de différence|Variable|Propriété|  
|-------------------------|--------------|--------------|  
|Déclaration|Instruction de déclaration unique|Série d’instructions dans un bloc de code|  
|Implémentation|Emplacement de stockage unique|Code exécutable (procédures de propriété)|  
|Stockage|Directement associée à la valeur de la variable|Est généralement pas disponible en dehors de la classe ou le module conteneur de la propriété de stockage interne<br /><br /> Valeur de propriété peut ou peut ne pas exister en tant qu’un élément stocké <sup>1</sup>|  
|Code exécutable|None|Doit avoir au moins une procédure|  
|Accès en lecture et écriture|En lecture/écriture ou en lecture seule|En lecture/écriture, en lecture seule ou en écriture seule|  
|Actions personnalisées (en plus l’acceptation ou le renvoi de valeur)|N’est pas possible|Peut être effectuée dans le cadre de la définition ou la récupération de valeur de propriété|  
  
 <sup>1</sup> Contrairement à une variable, la valeur d’une propriété ne peut pas correspondre directement à un seul élément de stockage. Le stockage peut être fractionné par commodité ou sécurité, ou la valeur peut être stockée sous forme chiffrée. Dans ce cas le `Get` procédure serait assembler les éléments ou de déchiffrer la valeur stockée et le `Set` procédure permet de chiffrer la nouvelle valeur ou fractionner dans le stockage constitutif. Une valeur de propriété peut être éphémère, comme l’heure du jour, auquel cas la `Get` procédure calcule à la volée chaque fois que vous accédez à la propriété.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures de propriété](./property-procedures.md)  
 [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)  
 [Property (instruction)](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [Dim (instruction)](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Guide pratique : créer une propriété](./how-to-create-a-property.md)  
 [Guide pratique : déclarer une propriété avec des niveaux d’accès mixtes](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [Guide pratique : appeler une procédure de propriété](./how-to-call-a-property-procedure.md)  
 [Comment : déclarer et appeler une propriété par défaut en Visual Basic](./how-to-declare-and-call-a-default-property.md)  
 [Guide pratique : placer une valeur dans une propriété](./how-to-put-a-value-in-a-property.md)  
 [Guide pratique : obtenir une valeur d’une propriété](./how-to-get-a-value-from-a-property.md)
