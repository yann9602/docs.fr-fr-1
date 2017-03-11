---
title: "Constants Overview (Visual Basic) | Microsoft Docs"
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
  - "constants"
ms.assetid: 29016fe8-78b3-4dc8-90b8-1cfec2fa8ac9
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# Constants Overview (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Une constante est un nom significatif qui symbolise un nombre ou une chaîne invariable.  Les constantes stockent des valeurs qui, comme leur nom l'indique, demeurent identiques lors de l'exécution d'une application.  Vous pouvez améliorer considérablement la lisibilité de votre code et simplifier sa gestion en utilisant des constantes.  Utilisez\-les dans du code qui contient des valeurs qui réapparaissent ou qui dépend de certains nombres qui sont difficiles à mémoriser ou qui n'ont aucune signification évidente.  
  
## Comment créer et utiliser des constantes  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] contient plusieurs constantes prédéfinies, qui sont utilisées principalement pour l'impression et l'affichage.  Vous pouvez également créer vos propres constantes avec l'instruction `Const`, en utilisant les mêmes indications que celles permettant de créer un nom de variable.  Si `Option Strict` est `On`, vous devez déclarer le type de constante de manière explicite.  
  
 La portée d'une constante, qui correspond à l'ensemble du code qui peut y faire référence sans qualifier son nom, est identique à celle d'une variable déclarée au même emplacement.  Pour créer une constante existant dans la portée d'une procédure particulière, vous devez la déclarer dans cette procédure.  Pour créer une constante qui soit disponible pour l'ensemble d'une application, vous devez la déclarer à l'aide du mot clé `Public` dans la section des déclarations de la classe.  
  
> [!NOTE]
>  Bien que les constantes ressemblent un peu aux variables, vous ne pouvez pas les modifier ni leur assigner de nouvelles valeurs, contrairement aux variables.  
  
 Les constantes utilisées dans votre code peuvent être définies par le modèle d'objet pour les contrôles ou les composants que vous utilisez ou être définies par l'utilisateur \(celles que vous créez personnellement\).  
  
## Constantes de compilation et d'exécution  
 Une constante de compilation est calculée lors de la compilation du code, alors qu'une constante d'exécution peut être calculée uniquement durant l'exécution de l'application.  Une constante de compilation aura la même valeur chaque fois qu'une application s'exécute, tandis qu'une constante d'exécution peut changer à chaque fois.  Les constantes de compilation sont nécessaires pour les cas, tels que les tailles de tableau, les expressions de cas ou les initialiseurs d'énumérateur.  
  
## Dans cette section  
  
|||  
|-|-|  
|Définition|Terme|  
|[How to: Declare A Constant](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)|Explique comment utiliser l'instruction `Const` pour déclarer une constante et définir sa valeur ; la déclaration d'une constante permet d'assigner un nom significatif à la valeur.|  
|[User\-Defined Constants](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)|Décrit comment créer vos propres constantes, y compris des informations sur les portées et comment éviter les références circulaires.|  
|[Constant and Literal Data Types](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)|Fournit des informations sur la façon dont le compilateur [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] initialise des constantes lorsque le paramètre `Option Explicit` est désactivé.|  
|[How to: Group Related Constant Values Together](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-group-related-constant-values-together.md)|Illustre le groupement des valeurs de constante qui sont liées.|  
  
## Référence  
  
|||  
|-|-|  
|Définition|Terme|  
|[Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md)|Répertorie les constantes prédéfinies par [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)].|  
|[Const Statement](../../../../visual-basic/language-reference/statements/const-statement.md)|Décrit l'instruction `Const` et son utilisation.|  
|[Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|Décrit l'instruction `Option Strict` et son utilisation.|  
  
## Voir aussi  
 [Enumerations Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)   
 [How to: Initialize an Array Variable in Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)