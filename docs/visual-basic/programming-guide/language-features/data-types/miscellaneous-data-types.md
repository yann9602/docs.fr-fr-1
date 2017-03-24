---
title: "Types de données divers (Visual Basic) | Documents Microsoft"
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
- Object data type, data types
- data types [Visual Basic], choosing
ms.assetid: 64c71a12-9057-4dbf-baca-7379c4aada69
caps.latest.revision: 22
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
ms.openlocfilehash: 2de377fa9dfd7ec13cdbb9b700f8485b0c0e2106
ms.lasthandoff: 03/13/2017

---
# <a name="miscellaneous-data-types-visual-basic"></a>Types de données divers (Visual Basic)
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]fournit plusieurs types de données qui ne sont pas adaptés pour les nombres ou de caractères. Au lieu de cela, ils traitent des données particulières telles qu’Oui/non valeurs, les valeurs de date/heure et adresses de l’objet.  
  
 Pour un tableau présentant une comparaison côte-à-côte de la [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] des types de données, consultez [des Types de données](../../../../visual-basic/language-reference/data-types/data-type-summary.md).  
  
## <a name="boolean-type"></a>Type booléen  
 Le [Type de données Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) est une valeur non signée qui est interprétée comme `True` ou `False`. Sa largeur de données dépend de la plateforme d’implémentation. Si une variable peut contenir uniquement les valeurs de deux États tels que true/false, Oui/non ou actif/inactif, déclarez-le en tant que `Boolean`.  
  
## <a name="date-type"></a>Type de date  
 Le [Type de données Date](../../../../visual-basic/language-reference/data-types/date-data-type.md) est une valeur 64 bits qui conserve des informations de date et d’heure. Chaque incrément représente 100 nanosecondes du temps écoulé depuis le début (12:00 AM) le 1er janvier de l’année 1 du calendrier grégorien. Si une variable peut contenir une valeur de date, une valeur d’heure ou les deux, déclarez-le en tant que `Date`.  
  
## <a name="object-type"></a>Type d'objet  
 Le [Type de données d’objet](../../../../visual-basic/language-reference/data-types/object-data-type.md) est une adresse 32 bits qui pointe vers une instance d’objet dans votre application ou une autre application. Une `Object` variable peut faire référence à un objet de votre application reconnaît ou à des données de n’importe quel type de données. Cela inclut les deux *des types valeur*, tel que `Integer`, `Boolean`et des instances de structure, et *types référence*, qui sont des instances d’objets créés à partir de classes telles que `String` et <xref:System.Windows.Forms.Form>et les instances de tableau.</xref:System.Windows.Forms.Form>  
  
 Si une variable stocke un pointeur vers une instance d’une classe que vous ne savez pas au moment de la compilation, ou si elle peut pointer vers des données de différents types de données, déclarez-le en tant que `Object`.  
  
 L’avantage de le `Object` est de type de données que vous pouvez l’utiliser pour stocker des données de n’importe quel type de données. L’inconvénient est que vous subissez des opérations supplémentaires qui prennent plus de temps d’exécution et de rendre votre application plus lentes. Si vous utilisez un `Object` variable pour les types valeur, vous subissez *boxing* et *unboxing*. Si vous l’utilisez pour les types référence, vous subissez *liaison tardive*.  
  
## <a name="see-also"></a>Voir aussi  
 [Caractères de type](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)   
 [Types de données élémentaires](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Types de données numériques](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)   
 [Types de données caractère](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)   
 [Dépannage des Types de données](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Liaison anticipée et liaison tardive](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
