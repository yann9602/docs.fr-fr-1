---
title: "Débogage d’arborescences d’expression dans Visual Studio (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
caps.latest.revision: "4"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d74df8ba339526e20850cd8b8f1a4b37c20e22ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a>Débogage d’arborescences d’expression dans Visual Studio (C#)
Vous pouvez analyser la structure et le contenu d’arborescences d’expression quand vous déboguez vos applications. Pour obtenir une vue d’ensemble rapide de la structure de l’arborescence d’expressions, vous pouvez utiliser la propriété `DebugView`, qui est disponible uniquement en mode débogage. Pour plus d’informations sur le débogage, consultez [Débogage dans Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).  
  
 Afin de mieux représenter le contenu des arborescences d’expressions, la propriété `DebugView` utilise des visualiseurs Visual Studio. Pour plus d’informations, consultez [Créer des visualiseurs de données personnalisés](/visualstudio/debugger/create-custom-visualizers-of-data).  
  
### <a name="to-open-a-visualizer-for-an-expression-tree"></a>Pour ouvrir un visualiseur pour une arborescence d’expressions  
  
1.  Cliquez sur l’icône représentant une loupe qui est située en regard de la propriété `DebugView` d’une arborescence d’expressions dans **DataTips**, dans une fenêtre **Espion**, dans la fenêtre **Automatique** ou dans la fenêtre **Variables locales**.  
  
     Une liste de visualiseurs s'affiche.  
  
2.  Cliquez sur le visualiseur à utiliser.  
  
 Chaque type d’expression s’affiche dans le visualiseur, comme décrit dans les sections suivantes.  
  
## <a name="parameterexpressions"></a>ParameterExpressions  
 Les noms de variables <xref:System.Linq.Expressions.ParameterExpression> s’affichent avec le symbole "$" en préfixe.  
  
 Si un paramètre n’a pas de nom, un nom généré automatiquement lui est assigné, tel que `$var1` ou `$var2`.  
  
### <a name="examples"></a>Exemples  
  
|Expression|Propriété `DebugView`|  
|----------------|--------------------------|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int), "num");`|`$num`|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int));`|`$var1`|  
  
## <a name="constantexpressions"></a>ConstantExpressions  
 Pour les objets <xref:System.Linq.Expressions.ConstantExpression> qui représentent des valeurs entières, des chaînes et des valeurs `null`, la valeur de la constante est affichée.  
  
 Pour les types numériques comportant des suffixes standard comme littéraux C#, le suffixe est ajouté à la valeur. Le tableau suivant indique les suffixes associés aux différents types numériques.  
  
|Type|Suffixe|  
|----------|------------|  
|<xref:System.UInt32>|U|  
|<xref:System.Int64>|L|  
|<xref:System.UInt64>|UL|  
|<xref:System.Double>|D|  
|<xref:System.Single>|F|  
|<xref:System.Decimal>|M|  
  
### <a name="examples"></a>Exemples  
  
|Expression|Propriété `DebugView`|  
|----------------|--------------------------|  
|`int num = 10; ConstantExpression expr = Expression.Constant(num);`|10|  
|`double num = 10; ConstantExpression expr = Expression.Constant(num);`|10D|  
  
## <a name="blockexpression"></a>BlockExpression  
 Si le type d’un objet <xref:System.Linq.Expressions.BlockExpression> diffère du type de la dernière expression du bloc, le type est affiché dans la propriété `DebugInfo` entre crochets pointus (\< et >). Sinon, le type de l’objet <xref:System.Linq.Expressions.BlockExpression> n’est pas affiché.  
  
### <a name="examples"></a>Exemples  
  
|Expression|Propriété `DebugView`|  
|----------------|--------------------------|  
|`BlockExpression block = Expression.Block(Expression.Constant("test"));`|`.Block() {`<br /><br /> `"test"`<br /><br /> `}`|  
|`BlockExpression block =  Expression.Block(typeof(Object), Expression.Constant("test"));`|`.Block<System.Object>() {`<br /><br /> `"test"`<br /><br /> `}`|  
  
## <a name="lambdaexpression"></a>LambdaExpression  
 Les objets <xref:System.Linq.Expressions.LambdaExpression> sont affichés avec leurs types délégués.  
  
 Si une expression lambda n’a pas de nom, un nom généré automatiquement lui est assigné, tel que `#Lambda1` ou `#Lambda2`.  
  
### <a name="examples"></a>Exemples  
  
|Expression|Propriété `DebugView`|  
|----------------|--------------------------|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1));`|`.Lambda #Lambda1<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1), "SampleLambda", null);`|`.Lambda SampleLambda<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
  
## <a name="labelexpression"></a>LabelExpression  
 Si vous spécifiez une valeur par défaut pour l’objet <xref:System.Linq.Expressions.LabelExpression>, cette valeur est affichée avant l’objet <xref:System.Linq.Expressions.LabelTarget>.  
  
 Le jeton `.Label` indique le début de l’étiquette. Le jeton `.LabelTarget` indique la destination de la cible à laquelle accéder.  
  
 Si une étiquette n’a pas de nom, un nom généré automatiquement lui est assigné, tel que `#Label1` ou `#Label2`.  
  
### <a name="examples"></a>Exemples  
  
|Expression|Propriété `DebugView`|  
|----------------|--------------------------|  
|`LabelTarget target = Expression.Label(typeof(int), "SampleLabel"); BlockExpression block = Expression.Block( Expression.Goto(target, Expression.Constant(0)), Expression.Label(target, Expression.Constant(-1)));`|`.Block() {`<br /><br /> `.Goto SampleLabel { 0 };`<br /><br /> `.Label`<br /><br /> `-1`<br /><br /> `.LabelTarget SampleLabel:`<br /><br /> `}`|  
|`LabelTarget target = Expression.Label(); BlockExpression block = Expression.Block( Expression.Goto(target5), Expression.Label(target5));`|`.Block() {`<br /><br /> `.Goto #Label1 { };`<br /><br /> `.Label`<br /><br /> `.LabelTarget #Label1:`<br /><br /> `}`|  
  
## <a name="checked-operators"></a>Opérateurs Checked  
 Les opérateurs Checked sont affichés précédés du symbole "#". Par exemple, l’opérateur d’addition checked est affiché sous la forme `#+`.  
  
### <a name="examples"></a>Exemples  
  
|Expression|Propriété `DebugView`|  
|----------------|--------------------------|  
|`Expression expr = Expression.AddChecked( Expression.Constant(1), Expression.Constant(2));`|`1 #+ 2`|  
|`Expression expr = Expression.ConvertChecked( Expression.Constant(10.0), typeof(int));`|`#(System.Int32)10D`|  
  
## <a name="see-also"></a>Voir aussi  
 [Arborescences d’expressions (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
 [Débogage dans Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)  
 [Créer des visualiseurs personnalisés](/visualstudio/debugger/create-custom-visualizers-of-data)
