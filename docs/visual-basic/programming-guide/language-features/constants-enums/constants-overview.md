---
title: Vue d'ensemble des constantes (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: constants [Visual Basic]
ms.assetid: 29016fe8-78b3-4dc8-90b8-1cfec2fa8ac9
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e6526f7270602b3e1a4e8d953732c393ff252b2c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="constants-overview-visual-basic"></a>Vue d'ensemble des constantes (Visual Basic)
Une constante est un nom explicite qui prend la place d’un nombre ou une chaîne qui ne change pas. Les constantes stockent des valeurs qui, comme son nom l’indique, restent les mêmes tout au long de l’exécution d’une application. Vous pouvez considérablement améliorer la lisibilité de votre code et le rendre plus facile à gérer à l’aide de constantes. Utilisez-les dans du code qui contient des valeurs qui réapparaissent ou qui dépend de certains numéros sont difficiles à mémoriser ou n’ont aucune signification évidente.  
  
## <a name="how-to-create-and-use-constants"></a>Comment créer et utiliser des constantes  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]contient plusieurs constantes prédéfinies, principalement à l’aide de l’impression et d’affichage. Vous pouvez également créer vos propres constantes avec le `Const` instruction, à l’aide des mêmes instructions que vous le feriez pour la création d’un nom de variable. Si `Option Strict` est `On`, vous devez déclarer explicitement le type de constante.  
  
 La portée d’une constante, qui est l’ensemble du code qui peut faire référence à ce dernier sans qualifier son nom, est identique à celle d’une variable déclarée dans le même emplacement. Pour créer une constante qui existe dans la portée d’une procédure particulière, vous devez la déclarer dans cette procédure. Pour créer une constante qui est disponible dans une application, déclarez-le à l’aide de la `Public` mot clé dans la section des déclarations de la classe.  
  
> [!NOTE]
>  Bien que les constantes ressemblent un peu aux variables, vous ne peut pas modifier ou leur assigner de nouvelles valeurs que vous pouvez effectuer sur les variables.  
  
 Les constantes que vous utilisez dans votre code peuvent être définies par le modèle objet pour les contrôles ou les composants que vous utilisez, ou ils peuvent être définis par l’utilisateur (autrement dit, celles que vous créez vous-même).  
  
## <a name="compile-time-and-run-time-constants"></a>Constantes de compilation et d’exécution  
 Une constante de compilation est calculée au moment que le code est compilé pendant une constante d’exécution peut être calculée uniquement pendant l’exécution de l’application. Une constante de compilation aura la même valeur chaque fois qu'une application s’exécute, une constante d’exécution peut être modifié chaque fois. Constantes de compilation sont requis pour les cas, tels que les limites de tableau, les expressions de cas ou les initialiseurs d’énumérateur.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Définition|Terme|  
|---|---|  
|[Guide pratique : déclarer une constante](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)|Explique comment utiliser la `Const` instruction pour déclarer une constante et définir sa valeur ; en déclarant une constante, vous affectez un nom significatif à la valeur.|  
|[Constantes définies par l’utilisateur](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)|Décrit comment créer vos propres constantes, y compris des informations sur la portée et comment éviter les références circulaires.|  
|[Constantes et types de données littérales](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)|Fournit des informations sur la façon dont le [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilateur initialise des constantes lorsque `Option Explicit` est désactivé.|  
|[Guide pratique : regrouper les valeurs de constante connexes](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-group-related-constant-values-together.md)|Montre comment regrouper des valeurs constantes qui sont liées.|  
  
## <a name="reference"></a>Référence  
  
|Définition|Terme|  
|---|---|  
|[Constantes et énumérations](../../../../visual-basic/language-reference/constants-and-enumerations.md)|Répertorie les constantes prédéfinies par [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].|  
|[Const (instruction)](../../../../visual-basic/language-reference/statements/const-statement.md)|Décrit la `Const` instruction et son utilisation.|  
|[Option Strict (instruction)](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|Décrit la `Option Strict` instruction et son utilisation.|  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des énumérations](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)  
 [Comment : initialiser une variable tableau en Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
