---
title: "Vue d’ensemble des constantes (Visual Basic) | Documents Microsoft"
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
- constants
ms.assetid: 29016fe8-78b3-4dc8-90b8-1cfec2fa8ac9
caps.latest.revision: 14
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
ms.openlocfilehash: 8004045d233da0db017b26b350743ad9f8d61845
ms.lasthandoff: 03/13/2017

---
# <a name="constants-overview-visual-basic"></a>Vue d'ensemble des constantes (Visual Basic)
Une constante est un nom significatif qui prend la place d’un nombre ou une chaîne qui ne change pas. Les constantes stockent des valeurs qui, comme son nom l’indique, demeurent identiques lors de l’exécution d’une application. Vous pouvez considérablement améliorer la lisibilité de votre code et le rendre plus facile à gérer à l’aide de constantes. Les utiliser dans le code qui contient des valeurs qui réapparaissent ou qui dépend de certains nombres difficiles à mémoriser ou sans signification évidente.  
  
## <a name="how-to-create-and-use-constants"></a>Comment créer et utiliser des constantes  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]contient plusieurs constantes prédéfinies, principalement à l’aide de l’impression et d’affichage. Vous pouvez également créer vos propres constantes avec le `Const` instruction, en utilisant les mêmes instructions que vous le feriez pour la création d’un nom de variable. Si `Option Strict` est `On`, vous devez déclarer explicitement le type de constante.  
  
 La portée d’une constante, qui est l’ensemble du code que vous pouvez vous y référer sans qualifier son nom, est identique à celle d’une variable déclarée au même emplacement. Pour créer une constante qui existe dans la portée d’une procédure particulière, vous devez la déclarer dans cette procédure. Pour créer une constante qui est disponible dans une application, déclarez-le à l’aide de le `Public` mot clé dans la section des déclarations de la classe.  
  
> [!NOTE]
>  Bien que les constantes ressemblent un peu aux variables, les modifier ni leur assigner de nouvelles valeurs que possible à des variables.  
  
 Les constantes utilisées dans votre code peuvent être définies par le modèle objet pour les contrôles ou les composants que vous utilisez, ou ils peuvent être définis par l’utilisateur (celles que vous créez vous-même).  
  
## <a name="compile-time-and-run-time-constants"></a>Constantes de compilation et d’exécution  
 Une constante de compilation est calculée au moment où que le code est compilé pendant une constante d’exécution peut être calculée uniquement pendant que l’application est en cours d’exécution. Une constante de compilation aura la même valeur chaque fois qu'une application s’exécute, une constante d’exécution peut être modifié chaque fois. Constantes de compilation sont nécessaires pour les cas tels que les limites de tableau, les expressions de cas ou les initialiseurs d’énumérateur.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Définition|Terme|  
|---|---|  
|[Guide pratique : déclarer une constante](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)|Explique comment utiliser le `Const` l’instruction pour déclarer une constante et définir sa valeur ; en déclarant une constante, vous attribuer un nom significatif à la valeur.|  
|[Constantes définies par l’utilisateur](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)|Décrit comment créer vos propres constantes, y compris des informations sur la portée et comment éviter les références circulaires.|  
|[Constantes et types de données littérales](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)|Fournit des informations sur la façon dont les [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilateur initialise des constantes lorsque `Option Explicit` est désactivé.|  
|[Guide pratique : regrouper les valeurs de constante connexes](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-group-related-constant-values-together.md)|Montre comment grouper des valeurs constantes qui sont liées.|  
  
## <a name="reference"></a>Référence  
  
|Définition|Terme|  
|---|---|  
|[Constantes et énumérations](../../../../visual-basic/language-reference/constants-and-enumerations.md)|Répertorie les constantes prédéfinies par [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].|  
|[Const (instruction)](../../../../visual-basic/language-reference/statements/const-statement.md)|Décrit la `Const` instruction et son utilisation.|  
|[Option Strict (instruction)](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|Décrit la `Option Strict` instruction et son utilisation.|  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des énumérations](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)   
 [Comment : initialiser une Variable tableau en Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
