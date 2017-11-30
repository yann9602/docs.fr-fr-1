---
title: "Opérateur GetType (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 38a984dce44133936f7f163e6afb20f0f336377c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="gettype-operator-visual-basic"></a>Opérateur GetType (Visual Basic)
Retourne un <xref:System.Type> objet pour le type spécifié. Le <xref:System.Type> objet fournit des informations sur le type telles que ses propriétés, méthodes et événements.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
GetType(typename)  
```  
  
#### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---|---|  
|`typename`|Le nom du type pour lequel vous souhaitez des informations.|  
  
## <a name="remarks"></a>Remarques  
 Le `GetType` opérateur retourne le <xref:System.Type> objet spécifié `typename`. Vous pouvez passer le nom de tout type défini dans `typename`. Ce dernier est détaillé ci-après :  
  
-   Type de données Visual Basic, tel que `Boolean` ou `Date`.  
  
-   Toute classe .NET Framework, structure, module ou interface, tel que <xref:System.ArgumentException?displayProperty=nameWithType> ou <xref:System.Double?displayProperty=nameWithType>.  
  
-   Toute classe, structure, module ou interface définie par votre application.  
  
-   Tout tableau défini par votre application.  
  
-   Tout délégué défini par votre application.  
  
-   Toute énumération définie par votre application, le .NET Framework ou Visual Basic.  
  
 Si vous souhaitez obtenir l’objet de type d’une variable objet, utilisez le <xref:System.Type.GetType%2A?displayProperty=nameWithType> (méthode).  
  
 Le `GetType` opérateur peut être utile dans les circonstances suivantes :  
  
-   Vous devez accéder à des métadonnées pour un type au moment de l’exécution. Le <xref:System.Type> objet qui fournit des métadonnées telles que les membres de type et des informations sur le déploiement. Vous devez, par exemple, réfléchir à un assembly. Pour plus d'informations, consultez <xref:System.Reflection?displayProperty=nameWithType>.  
  
-   Vous souhaitez comparer deux références d’objet pour voir s’ils font référence à des instances du même type. Dans le cas, `GetType` retourne des références au même <xref:System.Type> objet.  
  
## <a name="example"></a>Exemple  
 Les exemples suivants illustrent la `GetType` opérateur en cours d’utilisation.  
  
 [!code-vb[VbVbalrOperators#26](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/gettype-operator_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Opérateurs et expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
