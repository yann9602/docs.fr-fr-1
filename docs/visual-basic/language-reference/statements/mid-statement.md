---
title: Mid, instruction | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.MidB
- vb.Mid
dev_langs:
- VB
helpviewer_keywords:
- substrings, Mid statement
- strings [Visual Basic], substrings
- Mid statement
- strings [Visual Basic], replacing
ms.assetid: 2b82d7a8-9646-4cb0-bec5-80abc98297bf
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e385d6838daa16d45903c6b270fc47ad88797845
ms.lasthandoff: 03/13/2017

---
# <a name="mid-statement"></a>Mid, instruction
Remplace un nombre spécifié de caractères dans un `String` variable avec des caractères d’une autre chaîne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a>Composants  
 `Target`  
 Obligatoire. Nom de la `String` variable à modifier.  
  
 `Start`  
 Obligatoire. `Integer`expression. Position du caractère dans `Target` où commence le remplacement de texte. `Start`utilise un index de base&1;.  
  
 `Length`  
 Facultatif. `Integer`expression. Nombre de caractères à remplacer. Si omis, tous les `String` est utilisé.  
  
 `StringExpression`  
 Obligatoire. `String`Expression qui remplace une partie de `Target`.  
  
## <a name="exceptions"></a>Exceptions  
  
|Type d'exception|Condition|  
|--------------------|---------------|  
|<xref:System.ArgumentException></xref:System.ArgumentException>|`Start`<= 0="" or=""></=>`Length`< 0.></ 0.>|  
  
## <a name="remarks"></a>Remarques  
 Le nombre de caractères remplacés est toujours inférieur ou égal au nombre de caractères dans `Target`.  
  
 Visual Basic a un <xref:Microsoft.VisualBasic.Strings.Mid%2A>fonction et un `Mid` relevé.</xref:Microsoft.VisualBasic.Strings.Mid%2A> Ces éléments fonctionnent à la fois sur un nombre spécifié de caractères dans une chaîne, mais la `Mid` fonction retourne les caractères pendant que la `Mid` instruction remplace les caractères. Pour plus d’informations, consultez <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</xref:Microsoft.VisualBasic.Strings.Mid%2A>  
  
> [!NOTE]
>  La `MidB` instruction des versions antérieures de Visual Basic remplace une sous-chaîne en octets, plutôt que des caractères. Il est utilisé principalement pour la conversion de chaînes dans les applications codés sur deux octets (DBCS) de jeu. Toutes les chaînes Visual Basic sont en Unicode, et `MidB` n’est plus pris en charge.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise la `Mid` instruction pour remplacer un nombre spécifié de caractères dans une variable de chaîne de caractères à partir d’une autre chaîne.  
  
 [!code-vb[VbVbalrStrings n °&5;](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/mid-statement_1.vb)]  
  
## <a name="requirements"></a>Spécifications  
 **Namespace :** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Module :**`Strings`  
  
 **Assembly :**[!INCLUDE[vbprvbruntime](../../../visual-basic/language-reference/objects/includes/vbprvbruntime_md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A></xref:Microsoft.VisualBasic.Strings.Mid%2A>   
 [Chaînes](../../../visual-basic/programming-guide/language-features/strings/index.md)   
 [Introduction aux chaînes en Visual Basic](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
